---
title: "Laptop, ATI Mobility 3 video not working"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by ontwowheels on 2008-05-20
The install of 8.04LTS was going swimmingly until, when I assume, X started, then the screen was a mess and unuseable.  I dropped back and punted, did a new install and selected the safe graphics option and all went well.  Anytime I try to change the configuration to not use the Vesa complient (something like that) video driver the screen goes south again.

I have done several searches and haven't found much of a fix yet, to be able to use a non generic driver.  Years ago I have run other distros of Linux on this laptop without the issue.

Dell Inspiron 5000e
ATI R128 Mobility 3 chipset.

---

### Post by dstew on 2008-05-20
Boot in recovery mode, and use the xfix option to get a useable desktop. Use Update Manager to make sure your system is up to date. Then, check System --> Administration --> Hardware Drivers to see if you have a restricted driver available. If so, enable it. Reboot. If your screen has low resolutiion, hit alt-F2 and enter ```
gksudo displayconfig-gtk
```That will allow you to fine tune your window manager for your monitor. Be sure to use the wide screen option if you need to set up a generic display, and you have a wide-screen LCD.

---

### Post by ontwowheels on 2008-05-20
> **dstew said:**
> Boot in recovery mode, and use the xfix option to get a useable desktop. Use Update Manager to make sure your system is up to date. Then, check System --> Administration --> Hardware Drivers to see if you have a restricted driver available. If so, enable it. Reboot. If your screen has low resolutiion, hit alt-F2 and enter ```
gksudo displayconfig-gtk
```That will allow you to fine tune your window manager for your monitor. Be sure to use the wide screen option if you need to set up a generic display, and you have a wide-screen LCD.

Thanks.  I can get a usable desktop by struggling through Applications/Screens and Graphics and setting the graphic card back to vesa compatiable and rebooting.  Loaded all updates/upgardes through the package manager.  The only restricted drivers agailable are for my pcmcia WAN card.

---

