---
title: "Unable to log in after installation"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by gos on 2007-11-24
I just installed 7.10 desktop and initially got a MP-BIOS 8254 error when booting up.  I re-installed using a noapic parameter (picked up in other thread) and now the warning is not appearing but 
after I log in I get the desktop (white borders at top and bottom) for 2-3 seconds, then a black screen for 2-3 secs and then the login prompt again.  I tried the livecd and the alternate version, with/without the noapi and nothing changed - I always wind up in login prompt. 
I´m running a 3 year old PC with around 200 gigs free space so lack of space is not the problem.  Could this be related to graphics card maybe? Any pointers/help appreciated  since I threw out my Windows XP and cant use my computer :-)

[solution]
edited /etc/X11/xorg.conf and replaced ati with vesa !!!

---

### Post by Pumalite on 2007-11-24
Memory. graphics, chipset, processor?

---

