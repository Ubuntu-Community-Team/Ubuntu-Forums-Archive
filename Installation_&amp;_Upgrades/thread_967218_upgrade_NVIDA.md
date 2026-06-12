---
title: "upgrade NVIDA"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by goslings on 2008-11-01
Was looking forward to 8.1 all went well,,,then 
Upgrading may reduce desktop effects, and performance in games and other graphically intensive programs.

This computer is currently using the NVIDIA 'nvidia' graphics driver. No version of this driver is available that works with your video card in Ubuntu 8.10.

Anyone have any idea is there a driver available ?
Graphics is , GeForce Ti4600
thanks
Ian

---

### Post by shae on 2008-11-01
No, there is no driver that supports that card and 3D acceleration.

---

### Post by goslings on 2008-11-02
> **shae said:**
> No, there is no driver that supports that card and 3D acceleration.
thanks
so does that mean this is a non starter
I dont use ubuntu for games ect, just mail, surfing and the odd bit of music - my background is unix so linux is obvious for me 
card is not that old 2003/4 - supported under xp (dual boot, as family like xp)

---

### Post by PmDematagoda on 2008-11-02
> **goslings said:**
> thanks
so does that mean this is a non starter
I dont use ubuntu for games ect, just mail, surfing and the odd bit of music - my background is unix so linux is obvious for me 
card is not that old 2003/4 - supported under xp (dual boot, as family like xp)

There is a probability that it would work under the vesa or nv driver, but there is no 3D acceleration under both drivers, but since you aren't using the PC for games or graphics-intensive tasks, they should be more than enough. But keep in mind, no 3D means no Compiz-Fusion as well.

Edit:- By the way, since the nv and vesa drivers are already there, the X-Server should not have too many problems with your card.

---

### Post by drhowarddrfine on 2008-11-02
I'm having the same problem but fusion and nvidia was working for me before I upgraded.  I don't understand why the upgrade says there are no drivers now.

---

### Post by PmDematagoda on 2008-11-02
> **drhowarddrfine said:**
> I'm having the same problem but fusion and nvidia was working for me before I upgraded.  I don't understand why the upgrade says there are no drivers now.

It is possible that the driver in 8.10 no longer supports your card, or it could be that the drivers are in a flux of sorts which is pretty common with proprietary drivers such as nvidia and fglrx.

What is your VGA card? And also post the output of:-
```
cat /var/log/Xorg.0.log
```

---

### Post by drhowarddrfine on 2008-11-02
This was the first thread I saw after doing a search but now I see there are driver issues with Ibex that I'll have to wait for updates to.  Thanks.

---

### Post by goslings on 2008-11-08
> **PmDematagoda said:**
> 
What is your VGA card? And also post the output of:-
```
cat /var/log/Xorg.0.log
```

