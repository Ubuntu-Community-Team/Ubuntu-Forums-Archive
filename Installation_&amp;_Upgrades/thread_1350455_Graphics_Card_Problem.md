---
title: "Graphics Card Problem"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Wizard_xrc on 2009-12-09
Hi everyone ! I am trying to install Ubuntu on my desktop pc and there seems to be a graphics card problem. 
Motherboard is **Asrock p4i65gv** and and the graphics card is a **geforce FX 5500.**

The problem is on the first installation screen, when i choose "install Ubuntu", it seems to start loading the setup, but after a while it stops and i see vertical white lines on the screen. Note that this happens even with safe graphics mode, or even the "Try Ubuntu first" option of the setup.

My motherboard has an on-board graphics card, so i tried to remove my geforce, and run the setup again, which went good. Then, with Ubuntu installed, i installed the geforce again, but what happens is this : when i connect the monitor to the onboard card and select it as primary display from bios, Ubuntu starts but displays an error message stating that there's an error in the configuration file and puts me into low-graphics mode. When i switch the primary display to nvidia from bios, and plug the monitor to nvidia as well, it shows the same black screen with vertical white lines and cannot get Ubuntu started.  :(

I 've Googled it a lot and seen that there's a lot of deal going on with nvidia cards, and kinda got confused. Any suggestions ? Thanks in advance...

---

### Post by darkod on 2009-12-09
Leave it set on your Nvidia card, boot and select the recovery mode entry from grub menu. Try what I have described in post #2 here:
[http://ubuntuforums.org/showthread.php?t=1350430](http://ubuntuforums.org/showthread.php?t=1350430)

---

