---
title: "Installation Edgy+ATIX800+Asus P5VDC-X problem"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by SLOB on 2007-01-26
Hi!

Im trying to install Edgy on my computer (Asus P5VDC-X with VIA PT880 Pro-chipset) but I just cant seem to get it to work. First I installed on a SATA disk, co-existing with XP. But I couldn't get Grub to recognize my USB-keyboard, so I opted for installation on separate harddrive. Now I got Ubuntu (using alternate ISO) installed on its own PATA-disk, but I could only get into Gnome for  a few minutes when a freeze would occure (mouse pointer and screen just froze). Then I was pointed by a friend to the fact that ATI doesnt work well with Linux, so he gave me the advice to update the drivers as follows:

> 
(safe mode)
sudo apt-get update
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv 


Now, however, it boots straight into a black screen. I do see the Ubuntu load screen, but then everything is black.

Help?

Cheers,
SLOB

---

### Post by SLOB on 2007-01-26
I've now managed to get into Gnome, but I still have the freeze problem. System will freeze after a random, but very short, period of time.

*sigh*

---

### Post by SLOB on 2007-01-26
Tried using Dapper, but same problem there. More or less instant freeze upon Gnomestart.

---

### Post by SLOB on 2007-01-27
Nobody? Dang, I'll just have to keep using XP then *sigh*

---

### Post by philipacamaniac on 2007-02-17
DOH!

I have the same motherboard, and the same EXACT problem with both Edgy and Feisty (as of Herd 4). That's why I'm running Dapper with my own custom kernel.

I believe the problem is improper support for the VIA PT880 Chipset. According to this thread: [http://ubuntuforums.org/showthread.php?t=190341](http://ubuntuforums.org/showthread.php?t=190341) the define directive for the PT880 should be 0x0308 and not 0x0258.

In other words, I think that Edgy and and Feisty, as of yet, are not compatible with the ASUS P5VDC-X motherboard, when using an AGP card (and in these two cases, when using an ATI AGP card).

---

