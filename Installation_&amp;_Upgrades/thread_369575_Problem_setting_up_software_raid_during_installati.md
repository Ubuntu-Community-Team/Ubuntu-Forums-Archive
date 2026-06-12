---
title: "Problem setting up software raid during installation"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by SunMar on 2007-02-24
Hello,

Currently I'm running Gentoo with a software raid setup through mdadm however I'd like to install Ubuntu. The problem is that I'd like to preserve some of the logical volume's currently in my setup however I can't get the raid array to be setup.

I have two identical hard drives (/dev/hde and /dev/hdg). I'm using the alternate iso and text mode installation. When I switch to the console view with ALT+F2 and try to setup the array I get this problem:

mknod /dev/md1 b 9 1 (<-- does not report any errors and /dev/md1 is created)

then however I get this:
mdadm --assemble /dev/md1 /dev/hde1 /dev/hdg1 --super-minor=1
mdadm: error opening /dev/md1: No such device or address

Here's my raid setup:
```
/dev/md1:
        Version : 00.90.03
  Creation Time : Tue Oct 17 05:04:15 2006
     Raid Level : raid1
     Array Size : 128384 (125.40 MiB 131.47 MB)
  Used Dev Size : 128384 (125.40 MiB 131.47 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Feb 25 00:40:43 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 031e0ff9:fce816a3:a9838d1c:2efba007
         Events : 0.728

    Number   Major   Minor   RaidDevice State
       0      33        1        0      active sync   /dev/hde1
       1      34        1        1      active sync   /dev/hdg1

/dev/md2:
        Version : 00.90.03
  Creation Time : Tue Oct 17 05:04:30 2006
     Raid Level : raid1
     Array Size : 2000000 (1953.45 MiB 2048.00 MB)
  Used Dev Size : 2000000 (1953.45 MiB 2048.00 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Sat Feb 24 03:14:11 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 3e82b00b:69b929d6:d08db0d5:9d8a43e0
         Events : 0.4430

    Number   Major   Minor   RaidDevice State
       0      33        2        0      active sync   /dev/hde2
       1      34        2        1      active sync   /dev/hdg2

/dev/md3:
        Version : 00.90.03
  Creation Time : Tue Oct 17 05:04:48 2006
     Raid Level : raid1
     Array Size : 10000384 (9.54 GiB 10.24 GB)
  Used Dev Size : 10000384 (9.54 GiB 10.24 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Sun Feb 25 00:53:18 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 9913dcd9:ea23d866:c129e0b3:604e6132
         Events : 0.36580

    Number   Major   Minor   RaidDevice State
       0      33        3        0      active sync   /dev/hde3
       1      34        3        1      active sync   /dev/hdg3

/dev/md4:
        Version : 00.90.03
  Creation Time : Tue Oct 17 05:11:12 2006
     Raid Level : raid1
     Array Size : 232066880 (221.32 GiB 237.64 GB)
  Used Dev Size : 232066880 (221.32 GiB 237.64 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 4
    Persistence : Superblock is persistent

    Update Time : Sun Feb 25 00:53:03 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 52a7cb9b:2ddda653:85c0bb11:e11fc111
         Events : 0.766698

    Number   Major   Minor   RaidDevice State
       0      33        4        0      active sync   /dev/hde4
       1      34        4        1      active sync   /dev/hdg4
```

I can't seem to figure out what I'm doing wrong or if mdadm or the dev system isn't working correctly. Does anybody have a clue ?

Regards.

---

