---
title: "Problem with Nvidia Drivers after upgrade to Hardy 8.04"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by ifedeli on 2008-04-28
I have been trying for days to figure out how to get the drivers for my Nvidia 7900GT to work correctly with Ubuntu 8.04 Hardy. With 7.10, I was able to use Envy to install the drivers without issue. However, upon upgrading to Hardy, I am unable to get working drivers. When I try to use the Nvidia driver (as opposed to the nv driver), X.org is unable to start correctly (it tries 4 times), and instead uses the failsafe VESA option. I am able to boot at the right resolution when I use the nv driver in xorg.conf, but this is obviously suboptimal... I would like to run compiz. 

I have tried:

- Using the Hardware Drivers and package manager

- Using EnvyNG to install the drivers

- Using the beta drivers from Nvidia's website

- Trying various different things with xorg.conf and /etc/modules

- Trying sudo depmod -a -q

I have searched the forums as best I could and found no answer. I am at a loss. :confused:

I'm no expert, but I'm reasonably competent with linux. I would appreciate any solutions, help, or advice anyone could provide.

Thanks,
--ifedeli

---

### Post by Pumalite on 2008-04-28
Give details and post exact error messages.

---

### Post by ifedeli on 2008-04-28
> **Pumalite said:**
> Give details and post exact error messages.

There is no error message displayed when the relevant problem occurs, except the standard message saying there is a problem with the video drivers, low resolution 800x600 must be used.

