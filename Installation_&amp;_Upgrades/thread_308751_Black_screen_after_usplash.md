---
title: "Black screen after usplash"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by Rzulf on 2006-11-28
I have a strange when booting linux, after usplash I have a back screen but going to console and then alt+ctl+f7 everything starts to work just fine. I assume it is a problem with kdm so here is kdm.log but I don't really understand much from it.

```

SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux ubuntu 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Nov 28 18:14:57 2006
(==) Using config file: "/etc/X11/xorg.conf"
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+pl" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QInputContext: no input method context available
QInputContext: no input method context available
SetClientVersion: 0 9
SetGrabKeysState - disabled
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+pl" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No suc(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.h file or directory

Error opening /dev/wacom : No such file or directory
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
QInputContext: no input method context available
QInputContext: no input method context available

Backtrace:
0: /usr/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/lib/xorg/modules/libfb.so(fbResolveColor+0x32) [0xb735dd62]
3: /usr/bin/X(FakeAllocColor+0x58) [0x8078d68]
4: /usr/bin/X [0x811a2eb]
5: /usr/bin/X [0x811a660]
6: /usr/lib/xorg/modules/libramdac.so [0xb7c27c90]
7: /usr/bin/X(miPointerUpdate+0x164) [0x81129b4]
8: /usr/bin/X [0x8112ac9]
9: /usr/bin/X [0x8128ebe]
10: /usr/bin/X [0x814e4b7]
11: /usr/bin/X [0x808e387]
12: /usr/bin/X(DeactivatePointerGrab+0xa0) [0x80932c0]
13: /usr/bin/X(DeleteWindowFromAnyEvents+0x113) [0x8090ae3]
14: /usr/bin/X [0x80759a9]
15: /usr/bin/X(DeleteWindow+0x158) [0x8075c48]
16: /usr/bin/X(FreeClientResources+0x85) [0x806fc95]
17: /usr/bin/X(FreeAllResources+0x68) [0x806fd88]
18: /usr/bin/X(main+0x4b2) [0x806e742]
19: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7dd08cc]
20: /usr/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 8.  Server aborting


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux ubuntu 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 28 21:36:26 2006
(==) Using config file: "/etc/X11/xorg.conf"
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+pl" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
QInputContext: no input method context available
QInputContext: no input method context available
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+pl" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server

```

I hope you help me because I have the same problem on both ubuntu computers that I updated to edgy although they have totally different hardware.

---

### Post by cypherphreak on 2006-11-28
could you please post your xorg.conf and also lspci

---

### Post by Rzulf on 2006-11-28
```


00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:0d.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:13.0 Ethernet controller: Belkin Wireless PCI Card - F5D6001 (rev 20)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 02e1 (rev a2)


```

& 

