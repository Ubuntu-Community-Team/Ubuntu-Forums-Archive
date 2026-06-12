---
title: "VIA Graphics issues [S3 UniChrome Pro]"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by dsp3 on 2014-04-26
I have spent 3 days trying to get my wyse v90 terminal to run ubuntu with a display, I can work fine in the terminal, 

I have the CN700/P4M800 Pro/P4M800 CE/VN800 Graphics [S3 UniChrome Pro] drivers and still have an error on bootup about "longhaul option enable not set quiting"

Below is my xorg conf and I have tried so many fixes from reading forums but i am on the verge of giving up on this. Does any one have any experience with this issue? 




```
[    34.261] X.Org X Server 1.15.1
Release Date: 2014-04-13
[    34.262] X Protocol Version 11, Revision 0
[    34.262] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[    34.262] Current Operating System: Linux wyse1 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686
[    34.262] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=4d607226-56e9-4714-8d65-79652e910fe9 ro quiet splash vt.handoff=7
[    34.262] Build Date: 16 April 2014  01:40:08PM
[    34.262] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[    34.262] Current version of pixman: 0.30.2
[    34.262]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    34.262] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.263] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 26 12:15:24 2014
[    34.277] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.295] (==) No Layout section.  Using the first Screen section.
[    34.295] (==) No screen section available. Using defaults.
[    34.295] (**) |-->Screen "Default Screen Section" (0)
[    34.295] (**) |   |-->Monitor "<default monitor>"
[    34.299] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    34.301] (==) Automatically adding devices
[    34.301] (==) Automatically enabling devices
[    34.301] (==) Automatically adding GPU devices
[    34.302] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.302]     Entry deleted from font path.
[    34.302] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    34.302]     Entry deleted from font path.
[    34.302] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    34.302]     Entry deleted from font path.
[    34.302] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    34.302]     Entry deleted from font path.
[    34.302] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    34.302]     Entry deleted from font path.
[    34.302] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    34.302] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    34.302] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.302] (II) Loader magic: 0xb77c16c0
[    34.302] (II) Module ABI versions:
[    34.302]     X.Org ANSI C Emulation: 0.4
[    34.303]     X.Org Video Driver: 15.0
[    34.303]     X.Org XInput driver : 20.0
[    34.303]     X.Org Server Extension : 8.0
[    34.318] (--) PCI:*(0:1:0:0) 1106:3344:1106:3344 rev 1, Mem @ 0xf4000000/67108864, 0xfb000000/16777216, BIOS @ 0x????????/65536
[    34.319] Initializing built-in extension Generic Event Extension
[    34.319] Initializing built-in extension SHAPE
[    34.319] Initializing built-in extension MIT-SHM
[    34.319] Initializing built-in extension XInputExtension
[    34.319] Initializing built-in extension XTEST
[    34.319] Initializing built-in extension BIG-REQUESTS
[    34.319] Initializing built-in extension SYNC
[    34.319] Initializing built-in extension XKEYBOARD
[    34.319] Initializing built-in extension XC-MISC
[    34.319] Initializing built-in extension SECURITY
[    34.319] Initializing built-in extension XINERAMA
[    34.319] Initializing built-in extension XFIXES
[    34.319] Initializing built-in extension RENDER
[    34.319] Initializing built-in extension RANDR
[    34.319] Initializing built-in extension COMPOSITE
[    34.319] Initializing built-in extension DAMAGE
[    34.319] Initializing built-in extension MIT-SCREEN-SAVER
[    34.319] Initializing built-in extension DOUBLE-BUFFER
[    34.319] Initializing built-in extension RECORD
[    34.319] Initializing built-in extension DPMS
[    34.341] Initializing built-in extension Present
[    34.342] Initializing built-in extension DRI3
[    34.342] Initializing built-in extension X-Resource
[    34.342] Initializing built-in extension XVideo
[    34.342] Initializing built-in extension XVideo-MotionCompensation
[    34.342] Initializing built-in extension SELinux
[    34.342] Initializing built-in extension XFree86-VidModeExtension
[    34.342] Initializing built-in extension XFree86-DGA
[    34.342] Initializing built-in extension XFree86-DRI
[    34.342] Initializing built-in extension DRI2
[    34.342] (II) LoadModule: "glx"
[    34.393] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    34.480] (II) Module glx: vendor="X.Org Foundation"
[    34.480]     compiled for 1.15.1, module version = 1.0.0
[    34.480]     ABI class: X.Org Server Extension, version 8.0
[    34.480] (==) AIGLX enabled
[    34.480] Loading extension GLX
[    34.480] (==) Matched openchrome as autoconfigured driver 0
[    34.480] (==) Matched modesetting as autoconfigured driver 1
[    34.480] (==) Matched fbdev as autoconfigured driver 2
[    34.481] (==) Matched vesa as autoconfigured driver 3
[    34.481] (==) Assigned the driver to the xf86ConfigLayout
[    34.481] (II) LoadModule: "openchrome"
[    34.482] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
[    34.513] (II) Module openchrome: vendor="http://openchrome.org/"
[    34.513]     compiled for 1.15.0, module version = 0.3.3
[    34.514]     Module class: X.Org Video Driver
[    34.514]     ABI class: X.Org Video Driver, version 15.0
[    34.514] (II) LoadModule: "modesetting"
[    34.518] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    34.519] (II) Module modesetting: vendor="X.Org Foundation"
[    34.519]     compiled for 1.15.0, module version = 0.8.1
[    34.519]     Module class: X.Org Video Driver
[    34.519]     ABI class: X.Org Video Driver, version 15.0
[    34.519] (II) LoadModule: "fbdev"
[    34.527] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    34.527] (II) Module fbdev: vendor="X.Org Foundation"
[    34.527]     compiled for 1.15.0, module version = 0.4.4
[    34.527]     Module class: X.Org Video Driver
[    34.545]     ABI class: X.Org Video Driver, version 15.0
[    34.546] (II) LoadModule: "vesa"
[    34.546] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    34.547] (II) Module vesa: vendor="X.Org Foundation"
[    34.547]     compiled for 1.15.0, module version = 2.3.3
[    34.547]     Module class: X.Org Video Driver
[    34.547]     ABI class: X.Org Video Driver, version 15.0
[    34.552] (II) OPENCHROME: Driver for VIA Chrome chipsets: CLE266, KM400/KN400,
    K8M800/K8N800, PM800/PM880/CN400, VM800/P4M800Pro/VN800/CN700,
    CX700/VX700, K8M890/K8N890, P4M890, P4M900/VN896/CN896, VX800/VX820,
    VX855/VX875, VX900
[    34.553] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    34.553] (II) FBDEV: driver for framebuffer: fbdev
[    34.554] (II) VESA: driver for VESA chipsets: vesa
[    34.554] (++) using VT number 7


[    34.582] (!!) VIA Technologies does not support this driver in any way.
[    34.582] (!!) For support, please refer to http://www.openchrome.org/.
[    34.582] (!!) (openchrome 0.3.3 release)
[    34.582] (WW) Falling back to old probe method for modesetting
[    34.582] (EE) open /dev/dri/card0: No such file or directory
[    34.582] (WW) Falling back to old probe method for fbdev
[    34.582] (II) Loading sub module "fbdevhw"
[    34.583] (II) LoadModule: "fbdevhw"
[    34.584] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    34.585] (II) Module fbdevhw: vendor="X.Org Foundation"
[    34.585]     compiled for 1.15.1, module version = 0.0.2
[    34.585]     ABI class: X.Org Video Driver, version 15.0
[    34.585] (WW) Falling back to old probe method for vesa
[    34.585] (II) CHROME(0): VIAPreInit
[    34.585] (II) CHROME(0): VIAGetRec
[    34.586] (--) CHROME(0): Chipset: VM800/P4M800Pro/VN800/CN700
[    34.586] (--) CHROME(0): Chipset revision: 0
[    34.760] (EE) CHROME(0): [drm] Failed to open DRM device for pci:0000:01:00.0: No such file or directory
[    34.762] (II) Loading sub module "vgahw"
[    34.762] (II) LoadModule: "vgahw"
[    34.771] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[    34.777] (II) Module vgahw: vendor="X.Org Foundation"
[    34.778]     compiled for 1.15.1, module version = 0.1.0
[    34.778]     ABI class: X.Org Video Driver, version 15.0
[    34.778] (--) CHROME(0): Probed amount of VideoRAM = 32768 kB
[    34.778] (II) CHROME(0): VIAMapMMIO
[    34.778] (--) CHROME(0): mapping MMIO @ 0xfb000000 with size 0xd000
[    34.778] (--) CHROME(0): mapping BitBlt MMIO @ 0xfb200000 with size 0x200000
[    34.779] (II) CHROME(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0
[    34.779] (II) CHROME(0): VIAMapFB
[    34.779] (--) CHROME(0): mapping framebuffer @ 0xf4000000 with size 0x2000000
[    34.779] (--) CHROME(0): Frame buffer start: 0xb4a48000, free start: 0x0 end: 0x2000000
[    34.791] (II) CHROME(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    34.791] (==) CHROME(0): Depth 24, (--) framebuffer bpp 32
[    34.791] (==) CHROME(0): RGB weight 888
[    34.791] (==) CHROME(0): Default visual is TrueColor
[    34.791] (II) CHROME(0): VIASetupDefaultOptions - Setting up default chipset options.
[    34.793] (==) CHROME(0): Shadow framebuffer is disabled.
[    34.793] (==) CHROME(0): Hardware acceleration is enabled.
[    34.793] (==) CHROME(0): Using EXA acceleration architecture.
[    34.793] (==) CHROME(0): EXA composite acceleration enabled.
[    34.793] (==) CHROME(0): EXA scratch area size is 4096 kB.
[    34.793] (==) CHROME(0): Using hardware two-color cursors and software full-color cursors.
[    34.793] (==) CHROME(0): GPU virtual command queue will be enabled.
[    34.793] (==) CHROME(0): DRI IRQ will be enabled if DRI is enabled.
[    34.793] (==) CHROME(0): AGP DMA will be enabled if DRI is enabled.
[    34.793] (==) CHROME(0): AGP DMA will be used for 2D acceleration.
[    34.793] (==) CHROME(0): PCI DMA will be used for XV image transfer if DRI is enabled.
[    34.793] (==) CHROME(0): Will not enable VBE modes.
[    34.793] (==) CHROME(0): VBE VGA register save & restore will not be used
    if VBE modes are enabled.
[    34.793] (==) CHROME(0): Xv Bandwidth check is enabled.
[    34.793] (==) CHROME(0): Will not impose a limit on video RAM reserved for DRI.
[    34.793] (==) CHROME(0): Will try to allocate 32768 kB of AGP memory.
[    34.794] (==) CHROME(0): TV dotCrawl is disabled.
[    34.794] (==) CHROME(0): TV deflicker is set to 0.
[    34.794] (==) CHROME(0): No default TV type is set.
[    34.794] (==) CHROME(0): No default TV output signal type is set.
[    34.794] (==) CHROME(0): No default TV output port is set.
[    34.794] (==) CHROME(0): Will not print VGA registers.
[    34.794] (==) CHROME(0): Will not scan I2C buses.
[    34.794] (II) CHROME(0): ...Finished parsing config file options.
[    34.794] (WW) CHROME(0): Manufacturer plainly copied main PCI IDs to subsystem/card IDs.
[    34.794] (--) CHROME(0): Detected VIA VT3344 (VM800) - EPIA EN. Card-Ids (1106|3344)
[    34.794] (II) CHROME(0): Detected MemClk 7
[    34.794] (II) CHROME(0): ViaGetMemoryBandwidth. Memory type: 7
[    34.794] (II) CHROME(0): Detected TV standard: NTSC.
[    34.794] (II) Loading sub module "ramdac"
[    34.794] (II) LoadModule: "ramdac"
[    34.794] (II) Module "ramdac" already built-in
[    34.795] (II) Loading sub module "i2c"
[    34.795] (II) LoadModule: "i2c"
[    34.795] (II) Module "i2c" already built-in
[    34.795] (II) CHROME(0): ViaI2CInit
[    34.795] (II) CHROME(0): ViaI2CBus1Init
[    34.795] (II) CHROME(0): I2C bus "I2C bus 1" initialized.
[    34.795] (II) CHROME(0): ViaI2cBus2Init
[    34.795] (II) CHROME(0): I2C bus "I2C bus 2" initialized.
[    34.795] (II) CHROME(0): ViaI2CBus3Init
[    34.795] (II) CHROME(0): I2C bus "I2C bus 3" initialized.
[    34.795] (II) Loading sub module "ddc"
[    34.795] (II) LoadModule: "ddc"
[    34.795] (II) Module "ddc" already built-in
[    34.795] (II) CHROME(0): ViaOutputsDetect
[    34.795] (==) CHROME(0): LVDS-0 : Digital output bus width is 12 bits.
[    34.819] (==) CHROME(0): LVDS-0 : DVI Center is disabled.
[    34.819] (==) CHROME(0): LVDS Panel will not be forced.
[    34.819] (==) CHROME(0): Panel size is not selected from config file.
[    34.819] (II) CHROME(0): Output VGA-1 has no monitor section
[    34.823] (II) CHROME(0): I2C device "I2C bus 1:ddc2" registered at address 0xA0.
[    34.873] (--) CHROME(0): Test for CRT with VSYNC
[    34.885] (II) CHROME(0): EDID for output VGA-1
[    34.885] (II) CHROME(0): Output VGA-1 disconnected
[    34.885] (WW) CHROME(0): No outputs definitely connected, trying again...
[    34.885] (II) CHROME(0): Output VGA-1 disconnected
[    34.885] (WW) CHROME(0): Unable to find connected outputs - setting 1024x768 initial framebuffer
[    34.885] (II) CHROME(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    34.885] (==) CHROME(0): DPI set to (96, 96)
[    34.885] (II) Loading sub module "fb"
[    34.885] (II) LoadModule: "fb"
[    34.886] (II) Loading /usr/lib/xorg/modules/libfb.so
[    34.907] (II) Module fb: vendor="X.Org Foundation"
[    34.909]     compiled for 1.15.1, module version = 1.0.0
[    34.909]     ABI class: X.Org ANSI C Emulation, version 0.4
[    34.909] (II) Loading sub module "exa"
[    34.909] (II) LoadModule: "exa"
[    34.910] (II) Loading /usr/lib/xorg/modules/libexa.so
[    34.930] (II) Module exa: vendor="X.Org Foundation"
[    34.930]     compiled for 1.15.1, module version = 2.6.0
[    34.930]     ABI class: X.Org Video Driver, version 15.0
[    34.930] (II) UnloadModule: "modesetting"
[    34.931] (II) Unloading modesetting
[    34.931] (II) UnloadModule: "fbdev"
[    34.931] (II) Unloading fbdev
[    34.931] (II) UnloadSubModule: "fbdevhw"
[    34.931] (II) Unloading fbdevhw
[    34.938] (II) UnloadModule: "vesa"
[    34.938] (II) Unloading vesa
[    34.939] (--) Depth 24 pixmap format is 32 bpp
[    34.939] (II) CHROME(0): VIAScreenInit
[    34.939] (II) CHROME(0): Frame Buffer From (0,0) To (1024,8192)
[    34.939] (II) CHROME(0): Using 7424 lines for offscreen memory.
[    34.939] 3145728 bytes of Linear memory allocated at 300000, handle 3081961296
[    34.939] 262144 bytes of Linear memory allocated at 600000, handle 3081999184
[    34.939] 32 bytes of Linear memory allocated at 640000, handle 3081996592
[    34.939] 32 bytes of Linear memory allocated at 640080, handle 3081996720
[    34.952] (II) CHROME(0): - Visuals set up
[    34.952] (II) CHROME(0): - B & W
[    34.952] (**) CHROME(0): Option "MigrationHeuristic" "greedy"
[    34.953] (II) EXA(0): Offscreen pixmap area of 30408704 bytes
[    34.953] (II) EXA(0): Driver registered support for the following operations:
[    34.953] (II)         Solid
[    34.953] (II)         Copy
[    34.953] (II)         Composite (RENDER acceleration)
[    34.953] (II) CHROME(0): [EXA] Enabled EXA acceleration.
[    34.953] (==) CHROME(0): Backing store enabled
[    34.953] (II) CHROME(0): - Backing store set up
[    34.953] (II) CHROME(0): - SW cursor set up
[    34.953] (II) CHROME(0): HWCursor ARGB enabled
[    34.953] 16384 bytes of Linear memory allocated at 641000, handle 3081979248
[    34.953] 16384 bytes of Linear memory allocated at 645000, handle 3081995328
[    34.953] (II) CHROME(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    34.954] (II) CHROME(0): - Def Color map set up
[    34.954] (II) CHROME(0): - Palette loaded
[    34.954] (II) CHROME(0): - Color maps etc. set up
[    34.954] (==) CHROME(0): DPMS enabled
[    34.954] (II) CHROME(0): - DPMS set up
[    34.954] (II) CHROME(0): VIAEnterVT
[    34.954] (II) CHROME(0): VIASave
[    34.954] (II) CHROME(0): Primary
[    34.972] (II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
[    34.973] (II) CHROME(0): Crtc...
[    34.973] (II) CHROME(0): TVSave...
[    34.973] (II) CHROME(0): VIASave
[    34.973] (II) CHROME(0): Primary
[    34.973] (II) CHROME(0): Primary Adapter! saving VGA_SR_ALL !!
[    34.973] (II) CHROME(0): Crtc...
[    34.973] (II) CHROME(0): TVSave...
[    34.973] (II) CHROME(0): ViaDisplayDisableCRT
[    34.973] (II) CHROME(0): ViaDisplayDisableCRT
[    34.973] DRM memory allocation failed -6
[    34.974] 635904 bytes of Linear memory allocated at 649000, handle 3081979968
[    35.062] (II) CHROME(0): Benchmarking video copy.  Less time is better.
[    35.210] (--) CHROME(0): Timed   libc YUV420 copy... 40014196. Throughput: 11.9 MiB/s.
[    35.383] (--) CHROME(0): Timed kernel YUV420 copy... 58436575. Throughput: 8.1 MiB/s.
[    35.475] (--) CHROME(0): Timed    SSE YUV420 copy... 32115778. Throughput: 14.8 MiB/s.
[    35.574] (--) CHROME(0): Timed    MMX YUV420 copy... 28284159. Throughput: 16.8 MiB/s.
[    35.575] (--) CHROME(0): Ditching 3DNow! YUV420 copy. Not supported by CPU.
[    35.663] (--) CHROME(0): Timed   MMX2 YUV420 copy... 33543091. Throughput: 14.1 MiB/s.
[    35.674] Freed 6590464 (pool 4)
[    35.674] (--) CHROME(0): Using MMX YUV42X copy for video.
[    35.674] (WW) CHROME(0): [XvMC] Cannot use XvMC without DRI!
[    35.674] (II) CHROME(0): - Done
[    35.674] (--) RandR disabled
[    35.906] (II) SELinux: Disabled on system
[    35.947] (II) AIGLX: Screen 0 is not DRI2 capable
[    35.965] (EE) AIGLX: reverting to software rendering
[    36.959] (II) AIGLX: Loaded and initialized swrast
[    36.961] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    37.409] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    37.503] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    37.503] 
```

---

