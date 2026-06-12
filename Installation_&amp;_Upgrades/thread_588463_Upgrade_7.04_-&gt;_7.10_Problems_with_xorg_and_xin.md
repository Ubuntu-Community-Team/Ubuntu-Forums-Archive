---
title: "Upgrade: 7.04 -&gt; 7.10 Problems with xorg and xinerama"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by the_atlan on 2007-10-23
Hi folks,

<some blabla>:
I'm using kubuntu since a while now. Two years nearly, if not even longer. It's a cool community and kubuntu is a very nice distro.
So hi to you all cool freaks here

<the problem>:
I always had problems with upgrading to new debian/(k)ubuntu realeases. I hope this time this will be different, but, not that there where problems, not just what I'm up to here, I even wasn't able to find a solution in the forums this time. So I registered :-)

<the real problem>:
I ran Feisty with a xorg.conf with option "Xinerama" "true" and it was working perfect. After the upgrade this changed. When I set Xinerama to true in the new xorg.conf[1] the xserver crashes. Found that two lines in the Xorg.0.log[2]:

```
(WW) RADEON(1): Direct rendering is not supported when Xinerama is enabled
(EE) RADEON(1): [dri] DRIScreenInit failed.  Disabling DRI.

```
When I turn off Xinerama, then the xserver starts, but Screen1 is blank, though after a reboot and login via kdm Screen1 works, but not with xinerama, so that I have two instances of kde.

I searched the ubuntuforums.org for that Problem and there are people with similar sounding problems, but in the end it is yet different.

As I'm fixing the upgrade for two days now, I would be very happy to solve that problem as I had to work on this machine.

You can see the Hardware in the config file.

kind regards
Atlan

[1] xorg.conf:
```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
	Option 	       "Xinerama" "true"
        #Option         "clone" "off"
EndSection

#Section "ServerFlags"
#	Option	    "Xinerama" "1"
#EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
	Load  "GLcore"
	Load  "glx"
	Load  "record"
	Load  "xtrap"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Imagequest L72D"
        HorizSync    30.0 - 80.0
        VertRefresh  50.0 - 75.0
        Option      "DPMS"
        DisplaySize      340   270    #mm
EndSection

Section "Monitor"
	DisplaySize       310   230     # mm
        Identifier   "Monitor1"
        VendorName   "PHL"
        ModelName    "BL 151AX"
        HorizSync    30.0 - 61.0
        VertRefresh  56.0 - 75.0
        Option      "DPMS"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nv"
	VendorName  "nVidia Corporation"
	BoardName   "NV20 [GeForce3 Ti 200]"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "Card1"
	Driver      "ati"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon RV100 QY [Radeon 7000/VE]"
	BusID       "PCI:1:9:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	DefaultDepth 24

        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes     "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes     "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	DefaultDepth 24

	SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes     "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes     "1024x768" "800x600" "640x480"
        EndSubSection

EndSection
```




