---
title: "[SOLVED] NVIDIA drivers do not load on start up"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Kossilar on 2008-02-08
Hello. 

I'm runing Fluxbuntu 7.10 and I've having a really difficult time with my NVIDIA drivers. They work fine, except they refuse to load on start up. Every time I reboot the system I need to reinstall the drivers in order to get to the system. 

Its extremely strange.

I've tried asking on IRC, but to no avail.

Does anybody know what's causing this?

---

### Post by taurus on 2008-02-08
Which model of nvidia graphic card do you have and how did you install nvidia driver for your system?

---

### Post by Whiffle on 2008-02-08
Sounds like the nvidia kernel module isn't being loaded.  Next time you boot up, log in however you can, and run 'lsmod' before you do anything else.  Read through the list and see if 'nvidia' is listed.  If its not, do 

sudo modprobe nvidia

and then

sudo /etc/init.d/gdm restart

If that works, then we know where to start.

---

### Post by Kossilar on 2008-02-08
> Which model of nvidia graphic card do you have and how did you install nvidia driver for your system?

I'm running an NVIDIA 6800 GS. Sorry I should have mentioned that right away.

I installed the drivers by downloading the NVIDIA proprietary drivers from the NVIDIA website and installing them with the 'sh' command from the console.

> Sounds like the nvidia kernel module isn't being loaded. Next time you boot up, log in however you can, and run 'lsmod' before you do anything else. Read through the list and see if 'nvidia' is listed. If its not, do

sudo modprobe nvidia

and then

sudo /etc/init.d/gdm restart

If that works, then we know where to start.

I checked to see whether NVIDIA showed up under modprobe and it does show up. 

I imagine the next thing you'll ask for is my /var/log/xorg.0.log. So I'll post it now along with my xorg.conf file.

Log file first:

