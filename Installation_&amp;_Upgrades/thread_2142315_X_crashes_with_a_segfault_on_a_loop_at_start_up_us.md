---
title: "X crashes with a segfault on a loop at start up using live CD"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by esqmo on 2013-05-05
Hi,

I'm trying to install Ubuntu 13 on my flatmates old laptop (Asus Aspire 3630). When the live CD boots I get stuck with the screen switching between the normal ubuntu background with a mouse cursor then to a black screen on repeat.

So I got the server version and installed that then installed xubuntu with

```
sudo apt-get install xubuntu-desktop
```

However, after rebooting I get the same issue.

When switching to a tty using ctrl alt F1 the logs for /var/log/Xorg.0.log.old are:

```
[   327.804] X.Org X Server 1.13.3
Release Date: 2013-03-07
[   327.804] X Protocol Version 11, Revision 0
[   327.804] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[   327.804] Current Operating System: Linux ubuntujo 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:36:13 UTC 2013 i686
[   327.804] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-19-generic root=UUID=84dc533c-d731-4814-8655-86a7bb162562 ro
[   327.804] Build Date: 17 April 2013  10:42:56PM
[   327.804] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[   327.804] Current version of pixman: 0.28.2
[   327.804]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   327.804] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   327.804] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May  5 12:15:49 2013
[   327.804] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   327.805] (==) No Layout section.  Using the first Screen section.
[   327.805] (==) No screen section available. Using defaults.
[   327.805] (**) |-->Screen "Default Screen Section" (0)
[   327.805] (**) |   |-->Monitor "<default monitor>"
[   327.805] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   327.805] (==) Automatically adding devices
[   327.805] (==) Automatically enabling devices
[   327.805] (==) Automatically adding GPU devices
[   327.805] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   327.805]     Entry deleted from font path.
[   327.805] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   327.805]     Entry deleted from font path.
[   327.805] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   327.805]     Entry deleted from font path.
[   327.805] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   327.805]     Entry deleted from font path.
[   327.805] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   327.805]     Entry deleted from font path.
[   327.805] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   327.805]     Entry deleted from font path.
[   327.805] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   327.805] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   327.805] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   327.805] (II) Loader magic: 0xb78016a0
[   327.805] (II) Module ABI versions:
[   327.805]     X.Org ANSI C Emulation: 0.4
[   327.805]     X.Org Video Driver: 13.1
[   327.805]     X.Org XInput driver : 18.0
[   327.805]     X.Org Server Extension : 7.0
[   327.807] (--) PCI:*(0:1:0:0) 1039:6330:1025:0082 rev 0, Mem @ 0xe8000000/134217728, 0xe2100000/131072, I/O @ 0x00009000/128
[   327.808] (II) Open ACPI successful (/var/run/acpid.socket)
[   327.808] Initializing built-in extension Generic Event Extension
[   327.808] Initializing built-in extension SHAPE
[   327.808] Initializing built-in extension MIT-SHM
[   327.808] Initializing built-in extension XInputExtension
[   327.808] Initializing built-in extension XTEST
[   327.808] Initializing built-in extension BIG-REQUESTS
[   327.808] Initializing built-in extension SYNC
[   327.808] Initializing built-in extension XKEYBOARD
[   327.808] Initializing built-in extension XC-MISC
[   327.808] Initializing built-in extension SECURITY
[   327.808] Initializing built-in extension XINERAMA
[   327.808] Initializing built-in extension XFIXES
[   327.808] Initializing built-in extension RENDER
[   327.808] Initializing built-in extension RANDR
[   327.808] Initializing built-in extension COMPOSITE
[   327.808] Initializing built-in extension DAMAGE
[   327.808] Initializing built-in extension MIT-SCREEN-SAVER
[   327.808] Initializing built-in extension DOUBLE-BUFFER
[   327.808] Initializing built-in extension RECORD
[   327.808] Initializing built-in extension DPMS
[   327.808] Initializing built-in extension X-Resource
[   327.808] Initializing built-in extension XVideo
[   327.808] Initializing built-in extension XVideo-MotionCompensation
[   327.808] Initializing built-in extension SELinux
[   327.808] Initializing built-in extension XFree86-VidModeExtension
[   327.808] Initializing built-in extension XFree86-DGA
[   327.808] Initializing built-in extension XFree86-DRI
[   327.808] Initializing built-in extension DRI2
[   327.808] (II) LoadModule: "glx"
[   327.809] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   327.809] (II) Module glx: vendor="X.Org Foundation"
[   327.809]     compiled for 1.13.3, module version = 1.0.0
[   327.809]     ABI class: X.Org Server Extension, version 7.0
[   327.809] (==) AIGLX enabled
[   327.809] Loading extension GLX
[   327.809] (==) Matched sis as autoconfigured driver 0
[   327.809] (==) Matched vesa as autoconfigured driver 1
[   327.809] (==) Matched modesetting as autoconfigured driver 2
[   327.809] (==) Matched fbdev as autoconfigured driver 3
[   327.809] (==) Assigned the driver to the xf86ConfigLayout
[   327.809] (II) LoadModule: "sis"
[   327.810] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
[   327.810] (II) Module sis: vendor="X.Org Foundation"
[   327.810]     compiled for 1.12.99.902, module version = 0.10.7
[   327.810]     Module class: X.Org Video Driver
[   327.810]     ABI class: X.Org Video Driver, version 13.0
[   327.810] (II) LoadModule: "vesa"
[   327.810] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   327.810] (II) Module vesa: vendor="X.Org Foundation"
[   327.810]     compiled for 1.12.99.902, module version = 2.3.2
[   327.810]     Module class: X.Org Video Driver
[   327.810]     ABI class: X.Org Video Driver, version 13.0
[   327.810] (II) LoadModule: "modesetting"
[   327.811] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   327.811] (II) Module modesetting: vendor="X.Org Foundation"
[   327.811]     compiled for 1.13.3, module version = 0.7.0
[   327.811]     Module class: X.Org Video Driver
[   327.811]     ABI class: X.Org Video Driver, version 13.1
[   327.811] (II) LoadModule: "fbdev"
[   327.811] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   327.811] (II) Module fbdev: vendor="X.Org Foundation"
[   327.812]     compiled for 1.12.99.902, module version = 0.4.3
[   327.812]     Module class: X.Org Video Driver
[   327.812]     ABI class: X.Org Video Driver, version 13.0
[   327.812] (II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
    SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
    SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
    SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
    SIS340
[   327.812] (II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
    Volari V3XT/V5/V8/Duo (XG40)
[   327.812] (II) VESA: driver for VESA chipsets: vesa
[   327.812] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   327.812] (II) FBDEV: driver for framebuffer: fbdev
[   327.812] (++) using VT number 7


[   327.812] (WW) Falling back to old probe method for sis
[   327.812] (--) Assigning device section with no busID to primary device
[   327.812] (--) Chipset SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX] found
[   327.812] (WW) Falling back to old probe method for vesa
[   327.812] (WW) Falling back to old probe method for modesetting
[   327.812] (EE) open /dev/dri/card0: No such file or directory
[   327.812] (WW) Falling back to old probe method for fbdev
[   327.812] (II) Loading sub module "fbdevhw"
[   327.812] (II) LoadModule: "fbdevhw"
[   327.812] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   327.813] (II) Module fbdevhw: vendor="X.Org Foundation"
[   327.813]     compiled for 1.13.3, module version = 0.0.2
[   327.813]     ABI class: X.Org Video Driver, version 13.1
[   327.813] (II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.12.99.902)
[   327.813] (II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
[   327.813] (II) SIS(0): *** See http://www.winischhofer.eu/linuxsisvga.shtml
[   327.813] (II) SIS(0): *** for documentation and updates.
[   327.813] (--) SIS(0): sisfb not found
[   327.813] (--) SIS(0): Relocated I/O registers at 0x9000
[   327.813] (II) Loading sub module "ramdac"
[   327.813] (II) LoadModule: "ramdac"
[   327.813] (II) Module "ramdac" already built-in
[   327.813] (II) SIS(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   327.813] (==) SIS(0): Depth 24, (--) framebuffer bpp 32
[   327.813] (==) SIS(0): RGB weight 888
[   327.813] (==) SIS(0): Default visual is TrueColor
[   327.813] (WW) SIS(0): Could not find/read video BIOS
[   327.813] (==) SIS(0): Using HW cursor
[   327.813] (==) SIS(0): Color HW cursor is enabled
[   327.813] (II) SIS(0): Using VRAM command queue, size 512k
[   327.813] (==) SIS(0): Hotkey display switching is enabled
[   327.813] (II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
[   327.814] (II) SIS(0):          whether enabled or disabled. This is no driver bug.
[   327.814] (==) SIS(0): SiSCtrl utility interface is disabled
[   327.814] (II) SIS(0): For information on SiSCtrl, see
        http://www.winischhofer.eu/linuxsispart1.shtml#sisctrl
[   327.814] (==) SIS(0): DRI disabled
[   327.814] (II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
[   327.814] (II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
[   327.814] (--) SIS(0): DIMM0 is DDR SDRAM
[   327.814] (--) SIS(0): DIMM1 is not installed
[   327.814] (--) SIS(0): DIMM2 is not installed
[   327.814] (--) SIS(0): DRAM type: DDR SDRAM
[   327.814] (--) SIS(0): Memory clock: 332.892 MHz
[   327.814] (--) SIS(0): DRAM bus width: 64 bit
[   327.814] (--) SIS(0): Linear framebuffer at 0xE8000000
[   327.814] (--) SIS(0): MMIO registers at 0xE2100000 (size 64K)
[   327.814] (--) SIS(0): VideoRAM: 65536 KB
[   327.814] (II) SIS(0): Using 64960K of framebuffer memory at offset 0K
[   327.814] (--) SIS(0): Hardware supports two video overlays
[   327.814] (--) SIS(0): Detected SiS302LV video bridge (Charter/UMC-1, ID 1; Rev 0xe1)
[   328.549] (--) SIS(0): No CRT1/VGA detected
[   328.549] (--) SIS(0): Detected LCD/plasma panel (1280x800, 11, non-exp., RGB18 [2cc106])
[   328.549] (==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
[   328.549] (II) SIS(0): CRT1 gamma correction is enabled
[   328.549] (II) SIS(0): Separate Xv gamma correction for CRT1 is disabled
[   328.549] (II) SIS(0): CRT2 gamma correction is enabled
[   328.549] (--) SIS(0): Memory bandwidth at 32 bpp is 665.784 MHz
[   328.549] (--) SIS(0): Detected LCD PanelDelayCompensation 0x00 (for LCD=CRT2)
[   328.549] (--) SIS(0): Detected LCD PanelDelayCompensation1 0x00 (for LCD=CRT1)
[   328.549] (--) SIS(0): 302LV/302ELV: Using EMI 0x600d703f (LCD)
[   328.549] (II) Loading sub module "ddc"
[   328.549] (II) LoadModule: "ddc"
[   328.549] (II) Module "ddc" already built-in
[   328.549] (--) SIS(0): CRT2 DDC probing failed
[   328.549] (==) SIS(0): Min pixel clock is 10 MHz
[   328.549] (--) SIS(0): Max pixel clock is 400 MHz
[   328.550] (II) SIS(0): Replaced entire mode list with built-in modes
[   328.550] (II) SIS(0): Correcting missing CRT2 monitor HSync range
[   328.550] (II) SIS(0): Correcting missing CRT2 monitor VRefresh range
[   328.550] (II) SIS(0): "Unknown reason" in the following list means that the mode
[   328.550] (II) SIS(0): is not supported on the chipset/bridge/current output device.
[   328.550] (II) SIS(0): <default monitor>: Using hsync range of 30.00-80.00 kHz
[   328.550] (II) SIS(0): <default monitor>: Using vrefresh range of 59.00-61.00 Hz
[   328.550] (II) SIS(0): <default monitor>: Using vrefresh value of 71.00 Hz
[   328.550] (WW) SIS(0): Unable to estimate virtual size
[   328.550] (II) SIS(0): Clock range:  10.00 to 400.00 MHz
[   328.550] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "800x600" (hsync out of range)
[   328.550] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[   328.550] (II) SIS(0): Not using default mode "640x480" (hsync out of range)
[   328.550] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[   328.550] (II) SIS(0): Not using default mode "1024x768" (hsync out of range)
[   328.550] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1280x1024" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1600x1200" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1920x1440" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "2048x1536" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "800x480" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "1024x576" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "1280x720" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "1280x720" (hsync out of range)
[   328.550] (II) SIS(0): Not using default mode "1280x960" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1280x960" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1280x768" (vrefresh out of range)
[   328.550] (II) SIS(0): Not using default mode "1280x768" (hsync out of range)
[   328.550] (II) SIS(0): Not using default mode "1400x1050" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1400x1050" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "1152x864" (unknown reason)
[   328.550] (II) SIS(0): Not using default mode "848x480" (vrefresh out of range)
[   328.551] (II) SIS(0): Not using default mode "856x480" (vrefresh out of range)
[   328.551] (II) SIS(0): Not using default mode "1360x768" (unknown reason)
[   328.551] (II) SIS(0): Not using default mode "1280x800" (vrefresh out of range)
[   328.551] (II) SIS(0): Not using default mode "1280x800" (hsync out of range)
[   328.551] (II) SIS(0): Not using default mode "1680x1050" (unknown reason)
[   328.551] (II) SIS(0): Not using default mode "1920x1080" (unknown reason)
[   328.551] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[   328.551] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[   328.551] (II) SIS(0): Not using default mode "1280x854" (unknown reason)
[   328.551] (--) SIS(0): Virtual size is 1280x800 (pitch 1280)
[   328.551] (**) SIS(0): *Default mode "1280x800" (1280x800) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
[   328.551] (**) SIS(0): *Default mode "1280x768" (1280x768) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
[   328.551] (**) SIS(0): *Default mode "1280x720" (1280x720) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
[   328.551] (**) SIS(0): *Default mode "1024x768" (1024x768) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
[   328.551] (**) SIS(0): *Default mode "1024x576" (1024x576) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
[   328.551] (**) SIS(0): *Default mode "960x600" (960x600) (For CRT device: 41.5 MHz, 37.1 kHz, 60.0 Hz)
[   328.551] (**) SIS(0): *Default mode "960x540" (960x540) (For CRT device: 37.3 MHz, 33.8 kHz, 60.0 Hz)
[   328.551] (**) SIS(0): *Default mode "800x600" (800x600) (For CRT device: 40.0 MHz, 37.9 kHz, 60.3 Hz)
[   328.551] (**) SIS(0): *Default mode "768x576" (768x576) (For CRT device: 35.0 MHz, 35.9 kHz, 60.1 Hz)
[   328.551] (**) SIS(0): *Default mode "720x576" (720x576) (For CRT device: 32.7 MHz, 35.9 kHz, 60.1 Hz)
[   328.551] (**) SIS(0): *Default mode "856x480" (856x480) (For CRT device: 33.9 MHz, 31.7 kHz, 59.8 Hz)
[   328.551] (**) SIS(0): *Default mode "848x480" (848x480) (For CRT device: 33.7 MHz, 31.0 kHz, 60.0 Hz)
[   328.551] (**) SIS(0): *Default mode "800x480" (800x480) (For CRT device: 39.8 MHz, 37.7 kHz, 60.0 Hz)
[   328.551] (**) SIS(0): *Default mode "720x480" (720x480) (For CRT device: 28.3 MHz, 31.6 kHz, 61.0 Hz)
[   328.551] (**) SIS(0): *Default mode "640x480" (640x480) (For CRT device: 25.1 MHz, 31.3 kHz, 59.7 Hz)
[   328.551] (**) SIS(0): *Default mode "640x400" (640x400) (For CRT device: 25.1 MHz, 31.6 kHz, 71.6 Hz)
[   328.551] (**) SIS(0): *Default mode "512x384" (512x384) (For CRT device: 32.6 MHz, 48.5 kHz, 60.1 Hz (D))
[   328.551] (**) SIS(0): *Default mode "400x300" (400x300) (For CRT device: 20.0 MHz, 37.9 kHz, 60.3 Hz (D))
[   328.551] (**) SIS(0): *Default mode "320x240" (320x240) (For CRT device: 12.5 MHz, 31.3 kHz, 60.7 Hz (D))
[   328.551] (**) SIS(0): *Default mode "320x200" (320x200) (For CRT device: 12.5 MHz, 31.3 kHz, 70.9 Hz (D))
[   328.551] (==) SIS(0): DPI set to (96, 96)
[   328.551] (II) Loading sub module "fb"
[   328.551] (II) LoadModule: "fb"
[   328.551] (II) Loading /usr/lib/xorg/modules/libfb.so
[   328.552] (II) Module fb: vendor="X.Org Foundation"
[   328.552]     compiled for 1.13.3, module version = 1.0.0
[   328.552]     ABI class: X.Org ANSI C Emulation, version 0.4
[   328.552] (II) Loading sub module "exa"
[   328.552] (II) LoadModule: "exa"
[   328.552] (II) Loading /usr/lib/xorg/modules/libexa.so
[   328.552] (II) Module exa: vendor="X.Org Foundation"
[   328.552]     compiled for 1.13.3, module version = 2.6.0
[   328.552]     ABI class: X.Org Video Driver, version 13.1
[   328.552] (II) UnloadModule: "vesa"
[   328.552] (II) Unloading vesa
[   328.552] (II) UnloadModule: "modesetting"
[   328.552] (II) Unloading modesetting
[   328.552] (II) UnloadModule: "fbdev"
[   328.552] (II) Unloading fbdev
[   328.552] (II) UnloadSubModule: "fbdevhw"
[   328.552] (II) Unloading fbdevhw
[   328.552] (--) Depth 24 pixmap format is 32 bpp
[   328.552] (II) Loading sub module "vbe"
[   328.552] (II) LoadModule: "vbe"
[   328.553] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   328.553] (II) Module vbe: vendor="X.Org Foundation"
[   328.553]     compiled for 1.13.3, module version = 1.1.0
[   328.553]     ABI class: X.Org Video Driver, version 13.1
[   328.553] (II) Loading sub module "int10"
[   328.553] (II) LoadModule: "int10"
[   328.553] (II) Loading /usr/lib/xorg/modules/libint10.so
[   328.553] (II) Module int10: vendor="X.Org Foundation"
[   328.553]     compiled for 1.13.3, module version = 1.0.0
[   328.553]     ABI class: X.Org Video Driver, version 13.1
[   328.553] (II) SIS(0): initializing int10
[   328.556] (II) SIS(0): Primary V_BIOS segment is: 0xc000
[   328.557] (II) SIS(0): VESA BIOS detected
[   328.557] (II) SIS(0): VESA VBE Version 3.0
[   328.557] (II) SIS(0): VESA VBE Total Mem: 16384 kB
[   328.557] (II) SIS(0): VESA VBE OEM: SiS
[   328.557] (II) SIS(0): VESA VBE OEM Software Rev: 1.0
[   328.557] (II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
[   328.557] (II) SIS(0): VESA VBE OEM Product: 6330
[   328.557] (II) SIS(0): VESA VBE OEM Product Rev: 2.24.4e
[   328.561] (II) SIS(0): Setting standard mode 0x16
[   329.365] (II) EXA(0): Offscreen pixmap area of 62423040 bytes
[   329.365] (II) EXA(0): Driver registered support for the following operations:
[   329.365] (II)         Solid
[   329.365] (II)         Copy
[   329.365] (II)         UploadToScreen
[   329.365] (II)         DownloadFromScreen
[   329.365] (--) SIS(0): CPU frequency 1500.02Mhz
[   329.369] (II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
[   329.384] (--) SIS(0):     Checked libc memcpy()...     186.5 MiB/s
[   329.398] (--) SIS(0):     Checked built-in-1 memcpy()...     187.1 MiB/s
[   329.443] (--) SIS(0):     Checked built-in-2 memcpy()...     58.1 MiB/s
[   329.457] (--) SIS(0):     Checked MMX memcpy()...     186.4 MiB/s
[   329.472] (--) SIS(0):     Checked MMX2 memcpy()...     188.6 MiB/s
[   329.472] (--) SIS(0): Using MMX2 method for aligned data transfers to video RAM
[   329.472] (--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
[   329.472] (--) SIS(0): CPU frequency 1500.02Mhz
[   329.476] (II) SIS(0): Benchmarking video RAM to system RAM memory transfer methods:
[   329.562] (--) SIS(0):     Checked libc memcpy()...     35.6 MiB/s
[   329.639] (--) SIS(0):     Checked built-in-1 memcpy()...     36.7 MiB/s
[   329.750] (--) SIS(0):     Checked built-in-2 memcpy()...     24.0 MiB/s
[   329.804] (--) SIS(0):     Checked MMX memcpy()...     50.6 MiB/s
[   329.857] (--) SIS(0):     Checked MMX2 memcpy()...     52.2 MiB/s
[   329.858] (--) SIS(0): Using MMX2 method for aligned data transfers from video RAM
[   329.858] (--) SIS(0): Using MMX2 method for unaligned data transfers from video RAM
[   329.858] (==) SIS(0): Backing store disabled
[   329.858] (==) SIS(0): Silken mouse enabled
[   329.858] (==) SIS(0): DPMS enabled
[   329.858] (II) SIS(0): Using SiS300/315/330/340 series HW Xv
[   329.859] (II) SIS(0): Default Xv adaptor is Video Overlay
[   329.918] (II) SIS(0): Initialized SISCTRL extension version 0.1
[   329.918] (II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
[   329.918] (==) RandR enabled
[   329.930] (II) SELinux: Disabled on system
[   329.932] (II) AIGLX: Screen 0 is not DRI2 capable
[   329.932] (II) AIGLX: Screen 0 is not DRI capable
[   329.950] (II) AIGLX: Loaded and initialized swrast
[   329.950] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   329.967] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   329.971] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[   329.972] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   329.972] (II) LoadModule: "evdev"
[   329.972] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   329.972] (II) Module evdev: vendor="X.Org Foundation"
[   329.972]     compiled for 1.13.3, module version = 2.7.3
[   329.972]     Module class: X.Org XInput Driver
[   329.972]     ABI class: X.Org XInput driver, version 18.0
[   329.973] (II) Using input driver 'evdev' for 'Power Button'
[   329.973] (**) Power Button: always reports core events
[   329.973] (**) evdev: Power Button: Device: "/dev/input/event3"
[   329.973] (--) evdev: Power Button: Vendor 0 Product 0x1
[   329.973] (--) evdev: Power Button: Found keys
[   329.973] (II) evdev: Power Button: Configuring as keyboard
[   329.973] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[   329.973] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   329.973] (**) Option "xkb_rules" "evdev"
[   329.973] (**) Option "xkb_model" "pc105"
[   329.973] (**) Option "xkb_layout" "gb"
[   329.978] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[   329.979] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   329.979] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   329.979] (II) Using input driver 'evdev' for 'Power Button'
[   329.979] (**) Power Button: always reports core events
[   329.979] (**) evdev: Power Button: Device: "/dev/input/event1"
[   329.979] (--) evdev: Power Button: Vendor 0 Product 0x1
[   329.979] (--) evdev: Power Button: Found keys
[   329.979] (II) evdev: Power Button: Configuring as keyboard
[   329.979] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[   329.979] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   329.979] (**) Option "xkb_rules" "evdev"
[   329.979] (**) Option "xkb_model" "pc105"
[   329.979] (**) Option "xkb_layout" "gb"
[   329.980] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[   329.980] (II) No input driver specified, ignoring this device.
[   329.980] (II) This device may have been added with another device file.
[   329.981] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[   329.981] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[   329.981] (II) Using input driver 'evdev' for 'Sleep Button'
[   329.981] (**) Sleep Button: always reports core events
[   329.981] (**) evdev: Sleep Button: Device: "/dev/input/event2"
[   329.981] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[   329.981] (--) evdev: Sleep Button: Found keys
[   329.981] (II) evdev: Sleep Button: Configuring as keyboard
[   329.981] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[   329.981] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[   329.981] (**) Option "xkb_rules" "evdev"
[   329.981] (**) Option "xkb_model" "pc105"
[   329.981] (**) Option "xkb_layout" "gb"
[   329.982] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[   329.982] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   329.982] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   329.982] (**) AT Translated Set 2 keyboard: always reports core events
[   329.982] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[   329.982] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   329.982] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   329.982] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   329.982] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[   329.982] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[   329.982] (**) Option "xkb_rules" "evdev"
[   329.982] (**) Option "xkb_model" "pc105"
[   329.982] (**) Option "xkb_layout" "gb"
[   329.983] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   329.983] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   329.983] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   329.983] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[   329.983] (II) LoadModule: "synaptics"
[   329.983] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[   329.984] (II) Module synaptics: vendor="X.Org Foundation"
[   329.984]     compiled for 1.13.1.901, module version = 1.6.2
[   329.984]     Module class: X.Org XInput Driver
[   329.984]     ABI class: X.Org XInput driver, version 18.0
[   329.984] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[   329.984] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   329.984] (**) Option "Device" "/dev/input/event5"
[   329.984] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[   329.984] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[   329.984] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   329.984] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[   329.984] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple scroll-buttons
[   329.984] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[   329.984] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   329.984] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   329.984] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[   329.984] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 10)
[   329.984] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[   329.984] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[   329.984] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[   329.985] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   329.985] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[   329.985] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   329.985] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   329.985] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   329.985] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[   329.985] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[   331.935] (EE) 
[   331.935] (EE) Backtrace:
[   331.935] (EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb7787f49]
[   331.935] (EE) 1: /usr/bin/X (0xb75da000+0x1b1e86) [0xb778be86]
[   331.935] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb75b740c]
[   331.935] (EE) 3: /usr/lib/xorg/modules/drivers/sis_drv.so (0xb6f89000+0x4ebed) [0xb6fd7bed]
[   331.935] (EE) 4: /usr/lib/xorg/modules/drivers/sis_drv.so (0xb6f89000+0x3a669) [0xb6fc3669]
[   331.935] (EE) 5: /usr/lib/xorg/modules/drivers/sis_drv.so (0xb6f89000+0x289f5) [0xb6fb19f5]
[   331.935] (EE) 6: /usr/lib/xorg/modules/libexa.so (0xb6f2b000+0x5288) [0xb6f30288]
[   331.935] (EE) 7: /usr/lib/xorg/modules/libexa.so (0xb6f2b000+0x5621) [0xb6f30621]
[   331.935] (EE) 8: /usr/lib/xorg/modules/libexa.so (0xb6f2b000+0x56d0) [0xb6f306d0]
[   331.935] (EE) 9: /usr/lib/xorg/modules/libexa.so (0xb6f2b000+0x6262) [0xb6f31262]
[   331.935] (EE) 10: /usr/lib/xorg/modules/libexa.so (0xb6f2b000+0x3eaf) [0xb6f2eeaf]
[   331.935] (EE) 11: /usr/lib/xorg/modules/libexa.so (0xb6f2b000+0x6383) [0xb6f31383]
[   331.935] (EE) 12: /usr/lib/xorg/modules/libexa.so (0xb6f2b000+0x123dd) [0xb6f3d3dd]
[   331.935] (EE) 13: /usr/lib/xorg/modules/libexa.so (0xb6f2b000+0xec7c) [0xb6f39c7c]
[   331.935] (EE) 14: /usr/bin/X (0xb75da000+0x12e041) [0xb7708041]
[   331.935] (EE) 15: /usr/bin/X (CompositePicture+0x319) [0xb76fc4a9]
[   331.942] (EE) 16: /usr/bin/X (0xb75da000+0x126bfd) [0xb7700bfd]
[   331.942] (EE) 17: /usr/bin/X (0xb75da000+0x122bae) [0xb76fcbae]
[   331.942] (EE) 18: /usr/bin/X (0xb75da000+0x3e035) [0xb7618035]
[   331.942] (EE) 19: /usr/bin/X (0xb75da000+0x2b525) [0xb7605525]
[   331.942] (EE) 20: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0xb71d5935]
[   331.942] (EE) 21: /usr/bin/X (0xb75da000+0x2b8f9) [0xb76058f9]
[   331.942] (EE) 
[   331.942] (EE) Segmentation fault at address 0x0
[   331.942] 
Fatal server error:
[   331.942] Caught signal 11 (Segmentation fault). Server aborting
[   331.942] 
[   331.942] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   331.942] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   331.942] (EE) 
[   331.943] (II) evdev: Power Button: Close
[   331.943] (II) UnloadModule: "evdev"
[   331.943] (II) evdev: Power Button: Close
[   331.943] (II) UnloadModule: "evdev"
[   331.943] (II) evdev: Sleep Button: Close
[   331.944] (II) UnloadModule: "evdev"
[   331.944] (II) evdev: AT Translated Set 2 keyboard: Close
[   331.944] (II) UnloadModule: "evdev"
[   331.945] (II) UnloadModule: "synaptics"
[   331.955] (II) SIS(0): Restoring by setting old mode 0x62
[   332.470] Server terminated with error (1). Closing log file.
```