sorry for delay i've been away - rather long o/p but here it is 
hardware reports NVIDIA accelerated grahics driver

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  8 12:54:25 2008
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
(II) PCI: 00:00:0: chip 1039,0651 card 1043,8079 rev 02 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0001 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0962 card 0000,0000 rev 04 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 104d,8133 rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:6: chip 1039,7013 card 104d,8129 rev a0 class 07,03,00 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 104d,8127 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 104d,8133 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 104d,8133 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 104d,8133 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 104d,8133 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:0e:0: chip 14e4,4320 card 144f,7077 rev 03 class 02,80,00 hdr 00
(II) PCI: 00:0f:0: chip 1131,7134 card 1043,4830 rev 01 class 04,80,00 hdr 00
(II) PCI: 00:10:0: chip 1180,0475 card 1000,0000 rev 80 class 06,07,00 hdr 02
(II) PCI: 00:12:0: chip 10ec,8139 card 104d,80ea rev 10 class 02,00,00 hdr 00
(II) PCI: 00:13:0: chip 1033,00f2 card 104d,811e rev 01 class 0c,00,10 hdr 00
(II) PCI: 01:00:0: chip 10de,0250 card 1043,a00e rev a3 class 03,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe7000000 - 0xe7ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xef700000 - 0xfebfffff (0xf500000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 2: bridge is at (0:16:0), (0,2,5), BCTRL: 0x0580 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x00001000 - 0x000010ff (0x100) IX[B]
	[1] -1	0	0x00001400 - 0x000014ff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0x54000000 - 0x57ffffff (0x4000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0x50000000 - 0x53ffffff (0x4000000) MX[B]
(--) PCI:*(1:0:0) nVidia Corporation NV25 [GeForce4 Ti 4600] rev 163, Mem @ 0xe7000000/24, 0xf0000000/27, 0xef800000/19, BIOS @ 0xef7e0000/17
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
(II) PCI Memory resource overlap reduced 0xe8000000 from 0xebffffff to 0xe7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe3000000 - 0xe3000fff (0x1000) MX[B]
	[1] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[2] -1	0	0xe4000000 - 0xe40003ff (0x400) MX[B]
	[3] -1	0	0xe4800000 - 0xe4801fff (0x2000) MX[B]
	[4] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[5] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[6] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[7] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[10] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe7000000 - 0xe7ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe3000000 - 0xe3000fff (0x1000) MX[B]
	[1] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[2] -1	0	0xe4000000 - 0xe40003ff (0x400) MX[B]
	[3] -1	0	0xe4800000 - 0xe4801fff (0x2000) MX[B]
	[4] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[5] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[6] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[7] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B]
	[8] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[9] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[10] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[11] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[12] -1	0	0xe7000000 - 0xe7ffffff (0x1000000) MX[B](B)
	[13] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[15] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[16] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[17] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[18] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[19] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
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
	[4] -1	0	0xe3000000 - 0xe3000fff (0x1000) MX[B]
	[5] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[6] -1	0	0xe4000000 - 0xe40003ff (0x400) MX[B]
	[7] -1	0	0xe4800000 - 0xe4801fff (0x2000) MX[B]
	[8] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[9] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[10] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[11] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B]
	[12] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[13] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[14] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xe7000000 - 0xe7ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[25] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  96.43.05  Tue Jan 22 20:11:30 PST 2008
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
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
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
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
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  96.43.05  Tue Jan 22 19:38:46 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.2.0
	ABI class: X.Org Video Driver, version 2.0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3000000 - 0xe3000fff (0x1000) MX[B]
	[5] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[6] -1	0	0xe4000000 - 0xe40003ff (0x400) MX[B]
	[7] -1	0	0xe4800000 - 0xe4801fff (0x2000) MX[B]
	[8] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[9] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[10] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[11] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B]
	[12] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[13] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[14] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xe7000000 - 0xe7ffffff (0x1000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[20] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[21] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[22] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[23] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[24] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[25] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe3000000 - 0xe3000fff (0x1000) MX[B]
	[5] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[6] -1	0	0xe4000000 - 0xe40003ff (0x400) MX[B]
	[7] -1	0	0xe4800000 - 0xe4801fff (0x2000) MX[B]
	[8] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[9] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[10] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[11] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B]
	[12] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[13] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[14] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[15] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[16] -1	0	0xe7000000 - 0xe7ffffff (0x1000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[23] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[24] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[25] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[26] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[27] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[28] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(**) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce4 Ti 4600 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.25.00.37.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 Ti 4600 at PCI:1:0:0:
(--) NVIDIA(0):     Silicon Graphics GDM-5411 (CRT-1)
(--) NVIDIA(0): Silicon Graphics GDM-5411 (CRT-1): 350.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(II) NVIDIA(0): Assigned Display Device: CRT-1
(WW) NVIDIA(0): No valid modes for "2048x1536@75"; removing.
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1600x1200@70"
(II) NVIDIA(0):     "1600x1200@85"
(II) NVIDIA(0):     "1600x1200@75"
(II) NVIDIA(0):     "1792x1344@75"
(II) NVIDIA(0):     "1600x1200@60"
(II) NVIDIA(0):     "1792x1344@60"
(II) NVIDIA(0):     "1600x1200@65"
(II) NVIDIA(0):     "1856x1392@60"
(II) NVIDIA(0):     "1400x1050@75"
(II) NVIDIA(0):     "1856x1392@75"
(II) NVIDIA(0):     "1400x1050@60"
(II) NVIDIA(0):     "1920x1440@60"
(II) NVIDIA(0):     "1280x960@75"
(II) NVIDIA(0):     "1920x1440@75"
(II) NVIDIA(0):     "1280x1024@60"
(II) NVIDIA(0):     "2048x1536@60"
(II) NVIDIA(0):     "1280x1024@85"
(II) NVIDIA(0):     "1280x960@85"
(II) NVIDIA(0):     "1280x960@60"
(II) NVIDIA(0):     "1280x1024@75"
(II) NVIDIA(0):     "1152x864@75"
(II) NVIDIA(0):     "1024x768@43"
(II) NVIDIA(0):     "1024x768@60"
(II) NVIDIA(0):     "1024x768@70"
(II) NVIDIA(0):     "1024x768@75"
(II) NVIDIA(0):     "1024x768@85"
(II) NVIDIA(0):     "832x624@75"
(II) NVIDIA(0):     "800x600@60"
(II) NVIDIA(0):     "800x600@85"
(II) NVIDIA(0):     "800x600@75"
(II) NVIDIA(0):     "800x600@72"
(II) NVIDIA(0):     "800x600@56"
(II) NVIDIA(0):     "640x480@85"
(II) NVIDIA(0):     "640x480@75"
(II) NVIDIA(0):     "640x480@72"
(II) NVIDIA(0):     "640x480@60"
(II) NVIDIA(0): Virtual screen size determined to be 2048 x 1536
(--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xef800000 - 0xef87ffff (0x80000) MX[B]
	[1] 0	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B]
	[2] 0	0	0xe7000000 - 0xe7ffffff (0x1000000) MX[B]
	[3] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[4] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[5] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[6] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[7] -1	0	0xe3000000 - 0xe3000fff (0x1000) MX[B]
	[8] -1	0	0xe3800000 - 0xe38000ff (0x100) MX[B]
	[9] -1	0	0xe4000000 - 0xe40003ff (0x400) MX[B]
	[10] -1	0	0xe4800000 - 0xe4801fff (0x2000) MX[B]
	[11] -1	0	0xe5000000 - 0xe5000fff (0x1000) MX[B]
	[12] -1	0	0xe5800000 - 0xe5800fff (0x1000) MX[B]
	[13] -1	0	0xe6000000 - 0xe6000fff (0x1000) MX[B]
	[14] -1	0	0xe6800000 - 0xe6800fff (0x1000) MX[B]
	[15] -1	0	0xe8000000 - 0xe7ffffff (0x0) MX[B]O
	[16] -1	0	0xef7e0000 - 0xef7fffff (0x20000) MX[B](B)
	[17] -1	0	0xef800000 - 0xef87ffff (0x80000) MX[B](B)
	[18] -1	0	0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
	[19] -1	0	0xe7000000 - 0xe7ffffff (0x1000000) MX[B](B)
	[20] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[21] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[22] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[23] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[24] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[25] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[26] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B]
	[27] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[28] -1	0	0x0000a800 - 0x0000a87f (0x80) IX[B]
	[29] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[30] -1	0	0x0000b400 - 0x0000b40f (0x10) IX[B]
	[31] -1	0	0x0000e600 - 0x0000e61f (0x20) IX[B]
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Initialized GART.
(II) NVIDIA(0): Setting mode "1600x1200@70"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
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
(II) Initializing extension GLX
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(**) Option "Buttons" "5"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Option "ButtonMapping" "1 2 3 6 7"
(**) Configured Mouse: Buttons: 11
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
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "1792x1344@60"
(II) NVIDIA(0): v4l: memPhysBase=0xf0000000
SetClientVersion: 0 9
ian@goslinux:~$

