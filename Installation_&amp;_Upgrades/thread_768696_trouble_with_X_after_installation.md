---
title: "trouble with X after installation"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by stefanoBelletti on 2008-04-26
hi to all.
I just installed Kubuntu 8.04 (the "alternate" cd, the standard one refused to install).
After rebooting, when X started, the screen is garbled (sounds like wrong frequency), the mouse pointer appears like a cross and it seems to work; there is no "application bar" on the bottom of the screen.
Switching to text-mode all is ok.
I'm not a linux guru, but i have some experience (palying with linux under xp/vmware since one year ).
So far i've played with:
-> xfix
-> dpkg-reconfigure xserver-org
to no avail.
The various logs in /var/log show no evident errors (at least: no evident to me :-(  )
The pc is an acer desktop with pentium 4, integrated (on-board) video card. 
There can i go from here ?
Is someone willing to help me ?
heeeelp !!!!

thank you !

:-)

---

### Post by Pumalite on 2008-04-26
Post:
cat /etc/X11/xorg.conf

---

### Post by stefanoBelletti on 2008-04-26
i've removed the comments
------------------------------
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
Section "Device"
	Identifier	"Configured Video Device"
EndSection
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
----------------------------------------
thank you for your help !

---

### Post by Pumalite on 2008-04-26
Here is mine. Don't copy it exactly, but get from it what useful to you. Yours leaves a lot to be desired.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"en"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by stefanoBelletti on 2008-04-26
the (integrated) video card is "ati radeon express 200"

---

### Post by stefanoBelletti on 2008-04-26
hi Puma, thank you !
i'll do (it'll take me some time with vim ... ;-)

---

### Post by Pumalite on 2008-04-26
You can use 'vesa' or 'ati' as the driver. You would do better with vesa. ATI driver almost never works.

---

### Post by stefanoBelletti on 2008-04-26
now i get a black screen with a floating window that says:
"Non optimum mode
recommended mode:
1280x1024 60Hz"
I guess this window is an "hardware" one : it's the monitor (samsung flat screen, model "samtron") that complains ... i guess.
Now i start googling for discovering how to tell X to use that resolution... but if someone could give me a hint .. ;-)

---

### Post by Pumalite on 2008-04-26
This might fit you better:

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"en"
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
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"E70f-10"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"E70f-10"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by stefanoBelletti on 2008-04-26
thx !

---

### Post by stefanoBelletti on 2008-04-26
Thank you Pumalite, unfortunately no luck, still the @#@[ window with:
"Non optimum mode
recommended mode:
1280x1024 60Hz"
Here's my actual xorg.conf 
----------------------------------------
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
#	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"		"true"	
EndSection
Section "Monitor"
	Identifier	"samtron73v"
	VendorName	"Samsung"
	ModelName	"Samtron 73v"
	HorizSync	30.0 - 81.0
	VertRefresh	56.000 - 75.000
#	VertRefresh	60   tried: no luck
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"samtron73v"
	Device		"Generic Video Card"
	Defaultdepth	24
	Subsection	"Display"
#	Modes	"1280x1024" "1280x960" "1152x864" "1024x768" "836x624"  tried: no luck
		Modes	"1280x1024"
		Depth	24
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
----------------------------------------
The only driver that works is "vesa" (nvidia: not found; ati: hangs)
horiz/vert values are from samsung manual
the correct model is "samtron 73 v"

i still need help !
:-)

---

### Post by Pumalite on 2008-04-26
Did you try Envy?:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by stefanoBelletti on 2008-04-26
Thank you Pumalite, unfortunately no luck, still the @#@[ window with:
"Non optimum mode
recommended mode:
1280x1024 60Hz"
Here's my actual xorg.conf 
----------------------------------------
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"it"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
#	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"		"true"	
EndSection
Section "Monitor"
	Identifier	"samtron73v"
	VendorName	"Samsung"
	ModelName	"Samtron 73v"
	HorizSync	30.0 - 81.0
	VertRefresh	56.000 - 75.000
#	VertRefresh	60   tried: no luck
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"samtron73v"
	Device		"Generic Video Card"
	Defaultdepth	24
	Subsection	"Display"
#	Modes	"1280x1024" "1280x960" "1152x864" "1024x768" "836x624"  tried: no luck
		Modes	"1280x1024@60"
		Depth	24
	EndSubSection
EndSection
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
----------------------------------------
The only driver that works is "vesa" (nvidia: not found; ati: hangs)
horiz/vert values are from samsung manual
the correct model is "samtron 73 v"
i've found the "Modeline" somewhere, googling around, but it looks useless

i still need help !
:-)

---

### Post by stefanoBelletti on 2008-04-26
Did you try Envy?:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
---------------------------------------------

No, I look at it right now !
thx again

---

### Post by stefanoBelletti on 2008-04-29
after some other googlin, and without installing any other video driver, i've built up an xorg.conf that works very well (only a couple of messages when shutting down X)
I want to thank a lot Pumalite for his support.

here's the xorg.conf, in case it could be usefull to someone else
------------------------------------------------------------------
Section "Module"
# This loads the DBE extension module.
    Load        "dbe"  	# Double buffer extension
# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection
# This loads the font modules
    Load        "type1"
    Load        "freetype"
# This loads the GLX module
    Load       "glx"
# This loads xtrap extension, used by xrandr
    Load       "xtrap"
EndSection
Section "Files"
    RgbPath	"/usr/X11R7/lib/X11/rgb"
    FontPath   "/usr/X11R7/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R7/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R7/lib/X11/fonts/TTF/"
EndSection
Section "ServerFlags"
    Option "RandR" "on"
EndSection
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection
Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option      "XkbRules" "xorg"
	Option      "XkbModel" "pc105"
	Option      "XkbLayout" "it" #xkeymap0
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
EndSection
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "STN"
	ModelName    "SAMTRON"
	Option	    "DPMS"
	EndSection

Section "Modes"
	Identifier "Modes0"
EndSection
Section "Device"
	Option     "NoAccel"   "true"         	# [<bool>]
	Identifier  "Card0"
	Driver      "ati" #card0driver
	VendorName  "ATI Technologies Inc"
	BoardName   "RS400 [Radeon Xpress 200]"
	BusID       "PCI:1:5:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
    DefaultDepth 24
    Subsection "Display"
        Depth       24
        Modes       "1280x1024"
    EndSubsection
EndSection

---

### Post by Pumalite on 2008-04-29
Congrats!. Good for you. Good luck.

---

