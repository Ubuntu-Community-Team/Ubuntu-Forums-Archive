---
title: "laptop upgraded from 11.10 to 12.04, desktop but no taskbar"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by raymondvillain on 2012-05-18
HP notebook computer AMD 64 bit chip, Ubuntu 11.10 worked fine.  Upgraded (using update manager) to 12.04 and when finished booting to 12.04 I see the desktop with all its icons (and they function) but there is no taskbar or "Dash Home" on the left side (or the bottom, top or right side).

How to fix it?

Started recovery console, issued command sudo apt-get install -f but that didn't help.

Any other tricks to try?  Or maybe I should just create the CD and do a clean install.

---

### Post by zvacet on 2012-05-19
Try in terminal 

```
unity --reset
```

---

### Post by raymondvillain on 2012-05-19
Thanks zvacet, but it didn't help.  My desktop icons work, sort of, but a message box opens and says something about Ubuntu has detected an error.

I'm going to try a fresh install.

---

### Post by zvacet on 2012-05-21
You are not alone.I never saw ubuntu spitting errors like in this release.I did reinstall ( always thinking it is my mistake) but same result.I hope this will be solved with updates.

---

### Post by sikander3786 on 2012-05-21
Please take a look at this troubleshooting guide:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Specifically, you need to reset Compiz and install CCSM and see if Ubuntu Unity Plugin, and the other needed plugins, are enabled.

For the other error, if it mentions broken packages or something like that, please get to a Terminal by pressing 'Ctrl + Alt + T' and post the output of these commands:

```
sudo apt-get install -f
sudo dpkg --configure -a
```

If you are unable to get to the Terminal by pressing the shortcut keys, press 'Ctrl + Alt + F1' and login to the tty1 and execute:

```
DISPLAY=:0.0 gnome-terminal
```

---

