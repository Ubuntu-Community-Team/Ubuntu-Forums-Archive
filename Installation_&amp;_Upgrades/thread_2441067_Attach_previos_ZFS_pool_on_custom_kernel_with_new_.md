---
title: "Attach previos ZFS pool on custom kernel with new version ZFS"
date: 2020-04-18
forum: Installation &amp; Upgrades
---

### Post by dipol0 on 2020-04-18
Sorry for my ENG ^)

Previous i have standard kernel - 4.19.98-041998-lowlatency and build zfs-0.8.0_371 as module. Create pool TANK.
Now i:

- get kernel sources v5.4.33 from [https://www.kernel.org/](https://www.kernel.org/)
- get sources zfs-0.8.3 from [https://github.com/openzfs/zfs/releases/tag/zfs-0.8.3](https://github.com/openzfs/zfs/releases/tag/zfs-0.8.3) and integrate it in kernel sources. Make menuconfig, enable ZFS support (not as module), compile and build new custom kernel, install it and reboot....

After boot on new custom kernel i don't can attach may pool TANK.

When i mannualy try ***#zpool import TANK*** i get this message:

```
This pool uses the following feature(s) not supported by this system:
    com.delphix:log_spacemap (Log metaslab changes on a single spacemap and flush them periodically.)
All unsupported features are only required for writing to the pool.
The pool can be imported using '-o readonly=on'.
cannot import 'TANK': unsupported version or feature
```

:-k.... i can import pool TANK in read-only mode??? This is ](*,)

Check ***#zpool --version*** on custom kernel and get:

zfs-0.8.3-1
zfs-kmod-0.8.3-1

My previous installation be a 4.19.98-041998-lowlatency and i install zfs-0.8.0_371 as module and pool TANK be created with zfs-0.8.0_371 version and ***#zpool --version ***be as:

zfs-0.8.0_371
zfs-kmod-0.8.0_371

******************************************

Now i rebuild custom 5.4.33 kernel with previous zfs-0.8.0_371 version and pool TANK attached normally (in RW mode). But....

How i can do for use stable zfs-0.8.3 without recreate pool TANK as first time ? Another way exists ? Thnx.

---

### Post by dipol0 on 2020-04-19
I get answear here - [https://github.com/openzfs/zfs/issues/10229](https://github.com/openzfs/zfs/issues/10229)

:)

---

