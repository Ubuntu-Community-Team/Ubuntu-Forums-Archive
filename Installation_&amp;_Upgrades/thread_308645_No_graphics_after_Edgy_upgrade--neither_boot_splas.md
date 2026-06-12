---
title: "No graphics after Edgy upgrade--neither boot splash nor X.org"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by haynold on 2006-11-28
[SIZE="2"]Hello:

I upgraded to Edgy. Unfortunately, after the upgrade I don't get any kind of graphical output whatsoever on my machine--the console is all that works. I'm using an HP xw6000 workstation with an ATI graphics card.

On bootup, I see a blinking cursor on a dark screen where there used to be a splash screen under Dapper. Worse, X starts up, plays sounds, and responds to key commands. The log file (below, it's a little long, but I figured the bus scan output may be relevant) didn't suggest an obvious error to me either. But the screen doesn't get any signal and thus goes into energy saving mode.

When I'm using the ATI driver, I can kill X.org and get back to a working console. With the proprietary driver, I can still do that, but the screen stays black and doesn't even come back into text mode.

Does anyone have an idea what's going on there?

Best,

       Oliver

Here's the X.org log for the ATI driver:

[/SIZE]
[SIZE="1"]```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux xantara 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 28 01:01:17 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "hp L2335"
(**) |   |-->Device "ATI Technologies, Inc. Radeon 9600 (RV350 AS)"
(**) |-->Input Device "Sun Type 6 Keyboard"
(==) Keyboard: CustomKeycode disabled
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "LIRC Mouse"
    --SNIP--
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2550 card 103c,00cc rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2552 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 103c,00cc rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 103c,00cc rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 103c,00cc rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 103c,00cc rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 103c,00cc rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 103c,00c3 rev 01 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 1002,4153 card 17ee,2002 rev 00 class 03,00,00 hdr 80
(II) PCI: 01:00:1: chip 1002,4173 card 17ee,2003 rev 00 class 03,80,00 hdr 00
(II) PCI: 05:02:0: chip 14e4,16a6 card 103c,00cc rev 02 class 02,00,00 hdr 00
(II) PCI: 05:0a:0: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 05:0a:1: chip 1106,3038 card 1106,3038 rev 61 class 0c,03,00 hdr 80
(II) PCI: 05:0a:2: chip 1106,3104 card 1106,3104 rev 63 class 0c,03,20 hdr 80
(II) PCI: 05:0c:0: chip 9005,801f card 103c,00cc rev 03 class 01,00,00 hdr 80
(II) PCI: 05:0c:1: chip 9005,801f card 103c,00cc rev 03 class 01,00,00 hdr 80
(II) PCI: 05:0e:0: chip 10cd,1300 card 10cd,1310 rev 03 class 01,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00003000 - 0x00003fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf0500000 - 0xf07fffff (0x300000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xf01fffff (0x20200000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[2] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[3] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[4] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[5] -1	0	0x00002400 - 0x000024ff (0x100) IX[B]
	[6] -1	0	0x00002800 - 0x000028ff (0x100) IX[B]
	[7] -1	0	0x00002c00 - 0x00002cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xf0200000 - 0xf04fffff (0x300000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0x70000000 - 0x701fffff (0x200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) ATI Technologies Inc RV350 AS [Radeon 9550] rev 0, Mem @ 0xd0000000/28, 0xf0500000/16, I/O @ 0x3000/8
(--) PCI: (1:0:1) ATI Technologies Inc RV350 ? [Radeon 9550] (Secondary) rev 0, Mem @ 0xe0000000/28, 0xf0510000/16
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
(II) PCI Memory resource overlap reduced 0xf4000000 from 0xf7ffffff to 0xf3ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf0414100 - 0xf04141ff (0x100) MX[B]
	[1] -1	0	0xf0412000 - 0xf0413fff (0x2000) MX[B]
	[2] -1	0	0xf0410000 - 0xf0411fff (0x2000) MX[B]
	[3] -1	0	0xf0414000 - 0xf04140ff (0x100) MX[B]
	[4] -1	0	0xf0400000 - 0xf040ffff (0x10000) MX[B]
	[5] -1	0	0xf0a00600 - 0xf0a006ff (0x100) MX[B]
	[6] -1	0	0xf0a00400 - 0xf0a005ff (0x200) MX[B]
	[7] -1	0	0x70200000 - 0x702003ff (0x400) MX[B]
	[8] -1	0	0xf0a00000 - 0xf0a003ff (0x400) MX[B]
	[9] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[10] -1	0	0xf0510000 - 0xf051ffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf0500000 - 0xf050ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00002420 - 0x0000243f (0x20) IX[B]
	[16] -1	0	0x00002400 - 0x0000241f (0x20) IX[B]
	[17] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[18] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[19] -1	0	0x000044c0 - 0x000044cf (0x10) IX[B]
	[20] -1	0	0x000044e4 - 0x000044e4 (0x1) IX[B]
	[21] -1	0	0x000044d8 - 0x000044d8 (0x1) IX[B]
	[22] -1	0	0x000044e0 - 0x000044e0 (0x1) IX[B]
	[23] -1	0	0x000044d0 - 0x000044d0 (0x1) IX[B]
	[24] -1	0	0x00004480 - 0x0000449f (0x20) IX[B]
	[25] -1	0	0x00004460 - 0x0000447f (0x20) IX[B]
	[26] -1	0	0x00004440 - 0x0000445f (0x20) IX[B]
	[27] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[1] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[2] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[3] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xf0414100 - 0xf04141ff (0x100) MX[B]
	[1] -1	0	0xf0412000 - 0xf0413fff (0x2000) MX[B]
	[2] -1	0	0xf0410000 - 0xf0411fff (0x2000) MX[B]
	[3] -1	0	0xf0414000 - 0xf04140ff (0x100) MX[B]
	[4] -1	0	0xf0400000 - 0xf040ffff (0x10000) MX[B]
	[5] -1	0	0xf0a00600 - 0xf0a006ff (0x100) MX[B]
	[6] -1	0	0xf0a00400 - 0xf0a005ff (0x200) MX[B]
	[7] -1	0	0x70200000 - 0x702003ff (0x400) MX[B]
	[8] -1	0	0xf0a00000 - 0xf0a003ff (0x400) MX[B]
	[9] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[10] -1	0	0xf0510000 - 0xf051ffff (0x10000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xf0500000 - 0xf050ffff (0x10000) MX[B](B)
	[13] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[14] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[15] -1	0	0x00002420 - 0x0000243f (0x20) IX[B]
	[16] -1	0	0x00002400 - 0x0000241f (0x20) IX[B]
	[17] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[18] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[19] -1	0	0x000044c0 - 0x000044cf (0x10) IX[B]
	[20] -1	0	0x000044e4 - 0x000044e4 (0x1) IX[B]
	[21] -1	0	0x000044d8 - 0x000044d8 (0x1) IX[B]
	[22] -1	0	0x000044e0 - 0x000044e0 (0x1) IX[B]
	[23] -1	0	0x000044d0 - 0x000044d0 (0x1) IX[B]
	[24] -1	0	0x00004480 - 0x0000449f (0x20) IX[B]
	[25] -1	0	0x00004460 - 0x0000447f (0x20) IX[B]
	[26] -1	0	0x00004440 - 0x0000445f (0x20) IX[B]
	[27] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[1] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[2] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[3] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
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
	[4] -1	0	0xf0414100 - 0xf04141ff (0x100) MX[B]
	[5] -1	0	0xf0412000 - 0xf0413fff (0x2000) MX[B]
	[6] -1	0	0xf0410000 - 0xf0411fff (0x2000) MX[B]
	[7] -1	0	0xf0414000 - 0xf04140ff (0x100) MX[B]
	[8] -1	0	0xf0400000 - 0xf040ffff (0x10000) MX[B]
	[9] -1	0	0xf0a00600 - 0xf0a006ff (0x100) MX[B]
	[10] -1	0	0xf0a00400 - 0xf0a005ff (0x200) MX[B]
	[11] -1	0	0x70200000 - 0x702003ff (0x400) MX[B]
	[12] -1	0	0xf0a00000 - 0xf0a003ff (0x400) MX[B]
	[13] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[14] -1	0	0xf0510000 - 0xf051ffff (0x10000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xf0500000 - 0xf050ffff (0x10000) MX[B](B)
	[17] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[21] -1	0	0x00002420 - 0x0000243f (0x20) IX[B]
	[22] -1	0	0x00002400 - 0x0000241f (0x20) IX[B]
	[23] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[24] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[25] -1	0	0x000044c0 - 0x000044cf (0x10) IX[B]
	[26] -1	0	0x000044e4 - 0x000044e4 (0x1) IX[B]
	[27] -1	0	0x000044d8 - 0x000044d8 (0x1) IX[B]
	[28] -1	0	0x000044e0 - 0x000044e0 (0x1) IX[B]
	[29] -1	0	0x000044d0 - 0x000044d0 (0x1) IX[B]
	[30] -1	0	0x00004480 - 0x0000449f (0x20) IX[B]
	[31] -1	0	0x00004460 - 0x0000447f (0x20) IX[B]
	[32] -1	0	0x00004440 - 0x0000445f (0x20) IX[B]
	[33] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[34] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[35] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[36] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[37] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.1.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 6.6.2
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "keyboard"
(II) Loading /usr/lib/xorg/modules/input/keyboard_drv.so
(II) Module keyboard: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) ATI: ATI driver (version 6.6.2) for chipsets: ati, ativga
  --- SNIP ---
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon 9600 (RV350 AS)".
(--) Assigning device section with no busID to primary device
(WW) RADEON: No matching Device section for instance (BusID PCI:1:0:1) found
(--) Chipset ATI Radeon 9600 AS (AGP) found
   --SNIP--
(II) Setting vga for screen 0.
(**) RADEON(0): RADEONPreInit
(II) RADEON(0): MMIO registers at 0xf0500000: size 64KB
(II) RADEON(0): PCI bus 1 card 0 func 0
(**) RADEON(0): Depth 24, (--) framebuffer bpp 32
(II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) RADEON(0): Default visual is TrueColor
(**) RADEON(0): Option "MonitorLayout" "TMDS, AUTO"
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(==) RADEON(0): RGB weight 888
(II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
(++) RADEON(0): "-dpi 100" given in command line, assuming "ConstantDPI" set
(++) RADEON(0): X server will keep DPI constant for all screen sizes
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) RADEON(0): initializing int10
(II) RADEON(0): Primary V_BIOS segment is: 0xc000
(--) RADEON(0): Chipset: "ATI Radeon 9600 AS (AGP)" (ChipID = 0x4153)
(--) RADEON(0): Linear framebuffer at 0xd0000000
(II) RADEON(0): AGP card detected
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [dri] Found DRI library version 1.2.0 and kernel module version 1.25.0
(II) RADEON(0): AGP Fast Write disabled by default
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) RADEON(0): Page flipping disabled
(II) RADEON(0): Will try to use DMA for Xv image transfers
(II) RADEON(0): Generation 2 PCI interface, using max accessible memory
(II) RADEON(0): Detected total video RAM=262144K, accessible=262144K (PCI BAR=262144K)
(--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
(II) RADEON(0): Color tiling enabled by default
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) RADEON(0): I2C bus "DDC" initialized.
(II) RADEON(0): Legacy BIOS detected
(II) RADEON(0): Connector0: DDCType-2, DACType-1, TMDSType-0, ConnectorType-3
(II) RADEON(0): Connector1: DDCType-3, DACType-0, TMDSType--1, ConnectorType-2
(**) RADEON(0): MonitorLayout Option: 
	Monitor1--Type TMDS, Monitor2--Type AUTO

(**) RADEON(0): Option "NoDDC"
(II) RADEON(0): DDC Type: 2, Detected Type: 0
(II) RADEON(0): DDC Type: 3, Detected Type: 0
(II) RADEON(0): 
(II) RADEON(0): Primary:
 Monitor   -- TMDS
 Connector -- DVI-I
 DAC Type  -- TVDAC/ExtDAC
 TMDS Type -- Internal
 DDC Type  -- DVI_DDC
(II) RADEON(0): Secondary:
 Monitor   -- NONE
 Connector -- VGA
 DAC Type  -- Primary
 TMDS Type -- NONE
 DDC Type  -- VGA_DDC
(II) RADEON(0): PLL parameters: rf=2700 rd=12 min=20000 max=40000; xclk=20000
(WW) RADEON(0): Failed to detect secondary monitor, MergedFB/Clone mode disabled
(==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
(II) RADEON(0): Validating modes on Primary head ---------
(II) RADEON(0): DFP table revision: 3
(II) RADEON(0): Total number of valid DDC mode(s) found: 0
(II) RADEON(0): hp L2335: Using hsync range of 30.00-100.00 kHz
(II) RADEON(0): hp L2335: Using vrefresh value of 60.00 Hz
(II) RADEON(0): Clock range:  20.00 to 400.00 MHz
   -- SNIP --
(++) RADEON(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(==) RADEON(0): Using XAA acceleration architecture
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(II) RADEON(0): No MM_TABLE found - assuming CARD is not TV-in capable.
(!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xf0500000 - 0xf050ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xf0414100 - 0xf04141ff (0x100) MX[B]
	[7] -1	0	0xf0412000 - 0xf0413fff (0x2000) MX[B]
	[8] -1	0	0xf0410000 - 0xf0411fff (0x2000) MX[B]
	[9] -1	0	0xf0414000 - 0xf04140ff (0x100) MX[B]
	[10] -1	0	0xf0400000 - 0xf040ffff (0x10000) MX[B]
	[11] -1	0	0xf0a00600 - 0xf0a006ff (0x100) MX[B]
	[12] -1	0	0xf0a00400 - 0xf0a005ff (0x200) MX[B]
	[13] -1	0	0x70200000 - 0x702003ff (0x400) MX[B]
	[14] -1	0	0xf0a00000 - 0xf0a003ff (0x400) MX[B]
	[15] -1	0	0xf4000000 - 0xf3ffffff (0x0) MX[B]O
	[16] -1	0	0xf0510000 - 0xf051ffff (0x10000) MX[B](B)
	[17] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[18] -1	0	0xf0500000 - 0xf050ffff (0x10000) MX[B](B)
	[19] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[23] 0	0	0x00003000 - 0x000030ff (0x100) IX[B]
	[24] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[25] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[26] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
	[27] -1	0	0x00002420 - 0x0000243f (0x20) IX[B]
	[28] -1	0	0x00002400 - 0x0000241f (0x20) IX[B]
	[29] -1	0	0x00004400 - 0x0000443f (0x40) IX[B]
	[30] -1	0	0x00004000 - 0x000040ff (0x100) IX[B]
	[31] -1	0	0x000044c0 - 0x000044cf (0x10) IX[B]
	[32] -1	0	0x000044e4 - 0x000044e4 (0x1) IX[B]
	[33] -1	0	0x000044d8 - 0x000044d8 (0x1) IX[B]
	[34] -1	0	0x000044e0 - 0x000044e0 (0x1) IX[B]
	[35] -1	0	0x000044d0 - 0x000044d0 (0x1) IX[B]
	[36] -1	0	0x00004480 - 0x0000449f (0x20) IX[B]
	[37] -1	0	0x00004460 - 0x0000447f (0x20) IX[B]
	[38] -1	0	0x00004440 - 0x0000445f (0x20) IX[B]
	[39] -1	0	0x00003000 - 0x000030ff (0x100) IX[B](B)
	[40] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[41] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
	[42] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[43] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[44] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[45] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(**) RADEON(0): RADEONScreenInit d0000000 0
(**) RADEON(0): Map: 0xd0000000, 0x10000000
(==) RADEON(0): Write-combining range (0xd0000000,0x10000000)
(**) RADEON(0): RADEONSave
(**) RADEON(0): RADEONSaveMode(0x81fd168)
(**) RADEON(0): Read: 0x00080002 0x00010014 0x00000000
(**) RADEON(0): Read: rd=2, fd=20, pd=1
(**) RADEON(0): RADEONSaveMode returns 0x81fd168
(==) RADEON(0): Using 24 bit depth buffer
(WW) RADEON(0): Enabling DRM support

	*** Direct rendering support is highly experimental for Radeon 9500
	*** and newer cards. The 3d mesa driver is not provided in this tree.
	*** A very experimental (and incomplete) version is available from Mesa CVS.
	*** Additional information can be found on http://r300.sourceforge.net
	*** This message has been last modified on 2005-08-07.

drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) RADEON(0): [drm] DRM interface version 1.2
(II) RADEON(0): [drm] created "radeon" driver at busid "pci:0000:01:00.0"
(II) RADEON(0): [drm] added 8192 byte SAREA at 0xf95be000
(II) RADEON(0): [drm] mapped SAREA 0xf95be000 to 0xb7bb9000
(II) RADEON(0): [drm] framebuffer handle = 0xd0000000
(II) RADEON(0): [drm] added 1 reserved context for kernel
(II) RADEON(0): [agp] Mode 0x1f004209 [AGP 0x8086/0x2550; Card 0x1002/0x4153]
(II) RADEON(0): [agp] 8192 kB allocated with handle 0x00000001
(II) RADEON(0): [agp] ring handle = 0xf4000000
(II) RADEON(0): [agp] Ring mapped at 0xa7991000
(II) RADEON(0): [agp] ring read ptr handle = 0xf4101000
(II) RADEON(0): [agp] Ring read ptr mapped at 0xb7fad000
(II) RADEON(0): [agp] vertex/indirect buffers handle = 0xf4102000
(II) RADEON(0): [agp] Vertex/indirect buffers mapped at 0xa7791000
(II) RADEON(0): [agp] GART texture map handle = 0xf4302000
(II) RADEON(0): [agp] GART Texture map mapped at 0xa72b1000
(II) RADEON(0): [drm] register handle = 0xf0500000
(II) RADEON(0): [dri] Visual configs initialized
(**) RADEON(0): DRI New memory map param
(**) RADEON(0): RADEONInitMemoryMap() : 
(**) RADEON(0):   mem_size         : 0x10000000
(**) RADEON(0):   MC_FB_LOCATION   : 0xdfffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0): RADEONModeInit()
1920x1200       0.00     0    0    0    0     0    0    0    0 (24,32)
1920x1200       0.00     0    0    0    0     0    0    0    0 (24,32)
(**) RADEON(0): Pitch = 16777472 bytes (virtualX = 2048, displayWidth = 2048)
(**) RADEON(0): TMDS_PLL from 1fbb0155 to 1fbb0155
(II) RADEON(0): BIOS HotKeys Enabled
(**) RADEON(0): RADEONInit returns 0x81fdb18
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fdb18)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0xdfffd000
(**) RADEON(0):   MC_AGP_LOCATION  : 0xffffffc0
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00080002 0x00010014 0x00000000 (0x0000bf00)
(**) RADEON(0): Wrote: rd=2, fd=20, pd=1
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 20000000
(**) RADEON(0): RADEONSaveScreen(0)
(II) RADEON(0): Depth moves disabled by default
(**) RADEON(0): Setting up initial surfaces
(**) RADEON(0): Initializing fb layer
(**) RADEON(0): Setting up accel memmap
(II) RADEON(0): CP in BM mode
(II) RADEON(0): Using 8 MB GART aperture
(II) RADEON(0): Using 1 MB for the ring buffer
(II) RADEON(0): Using 2 MB for vertex/indirect buffers
(II) RADEON(0): Using 5 MB for GART textures
(II) RADEON(0): Memory manager initialized to (0,0) (2048,8191)
(II) RADEON(0): Reserved area from (0,1536) to (2048,1538)
(II) RADEON(0): Largest offscreen area available: 2048 x 6653
(II) RADEON(0): Will use back buffer at offset 0x3000000
(II) RADEON(0): Will use depth buffer at offset 0x3c00000
(II) RADEON(0): Will use 188416 kb for textures at offset 0x4800000
(**) RADEON(0): Initializing backing store
(==) RADEON(0): Backing store disabled
(**) RADEON(0): DRI Finishing init !
(II) RADEON(0): X context handle = 0x1
(II) RADEON(0): [drm] installed DRM signal handler
(II) RADEON(0): [DRI] installation complete
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
(II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
(II) RADEON(0): [drm] dma control initialized, using IRQ 193
(II) RADEON(0): [drm] Initialized kernel GART heap manager, 5111808
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xdfffd000 is: 0xdfffd000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xf47ff400
(**) RADEON(0): GRPH_BUFFER_CNTL from 30004c4c to 20000000
(II) RADEON(0): Direct rendering enabled
(**) RADEON(0): Setting up final surfaces
(**) RADEON(0): Initializing Acceleration
(II) RADEON(0): Render acceleration unsupported on Radeon 9500/9700 and newer.
(II) RADEON(0): Render acceleration disabled
(**) RADEON(0): EngineInit (32/32)
(**) RADEON(0): Pitch for acceleration = 256
(**) RADEON(0): EngineRestore (32/32)
(II) RADEON(0): Using XFree86 Acceleration Architecture (XAA)
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
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): Initializing DPMS
(**) Option "dpms"
(**) RADEON(0): DPMS enabled
(**) RADEON(0): Initializing Cursor
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): Using hardware cursor (scanline 1538)
(II) RADEON(0): Largest offscreen area available: 2048 x 6651
(**) RADEON(0): Initializing color map
(**) RADEON(0): Initializing DGA
(**) RADEON(0): Initializing Xv
(II) RADEON(0): No video input capabilities detected and no information is provided - disabling multimedia i2c
(II) Loading sub module "theatre_detect"
(II) LoadModule: "theatre_detect"
(II) Loading /usr/lib/xorg/modules/multimedia/theatre_detect_drv.so
(II) Module theatre_detect: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(II) RADEON(0): no multimedia table present, disabling Rage Theatre.
(**) RADEON(0): RADEONScreenInit finished
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
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
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
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
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Sun Type 6 Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Sun Type 6 Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Sun Type 6 Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Sun Type 6 Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Sun Type 6 Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Sun Type 6 Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "Protocol" "ImPS/2"
(**) LIRC Mouse: Device: "/dev/lircm"
(**) LIRC Mouse: Protocol: "ImPS/2"
(**) Option "Device" "/dev/lircm"
(==) LIRC Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) LIRC Mouse: ZAxisMapping: buttons 4 and 5
(**) LIRC Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "LIRC Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Sun Type 6 Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us" };
    xkb_geometry             { include "pc(pc105)" };
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element unix/:7100, removing from list!
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
(**) RADEON(0): RADEONSaveScreen(2)
(**) RADEON(0): RADEONCloseScreen
(**) RADEON(0): RADEONDRIStop
(**) RADEON(0): EngineRestore (32/32)
(**) RADEON(0): RADEONDisplayPowerManagementSet(0,0x0)
(**) RADEON(0): RADEONRestore
(**) RADEON(0): RADEONRestoreMode()
(**) RADEON(0): RADEONRestoreMode(0x81fd168)
(**) RADEON(0): RADEONRestoreMemMapRegisters() : 
(**) RADEON(0):   MC_FB_LOCATION   : 0x1fff0000
(**) RADEON(0):   MC_AGP_LOCATION  : 0x27ff2000
(**) RADEON(0):   Map Changed ! Applying ...
(**) RADEON(0):   Map applied, resetting engine ...
(**) RADEON(0): Updating display base addresses...
(**) RADEON(0): Memory map updated.
(**) RADEON(0): Programming CRTC1, offset: 0x00000000
(**) RADEON(0): Wrote: 0x00080002 0x00010014 0x00000000 (0x0000bf00)
(**) RADEON(0): Wrote: rd=2, fd=20, pd=1
(**) RADEON(0): Disposing accel...
(**) RADEON(0): Disposing cusor info
(**) RADEON(0): Disposing DGA
(**) RADEON(0): Unmapping memory
(**) RADEON(0): RADEONDRICloseScreen
(II) RADEON(0): [drm] removed 1 reserved context for kernel
(II) RADEON(0): [drm] unmapping 8192 bytes of SAREA 0xf95be000 at 0xb7bb9000
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
```[/SIZE]

---

### Post by Paul41 on 2006-11-28
Have you tried to switch to the non-proprietary driver to see if that helps. You can select all of the default options until you get to the video driver.
```
sudo dpkg-reconfigure xserver-xorg
```

That might at least get X working again until you can figure out what is wrong with the proprietary driver.

---

### Post by haynold on 2006-11-28
Yes, the sample output I posted is from the free driver. It behaves a little better than the proprietary driver: For both the screen goes blank, but the free driver at least allows me to switch back to a text console whereas the proprietary driver kills video until reboot.

---

### Post by haynold on 2006-11-29
Reconfiguring the X.org package (i.e., writing a new xorg.conf) made it work with the free driver!

I still can't get the proprietary driver to work, though. X starts normally with it except that the screen stays blank. Disconcertingly, the screen even stays blank after killing X--somehow the graphics card must get very confused or something.

---

