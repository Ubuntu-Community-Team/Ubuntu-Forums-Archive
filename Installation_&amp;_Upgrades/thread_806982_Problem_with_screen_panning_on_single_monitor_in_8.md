---
title: "Problem with screen panning on single monitor in 8.04"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by wires on 2008-05-25
I'm trying to set my screen resolution to 1024X768 so it fits entirely on my monitor's screen.  When I set the resolution to 1024X768  (System-->Preferences-->Screen resolution) my desktop pans larger than my monitor.  This is very Inconvenient and not what I want.  I can set the screen resolution to 800X600, but that's to small.  My video card is an older ATI Rage 128.  Has anyone seen and resolved this problem?  Thanks in advance.

Here is my xorg.conf:
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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ATI Rage 128"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Vendorname	"ATI"
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
	# V-freq: 60.00 Hz  // h-freq: 47.80 KHz
	Modeline "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796 
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768	
		Modes       "1024x768@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection
Section "ServerFlags"
EndSection

---

