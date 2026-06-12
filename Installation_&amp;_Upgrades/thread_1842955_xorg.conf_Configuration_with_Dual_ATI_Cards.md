---
title: "xorg.conf Configuration with Dual ATI Cards"
date: 2011-09-12
forum: Installation &amp; Upgrades
---

### Post by bensun13 on 2011-09-12
I just installed a second ATI card on my Dell Optiplex 760. The original card is ATI RV620 LE [Radeon HD 3450] with a dual header. The card worked out of the box and I installed the proprietary fglrx driver for it. Now, I've added an additional card (ATI RV516 [Radeon X1300/X1550 Series]) and am trying to configure it to run a third monitor. I've tried to run both proprietary (fglrx) and open source (radeon) drive on both cards. One thing I noticed is that when I set both cards to use fglrx in my xorg.conf aticonfig seg faults. Ubuntu doesn't seem to recognize the third monitor and merely displays the Ubuntu logo on it. Anybody know what I am doing wrong? Below is the xorg.conf:

```
Section "ServerLayout"
	Identifier     "aticonfig Layout" 
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen 	    "aticonfig-Screen[0]-0" LeftOf "aticonfig-Screen[0]-1"
#	Option	    "Xinemera" "on"
#	Option	    "Clone" "off"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1280 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-DFP3"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1280x1024"
	Option	    "TargetRefresh" "60"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP1" "0-DFP1"
	Option	    "Monitor-DFP2" "0-DFP2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-1"
	Driver      "ati"
	Option	    "Monitor-DFP3" "0-DFP3"
	BusID       "PCI:5:0.1"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Virtual   2560 2560
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-1"
	Device     "aticonfig-Device[0]-1"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
	EndSubSection
EndSection
```

---

### Post by bensun13 on 2011-09-14
Anyone?

---

