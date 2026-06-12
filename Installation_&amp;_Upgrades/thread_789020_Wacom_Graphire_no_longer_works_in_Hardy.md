---
title: "Wacom Graphire no longer works in Hardy"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by gwi on 2008-05-10
I have a Wacom Graphire, which worked perfectly well with Dapper, Edgy, Feisty and Gutsy. After upgrading to Hardy it doesn't anymore. After every time I log in, or switch to tty1-tty6 and back to tty7, the mouse pointer is frozen. I then have to unplug and reconnect the tablet (USB connected). The pen however loses it absolute positioning mode, and whenever the pen is out of reach of the tablet, the mouse pointer moves to the upper left corner of the screen. This makes things like photo editing impossible.
When the mouse pointer is frozen, the yellow led in the tablet is on (as normal), and when tapping with the pen, the led flashes green (as normal). So on the hardware side everything seems ok.

My Wacom settings in xorg.conf are still there after the upgrade, so I have no idea what is wrong.

I tried downgrading xserver-xorg-input-wacom and wacom-tools to their Gutsy versions. This didn't result in the tablet behaving the way it did under Gutsy.

Any ideas what's wrong here? Do I have to downgrade to Gutsy to get the tablet working?:mad:

Here are my Wacom related settings in xorg.conf:
```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"WacomStylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"InputFashion"	"Pen"
	Option		"Mode"	"Absolute"
	Option		"Name"	"GRAPHIRE / INTUOS Stylus (USB)"
	Option		"Protocol"	"Auto"
	Option		"SendCoreEvents"	"on"
	Option		"USB"	"on"
	Option		"Vendor"	"WACOM"
	Option		"Button2"	"3"
	Option		"Button3"	"2"
	#	Option		"Suppress"		"20"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"WacomEraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"InputFashion"	"Eraser"
	Option		"Mode"	"Absolute"
	Option		"Name"	"GRAPHIRE / INTUOS Eraser (USB)"
	Option		"Protocol"	"Auto"
	Option		"SendCoreEvents"	"on"
	Option		"Tilt"	"on"
	Option		"Type"	"eraser"
	Option		"USB"	"on"
	Option		"Vendor"	"WACOM"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"WacomCursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"Mode"	"Relative"
	Option		"InputFashion"	"Tablet"
	Option		"SendCoreEvents"	"on"
	Option		"USB"	"on"
	Option		"Vendor"	"WACOM"
	Option		"Name"	"GRAPHIRE / INTUOS (USB)"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"WacomStylus"	"AlwaysCore"
	Inputdevice	"WacomCursor"	"AlwaysCore"
	Inputdevice	"WacomEraser"	"AlwaysCore"
EndSection
```

---

