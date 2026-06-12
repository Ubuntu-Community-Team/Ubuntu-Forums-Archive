---
title: "SOLUTION:  LiveCD hangs on desktop load"
date: 2007-03-13
forum: Installation &amp; Upgrades
---

### Post by FrozenFOXX on 2007-03-13
Was over in the Kubuntu IRC channel discussing this and decided it'd be a good idea to make a forum thread here about my issue I recently solved in case anyone else experienced the same thing.  After much scouring I didn't find any information on this issue so hopefully it will help someone.

With the 6.10 Kubuntu installation disc (but also with others such as Dapper Drake) either under normal or safe graphics mode the LiveCD would hang as soon as the desktop background loaded.  The mouse cursor would be there and movable but the system would NOT respond to keyboard input of any kind so you couldn't get to a terminal to fix it.  After much playing around the following method works for me and hopefully others.

I determined that the issue was the autoconfiguration of X.org not properly detecting my graphics card driver (in my case a BFG GF7800 OC which it improperly selected the "nv" driver for).  We can modify the xorg.conf from single user mode to change it to a more appropriate graphics driver and then resume starting the graphical goodness.

1)At the boot menu press F6 for Other Options
2)At the end of the line put "single" by itself and press enter to boot
3)It will drop you to a text prompt.  From here we can fix the xorg.conf
4)Type "cd /etc/X11/"
5)Type "ls"
6)You should see in the file list "xorg.conf." This is the file we are to modify.  Use your favorite text editor to open it (many enjoy nano which would be "nano xorg.conf" but I personally like vi which is "vi xorg.conf")
7)There will be MANY lines here.  Fortunately we're just looking for one.  It will say, "Section  "Device"." The Identifier will probably read something familiar as it is the name of your graphics adapter.  Just below it will be a line that says something akin to "Driver  "nv" or similar.
8)Remove whatever word is between the quotations next to Driver and type "vesa" which is a default graphics driver compatible with nearly everything on the market.
9)Save the file and exit (in vi this would be ":wq" from command mode)
10)At the command prompt type "startx" and enjoy.

---

### Post by mandible on 2007-03-13
Excellent I will try this out when I get home, you posted this 5 minutes after my post about a similar issue though I haven't seen my mouse icon on screen but this may help.

---

