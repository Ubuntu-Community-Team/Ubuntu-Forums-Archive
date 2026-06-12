---
title: "Disk partitions / MDADM"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by delpi767 on 2011-09-05
Would someone be so kind as to recap the proper way of partitioning and formatting disk drives and creating a disk array?

Specifically, when I create a mirror, I create two partitions using CFDisk.  they are of type FD (Linux RAID autodetect)

Now, do I format the partitions before I use MDADM to create the array?

Once the array is created do I need to partition it?
Once the array is created to I need to format it?
It seems redundant to have to partition and format the array and the individual disks.

And finally, what is the brute force way of dealing with "device is apparently busy, will not make file system here"?

Thqanks,

-dmd-

---

### Post by opodaniel on 2012-01-06
I got myself a raid 0 using mdadm on 3 ssd drives. All was nice and dandy until i decided to resize one of the partition and make another one. I've been trying this stunt using gparted. The result was - I almost lose the 2 partition but I manage to realign them using testdisk. Now I have 2 partition and one empty space. I have try using Gparted to make a new partition but got myself the error ( see attached picture). 

If anyone have any idea on what should I use to make use of 18Gb empty space :d.

---

