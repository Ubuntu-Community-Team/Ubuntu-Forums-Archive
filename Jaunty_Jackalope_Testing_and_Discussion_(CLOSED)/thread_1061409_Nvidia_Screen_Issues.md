---
title: "Nvidia Screen Issues"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by BinaryApe on 2009-02-05
ALright So at first I was having issues with getting the nvidia driver installed. I got past that part and have installed without removing Xorg.

Now my issue is that after using it for about 4-5 days without issues when I reboot it brings me to a black screen after the splash screen. I never make it to the login screen. Sometimes I get a black screen with a small flashing E in the upper right corner. 

So I tried re-installing the drivers. I tried to reseat my video card (which is a nvidia 7950gx2) and that did not work. I can get in using the Vesa drivers or the nv drivers. 

So I re-installed everything (for the 10th time :)) and re-installed the drivers again (from the PPA launchpad [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu)). And it is still giving me the same issue.

My xorg.conf file is a default one with the added extra line 

Driver     "nvidia"

added to it.

Below is my Xorg.0.log from the unsuccessful boot
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.5.99.3
Release Date: (unreleased)
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server i686 Ubuntu
Current Operating System: Linux binaryape-desktop 2.6.28-4-generic #10-Ubuntu SMP Mon Jan 12 19:35:29 UTC 2009 i686
Build Date: 06 January 2009  06:23:46AM
xorg-server 2:1.5.99.3-0ubuntu4 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb  5 17:41:56 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
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
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x1ac0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI: (0@3:0:0) nVidia Corporation G71 [GeForce 7950 GX2] rev 161, Mem @ 0xf9000000/0, 0xc0000000/0, 0xfa000000/0, I/O @ 0x0000bf00/0, BIOS @ 0x????????/131072
(--) PCI:*(0@4:0:0) nVidia Corporation G71 [GeForce 7950 GX2] rev 161, Mem @ 0xf6000000/0, 0xb0000000/0, 0xf7000000/0, I/O @ 0x0000af00/0, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  180.27  Tue Jan 27 12:46:22 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) No matches found for this device in /usr/share/xserver-xorg/pci
(==) Registering 'vesa' as fallback
(==) Matched vesa for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.3.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 04@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.1.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 262144 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 5.113
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G71 Board - p602h0  
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) VESA(0): Depth 24, (--) framebuffer bpp 32
(==) VESA(0): RGB weight 888
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level 2
(II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
(II) VESA(0): VESA VBE DDC read successfully
(II) VESA(0): Manufacturer: DEL  Model: a010  Serial#: 842224211
(II) VESA(0): Year: 2005  Week: 45
(II) VESA(0): EDID Version: 1.3
(II) VESA(0): Digital Display Input
(II) VESA(0): Max Image Size [cm]: horiz.: 52  vert.: 33
(II) VESA(0): Gamma: 2.20
(II) VESA(0): DPMS capabilities: StandBy Suspend Off
(II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) VESA(0): Default color space is primary color space
(II) VESA(0): First detailed timing is preferred mode
(II) VESA(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.607
(II) VESA(0): blueX: 0.149 blueY: 0.060   whiteX: 0.312 whiteY: 0.328
(II) VESA(0): Supported VESA Video Modes:
(II) VESA(0): 720x400@70Hz
(II) VESA(0): 640x480@60Hz
(II) VESA(0): 640x480@75Hz
(II) VESA(0): 800x600@60Hz
(II) VESA(0): 800x600@75Hz
(II) VESA(0): 1024x768@60Hz
(II) VESA(0): 1024x768@75Hz
(II) VESA(0): 1280x1024@75Hz
(II) VESA(0): Manufacturer's mask: 0
(II) VESA(0): Supported Future Video Modes:
(II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) VESA(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) VESA(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) VESA(0): Supported additional Video Mode:
(II) VESA(0): clock: 154.0 MHz   Image Size:  519 x 324 mm
(II) VESA(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
(II) VESA(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 v_border: 0
(II) VESA(0): Serial No: T61335B123RS
(II) VESA(0): Monitor name: DELL 2405FPW
(II) VESA(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz, PixClock max 170 MHz
(II) VESA(0): EDID (in hex):
(II) VESA(0): 	00ffffffffffff0010ac10a053523332
(II) VESA(0): 	2d0f010380342178eeee50a3544c9b26
(II) VESA(0): 	0f5054a54b008180a940714fb3000101
(II) VESA(0): 	010101010101283c80a070b023403020
(II) VESA(0): 	360007442100001a000000ff00543631
(II) VESA(0): 	33333542313233525320000000fc0044
(II) VESA(0): 	454c4c20323430354650570a000000fd
(II) VESA(0): 	00384c1e5111000a20202020202000fc
(II) VESA(0): EDID vendor "DEL", prod id 40976
(II) VESA(0): Using EDID range info for horizontal sync
(II) VESA(0): Using EDID range info for vertical refresh
(II) VESA(0): Printing DDC gathered Modelines:
(II) VESA(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
(II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) VESA(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
(II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) VESA(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
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
	PhysBasePtr: 0xb0000000
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
	PhysBasePtr: 0xb0000000
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
	PhysBasePtr: 0xb0000000
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
	PhysBasePtr: 0xb0000000
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
	PhysBasePtr: 0xb0000000
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
Mode: 10e (320x200)
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
	PhysBasePtr: 0xb0000000
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
*Mode: 10f (320x200)
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
	PhysBasePtr: 0xb0000000
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
Mode: 111 (640x480)
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
	PhysBasePtr: 0xb0000000
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
*Mode: 112 (640x480)
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
	PhysBasePtr: 0xb0000000
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
Mode: 114 (800x600)
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
	PhysBasePtr: 0xb0000000
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
*Mode: 115 (800x600)
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
	PhysBasePtr: 0xb0000000
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
Mode: 117 (1024x768)
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
	PhysBasePtr: 0xb0000000
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
*Mode: 118 (1024x768)
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
	PhysBasePtr: 0xb0000000
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
Mode: 11a (1280x1024)
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
	PhysBasePtr: 0xb0000000
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
*Mode: 11b (1280x1024)
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
	PhysBasePtr: 0xb0000000
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
	PhysBasePtr: 0xb0000000
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
	PhysBasePtr: 0xb0000000
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
Mode: 132 (320x400)
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
	PhysBasePtr: 0xb0000000
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
*Mode: 133 (320x400)
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
	PhysBasePtr: 0xb0000000
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
	PhysBasePtr: 0xb0000000
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
Mode: 135 (320x240)
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
	PhysBasePtr: 0xb0000000
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
*Mode: 136 (320x240)
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
	PhysBasePtr: 0xb0000000
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
Mode: 13d (640x400)
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
	PhysBasePtr: 0xb0000000
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
*Mode: 13e (640x400)
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
	PhysBasePtr: 0xb0000000
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
(II) VESA(0): Configured Monitor: Using hsync range of 30.00-81.00 kHz
(II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-76.00 Hz
(II) VESA(0): Configured Monitor: Using maximum pixel clock of 170.00 MHz
(WW) VESA(0): Unable to estimate virtual size
(II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
(II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
(--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
(**) VESA(0): *Built-in mode "1280x1024"
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(**) VESA(0): Display dimensions: (520, 330) mm
(**) VESA(0): DPI set to (62, 78)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(II) VESA(0): VESA VBE OEM Product: G71 Board - p602h0  
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(II) VESA(0): virtual address = 0xa6828000,
	physical address = 0xb0000000, size = 268435456
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.99.3, module version = 2.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) AT Translated Set 2 keyboard: xkb_model: "pc105"
(**) Option "xkb_layout" "us"
(**) AT Translated Set 2 keyboard: xkb_layout: "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Desktop? 1.00
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: always reports core events
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: Device: "/dev/input/event5"
(II) Microsoft Microsoft Wireless Optical Desktop? 1.00: Found 5 mouse buttons
(II) Microsoft Microsoft Wireless Optical Desktop? 1.00: Found x and y relative axes
(II) Microsoft Microsoft Wireless Optical Desktop? 1.00: Configuring as mouse
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop? 1.00" (type: MOUSE)
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: (accel) filter chain progression: 2.00
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft Wireless Optical Desktop? 1.00: (accel) set acceleration profile 0
(II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found 8 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0
AUDIT: Thu Feb  5 17:42:00 2009: 3824: client 4 rejected from local host ( uid=0 gid=0 pid=3994 )
```


I'm not sure where to go from here. I'm going insane as the system is stable for a while, I don't change and the system stops responding. Any ideas as to what could be causing this?

---

### Post by minisori on 2009-02-06
It's a driver problem, you will not be able to see a text terminal and it's been around for some time now. You will have to wait for new drivers some day to fix this. Also i think there is a way to fix it by changing the framebuffer, but never tried it yet.

And if you mean with "stop responding" that the screen goes black or something similar just switch to a terminal and back to the X, you will probably get back to see the desktop.

---

### Post by taavikko on 2009-02-06
Why not using driver provided by the restricted repo.
It is fully functional.
(comment out anders ppa, and dist-upgrade) so that it gets upgraded.
and try again.

Also, ~/.xsession-errors is good place to watch for errors.

---

### Post by dk75 on 2009-02-06
```
gksu gedit /etc/modprobe.d/blacklist-framebuffer
```

and add "#" char at the beginning of the line "blacklist vesafb" so it would look like
```
#blacklist vesafb
```

From now on you could see terminal during bootup and you could change it's resolution by useing "vga" option in kernel load otpions ( GRUB "menu.lst" )

As for drivers - post your "xorg.conf" (you have alot strange reports in Xorg.0.log) and results of this commands:
```
uname -r
sudo dpkg -l 'linux-headers*'
sudo dpkg -l '*xorg*dev*'
```

---

### Post by minisori on 2009-02-06
Ooppss didn't read about the E thing flashing.

Probably the kernel module is not the same one as the driver which x is trying to load. Try to uninstall it completely and then reinstall from the official repo.

As for the framebuffer thing, some cards (mostly serie 9 if i'm not wrong), does not work neither. So funny black terminals forever :P

---

### Post by dk75 on 2009-02-06
my 9500 work's with vesafb - I've never touch nvidiafb at all.

---

### Post by minisori on 2009-02-06
my 9600gt gets a warm black screen :popcorn:

---

### Post by BinaryApe on 2009-02-06
Here we go

```
uname -r
```

2.6.28-6-generic

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-headers  <none>         (no description available)
un  linux-headers- <none>         (no description available)
pn  linux-headers- <none>         (no description available)
pn  linux-headers- <none>         (no description available)
ii  linux-headers- 2.6.28-6.17    Header files related to Linux kernel version
ii  linux-headers- 2.6.28-6.17    Linux kernel headers for version 2.6.28 on x
ii  linux-headers- 2.6.28.6.6     Generic Linux kernel headers

```


```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  xserver-xorg-d <none>         (no description available)
ii  xserver-xorg-i 1:2.1.1-1ubunt X.Org X server -- evdev input driver
ii  xserver-xorg-v 1:0.4.0-2      X.Org X server -- fbdev display driver

```



My xorg.conf

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

and my Xorg.0.log again:
```
[0 sec: 000000 usec]
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.
[0 sec: 000054 usec]
X.Org X Server 1.5.99[0 sec: 000073 usec].902[0 sec: 000092 usec] (1.6.0 RC 2)[0 sec: 000109 usec]
Release Date: 2009-1-30
[0 sec: 000125 usec]X Protocol Version 11, Revision 0
[0 sec: 000143 usec]Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
[0 sec: 000161 usec]Current Operating System: Linux binaryape-desktop 2.6.28-6-generic #17-Ubuntu SMP Fri Jan 30 15:34:36 UTC 2009 i686
[0 sec: 000195 usec]Build Date: 06 February 2009  02:57:24PM
[0 sec: 000213 usec]xorg-server 2:1.5.99.902-0ubuntu3 (buildd@rothera.buildd) 
[0 sec: 000230 usec]	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[0 sec: 000246 usec]Markers: [0 sec: 000269 usec](--) probed, [0 sec: 000286 usec](**) from config file, [0 sec: 000303 usec](==) default setting,
	[0 sec: 000320 usec](++) from command line, [0 sec: 000337 usec](!!) notice, [0 sec: 000354 usec](II) informational,
	[0 sec: 000371 usec](WW) warning, [0 sec: 000388 usec](EE) error, [0 sec: 000405 usec](NI) not implemented, [0 sec: 000422 usec](??) unknown.
[0 sec: 000517 usec](==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  6 16:21:12 2009
[0 sec: 001408 usec](==) Using config file: "/etc/X11/xorg.conf"
[0 sec: 001527 usec](==) No Layout section.  Using the first Screen section.
[0 sec: 001545 usec](**) |-->Screen "Default Screen" (0)
[0 sec: 001713 usec](**) |   |-->Monitor "Configured Monitor"
[0 sec: 002092 usec](**) |   |-->Device "Configured Video Device"
[0 sec: 002129 usec](==) Automatically adding devices
[0 sec: 002143 usec](==) Automatically enabling devices
[0 sec: 002341 usec](==) No FontPath specified.  Using compiled-in default.
[0 sec: 031241 usec](WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[0 sec: 031262 usec]	Entry deleted from font path.
[0 sec: 043372 usec](==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
[0 sec: 043395 usec](==) ModulePath set to "/usr/lib/xorg/modules"
[0 sec: 043410 usec](II) Cannot locate a core pointer device.
[0 sec: 043425 usec](II) Cannot locate a core keyboard device.
[0 sec: 043439 usec](II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[0 sec: 043460 usec](II) Loader magic: 0x3bc0
[0 sec: 043474 usec](II) Module ABI versions:
[0 sec: 043486 usec]	X.Org ANSI C Emulation: 0.4
[0 sec: 043498 usec]	X.Org Video Driver: 5.0
[0 sec: 043510 usec]	X.Org XInput driver : 4.0
[0 sec: 043525 usec]	X.Org Server Extension : 2.0
[0 sec: 043539 usec](II) Loader running on linux
[0 sec: 043558 usec](++) using VT number 7

[0 sec: 118646 usec](--) PCI: (0@3:0:0) [0 sec: 118684 usec]nVidia Corporation [0 sec: 118697 usec]G71 [GeForce 7950 GX2] [0 sec: 118709 usec]rev 161[0 sec: 118721 usec], Mem @ [0 sec: 118732 usec]0xf9000000/0[0 sec: 118745 usec], [0 sec: 118756 usec]0xc0000000/0[0 sec: 118768 usec], [0 sec: 118780 usec]0xfa000000/0[0 sec: 118792 usec], I/O @ [0 sec: 118803 usec]0x0000bf00/0[0 sec: 118816 usec], BIOS @ 0x????????/131072[0 sec: 118828 usec]
[0 sec: 118843 usec](--) PCI:*(0@4:0:0) [0 sec: 118856 usec]nVidia Corporation [0 sec: 118869 usec]G71 [GeForce 7950 GX2] [0 sec: 118880 usec]rev 161[0 sec: 118892 usec], Mem @ [0 sec: 118902 usec]0xf6000000/0[0 sec: 118914 usec], [0 sec: 118925 usec]0xb0000000/0[0 sec: 118936 usec], [0 sec: 118947 usec]0xf7000000/0[0 sec: 118959 usec], I/O @ [0 sec: 118970 usec]0x0000af00/0[0 sec: 118996 usec], BIOS @ 0x????????/131072[0 sec: 119008 usec]
[0 sec: 119054 usec](II) Open ACPI successful (/var/run/acpid.socket)
[0 sec: 119090 usec](II) System resource ranges:
[0 sec: 119105 usec]	[0] -1	0	0xffffffff - 0xffffffff (0x1)[0 sec: 119119 usec] M[0 sec: 119131 usec]X[0 sec: 119143 usec][B][0 sec: 119155 usec]
[0 sec: 119167 usec]	[1] -1	0	0x000f0000 - 0x000fffff (0x10000)[0 sec: 119181 usec] M[0 sec: 119194 usec]X[0 sec: 119205 usec][B][0 sec: 119215 usec]
[0 sec: 119226 usec]	[2] -1	0	0x000c0000 - 0x000effff (0x30000)[0 sec: 119238 usec] M[0 sec: 119249 usec]X[0 sec: 119260 usec][B][0 sec: 119271 usec]
[0 sec: 119281 usec]	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000)[0 sec: 119294 usec] M[0 sec: 119305 usec]X[0 sec: 119316 usec][B][0 sec: 119327 usec]
[0 sec: 119337 usec]	[4] -1	0	0x0000ffff - 0x0000ffff (0x1)[0 sec: 119350 usec] I[0 sec: 119361 usec]X[0 sec: 119371 usec][B][0 sec: 119382 usec]
[0 sec: 119392 usec]	[5] -1	0	0x00000000 - 0x00000000 (0x1)[0 sec: 119405 usec] I[0 sec: 119416 usec]X[0 sec: 119426 usec][B][0 sec: 119437 usec]
[0 sec: 119457 usec](II) LoadModule: "extmod"[0 sec: 119622 usec]
[0 sec: 128834 usec](II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[0 sec: 129070 usec](II) Module extmod: vendor="X.Org Foundation"
[0 sec: 129087 usec]	compiled for 1.5.99[0 sec: 129100 usec].902[0 sec: 129112 usec], module version = 1.0.0
[0 sec: 129125 usec]	Module class: X.Org Server Extension
[0 sec: 129138 usec]	ABI class: X.Org Server Extension, version 2.0
[0 sec: 129154 usec](II) Loading extension MIT-SCREEN-SAVER
[0 sec: 129169 usec](II) Loading extension XFree86-VidModeExtension
[0 sec: 129182 usec](II) Loading extension XFree86-DGA
[0 sec: 129198 usec](II) Loading extension DPMS
[0 sec: 129212 usec](II) Loading extension XVideo
[0 sec: 129228 usec](II) Loading extension XVideo-MotionCompensation
[0 sec: 129242 usec](II) Loading extension X-Resource
[0 sec: 129257 usec](II) LoadModule: "dbe"[0 sec: 129275 usec]
[0 sec: 129616 usec](II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[0 sec: 129720 usec](II) Module dbe: vendor="X.Org Foundation"
[0 sec: 129735 usec]	compiled for 1.5.99[0 sec: 129747 usec].902[0 sec: 129759 usec], module version = 1.0.0
[0 sec: 129771 usec]	Module class: X.Org Server Extension
[0 sec: 129783 usec]	ABI class: X.Org Server Extension, version 2.0
[0 sec: 129799 usec](II) Loading extension DOUBLE-BUFFER
[0 sec: 129813 usec](II) LoadModule: "glx"[0 sec: 129829 usec]
[0 sec: 130168 usec](II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[0 sec: 685031 usec](II) Module glx: vendor="NVIDIA Corporation"
[0 sec: 685074 usec]	compiled for 4.0.2[0 sec: 685087 usec], module version = 1.0.0
[0 sec: 685101 usec]	Module class: X.Org Server Extension
[0 sec: 685115 usec](II) NVIDIA GLX Module  180.27  Tue Jan 27 12:46:22 PST 2009
[0 sec: 685135 usec](II) Loading extension GLX
[0 sec: 685151 usec](II) LoadModule: "record"[0 sec: 685175 usec]
[0 sec: 685571 usec](II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[0 sec: 685705 usec](II) Module record: vendor="X.Org Foundation"
[0 sec: 685721 usec]	compiled for 1.5.99[0 sec: 685734 usec].902[0 sec: 685745 usec], module version = 1.13.0
[0 sec: 685757 usec]	Module class: X.Org Server Extension
[0 sec: 685770 usec]	ABI class: X.Org Server Extension, version 2.0
[0 sec: 685785 usec](II) Loading extension RECORD
[0 sec: 685800 usec](II) LoadModule: "dri"[0 sec: 685816 usec]
[0 sec: 686154 usec](II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[0 sec: 704011 usec](II) Module dri: vendor="X.Org Foundation"
[0 sec: 704035 usec]	compiled for 1.5.99[0 sec: 704048 usec].902[0 sec: 704060 usec], module version = 1.0.0
[0 sec: 704074 usec]	ABI class: X.Org Server Extension, version 2.0
[0 sec: 704093 usec](II) Loading extension XFree86-DRI
[0 sec: 704116 usec](II) LoadModule: "dri2"[0 sec: 704133 usec]
[0 sec: 704476 usec](II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[0 sec: 712518 usec](II) Module dri2: vendor="X.Org Foundation"
[0 sec: 712539 usec]	compiled for 1.5.99[0 sec: 712552 usec].902[0 sec: 712572 usec], module version = 1.0.0
[0 sec: 712585 usec]	ABI class: X.Org Server Extension, version 2.0
[0 sec: 712601 usec](II) Loading extension DRI2
[0 sec: 712644 usec](II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
[0 sec: 713604 usec](II) No matches found for this device in /usr/share/xserver-xorg/pci
[0 sec: 713623 usec](==) Registering 'vesa' as fallback
[0 sec: 713644 usec](==) Matched vesa for the autoconfigured driver
[0 sec: 713659 usec](==) Assigned the driver to the xf86ConfigLayout
[0 sec: 713675 usec](II) LoadModule: "vesa"[0 sec: 713691 usec]
[0 sec: 713940 usec](II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
[0 sec: 723453 usec](II) Module vesa: vendor="X.Org Foundation"
[0 sec: 723475 usec]	compiled for 1.5.99[0 sec: 723488 usec].902[0 sec: 723499 usec], module version = 1.3.0
[0 sec: 723513 usec]	Module class: X.Org Video Driver
[0 sec: 723525 usec]	ABI class: X.Org Video Driver, version 5.0
[0 sec: 723546 usec](II) VESA: driver for VESA chipsets:[0 sec: 723558 usec] [0 sec: 723569 usec]vesa[0 sec: 723581 usec]
[0 sec: 724966 usec](II) Primary Device is: PCI 04@00:00:0
[0 sec: 725004 usec](II) resource ranges after probing:
[0 sec: 725017 usec]	[0] -1	0	0xffffffff - 0xffffffff (0x1)[0 sec: 725031 usec] M[0 sec: 725043 usec]X[0 sec: 725055 usec][B][0 sec: 725067 usec]
[0 sec: 725078 usec]	[1] -1	0	0x000f0000 - 0x000fffff (0x10000)[0 sec: 725091 usec] M[0 sec: 725102 usec]X[0 sec: 725113 usec][B][0 sec: 725124 usec]
[0 sec: 725135 usec]	[2] -1	0	0x000c0000 - 0x000effff (0x30000)[0 sec: 725147 usec] M[0 sec: 725159 usec]X[0 sec: 725170 usec][B][0 sec: 725181 usec]
[0 sec: 725192 usec]	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000)[0 sec: 725205 usec] M[0 sec: 725216 usec]X[0 sec: 725227 usec][B][0 sec: 725238 usec]
[0 sec: 725249 usec]	[4] -1	0	0x0000ffff - 0x0000ffff (0x1)[0 sec: 725262 usec] I[0 sec: 725273 usec]X[0 sec: 725284 usec][B][0 sec: 725295 usec]
[0 sec: 725306 usec]	[5] -1	0	0x00000000 - 0x00000000 (0x1)[0 sec: 725318 usec] I[0 sec: 725329 usec]X[0 sec: 725340 usec][B][0 sec: 725351 usec]
[0 sec: 750717 usec](II) Loading sub module "vbe"
[0 sec: 750738 usec](II) LoadModule: "vbe"[0 sec: 750756 usec]
[0 sec: 750847 usec](II) Loading /usr/lib/xorg/modules//libvbe.so
[0 sec: 753511 usec](II) Module vbe: vendor="X.Org Foundation"
[0 sec: 753535 usec]	compiled for 1.5.99[0 sec: 753547 usec].902[0 sec: 753562 usec], module version = 1.1.0
[0 sec: 753574 usec]	ABI class: X.Org Video Driver, version 5.0
[0 sec: 753598 usec](II) Loading sub module "int10"
[0 sec: 753612 usec](II) LoadModule: "int10"[0 sec: 753630 usec]
[0 sec: 753728 usec](II) Loading /usr/lib/xorg/modules//libint10.so
[0 sec: 760260 usec](II) Module int10: vendor="X.Org Foundation"
[0 sec: 760281 usec]	compiled for 1.5.99[0 sec: 760294 usec].902[0 sec: 760308 usec], module version = 1.0.0
[0 sec: 760321 usec]	ABI class: X.Org Video Driver, version 5.0
[0 sec: 760340 usec](II) VESA(0): initializing int10
[0 sec: 768949 usec](II) VESA(0): Primary V_BIOS segment is: 0xc000
[0 sec: 803528 usec](II) VESA(0): VESA BIOS detected
[0 sec: 803556 usec](II) VESA(0): VESA VBE Version 3.0
[0 sec: 803571 usec](II) VESA(0): VESA VBE Total Mem: 262144 kB
[0 sec: 803589 usec](II) VESA(0): VESA VBE OEM: NVIDIA
[0 sec: 803604 usec](II) VESA(0): VESA VBE OEM Software Rev: 5.113
[0 sec: 803618 usec](II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[0 sec: 803632 usec](II) VESA(0): VESA VBE OEM Product: G71 Board - p602h0  
[0 sec: 803646 usec](II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[0 sec: 909262 usec](II) VESA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[0 sec: 909286 usec](==) VESA(0): Depth 24, [0 sec: 909300 usec](--) framebuffer bpp 32
[0 sec: 909316 usec](==) VESA(0): RGB weight 888
[0 sec: 909333 usec](==) VESA(0): Default visual is TrueColor
[0 sec: 909349 usec](==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[0 sec: 909382 usec](II) Loading sub module "ddc"
[0 sec: 909395 usec](II) LoadModule: "ddc"[0 sec: 909412 usec]
[0 sec: 909437 usec](II) Module "ddc" already built-in
[0 sec: 917512 usec](II) VESA(0): VESA VBE DDC supported
[0 sec: 917530 usec](II) VESA(0): VESA VBE DDC Level 2
[0 sec: 917545 usec](II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[1 sec: 095502 usec](II) VESA(0): VESA VBE DDC read successfully
[1 sec: 101861 usec](II) VESA(0): Manufacturer: DEL  Model: a010  Serial#: 842224211
[1 sec: 101881 usec](II) VESA(0): Year: 2005  Week: 45
[1 sec: 101896 usec](II) VESA(0): EDID Version: 1.3
[1 sec: 101911 usec](II) VESA(0): Digital Display Input
[1 sec: 101927 usec](II) VESA(0): Max Image Size [cm]: [1 sec: 101939 usec]horiz.: 52  [1 sec: 101951 usec]vert.: 33
[1 sec: 101965 usec](II) VESA(0): Gamma: 2.20
[1 sec: 101982 usec](II) VESA(0): DPMS capabilities:[1 sec: 101994 usec] StandBy[1 sec: 102006 usec] Suspend[1 sec: 102017 usec] Off[1 sec: 102029 usec]
[1 sec: 102042 usec](II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[1 sec: 102056 usec](II) VESA(0): Default color space is primary color space
[1 sec: 102070 usec](II) VESA(0): First detailed timing is preferred mode
[1 sec: 102085 usec](II) VESA(0): redX: 0.640 redY: 0.330   [1 sec: 102100 usec]greenX: 0.300 greenY: 0.607
[1 sec: 102117 usec](II) VESA(0): blueX: 0.149 blueY: 0.060   [1 sec: 102131 usec]whiteX: 0.312 whiteY: 0.328
[1 sec: 102148 usec](II) VESA(0): Supported VESA Video Modes:
[1 sec: 102161 usec](II) VESA(0): 720x400@70Hz
[1 sec: 102174 usec](II) VESA(0): 640x480@60Hz
[1 sec: 102187 usec](II) VESA(0): 640x480@75Hz
[1 sec: 102200 usec](II) VESA(0): 800x600@60Hz
[1 sec: 102213 usec](II) VESA(0): 800x600@75Hz
[1 sec: 102226 usec](II) VESA(0): 1024x768@60Hz
[1 sec: 102240 usec](II) VESA(0): 1024x768@75Hz
[1 sec: 102253 usec](II) VESA(0): 1280x1024@75Hz
[1 sec: 102266 usec](II) VESA(0): Manufacturer's mask: 0
[1 sec: 102280 usec](II) VESA(0): Supported Future Video Modes:
[1 sec: 102295 usec](II) VESA(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[1 sec: 102312 usec](II) VESA(0): #1: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[1 sec: 102328 usec](II) VESA(0): #2: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[1 sec: 102345 usec](II) VESA(0): #3: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[1 sec: 102361 usec](II) VESA(0): Supported additional Video Mode:
[1 sec: 102375 usec](II) VESA(0): clock: 154.0 MHz   [1 sec: 102392 usec]Image Size:  519 x 324 mm
[1 sec: 102408 usec](II) VESA(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 [1 sec: 102422 usec]h_border: 0
[1 sec: 102438 usec](II) VESA(0): v_active: 1200  v_sync: 1203  v_sync_end 1209 v_blanking: 1235 [1 sec: 102451 usec]v_border: 0
[1 sec: 102465 usec](II) VESA(0): Serial No: T61335B123RS
[1 sec: 102479 usec](II) VESA(0): Monitor name: DELL 2405FPW
[1 sec: 102494 usec](II) VESA(0): Ranges: V min: 56 V max: 76 Hz, H min: 30 H max: 81 kHz,[1 sec: 102508 usec] PixClock max 170 MHz
[1 sec: 102523 usec](II) VESA(0): EDID (in hex):
[1 sec: 102542 usec](II) VESA(0): 	00ffffffffffff0010ac10a053523332
[1 sec: 102561 usec](II) VESA(0): 	2d0f010380342178eeee50a3544c9b26
[1 sec: 102580 usec](II) VESA(0): 	0f5054a54b008180a940714fb3000101
[1 sec: 102599 usec](II) VESA(0): 	010101010101283c80a070b023403020
[1 sec: 102619 usec](II) VESA(0): 	360007442100001a000000ff00543631
[1 sec: 102637 usec](II) VESA(0): 	33333542313233525320000000fc0044
[1 sec: 102657 usec](II) VESA(0): 	454c4c20323430354650570a000000fd
[1 sec: 102676 usec](II) VESA(0): 	00384c1e5111000a20202020202000fc
[1 sec: 102700 usec](II) VESA(0): EDID vendor "DEL", prod id 40976
[1 sec: 102747 usec](II) VESA(0): Using EDID range info for horizontal sync
[1 sec: 102761 usec](II) VESA(0): Using EDID range info for vertical refresh
[1 sec: 102774 usec](II) VESA(0): Printing DDC gathered Modelines:
[1 sec: 102790 usec](II) VESA(0): Modeline "1920x1200"x0.0  154.00  1920 1968 2000 2080  1200 1203 1209 1235 +hsync -vsync (74.0 kHz)
[1 sec: 102815 usec](II) VESA(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[1 sec: 102839 usec](II) VESA(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[1 sec: 102872 usec](II) VESA(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[1 sec: 102896 usec](II) VESA(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[1 sec: 102919 usec](II) VESA(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[1 sec: 102943 usec](II) VESA(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[1 sec: 102966 usec](II) VESA(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[1 sec: 102989 usec](II) VESA(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[1 sec: 103012 usec](II) VESA(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[1 sec: 103035 usec](II) VESA(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[1 sec: 103058 usec](II) VESA(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[1 sec: 103081 usec](II) VESA(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[1 sec: 103108 usec](II) VESA(0): Searching for matching VESA mode(s):
[1 sec: 105624 usec]Mode: 100 (640x400)
[1 sec: 105644 usec]	ModeAttributes: 0x39f
[1 sec: 105656 usec]	WinAAttributes: 0x7
[1 sec: 105667 usec]	WinBAttributes: 0x0
[1 sec: 105679 usec]	WinGranularity: 64
[1 sec: 105690 usec]	WinSize: 64
[1 sec: 105702 usec]	WinASegment: 0xa000
[1 sec: 105713 usec]	WinBSegment: 0x0
[1 sec: 105725 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 105736 usec]	BytesPerScanline: 640
[1 sec: 105748 usec]	XResolution: 640
[1 sec: 105759 usec]	YResolution: 400
[1 sec: 105770 usec]	XCharSize: 8
[1 sec: 105781 usec]	YCharSize: 16
[1 sec: 105792 usec]	NumberOfPlanes: 1
[1 sec: 105804 usec]	BitsPerPixel: 8
[1 sec: 105815 usec]	NumberOfBanks: 1
[1 sec: 105826 usec]	MemoryModel: 4
[1 sec: 105837 usec]	BankSize: 0
[1 sec: 105848 usec]	NumberOfImages: 14
[1 sec: 105860 usec]	RedMaskSize: 0
[1 sec: 105871 usec]	RedFieldPosition: 0
[1 sec: 105882 usec]	GreenMaskSize: 0
[1 sec: 105893 usec]	GreenFieldPosition: 0
[1 sec: 105905 usec]	BlueMaskSize: 0
[1 sec: 105916 usec]	BlueFieldPosition: 0
[1 sec: 105927 usec]	RsvdMaskSize: 0
[1 sec: 105939 usec]	RsvdFieldPosition: 0
[1 sec: 105950 usec]	DirectColorModeInfo: 0
[1 sec: 105962 usec]	PhysBasePtr: 0xb0000000
[1 sec: 105973 usec]	LinBytesPerScanLine: 640
[1 sec: 105984 usec]	BnkNumberOfImagePages: 14
[1 sec: 105996 usec]	LinNumberOfImagePages: 14
[1 sec: 106007 usec]	LinRedMaskSize: 0
[1 sec: 106018 usec]	LinRedFieldPosition: 0
[1 sec: 106030 usec]	LinGreenMaskSize: 0
[1 sec: 106041 usec]	LinGreenFieldPosition: 0
[1 sec: 106052 usec]	LinBlueMaskSize: 0
[1 sec: 106063 usec]	LinBlueFieldPosition: 0
[1 sec: 106074 usec]	LinRsvdMaskSize: 0
[1 sec: 106085 usec]	LinRsvdFieldPosition: 0
[1 sec: 106097 usec]	MaxPixelClock: 229500000
[1 sec: 108719 usec]Mode: 101 (640x480)
[1 sec: 108735 usec]	ModeAttributes: 0x39f
[1 sec: 108747 usec]	WinAAttributes: 0x7
[1 sec: 108759 usec]	WinBAttributes: 0x0
[1 sec: 108771 usec]	WinGranularity: 64
[1 sec: 108782 usec]	WinSize: 64
[1 sec: 108794 usec]	WinASegment: 0xa000
[1 sec: 108806 usec]	WinBSegment: 0x0
[1 sec: 108818 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 108829 usec]	BytesPerScanline: 640
[1 sec: 108841 usec]	XResolution: 640
[1 sec: 108852 usec]	YResolution: 480
[1 sec: 108864 usec]	XCharSize: 8
[1 sec: 108887 usec]	YCharSize: 16
[1 sec: 108898 usec]	NumberOfPlanes: 1
[1 sec: 108909 usec]	BitsPerPixel: 8
[1 sec: 108920 usec]	NumberOfBanks: 1
[1 sec: 108931 usec]	MemoryModel: 4
[1 sec: 108942 usec]	BankSize: 0
[1 sec: 108953 usec]	NumberOfImages: 10
[1 sec: 108965 usec]	RedMaskSize: 0
[1 sec: 108976 usec]	RedFieldPosition: 0
[1 sec: 108987 usec]	GreenMaskSize: 0
[1 sec: 108998 usec]	GreenFieldPosition: 0
[1 sec: 109009 usec]	BlueMaskSize: 0
[1 sec: 109029 usec]	BlueFieldPosition: 0
[1 sec: 109041 usec]	RsvdMaskSize: 0
[1 sec: 109052 usec]	RsvdFieldPosition: 0
[1 sec: 109064 usec]	DirectColorModeInfo: 0
[1 sec: 109075 usec]	PhysBasePtr: 0xb0000000
[1 sec: 109086 usec]	LinBytesPerScanLine: 640
[1 sec: 109098 usec]	BnkNumberOfImagePages: 10
[1 sec: 109109 usec]	LinNumberOfImagePages: 10
[1 sec: 109120 usec]	LinRedMaskSize: 0
[1 sec: 109131 usec]	LinRedFieldPosition: 0
[1 sec: 109142 usec]	LinGreenMaskSize: 0
[1 sec: 109153 usec]	LinGreenFieldPosition: 0
[1 sec: 109165 usec]	LinBlueMaskSize: 0
[1 sec: 109176 usec]	LinBlueFieldPosition: 0
[1 sec: 109187 usec]	LinRsvdMaskSize: 0
[1 sec: 109198 usec]	LinRsvdFieldPosition: 0
[1 sec: 109209 usec]	MaxPixelClock: 229500000
[1 sec: 111539 usec]Mode: 102 (800x600)
[1 sec: 111556 usec]	ModeAttributes: 0x31f
[1 sec: 111568 usec]	WinAAttributes: 0x7
[1 sec: 111579 usec]	WinBAttributes: 0x0
[1 sec: 111591 usec]	WinGranularity: 64
[1 sec: 111602 usec]	WinSize: 64
[1 sec: 111613 usec]	WinASegment: 0xa000
[1 sec: 111624 usec]	WinBSegment: 0x0
[1 sec: 111637 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 111648 usec]	BytesPerScanline: 100
[1 sec: 111660 usec]	XResolution: 800
[1 sec: 111671 usec]	YResolution: 600
[1 sec: 111682 usec]	XCharSize: 8
[1 sec: 111694 usec]	YCharSize: 16
[1 sec: 111705 usec]	NumberOfPlanes: 4
[1 sec: 111716 usec]	BitsPerPixel: 4
[1 sec: 111727 usec]	NumberOfBanks: 1
[1 sec: 111738 usec]	MemoryModel: 3
[1 sec: 111749 usec]	BankSize: 0
[1 sec: 111760 usec]	NumberOfImages: 14
[1 sec: 111771 usec]	RedMaskSize: 0
[1 sec: 111782 usec]	RedFieldPosition: 0
[1 sec: 111793 usec]	GreenMaskSize: 0
[1 sec: 111805 usec]	GreenFieldPosition: 0
[1 sec: 111816 usec]	BlueMaskSize: 0
[1 sec: 111827 usec]	BlueFieldPosition: 0
[1 sec: 111838 usec]	RsvdMaskSize: 0
[1 sec: 111849 usec]	RsvdFieldPosition: 0
[1 sec: 111861 usec]	DirectColorModeInfo: 0
[1 sec: 111872 usec]	PhysBasePtr: 0x0
[1 sec: 111883 usec]	LinBytesPerScanLine: 100
[1 sec: 111895 usec]	BnkNumberOfImagePages: 14
[1 sec: 111906 usec]	LinNumberOfImagePages: 14
[1 sec: 111917 usec]	LinRedMaskSize: 0
[1 sec: 111929 usec]	LinRedFieldPosition: 0
[1 sec: 111940 usec]	LinGreenMaskSize: 0
[1 sec: 111951 usec]	LinGreenFieldPosition: 0
[1 sec: 111963 usec]	LinBlueMaskSize: 0
[1 sec: 111974 usec]	LinBlueFieldPosition: 0
[1 sec: 111985 usec]	LinRsvdMaskSize: 0
[1 sec: 111996 usec]	LinRsvdFieldPosition: 0
[1 sec: 112007 usec]	MaxPixelClock: 108500000
[1 sec: 114580 usec]Mode: 103 (800x600)
[1 sec: 114598 usec]	ModeAttributes: 0x39f
[1 sec: 114610 usec]	WinAAttributes: 0x7
[1 sec: 114621 usec]	WinBAttributes: 0x0
[1 sec: 114633 usec]	WinGranularity: 64
[1 sec: 114644 usec]	WinSize: 64
[1 sec: 114656 usec]	WinASegment: 0xa000
[1 sec: 114668 usec]	WinBSegment: 0x0
[1 sec: 114679 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 114691 usec]	BytesPerScanline: 800
[1 sec: 114702 usec]	XResolution: 800
[1 sec: 114714 usec]	YResolution: 600
[1 sec: 114726 usec]	XCharSize: 8
[1 sec: 114737 usec]	YCharSize: 16
[1 sec: 114749 usec]	NumberOfPlanes: 1
[1 sec: 114760 usec]	BitsPerPixel: 8
[1 sec: 114772 usec]	NumberOfBanks: 1
[1 sec: 114783 usec]	MemoryModel: 4
[1 sec: 114795 usec]	BankSize: 0
[1 sec: 114806 usec]	NumberOfImages: 6
[1 sec: 114818 usec]	RedMaskSize: 0
[1 sec: 114830 usec]	RedFieldPosition: 0
[1 sec: 114841 usec]	GreenMaskSize: 0
[1 sec: 114852 usec]	GreenFieldPosition: 0
[1 sec: 114864 usec]	BlueMaskSize: 0
[1 sec: 114876 usec]	BlueFieldPosition: 0
[1 sec: 114887 usec]	RsvdMaskSize: 0
[1 sec: 114899 usec]	RsvdFieldPosition: 0
[1 sec: 114911 usec]	DirectColorModeInfo: 0
[1 sec: 114923 usec]	PhysBasePtr: 0xb0000000
[1 sec: 114935 usec]	LinBytesPerScanLine: 800
[1 sec: 114947 usec]	BnkNumberOfImagePages: 6
[1 sec: 114959 usec]	LinNumberOfImagePages: 6
[1 sec: 114971 usec]	LinRedMaskSize: 0
[1 sec: 114983 usec]	LinRedFieldPosition: 0
[1 sec: 114994 usec]	LinGreenMaskSize: 0
[1 sec: 115006 usec]	LinGreenFieldPosition: 0
[1 sec: 115018 usec]	LinBlueMaskSize: 0
[1 sec: 115030 usec]	LinBlueFieldPosition: 0
[1 sec: 115042 usec]	LinRsvdMaskSize: 0
[1 sec: 115054 usec]	LinRsvdFieldPosition: 0
[1 sec: 115076 usec]	MaxPixelClock: 229500000
[1 sec: 117658 usec]Mode: 104 (1024x768)
[1 sec: 117677 usec]	ModeAttributes: 0x31f
[1 sec: 117688 usec]	WinAAttributes: 0x7
[1 sec: 117700 usec]	WinBAttributes: 0x0
[1 sec: 117711 usec]	WinGranularity: 64
[1 sec: 117722 usec]	WinSize: 64
[1 sec: 117734 usec]	WinASegment: 0xa000
[1 sec: 117745 usec]	WinBSegment: 0x0
[1 sec: 117757 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 117769 usec]	BytesPerScanline: 128
[1 sec: 117780 usec]	XResolution: 1024
[1 sec: 117792 usec]	YResolution: 768
[1 sec: 117803 usec]	XCharSize: 8
[1 sec: 117814 usec]	YCharSize: 16
[1 sec: 117825 usec]	NumberOfPlanes: 4
[1 sec: 117837 usec]	BitsPerPixel: 4
[1 sec: 117848 usec]	NumberOfBanks: 1
[1 sec: 117859 usec]	MemoryModel: 3
[1 sec: 117870 usec]	BankSize: 0
[1 sec: 117881 usec]	NumberOfImages: 6
[1 sec: 117892 usec]	RedMaskSize: 0
[1 sec: 117903 usec]	RedFieldPosition: 0
[1 sec: 117914 usec]	GreenMaskSize: 0
[1 sec: 117926 usec]	GreenFieldPosition: 0
[1 sec: 117937 usec]	BlueMaskSize: 0
[1 sec: 117948 usec]	BlueFieldPosition: 0
[1 sec: 117959 usec]	RsvdMaskSize: 0
[1 sec: 117970 usec]	RsvdFieldPosition: 0
[1 sec: 117982 usec]	DirectColorModeInfo: 0
[1 sec: 117993 usec]	PhysBasePtr: 0x0
[1 sec: 118004 usec]	LinBytesPerScanLine: 128
[1 sec: 118016 usec]	BnkNumberOfImagePages: 6
[1 sec: 118027 usec]	LinNumberOfImagePages: 6
[1 sec: 118038 usec]	LinRedMaskSize: 0
[1 sec: 118049 usec]	LinRedFieldPosition: 0
[1 sec: 118060 usec]	LinGreenMaskSize: 0
[1 sec: 118071 usec]	LinGreenFieldPosition: 0
[1 sec: 118082 usec]	LinBlueMaskSize: 0
[1 sec: 118093 usec]	LinBlueFieldPosition: 0
[1 sec: 118104 usec]	LinRsvdMaskSize: 0
[1 sec: 118115 usec]	LinRsvdFieldPosition: 0
[1 sec: 118127 usec]	MaxPixelClock: 108500000
[1 sec: 120729 usec]Mode: 105 (1024x768)
[1 sec: 120745 usec]	ModeAttributes: 0x39f
[1 sec: 120757 usec]	WinAAttributes: 0x7
[1 sec: 120768 usec]	WinBAttributes: 0x0
[1 sec: 120780 usec]	WinGranularity: 64
[1 sec: 120791 usec]	WinSize: 64
[1 sec: 120803 usec]	WinASegment: 0xa000
[1 sec: 120814 usec]	WinBSegment: 0x0
[1 sec: 120826 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 120838 usec]	BytesPerScanline: 1024
[1 sec: 120849 usec]	XResolution: 1024
[1 sec: 120861 usec]	YResolution: 768
[1 sec: 120882 usec]	XCharSize: 8
[1 sec: 120894 usec]	YCharSize: 16
[1 sec: 120905 usec]	NumberOfPlanes: 1
[1 sec: 120916 usec]	BitsPerPixel: 8
[1 sec: 120927 usec]	NumberOfBanks: 1
[1 sec: 120939 usec]	MemoryModel: 4
[1 sec: 120950 usec]	BankSize: 0
[1 sec: 120961 usec]	NumberOfImages: 3
[1 sec: 120972 usec]	RedMaskSize: 0
[1 sec: 120983 usec]	RedFieldPosition: 0
[1 sec: 120995 usec]	GreenMaskSize: 0
[1 sec: 121006 usec]	GreenFieldPosition: 0
[1 sec: 121017 usec]	BlueMaskSize: 0
[1 sec: 121028 usec]	BlueFieldPosition: 0
[1 sec: 121040 usec]	RsvdMaskSize: 0
[1 sec: 121051 usec]	RsvdFieldPosition: 0
[1 sec: 121063 usec]	DirectColorModeInfo: 0
[1 sec: 121074 usec]	PhysBasePtr: 0xb0000000
[1 sec: 121086 usec]	LinBytesPerScanLine: 1024
[1 sec: 121097 usec]	BnkNumberOfImagePages: 3
[1 sec: 121109 usec]	LinNumberOfImagePages: 3
[1 sec: 121120 usec]	LinRedMaskSize: 0
[1 sec: 121132 usec]	LinRedFieldPosition: 0
[1 sec: 121143 usec]	LinGreenMaskSize: 0
[1 sec: 121154 usec]	LinGreenFieldPosition: 0
[1 sec: 121166 usec]	LinBlueMaskSize: 0
[1 sec: 121177 usec]	LinBlueFieldPosition: 0
[1 sec: 121188 usec]	LinRsvdMaskSize: 0
[1 sec: 121200 usec]	LinRsvdFieldPosition: 0
[1 sec: 121211 usec]	MaxPixelClock: 229500000
[1 sec: 123736 usec]Mode: 106 (1280x1024)
[1 sec: 123752 usec]	ModeAttributes: 0x31f
[1 sec: 123764 usec]	WinAAttributes: 0x7
[1 sec: 123776 usec]	WinBAttributes: 0x0
[1 sec: 123788 usec]	WinGranularity: 64
[1 sec: 123799 usec]	WinSize: 64
[1 sec: 123811 usec]	WinASegment: 0xa000
[1 sec: 123823 usec]	WinBSegment: 0x0
[1 sec: 123834 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 123846 usec]	BytesPerScanline: 160
[1 sec: 123858 usec]	XResolution: 1280
[1 sec: 123870 usec]	YResolution: 1024
[1 sec: 123881 usec]	XCharSize: 8
[1 sec: 123893 usec]	YCharSize: 16
[1 sec: 123904 usec]	NumberOfPlanes: 4
[1 sec: 123916 usec]	BitsPerPixel: 4
[1 sec: 123927 usec]	NumberOfBanks: 1
[1 sec: 123949 usec]	MemoryModel: 3
[1 sec: 123961 usec]	BankSize: 0
[1 sec: 123972 usec]	NumberOfImages: 3
[1 sec: 123983 usec]	RedMaskSize: 0
[1 sec: 123994 usec]	RedFieldPosition: 0
[1 sec: 124005 usec]	GreenMaskSize: 0
[1 sec: 124016 usec]	GreenFieldPosition: 0
[1 sec: 124028 usec]	BlueMaskSize: 0
[1 sec: 124039 usec]	BlueFieldPosition: 0
[1 sec: 124050 usec]	RsvdMaskSize: 0
[1 sec: 124061 usec]	RsvdFieldPosition: 0
[1 sec: 124073 usec]	DirectColorModeInfo: 0
[1 sec: 124084 usec]	PhysBasePtr: 0x0
[1 sec: 124095 usec]	LinBytesPerScanLine: 160
[1 sec: 124107 usec]	BnkNumberOfImagePages: 3
[1 sec: 124118 usec]	LinNumberOfImagePages: 3
[1 sec: 124129 usec]	LinRedMaskSize: 0
[1 sec: 124140 usec]	LinRedFieldPosition: 0
[1 sec: 124152 usec]	LinGreenMaskSize: 0
[1 sec: 124163 usec]	LinGreenFieldPosition: 0
[1 sec: 124174 usec]	LinBlueMaskSize: 0
[1 sec: 124185 usec]	LinBlueFieldPosition: 0
[1 sec: 124196 usec]	LinRsvdMaskSize: 0
[1 sec: 124207 usec]	LinRsvdFieldPosition: 0
[1 sec: 124219 usec]	MaxPixelClock: 108500000
[1 sec: 126869 usec]Mode: 107 (1280x1024)
[1 sec: 126888 usec]	ModeAttributes: 0x39f
[1 sec: 126899 usec]	WinAAttributes: 0x7
[1 sec: 126911 usec]	WinBAttributes: 0x0
[1 sec: 126922 usec]	WinGranularity: 64
[1 sec: 126934 usec]	WinSize: 64
[1 sec: 126945 usec]	WinASegment: 0xa000
[1 sec: 126957 usec]	WinBSegment: 0x0
[1 sec: 126969 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 126980 usec]	BytesPerScanline: 1280
[1 sec: 126992 usec]	XResolution: 1280
[1 sec: 127004 usec]	YResolution: 1024
[1 sec: 127015 usec]	XCharSize: 8
[1 sec: 127027 usec]	YCharSize: 16
[1 sec: 127038 usec]	NumberOfPlanes: 1
[1 sec: 127050 usec]	BitsPerPixel: 8
[1 sec: 127061 usec]	NumberOfBanks: 1
[1 sec: 127073 usec]	MemoryModel: 4
[1 sec: 127084 usec]	BankSize: 0
[1 sec: 127096 usec]	NumberOfImages: 1
[1 sec: 127108 usec]	RedMaskSize: 0
[1 sec: 127119 usec]	RedFieldPosition: 0
[1 sec: 127130 usec]	GreenMaskSize: 0
[1 sec: 127142 usec]	GreenFieldPosition: 0
[1 sec: 127154 usec]	BlueMaskSize: 0
[1 sec: 127165 usec]	BlueFieldPosition: 0
[1 sec: 127177 usec]	RsvdMaskSize: 0
[1 sec: 127188 usec]	RsvdFieldPosition: 0
[1 sec: 127200 usec]	DirectColorModeInfo: 0
[1 sec: 127212 usec]	PhysBasePtr: 0xb0000000
[1 sec: 127224 usec]	LinBytesPerScanLine: 1280
[1 sec: 127236 usec]	BnkNumberOfImagePages: 1
[1 sec: 127248 usec]	LinNumberOfImagePages: 1
[1 sec: 127260 usec]	LinRedMaskSize: 0
[1 sec: 127272 usec]	LinRedFieldPosition: 0
[1 sec: 127284 usec]	LinGreenMaskSize: 0
[1 sec: 127296 usec]	LinGreenFieldPosition: 0
[1 sec: 127308 usec]	LinBlueMaskSize: 0
[1 sec: 127319 usec]	LinBlueFieldPosition: 0
[1 sec: 127331 usec]	LinRsvdMaskSize: 0
[1 sec: 127343 usec]	LinRsvdFieldPosition: 0
[1 sec: 127355 usec]	MaxPixelClock: 229500000
[1 sec: 130100 usec]Mode: 10e (320x200)
[1 sec: 130119 usec]	ModeAttributes: 0x39f
[1 sec: 130130 usec]	WinAAttributes: 0x7
[1 sec: 130142 usec]	WinBAttributes: 0x0
[1 sec: 130153 usec]	WinGranularity: 64
[1 sec: 130164 usec]	WinSize: 64
[1 sec: 130176 usec]	WinASegment: 0xa000
[1 sec: 130187 usec]	WinBSegment: 0x0
[1 sec: 130200 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 130211 usec]	BytesPerScanline: 640
[1 sec: 130223 usec]	XResolution: 320
[1 sec: 130234 usec]	YResolution: 200
[1 sec: 130245 usec]	XCharSize: 8
[1 sec: 130257 usec]	YCharSize: 8
[1 sec: 130268 usec]	NumberOfPlanes: 1
[1 sec: 130279 usec]	BitsPerPixel: 16
[1 sec: 130290 usec]	NumberOfBanks: 1
[1 sec: 130301 usec]	MemoryModel: 6
[1 sec: 130312 usec]	BankSize: 0
[1 sec: 130323 usec]	NumberOfImages: 30
[1 sec: 130334 usec]	RedMaskSize: 5
[1 sec: 130345 usec]	RedFieldPosition: 11
[1 sec: 130356 usec]	GreenMaskSize: 6
[1 sec: 130368 usec]	GreenFieldPosition: 5
[1 sec: 130379 usec]	BlueMaskSize: 5
[1 sec: 130390 usec]	BlueFieldPosition: 0
[1 sec: 130401 usec]	RsvdMaskSize: 0
[1 sec: 130412 usec]	RsvdFieldPosition: 0
[1 sec: 130424 usec]	DirectColorModeInfo: 0
[1 sec: 130435 usec]	PhysBasePtr: 0xb0000000
[1 sec: 130446 usec]	LinBytesPerScanLine: 640
[1 sec: 130458 usec]	BnkNumberOfImagePages: 30
[1 sec: 130469 usec]	LinNumberOfImagePages: 30
[1 sec: 130480 usec]	LinRedMaskSize: 5
[1 sec: 130502 usec]	LinRedFieldPosition: 11
[1 sec: 130513 usec]	LinGreenMaskSize: 6
[1 sec: 130524 usec]	LinGreenFieldPosition: 5
[1 sec: 130535 usec]	LinBlueMaskSize: 5
[1 sec: 130546 usec]	LinBlueFieldPosition: 0
[1 sec: 130557 usec]	LinRsvdMaskSize: 0
[1 sec: 130569 usec]	LinRsvdFieldPosition: 0
[1 sec: 130580 usec]	MaxPixelClock: 229500000
[1 sec: 133444 usec]*[1 sec: 133461 usec]Mode: 10f (320x200)
[1 sec: 133474 usec]	ModeAttributes: 0x39f
[1 sec: 133485 usec]	WinAAttributes: 0x7
[1 sec: 133497 usec]	WinBAttributes: 0x0
[1 sec: 133508 usec]	WinGranularity: 64
[1 sec: 133520 usec]	WinSize: 64
[1 sec: 133532 usec]	WinASegment: 0xa000
[1 sec: 133544 usec]	WinBSegment: 0x0
[1 sec: 133555 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 133567 usec]	BytesPerScanline: 1280
[1 sec: 133579 usec]	XResolution: 320
[1 sec: 133590 usec]	YResolution: 200
[1 sec: 133602 usec]	XCharSize: 8
[1 sec: 133614 usec]	YCharSize: 8
[1 sec: 133625 usec]	NumberOfPlanes: 1
[1 sec: 133637 usec]	BitsPerPixel: 32
[1 sec: 133648 usec]	NumberOfBanks: 1
[1 sec: 133660 usec]	MemoryModel: 6
[1 sec: 133671 usec]	BankSize: 0
[1 sec: 133683 usec]	NumberOfImages: 14
[1 sec: 133694 usec]	RedMaskSize: 8
[1 sec: 133706 usec]	RedFieldPosition: 16
[1 sec: 133719 usec]	GreenMaskSize: 8
[1 sec: 133731 usec]	GreenFieldPosition: 8
[1 sec: 133743 usec]	BlueMaskSize: 8
[1 sec: 133755 usec]	BlueFieldPosition: 0
[1 sec: 133766 usec]	RsvdMaskSize: 8
[1 sec: 133778 usec]	RsvdFieldPosition: 24
[1 sec: 133790 usec]	DirectColorModeInfo: 0
[1 sec: 133801 usec]	PhysBasePtr: 0xb0000000
[1 sec: 133813 usec]	LinBytesPerScanLine: 1280
[1 sec: 133825 usec]	BnkNumberOfImagePages: 14
[1 sec: 133836 usec]	LinNumberOfImagePages: 14
[1 sec: 133848 usec]	LinRedMaskSize: 8
[1 sec: 133860 usec]	LinRedFieldPosition: 16
[1 sec: 133871 usec]	LinGreenMaskSize: 8
[1 sec: 133883 usec]	LinGreenFieldPosition: 8
[1 sec: 133894 usec]	LinBlueMaskSize: 8
[1 sec: 133905 usec]	LinBlueFieldPosition: 0
[1 sec: 133917 usec]	LinRsvdMaskSize: 8
[1 sec: 133928 usec]	LinRsvdFieldPosition: 24
[1 sec: 133940 usec]	MaxPixelClock: 229500000
[1 sec: 136614 usec]Mode: 111 (640x480)
[1 sec: 136631 usec]	ModeAttributes: 0x39f
[1 sec: 136642 usec]	WinAAttributes: 0x7
[1 sec: 136654 usec]	WinBAttributes: 0x0
[1 sec: 136665 usec]	WinGranularity: 64
[1 sec: 136677 usec]	WinSize: 64
[1 sec: 136688 usec]	WinASegment: 0xa000
[1 sec: 136700 usec]	WinBSegment: 0x0
[1 sec: 136713 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 136724 usec]	BytesPerScanline: 1280
[1 sec: 136735 usec]	XResolution: 640
[1 sec: 136746 usec]	YResolution: 480
[1 sec: 136758 usec]	XCharSize: 8
[1 sec: 136769 usec]	YCharSize: 16
[1 sec: 136780 usec]	NumberOfPlanes: 1
[1 sec: 136791 usec]	BitsPerPixel: 16
[1 sec: 136802 usec]	NumberOfBanks: 1
[1 sec: 136813 usec]	MemoryModel: 6
[1 sec: 136824 usec]	BankSize: 0
[1 sec: 136835 usec]	NumberOfImages: 4
[1 sec: 136846 usec]	RedMaskSize: 5
[1 sec: 136856 usec]	RedFieldPosition: 11
[1 sec: 136867 usec]	GreenMaskSize: 6
[1 sec: 136890 usec]	GreenFieldPosition: 5
[1 sec: 136902 usec]	BlueMaskSize: 5
[1 sec: 136913 usec]	BlueFieldPosition: 0
[1 sec: 136924 usec]	RsvdMaskSize: 0
[1 sec: 136935 usec]	RsvdFieldPosition: 0
[1 sec: 136947 usec]	DirectColorModeInfo: 0
[1 sec: 136958 usec]	PhysBasePtr: 0xb0000000
[1 sec: 136969 usec]	LinBytesPerScanLine: 1280
[1 sec: 136981 usec]	BnkNumberOfImagePages: 4
[1 sec: 136992 usec]	LinNumberOfImagePages: 4
[1 sec: 137003 usec]	LinRedMaskSize: 5
[1 sec: 137014 usec]	LinRedFieldPosition: 11
[1 sec: 137026 usec]	LinGreenMaskSize: 6
[1 sec: 137037 usec]	LinGreenFieldPosition: 5
[1 sec: 137048 usec]	LinBlueMaskSize: 5
[1 sec: 137059 usec]	LinBlueFieldPosition: 0
[1 sec: 137070 usec]	LinRsvdMaskSize: 0
[1 sec: 137081 usec]	LinRsvdFieldPosition: 0
[1 sec: 137092 usec]	MaxPixelClock: 229500000
[1 sec: 139966 usec]*[1 sec: 139981 usec]Mode: 112 (640x480)
[1 sec: 139993 usec]	ModeAttributes: 0x39f
[1 sec: 140005 usec]	WinAAttributes: 0x7
[1 sec: 140016 usec]	WinBAttributes: 0x0
[1 sec: 140028 usec]	WinGranularity: 64
[1 sec: 140039 usec]	WinSize: 64
[1 sec: 140051 usec]	WinASegment: 0xa000
[1 sec: 140073 usec]	WinBSegment: 0x0
[1 sec: 140085 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 140097 usec]	BytesPerScanline: 2560
[1 sec: 140108 usec]	XResolution: 640
[1 sec: 140119 usec]	YResolution: 480
[1 sec: 140131 usec]	XCharSize: 8
[1 sec: 140142 usec]	YCharSize: 16
[1 sec: 140153 usec]	NumberOfPlanes: 1
[1 sec: 140164 usec]	BitsPerPixel: 32
[1 sec: 140175 usec]	NumberOfBanks: 1
[1 sec: 140186 usec]	MemoryModel: 6
[1 sec: 140198 usec]	BankSize: 0
[1 sec: 140209 usec]	NumberOfImages: 1
[1 sec: 140220 usec]	RedMaskSize: 8
[1 sec: 140231 usec]	RedFieldPosition: 16
[1 sec: 140242 usec]	GreenMaskSize: 8
[1 sec: 140253 usec]	GreenFieldPosition: 8
[1 sec: 140265 usec]	BlueMaskSize: 8
[1 sec: 140276 usec]	BlueFieldPosition: 0
[1 sec: 140287 usec]	RsvdMaskSize: 8
[1 sec: 140299 usec]	RsvdFieldPosition: 24
[1 sec: 140311 usec]	DirectColorModeInfo: 0
[1 sec: 140322 usec]	PhysBasePtr: 0xb0000000
[1 sec: 140334 usec]	LinBytesPerScanLine: 2560
[1 sec: 140345 usec]	BnkNumberOfImagePages: 1
[1 sec: 140357 usec]	LinNumberOfImagePages: 1
[1 sec: 140368 usec]	LinRedMaskSize: 8
[1 sec: 140379 usec]	LinRedFieldPosition: 16
[1 sec: 140391 usec]	LinGreenMaskSize: 8
[1 sec: 140402 usec]	LinGreenFieldPosition: 8
[1 sec: 140414 usec]	LinBlueMaskSize: 8
[1 sec: 140425 usec]	LinBlueFieldPosition: 0
[1 sec: 140436 usec]	LinRsvdMaskSize: 8
[1 sec: 140447 usec]	LinRsvdFieldPosition: 24
[1 sec: 140459 usec]	MaxPixelClock: 229500000
[1 sec: 143163 usec]Mode: 114 (800x600)
[1 sec: 143181 usec]	ModeAttributes: 0x39f
[1 sec: 143193 usec]	WinAAttributes: 0x7
[1 sec: 143204 usec]	WinBAttributes: 0x0
[1 sec: 143216 usec]	WinGranularity: 64
[1 sec: 143227 usec]	WinSize: 64
[1 sec: 143239 usec]	WinASegment: 0xa000
[1 sec: 143251 usec]	WinBSegment: 0x0
[1 sec: 143262 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 143274 usec]	BytesPerScanline: 1600
[1 sec: 143285 usec]	XResolution: 800
[1 sec: 143297 usec]	YResolution: 600
[1 sec: 143308 usec]	XCharSize: 8
[1 sec: 143320 usec]	YCharSize: 16
[1 sec: 143331 usec]	NumberOfPlanes: 1
[1 sec: 143342 usec]	BitsPerPixel: 16
[1 sec: 143354 usec]	NumberOfBanks: 1
[1 sec: 143365 usec]	MemoryModel: 6
[1 sec: 143376 usec]	BankSize: 0
[1 sec: 143388 usec]	NumberOfImages: 2
[1 sec: 143399 usec]	RedMaskSize: 5
[1 sec: 143410 usec]	RedFieldPosition: 11
[1 sec: 143422 usec]	GreenMaskSize: 6
[1 sec: 143433 usec]	GreenFieldPosition: 5
[1 sec: 143445 usec]	BlueMaskSize: 5
[1 sec: 143456 usec]	BlueFieldPosition: 0
[1 sec: 143468 usec]	RsvdMaskSize: 0
[1 sec: 143479 usec]	RsvdFieldPosition: 0
[1 sec: 143491 usec]	DirectColorModeInfo: 0
[1 sec: 143503 usec]	PhysBasePtr: 0xb0000000
[1 sec: 143515 usec]	LinBytesPerScanLine: 1600
[1 sec: 143527 usec]	BnkNumberOfImagePages: 2
[1 sec: 143539 usec]	LinNumberOfImagePages: 2
[1 sec: 143551 usec]	LinRedMaskSize: 5
[1 sec: 143563 usec]	LinRedFieldPosition: 11
[1 sec: 143575 usec]	LinGreenMaskSize: 6
[1 sec: 143586 usec]	LinGreenFieldPosition: 5
[1 sec: 143598 usec]	LinBlueMaskSize: 5
[1 sec: 143610 usec]	LinBlueFieldPosition: 0
[1 sec: 143622 usec]	LinRsvdMaskSize: 0
[1 sec: 143633 usec]	LinRsvdFieldPosition: 0
[1 sec: 143645 usec]	MaxPixelClock: 229500000
[1 sec: 146541 usec]*[1 sec: 146558 usec]Mode: 115 (800x600)
[1 sec: 146570 usec]	ModeAttributes: 0x39f
[1 sec: 146581 usec]	WinAAttributes: 0x7
[1 sec: 146592 usec]	WinBAttributes: 0x0
[1 sec: 146604 usec]	WinGranularity: 64
[1 sec: 146615 usec]	WinSize: 64
[1 sec: 146627 usec]	WinASegment: 0xa000
[1 sec: 146638 usec]	WinBSegment: 0x0
[1 sec: 146650 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 146661 usec]	BytesPerScanline: 3200
[1 sec: 146673 usec]	XResolution: 800
[1 sec: 146684 usec]	YResolution: 600
[1 sec: 146696 usec]	XCharSize: 8
[1 sec: 146707 usec]	YCharSize: 16
[1 sec: 146719 usec]	NumberOfPlanes: 1
[1 sec: 146730 usec]	BitsPerPixel: 32
[1 sec: 146742 usec]	NumberOfBanks: 1
[1 sec: 146753 usec]	MemoryModel: 6
[1 sec: 146765 usec]	BankSize: 0
[1 sec: 146776 usec]	NumberOfImages: 1
[1 sec: 146788 usec]	RedMaskSize: 8
[1 sec: 146799 usec]	RedFieldPosition: 16
[1 sec: 146811 usec]	GreenMaskSize: 8
[1 sec: 146822 usec]	GreenFieldPosition: 8
[1 sec: 146845 usec]	BlueMaskSize: 8
[1 sec: 146857 usec]	BlueFieldPosition: 0
[1 sec: 146868 usec]	RsvdMaskSize: 8
[1 sec: 146880 usec]	RsvdFieldPosition: 24
[1 sec: 146892 usec]	DirectColorModeInfo: 0
[1 sec: 146903 usec]	PhysBasePtr: 0xb0000000
[1 sec: 146914 usec]	LinBytesPerScanLine: 3200
[1 sec: 146926 usec]	BnkNumberOfImagePages: 1
[1 sec: 146937 usec]	LinNumberOfImagePages: 1
[1 sec: 146948 usec]	LinRedMaskSize: 8
[1 sec: 146959 usec]	LinRedFieldPosition: 16
[1 sec: 146971 usec]	LinGreenMaskSize: 8
[1 sec: 146982 usec]	LinGreenFieldPosition: 8
[1 sec: 146993 usec]	LinBlueMaskSize: 8
[1 sec: 147004 usec]	LinBlueFieldPosition: 0
[1 sec: 147016 usec]	LinRsvdMaskSize: 8
[1 sec: 147027 usec]	LinRsvdFieldPosition: 24
[1 sec: 147038 usec]	MaxPixelClock: 229500000
[1 sec: 149797 usec]Mode: 117 (1024x768)
[1 sec: 149816 usec]	ModeAttributes: 0x39f
[1 sec: 149828 usec]	WinAAttributes: 0x7
[1 sec: 149840 usec]	WinBAttributes: 0x0
[1 sec: 149852 usec]	WinGranularity: 64
[1 sec: 149863 usec]	WinSize: 64
[1 sec: 149875 usec]	WinASegment: 0xa000
[1 sec: 149886 usec]	WinBSegment: 0x0
[1 sec: 149899 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 149911 usec]	BytesPerScanline: 2048
[1 sec: 149922 usec]	XResolution: 1024
[1 sec: 149933 usec]	YResolution: 768
[1 sec: 149945 usec]	XCharSize: 8
[1 sec: 149956 usec]	YCharSize: 16
[1 sec: 149967 usec]	NumberOfPlanes: 1
[1 sec: 149978 usec]	BitsPerPixel: 16
[1 sec: 149989 usec]	NumberOfBanks: 1
[1 sec: 150001 usec]	MemoryModel: 6
[1 sec: 150012 usec]	BankSize: 0
[1 sec: 150023 usec]	NumberOfImages: 1
[1 sec: 150034 usec]	RedMaskSize: 5
[1 sec: 150045 usec]	RedFieldPosition: 11
[1 sec: 150056 usec]	GreenMaskSize: 6
[1 sec: 150068 usec]	GreenFieldPosition: 5
[1 sec: 150079 usec]	BlueMaskSize: 5
[1 sec: 150090 usec]	BlueFieldPosition: 0
[1 sec: 150101 usec]	RsvdMaskSize: 0
[1 sec: 150112 usec]	RsvdFieldPosition: 0
[1 sec: 150124 usec]	DirectColorModeInfo: 0
[1 sec: 150135 usec]	PhysBasePtr: 0xb0000000
[1 sec: 150146 usec]	LinBytesPerScanLine: 2048
[1 sec: 150158 usec]	BnkNumberOfImagePages: 1
[1 sec: 150169 usec]	LinNumberOfImagePages: 1
[1 sec: 150180 usec]	LinRedMaskSize: 5
[1 sec: 150191 usec]	LinRedFieldPosition: 11
[1 sec: 150202 usec]	LinGreenMaskSize: 6
[1 sec: 150213 usec]	LinGreenFieldPosition: 5
[1 sec: 150224 usec]	LinBlueMaskSize: 5
[1 sec: 150235 usec]	LinBlueFieldPosition: 0
[1 sec: 150246 usec]	LinRsvdMaskSize: 0
[1 sec: 150257 usec]	LinRsvdFieldPosition: 0
[1 sec: 150268 usec]	MaxPixelClock: 229500000
[1 sec: 153246 usec]*[1 sec: 153263 usec]Mode: 118 (1024x768)
[1 sec: 153276 usec]	ModeAttributes: 0x39f
[1 sec: 153287 usec]	WinAAttributes: 0x7
[1 sec: 153299 usec]	WinBAttributes: 0x0
[1 sec: 153310 usec]	WinGranularity: 64
[1 sec: 153322 usec]	WinSize: 64
[1 sec: 153334 usec]	WinASegment: 0xa000
[1 sec: 153345 usec]	WinBSegment: 0x0
[1 sec: 153357 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 153369 usec]	BytesPerScanline: 4096
[1 sec: 153380 usec]	XResolution: 1024
[1 sec: 153392 usec]	YResolution: 768
[1 sec: 153404 usec]	XCharSize: 8
[1 sec: 153415 usec]	YCharSize: 16
[1 sec: 153427 usec]	NumberOfPlanes: 1
[1 sec: 153438 usec]	BitsPerPixel: 32
[1 sec: 153450 usec]	NumberOfBanks: 1
[1 sec: 153461 usec]	MemoryModel: 6
[1 sec: 153473 usec]	BankSize: 0
[1 sec: 153485 usec]	NumberOfImages: 1
[1 sec: 153496 usec]	RedMaskSize: 8
[1 sec: 153507 usec]	RedFieldPosition: 16
[1 sec: 153519 usec]	GreenMaskSize: 8
[1 sec: 153530 usec]	GreenFieldPosition: 8
[1 sec: 153542 usec]	BlueMaskSize: 8
[1 sec: 153553 usec]	BlueFieldPosition: 0
[1 sec: 153565 usec]	RsvdMaskSize: 8
[1 sec: 153576 usec]	RsvdFieldPosition: 24
[1 sec: 153588 usec]	DirectColorModeInfo: 0
[1 sec: 153600 usec]	PhysBasePtr: 0xb0000000
[1 sec: 153612 usec]	LinBytesPerScanLine: 4096
[1 sec: 153624 usec]	BnkNumberOfImagePages: 1
[1 sec: 153635 usec]	LinNumberOfImagePages: 1
[1 sec: 153647 usec]	LinRedMaskSize: 8
[1 sec: 153659 usec]	LinRedFieldPosition: 16
[1 sec: 153671 usec]	LinGreenMaskSize: 8
[1 sec: 153682 usec]	LinGreenFieldPosition: 8
[1 sec: 153694 usec]	LinBlueMaskSize: 8
[1 sec: 153706 usec]	LinBlueFieldPosition: 0
[1 sec: 153718 usec]	LinRsvdMaskSize: 8
[1 sec: 153740 usec]	LinRsvdFieldPosition: 24
[1 sec: 153752 usec]	MaxPixelClock: 229500000
[1 sec: 156277 usec]Mode: 11a (1280x1024)
[1 sec: 156294 usec]	ModeAttributes: 0x39f
[1 sec: 156305 usec]	WinAAttributes: 0x7
[1 sec: 156317 usec]	WinBAttributes: 0x0
[1 sec: 156328 usec]	WinGranularity: 64
[1 sec: 156339 usec]	WinSize: 64
[1 sec: 156351 usec]	WinASegment: 0xa000
[1 sec: 156362 usec]	WinBSegment: 0x0
[1 sec: 156374 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 156386 usec]	BytesPerScanline: 2560
[1 sec: 156397 usec]	XResolution: 1280
[1 sec: 156409 usec]	YResolution: 1024
[1 sec: 156420 usec]	XCharSize: 8
[1 sec: 156431 usec]	YCharSize: 16
[1 sec: 156442 usec]	NumberOfPlanes: 1
[1 sec: 156454 usec]	BitsPerPixel: 16
[1 sec: 156465 usec]	NumberOfBanks: 1
[1 sec: 156476 usec]	MemoryModel: 6
[1 sec: 156487 usec]	BankSize: 0
[1 sec: 156499 usec]	NumberOfImages: 1
[1 sec: 156510 usec]	RedMaskSize: 5
[1 sec: 156521 usec]	RedFieldPosition: 11
[1 sec: 156532 usec]	GreenMaskSize: 6
[1 sec: 156543 usec]	GreenFieldPosition: 5
[1 sec: 156554 usec]	BlueMaskSize: 5
[1 sec: 156565 usec]	BlueFieldPosition: 0
[1 sec: 156577 usec]	RsvdMaskSize: 0
[1 sec: 156588 usec]	RsvdFieldPosition: 0
[1 sec: 156599 usec]	DirectColorModeInfo: 0
[1 sec: 156611 usec]	PhysBasePtr: 0xb0000000
[1 sec: 156622 usec]	LinBytesPerScanLine: 2560
[1 sec: 156633 usec]	BnkNumberOfImagePages: 1
[1 sec: 156644 usec]	LinNumberOfImagePages: 1
[1 sec: 156655 usec]	LinRedMaskSize: 5
[1 sec: 156666 usec]	LinRedFieldPosition: 11
[1 sec: 156678 usec]	LinGreenMaskSize: 6
[1 sec: 156689 usec]	LinGreenFieldPosition: 5
[1 sec: 156700 usec]	LinBlueMaskSize: 5
[1 sec: 156711 usec]	LinBlueFieldPosition: 0
[1 sec: 156722 usec]	LinRsvdMaskSize: 0
[1 sec: 156733 usec]	LinRsvdFieldPosition: 0
[1 sec: 156744 usec]	MaxPixelClock: 229500000
[1 sec: 159736 usec]*[1 sec: 159753 usec]Mode: 11b (1280x1024)
[1 sec: 159765 usec]	ModeAttributes: 0x39f
[1 sec: 159777 usec]	WinAAttributes: 0x7
[1 sec: 159788 usec]	WinBAttributes: 0x0
[1 sec: 159800 usec]	WinGranularity: 64
[1 sec: 159812 usec]	WinSize: 64
[1 sec: 159823 usec]	WinASegment: 0xa000
[1 sec: 159835 usec]	WinBSegment: 0x0
[1 sec: 159847 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 159859 usec]	BytesPerScanline: 5120
[1 sec: 159870 usec]	XResolution: 1280
[1 sec: 159882 usec]	YResolution: 1024
[1 sec: 159893 usec]	XCharSize: 8
[1 sec: 159905 usec]	YCharSize: 16
[1 sec: 159916 usec]	NumberOfPlanes: 1
[1 sec: 159928 usec]	BitsPerPixel: 32
[1 sec: 159939 usec]	NumberOfBanks: 1
[1 sec: 159951 usec]	MemoryModel: 6
[1 sec: 159962 usec]	BankSize: 0
[1 sec: 159974 usec]	NumberOfImages: 0
[1 sec: 159985 usec]	RedMaskSize: 8
[1 sec: 159997 usec]	RedFieldPosition: 16
[1 sec: 160008 usec]	GreenMaskSize: 8
[1 sec: 160020 usec]	GreenFieldPosition: 8
[1 sec: 160031 usec]	BlueMaskSize: 8
[1 sec: 160042 usec]	BlueFieldPosition: 0
[1 sec: 160054 usec]	RsvdMaskSize: 8
[1 sec: 160066 usec]	RsvdFieldPosition: 24
[1 sec: 160077 usec]	DirectColorModeInfo: 0
[1 sec: 160089 usec]	PhysBasePtr: 0xb0000000
[1 sec: 160101 usec]	LinBytesPerScanLine: 5120
[1 sec: 160113 usec]	BnkNumberOfImagePages: 0
[1 sec: 160125 usec]	LinNumberOfImagePages: 0
[1 sec: 160136 usec]	LinRedMaskSize: 8
[1 sec: 160148 usec]	LinRedFieldPosition: 16
[1 sec: 160160 usec]	LinGreenMaskSize: 8
[1 sec: 160172 usec]	LinGreenFieldPosition: 8
[1 sec: 160184 usec]	LinBlueMaskSize: 8
[1 sec: 160196 usec]	LinBlueFieldPosition: 0
[1 sec: 160207 usec]	LinRsvdMaskSize: 8
[1 sec: 160219 usec]	LinRsvdFieldPosition: 24
[1 sec: 160231 usec]	MaxPixelClock: 229500000
[1 sec: 162625 usec]Mode: 130 (320x200)
[1 sec: 162644 usec]	ModeAttributes: 0x39f
[1 sec: 162656 usec]	WinAAttributes: 0x7
[1 sec: 162667 usec]	WinBAttributes: 0x0
[1 sec: 162678 usec]	WinGranularity: 64
[1 sec: 162690 usec]	WinSize: 64
[1 sec: 162701 usec]	WinASegment: 0xa000
[1 sec: 162712 usec]	WinBSegment: 0x0
[1 sec: 162725 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 162736 usec]	BytesPerScanline: 320
[1 sec: 162748 usec]	XResolution: 320
[1 sec: 162759 usec]	YResolution: 200
[1 sec: 162770 usec]	XCharSize: 8
[1 sec: 162782 usec]	YCharSize: 8
[1 sec: 162801 usec]	NumberOfPlanes: 1
[1 sec: 162812 usec]	BitsPerPixel: 8
[1 sec: 162823 usec]	NumberOfBanks: 1
[1 sec: 162835 usec]	MemoryModel: 4
[1 sec: 162846 usec]	BankSize: 0
[1 sec: 162857 usec]	NumberOfImages: 62
[1 sec: 162868 usec]	RedMaskSize: 0
[1 sec: 162879 usec]	RedFieldPosition: 0
[1 sec: 162890 usec]	GreenMaskSize: 0
[1 sec: 162901 usec]	GreenFieldPosition: 0
[1 sec: 162912 usec]	BlueMaskSize: 0
[1 sec: 162924 usec]	BlueFieldPosition: 0
[1 sec: 162935 usec]	RsvdMaskSize: 0
[1 sec: 162946 usec]	RsvdFieldPosition: 0
[1 sec: 162957 usec]	DirectColorModeInfo: 0
[1 sec: 162969 usec]	PhysBasePtr: 0xb0000000
[1 sec: 162980 usec]	LinBytesPerScanLine: 320
[1 sec: 162991 usec]	BnkNumberOfImagePages: 62
[1 sec: 163002 usec]	LinNumberOfImagePages: 62
[1 sec: 163013 usec]	LinRedMaskSize: 0
[1 sec: 163024 usec]	LinRedFieldPosition: 0
[1 sec: 163036 usec]	LinGreenMaskSize: 0
[1 sec: 163047 usec]	LinGreenFieldPosition: 0
[1 sec: 163058 usec]	LinBlueMaskSize: 0
[1 sec: 163069 usec]	LinBlueFieldPosition: 0
[1 sec: 163080 usec]	LinRsvdMaskSize: 0
[1 sec: 163091 usec]	LinRsvdFieldPosition: 0
[1 sec: 163102 usec]	MaxPixelClock: 229500000
[1 sec: 165516 usec]Mode: 131 (320x400)
[1 sec: 165534 usec]	ModeAttributes: 0x39f
[1 sec: 165546 usec]	WinAAttributes: 0x7
[1 sec: 165557 usec]	WinBAttributes: 0x0
[1 sec: 165569 usec]	WinGranularity: 64
[1 sec: 165580 usec]	WinSize: 64
[1 sec: 165592 usec]	WinASegment: 0xa000
[1 sec: 165604 usec]	WinBSegment: 0x0
[1 sec: 165615 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 165627 usec]	BytesPerScanline: 320
[1 sec: 165638 usec]	XResolution: 320
[1 sec: 165650 usec]	YResolution: 400
[1 sec: 165661 usec]	XCharSize: 8
[1 sec: 165673 usec]	YCharSize: 16
[1 sec: 165685 usec]	NumberOfPlanes: 1
[1 sec: 165696 usec]	BitsPerPixel: 8
[1 sec: 165708 usec]	NumberOfBanks: 1
[1 sec: 165719 usec]	MemoryModel: 4
[1 sec: 165731 usec]	BankSize: 0
[1 sec: 165742 usec]	NumberOfImages: 30
[1 sec: 165754 usec]	RedMaskSize: 0
[1 sec: 165765 usec]	RedFieldPosition: 0
[1 sec: 165777 usec]	GreenMaskSize: 0
[1 sec: 165788 usec]	GreenFieldPosition: 0
[1 sec: 165800 usec]	BlueMaskSize: 0
[1 sec: 165811 usec]	BlueFieldPosition: 0
[1 sec: 165823 usec]	RsvdMaskSize: 0
[1 sec: 165834 usec]	RsvdFieldPosition: 0
[1 sec: 165846 usec]	DirectColorModeInfo: 0
[1 sec: 165858 usec]	PhysBasePtr: 0xb0000000
[1 sec: 165870 usec]	LinBytesPerScanLine: 320
[1 sec: 165882 usec]	BnkNumberOfImagePages: 30
[1 sec: 165894 usec]	LinNumberOfImagePages: 30
[1 sec: 165906 usec]	LinRedMaskSize: 0
[1 sec: 165917 usec]	LinRedFieldPosition: 0
[1 sec: 165929 usec]	LinGreenMaskSize: 0
[1 sec: 165941 usec]	LinGreenFieldPosition: 0
[1 sec: 165953 usec]	LinBlueMaskSize: 0
[1 sec: 165964 usec]	LinBlueFieldPosition: 0
[1 sec: 165976 usec]	LinRsvdMaskSize: 0
[1 sec: 165988 usec]	LinRsvdFieldPosition: 0
[1 sec: 166000 usec]	MaxPixelClock: 229500000
[1 sec: 168434 usec]Mode: 132 (320x400)
[1 sec: 168451 usec]	ModeAttributes: 0x39f
[1 sec: 168463 usec]	WinAAttributes: 0x7
[1 sec: 168474 usec]	WinBAttributes: 0x0
[1 sec: 168485 usec]	WinGranularity: 64
[1 sec: 168497 usec]	WinSize: 64
[1 sec: 168508 usec]	WinASegment: 0xa000
[1 sec: 168519 usec]	WinBSegment: 0x0
[1 sec: 168532 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 168543 usec]	BytesPerScanline: 640
[1 sec: 168555 usec]	XResolution: 320
[1 sec: 168566 usec]	YResolution: 400
[1 sec: 168577 usec]	XCharSize: 8
[1 sec: 168589 usec]	YCharSize: 16
[1 sec: 168600 usec]	NumberOfPlanes: 1
[1 sec: 168611 usec]	BitsPerPixel: 16
[1 sec: 168622 usec]	NumberOfBanks: 1
[1 sec: 168633 usec]	MemoryModel: 6
[1 sec: 168644 usec]	BankSize: 0
[1 sec: 168655 usec]	NumberOfImages: 14
[1 sec: 168666 usec]	RedMaskSize: 5
[1 sec: 168677 usec]	RedFieldPosition: 11
[1 sec: 168689 usec]	GreenMaskSize: 6
[1 sec: 168700 usec]	GreenFieldPosition: 5
[1 sec: 168711 usec]	BlueMaskSize: 5
[1 sec: 168722 usec]	BlueFieldPosition: 0
[1 sec: 168733 usec]	RsvdMaskSize: 0
[1 sec: 168744 usec]	RsvdFieldPosition: 0
[1 sec: 168756 usec]	DirectColorModeInfo: 0
[1 sec: 168767 usec]	PhysBasePtr: 0xb0000000
[1 sec: 168778 usec]	LinBytesPerScanLine: 640
[1 sec: 168798 usec]	BnkNumberOfImagePages: 14
[1 sec: 168810 usec]	LinNumberOfImagePages: 14
[1 sec: 168820 usec]	LinRedMaskSize: 5
[1 sec: 168832 usec]	LinRedFieldPosition: 11
[1 sec: 168843 usec]	LinGreenMaskSize: 6
[1 sec: 168854 usec]	LinGreenFieldPosition: 5
[1 sec: 168865 usec]	LinBlueMaskSize: 5
[1 sec: 168887 usec]	LinBlueFieldPosition: 0
[1 sec: 168899 usec]	LinRsvdMaskSize: 0
[1 sec: 168910 usec]	LinRsvdFieldPosition: 0
[1 sec: 168921 usec]	MaxPixelClock: 229500000
[1 sec: 171835 usec]*[1 sec: 171851 usec]Mode: 133 (320x400)
[1 sec: 171863 usec]	ModeAttributes: 0x39f
[1 sec: 171875 usec]	WinAAttributes: 0x7
[1 sec: 171886 usec]	WinBAttributes: 0x0
[1 sec: 171898 usec]	WinGranularity: 64
[1 sec: 171909 usec]	WinSize: 64
[1 sec: 171921 usec]	WinASegment: 0xa000
[1 sec: 171933 usec]	WinBSegment: 0x0
[1 sec: 171945 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 171956 usec]	BytesPerScanline: 1280
[1 sec: 171968 usec]	XResolution: 320
[1 sec: 171980 usec]	YResolution: 400
[1 sec: 171991 usec]	XCharSize: 8
[1 sec: 172003 usec]	YCharSize: 16
[1 sec: 172015 usec]	NumberOfPlanes: 1
[1 sec: 172026 usec]	BitsPerPixel: 32
[1 sec: 172038 usec]	NumberOfBanks: 1
[1 sec: 172049 usec]	MemoryModel: 6
[1 sec: 172061 usec]	BankSize: 0
[1 sec: 172073 usec]	NumberOfImages: 6
[1 sec: 172084 usec]	RedMaskSize: 8
[1 sec: 172096 usec]	RedFieldPosition: 16
[1 sec: 172108 usec]	GreenMaskSize: 8
[1 sec: 172121 usec]	GreenFieldPosition: 8
[1 sec: 172133 usec]	BlueMaskSize: 8
[1 sec: 172144 usec]	BlueFieldPosition: 0
[1 sec: 172156 usec]	RsvdMaskSize: 8
[1 sec: 172167 usec]	RsvdFieldPosition: 24
[1 sec: 172179 usec]	DirectColorModeInfo: 0
[1 sec: 172191 usec]	PhysBasePtr: 0xb0000000
[1 sec: 172202 usec]	LinBytesPerScanLine: 1280
[1 sec: 172214 usec]	BnkNumberOfImagePages: 6
[1 sec: 172226 usec]	LinNumberOfImagePages: 6
[1 sec: 172237 usec]	LinRedMaskSize: 8
[1 sec: 172249 usec]	LinRedFieldPosition: 16
[1 sec: 172261 usec]	LinGreenMaskSize: 8
[1 sec: 172272 usec]	LinGreenFieldPosition: 8
[1 sec: 172284 usec]	LinBlueMaskSize: 8
[1 sec: 172295 usec]	LinBlueFieldPosition: 0
[1 sec: 172307 usec]	LinRsvdMaskSize: 8
[1 sec: 172318 usec]	LinRsvdFieldPosition: 24
[1 sec: 172329 usec]	MaxPixelClock: 229500000
[1 sec: 174784 usec]Mode: 134 (320x240)
[1 sec: 174803 usec]	ModeAttributes: 0x39f
[1 sec: 174815 usec]	WinAAttributes: 0x7
[1 sec: 174826 usec]	WinBAttributes: 0x0
[1 sec: 174838 usec]	WinGranularity: 64
[1 sec: 174849 usec]	WinSize: 64
[1 sec: 174860 usec]	WinASegment: 0xa000
[1 sec: 174872 usec]	WinBSegment: 0x0
[1 sec: 174884 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 174896 usec]	BytesPerScanline: 320
[1 sec: 174907 usec]	XResolution: 320
[1 sec: 174919 usec]	YResolution: 240
[1 sec: 174930 usec]	XCharSize: 8
[1 sec: 174941 usec]	YCharSize: 8
[1 sec: 174952 usec]	NumberOfPlanes: 1
[1 sec: 174963 usec]	BitsPerPixel: 8
[1 sec: 174974 usec]	NumberOfBanks: 1
[1 sec: 174985 usec]	MemoryModel: 4
[1 sec: 174997 usec]	BankSize: 0
[1 sec: 175008 usec]	NumberOfImages: 30
[1 sec: 175019 usec]	RedMaskSize: 0
[1 sec: 175030 usec]	RedFieldPosition: 0
[1 sec: 175041 usec]	GreenMaskSize: 0
[1 sec: 175052 usec]	GreenFieldPosition: 0
[1 sec: 175064 usec]	BlueMaskSize: 0
[1 sec: 175075 usec]	BlueFieldPosition: 0
[1 sec: 175086 usec]	RsvdMaskSize: 0
[1 sec: 175097 usec]	RsvdFieldPosition: 0
[1 sec: 175109 usec]	DirectColorModeInfo: 0
[1 sec: 175120 usec]	PhysBasePtr: 0xb0000000
[1 sec: 175131 usec]	LinBytesPerScanLine: 320
[1 sec: 175143 usec]	BnkNumberOfImagePages: 30
[1 sec: 175154 usec]	LinNumberOfImagePages: 30
[1 sec: 175165 usec]	LinRedMaskSize: 0
[1 sec: 175176 usec]	LinRedFieldPosition: 0
[1 sec: 175188 usec]	LinGreenMaskSize: 0
[1 sec: 175199 usec]	LinGreenFieldPosition: 0
[1 sec: 175210 usec]	LinBlueMaskSize: 0
[1 sec: 175221 usec]	LinBlueFieldPosition: 0
[1 sec: 175232 usec]	LinRsvdMaskSize: 0
[1 sec: 175244 usec]	LinRsvdFieldPosition: 0
[1 sec: 175255 usec]	MaxPixelClock: 229500000
[1 sec: 177737 usec]Mode: 135 (320x240)
[1 sec: 177755 usec]	ModeAttributes: 0x39f
[1 sec: 177767 usec]	WinAAttributes: 0x7
[1 sec: 177778 usec]	WinBAttributes: 0x0
[1 sec: 177790 usec]	WinGranularity: 64
[1 sec: 177811 usec]	WinSize: 64
[1 sec: 177822 usec]	WinASegment: 0xa000
[1 sec: 177833 usec]	WinBSegment: 0x0
[1 sec: 177845 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 177856 usec]	BytesPerScanline: 640
[1 sec: 177867 usec]	XResolution: 320
[1 sec: 177878 usec]	YResolution: 240
[1 sec: 177889 usec]	XCharSize: 8
[1 sec: 177901 usec]	YCharSize: 8
[1 sec: 177912 usec]	NumberOfPlanes: 1
[1 sec: 177923 usec]	BitsPerPixel: 16
[1 sec: 177934 usec]	NumberOfBanks: 1
[1 sec: 177945 usec]	MemoryModel: 6
[1 sec: 177956 usec]	BankSize: 0
[1 sec: 177967 usec]	NumberOfImages: 19
[1 sec: 177978 usec]	RedMaskSize: 5
[1 sec: 177989 usec]	RedFieldPosition: 11
[1 sec: 178000 usec]	GreenMaskSize: 6
[1 sec: 178011 usec]	GreenFieldPosition: 5
[1 sec: 178022 usec]	BlueMaskSize: 5
[1 sec: 178033 usec]	BlueFieldPosition: 0
[1 sec: 178044 usec]	RsvdMaskSize: 0
[1 sec: 178056 usec]	RsvdFieldPosition: 0
[1 sec: 178067 usec]	DirectColorModeInfo: 0
[1 sec: 178078 usec]	PhysBasePtr: 0xb0000000
[1 sec: 178090 usec]	LinBytesPerScanLine: 640
[1 sec: 178101 usec]	BnkNumberOfImagePages: 19
[1 sec: 178113 usec]	LinNumberOfImagePages: 19
[1 sec: 178124 usec]	LinRedMaskSize: 5
[1 sec: 178135 usec]	LinRedFieldPosition: 11
[1 sec: 178146 usec]	LinGreenMaskSize: 6
[1 sec: 178157 usec]	LinGreenFieldPosition: 5
[1 sec: 178168 usec]	LinBlueMaskSize: 5
[1 sec: 178179 usec]	LinBlueFieldPosition: 0
[1 sec: 178191 usec]	LinRsvdMaskSize: 0
[1 sec: 178202 usec]	LinRsvdFieldPosition: 0
[1 sec: 178213 usec]	MaxPixelClock: 229500000
[1 sec: 181154 usec]*[1 sec: 181171 usec]Mode: 136 (320x240)
[1 sec: 181183 usec]	ModeAttributes: 0x39f
[1 sec: 181194 usec]	WinAAttributes: 0x7
[1 sec: 181206 usec]	WinBAttributes: 0x0
[1 sec: 181217 usec]	WinGranularity: 64
[1 sec: 181229 usec]	WinSize: 64
[1 sec: 181240 usec]	WinASegment: 0xa000
[1 sec: 181252 usec]	WinBSegment: 0x0
[1 sec: 181263 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 181275 usec]	BytesPerScanline: 1280
[1 sec: 181286 usec]	XResolution: 320
[1 sec: 181298 usec]	YResolution: 240
[1 sec: 181309 usec]	XCharSize: 8
[1 sec: 181321 usec]	YCharSize: 8
[1 sec: 181332 usec]	NumberOfPlanes: 1
[1 sec: 181343 usec]	BitsPerPixel: 32
[1 sec: 181355 usec]	NumberOfBanks: 1
[1 sec: 181366 usec]	MemoryModel: 6
[1 sec: 181378 usec]	BankSize: 0
[1 sec: 181389 usec]	NumberOfImages: 10
[1 sec: 181401 usec]	RedMaskSize: 8
[1 sec: 181412 usec]	RedFieldPosition: 16
[1 sec: 181424 usec]	GreenMaskSize: 8
[1 sec: 181435 usec]	GreenFieldPosition: 8
[1 sec: 181447 usec]	BlueMaskSize: 8
[1 sec: 181458 usec]	BlueFieldPosition: 0
[1 sec: 181469 usec]	RsvdMaskSize: 8
[1 sec: 181481 usec]	RsvdFieldPosition: 24
[1 sec: 181493 usec]	DirectColorModeInfo: 0
[1 sec: 181505 usec]	PhysBasePtr: 0xb0000000
[1 sec: 181517 usec]	LinBytesPerScanLine: 1280
[1 sec: 181529 usec]	BnkNumberOfImagePages: 10
[1 sec: 181540 usec]	LinNumberOfImagePages: 10
[1 sec: 181552 usec]	LinRedMaskSize: 8
[1 sec: 181564 usec]	LinRedFieldPosition: 16
[1 sec: 181576 usec]	LinGreenMaskSize: 8
[1 sec: 181588 usec]	LinGreenFieldPosition: 8
[1 sec: 181600 usec]	LinBlueMaskSize: 8
[1 sec: 181612 usec]	LinBlueFieldPosition: 0
[1 sec: 181624 usec]	LinRsvdMaskSize: 8
[1 sec: 181635 usec]	LinRsvdFieldPosition: 24
[1 sec: 181647 usec]	MaxPixelClock: 229500000
[1 sec: 184160 usec]Mode: 13d (640x400)
[1 sec: 184176 usec]	ModeAttributes: 0x39f
[1 sec: 184188 usec]	WinAAttributes: 0x7
[1 sec: 184199 usec]	WinBAttributes: 0x0
[1 sec: 184211 usec]	WinGranularity: 64
[1 sec: 184223 usec]	WinSize: 64
[1 sec: 184234 usec]	WinASegment: 0xa000
[1 sec: 184246 usec]	WinBSegment: 0x0
[1 sec: 184257 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 184269 usec]	BytesPerScanline: 1280
[1 sec: 184280 usec]	XResolution: 640
[1 sec: 184292 usec]	YResolution: 400
[1 sec: 184303 usec]	XCharSize: 8
[1 sec: 184314 usec]	YCharSize: 16
[1 sec: 184325 usec]	NumberOfPlanes: 1
[1 sec: 184336 usec]	BitsPerPixel: 16
[1 sec: 184348 usec]	NumberOfBanks: 1
[1 sec: 184359 usec]	MemoryModel: 6
[1 sec: 184370 usec]	BankSize: 0
[1 sec: 184382 usec]	NumberOfImages: 6
[1 sec: 184393 usec]	RedMaskSize: 5
[1 sec: 184404 usec]	RedFieldPosition: 11
[1 sec: 184425 usec]	GreenMaskSize: 6
[1 sec: 184438 usec]	GreenFieldPosition: 5
[1 sec: 184449 usec]	BlueMaskSize: 5
[1 sec: 184460 usec]	BlueFieldPosition: 0
[1 sec: 184472 usec]	RsvdMaskSize: 0
[1 sec: 184483 usec]	RsvdFieldPosition: 0
[1 sec: 184494 usec]	DirectColorModeInfo: 0
[1 sec: 184506 usec]	PhysBasePtr: 0xb0000000
[1 sec: 184517 usec]	LinBytesPerScanLine: 1280
[1 sec: 184529 usec]	BnkNumberOfImagePages: 6
[1 sec: 184540 usec]	LinNumberOfImagePages: 6
[1 sec: 184551 usec]	LinRedMaskSize: 5
[1 sec: 184562 usec]	LinRedFieldPosition: 11
[1 sec: 184574 usec]	LinGreenMaskSize: 6
[1 sec: 184585 usec]	LinGreenFieldPosition: 5
[1 sec: 184596 usec]	LinBlueMaskSize: 5
[1 sec: 184607 usec]	LinBlueFieldPosition: 0
[1 sec: 184619 usec]	LinRsvdMaskSize: 0
[1 sec: 184630 usec]	LinRsvdFieldPosition: 0
[1 sec: 184641 usec]	MaxPixelClock: 229500000
[1 sec: 187602 usec]*[1 sec: 187619 usec]Mode: 13e (640x400)
[1 sec: 187631 usec]	ModeAttributes: 0x39f
[1 sec: 187642 usec]	WinAAttributes: 0x7
[1 sec: 187654 usec]	WinBAttributes: 0x0
[1 sec: 187665 usec]	WinGranularity: 64
[1 sec: 187676 usec]	WinSize: 64
[1 sec: 187688 usec]	WinASegment: 0xa000
[1 sec: 187700 usec]	WinBSegment: 0x0
[1 sec: 187711 usec]	WinFuncPtr: 0xc00094c1
[1 sec: 187723 usec]	BytesPerScanline: 2560
[1 sec: 187734 usec]	XResolution: 640
[1 sec: 187746 usec]	YResolution: 400
[1 sec: 187757 usec]	XCharSize: 8
[1 sec: 187769 usec]	YCharSize: 16
[1 sec: 187780 usec]	NumberOfPlanes: 1
[1 sec: 187792 usec]	BitsPerPixel: 32
[1 sec: 187803 usec]	NumberOfBanks: 1
[1 sec: 187815 usec]	MemoryModel: 6
[1 sec: 187826 usec]	BankSize: 0
[1 sec: 187838 usec]	NumberOfImages: 2
[1 sec: 187849 usec]	RedMaskSize: 8
[1 sec: 187861 usec]	RedFieldPosition: 16
[1 sec: 187872 usec]	GreenMaskSize: 8
[1 sec: 187884 usec]	GreenFieldPosition: 8
[1 sec: 187895 usec]	BlueMaskSize: 8
[1 sec: 187907 usec]	BlueFieldPosition: 0
[1 sec: 187918 usec]	RsvdMaskSize: 8
[1 sec: 187930 usec]	RsvdFieldPosition: 24
[1 sec: 187942 usec]	DirectColorModeInfo: 0
[1 sec: 187954 usec]	PhysBasePtr: 0xb0000000
[1 sec: 187965 usec]	LinBytesPerScanLine: 2560
[1 sec: 187977 usec]	BnkNumberOfImagePages: 2
[1 sec: 187989 usec]	LinNumberOfImagePages: 2
[1 sec: 188001 usec]	LinRedMaskSize: 8
[1 sec: 188012 usec]	LinRedFieldPosition: 16
[1 sec: 188024 usec]	LinGreenMaskSize: 8
[1 sec: 188036 usec]	LinGreenFieldPosition: 8
[1 sec: 188048 usec]	LinBlueMaskSize: 8
[1 sec: 188060 usec]	LinBlueFieldPosition: 0
[1 sec: 188072 usec]	LinRsvdMaskSize: 8
[1 sec: 188084 usec]	LinRsvdFieldPosition: 24
[1 sec: 188095 usec]	MaxPixelClock: 229500000
[1 sec: 188109 usec]
[1 sec: 188124 usec](II) VESA(0): Total Memory: 4096 64KB banks (262144kB)
[1 sec: 188170 usec](II) VESA(0): Configured Monitor: Using hsync range of 30.00-81.00 kHz
[1 sec: 188194 usec](II) VESA(0): Configured Monitor: Using vrefresh range of 56.00-76.00 Hz
[1 sec: 188214 usec](II) VESA(0): Configured Monitor: Using maximum pixel clock of 170.00 MHz
[1 sec: 188233 usec](WW) VESA(0): Unable to estimate virtual size
[1 sec: 220373 usec](II) VESA(0): Not using built-in mode "640x400" (no mode of this name)
[1 sec: 220399 usec](II) VESA(0): Not using built-in mode "320x400" (no mode of this name)
[1 sec: 220418 usec](II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[1 sec: 220437 usec](II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[1 sec: 220462 usec](--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[1 sec: 220479 usec](**) VESA(0): *Built-in mode "1280x1024"
[1 sec: 220494 usec](**) VESA(0): *Built-in mode "1024x768"
[1 sec: 220508 usec](**) VESA(0): *Built-in mode "800x600"
[1 sec: 220522 usec](**) VESA(0): *Built-in mode "640x480"
[1 sec: 220538 usec](**) VESA(0): Display dimensions: (520, 330) mm
[1 sec: 220552 usec](**) VESA(0): DPI set to (62, 78)
[1 sec: 220575 usec](**) VESA(0): Using "Shadow Framebuffer"
[1 sec: 220589 usec](II) Loading sub module "shadow"
[1 sec: 220602 usec](II) LoadModule: "shadow"[1 sec: 220620 usec]
[1 sec: 220699 usec](II) Loading /usr/lib/xorg/modules//libshadow.so
[1 sec: 221193 usec](II) Module shadow: vendor="X.Org Foundation"
[1 sec: 221225 usec]	compiled for 1.5.99[1 sec: 221237 usec].902[1 sec: 221249 usec], module version = 1.1.0
[1 sec: 221262 usec]	ABI class: X.Org ANSI C Emulation, version 0.4
[1 sec: 221277 usec](II) Loading sub module "fb"
[1 sec: 221291 usec](II) LoadModule: "fb"[1 sec: 221307 usec]
[1 sec: 221393 usec](II) Loading /usr/lib/xorg/modules//libfb.so
[1 sec: 221564 usec](II) Module fb: vendor="X.Org Foundation"
[1 sec: 221580 usec]	compiled for 1.5.99[1 sec: 221592 usec].902[1 sec: 221603 usec], module version = 1.0.0
[1 sec: 221616 usec]	ABI class: X.Org ANSI C Emulation, version 0.4
[1 sec: 221731 usec](==) Depth 24 pixmap format is 32 bpp
[1 sec: 221747 usec](II) do I need RAC?[1 sec: 221759 usec]  No, I don't.
[1 sec: 221771 usec](II) resource ranges after preInit:
[1 sec: 221783 usec]	[0] -1	0	0xffffffff - 0xffffffff (0x1)[1 sec: 221796 usec] M[1 sec: 221807 usec]X[1 sec: 221818 usec][B][1 sec: 221829 usec]
[1 sec: 221840 usec]	[1] -1	0	0x000f0000 - 0x000fffff (0x10000)[1 sec: 221853 usec] M[1 sec: 221864 usec]X[1 sec: 221875 usec][B][1 sec: 221885 usec]
[1 sec: 221896 usec]	[2] -1	0	0x000c0000 - 0x000effff (0x30000)[1 sec: 221909 usec] M[1 sec: 221920 usec]X[1 sec: 221930 usec][B][1 sec: 221941 usec]
[1 sec: 221951 usec]	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000)[1 sec: 221964 usec] M[1 sec: 221975 usec]X[1 sec: 221986 usec][B][1 sec: 221997 usec]
[1 sec: 222007 usec]	[4] -1	0	0x0000ffff - 0x0000ffff (0x1)[1 sec: 222020 usec] I[1 sec: 222031 usec]X[1 sec: 222041 usec][B][1 sec: 222052 usec]
[1 sec: 222062 usec]	[5] -1	0	0x00000000 - 0x00000000 (0x1)[1 sec: 222075 usec] I[1 sec: 222086 usec]X[1 sec: 222096 usec][B][1 sec: 222107 usec]
[1 sec: 222121 usec](II) Loading sub module "int10"
[1 sec: 222135 usec](II) LoadModule: "int10"[1 sec: 222152 usec]
[1 sec: 222245 usec](II) Reloading /usr/lib/xorg/modules//libint10.so
[1 sec: 222268 usec](II) VESA(0): initializing int10
[1 sec: 230680 usec](II) VESA(0): Primary V_BIOS segment is: 0xc000
[1 sec: 264479 usec](II) VESA(0): VESA BIOS detected
[1 sec: 264502 usec](II) VESA(0): VESA VBE Version 3.0
[1 sec: 264517 usec](II) VESA(0): VESA VBE Total Mem: 262144 kB
[1 sec: 264531 usec](II) VESA(0): VESA VBE OEM: NVIDIA
[1 sec: 264545 usec](II) VESA(0): VESA VBE OEM Software Rev: 5.113
[1 sec: 264559 usec](II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
[1 sec: 264573 usec](II) VESA(0): VESA VBE OEM Product: G71 Board - p602h0  
[1 sec: 264587 usec](II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
[1 sec: 266116 usec](II) VESA(0): virtual address = 0xa6985000,
	physical address = 0xb0000000, size = 268435456
[1 sec: 692573 usec](==) VESA(0): Default visual is TrueColor
[1 sec: 697401 usec](==) VESA(0): Backing store disabled
[1 sec: 701059 usec](II) VESA(0): DPMS enabled
[1 sec: 701095 usec](==) RandR enabled
[1 sec: 725363 usec](II) Initializing built-in extension Generic Event Extension
[1 sec: 725384 usec](II) Initializing built-in extension SHAPE
[1 sec: 725398 usec](II) Initializing built-in extension MIT-SHM
[1 sec: 725412 usec](II) Initializing built-in extension XInputExtension
[1 sec: 725425 usec](II) Initializing built-in extension XTEST
[1 sec: 725439 usec](II) Initializing built-in extension BIG-REQUESTS
[1 sec: 725453 usec](II) Initializing built-in extension SYNC
[1 sec: 725466 usec](II) Initializing built-in extension XKEYBOARD
[1 sec: 725479 usec](II) Initializing built-in extension XC-MISC
[1 sec: 725492 usec](II) Initializing built-in extension SECURITY
[1 sec: 725506 usec](II) Initializing built-in extension XINERAMA
[1 sec: 725519 usec](II) Initializing built-in extension XFIXES
[1 sec: 725532 usec](II) Initializing built-in extension RENDER
[1 sec: 725545 usec](II) Initializing built-in extension RANDR
[1 sec: 725558 usec](II) Initializing built-in extension COMPOSITE
[1 sec: 725571 usec](II) Initializing built-in extension DAMAGE
[1 sec: 729215 usec](EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[2 sec: 161385 usec](II) config/hal: Adding input device AT Translated Set 2 keyboard
[2 sec: 161449 usec](II) LoadModule: "evdev"[2 sec: 161477 usec]
[2 sec: 161629 usec](II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
[2 sec: 162234 usec](II) Module evdev: vendor="X.Org Foundation"
[2 sec: 162256 usec]	compiled for 1.5.99[2 sec: 162269 usec].901[2 sec: 162281 usec], module version = 2.1.1
[2 sec: 162294 usec]	Module class: X.Org XInput Driver
[2 sec: 162306 usec]	ABI class: X.Org XInput driver, version 4.0
[2 sec: 162351 usec](**) AT Translated Set 2 keyboard: always reports core events
[2 sec: 162372 usec](**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[2 sec: 168914 usec](II) AT Translated Set 2 keyboard: Found keys
[2 sec: 168933 usec](II) AT Translated Set 2 keyboard: Configuring as keyboard
[2 sec: 168970 usec](II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[2 sec: 169001 usec](**) Option "xkb_rules"[2 sec: 169014 usec] "evdev"[2 sec: 169025 usec]
[2 sec: 169037 usec](**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
[2 sec: 169051 usec](**) Option "xkb_model"[2 sec: 169063 usec] "pc105"[2 sec: 169074 usec]
[2 sec: 169086 usec](**) AT Translated Set 2 keyboard: xkb_model: "pc105"
[2 sec: 169100 usec](**) Option "xkb_layout"[2 sec: 169112 usec] "us"[2 sec: 169123 usec]
[2 sec: 169135 usec](**) AT Translated Set 2 keyboard: xkb_layout: "us"
[2 sec: 249998 usec](II) config/hal: Adding input device Macintosh mouse button emulation
[2 sec: 250085 usec](**) Macintosh mouse button emulation: always reports core events
[2 sec: 250105 usec](**) Macintosh mouse button emulation: Device: "/dev/input/event2"
[2 sec: 256899 usec](II) Macintosh mouse button emulation: Found 3 mouse buttons
[2 sec: 256918 usec](II) Macintosh mouse button emulation: Found x and y relative axes
[2 sec: 256932 usec](II) Macintosh mouse button emulation: Configuring as mouse
[2 sec: 256957 usec](**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[2 sec: 256974 usec](**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[2 sec: 257002 usec](II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[2 sec: 257051 usec](**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[2 sec: 257069 usec](**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
[2 sec: 257089 usec](**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
[2 sec: 257115 usec](**) Macintosh mouse button emulation: (accel) set acceleration profile 0
[2 sec: 259722 usec](II) config/hal: Adding input device Microsoft Microsoft Wireless Optical Desktop? 1.00
[2 sec: 259769 usec](**) Microsoft Microsoft Wireless Optical Desktop? 1.00: always reports core events
[2 sec: 259787 usec](**) Microsoft Microsoft Wireless Optical Desktop? 1.00: Device: "/dev/input/event5"
[2 sec: 264902 usec](II) Microsoft Microsoft Wireless Optical Desktop? 1.00: Found 5 mouse buttons
[2 sec: 264921 usec](II) Microsoft Microsoft Wireless Optical Desktop? 1.00: Found x and y relative axes
[2 sec: 264935 usec](II) Microsoft Microsoft Wireless Optical Desktop? 1.00: Configuring as mouse
[2 sec: 264958 usec](**) Microsoft Microsoft Wireless Optical Desktop? 1.00: YAxisMapping: buttons 4 and 5
[2 sec: 264974 usec](**) Microsoft Microsoft Wireless Optical Desktop? 1.00: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[2 sec: 264999 usec](II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Desktop? 1.00" (type: MOUSE)
[2 sec: 265032 usec](**) Microsoft Microsoft Wireless Optical Desktop? 1.00: (accel) keeping acceleration scheme 1
[2 sec: 265048 usec](**) Microsoft Microsoft Wireless Optical Desktop? 1.00: (accel) filter chain progression: 2.00
[2 sec: 265066 usec](**) Microsoft Microsoft Wireless Optical Desktop? 1.00: (accel) filter stage 0: 20.00 ms
[2 sec: 265091 usec](**) Microsoft Microsoft Wireless Optical Desktop? 1.00: (accel) set acceleration profile 0
[2 sec: 266886 usec](II) config/hal: Adding input device Logitech USB-PS/2 Optical Mouse
[2 sec: 266945 usec](**) Logitech USB-PS/2 Optical Mouse: always reports core events
[2 sec: 266964 usec](**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
[2 sec: 272898 usec](II) Logitech USB-PS/2 Optical Mouse: Found 8 mouse buttons
[2 sec: 272917 usec](II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
[2 sec: 272931 usec](II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
[2 sec: 272953 usec](**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
[2 sec: 272970 usec](**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[2 sec: 272994 usec](II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
[2 sec: 273025 usec](**) Logitech USB-PS/2 Optical Mouse: (accel) keeping acceleration scheme 1
[2 sec: 273041 usec](**) Logitech USB-PS/2 Optical Mouse: (accel) filter chain progression: 2.00
[2 sec: 273059 usec](**) Logitech USB-PS/2 Optical Mouse: (accel) filter stage 0: 20.00 ms
[2 sec: 273085 usec](**) Logitech USB-PS/2 Optical Mouse: (accel) set acceleration profile 0
```

---

### Post by minisori on 2009-02-06
> [1 sec: 729215 usec](EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


Check what i told you about the nvidia kernel module and the x driver, it smells like the problem.

---

### Post by dk75 on 2009-02-07
BinaryApe@ are you sure it's good idea to install drivers from [http://ppa.launchpad.net/anders-kaseorg/ubuntu](http://ppa.launchpad.net/anders-kaseorg/ubuntu)? I've searched it manually and it have packages information for 9.04 but real DEB pakages is for 8.10 and... not labeled.
I wonder, maybe these drivers are the core of the problem.
Did you ever tryed to run nVidia drivers compilation&installation script instead?

Besides - didn't 9.04 have it's own official repo for 180 drivers? I've thought that meddling with some private launchpad.ppa isn't needed at it anymore.

---

### Post by BinaryApe on 2009-02-07
I did install from the PPA earlier and it worked fine. This is when the repo had the 177 issue and was removing the Xorg. I have removed it since then and done the official repo which still causes issue. I have also downloaded straight from Nvidia the 180.22 (on their site) to install it.

I have tried several drivers and config files and getting the same issue.

---

### Post by dk75 on 2009-02-07
I've read that 180.27 probably work... or probably one need to add "Option DisableABI" to "xorg.conf"... It seems that I need to install 9.04 on a spare partition and test it. ;P
It's about a time to test new Ubuntu... alpha4 is available.

---

### Post by Kevbert on 2009-02-07
> **dk75 said:**
> I've read that 180.27 probably work... or probably one need to add "Option DisableABI" to "xorg.conf"... It seems that I need to install 9.04 on a spare partition and test it. ;P
It's about a time to test new Ubuntu... alpha4 is available.
180.27 seems to work fine with my 7600GS card - no added option required.

---

### Post by hype on 2009-02-07
If you use Nvidia 180.27 driver, you wont be able able to go after gdm login screen.

Compiz doesnt support direct rendering anymore due to some X server changes.

So if you are stuck after gdm, just switch to a tty, and kill compiz.
I perosnnaly used htop.

You'll hear the login sound.

Switch back to TTY7 and , using fusion icon, set compiz options to "indirect rendering" and "loose binding".

That works quite sufficently for me, at least for the moment :)

---

### Post by Kevbert on 2009-02-07
> **hype said:**
> If you use Nvidia 180.27 driver, you wont be able able to go after gdm login screen.

Compiz doesnt support direct rendering anymore due to some X server changes.

So if you are stuck after gdm, just switch to a tty, and kill compiz.
I perosnnaly used htop.

You'll hear the login sound.

Switch back to TTY7 and , using fusion icon, set compiz options to "indirect rendering" and "loose binding".

That works quite sufficently for me, at least for the moment :)

The latest updates/changes today have also caused my Nvidia display to stop working (another thread) and I'm not using compiz !

---

