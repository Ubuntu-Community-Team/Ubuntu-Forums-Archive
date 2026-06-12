---
title: "Yet Another Gutsy-Twinview Issue: One monitor okay, two monitors with Twinview crash"
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Hans Bogar on 2008-02-03
Hello everybody,

Recently I switched from Gentoo to Ubuntu Gutsy 7.10. (Gnome)
With only the first monitor enabled, everything is working fine (desktop, Compiz, etc), but as soon as I enable twinview I fall back to Fail-save login during login.
I've searched this forums numerous times also Internet linux sites, I changed my xorg.conf many many times, but I'm unable to solve this one. And it seems thay I'm not the only one experiencing problems on this subject.

My configuration:
AMD64, running in 32bits mode. I've used the i386.iso
nVidia 6600 GT
BenQ FP937s as main monitor (Flatscreen, but with Sub-D connector (= CRT)
Sony E400 as second monitor (CRT)

Here is what I've done so far:

- Enable Twinview with "nvidia-settings"
- Enable Twinview by changing xorg.conf by hand
- One possibility is to remove "xserver-xgl". But this program is not installed during standard installation.
  A thread about "xserver-xgl" : 
[http://ubuntuforums.org/showthread.php?t=588281&highlight=disable+gdm]("http://ubuntuforums.org/showthread.php?t=588281&highlight=disable+gdm")



My xorg.conf:

```
# Xorg.conf setting
# 20080203
#
# info:
# http://www.glawing.com/forum/viewtopic.php?t=14&highlight=twinview
# http://ubuntuforums.org/archive/index.php/t-75149.html

# ============================================================================

Section "Files"
EndSection

# ============================================================================

Section "Module"
	Load		"glx"
	Load		"dri"
	Load		"v4l"
EndSection

# ============================================================================

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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

# ============================================================================

Section "Device"
	Identifier	"nVidia Corporation NV43 [GeForce 6600 GT]"
	Boardname	"nv"
	Busid		"PCI:5:0:0"
	Driver		"nvidia"

	Option 		"NoLogo" "True"


	# *** Twinview ***
	#
	# ENABLING THE FOLLOWING OPTIONS, WILL CRASH THE X-SYSTEM BACK TO FAIL-SAVE...
	#
#	Option 		"TwinView" "True"
#	Option 		"TwinViewOrientation" "LeftOf"   
#	Option 		"MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
#	Option 		"SecondMonitorHorizSync" "30-96"
#	Option 		"SecondMonitorVertRefresh" "48-120"
#	Option 		"UseDisplayDevice" "CRT, CRT"


EndSection

# ============================================================================

Section "Monitor"
	Identifier	"Monitor"
	Horizsync	57-82
	Vertrefresh	60.77
EndSection

# ============================================================================

Section "Screen"
	Identifier	"Generic Monitor"
	Device		"nVidia Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Monitor"
	Defaultdepth	24
	SubSection "Display"
		Viewport 0 0
		Depth	16
		# Toevoeging ivm desktop groter dan display
		Virtual 1280 1024
		Modes	"1280x1024@75" "1024x768@75" 
	EndSubSection
	SubSection "Display"
		Viewport 0 0
		Depth	24
		# Toevoeging ivm desktop groter dan display
		Virtual 1280 1024
		Modes	"1280x1024@75" "1024x768@75"
	EndSubSection
EndSection


# ============================================================================

Section "ServerLayout"
	Identifier	"TwinView Configuration"
  	screen 		"Generic Monitor"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Option 		"Xinerama"   "Off"
EndSection

# ============================================================================

Section "DRI"
	Mode	0666
EndSection

# ============================================================================


```



I'm running out of ideas.  :(

Is there a known bug about this???

Any ideas where else I could look, or what to look for?
Thanks in advance!

---

### Post by Hans Bogar on 2008-02-09
*BUMP*

Any hints?

thx.

---

