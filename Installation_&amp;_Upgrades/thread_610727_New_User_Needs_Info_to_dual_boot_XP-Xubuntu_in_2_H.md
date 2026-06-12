---
title: "New User Needs Info to dual boot XP-Xubuntu in 2 HDD (IDE/SATA)"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by X-Gamer on 2007-11-12
Hey guys im a Windoze user for some years now and i wanted to try Linux. After searching various distribution and version I decided to get Ubuntu 7.10 with Xfce desktop (aka Xubuntu). Now, I have already downloaded the standard setup image file to my computer but still haven't done anything yet. When I bought my PC i had an IDE/ATA hard disk of 80GB. Recently i added an SATA hard disk of 320GB which i use mainly for storage but sometimes also install programms in it. Both drives are formatted in NTFS. I have seen various guides and what i want to do is to be able to boot from grub to either WinXP or Xubuntu without much trouble in every boot. I also want both Operating Systems to be able to access both drives and i want Windows to be able to use programs from the drive in which Xubuntu is installed. I don't particularly like the idea of partitioning any of my disks, so i would like not to do it if possible.

By the way, my motherboard is a Shuttle AB60P with Intel socket 478, is it supported by Xubuntu?

I would really appreciate it if someone could tell me what i have to do to achieve all the above, what are my options and what i can't do. :popcorn:

*Note that I have already read and understood how to burn the iso to a CD and boot to the Linux Live cd but what after that?*  :lolflag:

---

### Post by armalite1969 on 2007-11-12
I have the same configuration.  Two drives each on their own serial ATA port.  One is my original XP drive, and one is a new drive configured to dual boot both XP and Ubuntu 7.10.  I would like to be able to select which drive to boot to however when I power up, my only options are to boot to the drive I configured with both XP and Ubuntu.

---

### Post by armalite1969 on 2007-11-24
I figured it out.  Just install with all the drives online.

---

### Post by X-Gamer on 2007-11-25
Actually i came across a strange problem. I checked the cd for problems after burning but it was ok. When trying to boot into Live CD though, the loading screen got messed up and my screen's ON/OFF button turned red (e.g. problem) and while the rest screen got black a white message appeared saying:

"The screen's resolution/refresh rate too high.
1024x768/60 Hz recommended."

The thing is that the options in my pc were ALWAYS like that. My graphics card is albatron nvidia 7600GS with the latest nvidia drivers installed. What might be the problem? :confused:

P.S. the way YOU did the installation did u have to create any partitions or format the HD?

---

### Post by armalite1969 on 2007-11-25
I have never had the resolution problem booting to the CD.  I have had the resolution problem after installing the OS.  The problem I had was that I could not go beyond 1024x768 when I wanted 1280x1024.  I fixed that problem with a solution provided on the forums.  I think you make some changes with xorg.config or something like that.  I am new to the linux stuff.  My booting problem was that I have two drives, one has my original WinXP and the other I installed specifically to build a dual boot (one physical drive partitioned into two logical drives) WinXP with Ubuntu.  When I built up the new drive with XP and Ubuntu, I made the mistake of taking my original drive offline.  I re-did everything with all drives on line and now everything shows up in the boot menu when I turn on the machine.  Works good now.

---

