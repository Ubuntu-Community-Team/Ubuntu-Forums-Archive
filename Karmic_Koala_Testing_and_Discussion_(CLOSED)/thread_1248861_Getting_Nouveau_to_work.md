---
title: "Getting Nouveau to work"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-08-24
Having installed nouveau from the Karmic repos, and edited xorg.conf to use nouveau in 'drivers', I boot into a Black screen. I have completely removed nvidia binary from the system and deleted legacy .ko files in lib/modules. I have also searched the net and the 'Black Screen' issue pops up a lot but i have yet to find a solution that solves my problem. I have since changed xorg.conf to use 'nv' and it has given me about 2/3 of the screen to work with so things are'nt terrible :)

any sage assistance ? i'd like to stick with nouveau if i can. My chipset is an onboard GeForce6 series.

Thanks for any help.

---

### Post by taavikko on 2009-08-24
Check the /var/log/Xorg.[0-9].log* for clues.

I had an issue during jaunty cycle with nouveau and GF6800
[https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/361594](https://bugs.edge.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/361594)

though that laptop isn't at my possession at this time, so cannot test...
Damn poor relatives :D

---

### Post by Regenweald on 2009-08-24
Hate to do this but, i'll post the log. I noticed 'hsync out of range' among other things for 1400by900 which is my max res.
But typically once i install and edit the .conf to say 'nouveau' should that be it ?
```

X.Org X Server 1.6.3
Release Date: 2009-7-31
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux Horsford 2.6.31-6-generic #26-Ubuntu SMP Fri Aug 21 17:55:00 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-6-generic root=UUID=09b65342-1923-4a58-93e7-dc8e35fcddbb ro quiet splash
Build Date: 19 August 2009  05:56:23PM
xorg-server 2:1.6.3-1ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 24 16:39:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:13:0) 10de:03d0:1028:020e nVidia Corporation C61 [GeForce 6150SE nForce 430] rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
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
	compiled for 1.6.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 2.1.14
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
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
	GeForce Go 6600, GeForce Go 6600 GT, Quadro NVS 440, Quadro FX 550,
	Quadro FX 550, Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT,
	GeForce 6200, GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7350 LE,
	GeForce 7300 LE, GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300,
	GeForce Go 7400, GeForce Go 7400 GS, Quadro NVS 110M,
	Quadro NVS 120M, Quadro FX 350M, GeForce 7500 LE, Quadro FX 350,
	GeForce 7300 GS, GeForce 7650 GS, GeForce 7600 GT, GeForce 7600 GS,
	GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT, GeForce Go 7700,
	GeForce Go 7600, GeForce Go 7600 GT, Quadro NVS 300M,
	GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560, GeForce 7900 GTX,
	GeForce 7900 GT, GeForce 7900 GS, GeForce 7950 GX2, GeForce 7950 GX2,
	GeForce 7950 GT, GeForce Go 7950 GTX, GeForce Go 7900 GS,
	GeForce Go 7900 GTX, Quadro FX 2500M, Quadro FX 1500M,
	Quadro FX 5500, Quadro FX 3500, Quadro FX 1500, Quadro FX 4500 X2,
	GeForce 6150, GeForce 6150 LE, GeForce 6100, GeForce Go 6150,
	Quadro NVS 210S / NVIDIA GeForce 6150LE, GeForce Go 6100,
	GeForce 6150SE, GeForce 6100 nForce 405, GeForce 6100 nForce 400,
	GeForce 6100 nForce 420, GeForce 7025, GeForce 7050,
	GeForce 8800 GTX, GeForce 8800 GTS, GeForce 8800 Ultra,
	Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS, GeForce 8600 GT,
	GeForce 8600 GT, GeForce 8600 GS, GeForce 8400 GS, GeForce 9500M GS,
	GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
	Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
	Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, GeForce 9400 GT, Quadro FX 360M, GeForce 9300M G,
	Quadro NVS 290, GeForce GTX 295, GeForce GTX 280, GeForce GTX 260,
	GeForce GTX 285, Quadro CX, Quadro FX 5800, Quadro FX 4800,
	Quadro FX 3800, GeForce 8800 GTS 512, GeForce 9800 GT,
	GeForce 8800 GT, GeForce 9800 GX2, GeForce 9800 GT, GeForce 8800 GS,
	GeForce 9800M GTX, GeForce 8800M GTS, GeForce 9800M GT,
	GeForce 8800M GTX, GeForce 8800 GS, GeForce 9600 GSO,
	GeForce 8800 GT, GeForce 9800 GTX, GeForce 9800 GTX+,
	GeForce 9800 GT, GeForce GTS 250, GeForce 9800M GTX, Quadro FX 3700,
	Quadro FX 3600M, Quadro FX 3700M, GeForce 9600 GT, GeForce 9600 GS,
	GeForce 9600 GSO 512, GeForce GT 130, GeForce GT 140,
	GeForce 9800M GTS, GeForce 9700M GTS, GeForce 9800M GS,
	GeForce 9800M GTS, Quadro FX 1800, Quadro FX 2700M, GeForce 9500 GT,
	GeForce 9400 GT, GeForce 9500 GT, GeForce GT 120, GeForce 9600M GT,
	GeForce 9600M GS, GeForce 9600M GT, GeForce 9700M GT,
	GeForce 9500M G, GeForce 9650M GT, GeForce 9500 GT, Quadro FX 380,
	Quadro FX 580, Quadro FX 770M, GeForce 9300 GE, GeForce 9300 GS,
	GeForce 8400 GS, GeForce 9300M GS, GeForce G100, GeForce 9200M GS,
	GeForce 9300M GS, Quadro NVS 150M, Quadro NVS 160M, Quadro NVS 420,
	Quadro FX 370 LP, Quadro NVS 450, Quadro NVS 295
(II) Primary Device is: PCI 00@00:0d:0
(--) NV: Found NVIDIA GeForce 6150SE at 00@00:0d:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 6150SE"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE0000000
(--) NV(0): MMIO registers at 0xFB000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: DEL  Model: d017  Serial#: 825641800
(II) NV(0): Year: 2007  Week: 37
(II) NV(0): EDID Version: 1.4
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate  SyncOnGreen
(II) NV(0): Max Image Size [cm]: horiz.: 37  vert.: 23
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): Preferred mode is native pixel format and refresh rate
(II) NV(0): Display is continuous-frequency
(II) NV(0): redX: 0.650 redY: 0.331   greenX: 0.317 greenY: 0.568
(II) NV(0): blueX: 0.146 blueY: 0.091   whiteX: 0.312 whiteY: 0.328
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 88.8 MHz   Image Size:  370 x 230 mm
(II) NV(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
(II) NV(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
(II) NV(0): Serial No: PK25679A16KH
(II) NV(0): Ranges: V min: 50 V max: 77 Hz, H min: 30 H max: 83 kHz, PixClock max 129000 kHz
(II) NV(0): Maximum pixel width: 4136
(II) NV(0): Supported aspect ratios: 4:3 16:9 16:10* 5:4 15:9
(II) NV(0): Supported blankings: standard reduced
(II) NV(0): Supported scalings: hshrink hstretch vshrink vstretch
(II) NV(0): Preferred refresh rate: 0
(II) NV(0): Monitor name: DELL SE178WFP
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff0010ac17d0484b3631
(II) NV(0): 	251101046a251778efb690a654519125
(II) NV(0): 	175054a54b008180714f950001010101
(II) NV(0): 	010101010101ab22a0a050841a303020
(II) NV(0): 	360072e61000001a000000ff00504b32
(II) NV(0): 	353637394131364b480a000000fd0032
(II) NV(0): 	4d1e530e0411b205f858f000000000fc
(II) NV(0): 	0044454c4c2053453137385746500047
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): EDID vendor "DEL", prod id 53271
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Monitor0: Using hsync range of 28.00-33.00 kHz
(II) NV(0): Monitor0: Using vrefresh range of 43.00-72.00 Hz
(II) NV(0): Monitor0: Using maximum pixel clock of 129.00 MHz
(II) NV(0): Estimated virtual size for aspect ratio 0.0000 is 1440x900
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (hsync out of range)
(II) NV(0): Not using default mode "320x175" (hsync out of range)
(II) NV(0): Not using default mode "640x400" (hsync out of range)
(II) NV(0): Not using default mode "320x200" (hsync out of range)
(II) NV(0): Not using default mode "720x400" (hsync out of range)
(II) NV(0): Not using default mode "360x200" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (height too large for virtual size)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (height too large for virtual size)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) NV(0): Not using default mode "960x540" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1440x900" (hsync out of range)
(II) NV(0): Not using driver mode "800x600" (hsync out of range)
(II) NV(0): Not using driver mode "640x480" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using driver mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "800x600" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using driver mode "1152x864" (hsync out of range)
(II) NV(0): Not using driver mode "1440x900" (hsync out of range)
(WW) NV(0): Shrinking virtual size estimate from 1440x900 to 640x480
(--) NV(0): Virtual size is 640x480 (pitch 640)
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) NV(0): Display dimensions: (370, 230) mm
(**) NV(0): DPI set to (43, 53)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(**) Option "dpms"
(**) NV(0): DPMS enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Logitech BT Mini-Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 2.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech BT Mini-Receiver: always reports core events
(**) Logitech BT Mini-Receiver: Device: "/dev/input/event5"
(II) Logitech BT Mini-Receiver: Found keys
(II) Logitech BT Mini-Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Logitech BT Mini-Receiver
(**) Logitech BT Mini-Receiver: always reports core events
(**) Logitech BT Mini-Receiver: Device: "/dev/input/event6"
(II) Logitech BT Mini-Receiver: Found 13 mouse buttons
(II) Logitech BT Mini-Receiver: Found x and y relative axes
(II) Logitech BT Mini-Receiver: Found scroll wheel(s)
(II) Logitech BT Mini-Receiver: Found keys
(II) Logitech BT Mini-Receiver: Configuring as mouse
(II) Logitech BT Mini-Receiver: Configuring as keyboard
(**) Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
(**) Logitech BT Mini-Receiver: (accel) filter chain progression: 2.00
(**) Logitech BT Mini-Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech BT Mini-Receiver: (accel) set acceleration profile 0
(II) config/hal: Adding input device Dell Dell USB Keyboard
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event4"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
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
(II) config/hal: Adding input device Dell Dell USB Optical Mouse
(**) Dell Dell USB Optical Mouse: always reports core events
(**) Dell Dell USB Optical Mouse: Device: "/dev/input/event3"
(II) Dell Dell USB Optical Mouse: Found 3 mouse buttons
(II) Dell Dell USB Optical Mouse: Found x and y relative axes
(II) Dell Dell USB Optical Mouse: Found scroll wheel(s)
(II) Dell Dell USB Optical Mouse: Configuring as mouse
(**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
(**) Dell Dell USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Dell Dell USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Dell Dell USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(X.Org X Server 1.6.3
Release Date: 2009-7-31
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux Horsford 2.6.31-6-generic #26-Ubuntu SMP Fri Aug 21 17:55:00 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-6-generic root=UUID=09b65342-1923-4a58-93e7-dc8e35fcddbb ro quiet splash
Build Date: 19 August 2009  05:56:23PM
xorg-server 2:1.6.3-1ubuntu3 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 24 16:39:30 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:13:0) 10de:03d0:1028:020e nVidia Corporation C61 [GeForce 6150SE nForce 430] rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
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
	compiled for 1.6.3, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nv"
(II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
(II) Module nv: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 2.1.14
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
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
	GeForce Go 6600, GeForce Go 6600 GT, Quadro NVS 440, Quadro FX 550,
	Quadro FX 550, Quadro FX 540, GeForce 6200, GeForce 6500,
	GeForce 6200 TurboCache(TM), GeForce 6200SE TurboCache(TM),
	GeForce 6200 LE, GeForce Go 6200, Quadro NVS 285, GeForce Go 6400,
	GeForce Go 6200, GeForce Go 6400, GeForce 6250, GeForce 7100 GS,
	GeForce 6800, GeForce 6800 LE, GeForce 6800 GT, GeForce 6800 XT,
	GeForce 6200, GeForce 6200 A-LE, GeForce 7800 GTX, GeForce 7800 GTX,
	GeForce 7800 GT, GeForce 7800 GS, GeForce 7800 SLI, GeForce Go 7800,
	GeForce Go 7800 GTX, Quadro FX 4500, GeForce 7350 LE,
	GeForce 7300 LE, GeForce 7300 SE, GeForce Go 7200, GeForce Go 7300,
	GeForce Go 7400, GeForce Go 7400 GS, Quadro NVS 110M,
	Quadro NVS 120M, Quadro FX 350M, GeForce 7500 LE, Quadro FX 350,
	GeForce 7300 GS, GeForce 7650 GS, GeForce 7600 GT, GeForce 7600 GS,
	GeForce 7300 GT, GeForce 7600 LE, GeForce 7300 GT, GeForce Go 7700,
	GeForce Go 7600, GeForce Go 7600 GT, Quadro NVS 300M,
	GeForce Go 7900 SE, Quadro FX 550M, Quadro FX 560, GeForce 7900 GTX,
	GeForce 7900 GT, GeForce 7900 GS, GeForce 7950 GX2, GeForce 7950 GX2,
	GeForce 7950 GT, GeForce Go 7950 GTX, GeForce Go 7900 GS,
	GeForce Go 7900 GTX, Quadro FX 2500M, Quadro FX 1500M,
	Quadro FX 5500, Quadro FX 3500, Quadro FX 1500, Quadro FX 4500 X2,
	GeForce 6150, GeForce 6150 LE, GeForce 6100, GeForce Go 6150,
	Quadro NVS 210S / NVIDIA GeForce 6150LE, GeForce Go 6100,
	GeForce 6150SE, GeForce 6100 nForce 405, GeForce 6100 nForce 400,
	GeForce 6100 nForce 420, GeForce 7025, GeForce 7050,
	GeForce 8800 GTX, GeForce 8800 GTS, GeForce 8800 Ultra,
	Quadro FX 5600, Quadro FX 4600, GeForce 8600 GTS, GeForce 8600 GT,
	GeForce 8600 GT, GeForce 8600 GS, GeForce 8400 GS, GeForce 9500M GS,
	GeForce 8600M GT, GeForce 9650M GS, GeForce 8700M GT, Quadro FX 370,
	Quadro NVS 320M, Quadro FX 570M, Quadro FX 1600M, Quadro FX 570,
	Quadro FX 1700, GeForce 8400 SE, GeForce 8500 GT, GeForce 8400 GS,
	GeForce 8300 GS, GeForce 8400 GS, GeForce 8600M GS, GeForce 8400M GT,
	GeForce 8400M GS, GeForce 8400M G, Quadro NVS 140M, Quadro NVS 130M,
	Quadro NVS 135M, GeForce 9400 GT, Quadro FX 360M, GeForce 9300M G,
	Quadro NVS 290, GeForce GTX 295, GeForce GTX 280, GeForce GTX 260,
	GeForce GTX 285, Quadro CX, Quadro FX 5800, Quadro FX 4800,
	Quadro FX 3800, GeForce 8800 GTS 512, GeForce 9800 GT,
	GeForce 8800 GT, GeForce 9800 GX2, GeForce 9800 GT, GeForce 8800 GS,
	GeForce 9800M GTX, GeForce 8800M GTS, GeForce 9800M GT,
	GeForce 8800M GTX, GeForce 8800 GS, GeForce 9600 GSO,
	GeForce 8800 GT, GeForce 9800 GTX, GeForce 9800 GTX+,
	GeForce 9800 GT, GeForce GTS 250, GeForce 9800M GTX, Quadro FX 3700,
	Quadro FX 3600M, Quadro FX 3700M, GeForce 9600 GT, GeForce 9600 GS,
	GeForce 9600 GSO 512, GeForce GT 130, GeForce GT 140,
	GeForce 9800M GTS, GeForce 9700M GTS, GeForce 9800M GS,
	GeForce 9800M GTS, Quadro FX 1800, Quadro FX 2700M, GeForce 9500 GT,
	GeForce 9400 GT, GeForce 9500 GT, GeForce GT 120, GeForce 9600M GT,
	GeForce 9600M GS, GeForce 9600M GT, GeForce 9700M GT,
	GeForce 9500M G, GeForce 9650M GT, GeForce 9500 GT, Quadro FX 380,
	Quadro FX 580, Quadro FX 770M, GeForce 9300 GE, GeForce 9300 GS,
	GeForce 8400 GS, GeForce 9300M GS, GeForce G100, GeForce 9200M GS,
	GeForce 9300M GS, Quadro NVS 150M, Quadro NVS 160M, Quadro NVS 420,
	Quadro FX 370 LP, Quadro NVS 450, Quadro NVS 295
(II) Primary Device is: PCI 00@00:0d:0
(--) NV: Found NVIDIA GeForce 6150SE at 00@00:0d:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NV(0): Initializing int10
(II) NV(0): Primary V_BIOS segment is: 0xc000
(--) NV(0): Chipset: "GeForce 6150SE"
(**) NV(0): Depth 24, (--) framebuffer bpp 32
(==) NV(0): RGB weight 888
(==) NV(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(==) NV(0): Using HW cursor
(--) NV(0): Linear framebuffer at 0xE0000000
(--) NV(0): MMIO registers at 0xFB000000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) NV(0): I2C bus "DDC" initialized.
(II) NV(0): Probing for analog device on output A...
(--) NV(0):   ...found one
(II) NV(0): Probing for analog device on output B...
(--) NV(0):   ...can't find one
(II) NV(0): Probing for EDID on I2C bus A...
(II) NV(0): I2C device "DDC:E-EDID segment register" registered at address 0x60.
(II) NV(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) NV(0):   ... none found
(II) NV(0): Probing for EDID on I2C bus B...
(--) NV(0): DDC detected a CRT:
(II) NV(0): Manufacturer: DEL  Model: d017  Serial#: 825641800
(II) NV(0): Year: 2007  Week: 37
(II) NV(0): EDID Version: 1.4
(II) NV(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NV(0): Sync:  Separate  SyncOnGreen
(II) NV(0): Max Image Size [cm]: horiz.: 37  vert.: 23
(II) NV(0): Gamma: 2.20
(II) NV(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NV(0): Default color space is primary color space
(II) NV(0): First detailed timing is preferred mode
(II) NV(0): Preferred mode is native pixel format and refresh rate
(II) NV(0): Display is continuous-frequency
(II) NV(0): redX: 0.650 redY: 0.331   greenX: 0.317 greenY: 0.568
(II) NV(0): blueX: 0.146 blueY: 0.091   whiteX: 0.312 whiteY: 0.328
(II) NV(0): Supported established timings:
(II) NV(0): 720x400@70Hz
(II) NV(0): 640x480@60Hz
(II) NV(0): 640x480@75Hz
(II) NV(0): 800x600@60Hz
(II) NV(0): 800x600@75Hz
(II) NV(0): 1024x768@60Hz
(II) NV(0): 1024x768@75Hz
(II) NV(0): 1280x1024@75Hz
(II) NV(0): Manufacturer's mask: 0
(II) NV(0): Supported standard timings:
(II) NV(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NV(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NV(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NV(0): Supported detailed timing:
(II) NV(0): clock: 88.8 MHz   Image Size:  370 x 230 mm
(II) NV(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
(II) NV(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
(II) NV(0): Serial No: PK25679A16KH
(II) NV(0): Ranges: V min: 50 V max: 77 Hz, H min: 30 H max: 83 kHz, PixClock max 129000 kHz
(II) NV(0): Maximum pixel width: 4136
(II) NV(0): Supported aspect ratios: 4:3 16:9 16:10* 5:4 15:9
(II) NV(0): Supported blankings: standard reduced
(II) NV(0): Supported scalings: hshrink hstretch vshrink vstretch
(II) NV(0): Preferred refresh rate: 0
(II) NV(0): Monitor name: DELL SE178WFP
(II) NV(0): EDID (in hex):
(II) NV(0): 	00ffffffffffff0010ac17d0484b3631
(II) NV(0): 	251101046a251778efb690a654519125
(II) NV(0): 	175054a54b008180714f950001010101
(II) NV(0): 	010101010101ab22a0a050841a303020
(II) NV(0): 	360072e61000001a000000ff00504b32
(II) NV(0): 	353637394131364b480a000000fd0032
(II) NV(0): 	4d1e530e0411b205f858f000000000fc
(II) NV(0): 	0044454c4c2053453137385746500047
(--) NV(0): CRTC 0 appears to have a CRT attached
(II) NV(0): Using CRT on CRTC 0
(II) NV(0): EDID vendor "DEL", prod id 53271
(II) NV(0): Using hsync ranges from config file
(II) NV(0): Using vrefresh ranges from config file
(II) NV(0): Printing DDC gathered Modelines:
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NV(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NV(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NV(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NV(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NV(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NV(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NV(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NV(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NV(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(--) NV(0): VideoRAM: 131072 kBytes
(==) NV(0): Using gamma correction (1.0, 1.0, 1.0)
(II) NV(0): Monitor0: Using hsync range of 28.00-33.00 kHz
(II) NV(0): Monitor0: Using vrefresh range of 43.00-72.00 Hz
(II) NV(0): Monitor0: Using maximum pixel clock of 129.00 MHz
(II) NV(0): Estimated virtual size for aspect ratio 0.0000 is 1440x900
(II) NV(0): Clock range:  12.00 to 400.00 MHz
(II) NV(0): Not using default mode "640x350" (hsync out of range)
(II) NV(0): Not using default mode "320x175" (hsync out of range)
(II) NV(0): Not using default mode "640x400" (hsync out of range)
(II) NV(0): Not using default mode "320x200" (hsync out of range)
(II) NV(0): Not using default mode "720x400" (hsync out of range)
(II) NV(0): Not using default mode "360x200" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "320x240" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "400x300" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "512x384" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (height too large for virtual size)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x960" (height too large for virtual size)
(II) NV(0): Not using default mode "640x480" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using default mode "640x512" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1600x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "800x600" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1792x1344" (width too large for virtual size)
(II) NV(0): Not using default mode "896x672" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1856x1392" (width too large for virtual size)
(II) NV(0): Not using default mode "928x696" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "832x624" (hsync out of range)
(II) NV(0): Not using default mode "416x312" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1152x864" (hsync out of range)
(II) NV(0): Not using default mode "576x432" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1360x768" (hsync out of range)
(II) NV(0): Not using default mode "680x384" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1400x1050" (height too large for virtual size)
(II) NV(0): Not using default mode "700x525" (hsync out of range)
(II) NV(0): Not using default mode "1440x900" (hsync out of range)
(II) NV(0): Not using default mode "720x450" (hsync out of range)
(II) NV(0): Not using default mode "1600x1024" (width too large for virtual size)
(II) NV(0): Not using default mode "800x512" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NV(0): Not using default mode "840x525" (hsync out of range)
(II) NV(0): Not using default mode "1920x1080" (width too large for virtual size)
(II) NV(0): Not using default mode "960x540" (hsync out of range)
(II) NV(0): Not using default mode "1920x1200" (width too large for virtual size)
(II) NV(0): Not using default mode "960x600" (hsync out of range)
(II) NV(0): Not using default mode "1920x1440" (width too large for virtual size)
(II) NV(0): Not using default mode "960x720" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using default mode "2048x1536" (width too large for virtual size)
(II) NV(0): Not using default mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1440x900" (hsync out of range)
(II) NV(0): Not using driver mode "800x600" (hsync out of range)
(II) NV(0): Not using driver mode "640x480" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using driver mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "1024x768" (hsync out of range)
(II) NV(0): Not using driver mode "800x600" (hsync out of range)
(II) NV(0): Not using driver mode "1280x1024" (height too large for virtual size)
(II) NV(0): Not using driver mode "1152x864" (hsync out of range)
(II) NV(0): Not using driver mode "1440x900" (hsync out of range)
(WW) NV(0): Shrinking virtual size estimate from 1440x900 to 640x480
(--) NV(0): Virtual size is 640x480 (pitch 640)
(**) NV(0): *Driver mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(II) NV(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NV(0): *Driver mode "720x400": 28.3 MHz, 31.5 kHz, 70.1 Hz
(II) NV(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NV(0): *Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NV(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) NV(0): Display dimensions: (370, 230) mm
(**) NV(0): DPI set to (43, 53)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 1.2.1
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[5] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
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
(**) Option "dpms"
(**) NV(0): DPMS enabled
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
(II) AIGLX: Screen 0 is not DRI2 capable
(II) AIGLX: Screen 0 is not DRI capable
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) config/hal: Adding input device Logitech BT Mini-Receiver
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 2.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) Logitech BT Mini-Receiver: always reports core events
(**) Logitech BT Mini-Receiver: Device: "/dev/input/event5"
(II) Logitech BT Mini-Receiver: Found keys
(II) Logitech BT Mini-Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(II) config/hal: Adding input device Logitech BT Mini-Receiver
(**) Logitech BT Mini-Receiver: always reports core events
(**) Logitech BT Mini-Receiver: Device: "/dev/input/event6"
(II) Logitech BT Mini-Receiver: Found 13 mouse buttons
(II) Logitech BT Mini-Receiver: Found x and y relative axes
(II) Logitech BT Mini-Receiver: Found scroll wheel(s)
(II) Logitech BT Mini-Receiver: Found keys
(II) Logitech BT Mini-Receiver: Configuring as mouse
(II) Logitech BT Mini-Receiver: Configuring as keyboard
(**) Logitech BT Mini-Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech BT Mini-Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech BT Mini-Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
(**) Logitech BT Mini-Receiver: (accel) keeping acceleration scheme 1
(**) Logitech BT Mini-Receiver: (accel) filter chain progression: 2.00
(**) Logitech BT Mini-Receiver: (accel) filter stage 0: 20.00 ms
(**) Logitech BT Mini-Receiver: (accel) set acceleration profile 0
(II) config/hal: Adding input device Dell Dell USB Keyboard
(**) Dell Dell USB Keyboard: always reports core events
(**) Dell Dell USB Keyboard: Device: "/dev/input/event4"
(II) Dell Dell USB Keyboard: Found keys
(II) Dell Dell USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(**) Option "xkb_options" "lv3:ralt_switch"
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
(II) config/hal: Adding input device Dell Dell USB Optical Mouse
(**) Dell Dell USB Optical Mouse: always reports core events
(**) Dell Dell USB Optical Mouse: Device: "/dev/input/event3"
(II) Dell Dell USB Optical Mouse: Found 3 mouse buttons
(II) Dell Dell USB Optical Mouse: Found x and y relative axes
(II) Dell Dell USB Optical Mouse: Found scroll wheel(s)
(II) Dell Dell USB Optical Mouse: Configuring as mouse
(**) Dell Dell USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Dell Dell USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Dell Dell USB Optical Mouse" (type: MOUSE)
(**) Dell Dell USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Dell Dell USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Dell Dell USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Dell Dell USB Optical Mouse: (accel) set acceleration profile 0*) Dell Dell USB Optical Mouse: (accel) set acceleration profile 0


```

Hope i didn't middle click twice, my current screen res is annoying to work with.

---

### Post by taavikko on 2009-08-24
That log isn't very useful, since it's the one with nv as driver.
We need one with nouveau.

Change the driver in xorg.conf to nouveau and restart X
If it fails to start -> check the log again or make a copy of it to paste here
```
cat /var/log/Xorg.0.log > ~/xorg.log
```

---

### Post by Regenweald on 2009-08-24
LOL, one would think that that would be obvious :) sorry about that.... I'll just edit this post with the correct one.

