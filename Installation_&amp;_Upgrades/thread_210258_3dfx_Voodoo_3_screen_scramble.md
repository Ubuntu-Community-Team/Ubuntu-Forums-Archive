---
title: "3dfx Voodoo 3 screen scramble"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by tomhollis on 2006-07-06
Hi,

I have recently upgraded to the latest version of ubuntu and cannot find any explanation for the problem I am having anywhere else.

The screen is all scrambled and although there is clearly something there, it cannot be seen properly. The xorg.conf is exactly as it has been in previous versions of Ubuntu when it has worked fine. I have included it anyway. I have tried reconfiguring the xserver-xorg package, but that didn't help. I am using a voodoo 3 2000 card.

Can anyone make any further suggestions?

Thanks

Tom

```


Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
	Driver		"tdfx"
	BusID		"PCI:1:10:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768"  "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by tomhollis on 2006-07-06
I forgot to mention, the livecd is exactly the same

Tom

---

### Post by tomhollis on 2006-07-09
I have checked the xorg log file and found a few issues, can anyone help please?

```
(II) TDFX(1): Softbooting the board (through the int10 interface).
Requesting insufficient memory window!: start: 0xe0000000 end: 0xe1ffffff size 0xde090000
Requesting insufficient memory window!: start: 0xdc000000 end: 0xdfffffff size 0xde090000
Requesting insufficient memory window!: start: 0xe0000000 end: 0xe1ffffff size 0xde090000
Requesting insufficient memory window!: start: 0xdc000000 end: 0xdfffffff size 0xde090000
Requesting insufficient memory window!: start: 0xe0000000 end: 0xe1ffffff size 0xde090000
Requesting insufficient memory window!: start: 0xdc000000 end: 0xdfffffff size 0xde090000
(EE) TDFX(1): Cannot read V_BIOS
(WW) TDFX(1): Softbooting the board failed.
(II) TDFX(1): TDFXFindChips: found 1 chip(s)
(**) TDFX(1): Depth 16, (--) framebuffer bpp 16
(==) TDFX(1): RGB weight 565
(==) TDFX(1): Default visual is TrueColor
(**) TDFX(1): Option "DRI" "false"
(--) TDFX(1): Chipset: "3dfx Voodoo3"

