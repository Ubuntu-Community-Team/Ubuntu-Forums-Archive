---
title: "ubuntu-artwork splash?"
date: 2008-07-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by TheForkOfJustice on 2008-07-30
I'm in Hardy now but maybe someone can tell me if this is happening in Intrepid.

Open /usr/share/gconf/defaults/16_ubuntu_artwork in gedit

Notice the first line:

/apps/gnome-session/options/splash_image splash/ubuntu-splash.png

If I'm not mistaken, this refers to the splash (the one that used to load when Gnome started) that was removed from Ubuntu for some time now.

I'm just wondering if the reference should be removed since I don't think the gnome splash is coming back.

---

### Post by ccw on 2008-07-30
X:~$ cat /usr/share/gconf/defaults/16_ubuntu-artwork 
/apps/gnome-session/options/splash_image splash/ubuntu-splash.png
/desktop/gnome/interface/gtk_theme      NewHuman
/desktop/gnome/interface/icon_theme     Human
/desktop/gnome/peripherals/mouse/cursor_theme   Human
/apps/metacity/general/theme	NewHuman
/apps/gnome-screensaver/theme screensavers-ubuntu_theme

---

