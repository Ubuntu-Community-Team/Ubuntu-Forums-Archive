---
title: "Mounting NTFS hard Drives"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by Terdog on 2006-12-09
OK, here my problem, got ubuntu up and running, but I have 2 hard drives I keep data on for safe keeping. Both are NTFS partitions, and I would like to be able to read/write data from them. Note: These are all seperate drive. NO partitions.


Here is my sudo fdisk-l listing
Disk /dev/sda: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      484521   244198552+  42  SFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        6950    55825843+   7  HPFS/NTFS
/dev/sdb2            6951        9729    22322317+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      310097   156288856+   7  HPFS/NTFS

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2330    18715693+  83  Linux
/dev/hda2            2331        2434      835380    5  Extended
/dev/hda5   *        2331        2434      835348+  82  Linux swap / Solaris

---

### Post by taurus on 2006-12-09
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

