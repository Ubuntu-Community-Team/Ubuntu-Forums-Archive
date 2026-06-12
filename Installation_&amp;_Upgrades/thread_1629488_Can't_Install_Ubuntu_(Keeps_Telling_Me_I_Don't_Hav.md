---
title: "Can't Install Ubuntu (Keeps Telling Me I Don't Have Enough Space)"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by grkstln on 2010-11-23
Hi everyone,

I'm trying to install Ubuntu 64 bit on my system, but whenever I try to install it, I can't get through the part where it does the preinstall checks. I can't figure out what's going on because I definitely have enough space for it, but it's like its not detecting my hard drive.

I also updated by bios, but it didn't fix the problem :/

I'm running on a system with a gigabyte P55A-UD3 mobo, an i5 processor, and have a WD Caviar Black WD1002FAEX hard drive. 

Any thoughts on how I could fix this?

Thanks.

---

### Post by Bucky Ball on 2010-11-23
What is currently on the hard drive?

---

### Post by grkstln on 2010-11-23
> **Bucky Ball said:**
> What is currently on the hard drive?

Two partitions, one with windows 7 and another with windows vista. There's 500 gb free on the main partition with 7 though.

---

### Post by Bucky Ball on 2010-11-23
Having 500Gb free in an existing partition is of no help. That will be read as a used partition (because it is). 

You need to shrink that partition and create 500Gb of *FREE SPACE!* to install Ubuntu to.

The message you are getting is no mistake; completely correct. There *is* no free space as your drive is full up with two partitions. There is no free space for Ubuntu to create any partitions.

As you have Windows on the two partitions, shrinking can take some time as you should defragment the partition you are going to shrink.

---

### Post by grkstln on 2010-11-23
> **Bucky Ball said:**
> Having 500Gb free in an existing partition is of no help. That will be read as a used partition (because it is). 

You need to shrink that partition and create 500Gb of *FREE SPACE!* to install Ubuntu to.

The message you are getting is no mistake; completely correct. There *is* no free space as your drive is full up with two partitions. There is no free space for Ubuntu to create any partitions.

As you have Windows on the two partitions, shrinking can take some time as you should defragment the partition you are going to shrink.

Ah, well I forgot to add that there is 78.13 of unallocated space from me shrinking the main partition prior to trying to install, assuming that I could just create a partition with it within the installer. 

So do I need to create a partition with this unallocated space prior to installing?

Sorry that I didn't mention this sooner, but I assumed it was unrelated.

---

### Post by Bucky Ball on 2010-11-23
No, you were right. You will be able to create the appropriate partitions in your 78Gb free space when you get to that part of the install.

When you get to partitioning, and you will, shoot for manual partitioning. You will see all your windows stuff there (they will be labelled as NTFS or FAT partitions); just leave 'em alone. The free space will be clearly visible also. Shoot for that.

You are going to need (advisably) three partitions:

/ (which is your root partition for the OS to go to;
/home (your personal data;
/swap (self explanatory: you don't need more that 2Gb)

These all go in your 78Gb free space. the / partition does not have to be huge (15Gb?), it depends how you want to set things up. /swap should go at the end.

I don't really know, yet, why the install disk is having problems. The best and most reliable way to get the ISO is via a torrent. Have you checked you install disk, as in, 'Check this disk for defects' or an option like it when it hits the screen, if you get that far?

Plan B: Torrent down the ISO again (this will be checked for defects on the way down), make a CD, try from that and see if you get the same issues.

---

### Post by grkstln on 2010-11-23
> **Bucky Ball said:**
> No, you were right. You will be able to create the appropriate partitions in your 78Gb free space when you get to that part of the install.

When you get to partitioning, and you will, shoot for manual partitioning. You will see all your windows stuff there (they will be labelled as NTFS or FAT partitions); just leave 'em alone. The free space will be clearly visible also. Shoot for that.

You are going to need (advisably) three partitions:

/ (which is your root partition for the OS to go to;
/home (your personal data;
/swap (self explanatory: you don't need more that 2Gb)

These all go in your 78Gb free space. the / partition does not have to be huge (15Gb?), it depends how you want to set things up. /swap should go at the end.

I don't really know, yet, why the install disk is having problems. The best and most reliable way to get the ISO is via a torrent. Have you checked you install disk, as in, 'Check this disk for defects' or an option like it when it hits the screen, if you get that far?

Plan B: Torrent down the ISO again (this will be checked for defects on the way down), make a CD, try from that and see if you get the same issues.

Well... I downloaded the torrent and compared it with the original file I downloaded and they both had the same checksum. So that leads me to believe it's not the iso.

---

### Post by efflandt on 2010-11-23
Does your drive have regular partitions, or some sort of Windows dynamic volumes.  In other words if you boot the install CD (or bootable iso on USB) to a live system, what does **sudo fdisk -l** (small L) show for partition type(s)?

Or you can get more complete info about things on your drive using the boot info script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by grkstln on 2010-11-24
> **efflandt said:**
> Does your drive have regular partitions, or some sort of Windows dynamic volumes.  In other words if you boot the install CD (or bootable iso on USB) to a live system, what does **sudo fdisk -l** (small L) show for partition type(s)?

Or you can get more complete info about things on your drive using the boot info script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

This is what I got from the script: Sorry it took me so long to respond. This was from running ubuntu off of the CD.

[B]                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found [/B]

---

### Post by Quackers on 2010-11-24
Which partition was shrunk to generate the free space, and what was used to shrink it please?

---

### Post by grkstln on 2010-11-24
> **Quackers said:**
> Which partition was shrunk to generate the free space, and what was used to shrink it please?

Hrm I actually just managed to fix this by switching the gsata ctl mode option to "ahci" in the bios settings.

I'm running into some problems with the internet connection now though, but I'll post that in the proper area.

Either way though, thanks for all the help and replies guys. :D

---

### Post by Quackers on 2010-11-24
Nice one :-)

---

