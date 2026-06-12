---
title: "Blank console screen after karmic install or upgrade"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by boscorama on 2009-11-19
I have an issue where the console is nothing but a blank screen after grub hands off screen management to the kernel.

This is occurring in both ubuntu server (both a fresh install & an upgrade from Jaunty) and a kubuntu upgrade from Jaunty.

This only happens when I have a vga=NNN option in the kernel command line.  If the vga option is missing the console is visible but is in the basic console mode (80x24 IIRC).

Interestingly, it's not related to grub or grub2 as the upgrades still use grub afterwards and the fresh install uses grub2.  Either way the symptoms are the same.

Additionally, the fact that the two server-based versions experience this indicates that it isn't an X problem since neither has X installed.

I have also experienced this when the installation is performed on a physical machine and with the install/upgrade performed as a guest within VMware Player.

Any thoughts?  Others have seemed to experience this problem but have attributed it to some "modeset" in Intel graphics.  None of the scenarios I've encountered have Intel graphics. 

TIA

---

### Post by sb37 on 2009-11-30
Hoi,

I can confirm the behaviour described above. Any of the vga=normal, nofb, vga=771 options don't seem to help.

I've installed all kinds of ubuntu on an HP PC with built-in INTEL graphics. Installation completed succesfully. I can log-in and do stuff. No problem.

Then I switched off the built-in gfx and inserted a CT 69000 card. I need this card because it has a touchscreen attached to it.

I've even tried the server edition to rule out any X stuff. Same thing happens as with all the other Ubuntu tastes. I see the Starting prompt and then the screen blanks out. Grub shows up fine...

Funny thing is that a lot of other distros (Knoppix, Fedora, CentOS) work fine. But I would really like to use Ubuntu

---

### Post by Regenpak on 2009-12-10
I'm struggling with Grub2 as well. I'm trying to get a console with the much-loved vga=791 option in Karmic, but I either get a 720x400 display with the above crap 80x24 resolution or a proper scanrate but with a blank (or black, if you will) screen. It's like the fonts for this resolution are gone. Most annoying. I'll do some more searching and reading...

---

### Post by Reardon on 2009-12-20
I only have the problem in the 2.6.31-17 kernel update.  It also occurs with the 2.6.32 kernel (from ppa).  For whatever reason -16 is fine.

Note that my console is blank and/or scrambled at all times, not just boot.  I cannot use Ctrl-Alt-F1 to bring up a console.

---

### Post by ridix on 2009-12-20
Today, i updated the kernel **only** (i have selected in update manager dialog) to version 2.6.31-16 and GDM / Gnome will not start. In 2.6.31-14 kernel version is ok.

---

