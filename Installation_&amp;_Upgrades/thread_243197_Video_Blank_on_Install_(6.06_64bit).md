---
title: "Video Blank on Install (6.06 64bit)"
date: 2006-08-24
forum: Installation &amp; Upgrades
---

### Post by agisfox on 2006-08-24
I'm attempting to install Ubuntu 6.06 (AMD 64bit version) - it goes through initial bootup fine, but after startup where I think it's starting up the Xserver the monitor goes blank and seems to lose the signal.

Video card is an ATI AIW x800 XT; the support documentation I can find suggests I should be getting at least 2d support but I couldn't find the X.org package version the install CD uses or any direct "6.06 has <x> support for x800 XT cards" docs.

Edit Note:
I ran the CD Check from the menu and the CD checked out ok.  Also, it didn't matter if I it the boot/install option or the safe video boot option.

---

### Post by orb9220 on 2006-08-24
You might try the 386 version as I have read others having problems with 64-bit version.

---

### Post by agisfox on 2006-08-24
After looking further, it appears that the 6.06 64bit CD image sets up the x800 series cards with an ATI driver that doesn't support the x800 series.

(Though I had trouble finding the docs, and this could be out of date or just wrong, it seems to suggest that it's using the driver here
[http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html](http://xorg.freedesktop.org/releases/X11R6.7.0/doc/radeon.4.html)
which doesn't list x800 series cards at all)

After some fiddling I can get to a console, kill X and GDM (which stayed running, along with some of GNOME) and try and reconfigure X, but it didn't work - seemed like it was still booting the ATI driver instead of vesa.

I tried both the suggestions I ran into -
[http://www.ubuntuforums.org/showthread.php?t=242859](http://www.ubuntuforums.org/showthread.php?t=242859)
[http://www.ubuntuforums.org/showthread.php?t=240038&highlight=server+ATI](http://www.ubuntuforums.org/showthread.php?t=240038&highlight=server+ATI)
but they seem to require rebooting, which misses the point when you're running off of RAM because you need to install.

---

