---
title: "Lost Taskbars/Panels after Upgrade to Gutsy"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2008-04-19
After successfully (ie. completed all steps including a reboot), I had a problem with nVidia. I used Envy to get the latest drivers and that went ok as well.

Problem is that when I log on, I have no Taskbars (top or bottom) and therefore no panels. I can see the top and bottom taskbars 'flashing' a few times before they disappear.

I have amarok starting automatically and that works, so I think the system is ok in general.

I have tried logging on with other usernames and get the same result.


Any suggestions?

Leo

---

### Post by lister171254 on 2008-04-26
I have a bit more info.

 Found one problem in my xorg.conf where during the upgrade I ended up with a default Depth of 24, but only had a depth of 1 in the Display subsection. I have manually added the other sections and can now launch different windows from a terminal session and setting the display to :0.0

When running gnome-panel I get the following errors:

Gtk-warning about trying to allocate a widget with width -3 and height 24
gnome-panel error where it cannot find FT_Library_SetLcdFilter in /usr/lib/libcairo.so.2

Cheers,

Leo

---

