---
title: "LVM not seeing mdadm array after reinstall"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by Onthax on 2011-11-16
So i was previously on mythbuntu 10.04 and setting a 6 disk raid 6 array. All was working fine, a year later i decided to upgrade to the latest version of mythbuntu, 11.10 but unfortunately 11.10 isnt supported by a script i use to get TV guide data.

So i've dropped back to the latest version that did, 11.04.

Flash forward, i've installed mythbuntu 11.04 and installed mdadm and lvm2

mdadm sees the raid array fine, i get a /dev/md0 and for some reason a /dev/md0p1

a 'sudo mdadm --detail /dev/md0' reveals
```



sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Fri Sep 10 22:35:28 2010
     Raid Level : raid6
     Array Size : 7814049792 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 1953512448 (1863.01 GiB 2000.40 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Nov 17 09:05:11 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 128K

           UUID : e60b2d7e:a5b6dc0e:462a36bb:f8f383a4 (local to host media)
         Events : 0.8641516

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd
       4       8       64        4      active sync   /dev/sde
       5       8       80        5      active sync   /dev/sdf
media@media:/dev$ vgscan
  WARNING: Running as a non-root user. Functionality may be unavailable.
  Reading all physical volumes.  This may take a while...
  No volume groups found

```

but as you can see vgscan within LVM doesnt find anything

the previous setup was /dev/md0 had a vg and lv on top of it but lvm2 doesnt seem to be able to find these, however it all worked fine under 11.10 yesterday, any ideas?

---

### Post by Onthax on 2011-11-16
Nevermind, MDADM was mounting the array badly, it was finding the superblocks on /dev/sda instead of on the partitions /dev/sda1

this was due to the fact of mounting mdadm on the partitions to allow for partition alignment of 4k for WD Green drives :^)

---

