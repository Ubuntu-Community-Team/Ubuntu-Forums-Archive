---
title: "[SOLVED] Intel driver not recognized - always running in low FX mode"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by 3m_g33k on 2008-07-20
Hello all,

Ive recently switched to Hardy and I cant seem to get my GFX card to work - everytime I boot I get the error message saying that it is not recognized and needs to run in low graphics mode :confused:

Can someone suggest like a step by step procedure i need to go through i.e. determine GFX card version (i know its an Intel integrated one, but not sure of what version) and then how to install the correct driver?

Many thanks in advance! :guitar: (guitar has no significant meaning, just diggin' the smiley!)

---

### Post by JagDragon on 2008-07-20
Open a terminal and type ```
lspci
``` and look for anything that looks like an intel graphics card. Post it here, and we can determine what graphics driver would be appropriate.

---

### Post by 3m_g33k on 2008-07-20
CHeers for the quick reply, found the following:

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by JagDragon on 2008-07-20
You need to get a different driver running the graphics on your laptop, the i810 driver. To do this we need to edit the xorg.conf file and add the driver in. Open up a terminal.
```
gksu gedit /etc/X11/xorg.conf
```
will open your xorg.conf file. From there you need to find the section of the file that is ```
Section "Device"
```
You need to add, or modify, that part of the file so that the line ```
Driver "i810"
``` is in there. So that means either adding that line if no other Driver entry exists, or changing the existing Driver entry so that it reads like what is about.
You should end up with a section that looks something like
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"i810"
	DefaultDepth	"24"
EndSection
```

That should work. After that, you need to restart your X server. Save and close the edited xorg.conf and run this command:```
sudo /etc/init.d/gdm restart
```

Let me know how that goes.

---

### Post by 3m_g33k on 2008-07-20
Hiya,

No luck I'm afraid. Still got the message when I restarted the computer :confused:

---

### Post by JagDragon on 2008-07-20
Can you post your /var/log/Xorg.0.log here please?

---

### Post by 3m_g33k on 2008-07-20
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux crizzle-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 20 17:45:13 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1179,ff00 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 1179,ff03 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 1179,ff03 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 1179,ff02 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1179,ff00 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1179,ff00 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1179,ff00 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1179,ff00 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1179,ff00 rev 02 class 0c,05,00 hdr 00
(II) PCI: 04:00:0: chip 168c,001c card 144f,7128 rev 01 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 10ec,8136 card 1179,ff00 rev 01 class 02,00,00 hdr 00
(II) PCI: 06:04:0: chip 104c,8039 card 1400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 06:04:1: chip 104c,803a card 1179,ff00 rev 00 class 0c,00,10 hdr 80
(II) PCI: 06:04:2: chip 104c,803b card 1179,ff00 rev 00 class 01,80,00 hdr 80
(II) PCI: 06:04:3: chip 104c,803c card 1179,ff00 rev 00 class 08,05,01 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd6000000 - 0xd7ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:1), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:2), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xda000000 - 0xdbffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,10), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdc0fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:4:0), (6,7,10), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdc100000/19, 0xc0000000/28, 0xdc200000/18, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdc180000/19
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
	[0] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[1] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[2] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[3] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[4] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[5] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[6] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[7] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[8] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[9] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[12] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[1] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[2] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[3] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[4] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[5] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[6] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[7] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[8] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[9] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[12] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
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
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(==) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: LPL  Model: dd00  Serial#: 0
(II) VESA(0): Year: 2006  Week: 0
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) VESA(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) VESA(0):  LGPhilipsLCD
(II) VESA(0):  LP154WX4-TLE2
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff00320c00dd00000000
(II) VESA(0): 	00100103802115780ab3409959538d27
(II) VESA(0): 	25505400000001010101010101010101
(II) VESA(0): 	010101010101bc1b00a0502017303020
(II) VESA(0): 	36004bcf100000190000000000000000
(II) VESA(0): 	00000000000000000000000000fe004c
(II) VESA(0): 	475068696c6970734c43440a000000fe
(II) VESA(0): 	004c503135345758342d544c45320041
(II) VESA(0): EDID vendor "LPL", prod id 56576
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 161 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 162 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 163 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 164 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 165 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 166 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 167 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 168 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 169 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16e (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16f (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 170 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 171 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 14d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 15c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 14b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 15a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 107 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 105 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 101 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 23
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 23
	LinNumberOfImagePages: 23
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 103 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 123 64KB banks (7872kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-49.31 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-59.91 Hz
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(--) VESA(0): Virtual size is 1280x800 (pitch 1280)
(**) VESA(0):  Built-in mode "1280x800"
(**) VESA(0): Display dimensions: (330, 210) mm
(**) VESA(0): DPI set to (98, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x800" (161)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Splitting WC range: base: 0xc0000000, size: 0x7b0000
(II) VESA(0): Splitting WC range: base: 0xc0400000, size: 0x3b0000
(II) VESA(0): Splitting WC range: base: 0xc0600000, size: 0x1b0000
(II) VESA(0): Splitting WC range: base: 0xc0700000, size: 0xb0000
(II) VESA(0): Splitting WC range: base: 0xc0780000, size: 0x30000
(==) VESA(0): Write-combining range (0xc07a0000,0x10000)
(==) VESA(0): Write-combining range (0xc0780000,0x30000)
(==) VESA(0): Write-combining range (0xc0700000,0xb0000)
(==) VESA(0): Write-combining range (0xc0600000,0x1b0000)
(==) VESA(0): Write-combining range (0xc0400000,0x3b0000)
(WW) VESA(0): Failed to set up write-combining range (0xc0000000,0x7b0000)
(II) VESA(0): virtual address = 0xb71e6000,
	physical address = 0xc0000000, size = 8060928
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event11
(**) Option "Device" "/dev/input/event11"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event11
(**) Option "Device" "/dev/input/event11"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9

---

### Post by JagDragon on 2008-07-20
For future reference, enclose that in [noparse]```

```[/noparse] tags so that it doesn't fill up about 16 screens. Did you remove the i810 driver entry? Put it back in and then show me your xorg.conf and your log (enclosed in the code tags) after you have rebooted your X server with ```
sudo /etc/init.d/gdm restart
```

---

### Post by 3m_g33k on 2008-07-20
CHeers for the advice for posting code, and yeah - copy and pasted the entry in your previous post to replace the current text in the xorg file, closed and saved, restarted then posted the log file.

---

### Post by JagDragon on 2008-07-20
```
gksu gedit /etc/X11/xorg.conf
```
Add this to your device section:```
Driver "i810"
BusID "PCI:0:2:0"
```

After that, reboot the whole system, and if it doesn't work, post the log

---

### Post by 3m_g33k on 2008-07-20
Still no luck im afraid:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux crizzle-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul 20 18:43:56 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1179,ff00 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 1179,ff03 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 1179,ff03 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 1179,ff02 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1179,ff00 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1179,ff00 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1179,ff00 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1179,ff00 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1179,ff00 rev 02 class 0c,05,00 hdr 00
(II) PCI: 04:00:0: chip 168c,001c card 144f,7128 rev 01 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 10ec,8136 card 1179,ff00 rev 01 class 02,00,00 hdr 00
(II) PCI: 06:04:0: chip 104c,8039 card 1400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 06:04:1: chip 104c,803a card 1179,ff00 rev 00 class 0c,00,10 hdr 80
(II) PCI: 06:04:2: chip 104c,803b card 1179,ff00 rev 00 class 01,80,00 hdr 80
(II) PCI: 06:04:3: chip 104c,803c card 1179,ff00 rev 00 class 08,05,01 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd6000000 - 0xd7ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:1), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:2), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xda000000 - 0xdbffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,10), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdc0fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:4:0), (6,7,10), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdc100000/19, 0xc0000000/28, 0xdc200000/18, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdc180000/19
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
	[0] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[1] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[2] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[3] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[4] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[5] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[6] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[7] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[8] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[9] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[12] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[1] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[2] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[3] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[4] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[5] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[6] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[7] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[8] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[9] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[12] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
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
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(==) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: LPL  Model: dd00  Serial#: 0
(II) VESA(0): Year: 2006  Week: 0
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) VESA(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) VESA(0):  LGPhilipsLCD
(II) VESA(0):  LP154WX4-TLE2
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff00320c00dd00000000
(II) VESA(0): 	00100103802115780ab3409959538d27
(II) VESA(0): 	25505400000001010101010101010101
(II) VESA(0): 	010101010101bc1b00a0502017303020
(II) VESA(0): 	36004bcf100000190000000000000000
(II) VESA(0): 	00000000000000000000000000fe004c
(II) VESA(0): 	475068696c6970734c43440a000000fe
(II) VESA(0): 	004c503135345758342d544c45320041
(II) VESA(0): EDID vendor "LPL", prod id 56576
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 161 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 162 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 163 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 164 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 165 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 166 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 167 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 168 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 169 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16e (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16f (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 170 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 171 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 14d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 15c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 14b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 15a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 107 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 105 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 101 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 23
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 23
	LinNumberOfImagePages: 23
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 103 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 123 64KB banks (7872kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-49.31 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-59.91 Hz
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(--) VESA(0): Virtual size is 1280x800 (pitch 1280)
(**) VESA(0):  Built-in mode "1280x800"
(**) VESA(0): Display dimensions: (330, 210) mm
(**) VESA(0): DPI set to (98, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x800" (161)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Splitting WC range: base: 0xc0000000, size: 0x7b0000
(II) VESA(0): Splitting WC range: base: 0xc0400000, size: 0x3b0000
(II) VESA(0): Splitting WC range: base: 0xc0600000, size: 0x1b0000
(II) VESA(0): Splitting WC range: base: 0xc0700000, size: 0xb0000
(II) VESA(0): Splitting WC range: base: 0xc0780000, size: 0x30000
(==) VESA(0): Write-combining range (0xc07a0000,0x10000)
(==) VESA(0): Write-combining range (0xc0780000,0x30000)
(==) VESA(0): Write-combining range (0xc0700000,0xb0000)
(==) VESA(0): Write-combining range (0xc0600000,0x1b0000)
(==) VESA(0): Write-combining range (0xc0400000,0x3b0000)
(WW) VESA(0): Failed to set up write-combining range (0xc0000000,0x7b0000)
(II) VESA(0): virtual address = 0xb722c000,
	physical address = 0xc0000000, size = 8060928
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9 
```

---

### Post by 3m_g33k on 2008-07-20
Ive also tried the code:

```
 sudo dpkg-reconfigure xserver-xorg 
```

But all it goes on about is my keyboard and doesnt ask me about any of my other devices which I think is rather strange?

---

### Post by JagDragon on 2008-07-20
Try this configuration of xorg.conf:

```


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Option		"AIGLX"	"true"
	Identifier	"Default Layout"
  	Screen		"Default Screen"
EndSection

Section "DRI"
	Mode 0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	"28-51"
	VertRefresh	"43-60"
EndSection

Section "Device"
	Identifier	"Intel Corporation 945GM Integrated Graphics Device"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 945GM Integrated Graphics Device"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth 24
		Modes "1280x1024" "1024x768" "800x600" "648x480"
	EndSubSection
EndSection

```

---

### Post by 3m_g33k on 2008-07-21
Still no luck, have attached the log again. Do I need to fiddle around with the Applications -> Other -> Screen and Graphics option?

When I go in there my default screen (screen 1) is set at Plug n Play and at 1280 x 1800. Going onto the driver tab I have as the graphics card (intel945) set to i810 intel chipset and the VESA graphics card set to vesa-vesa generic graphics card

Ive attached screenshots of both those option tabs:



```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux crizzle-laptop 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jul 21 07:05:12 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(**) |-->Input Device "Synaptics Touchpad"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,27a0 card 1179,ff00 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,27a2 card 1179,ff03 rev 03 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,27a6 card 1179,ff03 rev 03 class 03,80,00 hdr 80
(II) PCI: 00:1b:0: chip 8086,27d8 card 1179,ff02 rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:2: chip 8086,27d4 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1179,ff00 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1179,ff00 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1179,ff00 rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,2448 card 0000,0000 rev e2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b9 card 1179,ff00 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,27c4 card 1179,ff00 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1179,ff00 rev 02 class 0c,05,00 hdr 00
(II) PCI: 04:00:0: chip 168c,001c card 144f,7128 rev 01 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 10ec,8136 card 1179,ff00 rev 01 class 02,00,00 hdr 00
(II) PCI: 06:04:0: chip 104c,8039 card 1400,0000 rev 00 class 06,07,00 hdr 82
(II) PCI: 06:04:1: chip 104c,803a card 1179,ff00 rev 00 class 0c,00,10 hdr 80
(II) PCI: 06:04:2: chip 104c,803b card 1179,ff00 rev 00 class 01,80,00 hdr 80
(II) PCI: 06:04:3: chip 104c,803c card 1179,ff00 rev 00 class 08,05,01 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,7), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[1] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[2] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[3] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xd6000000 - 0xd7ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:1), (0,4,4), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[1] -1	0	0x00003400 - 0x000034ff (0x100) IX[B]
	[2] -1	0	0x00003800 - 0x000038ff (0x100) IX[B]
	[3] -1	0	0x00003c00 - 0x00003cff (0x100) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xd8000000 - 0xd9ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xd2000000 - 0xd3ffffff (0x2000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:28:2), (0,5,5), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[1] -1	0	0x00004400 - 0x000044ff (0x100) IX[B]
	[2] -1	0	0x00004800 - 0x000048ff (0x100) IX[B]
	[3] -1	0	0x00004c00 - 0x00004cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xda000000 - 0xdbffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xd5ffffff (0x2000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 6: bridge is at (0:30:0), (0,6,10), BCTRL: 0x0004 (VGA_EN is cleared)
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0xdc000000 - 0xdc0fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 7: bridge is at (6:4:0), (6,7,10), BCTRL: 0x05c0 (VGA_EN is cleared)
(--) PCI:*(0:2:0) Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdc100000/19, 0xc0000000/28, 0xdc200000/18, I/O @ 0x1800/3
(--) PCI: (0:2:1) Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller rev 3, Mem @ 0xdc180000/19
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
	[0] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[1] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[2] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[3] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[4] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[5] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[6] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[7] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[8] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[9] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[12] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[1] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[2] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[3] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[4] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[5] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[6] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[7] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[8] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[9] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[10] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[11] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[12] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[13] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[14] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[20] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[21] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[22] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[23] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
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
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
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
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[19] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[20] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[26] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[27] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[28] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[29] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(==) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: LPL  Model: dd00  Serial#: 0
(II) VESA(0): Year: 2006  Week: 0
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 33  vert.: 21
(II) VESA(0): Gamma: 2.20
(II) VESA(0): No DPMS capabilities specified; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.600 redY: 0.351   greenX: 0.324 greenY: 0.554
(II) VESA(0): blueX: 0.153 blueY: 0.145   whiteX: 0.312 whiteY: 0.328
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 71.0 MHz   Image Size:  331 x 207 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
(II) VESA(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
(II) VESA(0):  LGPhilipsLCD
(II) VESA(0):  LP154WX4-TLE2
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff00320c00dd00000000
(II) VESA(0): 	00100103802115780ab3409959538d27
(II) VESA(0): 	25505400000001010101010101010101
(II) VESA(0): 	010101010101bc1b00a0502017303020
(II) VESA(0): 	36004bcf100000190000000000000000
(II) VESA(0): 	00000000000000000000000000fe004c
(II) VESA(0): 	475068696c6970734c43440a000000fe
(II) VESA(0): 	004c503135345758342d544c45320041
(II) VESA(0): EDID vendor "LPL", prod id 56576
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 161 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 162 (1280x800)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 800
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 163 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 164 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 165 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 166 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 167 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 168 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 169 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16e (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 16f (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 170 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 171 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 14d (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 15c (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 13a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 14b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 15a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 107 (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11a (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 11b (0x0)
	ModeAttributes: 0x0
	WinAAttributes: 0x0
	WinBAttributes: 0x0
	WinGranularity: 0
	WinSize: 0
	WinASegment: 0x0
	WinBSegment: 0x0
	WinFuncPtr: 0x0
	BytesPerScanline: 0
	XResolution: 0
	YResolution: 0
	XCharSize: 0
	YCharSize: 0
	NumberOfPlanes: 0
	BitsPerPixel: 0
	NumberOfBanks: 0
	MemoryModel: 0
	BankSize: 0
	NumberOfImages: 0
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 0
	BnkNumberOfImagePages: 0
	LinNumberOfImagePages: 0
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 0
Mode: 105 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1024
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 9
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1024
	BnkNumberOfImagePages: 9
	LinNumberOfImagePages: 9
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 117 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 4
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 4
	LinNumberOfImagePages: 4
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 118 (1024x768)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 112 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 5
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 5
	LinNumberOfImagePages: 5
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
*Mode: 114 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 7
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 7
	LinNumberOfImagePages: 7
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 115 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 3
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 230000000
Mode: 101 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 23
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 23
	LinNumberOfImagePages: 23
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
Mode: 103 (800x600)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 832
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 832
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000
*Mode: 111 (640x480)
	ModeAttributes: 0x9b
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0007863
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 11
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xc0000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 11
	LinNumberOfImagePages: 11
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 230000000

(II) VESA(0): Total Memory: 123 64KB banks (7872kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.50-49.31 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-59.91 Hz
(II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
(II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
(II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
(--) VESA(0): Virtual size is 1280x800 (pitch 1280)
(**) VESA(0):  Built-in mode "1280x800"
(**) VESA(0): Display dimensions: (330, 210) mm
(**) VESA(0): DPI set to (98, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1280x800" (161)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdc005800 - 0xdc0058ff (0x100) MX[B]
	[5] -1	0	0xdc004000 - 0xdc004fff (0x1000) MX[B]
	[6] -1	0	0xdc000000 - 0xdc003fff (0x4000) MX[B]
	[7] -1	0	0xdc005000 - 0xdc0057ff (0x800) MX[B]
	[8] -1	0	0xda000000 - 0xda000fff (0x1000) MX[B]
	[9] -1	0	0xd8000000 - 0xd800ffff (0x10000) MX[B]
	[10] -1	0	0xdc444000 - 0xdc4443ff (0x400) MX[B]
	[11] -1	0	0xdc440000 - 0xdc443fff (0x4000) MX[B]
	[12] -1	0	0xdc180000 - 0xdc1fffff (0x80000) MX[B](B)
	[13] -1	0	0xdc200000 - 0xdc23ffff (0x40000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[15] -1	0	0xdc100000 - 0xdc17ffff (0x80000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[22] -1	0	0x000018c0 - 0x000018df (0x20) IX[B]
	[23] -1	0	0x000018b0 - 0x000018bf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00001880 - 0x0000189f (0x20) IX[B]
	[29] -1	0	0x00001860 - 0x0000187f (0x20) IX[B]
	[30] -1	0	0x00001840 - 0x0000185f (0x20) IX[B]
	[31] -1	0	0x00001820 - 0x0000183f (0x20) IX[B]
	[32] -1	0	0x00001800 - 0x00001807 (0x8) IX[B](B)
	[33] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[34] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(r) 82945GM Chipset Family Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r) 82945GM Chipset Family Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Splitting WC range: base: 0xc0000000, size: 0x7b0000
(II) VESA(0): Splitting WC range: base: 0xc0400000, size: 0x3b0000
(II) VESA(0): Splitting WC range: base: 0xc0600000, size: 0x1b0000
(II) VESA(0): Splitting WC range: base: 0xc0700000, size: 0xb0000
(II) VESA(0): Splitting WC range: base: 0xc0780000, size: 0x30000
(==) VESA(0): Write-combining range (0xc07a0000,0x10000)
(==) VESA(0): Write-combining range (0xc0780000,0x30000)
(==) VESA(0): Write-combining range (0xc0700000,0xb0000)
(==) VESA(0): Write-combining range (0xc0600000,0x1b0000)
(==) VESA(0): Write-combining range (0xc0400000,0x3b0000)
(WW) VESA(0): Failed to set up write-combining range (0xc0000000,0x7b0000)
(II) VESA(0): virtual address = 0xb7196000,
	physical address = 0xc0000000, size = 8060928
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
Atom 4, CARD32 4, unsigned long 4
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(**) Option "HorizEdgeScroll" "0"
(--) Synaptics Touchpad touchpad found
(**) Option "SendCoreEvents" "true"
(**) Synaptics Touchpad: always reports core events
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Synaptics Touchpad)
(II) XINPUT: Adding extended input device "Synaptics Touchpad" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event9
(**) Option "Device" "/dev/input/event9"
(--) Synaptics Touchpad touchpad found
SetClientVersion: 0 9
```

---

### Post by 3m_g33k on 2008-07-21
Alas 'tis fixed!! =D>

Found that it had something to do with me getting a strange message upon startup - namely that no resume imagine could be found. Looking at other threads in relation to that problem found a command to rebuild my corrupt image file and now dont get the boot message anymore - many thanks Jag though for all your help and suggestions!

Solved baby yea!:guitar:

---

