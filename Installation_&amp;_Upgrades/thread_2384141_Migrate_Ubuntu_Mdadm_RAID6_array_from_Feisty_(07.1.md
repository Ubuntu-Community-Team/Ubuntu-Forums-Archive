---
title: "Migrate Ubuntu Mdadm RAID6 array from Feisty (07.10) to latest.  Possible?"
date: 2018-02-02
forum: Installation &amp; Upgrades
---

### Post by rbm0307 on 2018-02-02
My ancient Ubuntu installation has been out of service for several years now.  I was running a RAID 6 array on it using the built-in mdadm up until the boot drive died.  The individual RAID disks are still intact as is the RAID blocks that can re-create the array. I have backups of the configs somewhere so that will help also if I can rebuild.  Below is the Linux kernel and mdadm I was using:

```
 Linux version 2.6.35-25-server (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #44-Ubuntu SMP Fri Jan 21 19:09:14 UTC 2011 (Ubuntu 2.6.35-25.44-server 2.6.35.10)

root@mythbe:/var/log# mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Mon Sep 15 23:51:21 2008
     Raid Level : raid6
     Array Size : 1953535744 (1863.04 GiB 2000.42 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 6
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Nov 26 13:49:22 2010
          State : clean, degraded
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 614a41ae:61369299:f04c99b8:3fd94616 (local to host mythbe)
         Events : 0.178464

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       0        0        3      removed
       4       8       97        4      active sync   /dev/sdg1
       5       8       81        5      active sync   /dev/sdf1

```

I am in the process of upgrading the computer with newer hardware and installing the latest Ubuntu.  I'm wondering if I can recover the array on the new installation if I import the disks to the machine after the OS install?  Or has the Ubuntu distribution and mdadm moved on so far that this would be an impossible task?

(p.s. I have backups)

---

### Post by Tadaen_Sylvermane on 2018-02-02
If you've got backups it wouldn't hurt to try. Be prepared for it not to work though. I'm curious if something that old can work with the latest and greatest.

---

### Post by rbm0307 on 2018-02-04
UPDATE: Bottom-line is that mdadm works on an array built using a very old Ubuntu. 

I upgraded the hardware in the computer and then installed Ubuntu Server 16.04 LTS on a USB disk.  Booted the new OS and all the RAID elements were visible.  I updated the /etc/mdadm/mdadm.conf manually from the information I saved and (after some head scratching) issued the command mdadm --assemble --scan --force -v.  The array was detected by mdmadm as being dirty and so the system started to rebuild it.  When finished, the volume wouldn't mount until I did a fsck.

---

