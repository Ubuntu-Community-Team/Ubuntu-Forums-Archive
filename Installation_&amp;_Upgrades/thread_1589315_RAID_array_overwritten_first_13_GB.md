---
title: "RAID array overwritten first 13 GB"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by CrimsonRider on 2010-10-06
Hi guys,

I've got a doozy, and can't figure it out how to fix it.

I've got a failed RAID5 array. To be more presice, I've got 3 disks of which 2 had their first 13 GB overwritten. Is it possible to save those?

The situation is this;

Disk A [ 13 GB Destroyed ] [ RAID 5 Proper data ]
Disk B [         RAID 5 Proper data             ]
Disk C [ 13 GB Destroyed ] [ RAID 5 Proper data ]

The examine of the middle disk is this;

```

root@ruby:/etc# mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : fd5f0b43:9ba326f8:140ee418:7ef6ee01 (local to host ruby)
  Creation Time : Mon Apr 19 15:44:39 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 3

    Update Time : Wed Oct  6 14:27:19 2010
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a7f92348 - correct
         Events : 650369

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8        1        2      active sync   /dev/sda1
root@ruby:/etc#

```

---

