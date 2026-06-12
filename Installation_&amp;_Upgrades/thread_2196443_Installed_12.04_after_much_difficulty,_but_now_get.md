---
title: "Installed 12.04 after much difficulty, but now getting blank screen at login"
date: 2013-12-29
forum: Installation &amp; Upgrades
---

### Post by The-Master on 2013-12-29
Hi there. I've been trying to solve the problems I've been having myself but I've finally hit a wall. I was having difficulty with blank screens and no backlight turning on with the 13.10 install disk but 12.04 seemed to install OK. I've installed it alongside windows 8 and the system is in UEFI mode. I had to run startup repair to get grub to show up though.

I have a problem where the backlight flickers and then turns off but I can increase the brightness by using the function key shortcut. This allows me to see the splash screen. The screen then becomes black after it has loaded but I hear the drum noise indicating that the system is trying to get me to login. So it seems the video isn't working.

Some extra info:
Graphics card nvidia Geforce 750M
Tried nomodeset with no success 
Tried editing xorg.conf ("UseDisplayDevice" "DFP") - no change
Tried nvidia-settings command  - changed the xorg.conf file considerably
Tried no splash screen to look for errors. Couldn't see anything significant
Tried recovery mode with graphics failsafe without success. Didn't start.
I also try to put my password in once I hear the drumroll and hit enter and don't hear anything else so this may indicate that the keyboard isn't functioning either.

I've run out of things to try now. Any help would be greatly appreciated.

---

### Post by The-Master on 2013-12-29
I've managed to get it to boot by uninstalling the proprietary nvidia drivers via the command line. It makes sense now I think of it. I would like to run the proprietary drivers though since I got a high powered computer so that I could try out some games through linux. I'll update this post if I succeed and mark the thread read once I've finished.

I am also looking for a solution to the screen brightness issue on power on if anyone happens to read this before I try to figure it out myself.

---

