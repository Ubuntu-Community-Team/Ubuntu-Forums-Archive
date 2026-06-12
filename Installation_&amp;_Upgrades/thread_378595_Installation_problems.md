---
title: "Installation problems"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by catalin59 on 2007-03-07
I am trying to install Ubuntu 6.06 64-bit version on a computer with Pentium 2 Duo processor, 2GB RAM, 320GB SATA HDD and an nVidia 7300LE video card. The installation process stops with the following message on the screen: 

.
Decompressing Linux...Done.
Booting the kernel.


BusyBox v1.01 (Debian 1:1:01-4ubuntu3) Built-in shell (ash)
enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
#

Sometimes it halts immediately after the "Booting kernel." message and then nothing happens. 

I have no idea what the problem is or what to do next.

---

### Post by wpshooter on 2007-03-07
First make sure that you have checked the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

If you have done this and the verification function reported NO sumcheck errors, then this is probably video card related.

Try using either the safe video mode parameter or try setting your video resolution manually by using the (I think it if the F4 key).

Good luck.

---

### Post by catalin59 on 2007-03-07
I already tried both these suggestions (checking the CD and safe graphics mode). They both fail the same way, immediately after "Booting the kernel." message. I have also ran a memory test and there were no errors. 

i also tried F4 and VGA 640x480x16 mode and I get the same "BusyBox" message. With 1280x1024x32 I just get a blank screen. Does this mean Ubuntu doesn't support nVidia video cards?

---

### Post by andrewabc on 2007-03-09
I have a similar problem. My computer seems unable to start ubuntu. I get to the menu page, but no matter what option I use it freezes or doesn't continue anymore after I select an option. It just goes to a blank page or stops at "booting the kernel". 
It couldn't even boot memtest iso cd.
I tried the ubuntu cd iso and then used the dvd iso. Same problems.

---

