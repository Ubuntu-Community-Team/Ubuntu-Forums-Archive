---
title: "New Dual Installation"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by fuligin on 2007-01-29
Hi everyone,
This is my first post as this is my first attempt at Ubuntu, 
I was recently runing Suse 10.2 however i would like to experiance Ubuntu 6.10, before I decide on which Linux distro to settle on. Previously I have installed this version of Ubuntu on my junk laptop and must say it performs alot faster then Suse 10.1. 
Anyways here is my ordeal. 
I have a 40gb HD
C: 5.86Gb  (2.01 Gb Free) (XP Installation)
D: 1.49Gb  (890 Mb Free) (Program Files)
E: 19.00Gb (5 Gb Free)    ( Misc & data files)

10.87gb  ( This partition will be dedicated for Ubuntu, is this sufficient or do i need to allocate one)

Initially i am planing for 1gb swap and the rest goes to ubuntu, however when i try to create the partition from the installation on the live disk, it tells me that i cant create a new partioon, 
What can i do in order to properly install my new ubuntu.
Thank you all in advance for your support.

BTW my laptop is Thinkpad R51e, 512 mb ram, in case any of this info is needed or any extra tips can be given in regards to this sysem

---

### Post by mysticrider92 on 2007-01-29
Is it saying you can't make the swap partition after making the main Ubuntu partition? The reason for that might be that you can only have 5 primary partitions on a single hard drive. It would be possible to make a 10 gb logical partition and separate that into a swap and main partition and everything should work.

10 gb is plenty for Ubuntu. You shouldn't need 1 gb for swap, I have 512 mb of RAM and about 600 mb of swap (I don't even need that) and everything runs fine.

---

### Post by glabouni on 2007-01-29
you should consider [creating a separate /home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome"). 
you can also read [Partitioning Windows and Ubuntu]("http://www.psychocats.net/ubuntu/partitioning").

> A maximum of four partitions can be placed on any hard disk. These are sometimes called primary partitions. The limitation of four is one that is imposed on the system by the way that the master boot record is structured.
[http://www.pcguide.com/ref/hdd/file/structPartitions-c.html](http://www.pcguide.com/ref/hdd/file/structPartitions-c.html)

> Partitions are divided in three types: primary, extended and logical. 

A primary partition is a partition which has its information stored in the MBR (master boot record). As an MBR is very small (512 bytes) only four primary partitions can be defined (for instance, /dev/hda1 to /dev/hda4). 

An extended partition is a special primary partition (meaning the extended partition must be one of the four possible primary partitions) which contains more partitions. Such a partition didn't exist originally, but as four partitions were too few, it was brought to life to extend the formatting scheme without losing backward compatibility. 

A logical partition is a partition inside the extended partition. Their definitions aren't placed inside the MBR, but are declared inside the extended partition.
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4)

the answer to your problem is to use extended partition.

---

### Post by fuligin on 2007-01-30
Thank you all, I created 2 logical disks from xp side, one in ext3 format and one as a linux swap, then directed the installation to those drives. 
Ideally how much space is needed for Ubuntu to run, from wut i read above my 1gb swap is too big. I understand that the minimal required space is 2gb, would. Would  4-5 gb be suffiient. 
Im justing trying to figure out what kind of paritioning would be advisable for a 40gb drive. As after I have tested gotten used to Ubuntu, i plan on doing a clean format and reinstall xp & Ubuntu and my data partitions ( without too many primary parts.)

I really like the feel of Ubuntu so far, though it keeps crashing :(  I havent done any upates or installed anything yet, so hopefully all those porblems will go away after i have done that :)

---

