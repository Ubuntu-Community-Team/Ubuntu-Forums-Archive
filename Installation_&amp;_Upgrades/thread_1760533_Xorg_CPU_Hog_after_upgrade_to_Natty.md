---
title: "Xorg CPU Hog after upgrade to Natty"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by 404wanderer on 2011-05-17
Hello all,

I've just upgraded my Mythbuntu box to Natty. Now I have a completely unusable system due to Xorg taking 70% of CPU. Mouse movement is possible and I can just type but that is about it. Using MythTv is impossible.

I'm running a standard mythtv build with the xfce desktop.
Anybody any ideas how to fix this one as it has rendered my PVR system impotent.

Cheers,
Wanderer :confused:

---

### Post by NormanFLinux on 2011-05-17
Duh.

Upgrade the kernel to 2.6.39.0.

The kernel Natty shipped with is buggy to say the least.

---

### Post by 404wanderer on 2011-05-19
Thanks foe the reply. How do I update the kernel? It's not showing as an available package for update yet.

---

### Post by 404wanderer on 2011-05-30
*bump*

Can anybody assist at all. I've applied all of the updates I can find and the Xorg is still running flat out and refreshing the screen every second or two. The system is still completely unusable as a media centre.

---

### Post by 404wanderer on 2011-06-11
OK, fixed.

Killed processes until CPU usage of Xorg dropped. Found out it was 'fuzzyflakes', the screensaver (even though screensaver wasn't currently activated).

Removed screensaver packages and that fixed problem.

---

