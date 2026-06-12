---
title: "Help! Can't configure xorg.conf correctly..."
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by vsanghvi on 2006-11-19
So, I installed 6.10 server, and wanted to install ubuntu desktop on top so I could have an interface... so i used:
'sudo apt-get update'
'sudo apt-get install ubuntu-desktop'

The install goes fine and I reboot. Unfortunately when it boots up, I get a message saying failed to start the X server.

The main error is:
(EE) AIGLX: Screen 0 is not DRI capable

and other errors like:
(EE) xf86OpenSerial: Cannot open device /dev/wacom

I looked online and this issues seems like its common, but I haven't found a solution that seems to make it work.

I have an old system (Pentium III, 1 GHz) with a Intel® Direct 3D 2x AGP (shared memory) card.

I've been going at this for a few days so any help is much appreciated!

---

### Post by vsanghvi on 2006-11-19
nevermind, it looks like the i810 driver worked :-/ sorry for the usless post....

---

