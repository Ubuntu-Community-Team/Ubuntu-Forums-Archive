---
title: "Display problems in 8.10"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by koulanji on 2008-11-02
I'm using xubuntu 8.1.0 and I only have a 1024x768 resolution when my native resolution is 1280x800. This happened immediately after I upgraded from 8.0.4 
My graphics card is an  Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller and I am using an HP dv6000 laptop. I have tried editing my xorg config manually by adding the modes of display and my monitor configuration, but everytime I restart my computer xubunutu ignores or deletes the configuration entirely. I've also tried using xrandr -q  and sudo dpkg-reconfigure xserver-xorg. When i use the latter command I get no options to reconfigure my graphics card - just my keyboard and mouse. This is what my xorg looks like now
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier "Monitor0"
	Option "DPMS"
	HorizSync 28-64
	VertRefresh 43-60
EndSection

Section "Screen"
	Identifier "Default Screen"
	Monitor "Monitor0"
	Device "Configured Video Device"
	DefaultDepth 24
SubSection "Display"
	Depth 24
	Modes "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
Any help would be appreciated.

---

