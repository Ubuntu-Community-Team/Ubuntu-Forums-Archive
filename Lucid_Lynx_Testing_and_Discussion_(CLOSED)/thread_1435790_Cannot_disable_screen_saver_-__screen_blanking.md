---
title: "Cannot disable screen saver -  screen blanking"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rthawkcom on 2010-03-21
I cannot stop screen blanking from kicking in.  Very annoying!  Here is what I have:

/etc/X11/xinit/xinitrc

setterm -blank 0 -powersave off -powerdown 0
xset -dpms
xset s off
xset s noblank


I later then tried to add:

~/.xinitrc

setterm -blank 0 -powersave off -powerdown 0 
xset s off

It still blanks the screen!  NOTHING!  Nothing works!   Any ideas how to stop this?

---

### Post by collinp on 2010-03-21
If you're running GNOME, open "Power Management Preferences" (System -> Preferences -> Power Management Preferences). Then, change the time in the drop-down menu next to "Put display to sleep when inactive for:" to "Never".

---

