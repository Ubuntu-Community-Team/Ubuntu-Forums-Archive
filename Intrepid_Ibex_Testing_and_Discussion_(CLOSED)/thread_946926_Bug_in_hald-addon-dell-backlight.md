---
title: "Bug in hald-addon-dell-backlight?"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dark_phantom on 2008-10-13
I upgraded to 8.10 from 8.04 via 'sudo update-manager -d', noticed it had a few problems towards the end mainly with nvidia driver and not doing the cleanup.  I ended up doing a ' sudo dpkg-reconfigure -a' and a 'sudo apt-get autoclean'.  But even before that I noticed that after logging in the brightness was being increased automatically.  If I bring it down manually, everything freezes and the hald-addon-dell-backlight process consumes much of the cpu.  I can't do anything after that, menus don't work and the keyboard doesn't respond.  And even though the process either goes to sleep or stops (not sure if this happens or not) I still can't do anything but ctl+alt+bkspc to log back in.

Any ideas if this is a current bug with the beta version?

PS. I constantly get the updates whenever they're available.

---

### Post by wgrant on 2008-10-13
There appears to be a kernel bug which causes the brightness keys to never appear to be released, triggering key repeat. gnome-power-manager then somehow permanently steals focus. One can generally recover normal focusing abilities by switching to a VT (Ctrl+Alt+F1) and back (Ctrl+Alt+F7).

---

### Post by dark_phantom on 2008-10-13
Thanks, that helped.  I assume this will get fix by the final release.

---

