---
title: "Boot Ubuntu off of second har drive"
date: 2007-04-05
forum: Installation &amp; Upgrades
---

### Post by klauern on 2007-04-05
So I have been messing around with this for a couple days and I still have not gotten anywhere...

I have The following configuration: 2 Hard drives RAIDed in the BIOS before a boot screen comes up, one IDE drive that has Windows Vista and Ubuntu installed on separate partitions.

The Raid has XP installed on it as well as Vista's Bootloader.

The issue is that I cannot figure out how to get ubuntu to boot using Windows Vista's bootloader.  I believe Ubuntu's GRUB is loaded into the MBR of the IDE drive(secondary drive), and when I switch the boot order in the BIOS to boot off of the IDE instead of the RAID, it will boot Ubuntu immediately.

I've tried doing all sorts of dumps to file, such as dd of=/dev/hdb if=/media/Temp blah blah blah

But the issue is that whenever I put that dump into Window's XP's legacy boot loader, it won't load, simply hangs or ends up with "GRUB" on the screen but nothing happening.

Is there any way to make this work?  Am I forgetting something?

---

