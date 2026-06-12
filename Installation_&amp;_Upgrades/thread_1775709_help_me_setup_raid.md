---
title: "help me setup raid"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by gpost3 on 2011-06-05
hi folks.

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x674f31a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13053   104845534+   7  HPFS/NTFS
/dev/sda2           13054       55262   339043792+   f  W95 Ext'd (LBA)
/dev/sda3           55263       60802    44489728   83  Linux
/dev/sda5           13054       47520   276856146    7  HPFS/NTFS
/dev/sda6           47521       55262    62187583+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe515cf51

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488383024+   f  W95 Ext'd (LBA)
/dev/sdb5               1       60801   488383008+   7  HPFS/NTFS

```sda6 is Ubuntu partition
sda5 is my data partition
and finally...
sdb5 is my backup partition

I don't have hardware raid controller. I have two hard drives, both are 500 gb. I want sda5 and sdb5 to run on raid 1 for data mirroring. I want to split sda6 and run it on raid 0 with another equal sized partition on sdb. Is this possible? what software will I need to do this? is this raid1+0 configuration or is it raid0+1 configuration?

---

### Post by gpost3 on 2011-06-05
bump

---

