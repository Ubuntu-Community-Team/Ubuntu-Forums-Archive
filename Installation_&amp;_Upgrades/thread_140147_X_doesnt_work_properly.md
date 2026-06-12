---
title: "X doesnt work properly"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by fish47 on 2006-03-05
hello, i'm a real linux noob, and im trying to install 5.10.
it installs nicely with no problems at all, but when it boots and enters X, I hear sound but can only see vertical lines with some coloured squares around. I have:

ASUS A8N SLI Deluxe
Geforce 6600GT PCI-Express
AMD 64 3500+ Newcastle

I tried with an old S3 1Meg card PCI and got some results, but dont want to spend my life in 1024*768*8...

Weird thing is, i booted an old Ubuntu 4 liveCD and it works, even though most of the hardware isnt detected properly (device manager shows a lot of nVidia devices with no drivers, chipset is nforce4)

any ideas? thnks

---

### Post by rjwood on 2006-03-05
from the command line
```
sudo dpkg-reconfigure xserver-xorg
```

Let x read your hardware and make sure your video card has the correct driver. If nvidia driver causes problems do it again and make your driver "nv" instead of nvidia. if that does not work. Let us know----good luck;)

---

### Post by DirkBreeuwer on 2006-03-05
I have almost the same problem, I've read the forums and I found some info, yet I still have the same problem. When I boot into ubuntu 5.10, everything runs smooth except that I get a apic error when I press Ctrl + Alt + F1 (while at the splash screen ,when ubuntu is starting). I had the same error when I used knoppix, but I managed to pass it using ```
knoppix xmodule=nv noapm aoapic desktop=kde
```

After I get that apic error my xserver crashes and displays a message with an error log. It contains the following: 

```

X Window System Version 6.8.2 (Ubuntu 6.8.2-77 20051010174523 root@vernadsky.buildd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF] 
Current Operating System: Linux DBreeuwerLinux-Ubuntu 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686
Build Date: 10 October 2005
	Before reporting problems, check http://wiki.X.Org
	to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.12-9-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Oct 10 13:14:36 BST 2005 
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Mar  5 17:20:10 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Acer AL1714"
(**) |   |-->Device "Intel Corporation 82865G Integrated Graphics Device"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
	Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.2
	X.Org Video Driver: 0.7
	X.Org XInput driver : 0.4
	X.Org Server Extension : 0.2
	X.Org Font Renderer : 0.4
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Module bitmap: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/X11R6/lib/modules/libpcidata.a
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2570 card 8086,2570 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 8086,2572 card 8086,485a rev 02 class 03,80,00 hdr 00
(II) PCI: 00:1d:0: chip 8086,24d2 card 8086,485a rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24d4 card 8086,485a rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24d7 card 8086,485a rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,24de card 8086,485a rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24dd card 8086,485a rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24db card 8086,485a rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,24d1 card 8086,485a rev 02 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,24d3 card 8086,485a rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24d5 card 8086,0210 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 1b13,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 01:01:0: chip 11bd,bede card 11bd,0022 rev 00 class 04,80,00 hdr 80
(II) PCI: 01:01:1: chip 11bd,0015 card 11bd,0022 rev 00 class 0c,00,10 hdr 80
(II) PCI: 01:08:0: chip 8086,1050 card 8086,304a rev 01 class 02,00,00 hdr 00
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
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x020a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000b000 - 0x0000bfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xd4800000 - 0xe47fffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:2:0) Intel Corp. 82865G Integrated Graphics Device rev 2, Mem @ 0x20000000/27, I/O @ 0xfff8/3
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/24, 0xd8000000/27, BIOS @ 0xfe9e0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfe9dd000 - 0xfe9ddfff (0x1000) MX[B]
	[1] -1	0	0xfe9df800 - 0xfe9dffff (0x800) MX[B]
	[2] -1	0	0xfe9de000 - 0xfe9defff (0x1000) MX[B]
	[3] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[5] -1	0	0x1f000000 - 0x1f0003ff (0x400) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[12] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
