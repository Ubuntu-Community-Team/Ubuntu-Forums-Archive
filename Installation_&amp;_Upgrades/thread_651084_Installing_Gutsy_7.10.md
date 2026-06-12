---
title: "Installing Gutsy 7.10"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by LezSpiller on 2007-12-27
I am a total 'rabbit' in the Linux arena!  I've just bought a 'Ubuntu-on-a-disk' and 'Ubuntu Linux for Dummies' and tried to follow the procedure therein to install the program - to absolutely no avail! 
I have a 160 gb HDD, 2 partitions.
Partition1 is 130gb with XPpro NTFS, spare partition for Ubuntu 30gb NTFS.
When I go thru install procedure from the CD it gets as far as trying to put it on the spare partition, but tells me that I have to do some sort of 'mount' operation - none of which are described in the book! (surprise, surprise??)
What do I have to do, please?

Lez

---

### Post by icheyne on 2007-12-27
Go into the manual partitioner and partition the 30GB as EXT3 - NTFS is a Windows file system.

Maybe that will fix the mount problem?

---

### Post by dvijaydev46 on 2007-12-27
Go to manual partition and click on the partition you want to install ubuntu and select it with Ext3 file system and select it as "/" and not anything else. you must also create a swap partition which should be easy to do.

---

### Post by icheyne on 2007-12-27
[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Irony on 2007-12-27
Simplest way is to go into windows and unallocate the 30 GB partition (admininstrative tools > computer management).

Now re-boot into the Ubuntu CD and choose auto-install to the 30GB freespace - this will divide the freespace into root and swap partitions.

---

### Post by a-converted-sparky on 2007-12-27
I can second that

I have just moved over to the dark side, so to speak! and i done exactly what irony said.

Being that i had Vista, you can shrink the volume and use that space to install ubuntu onto - so you dont need to be a partition expert.

Loving this place btw

---

