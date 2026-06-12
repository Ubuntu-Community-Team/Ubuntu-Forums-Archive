---
title: "1440x900 does not work after upgrade from feisty"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by seespatz on 2008-01-18
I just upgraded from feisty to gutsy. Before I had my ATI radeon x 1400 working with the driver from ati on a resolution of 1440 x 900. I used envy to install it and it worked.
After the upgrade I can only do max. 1280 x 720.
Before the upgrade deinstalled the driver and afterwards I installed an actual version of envy and reinstalled the driver. I tried both the new (envy created) and the old (mine -> the working one) version of xorg.conf. Didn't help.

I remember I also had problems, when I first installed feisty (over a year ago). But then I found a script on the web, which took care of this (some kind of "dpkg- and apt-get-Vodoo). But I can't find the site anymore.

PC: DELL Inspiron 9400
Graphics: ATI Radeon Mobility x1400

```

seespatz@terra:~$ lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
seespatz@terra:~$ 

seespatz@terra:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7170 Release
seespatz@terra:~$ 


```

xorg.conf (mine):
```


Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
	
	# path to defoma fonts
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"dri"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	Defaultdepth	24
	SubSection "Display"
		Viewport	0	0
		Depth	24
		Modes		"1440x900"
	EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "ServerFlags"
	Option		"AIGLX"	"off"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

Xorg.0.log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.2)
Current Operating System: Linux terra 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 19 00:44:08 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
(**) Option "AIGLX" "off"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(WW) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(**) Extension "Composite" is enabled
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1028,01cd rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,27a1 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1028,01cd rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:3: chip 8086,27d6 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01cd rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01cd rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01cd rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01cd rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01cd rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1028,01cd rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1028,01cd rev 01 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01cd rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 1002,7145 card 1028,2002 rev 00 class 03,00,00 hdr 00
(II) PCI: 03:00:0: chip 14e4,170c card 1028,01cd rev 02 class 02,00,00 hdr 00
(II) PCI: 03:01:0: chip 1180,0832 card 1028,01cd rev 00 class 0c,00,10 hdr 80
(II) PCI: 03:01:1: chip 1180,0822 card 1028,01cd rev 19 class 08,05,01 hdr 80
(II) PCI: 03:01:2: chip 1180,0843 card 1028,01cd rev 01 class 08,80,00 hdr 80
(II) PCI: 03:01:3: chip 1180,0592 card 1028,01cd rev 0a class 08,80,00 hdr 80
(II) PCI: 03:01:4: chip 1180,0852 card 1028,01cd rev 05 class 08,80,00 hdr 80
(II) PCI: 0c:00:0: chip 8086,4222 card 8086,1021 rev 02 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,13), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xefd00000 - 0xefefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 11: bridge is at (0:28:0), (0,11,11), BCTRL: 0x0002 (VGA_EN is cleared)
(II) PCI-to-PCI bridge:
(II) Bus 12: bridge is at (0:28:1), (0,12,12), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 12 non-prefetchable memory range:
	[0] -1	0	0xefc00000 - 0xefcfffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 13: bridge is at (0:28:3), (0,13,14), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 13 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 13 non-prefetchable memory range:
	[0] -1	0	0xefa00000 - 0xefbfffff (0x200000) MX[B]
(II) Bus 13 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe01fffff (0x200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:30:0), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xef900000 - 0xef9fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Radeon Mobility X1400 rev 0, Mem @ 0xd0000000/28, 0xefdf0000/16, I/O @ 0xee00/8, BIOS @ 0xefe00000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xefcff000 - 0xefcfffff (0x1000) MX[B]
	[1] -1	0	0xef9fd700 - 0xef9fd7ff (0x100) MX[B]
	[2] -1	0	0xef9fd600 - 0xef9fd6ff (0x100) MX[B]
	[3] -1	0	0xef9fd500 - 0xef9fd5ff (0x100) MX[B]
	[4] -1	0	0xef9fd400 - 0xef9fd4ff (0x100) MX[B]
	[5] -1	0	0xef9fd800 - 0xef9fdfff (0x800) MX[B]
	[6] -1	0	0xef9fe000 - 0xef9fffff (0x2000) MX[B]
	[7] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[8] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[9] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[10] -1	0	0xefdf0000 - 0xefdfffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[13] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xefcff000 - 0xefcfffff (0x1000) MX[B]
	[1] -1	0	0xef9fd700 - 0xef9fd7ff (0x100) MX[B]
	[2] -1	0	0xef9fd600 - 0xef9fd6ff (0x100) MX[B]
	[3] -1	0	0xef9fd500 - 0xef9fd5ff (0x100) MX[B]
	[4] -1	0	0xef9fd400 - 0xef9fd4ff (0x100) MX[B]
	[5] -1	0	0xef9fd800 - 0xef9fdfff (0x800) MX[B]
	[6] -1	0	0xef9fe000 - 0xef9fffff (0x2000) MX[B]
	[7] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[8] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[9] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[10] -1	0	0xefdf0000 - 0xefdfffff (0x10000) MX[B](B)
	[11] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[13] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[14] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[15] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[16] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[18] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[19] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[20] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[21] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[22] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xefcff000 - 0xefcfffff (0x1000) MX[B]
	[5] -1	0	0xef9fd700 - 0xef9fd7ff (0x100) MX[B]
	[6] -1	0	0xef9fd600 - 0xef9fd6ff (0x100) MX[B]
	[7] -1	0	0xef9fd500 - 0xef9fd5ff (0x100) MX[B]
	[8] -1	0	0xef9fd400 - 0xef9fd4ff (0x100) MX[B]
	[9] -1	0	0xef9fd800 - 0xef9fdfff (0x800) MX[B]
	[10] -1	0	0xef9fe000 - 0xef9fffff (0x2000) MX[B]
	[11] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[12] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[13] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[14] -1	0	0xefdf0000 - 0xefdfffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[19] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) LoadModule: "i2c"(II) Module already built-in
(II) LoadModule: "ddc"(II) Module already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(**) AIGLX disabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.44.3
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"
	compiled for 4.2.0, module version = 1.0.0
	Module class: XFree86 XInput Driver
	ABI class: XFree86 XInput driver, version 0.3
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.44.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.443.1                  
(II) ATI Proprietary Linux Driver Build Date: Dec 19 2007 21:29:14
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x7145) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xefcff000 - 0xefcfffff (0x1000) MX[B]
	[5] -1	0	0xef9fd700 - 0xef9fd7ff (0x100) MX[B]
	[6] -1	0	0xef9fd600 - 0xef9fd6ff (0x100) MX[B]
	[7] -1	0	0xef9fd500 - 0xef9fd5ff (0x100) MX[B]
	[8] -1	0	0xef9fd400 - 0xef9fd4ff (0x100) MX[B]
	[9] -1	0	0xef9fd800 - 0xef9fdfff (0x800) MX[B]
	[10] -1	0	0xef9fe000 - 0xef9fffff (0x2000) MX[B]
	[11] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[12] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[13] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[14] -1	0	0xefdf0000 - 0xefdfffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[19] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[20] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[21] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[22] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[24] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[25] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[26] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[27] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[28] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x8208a00
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xefcff000 - 0xefcfffff (0x1000) MX[B]
	[5] -1	0	0xef9fd700 - 0xef9fd7ff (0x100) MX[B]
	[6] -1	0	0xef9fd600 - 0xef9fd6ff (0x100) MX[B]
	[7] -1	0	0xef9fd500 - 0xef9fd5ff (0x100) MX[B]
	[8] -1	0	0xef9fd400 - 0xef9fd4ff (0x100) MX[B]
	[9] -1	0	0xef9fd800 - 0xef9fdfff (0x800) MX[B]
	[10] -1	0	0xef9fe000 - 0xef9fffff (0x2000) MX[B]
	[11] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[12] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[13] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[14] -1	0	0xefdf0000 - 0xefdfffff (0x10000) MX[B](B)
	[15] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[22] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[23] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[24] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[25] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[27] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[28] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[29] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[30] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[31] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin, [x]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(**) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Mobility Radeon X1400" (Chipset = 0x7145)
(--) fglrx(0): (PciSubVendor = 0x1028, PciSubDevice = 0x2002)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xefdf0000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 9.12
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: M54P
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.44.3
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR2
(II) fglrx(0): PCIE card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) fglrx(0): Connected Display1: LCD on internal LVDS [lvds]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: LPL  Model: 0  Serial#: 0
(II) fglrx(0): Year: 2005  Week: 0
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Digital Display Input
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 37  vert.: 23
(II) fglrx(0): Gamma: 2.20
(II) fglrx(0): No DPMS capabilities specified; RGB/Color Display
(II) fglrx(0): First detailed timing is preferred mode
(II) fglrx(0): redX: 0.592 redY: 0.344   greenX: 0.319 greenY: 0.553
(II) fglrx(0): blueX: 0.159 blueY: 0.144   whiteX: 0.312 whiteY: 0.328
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 96.2 MHz   Image Size:  367 x 230 mm
(II) fglrx(0): h_active: 1440  h_sync: 1504  h_sync_end 1536 h_blank_end 1760 h_border: 0
(II) fglrx(0): v_active: 900  v_sync: 901  v_sync_end 904 v_blanking: 912 v_border: 0
(II) fglrx(0):  YD477171WX2
(II) fglrx(0):  &5@ImÈÿ
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff00320c000000000000
(II) fglrx(0): 	000f0103802517780a8ef09758518d28
(II) fglrx(0): 	24505400000001010101010101010101
(II) fglrx(0): 	0101010101019525a04051840c304020
(II) fglrx(0): 	13006fe6100000190000000000000000
(II) fglrx(0): 	00000000000000000000000000fe0059
(II) fglrx(0): 	44343737023137315758320a000000fe
(II) fglrx(0): 	00263540496d9dc8ff02010a202000cd
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - LCD on internal LVDS
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(II) fglrx(0): POWERplay version 3.  5 power states available:
(II) fglrx(0):   1. 432/396MHz @ 60Hz [enable load balancing]
(II) fglrx(0):   2. 324/135MHz @ 60Hz [low voltage, enable sleep]
(II) fglrx(0):   3. 324/135MHz @ 60Hz [low voltage, enable sleep, thermal diode mode]
(II) fglrx(0):   4. 392/252MHz @ 60Hz [enable sleep]
(II) fglrx(0):   5. 392/252MHz @ 60Hz [enable sleep, thermal diode mode]
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 12 modes found for primary display.
(--) fglrx(0): Virtual size is 1280x720 (pitch 0)
(**) fglrx(0): *Mode "1280x720": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   96.21  1280 1504 1536 1760  720 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.21  1152 1504 1536 1760  864 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   96.21  1024 1504 1536 1760  768 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   96.21  800 1504 1536 1760  600 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   96.21  720 1504 1536 1760  480 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   96.21  640 1504 1536 1760  480 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   96.21  640 1504 1536 1760  432 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   96.21  640 1504 1536 1760  400 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   96.21  512 1504 1536 1760  384 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   96.21  400 1504 1536 1760  300 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   96.21  320 1504 1536 1760  240 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   96.21  320 1504 1536 1760  200 901 904 912 +hsync +vsync
(--) fglrx(0): Display dimensions: (370, 230) mm
(--) fglrx(0): DPI set to (87, 79)
(--) fglrx(0): Virtual size is 1280x720 (pitch 1280)
(**) fglrx(0): *Mode "1280x720": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"   96.21  1280 1504 1536 1760  720 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1152x864": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   96.21  1152 1504 1536 1760  864 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "1024x768": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   96.21  1024 1504 1536 1760  768 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   96.21  800 1504 1536 1760  600 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "720x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"   96.21  720 1504 1536 1760  480 901 904 912 +hsync +vsync
(**) fglrx(0): *Mode "640x480": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   96.21  640 1504 1536 1760  480 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "640x432": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x432"   96.21  640 1504 1536 1760  432 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   96.21  640 1504 1536 1760  400 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "512x384": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   96.21  512 1504 1536 1760  384 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "400x300": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "400x300"   96.21  400 1504 1536 1760  300 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "320x240": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x240"   96.21  320 1504 1536 1760  240 901 904 912 +hsync +vsync
(**) fglrx(0):  Default mode "320x200": 96.2 MHz (scaled from 0.0 MHz), 54.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "320x200"   96.21  320 1504 1536 1760  200 901 904 912 +hsync +vsync
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) fglrx(0): HPV inactive
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 256 MB
(II) fglrx(0): [pcie] 258048 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xefdf0000 - 0xefdfffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xefcff000 - 0xefcfffff (0x1000) MX[B]
	[7] -1	0	0xef9fd700 - 0xef9fd7ff (0x100) MX[B]
	[8] -1	0	0xef9fd600 - 0xef9fd6ff (0x100) MX[B]
	[9] -1	0	0xef9fd500 - 0xef9fd5ff (0x100) MX[B]
	[10] -1	0	0xef9fd400 - 0xef9fd4ff (0x100) MX[B]
	[11] -1	0	0xef9fd800 - 0xef9fdfff (0x800) MX[B]
	[12] -1	0	0xef9fe000 - 0xef9fffff (0x2000) MX[B]
	[13] -1	0	0xffa80000 - 0xffa803ff (0x400) MX[B]
	[14] -1	0	0xefffc000 - 0xefffffff (0x4000) MX[B]
	[15] -1	0	0xefe00000 - 0xefe1ffff (0x20000) MX[B](B)
	[16] -1	0	0xefdf0000 - 0xefdfffff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000ee00 - 0x0000eeff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x000010c0 - 0x000010df (0x20) IX[B]
	[25] -1	0	0x0000bfa0 - 0x0000bfaf (0x10) IX[B]
	[26] -1	0	0x00000374 - 0x00000374 (0x1) IX[B]
	[27] -1	0	0x00000170 - 0x00000177 (0x8) IX[B]
	[28] -1	0	0x000003f4 - 0x000003f4 (0x1) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[30] -1	0	0x0000bf20 - 0x0000bf3f (0x20) IX[B]
	[31] -1	0	0x0000bf40 - 0x0000bf5f (0x20) IX[B]
	[32] -1	0	0x0000bf60 - 0x0000bf7f (0x20) IX[B]
	[33] -1	0	0x0000bf80 - 0x0000bf9f (0x20) IX[B]
	[34] -1	0	0x0000ee00 - 0x0000eeff (0x100) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.0
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -19
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0x2000
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0xb7c15000
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.44.3
(II) fglrx(0):     Date: Dec 19 2007
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.22-14-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00004000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x01000400
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,3277)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,720) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1280 x 2557
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(**) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 16
(II) fglrx(0): GLESX is enabled
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		19 256x256 slots
		5 512x512 slots
(II) fglrx(0): Acceleration enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
[atiddx] ASYNCIO init succeed!
(==) fglrx(0): Silken mouse enabled
(==) fglrx(0): Using hardware cursor
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "de"
(**) Generic Keyboard: XkbLayout: "de"
(**) Option "XkbVariant" "nodeadkeys"
(**) Generic Keyboard: XkbVariant: "nodeadkeys"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(**) Option "HorizScrollDelta" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event6
(**) Option "Device" "/dev/input/event6"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?

```

Any help is greatly appreciated.

---

### Post by seespatz on 2008-01-18
Ok, now I managed to get the resolution by using the "xorg-driver-fglrx":

first I started envy and removed the driver from ATI. Then:

```

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo modprobe fglrx
sudo /etc/init.d/gdm restart

```

Then I had to outcomment a part of xorg.conf:

```

...
Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

#Section "Device"
#	Identifier  "aticonfig-Device[0]"
#	Driver      "vesa"
#EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
EndSection
...

```

It works now with 1440x900. But I would like to get the original ATI driver to work. Any suggestions?

---

### Post by Pumalite on 2008-01-18
Stay put.

---