[2] Xorg.0.log:
```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux atlan 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 23 19:40:30 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "X.org Configured"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Card0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Card1"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
(**) Option "Xinerama" "true"
(**) Xinerama: enabled
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
(**) RgbPath set to "/etc/X11/rgb"
(**) ModulePath set to "/usr/lib/xorg/modules"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 1274,1371 card 1274,1371 rev 06 class 04,01,00 hdr 00
(II) PCI: 01:08:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:09:0: chip 1002,5159 card 174b,7c02 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 10de,0201 card 0000,0000 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI: (1:9:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xc8000000/27, 0xe9000000/16, I/O @ 0xc800/8
(--) PCI:*(2:0:0) nVidia Corporation NV20 [GeForce3 Ti 200] rev 163, Mem @ 0xe0000000/24, 0xd0000000/27, 0xd8000000/19
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
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xc7ffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[1] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[2] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[3] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[4] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[5] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[12] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[1] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[1] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[2] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[3] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[4] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[5] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[10] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[11] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[12] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[13] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[1] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
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
	[4] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[5] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[6] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[7] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[8] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[9] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[15] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "xtrap"
(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DEC-XTRAP
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 2.1.5
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
	GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
	GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
	GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
	GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
	GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
	GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
	GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
	Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
	GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
	GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
	GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
	GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
	GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
	Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
	GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
	GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
	Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
	GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
	GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
	GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
	Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
	GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
	GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
	GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
	GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
	GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
	GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
	GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
	Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
	GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
	GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
	Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
	Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
	GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
	GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
	GeForce 8600 GT, GeForce 8400 GS, GeForce 8600M GT, GeForce 8700M GT,
	Quadro FX 370, Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M,
	Quadro FX 570, Quadro FX 1700, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, Quadro FX 360M, Quadro NVS 290
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 02:00:0
(--) Chipset GeForce3 Ti 200 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[5] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[6] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[7] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[8] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[9] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[15] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(--) Chipset ATI Radeon VE/7000 QY (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[5] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[6] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[7] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[8] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[9] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[15] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[5] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[6] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[7] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[8] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[9] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[15] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[20] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[21] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[31] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
	[34] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[35] 1	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Setting vga for screen 1.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce3 Ti 200"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xD0000000
(--) NV(0): MMIO registers at 0xE0000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0): I2C device "DDC:ddc2" removed.
(II) NV(0):   ... none found
(--) NV(0): HW is currently programmed for DFP
(II) NV(0): Using DFP on CRTC 0
(--) NV(0): Panel size is 1280 x 1024
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Monitor0: Using hsync range of 30.00-80.00 kHz
(II) NV(0): Monitor0: Using vrefresh range of 50.00-75.00 Hz
(II) NV(0): Clock range:  12.00 to 350.00 MHz
(II) NV(0): Not using default mode "640x350" (vrefresh out of range)
(II) NV(0): Not using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (vrefresh out of range)
(II) NV(0): Not using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "720x400" (vrefresh out of range)
(II) NV(0): Not using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (vrefresh out of range)
(II) NV(0): Not using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "800x600" (vrefresh out of range)
(II) NV(0): Not using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NV(0): Not using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x960" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1280x1024" (hsync out of range)
(II) NV(0): Not using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1792x1344" (exceeds panel dimensions)
(II) NV(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1856x1392" (exceeds panel dimensions)
(II) NV(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NV(0): Not using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1400x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1440x900" (exceeds panel dimensions)
(II) NV(0): Not using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1600x1024" (exceeds panel dimensions)
(II) NV(0): Not using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1680x1050" (exceeds panel dimensions)
(II) NV(0): Not using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1200" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1920x1440" (exceeds panel dimensions)
(II) NV(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (exceeds panel dimensions)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NV(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(--) NV(0): Virtual size is 1280x1024 (pitch 1280)
(**) NV(0): *Driver mode "1280x1024": 90.8 MHz, 63.0 kHz, 59.8 Hz
(II) NV(0): Modeline "1280x1024"   90.75  1280 1328 1360 1440  1024 1027 1034 1054 +hsync -vsync
(**) NV(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) NV(0): *Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) NV(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) NV(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) NV(0): Display dimensions: (340, 270) mm
(**) NV(0): DPI set to (95, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) RADEON(1): MMIO registers at 0xe9000000: size 64KB
(II) RADEON(1): PCI bus 1 card 9 func 0
(**) RADEON(1): Depth 24, (--) framebuffer bpp 32
(II) RADEON(1): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(1): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Reloading /usr/lib/xorg/modules//libvgahw.so
(II) RADEON(1): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(1): RGB weight 888
(II) RADEON(1): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) RADEON(1): initializing int10
(II) Attempted to read BIOS 128KB from /sys/bus/pci/devices/0000:01:09.0/rom: got 0KB
Requesting insufficient memory window!: start: 0xe8000000 end: 0xe9ffffff size 0x8000000
(EE) Cannot find empty range to map base to
(EE) RADEON(1): Cannot read V_BIOS (3)
(WW) RADEON(1): Restoring MEM_CNTL (00000000), setting to 00002e00
(--) RADEON(1): Chipset: "ATI Radeon VE/7000 QY (AGP/PCI)" (ChipID = 0x5159)
(--) RADEON(1): Linear framebuffer at 0xc8000000
(II) RADEON(1): PCI card detected
(II) Attempted to read BIOS 64KB from /sys/bus/pci/devices/0000:01:09.0/rom: got 0KB
Requesting insufficient memory window!: start: 0xe8000000 end: 0xe9ffffff size 0x8000000
(EE) Cannot find empty range to map base to
(WW) RADEON(1): Video BIOS not detected in PCI space!
(WW) RADEON(1): Attempting to read Video BIOS from legacy ISA space!
(II) RADEON(1): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:09.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:09.0
(II) RADEON(1): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(1): Page Flipping disabled
(II) RADEON(1): Will try to use DMA for Xv image transfers
(II) RADEON(1): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(1): Mapped VideoRAM: 65536 kByte (64 bit DDR SDRAM)
(II) RADEON(1): Color tiling enabled by default
(II) RADEON(1): Max desktop size set to 2048x1200
(II) RADEON(1): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(1): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(1): PLL parameters: rf=18774 rd=17732 min=860239 max=15990784; xclk=59696
(II) RADEON(1): Bios Connector table: 
(II) RADEON(1): Port0: DDCType-5, DACType-0, TMDSType-0, ConnectorType-0
(II) RADEON(1): Port1: DDCType-14, DACType-0, TMDSType-0, ConnectorType-6
(II) RADEON(1): Port2: DDCType-14, DACType-1, TMDSType-0, ConnectorType-0
(II) RADEON(1): Port3: DDCType-6, DACType-0, TMDSType-0, ConnectorType-0
(II) RADEON(1): Output None using monitor section Monitor1
(II) RADEON(1): I2C bus "LCD_DDC" initialized.
(II) RADEON(1): Output S-video has no monitor section
(II) RADEON(1): Output None has no monitor section
(II) RADEON(1): Output None has no monitor section
(II) RADEON(1): Port0:
 Monitor   -- AUTO
 Connector -- None
 DAC Type  -- Primary
 TMDS Type -- Internal
 DDC Type  -- LCD_DDC
(II) RADEON(1): Port1:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- Primary
 TMDS Type -- Internal
 DDC Type  -- Proprietary/LVDS
(II) RADEON(1): Port2:
 Monitor   -- AUTO
 Connector -- None
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- Proprietary/LVDS
(II) RADEON(1): Port3:
 Monitor   -- AUTO
 Connector -- None
 DAC Type  -- Primary
 TMDS Type -- Internal
 DDC Type  -- Unknown
(II) RADEON(1): I2C device "LCD_DDC:ddc2" registered at address 0xA0.
(II) RADEON(1): I2C device "LCD_DDC:ddc2" removed.
(II) RADEON(1): DDC Type: 5, Detected Monitor Type: 0
(II) RADEON(1): Found color CRT connected to primary DAC
finished output detect: 0
finished output detect: 1
(WW) RADEON(1): DDC2/I2C is not properly initialized
(II) RADEON(1): DDC Type: 14, Detected Monitor Type: 0
finished output detect: 2
(WW) RADEON(1): DDC2/I2C is not properly initialized
(II) RADEON(1): DDC Type: 6, Detected Monitor Type: 0
(II) RADEON(1): Found color CRT connected to primary DAC
finished output detect: 3
finished all detect
before xf86InitialConfiguration
(II) RADEON(1): I2C device "LCD_DDC:ddc2" registered at address 0xA0.
(II) RADEON(1): I2C device "LCD_DDC:ddc2" removed.
(II) RADEON(1): DDC Type: 5, Detected Monitor Type: 0
(II) RADEON(1): Found color CRT connected to primary DAC
(II) RADEON(1): Output None connected
in RADEONProbeOutputModes
(II) RADEON(1): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(1): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(1): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(1): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(1): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1152x864" (hsync out of range)
(II) RADEON(1): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(1): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(1): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(1): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(1): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(1): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1152x768" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(1): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(1): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(1): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(1): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(1): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(1): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(1): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(1): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(1): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(1): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(1): Printing probed modes for output None
(II) RADEON(1): Modeline "1440x900"x60.2  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync (56.9 kHz)
(II) RADEON(1): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(1): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) RADEON(1): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) RADEON(1): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(1): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(1): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(1): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(1): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(1): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Output S-video disconnected
(II) RADEON(1): EDID for output S-video
(WW) RADEON(1): DDC2/I2C is not properly initialized
(II) RADEON(1): DDC Type: 14, Detected Monitor Type: 0
(II) RADEON(1): Output None disconnected
(II) RADEON(1): EDID for output None
(WW) RADEON(1): DDC2/I2C is not properly initialized
(II) RADEON(1): DDC Type: 6, Detected Monitor Type: 0
(II) RADEON(1): Found color CRT connected to primary DAC
(II) RADEON(1): Output None connected
in RADEONProbeOutputModes
(II) RADEON(1): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(1): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(1): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(1): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(1): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(1): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(1): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(1): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(1): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(1): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1280x960" (hsync out of range)
(II) RADEON(1): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(1): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1600x1200" (hsync out of range)
(II) RADEON(1): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1600x1200" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(1): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(1): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1152x768" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1400x1050" (hsync out of range)
(II) RADEON(1): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1400x1050" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1440x900" (hsync out of range)
(II) RADEON(1): Not using default mode "1600x1024" (hsync out of range)
(II) RADEON(1): Not using default mode "1680x1050" (hsync out of range)
(II) RADEON(1): Not using default mode "1920x1200" (hsync out of range)
(II) RADEON(1): Not using default mode "1920x1200" (vrefresh out of range)
(II) RADEON(1): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(1): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(1): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(1): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(1): Printing probed modes for output None
(II) RADEON(1): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) RADEON(1): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) RADEON(1): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(1): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(1): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(1): Output None connected
(II) RADEON(1): Output S-video disconnected
(II) RADEON(1): Output None disconnected
(II) RADEON(1): Output None connected
(II) RADEON(1): Output None using initial mode 1280x768
(II) RADEON(1): Output None using initial mode 1280x768
after xf86InitialConfiguration
(**) RADEON(1): Display dimensions: (310, 230) mm
(**) RADEON(1): DPI set to (117, 132)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Reloading /usr/lib/xorg/modules//libfb.so
(==) RADEON(1): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(1): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Reloading /usr/lib/xorg/modules//libxaa.so
(==) RADEON(1): Assuming overlay scaler buffer width is 1536
(II) RADEON(1): MM_TABLE: c3-66-be-04-08-68-00-e8-09-57-26-8a-45-0a
(II) RADEON(1): This card has MM_TABLE we do not recognize.
		If your card is TV-in capable you will need to specify options RageTheatreCrystal, RageTheatreTunerPort, 
		RageTheatreSVideoPort and TunerType in /etc/X11/xorg.conf.
(!!) RADEON(1): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(1): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] 1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B]
	[1] 1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
	[2] 0	0	0xd8000000 - 0xd807ffff (0x80000) MX[B]
	[3] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[4] 0	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B]
	[5] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[6] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[7] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[8] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[9] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[10] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[11] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[12] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[13] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[14] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[15] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[16] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[18] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[19] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[20] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[24] 1	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[25] 1	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[26] 1	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[27] 1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[31] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[32] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[33] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[34] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[35] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
	[40] 1	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[41] 1	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) NV(0): Write-combining range (0xd0000000,0x8000000)
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(**) Option "dpms"
(**) NV(0): DPMS enabled
(==) RandR enabled
(==) RADEON(1): Write-combining range (0xc8000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(==) RADEON(1): Using 24 bit depth buffer
(II) RADEON(1): RADEONInitMemoryMap() : 
(II) RADEON(1):   mem_size         : 0x04000000
(II) RADEON(1):   MC_FB_LOCATION   : 0xcbffc800
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(1): Depth moves disabled by default
(II) RADEON(1): CP in BM mode
(II) RADEON(1): Using 8 MB GART aperture
(II) RADEON(1): Using 1 MB for the ring buffer
(II) RADEON(1): Using 2 MB for vertex/indirect buffers
(II) RADEON(1): Using 5 MB for GART textures
(II) RADEON(1): Memory manager initialized to (0,0) (1472,8191)
(II) RADEON(1): Reserved area from (0,1200) to (1472,1202)
(II) RADEON(1): Largest offscreen area available: 1472 x 6989
(II) RADEON(1): Will use front buffer at offset 0x0
(II) RADEON(1): Will use back buffer at offset 0xd7a000
(II) RADEON(1): Will use depth buffer at offset 0x1437000
(II) RADEON(1): Will use 37888 kb for textures at offset 0x1af4000
(WW) RADEON(1): Direct rendering is not supported when Xinerama is enabled
(EE) RADEON(1): [dri] DRIScreenInit failed.  Disabling DRI.
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xcbffc800
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
init memmap
init common
init crtc2
init pll2
restore memmap
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xcbffc800
(II) RADEON(1):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc2
restore pll2
finished PLL2
restore dac
enable montype: 1
disable montype: 1
disable montype: 1
(==) RADEON(1): Backing store disabled
(WW) RADEON(1): Direct rendering disabled
(II) RADEON(1): Render acceleration enabled
(II) RADEON(1): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(1): Acceleration enabled
(**) Option "dpms"
(**) RADEON(1): DPMS enabled
(==) RADEON(1): Silken mouse enabled
(II) RADEON(1): Using hardware cursor (scanline 1202)
(II) RADEON(1): Largest offscreen area available: 1472 x 6986
(II) RADEON(1): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(1): no multimedia table present, disabling Rage Theatre.
(II) RADEON(1): RandR 1.2 enabled, ignore the following RandR disabled message.

Backtrace:
0: X(xf86SigHandler+0x81) [0x80c9581]
1: [0xffffe420]
2: X(xf86RandR12SetRotations+0x6b) [0x80fe2cb]
3: X(xf86CrtcScreenInit+0x9e) [0x80fa45e]
4: /usr/lib/xorg/modules/drivers//radeon_drv.so(RADEONScreenInit+0x17d2) [0xb7b97ca2]
5: X(AddScreen+0x1ee) [0x807653e]
6: X(InitOutput+0x21e) [0x80a86ce]
7: X(main+0x27b) [0x8076ceb]
8: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d88050]
9: X(FontFileCompleteXLFD+0x1e1) [0x8076241]

Fatal server error:
Caught signal 11.  Server aborting

(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
disable montype: 1
disable montype: 1
(II) RADEON(1): RADEONRestoreMemMapRegisters() : 
(II) RADEON(1):   MC_FB_LOCATION   : 0xffff0000
(II) RADEON(1):   MC_AGP_LOCATION  : 0x003fffc0
finished PLL2
finished PLL1
Entering Restore TV
Restore TV PLL
Restore TVHV
Restore TV Restarts
Restore Timing Tables
Restore TV standard
Leaving Restore TV
```

