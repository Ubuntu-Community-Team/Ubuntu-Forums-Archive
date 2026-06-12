---
title: "screen size dissapears"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by twopeak on 2007-12-27
hello
I've finally updated from .04 to the last version.
But now when I start up, my screen is too small for the whole desktop. So when push my mous against the bottom of the screen, then it scrolls down to show a panel, nd the same when I go up.

I can move my screen to open system>admin>screen and then change the resolution to something that works...

it might be a problem related to an nvidea card? I'm using a compaq S720 screen (it isn't listed in the ubuntu options, so I chose S710)

how do I make this change of resolution stay after I restart the computer?

---

### Post by NilsE on 2007-12-27
Try editing /etc/X11/xorg.conf and change the 

Section "Device" > driver to NV or nvidea and see if that helps.

Another alternative is to rename the xorg.conf to something like OLDxorg.conf so it thinks it is not there and tries to rebuild it when you reboot.  If that fails you can always rename it back.

Type gksudo nautilus in a terminal and then navigate to the /etc/X11/xorg.conf file.

---

