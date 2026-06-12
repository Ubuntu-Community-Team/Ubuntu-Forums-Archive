---
title: "XP erased my Grub"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by ddwyer50 on 2005-09-06
Hello all,

I have just installed Ubuntu and everything installed great.  However, I just put in my Windows XP CD and booted from it and all of a sudden my Grub boot menu is gone. I only have one hard drive, and I installed Grub on my MBR. Hopefully there is a way to recover Grub without reinstalling the entire system. Help!

Thanks,
Dennis

PS - I also have a SATA 2.0 HDD. Any way to make sure I am getting the max transfer rate I can out of this drive?

---

### Post by bored2k on 2005-09-06
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)
** /dev/hda does not work, try /dev/hd0

Max transfer ? Enable DMA
[http://ubuntuforums.org/showthread.php?t=30949&highlight=hdparm](http://ubuntuforums.org/showthread.php?t=30949&highlight=hdparm)

---

### Post by aleksi on 2005-09-06
How is it possible to follow those instructions, if I cannot boot ubuntu because windose wiped away my grub??

This might sound stupid but I really dont know and ubuntu livecd don't seem to work in that laptop.

---

### Post by bored2k on 2005-09-06
[QUOTE=aleksi]How is it possible to follow those instructions, if I cannot boot ubuntu because windose wiped away my grub??

This might sound stupid but I really dont know and ubuntu livecd don't seem to work in that laptop.[/QUOTE]
 Read it carefully, this applies to the Installer disc, no the live on (although it works there too).
[Q: How to use Ubuntu Installation CD, to gain root user access?](http://ubuntuguide.org/#gainrootinstallcd)

---

