---
title: "Using 915resolution"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by ugroh on 2007-03-27
After using the program 915resolution to chance the font size of my externally attached display (on my lenovo X60s laptop) I can not longer login but have to use the gnome-safe modus. After login I get the message:

..
Unable to determine the address of the message bus (try 'man dbus-launch' or 'man dbus-Daemon' for help)
..

This message is not helpful because I get no real help for the problem. Any suggestions out there?

Ulrich

---

### Post by ariel on 2007-04-08
I saw the same error message today in an nvidia-based machine (without 915resolution). Not sure if it is the same problem or not, but in my case I had to remove beryl-manager from my auto startup programs (located in ~/.config/autostart/, editing the beryl*.....desktop file and setting the last line to X-GNOME-Autostart-enabled=false)

---

