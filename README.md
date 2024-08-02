# subnetwork

Returns an iterator that iterates over all subnet IPs.

[![Rust](https://github.com/rikonaka/subnetwork-rs/actions/workflows/rust.yml/badge.svg?branch=main)](https://github.com/rikonaka/subnetwork-rs/actions/workflows/rust.yml)

# Example

```rust
use std::net::Ipv4Addr;
use subnetwork::Ipv4Pool;

fn main() {
    let ipv4_pool = Ipv4Pool::from("192.168.1.0/24").unwrap();
    for i in ipv4_pool {
        println!("{:?}", i);
    }
    let ret = ipv4_pool.contain_from_str("192.168.1.200").unwrap();
    assert_eq!(ret, true);
    let ipv4 = Ipv4Addr::new(192, 168, 1, 1);
    let ret = ipv4_pool.contain(ipv4);
    assert_eq!(ret, true);
}
```

# Benchmark

You can see how our performance compares to other similar libraries [here](./benchmark/README.md).
