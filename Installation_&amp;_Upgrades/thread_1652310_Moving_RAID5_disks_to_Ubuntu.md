---
title: "Moving RAID5 disks to Ubuntu"
date: 2010-12-24
forum: Installation &amp; Upgrades
---

### Post by gregmcc on 2010-12-24
I've got 3 x 1TB drives in a software  raid5 array on OpenSuse 11.3  I have to move this to Ubuntu. 

I've have to following: 

> /dev/md0:
        Version : 1.00
  Creation Time : Sun Jun 27 12:28:59 2010
     Raid Level : raid5
     Array Size : 1953519616 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 2
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Fri Dec 24 22:32:31 2010
          State : active, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-asymmetric
     Chunk Size : 128K

           Name : movies:0  (local to host movies)
           UUID : 31a67eaa:b95858db:6f2a292d:391f9829
         Events : 68642

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1


I've now moved the disks to Ubuntu and added them to the raid5 array - all seems to go well and the mdadm shows:

> /dev/md0:
        Version : 00.90
  Creation Time : Sat Jun 26 12:38:59 2010
     Raid Level : raid5
     Array Size : 1953524992 (1863.03 GiB 2000.41 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Dec 24 17:17:04 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 7026f4df:68c7d696:a74c32ba:c27fc7b1
         Events : 0.47

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd
       2       8       16        2      active sync   /dev/sdb


If however I try to mount the raid5 volume I get:

sudo mount /dev/md0 /raid5/
mount: unknown filesystem type 'crypto_LUKS'

The volume is not encrypted? What am I missing?

---

### Post by gregmcc on 2010-12-25
No one with any ideas?

---

