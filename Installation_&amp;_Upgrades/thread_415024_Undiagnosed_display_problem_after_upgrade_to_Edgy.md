---
title: "Undiagnosed display problem after upgrade to Edgy"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by cajunaggie on 2007-04-20
When Edgy Eft was released I didn't upgrade from Dapper. With the release of Feisty, however, I decided an upgrade was in order. I upgrade Dapper to Eft using the GUI method and let it download and upgrade overnight. The update manager did ask me if I wanted to keep two custom settings. I can't remember exactly what they were but one had to do with the GDM and the other had to do with "Init" I think. I kept my custom settings instead of going with the defaults. In restrospect this might have been an error.

Upon reboot I ran into trouble. The screen goes blank upon hitting the GDM. I figured it was a x-server issue and rebooted in safe mode to try and find out what went wrong. I gave the "startx" command and was rewarded with a blank screen.

Under normal circumstances, when both monitor and box are on a small blue light displays from the power button. When monitor is on and box is off it turns orange. When I run "startx" in safe mode the light turns orange. My theory is that somewhere along the line my video card stopped talking to my monitor. Unfortunately my command line kung-fu is not strong enough for this particular task.

Anyone got any ideas? :confused:

---

### Post by cbravo on 2007-04-20
First, log in (get to the loginprompt with Alt-F2 or Ctrl-Alt-F2) and get to the commandline. Become root by typing:

```
sudo su
```

Then look at the Xorg log:

```
cat /var/log/Xorg.0.log
```

Maybe more hints are available there. Post it for us to see please.

---

### Post by cajunaggie on 2007-04-20
Is there a way to slow down the output? It's screaming a bunch of lines at me in a blur and I can't read them quick enough to keep up, let alone write them down? Is there a command line text editor I could view the log in?

---

### Post by cajunaggie on 2007-04-20
Okay I found it. I'm posting it in two parts because there's a character limit on this forum
PART 1
```

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux hex 2.6.17-11-386 #2 Tue Mar 13 23:30:30 UTC 2007 i686
Build Date: 07 July 2006
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 20 11:26:13 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "aticonfig-Screen[0]" (0)
(**) |   |-->Monitor "aticonfig-Monitor[0]"
(**) |   |-->Device "aticonfig-Device[0]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
	Entry deleted from font path.
(**) FontPath set to:
	/usr/share/X11/fonts/misc,
	/usr/share/X11/fonts/100dpi/:unscaled,
	/usr/share/X11/fonts/75dpi/:unscaled,
	/usr/share/X11/fonts/Type1,
	/usr/share/X11/fonts/100dpi,
	/usr/share/X11/fonts/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	/usr/share/fonts/X11/misc/,
	/usr/share/fonts/X11/TTF/,
	/usr/share/fonts/X11/OTF,
	/usr/share/fonts/X11/Type1/,
	/usr/share/fonts/X11/CID/,
	/usr/share/fonts/X11/100dpi/,
	/usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
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

```

---

