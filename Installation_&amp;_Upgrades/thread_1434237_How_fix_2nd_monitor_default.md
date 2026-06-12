---
title: "How fix 2nd monitor default"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by daisho73 on 2010-03-20
I recently had a wine program crash after I tried to set it within itself to windowed mode. Now ever since, when I boot, I load my sound app and it loads on the smaller 2nd monitor to the right. ANY wine pop-up or program loads on the 2nd monitor to the right. Even though I've checked that my primary, larger monitor on the left is #1 both in displays and through amdcccle.

I've read through my xorg.conf but don't see why pop-ups windows and wine windows are loading to the smaller monitor.

My xorg.conf:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-DFP2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1920x1200"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1024x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1920 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-DFP2" "0-DFP2"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2944 2944
		Depth     24
	EndSubSection
EndSection

---

### Post by daisho73 on 2010-03-20
Has anyone seen this behavior before where Wine and other pop-ups menus default to loading on the 2nd monitor while most Linux programs load on the main? I am running a virtual desktop across both but in the past everything opened on the primary monitor first.

---