---

### Post by gronbaek on 2007-10-23
Hi Atlan

I don't know if any of this could help you, but there's some information about Xinerame (and other screen setups) in [this post]("http://ubuntuforums.org/showthread.php?t=221174") and also in [this post]("http://ubuntuforums.org/showthread.php?p=1773624"), which is also linked to from the first post. I use twinview and don't have any experience with xinerama, but the stuff in the posts helped me, and seemed pretty good quality. Take a look at it, maybe there is something that will help you.

---

### Post by the_atlan on 2007-10-24
Hi,
thx for the links, I already read them, but since there where no other replies to my problem, I tried something different.
I have a nvidia and an ati card, and wanted them to play togheter in a xinerama sandbox. But then I thought, I might use just the ATI radeon 7000/ve card, as it has two heads togther with [this post]("http://ubuntuforums.org/showthread.php?p=1773710").
I configured MergedFB in the xorg.conf and thought, that this problem led to a solution where I can use 3d acceleration AND have two monitors. But crap. I configured everything but the output was, that both monitors where showing the same content. So I played with it a little. With no problem solving result. Why? Because of RandR 1.2. This is what changed in Xorg 7.2, the version of Xorg shipped with the new Gutsy. So Someone posted a link to [this]("http://ubuntuforums.org/showthread.php?t=301961&page=12") where RandR is described a bit. I looked at it and thought: Cool. Nice tool.
But it's not working eather. Probably, somebody can tell me why? I would be very grateful.
Here is my xorg.conf:

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"BothScreens"
	InputDevice	"Mouse0" "CorePointer"
	InputDevice	"Keyboard0" "CoreKeyboard"
