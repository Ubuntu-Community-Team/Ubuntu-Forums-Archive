---
title: "Installing my second HD, brand new to Ubuntu"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by morissette on 2008-09-16
I know there are like 500 tutorials for this but unfortunately i cant find one that helps me lol

So if someone could walk me through step by step id love you
heres my fdisk -l


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d773d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37828   303853378+  83  Linux
/dev/sda2           37829       38913     8715262+   5  Extended
/dev/sda5           37829       38913     8715231   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by badfish69 on 2008-09-16
use the ubuntu installer to partition/format it.

---

### Post by jken146 on 2008-09-16
A nice easy way is to use gparted to format it.  First, install gparted: ```
sudo apt-get install gparted
```
Then find gparted under System -> Administration -> Partition Editor

Partition and format your new drive as you like.  If you're just using it for extra storage then I'd recommend one partition spanning the entire drive, formatted in ext3.

---

