---
title: "I broke Windoze ( oops...) :-k"
date: 2006-04-02
forum: Installation &amp; Upgrades
---

### Post by Ric95 on 2006-04-02
I just got Ubuntu ( 6.04 ) set up on dual boot, and I like it. :) 
But we still need WinXP ( and the files there). 
I used Partition magic to make the partition and start the Ubuntu install so now Ubuntu works on hda/3 8) 
But I should have used Partition magic to partition only, not start inst. when I try to boot to Windoze, (on hda/2) it get to the loading screen for a moment, then I get the blue screen ( with orange stripe across top and bottom...) saying 'xmny not found'. and it kicks me back the starting compaq screen. 
I think Partition magic screwed the registry. If anyone knows how to fix that, please tell me. 
Alternatly, I have tried re-intalling XP from a disc, but it doesn't show the partition hda/2 that I want it to overwrite. 
If anyone here has fixed this please tell me. :-k

---

### Post by Sef on 2006-04-02
> But I should have used Partition magic to partition only

There are known issues with Partition Magic and Linux.  GParted on the Live CD is a better to partition with.  Applications > System Tools > GParted


> Alternatly, I have tried re-intalling XP from a disc, but it doesn't show the partition hda/2 that I want it to overwrite.
If anyone here has fixed this please tell me. 

Is hda2 set up as a NTFS file?  You should try converting it to that and see if that works.

---

### Post by Ric95 on 2006-04-02
Fixed. And you were close (thanks), It already was NTFS, but Partition Trajic set it as 'Hidden' . I just used sfdisk and unhid it. ( type 17, in other fdisk programs)

---

