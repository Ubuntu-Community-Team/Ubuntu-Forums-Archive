---
title: "Fresh install fails to detect video and monitor"
date: 2008-07-07
forum: Installation &amp; Upgrades
---

### Post by jlhughes on 2008-07-07
After a clean install of the most recent version of Ubuntu Hardy, the default screen resolution was completely wrong for the monitor.

I ran sudo dpkg-reconfigure xserver-xorg

BUT all I get are keyboard choices. Once finished with the keyboard configuration, the program quits and returns me to the terminal window.

This machine was running Ubuntu Hardy BEFORE I reinstalled. The log-in screen was NOT perfect (sizing was off), but I was able to reset the screen size once I logged in and that was working fine BEFORE I reinstalled.

So, I know this system can work with Ubuntu.

If sudo dpkg-reconfigure xserver-xorg doesn't get me into the video/monitor reconfiguration, what will?

Thanks for the help.

---

### Post by avtolle on 2008-07-07
Try from terminal```
gksudo displayconfig-gtk
```select the correct monitor; check on the graphics card tab to be sure the system is detecting the correct card, apply changes, then restart the computer to be sure the changes took effect. HTH.

---

### Post by jlhughes on 2008-07-07
Before I reinstalled, I copied  the /etc directory. I've now copied over the old xorg.conf file and that APPEARS to have restored the functionality to the system.

The BAD (new install) xorg.conf looked like this:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

The old (correct) xorg.conf looks like this:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
	Modeline "1280x960@60.00"  102.10  1280 1360 1496 1712  960 961 964 994  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
		Modes "1280x960@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

========================================

Clearly, something in the install process did NOT work.

---

### Post by avtolle on 2008-07-07
Glad that you got it working. For some general information on the "new" xorg, see [https://help.ubuntu.com/community/XORGHardy](https://help.ubuntu.com/community/XORGHardy) for the changes and what sometimes must be done to get things working.

---

