---
title: "[SOLVED] Corrupt open animation on some apps using Intel drivers and Intrepid Ibex"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by druellan on 2008-11-10
On a clean installation of Ubuntu 8.10 on a eeePC 1000h (Intel 945GM chipset) I noted that compiz's animation get corrupted while opening some windows:

[IMG]http://members.lycos.co.uk/biosfera/Ubuntu/intrepid.corruption.png[/IMG]

This seems to happen on apps that have some sort of text box, like Firefox, OpenOffice or Geany editor, and its visible even booting as a live CD.

I've managed to work around the problem adding some options on my xorg.conf. More information: [https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492)


**Method 1, revert to XAA:**

Open xorg.conf using: **sudo nano /etc/X11/xorg.conf**
Locate the section showing: **Identifier "Configured Video Device"**
Below, add:
**Option "AccelMethod" "XAA"**
**Option "XAANoOffscreenPixmaps" "true"**
Save the file and push CTRL+ALT+BACKSPACE to reload X


**Method 2, EXA using "greedy" Heuristics:**

Open xorg.conf using: **sudo nano /etc/X11/xorg.conf**
Locate the section showing: **Identifier "Configured Video Device"**
Below, add:
**Option "AccelMethod" "EXA"** (just to make sure is enabled)
**Option "MigrationHeuristic" "greedy"**
Save the file and push CTRL+ALT+BACKSPACE to reload X

---

