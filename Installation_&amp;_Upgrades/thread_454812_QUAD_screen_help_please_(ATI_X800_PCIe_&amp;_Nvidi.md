---
title: "QUAD screen help please (ATI X800 PCIe &amp; Nvidia FX5200 PCI)"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by JavaIsRobust on 2007-05-25
I have 4 screens.  Dual 22" LCDs and two CRT's.  I want to run the LCD's on my ATI card in the center with a CRT on each side running on the Nvidia card.

So far this is what I have which runs both LCDs.
I can't figure out how to install and setup the nvidia card.
Any help would be much appreciated.

[PHP]Section "Device"
	Identifier	"ATI Technologies Inc R423 5F57 [Radeon X800XT (PCIE)]"
	Driver		"ati"
	Busid		"PCI:1:0:0"
	
	Option		"MergedFB"	"true"#Enable MergedFB function
	Option		"MonitorLayout"	"TMDS, CRT"# LVDS = Laptop Screen, TMDS = DVI Port, CRT = VGA Port NOT MONITOR TYPE!
	Option		"CRT2Hsync"	"30-65"#Horizontal Sync of the Monitor (check your monitor's manual for correct values)
	Option		"CRT2VRefresh"	"50-75"#Vertical Refresh rate of the Monitor (check your monitor's manual for correct values)
	Option		"OverlayOnCRTC2"	"true"
	Option		"CRT2Position"	"LeftOf"#Physical location of your secondary monitor in relationship to your primary monitor. Values can be: LeftOf, RightOf, Above, Below, and Clone.
	Option		"MetaModes"	"1680x1050-1680x1050"#Monitor Resolutions for Primary-Secondary monitors 
	#Option "MergedXineramaCRT2IsScreen0" "true" #determines which screen is going to be the primary screen; value can be "true" or "false"
EndSection

Section "Monitor"
	Identifier	"LCM-22w3"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R423 5F57 [Radeon X800XT (PCIE)]"
	Monitor		"LCM-22w3"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1680x1050"	"1440x1440"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1680x1050"	"1440x1440"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1680x1050"	"1440x1440"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1680x1050"	"1440x1440"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1680x1050"	"1440x1440"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1680x1050"	"1440x1440"	"1360x850"	"1280x1024"	"1280x960"	"1280x800"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection[/PHP]

---

### Post by JavaIsRobust on 2007-05-26
bump

---