(II) Inactive PCI resource ranges:
	[0] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
	[1] -1	0	0x0000fff8 - 0x0000ffff (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfe9dd000 - 0xfe9ddfff (0x1000) MX[B]
	[1] -1	0	0xfe9df800 - 0xfe9dffff (0x800) MX[B]
	[2] -1	0	0xfe9de000 - 0xfe9defff (0x1000) MX[B]
	[3] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[4] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[5] -1	0	0x1f000000 - 0x1f0003ff (0x400) MX[B]
	[6] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[9] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[12] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[14] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[15] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[17] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[18] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[19] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[21] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[22] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
	[1] -1	0	0x0000fff8 - 0x0000ffff (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1effffff (0x1ef00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[6] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1effffff (0x1ef00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe9dd000 - 0xfe9ddfff (0x1000) MX[B]
	[6] -1	0	0xfe9df800 - 0xfe9dffff (0x800) MX[B]
	[7] -1	0	0xfe9de000 - 0xfe9defff (0x1000) MX[B]
	[8] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[9] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[10] -1	0	0x1f000000 - 0x1f0003ff (0x400) MX[B]
	[11] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[30] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[31] -1	0	0x0000fff8 - 0x0000ffff (0x8) IX[B](B)
(WW) Ignoring request to load module GLcore
(II) LoadModule: "bitmap"
(II) Reloading /usr/X11R6/lib/modules/fonts/libbitmap.a
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/X11R6/lib/modules/libddc.a
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "dri"
(II) Loading /usr/X11R6/lib/modules/extensions/libdri.a
(II) Module dri: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/X11R6/lib/modules/linux/libdrm.a
(II) Module drm: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/X11R6/lib/modules/extensions/libextmod.a
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.2
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
(II) Loading /usr/X11R6/lib/modules/fonts/libfreetype.a
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 6.8.2, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/X11R6/lib/modules/extensions/libglx.a
(II) Module glx: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/X11R6/lib/modules/extensions/libGLcore.a
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.2
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/X11R6/lib/modules/linux/libint10.a
(II) Module int10: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "type1"
(II) Loading /usr/X11R6/lib/modules/fonts/libtype1.a
(II) Module type1: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.2
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.4
(II) Loading font Type1
(II) Loading font CID
(II) LoadModule: "vbe"
(II) Loading /usr/X11R6/lib/modules/libvbe.a
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.1.0
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "nv"
(II) Loading /usr/X11R6/lib/modules/drivers/nv_drv.o
(II) Module nv: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 0.7
(II) LoadModule: "kbd"
(II) Loading /usr/X11R6/lib/modules/input/kbd_drv.o
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) LoadModule: "mouse"
(II) Loading /usr/X11R6/lib/modules/input/mouse_drv.o
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.4
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
	Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
	Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
	GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
	GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
	Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
	GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
	GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
	GeForce4 440 Go 64M, Quadro4 NVS, Quadro4 500 GoGL,
	GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
	GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
	GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
	Quadro4 280 NVS, Quadro4 380 XGL, Quadro NVS 50 PCI, GeForce4 448 Go,
	GeForce4 MX Integrated GPU, GeForce3, GeForce3 Ti 200,
	GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600, GeForce4 Ti 4400,
	0x0252, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
	Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
	GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
	Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
	GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
	GeForce FX 5600 Ultra, GeForce FX 5600, 0x0313, GeForce FX 5600SE,
	0x0316, 0x0317, GeForce FX Go5600, GeForce FX Go5650,
	Quadro FX Go700, 0x031D, 0x031E, 0x031F, GeForce FX 5200,
	GeForce FX 5200 Ultra, GeForce FX 5200, GeForce FX 5200SE,
	GeForce FX Go5200, GeForce FX Go5250, GeForce FX 5500,
	GeForce FX 5100, GeForce FX Go5200 32M/64M, 0x0329,
	Quadro NVS 280 PCI, Quadro FX 500/600 PCI, GeForce FX Go53xx Series,
	GeForce FX Go5100, 0x032F, GeForce FX 5900 Ultra, GeForce FX 5900,
	GeForce FX 5900XT, GeForce FX 5950 Ultra, Quadro FX 700,
	GeForce FX 5900ZT, Quadro FX 3000, GeForce FX 5700 Ultra,
	GeForce FX 5700, GeForce FX 5700LE, GeForce FX 5700VE, 0x0345,
	GeForce FX Go5700, GeForce FX Go5700, 0x0349, 0x034B,
	Quadro FX Go1000, Quadro FX 1100, 0x034F, GeForce 6800 Ultra,
	GeForce 6800, GeForce 6800 LE, 0x0043, GeForce 6800 GT, 0x0049,
	Quadro FX 4000, 0x00C0, GeForce 6800, GeForce 6800 LE,
	GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400, 0x00CD,
	Quadro FX 1400, GeForce 6600 GT, GeForce 6600, 0x0142, 0x0143,
	GeForce Go 6600, GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, 0x0147,
	GeForce Go 6600, 0x0149, 0x014B, 0x014C, 0x014D, Quadro FX 540,
	GeForce 6200, 0x0160, GeForce 6200 TurboCache(TM), 0x0162, 0x0163,
	GeForce Go 6200, 0x0163, GeForce Go 6250, GeForce Go 6200,
	GeForce Go 6250, 0x0169, 0x016B, 0x016C, 0x016D, 0x016E, 0x0210,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, 0x0220, 0x0221,
	0x0222, 0x0228
(II) Primary Device is: PCI 01:00:0
(--) Chipset GeForce FX 5200 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1effffff (0x1ef00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe9dd000 - 0xfe9ddfff (0x1000) MX[B]
	[6] -1	0	0xfe9df800 - 0xfe9dffff (0x800) MX[B]
	[7] -1	0	0xfe9de000 - 0xfe9defff (0x1000) MX[B]
	[8] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[9] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[10] -1	0	0x1f000000 - 0x1f0003ff (0x400) MX[B]
	[11] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[20] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[21] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[22] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[24] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[25] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[28] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[29] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[30] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[31] -1	0	0x0000fff8 - 0x0000ffff (0x8) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0xffe00000 - 0xffffffff (0x200000) MX[B](B)
	[1] -1	0	0x00100000 - 0x1effffff (0x1ef00000) MX[B]E(B)
	[2] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[3] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[4] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[5] -1	0	0xfe9dd000 - 0xfe9ddfff (0x1000) MX[B]
	[6] -1	0	0xfe9df800 - 0xfe9dffff (0x800) MX[B]
	[7] -1	0	0xfe9de000 - 0xfe9defff (0x1000) MX[B]
	[8] -1	0	0xfebff400 - 0xfebff4ff (0x100) MX[B]
	[9] -1	0	0xfebff800 - 0xfebff9ff (0x200) MX[B]
	[10] -1	0	0x1f000000 - 0x1f0003ff (0x400) MX[B]
	[11] -1	0	0xfebffc00 - 0xfebfffff (0x400) MX[B]
	[12] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[13] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[16] -1	0	0x20000000 - 0x27ffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000bc00 - 0x0000bc3f (0x40) IX[B]
	[23] -1	0	0x0000c800 - 0x0000c81f (0x20) IX[B]
	[24] -1	0	0x0000dc00 - 0x0000dc0f (0x10) IX[B]
	[25] -1	0	0x0000e000 - 0x0000e003 (0x4) IX[B]
	[26] -1	0	0x0000e400 - 0x0000e407 (0x8) IX[B]
	[27] -1	0	0x0000e800 - 0x0000e803 (0x4) IX[B]
	[28] -1	0	0x0000ec00 - 0x0000ec07 (0x8) IX[B]
	[29] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[30] -1	0	0x0000d800 - 0x0000d81f (0x20) IX[B]
	[31] -1	0	0x0000d400 - 0x0000d41f (0x20) IX[B]
	[32] -1	0	0x0000d000 - 0x0000d01f (0x20) IX[B]
	[33] -1	0	0x0000cc00 - 0x0000cc1f (0x20) IX[B]
	[34] -1	0	0x0000fff8 - 0x0000ffff (0x8) IX[B](B)
	[35] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[36] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/X11R6/lib/modules/linux/libint10.a
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce FX 5200"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/X11R6/lib/modules/libvgahw.a
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.1.0
	ABI class: X.Org Video Driver, version 0.7
(**) NV(0): Option "UseFBDev" "true"
(==) NV(0): Using HW cursor
(**) NV(0): Using framebuffer device
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/X11R6/lib/modules/linux/libfbdevhw.a
(II) Module fbdevhw: vendor="X.Org Foundation"
	compiled for 6.8.2, module version = 0.0.2
	ABI class: X.Org Video Driver, version 0.7
(WW) open /dev/fb1: No such file or directory
(WW) open /dev/fb2: No such file or directory
(WW) open /dev/fb3: No such file or directory
(WW) open /dev/fb4: No such file or directory
(WW) open /dev/fb5: No such file or directory
(WW) open /dev/fb6: No such file or directory
(WW) open /dev/fb7: No such file or directory
(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons
	(you may have to look at the server log to see warnings)
(II) UnloadModule: "nv"
(II) UnloadModule: "fbdevhw"
(II) Unloading /usr/X11R6/lib/modules/linux/libfbdevhw.a
(II) UnloadModule: "vgahw"
(II) Unloading /usr/X11R6/lib/modules/libvgahw.a
(II) UnloadModule: "int10"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.X.Org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.


```

My graphics card is an Nvidia GeForce FX 5200 I use Intel Pentium 4 Ht. 

I am kind off a n00b for linux, so I need help. 

As for the suggestion rjwood said, I dont know were to put it. Do i write it on the command line by pressing c on grub boot loader? Or after I get the error? (witch I cant do right now because I am asked for a password and username that I dont have :p) 

How can I do the same thing I used with knoppix on ubuntu? How do I boot to kde without first logging into ubuntu? Is there a way to tell ubuntu I want my xmodule to be nv without using sudo dpkg-reconfigure xserver-xorg?

As you see I have many doubts, but I want to learn. Thank You very much

Dirk Breeuwer

---

### Post by Jason_25 on 2006-03-05
Hi.  Check out this thread from just 2 hours ago...;) 

[http://www.ubuntuforums.org/showthread.php?t=139924](http://www.ubuntuforums.org/showthread.php?t=139924)

---

### Post by DirkBreeuwer on 2006-03-05
I guess my problem is that I dont know my password that i set during the install, currently i am in knoppix, is there a way to resset my password via knoppix ?

Thanks for the help .


Ok nevermid thanks jason_25  I am right now using ubuntu. Thanks for all the help guys. If anyone wants to hear what I did just mail me.

---

### Post by fish47 on 2006-03-08
hey it's functioning, i'm live from gnome :)
i got tired of the "sudo dpkg-reconfigure xserver-xorg", its really messy, very complicated and the characters are all messed, all ones on top of others, so i cant read some options. so i went cowboy ant startd editing xorg.conf myself. that and taking down "startx" errors started working, i had to use the "vesa" driver, "nv" driver cant start the framebuffer, dont know why. is there any other drivers i can use to replace the nvidia one? is there any disavantage in not using the nv driver (full hardware features usage / 3d hardware accelatation ) ?

---

### Post by GfµnK on 2006-03-25
I am basically having this same problem, however instead of seeing a bunch of weird lines and squares, I just see what was last on the screen, which after booting is a solid dash in the upper left corner.  I can get into terminals 1-6 fine, but when I try to go into terminal 7, I have the same problem of just seeing what was last displayed on the screen.  When it first boots up and I see the dash, I can successfully log in (based upon the sounds), but again I can't really do anything past that, because I can only see the dash.

My specs are:

Gigabyte K8N SLI F4 mobo
2 x PNY 6600 GT video cards
AMD 3500 + socket 939 proccy

I installed the latest nVidia drivers aparantly successfully, but that didn't change anything, and neither did changing the drivers to "vesa".

---

### Post by mofojones on 2006-03-25
[QUOTE=fish47]hey it's functioning, i'm live from gnome :)
i got tired of the "sudo dpkg-reconfigure xserver-xorg", its really messy, very complicated and the characters are all messed, all ones on top of others, so i cant read some options. so i went cowboy ant startd editing xorg.conf myself. that and taking down "startx" errors started working, i had to use the "vesa" driver, "nv" driver cant start the framebuffer, dont know why. is there any other drivers i can use to replace the nvidia one? is there any disavantage in not using the nv driver (full hardware features usage / 3d hardware accelatation ) ?[/QUOTE]

actually, the open-source "nv" driver only offers 2d acceleration.  You might try to install the latest version of the "nvidia" driver from nvidia.com.  Do a search of the wiki first, to see if there's a tutorial.

---

### Post by mofojones on 2006-03-25
[QUOTE=GfµnK]I am basically having this same problem, however instead of seeing a bunch of weird lines and squares, I just see what was last on the screen, which after booting is a solid dash in the upper left corner.  I can get into terminals 1-6 fine, but when I try to go into terminal 7, I have the same problem of just seeing what was last displayed on the screen.  When it first boots up and I see the dash, I can successfully log in (based upon the sounds), but again I can't really do anything past that, because I can only see the dash.

My specs are:

Gigabyte K8N SLI F4 mobo
2 x PNY 6600 GT video cards
AMD 3500 + socket 939 proccy

I installed the latest nVidia drivers aparantly successfully, but that didn't change anything, and neither did changing the drivers to "vesa".[/QUOTE]

I'd be willing to bet that your SLI rig is the culpret (sp?)  Try running with just one video card and the nvidia driver to see if that's not the case.  I know it's not cool to run with just one video card, but nvidia will likely release an update soon to fix your problem, if it turns out to be the SLI/driver.

---

### Post by GfµnK on 2006-03-26
But what would make my system any different from the other SLI rigs that are running linux fine?  I have a feeling it's just some setting in the Xorg.conf file, but I don't know what should be changed.

---

### Post by Tamale on 2006-03-26
did running: "sudo nvidia-glx-config enable"   help ?

---

