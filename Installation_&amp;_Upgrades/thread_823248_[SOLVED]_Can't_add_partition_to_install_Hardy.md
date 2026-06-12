---
title: "[SOLVED] Can't add partition to install Hardy"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by dapps2k on 2008-06-09
I'm trying to create a new partition to install Hardy to test it out before I make the full transition, but the Guided Partition and Manual Partition both fail at resizing and creating a new partition.  GParted won't even give me the option to add a new partition, though that may be because I've never used it before.

I'm trying to partition my 7.10 Gutsy partition into two 50GB partitions.  What can I do to fix this?  Here is my fdisk -l output if it helps:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x68a7e822

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15487   124399296    7  HPFS/NTFS
/dev/sda2           15488       15609      979965   82  Linux swap / Solaris
/dev/sda3           15610       30401   118816740   83  Linux

```

---

### Post by Partyboi2 on 2008-06-09
use the gparted live cd or ubuntu live cd to shrink down your current gusty install and use the free space from that to install hardy.
So if you are using the ubuntu live cd open up gparted (System>Admin>Partition Editor) and highlight your sda3  partiton and choose the resize option shrink it down and then with the new unllocated space create a new ext3 partition. Then install hardy and choose to use that newly created partition. So take note
 if it is sda4 or sda....

---

### Post by dapps2k on 2008-06-10
Shrinking the partition failed too with GParted, so I just went ahead and used the entire Ubuntu 7.10 partition.

Thanks for the help though.

---

