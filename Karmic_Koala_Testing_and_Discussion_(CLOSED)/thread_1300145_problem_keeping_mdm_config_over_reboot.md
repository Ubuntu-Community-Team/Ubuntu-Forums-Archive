---
title: "problem keeping mdm config over reboot"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pootle1 on 2009-10-24
I'm building a recycled machine (was previously running windoze) as a vm host machine (QEMU).  After the system disc I have 4 discs to set up in a raid 10 array.  I've done this before with Jaunty and it has been running for a few months with no problems.

I wanted to try softraid on the new machine. At first I had problems with dmraid picking up the discs  - they had previously been on a raid array with a 3ware 3650 card (under windoze), so I removed dmraid and did a clean array build (under karmic beta AMD 64).  raid array built OK, but when I reboot the md device never comes up by itself.  If I use --assemble --scan, it finds the array, but always 1 disc (the particular one varies) is missing and I can't add it back in as it is 'busy'.  when I look in syslog, mdadm grabbed it earlier, and won't let go.

NE1 got any idea what is going on here :confused:

After building the 4 disc set and letting it fully sync I rebooted - here are obvious bits of syslog
```
Oct 24 22:26:16 alfredii kernel: [    8.684569] md: bind<sda>
```and a little later when I issued --assemble --scan

```
Oct 24 22:43:03 alfredii kernel: [ 1015.249129] md: bind<sdc>
Oct 24 22:43:03 alfredii kernel: [ 1015.256954] md: bind<sdd>
Oct 24 22:43:03 alfredii kernel: [ 1015.257473] md: bind<sdb>
Oct 24 22:43:03 alfredii kernel: [ 1015.270874] raid10: raid set md0 active with 3 out of 4 devices
Oct 24 22:43:03 alfredii kernel: [ 1015.270952] md0: detected capacity change from 0 to 1000215543808
Oct 24 22:43:03 alfredii mdadm[1146]: NewArray event detected on md device /dev/md0
Oct 24 22:43:03 alfredii kernel: [ 1015.271123]  md0:
```
here's the output from --detail:

```
/dev/md0:
        Version : 00.90
  Creation Time : Sat Oct 24 18:27:49 2009
     Raid Level : raid10
     Array Size : 976772992 (931.52 GiB 1000.22 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Oct 24 23:27:16 2009
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2, far=1
     Chunk Size : 64K

           UUID : ef56635a:22c54d13:99822e4d:a676832e (local to host alfredii)
         Events : 0.24

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
       3       8       48        3      active sync   /dev/sdd

```

---

