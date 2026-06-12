---
title: "Problems with Live &amp; Install for Ubuntu 8.04"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by Arieder on 2008-10-04
Hi, recently I tried to run Ubuntu 8.04 on my desktop (that I have previously installed Ubuntu 7 on successfully). As soon as I try to run it live I get to the black screen with messages about ata0. Please remember that I have had no problems with Ubuntu 7.

Specs:
Intel Core2 Duo Processor
40 GB Western Digital Hard Drive
4 Gigs of ram
ATI Video Card

Any help would be appreciated.

Thankyou.

---

### Post by Arieder on 2008-10-05
Guess I should also mention that instead of going to live it goes into Busybox.

---

### Post by coltrane on 2008-10-06
Try 'all_generic_ide floppy=off irqpoll pci=nomsi' at the boot options of the install/Live screen.
It worked for me.

---

### Post by montyw47 on 2008-10-06
Tried booting Ubuntu 8.04  LiveDVD. Used with my brand new monitor and went to Busybox! Old monitor CRT worked fine 800x600 & 1024x768 (NEC 5Fge). New monitor large screen LCD, native resolution 1680x1050 (60hz only). It is Samsung T220 22" LCD connected w/DVI cable from nvidia GeForce FX 5600. What boot parm do I need to enter to get into a graphical screen?

Jack

---

