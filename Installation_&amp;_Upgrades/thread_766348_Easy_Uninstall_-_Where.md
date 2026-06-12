---
title: "Easy Uninstall - Where ?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by drsox1899 on 2008-04-25
I installed 8.04 on my old laptop - much too slow and screen only quarter size.  8.04 is supposed to have an easy uninstall option - where is it ?

I'll go back to the Gibbon.

):P

---

### Post by tormod on 2008-04-25
> **drsox1899 said:**
> I installed 8.04 on my old laptop - much too slow and screen only quarter size.  8.04 is supposed to have an easy uninstall option - where is it ?

The quarter screen size is probably easy to fix, try filing a bug or ask somewhere giving relevant detailed information on your issue.

If you give some details about what is slower and how much (benchmark numbers in seconds will surely give your issue more attention than vague subjective statements) there might be ways to improve this as well.

I am also curious about that Uninstall option they advertise on [www.ubuntu.com](www.ubuntu.com) :)

---

### Post by drsox1899 on 2008-04-25
Quote from PmDematagoda

Quote "  ...  

Please do not start duplicate threads in an attempt to solve your problem, one thread on one issue in the proper section will suffice.

This thread is a duplicate of this thread, this thread is closed.

... " Unquote

How about a helpful answer ?

---

### Post by drsox1899 on 2008-04-25
> **tormod said:**
> The quarter screen size is probably easy to fix, try filing a bug or ask somewhere giving relevant detailed information on your issue.

If you give some details about what is slower and how much (benchmark numbers in seconds will surely give your issue more attention than vague subjective statements) there might be ways to improve this as well.

I am also curious about that Uninstall option they advertise on [www.ubuntu.com](www.ubuntu.com) :)

It's an old Toshiba from 1998 but I'm trying to keep it alive without running the WinXp it came with.  It can run Xandros 4.1 OK but I'll try re-installing U 7.0x or K 7.0x as they may be more suitable.

---

### Post by tormod on 2008-04-25
> **drsox1899 said:**
> It's an old Toshiba from 1998 but I'm trying to keep it alive without running the WinXp it came with.  It can run Xandros 4.1 OK but I'll try re-installing U 7.0x or K 7.0x as they may be more suitable.

Xubuntu will probably be the best choice. I don't think 8.04 should be much more heavy than earlier versions, just make sure for instance trackerd is not running. For the screen size issue, we would like to see your /var/log/Xorg.0.log . You probably have something wrong in /etc/X11/xorg.conf - try without one for a start.

---

### Post by drsox1899 on 2008-04-25
Thanks.  I'll try the XU 8.04 first.

The U forum tells me that I have 11 images in this post - so I'll break the log file into two bits and post twice :



