---
title: "Partition Question"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by ivotedforkodos on 2006-06-06
I have a 320 GB WD hard drive, and when running the Dapper installer from the CD, I tried to set aside 178 GB or so for /home. For some reason the installer failed when creating the partition, and scaled it back to 88.4 GB. Now my partition scheme looks like this:

[ATTACH]10747[/ATTACH]

and I have 87 GB of unused space. I can't seem to resize or move any of the partitions, nor mount the unused space. Is there any way that I can recover this space without repartitioning the whole drive?

BTW, is this a stupid partition scheme? (Noob)

---

### Post by aysiu on 2006-06-06
QTParted and GParted are generally good partitioners.

Sometimes, though, they have these weird situations where options that should be available are greyed out or unavailable.

The only reliable and free disk partitioning program I've seen is [DiskDrake](http://www.ubuntuforums.org/showthread.php?t=114142).

---

### Post by rcarring on 2006-06-06
The unallocated  space is beyond the fourth partition:

You have four primary partitions including the extended partition. You cannot have more than four primary partitions.

I am beginning to realize that hard disks are getting so huge now, operating systems cannot cope.

---

