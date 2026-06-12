---
title: "mdadm - Using whole disk rather than &quot;Linux raid auto&quot;"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by Rob_Quads on 2007-04-17
I have created a RAID5 array on my Ubuntu machine. Unfortunatly I forgot to create a single partition on each disk of type "Linux raid auto" instead I built the array just using the whole disks i.e. /dev/hde. 

Will this cause a problem if I need to move the array to another machine?

I tried removing a drive and then formatting a partition but I was unable to add it back into the array. I was only able to add back in a full drive without any partitions

Below is the output of mdadm --detail /dev/md0 (after adding back in a drive)

```

/dev/md0:
        Version : 00.90.03
  Creation Time : Sat Mar 24 00:00:31 2007
     Raid Level : raid5
     Array Size : 879108288 (838.38 GiB 900.21 GB)
  Used Dev Size : 293036096 (279.46 GiB 300.07 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Apr 17 16:08:09 2007
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 2% complete

           UUID : d41d20ba:89f42c99:1f9c2965:759ec036
         Events : 0.195010

    Number   Major   Minor   RaidDevice State
       4      33        0        0      spare rebuilding   /dev/hde
       1      33       64        1      active sync   /dev/hdf
       2      34       64        2      active sync   /dev/hdh
       3      34        0        3      active sync   /dev/hdg

```

---

