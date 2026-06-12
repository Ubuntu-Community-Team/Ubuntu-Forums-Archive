---
title: "Is there a patch for Error: diskfilter writes are not supported ?"
date: 2014-09-01
forum: Installation &amp; Upgrades
---

### Post by agarrett5 on 2014-09-01
I have just tried upgrading to Ubuntu Server 14.04.  After grub I get 'Error: diskfilter writes are not supported press any key to continue.'  

I tried back in April time had the same error and it wouldn't boot.  This time round it does boot after the error.  I have looked around the for answers and it seems to be a bug in Ubuntu server with RAIDs.  I am running a RAID.  Raid info is below:

```
 Version : 1.2
  Creation Time : Fri Apr 25 11:36:29 2014
     Raid Level : raid1
     Array Size : 118936448 (113.43 GiB 121.79 GB)
  Used Dev Size : 118936448 (113.43 GiB 121.79 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Sep  1 09:58:57 2014
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : eserver:0  (local to host eserver)
           UUID : 22d694ff:6007e51d:8074bbbb:4ecfc83b
         Events : 245

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1

```

Is there a patch for the bug?  or do I need to do a manual work around?

---

