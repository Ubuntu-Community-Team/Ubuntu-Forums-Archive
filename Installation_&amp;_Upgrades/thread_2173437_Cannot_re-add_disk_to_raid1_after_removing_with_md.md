---
title: "Cannot re-add disk to raid1 after removing with mdadm"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by klausmedk on 2013-09-09
Hello 
I wanted to test drive failure on my raid1 array.

My array initially looked like this:

> /dev/md1p1:
        Version : 1.0
  Creation Time : Thu Mar 22 15:55:42 2012
     Raid Level : raid1
     Array Size : 2930265407 (2794.52 GiB 3000.59 GB)
  Used Dev Size : unknown
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Sep  9 21:17:32 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : HEV271-NAS:1
           UUID : 24f6612a:f9045c3c:a09823be:0a00399b
         Events : 18353

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       48        1      active sync   /dev/sdd


I then set /dev/sdd faulty and removed it with:

> 
mdadm --manage --set-faulty /dev/md1p1 /dev/sdd
mdadm /dev/md1p1 -r /dev/sdd


Then I wanted to re-add the device with:

> mdadm /dev/md1p1 -a /dev/sdd

But got the response: mdadm: /dev/sdd not large enough to join array

Why is that? It's the same disk that was in the array just a second ago?

The detailts for the disks are:

> sudo fdisk -l /dev/sdc

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


sudo fdisk -l /dev/sdd

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.


What have I done wrong?
What can I do to correct my mistake without losing data?

Regards
Klaus

---

### Post by SaturnusDJ on 2013-09-10
> 
 Used Dev Size : unknown

That's a bit strange.

Can you post the examine's?

---

### Post by klausmedk on 2013-09-10
Thank you for the response.

mdadm examines are:

> sudo mdadm --examine /dev/sdc
/dev/sdc:
          Magic : a92b4efc
        Version : 1.0
    Feature Map : 0x0
     Array UUID : 24f6612a:f9045c3c:a09823be:0a00399b
           Name : HEV271-NAS:1
  Creation Time : Thu Mar 22 15:55:42 2012
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 5860532896 (2794.52 GiB 3000.59 GB)
     Array Size : 2930266448 (2794.52 GiB 3000.59 GB)
   Super Offset : 5860533152 sectors
          State : clean
    Device UUID : 1f43ca76:1efe8a74:a9a477d1:0064dbe4

    Update Time : Tue Sep 10 15:43:28 2013
       Checksum : 75778816 - correct
         Events : 18575


   Device Role : Active device 0
   Array State : A. ('A' == active, '.' == missing)


and 

> sudo mdadm --examine /dev/sdd
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)


I wiped the partition table on sdd before trying to add to the array again in order to make the system belæeive it was a completely fresh disk. 
I guess that's why you see nothing for that disk.

Regards
Klaus

---

### Post by klausmedk on 2013-09-12
I moved on and created a new array from scratch.
Now I use partitions instead of raw devices, and made the partitions a little smaller than the entire disk to avoid that something similar will happen again. This also mean that if I ever have to replace a disk with another one of not quite the same size it will probably fit anyway.

I used:

create partition sdd1 on orphan disk with 100 MB free space both before AND after the partition
create new array with:
> sudo mdadm --create /dev/md0 --level=2 --raid-devices=2 /dev/sdd1 missing
rsync all files from old array (/dev/md1) to new array (/dev/md0)
stopped old array
created a partition sdc of similar size as sdd1
added the last disk from the old array to the new array with :
> sudo mdadm --manage /dev/md0 -add /dev/sdc1

---