### Post by cajunaggie on 2007-04-20
PART II
```

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 10de,01e0 card 0000,0000 rev c1 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,01eb card 1297,0531 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,01ee card 1297,0531 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,01ed card 1297,0531 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:4: chip 10de,01ec card 1297,0531 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:00:5: chip 10de,01ef card 1297,0531 rev c1 class 05,00,00 hdr 80
(II) PCI: 00:01:0: chip 10de,0060 card 1297,0531 rev a4 class 06,01,00 hdr 80
(II) PCI: 00:01:1: chip 10de,0064 card 1297,0531 rev a2 class 0c,05,00 hdr 80
(II) PCI: 00:02:0: chip 10de,0067 card 1297,0531 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:1: chip 10de,0067 card 1297,0531 rev a4 class 0c,03,10 hdr 80
(II) PCI: 00:02:2: chip 10de,0068 card 1297,0531 rev a4 class 0c,03,20 hdr 80
(II) PCI: 00:06:0: chip 10de,006a card 1297,0531 rev a1 class 04,01,00 hdr 00
(II) PCI: 00:08:0: chip 10de,006c card 0000,0000 rev a3 class 06,04,00 hdr 01
(II) PCI: 00:09:0: chip 10de,0065 card 1297,0531 rev a2 class 01,01,8a hdr 00
(II) PCI: 00:1e:0: chip 10de,01e8 card 0000,0000 rev c1 class 06,04,00 hdr 01
(II) PCI: 01:06:0: chip 10ec,8169 card 1385,311a rev 10 class 02,00,00 hdr 00
(II) PCI: 01:08:0: chip 168c,0013 card 1385,5a00 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 1002,5964 card 1787,5964 rev 01 class 03,00,00 hdr 80
(II) PCI: 02:00:1: chip 1002,5d44 card 1787,5965 rev 01 class 03,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:1:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:8:0), (0,1,1), BCTRL: 0x0202 (VGA_EN is cleared)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x00009fff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xe6000000 - 0xe7ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0x30000000 - 0x300fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xe4000000 - 0xe5ffffff (0x2000000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xd0000000 - 0xdfffffff (0x10000000) MX[B]
(--) PCI:*(2:0:0) ATI Technologies Inc RV280 [Radeon 9200 SE] rev 1, Mem @ 0xd0000000/27, 0xe5000000/16, I/O @ 0xa000/8
(--) PCI: (2:0:1) ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) rev 1, Mem @ 0xd8000000/27, 0xe5010000/16
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
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[1] -1	0	0xe7010000 - 0xe70100ff (0x100) MX[B]
	[2] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[3] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[4] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[5] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[11] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[13] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges:
	[0] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[1] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[1] -1	0	0xe7010000 - 0xe70100ff (0x100) MX[B]
	[2] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[3] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[4] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[5] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[10] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[11] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[12] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[13] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[14] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) Inactive PCI resource ranges after removing overlaps:
	[0] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[1] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
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
	[4] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[5] -1	0	0xe7010000 - 0xe70100ff (0x100) MX[B]
	[6] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[7] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[8] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[9] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
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
(II) LoadModule: "fglrx"
(II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
(II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.28.8
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
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
(II) ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9250/9200 Series (RV280 5961),
	RADEON 9250/9200 Series (RV280 5962),
	RADEON 9250/9200 Series (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300/X550 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 SE (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600/X550 Series (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 GTO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), FireGL V7200 (R480 5D50),
	RADEON X850 XT (R480 5D52), RADEON X850 (R481 4B48),
	RADEON X850 XT (R481 4B49), RADEON X850 SE (R481 4B4A),
	RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), RADEON X700 XT (RV410 5E4A),
	RADEON X700 PRO (RV410 5E4B), RADEON X700 SE (RV410 5E4C),
	RADEON X700 (RV410 5E4D), RADEON X700/X550 Series (RV410 5E4F),
	MOBILITY RADEON X700 (M26 5652), MOBILITY RADEON X700 (M26 5653),
	MOBILITY RADEON X700 XL (M26-XC 564F),
	RADEON 9000/9100 IGP Series (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000 IGP (RL300MB 7835),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 XT (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 Series (R520 7108),
	RADEON X1800 Series (R520 7109), RADEON X1800 Series (R520 710A),
	RADEON X1800 Series (R520 710B), RADEON X1800 Series (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1600 Series (RV515 7140), RADEON X1300 Series (RV515 7142),
	MOBILITY FireGL (M54 GL 7144), MOBILITY RADEON X1400 (M54 7145),
	RADEON X1300 Series (RV515 7146), MOBILITY RADEON X1300 (M52 7149),
	MOBILITY RADEON X1300 (M52 714A), RADEON X1300 Series (RV515 714D),
	RADEON X1300 Series (RV515 714E), FireGL V3300 (RV515 7152),
	RADEON X1300 Series (RV515 715E), RADEON X1300 (RV516 7180),
	RADEON X1600 Series (RV516 7181), RADEON X1300 (RV516 7183),
	MOBILITY RADEON X1450 (M64P 7186), RADEON X1300 (RV516 7187),
	MOBILITY RADEON X1350 (M62P 718B),
	MOBILITY RADEON X1350 (M62CSP 718C),
	MOBILITY RADEON X1450 (M64CSP 718D),
	MOBILITY RADEON X1350 (M62S 7196), RADEON X1900 (R580 7240),
	RADEON X1900 (R580 7243), RADEON X1900 (R580 7244),
	RADEON X1900 (R580 7245), RADEON X1900 (R580 7246),
	RADEON X1900 (R580 7247), RADEON X1900 (R580 7248),
	RADEON X1900 (R580 7249), RADEON X1900 (R580 724A),
	RADEON X1900 (R580 724B), RADEON X1900 (R580 724C),
	RADEON X1900 (R580 724D), FireStream 2U (R580 724E),
	FireStream 2U (R580 724F), RADEON X1600 Series (RV530 71C0),
	RADEON X1600 Series (RV530 71C2), MOBILITY FireGL V5200 (M56 71C4),
	MOBILITY RADEON X1600 (M56 71C5),
	RADEON X1600 Series (RV530 LE 71C6),
	RADEON X1600 Series (RV530 VE 71CE), FireGL V3400 (RV530 71D2),
	MOBILITY RADEON X1700 (M66-XT 71D6), FireGL V5200 (RV530 71DA),
	RADEON X1600 Series (RV530 SE 71DE), RADEON X1600 XT (RV535 XT 71C1),
	MOBILITY FireGL V5250 (M66GL 71D4),
	MOBILITY RADEON X1700 (M66-P 71D5), RADEON Xpress 1200 (RS600 7941),
	RADEON Xpress 1200 (RS600 7942)
(II) Primary Device is: PCI 02:00:0
(II) ATI Proprietary Linux Driver Version Identifier:8.28.8
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.28g1                           
(II) ATI Proprietary Linux Driver Build Date: Aug 17 2006 09:28:12
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.28.1.1.2.3-driver-lnx-x86-x86_64-287161
(--) Assigning device section with no busID to primary device
(WW) fglrx: No matching Device section for instance (BusID PCI:2:0:1) found
(--) Chipset RADEON 9250/9200 Series (RV280 5964) found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[5] -1	0	0xe7010000 - 0xe70100ff (0x100) MX[B]
	[6] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[7] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[8] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[9] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[18] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[19] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[20] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[21] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[22] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
(II) fglrx(0): pEnt->device->identifier=0x81e17d8
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[5] -1	0	0xe7010000 - 0xe70100ff (0x100) MX[B]
	[6] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[7] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[8] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[9] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[14] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[21] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[22] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[23] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[24] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[25] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) fglrx(0): === [R200PreInit] === begin, [s]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.0
(II) fglrx(0): PCI bus 2 card 0 func 0
(**) fglrx(0): Depth 24, (--) framebuffer bpp 32
(II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
(==) fglrx(0): Default visual is TrueColor
(**) fglrx(0): Option "OpenGLOverlay" "off"
(**) fglrx(0): Option "VideoOverlay" "on"
(**) fglrx(0): Option "DPMS" "true"
(==) fglrx(0): RGB weight 888
(II) fglrx(0): Using 8 bits per RGB (8 bit DAC)
(==) fglrx(0): Gamma Correction for I is 0x06419064
(==) fglrx(0): Gamma Correction for II is 0x06419064
(==) fglrx(0): Buffer Tiling is ON
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) fglrx(0): Primary V_BIOS segment is: 0xc000
(--) fglrx(0): Chipset: "RADEON 9250/9200 Series (RV280 5964)" (Chipset = 0x5964)
(--) fglrx(0): (PciSubVendor = 0x1787, PciSubDevice = 0x5964)
(--) fglrx(0): board vendor info: third party graphics adapter - NOT original ATI
(--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
(--) fglrx(0): MMIO registers at 0xe5000000
(==) fglrx(0): ROM-BIOS at 0x000c0000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) fglrx(0): VESA BIOS detected
(II) fglrx(0): VESA VBE Version 2.0
(II) fglrx(0): VESA VBE Total Mem: 131072 kB
(II) fglrx(0): VESA VBE OEM: ATI RADEON 9200
(II) fglrx(0): VESA VBE OEM Software Rev: 1.0
(II) fglrx(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) fglrx(0): VESA VBE OEM Product: V280
(II) fglrx(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Reloading /usr/lib/xorg/modules/linux/libdrm.so
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 6, (OK)
drmGetBusid returned ''
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) Module fglrxdrm: vendor="FireGL - ATI Technologies Inc."
	compiled for 7.1.0, module version = 8.28.8
	ABI class: X.Org Server Extension, version 0.3
(--) fglrx(0): VideoRAM: 131072 kByte, Type: DDR SGRAM / SDRAM
(II) fglrx(0): AGP card detected
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) fglrx(0): Primary Controller - CRT on primary DAC
(II) fglrx(0): Internal Desktop Setting: 0x00000008
(II) fglrx(0): POWERplay version 3.  1 power state available:
(II) fglrx(0):   1. 200/133MHz @ 50Hz [enable load balancing]
(==) fglrx(0): Qbs disabled
(==) fglrx(0): FAST_SWAP disabled
(==) fglrx(0):  PseudoColor visuals disabled
(==) fglrx(0): Using gamma correction (1.0, 1.0, 1.0)
(==) fglrx(0): Center Mode is disabled 
(==) fglrx(0): TMDS coherent mode is enabled 
(II) fglrx(0): Total of 17 modes found for primary display.
(--) fglrx(0): Virtual size is 1600x1200 (pitch 0)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
(==) fglrx(0): DPI set to (75, 75)
(--) fglrx(0): Virtual size is 1600x1200 (pitch 1600)
(**) fglrx(0): *Mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1600x1200"  162.00  1600 1664 1856 2160  1200 1201 1204 1250
(**) fglrx(0): *Mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066
(**) fglrx(0):  Default mode "1280x1024": 85.5 MHz (scaled from 0.0 MHz), 50.9 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   85.51  1280 1344 1480 1680  1024 1025 1028 1083 interlace +hsync
(**) fglrx(0):  Default mode "1280x1024": 77.8 MHz (scaled from 0.0 MHz), 46.3 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1280x1024"   77.80  1280 1344 1480 1680  1024 1025 1028 1077 interlace +hsync
(**) fglrx(0): *Mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1152x864"   81.62  1152 1216 1336 1520  864 865 868 895 +hsync
(**) fglrx(0):  Default mode "1152x864": 64.7 MHz (scaled from 0.0 MHz), 43.0 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   64.67  1152 1208 1328 1504  864 865 868 915 interlace +hsync
(**) fglrx(0):  Default mode "1152x864": 58.3 MHz (scaled from 0.0 MHz), 39.2 kHz, 43.0 Hz (I)
(II) fglrx(0): Modeline "1152x864"   58.28  1152 1200 1320 1488  864 865 868 911 interlace +hsync
(**) fglrx(0): *Mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) fglrx(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 +hsync +vsync
(**) fglrx(0): *Mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.0 Hz
(II) fglrx(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628
(**) fglrx(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.0 Hz
(II) fglrx(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625
(**) fglrx(0):  Default mode "800x600": 29.6 MHz (scaled from 0.0 MHz), 29.8 kHz, 47.0 Hz (I)
(II) fglrx(0): Modeline "800x600"   29.60  800 816 896 992  600 601 604 635 interlace +hsync
(**) fglrx(0): *Mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x480"   25.18  640 656 752 800  480 490 492 525 +hsync +vsync
(**) fglrx(0):  Default mode "640x400": 24.9 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) fglrx(0): Modeline "640x400"   24.92  640 664 760 792  400 460 462 525
(**) fglrx(0):  Default mode "512x384": 19.8 MHz (scaled from 0.0 MHz), 29.8 kHz, 60.0 Hz
(II) fglrx(0): Modeline "512x384"   19.81  512 544 624 664  384 451 453 497
(**) fglrx(0):  Default mode "400x300": 22.3 MHz (scaled from 0.0 MHz), 45.0 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "400x300"   22.33  400 416 480 496  300 601 605 742 doublescan
(**) fglrx(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x240"   12.59  320 328 376 400  240 491 493 525 doublescan
(**) fglrx(0):  Default mode "320x200": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz (D)
(II) fglrx(0): Modeline "320x200"   12.59  320 336 384 400  200 457 459 524 doublescan
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
(==) fglrx(0): NoAccel = NO
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.0
(==) fglrx(0): HPV inactive
(==) fglrx(0): FSAA enabled: NO
(==) fglrx(0): FSAA Gamma enabled
(==) fglrx(0): FSAA Multisample Position is fix
(==) fglrx(0): NoDRI = NO
(II) Loading sub module "fglrxdrm"
(II) LoadModule: "fglrxdrm"
(II) Reloading /usr/lib/xorg/modules/linux/libfglrxdrm.so
(II) fglrx(0): Depth moves disabled by default
(==) fglrx(0): Capabilities: 0x00000000
(==) fglrx(0): CapabilitiesEx: 0x00000000
(==) fglrx(0): cpuFlags: 0x4000000f
(==) fglrx(0): cpuSpeedMHz: 0x00000446
(==) fglrx(0): OpenGL ClientDriverName: "atiogl_a_dri.so"
(==) fglrx(0): UseFastTLS=0
(==) fglrx(0): BlockSignalsOnLock=1
(==) fglrx(0): EnablePrivateBackZ = NO
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe5000000 - 0xe500ffff (0x10000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xe7000000 - 0xe700ffff (0x10000) MX[B]
	[7] -1	0	0xe7010000 - 0xe70100ff (0x100) MX[B]
	[8] -1	0	0xe8000000 - 0xe8000fff (0x1000) MX[B]
	[9] -1	0	0xe8004000 - 0xe80040ff (0x100) MX[B]
	[10] -1	0	0xe8003000 - 0xe8003fff (0x1000) MX[B]
	[11] -1	0	0xe8002000 - 0xe8002fff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xe5000000 - 0xe500ffff (0x10000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xe5010000 - 0xe501ffff (0x10000) MX[B](B)
	[16] -1	0	0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
	[17] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[18] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[19] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[20] 0	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[21] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[22] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[23] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[24] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[25] -1	0	0x0000b000 - 0x0000b07f (0x80) IX[B]
	[26] -1	0	0x0000c000 - 0x0000c0ff (0x100) IX[B]
	[27] -1	0	0x0000bc00 - 0x0000bc1f (0x20) IX[B]
	[28] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B](B)
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) fglrx(0): UMM Bus area:     0xd0954000 (size=0x076ac000)
(II) fglrx(0): UMM area:     0xd0954000 (size=0x076ac000)
(II) fglrx(0): Composite extension enabled, disabling direct rendering
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xd0000000 FBMappedSize: 0x08000000
(==) fglrx(0): Write-combining range (0xd0000000,0x8000000)
(II) fglrx(0): FBMM initialized for area (0,0)-(1600,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1600,1200) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled
(**) fglrx(0): DPMS enabled
(WW) fglrx(0): Option "VendorName" is not used
(WW) fglrx(0): Option "ModelName" is not used
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	Solid Horizontal and Vertical Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
(II) fglrx(0): Acceleration enabled
(II) fglrx(0): Direct rendering disabled
(==) fglrx(0): Using hardware cursor
(II) fglrx(0): Largest offscreen area available: 1600 x 6988
(**) fglrx(0): Video overlay enabled on CRTC1
(II) Loading extension FGLRXEXTENSION
(II) Loading extension ATITVOUT
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
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions/libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3

```

---

### Post by cajunaggie on 2007-04-20
Okay, in 3 parts
```
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
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
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us" };
    xkb_geometry             { include "pc(pc104)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
    xkb_types                { include "%" };
    xkb_compatibility        { include "%" };
    xkb_symbols              { include "%" };
    xkb_geometry             { include "%" };
(EE) Error loading keymap /var/lib/xkb/server-0.xkm
    xkb_types                { include "%" };
    xkb_compatibility        { include "%" };
    xkb_symbols              { include "%" };
    xkb_geometry             { include "%" };
(EE) Error loading keymap /var/lib/xkb/server-0.xkm

```

I used a liveCD to hunt this down. When I was poking around I noticed a lot of top-level duplicate system folders. Could that be screwing things up?

---

### Post by BOIX on 2007-04-20
this might work, in the previous version. 6.10, the motherboard bios had to be set to 
AGP 4x and NOT 8x

for ubuntu to load up and output to the display monitor properly.

just a quick suggesiton, to change you motherboard bios agp settings to 4x and then try doing it again.

---

### Post by cajunaggie on 2007-04-21
And, no dice.

---

