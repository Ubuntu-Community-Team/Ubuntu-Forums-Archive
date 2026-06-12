---
title: "Ubuntu 6.10, no graphics."
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Mavrick3020 on 2006-11-06
Alright, though I've used Unix before, I'm a Linux noob so please bear with me.  Anyway, here is my problem.  I'm using a GeForce 6600 on an ASUS A8V with an Athlon 64 3500+.  When I went to use the live CD to install, whenever I got past the splash screen, my monitor(An LG Flatron L19175) blinked out and showed an out of frequency message.  Figuring the system has somehow set my resolution too high, I used the VGA option and used the stardard 800X600.  This worked fine, except for the fact my mouse pointer wouldn't render, even though I could still use it to click, mouseover and make selection boxes, but that's another problem.  

My main problem is this:  After installing, I get the the splash screen and my monitor blanks out again.  I realize I probably have to build the nVidia drivers in the OS, but I can't see anything to do that.  So, here is my question.  Is there anyway to change my boot command line so that I boot into 800x600  like I could on the live CD?  If not, is there any other solution for this problem?

---

### Post by taurus on 2006-11-06
Boot to recovery mode from GRUB menu, and at the prompt, reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
```

---

