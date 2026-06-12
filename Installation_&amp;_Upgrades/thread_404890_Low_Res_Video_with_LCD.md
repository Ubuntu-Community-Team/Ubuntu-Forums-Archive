---
title: "Low Res Video with LCD"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by project606 on 2007-04-09
Follow up to the inability of Ubu 6.06 to sense the correct refresh rate on LCD.  This install was an experiment using an old Dell GX150 with a CRT.  When switched to the LCD it failed to sense the change is refresh rate from 85Hz to 60Hz as does windows on the same PC and monitor (dual boot).   The Ubu install reverted to a 640x480base VGA on the LCD instead of a selectable choice between 1280x1024 or 1024x768 as available with Windows on either the CRT or LCD.


On examining the xorg.conf file (my first ever command line foray into Linux) is shows the correct driver for 82815 Dell/Intel  on-board graphics chipset.  The upshot of all this is that Ubu6.06 seems to set the video res/refresh to the monitor used in the initial install and sticks there. Perhaps there is some way to insert a different line in the xorg.conf to change the refresh rate and resolution without reinstalling Ubu6.06 on the same machine with the LCD attached instead of the CRT.  


Is this inability to sense and adapt to a different display a standard condition with Ubuntu linux?  Can anyone suggest how to approach modifying the xorg.conf to suit the 19" LCD or should I just reinstall the OS?


How about a dialog in the preferences menu asking not just the resolution but the type of display? 

Bill C
Indiana

---

