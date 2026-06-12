---
title: "SATA/EIDE access problem"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by Uruclef on 2008-07-18
Hi all!
I have a new system, with the motherboard Asus P5Q-E.
I have 2 disks:

- 500gb SATA drive, with windows XP installed and a data partition
- 120gb EIDE drive, with Ubuntu 8.04 installed

I've had to set the Enhanced IDE mode for the SATA controller, since when using AHCI Windows fails to boot (:|) with a BSOD, and IDE seems to be the only working mode for both operating systems. The problem is that in IDE mode linux can't access the windows drive, it's not even listed in "fdisk -l" output. Windows can normally see the linux drive. Using AHCI Linux can see both drives and normally operate with it, but (as already stated) Windows can't boot.
It seems that one of the two drives at a time is recognized by the Ubuntu live cd; specifically the one that is set in the motherboard's BIOS as boot the device. 

I also have another (minor) problem: the CPU and chassis fans are always at the highest speed, and detect-sensors can't find them even if they're clearly pwm-supported in Windows. 

Thank you for your attention

---

