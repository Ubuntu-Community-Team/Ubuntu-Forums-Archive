---
title: "Ubuntu 19.10 wouldn't install on top of 18.04 until I removed all partitions"
date: 2019-10-17
forum: Installation &amp; Upgrades
---

### Post by dankegel on 2019-10-17
A Skull Canyon (I think booting in classic mode) was running ubuntu 18.04.
I downloaded 19.10 onto a usb stick and installed.
Installation went bellyup with some error message about two partitions mapping to the same directory,
so I rebooted and tried again.  It kept failing, unable to mount VFAT partition #1.

So... I got a shell in the installer, used fdisk to delete all partitions, rebooted and retried.
That worked.

---

