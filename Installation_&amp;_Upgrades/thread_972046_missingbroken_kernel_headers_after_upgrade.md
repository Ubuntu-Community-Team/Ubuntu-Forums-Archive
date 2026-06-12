---
title: "missing/broken kernel headers after upgrade"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by cnkbrown on 2008-11-05
after upgrading, my new linux headers directory has a bunch of softlinks to a directory that doesn't exist.  Do i need to install some other package?

Here's what I have;

```

cbrown@cbrown-laptop:/usr/src/linux-headers-2.6.25-2-386$ ls -l
total 436
drwxr-xr-x 3 root root   4096 2008-10-31 01:46 arch
lrwxrwxrwx 1 root root     31 2008-10-31 01:46 block -> ../linux-headers-2.6.25-2/block
lrwxrwxrwx 1 root root     32 2008-10-31 01:46 crypto -> ../linux-headers-2.6.25-2/crypto
lrwxrwxrwx 1 root root     39 2008-10-31 01:46 Documentation -> ../linux-headers-2.6.25-2/Documentation
lrwxrwxrwx 1 root root     33 2008-10-31 01:46 drivers -> ../linux-headers-2.6.25-2/drivers
lrwxrwxrwx 1 root root     28 2008-10-31 01:46 fs -> ../linux-headers-2.6.25-2/fs
drwxr-xr-x 5 root root   4096 2008-10-31 01:46 include
lrwxrwxrwx 1 root root     30 2008-10-31 01:46 init -> ../linux-headers-2.6.25-2/init
lrwxrwxrwx 1 root root     29 2008-10-31 01:46 ipc -> ../linux-headers-2.6.25-2/ipc
lrwxrwxrwx 1 root root     32 2008-10-31 01:46 Kbuild -> ../linux-headers-2.6.25-2/Kbuild
lrwxrwxrwx 1 root root     32 2008-10-31 01:46 kernel -> ../linux-headers-2.6.25-2/kernel
lrwxrwxrwx 1 root root     29 2008-10-31 01:46 lib -> ../linux-headers-2.6.25-2/lib
lrwxrwxrwx 1 root root     34 2008-10-31 01:46 Makefile -> ../linux-headers-2.6.25-2/Makefile
lrwxrwxrwx 1 root root     28 2008-10-31 01:46 mm -> ../linux-headers-2.6.25-2/mm
-rw-r--r-- 1 root root 426118 2008-09-30 11:28 Module.symvers
lrwxrwxrwx 1 root root     29 2008-10-31 01:46 net -> ../linux-headers-2.6.25-2/net
lrwxrwxrwx 1 root root     33 2008-10-31 01:46 samples -> ../linux-headers-2.6.25-2/samples
drwxr-xr-x 6 root root   4096 2008-10-31 01:46 scripts
lrwxrwxrwx 1 root root     34 2008-10-31 01:46 security -> ../linux-headers-2.6.25-2/security
lrwxrwxrwx 1 root root     31 2008-10-31 01:46 sound -> ../linux-headers-2.6.25-2/sound
lrwxrwxrwx 1 root root     29 2008-10-31 01:46 usr -> ../linux-headers-2.6.25-2/usr
cbrown@cbrown-laptop:/usr/src/linux-headers-2.6.25-2-386$ ls ..
linux-headers-2.6.20-16-386  linux-headers-2.6.25-2-386  linux-headers-2.6.27-7-generic  modules
linux-headers-2.6.24-17      linux-headers-2.6.27-7      linux-ports-headers-2.6.25-2    rpm

```

---

