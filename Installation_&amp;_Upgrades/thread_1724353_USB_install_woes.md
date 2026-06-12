---
title: "USB install woes"
date: 2011-04-08
forum: Installation &amp; Upgrades
---

### Post by dbyrne on 2011-04-08
I've been trying to install Ubuntu on a HP Proliant mini-server for the last three days, and I was close to giving up on it. I've spent hours burning USB images and searching the web.

In case it helps anyone else, the problem turned out to be that although I was trying to install 10.04.02-server-amd64.iso using
the Universal-USB-Installer-ver 1.8.3.9, I had selected "Ubuntu 10.04.X" instead of "Ubuntu Server 10.04.X Installer" further down the list. I tried four other distros too, and in each and every case failed to notice that there was a different option for the server version of the OS in the USB creator, and selected the wrong one. Aaaaaaaarrrrgggghhhh !!!! If only it had said "Ubuntu 10.04.X Desktop Installer" instead of "Ubuntu 10.04.X" I would have saved days ...

Anyway, the symptoms were that although the USB always booted up fine, none of the Run or Install options on the Installer Menu ever worked - they just returned to the menu with no indication of what was wrong.

As soon as I had matched the USB installer option and the ISO, everything worked fine.

---