Details of Xorg.5.log
```


X.Org X Server 1.6.3
Release Date: 2009-7-31
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux Horsford 2.6.31-6-generic #26-Ubuntu SMP Fri Aug 21 17:55:00 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-6-generic root=UUID=09b65342-1923-4a58-93e7-dc8e35fcddbb ro quiet splash
Build Date: 19 August 2009  05:56:23PM
xorg-server 2:1.6.3-1ubuntu3 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.5.log", Time: Mon Aug 24 16:03:58 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 8

(--) PCI:*(0:0:13:0) 10de:03d0:1028:020e nVidia Corporation C61 [GeForce 6150SE nForce 430] rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 1.0.0
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
    compiled for 1.6.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers//nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 0.0.10
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) NOUVEAU driver Date:   Mon Jul 6 20:33:49 2009 +1000
(II) NOUVEAU driver for NVIDIA chipset families :
    RIVA TNT    (NV04)
    RIVA TNT2   (NV05)
    GeForce 256 (NV10)
    GeForce 2   (NV11, NV15)
    GeForce 4MX (NV17, NV18)
    GeForce 3   (NV20)
    GeForce 4Ti (NV25, NV28)
    GeForce FX  (NV3x)
    GeForce 6   (NV4x)
    GeForce 7   (G7x)
    GeForce 8   (G8x)
(II) Primary Device is: PCI 00@00:0d:0
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(--) NOUVEAU(0): Chipset: "NVIDIA NV4C"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) NOUVEAU(0): Initializing int10
(II) NOUVEAU(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "nouveau"
(EE) [drm] drmOpen failed.
(EE) NOUVEAU(0): [drm] error opening the drm
(!!) NOUVEAU(0): Failing back to NoAccel mode
(**) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(==) NOUVEAU(0): Using HW cursor
(--) NOUVEAU(0): Linear framebuffer at 0xE0000000
(--) NOUVEAU(0): MMIO registers at 0xFB000000
(II) NOUVEAU(0): Initial CRTC_OWNER is 0
(II) NOUVEAU(0): Attempting to load BIOS image from PROM
(!!) NOUVEAU(0): ... BIOS signature not found
(II) NOUVEAU(0): Attempting to load BIOS image from PRAMIN
(II) NOUVEAU(0): ... appears to be valid
(II) NOUVEAU(0): BIT BIOS found
(II) NOUVEAU(0): Bios version 05.61.32.25
(II) NOUVEAU(0): Found Display Configuration Block version 3.0
(!!) NOUVEAU(0): Raw DCB entry 0: 01000310 00000023
(!!) NOUVEAU(0): Raw DCB entry 1: 00110204 98830003
(--) NOUVEAU(0): Parsing VBIOS init table 0 at offset 0xDEB3
(EE) NOUVEAU(0): ========== misaligned reg 0x0060081D ==========
(EE) NOUVEAU(0): ========== misaligned reg 0x0060081D ==========
(--) NOUVEAU(0): Parsing VBIOS init table 1 at offset 0xE00A
(--) NOUVEAU(0): Parsing VBIOS init table 2 at offset 0xE00B
(EE) NOUVEAU(0): ========== unknown reg 0x0077FFF4 ==========
(EE) NOUVEAU(0): ========== unknown reg 0x0077FFF8 ==========
(EE) NOUVEAU(0): ========== unknown reg 0x0077FFFC ==========
(--) NOUVEAU(0): Parsing VBIOS init table 3 at offset 0xE18D
(--) NOUVEAU(0): Parsing VBIOS init table 4 at offset 0xE1D6
(WW) NOUVEAU(0): DCB type 4 not known
(II) NOUVEAU(0): Output VGA-0 using monitor section Monitor0
(II) NOUVEAU(0): I2C bus "VGA-0" initialized.
(II) NOUVEAU(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
(II) NOUVEAU(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
(II) NOUVEAU(0): EDID for output VGA-0
(II) NOUVEAU(0): Manufacturer: DEL  Model: d017  Serial#: 825641800
(II) NOUVEAU(0): Year: 2007  Week: 37
(II) NOUVEAU(0): EDID Version: 1.4
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
(II) NOUVEAU(0): Sync:  Separate  SyncOnGreen
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 37  vert.: 23
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
(II) NOUVEAU(0): Default color space is primary color space
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): Preferred mode is native pixel format and refresh rate
(II) NOUVEAU(0): Display is continuous-frequency
(II) NOUVEAU(0): redX: 0.650 redY: 0.331   greenX: 0.317 greenY: 0.568
(II) NOUVEAU(0): blueX: 0.146 blueY: 0.091   whiteX: 0.312 whiteY: 0.328
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 88.8 MHz   Image Size:  370 x 230 mm
(II) NOUVEAU(0): h_active: 1440  h_sync: 1488  h_sync_end 1520 h_blank_end 1600 h_border: 0
(II) NOUVEAU(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 926 v_border: 0
(II) NOUVEAU(0): Serial No: PK25679A16KH
(II) NOUVEAU(0): Ranges: V min: 50 V max: 77 Hz, H min: 30 H max: 83 kHz, PixClock max 129000 kHz
(II) NOUVEAU(0): Maximum pixel width: 4136
(II) NOUVEAU(0): Supported aspect ratios: 4:3 16:9 16:10* 5:4 15:9
(II) NOUVEAU(0): Supported blankings: standard reduced
(II) NOUVEAU(0): Supported scalings: hshrink hstretch vshrink vstretch
(II) NOUVEAU(0): Preferred refresh rate: 0
(II) NOUVEAU(0): Monitor name: DELL SE178WFP
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0):     00ffffffffffff0010ac17d0484b3631
(II) NOUVEAU(0):     251101046a251778efb690a654519125
(II) NOUVEAU(0):     175054a54b008180714f950001010101
(II) NOUVEAU(0):     010101010101ab22a0a050841a303020
(II) NOUVEAU(0):     360072e61000001a000000ff00504b32
(II) NOUVEAU(0):     353637394131364b480a000000fd0032
(II) NOUVEAU(0):     4d1e530e0411b205f858f000000000fc
(II) NOUVEAU(0):     0044454c4c2053453137385746500047
(II) NOUVEAU(0): EDID vendor "DEL", prod id 53271
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
(II) NOUVEAU(0): EDID vendor "DEL", prod id 53271
(II) NOUVEAU(0): Not using mode "1440x900" (hsync out of range)
(II) NOUVEAU(0): Not using mode "800x600" (hsync out of range)
(II) NOUVEAU(0): Not using mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using mode "1024x768" (hsync out of range)
(II) NOUVEAU(0): Not using mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using mode "1280x1024" (hsync out of range)
(II) NOUVEAU(0): Not using mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using mode "1440x900" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "640x350" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x175" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x400" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "720x400" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "360x200" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x240" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x240" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "320x240" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "400x300" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "512x384" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1280x960" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "640x480" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "640x480" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1280x1024" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "640x512" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "640x512" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "640x512" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "800x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "800x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "800x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "800x600" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "896x672" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "928x696" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "960x720" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "832x624" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "416x312" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "576x432" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1360x768" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "680x384" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1360x768" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "680x384" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1400x1050" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "700x525" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "700x525" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "700x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "700x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1440x900" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "720x450" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1600x1024" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "800x512" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1680x1050" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "840x525" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "840x525" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "840x525" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "840x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "840x525" (vrefresh out of range)
(II) NOUVEAU(0): Not using default mode "1920x1080" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "960x540" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "960x600" (hsync out of range)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Printing probed modes for output VGA-0
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Output VGA-0 connected
(II) NOUVEAU(0): Using fuzzy aspect match for initial modes
(II) NOUVEAU(0): Output VGA-0 using initial mode 640x480
(--) NOUVEAU(0): VideoRAM: 131072 kBytes
(==) NOUVEAU(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NOUVEAU(0): Virtual size is 720x720 (pitch 768)
(**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NOUVEAU(0):  Default mode "320x240": 12.6 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.1 Hz (D)
(II) NOUVEAU(0): Modeline "320x240"x60.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz)
(**) NOUVEAU(0): Display dimensions: (370, 230) mm
(**) NOUVEAU(0): DPI set to (49, 79)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [18] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [19] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [20] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [21] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [22] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [23] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]

```

