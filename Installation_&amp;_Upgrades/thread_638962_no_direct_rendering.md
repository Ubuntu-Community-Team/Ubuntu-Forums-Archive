---
title: "no direct rendering"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by adamb23 on 2007-12-12
ok here is my problem. I have installed the newest driver for my ati radeon pro 9800 graphics card through the restricted drivers manager. this is the error when i give the following command.
  glxinfo | grep rendering
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
this is a copy of my xorg file.
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
	Identifier	"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"DELL 1703FP"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]"
	Monitor		"DELL 1703FP"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"800x600"	"720x400"	"640x480"
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
Section "Device"
Identifier "aticonfig-Device[0]"
Driver "fglrx"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "DRI" "true"
Option "XAANoOffscreenPixmaps" "true"
EndSection

Does anyone know how to get direct rendering up and running? the video is really choppy in zsnes and my normal video files are choppy when in full screen mode. this is what happens when i type the command fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 PRO
OpenGL version string: 2.0.6958 Release

if anyone can help i would appreciate it ive been trying to find a solution to this problem for weeks and i know my graphics card can handle it, so thanks to anyone who helps.

---

### Post by adamb23 on 2007-12-13
bump

---

### Post by adamb23 on 2007-12-17
bump

---

