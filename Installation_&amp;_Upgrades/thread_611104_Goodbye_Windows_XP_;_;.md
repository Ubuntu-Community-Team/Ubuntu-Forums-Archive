---
title: "Goodbye Windows XP? ;_;"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by VGF on 2007-11-12
Okay, I've been using Ubuntu off LiveCd for a while, and have fallen in love with it.  So I started to install it last night, but for some reason, the partitioning wasn't going well, so I stopped it, went back into XP and finished my night.

Now today I decided to give it another shot.  I go into the manual partition during installation and here's what comes up:

*Device*: /dev/hda1 *Type*: fat32 *Mount Point*: /media/hda1* Size*: 3855MB *Used*: 3800MB
*Device*: /dev/hda2 *Type*: ntfs* Mount Point*: /media/hda2 *Size*: 35448MB *Used:* ***_unknown_***
and about 700MB of "free space"

Elsewhere, when I start up the PC without the LiveCD in, it won't start XP, but show a black screen with a little white line blinking.  

So am I screwed out of XP now? (prebuilt compy, so no copy of XP).  I'm only going to have this computer for maybe another month, so its not a huge deal.  but it would be nice to know my future.

And if XP is done for, how would I go about installing Ubuntu (7.10) over everything else?

Thanks! ;D

---

### Post by Pumalite on 2007-11-12
Boot your XP Installation CD>hit 'r' for Recovery>FIXMBR>FIXBOOT. Boot into XP, defrag several times, erase all temp files, set Page File to '0' (reset to normal value later). Then get Gparted Live CD. Boot from it and resize your XP partition. Then install Ubuntu in that partition.

---

### Post by kyphi on 2007-11-12
Since you do not have an XP installation disk I cannot advise you on how to repair your XP installation.

One essential that everyone should have is a Boot Disc such as the 'Super Grub Boot Disc' that would repair the Master Boot Record if it is possible.  Keep it in mind for when you have a functioning operating system again.

If you are resigned to having lost XP, just place your Ubuntu disc into your DVD/CD player and reboot.  You can then use the whole disc for the installation and Ubuntu will take care of all the formatting and partitioning.

---

### Post by Pumalite on 2007-11-12
If you don't have XP CD, you can fix your MBR with Super Grub: 
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by VGF on 2007-11-12
I did manage to find my recovery disks...but something was wrong with one of them....and it ruined that whole idea....

---

### Post by arnix on 2007-11-12
Try boot your system with rescue dos diskette (don't have floppy drive?'use Hiren's Boot CD or similar':'') and execute:

fdisk.exe /MBR

Then remove the diskette and press ctrl-alt-del

---

### Post by Pumalite on 2007-11-12
Did you try Super Grub?

---

### Post by sports fan Matt on 2007-11-13
> **VGF said:**
> I did manage to find my recovery disks...but something was wrong with one of them....and it ruined that whole idea....  I always hated that about windows..Are their any scratches on the disk, may try a cd cleaner as well..It helped me in getting cd's to run alot:)

---

