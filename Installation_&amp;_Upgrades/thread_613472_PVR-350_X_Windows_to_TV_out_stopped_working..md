---
title: "PVR-350 X Windows to TV out stopped working."
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by stollefsen on 2007-11-15
You think I would learn. If it ain't broke...... don't fix it......

Sigh.. Here comes another 80 hours of searching  the web and trying stuff.   This stuff will never pass the wife test :lolflag:


I found that when I upgraded from Fiesty Fawn to Gutsy Gibbons that my output to the TV for X windows desktop had stopped working. The strange part is I only see the Ubuntu splash screen on the TV when I am booting or shutting down. 

Has anyone else been having problems with the PVR-350 after this upgrade?

I will keep searching. This shouldn't be rocket science.


I went and checked to see everything is working:

1) Checked for IVTV driver loaded properly. Yes
2) Checked /etc/x11/xorg.conf for settings. Yes


:confused:

---

### Post by stollefsen on 2008-04-23
My eventual fix for this was to rollback the kernel to where the ivtv driver worked and just to forget about wasting time to figure out what was busted and what til the next major release.

I just don't have the time to burn on this stuff.

---

### Post by Orchid on 2008-05-18
I have the same problem: X with PVR350 tv-out worked with Feisty Fawn.
Then I upgraded to Gutsy Gibbon and X wouldn't work anymore.
MythTV was still capable to output recordings to tv-out.
The only time X server appears is during shutdown.
Tried to fix things under Gutsy Gibbon but couldn't find a solution and hoped Hardy Heron release would give solution: nop :(

If somebody could hint to a solution, this is my xorg.log:

============================================================
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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux purgatory 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 18 15:08:55 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "TV Screen" (0)
(**) |   |-->Monitor "TV"
(**) |   |-->Device "Hauppauge PVR 350 iTVC15 Framebuffer"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
	Entry deleted from font path.
