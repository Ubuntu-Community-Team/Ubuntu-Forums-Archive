---
title: "upgrade to 9.10 has hidden my desktop"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Timothy Taylor on 2010-02-25
I've just upgraded to Ubuntu 9.10 from 9.04 (??) and now I have no desktop.

The files are still in my desktop directory and right-clicking and selecting "change desktop background" shows the image list, but selecting a background has no effect - I'm stuck with a black screen.

I've tried shutting down and saw the background image flash up for a split-second but on restarting, the desktop is still blank.

Any ideas?

---

### Post by Timothy Taylor on 2010-02-25
Ah-ha!

Just tried System\preferences\appearance\appearance preferences\visual effects

I changed from "normal" to "none" and now have my desktop back.

Whew!

:)

---

### Post by thechaser on 2010-02-25
From the main menu:
System/preference/startup application

Uncheck:
Maximus Window Management 
Netbook Launcher

Launch your terminal:
sudo gconf-editor

apps/nautilus/preferences
Scroll down and check "show desktop" 

This should set you straight.  

Also, you can:
apps/nautilus/desktop

you can check to see home folder, trash, and a few others

---

### Post by ajgreeny on 2010-02-25
I imagine you have an ATI graphics card, are using compiz 3D desktop effects, have a screen resolution greater than 1024x768, and are using the default of 24 bit colour.  Am I correct?

If so, and you really want compiz running, you can either use a lower resolution, probably not a great idea on a large screen, or as I have done, you can manually edit xorg.conf to run the system at 16 bit colour.  It's a bit of a cheat, and there are still a few graphics problems with movies showing slight visual lines in the screen, but "compiz-switch" is available to get rid of compiz when needed and then bring it back, all with a single click.

The easiest way, of course, is just to stop compiz from running, and accept a 2D desktop.

---