Xorg.conf:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Wed May 27 01:58:49 PDT 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
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
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nouveau"
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

---

### Post by Regenweald on 2009-08-24
Back in , on a live cd. Please see above :) thanks.

---

### Post by gaspard.leon on 2009-08-24
> ```
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
[drm] failed to load kernel module "nouveau"
(EE) [drm] drmOpen failed.
(EE) NOUVEAU(0): [drm] error opening the drm
(!!) NOUVEAU(0): Failing back to NoAccel mode
```


I noticed that DRI failed to load kernel module -- is this normal?

---

### Post by Regenweald on 2009-08-24
> **gaspard.leon said:**
> I noticed that DRI failed to load kernel module -- is this normal?

I honestly could not say. I do however have text boot on and i did not notice the module fail. Should i attempt a re-build ?

---

### Post by taavikko on 2009-08-24
It would better if you'd reported this on LP.

Is the module builded ok? "dkms status"
Try to manually install "libdrm-nouveau1" from repos to see if it fixes this, probably not ;)

---

### Post by Regenweald on 2009-08-24
> **taavikko said:**
> It would better if you'd reported this on LP.

Is the module builded ok? "dkms status"
Try to manually install "libdrm-nouveau1" from repos to see if it fixes this, probably not ;)

the first install i used aptitude and it *did* take a few minutes well to build. On the second attempt I used synaptic. Should libdrm-nouveau-dev also be installed ? would a dpkg-reconfigure be applicable ?

