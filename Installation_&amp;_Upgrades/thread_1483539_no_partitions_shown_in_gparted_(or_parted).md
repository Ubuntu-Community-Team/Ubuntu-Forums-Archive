---
title: "no partitions shown in gparted (or parted)"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by kswenson on 2010-05-14
Hello...
  i'm trying to install 10.4 but i'm stuck at the partitioning step.
none of my partitions are detected!

using 9.10 on the same machine i'm not able to run gparted:
"
======================
libparted : 1.8.8.1.159-1e0e
======================
Unable to satisfy all constraints on the partition.
"

i'm also not able to run cfdisk:
"
FATAL ERROR: Bad primary partition 3: Partition ends in the final partial cylinder
"

palimpsest and and fdisk run fine however:
"
=> sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      224909      112423+  de  Dell Utility
/dev/sda2   *      225280    21196799    10485760    7  HPFS/NTFS
/dev/sda3        21196800   214677503    96740352    7  HPFS/NTFS
/dev/sda4       214692721   390719487    88013383+   f  W95 Ext'd (LBA)
/dev/sda5   *   214692723   228347909     6827593+  83  Linux
/dev/sda6       228347973   383696459    77674243+  83  Linux
/dev/sda7       383696460   390716864     3510202+  82  Linux swap / Solaris

=> sudo sfdisk -d
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=   224847, Id=de
/dev/sda2 : start=   225280, size= 20971520, Id= 7, bootable
/dev/sda3 : start= 21196800, size=193480704, Id= 7
/dev/sda4 : start=214692721, size=176026767, Id= f
/dev/sda5 : start=214692723, size= 13655187, Id=83, bootable
/dev/sda6 : start=228347973, size=155348487, Id=83
/dev/sda7 : start=383696460, size=  7020405, Id=82
"

could anyone help me?
i found the following post but it doesn't appear that i have the same problem:
[http://ubuntuforums.org/showthread.php?t=1054064&page=2](http://ubuntuforums.org/showthread.php?t=1054064&page=2)

caljohnsmith...
  you out there?

---

### Post by srs5694 on 2010-05-14
I think I found the problem: There's no space between partitions 6 (ending on sector   383,696,459) and 7 (starting on sector       383,696,460). These are both logical partitions, and logical partitions require at least one empty sector between them. Fortunately, /dev/sda7 is a swap partition, so you should be able to delete it (and re-create a new swap partition, if you like) using fdisk and you should be set. Before you do this, though, disable your swap space ("sudo swapoff -a"). If you create a new swap partition in its place, you should create swap space on it ("sudo mkswap /dev/sda7", assuming the new one is /dev/sda7, which it should be) and check that there's at least one unallocated sector between it and the preceding sector.

---

### Post by kswenson on 2010-05-15
appreciate the help...
  had to play with the uuid a bit but everything is good now.

---

