---
title: "screen resolution limitted to 1024x768 with radeon x850"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by SodiumKPump on 2007-04-18
I'm a totally new to linux so I am hoping that I could get some direction here. I realize ATI cards are difficult to get working but I've recently installed ubuntu 7.04 and am unable to get my resolution higher than 1024x768.  I've tried the fglrx drivers and installed through synaptics, i've tried the ati driver and the radeon driver but none of these allow me to increase my resolution.  Could it be my monitor? Thanks for any help!

here is my xorg.conf: (from my video card down.. i didn't think everything before this point was necessary)
```
Section "Device"
	Identifier	"ATI radeonx850"
	Driver		"fglrx"
	BusID		"PCI:5:0:0"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072 
	Option		"DPMS"
	HorizSync	28-80
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI radeonx850"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024@75" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024@75" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024@75" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024@75" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024@75" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024@75" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by SodiumKPump on 2007-04-18
Solved the problem--reran dpkg -reconfigure and lowered the refresh rate

=D

---

