---
title: "NVidia 6800XT Low Resolution"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by Ianvn on 2008-01-11
I just installed gutsy running gnome.
I have a NVidia Geforce 6800 XT

For some reason the only resolutions I'm able to select are the following:
320*240, 400*300, 640*480

I have already installed and enabled the restricted drivers for nvidia. 
I have also tried running dpkg-reconfigure xserver-xorg and selecting resolutions higher than 640*480

Here is my xorg.conf file:

> Section "Files"
EndSection

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
	Identifier	"nVidia Corporation NV40 [GeForce 6800 XT]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
	Modeline "640x480" 25.175 640 664 760 800 480 491 493 525 #60Hz
	Modeline "800x600" 40 800 848 968 1056 600 601 605 628 +hsync +vsync
	Modeline "1024x768" 65 1024 1032 1176 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV40 [GeForce 6800 XT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
	Modes		"1024x768" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Any help solving this would be appreciated.

---

### Post by taurus on 2008-01-11
You mean

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
didn't help, either?

---

### Post by Ianvn on 2008-01-11
Yes, I have tried that as well-  but with the same result
Still no change in the resolutions I can select.
:(

---

### Post by taurus on 2008-01-11
What kind of monitor you have and are those vertical and horizontal refreshing rates correct?

I have a 6800XT card and I don't even have the vertical/horizontal refreshing rates and modelines in my /etc/X11/xorg.conf.  Everything is working fine my end with the restricted driver from System -> Administration -> Restricted Drivers Manager.

---

### Post by Ianvn on 2008-01-11
It's a pretty old no-name brand 17" screen.
When I did the dpkg-reconfigure it detected it as a generic model.
During that configure it gives u 3 option to configure your screen.
I only selected that it was a 17" capable of going at least 1024*768 @ 72Hz

I know in Windows I normally run it @ that settings and it can still go a bit higher.

---

### Post by Ianvn on 2008-01-11
After installing all available ubuntu updates and doing the required restart 
I'm now able to set my resolution up to 1024*768 but the max refresh rate I can select is 52Hz

:(

---

