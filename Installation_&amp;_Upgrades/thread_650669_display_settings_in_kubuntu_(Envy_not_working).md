---
title: "display settings in kubuntu (Envy not working)"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by bone2006 on 2007-12-26
I would like to increase my resolution as I have on my other systems and really have had an easy time with envy, now I'm installing it in kubuntu and it's complaining about decencies and from doing a few searches it seems that envy doesn't play well with kubuntu.

Well my resolution is 1280x1024 and I'd like to increase the resolution.  	Xorg.conf has the device as:
Device		"nVidia Corporation NV34 [GeForce FX 5200]"  

I see the first mode in the Xorg.conf as "1600x1200", but I can't go this high in the Monitor & Display in system settings.  It will only go to 1280X1024

I have nVidia GeForce FX 5200 and a Samsung SyncMaster 932b

Any help is greatly appreciated

---

### Post by bone2006 on 2007-12-26
As I'm looking at the Xorg.conf file I see it has:

Section "Monitor"
	Identifier	"Visual Sensa"
	Option		"DPMS"

Which is my old monitor.  Could this be the cause?  I've tried changing it in the system settings, but the monitor is new and it wasn't in the list and auto detecting it I guess isn't working.

---

