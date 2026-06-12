---
title: "hardlocks in gui"
date: 2008-09-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by of_darkness on 2008-09-07
64bit intrepid: both gdm and kdm(3.5* version) is hardlocking  after nvidia 177 install and subsequent removal in rescue shell.

and its happening both in the 2.6.26 and 2.6.27 kernel

gdm totaly locks upp just shows the brown screan whit a round clock like mouse pointer thats totaly frozen. ctrl alt delete dosent work.

kdm gets as far as login screen but its frozen no keeboard or mouse input.
i have purged all nvidia packages.

if it has any relvance i have kde3*packages from hardy installed from clean env. then pinned down and the removed hardy repos.


tried reconfigure -all but no luck.

motherboard is a msi p35 neo
8gb ram in 4 mathced stics.

msi nx8400gs graphics card.

monitor is a 20 ich lg L204WT contected by both d-sub and and dvi

xorg.0.log
```
(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.99.906 (1.5.0 RC 6)
Release Date: 
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-15-server x86_64 Ubuntu
Current Operating System: Linux Kurald-Galain 2.6.26-5-generic #1 SMP Fri Aug 15 13:54:22 UTC 2008 x86_64
Build Date: 03 September 2008  01:25:10PM
xorg-server 2:1.4.99.906-2ubuntu5 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Sep  7 21:29:53 2008
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
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 4.1
    X.Org XInput driver : 2.1
    X.Org Server Extension : 1.1
    X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation GeForce 8400 GS rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(--) PCI: (0@5:0:0) Internext Compression Inc iTVC15 MPEG-2 Encoder rev 1, Mem @ 0xf4000000/67108864
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
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
    compiled for 1.4.99.906, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.99.906, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
    ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(==) Matched nv for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "nv"

(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
    compiled for 1.4.99.905, module version = 2.1.10
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 4.1
(II) NV: driver for NVIDIA chipsets: RIVA 128, RIVA TNT, RIVA TNT2,
    Unknown TNT2, Vanta, RIVA TNT2 Ultra, RIVA TNT2 Model 64,
    Aladdin TNT2, GeForce 256, GeForce DDR, Quadro, GeForce2 MX/MX 400,
    GeForce2 MX 100/200, GeForce2 Go, Quadro2 MXR/EX/Go,
    GeForce2 Integrated GPU, GeForce2 GTS, GeForce2 Ti, GeForce2 Ultra,
    Quadro2 Pro, GeForce4 MX 460, GeForce4 MX 440, GeForce4 MX 420,
    GeForce4 MX 440-SE, GeForce4 440 Go, GeForce4 420 Go,
    GeForce4 420 Go 32M, GeForce4 460 Go, Quadro4 550 XGL,
    GeForce4 440 Go 64M, Quadro NVS, Quadro4 500 GoGL,
    GeForce4 410 Go 16M, GeForce4 MX 440 with AGP8X,
    GeForce4 MX 440SE with AGP8X, GeForce4 MX 420 with AGP8X,
    GeForce4 MX 4000, GeForce4 448 Go, GeForce4 488 Go, Quadro4 580 XGL,
    Quadro4 NVS 280 SD, Quadro4 380 XGL, Quadro NVS 50 PCI,
    GeForce4 448 Go, GeForce4 MX Integrated GPU, GeForce3,
    GeForce3 Ti 200, GeForce3 Ti 500, Quadro DCC, GeForce4 Ti 4600,
    GeForce4 Ti 4400, GeForce4 Ti 4200, Quadro4 900 XGL, Quadro4 750 XGL,
    Quadro4 700 XGL, GeForce4 Ti 4800, GeForce4 Ti 4200 with AGP8X,
    GeForce4 Ti 4800 SE, GeForce4 4200 Go, Quadro4 700 GoGL,
    Quadro4 980 XGL, Quadro4 780 XGL, GeForce FX 5800 Ultra,
    GeForce FX 5800, Quadro FX 2000, Quadro FX 1000,
    GeForce FX 5600 Ultra, GeForce FX 5600, GeForce FX 5600XT,
    GeForce FX Go5600, GeForce FX Go5650, Quadro FX Go700,
    GeForce FX 5200, GeForce FX 5200 Ultra, GeForce FX 5200,
    GeForce FX 5200LE, GeForce FX Go5200, GeForce FX Go5250,
    GeForce FX 5500, GeForce FX 5100, GeForce FX Go5200 32M/64M,
    Quadro NVS 55/280 PCI, Quadro FX 500/600 PCI,
    GeForce FX Go53xx Series, GeForce FX Go5100, GeForce FX 5900 Ultra,
    GeForce FX 5900, GeForce FX 5900XT, GeForce FX 5950 Ultra,
    GeForce FX 5900ZT, Quadro FX 3000, Quadro FX 700,
    GeForce FX 5700 Ultra, GeForce FX 5700, GeForce FX 5700LE,
    GeForce FX 5700VE, GeForce FX Go5700, GeForce FX Go5700,
    Quadro FX Go1000, Quadro FX 1100, GeForce 6800 Ultra, GeForce 6800,
    GeForce 6800 LE, GeForce 6800 XE, GeForce 6800 XT, GeForce 6800 GT,
    GeForce 6800 GT, GeForce 6800 GS, GeForce 6800 XT, Quadro FX 4000,
    GeForce 6800 GS, GeForce 6800, GeForce 6800 LE, GeForce 6800 XT,
    GeForce Go 6800, GeForce Go 6800 Ultra, Quadro FX Go1400,
    Quadro FX 3450/4000 SDI, Quadro FX 1400, GeForce 6600 GT,
    GeForce 6600, GeForce 6600 LE, GeForce 6600 VE, GeForce Go 6600,
    GeForce 6610 XL, GeForce Go 6600 TE/6200 TE, GeForce 6700 XL,
    GeForce Go 6600, GeForce Go 6600 GT, Quadro FX 550, Quadro FX 550,
    Quadro FX 540, GeForce 6200, GeForce 6500,
    GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
    GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
    GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 6800,
    GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT, GeForce 6200,
    GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
    GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
    GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7300 LE,
    GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300, GeForce Go 7400,
    GeForce Go 7400 GS, Quadro NVS 110M, Quadro NVS 120M, Quadro FX 350M,
    GeForce 7500 LE, Quadro FX 350, GeForce 7300 GS, GeForce 7600 GT,
    GeForce 7600 GS, GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT,
    GeForce Go 7700, GeForce Go 7600, GeForce Go 7600 GT,
    Quadro NVS 300M, GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560,
    GeForce 7900 GTX, GeForce 7900 GT, GeForce 7900 GS,
    GeForce Go 7900 GS, GeForce Go 7900 GTX, Quadro FX 2500M,
    Quadro FX 1500M, Quadro FX 5500, Quadro FX 3500, Quadro FX 1500,
    Quadro FX 4500 X2, GeForce 6150, GeForce 6150 LE, GeForce 6100,
    GeForce Go 6150, GeForce Go 6100, GeForce 8800 GTX, GeForce 8800 GTS,
    GeForce 8800 Ultra, Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS,
    GeForce 8600 GT, GeForce 8600 GT, GeForce 8400 GS, GeForce 9500M GS,
    GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
    Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
    Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
    GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
    GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
    Quadro NVS 135M, Quadro FX 360M, GeForce 9300M G, Quadro NVS 290,
    GeForce GTX 280, GeForce GTX 260, GeForce 8800 GTS 512,
    GeForce 8800 GT, GeForce 9800 GX2, GeForce 8800 GS,
    GeForce 8800M GTS, GeForce 8800M GTX, GeForce 8800 GS,
    GeForce 9600 GSO, GeForce 8800 GT, GeForce 9800 GTX, Quadro FX 3700,
    Quadro FX 3600M, GeForce 9600 GT, GeForce 9600M GT, GeForce 9600M GS,
    GeForce 9600M GT, GeForce 9500M G, GeForce 8400 GS, GeForce 9300M GS,
    GeForce 9200M GS, GeForce 9300M GS
(II) Primary Device is: PCI 01@00:00:0
(--) NV: Found NVIDIA GeForce 8400 GS at 01@00:00:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
    ABI class: X.Org Video Driver, version 4.1
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Console is VGA mode 0x3
(II) NV(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) NV(0): Depth 24, (==) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(==) NV(0): Using hardware cursor
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): MMIO registers mapped at 0x7fcda4050000
(--) NV(0): Total video RAM: 256.0 MB
(--) NV(0):       BAR1 size: 256.0 MB
(--) NV(0):   Mapped memory: 255.0 MB
(II) NV(0): Linear framebuffer mapped at 0x7fcd94150000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(--) NV(0): Connector map:
(--) NV(0):   Bus 0 -> DAC1
(--) NV(0):   Bus 0 -> SOR0
(--) NV(0):   Bus 1 -> DAC0
(--) NV(0): Load detection: 340
(II) NV(0): I2C bus "I2C0" initialized.
(II) NV(0): Output VGA1 using monitor section Configured Monitor
(II) NV(0): Output DVI0 has no monitor section
(II) NV(0): I2C bus "I2C1" initialized.
(II) NV(0): Output VGA0 has no monitor section
(II) NV(0): Probing for EDID on I2C bus 0...
(II) NV(0): I2C device "I2C0:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: GSM  Model: 4e48  Serial#: 14781
(II) NV(0): Year: 2006  Week: 12
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off(II) NV(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.651 redY: 0.333   greenX: 0.277 greenY: 0.614
(II) NV(0): blueX: 0.145 blueY: 0.082   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  434 x 270 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: L204WT
(II) NV(0): Monitor name: 
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff001e6d484ebd390000
(II) NV(0):     0c100103ea2b1b78ead105a655479d25
(II) NV(0):     155054a76b80010181808140714f0101
(II) NV(0):     01010101010121399030621a274068b0
(II) NV(0):     3600b20e1100001c000000fd00384b1c
(II) NV(0):     530f000a202020202020000000fc004c
(II) NV(0):     32303457540a202020202020000000fc
(II) NV(0):     000a20202020202020202020202000b3
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID vendor "GSM", prod id 20040
(II) NV(0): Probing for EDID on I2C bus 1...
(II) NV(0): I2C device "I2C1:ddc2" registered at address 0xA0.
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GSM  Model: 4e47  Serial#: 14781
(II) NV(0): Year: 2006  Week: 12
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate  SyncOnGreen
(II) NV(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.651 redY: 0.333   greenX: 0.277 greenY: 0.614
(II) NV(0): blueX: 0.145 blueY: 0.082   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  434 x 270 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: L204WT
(II) NV(0): Monitor name: 
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff001e6d474ebd390000
(II) NV(0):     0c1001036a2b1b78ead105a655479d25
(II) NV(0):     155054a76b80010181808140714f0101
(II) NV(0):     01010101010121399030621a274068b0
(II) NV(0):     3600b20e1100001c000000fd00384b1c
(II) NV(0):     530f000a202020202020000000fc004c
(II) NV(0):     32303457540a202020202020000000fc
(II) NV(0):     000a2020202020202020202020200034
(--) NV(0): Trying load detection on VGA0 ... found one!
(II) NV(0): EDID vendor "GSM", prod id 20039
(II) NV(0): Output VGA1 disconnected
(II) NV(0): Output DVI0 connected
(II) NV(0): Output VGA0 connected
(II) NV(0): Using exact sizes for initial modes
(II) NV(0): Output DVI0 using initial mode 1680x1050
(II) NV(0): Output VGA0 using initial mode 1680x1050
(--) NV(0): Virtual size is 1680x1680 (pitch 1792)
(**) NV(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
(II) NV(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
(**) NV(0):  Default mode "1600x1024": 103.1 MHz (scaled from 0.0 MHz), 62.0 kHz, 60.2 Hz
(II) NV(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(**) NV(0):  Default mode "1400x1050": 145.1 MHz (scaled from 0.0 MHz), 76.5 kHz, 70.0 Hz
(II) NV(0): Modeline "1400x1050"x70.0  145.06  1400 1496 1648 1896  1050 1051 1054 1093 -hsync +vsync (76.5 kHz)
(**) NV(0):  Default mode "1400x1050": 122.0 MHz (scaled from 0.0 MHz), 64.9 kHz, 60.0 Hz
(II) NV(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(**) NV(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NV(0):  Driver mode "1280x1024": 108.9 MHz (scaled from 0.0 MHz), 63.6 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(**) NV(0):  Default mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NV(0):  Default mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
(II) NV(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) NV(0):  Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NV(0):  Driver mode "1280x960": 102.1 MHz (scaled from 0.0 MHz), 59.6 kHz, 60.0 Hz
(II) NV(0): Modeline "1280x960"x60.0  102.10  1280 1360 1496 1712  960 961 964 994 -hsync +vsync (59.6 kHz)
(**) NV(0):  Default mode "1360x768": 84.8 MHz (scaled from 0.0 MHz), 47.7 kHz, 59.8 Hz
(II) NV(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) NV(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NV(0):  Driver mode "1152x864": 105.0 MHz (scaled from 0.0 MHz), 67.7 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(**) NV(0):  Default mode "1152x864": 105.0 MHz (scaled from 0.0 MHz), 67.6 kHz, 75.0 Hz
(II) NV(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) NV(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) NV(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) NV(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) NV(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) NV(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
(II) NV(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(**) NV(0):  Default mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) NV(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NV(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NV(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NV(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NV(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NV(0):  Default mode "896x672": 102.4 MHz (scaled from 0.0 MHz), 83.7 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "896x672"x60.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz)
(**) NV(0):  Default mode "960x600": 77.0 MHz (scaled from 0.0 MHz), 74.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "960x600"x60.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz)
(**) NV(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) NV(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NV(0):  Default mode "960x540": 69.2 MHz (scaled from 0.0 MHz), 66.6 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "960x540"x60.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz)
(**) NV(0):  Default mode "800x600": 87.8 MHz (scaled from 0.0 MHz), 81.2 kHz, 65.0 Hz (D)
(II) NV(0): Modeline "800x600"x65.0   87.75  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (81.2 kHz)
(**) NV(0):  Default mode "800x600": 81.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "800x600"x60.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz)
(**) NV(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NV(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NV(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NV(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NV(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NV(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NV(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NV(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NV(0):  Default mode "840x525": 93.5 MHz (scaled from 0.0 MHz), 82.3 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "840x525"x75.0   93.50  840 900 988 1136  525 526 529 549 doublescan -hsync +vsync (82.3 kHz)
(**) NV(0):  Default mode "840x525": 87.0 MHz (scaled from 0.0 MHz), 76.6 kHz, 69.9 Hz (D)
(II) NV(0): Modeline "840x525"x69.9   87.00  840 900 988 1136  525 526 529 548 doublescan -hsync +vsync (76.6 kHz)
(**) NV(0):  Default mode "840x525": 73.1 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "840x525"x60.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz)
(**) NV(0):  Default mode "840x525": 59.5 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz (D)
(II) NV(0): Modeline "840x525"x59.9   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz)
(**) NV(0):  Default mode "800x512": 51.6 MHz (scaled from 0.0 MHz), 62.0 kHz, 60.2 Hz (D)
(II) NV(0): Modeline "800x512"x60.2   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz)
(**) NV(0):  Default mode "700x525": 77.9 MHz (scaled from 0.0 MHz), 81.5 kHz, 74.8 Hz (D)
(II) NV(0): Modeline "700x525"x74.8   77.90  700 732 892 956  525 526 532 545 doublescan +hsync +vsync (81.5 kHz)
(**) NV(0):  Default mode "700x525": 72.5 MHz (scaled from 0.0 MHz), 76.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "700x525"x70.1   72.53  700 748 824 948  525 525 527 546 doublescan -hsync +vsync (76.5 kHz)
(**) NV(0):  Default mode "700x525": 61.0 MHz (scaled from 0.0 MHz), 64.9 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "700x525"x60.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz)
(**) NV(0):  Default mode "640x512": 67.5 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "640x512"x75.0   67.50  640 648 720 844  512 512 514 533 doublescan +hsync +vsync (80.0 kHz)
(**) NV(0):  Default mode "640x512": 54.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x512"x60.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz)
(**) NV(0):  Default mode "720x450": 53.2 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz (D)
(II) NV(0): Modeline "720x450"x59.9   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz)
(**) NV(0):  Default mode "640x480": 54.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "640x480"x60.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NV(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NV(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NV(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NV(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
(II) NV(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NV(0):  Default mode "680x384": 42.4 MHz (scaled from 0.0 MHz), 47.7 kHz, 59.8 Hz (D)
(II) NV(0): Modeline "680x384"x59.8   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz)
(**) NV(0):  Default mode "680x384": 36.0 MHz (scaled from 0.0 MHz), 47.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "680x384"x60.0   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz)
(**) NV(0):  Default mode "576x432": 54.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   54.00  576 608 672 800  432 432 434 450 doublescan +hsync +vsync (67.5 kHz)
(**) NV(0):  Default mode "576x432": 52.5 MHz (scaled from 0.0 MHz), 67.6 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "576x432"x75.0   52.49  576 612 676 776  432 432 434 451 doublescan -hsync +vsync (67.6 kHz)
(**) NV(0):  Default mode "576x432": 48.4 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz (D)
(II) NV(0): Modeline "576x432"x70.0   48.38  576 612 672 768  432 432 434 450 doublescan -hsync +vsync (63.0 kHz)
(**) NV(0):  Default mode "576x432": 40.8 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "576x432"x60.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz)
(**) NV(0):  Default mode "512x384": 39.4 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz (D)
(II) NV(0): Modeline "512x384"x75.0   39.38  512 520 568 656  384 384 386 400 doublescan +hsync +vsync (60.0 kHz)
(**) NV(0):  Default mode "512x384": 37.5 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz (D)
(II) NV(0): Modeline "512x384"x70.1   37.50  512 524 592 664  384 385 388 403 doublescan -hsync -vsync (56.5 kHz)
(**) NV(0):  Default mode "512x384": 32.5 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz (D)
(II) NV(0): Modeline "512x384"x60.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz)
(**) NV(0):  Default mode "416x312": 28.6 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.7 Hz (D)
(II) NV(0): Modeline "416x312"x74.7   28.64  416 432 464 576  312 312 314 333 doublescan -hsync -vsync (49.7 kHz)
(**) NV(0):  Default mode "400x300": 25.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz (D)
(II) NV(0): Modeline "400x300"x72.2   25.00  400 428 488 520  300 318 321 333 doublescan +hsync +vsync (48.1 kHz)
(==) NV(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"

(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 1.2.0
    ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(--) NV(0): 212.51 MB available for offscreen pixmaps
(II) NV(0): Using XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    Indirect CPU to Screen color expansion
    Solid Lines
    Scanline Image Writes
    Setting up tile and stipple cache:
        32 128x128 slots
        32 256x256 slots
        16 512x512 slots
(==) NV(0): Backing store disabled
(==) NV(0): Silken mouse enabled
(II) NV(0): DPMS enabled
(II) NV(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NV(0): Setting screen physical size to 434 x 270
(II) config/hal: Adding input device ImExPS/2 Logitech MX Mouse
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.4.99.906, module version = 2.0.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.1
(**) ImExPS/2 Logitech MX Mouse: always reports core events
(**) ImExPS/2 Logitech MX Mouse: Device: "/dev/input/event4"
(II) ImExPS/2 Logitech MX Mouse: Found x and y relative axes
(II) ImExPS/2 Logitech MX Mouse: Found mouse buttons
(II) ImExPS/2 Logitech MX Mouse: Configuring as mouse
(II) XINPUT: Adding extended input device "ImExPS/2 Logitech MX Mouse" (type: MOUSE)
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event1"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "base"
(**) AT Translated Set 2 keyboard: xkb_rules: "base"
(**) Option "xkb_model" "evdev"
(**) AT Translated Set 2 keyboard: xkb_model: "evdev"
(**) Option "xkb_layout" "se"
(**) AT Translated Set 2 keyboard: xkb_layout: "se"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) AT Translated Set 2 keyboard: xkb_options: "lv3:ralt_switch"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) NV(0): Probing for EDID on I2C bus 0...
(--) NV(0): DDC detected a DFP:
(II) NV(0): Manufacturer: GSM  Model: 4e48  Serial#: 14781
(II) NV(0): Year: 2006  Week: 12
(II) NV(0): EDID Version: 1.3
(II) NV(0): Digital Display Input
(II) NV(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off(II) NV(0): 
Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.651 redY: 0.333   greenX: 0.277 greenY: 0.614
(II) NV(0): blueX: 0.145 blueY: 0.082   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  434 x 270 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: L204WT
(II) NV(0): Monitor name: 
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff001e6d484ebd390000
(II) NV(0):     0c100103ea2b1b78ead105a655479d25
(II) NV(0):     155054a76b80010181808140714f0101
(II) NV(0):     01010101010121399030621a274068b0
(II) NV(0):     3600b20e1100001c000000fd00384b1c
(II) NV(0):     530f000a202020202020000000fc004c
(II) NV(0):     32303457540a202020202020000000fc
(II) NV(0):     000a20202020202020202020202000b3
(--) NV(0): Trying load detection on VGA1 ... nothing.
(II) NV(0): EDID vendor "GSM", prod id 20040
(II) NV(0): Probing for EDID on I2C bus 1...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: GSM  Model: 4e47  Serial#: 14781
(II) NV(0): Year: 2006  Week: 12
(II) NV(0): EDID Version: 1.3
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate  SyncOnGreen
(II) NV(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): redX: 0.651 redY: 0.333   greenX: 0.277 greenY: 0.614
(II) NV(0): blueX: 0.145 blueY: 0.082   whiteX: 0.313 whiteY: 0.329
(II) NV(0): Supported VESA Video Modes:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@56Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 832x624@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): 1152x870@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported Future Video Modes:
(II) NV(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) NV(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): Supported additional Video Mode:
(II) NV(0): clock: 146.2 MHz   Image Size:  434 x 270 mm
(II) NV(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) NV(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) NV(0): Ranges: V min: 56 V max: 75 Hz, H min: 28 H max: 83 kHz, PixClock max 150 MHz
(II) NV(0): Monitor name: L204WT
(II) NV(0): Monitor name: 
(II) NV(0): EDID (in hex):
(II) NV(0):     00ffffffffffff001e6d474ebd390000
(II) NV(0):     0c1001036a2b1b78ead105a655479d25
(II) NV(0):     155054a76b80010181808140714f0101
(II) NV(0):     01010101010121399030621a274068b0
(II) NV(0):     3600b20e1100001c000000fd00384b1c
(II) NV(0):     530f000a202020202020000000fc004c
(II) NV(0):     32303457540a202020202020000000fc
(II) NV(0):     000a2020202020202020202020200034
(--) NV(0): Trying load detection on VGA0 ... 
```

---

