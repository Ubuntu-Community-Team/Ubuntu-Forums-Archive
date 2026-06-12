---
title: "xwindows"
date: 2005-11-16
forum: Installation &amp; Upgrades
---

### Post by jimhammer on 2005-11-16
Hi,

fairly new to Linux so please forgive ignorance. Installed ubuntu and appears OK until loading XWindows, screen just goes blank. Monitor then shows no signal from graohics card. Can boot to terminal prompt using recovery mode.
Both Monitor and graphics cards are OK.

I wondered if it was anything to do with the KVM Switch I use? 

If so how can I overcome this prob' without removing the KVM switch? any sensible advice and guidence appreciated.

jim

---

### Post by oskude on 2005-11-16
[QUOTE=jimhammer]I wondered if it was anything to do with the KVM Switch I use?[/QUOTE]i wonder if you have tested without the KVM :rolleyes:

[QUOTE=jimhammer]If so how can I overcome this prob' without removing the KVM switch? any sensible advice and guidence appreciated[/QUOTE]i can imagine that your KVM has a resolution/refreshrate limitations, check the manuals...
and then check your /etc/X11/xorg.conf that i wont exceed your KVMs restrictions...
and /var/log/Xorg.0.log could also give some clues...

---

