---
title: "Installation questions"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by socalheel on 2011-04-21
I have a Sony Vaio laptop with 64-bit Windows Vista. 
 
Two partions
 
C:\ - for my OS and program files
D:\ - World of Warcraft and music files
 
 
I want to install 11.04 when it is released (heck I might just not wait and install 10.10) and use it solely as my OS. My questions are:
 
1) When I install Ubuntu, will I have the option to overwrite the OS on the C:\ partition; and
2) How will my D:\ drive be affected? Will I just be able to install Ubuntu onto C:\ and then everything will function normally?
 
 
Nevermind ... WoW requires Windows or Mac, Ubuntu is not supported.

---

### Post by Rubi1200 on 2011-04-21
Some links you might want to read:
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
[https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549)

Depending on how much space you have, you could consider dual-booting.

---

### Post by socalheel on 2011-04-27
oh awesome info ... thanks a lot!!!

---

### Post by mmad on 2011-04-27
> **socalheel said:**
> oh awesome info ... thanks a lot!!!

Just to add, are you sure you want a sole Ubuntu partition? Whilst I don't mind using it now, when I first used Ubuntu I hated it because of the massive transition. Id suggest a dual boot and then if you are sure you are comfortable with Ubuntu alone, remove the Windows partition later.

---

### Post by socalheel on 2011-11-14
> **mmad said:**
> Just to add, are you sure you want a sole Ubuntu partition? Whilst I don't mind using it now, when I first used Ubuntu I hated it because of the massive transition. Id suggest a dual boot and then if you are sure you are comfortable with Ubuntu alone, remove the Windows partition later.


sorry, was away for awhile and wasn't able to check in until a few days ago.  

i did install with windows option so i do dual-boot for now and hopefully will transition into full ubuntu after the holidays.

thanks for the help.

---

### Post by Mark Phelps on 2011-11-14
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

