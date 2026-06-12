---
title: "Installed 10.10, no Xorg.conf and issues trying to make one..."
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by lbox on 2011-01-31
After many years of being a Red Hat/Fedora/Mandrake user, I just stood up a little box with Ubuntu 10.10 last night on this machine:
 
Dell Optiplex GX200 (beige)
P3-933MHz
512MB PC800 RAMBUS RAM
16MB Matrox G450 Dual Head PCI card.
Adaptec 29160 U160 SCSI card
18GB Fujitsu U160 SCSI drive
Generic CDRW drive
 
After first login, I notice that screen redraws are HORRIBLY slow and I figure that Xorg is probably using a generic VESA driver. A quick trip to /etc/X11 turned up empty. A trip here to search for an answer said that I should drop to shell via recovery console and run X and have it configure itself to create a config. Fine, nothing I don't have to do with my FreeBSD machines except that I can't get the recovery console to come up without X running. I go into a console vial CTRL-ALT-F1 and kill the X process and, lo and behold, X restarts itself after being killed (-9 option). This is ANNOYING. How in the world am I supposed to build a new config if I can't kill off X OR simply boot to a command line login? Tel/init 3 doesn't do it either and I don't see an /etc/inittab file to set a runlevel at boot.
 
How am I supposed to set this up with the correct driver so my desktop doesn't look like a slideshow every time I drag a window or scroll?

---

### Post by slooksterpsv on 2011-01-31
[http://www.matrox.com/graphics/](http://www.matrox.com/graphics/)

I would install the Linux drivers from there, or see if Additional Drivers/Hardware Drivers can find it for you.

---

### Post by lbox on 2011-02-01
> **slooksterpsv said:**
> [http://www.matrox.com/graphics/](http://www.matrox.com/graphics/)
 
I would install the Linux drivers from there, or see if Additional Drivers/Hardware Drivers can find it for you.
 
well... the mga driver included with Xorg is typically what I use for my matrox cards under Linux and FreeBSD (I have another G450 and a G200 in service now), and thats what I'd like to use as it's quite good and has pretty much everything enabled, no need to use a 3rd party driver when Xorg's is so good.

---