I am not sure what to attach. Below is the contents of Xorg.0.log, as well as the most recent iteration of xorg.conf which I am currently using. It is unchanged from that which is produced by EnvyNG.

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
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux trask 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64
Build Date: 15 April 2008  05:41:18PM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr 28 11:54:14 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
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
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
	Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
	Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7bd660
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
(II) PCI: 00:00:0: chip 8086,29a0 card 1043,81ea rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,29a1 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1a:0: chip 8086,2834 card 1043,81ec rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1a:1: chip 8086,2835 card 1043,81ec rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1a:7: chip 8086,283a card 1043,81ec rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1b:0: chip 8086,284b card 1043,81ec rev 02 class 04,03,00 hdr 00
(II) PCI: 00:1c:0: chip 8086,283f card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:4: chip 8086,2847 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1c:5: chip 8086,2849 card 0000,0000 rev 02 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,2830 card 1043,81ec rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,2831 card 1043,81ec rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,2832 card 1043,81ec rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,2836 card 1043,81ec rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev f2 class 06,04,01 hdr 01
(II) PCI: 00:1f:0: chip 8086,2810 card 1043,81ec rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:2: chip 8086,2822 card 1043,81ec rev 02 class 01,04,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,283e card 1043,81ec rev 02 class 0c,05,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0291 card 3842,c584 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:00:0: chip 11ab,4364 card 1043,81f8 rev 12 class 02,00,00 hdr 00
(II) PCI: 03:00:0: chip 197b,2363 card 1043,81e4 rev 02 class 01,06,01 hdr 80
(II) PCI: 03:00:1: chip 197b,2363 card 1043,81e4 rev 02 class 01,01,85 hdr 00
(II) PCI: 05:03:0: chip 104c,8023 card 1043,815b rev 00 class 0c,00,10 hdr 00
(II) PCI: 05:04:0: chip 11ab,4320 card 1043,811a rev 13 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfa700000 - 0xfe7fffff (0x4100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xbfe00000 - 0xdfdfffff (0x20000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:28:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0xdfe00000 - 0xdfefffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:4), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfe900000 - 0xfe9fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:5), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfe800000 - 0xfe8fffff (0x100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 5: bridge is at (0:30:0), (0,5,5), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 5 I/O range:
	[0] -1	0	0x0000c000 - 0x0000cfff (0x1000) IX[B]
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation G71 [GeForce 7900 GT/GTO] rev 161, Mem @ 0xfd000000/24, 0xc0000000/28, 0xfc000000/24, I/O @ 0x9c00/7, BIOS @ 0xfe7e0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
	[0] -1	0	0xfeaf4000 - 0xfeaf7fff (0x4000) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[3] -1	0	0xfe9fe000 - 0xfe9fffff (0x2000) MX[B]
	[4] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[5] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[6] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[7] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[8] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[9] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[15] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[17] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[27] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[29] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[31] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0x88000000 - 0x880000ff (0x100) MX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeaf4000 - 0xfeaf7fff (0x4000) MX[B]
	[1] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[2] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[3] -1	0	0xfe9fe000 - 0xfe9fffff (0x2000) MX[B]
	[4] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[5] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[6] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[7] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[8] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[9] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[14] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[15] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[16] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[17] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[18] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[19] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[20] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[21] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[22] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[23] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[24] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[27] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[28] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[29] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[30] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[31] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x88000000 - 0x880000ff (0x100) MX[B]
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
	[4] -1	0	0xfeaf4000 - 0xfeaf7fff (0x4000) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[7] -1	0	0xfe9fe000 - 0xfe9fffff (0x2000) MX[B]
	[8] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[9] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[10] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[11] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[12] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[13] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x88000000 - 0x880000ff (0x100) MX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[22] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[24] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[25] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[27] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[29] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[31] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[34] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[36] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
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
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:34:02 PST 2008
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
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaf4000 - 0xfeaf7fff (0x4000) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[7] -1	0	0xfe9fe000 - 0xfe9fffff (0x2000) MX[B]
	[8] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[9] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[10] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[11] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[12] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[13] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x88000000 - 0x880000ff (0x100) MX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[21] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[22] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[23] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[24] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[25] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[26] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[27] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[28] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[29] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[30] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[31] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[32] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[34] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[35] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[36] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[37] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[38] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeaf4000 - 0xfeaf7fff (0x4000) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[7] -1	0	0xfe9fe000 - 0xfe9fffff (0x2000) MX[B]
	[8] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[9] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[10] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[11] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[12] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[13] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x88000000 - 0x880000ff (0x100) MX[B]
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[25] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[27] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[29] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[30] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[32] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[34] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[37] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[38] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[39] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[40] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[41] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
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
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.113
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G71 Board - p455h0f 
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
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
(II) VESA(0): Manufacturer: BNQ  Model: 76d5  Serial#: 6404
(II) VESA(0): Year: 2006  Week: 11
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max H-Image Size [cm]: horiz.: 38  vert.: 30
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.610
(II) VESA(0): blueX: 0.140 blueY: 0.070   whiteX: 0.310 whiteY: 0.330
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@67Hz
(II) VESA(0): 640x480@72Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@72Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 832x624@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@70Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): 1152x870@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #1: hsize: 1280  vsize 1024  refresh: 76  vid: 36993
(II) VESA(0): #2: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 108.0 MHz   Image Size:  376 x 301 mm
(II) VESA(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0
(II) VESA(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 25.2 MHz   Image Size:  376 x 301 mm
(II) VESA(0): h_active: 640  h_sync: 656  h_sync_end 752 h_blank_end 800 h_border: 0
(II) VESA(0): v_active: 350  v_sync: 387  v_sync_end 389 v_blanking: 449 v_border: 0
(II) VESA(0): Ranges: V min: 56  V max: 76 Hz, H min: 31  H max: 83 kHz, PixClock max 140 MHz
(II) VESA(0): Monitor name: BenQ FP93GX
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0009d1d57604190000
(II) VESA(0): 	0b10010380261e78eac5c6a3574a9c23
(II) VESA(0): 	124f54bdef80714f81908180818c0101
(II) VESA(0): 	010101010101302a009851002a403070
(II) VESA(0): 	1300782d1100001ed50980a0205e6310
(II) VESA(0): 	10605208782d1100001a000000fd0038
(II) VESA(0): 	4c1f530e000a202020202020000000fc
(II) VESA(0): 	0042656e51204650393347580a200054
(II) VESA(0): EDID vendor "BNQ", prod id 30421
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) VESA(0): Modeline "640x350"x0.0   25.17  640 656 752 800  350 387 389 449 +hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz)
(II) VESA(0): Modeline "1280x1024"x76.0  140.75  1280 1368 1504 1728  1024 1027 1034 1072 -hsync +vsync (81.5 kHz)
(II) VESA(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
(II) VESA(0): Modeline "1280x1024"x71.9  133.00  1280 1368 1504 1728  1024 1027 1034 1070 -hsync +vsync (77.0 kHz)
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 100 (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 640
	XResolution: 640
	YResolution: 400
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
	LinBytesPerScanLine: 640
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
	MaxPixelClock: 229500000
Mode: 101 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
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
	NumberOfImages: 10
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
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 102 (800x600)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 100
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
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
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 100
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
	MaxPixelClock: 108500000
Mode: 103 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 800
	XResolution: 800
	YResolution: 600
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
	LinBytesPerScanLine: 800
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
	MaxPixelClock: 229500000
Mode: 104 (1024x768)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 128
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
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
	PhysBasePtr: 0x0
	LinBytesPerScanLine: 128
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
	MaxPixelClock: 108500000
Mode: 105 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
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
	NumberOfImages: 3
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
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 106 (1280x1024)
	ModeAttributes: 0x31f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 160
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 4
	BitsPerPixel: 4
	NumberOfBanks: 1
	MemoryModel: 3
	BankSize: 0
	NumberOfImages: 3
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
	LinBytesPerScanLine: 160
	BnkNumberOfImagePages: 3
	LinNumberOfImagePages: 3
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 108500000
Mode: 107 (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 1280
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 1
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
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 10e (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 30
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
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 10f (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
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
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 111 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
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
	LinBytesPerScanLine: 1280
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
	MaxPixelClock: 229500000
Mode: 112 (640x480)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
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
	LinBytesPerScanLine: 2560
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
	MaxPixelClock: 229500000
*Mode: 114 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
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
	LinBytesPerScanLine: 1600
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
	MaxPixelClock: 229500000
Mode: 115 (800x600)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
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
	LinBytesPerScanLine: 3200
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
	MaxPixelClock: 229500000
*Mode: 117 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
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
	NumberOfImages: 1
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
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 118 (1024x768)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
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
	MaxPixelClock: 229500000
*Mode: 11a (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1

	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
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
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 11b (1280x1024)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
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
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
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
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
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
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 132 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
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
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 133 (320x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
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
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
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
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 135 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
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
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 136 (320x240)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
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
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
*Mode: 13d (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
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
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 13e (640x400)
	ModeAttributes: 0x39f
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc00094c1
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
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
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
(II) VESA(0): Configured Monitor: Using hsync range of 31.00-83.00 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-76.00 Hz
(II) VESA(0): Configured Monitor: Using maximum pixel clock of 140.00 MHz
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(**) VESA(0): Display dimensions: (380, 300) mm
(**) VESA(0): DPI set to (53, 50)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 73Hz refresh for mode "640x480" (111)
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
	[4] -1	0	0xfeaf4000 - 0xfeaf7fff (0x4000) MX[B]
	[5] -1	0	0xfeaf8000 - 0xfeafbfff (0x4000) MX[B]
	[6] -1	0	0xfeaff800 - 0xfeafffff (0x800) MX[B]
	[7] -1	0	0xfe9fe000 - 0xfe9fffff (0x2000) MX[B]
	[8] -1	0	0xfe8fc000 - 0xfe8fffff (0x4000) MX[B]
	[9] -1	0	0xfebff800 - 0xfebfffff (0x800) MX[B]
	[10] -1	0	0xfebff000 - 0xfebff3ff (0x400) MX[B]
	[11] -1	0	0xfebf8000 - 0xfebfbfff (0x4000) MX[B]
	[12] -1	0	0xfebff400 - 0xfebff7ff (0x400) MX[B]
	[13] -1	0	0xfe7e0000 - 0xfe7fffff (0x20000) MX[B](B)
	[14] -1	0	0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
	[15] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[16] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[17] -1	0	0x88000000 - 0x880000ff (0x100) MX[B]
	[18] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[19] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[20] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c8ff (0x100) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[25] -1	0	0x0000b480 - 0x0000b483 (0x4) IX[B]
	[26] -1	0	0x0000b800 - 0x0000b807 (0x8) IX[B]
	[27] -1	0	0x0000b880 - 0x0000b883 (0x4) IX[B]
	[28] -1	0	0x0000bc00 - 0x0000bc07 (0x8) IX[B]
	[29] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[30] -1	0	0x00000400 - 0x0000041f (0x20) IX[B]
	[31] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[32] -1	0	0x0000e480 - 0x0000e483 (0x4) IX[B]
	[33] -1	0	0x0000e800 - 0x0000e807 (0x8) IX[B]
	[34] -1	0	0x0000e880 - 0x0000e883 (0x4) IX[B]
	[35] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[36] -1	0	0x0000dc00 - 0x0000dc1f (0x20) IX[B]
	[37] -1	0	0x0000d880 - 0x0000d89f (0x20) IX[B]
	[38] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[39] -1	0	0x0000e080 - 0x0000e09f (0x20) IX[B]
	[40] -1	0	0x0000e000 - 0x0000e01f (0x20) IX[B]
	[41] -1	0	0x00009c00 - 0x00009c7f (0x80) IX[B](B)
	[42] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[43] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.113
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G71 Board - p455h0f 
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Write-combining range (0xc0000000,0x10000000)
(II) VESA(0): virtual address = 0x7f88d0bd2000,
	physical address = 0xc0000000, size = 268435456
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
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
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
```


```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Wed Apr  2 08:22:13 PST 2008
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Depth	24
		Modes		"1280x1024@60"	"1280x960@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Screen"
	#        
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Option		"AddARGBGLXVisuals"	"True"
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Screen	0
EndSection

Section "Device"
	#        
	Identifier	"device1"
	Driver		"nvidia"
	Boardname	"vesa"
	Busid		"PCI:1:0:0"
	Screen	1
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
	Option		"Emulate3Buttons"	"true"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	Inputdevice	"Configured Mouse"	"CorePointer"
EndSection

Section "Module"
	Load		"glx"
	Load		"v4l"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5	-	64.0
	Vertrefresh	56.0	-	65.0
	Gamma	1
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
	#        
	Identifier	"monitor1"
	Gamma	1
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by Pumalite on 2008-04-28
What happened when you tried the driver from the Nvidia site? How did you try to install it?

---

### Post by ifedeli on 2008-04-28
> What happened when you tried the driver from the Nvidia site? How did you try to install it? 

I ran

```
sudo sh NVIDIA-Linux-x86_64-173.08-pkg2.run
```

Installation appeared to succeed. However, nothing changed when I rebooted. Same problem as before.

---

### Post by rolen on 2008-04-28
I am getting the same problem with my Nforce2 chipset. When i boot up comes up with the same message about running in low graphics mode. It also seems to trash any changes i make to Xorg.conf.  

Another problem i have which i am not sure if it is related or not is that i unable to boot the kernel version 2.6.24-16-generic rather i have to select the previous version of 2.6.22-14-generic.

I can't see anything in the dmesg, are there any suggestions as to other log files which may shed some light on this problem?

---

### Post by Pumalite on 2008-04-28
If another OS owns the Grub, check UUID's. Compare blkid, fstab and menu.lst. They have to coincide.

---

### Post by ifedeli on 2008-04-28
> If another OS owns the Grub, check UUID's. Compare blkid, fstab and menu.lst. They have to coincide. 

Here is the output of each. I am not sure what I am looking for. Thanks in advance for your reply, and sorry I can't be more helpful.

menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

title Windows XP
rootnoverify (hd0,0)
chainloader +1

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/mapper/isw_cechhbacha_Adam3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

blkid
```
/dev/mapper/isw_cechhbacha_Adam5: UUID="A6FC7280FC724A97" LABEL="Aron" TYPE="ntfs" 
/dev/mapper/isw_cechhbacha_Adam4: TYPE="swap" 
/dev/mapper/isw_cechhbacha_Adam3: LABEL="Samuel" UUID="9a9e5775-37e1-4962-be74-7c5384e1a4f9" TYPE="ext3" 
/dev/mapper/isw_cechhbacha_Adam1: UUID="4E2CEBF22CEBD2CF" LABEL="Caleb" TYPE="ntfs" 
/dev/mapper/isw_cechhbacha_Adam6: UUID="C448173948172A26" LABEL="Lee" TYPE="ntfs" 

```

fstab
```
proc /proc proc rw 0 0
/dev/mapper/isw_cechhbacha_Adam3 / ext3 defaults 0 1
/dev/mapper/isw_cechhbacha_Adam4 none swap sw
/dev/mapper/isw_cechhbacha_Adam1 /mnt/Caleb ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/mapper/isw_cechhbacha_Adam5 /mnt/Aron ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/mapper/isw_cechhbacha_Adam6 /mnt/Lee ntfs-3g defaults,locale=en_US.utf8 0 0 
```

---

### Post by billrad1 on 2008-04-28
I have the same issue, Geforce 5700le.

Every single time I upgrade, everything goes well, but I have to do this two day video drill to finally get the nvidia drivers working.

I have used Envyng, and nvidia driver root install routine, and same thing happens - defaults to failsafe.

Something doesn't match with the GCC compilers and the kernel, says the error on the nvidia install routine. 

calgon, take me away.....

---

### Post by Pumalite on 2008-04-28
> **ifedeli said:**
> Here is the output of each. I am not sure what I am looking for. Thanks in advance for your reply, and sorry I can't be more helpful.

menu.lst
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

title Windows XP
rootnoverify (hd0,0)
chainloader +1

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/mapper/isw_cechhbacha_Adam3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/mapper/isw_cechhbacha_Adam3 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```

blkid
```
/dev/mapper/isw_cechhbacha_Adam5: UUID="A6FC7280FC724A97" LABEL="Aron" TYPE="ntfs" 
/dev/mapper/isw_cechhbacha_Adam4: TYPE="swap" 
/dev/mapper/isw_cechhbacha_Adam3: LABEL="Samuel" UUID="9a9e5775-37e1-4962-be74-7c5384e1a4f9" TYPE="ext3" 
/dev/mapper/isw_cechhbacha_Adam1: UUID="4E2CEBF22CEBD2CF" LABEL="Caleb" TYPE="ntfs" 
/dev/mapper/isw_cechhbacha_Adam6: UUID="C448173948172A26" LABEL="Lee" TYPE="ntfs" 

```

fstab
```
proc /proc proc rw 0 0
/dev/mapper/isw_cechhbacha_Adam3 / ext3 defaults 0 1
/dev/mapper/isw_cechhbacha_Adam4 none swap sw
/dev/mapper/isw_cechhbacha_Adam1 /mnt/Caleb ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/mapper/isw_cechhbacha_Adam5 /mnt/Aron ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/mapper/isw_cechhbacha_Adam6 /mnt/Lee ntfs-3g defaults,locale=en_US.utf8 0 0 
```

You are not using UUID's. I'm not familiar with your arrangement.

---

### Post by ifedeli on 2008-04-28
> **Pumalite said:**
> You are not using UUID's. I'm not familiar with your arrangement.
I had to do things slightly differently because I'm using 'fakeraid'. What does grub have to do with the loading of video drivers? It is a question of kernel modules?

---

### Post by Pumalite on 2008-04-28
Grub has to know exactly where everything is and also know what to load and what to mount.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ifedeli on 2008-04-28
> **Pumalite said:**
> Grub has to know exactly where everything is and also know what to load and what to mount.
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
Perhaps I'm missing the point, but I still don't see why grub is relevant here. I am able to boot into Hardy, using the correct kernel (2.6.24-16-generic). The problem is that when X.org tries to start, it is unable to use the Nvidia driver for some reason I don't understand. Maybe you're suggesting that it can't find the Nvidia driver kernel module?

---

### Post by Pumalite on 2008-04-28
We got off track. Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=768749](http://ubuntuforums.org/showthread.php?t=768749)

---

### Post by ifedeli on 2008-04-28
> **Pumalite said:**
> We got off track. Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=768749](http://ubuntuforums.org/showthread.php?t=768749)
I don't mean to be a pain, but I've already tried that. Any other ideas?

---

### Post by Pumalite on 2008-04-28
Yes. Do a clean install. They have never failed me. In fact I have 4 Hardies in clean install with Nvidia cards and none have a problem.

---

### Post by brigadoon on 2008-04-28
I saw your thread. I had some similar issues with the upgrade as well. I posted my solutions at...

[http://ubuntuforums.org/showthread.php?p=4828515#post4828515](http://ubuntuforums.org/showthread.php?p=4828515#post4828515)

It may give you some ideas. Hope it helps. Good luck.

---

### Post by sowelie on 2008-04-28
I don't know exactly what's been suggested, but I had a similar problem.  The old kernel module stuck around for some reason (I think I had the non free drivers installed manually previously).  Try removing nvidia-kernel-common and nvidia-glx-new and re-installing.  If that doesn't work, download the latest driver from NVIDIA and install that manually.

---

### Post by jblackhall on 2008-04-28
Are you 100% sure that you're booted into the correct kernel?  I had the exact same problem after upgrading and I thought I was booting into the correct kernel.  If you're not sure how to do check, simply run "uname -a" (without quotes) in Terminal.  The Hardy kernel is 2.6.24-16 (as of now).  If you're showing something else, like 2.6.22-14, then you're not booted into the correct one.  See here for more: [http://ubuntuforums.org/showpost.php?p=4802647&postcount=14](http://ubuntuforums.org/showpost.php?p=4802647&postcount=14) .  Once in the correct kernel the restricted drivers should work like a charm (did for me anyways).

If you are in the correct kernel, then I apologize.  It could be the fact that it's a newer card. (I only have a 6600GT).

---

### Post by ifedeli on 2008-04-29
Thanks for all the responses:

> Are you 100% sure that you're booted into the correct kernel?

I am booted into 2.6.24-16-generic, which is correct I believe.

> I don't know exactly what's been suggested, but I had a similar problem. The old kernel module stuck around for some reason (I think I had the non free drivers installed manually previously). Try removing nvidia-kernel-common and nvidia-glx-new and re-installing. If that doesn't work, download the latest driver from NVIDIA and install that manually.

I also suspected it has something to do with kernel modules. I tried removing nvidia-kernel-common and nvidia-glx-new and then reinstalling. There was no effect. I then tried the 173.08 beta driver from the NVIDIA website, again to no effect. 

So I'm still in the same spot. Any other ideas?

I thought it was interesting that in Xorg.0.log, it shows the glx module being loaded:

```
<snip>
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  173.08  Wed Apr  2 08:19:55 PST 2008
(II) Loading extension GLX
<snip>
```

I also thought it was interesting that in dmesg, there are three warnings about nvidia and sysctl, and also three gdm segfaults:

```
<snip>
[  467.263817] gdm[5677]: segfault at 800690b68 rip 7fd2fc581d1f rsp 7fff07ddca50 error 6
[  590.785835] gdm[7398]: segfault at 800691918 rip 7fbed99f7d1f rsp 7fffe52532c0 error 6
[  624.897281] warning: process `nvidia-installe' used the deprecated sysctl system call with 1.23.
[  624.897289] warning: process `nvidia-installe' used the deprecated sysctl system call with 1.23.
[  624.956318] nvidia: module license 'NVIDIA' taints kernel.
[  625.209763] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  625.209770] PCI: Setting latency timer of device 0000:01:00.0 to 64
[  625.210384] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.08  Wed Apr  2 07:55:48 PST 2008
[  625.233009] warning: process `nvidia-installe' used the deprecated sysctl system call with 1.23.
[  770.327503] gdm[8901]: segfault at 800689f98 rip 7fc986fa1d1f rsp 7fff927fb8e0 error 6
<snip>
```

Hope this info is useful, and thanks again to all who have responded.

---

### Post by ifedeli on 2008-04-29
More info:

I printed out the current active kernel modules. Nvidia does not appear, nor does lrm. Perhaps this is the issue? Any ideas how to fix this?

Thanks!

```
Module                  Size  Used by
af_packet              27272  2 
binfmt_misc            14860  1 
rfcomm                 47392  2 
l2cap                  28800  13 rfcomm
bluetooth              67748  4 rfcomm,l2cap
ppdev                  11400  0 
parport_pc             41128  0 
lp                     14916  0 
parport                44300  3 ppdev,parport_pc,lp
ipv6                  311720  18 
acpi_cpufreq           10832  1 
cpufreq_userspace       6180  0 
cpufreq_stats           8416  0 
cpufreq_powersave       3200  0 
cpufreq_ondemand       11152  2 
freq_table              6464  3 acpi_cpufreq,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative    10632  0 
video                  23444  0 
output                  5632  1 video
sbs                    17808  0 
sbshc                   8960  1 sbs
dock                   12960  0 
container               6656  0 
battery                16776  0 
iptable_filter          4608  0 
ip_tables              24104  1 iptable_filter
x_tables               23560  1 ip_tables
aes_x86_64             26920  0 
dm_crypt               16776  0 
ac                      8328  0 
coretemp                9856  0 
w83627ehf              27272  0 
hwmon_vid               5120  1 w83627ehf
arc4                    3456  2 
ecb                     5248  2 
blkcipher               9476  1 ecb
rtl8187                37248  0 
mac80211              192532  1 rtl8187
cfg80211               17680  1 mac80211
joydev                 15488  0 
usblp                  17664  0 
eeprom_93cx6            3840  1 rtl8187
sky2                   53892  0 
snd_hda_intel         440408  3 
snd_hwdep              12552  1 snd_hda_intel
snd_pcm_oss            47648  0 
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm
snd_mixer_oss          20224  1 snd_pcm_oss
i2c_core               28544  0 
snd_seq_dummy           5764  0 
snd_seq_oss            38912  0 
snd_seq_midi           10688  0 
snd_rawmidi            29856  1 snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                46236  0 
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               9092  0 
button                 10912  0 
intel_agp              30624  0 
snd                    70856  17 snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iTCO_wdt               15312  0 
shpchp                 38172  0 
pci_hotplug            34608  1 shpchp
soundcore              10400  1 snd
iTCO_vendor_support     5764  1 iTCO_wdt
evdev                  14976  4 
pcspkr                  4992  0 
ext3                  149264  1 
jbd                    57000  1 ext3
mbcache                11392  1 ext3
dm_mirror              26368  0 
dm_mod                 71160  16 dm_crypt,dm_mirror
sr_mod                 20132  0 
cdrom                  41512  1 sr_mod
pata_jmicron            8448  0 
pata_acpi               9856  0 
sg                     41880  0 
sd_mod                 33280  2 
usbhid                 35168  0 
hid                    44992  1 usbhid
skge                   47888  0 
ohci1394               36532  0 
ieee1394              106968  1 ohci1394
ata_generic             9988  0 
ahci                   33028  2 
libata                176304  4 pata_jmicron,pata_acpi,ata_generic,ahci
scsi_mod              178488  4 sr_mod,sg,sd_mod,libata
ehci_hcd               41996  0 
uhci_hcd               29856  0 
usbcore               169904  6 rtl8187,usblp,usbhid,ehci_hcd,uhci_hcd
thermal                19744  0 
processor              41448  2 acpi_cpufreq,thermal
fan                     6792  0 
fbcon                  46336  0 
tileblit                4096  1 fbcon
font                   10112  1 fbcon
bitblit                 7424  1 fbcon
softcursor              3712  1 bitblit
fuse                   56112  9
```

---

### Post by ifedeli on 2008-04-29
I figured it out! :) The problem was the kernel module was not being inserted.
To fix it:

```
sudo /etc/init.d/gdm stop
sudo insmod /lib/modules/`uname -r`/volatile/nvidia_new.ko
sudo /etc/init.d/gdm start
```

Thanks to everyone for all your help!

--ifedeli

---

### Post by ghstridr on 2008-04-29
> **ifedeli said:**
> I figured it out! :) The problem was the kernel module was not being inserted.
To fix it:

```
sudo /etc/init.d/gdm stop
sudo insmod /lib/modules/`uname -r`/volatile/nvidia_new.ko
sudo /etc/init.d/gdm start
```

Thanks to everyone for all your help!

--ifedeli

Now the question is, does it still load when the machine is rebooted?  Manually inserting the kernel module worked for me, but how do I guarentee that it will load on next boot of the laptop?

---

### Post by emptybox on 2008-04-29
> **ifedeli said:**
> I figured it out! :) The problem was the kernel module was not being inserted.
To fix it:

```
sudo /etc/init.d/gdm stop
sudo insmod /lib/modules/`uname -r`/volatile/nvidia_new.ko
sudo /etc/init.d/gdm start
```

Thanks to everyone for all your help!

--ifedeli

I'm having a similar problem with an nvidia 7600GT.
It worked fine under Gutsy with the restricted driver, but neither this nor Envyng seem to work under Hardy. :(

I'm not sure if it's anything to do with kernels in my case?
How would I find out, and when should I apply your solution to test it out?
Should I apply the restricted driver then restart in Recovery mode to use your command?

Under Gutsy I used to use "sudo dpkg-reconfigure -phigh xserver-xorg" to get the correct driver for xorg.conf, but that command doesn't seem to have any effect in Hardy?

Another problem I have now is that although I'm able to get back to the correct resolution (1440x900) using the nv driver, my login screen is messed up. It is huge, and I can only see my user name in the bottom right corner. I can click on it and type my password to get to my desktop, but the other users can't get to theirs.
However, I presume if I can get nvidia-glx-new to work, then that would sort that out?

---

### Post by ifedeli on 2008-04-29
> Now the question is, does it still load when the machine is rebooted? Manually inserting the kernel module worked for me, but how do I guarentee that it will load on next boot of the laptop?

@ghstridr

Manually inserting th kernel module will only work for the current boot session. However, you can script it to insert every time before you start GNOME. This is *not* official or even probably the best way to do it, but it worked for me.

At the beginning of /etc/init.d/gdm, I inserted the middle line from before. I believe this will cause it to run every time GNOME is started or stopped, but there doesn't seem to be any detrimental effect from running it too many times.

```
#! /bin/sh
#
# Originally based on:
# Version:	@(#)skeleton  1.8  03-Mar-1998  miquels@cistron.nl
#
# Modified for gdm, Steve Haslam <steve@arise.dmeon.co.uk> 14mar99
# modified to remove --exec, as it does not work on upgrades. 18jan2000
# modified to use --name, to detect stale PID files 18mar2000
# sleep until gdm dies, then restart it 16jul2000
# get along with other display managers (Branden Robinson, Ryan Murray) 05sep2001

#INSERTED BY IFEDELI
insmod /lib/modules/`uname -r`/volatile/nvidia_new.ko

set -e

# To start gdm even if it is not the default display manager, change
# HEED_DEFAULT_DISPLAY_MANAGER to "false."
HEED_DEFAULT_DISPLAY_MANAGER=true
DEFAULT_DISPLAY_MANAGER_FILE=/etc/X11/default-display-manager
PATH=/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/gdm
PIDFILE=/var/run/gdm.pid
UPGRADEFILE=/var/run/gdm.upgrade

<snip>

```

> I'm having a similar problem with an nvidia 7600GT.
It worked fine under Gutsy with the restricted driver, but neither this nor Envyng seem to work under Hardy.

I'm not sure if it's anything to do with kernels in my case?
How would I find out, and when should I apply your solution to test it out?
Should I apply the restricted driver then restart in Recovery mode to use your command?


@emptybox

To find out if the kernel module is currently inserted, run this:

```
sudo lsmod | grep nvidia
```

If it returns something like this:

```
nvidia               8858052  34 
```

then the module is inserted and this is not your problem. If it returns nothing, this could be it.

Heres what I would do:
1. Remove any beta drivers (sh NVIDIA*.run --uninstall)
2. Undo anything from EnvyNG by uninstalling
3. Open up synaptic, search for nvidia, and remove completely nvidia-glx-new, nvidia-kernel-common and linux-restricted-modules for your kernel, if they are there.
4. run ```
 sudo find /lib/modules/`uname -r` -name "*nvidia*"
``` This will produce of list of kernel modules that are still there. I don't know why they are still there. If you want to be safe, move them to some folder for safe keeping. I just deleted them. 
5. Open up synaptic again and install nvidia-glx-new, nvidia-kernel-common and linux-restricted-modules. Close synaptic.
6. Switch to the terminal (CTRL-ALT-F1). Ensure your /etc/X11/xorg.conf has something like this:

```
Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "vesa"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection
``` The important part is the Driver "nvidia" part.

7. run ```
sudo /etc/init.d/gdm stop
sudo insmod /lib/modules/`uname -r`/volatile/nvidia_new.ko
sudo /etc/init.d/gdm start
```
8. Switch back to GNOME (CTRL-ALT-F7). Hopefully it works now!
9. To make the insert happen on every start up, follow the instructions above (or if you know a better way, do that and let me know!)

> Under Gutsy I used to use "sudo dpkg-reconfigure -phigh xserver-xorg" to get the correct driver for xorg.conf, but that command doesn't seem to have any effect in Hardy?

I think i read somewhere this doesn't work any more. I would try rebooting in recovery mode and running xfix. That seems to give a decent xorg.conf. 

> Another problem I have now is that although I'm able to get back to the correct resolution (1440x900) using the nv driver, my login screen is messed up. It is huge, and I can only see my user name in the bottom right corner. I can click on it and type my password to get to my desktop, but the other users can't get to theirs.
However, I presume if I can get nvidia-glx-new to work, then that would sort that out? 

I'm really not sure on this one. I would hope that problem sorts itself out when nvidia-glx-new is working.

Hope this helps. Let me know if I can give more info.

--ifedeli

---

### Post by astepintothedark on 2008-04-29
> **emptybox said:**
> I'm having a similar problem with an nvidia 7600GT.
It worked fine under Gutsy with the restricted driver, but neither this nor Envyng seem to work under Hardy. :(

I'm not sure if it's anything to do with kernels in my case?
How would I find out, and when should I apply your solution to test it out?
Should I apply the restricted driver then restart in Recovery mode to use your command?

Under Gutsy I used to use "sudo dpkg-reconfigure -phigh xserver-xorg" to get the correct driver for xorg.conf, but that command doesn't seem to have any effect in Hardy?

Another problem I have now is that although I'm able to get back to the correct resolution (1440x900) using the nv driver, my login screen is messed up. It is huge, and I can only see my user name in the bottom right corner. I can click on it and type my password to get to my desktop, but the other users can't get to theirs.
However, I presume if I can get nvidia-glx-new to work, then that would sort that out?

I'm had the same exact issue with my 7600GT, so I've been sticking to the 'nv' driver for now. But I can't use any other driver, such as the one envyng downloads, which may be why Warzone 2100 runs **horribly** slow and Urban Terror freezes my x.

As for the login screen, I believe it's related to your x.org configuration (or something like that, I'm still a linux noob). I found a solution [here]("http://linuxfud.wordpress.com/2006/08/13/gdm-login-screen-resolution-too-big-to-fit-screen-try-this/") for that.

I hope this gets figured out, because I really don't want to have to do a clean install -- but alas, if I have to I will.

---

### Post by emptybox on 2008-04-29
@ ifedeli
Unfortunately that doesn't seem to be my problem?
I went through all your steps, but I still couldn't get it to run at more than 800x600 using the nvidia-glx-new driver, and the desktop effects didn't work either. :(

I've reverted to the nv drivers, and will run with those for a few days, and if no other solution presents itself, then I'll try a fresh install of 8.04. And if that doesn't work then it's back to good stable Gutsy.

@ astepintothedark
The only good news is that my login screen has righted itself. :)


BTW Ctrl-Alt-F1 has never worked on this machine for some reason?
Or Ctrl-Alt-F anything for that matter?
I can only get to a shell terminal by booting into Recovery mode, unless someone knows another way?

In Hardy when you go into Recovery mode, instead of ending at the command prompt, a box come up with 3 options.
1. continue to boot normally
2. drop down to a command prompt (or wtte)
3. xfix

Using xfix seems to restore the default Hardy xorg.conf which doesn't have any mention of video drivers in it.
It still only allowed me 1024x768 though. To get back to my native 1440x900 res I had to enable then disable the nvidia-glx-new.

Will look on the forum for more solutions Tomorrow.

---

### Post by ifedeli on 2008-04-30
@emptybox
Sorry I couldn't be more help. Good luck!

---

### Post by astepintothedark on 2008-04-30
So I think I might have found a [solution]("https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/217856").

What happened to me since I last posted is that I did a fresh install of Ubuntu, but I tried playing urban terror and I had the same issues as before. So I got the envyng pkg and tried installing the nvidia drivers, but to no avail. A bug error was reported, so I went to the link mentioned above and some wrote that I need to type in this code:
```
sudo apt-get install linux-headers-server linux-headers-$(uname -r)
``` I typed in the code, then ran envyng again, installed the drivers, restarted and bam! Fixed.

It worked for me, hopefully it can work for you guys.

---

### Post by ghstridr on 2008-04-30
> **ifedeli said:**
> @ghstridr

Manually inserting th kernel module will only work for the current boot session. However, you can script it to insert every time before you start GNOME. This is *not* official or even probably the best way to do it, but it worked for me.

At the beginning of /etc/init.d/gdm, I inserted the middle line from before. I believe this will cause it to run every time GNOME is started or stopped, but there doesn't seem to be any detrimental effect from running it too many times.



I tried that and it was still failing to vesa safe mode.
I did fix that though, found that 'nvidia' was being black listed in /etc/modprobe.d/blacklist-restricted. Commenting out the 'nvidia' statement allowed me finally to use the Nvidia driver.
I found this out by looking in /var/log/daemon.log

```
# This file is used to disable restricted drivers
#blacklist nvidia
blacklist nvidia.bad
blacklist nvidia_legacy.bad
blacklist nvidia_new
blacklist nvidia_new.bad

```
Now I'm just trying to figure out why the Gnome Settings Daemon is issuing a warnign on login to the desktop:
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

```
The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.
```

---

### Post by stianalm on 2008-04-30
A warm thank you to you guys, astepintothedark and ghstridr. Thanks to you I am no longer looking at Hardy in 800x600 resolution.

Good karma is coming your way!

---

### Post by biriachan on 2008-04-30
Ubuntu Hardy 8.04 AMD64 Alternate Install CD

Well I've been having problems with my Nvidia 7800 GT with a fresh ubuntu 8.04 Install.

My biggest problem was none of the packages provided with the installation worked. I always had the same problem the second after I logged into the desktop the system freezes, and I had to hard boot!

The follow drivers have not worked for me: nv, nvidia-glx-new, nvidia-glx-dev, nvidia-glx.

So here is how I got my system fixed.

Starting with a clean install.

Got to logon screen pressed "Ctrl+Alt+F1" to drop into a new console session. - logged into console
Stopped Gnome ```
sudo /etc/init.d/gdm stop
```
Removed the Restricted drivers ```
sudo apt-get remove --purge linux-restricted-modules
```
Removed nv drivers [HTML]sudo apt-get remove --purge xserver-xorg-video-nv[/HTML]
Removed Nvidia drivers from loading [HTML]sudo nano /etc/default/linux-restricted-modules-common[/HTML]

The last line should read DISABLED_MODULES=""
I then modified the last line to DISABLED_MODULES="nv nvidia_new"

Not sure if its needed but I deleted xorg.conf 
[HTML]sudo rm /etc/X11/xorg.conf[/HTML]

Then restarted 
[HTML]sudo shutdown -r 0[/HTML]

After all this I was able to login to my Desktop without the computer freezing up

downloaded nvidia drivers for linux - 64bit 
[http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run]("http://us.download.nvidia.com/XFree86/Linux-x86_64/169.12/NVIDIA-Linux-x86_64-169.12-pkg2.run")

-- link for 32bit drivers
[http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run")

After downloading the drivers onto my Desktop pressed "Ctrl+Alt+F1" to enter a console.
Logged in

installed build essential packages needed for the Nvidia driver install
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Changed directory to the location of the Downloaded Nvidia Drivers (Desktop for me)
```
cd ~/Desktop
```

Next I enabled the nvidia driver file for execution
```
sudo chmod +x NVIDIA-Linux-x86_64-169.12-pkg2.run
```

Then I executed the Nvidia Driver file
```
sudo ./NVIDIA-Linux-x86_64-169.12-pkg2.run
```
if using the 32bit package run
```
sudo chmod +x NVIDIA-Linux-x86-169.12.pkg1.run
```
```
sudo ./NVIDIA-Linux-x86-169.12.pkg1.run
```

During the Nvidia Driver Install I selected Yes to every option.

Restarted and now everything is happy.


I'm a pretty big noob, but I did run through this process twice today in order to better understand it, and each time it worked on my system.  This is the only process that I found to work for me so far after working on it and searching google and these forums for 3 days now.

---

### Post by emptybox on 2008-04-30
I gave up and did a clean install, and the offered restricted nvidia driver worked first time, so whatever my problem was it was caused by the upgrade rather than Hardy itself.
I'm running compiz smoothly now at 1440x900. :cool:

I do have other problems, error messages at shutdown, but I see other threads on that so I won't bother about it here. :D

---