---

### Post by PmDematagoda on 2008-11-08
Well, according to your log file, the driver in use is the Nvidia driver itself. So I guess it's just a mistake on the part of Jockey, anyway, I think you can safely ignore it for now.

---

### Post by goslings on 2008-11-08
> **PmDematagoda said:**
> Well, according to your log file, the driver in use is the Nvidia driver itself. So I guess it's just a mistake on the part of Jockey, anyway, I think you can safely ignore it for now.

that was the log file that I got from ubuntu 8.04 
So is it safe to go to 8.10, cause it was on that upgrade that I got the initial nvidia unsupported message.
thanks

---

### Post by Adam Moreno on 2008-11-08
I just ran into the same problem while attempting to upgrade from Ubuntu Studio 8.04 to 8.10. Oh well, I'm perfectly happy with 8.04, and I need 3D support, so I guess I'll just hold off on upgrading until updated drivers are available. I wish I'd come here before downloading and burning the 8.10 ISO!

---

### Post by goslings on 2008-11-08
[QUOTE=PmDematagoda;
What is your VGA card? 
```
cat /var/log/Xorg.0.log
```[/QUOTE]

NV25 [GeForce4 Ti 4600]

upgrading to 8.1 - would it be any different graphically to 8.04 if I use whatever it is that I have installed now ?
(I also read that open-office 3 never made ir into 8.10, is this true?
(are all wireless (broadcom B43 issues sorted in 8.10, casue it was a real real real pain in 8.04)

---

### Post by Chunky Dunk on 2008-11-08
They have released a beta driver for the GeForce4, that is supposed to work with the x server in 8.10... [http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)

---

### Post by goslings on 2008-11-08
> **Chunky Dunk said:**
> They have released a beta driver for the GeForce4, that is supposed to work with the x server in 8.10... [http://www.nvnews.net/vbulletin/showthread.php?t=122139](http://www.nvnews.net/vbulletin/showthread.php?t=122139)
so not being totally au fait with this sort of thing, what do i do with it 

I assume I need to do more that just ley >system >admin >upgrade manager and  let it do an 8.1 upgrade  

any "fool proof" steps described anywhere to install the driver and the sequence wrt upgrade manager?
thanks

---

### Post by Chunky Dunk on 2008-11-08
Since you'd be downloading directly from nvidia and not ubuntu, you have to install it the hard way... This site has directions on how to do it: [http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/](http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/)

Hopefully this can all be resolved soon, and we can go back to the easy way it was handled in 8.04. Good luck! :)

---

### Post by goslings on 2008-11-11
[QUOTE=Chunky Dunk;6134411]This site has directions on how to do it: [http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/](http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/)
QUOTE]

Seems it may be possible ... comments on my though IAN at bottom
[http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/]("http://kmandla.wordpress.com/2008/11/04/compiling-nvidia-driver-964309-on-intrepid-2627-7/"), can't say that I fully comprehend the instructiions. Maybe Ubuntu can offer some further instruction, as it does seem possible, so why not included ???
What worries me about this is trying and completely messing up my orking version of 8.04. These issues seem to be "black art" side of Ubuntu.
thanks

---

### Post by PmDematagoda on 2008-11-11
goslings, I can help you out with the instructions, exactly what don't you understand?

And about the drivers, yes, Nvidia proprietary drivers aren't all that reliable, but the Ubuntu devs can't be held responsible for this since they do not have the driver source in order to make it easier to install, so you would need to ask Nvidia themselves.

---

### Post by goslings on 2008-11-12
[QUOTE=PmDematagoda;6151269]goslings, I can help you out with the instructions, exactly what don't you understand?
QUOTE]
Hi It is really a step by step set of instructions I am after,
8.04 works well with my sony desktop (GeForce 4200)
If I upgrade to 8.1 via upgrade manager it reports nvidia not supported?
couple of pages back offered some suggestions, also read 3D accelerated graphics not support under 8.10 for this card type.
Can't try as away alll week
regards

---

### Post by PmDematagoda on 2008-11-12
Lol goslings, isn't the guide a step-by-step thing itself? I know it doesn't seem to be very clear that it is step-by-step, but it is, and if you need my help, then I can't help you any more than the guide can, except if you face some errors.

But I would advise you to download the driver first before killing the X-Server.

And you may want to do this before the upgrade itself, first open the xorg.conf file for editing with:-
```
gksudo gedit /etc/X11/xorg.conf
```
go to the section which looks something like this:-
```
Section "Device"
	Identifier  "Videocard0"
	Driver      "intel"
EndSection
```
and change the entry in front of Driver to "vesa" and save it, you should then be good to go.

---

### Post by Chunky Dunk on 2008-11-25
I don't know if you worked this out yet, goslings, but it seems as though this driver has finally made it to the repos. :)

---

### Post by goslings on 2008-11-29
> **Chunky Dunk said:**
> I don't know if you worked this out yet, goslings, but it seems as though this driver has finally made it to the repos. :)
really as part of the main upgrade ?
thanks
Ian

---

### Post by Chunky Dunk on 2008-11-29
Just make sure "Recommended Updates" is checked on the "Updates" tab of "System" >> "Administration" >> "Software Sources", make sure your sources are up to date (which it should do on its own), then go to "System" >> Administration" >> "Hardware Drivers", and it should find the correct driver.

---

### Post by goslings on 2008-11-29
> **Chunky Dunk said:**
> Just make sure "Recommended Updates" is checked on the "Updates" tab of "System" >> "Administration" >> "Software Sources", make sure your sources are up to date (which it should do on its own), then go to "System" >> Administration" >> "Hardware Drivers", and it should find the correct driver.

on the other side - all looks ok and yes have the drivers.
One bummer .
It look me ages to get my logitek mouse to work on the thumb back and forward side buttons these do not work again .
Is there a quick fix ?
thanks all

---

### Post by goslings on 2008-12-06
> **goslings said:**
> vers.
One bummer .
It look me ages to get my logitek mouse to work on the thumb back and forward side buttons these do not work again .
Is there a quick fix ?
thanks all
anyone any ideas - or do I have to go digging in the config again!
thanks

---

### Post by goslings on 2008-12-06
> **goslings said:**
> anyone any ideas - or do I have to go digging in the config again!
thanks
found another side effect mpegs of web site do not now play.
Mplayer fires up and the clips constantly have error and do not play
Is this nvidia related ?

---

