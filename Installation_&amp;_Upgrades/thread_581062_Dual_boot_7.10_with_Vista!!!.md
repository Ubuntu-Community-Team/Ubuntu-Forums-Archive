---
title: "Dual boot 7.10 with Vista!!!"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by feelinggood on 2007-10-19
Ok, I have done this before on my old machine with the grub installed, and had no problems.  My question is I have a new system.  An HP media center 2.8ghz processor, 3 gigs of ram and a 500gig harddrive.  All I have is recovery DVD's if it gets screwed up.  How can I dual boot so that vista comes up first??   Don't want the whole system messed up if something goes wrong.  Thanks

---

### Post by Luke771 on 2007-10-19
Edit /boot/grub/sources.lst and move the Vista entry on top of the first Ubuntu entry?

---

### Post by Zacha on 2007-10-19
Well... you could install ubuntu and tell it not to install GRUB to MBR but the partition istead and then use EasyBCD to put it in Vista Bootloader. (This was how I planned to do... [but something happened](http://ubuntuforums.org/showthread.php?t=581052))

---

### Post by Gooorn on 2007-10-19
Just shrink your Vista partition (you can do it safely from Vista) and Ubuntu installation will do everything else automatically. I just bought a new Toshiba laptop and this procedure worked for me flawlessly. It will also leave Toshiba's "system" partition intact for your eventual use.

---

### Post by sean_gilmore on 2007-10-19
How did you install the GRUB though, I want to know before i try anything, i have a toshiba as well but it came with vista and all i have is the recovery disks.. I'm just worried because last time I attempted installing i accidentally wiped out my whole drive for ubuntu, and i cant do that again, im not skilled enough to only use it as of yet... heh.

---

