---
title: "Screen Resolution"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by iampriteshdesai on 2008-06-25
I installed Ubuntu today, but the screen resolution is around 600-400. Previously when I had installed Ubuntu it gave correct option of 1024-786. Now there isn't even an option for doing it. Plz help. I am using Hardy

---

### Post by avtolle on 2008-06-25
Have you installed the correct video drivers?

Also, on screen resolution, from the console```
gksudo displayconfig-gtk
```which will allow you to scan for your monitor, and if found, select it and apply. The graphics card tab will also allow you to ascertain whether your graphics card is found, again if not, search and if it is there, select it and apply the change.

---

### Post by Mark Phelps on 2008-06-25
I may be unique in this, but in the four machines that I installed/upgraded with Hardy, not a single one came up with the full screen resolution.  Not one!  And, all had been using Ubuntu 7.04 or 7.10 with full resolutions without problems.

If the screen resolution panel is not giving you the full resolution, that probably means it did not detect your video card and/or monitor correctly; at least, that's what happened to me in all the cases.

Use the configuration command previously suggested and, if it doesn't find your card or monitor, just select a generic one.  I used 1024x768 LCD (or flat panel?), and it worked fine for all my machines after that.

BTW, my experience with trying to force resolutions using modelines and display settings in the xorg.conf file indicates that these are no longer used in Hardy.  The configuration command now appears to be the way to go.

---

### Post by avtolle on 2008-06-25
@Mark Phelps, exactly to a limited degree. When using the command I posted earlier, a new /etc/X11/xorg.conf file is generated. If you are interested in seeing what happens, open one ```
cat /etc/X11/xorg.conf
``` and take a look. I was surprised what was added to the "stub" file in my systems.

---

### Post by iampriteshdesai on 2008-06-26
I tried it guys but doesnt work. I got an option to select higher resolution but it didnt come into effect. Guess I ll have to reinstall Ubuntu. Thanx!!! though

---

