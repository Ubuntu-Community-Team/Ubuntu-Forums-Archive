---
title: "Framerate very low with opengl"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by scottiw2000 on 2010-04-17
When I run glxgears I only get framerates of around 50 fps. I also get flickering and jerkiness in the test video (the cube with gears). That fits what I find on the screen--docky is very slow and jerky. Any suggestions about why opengl is so slow? Here is some info to work with:

I'm running an ATI radeon hd4870 video card with the fglrx driver. The driver seems to be working, and glxinfo tells me that direct rendering is working. 

When I run glxgears I also get the message Using GLX_SGIX_pbuffer

**glxinfo | grep rendering**
gets result: direct rendering: Yes

**fglrxinfo**
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 4800 Series 
OpenGL version string: 3.2.9756 Compatibility Profile Context

**uname -a**
Linux ian-desktop-home 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

and here's the content of my **xorg.conf** file:

Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load "dri"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "TexturedVideoSync" "off"
	BusID       "PCI:1:0:0"
	Option 	    "DRI" "true"
	Option      "AllowGLXWithComposite" "true"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes    "1680x1050"
	EndSubSection
EndSection

Section "Extensions"
	Option "Composite" "enable"
EndSection

Section "DRI"
	Group "users"
	Mode 0666
EndSection

---