EndSection

Section "DRI"
	Mode	0666
EndSection
        
Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "Files"
	RgbPath      "/etc/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dbe"
	Load  "dri"
	Load  "GLcore"
	Load  "glx"
	Load  "record"
	Load  "xtrap"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "BigMonitor"
	VendorName   "Monitor Vendor"
	ModelName    "Imagequest L72D"
        HorizSync    30.0 - 80.0
        VertRefresh  50.0 - 75.0
        Option      "DPMS"
        DisplaySize      340   270    #mm
	Option	     "Position" "0 0"
EndSection

Section "Monitor"
	DisplaySize       310   230     # mm
        Identifier   "SmallMonitor"
        VendorName   "PHL"
        ModelName    "BL 151AX"
        HorizSync    30.0 - 61.0
        VertRefresh  56.0 - 75.0
        Option      "DPMS"
	Option	    "RightOf" "BigMonitor"
	Option	    "Position" "1280 0"
EndSection

Section "Device"
	Identifier  "AtiCard"
	Driver      "ati"
	VendorName  "ATI Technologies Inc"
	BoardName   "Radeon RV100 QY [Radeon 7000/VE]"
	BusID       "PCI:1:9:0"
	Option	    "TMDS" "BigMonitor"
	Option	    "CRT" "SmallMonitor"
EndSection

Section "Screen"
	Identifier "BothScreens"
	Device     "AtiCard"
	Monitor    "BigMonitor"
	DefaultDepth 24

        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes     "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
		Virtual	  2304 1024
        EndSubSection
