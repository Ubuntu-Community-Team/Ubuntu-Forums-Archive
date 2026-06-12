---
title: "[SOLVED] Problems with GRUB loading on my internal HDD after using Hardy on my extern"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by Berean on 2008-07-24
Hi, 

I've got 8.04 dual booted on my wife's Vista laptop, but also have just installed Hardy upon my external 80GB HDD so I can take files and OS with me to work etc.  However, when at home, after each time that I've booted from the external HDD when I attempt to get back into my internal HDD I find that I have to reinstall GRUB.  This is frustrating - but achievable - but I don't want to boot from my external HDD somewhere away from home and then find that I have to reinstall GRUB on someone else's PC.  If for no other reason than I think it rude to mess with another's OS.  Any ideas?  Thanks in advance for your help.

---

### Post by dstew on 2008-07-24
When you plug in your external hard drive, do you go to the BIOS and tell it to boot from that drive? Do you have the grub boot loader on both the external and internal drives?

If you want a self-contained system on your external drive, grub needs to be in the MBR of that drive AND whatever system you put it on has to be re-configured in BIOS to boot the external drive. If you have it this way, you should not have to re-install grub on the internal drive in order to boot the external drive.

---

