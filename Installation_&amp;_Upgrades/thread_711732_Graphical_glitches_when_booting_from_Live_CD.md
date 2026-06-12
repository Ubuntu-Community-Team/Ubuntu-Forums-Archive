---
title: "Graphical glitches when booting from Live CD"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by nemesis256 on 2008-02-29
So I'm trying to boot up Ubuntu for the first time on a Mac Pro.  I got to the initial menu, and selected the first option to install or boot Ubuntu.  After that, I got to the loading screen with the orange bar.  After a short while, the bar duplicated itself several times on the screen.  After that probably about 5 screens followed with strange colors and patterns.  The last one was white with some pink/red coloring.  At this point the CD stopped spinning, so I just held down the power button to turn off.  

What could be the problem?  The graphics card in my Mac Pro is a NVIDIA GeForce 7300 GT.  I am using the 32 bit version of Ubuntu.  Would the 64 bit make any difference?

---

### Post by nemesis256 on 2008-03-01
anyone?

---

### Post by nemesis256 on 2008-03-01
this forum moves way too quickly...

---

### Post by dstew on 2008-03-01
> So I'm trying to boot up Ubuntu for the first time on a Mac ProMac Pro is Intel-based, correct? Anyway, the Live CD problem you have is that the graphics driver is not working well with your computer. You can do several things. Try to boot the live CD in Safe Graphics Mode. Try kernel parameters. You can edit the kernel line by pressing F6 at the first menu. Remove quiet splash from the kernel line. You can also add vesa=force or vga=791 to try to get the graphics to work.

If none of this works, install with an Alternate Install CD. It uses a text-based installer. Get it from the Download Ubuntu page, check the box beneath the Start Download button.

---

