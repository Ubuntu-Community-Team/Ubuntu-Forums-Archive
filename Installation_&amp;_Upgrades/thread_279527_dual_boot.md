---
title: "dual boot"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by Intruder on 2006-10-18
hi guys little advice needed running an AMD 3500+ with XP installed on a sata drive, i want to installed Ubuntu desktop on to another drive to dual boot other drive is a PATA drive is this possible and how hard is it, im a newbie to linux so please be gentle....

Int

---

### Post by Kateikyoushi on 2006-10-18
Yes it is possible and isn't hard to set up. Unfortunately the graphical instller does not let you select on which disks mbr to install grub this combined with some motherboard's sata pata boot order selection can cause some trouble.

In my opinion the safest way is to disconnect the windows sata drive and install ubuntu on the pata disc set bios to boot from the pata disc, connect the sata disc and set up the bootloader in ubuntu to load windows.
Then you can select at startup which os to boot.

This way it takes 5 minutes longer but probably the easiest way to install.

---

### Post by gn2 on 2006-10-18
> **Intruder said:**
> hi guys little advice needed running an AMD 3500+ with XP installed on a sata drive, i want to installed Ubuntu desktop on to another drive to dual boot other drive is a PATA drive is this possible and how hard is it, im a newbie to linux so please be gentle....

Int

This may help: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

There's a potential problem with dual-booting, which is that Ubuntu's bootloader may want to install it's self over your Windows Drive's Master Boot Record.
This should be avoided if at all possible, by unplugging the Windows drive during Ubuntu install.

Basically to answer your question it is possible, and it is remarkably 
simple, so long as you accept the default install options.

---

