---
title: "login screen huge"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by yon2501 on 2008-04-24
I just updated to 8.04 and configured my screen resolution unfortunately for some reason my login screen is now so large that i can only see the top left corner. also nvidia settings manager which i would normally use for resolution control will not start.

---

### Post by thasan on 2008-04-26
I get the same after the upgrade from 7.10 to 8.04.  The login prompt is close to the bottom right corner.

---

### Post by meimato on 2008-04-26
Check the section "**Screen**" of your xorg.conf, subsection "**Display**".
Look for **[COLOR="Red"]Virtual[/COLOR]**, and change vertical and orizontal resolution to match those you desire; in case it is not sufficient, also delete every Modes in Screen section and Modelines in Monitor section which are above your desired (maximum) resolution.

---

### Post by yon2501 on 2008-04-26
I just fixed it on my machine turns out i had to reinstall nvidia-settings and once i did that i was able to get the resolution right. i dont know if you have an nvidia thasan but this worked for me.

---

### Post by thasan on 2008-04-26
Thank you both, I tried reinstalling nvidia-settings after removing it, but didn't help.
So, changed the virtual from 1920x1200 to my monitor's default 1680x1050 in xorg.conf.  It solved the problem.:)

---

### Post by User20202 on 2008-04-27
Thanks to you and yon2051. I also had the same problem and also tried redoing my nvidia-settings with no luck. I then changed my Virtual from 1600x1200 (which worked fine in 7.10 even though my normal desktop is 1024x768) to 1024x768, did a CNTL+ALT+Backspace and everything then worked perfectly. I did not have to go in and delete the higher level modes.

---

