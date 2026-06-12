---
title: "software raid and boot flag requirements"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2013-01-10
Just did a fresh install with a software RAID1 with two disks and two partitiones; "/" and "/home" plus a spare disk.

looking at the partitiones with gparted I noticed that only one disk in the array has the boot flag set.

Wouldn't that cause the a boot failure if that disk is faulty and the spare disk syncs in?

Thanks

---