---

### Post by esqmo on 2013-05-05
Ok after attaching a debugger the stacktrace in more detail gives:

```
Program received signal SIGSEGV, Segmentation fault.0xb7192ed6 in ?? () from /lib/i386-linux-gnu/libc.so.6
(gdb) bt f
#0  0xb7192ed6 in ?? () from /lib/i386-linux-gnu/libc.so.6
No symbol table info available.
#1  0x000000a0 in ?? ()
No symbol table info available.
#2  0xb6f2ee0b in ?? () from /usr/lib/xorg/modules/drivers/sis_drv.so
No symbol table info available.
#3  0xb6f1a676 in ?? () from /usr/lib/xorg/modules/drivers/sis_drv.so
No symbol table info available.
#4  0xb6f089f5 in ?? () from /usr/lib/xorg/modules/drivers/sis_drv.so
No symbol table info available.
#5  0xb6e87288 in exaCopyDirty (migrate=migrate@entry=0xbfc139f0, pValidDst=pValidDst@entry=0xb8b19d4c, 
    pValidSrc=pValidSrc@entry=0xb8b19d58, transfer=0xb6f08930, fallback_index=fallback_index@entry=1, 
    sync=sync@entry=0xb6e85dc0 <exaWaitSync>) at ../../exa/exa_migration_classic.c:220
        pPixmap = 0xb8b19ce8
        pExaPixmap = 0xb8b19d24
        damage = <optimised out>
        CopyReg = {extents = {x1 = 0, y1 = 0, x2 = 40, y2 = 40}, data = 0x0}
        save_use_gpu_copy = 1
        save_pitch = 160
        pBox = 0xbfc13898
        nbox = 160
        access_prepared = 0
        need_sync = 0
#6  0xb6e87621 in exaCopyDirtyToSys (migrate=migrate@entry=0xbfc139f0) at ../../exa/exa_migration_classic.c:285
        pPixmap = <optimised out>
        pExaScr = 0x28
        pExaPixmap = 0xb8b19d58
#7  0xb6e876d0 in exaDoMoveOutPixmap (migrate=migrate@entry=0xbfc139f0) at ../../exa/exa_migration_classic.c:404
        pPixmap = 0xb8b19ce8
        pExaPixmap = 0xb8b19d24
#8  0xb6e88262 in exaDoMigration_classic (pixmaps=0xbfc139f0, npixmaps=1, can_accel=0) at ../../exa/exa_migration_classic.c:719
        pScreen = <optimised out>
        pExaScr = 0xb895dd88
        i = <optimised out>
        j = <optimised out>
        __func__ = "exaDoMigration_classic"
#9  0xb6e85eaf in exaDoMigration (pixmaps=pixmaps@entry=0xbfc139f0, npixmaps=npixmaps@entry=1, can_accel=can_accel@entry=0)
    at ../../exa/exa.c:1134
        pScreen = <optimised out>
        pExaScr = 0x0
#10 0xb6e88383 in exaPrepareAccessReg_classic (pPixmap=0xb8b19ce8, index=1, pReg=0xb895df2c) at ../../exa/exa_migration_classic.c:758
        pixmaps = {{as_dst = 0, as_src = 1, pPix = 0xb8b19ce8, pReg = 0xb895df2c}}
#11 0xb6e943dd in ExaPrepareCompositeReg (height=16, width=4, yDst=0, xDst=0, yMask=0, xMask=0, ySrc=4, xSrc=1145, pDst=0xb89e4998, 
    pMask=0x0, pSrc=0xb8aeaa98, op=3 '\003', pScreen=0xb89724a8) at ../../exa/exa_unaccel.c:560
        region = {extents = {x1 = 0, y1 = 0, x2 = 4, y2 = 16}, data = 0x0}
        srcReg = 0xb895df2c
        pSrcPix = 0xb8b19ce8
        ret = 1
        dstReg = 0x0
        maskReg = 0x0
---Type <return> to continue, or q <return> to quit---
        pMaskPix = 0x0
        pDstPix = <optimised out>
        pExaScr = 0xb895dd88
#12 ExaCheckComposite (op=op@entry=3 '\003', pSrc=pSrc@entry=0xb8aeaa98, pMask=pMask@entry=0x0, pDst=pDst@entry=0xb89e4998, 
    xSrc=xSrc@entry=1145, ySrc=ySrc@entry=4, xMask=0, yMask=yMask@entry=0, xDst=0, yDst=yDst@entry=0, width=width@entry=4, 
    height=height@entry=16) at ../../exa/exa_unaccel.c:608
        pScreen = 0xb89724a8
        ps = 0xb89612b0
        pExaScr = 0xb895dd88
#13 0xb6e90c7c in exaComposite (op=3 '\003', pSrc=0xb8aeaa98, pMask=0x0, pDst=0xb89e4998, xSrc=<optimised out>, ySrc=<optimised out>, 
    xMask=0, yMask=0, xDst=<optimised out>, yDst=<optimised out>, width=4, height=16) at ../../exa/exa_render.c:1039
        pExaScr = 0xb89e4998
        ret = <optimised out>
        saveSrcRepeat = 1
        saveMaskRepeat = 0
        region = {extents = {x1 = 1, y1 = 0, x2 = 0, y2 = 0}, data = 0xb775dda0 <damageGCFuncs>}
#14 0xb765f041 in damageComposite (op=3 '\003', pSrc=0xb8aeaa98, pMask=0x0, pDst=0xb89e4998, xSrc=1145, ySrc=4, xMask=0, yMask=0, xDst=0, 
    yDst=0, width=4, height=16) at ../../../miext/damage/damage.c:559
        pScreen = <optimised out>
        ps = 0xb89612b0
        pScrPriv = 0xb8961508
#15 0xb76534a9 in CompositePicture (op=<optimised out>, pSrc=0xb8aeaa98, pMask=pMask@entry=0x0, pDst=0xb89e4998, xSrc=1145, ySrc=4, xMask=0, 
    yMask=0, xDst=0, yDst=0, width=4, height=16) at ../../render/picture.c:1611
        ps = 0xb89612b0
#16 0xb7657bfd in ProcRenderComposite (client=0xb8ad8a38) at ../../render/render.c:708
        pSrc = 0xb8aeaa98
        pMask = 0x0
        pDst = 0xb89e4998
        stuff = 0xb8ad1720
#17 0xb7653bae in ProcRenderDispatch (client=0xb8ad8a38) at ../../render/render.c:1989
        stuff = <optimised out>
#18 0xb756f035 in Dispatch () at ../../dix/dispatch.c:428
        clientReady = 0xb8aabd00
        result = <optimised out>
        client = 0xb8ad8a38
        nready = 0
        icheck = 0xb7765318 <checkForInput>
        start_tick = 700
#19 0xb755c525 in main (argc=9, argv=0xbfc13ed4, envp=0xbfc13efc) at ../../dix/main.c:298
        i = <optimised out>
        alwaysCheckForInput = {0, 1}
(gdb) 



```

---

### Post by esqmo on 2013-05-05
Any ideas. Can I roll back to another older driver? I didn't have these problems with Ubuntu 10.10 but I've seen it with all versions after that.

---

### Post by mörgæs on 2013-05-07
Is this our guy
[http://panam.acer.com/acerpanam/notebook/0000/acer/aspire3630/aspire3630sp2.shtml](http://panam.acer.com/acerpanam/notebook/0000/acer/aspire3630/aspire3630sp2.shtml)
(Acer, not Asus)

and how much memory does it have?

---