I'll edit xorg.conf back to 'nv' and go back in to the fray....

If the next steps don't work, I'll head over to launchpad :)

---

### Post by taavikko on 2009-08-24
> **Regenweald said:**
> the first install i used aptitude and it *did* take a few minutes well to build. On the second attempt I used synaptic. Should libdrm-nouveau-dev also be installed ? would a dpkg-reconfigure be applicable ?

I'll edit xorg.conf back to 'nv' and go back in to the fray....

It makes no difference if you run apt-get/aptitude/synaptic/add-remove
they're all just front-ends to dpkg.
and no need for dpkg-reconfigure.
Allthough the xorg.conf is quite flooded, when it's automatically detected nowadays...

I'm not entirely sure about the libdrm-nouveau1... It would still need the upgraded mesa/libdrm to properly function. and they're in the queue atm.

---

### Post by Regenweald on 2009-08-24
Thanks guys :) I'll head back in now. Let you know of any progress in a few mins.

---

### Post by Regenweald on 2009-08-25
@Taavikko, thanks for all the help but nouveau won this round. Will try again  after a few more weeks of development.
when i go into my monitors menu i notice that the res is one that is not accommodated as well as the refresh rate being 70hz. My max is 60hz, would out of range refresh rate and res cause the unresponsive black screen ?

