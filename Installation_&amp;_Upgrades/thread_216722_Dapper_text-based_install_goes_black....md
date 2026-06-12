---
title: "Dapper text-based install goes black..."
date: 2006-07-15
forum: Installation &amp; Upgrades
---

### Post by TheBlackNoodle on 2006-07-15
I'm trying to install Dapper on an oldish Dell, 2.4 GHz, 256 MB memory. I resorted to the text-based method since, for some reason, the LiveCD installer was INSANELY slow. Actually, I couldn't load any programs in X on it.

Anyway, the text-based install was going nicely until a few minutes ago. I was watching the screen, and while it was installing Ubuntu-Desktop, the screen went black except for what looks like two non-blinking cursors in the middle of the screen. I have no idea what's going on. Is my installation broken?

I'm not sure the exact model of the video card, but while it had Windows on it, the Graphics Controller was listed as Intel(R) 82845/GL/GE/PE/GV.

Any help would be greatly appreciated.

---

### Post by cotcot on 2006-07-16
Do not know what "insanely slow" means.
As you got to the graphical installer it means that the graphics card is recognised. So I think it is something else. 
Maybe it helps using the Alternate InstallCD. It has a text version to install.

---

### Post by tseliot on 2006-07-16
> **TheBlackNoodle said:**
> I'm trying to install Dapper on an oldish Dell, 2.4 GHz, 256 MB memory. I resorted to the text-based method since, for some reason, the LiveCD installer was INSANELY slow. Actually, I couldn't load any programs in X on it.

Anyway, the text-based install was going nicely until a few minutes ago. I was watching the screen, and while it was installing Ubuntu-Desktop, the screen went black except for what looks like two non-blinking cursors in the middle of the screen. I have no idea what's going on. Is my installation broken?

I'm not sure the exact model of the video card, but while it had Windows on it, the Graphics Controller was listed as Intel(R) 82845/GL/GE/PE/GV.

Any help would be greatly appreciated.

Try burning the CD at a lower speed (4X)

---

### Post by TheBlackNoodle on 2006-07-16
I tried the text-based install. It was fast and working quite well, but that's what's giving the black screen, which surprised me. I tried an integrity check on the CD; it said everything was fine. But I'll try burning it slower now. Hopefully that will fix it.

For the graphical installer: Insanely slow means that, when I double-clicked, the Installer, it took roughly 15 minutes before any GUI appeared. It was taking about 30 minutes to load the location screen, so I gave up there in favor of the text-based install. It may just be that the CD reader isn't very good in this computer, and the disk was burned too high. It works fine on my laptop, but that has better and newer hardware.

---

### Post by TheBlackNoodle on 2006-07-16
Okay, I tried installing again with a disk burned at 4x. Same problem--I was wrong about where the black screen comes up. When it hits "Configuring xserver-xorg..." is when the black screen pops up. That makes more sense. I'm going to try something else, but if anyone has any ideas, let me know.

Since I figured out exactly where it was crashing, I was able to find this thread:
[http://www.ubuntuforums.org/showthread.php?t=209364](http://www.ubuntuforums.org/showthread.php?t=209364)
which covered the problem exactly. Simply hitting F4 and changing to the native resolution (640x480 in my case) fixed it.

---

