---
title: "Latest Driver"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by thetimekeeper on 2007-11-02
Hi, here's the line from my xorg.conf dealing with my graphics driver. I'm running a Geforce Go 6200 card.

> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option "RenderAccel" "true"
EndSection

Is there any way to improve on what I have already, like update the driver for increased performance, and less chance of those occasional slowdowns I'm getting?

---

