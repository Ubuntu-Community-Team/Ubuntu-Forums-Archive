---
title: "Booting into Dapper with Windows XP Pro"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by encynerate on 2006-10-27
I'm attempting to install Ubuntu on my box by partitioning my current system drive, an 80gig SATA, into 3 parts, the current File system, ext2 and the swap file system. I've done this with the help of Arconis Disk Director Suite, and have had no problems. The thing I'm hung up on, is getting able to boot into Ubuntu after completing the install. I've double checked the mounts, so I'm almost certain they're ok. I've heard some things about using GRUB to set up the boot, but haven't seen anything resembling GRUB while installing. What I want ideally is to be able to edit the XP Boot startup menu and use that. If not, oh well.

---

### Post by Swab on 2006-10-27
> **encynerate said:**
> I'm attempting to install Ubuntu on my box by partitioning my current system drive, an 80gig SATA, into 3 parts, the current File system, ext2 and the swap file system. I've done this with the help of Arconis Disk Director Suite, and have had no problems. The thing I'm hung up on, is getting able to boot into Ubuntu after completing the install. I've double checked the mounts, so I'm almost certain they're ok. I've heard some things about using GRUB to set up the boot, but haven't seen anything resembling GRUB while installing. What I want ideally is to be able to edit the XP Boot startup menu and use that. If not, oh well.

How far through the install did you get?  I believe with the graphical installer there is actually no mention of GRUB but after installation is complete and you reboot, GRUB should be there with the option to boot into Windows or Ubuntu.  With the text installer GRUB is mentioned at the end of the install.

---

### Post by encynerate on 2006-10-28
I got all the way through the install, restarted, removed the CD, and let it boot. After which, it went right into XP Pro, with no GRUB screen at all.

---

### Post by encynerate on 2006-10-28
alright, so, I tried a couple of different guides out there, like the one the Ubuntu Wiki 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

according to Step 9, it should automatically detect Ubuntu, but it doesn't. So I'm all confused and the like.

EDIT: If anybody has a clue how to Manually input the Ubuntu boot info into my Boot.ini in windows, it would also be greatly appreciated.

---

