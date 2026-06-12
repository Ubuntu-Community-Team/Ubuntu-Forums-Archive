---
title: "Partition not recognized by PartMan"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by gasparov on 2005-10-14
Hi, 
  this problem came out after installing windows,after that gparted was unable to recognize partitions on /dev/sda,it sees them as unallocated space.Partitions are there cause get mounted and actually the linux box I'm writing from is in one of those partitions and everything works fine...

```

gas@ubuntu:~ $ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            5101       19227   113475127+   f  W95 Ext'd (LBA)
/dev/sda3           17338       17421      674698+  82  Linux swap / Solaris
/dev/sda4           19228       19929     5638815   83  Linux
/dev/sda5            5101       17337    98293639+  83  Linux
/dev/sda6           17422       19227    14506663+  83  Linux

Disk /dev/sdb: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1275    10241406   83  Linux
/dev/sdb2            1276        2550    10241437+  83  Linux
/dev/sdb3            2551       19929   139596817+   5  Extended
/dev/sdb5            2551        2932     3068383+  83  Linux
/dev/sdb6            2933       19929   136528371   83  Linux



```

Now the problem is coming also with partiotioning utility on Breezy install CD and I can't find any swap space...I suppose I could use empty sdb5 for that...

---