```


X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux ubuntu 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Nov 28 21:36:26 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Philips 170S4"
(**) |   |-->Device "NVIDIA Corporation NVIDIA Default Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/TTF/" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/OTF" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/CID/" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.0
	X.Org XInput driver : 0.6
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1106,3189 card 1043,807f rev 80 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1106,b198 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:0d:0: chip 13f6,0111 card 13f6,0111 rev 10 class 04,01,00 hdr 00
(II) PCI: 00:0e:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0f:0: chip 1106,3149 card 1043,80ed rev 80 class 01,04,00 hdr 80
(II) PCI: 00:0f:1: chip 1106,0571 card 1043,80ed rev 06 class 01,01,8a hdr 00
(II) PCI: 00:10:0: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:1: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:2: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:3: chip 1106,3038 card 1043,80ed rev 81 class 0c,03,00 hdr 80
(II) PCI: 00:10:4: chip 1106,3104 card 1043,80ed rev 86 class 0c,03,20 hdr 80
(II) PCI: 00:11:0: chip 1106,3227 card 1043,80ed rev 00 class 06,01,00 hdr 80
(II) PCI: 00:11:5: chip 1106,3059 card 1043,810d rev 60 class 04,01,00 hdr 00
(II) PCI: 00:11:6: chip 1106,3068 card 0000,0000 rev 80 class 07,80,00 hdr 00
(II) PCI: 00:12:0: chip 1106,3065 card 1043,80ed rev 78 class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1799,6001 card 1799,6001 rev 20 class 02,00,00 hdr 00
(II) PCI: 01:00:0: chip 10de,02e1 card 1458,3428 rev a2 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdd000000 - 0xdfefffff (0x2f00000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xdff00000 - 0xefffffff (0x10100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:17:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation unknown chipset (0x02e1) rev 162, Mem @ 0xde000000/24, 0xe0000000/28, 0xdd000000/24, BIOS @ 0xdffe0000/17
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[1] -1	0	0xdb800000 - 0xdb8000ff (0x100) MX[B]
	[2] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[3] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[4] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[5] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[6] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[10] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[11] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[13] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[14] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[15] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[16] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[1] -1	0	0xdb800000 - 0xdb8000ff (0x100) MX[B]
	[2] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[3] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[4] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[5] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[6] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[7] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[8] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[9] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[10] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[11] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[12] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[13] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[14] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[15] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[16] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[17] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[18] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[22] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[23] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[24] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[25] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
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
	[4] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[5] -1	0	0xdb800000 - 0xdb8000ff (0x100) MX[B]
	[6] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[7] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[16] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[17] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[20] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[21] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[22] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[27] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
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
(II) Loading /usr/lib/xorg/modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.0
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.o
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.8776
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) NVIDIA X Driver  1.0-8776  Mon Oct 16 21:58:46 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
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
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[5] -1	0	0xdb800000 - 0xdb8000ff (0x100) MX[B]
	[6] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[7] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[16] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[17] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[18] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[19] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[20] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[21] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[22] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[27] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[28] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[30] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[31] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[5] -1	0	0xdb800000 - 0xdb8000ff (0x100) MX[B]
	[6] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[7] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[8] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[9] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[10] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[19] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[20] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[21] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[22] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[23] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[24] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[25] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[26] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[27] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[28] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[30] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[31] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[32] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[33] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[34] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS at PCI:1:0:0
(--) NVIDIA(0): VideoRAM: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.37.01
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:1:0:0:
(--) NVIDIA(0):     Philips 170S4 (CRT-1)
(--) NVIDIA(0): Philips 170S4 (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "1280x1024@60"; removing.
(WW) NVIDIA(0): No valid modes for "1024x768@60"; removing.
(WW) NVIDIA(0): No valid modes for "800x600@60"; removing.
(WW) NVIDIA(0): No valid modes for "640x480@60"; removing.
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (95, 96); computed from "UseEdidDpi" X config option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdd000000 - 0xddffffff (0x1000000) MX[B]
	[1] 0	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
	[2] 0	0	0xde000000 - 0xdeffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xdb000000 - 0xdb0000ff (0x100) MX[B]
	[8] -1	0	0xdb800000 - 0xdb8000ff (0x100) MX[B]
	[9] -1	0	0xdc000000 - 0xdc0000ff (0x100) MX[B]
	[10] -1	0	0xdc800000 - 0xdc8000ff (0x100) MX[B]
	[11] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[12] -1	0	0xdffe0000 - 0xdfffffff (0x20000) MX[B](B)
	[13] -1	0	0xdd000000 - 0xddffffff (0x1000000) MX[B](B)
	[14] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[15] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[19] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[20] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[21] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[22] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[23] -1	0	0x0000e500 - 0x0000e5ff (0x100) IX[B]
	[24] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[25] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[26] -1	0	0x00009000 - 0x0000901f (0x20) IX[B]
	[27] -1	0	0x00009400 - 0x0000941f (0x20) IX[B]
	[28] -1	0	0x00009800 - 0x0000981f (0x20) IX[B]
	[29] -1	0	0x0000a000 - 0x0000a00f (0x10) IX[B]
	[30] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[31] -1	0	0x0000a800 - 0x0000a80f (0x10) IX[B]
	[32] -1	0	0x0000b000 - 0x0000b003 (0x4) IX[B]
	[33] -1	0	0x0000b400 - 0x0000b407 (0x8) IX[B]
	[34] -1	0	0x0000b800 - 0x0000b803 (0x4) IX[B]
	[35] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[36] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[37] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) Initializing extension GLX
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "pl"
(**) Generic Keyboard: XkbLayout: "pl"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+pl" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : No such file or directory
(II) Configured Mouse: ps2EnableDataReporting: succeeded
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+pl" };
    xkb_geometry             { include "pc(pc105)" };
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled


```

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
	Option		"XkbLayout"	"pl"
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
	Identifier	"NVIDIA Corporation NVIDIA Default Card"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Philips 170S4"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NVIDIA Default Card"
	Monitor		"Philips 170S4"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024@60" "1024x768@60" "800x600@60" "640x480@60"
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

---

### Post by Rzulf on 2006-11-29
Ok I found a solution :) 
Simply remove usplash and everything is fine :) Moreover I don't have this windowslike splash any more :D

---

### Post by enochian on 2006-11-30
I just tried to respond to a thread but I had to register first - It is important to let the others that the BSOD black screen of death is NOT limited to ATI + AMD's my PC does the same BSOD with Intel Pentium 4 On ASUS P4P800 board
with ATI (Everything loads up until the Desktop Initiates then OUT of Range Message displays..   I don't know where exactly to post this since I am new to this discussion board...  Maybe you can repost this where it will help ?
Thanks....

---