---

### Post by dinxter on 2009-08-26
theres a new nouveau out that seems to deal with the black screen and gets it working again, might be worth a try.
be warned, if you see something like,

[   14.113272] ttm: Unknown symbol drm_class_device_register
[   14.114441] ttm: Unknown symbol drm_class_device_unregister

in dmesg you'll end up at tty since the nouveau module cant load. the problem is the loading of a number of different modules automatically for some reason. (see [bug 404496]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404496") )
to get round this you'll need to remove some or all of 

rmmod i915 drm nvidia
before
modprobe nouveau

an additional problem seems to be with gnome-display-properties, 
display-properties:ERROR:xrandr-capplet.c:684:rebuild_resolution_combo: code should not be reached
you can still set resolution using xrandr, eg

xrandr 1280x1024 

apart from that it works well here :)

---

### Post by Regenweald on 2009-08-26
> **dinxter said:**
> theres a new nouveau out that seems to deal with the black screen and gets it working again, might be worth a try.
be warned, if you see something like,

[   14.113272] ttm: Unknown symbol drm_class_device_register
[   14.114441] ttm: Unknown symbol drm_class_device_unregister

in dmesg you'll end up at tty since the nouveau module cant load. the problem is the loading of a number of different modules automatically for some reason. (see [bug 404496]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404496") )
to get round this you'll need to remove some or all of 

