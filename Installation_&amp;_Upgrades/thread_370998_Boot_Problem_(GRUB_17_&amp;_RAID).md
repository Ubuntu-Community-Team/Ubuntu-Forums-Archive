---
title: "Boot Problem (GRUB 17 &amp; RAID)"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by obe1kenobi on 2007-02-26
So, my situation is kind of odd, at least to me.  So this is one of our computer club lab servers and I'm trying to install Edgy on it.  The former president had installed it on there just fine, but before I did I used DBAN to wipe the drives.  It may have had a RAID setup on it before but nobody knows.  So, if I don't have a RAID array set up and I  install Ubuntu, it will boot up and say DISK BOOT FAILURE PLEASE INSERT SYSTEM DISK.  But if I set up a RAID array I get a GRUB ERROR 17.  There's no way to turn the RAID controller off (it's a Biostar M7VIK) that I can see and I tried flashing the BIOS.  It may be something I'm doing wrong in setting up my partitions during install. I've never installed on a RAID before so this is a very likely possibility, but the other guy who installed it didn't do anything out of the ordinary, he says.  

I've tried to set up normal partitions like I would for nonRAIDed drives, I tried LVM for the / and regulars for /boot and swap, I tried the same with RAID 0 for / instead of LVM, so I don't know what to do.  

I've been using RAID 0 for the arrays I was setting up, not sure what if any it was set to before.  And they are two SATA drives.  Any help would be awesome, so thanks in advance.

---

