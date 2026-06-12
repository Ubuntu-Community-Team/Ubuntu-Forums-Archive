---
title: "Black screen right after grub, never comes on, fresh install"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by hereitcomes on 2007-11-13
Hi 
I have just install 7.10 i386 on my 2nd hard drive.  Everything's nice on the install side and then after the first reboot, straight after selecting to boot Ubuntu, black screen all the way.  I know it's booting into it ok, I'm just not seeing the screen...
I'm using ATI X1650, tried changing the "vesa" in xorg.conf to "ati" but no change..
any ideas please?

---

### Post by taurus on 2007-11-13
You are saying that **vesa** driver doesn't even work?  Does the LiveCD work on your machine at all?

---

### Post by hereitcomes on 2007-11-13
thanks for replying, yeah the vesa was what was in xorg.conf originally.  I installed using the livecd, and that worked fine...
I've tried "ati", "radeon", and "fglrx" in place of "vesa" and none have worked...

---

### Post by hereitcomes on 2007-11-13
sorry to bump.. but im itching to try gutsy out  ..
really annoying problem. I've seen others just missing the loader, but my screen never comes on after GRUB..

---

### Post by Sheepeh on 2007-11-13
Hi, I appear to be having the same problem with a fresh install of 7.10 (alt cd).  I'm using a x1950Pro, I've done reconfigure and explicitly set VESA, but I don't get a splash or anything after...the hard drive light is going so I think it is working just no display.  Oddly,..if I choose recovery kernel it boots fine in to X and I get scrolling text instead of the splash.  Even the net works fine (it's how I'm typing this right now.

Given I can get in to the system now, where would I look for logs to see what the problem is?

---

### Post by Sheepeh on 2007-11-13
Sorry to reply to my own post, but I just fixed the problem (never let it be said posting doesn't help).

The problem was for some reason, the two DVI connectors on my graphics card aren't both activated properly on normal boot-up.

Turns out I had my monitor in what the card counts as DVI Port 2, and although it didn't faze Windows, or Ubuntu's recovery kernel, it fluffed the main kernel good and proper.  Switched sockets, and BAM; all working fine.

I assume this is a bug that should be logged?

---

### Post by hereitcomes on 2007-11-14
if that's the solution, my card has a VGA and a DVI slot, and I'm using DVI.. I dont have a vga cable or a DVI-VGA adapter handy.. is there any way to tell X to use the DVI port instead?

<edit>
I booted into recovery mode and startx gets me in graphically... why would this be??

---

