---
title: "Error msg after useing pysdm"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by Sovereign Entity on 2010-05-26
Hello it's me again. I have a ubuntu minimal install. 5 hard drives to be used as a server. I installed pysdm to auto mount the drives. All but one worked. And i got this msg. at boot --An error occurred while mounting /media/sdc1-- I uninstalled pysdm and installed NTFS Config tools that works perfect. But i still get the error.I would like to clesr this before I backup the system. Being that it took so long to get it installed. 
 This is my setup:
sidney@Sovereign:~$ sudo fdisk -l
[sudo] password for sidney: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00043fa6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1646963a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007cd0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9356    75143168   83  Linux
/dev/sdc2            9356        9730     3005441    5  Extended
/dev/sdc5            9356        9730     3005440   82  Linux swap / Solaris

Disk /dev/sdd: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x88e9a09f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       24792   199141708+   7  HPFS/NTFS

Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6bd39344

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       14593   117218241    7  HPFS/NTFS

---

