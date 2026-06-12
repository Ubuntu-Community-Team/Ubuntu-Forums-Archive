---
title: "Cannot change screen resolution"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by LeoTheComm on 2007-07-23
Am less than 24 hrs into a new (to me) install of 7.04 and all is running well. The machine in question is a P4 1.6ghz 512 RAM and an Nvidia Ge4 440. Gnome is up, and the compiz features are also working. No complaints there, but my screen resolution is stuck at 600x800x50hz and I cannot make it larger nor keep it from looking like a strobe light.  I've added the proper Horiz and Vert refresh rates of my monitor to xorg.conf and still I cannot change the desktop resolution. Any help to solve this would be greatly appreciated!

---

### Post by epyon_avenger on 2007-07-23
I know for me the easiest thing to do is arrange my xorg.conf as follows...

```

Section "Device"
	Identifier	"nVidia GeForce 4"
	Driver		"nvidia"
EndSection

Section "Monitor"
	Identifier	"Built-In"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia GeForce 4"
	Monitor		"Built-In"
	Option		"AddARGBGLXVisuals" "True"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Viewport	0 0
	EndSubSection
EndSection

```

Make sure you back up your xorg.conf before making the changes. ^_~

---

