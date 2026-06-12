---
title: "ubuntu-desktop GF 6600 install problems"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by Deadheded on 2007-06-10
I installed Ubuntu Server 6.06 LTS and samba on my new server without much problem.  I now need to install the ubuntu-desktop for some that can't use CLI.

*apt-get install ubuntu-desktop *

Install the Nvidia drivers

*apt-get install nvidia-glx*

Then configure

*dpkg-reconfigure -phigh xserver-xorg*

No mater what I do I get the same two screen patterns.  One of thin blue and green vertical lines and the other a much more dense mishmash of vertical lines and small squares.

My setup is:

Tyan Tiger with 2 duel core AMD Opterons
XFX GF 6600 GT 128MB DDR3 Duel DVI TV video card
2 512 Corsair mem chips
2 Seagate 37Gb SATA hard drives in a RAID1 config
Samsung SyncMaster 750s monitor


I have checked my vertical and horizontal refresh and also tried a different monitor with the same exact results.

I check my BusID and it is correct according to *lspci -X*

I started from scratch 2 weeks ago learning by doing my first Linux PDC and have been able to get through all problems with the help of google and a ton of reading.  Now I am able to do a  PDC install in about 5 hours.  I have looked high and low and can not figure out what is the display problem I am having.  I get the menu display when I boot to the install CD but never get xwindows to display correctly, even in safe mode.  The log file shows support for my chipset.  I am very much a noob to the linux world but have jumped in with both feet.  I am sure I have done something stupid but could really use a hand in pointing it out.

Here is my xorg.conf:

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by pt123 on 2007-06-10
Similar card, I have never had success running the the restricted nvidia drivers Ubuntu.

But I have had success using the driver installation run package @ the nvidia site.

Not hard to follow either:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

It was very good at picking up monitor and its capability.

---

### Post by Deadheded on 2007-06-10
If I use the ".run" file from Nvidia I have to install gcc and the kernel source files because it wants to build a new kernel for my system.

Is this what I am to expect in order to load the drivers?

---

### Post by pt123 on 2007-06-10
yes it compiles the kernel

---

