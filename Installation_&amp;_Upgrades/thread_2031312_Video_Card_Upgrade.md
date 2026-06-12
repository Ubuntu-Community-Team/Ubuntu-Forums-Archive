---
title: "Video Card Upgrade"
date: 2012-07-21
forum: Installation &amp; Upgrades
---

### Post by stokan on 2012-07-21
Good day brillant people :D

I am having a little bit of an issue with my Ubuntu install (in my Windows partition ATM) and I seem to have come to a dead end.  My EVGA GeForce 280 died on me and I upgraded to the 570.  After upgrade, X was essentially useless, as the mouse appeared pinned to the left side of the monitor and graphics were highly distorted.  As such I got the drivers for the 570 and attempted an upgrade.

-Moved drivers onto disk
-Booted into recovery
-Swapped to Terminal 1 and stopped Lightdm
-Ran the drivers, it complained about unable to run startup script.
-Tinkered with that for a bit was unable to resolve so I installed it anyways

Now when I boot into Ubuntu, the graphics session is just a blinking cursor.  I have tries some other steps found through searching the forums such as deleting X-Conf and a few others that I regretfully can't remember at the moment (had to leave town for a few days).  

At this point I am tempted to move important files off to another partition and nuke and pave the Ubuntu drive.  However, before I do that I thought I would ask for any suggestions?

My thanks in advance.

---

### Post by soldier1st on 2012-07-22
did you try to purge the previous nvidia driver? try this  When you see the log in screen, hit CTRL+ALT+F2, enter your login name and password, then run these commands in the terminal:   Code: sudo apt-get purge nvidia* sudo dpkg-reconfigure -phigh xserver-xorg      .This is one issue that linux has not fixed yet. Windows usually has no issue. but when it does, it is easy to fix.

---

### Post by stokan on 2012-07-22
Thanks for the response, tried that and it purged a number of packaged and still goes back to the blinking cursor.  Should I run the new driver install again?

---

### Post by stokan on 2012-07-26
I ended up giving up and wiping it :(

but its working again :)

---

