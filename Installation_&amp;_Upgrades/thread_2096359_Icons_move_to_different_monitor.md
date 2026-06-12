---
title: "Icons move to different monitor"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by justcarroll on 2012-12-19
I recently moved from 11.04 to 11.10.  Everything went surprisingly  well.  

I have a dual monitor display that worked in 11.04 and still worked in 11.10, well mostly. The only issues is that whenever I click on a icon (file, folder, etc.) on the right monitor, hoping to move it, the icon instantly moves to the left monitor even though the mouse pointer is still in the right.  I can still move the icon.

Similar things happen when I attempt to move an icon on the left monitor.  As soon as I try to move it the icon gets moved to the left.  In this case I can't even see the icon until I move the mouse back to the right side.  

The monitors resolution is 1680x1050.  Basically whenever I attempt to move an Icon it's position gets offset one monitor width to the left.

This is fairly annoying but usable.  I would be more upset except the upgrade fixed so many other issues.

xorg.conf is below.

```
Section "ServerLayout"
	Identifier     "amdcccle Layout"
	Screen         "amdcccle-Screen[1]-0" RightOf "amdcccle-Screen[1]-1"
	Screen         "amdcccle-Screen[1]-1"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
        Option	    "Xinerama" "on"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "Disable" "false"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
EndSection

Section "Monitor"
	Identifier   "0-DFP5"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1680x1050"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP5" "0-DFP5"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
	SubSection "Display"
		Virtual   2960 1050
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-0"
	Device     "amdcccle-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

