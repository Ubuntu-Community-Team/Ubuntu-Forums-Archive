---
title: "Dual-Head setup that works with latest radeon driver in jaunty"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Blue Beard on 2009-03-23
The most useful howto IMO is [http://wiki.debian.org/XStrikeForce/HowToRandr12](http://wiki.debian.org/XStrikeForce/HowToRandr12) 
Use gtf 1280 1024 60 to get modeline info if required.  This case is for 1280x1024 at 60 Hz.

My xorg.conf is:

# xorg.conf (X.Org X Window System server configuration file)

Section "Device"
	Identifier	"HD3450"
	Option		"Monitor-VGA-0" "NEC-M500"
	Option		"Monitor-DVI-0" "DayTek-G701PF"
EndSection

Section "Monitor"
	Identifier	"NEC-M500"
	Option		"PreferredMode" "1280x1024x60.0"
EndSection

Section "Monitor"
	Identifier	"DayTek-G701PF"
	Option		"RightOf" "NEC-M500"
	Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
	Option		"PreferredMode" "1280x1024_60.00"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"NEC-500"
	Device		"HD3450"
	DefaultDepth	24
	SubSection	"Display"
	    Depth	24
	    Virtual	2704 1050
	EndSubSection
EndSection

---

