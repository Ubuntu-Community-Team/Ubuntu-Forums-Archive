---
title: "dual booting ubuntu and windows 7 with truecrypt"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by rvkid15 on 2010-12-27
Hi all,

right now I have windows 7 encrypted with truecrypt and I want to dual boot Ubuntu 10.04(not encrypted). I'm going to shrink my windows partition to install Ubuntu. Is there a way to add ubuntu to truecrypts bootloader?

---

### Post by Mark Phelps on 2010-12-27
Don't know about adding Ubuntu ... but be sure to use the Win7 Disk Management utility to shrink the Win7 OS partition.  Don't trust the Ubuntu installer to do that for you.

Also, after you do the shrinkage, boot into Win7 a couple of times to allow it do do any needed filesystem adjustments.

And, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will provide you a way to repair the Win7 Boot Loader should it become damaged during the dual-boot install.

---

