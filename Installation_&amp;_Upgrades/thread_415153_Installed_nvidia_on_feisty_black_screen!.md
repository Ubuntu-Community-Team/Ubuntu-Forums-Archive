---
title: "Installed nvidia on feisty black screen!"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by alien_doggy on 2007-04-20
I installed feisty on my computer and everything was fine. Until i installed the nvidia drivers in apt-get. When I start kubuntu I get a black screen and just stops. But the nv driver work fine. Here is the X-org-logen. I hope some one can help me.

[HTML]
X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Kubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 20 16:18:40 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Hansol SyncMaster 204B"
(**) |   |-->Device "Geforce 8800GTX"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,03a1 card 10de,c55e rev a2 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,03ac card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,03aa card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,03a9 card 10de,c55e rev a1 class 05,00,00 hdr 00
(II) PCI: 00:00:4: chip 10de,03ab card 10de,c55e rev a1 class 05,00,00 hdr 00
(II) PCI: 00:00:5: chip 10de,03a8 card 10de,c55e rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:6: chip 10de,03b5 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:00:7: chip 10de,03b4 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,03ad card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:1: chip 10de,03ae card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:2: chip 10de,03af card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:3: chip 10de,03b0 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:4: chip 10de,03b1 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:5: chip 10de,03b2 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:01:6: chip 10de,03b3 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:0: chip 10de,03b6 card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:02:1: chip 10de,03bc card 10de,c55e rev a1 class 05,00,00 hdr 00
(II) PCI: 00:02:2: chip 10de,03ba card 10de,c55e rev a1 class 05,00,00 hdr 80
(II) PCI: 00:03:0: chip 10de,03b7 card 0000,0000 rev a1 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0369 card 10de,c55e rev a1 class 05,00,00 hdr 00
(II) PCI: 00:0a:0: chip 10de,0360 card 10de,c55e rev a2 class 06,01,00 hdr 80
(II) PCI: 00:0a:1: chip 10de,0368 card 10de,c55e rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:0a:2: chip 10de,036a card 10de,c55e rev a2 class 05,00,00 hdr 80
(II) PCI: 00:0b:0: chip 10de,036c card 10de,c55e rev a1 class 0c,03,10 hdr 80
(II) PCI: 00:0b:1: chip 10de,036d card 10de,c55e rev a2 class 0c,03,20 hdr 80
(II) PCI: 00:0d:0: chip 10de,036e card 10de,c55e rev a1 class 01,01,8a hdr 00
(II) PCI: 00:0e:0: chip 10de,037f card 10de,c55e rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0e:1: chip 10de,037f card 10de,c55e rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0e:2: chip 10de,037f card 10de,c55e rev a2 class 01,01,85 hdr 80
(II) PCI: 00:0f:0: chip 10de,0370 card 0000,0000 rev a2 class 06,04,01 hdr 81
(II) PCI: 00:0f:1: chip 10de,0371 card 10de,c55e rev a2 class 04,03,00 hdr 80
(II) PCI: 00:11:0: chip 10de,0373 card 10de,c55e rev a2 class 06,80,00 hdr 00
(II) PCI: 00:12:0: chip 10de,0373 card 10de,c55e rev a2 class 06,80,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0191 card 10de,039c rev a2 class 03,00,00 hdr 00
(II) PCI: 02:07:0: chip 104c,8023 card 10de,c55e rev 00 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:3:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xca000000 - 0xcdffffff (0x4000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:10:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:15:0), (0,2,2), BCTRL: 0x0a04 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xcfd00000 - 0xcfdfffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xcfe00000 - 0xcfefffff (0x100000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x0191) rev 162, Mem @ 0xcc000000/24, 0xb0000000/28, 0xca000000/25, I/O @ 0x9c00/7
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
	[0] -1	0	0xcfdf8000 - 0xcfdfbfff (0x4000) MX[B]
	[1] -1	0	0xcfdff000 - 0xcfdff7ff (0x800) MX[B]
	[2] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[3] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[4] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[5] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[6] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[7] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[8] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[9] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[10] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[11] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[12] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[13] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[14] -1	0	0xca000000 - 0xcbffffff (0x2000000) MX[B](B)
	[15] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[25] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[26] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[27] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[28] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[35] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[36] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[37] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[38] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[39] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xcfdf8000 - 0xcfdfbfff (0x4000) MX[B]
	[1] -1	0	0xcfdff000 - 0xcfdff7ff (0x800) MX[B]
	[2] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[3] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[4] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[5] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[6] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[7] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[8] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[9] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[10] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[11] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[12] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[13] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[14] -1	0	0xca000000 - 0xcbffffff (0x2000000) MX[B](B)
	[15] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[18] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[20] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[21] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[24] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[25] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[26] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[27] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[28] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[29] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[30] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[31] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[32] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[33] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[34] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[35] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[36] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[37] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[38] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[39] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
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
	[4] -1	0	0xcfdf8000 - 0xcfdfbfff (0x4000) MX[B]
	[5] -1	0	0xcfdff000 - 0xcfdff7ff (0x800) MX[B]
	[6] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[7] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[8] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[9] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[10] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[11] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[12] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[13] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[14] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[15] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[16] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[17] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[18] -1	0	0xca000000 - 0xcbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[31] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[32] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[33] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[34] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[36] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[37] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[38] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[39] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[40] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[41] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[42] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[43] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[44] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[45] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
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
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9755
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-9755  Mon Feb 26 23:23:13 PST 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(WW) Warning, couldn't open module wfb
(II) UnloadModule: "wfb"
(EE) Failed to load module "wfb" (module does not exist, 0)
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfdf8000 - 0xcfdfbfff (0x4000) MX[B]
	[5] -1	0	0xcfdff000 - 0xcfdff7ff (0x800) MX[B]
	[6] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[7] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[8] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[9] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[10] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[11] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[12] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[13] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[14] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[15] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[16] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[17] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[18] -1	0	0xca000000 - 0xcbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[24] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[26] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[27] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[29] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[30] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[31] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[32] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[33] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[34] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[36] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[37] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[38] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[39] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[40] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[41] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[42] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[43] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[44] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[45] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xcfdf8000 - 0xcfdfbfff (0x4000) MX[B]
	[5] -1	0	0xcfdff000 - 0xcfdff7ff (0x800) MX[B]
	[6] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[7] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[8] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[9] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[10] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[11] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[12] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[13] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[14] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[15] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[16] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[17] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[18] -1	0	0xca000000 - 0xcbffffff (0x2000000) MX[B](B)
	[19] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[20] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[21] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[22] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[23] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[27] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[28] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[29] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[30] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[31] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[32] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[33] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[34] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[35] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[36] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[37] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[38] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[39] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[40] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[41] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[42] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[43] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[44] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[45] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[46] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[47] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[48] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
	[49] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[50] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 8800 GTX at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 786432 kBytes
