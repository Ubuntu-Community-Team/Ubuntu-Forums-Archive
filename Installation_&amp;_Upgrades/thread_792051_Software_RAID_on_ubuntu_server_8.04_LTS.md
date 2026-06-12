---
title: "Software RAID on ubuntu server 8.04 LTS"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by pavlizz on 2008-05-12
I have create a software array and this is my fdisk

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69617220

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  fd  Linux raid autodetect
/dev/sda2             123         256     1076355   fd  Linux raid autodetect
/dev/sda3             257       60801   486327712+  fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0d646961

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      979933+  fd  Linux raid autodetect
/dev/sdb2             123         256     1076355   fd  Linux raid autodetect
/dev/sdb3             257       60801   486327712+  fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00746573

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         122      979933+  fd  Linux raid autodetect
/dev/sdc2             123         256     1076355   fd  Linux raid autodetect
/dev/sdc3             257       60801   486327712+  fd  Linux raid autodetect

Disk /dev/md0: 1003 MB, 1003356160 bytes
2 heads, 4 sectors/track, 244960 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 2204 MB, 2204237824 bytes
2 heads, 4 sectors/track, 538144 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md2: 995.9 GB, 995998957568 bytes
2 heads, 4 sectors/track, 243163808 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md2 doesn't contain a valid partition table


I'm worrying about those errors 

Disk /dev/md0 doesn't contain a valid partition table
Disk /dev/md1 doesn't contain a valid partition table
Disk /dev/md2 doesn't contain a valid partition table

IS that a real problem ?
How can I fix it ?

---

### Post by wumpus on 2008-05-21
If you already have annother disk with your 8.04LTS system running, there shouldn't be a problem.  My blather below assumes you want to install to this system:

I'm not sure if this is a problem.  I am typing this from a new 8.4 desktop using software RAID (just got it working) and I never tried to fdisk any of my /dev/md? drives.  I'd just use the various mkfs commands to build filesystems and run with it.

The bigger problems are getting the thing to boot.  If you don't have an additional drive to use as a boot partition, you will need to re-partition your drives to include one (just on one drive).  You might also want to split swap drives into seperate partitions unless this is a high availability unit, swap drives are said to raid well enough on their own.

Installation follows the "ubuntu fakeraid installation howto" (ubuntu fakeraid should google it), but you will need a few other tricks, possibly compiling your own kernel to get the mdadm module loaded during boot.

---