(==) Including the default font path /usr/share/fonts/X11/misc,/usr/share/fonts/X11/cyrillic,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
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
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
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
(--) using VT number 2

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 1043,80ac rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1043,80ac rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1043,80ad rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1043,0c11 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1043,0c11 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1043,0c11 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:04:0: chip 10de,0066 card 1043,80a7 rev a1 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 10de,006b card 1043,0c11 rev a2 class 04,01,00 hdr 00
(II) PCI: 00:06:0: chip 10de,006a card 1043,8095 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1043,0c11 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 01:04:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 01:08:0: chip 4444,0803 card 0070,4000 rev 01 class 04,00,00 hdr 00
(II) PCI: 01:0a:0: chip 12d8,8140 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 02:08:0: chip 4444,0016 card 0070,e807 rev 01 class 04,00,00 hdr 00
(II) PCI: 02:09:0: chip 4444,0016 card 0070,e817 rev 01 class 04,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,5964 card 1458,4018 rev 01 class 03,00,00 hdr 80
(II) PCI: 04:00:1: chip 1002,5d44 card 1458,4019 rev 01 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,2), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe3000000 - 0xe4ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdbffffff (0xc000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0xe1000000 - 0xe2ffffff (0x2000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (1:10:0), (1,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd4000000 - 0xdbffffff (0x8000000) MX[B]
(--) PCI: (1:8:0) unknown vendor (0x4444) unknown chipset (0x0803) rev 1, Mem @ 0xd0000000/26
(--) PCI: (2:8:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xd4000000/26
(--) PCI: (2:9:0) unknown vendor (0x4444) unknown chipset (0x0016) rev 1, Mem @ 0xd8000000/26
(--) PCI:*(4:0:0) ATI Technologies Inc RV280 [Radeon 9200 SE] rev 1, Mem @ 0xc0000000/27, 0xe2000000/16, I/O @ 0xc000/8
(--) PCI: (4:0:1) ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) rev 1, Mem @ 0xc8000000/27, 0xe2010000/16
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
(II) PCI Memory resource overlap reduced 0xdc000000 from 0xdfffffff to 0xdbffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[1] -1	0	0xe5085000 - 0xe5085fff (0x1000) MX[B]
	[2] -1	0	0xe5000000 - 0xe507ffff (0x80000) MX[B]
	[3] -1	0	0xe5083000 - 0xe5083fff (0x1000) MX[B]
	[4] -1	0	0xe5082000 - 0xe50820ff (0x100) MX[B]
	[5] -1	0	0xe5081000 - 0xe5081fff (0x1000) MX[B]
	[6] -1	0	0xe5084000 - 0xe5084fff (0x1000) MX[B]
	[7] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[8] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[11] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd3ffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe2010000 - 0xe201ffff (0x10000) MX[B](B)
	[1] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[1] -1	0	0xe5085000 - 0xe5085fff (0x1000) MX[B]
	[2] -1	0	0xe5000000 - 0xe507ffff (0x80000) MX[B]
	[3] -1	0	0xe5083000 - 0xe5083fff (0x1000) MX[B]
	[4] -1	0	0xe5082000 - 0xe50820ff (0x100) MX[B]
	[5] -1	0	0xe5081000 - 0xe5081fff (0x1000) MX[B]
	[6] -1	0	0xe5084000 - 0xe5084fff (0x1000) MX[B]
	[7] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[8] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B](B)
	[9] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[10] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[11] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd3ffffff (0x4000000) MX[B](B)
	[13] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[14] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[15] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[16] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[17] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[19] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe2010000 - 0xe201ffff (0x10000) MX[B](B)
	[1] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
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
	[4] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[5] -1	0	0xe5085000 - 0xe5085fff (0x1000) MX[B]
	[6] -1	0	0xe5000000 - 0xe507ffff (0x80000) MX[B]
	[7] -1	0	0xe5083000 - 0xe5083fff (0x1000) MX[B]
	[8] -1	0	0xe5082000 - 0xe50820ff (0x100) MX[B]
	[9] -1	0	0xe5081000 - 0xe5081fff (0x1000) MX[B]
	[10] -1	0	0xe5084000 - 0xe5084fff (0x1000) MX[B]
	[11] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[12] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xd3ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xe2010000 - 0xe201ffff (0x10000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "extmod"
(II) Reloading /usr/lib/xorg/modules/extensions//libextmod.so
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
(II) Reloading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "ivtv"
(II) Loading /usr/lib/xorg/modules/drivers//ivtv_drv.so
(II) Module ivtv: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) Wacom driver level: 47-0.7.9-8 $
(II) v4l driver for Video4Linux
(II) IVTV: driver for ivtv framebuffer: PVR-350
(II) Primary Device is: PCI 04:00:0
(WW) ivtv: No matching Device section for instance (BusID PCI:2:8:0) found
(WW) ivtv: No matching Device section for instance (BusID PCI:2:9:0) found
(--) Chipset PVR-350 found
(II) IVTV(0): using /dev/fb0
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[5] -1	0	0xe5085000 - 0xe5085fff (0x1000) MX[B]
	[6] -1	0	0xe5000000 - 0xe507ffff (0x80000) MX[B]
	[7] -1	0	0xe5083000 - 0xe5083fff (0x1000) MX[B]
	[8] -1	0	0xe5082000 - 0xe50820ff (0x100) MX[B]
	[9] -1	0	0xe5081000 - 0xe5081fff (0x1000) MX[B]
	[10] -1	0	0xe5084000 - 0xe5084fff (0x1000) MX[B]
	[11] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[12] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[15] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xd3ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xe2010000 - 0xe201ffff (0x10000) MX[B](B)
	[18] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[22] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[24] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[27] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(--) IVTV(0): Framebuffer id from dev /dev/fb0 is 0
(II) IVTV(0): IVTV driver version 1.0.0
(II) IVTV(0): Using new API
(II) IVTV(0): Linked framebuffer 'dev/fb0' to yuv device '/dev/video48'
(**) IVTV(0): Depth 24, (**) framebuffer bpp 32
(==) IVTV(0): RGB weight 888
(==) IVTV(0): Default visual is TrueColor
(==) IVTV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) IVTV(0): Hardware: cx23415 TV out (vidmem: 1665k)
(II) IVTV(0): Checking Modes against framebuffer device...
(II) IVTV(0): 	mode "720x480" not found
(II) IVTV(0): Checking Modes against monitor...
(--) IVTV(0): Virtual size is 720x576 (pitch 720)
(**) IVTV(0):  Built-in mode "current": 23.7 MHz, 29.6 kHz, 50.0 Hz
(II) IVTV(0): Modeline "current"x0.0   23.72  720 775 799 800  576 590 592 593 -hsync -vsync -csync (29.6 kHz)
(==) IVTV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(**) IVTV(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xd0000000 - 0xd3ffffff (0x4000000) MX[B]
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xe4000000 - 0xe4003fff (0x4000) MX[B]
	[6] -1	0	0xe5085000 - 0xe5085fff (0x1000) MX[B]
	[7] -1	0	0xe5000000 - 0xe507ffff (0x80000) MX[B]
	[8] -1	0	0xe5083000 - 0xe5083fff (0x1000) MX[B]
	[9] -1	0	0xe5082000 - 0xe50820ff (0x100) MX[B]
	[10] -1	0	0xe5081000 - 0xe5081fff (0x1000) MX[B]
	[11] -1	0	0xe5084000 - 0xe5084fff (0x1000) MX[B]
	[12] -1	0	0xdc000000 - 0xdbffffff (0x0) MX[B]O
	[13] -1	0	0xe2000000 - 0xe200ffff (0x10000) MX[B](B)
	[14] -1	0	0xc0000000 - 0xc7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xd8000000 - 0xdbffffff (0x4000000) MX[B](B)
	[16] -1	0	0xd4000000 - 0xd7ffffff (0x4000000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xd3ffffff (0x4000000) MX[B](B)
	[18] -1	0	0xe2010000 - 0xe201ffff (0x10000) MX[B](B)
	[19] -1	0	0xc8000000 - 0xcfffffff (0x8000000) MX[B](B)
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[23] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[24] -1	0	0x0000d000 - 0x0000d07f (0x80) IX[B]
	[25] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[26] -1	0	0x0000e000 - 0x0000e007 (0x8) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[28] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B](B)
(II) IVTV(0): bitsPerPixel=32, depth=24, defaultVisual=TrueColor
	mask: ff0000,ff00,ff, offset: 16,8,0
(EE) IVTV(0): FBIOPUT_VSCREENINFO: Invalid argument
(EE) IVTV(0): Mode init failed

Fatal server error:
AddScreen/ScreenInit failed for driver 0

===============================================================

---

