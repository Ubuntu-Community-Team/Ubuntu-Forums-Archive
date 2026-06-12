---
title: "Gutsy upgrade -- menu bar disappears"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by crhumber on 2007-10-20
I just upgraded to Gutsy from Feisty this morning, using the recommended upgrade method.  Everything seemed to go well during the upgrade, but now when I startup my menu bar disappears.  My menu bar is at the top.  It shows up when it first starts, but I get a message about a problem with the Gnome mixer applet.  The screen then blinks a few times and the menu bar disappears.  I am having some other minor but expected problems that I need to fix, but I need to figure out how to get my menu bar back.  Can anyone help?

---

### Post by matthew.lns1 on 2007-10-20
Try typeing "gnome-panel" in the terminal.

---

### Post by crhumber on 2007-10-20
I tried that and it does the same thing.  The terminal prints out several errors, but here is the last one:

** (gnome-panel:7533): WARNING **: panel-applet-frame.c:1278: failed to load applet OAFIID:GNOME_MixerApplet:
Failed to resolve, or extend '!prefs_key=/apps/panel/applets/applet_2/prefs;background=pixmap:27263143,-1,-1;orient=down;size=x-small;locked_down=false
gnome-panel: symbol lookup error: /usr/lib/gnome-panel/libclock-applet.so: undefined symbol: gtk_widget_set_tooltip_text


Is there something that I can temporarily disable so I can get this going?  thanks

---

### Post by matthew.lns1 on 2007-10-28
Could you post all the errors?

---

