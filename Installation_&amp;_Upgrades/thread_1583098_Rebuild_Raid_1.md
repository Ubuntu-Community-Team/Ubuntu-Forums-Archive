---
title: "Rebuild Raid 1"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by xhotardx on 2010-09-27
Ladies and Gentlemen, 

I am looking for information on how to rebuild a raid 1 array. I have added a new disk and it is still showing as degraded. I attached output from a few mdadm commands. 

Thanks in advance!


> 
  root@SomeComputerName:/#  mdadm -D /dev/md1
/dev/md1:
        Version : 01.00
  Creation Time : Sun Sep 20 17:10:16 2009
     Raid Level : raid1
     Array Size : 974722192 (929.57 GiB 998.12 GB)
  Used Dev Size : 1949444384 (1859.14 GiB 1996.23 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Sep 27 08:30:24 2010
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : storage:1
           UUID : 0b0b3afd:ff17ffe8:ef3722d2:65d5c942
         Events : 153330

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2
root@SomeComputerName:/#


So it appears to me that /dev/sdb1 has been removed. The data currently residing on /dev/sdb2 would need to be copied over to sdb1 to make this work correctly.

>    
root@SomeComputerName:/# fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x26ff1ed0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         254     2040223+  83  Linux
/dev/sda2             255      121602   974722329   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00086a53

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         254     2040254+  83  Linux
/dev/sdb2             255      121602   974722329   83  Linux

Disk /dev/md0: 2089 MB, 2089091072 bytes
2 heads, 4 sectors/track, 510032 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/md1: 998.1 GB, 998115524608 bytes
2 heads, 4 sectors/track, 243680548 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table
root@SomeComputerName:/#


> 

root@SomeComputerName:/# cat /proc/mdstat
Personalities : [linear] [raid0] [raid1] [raid6] [raid5] [raid4]
md1 : active raid1 sdb2[1]
      974722192 blocks super 1.0 [2/1] [_U]

md0 : active raid1 sda1[0] sdb1[1]
      2040128 blocks [2/2] [UU]

unused devices: <none>
root@SomeComputerName:/#

---

