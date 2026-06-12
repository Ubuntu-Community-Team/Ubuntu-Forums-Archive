---
title: "ATi X300 (THINKPAD R52)"
date: 2007-10-14
forum: Installation &amp; Upgrades
---

### Post by Benjamin888 on 2007-10-14
Hello. I am still quite new with Linux, but am very keen to learn. 

I have an [IBM Thinkpad R52 1846-61M]("http://www.lenovo.com/think/support/site.wss/quickPath.do?quickPathEntry=184661m&sitestyle=lenovo"). 

The video card i have is an ATI X300 Radeon 64MB. I have 1.5GB of System RAM.

I have had Beryl working once before, but am not sure what ive done or what to do to get it working again. Ive followed many different tutorials online, and possible done more damage than good now. 

But anyway i followed a tutorial to get XGL working. Now i am at the point where:
When i load an XGL session after a restart, the graphics load but the computer freezes up and i can only move the mouse around, but not select anything.

 If i load a GNOME session, logout, then load the XGL session all my graphics are distorted any messy (like the image attached).

What is XGL and Compiz and AIGL?

Which are the better drivers to use to get this done with my Video card.

```
~$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
```

```
Section "Monitor"
	Identifier "Builtin LCD"
	HorizSync 28.0 - 70.0
	VertRefresh 43.0 - 60.0
	Option "DPMS"
EndSection
Section "Device"
    Identifier  "ATI Technologies Inc M22 [Radeon Mobility M300]"
    Driver      "fglrx"
    Option      "VideoOverlay" "on"
    Option      "OpenGLOverlay" "on"
    BusID       "PCI:1:0:0"
	Option "DRI" "true"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	Option "AccelMethod" "EXA"
	Option "XAANoOffscreenPixmaps"
	Option "RenderAccel" "true"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "on"
EndSection
Section "Screen"
    Identifier "Default Screen"
    Device     "ATI Technologies Inc M22 [Radeon Mobility M300]"
    Monitor    "Builtin LCD"
    DefaultDepth     24	
	SubSection "Display"
		Depth	1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
Section "Extensions"
    Option  "Composite" "Disable" 
EndSection
Section "ServerFlags"
	Option "AIGLX" "off"
EndSection 
```

---

### Post by timetunnel on 2007-10-18
I've got the same laptop and had the same problem after I did a fresh install of Gutsy Release Candidate. A few hours after my installation an update for compiz arrived and from then on I couldn't enable it anymore (at least not "System->Settings->Appearance"). 

It's a bug actually, and on a default Gutsy this graphics card is on a blacklist now: 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/108527](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/108527)

Though I prefer a stable system over some effects I was kind of looking  forward to them - they worked fine when starting Gutsy RC as a live CD and looked amazing. :-/

Jens

---

