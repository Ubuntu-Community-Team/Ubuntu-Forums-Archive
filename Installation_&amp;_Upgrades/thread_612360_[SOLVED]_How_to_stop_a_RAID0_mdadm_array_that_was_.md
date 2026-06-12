---
title: "[SOLVED] How to stop a RAID0 mdadm array that was the swap device?"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by davidkahn on 2007-11-13
/dev/md1 was a RAID0 array (stripping) Linux software RAID that was being used as the sole swap device.[INDENT]swapoff -a
[/INDENT]seems to correctly unmount the  swap file, as "umount /dev/md1" indicates that it is no longer mounted and the system monitor says that there's no swap space.  I have even removed the swap device from /etc/fstab and rebooted.

Nevertheless,[INDENT] sudo mdadm --query --detail /dev/md1
[/INDENT]says that the  RAID array's status is "active" and[INDENT] sudo mdadm --manage --stop  /dev/md1
[/INDENT]fails, returning:[INDENT]mdadm: fail to stop array /dev/md1: Device or resource busy
[/INDENT]Another thread indicated that the way to stop the array was to first fail each disk, then remove them.  While[INDENT]sudo mdadm --manage /dev/md1 --fail /dev/sda5
(Note: /dev/sda5 and /dev/sdb5 are the two partions constituting the RAID array.)
[/INDENT]seemed to work[INDENT]sudo mdadm --manage /dev/md1 --remove /dev/sda5
[/INDENT]fails with the message:[INDENT]mdadm: hot remove failed for /dev/sda5: Device or resource busy
[/INDENT]I even tried:[INDENT]sudo mdadm --misc --zero-superblock  /dev/sda5
[/INDENT]But that failed because the partition is part of the RAID array and cannot be written to directly.
 
What are the commands that will let me stop this unused, and unmounted former swap RAID0?


Thanks,

David

---

### Post by davidkahn on 2007-11-13
I tried editing  /etc/mdadm/mdadm.conf to attempt to stop the RAID0 array from being created:

1. Commented the RAID array:[INDENT]# ARRAY /dev/md1 level=raid0 num-devices=2 UUID=fc42d7a5:a9e23546:edb292e5:3a280337
[/INDENT]2. Made mdadm not search for super blocks in  /dev/sda5 and /dev/sdb5[INDENT]# DEVICE partitions (stop default to search all partitions) 
DEVICE /dev/sd[ab]1
[/INDENT]Nevertheless, the RAID array is still there after a reboot.

sudo mdadm --query --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Fri Jul  6 10:49:23 2007
     Raid Level : raid0
     Array Size : 19486592 (18.58 GiB 19.95 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Tue Nov 13 18:12:52 2007
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : fc42d7a5:a9e23546:edb292e5:3a280337
         Events : 0.21

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5

---

### Post by davidkahn on 2007-11-14
SOLVED!

I just proved that the Heisenberg Uncertainty Principal -- that the act of observing changes the object observed -- applies to Ubuntu as well as to subatomic particles.

It turns out that editing /etc/mdadm/mdadm.conf and replacing[INDENT]DEVICE partitions
[/INDENT]with[INDENT]DEVICE /dev/sda1 /dev/sdb1
[/INDENT]which allowed the primary RAID1 on /dev/md0, consisting of /dev/sda1 and /dev/sdb1 to keep working while turning off the RAID1 swap partition /dev/md1, which consisted of /dev/sda5 and /dev/sdb5.

The problem was that I repeatedly, except one fortuitous time, always ran :[INDENT]sudo mdadm --query --detail /dev/md1
[/INDENT]after each reboot before trying to --stop the RAID array, _and inspecting the RAID turn the darn thing on_! The state on the first --query is "clean", and it quickly goes to "active" upon inspection. It make some sense too that the RAID has to be running to respond to the query.

It turned out to be quite easy to turn /dev/sda5 and /dev/sdb5 into simple swap partitions using the Gnome Partition Editor.

---

