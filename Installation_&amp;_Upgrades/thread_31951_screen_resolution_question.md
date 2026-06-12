---
title: "screen resolution question"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by upalm on 2005-05-05
Hi
is there a way to force Ubuntu to display at 1024x768? currently my screen res. maxes out at 800x600 when changed from the desktop "applet" but my laptop screen says it is TFT 1024x768. Perhaps by editing something in /etc/X11/xorg.conf but what? any help gratefully appreciated.
cheers
upalm

---

### Post by sprucio on 2005-05-05
In that file, look for entries that have "800x600". You'll have to add "1024x768" in front of that section.

---

### Post by bored2k on 2005-05-05
did you try
 sudo dpkg-reconfigure xserver-xorg && sudo reboot 

?

---

