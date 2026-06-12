---
title: "mdadm RAID 5 - is there something wrong here?"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by zac_haryy on 2008-07-14
So I have a server with 5 1tb hard drives that have been working in a RAID 5 configuration for about 8 months now. Everything is working fine, I am just wanting to add three more hard drives to the array (grow it). Well I went to check the status on the current RAID 5 before I get ready to add the other three hard drives to it and it looks like there are only 4 hard drives working for some reason. Here is details from mdadm:
```
harold@server:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Feb 11 16:48:31 2008
     Raid Level : raid5
     Array Size : 3907039744 (3726.04 GiB 4000.81 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 5
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 13 23:12:12 2008
          State : clean, degraded
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 72fa18f5:bf5d1a62:31a05266:02bffc2c
         Events : 0.54

    Number   Major   Minor   RaidDevice State
       0       8      113        0      active sync   /dev/sdh1
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1

```

I dont know why I am getting this error:

```
       1       0        0        1      removed
```

If I go into the partition editor I can see that I have all eight hard drives hooked up to the computer and running, but I just don't understand this. I am not the greatest with linux but am getting be decent, so take it easy on me! Thanks!

-haryy

---

### Post by zac_haryy on 2008-07-14
Anybody have any ideas? I really am not the greatest with linux but would like to make sure that it is working correctly.

---

### Post by CooLGeeK on 2008-07-19
Looking at the output of: sudo mdadm --detail /dev/md0 you will see the lines:

   Raid Devices : 5
  Total Devices : 4

This means that your RAID device is a RAID 5 type.
Unfortunately one of your device seems to be missing OR has failed.

Since your RAID 5 device is missing one (1) component,
your data is still intact but the RAID device cannot afford another
failing component.

You must add another/separate Linux RAID partition immediately...
by using the --manage /dev/md0 --add /dev/???

Don't forget to create a disk partition (must be on another disk)
of EXACTLY the same size (use blocks not megabytes/gigabytes) as
that of the other components of your RAID device.

---

