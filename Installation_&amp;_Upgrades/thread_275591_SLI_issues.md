---
title: "SLI issues"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by Kacey on 2006-10-11
I have been seen that there are allot of people who are having a issue with the install where they get everything loaded then get a black screen with a flashing cursor. The login sounds play but nothing is displayed. You can still press ctrl+alt+1 and look at the xorg.conf file but as to what to place in there is still a mystery. I have concluded that this is due to SLI as almost all the posts of people having this problem are currently running SLI. 

  My question to the community is this, is there anyone who has SLI that faced this problem and found a work around and if so what was it? Also I am wondering if there is anyone who has SLI and DIDN'T have this issue and if so what cards do you have? Allot of the people affected have 6600's but I have 6800's so I don't think that it is a issue there, also I know that mine is listed as supported. 

  Maybe the alt. install would be the way to go, but it seems that this issue carries over to there as well, but I would think that after you got it setup and working you could then install the proper drivers.

  And for when you do get the install to work I did happen across a nice post about getting SLI setup
[http://www.ubuntuforums.org/showthread.php?t=272295&highlight=SLI]("http://www.ubuntuforums.org/showthread.php?t=272295&highlight=SLI")

---

### Post by Kacey on 2006-10-11
I am installing the on the other machine now and hope to have a better insite into the issue. I am starting to wonder if I can solve this, but if someone knows of anything I know of at lest 6 to 7 people who want to make the switch to ubuntu.

---

### Post by Kacey on 2006-10-16
So I got mine to work today, I changed the port on the PCI from 4:0:0 to 5:0:0, this is found in the device section of your xorg.conf. It may be diffrent numbers for other main boards but change it around and give it a try.

---

### Post by sandbagger on 2006-10-21
I got mine working by removing one of the cards, installing linux, then reinstalling the card. I'm still having trouble getting twinview to work though.

---

### Post by BeerMit on 2007-12-09
afterfinally achieving a stable setup i would like to share my experiences with SLI in Ubuntu

I DO have it working.
however, i want to point out some issues i am still having

>instead of outputing through the same card as windows, X outputs through the other card
(my PCIs are 2:0:0 and 3:0:0, windows and ubuntu output respectively. if you know how to fix this let me know)

>my monitor is shown (right model, wrong specs) as connected to one card, but disabled, and connected to the other car as generic monitor(right specs)

>this isnt really an issue but i too have experienced the blank screen with blinking cursor. for those who have experienced it as well, and wondered why they heard the login screen sound but saw no login screen, just switch to your other card, your video output got switched, like mine

details about my setup:

>for some reason the Nvidia driver wouldnt work at all. im currently using the "nv" driver

>ive been using Envy to experiment with my setup. i believe it is why  there are quite a few superflous entries in my xorg.conf. i keep taking them out because they just get confusing

>two 7600 GTs (one PCI is detected as 8x by Envy, the other 16x. I found this odd, they should both be 16x)


Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"int10"
	Load		"record"
	Load		"type1"
	Load		"vbe"
	Load		"glx"
	Load		"v4l"
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
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier	"AH191"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1440x900"
	Horizsync	31.5-56.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"device0"
	Boardname	"nv"
	Busid		"PCI:2:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"nv"
	Busid		"PCI:3:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"device0"
	Monitor		"AH191"
	Defaultdepth	24
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"False"
	Option		"SLI"	"auto"
	SubSection "Display"
		Depth	24
		Virtual	1440	900
		Modes		"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

EDIT: so really all my problem was i needed to change "device0" to "device1" in the "screen" section to get the output to the right card
i feel a bit dumb now :-P
i do ant to point out now that i can confirm SLI is running through Envy
and SLI + Compiz = hotness
well, for the most part
im getting mixed results from SFR and AFR
lets just say that Expo and unfolding the cube dont look too pretty (the background goes nuts)
still havent tried SLIAA

but now we can confirm
SLI in Ubuntu Gutsy 64
it is stable, for the most part
still havent tried it in any games
but its does play nicely with Compiz
again, for the most part :-P

I hope this helps someone who is as frustrated as i was :-)

---