(--) NVIDIA(0): VideoBIOS: 60.80.08.00.37
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8800 GTX at PCI:1:0:0:
(--) NVIDIA(0):     Samsung SyncMaster (DFP-1)
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): Samsung SyncMaster (DFP-1): Internal Dual Link TMDS
(II) NVIDIA(0): Assigned Display Device: DFP-1
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200"
(II) NVIDIA(0):     "1024x768"
(II) NVIDIA(0):     "800x600"
(II) NVIDIA(0):     "640x480"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(++) NVIDIA(0): DPI set to (100, 100); computed from -dpi X commandline option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xca000000 - 0xcbffffff (0x2000000) MX[B]
	[1] 0	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B]
	[2] 0	0	0xcc000000 - 0xccffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xcfdf8000 - 0xcfdfbfff (0x4000) MX[B]
	[8] -1	0	0xcfdff000 - 0xcfdff7ff (0x800) MX[B]
	[9] -1	0	0xcfff5000 - 0xcfff500f (0x10) MX[B]
	[10] -1	0	0xcfff6000 - 0xcfff60ff (0x100) MX[B]
	[11] -1	0	0xcfff7000 - 0xcfff7fff (0x1000) MX[B]
	[12] -1	0	0xcfff8000 - 0xcfff800f (0x10) MX[B]
	[13] -1	0	0xcfff9000 - 0xcfff90ff (0x100) MX[B]
	[14] -1	0	0xcfffa000 - 0xcfffafff (0x1000) MX[B]
	[15] -1	0	0xcfff0000 - 0xcfff3fff (0x4000) MX[B]
	[16] -1	0	0xcfffb000 - 0xcfffbfff (0x1000) MX[B]
	[17] -1	0	0xcfffc000 - 0xcfffcfff (0x1000) MX[B]
	[18] -1	0	0xcfffd000 - 0xcfffdfff (0x1000) MX[B]
	[19] -1	0	0xcfffe000 - 0xcfffe0ff (0x100) MX[B]
	[20] -1	0	0xcffff000 - 0xcfffffff (0x1000) MX[B]
	[21] -1	0	0xca000000 - 0xcbffffff (0x2000000) MX[B](B)
	[22] -1	0	0xb0000000 - 0xbfffffff (0x10000000) MX[B](B)
	[23] -1	0	0xcc000000 - 0xccffffff (0x1000000) MX[B](B)
	[24] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[25] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[26] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[27] 0	0	0x00009c00 - 0x00009c7f (0x80) IX[B]
	[28] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[29] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[30] -1	0	0x0000a800 - 0x0000a807 (0x8) IX[B]
	[31] -1	0	0x0000ac00 - 0x0000ac07 (0x8) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b00f (0x10) IX[B]
	[33] -1	0	0x0000b400 - 0x0000b403 (0x4) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[35] -1	0	0x0000bc00 - 0x0000bc03 (0x4) IX[B]
	[36] -1	0	0x0000c000 - 0x0000c007 (0x8) IX[B]
	[37] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[38] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[39] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[40] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[41] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[42] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[43] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[44] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[45] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[46] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[47] -1	0	0x0000ec00 - 0x0000ec0f (0x10) IX[B]
	[48] -1	0	0x0000f000 - 0x0000f03f (0x40) IX[B]
	[49] -1	0	0x0000f400 - 0x0000f43f (0x40) IX[B]
	[50] -1	0	0x0000f800 - 0x0000f83f (0x40) IX[B]
	[51] -1	0	0x0000fc00 - 0x0000fc7f (0x80) IX[B]
	[52] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
	[53] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[54] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1600x1200"
