---
title: "w2000 and ubuntu install"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by DaveDoesIT on 2008-06-01
Hi people,

I am positive this has been asked about a zillion times, but my searches proved futile. My searches got hundreds of results so thought I would badger you experienced guys one more time. 

I have a desktop PC with w2k-sp4 on it and would like to dual boot Ubuntu, actually Kubuntu. Can someone please point me at a good tutorial on the process?

I am so new to Kubuntu the disk has not yet arrived in the mail. I am however a programmer of some 30+ years experience so wandering around the dusty portals of the PC architecture holds little fear for me.

I would appreciate some pointers on where to start with the dual boot set up. I have read so far that Linux needs to be located in the first 1024 Cylinders on the hard drive. This may not be possible as my w2k has been in use for 4 years and a new partition would almost certainly be created well beyond that 1024 Cyl. mark. Is that a problem?

Thanks 

Dave

---

### Post by aqk on 2008-06-02
It should be a piece of cake. 
I just did this myself this week with my new 8.04

If you currently have some windows partitioner such as Partition-Magic,
shrink your C partition down to about 15 gig smaller than it now is, giving you some 15 G of empty space.
 Whether it should be before the "1024 cyl" boundary, I have no idea.- I haven't worked with cyl-count-key stuff since my mainframe days 20 years ago.
In this 15 gig area, define 2 linux partitions:  a small 1G swap, and the rest (14G or whatever) as EXT2 

If you think the spare room should go at beginning of disk, then why not?

If you do NOT have a Windows partition program, then wait for your Ubuntu disk. 
And boot from it. It will guide you. Use the regular setup. At some point it will ask you about disk room.
Just make sure you DO NOT choose the "USE WHOLE DISK FOR UBUNTU" option.
I didn't try it, but Ubuntu install should be able to re-allocate your Win partition (NTFS? FAT32?) to free up that 15 G. 

Once you have this 1G swap area and 14 or so Gigs of EXT2, Ubuntu will install itself accordingly.
And it will install a GRUB boot-time loader to allow you to choose either Ubuntu or Win2K. Bu note that it default to Ubuntu after 7 seconds or so, so do NOT go get a coffee when you first turn on your PC, unless you want Ubuntu booted!
Later you can change the GRUB params to default to Windows, 30 second timeout etc.  
Good luck!

---

### Post by DaveDoesIT on 2008-06-03
> **aqk said:**
> It should be a piece of cake. 
I just did this myself this week with my new 8.04

Thanks aqk,

I'll wait for the DVD to arrive then follow the bouncing ball. Ahh, mainframe days. <g> You must be about as old as I am. :)

Dave

---

