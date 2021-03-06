# `smol-timeout`

[![img](https://img.shields.io/crates/l/smol-timeout.svg)](https://github.com/r3v2d0g/smol-timeout/blob/main/LICENSE.txt) [![img](https://img.shields.io/crates/v/smol-timeout.svg)](https://crates.io/crates/smol-timeout) [![img](https://docs.rs/smol-timeout/badge.svg)](https://docs.rs/smol-timeout)

A way to poll a future until it or a timer completes.


## Example

```rust
use async_io::Timer;
use smol_timeout::TimeoutExt;
use std::time::Duration;

let foo = async {
    Timer::new(Duration::from_millis(250)).await;
    24
};

let foo = foo.timeout(Duration::from_millis(100));
assert_eq!(foo.await, None);

let bar = async {
    Timer::new(Duration::from_millis(100)).await;
    42
};

let bar = bar.timeout(Duration::from_millis(250));
assert_eq!(bar.await, Some(42));
```


## License

> This Source Code Form is subject to the terms of the Mozilla Public License, v. 2.0. If a copy of the MPL was not distributed with this file, You can obtain one at <http://mozilla.org/MPL/2.0/>.
