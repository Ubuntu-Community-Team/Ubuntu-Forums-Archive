---
title: "Raid 5 - 2.8tb?"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by orion114 on 2008-04-15
I am trying to setup a disk on Ubuntu that I can then mount as a network drive in windows XP.
I have 4 x 1TB disks in the machine and 1 x 160GB.

I have installed Ubuntu on the 160GB disk and I am having trouble setting up the RAID on the others.
I used mdadm to create the RAID5 array, but when I use gprated I only see a 700GB /dev/md0
qtparted does not even show the /dev/md0 device at all??

Is there a limitation on mdadm? or am I doing something wrong?

Result of sudo mdadm --misc --detail /dev/md0
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Apr 14 11:18:18 2008
     Raid Level : raid5
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 15 11:52:48 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : b43807b8:6112ca56:2f8422f2:c91336a5 (local to host dcmdisk01)
         Events : 0.10

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd

```

---

### Post by dstew on 2008-04-17
I do not think that gparted can partition a software RAID. You might need to use fdisk, or one of the other command-line partitioners. I think partman (on the alternate install disk) can partition a software RAID for you also.

---

### Post by orion114 on 2008-04-18
Thanks dstew,

I found another tool in synaptic that appears to be working now.
I am using parted.
It is currently making a 3000GB partition.
I hope it works. hold thumbs :)

---

