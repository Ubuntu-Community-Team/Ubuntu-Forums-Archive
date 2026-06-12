---
title: "Dual Monitors on Radeon HD 3870"
date: 2008-04-04
forum: Installation &amp; Upgrades
---

### Post by Annirak on 2008-04-04
I'm trying to get dual monitors working on my new computer.

I have a Core 2 Q6600, 4 GB of DDR2-1066 and a radeon HD 3870.  The MB is a P35.

EDIT: I'm running Hardy Heron

I got xserver-xorg-video-radeonhd working, but I don't have dual monitor support.  When I try to configure dual monitors, my display defaults back to vesa.

I haven't installed compiz-fusion yet, but that is a goal of mine.  I want compiz to run on both monitors.

I don't really care if I have one desktop on each monitor or a giant desktop which spans both.

Here's the xorg.conf that I tried to use:
```
Section "Files"
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"Sapphire Radeon HD 3870[0]"
	Driver		"radeonhd"
	BusID		"PCI:1:0:0"
	Screen		"0"
	
EndSection

Section "Device"
	Identifier	"Sapphire Radeon HD 3870[1]"
	Driver		"radeonhd"
	BusID		"PCI:1:0:0"
	Screen		"1"
	
EndSection

Section "Monitor"
	Identifier	"DELL E228WFP[0]"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"DELL E228WFP[1]"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"HD[0]"
	Device		"Sapphire Radeon HD 3870[0]"
	Monitor		"DELL E228WFP[0]"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"HD[1]"
	Device		"Sapphire Radeon HD 3870[1]"
	Monitor		"DELL E228WFP[1]"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" #"720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"HD[0]"
	Screen		"HD[1]" LeftOf "HD[0]"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

EndSection
```

What can I do to get my second monitor to display independently?  Currently, it's got cloned output.

---

### Post by Annirak on 2008-04-07
There must be someone out there who has an idea of where to start on this.

---

### Post by asbjorne08 on 2008-04-07
check for xinerama (in config files and on google).

I can't send you a config file, cause I haven't such a config myself at hand right now, but I'm certain you can figure this one if you get to enable xinerama.

-- 
a

---

### Post by tommyarmour on 2008-04-12
simple install a program called Envy, this program enables you to install the most current ati driver. once you install Envy, go to applications then system tools run envy install ati driver automatically, Then you look under applications, acessories there will be a ati catalyst control center. Enable one big screen. One thing you will want to know, after you install compiz settings mananger you will need to change general options, display settings then disable detect output and type in the following in the Outputs section 1280x1024+0+0,1280x1024+0+0 this is the only way you can spin one large cube on both screens

---

### Post by broas on 2008-04-14
hi, :)

i'm trying to learn ubuntu but i'm no good at it. currently running 7.10 gutsy.

my setup is similar to Annirak's.
MB = p35e
core2 Q6600
4GB DDR2-800
ATI HD3870

to Annirak - how did you manage to make Radeon HD 3870 to work?

i tried the binary drivers and the envy method. maybe i'm doing something wrong. so i'm asking. thanks.

---

