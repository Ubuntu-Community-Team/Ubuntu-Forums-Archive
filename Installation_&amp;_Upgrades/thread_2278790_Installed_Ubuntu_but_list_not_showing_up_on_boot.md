---
title: "Installed Ubuntu but list not showing up on boot"
date: 2015-05-19
forum: Installation &amp; Upgrades
---

### Post by verber001 on 2015-05-19
I just installed Ubuntu on my laptop next to Windows 8.1.  I made a partition, setup the boot, and swap areas.  But when I restarted the blank page with the option to boot into Ubuntu doesn't show up.  It just goes straight to Windows 8.1.  I installed under legacy mode.  I disabled secure boot and fast boot.  I still have no luck.  Can someone help me out.

---

### Post by dino99 on 2015-05-19
Look at the 'oldfred' posts into 'general' subforum; there are many answers related to win/ubu dual boot problems.

---

### Post by Bucky Ball on 2015-05-19
Windows 8 is probably installed in UEFI. Try installing Ubuntu in UEFI mode, leave secure boot OFF to do this. 

You can't have one installed with UEFI and the other not. I just installed Xubuntu alongside Win8.1 on my new laptop. Secure boot and fastboot off, legacy mode disabled, install in UEFI (on my system there is nothing else to do, but on yours you may need to designate a UEFI install). Win8 is almost definitely installed in UEFI unless you have installed it manually in legacy. 

I go with 'Something Else' at the partitioning section. Leave any existing Win partitions, choose the existing / partition and /swap for your install (set / to format and, if you have one, also /home to 'USE' but not format, leave everything else), and away you go. Good luck.

---

### Post by oldfred on 2015-05-19
UEFI and Legacy/BIOS/CSM boot modes are not compatible. 
You must totally reboot to switch and you should be able to do that. But a lot easier to have all systems installed in same boot mode. And since Windows is UEFI, install Ubuntu in UEFI boot mode.

You also may have to turn on/off UEFI or CSM boot mode settings in UEFI to switch to system installed in that mode. Sometimes systems auto switch and you can use one time boot key like f10 or f12. See system manual for which key is used by your system. But once you start booting in one mode you cannot change or grub menu will not offer (or should not) to boot system in other mode.

---