```
X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux moriah 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  8 20:36:59 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(**) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81e9800
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
(II) PCI: 00:00:0: chip 8086,2774 card 1043,8178 rev 81 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2775 card 0000,0000 rev 81 class 06,04,00 hdr 01
(II) PCI: 00:1b:0: chip 8086,27d8 card 1043,8193 rev 01 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,27e0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,27e2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1043,8179 rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1043,8179 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1043,8179 rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,27b8 card 1043,8179 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1043,8179 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1043,2601 rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1043,8179 rev 01 class 0c,05,00 hdr 00
(II) PCI: 01:02:0: chip 10ec,8029 card 10ec,8029 rev 00 class 02,00,00 hdr 00
(II) PCI: 01:03:0: chip 104c,8023 card 1043,808b rev 00 class 0c,00,10 hdr 00
(II) PCI: 01:04:0: chip 1283,8211 card 1043,8138 rev 11 class 01,80,00 hdr 00
(II) PCI: 01:05:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 1095,3132 card 1043,819f rev 01 class 01,80,00 hdr 00
(II) PCI: 03:00:0: chip 8086,108b card 1043,8197 rev 03 class 02,00,00 hdr 00
(II) PCI: 05:00:0: chip 10de,00c0 card 10de,0339 rev a2 class 03,00,00 hdr 00
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
(II) Bus 5: bridge is at (0:1:0), (0,5,5), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000e000 - 0x0000efff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xddf00000 - 0xdfffffff (0x2100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:0), (0,4,4), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 4 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[1] -1	0	0x0000c400 - 0x0000c4ff (0x100) IX[B]
	[2] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[3] -1	0	0x0000cc00 - 0x0000ccff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xdde00000 - 0xddefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:5), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[1] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[2] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[3] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xddd00000 - 0xdddfffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00008000 - 0x000080ff (0x100) IX[B]
	[1] -1	0	0x00008400 - 0x000084ff (0x100) IX[B]
	[2] -1	0	0x00008800 - 0x000088ff (0x100) IX[B]
	[3] -1	0	0x00008c00 - 0x00008cff (0x100) IX[B]
	[4] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[5] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[6] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[7] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
	[8] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[9] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[10] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[11] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xddc00000 - 0xddcfffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x88000000 - 0x880fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(5:0:0) nVidia Corporation NV41 [GeForce 6800 GS] rev 162, Mem @ 0xdf000000/24, 0xe0000000/28, 0xde000000/24, BIOS @ 0xddfe0000/17
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
	[0] -1	0	0xddee0000 - 0xddefffff (0x20000) MX[B]
	[1] -1	0	0xdddf8000 - 0xdddfbfff (0x4000) MX[B]
	[2] -1	0	0xdddffc00 - 0xdddffc7f (0x80) MX[B]
	[3] -1	0	0xddcfc000 - 0xddcfffff (0x4000) MX[B]
	[4] -1	0	0xddcf4000 - 0xddcf7fff (0x4000) MX[B]
	[5] -1	0	0xddcfb800 - 0xddcfbfff (0x800) MX[B]
	[6] -1	0	0xddbffc00 - 0xddbfffff (0x400) MX[B]
	[7] -1	0	0xddbff800 - 0xddbffbff (0x400) MX[B]
	[8] -1	0	0xddbf8000 - 0xddbfbfff (0x4000) MX[B]
	[9] -1	0	0xddfe0000 - 0xddffffff (0x20000) MX[B](B)
	[10] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[15] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[16] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[17] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[18] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[21] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[22] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[23] -1	0	0x00006400 - 0x0000640f (0x10) IX[B]
	[24] -1	0	0x00006800 - 0x00006803 (0x4) IX[B]
	[25] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[26] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[27] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[34] -1	0	0x00005800 - 0x0000581f (0x20) IX[B]
	[35] -1	0	0x00005400 - 0x0000541f (0x20) IX[B]
	[36] -1	0	0x00005000 - 0x0000501f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xddee0000 - 0xddefffff (0x20000) MX[B]
	[1] -1	0	0xdddf8000 - 0xdddfbfff (0x4000) MX[B]
	[2] -1	0	0xdddffc00 - 0xdddffc7f (0x80) MX[B]
	[3] -1	0	0xddcfc000 - 0xddcfffff (0x4000) MX[B]
	[4] -1	0	0xddcf4000 - 0xddcf7fff (0x4000) MX[B]
	[5] -1	0	0xddcfb800 - 0xddcfbfff (0x800) MX[B]
	[6] -1	0	0xddbffc00 - 0xddbfffff (0x400) MX[B]
	[7] -1	0	0xddbff800 - 0xddbffbff (0x400) MX[B]
	[8] -1	0	0xddbf8000 - 0xddbfbfff (0x4000) MX[B]
	[9] -1	0	0xddfe0000 - 0xddffffff (0x20000) MX[B](B)
	[10] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[11] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[12] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[14] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[15] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[16] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[17] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[18] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[19] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[20] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[21] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[22] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[23] -1	0	0x00006400 - 0x0000640f (0x10) IX[B]
	[24] -1	0	0x00006800 - 0x00006803 (0x4) IX[B]
	[25] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[26] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[27] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[28] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[32] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[33] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[34] -1	0	0x00005800 - 0x0000581f (0x20) IX[B]
	[35] -1	0	0x00005400 - 0x0000541f (0x20) IX[B]
	[36] -1	0	0x00005000 - 0x0000501f (0x20) IX[B]
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
	[4] -1	0	0xddee0000 - 0xddefffff (0x20000) MX[B]
	[5] -1	0	0xdddf8000 - 0xdddfbfff (0x4000) MX[B]
	[6] -1	0	0xdddffc00 - 0xdddffc7f (0x80) MX[B]
	[7] -1	0	0xddcfc000 - 0xddcfffff (0x4000) MX[B]
	[8] -1	0	0xddcf4000 - 0xddcf7fff (0x4000) MX[B]
	[9] -1	0	0xddcfb800 - 0xddcfbfff (0x800) MX[B]
	[10] -1	0	0xddbffc00 - 0xddbfffff (0x400) MX[B]
	[11] -1	0	0xddbff800 - 0xddbffbff (0x400) MX[B]
	[12] -1	0	0xddbf8000 - 0xddbfbfff (0x4000) MX[B]
	[13] -1	0	0xddfe0000 - 0xddffffff (0x20000) MX[B](B)
	[14] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[22] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[23] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[24] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[26] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[27] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[28] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[29] -1	0	0x00006400 - 0x0000640f (0x10) IX[B]
	[30] -1	0	0x00006800 - 0x00006803 (0x4) IX[B]
	[31] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[32] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[33] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[34] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[40] -1	0	0x00005800 - 0x0000581f (0x20) IX[B]
	[41] -1	0	0x00005400 - 0x0000541f (0x20) IX[B]
	[42] -1	0	0x00005000 - 0x0000501f (0x20) IX[B]
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
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
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.09  Fri Jan 11 15:31:25 PST 2008
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
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
(II) NVIDIA dlloader X Driver  169.09  Fri Jan 11 14:41:00 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="NVIDIA Corporation"
	compiled for 7.1.99.2, module version = 1.0.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xddee0000 - 0xddefffff (0x20000) MX[B]
	[5] -1	0	0xdddf8000 - 0xdddfbfff (0x4000) MX[B]
	[6] -1	0	0xdddffc00 - 0xdddffc7f (0x80) MX[B]
	[7] -1	0	0xddcfc000 - 0xddcfffff (0x4000) MX[B]
	[8] -1	0	0xddcf4000 - 0xddcf7fff (0x4000) MX[B]
	[9] -1	0	0xddcfb800 - 0xddcfbfff (0x800) MX[B]
	[10] -1	0	0xddbffc00 - 0xddbfffff (0x400) MX[B]
	[11] -1	0	0xddbff800 - 0xddbffbff (0x400) MX[B]
	[12] -1	0	0xddbf8000 - 0xddbfbfff (0x4000) MX[B]
	[13] -1	0	0xddfe0000 - 0xddffffff (0x20000) MX[B](B)
	[14] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[20] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[21] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[22] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[23] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[24] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[26] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[27] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[28] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[29] -1	0	0x00006400 - 0x0000640f (0x10) IX[B]
	[30] -1	0	0x00006800 - 0x00006803 (0x4) IX[B]
	[31] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[32] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[33] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[34] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[35] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[36] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[37] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[39] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[40] -1	0	0x00005800 - 0x0000581f (0x20) IX[B]
	[41] -1	0	0x00005400 - 0x0000541f (0x20) IX[B]
	[42] -1	0	0x00005000 - 0x0000501f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xddee0000 - 0xddefffff (0x20000) MX[B]
	[5] -1	0	0xdddf8000 - 0xdddfbfff (0x4000) MX[B]
	[6] -1	0	0xdddffc00 - 0xdddffc7f (0x80) MX[B]
	[7] -1	0	0xddcfc000 - 0xddcfffff (0x4000) MX[B]
	[8] -1	0	0xddcf4000 - 0xddcf7fff (0x4000) MX[B]
	[9] -1	0	0xddcfb800 - 0xddcfbfff (0x800) MX[B]
	[10] -1	0	0xddbffc00 - 0xddbfffff (0x400) MX[B]
	[11] -1	0	0xddbff800 - 0xddbffbff (0x400) MX[B]
	[12] -1	0	0xddbf8000 - 0xddbfbfff (0x4000) MX[B]
	[13] -1	0	0xddfe0000 - 0xddffffff (0x20000) MX[B](B)
	[14] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[24] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[25] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[26] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[27] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[29] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[30] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[31] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[32] -1	0	0x00006400 - 0x0000640f (0x10) IX[B]
	[33] -1	0	0x00006800 - 0x00006803 (0x4) IX[B]
	[34] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[35] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[36] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[37] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[42] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[43] -1	0	0x00005800 - 0x0000581f (0x20) IX[B]
	[44] -1	0	0x00005400 - 0x0000541f (0x20) IX[B]
	[45] -1	0	0x00005000 - 0x0000501f (0x20) IX[B]
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 6800 GS (NV41) at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.41.02.49.02
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 6800 GS at PCI:5:0:0:
(--) NVIDIA(0):     ViewSonic (CRT-1)
(--) NVIDIA(0): ViewSonic (CRT-1): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(++) NVIDIA(0): DPI set to (85, 85); computed from -dpi X commandline option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xddee0000 - 0xddefffff (0x20000) MX[B]
	[5] -1	0	0xdddf8000 - 0xdddfbfff (0x4000) MX[B]
	[6] -1	0	0xdddffc00 - 0xdddffc7f (0x80) MX[B]
	[7] -1	0	0xddcfc000 - 0xddcfffff (0x4000) MX[B]
	[8] -1	0	0xddcf4000 - 0xddcf7fff (0x4000) MX[B]
	[9] -1	0	0xddcfb800 - 0xddcfbfff (0x800) MX[B]
	[10] -1	0	0xddbffc00 - 0xddbfffff (0x400) MX[B]
	[11] -1	0	0xddbff800 - 0xddbffbff (0x400) MX[B]
	[12] -1	0	0xddbf8000 - 0xddbfbfff (0x4000) MX[B]
	[13] -1	0	0xddfe0000 - 0xddffffff (0x20000) MX[B](B)
	[14] -1	0	0xde000000 - 0xdeffffff (0x1000000) MX[B](B)
	[15] -1	0	0xe0000000 - 0xefffffff (0x10000000) MX[B](B)
	[16] -1	0	0xdf000000 - 0xdfffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b87f (0x80) IX[B]
	[24] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[25] -1	0	0x00009000 - 0x0000900f (0x10) IX[B]
	[26] -1	0	0x00009400 - 0x00009403 (0x4) IX[B]
	[27] -1	0	0x00009800 - 0x00009807 (0x8) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a003 (0x4) IX[B]
	[29] -1	0	0x0000a400 - 0x0000a407 (0x8) IX[B]
	[30] -1	0	0x00008800 - 0x0000881f (0x20) IX[B]
	[31] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[32] -1	0	0x00006400 - 0x0000640f (0x10) IX[B]
	[33] -1	0	0x00006800 - 0x00006803 (0x4) IX[B]
	[34] -1	0	0x00007000 - 0x00007007 (0x8) IX[B]
	[35] -1	0	0x00007400 - 0x00007403 (0x4) IX[B]
	[36] -1	0	0x00007800 - 0x00007807 (0x8) IX[B]
	[37] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[38] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[39] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[40] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[41] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[42] -1	0	0x00006000 - 0x0000601f (0x20) IX[B]
	[43] -1	0	0x00005800 - 0x0000581f (0x20) IX[B]
	[44] -1	0	0x00005400 - 0x0000541f (0x20) IX[B]
	[45] -1	0	0x00005000 - 0x0000501f (0x20) IX[B]
	[46] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[47] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized GPU GART.
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
(II) Initializing extension GLX
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
(**) Option "Protocol" "auto"
(**) Mouse0: Device: "/dev/psaux"
(**) Mouse0: Protocol: "auto"
(**) Option "CorePointer"
(**) Mouse0: Core Pointer
(**) Option "Device" "/dev/psaux"
(**) Option "Emulate3Buttons" "no"
(**) Option "ZAxisMapping" "4 5"
(**) Mouse0: ZAxisMapping: buttons 4 and 5
(**) Mouse0: Buttons: 9
(**) Mouse0: Sensitivity: 1
(II) XINPUT: Adding extended input device "Mouse0" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
(--) Mouse0: PnP-detected protocol: "ExplorerPS/2"
(II) Mouse0: ps2EnableDataReporting: succeeded
 
```

