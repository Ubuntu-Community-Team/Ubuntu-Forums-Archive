---
title: "Ubuntu 10.10 Install crash"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by phoenix17 on 2010-12-02
Each time, different methods, I get this about 3/4 of the way through:

The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.


The only possibility of those is the CD being bad. But I've used it before, recently, and it was fine. I will burn another one from my other computer and try, but it shouldn't be doing this.



Question:
If I plan to only use Ubuntu on this computer (no dual boot) should I make the /,swap and /home partitions all Primary or some logical, or does it even matter?

Sorry for yet another crash bug post, but the others I found via search didn't have the same problem.

---

### Post by grahammechanical on 2010-12-02
As I understand things, the installation process puts /swap on its own partition. Your only choice is perhaps the size of it.

In my opinion it is better to have /home on its own partition then if you need to reinstall the Operating System and format the partition you do not loose your data or settings information. 

Again as I understand it, the file system or something can only access 4 primary partitions but many more logical partitions. I have one primary partition and three logical partitions on what is called an extended partition (I think). I do not think that I was given a choice in this. I first installed Ubuntu on one partition. Then, as I became more confident I created other partitions and Partition Manager did the rest.

I hope this helps and is mostly accurate.

regards.

---

### Post by Sef on 2010-12-02
> If I plan to only use Ubuntu on this computer (no dual boot) should I make the /,swap and /home partitions all Primary or some logical, or does it even matter?


Does not matter. Just remember you can make only four primary partitions, but an unlimited number of logical (extended) partitions.

---

### Post by Fluffgar on 2011-01-28
This is exactly the same installer crash I am getting trying to put Ubuntu 10.10 on my mum's computer. I've tried both installation methods repeatedly. Always crashes at the same point as this. Always with the same message. 

Had to dig out an old copy of XP in the end. Not happy about that. If anyone knows of a way to fix this/work around I'd be very glad to hear it.

---

### Post by nogoodnamesleft on 2011-01-28
check the md5 hash for the CD to determine if it is corrupt

edit: sorry didnt see you say it was working before, but no harm to check

also just general stuff update flash the bios (if outdated) and i dont know how wubi works (never used it) but scan the file systems of course

---

### Post by ommos on 2011-02-14
I have the same problem.

Made the boot CD from the downloaded ISO. The MD5 on the ISO is correct. The CD was written at lowest speed (8x) and verified afterwards (OK).

The machine I try to install it on has to HDs (sda, sdb) on which I originally installed 8.04 or something and upgraded until 10.10.
I bought an SSD and wanted to do a clean install on the SSD, so I made the LiveCD and booted from it and partitioned the SSD (sdc) and the install starts copying files. Then after some time it gives the messages as described by the original poster.
From the old installation, I can mount the SSD and see indeed files on it.

What can I do to get the installer working correctly? I want to keep my old installation alive to copy stuff from it to the new.

Edit: amd64 desktop version

---

### Post by lfod on 2011-02-22
I have been having the same problem with a system that I reinstalled ubuntu onto after I got a new HD. I removed the new HD and tried to install with a DVD and a USB stick and I get the same error. I have downloaded the iso multiple times and each time it checks out. What is going on? I love ubuntu but it is being a pain. I have a laptop that works(OS X) and a desktop that runs windows 7 if I really want it to...

---

