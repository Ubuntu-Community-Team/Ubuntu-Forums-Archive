---
title: "Desktop Activity Settings leads to blank screen"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by dajashby on 2010-04-27
I've upgraded from Karmic 64-bit kubuntu to the RC build for Lucid.  I have two pcs connected to two monitors via an Aten dual head KVM switch.  With the new release I only get a background slideshow on one monitor.  I can get an image on the first monitor by right clicking and choosing Next Wallpaper image, but it never changes.  When I select Desktop Activity Settings both monitors go entirely blank, except for the mouse cursor.  The Display Multiple Monitors screen has ticks in all the multiple monitor checkboxes and Identify All Displays correctly identifies both monitors.

---

### Post by GnuSense on 2010-05-05
I'm getting the same thing on a fresh install, I've never had a virus in 5 years of daily Linux use and don't think that is an issue.  Selecting Desktop Activity Settings causes the screen to go blank.  Actually, what it is apparently doing is killing the plasma desktop, hence the context menu.  I was able to restore the session by starting a konsole terminal and typing:

plasma-desktop&

---

