---
title: "Disabling spurious mouse gestures."
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Rob Landley on 2006-06-29
Ever since I upgraded to 6.06, mouse gesture support has been stuck on for the entire KDE desktop.  It switches window focus in the toolbar, switches tabs in Konqueror, scrolls my kterm windows back up...  It does this intermittently, with no pattern I've been able to detect, but it's _really_annoying_.  Despite the documentation, I don't have to hold down a mouse button to trigger it, it just triggers itself randomly.

I tracked down how to disable tap-to-click in my touchpad (edit the config file and add "option maxtaptime 0" which would be nice if you could control that through the "control panel" clone).  That works fine, but it didn't make the spurious gestures go away when I move the mouse cursor around my desktop.

I tracked down how to disable mouse gestures in the KDE control panel (system settings -> regional and accessability ->input actions -> gestures settings) but "disable gestuers globally" was already clicked.  I then deleted every gesture out of the list, but that made no difference.  I set the gesture timeout to 0 ms, and to 999.

How do I make this thing stop?  Is there a gesture support shared library I can delete, perhaps?

---