rmmod i915 drm nvidia
before
modprobe nouveau

an additional problem seems to be with gnome-display-properties, 
display-properties:ERROR:xrandr-capplet.c:684:rebuild_resolution_combo: code should not be reached
you can still set resolution using xrandr, eg

xrandr 1280x1024 

apart from that it works well here :)

I just tried again with the updates, this time x did not start but i dropped to a text login prompt so it's more positive anyway :)
Do i also need to add the drm setting to xorg.conf ? I'm going to try your solution and check back.

Thanks dinxter.

edit: Small hiccup on xrandr
```

~$ xrandr -s 1400x900
Size 1400x900 not found in available modes

```

---

### Post by Regenweald on 2009-08-26
Got it working, removed all but the failsafe xorg.conf and edited it to 'nouveau'. Thanks all ! :)

---

### Post by Regenweald on 2009-09-01
The Black screen is back with kernel 31-9 Anyone else using Nouveau and experiencing this ?

---

### Post by dinxter on 2009-09-01
with the -8 kernel the i915 module was broken and could load, this meant that nouveau would load without any problems. 
with -9, the i915 is now fixed and autoloads again, seemingly unable to be blacklisted too. this means that nouveau can't load
[    8.111977] ttm: Unknown symbol drm_class_device_register
[    8.113104] ttm: Unknown symbol drm_class_device_unregister

so its back to rmmod i915 drm ttm to allow nouveau to modprobe successfully
in short, nouveau works fine at least here, but [bug 404496]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404496") is back and needs to be manually worked around :(

---

### Post by Regenweald on 2009-09-02
> **dinxter said:**
> with the -8 kernel the i915 module was broken and could load, this meant that nouveau would load without any problems. 
with -9, the i915 is now fixed and autoloads again, seemingly unable to be blacklisted too. this means that nouveau can't load
[    8.111977] ttm: Unknown symbol drm_class_device_register
[    8.113104] ttm: Unknown symbol drm_class_device_unregister

so its back to rmmod i915 drm ttm to allow nouveau to modprobe successfully
in short, nouveau works fine at least here, but [bug 404496]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404496") is back and needs to be manually worked around :(

latest round of updates, resolved again :) the devs are not playing around...

---

