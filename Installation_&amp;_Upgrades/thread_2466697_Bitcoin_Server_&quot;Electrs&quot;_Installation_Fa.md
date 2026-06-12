---
title: "Bitcoin Server &quot;Electrs&quot; Installation Failing"
date: 2021-09-03
forum: Installation &amp; Upgrades
---

### Post by lonephonix on 2021-09-03
I am trying to install an Electrum Server (electrs) to use it as a bridge between my Electrum Wallet software and my own Bitcoin node. However, while building the electrs, getting below mentioned error when I run the command - ./target/release/electrs -vvv --timestamp --db-dir ./db --electrum-rpc-addr="127.0.0.1:50001"   

2021-09-03T07:45:53.638-07:00 - WARN - failed to connect daemon at 127.0.0.1:8332: Connection refused (os error 111)

When I abort the command and rerun it, the output is -

Config { log: StdErrLog { verbosity: Debug, quiet: false, show_level: true, timestamp: Millisecond, modules: [], writer: "stderr", color_choice: Auto }, network_type: Bitcoin, db_path: "./db/mainnet", daemon_dir: "/home/phonix/.bitcoin", blocks_dir: "/home/phonix/.bitcoin/blocks", daemon_rpc_addr: V4(127.0.0.1:8332), electrum_rpc_addr: V4(127.0.0.1:50001), monitoring_addr: V4(127.0.0.1:4224), jsonrpc_import: false, index_batch_size: 10, bulk_index_threads: 4, tx_cache_size: 10485760, txid_limit: 100, server_banner: "Welcome to electrs 0.8.11 (Electrum Rust Server)!", blocktxids_cache_size: 10485760 }
thread 'main' panicked at 'failed to start monitoring HTTP server at 127.0.0.1:4224: Address already in use (os error 98)', src/metrics.rs:73:13
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace.

I am referring the video for the steps of Electrs installation - [https://www.youtube.com/watch?v=SMYlRICQ1cQ](https://www.youtube.com/watch?v=SMYlRICQ1cQ)

Please suggest how to overcome this error

---

### Post by coffeecat on 2021-09-04
Your linked video shows electrs being installed to Ubuntu Bionic Beaver. Please confirm which release and flavour of Ubuntu you are trying to install electrs to, or which Linux distro if not Ubuntu. Thanks.

---

