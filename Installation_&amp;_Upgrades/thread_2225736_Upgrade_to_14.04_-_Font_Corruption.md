---
title: "Upgrade to 14.04 - Font Corruption"
date: 2014-05-22
forum: Installation &amp; Upgrades
---

### Post by richardbrucebaxter on 2014-05-22
I am getting the same issue as identified in [this]("http://ubuntuforums.org/showthread.php?t=2218596") thread ("Upgrade to 14.04 - Graphics Went Wrong").

Upon upgrading to Ubuntu 14.04 the WM fonts change to an outline font of some kind, approximately 50% of times the PC is booted. e.g. Thunar, Nautilus, Gedit, Gnome-terminal, all toolbars (including Gimp, OpenOffice, calculator, current version of Firefox appears unaffected). I am using icewm with an AMD proprietary graphics driver (AMD catalyst 14.4). Note this system also has the proprietary font package installed (Arial etc), although this shouldn't make a difference.

Cheers,

Richard

---

### Post by richardbrucebaxter on 2014-07-05
Note the thin outline fonts may well be default icewm/X11 fonts (which happen to look like the original google chrome fonts). They appear on EL6 also and can be changed by temporarily initialising gnome-appearance-properties (gnome-appearance-properties; sleep 3; killall gnome-appearance-properties). The same kind of trick appears to work on UB14 (which can be adding to ~/.icewm/startup);

gnome-settings-daemon &
#makes all GTK applications (eg Firefox/Thunar) use the Gnome3/Unity graphics (dark grey)
sleep 3 &
killall gnome-settings-daemon

---

