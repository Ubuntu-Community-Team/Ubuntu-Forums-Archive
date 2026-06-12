---
title: "Upgraded and now LVM on RAID is gone"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by atxdavid on 2011-12-13
A few weeks ago, I set up an old Pentium IV system with two 2TB SATA drives (/dev/sdb and /dev/sdc), configured in a RAID-1 array, with an LVM filesystem on top of it.  The system boots off of a non-RAID, non-LVM /dev/sda.  Then, over the weekend, I did the usual “sudo apt-get update” followed by “sudo apt-get dist-upgrade” to update my system (Ubuntu 10.04 LTS Desktop).  Following a reboot, my LVM was no longer available, and my RAID showed “degraded.”
   
  The Disk Utility in Ubuntu showed the following message:
  

Error assembling array: mdadm exited with exit code 1: mdadm: WARNING /dev/sdb1 and /dev/sdb appear to have very similar superblocks.
        If they are really different, please --zero the superblock on one
        If they are the same or overlap, please remove one from the list.
   
  I never actually zeroed the superblock, but noticed that the RAID system was attempting to repair itself (via looking at /proc/mdstat).
   
  I now find myself in the situation where the RAID array appears to be intact.  Below is the output of “cat /proc/mdstat”:
  

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
  md_d0 : active raid1 sdb[0] sdc[1]
        1953513472 blocks [2/2] [UU]
   
  unused devices: <none>
   
  So the RAID array looks fine.  The LVM partitions appear to still be there too.  Below is the output of sfdisk –l:


  Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
  Warning: extended partition does not start at a cylinder boundary.
  DOS and Linux will interpret the contents differently.
  Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0
   
     Device Boot Start     End   #cyls    #blocks   Id  System
  /dev/sda1   *      0+  29650-  29651- 238164992   83  Linux
  /dev/sda2      29650+  30401-    751-   6031361    5  Extended
  /dev/sda3          0       -       0          0    0  Empty
  /dev/sda4          0       -       0          0    0  Empty
  /dev/sda5      29650+  30401-    751-   6031360   82  Linux swap / Solaris
   
  WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util sfdisk doesn't support GPT. Use GNU Parted.
   
  Disk /dev/sdb: 243201 cylinders, 255 heads, 63 sectors/track
  Warning: The partition table looks like it was made
    for C/H/S=*/81/63 (instead of 243201/255/63).
  For this listing I'll assume that geometry.
  Units = cylinders of 2612736 bytes, blocks of 1024 bytes, counting from 0
   
     Device Boot Start     End   #cyls    #blocks   Id  System
  /dev/sdb1          0+ 765633- 765634- 1953513560   8e  Linux LVM
                  end: (c,h,s) expected (1023,80,63) found (513,80,63)
  /dev/sdb2          0       -       0          0    0  Empty
  /dev/sdb3          0       -       0          0    0  Empty
  /dev/sdb4          0       -       0          0    0  Empty
   
  WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util sfdisk doesn't support GPT. Use GNU Parted.
   
   
  Disk /dev/sdc: 243201 cylinders, 255 heads, 63 sectors/track
  Warning: The partition table looks like it was made
    for C/H/S=*/81/63 (instead of 243201/255/63).
  For this listing I'll assume that geometry.
  Units = cylinders of 2612736 bytes, blocks of 1024 bytes, counting from 0
   
     Device Boot Start     End   #cyls    #blocks   Id  System
  /dev/sdc1          0+ 765633- 765634- 1953513560   8e  Linux LVM
                  end: (c,h,s) expected (1023,80,63) found (513,80,63)
  /dev/sdc2          0       -       0          0    0  Empty
  /dev/sdc3          0       -       0          0    0  Empty
  /dev/sdc4          0       -       0          0    0  Empty
   
  WARNING: GPT (GUID Partition Table) detected on '/dev/md_d0'! The util sfdisk doesn't support GPT. Use GNU Parted.
   
  

However, the actual LVM information is nowhere to be found.  Pvscan simply outputs “No matching physical volumes found.”
   
  Is there a way to recover the data I had on these drives, or am I toast?
   
  Thanks in advance.

---

### Post by bjrnfrdnnd on 2013-03-23
Hi, 

I have a similar problem:

[http://ubuntuforums.org/showthread.php?t=2128504](http://ubuntuforums.org/showthread.php?t=2128504)

Did you ever find a solution?

---