And finally xorg.conf

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Jan 11 15:05:59 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection 
```

Also my old log file, since it was there and seems to contain more info even though its much shorter. There's a reference to 'options' not being a valid section name. I think that's because I recently tried adding a line somebody mentioned in one of the threads but did it wrong. That bit no longer exists since I last reinstalled the NVIDIA driver so I don't think that was the problem. However the other part may be useful.

Fortunately this one is shorter :P

```

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux moriah 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  8 20:35:53 2008
(==) Using config file: "/etc/X11/xorg.conf"
Parse error on line 89 of section Options in file /etc/X11/xorg.conf
	"Options" is not a valid section name.
(EE) Problem parsing the config file
(EE) Error parsing the config file

Fatal server error:
no screens found
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor

```

Thanks for all your help guys.

---

### Post by PmDematagoda on 2008-02-08
I believe the problem could be due to conflicting modules, try doing the following:-

1) Open the restricted modules file for editing:-
```
sudo nano /etc/default/linux-restricted-modules-common
```

2) Change the DISABLED_MODULES line to make it look like this:-
```
DISABLED_MODULES="nv nvidia_new"
```

3) Save the file and reinstall the driver again.

---

### Post by Kossilar on 2008-02-09
Thanks a lot!

That solved it in a hurry and I didn't even have to reinstall the driver.  :)

Thanks also to everybody who had a look at this thread and took the time to reply.

---

### Post by ljoslin on 2008-02-29
worked for me as well!  Thanks everyone!

-=ljoslin=-

---

### Post by Mr. Brightside on 2008-03-08
Sorry for digging up such an old thread but I have a similar problem with my 8800GT.

Re-installing the drivers every time I boot is a bit of a pain, aye. 

I tried editing the restricted modules via the terminal but I didn't know how to save the changes. 

Any help would be highly appreciated.

---

### Post by Kossilar on 2008-03-08
You need to be a super-user to edit that file. Try running gedit, or whatever software you're using to edit the file with sudo first in a terminal window like this.

```
sudo gedit /etc/default/linux-restricted-modules-common
```

Otherwise you won't be able to save the file.

---

### Post by Mr. Brightside on 2008-03-08
I'll try doing that mate but before I proceed, do you have any idea how I can restart xconfig?

Every time I boot, before re-installing the driver, when I go under the nVidia Control Panel(or whatever we call it on Ubuntu); it tells me to run 'nvidia-config' as root user and restart sconfig.

I did run:
```
sudo -i
```

```
nvidia-xconfig
```

but I don't know how to restart xconfig. Do you have any idea how to? I'd rather try that first.

P.S: I know I should have said that earlier.

---

### Post by kangol69 on 2008-03-11
```
sudo /etc/init.d/gdm restart
```
That should restart x for you which is what I think you're wanting to do. Rebooting your computer will also do the trick if you don't want to use the terminal.

---

