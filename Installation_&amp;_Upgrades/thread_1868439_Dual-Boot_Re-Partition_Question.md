---
title: "Dual-Boot Re-Partition Question"
date: 2011-10-24
forum: Installation &amp; Upgrades
---

### Post by justjustin on 2011-10-24
Hi, I would like to install windows alongside my ubuntu installation, I have done this before (both ways, linux first, windows first) without any problems.

My problem is that I already have too many Primary Partitions on my drive, and I only have one usable drive on this machine.

My current partitions look like this...

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          67      538146   83  Linux
/dev/sda2              68        3891    30716280   83  Linux
/dev/sda3            3892       96575   744476742+  83  Linux
/dev/sda4          120328      121601    10233405   82  Linux swap / Solaris


```

sda1 is 500MB boot
sda2 is 30GB /
sda3 is 700GB /home (shrunk, followed by 180GB unallocated space intended for windows installation)
sda4 is swap

If I was to remove my Swap and create an Extended Partition, could I then create a Logical Partition and Swap Partition inside it, using the Logical Partition as my Windows System Partition?

---

### Post by Mark Phelps on 2011-10-24
Basically -- NO.  

You will need a Primary partition to install Windows.  

While Win7, I believe, will allow you to run from Logical partition, like XP, it must boot from a Primary partition.  I believe that XP requires a Primary partition as well.

---

### Post by satanselbow on 2011-10-24
Mr Phelps comments above are true and correct.

If your /home partition is not "too full" you could shrink it down and recreate it - as well as you swap (which you might might not need at all?)  - within the extended partition thus freeing up the 2 required primary partitions ;) 1 for windoze, 1 for extended :D

Moving your /home is not usually as painful as it sounds :guitar:

---

### Post by justjustin on 2011-10-24
Ok, thanks for the reply,
How about if I kept my /home, but wipe /boot and /, and leave unallocated 30GB at start of disk for Windows and install it.
In the unallocated 180GB at end of disk, create an extended partition for Ubuntu / and /swap, and an NTFS or FAT partition for data, then install Ubuntu.
Do you think this would be ok?

---

### Post by satanselbow on 2011-10-24
> **justjustin said:**
> Ok, thanks for the reply,
How about if I kept my /home, but wipe /boot and /, and leave unallocated 30GB at start of disk for Windows and install it.
In the unallocated 180GB at end of disk, create an extended partition for Ubuntu / and /swap, and an NTFS or FAT partition for data, then install Ubuntu.
Do you think this would be ok?

If you are happy to clean install ubu then yeah knock yourself out ;)

The aim of the game is to free up 2 primary partitions ;)

If you want to close up the gaps of unallocated space you can slide the partitions snug up to each other in gparted - this may however involve moving large volumes of data and be very time consuming :(

You may also want to consider placing you Windows partition right at the front of the drive. Whilst an extended partition can contain multiple logical partitions - the extended partition itself cannot be split across multiple areas of the drive.

---

