---
title: "[SOLVED] Install, reinstall etc"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by Xoanan on 2008-07-24
Hi All

I have been attempting to help my mom with a pc we bought. When we bought it, we installed Xubuntu 6.10 onto it and it worked fine.  The moment we attempted to upgrade, we got such things as "kernel panic" and various other errors.

I attempted to wipe it and install 8.04 onto several times, and although it appears to install fine most of the time, it either comes up with various grub errors  (18, 25 et al) or it runs very slowly.

The pc is a rather compact afair.  The monitor and the unit are joined together as a single unit.  We have 256 MB of RAM and a 40.1 Gig Maxtor Harddrive.  It appears to be a an Intel Processor.

Keep in mind that when we got it, it had no OS on it all, so there is nothing else but Xubuntu on it.  Now considering that we have attempting to do this several times without success, there might be several versions on it, now scattered about. 

Any advice on this?

:popcorn:

---

### Post by overdrank on 2008-07-24
> **Xoanan said:**
> Hi All

I have been attempting to help my mom with a pc we bought. When we bought it, we installed Xubuntu 6.10 onto it and it worked fine.  The moment we attempted to upgrade, we got such things as "kernel panic" and various other errors.

I attempted to wipe it and install 8.04 onto several times, and although it appears to install fine most of the time, it either comes up with various grub errors  (18, 25 et al) or it runs very slowly.

The pc is a rather compact afair.  The monitor and the unit are joined together as a single unit.  We have 256 MB of RAM and a 40.1 Gig Maxtor Harddrive.  It appears to be a an Intel Processor.

Keep in mind that when we got it, it had no OS on it all, so there is nothing else but Xubuntu on it.  Now considering that we have attempting to do this several times without success, there might be several versions on it, now scattered about. 

Any advice on this?

:popcorn:

Hi and if the system has 256mb that is the minimum but the graphics will share that with the onboard graphics. You may look at something lighter as a distro. Puppy and DSL come to mind but there are plenty others.

---

### Post by Xoanan on 2008-07-24
Possibly; however; I installed Xubuntu on my machine at only had 128 MB on it. I did upgrade the ram to 256 and then 384, but that's about it.

---

### Post by overdrank on 2008-07-24
> **Xoanan said:**
> Possibly; however; I installed Xubuntu on my machine at only had 128 MB on it. I did upgrade the ram to 256 and then 384, but that's about it.

I understand that you had Xubuntu 6.10 but IMO Hardy Xubuntu is more resource heavy. As the minimum sys req. went up to  
Ubuntu is available for PC, 64-Bit PC and Intel based Mac architectures. At least 256 MB of RAM is required to run the alternate install CD (**384MB of RAM is required to use the live CD based installer**). Install requires at least 4 GB of disk space.
> I attempted to wipe it and install 8.04 onto several times, and although it appears to install fine most of the time, it either comes up with various grub errors (18, 25 et al) **or it runs very slowly**.
This has been my experience also. It runs slow on a 256mb system but will make do on a 512mb system. I could see a slight improvement at 384.
Maybe try Feisty or Gutsy. as for the grub errors you may be able to install the grub again or check the cd for errors and 
do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Xoanan on 2008-07-24
hmmm.  Okay;  I will try that.  I may have to go back and get the 6.10 CD and run that instead of 8.04. Mom still has it at her house.

---

### Post by Xoanan on 2008-07-24
Hi All

I still don't have the 6.10 install, but I managed to try a few install options that hadn't tried before to get my Mom's pc working.  I created a new partition for it that was only 2 GBs.  The whole HD is 40 GB and that was what kept generating GRUB error 18.

Now I have a different issue.

Now at boot up, GRUB shows 4 different options for booting. There are as follows
[list] Xubuntu 8.04,
Xubuntu 8.04 (recovery mode)
Xubuntu 8.04 (memtest
**Other OS**
Xubuntu 8.04 hd1[/list]

The only one that works sufficiently well is the recovery mode which boots up nicely and runs smoothly after the boot. 

I could leave it at that, but the last time that happened, the pc froze again with another GRUB error, so what I am thinking is, I need to format the other partitions on the system.  The problem is, I can't tell which one I am using at the moment by using the ```
fdisk -l
``` command.  Is there a way to tell which partition I am actually using?

:popcorn:

---

### Post by Xoanan on 2008-07-29
Update

harddrive failure; I replaced the harddrive and installed Xubuntu. Works like a charm.  Thanx!

---

