---
title: "ATI Drivers"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by joplass on 2006-11-26
I have Edgy running I am trying to find out what driver I have installed.  Anyone knows the command to display this information? Or maybe any other way of finding out?
My appreciations.

---

### Post by CowzRule on 2006-11-26
To see which driver is being loaded, you can view the file "xorg.conf". In a terminal type```
gedit /etc/X11/xorg.conf
```Look for a section that looks similar to this> Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	[COLOR="Red"]Driver		"ati"[/COLOR]
	BusID		"PCI:1:0:0"
EndSectionThe line in red is what driver is being loaded.
Also, in a terminal you can type```
glxinfo
```And, if you updated the drivers with the ones from the repos or from ati.com you can type```
fglrx
```Hope that helps :)

---

