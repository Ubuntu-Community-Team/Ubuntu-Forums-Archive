---
title: "RAID 1 (Mirror) problem with dual-boot XP system"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by aphex./ on 2008-01-11
Hi,

This is my first post, so bear with me!

I've used Ubuntu before, but I'm pretty much a n00b; I've just installed 7.10 on my PC after first installing XP, but my problem is with my hardware RAID 1 (Promise FastTrack 378 controller).
In Windows you only see effectively see 1 drive, which is fine. When installing Ubuntu, I select manual installation, and can see BOTH drives.

My question is: do I just go ahead and install on partition x and will this be mirrored across? I.e. I have the option of installing on partition x on sda1 or sda2, and does this matter, as they should be mirrored anyway?

TIA,

aphex

---

### Post by kipling100 on 2008-01-11
Hi, check out this link for a step-by-step guide:

[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

I just finished installing Ubuntu on a RAID 0 set with Vista installed, so it worked for me...good luck!

---

### Post by miceagol on 2008-01-12
I have 2x320 GB in RAID 1, and a 500 GB in non-RAID. I'm going to install Ubuntu on the 500 GB, but I want my /home folder on the RAID-array. In other words, I'm not installing Ubuntu on the RAID-array, but all guides I find is about installing Ubuntu on the RAID-array.

In the Ubuntu-installer, I see the RAID-array only as two separate disks. If I fire up gparted I see the RAID-array in addition to the two disks (/dev/mapper/isw_bhfbehdiee_Mirror).

What do I do to make the Ubuntu-installer treat the two disks as a RAID-array?

---