Here's the first part of the log


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
Current Operating System: Linux Bagpuss 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 25 14:43:51 2008
(==) Using config file: "/etc/X11/xorg.conf"
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
(II) PCI: 00:00:0: chip 10b9,1644 card 0000,0000 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 10b9,5247 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 10b9,5237 card 1179,0004 rev 03 class 0c,03,10 hdr 00
(II) PCI: 00:04:0: chip 10b9,5229 card 1179,0004 rev c3 class 01,01,f0 hdr 00
(II) PCI: 00:06:0: chip 10b9,5451 card 1179,0001 rev 01 class 04,01,00 hdr 00
(II) PCI: 00:07:0: chip 10b9,1533 card 1179,0004 rev 00 class 06,01,00 hdr 00
(II) PCI: 00:08:0: chip 10b9,7101 card 1179,0001 rev 00 class 06,80,00 hdr 00
(II) PCI: 00:11:0: chip 1179,0617 card 1400,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 00:11:1: chip 1179,0617 card 1c00,0000 rev 32 class 06,07,00 hdr 82
(II) PCI: 01:00:0: chip 1023,8820 card 1179,0001 rev 82 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,6), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xf7f00000 - 0xfdffffff (0x6100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x300fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:17:0), (0,2,5), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
	[1] -1	0	0x00001800 - 0x000018ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x24000000 - 0x27ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x20000000 - 0x23ffffff (0x4000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 6: bridge is at (0:17:1), (0,6,9), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 6 I/O range:
	[0] -1	0	0x00001c00 - 0x00001cff (0x100) IX[B]
	[1] -1	0	0x00002000 - 0x000020ff (0x100) IX[B]
(II) Bus 6 non-prefetchable memory range:
	[0] -1	0	0x2c000000 - 0x2fffffff (0x4000000) MX[B]
(II) Bus 6 prefetchable memory range:
	[0] -1	0	0x28000000 - 0x2bffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) Trident Microsystems CyberBlade XPAi1 rev 130, Mem @ 0xfc000000/25, 0xfbc00000/22, 0xf8000000/25, 0xf7ff8000/15
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
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf3ffffff to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0x30100000 - 0x30100fff (0x1000) MX[B]
	[1] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[2] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[3] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[4] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[5] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[7] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[8] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0x30100000 - 0x30100fff (0x1000) MX[B]
	[1] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[2] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[3] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[4] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[5] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[6] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[7] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[8] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x300fffff (0x30000000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x300fffff (0x30000000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x30100000 - 0x30100fff (0x1000) MX[B]
	[5] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[8] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[9] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[14] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
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
(II) Matched trident from file name trident.ids in autoconfig
(==) Matched trident for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "trident"
(II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
(II) Module trident: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.4
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
(II) TRIDENT: driver for Trident chipsets: tvga9000, tvga9000i, tvga8900c,
	tvga8900d, tvga9200cxr, tgui9400cxi, cyber9320, cyber9388, cyber9397,
	cyber9397dvd, cyber9520, cyber9525dvd, cyberblade/e4, tgui9420dgi,
	tgui9440agi, tgui9660, tgui9680, providia9682, providia9685,
	cyber9382, cyber9385, 3dimage975, 3dimage985, blade3d, cyberbladei7,
	cyberbladei7d, cyberbladei1, cyberbladei1d, cyberbladeAi1,
	cyberbladeAi1d, bladeXP, cyberbladeXPAi1, cyberbladeXP4, XP5
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset cyberbladeXPAi1 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x300fffff (0x30000000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]


	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x30100000 - 0x30100fff (0x1000) MX[B]
	[5] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[8] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[9] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[11] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[12] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[13] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[14] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x300fffff (0x30000000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x30100000 - 0x30100fff (0x1000) MX[B]
	[5] -1	0	0xf7eff000 - 0xf7efffff (0x1000) MX[B]
	[6] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[7] -1	0	0xf7ff8000 - 0xf7ffffff (0x8000) MX[B](B)
	[8] -1	0	0xf8000000 - 0xf9ffffff (0x2000000) MX[B](B)
	[9] -1	0	0xfbc00000 - 0xfbffffff (0x400000) MX[B](B)
	[10] -1	0	0xfc000000 - 0xfdffffff (0x2000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[17] -1	0	0x0000eff0 - 0x0000efff (0x10) IX[B]
	[18] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[19] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]

---

### Post by drsox1899 on 2008-04-25
Here's Part 2

(II) Setting vga for screen 0.
(II) TRIDENT(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) TRIDENT(0): Depth 24, (==) framebuffer bpp 32
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 0.1.0
	ABI class: X.Org Video Driver, version 2.0
(II) TRIDENT(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(==) TRIDENT(0): RGB weight 888
(==) TRIDENT(0): Default visual is TrueColor
(==) TRIDENT(0): Using gamma correction (1.0, 1.0, 1.0)
(==) TRIDENT(0): Using XAA for acceleration
(==) TRIDENT(0): Linear framebuffer at 0xFC000000
(--) TRIDENT(0): IO registers at 0xFBC00000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.1.0
	ABI class: X.Org Video Driver, version 2.0

Seems to need more than 2 posts :

More to come

---

### Post by drsox1899 on 2008-04-25
I still can't post the whole file as there seem to some damn images or equivalent that it won't let me post - so I'm not going to post the rest !

How do do I do without the /etc/X11/xorg.conf ?  Just rename it 

If I can't solve it I'll try XU 7

Thanks

---

### Post by tormod on 2008-04-25
Please use attachments. Sometimes it helps (the brainless forum software) to rename the files .txt (like we're using DOS :) )

Even better, use the bug tracker and attach the files there. The screen issue is a bug (at least an upgrade configuration bug) and should be reported.

---

### Post by tormod on 2008-04-25
> **drsox1899 said:**
> How do do I do without the /etc/X11/xorg.conf ?  Just rename it 

Yes, that should work.

---

### Post by tormod on 2008-04-25
See also [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/200411](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-trident/+bug/200411)

---

### Post by drsox1899 on 2008-04-25
> **tormod said:**
> Please use attachments. Sometimes it helps (the brainless forum software) to rename the files .txt (like we're using DOS :) )

Even better, use the bug tracker and attach the files there. The screen issue is a bug (at least an upgrade configuration bug) and should be reported.

OK, I'll try again as an attachment !  Gets to be a real pain using an old sloooowww machine again.

Then I'll look at the other links you sent.

Thanks

---

### Post by drsox1899 on 2008-04-25
OK.  Here's the log file (hopefully)

---

### Post by drsox1899 on 2008-04-25
What a palaver.  I had to split this as an attachment also !

---

### Post by drsox1899 on 2008-04-25
I've run Xubuntu 7.10 as a live CD - it's much faster than the others I've tried, even as a live CD !  I'll stick with it and upgrade to XU 8.04 when the screen issue has gone.  No luck yet with the other actions.  Next to do.

As I name all my "boxes" after cats past and present, it seems fitting to have a mouse OS running on a cat laptop !

---

### Post by tormod on 2008-04-25
> **drsox1899 said:**
> I'll stick with it and upgrade to XU 8.04 when the screen issue has gone.
I guess you just need to copy the working xorg.conf from that bug report and you'll be fine.

---

### Post by drsox1899 on 2008-04-25
> **tormod said:**
> I guess you just need to copy the working xorg.conf from that bug report and you'll be fine.

Thanks.

First I'm going to convert the U 8.04 into a XU 8.04.  Is it possible to process sideways or do I have to uninstall the U 8.04 ?

---

### Post by tormod on 2008-04-25
You can install the xubuntu-desktop package which will drag in all the Xubuntu stuff. Now you'll have both Ubuntu and Xubuntu, and there will probably be some Ubuntu cruft that you can live without. I have not tested this, but you can try to then remove the ubuntu-desktop package and then do a "sudo apt-get autoremove" to remove those packages that came as dependencies of ubuntu-desktop.

---

### Post by drsox1899 on 2008-04-26
> **tormod said:**
> You can install the xubuntu-desktop package which will drag in all the Xubuntu stuff. Now you'll have both Ubuntu and Xubuntu, and there will probably be some Ubuntu cruft that you can live without. I have not tested this, but you can try to then remove the ubuntu-desktop package and then do a "sudo apt-get autoremove" to remove those packages that came as dependencies of ubuntu-desktop.

Thanks.  I tried it OK.

Xubuntu is a disappointment to me with the lack of native support for networking, but otherwise real fast on my old laptop.

I've tried the two approaches listed in the forums for fixing it - neither are good enough, so I'm going to have a go at an even smaller Ubuntu - Fluxbuntu.

---

### Post by tormod on 2008-04-26
"lack of native support for networking" ? You mean there is no GUI for network configuration in Xubuntu?

---

### Post by drsox1899 on 2008-04-27
> **tormod said:**
> "lack of native support for networking" ? You mean there is no GUI for network configuration in Xubuntu?

Yep.  My problem is that I need to access a Unix based RAID NAS where all my files are located (allows me to have very very quiet PCs in my study).
  Trying the two approaches to Xubuntu network configuration have both resulted in my being unable to open the RAID NAS shares.  There must be some issue that I can't identify.

I've had a go at Flexbuntu and UbuntuLite.  Both unsuitable.  Yes, they are light - to the point of being invisible !  Both are trying to run on platforms that are much older/more limited than my old laptop.

I'm going to have to make Xubuntu work or go back to using regular flavour Ubuntu.  I suppose I could always try to install Nautilus in Xubuntu.

Today I am going to reinstall Xubuntu and have another go at it.  I had so many versions of U on my test machine that I kept booting up the wrong one  - so I wiped the lot and will start again.  I even had a look at Icebuntu.

I'm going to have to dual boot the laptop with WinXp anyway as my HP Scanjet 4850 is unrecognised in all flavours of Linux - but use it only for that.

If you can help with the Xubuntu networking problems then I'll post some results of my efforts.  The two forum threads for the two networking approaches are :

A. [http://ubuntuforums.org/showthread.php?t=500734](http://ubuntuforums.org/showthread.php?t=500734). This uses PyNeighborhood

B. [http://ubuntuforums.org/showthread.php?t=304131](http://ubuntuforums.org/showthread.php?t=304131). This uses fusesmb.

They both came from this posting :

[http://ubuntuforums.org/showthread.php?t=745825&highlight=Xubuntu+networking](http://ubuntuforums.org/showthread.php?t=745825&highlight=Xubuntu+networking)

I haven't tried doing the normal Ubuntu setup for Samba that I always need to do for a Ubuntu install.  Maybe I'll try that too.

Of course I could also be misunderstanding the difference between a Networking Setup and a GUI for Networking Setup, and just not doing the right sequence of stuff.  Accessing this RAID NAS works all the time in regular Ubuntu through Samba.

Thanks

---

### Post by tormod on 2008-04-27
So Xubuntu lacks out-of-the-box support for browsing SMB (Windows) shares? That's something else than "lack of native support for networking" I would say.

These forum posts you refer to are really old. Did you check the Xubuntu wiki or an Xubuntu forum?

---

### Post by drsox1899 on 2008-04-27
> **tormod said:**
> So Xubuntu lacks out-of-the-box support for browsing SMB (Windows) shares? That's something else than "lack of native support for networking" I would say.

These forum posts you refer to are really old. Did you check the Xubuntu wiki or an Xubuntu forum?

No info in the Wiki or Forum.

I've got Xubuntu installed and have set up Samba as I used to with Ubuntu 7.10, but no progress yet in connecting to the RAID NAS.

---

### Post by tormod on 2008-04-27
I just understood there is no Xubuntu forum any longer, it's all merged and they use Xubuntu "prefix" tags instead.

You're not alone:
[http://ubuntuforums.org/showthread.php?t=767187](http://ubuntuforums.org/showthread.php?t=767187)

edit: oops I mixed up Xubuntu and Kubuntu there :)

---

### Post by drsox1899 on 2008-04-27
Well, I followed the steps in the B link and I can see all the shares.  

All the unprotected shares I can work with as normal, but those with Passwords are blocked.  There is usually a login procedure for these (name, workgroup, password) in U 7.10etc, but zippo here.  

What else can I try ?

---

### Post by tormod on 2008-04-27
Did you read [http://ubuntuforums.org/showpost.php?p=2240743&postcount=41](http://ubuntuforums.org/showpost.php?p=2240743&postcount=41) from your B thread?

---

### Post by drsox1899 on 2008-04-27
No, I forgot that.  I'll give that a try.

I'm also installing U7.10 on the laptop to see how slow it really is.  If it's not too slow and I can't get the preferred approach to work, then I'll go with U7.10 until I see an update to Xu that allows Easy Networking in Thunar.

Thanks

---

