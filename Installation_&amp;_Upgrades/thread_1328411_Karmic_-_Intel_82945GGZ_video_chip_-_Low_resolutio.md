---
title: "Karmic - Intel 82945G/GZ video chip - Low resolution / no monitor detection"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by e.m.fields on 2009-11-16
Hi-
Just posting my own thread on the subject in hopes of catching an answer.

Problem:
Upgrade to Karmic from 9.04, with Intel 82945G/GZ video chip, produces low resolution settings, which cannot be changed under "Display".

Attempted solutions:
[LIST]Editing /etc/X11/xorg.conf: 
  Attempting to add higher resolution manually.
[/LIST]
  No results, as I don't know much what I'm doing here.

Anyone can guide me to a solution?

---

### Post by choochoo22 on 2009-12-05
I have the same problem with an Intel 965G video.  Still searching for a solution.

---

### Post by AlexanderDGreat on 2010-03-22
Anyone find a solution? I'm a newbie and am so frustrated I'm just using 800x600 resolution. But I have a 1280x1024 screen and 82945G/GZ Integrated Intel VGA card. Where do I begin? Pls. help.

---

### Post by AlexanderDGreat on 2010-03-24
I found the solution, use this:

Section "Monitor"
	Identifier	"Monitor0"
	ModelName	"LG L1753S"
	HorizSync	30 - 64.0
	VertRefresh	56.0 - 65.0
	Option		"DPMS"
EndSection

Section "Device"
	Identifier	"Videocard0"
	Driver		"intel"
EndSection

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24

	SubSection "Display"
		Depth	24
	EndSubSection
EndSection

---