EndSection
```

The result of this xorg.conf is, that I see the same things on both screens.
Here is the Xorg.0.log


```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux atlan 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 24 23:46:53 2007
(++) Using config file: "/etc/X11/xorg.conf_gutsy"
(==) ServerLayout "Default Layout"
(**) |-->Screen "BothScreens" (0)
(**) |   |-->Monitor "BigMonitor"
(**) |   |-->Device "AtiCard"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Keyboard0"
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
(**) RgbPath set to "/etc/X11/rgb"
(**) ModulePath set to "/usr/lib/xorg/modules"
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
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 10de,0c17 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a3 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a3 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a3 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev a2 class 06,04,00 hdr 01
(II) PCI: 01:07:0: chip 1274,1371 card 1274,1371 rev 06 class 04,01,00 hdr 00
(II) PCI: 01:08:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:09:0: chip 1002,5159 card 174b,7c02 rev 00 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 10de,0201 card 0000,0000 rev a3 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x020a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe8000000 - 0xe9ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xe7ffffff (0x8000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI:*(1:9:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xc8000000/27, 0xe9000000/16, I/O @ 0xc800/8
(--) PCI: (2:0:0) nVidia Corporation NV20 [GeForce3 Ti 200] rev 163, Mem @ 0xe0000000/24, 0xd0000000/27, 0xd8000000/19
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
(II) PCI Memory resource overlap reduced 0xc0000000 from 0xc7ffffff to 0xbfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[1] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[2] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[3] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[4] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[5] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[8] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[11] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[1] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[1] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[2] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[3] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[4] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[5] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[6] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[7] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[8] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[9] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[10] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[11] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[13] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[14] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[16] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[1] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[2] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
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
	[4] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[5] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[6] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[7] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[8] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[9] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[12] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "xtrap"
(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so
(II) Module xtrap: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DEC-XTRAP
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 6.7.195
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) ATI: ATI driver wrapper (version 6.7.195) for chipsets: mach64, rage128, radeon
(II) Primary Device is: PCI 01:09:0
(II) Loading sub module "radeon"
(II) LoadModule: "radeon"
(II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
(II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 4.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/PCI),
	ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
	ATI Radeon IGP330/340/350 (A4) 4137,
	ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP 4437,
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
	ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP),
	ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO IGP 7834,
	ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
	ATI FireGL RV360 AV (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
	ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
	ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
	ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
	ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
	ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE),
	ATI Radeon Mobility X600 (M24) 3150 (PCIE),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE),
	ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410) (PCIE),
	ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420) (AGP),
	ATI Radeon AIW X800 VE (R420) JT (AGP),
	ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430) (PCIE),
	ATI Radeon X850 5D4C (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP)