```

```
(**) TDFX(1): VideoRAM: 16384 kByte Mapping 32768 kByte
(==) TDFX(1): Using gamma correction (1.0, 1.0, 1.0)
(II) TDFX(1): CTX VL700: Using hsync range of 30.00-70.00 kHz
(II) TDFX(1): CTX VL700: Using vrefresh range of 50.00-160.00 Hz
(II) TDFX(1): Clock range:  12.00 to 300.00 MHz
(II) TDFX(1): Not using default mode "1280x960" (hsync out of range)
(II) TDFX(1): Not using default mode "640x480" (hsync out of range)
(II) TDFX(1): Not using default mode "1280x1024" (hsync out of range)
(II) TDFX(1): Not using default mode "640x512" (hsync out of range)
(II) TDFX(1): Not using default mode "1280x1024" (hsync out of range)
(II) TDFX(1): Not using default mode "640x512" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1600x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "800x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1792x1344" (hsync out of range)
(II) TDFX(1): Not using default mode "896x672" (hsync out of range)
(II) TDFX(1): Not using default mode "1792x1344" (hsync out of range)
(II) TDFX(1): Not using default mode "896x672" (hsync out of range)
(II) TDFX(1): Not using default mode "1856x1392" (hsync out of range)
(II) TDFX(1): Not using default mode "928x696" (hsync out of range)
(II) TDFX(1): Not using default mode "1856x1392" (hsync out of range)
(II) TDFX(1): Not using default mode "928x696" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1440" (hsync out of range)
(II) TDFX(1): Not using default mode "960x720" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1440" (hsync out of range)
(II) TDFX(1): Not using default mode "960x720" (hsync out of range)
(II) TDFX(1): Not using default mode "1152x864" (hsync out of range)
(II) TDFX(1): Not using default mode "576x432" (hsync out of range)
(II) TDFX(1): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(1): Not using default mode "700x525" (hsync out of range)
(II) TDFX(1): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(1): Not using default mode "700x525" (hsync out of range)
(II) TDFX(1): Not using default mode "1400x1050" (unknown reason)
(II) TDFX(1): Not using default mode "700x525" (hsync out of range)
(II) TDFX(1): Not using default mode "1680x1050" (hsync out of range)
(II) TDFX(1): Not using default mode "840x525" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "960x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1200" (hsync out of range)
(II) TDFX(1): Not using default mode "960x600" (hsync out of range)
(II) TDFX(1): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) TDFX(1): Not using default mode "960x720" (hsync out of range)
(II) TDFX(1): Not using default mode "2048x1536" (hsync out of range)
(II) TDFX(1): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(1): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) TDFX(1): Not using default mode "1024x768" (hsync out of range)
(II) TDFX(1): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) TDFX(1): Not using default mode "1024x768" (hsync out of range)
(--) TDFX(1): Virtual size is 1280x1024 (pitch 1280)
(**) TDFX(1): *Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(II) TDFX(1): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) TDFX(1): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) TDFX(1): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) TDFX(1): *Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(II) TDFX(1): Modeline "800x600"   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) TDFX(1): *Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(II) TDFX(1): Modeline "640x480"   36.00  640 696 752 832  480 481 484 509 -hsync -vsync
(==) TDFX(1): DPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules/libfb.so
```

I have tried defining the hsync and vsync for my monitor, but it does not make any difference. Can anyone suggest anything at all? By the sound of it quite a few people have their voodoo 3 working in Dapper, if you do could you post your config file so I can try that?

Thanks

Tom

---

### Post by jerryf70 on 2006-07-15
Tom, I assume you've done:

$ sudo dpkg-reconfigure xserver-xorg

And reconfigured? That always fixes things for me, though I did just carry over xorg.conf from 5.10 to 6.06.

Here it is:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

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
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
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
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
	Driver		"tdfx"
	BusID		"PCI:2:10:0"
EndSection

Section "Monitor"
	Identifier	"Acer AL511"
	Option		"DPMS"
	HorizSync	28-49
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"Acer AL511"
	DefaultDepth	16
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
```

HTH

---

### Post by McQuaid on 2006-07-24
jerryf70 does opengl work for you with your voodoo 3?  I have a voodoo3 pci as well and 2d works fine, but never could get opengl working in dapper(or breezy for that matter).

---

### Post by tomhollis on 2006-07-24
I have tried the reconfigure, and I copied the posted xorg file, except for some essential changes and it still didn't work.

I do not have opengl working as I do not have 2D yet. 

Bizzarely if I have been playing with the 3dfx card in linux I have to unplug my computer for a few seconds or windows does not start, it seems it cannot activate the card either. Is fine after unplugging though.

Tom

---

### Post by FadeFX on 2008-04-29
try this in your xorg.conf
```

Section "Device"
	Identifier	"3Dfx Interactive, Inc. Voodoo 3"
	Driver		"tdfx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
	ModeLine "640x480PAL"   29.50       640  675  678  944  480  530  535  625
	ModeLine "800x600PAL"   36.00       800  818  820  960  600  653  655  750
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"3Dfx Interactive, Inc. Voodoo 3"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1152x864" "1024x768" "800x600"
	EndSubSection
	Subsection "Display"
                Depth 16
#               Modes "1024x768" "640x480" "800x600" "800x600PAL" #"400x300"
                Modes "1024x768" "800x600PAL" # "800x600NTSC" ...
        EndSubSection
EndSection

```

i fiddled arround trying to get tv-out running on my voodoo3 3000, did not get it running, but after trying another graphics board (ati rage 128 ) and not getting it runnin either i expirienced the same problems like you. i took this from an old xorg.conf and switched the computer off (without shuting down ubuntu) after next reboot it worked for me...

---