(--) NVIDIA(0): No video decoder detected
(II) NVIDIA(0): Setting mode "1600x1200"
(--) NVIDIA(0): No video decoder detected
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(EE) NVIDIA(0): Need libwfb but wfbScreenInit not found

Fatal server error:
AddScreen/ScreenInit failed for driver 0

[/HTML]

---

### Post by rich.bradshaw on 2007-04-20
I think you should have just gone to System/Admin/Restricted Drivers, and it would have done it automagically. No sure how to fix it, but perhaps if you end up reinstalling, just try that.

---

### Post by Steve H on 2007-04-20
Alot of people have had problems with Feisty and the Restricted Modules, have a look at [_this thread_]("http://ubuntuforums.org/showthread.php?t=409940"):

I had similar problem, I had to download the drivers from Nvidia and reinstall them.

Hope it helps.

---

### Post by alien_doggy on 2007-04-20
> **rich.bradshaw said:**
> I think you should have just gone to System/Admin/Restricted Drivers, and it would have done it automagically. No sure how to fix it, but perhaps if you end up reinstalling, just try that.

Do I access System/Admin/Restricted Drivers true k-menu right?
Cant find it :-k

---

### Post by bg1256 on 2007-04-20
I can't find this tool in Kubuntu.  Methinks it's only a Gnome thing, which is incredibly disappointing.

---

