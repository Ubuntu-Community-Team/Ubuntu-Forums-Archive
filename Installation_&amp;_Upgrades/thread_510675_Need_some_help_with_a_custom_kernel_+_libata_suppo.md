---
title: "Need some help with a custom kernel + libata support"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by limaunion on 2007-07-26
Hi all, i'm trying to run a custom vanilla kernel with libata support, I've disabled the old IDE/PATA driver and enabled the new one (CONFIG_PATA_AMD=y that's required for my nforce2 controller).

The problem is that when the system boots I get this error:

VFS: cannot open root device "sda2" or unknow-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS unable to mount root fs on unknown-block(0,0)

I modified my menu.lst file from hda2 to sda2 and also by UUID but neither of these options worked.
Any idea what could be wrong here ? 
Thanks in advance.

---

