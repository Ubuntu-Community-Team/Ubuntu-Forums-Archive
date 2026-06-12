---
title: "Using partimage restore ubuntu - result , Error loading operating System"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by moonhk on 2007-01-13
I am using SystemRescueCd create image, then load other hard disk below error prompted duing booting. How to fix it ? 


Error loading operating System

---

### Post by MyTer on 2008-01-13
Check to see if it is flagged "bootable"
One way to do it is
fdisk -l
Which prints out the disk  partitions You have

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241    7  HPFS/NTFS

The first column is the device, in my case /dev/sda1 (first disk, first partition)
The second column tells you if it is bootable, in my case it is (contains a * )

Otherwise You could use the more helpful cfdisk.

cfdisk
or if it is not the /dev/sda disk, but another one, then You have to say wich one.
cfdisk /dev/sdb

Good Luck! :idea:

---

