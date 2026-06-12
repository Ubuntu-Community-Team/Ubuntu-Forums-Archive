---
title: "Partition 1 does not end on cylinder boundary."
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by Plakband on 2008-03-17
Hi after installing Ubuntu 7.10 (with resize the NTFS partition) i now have the following partition error:

fdisk -l :

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64656469

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6893    55361848+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            6894        9606    21792172+  83  Linux
/dev/sda3            9607        9729      987997+   5  Extended
/dev/sda5            9607        9729      987966   82  Linux swap / Solaris

How can i fix this partition error ?
I have a mbr backup, from before the resize action by the installer, that will proberly won't do me any good since it's resized right ?

Any help is very appreciated.

---

### Post by Plakband on 2008-03-17
also i found that the head-count isn't correct right ? the output of fdisk:

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 80   1   1    0 239  63 1023         63  110723697 07
Partition 1 does not end on cylinder boundary.
 2 00 254  63 1023 254  63 1023  110736045   43584345 83
 3 00 254  63 1023 254  63 1023  154320390    1975995 05
 4 00   0   0    0   0   0    0          0          0 00
 5 00 254  63 1023 254  63 1023         63    1975932 82

---