(--) Chipset ATI Radeon VE/7000 QY (AGP/PCI) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[5] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[6] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[7] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[8] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[9] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[12] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[20] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[22] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[25] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[5] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[6] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[7] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[8] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[9] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[10] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[11] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[12] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[13] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[22] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[25] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[26] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[27] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[28] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) RADEON(0): MMIO registers at 0xe9000000: size 64KB
(II) RADEON(0): PCI bus 1 card 9 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon VE/7000 QY (AGP/PCI)" (ChipID = 0x5159)
(--) RADEON(0): Linear framebuffer at 0xc8000000
(II) RADEON(0): PCI card detected
(II) RADEON(0): Legacy BIOS detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:09.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:09.0
(II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.27.0
(==) RADEON(0): Page Flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Detected total video RAM=65536K, accessible=65536K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 65536 kByte (64 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(WW) RADEON(0): Requested desktop size exceeds surface limts for tiling, ColorTiling disabled
(II) RADEON(0): Max desktop size set to 2304x1024
(II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
(II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module already built-in
(II) RADEON(0): PLL parameters: rf=2700 rd=60 min=12000 max=35000; xclk=15000
(II) RADEON(0): Bios Connector table: 
(II) RADEON(0): Port0: DDCType-3, DACType-0, TMDSType-0, ConnectorType-2
(II) RADEON(0): Port1: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Port5: DDCType-0, DACType-1, TMDSType-2, ConnectorType-6
(II) RADEON(0): Output VGA-0 using monitor section BigMonitor
(**) RADEON(0): Option "Position" "0 0"
(II) RADEON(0): I2C bus "VGA_DDC" initialized.
(II) RADEON(0): Output DVI-0 has no monitor section
(II) RADEON(0): I2C bus "DVI_DDC" initialized.
(II) RADEON(0): DFP table revision: 3
(II) RADEON(0): Output S-video has no monitor section
(II) RADEON(0): Default TV standard: PAL
(II) RADEON(0): TV standards supported by chip: NTSC PAL 
(II) RADEON(0): Port0:
 Monitor   -- AUTO
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- None
 DDC Type  -- VGA_DDC
(II) RADEON(0): Port1:
 Monitor   -- AUTO
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Port2:
 Monitor   -- AUTO
 Connector -- STV
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- None
 DDC Type  -- None
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 1510  Serial#: 64487
(II) RADEON(0): Year: 1999  Week: 45
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.630 redY: 0.340   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.140 blueY: 0.100   whiteX: 0.320 whiteY: 0.340
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 448 v_border: 0
(II) RADEON(0): Serial No:  TY  064487
(II) RADEON(0): Monitor name: BL 151AX
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 61 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c1015e7fb0000
(II) RADEON(0): 	2d0901010e1e1796e84ee0a1574c9923
(II) RADEON(0): 	195257bfee003140314f454f6140614f
(II) RADEON(0): 	010101010101d50980a0205e62101060
(II) RADEON(0): 	520833e610000000000000ff00205459
(II) RADEON(0): 	20203036343438370a20000000fc0042
(II) RADEON(0): 	4c2031353141580a20202020000000fd
(II) RADEON(0): 	00384b1e3d08000a20202020202000db
finished output detect: 0
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 3
(II) RADEON(0): Panel infos found from DDC detailed: 1280x1024
(II) RADEON(0): EDID data from the display on connector: DVI-I ----------------------
(II) RADEON(0): Manufacturer: HIQ  Model: 5003  Serial#: 20060208
(II) RADEON(0): Year: 2006  Week: 6
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 33  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  330 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 40.0 MHz   Image Size:  330 x 270 mm
(II) RADEON(0): h_active: 800  h_sync: 840  h_sync_end 968 h_blank_end 1056 h_border: 0
(II) RADEON(0): v_active: 600  v_sync: 601  v_sync_end 605 v_blanking: 628 v_border: 0
(II) RADEON(0): Ranges: V min: 59  V max: 61 Hz, H min: 31  H max: 67 kHz,
(II) RADEON(0): Monitor name: L72D DVI
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff002131035030183201
(II) RADEON(0): 	0610010380211b78eaaea5a6544c9926
(II) RADEON(0): 	14505421080031404540614081800101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	13004a0e1100001ea00f200031581c20
(II) RADEON(0): 	288014004a0e1100001e000000fd003b
(II) RADEON(0): 	3d1f43ff000a202020202020000000fc
(II) RADEON(0): 	004c373244204456490a2020202000f5
finished output detect: 1
finished output detect: 2
finished all detect
before xf86InitialConfiguration
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 3, Detected Monitor Type: 1
(II) RADEON(0): EDID data from the display on connector: VGA ----------------------
(II) RADEON(0): Manufacturer: PHL  Model: 1510  Serial#: 64487
(II) RADEON(0): Year: 1999  Week: 45
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.630 redY: 0.340   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.140 blueY: 0.100   whiteX: 0.320 whiteY: 0.340
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 448 v_border: 0
(II) RADEON(0): Serial No:  TY  064487
(II) RADEON(0): Monitor name: BL 151AX
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 61 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c1015e7fb0000
(II) RADEON(0): 	2d0901010e1e1796e84ee0a1574c9923
(II) RADEON(0): 	195257bfee003140314f454f6140614f
(II) RADEON(0): 	010101010101d50980a0205e62101060
(II) RADEON(0): 	520833e610000000000000ff00205459
(II) RADEON(0): 	20203036343438370a20000000fc0042
(II) RADEON(0): 	4c2031353141580a20202020000000fd
(II) RADEON(0): 	00384b1e3d08000a20202020202000db
(II) RADEON(0): Output VGA-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "VGA_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "VGA_DDC:ddc2" removed.
(II) RADEON(0): EDID for output VGA-0
(II) RADEON(0): Manufacturer: PHL  Model: 1510  Serial#: 64487
(II) RADEON(0): Year: 1999  Week: 45
(II) RADEON(0): EDID Version: 1.1
(II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) RADEON(0): Sync:  Separate  Composite  SyncOnGreen
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 30  vert.: 23
(II) RADEON(0): Gamma: 2.50
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): redX: 0.630 redY: 0.340   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.140 blueY: 0.100   whiteX: 0.320 whiteY: 0.340
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 720x400@70Hz
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 640x480@67Hz
(II) RADEON(0): 640x480@72Hz
(II) RADEON(0): 640x480@75Hz
(II) RADEON(0): 800x600@56Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 800x600@72Hz
(II) RADEON(0): 800x600@75Hz
(II) RADEON(0): 832x624@75Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): 1024x768@70Hz
(II) RADEON(0): 1024x768@75Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 640  vsize 480  refresh: 75  vid: 20273
(II) RADEON(0): #2: hsize: 800  vsize 600  refresh: 75  vid: 20293
(II) RADEON(0): #3: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #4: hsize: 1024  vsize 768  refresh: 75  vid: 20321
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 25.2 MHz   Image Size:  307 x 230 mm
(II) RADEON(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) RADEON(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 448 v_border: 0
(II) RADEON(0): Serial No:  TY  064487
(II) RADEON(0): Monitor name: BL 151AX
(II) RADEON(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 61 kHz, PixClock max 80 MHz
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff00410c1015e7fb0000
(II) RADEON(0): 	2d0901010e1e1796e84ee0a1574c9923
(II) RADEON(0): 	195257bfee003140314f454f6140614f
(II) RADEON(0): 	010101010101d50980a0205e62101060
(II) RADEON(0): 	520833e610000000000000ff00205459
(II) RADEON(0): 	20203036343438370a20000000fc0042
(II) RADEON(0): 	4c2031353141580a20202020000000fd
(II) RADEON(0): 	00384b1e3d08000a20202020202000db
(II) RADEON(0): DDCModeFromDetailedTiming: 640x350 Warning: We only handle seperate sync.
(II) RADEON(0): Using hsync ranges from config file
(II) RADEON(0): Using vrefresh ranges from config file
(II) RADEON(0): Printing DDC gathered Modelines:
(II) RADEON(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync
(II) RADEON(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(II) RADEON(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(II) RADEON(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(II) RADEON(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync
(II) RADEON(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync
(II) RADEON(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync
(II) RADEON(0): Modeline "640x480"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync
(II) RADEON(0): Modeline "640x480"   30.75  640 664 728 816  480 483 487 504 -hsync +vsync
(II) RADEON(0): Modeline "800x600"   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
(II) RADEON(0): Modeline "1024x768"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
(II) RADEON(0): Modeline "640x350"   25.17  640 656 752 800  350 387 389 448 -hsync -vsync
(II) RADEON(0): EDID vendor "PHL", prod id 5392
(II) RADEON(0): DDCModeFromDetailedTiming: 640x350 Warning: We only handle seperate sync.
(II) RADEON(0): Not using mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using mode "640x480" (hsync out of range)
(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1280x800" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1440x900" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output VGA-0
(II) RADEON(0): Modeline "1024x768"x74.9   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync (60.3 kHz)
(II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) RADEON(0): Modeline "800x600"x74.9   49.00  800 840 920 1040  600 603 607 629 -hsync +vsync (47.1 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) RADEON(0): Modeline "640x480"x74.8   30.75  640 664 728 816  480 483 487 504 -hsync +vsync (37.7 kHz)
(II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x350"x70.2   25.17  640 656 752 800  350 387 389 448 -hsync -vsync (31.5 kHz)
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): DDC Type: 2, Detected Monitor Type: 3
(II) RADEON(0): EDID data from the display on connector: DVI-I ----------------------
(II) RADEON(0): Manufacturer: HIQ  Model: 5003  Serial#: 20060208
(II) RADEON(0): Year: 2006  Week: 6
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 33  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  330 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 40.0 MHz   Image Size:  330 x 270 mm
(II) RADEON(0): h_active: 800  h_sync: 840  h_sync_end 968 h_blank_end 1056 h_border: 0
(II) RADEON(0): v_active: 600  v_sync: 601  v_sync_end 605 v_blanking: 628 v_border: 0
(II) RADEON(0): Ranges: V min: 59  V max: 61 Hz, H min: 31  H max: 67 kHz,
(II) RADEON(0): Monitor name: L72D DVI
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff002131035030183201
(II) RADEON(0): 	0610010380211b78eaaea5a6544c9926
(II) RADEON(0): 	14505421080031404540614081800101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	13004a0e1100001ea00f200031581c20
(II) RADEON(0): 	288014004a0e1100001e000000fd003b
(II) RADEON(0): 	3d1f43ff000a202020202020000000fc
(II) RADEON(0): 	004c373244204456490a2020202000f5
(II) RADEON(0): Output DVI-0 connected
in RADEONProbeOutputModes
(II) RADEON(0): I2C device "DVI_DDC:ddc2" registered at address 0xA0.
(II) RADEON(0): I2C device "DVI_DDC:ddc2" removed.
(II) RADEON(0): EDID for output DVI-0
(II) RADEON(0): Manufacturer: HIQ  Model: 5003  Serial#: 20060208
(II) RADEON(0): Year: 2006  Week: 6
(II) RADEON(0): EDID Version: 1.3
(II) RADEON(0): Digital Display Input
(II) RADEON(0): Max H-Image Size [cm]: horiz.: 33  vert.: 27
(II) RADEON(0): Gamma: 2.20
(II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) RADEON(0): First detailed timing is preferred mode
(II) RADEON(0): redX: 0.650 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) RADEON(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329
(II) RADEON(0): Supported VESA Video Modes:
(II) RADEON(0): 640x480@60Hz
(II) RADEON(0): 800x600@60Hz
(II) RADEON(0): 1024x768@60Hz
(II) RADEON(0): Manufacturer's mask: 0
(II) RADEON(0): Supported Future Video Modes:
(II) RADEON(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
(II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
(II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 108.0 MHz   Image Size:  330 x 270 mm
(II) RADEON(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) RADEON(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) RADEON(0): Supported additional Video Mode:
(II) RADEON(0): clock: 40.0 MHz   Image Size:  330 x 270 mm
(II) RADEON(0): h_active: 800  h_sync: 840  h_sync_end 968 h_blank_end 1056 h_border: 0
(II) RADEON(0): v_active: 600  v_sync: 601  v_sync_end 605 v_blanking: 628 v_border: 0
(II) RADEON(0): Ranges: V min: 59  V max: 61 Hz, H min: 31  H max: 67 kHz,
(II) RADEON(0): Monitor name: L72D DVI
(II) RADEON(0): EDID (in hex):
(II) RADEON(0): 	00ffffffffffff002131035030183201
(II) RADEON(0): 	0610010380211b78eaaea5a6544c9926
(II) RADEON(0): 	14505421080031404540614081800101
(II) RADEON(0): 	010101010101302a009851002a403070
(II) RADEON(0): 	13004a0e1100001ea00f200031581c20
(II) RADEON(0): 	288014004a0e1100001e000000fd003b
(II) RADEON(0): 	3d1f43ff000a202020202020000000fc
(II) RADEON(0): 	004c373244204456490a2020202000f5
(II) RADEON(0): EDID vendor "HIQ", prod id 20483
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1600x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1792x1344" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1856x1392" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x768" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1680x1050" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1200" (height too large for virtual size)
(II) RADEON(0): Not using default mode "1920x1440" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Not using default mode "2048x1536" (height too large for virtual size)
(II) RADEON(0): Printing probed modes for output DVI-0
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1600x1024"x60.0  106.91  1600 1620 1640 1670  1024 1027 1030 1067 -hsync -vsync (64.0 kHz)
(II) RADEON(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) RADEON(0): Modeline "1440x900"x60.2  108.84  1440 1472 1880 1912  900 918 927 946 +hsync +vsync (56.9 kHz)
(II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) RADEON(0): Modeline "1280x800"x60.0   83.46  1280 1344 1480 1680  800 801 804 828 (49.7 kHz)
(II) RADEON(0): Modeline "1280x768"x60.0   80.14  1280 1344 1480 1680  768 769 772 795 (47.7 kHz)
(II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
(II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): EDID for output S-video
(II) RADEON(0): Output VGA-0 connected
(II) RADEON(0): Output DVI-0 connected
(II) RADEON(0): Output S-video disconnected
(II) RADEON(0): Output VGA-0 using initial mode 1024x768
(II) RADEON(0): Output DVI-0 using initial mode 1280x1024
after xf86InitialConfiguration
(**) RADEON(0): Display dimensions: (340, 270) mm
(WW) RADEON(0): Probed monitor is 300x230 mm, using Displaysize 340x270 mm
(**) RADEON(0): DPI set to (172, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(==) RADEON(0): Assuming overlay scaler buffer width is 1536
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe9000000 - 0xe900ffff (0x10000) MX[B]
	[1] 0	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe9010000 - 0xe90100ff (0x100) MX[B]
	[7] -1	0	0xea000000 - 0xea000fff (0x1000) MX[B]
	[8] -1	0	0xea005000 - 0xea005fff (0x1000) MX[B]
	[9] -1	0	0xea004000 - 0xea0040ff (0x100) MX[B]
	[10] -1	0	0xea003000 - 0xea003fff (0x1000) MX[B]
	[11] -1	0	0xea002000 - 0xea002fff (0x1000) MX[B]
	[12] -1	0	0xc0000000 - 0xbfffffff (0x0) MX[B]O
	[13] -1	0	0xe9000000 - 0xe900ffff (0x10000) MX[B](B)
	[14] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xd8000000 - 0xd807ffff (0x80000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xe0ffffff (0x1000000) MX[B](B)
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[21] 0	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[25] -1	0	0x0000c000 - 0x0000c03f (0x40) IX[B]
	[26] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[30] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[31] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) RADEON(0): Write-combining range (0xc8000000,0x4000000)
Entering TV Save
Save TV timing tables
saveTimingTables: reading timing tables
TV Save done
(==) RADEON(0): Using 24 bit depth buffer
(II) RADEON(0): RADEONInitMemoryMap() : 
(II) RADEON(0):   mem_size         : 0x04000000
(II) RADEON(0):   MC_FB_LOCATION   : 0xcbffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(II) RADEON(0): Depth moves disabled by default
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (2304,7281)
(II) RADEON(0): Reserved area from (0,1024) to (2304,1026)
(II) RADEON(0): Largest offscreen area available: 2304 x 6255
(II) RADEON(0): Will use front buffer at offset 0x0
(II) RADEON(0): Will use back buffer at offset 0x1200000
(II) RADEON(0): Will use depth buffer at offset 0x1b00000
(II) RADEON(0): Will use 28672 kb for textures at offset 0x2400000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:09.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:09.0
(II) RADEON(0): [drm] DRM interface version 1.3
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:09.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xf8c02000
(II) RADEON(0): [drm] mapped SAREA 0xf8c02000 to 0xb7b8c000
(II) RADEON(0): [drm] framebuffer handle = 0xc8000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [pci] 8192 kB allocated with handle 0xf8cff000
(II) RADEON(0): [pci] ring handle = 0xf8cff000
(II) RADEON(0): [pci] Ring mapped at 0xb7a8b000
(II) RADEON(0): [pci] Ring contents 0x00000000
(II) RADEON(0): [pci] ring read ptr handle = 0xf8e00000
(II) RADEON(0): [pci] Ring read ptr mapped at 0xb7a8a000
(II) RADEON(0): [pci] Ring read ptr contents 0x00000000
(II) RADEON(0): [pci] vertex/indirect buffers handle = 0xf8e01000
(II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0xb37b6000
(II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
(II) RADEON(0): [pci] GART texture map handle = 0xf9001000
(II) RADEON(0): [pci] GART Texture map mapped at 0xb32d6000
(II) RADEON(0): [drm] register handle = 0xe9000000
(II) RADEON(0): [dri] Visual configs initialized
init memmap
init common
init crtc1
init pll1
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcbffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc1
restore pll1
finished PLL1
restore dac
enable montype: 1
init memmap
init common
init crtc2
init pll2
restore memmap
(II) RADEON(0): RADEONRestoreMemMapRegisters() : 
(II) RADEON(0):   MC_FB_LOCATION   : 0xcbffc800
(II) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
restore common
restore crtc2
restore pll2
finished PLL2
restore FP
enable montype: 3
disable montype: 1
disable montype: 3
(==) RADEON(0): Backing store disabled
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 21
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	Indirect CPU to Screen color expansion
	Solid Lines
	Dashed Lines
	Scanline Image Writes
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) RADEON(0): Acceleration enabled
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1026)
(II) RADEON(0): Largest offscreen area available: 2304 x 6253
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia//theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "TMDS" is not used
(WW) RADEON(0): Option "CRT" is not used
(WW) RADEON(0): Option "Position" is not used
(--) RandR disabled
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:09.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:09.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/radeon_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) RADEON(0): Setting screen physical size to 330 x 270
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/input/mice"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Mouse0: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5 6 7"
(**) Mouse0: ZAxisMapping: buttons 4, 5, 6 and 7
(**) Mouse0: Buttons: 11
(**) Mouse0: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Keyboard0: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
enable montype: 1
enable montype: 3
```

Those lines are suspicious:

```
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(WW) RADEON(0): Option "TMDS" is not used
(WW) RADEON(0): Option "CRT" is not used
(WW) RADEON(0): Option "Position" is not used
(--) RandR disabled
```

What does this mean? Why disabling RandR and why some options are going to be ignored? Please, can somebody explain?

Thanks for any hints

---

### Post by the_atlan on 2007-10-24
Just tried[FONT="Courier New"] xrandr -q[/FONT] which should give me a info about my ati device, but it just says "Can't open display". Probably somebody knows why.

---

