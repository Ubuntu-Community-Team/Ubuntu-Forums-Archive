---
title: "Software RAID not working after upgrade to 11.04"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by vitke on 2011-05-06
Hi all

I upgraded from 10.10 to 11.04, and now I cannot mount my raid drive. At the boot time I'm getting the message that the drive cannot be mounted, and I choose to skip it. Then I try to mount it from the command line, but I'm getting

```
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
cat /proc/mdstat gives
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb[1](S)
      1465138496 blocks

```
mdadm --examine /dev/sda gives
```
mdadm: No md superblock detected on /dev/sda.

```
and /dev/sdb seems to be fine because mdadm --examine /dev/sdb gives
```
/dev/sdb:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : 93d55dae:ba268f09:9c0f36fb:5e8cac09 (local to host yes)
  Creation Time : Fri Jan 22 20:48:02 2010
     Raid Level : raid1
  Used Dev Size : 1465138496 (1397.26 GiB 1500.30 GB)
     Array Size : 1465138496 (1397.26 GiB 1500.30 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Thu May  5 22:00:34 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : e27b25f8 - correct
         Events : 2319164


      Number   Major   Minor   RaidDevice State
this     1       8       16        1      active sync   /dev/sdb

   0     0       8        0        0      active sync   /dev/sda
   1     1       8       16        1      active sync   /dev/sdb

```
/etc/mdadm/mdadm.conf contains
```
DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=93d55dae:ba268f09:9c0f36fb:       5e8cac09
   devices=/dev/sda,/dev/sdb

```
So what could be wrong?

---

### Post by vitke on 2011-05-07
To answer my own question, the problem was that on each disk the file systems were larger than devices, and this was the case because something (me?) has created the file systems before adding superblocks at the end of the disks, if I understood correctly some link that I can't find now. So the file systems were supposed to be resized at the end (by something - me?), but they were not resized. It is an enigma how it worked so far, but after the upgrade it didn't work any more. So all I had to do was to run
```
sudo e2fsck -f /dev/sda
```
and answer 'n' when asked to quit, then
```
sudo resize2fs /dev/sda
```
and then all the same for /dev/sdb.

---

### Post by vitke on 2011-05-08
Well, not really... As a result, I can now mount both disks separately, but I cannot assemble /dev/md0. It says
```
mdadm: /dev/sda has no superblock - assembly aborted
```
So it seems that my resize command deleted the superblocks. How can I create them?

---

