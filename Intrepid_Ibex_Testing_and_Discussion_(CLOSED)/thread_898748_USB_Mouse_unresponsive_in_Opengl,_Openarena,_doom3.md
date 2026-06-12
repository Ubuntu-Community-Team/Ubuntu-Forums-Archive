---
title: "USB Mouse unresponsive in Opengl, Openarena, doom3.."
date: 2008-08-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by grigio on 2008-08-23
My usb mouse works well in gnome but in Opengl it is slow..

ideas?

---

### Post by RIchard James13 on 2008-08-24
First major possibility is that your video drivers are not set up correctly and OpenGL is running in software mode thus making the mouse sluggish. You can check this by using the keyboard to move around in a game, if the movement is still sluggish it would probably be a video driver issue.

The second thing to check is that your mouse movement is smooth in a non-3D game, especially any that use SDL. Try pingus as that game requires a mouse to play.

---

### Post by grigio on 2008-08-24
I use the catalyst fglrx driver

---

### Post by Nullack on 2008-08-24
You sure about that :) Checkout your X logs

---

### Post by grigio on 2008-08-24
Here is the log
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
Current Operating System: Linux utente-desktop 2.6.26-4-generic #1 SMP Mon Jul 14 18:39:53 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Aug 24 10:24:50 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(**) Extension "Composite" is enabled
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first core pointer device.
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
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2e20 card 1043,82d3 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2e21 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,3a37 card 1043,82d4 rev 00 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,3a38 card 1043,82d4 rev 00 class 0c,03,00 hdr 00
(II) PCI: 00:1a:2: chip 8086,3a39 card 1043,82d4 rev 00 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,3a3c card 1043,82d4 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,3a3e card 1043,82fe rev 00 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,3a40 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,3a48 card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,3a4a card 0000,0000 rev 00 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,3a34 card 1043,82d4 rev 00 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,3a35 card 1043,82d4 rev 00 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,3a36 card 1043,82d4 rev 00 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,3a3a card 1043,82d4 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 90 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,3a16 card 1043,82d4 rev 00 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,3a20 card 1043,82d4 rev 00 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,3a30 card 1043,82d4 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,3a26 card 1043,82d4 rev 00 class 01,01,85 hdr 00
(II) PCI: 01:00:0: chip 1002,9442 card 1002,0502 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,aa30 card 1002,aa30 rev 00 class 04,03,00 hdr 80
(II) PCI: 02:00:0: chip 1969,1026 card 1043,8226 rev b0 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 11ab,6121 card 1043,82e0 rev b2 class 01,01,8f hdr 00
(II) PCI: 05:00:0: chip 10ec,8185 card 13d1,8225 rev 20 class 02,00,00 hdr 00
(II) PCI: 05:02:0: chip 1131,7133 card 1043,4876 rev d1 class 04,80,00 hdr 00
(II) PCI: 05:03:0: chip 11c1,5811 card 1043,8294 rev 70 class 0c,00,10 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x001a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xfdf00000 - 0xfdffffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
*[I]*[/I](II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:5), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfeb00000 - 0xfebfffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc unknown chipset (0x9442) rev 0, Mem @ 0xd0000000/28, 0xfe8e0000/16, I/O @ 0xb000/8, BIOS @ 0xfe8c0000/17
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
	[0] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[1] -1	0	0xfebff000 - 0xfebff7ff (0x800) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebffdff (0x200) MX[B]
	[3] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[4] -1	0	0xfe9c0000 - 0xfe9fffff (0x40000) MX[B]
	[5] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[6] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[7] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[8] -1	0	0xfe7f8000 - 0xfe7fbfff (0x4000) MX[B]
	[9] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[10] -1	0	0xfe8c0000 - 0xfe8dffff (0x20000) MX[B](B)
	[11] -1	0	0xfe8e0000 - 0xfe8effff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[15] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[17] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[20] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[21] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[24] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[26] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[27] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[28] -1	0	0x00008480 - 0x0000848f (0x10) IX[B]
	[29] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[30] -1	0	0x00008880 - 0x00008887 (0x8) IX[B]
	[31] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[32] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[33] -1	0	0x0000a480 - 0x0000a49f (0x20) IX[B]
	[34] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[35] -1	0	0x0000a080 - 0x0000a09f (0x20) IX[B]
	[36] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[37] -1	0	0x0000a880 - 0x0000a89f (0x20) IX[B]
	[38] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[39] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[1] -1	0	0xfebff000 - 0xfebff7ff (0x800) MX[B]
	[2] -1	0	0xfebffc00 - 0xfebffdff (0x200) MX[B]
	[3] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[4] -1	0	0xfe9c0000 - 0xfe9fffff (0x40000) MX[B]
	[5] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[6] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[7] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[8] -1	0	0xfe7f8000 - 0xfe7fbfff (0x4000) MX[B]
	[9] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[10] -1	0	0xfe8c0000 - 0xfe8dffff (0x20000) MX[B](B)
	[11] -1	0	0xfe8e0000 - 0xfe8effff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[15] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[16] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[17] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[18] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[19] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[20] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[21] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[22] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[23] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[24] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[26] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[27] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[28] -1	0	0x00008480 - 0x0000848f (0x10) IX[B]
	[29] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[30] -1	0	0x00008880 - 0x00008887 (0x8) IX[B]
	[31] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[32] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[33] -1	0	0x0000a480 - 0x0000a49f (0x20) IX[B]
	[34] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[35] -1	0	0x0000a080 - 0x0000a09f (0x20) IX[B]
	[36] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[37] -1	0	0x0000a880 - 0x0000a89f (0x20) IX[B]
	[38] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[39] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
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
	[4] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebff7ff (0x800) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffdff (0x200) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[8] -1	0	0xfe9c0000 - 0xfe9fffff (0x40000) MX[B]
	[9] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[10] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[11] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[12] -1	0	0xfe7f8000 - 0xfe7fbfff (0x4000) MX[B]
	[13] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[14] -1	0	0xfe8c0000 - 0xfe8dffff (0x20000) MX[B](B)
	[15] -1	0	0xfe8e0000 - 0xfe8effff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[26] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[27] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[28] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[29] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[30] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[32] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[33] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[34] -1	0	0x00008480 - 0x0000848f (0x10) IX[B]
	[35] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[36] -1	0	0x00008880 - 0x00008887 (0x8) IX[B]
	[37] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[38] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[39] -1	0	0x0000a480 - 0x0000a49f (0x20) IX[B]
	[40] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[41] -1	0	0x0000a080 - 0x0000a09f (0x20) IX[B]
	[42] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[43] -1	0	0x0000a880 - 0x0000a89f (0x20) IX[B]
	[44] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[45] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers//fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.51.3
	Module class: X.Org Video Driver
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
(II) Primary Device is: PCI 01:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.51.3
(II) ATI Proprietary Linux Driver Release Identifier: UNSUPPORTED-8.512                    
(II) ATI Proprietary Linux Driver Build Date: Jul  3 2008 22:50:40
(--) Assigning device section with no busID to primary device
(--) Chipset Supported AMD Graphics Processor (0x9442) found
(II) AMD Video driver is running on a device belonging to a group targeted for this release
(II) AMD Video driver is signed
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebff7ff (0x800) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffdff (0x200) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[8] -1	0	0xfe9c0000 - 0xfe9fffff (0x40000) MX[B]
	[9] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[10] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[11] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[12] -1	0	0xfe7f8000 - 0xfe7fbfff (0x4000) MX[B]
	[13] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[14] -1	0	0xfe8c0000 - 0xfe8dffff (0x20000) MX[B](B)
	[15] -1	0	0xfe8e0000 - 0xfe8effff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[21] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[22] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[23] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[25] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[26] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[27] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[28] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[29] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[30] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[31] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[32] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[33] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[34] -1	0	0x00008480 - 0x0000848f (0x10) IX[B]
	[35] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[36] -1	0	0x00008880 - 0x00008887 (0x8) IX[B]
	[37] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[38] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[39] -1	0	0x0000a480 - 0x0000a49f (0x20) IX[B]
	[40] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[41] -1	0	0x0000a080 - 0x0000a09f (0x20) IX[B]
	[42] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[43] -1	0	0x0000a880 - 0x0000a89f (0x20) IX[B]
	[44] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[45] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x90a7768
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebff7ff (0x800) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebffdff (0x200) MX[B]
	[7] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[8] -1	0	0xfe9c0000 - 0xfe9fffff (0x40000) MX[B]
	[9] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[10] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[11] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[12] -1	0	0xfe7f8000 - 0xfe7fbfff (0x4000) MX[B]
	[13] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[14] -1	0	0xfe8c0000 - 0xfe8dffff (0x20000) MX[B](B)
	[15] -1	0	0xfe8e0000 - 0xfe8effff (0x10000) MX[B](B)
	[16] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[24] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[26] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[27] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[28] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[29] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[30] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[31] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[32] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[33] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[34] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[35] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[36] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[37] -1	0	0x00008480 - 0x0000848f (0x10) IX[B]
	[38] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[39] -1	0	0x00008880 - 0x00008887 (0x8) IX[B]
	[40] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[41] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[42] -1	0	0x0000a480 - 0x0000a49f (0x20) IX[B]
	[43] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[44] -1	0	0x0000a080 - 0x0000a09f (0x20) IX[B]
	[45] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[46] -1	0	0x0000a880 - 0x0000a89f (0x20) IX[B]
	[47] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[48] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
	[49] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[50] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [atiddxPreInit] === begin
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): PCI bus 1 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "MonitorLayout" "AUTO, AUTO"
(**) fglrx(0): Option "UseInternalAGPGART" "no"
(II) fglrx(0): Loading PCS database from /etc/ati/amdpcsdb
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(--) fglrx(0): Chipset: "ATI Radeon HD 4800 Series" (Chipset = 0x9442)
(--) fglrx(0): (PciSubVendor = 0x1002, PciSubDevice = 0x0502)
(--) fglrx(0): board vendor info: original ATI graphics adapter
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xfe8e0000
(--) fglrx(0): I/O port at 0x0000b000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 3.0
(II) fglrx(0): VESA VBE Total Mem: 16384 kB
(II) fglrx(0): VESA VBE OEM: ATI ATOMBIOS
(II) fglrx(0): VESA VBE OEM Software Rev: 11.3
(II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2005, ATI Technologies Inc. 
(II) fglrx(0): VESA VBE OEM Product: RV770
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) fglrx(0): ATI Video BIOS revision 9 or later detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.51.3
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): Using adapter: 1:0.0.
(II) fglrx(0): [FB] Find the MC FB aperturs range(MCFBBase = 0xfe0000000, MCFBSize = 0x20000000)
(--) fglrx(0): VideoRAM: 262144 kByte, Type: GDDR3
(II) fglrx(0): PCIE card detected
(--) fglrx(0): Using per-process page tables (PPPT) as GART.
(II) fglrx(0): board/chipset is supported by this driver (original ATI board)
(WW) fglrx(0): MonitorLayout is no longer supported. 
               Please use DesktopSetup and ForceMonitors options
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) fglrx(0): Connected Display1: CRT on primary DAC [crt1]
(II) fglrx(0): Display1 EDID data ---------------------------
(II) fglrx(0): Manufacturer: BNQ  Model: 3  Serial#: 409
(II) fglrx(0): Year: 2002  Week: 50
(II) fglrx(0): EDID Version: 1.3
(II) fglrx(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) fglrx(0): Sync:  Separate  Composite  SyncOnGreen
(II) fglrx(0): Max H-Image Size [cm]: horiz.: 39  vert.: 29
(II) fglrx(0): Gamma: 2.86
(II) fglrx(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) fglrx(0): First detailed timing not preferred mode in violation of standard!(II) fglrx(0): redX: 0.642 redY: 0.321   greenX: 0.284 greenY: 0.595
(II) fglrx(0): blueX: 0.144 blueY: 0.061   whiteX: 0.282 whiteY: 0.297
(II) fglrx(0): Supported VESA Video Modes:
(II) fglrx(0): 720x400@70Hz
(II) fglrx(0): 640x480@60Hz
(II) fglrx(0): 640x480@72Hz
(II) fglrx(0): 640x480@75Hz
(II) fglrx(0): 800x600@56Hz
(II) fglrx(0): 800x600@60Hz
(II) fglrx(0): 800x600@72Hz
(II) fglrx(0): 800x600@75Hz
(II) fglrx(0): 1024x768@60Hz
(II) fglrx(0): 1024x768@70Hz
(II) fglrx(0): 1024x768@75Hz
(II) fglrx(0): 1280x1024@75Hz
(II) fglrx(0): Manufacturer's mask: 0
(II) fglrx(0): Supported Future Video Modes:
(II) fglrx(0): #0: hsize: 1600  vsize 1200  refresh: 85  vid: 22953
(II) fglrx(0): #1: hsize: 1600  vsize 1200  refresh: 75  vid: 20393
(II) fglrx(0): #2: hsize: 1280  vsize 1024  refresh: 85  vid: 39297
(II) fglrx(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) fglrx(0): #4: hsize: 1920  vsize 1440  refresh: 75  vid: 20433
(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 157.5 MHz   Image Size:  360 x 270 mm
(II) fglrx(0): h_active: 1280  h_sync: 1344  h_sync_end 1504 h_blank_end 1728 h_border: 0
(II) fglrx(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1072 v_border: 0
(II) fglrx(0): Monitor name: BENQ P211
(II) fglrx(0): Serial No: 00409
(II) fglrx(0): Ranges: V min: 50  V max: 160 Hz, H min: 30  H max: 115 kHz, PixClock max 290 MHz
(II) fglrx(0): EDID (in hex):
(II) fglrx(0): 	00ffffffffffff0009d1030099010000
(II) fglrx(0): 	320c01030e271dbae85de4a452489824
(II) fglrx(0): 	0f484cafcf00a959a94f81996159d14f
(II) fglrx(0): 	010101010101863d00c05100304040a0
(II) fglrx(0): 	1300680e11000000000000fc0042454e
(II) fglrx(0): 	5120503231310a202020000000ff0030
(II) fglrx(0): 	303430390a20202020202020000000fd
(II) fglrx(0): 	0032a01e731d000a202020202020008e
(II) fglrx(0): End of Display1 EDID data --------------------
(WW) fglrx(0): Only one display is connnected,so single mode is enabled
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000001
(==) fglrx(0): Qbs is not supported in this release. Disabled.
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 74 modes found for primary display.
(--) fglrx(0): Virtual size is 1920x1440 (pitch 0)
(**) fglrx(0): *Mode "1920x1440": 297.0 MHz (scaled from 0.0 MHz), 112.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1920x1440"x75.0  297.00  1920 2064 2288 2640  1440 1441 1444 1500 +hsync (112.5 kHz)
(**) fglrx(0):  Default mode "1920x1440": 234.0 MHz (scaled from 0.0 MHz), 90.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 +hsync (90.0 kHz)
(**) fglrx(0): *Mode "1920x1200": 281.2 MHz (scaled from 0.0 MHz), 107.2 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1920x1200"x85.0  281.25  1920 2064 2272 2624  1200 1203 1209 1262 +hsync (107.2 kHz)
(**) fglrx(0):  Default mode "1920x1200": 245.2 MHz (scaled from 0.0 MHz), 94.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1920x1200"x75.0  245.25  1920 2056 2264 2608  1200 1203 1209 1255 +hsync (94.0 kHz)
(**) fglrx(0):  Default mode "1920x1200": 193.2 MHz (scaled from 0.0 MHz), 74.6 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1200"x60.0  193.25  1920 2056 2256 2592  1200 1203 1209 1245 +hsync (74.6 kHz)
(**) fglrx(0): *Mode "1920x1080": 220.6 MHz (scaled from 0.0 MHz), 84.6 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1920x1080"x75.0  220.63  1920 2056 2264 2608  1080 1081 1084 1128 +hsync (84.6 kHz)
(**) fglrx(0):  Default mode "1920x1080": 172.8 MHz (scaled from 0.0 MHz), 67.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"x60.0  172.79  1920 2040 2248 2576  1080 1081 1084 1118 +hsync (67.1 kHz)
(**) fglrx(0):  Default mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"x30.0   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync (33.6 kHz)
(**) fglrx(0): *Mode "1856x1392": 218.2 MHz (scaled from 0.0 MHz), 86.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1856x1392"x60.0  218.25  1856 1952 2176 2528  1392 1393 1396 1439 +hsync (86.3 kHz)
(**) fglrx(0): *Mode "1800x1440": 259.4 MHz (scaled from 0.0 MHz), 104.9 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1800x1440"x70.0  259.38  1800 1936 2136 2472  1440 1441 1444 1499 +hsync (104.9 kHz)
(**) fglrx(0):  Default mode "1800x1440": 219.6 MHz (scaled from 0.0 MHz), 89.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1800x1440"x60.0  219.56  1800 1928 2128 2456  1440 1441 1444 1490 +hsync (89.4 kHz)
(**) fglrx(0): *Mode "1792x1344": 261.0 MHz (scaled from 0.0 MHz), 106.3 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1792x1344"x75.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 +hsync (106.3 kHz)
(**) fglrx(0):  Default mode "1792x1344": 204.8 MHz (scaled from 0.0 MHz), 83.6 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1792x1344"x60.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 +hsync (83.6 kHz)
(**) fglrx(0): *Mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +vsync (65.3 kHz)
(**) fglrx(0): *Mode "1600x1200": 229.5 MHz (scaled from 0.0 MHz), 106.2 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1600x1200"x85.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 (106.2 kHz)
(**) fglrx(0):  Default mode "1600x1200": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200"x75.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 (93.8 kHz)
(**) fglrx(0):  Default mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 (91.1 kHz)
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(0):  Default mode "1280x1024": 191.0 MHz (scaled from 0.0 MHz), 108.5 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1280x1024"x100.0  190.96  1280 1376 1520 1760  1024 1025 1028 1085 +hsync (108.5 kHz)
(**) fglrx(0):  Default mode "1280x1024": 169.2 MHz (scaled from 0.0 MHz), 97.0 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1280x1024"x90.0  169.20  1280 1376 1512 1744  1024 1025 1028 1078 +hsync (97.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 +hsync (77.1 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(0):  Default mode "1152x864": 143.5 MHz (scaled from 0.0 MHz), 91.5 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 +hsync (91.5 kHz)
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 (68.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 139.1 MHz (scaled from 0.0 MHz), 98.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "1024x768"x120.0  139.05  1024 1104 1216 1408  768 769 772 823 +hsync (98.8 kHz)
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"x100.0  113.30  1024 1096 1208 1392  768 769 772 814 +hsync (81.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"x90.0  100.18  1024 1088 1200 1376  768 769 772 809 +hsync (72.8 kHz)
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 (53.7 kHz)
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 116.4 MHz (scaled from 0.0 MHz), 105.4 kHz, 160.0 Hz
(II) fglrx(0): Modeline "800x600"x160.0  116.40  800 864 952 1104  600 601 604 659 +hsync (105.4 kHz)
(**) fglrx(0):  Default mode "800x600": 83.9 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"x120.0   83.94  800 856 944 1088  600 601 604 643 +hsync (77.2 kHz)
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 +hsync (63.6 kHz)
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"x90.0   60.06  800 840 928 1056  600 601 604 632 +hsync (56.9 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 +hsync +vsync (43.3 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"x160.0   72.85  640 680 752 864  480 481 484 527 +hsync (84.3 kHz)
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"x120.0   52.40  640 680 744 848  480 481 484 515 +hsync (61.8 kHz)
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"x100.0   43.16  640 680 744 848  480 481 484 509 +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"x90.0   37.89  640 672 736 832  480 481 484 506 +hsync (45.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(--) fglrx(0): Display dimensions: (390, 290) mm
(--) fglrx(0): DPI set to (125, 126)
(--) fglrx(0): Virtual size is 1920x1440 (pitch 1920)
(**) fglrx(0): *Mode "1920x1440": 297.0 MHz (scaled from 0.0 MHz), 112.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1920x1440"x75.0  297.00  1920 2064 2288 2640  1440 1441 1444 1500 +hsync (112.5 kHz)
(**) fglrx(0):  Default mode "1920x1440": 234.0 MHz (scaled from 0.0 MHz), 90.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1440"x60.0  234.00  1920 2048 2256 2600  1440 1441 1444 1500 +hsync (90.0 kHz)
(**) fglrx(0): *Mode "1920x1200": 281.2 MHz (scaled from 0.0 MHz), 107.2 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1920x1200"x85.0  281.25  1920 2064 2272 2624  1200 1203 1209 1262 +hsync (107.2 kHz)
(**) fglrx(0):  Default mode "1920x1200": 245.2 MHz (scaled from 0.0 MHz), 94.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1920x1200"x75.0  245.25  1920 2056 2264 2608  1200 1203 1209 1255 +hsync (94.0 kHz)
(**) fglrx(0):  Default mode "1920x1200": 193.2 MHz (scaled from 0.0 MHz), 74.6 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1200"x60.0  193.25  1920 2056 2256 2592  1200 1203 1209 1245 +hsync (74.6 kHz)
(**) fglrx(0): *Mode "1920x1080": 220.6 MHz (scaled from 0.0 MHz), 84.6 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1920x1080"x75.0  220.63  1920 2056 2264 2608  1080 1081 1084 1128 +hsync (84.6 kHz)
(**) fglrx(0):  Default mode "1920x1080": 172.8 MHz (scaled from 0.0 MHz), 67.1 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1920x1080"x60.0  172.79  1920 2040 2248 2576  1080 1081 1084 1118 +hsync (67.1 kHz)
(**) fglrx(0):  Default mode "1920x1080": 81.6 MHz (scaled from 0.0 MHz), 33.6 kHz, 30.0 Hz (I)
(II) fglrx(0): Modeline "1920x1080"x30.0   81.64  1920 1984 2176 2432  1080 1081 1084 1119 interlace +hsync (33.6 kHz)
(**) fglrx(0): *Mode "1856x1392": 218.2 MHz (scaled from 0.0 MHz), 86.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1856x1392"x60.0  218.25  1856 1952 2176 2528  1392 1393 1396 1439 +hsync (86.3 kHz)
(**) fglrx(0): *Mode "1800x1440": 259.4 MHz (scaled from 0.0 MHz), 104.9 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1800x1440"x70.0  259.38  1800 1936 2136 2472  1440 1441 1444 1499 +hsync (104.9 kHz)
(**) fglrx(0):  Default mode "1800x1440": 219.6 MHz (scaled from 0.0 MHz), 89.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1800x1440"x60.0  219.56  1800 1928 2128 2456  1440 1441 1444 1490 +hsync (89.4 kHz)
(**) fglrx(0): *Mode "1792x1344": 261.0 MHz (scaled from 0.0 MHz), 106.3 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1792x1344"x75.0  261.00  1792 1888 2104 2456  1344 1345 1348 1417 +hsync (106.3 kHz)
(**) fglrx(0):  Default mode "1792x1344": 204.8 MHz (scaled from 0.0 MHz), 83.6 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1792x1344"x60.0  204.75  1792 1920 2120 2448  1344 1345 1348 1394 +hsync (83.6 kHz)
(**) fglrx(0): *Mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 +vsync (65.3 kHz)
(**) fglrx(0): *Mode "1600x1200": 229.5 MHz (scaled from 0.0 MHz), 106.2 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1600x1200"x85.0  229.50  1600 1664 1856 2160  1200 1201 1204 1250 (106.2 kHz)
(**) fglrx(0):  Default mode "1600x1200": 202.5 MHz (scaled from 0.0 MHz), 93.8 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1600x1200"x75.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 (93.8 kHz)
(**) fglrx(0):  Default mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 (75.0 kHz)
(**) fglrx(0): *Mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1440x900"x60.0  106.50  1440 1520 1672 1904  900 903 909 934 +vsync (55.9 kHz)
(**) fglrx(0): *Mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 +hsync (65.3 kHz)
(**) fglrx(0): *Mode "1280x1024": 157.5 MHz (scaled from 0.0 MHz), 91.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1280x1024"x85.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 (91.1 kHz)
(**) fglrx(0):  Default mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 (80.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 +hsync (74.6 kHz)
(**) fglrx(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 (64.0 kHz)
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x47.0   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"x43.0   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync (46.3 kHz)
(**) fglrx(0):  Default mode "1280x1024": 191.0 MHz (scaled from 0.0 MHz), 108.5 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1280x1024"x100.0  190.96  1280 1376 1520 1760  1024 1025 1028 1085 +hsync (108.5 kHz)
(**) fglrx(0):  Default mode "1280x1024": 169.2 MHz (scaled from 0.0 MHz), 97.0 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1280x1024"x90.0  169.20  1280 1376 1512 1744  1024 1025 1028 1078 +hsync (97.0 kHz)
(**) fglrx(0): *Mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 (60.0 kHz)
(**) fglrx(0): *Mode "1280x768": 79.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x768"x60.0   79.50  1280 1344 1472 1664  768 771 778 798 +hsync (47.8 kHz)
(**) fglrx(0): *Mode "1280x720": 74.5 MHz (scaled from 0.0 MHz), 44.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 +hsync (44.8 kHz)
(**) fglrx(0): *Mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 +hsync (77.1 kHz)
(**) fglrx(0):  Default mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 (67.5 kHz)
(**) fglrx(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1152x864"x70.0   96.76  1152 1224 1344 1536  864 865 868 900 +hsync (63.0 kHz)
(**) fglrx(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 +hsync (53.7 kHz)
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"x43.0   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync (39.2 kHz)
(**) fglrx(0):  Default mode "1152x864": 143.5 MHz (scaled from 0.0 MHz), 91.5 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1152x864"x100.0  143.47  1152 1232 1360 1568  864 865 868 915 +hsync (91.5 kHz)
(**) fglrx(0): *Mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 (68.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 (60.0 kHz)
(**) fglrx(0):  Default mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
(II) fglrx(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 +hsync (57.7 kHz)
(**) fglrx(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.0 Hz
(II) fglrx(0): Modeline "1024x768"x70.0   75.00  1024 1048 1184 1328  768 771 777 806 +hsync +vsync (56.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync (48.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 44.9 MHz (scaled from 0.0 MHz), 35.5 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1024x768"x43.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace (35.5 kHz)
(**) fglrx(0):  Default mode "1024x768": 139.1 MHz (scaled from 0.0 MHz), 98.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "1024x768"x120.0  139.05  1024 1104 1216 1408  768 769 772 823 +hsync (98.8 kHz)
(**) fglrx(0):  Default mode "1024x768": 113.3 MHz (scaled from 0.0 MHz), 81.4 kHz, 100.0 Hz
(II) fglrx(0): Modeline "1024x768"x100.0  113.30  1024 1096 1208 1392  768 769 772 814 +hsync (81.4 kHz)
(**) fglrx(0):  Default mode "1024x768": 100.2 MHz (scaled from 0.0 MHz), 72.8 kHz, 90.0 Hz
(II) fglrx(0): Modeline "1024x768"x90.0  100.18  1024 1088 1200 1376  768 769 772 809 +hsync (72.8 kHz)
(**) fglrx(0): *Mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.0 Hz
(II) fglrx(0): Modeline "800x600"x85.0   56.25  800 832 896 1048  600 601 604 631 (53.7 kHz)
(**) fglrx(0):  Default mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 (46.9 kHz)
(**) fglrx(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.0 Hz
(II) fglrx(0): Modeline "800x600"x72.0   50.00  800 856 976 1040  600 637 643 666 (48.1 kHz)
(**) fglrx(0):  Default mode "800x600": 45.5 MHz (scaled from 0.0 MHz), 43.8 kHz, 70.0 Hz
(II) fglrx(0): Modeline "800x600"x70.0   45.50  800 840 920 1040  600 601 604 625 +hsync (43.8 kHz)
(**) fglrx(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 (37.9 kHz)
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"x56.0   36.00  800 824 896 1024  600 601 603 625 (35.2 kHz)
(**) fglrx(0):  Default mode "800x600": 116.4 MHz (scaled from 0.0 MHz), 105.4 kHz, 160.0 Hz
(II) fglrx(0): Modeline "800x600"x160.0  116.40  800 864 952 1104  600 601 604 659 +hsync (105.4 kHz)
(**) fglrx(0):  Default mode "800x600": 83.9 MHz (scaled from 0.0 MHz), 77.2 kHz, 120.0 Hz
(II) fglrx(0): Modeline "800x600"x120.0   83.94  800 856 944 1088  600 601 604 643 +hsync (77.2 kHz)
(**) fglrx(0):  Default mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
(II) fglrx(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 +hsync (63.6 kHz)
(**) fglrx(0):  Default mode "800x600": 60.1 MHz (scaled from 0.0 MHz), 56.9 kHz, 90.0 Hz
(II) fglrx(0): Modeline "800x600"x90.0   60.06  800 840 928 1056  600 601 604 632 +hsync (56.9 kHz)
(**) fglrx(0): *Mode "720x480": 26.7 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "720x480"x60.0   26.71  720 736 808 896  480 481 484 497 +hsync (29.8 kHz)
(**) fglrx(0): *Mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) fglrx(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 +hsync +vsync (43.3 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 +hsync +vsync (37.5 kHz)
(**) fglrx(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.0 Hz
(II) fglrx(0): Modeline "640x480"x72.0   31.50  640 664 704 832  480 489 492 520 +hsync +vsync (37.9 kHz)
(**) fglrx(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 +hsync +vsync (31.5 kHz)
(**) fglrx(0):  Default mode "640x480": 72.8 MHz (scaled from 0.0 MHz), 84.3 kHz, 160.0 Hz
(II) fglrx(0): Modeline "640x480"x160.0   72.85  640 680 752 864  480 481 484 527 +hsync (84.3 kHz)
(**) fglrx(0):  Default mode "640x480": 52.4 MHz (scaled from 0.0 MHz), 61.8 kHz, 120.0 Hz
(II) fglrx(0): Modeline "640x480"x120.0   52.40  640 680 744 848  480 481 484 515 +hsync (61.8 kHz)
(**) fglrx(0):  Default mode "640x480": 43.2 MHz (scaled from 0.0 MHz), 50.9 kHz, 100.0 Hz
(II) fglrx(0): Modeline "640x480"x100.0   43.16  640 680 744 848  480 481 484 509 +hsync (50.9 kHz)
(**) fglrx(0):  Default mode "640x480": 37.9 MHz (scaled from 0.0 MHz), 45.5 kHz, 90.0 Hz
(II) fglrx(0): Modeline "640x480"x90.0   37.89  640 672 736 832  480 481 484 506 +hsync (45.5 kHz)
(**) fglrx(0):  Default mode "640x400": 28.1 MHz (scaled from 0.0 MHz), 33.7 kHz, 75.0 Hz
(II) fglrx(0): Modeline "640x400"x75.0   28.07  640 696 736 832  400 413 415 449 (33.7 kHz)
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"x60.0   24.92  640 664 760 792  400 460 462 525 (31.5 kHz)
(**) fglrx(0):  Default mode "512x384": 19.7 MHz (scaled from 0.0 MHz), 31.1 kHz, 75.0 Hz
(II) fglrx(0): Modeline "512x384"x75.0   19.68  512 528 576 632  384 384 385 416 (31.1 kHz)
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"x60.0   19.81  512 544 624 664  384 451 453 497 (29.8 kHz)
(**) fglrx(0):  Default mode "400x300": 24.8 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x75.0   24.75  400 408 448 528  300 601 602 625 doublescan (46.9 kHz)
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"x60.0   22.33  400 416 480 496  300 601 605 742 doublescan (45.0 kHz)
(**) fglrx(0):  Default mode "320x240": 15.8 MHz (scaled from 0.0 MHz), 37.9 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x75.0   15.75  320 328 360 416  240 481 482 501 doublescan (37.9 kHz)
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"x60.0   12.59  320 328 376 400  240 491 493 525 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 13.1 MHz (scaled from 0.0 MHz), 31.5 kHz, 75.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x75.0   13.10  320 352 368 416  200 406 407 417 doublescan (31.5 kHz)
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"x60.0   12.59  320 336 384 400  200 457 459 524 doublescan (31.5 kHz)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux//libfglrxdrm.so
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x8000001d
(==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
(**) fglrx(0): ATI GART size: 255 MB
(II) fglrx(0): [pcie] 261120 kB allocated
(II) fglrx(0): [drm] DRM buffer queue setup: nbufs = 100 bufsize = 65536
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xfe8e0000 - 0xfe8effff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebff000 - 0xfebff7ff (0x800) MX[B]
	[8] -1	0	0xfebffc00 - 0xfebffdff (0x200) MX[B]
	[9] -1	0	0xfeaffc00 - 0xfeafffff (0x400) MX[B]
	[10] -1	0	0xfe9c0000 - 0xfe9fffff (0x40000) MX[B]
	[11] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[12] -1	0	0xfe7ff400 - 0xfe7ff4ff (0x100) MX[B]
	[13] -1	0	0xfe7ff800 - 0xfe7ffbff (0x400) MX[B]
	[14] -1	0	0xfe7f8000 - 0xfe7fbfff (0x4000) MX[B]
	[15] -1	0	0xfe7ffc00 - 0xfe7fffff (0x400) MX[B]
	[16] -1	0	0xfe8c0000 - 0xfe8dffff (0x20000) MX[B](B)
	[17] -1	0	0xfe8e0000 - 0xfe8effff (0x10000) MX[B](B)
	[18] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[19] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[20] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[21] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[22] 0	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[26] -1	0	0x0000d400 - 0x0000d40f (0x10) IX[B]
	[27] -1	0	0x0000d480 - 0x0000d483 (0x4) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d807 (0x8) IX[B]
	[29] -1	0	0x0000d880 - 0x0000d883 (0x4) IX[B]
	[30] -1	0	0x0000dc00 - 0x0000dc07 (0x8) IX[B]
	[31] -1	0	0x0000cc00 - 0x0000cc7f (0x80) IX[B]
	[32] -1	0	0x00009400 - 0x0000940f (0x10) IX[B]
	[33] -1	0	0x00009480 - 0x0000948f (0x10) IX[B]
	[34] -1	0	0x00009800 - 0x00009803 (0x4) IX[B]
	[35] -1	0	0x00009880 - 0x00009887 (0x8) IX[B]
	[36] -1	0	0x00009c00 - 0x00009c03 (0x4) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a007 (0x8) IX[B]
	[38] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[39] -1	0	0x00008400 - 0x0000840f (0x10) IX[B]
	[40] -1	0	0x00008480 - 0x0000848f (0x10) IX[B]
	[41] -1	0	0x00008800 - 0x00008803 (0x4) IX[B]
	[42] -1	0	0x00008880 - 0x00008887 (0x8) IX[B]
	[43] -1	0	0x00008c00 - 0x00008c03 (0x4) IX[B]
	[44] -1	0	0x00009000 - 0x00009007 (0x8) IX[B]
	[45] -1	0	0x0000a480 - 0x0000a49f (0x20) IX[B]
	[46] -1	0	0x0000a400 - 0x0000a41f (0x20) IX[B]
	[47] -1	0	0x0000a080 - 0x0000a09f (0x20) IX[B]
	[48] -1	0	0x0000ac00 - 0x0000ac1f (0x20) IX[B]
	[49] -1	0	0x0000a880 - 0x0000a89f (0x20) IX[B]
	[50] -1	0	0x0000a800 - 0x0000a81f (0x20) IX[B]
	[51] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B](B)
	[52] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[53] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): detected X.org 7.1.0.90
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
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
(II) [drm] DRM interface version 1.0
(II) [drm] DRM open master succeeded.
(II) fglrx(0): [drm] Using the DRM lock SAREA also for drawables.
(II) fglrx(0): [drm] framebuffer handle = 0x3000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): X context handle = 0x1
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.51.3
(II) fglrx(0):     Date: Jul  3 2008
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.26-4-generic
(II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
(II) fglrx(0):     Build-Kernel __SMP__:            yes
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
(II) fglrx(0): [drm] register handle = 0x00005000
(II) fglrx(0): Interrupt handler installed at IRQ 16.
(II) fglrx(0): Exposed events to the /proc interface
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): FBADPhys: 0xfe0000000 FBMappedSize: 0x01068000
(II) fglrx(0): FBMM initialized for area (0,0)-(1920,2240)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1920,1440) (front color buffer - assumption)
(II) fglrx(0): Largest offscreen area available: 1920 x 800
(==) fglrx(0): Backing store disabled
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
(II) fglrx(0): DPMS enabled
(**) fglrx(0): Textured Video is enabled.
(II) LoadModule: "glesx"
(II) Loading /usr/lib/xorg/modules//glesx.so
(II) Module glesx: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension GLESX
(II) fglrx(0): GLESX enableFlags = 26
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Driver provided ScreenToScreenBitBlt replacement
	Driver provided FillSolidRects replacement
(II) fglrx(0): GLESX is enabled
(II) LoadModule: "amdxmm"
(II) Loading /usr/lib/xorg/modules//amdxmm.so
(II) Module amdxmm: vendor="X.Org Foundation"
	compiled for 7.1.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) fglrx(0): [DRI] installation complete
(II) fglrx(0): Direct rendering enabled
(II) fglrx(0): Finished Initialize PPLIB!
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
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
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
(WW) AIGLX: 3D driver claims to not support visual 0x33
(WW) AIGLX: 3D driver claims to not support visual 0x34
(WW) AIGLX: 3D driver claims to not support visual 0x35
(WW) AIGLX: 3D driver claims to not support visual 0x36
(WW) AIGLX: 3D driver claims to not support visual 0x37
(WW) AIGLX: 3D driver claims to not support visual 0x38
(WW) AIGLX: 3D driver claims to not support visual 0x39
(WW) AIGLX: 3D driver claims to not support visual 0x3a
(WW) AIGLX: 3D driver claims to not support visual 0x3b
(WW) AIGLX: 3D driver claims to not support visual 0x3c
(WW) AIGLX: 3D driver claims to not support visual 0x3d
(WW) AIGLX: 3D driver claims to not support visual 0x3e
(WW) AIGLX: 3D driver claims to not support visual 0x3f
(WW) AIGLX: 3D driver claims to not support visual 0x40
(WW) AIGLX: 3D driver claims to not support visual 0x41
(WW) AIGLX: 3D driver claims to not support visual 0x42
(WW) AIGLX: 3D driver claims to not support visual 0x43
(WW) AIGLX: 3D driver claims to not support visual 0x44
(WW) AIGLX: 3D driver claims to not support visual 0x45
(WW) AIGLX: 3D driver claims to not support visual 0x46
(WW) AIGLX: 3D driver claims to not support visual 0x47
(WW) AIGLX: 3D driver claims to not support visual 0x48
(WW) AIGLX: 3D driver claims to not support visual 0x49
(WW) AIGLX: 3D driver claims to not support visual 0x4a
(WW) AIGLX: 3D driver claims to not support visual 0x4b
(WW) AIGLX: 3D driver claims to not support visual 0x4c
(WW) AIGLX: 3D driver claims to not support visual 0x4d
(WW) AIGLX: 3D driver claims to not support visual 0x4e
(WW) AIGLX: 3D driver claims to not support visual 0x4f
(WW) AIGLX: 3D driver claims to not support visual 0x50
(WW) AIGLX: 3D driver claims to not support visual 0x51
(WW) AIGLX: 3D driver claims to not support visual 0x52
(WW) AIGLX: 3D driver claims to not support visual 0x53
(WW) AIGLX: 3D driver claims to not support visual 0x54
(WW) AIGLX: 3D driver claims to not support visual 0x55
(WW) AIGLX: 3D driver claims to not support visual 0x56
(WW) AIGLX: 3D driver claims to not support visual 0x57
(WW) AIGLX: 3D driver claims to not support visual 0x58
(WW) AIGLX: 3D driver claims to not support visual 0x59
(WW) AIGLX: 3D driver claims to not support visual 0x5a
(WW) AIGLX: 3D driver claims to not support visual 0x5b
(WW) AIGLX: 3D driver claims to not support visual 0x5c
(WW) AIGLX: 3D driver claims to not support visual 0x5d
(WW) AIGLX: 3D driver claims to not support visual 0x5e
(WW) AIGLX: 3D driver claims to not support visual 0x5f
(WW) AIGLX: 3D driver claims to not support visual 0x60
(WW) AIGLX: 3D driver claims to not support visual 0x61
(WW) AIGLX: 3D driver claims to not support visual 0x62
(WW) AIGLX: 3D driver claims to not support visual 0x63
(WW) AIGLX: 3D driver claims to not support visual 0x64
(WW) AIGLX: 3D driver claims to not support visual 0x65
(WW) AIGLX: 3D driver claims to not support visual 0x66
(WW) AIGLX: 3D driver claims to not support visual 0x67
(WW) AIGLX: 3D driver claims to not support visual 0x68
(WW) AIGLX: 3D driver claims to not support visual 0x69
(WW) AIGLX: 3D driver claims to not support visual 0x6a
(WW) AIGLX: 3D driver claims to not support visual 0x6b
(WW) AIGLX: 3D driver claims to not support visual 0x6c
(WW) AIGLX: 3D driver claims to not support visual 0x6d
(WW) AIGLX: 3D driver claims to not support visual 0x6e
(WW) AIGLX: 3D driver claims to not support visual 0x6f
(WW) AIGLX: 3D driver claims to not support visual 0x70
(WW) AIGLX: 3D driver claims to not support visual 0x71
(WW) AIGLX: 3D driver claims to not support visual 0x72
(II) AIGLX: Loaded and initialized /usr/lib/dri/fglrx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) fglrx(0): Enable the clock gating!
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
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
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(**) saa7134 IR (ASUSTeK P7131 Hybri: always reports core events
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "it"
(II) XINPUT: Adding extended input device "saa7134 IR (ASUSTeK P7131 Hybri" (type: KEYBOARD)
(II) saa7134 IR (ASUSTeK P7131 Hybri: Init
(II) saa7134 IR (ASUSTeK P7131 Hybri: On
(**) Logitech USB Optical Mouse: always reports core events
(II) Logitech USB Optical Mouse: Found 3 relative axes.
(II) Logitech USB Optical Mouse: Configuring as pointer.
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Configured 6 mouse buttons.
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: 2 valuators.
(**) Logitech USB Optical Mouse: Configuring in Absolute mode.
(**) Logitech USB Optical Mouse: Registering 6 buttons.
(II) Logitech USB Optical Mouse: Init
(II) Logitech USB Optical Mouse: On
(**) LITEON Technology USB Multimedia Keyboard: always reports core events
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "it"
(II) XINPUT: Adding extended input device "LITEON Technology USB Multimedia Keyboard" (type: KEYBOARD)
(II) LITEON Technology USB Multimedia Keyboard: Init
(II) LITEON Technology USB Multimedia Keyboard: On
(**) Macintosh mouse button emulation: always reports core events
(II) Macintosh mouse button emulation: Found 2 relative axes.
(II) Macintosh mouse button emulation: Configuring as pointer.
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configured 4 mouse buttons.
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: 2 valuators.
(**) Macintosh mouse button emulation: Configuring in Absolute mode.
(**) Macintosh mouse button emulation: Registering 4 buttons.
(II) Macintosh mouse button emulation: Init
(II) Macintosh mouse button emulation: On
Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().
Warning: LookupWindow()/SecurityLookupWindow() are deprecated.  Please convert your driver/module to use dixLookupWindow().
SetClientVersion: 0 9
(II) Macintosh mouse button emulation: Off
(II) LITEON Technology USB Multimedia Keyboard: Off
(II) Logitech USB Optical Mouse: Off
(II) saa7134 IR (ASUSTeK P7131 Hybri: Off
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) Macintosh mouse button emulation: On
(II) LITEON Technology USB Multimedia Keyboard: On
(II) Logitech USB Optical Mouse: On
(II) saa7134 IR (ASUSTeK P7131 Hybri: On
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
(II) Macintosh mouse button emulation: Off
(II) LITEON Technology USB Multimedia Keyboard: Off
(II) Logitech USB Optical Mouse: Off
(II) saa7134 IR (ASUSTeK P7131 Hybri: Off
(II) AIGLX: Suspending AIGLX clients for VT switch
(II) Open ACPI successful (/var/run/acpid.socket)
(II) AIGLX: Resuming AIGLX clients after VT switch
(II) Macintosh mouse button emulation: On
(II) LITEON Technology USB Multimedia Keyboard: On
(II) Logitech USB Optical Mouse: On
(II) saa7134 IR (ASUSTeK P7131 Hybri: On
(II) Configured Mouse: ps2EnableDataReporting: succeeded
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
```

---

### Post by grigio on 2008-08-25
up

---

### Post by Nullack on 2008-08-25
Personally Im not going to provide you with support because you are not in Intrepid build revisions. You have a custom version of X installed and thats not part of the Intrepid build.

---

### Post by RIchard James13 on 2008-08-26
I don't think it should be saying
> (WW) Configured Mouse: No Device specified, looking for one...

Protocol is set to Auto maybe it should be set to ImPS/2

What does your input device section of you /etc/X11/xorg.conf read like?

Mine looks like this
```
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
```

---

