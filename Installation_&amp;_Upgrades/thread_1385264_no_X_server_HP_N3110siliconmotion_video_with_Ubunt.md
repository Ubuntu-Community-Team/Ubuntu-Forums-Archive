---
title: "no X server HP N3110/siliconmotion video with Ubuntu 9.10 - worked with Ubuntu 6.10"
date: 2010-01-19
forum: Installation &amp; Upgrades
---

### Post by jwmueller5 on 2010-01-19
I have an old laptop I am trying to upgrade the Ubuntu version on.  It is an HP Pavilion N3110.  System specifications:

                                 [FONT=Verdana, Tahoma]433 MHz Intel Celeron Processor
256 MB SDRAM
20 GB hard disk drive
24x IDE CD-ROM drive (CD-224E)
1.44MB floppy disk drive
2 Type II 16-/32-bit PCMCIA slots (3.3- and 5-V support)
Internal V.90 modem
ESS Maestro-2EM PCI audio
12.1" HPA display (800x600x64K colors)
SMI LynxE SM811 video controller w/ 2MB 135 MHz SGRAM
87/88-key touch-type keyboard
Synaptics Touchpad pointing device[/FONT]


[FONT=Verdana, Tahoma]This PC works with the 6.10 Ubuntu desktop LiveCD.  [/FONT]                                  
[SIZE=2]Ran live CD on HP N3110 using F4 VGA mode 800x600x24 and it brings me to the desktop.[/SIZE]


[SIZE=2]I hope someone can help me compare the xorg.0.log files to find out why one works and one doesn't.  I apologize if the following format is incorrect for posting this type of question.  Thank you in advance for your assistance.
[/SIZE]


[SIZE=2]Here is the Xorg.0.log from that successful install:[/SIZE]


```
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux ubuntu 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686
Build Date: 07 July 2006
    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 19 14:49:37 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Silicon Motion, Inc. SM810 LynxE"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType").
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
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

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7192 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:02:0: chip 126f,0810 card 126f,0810 rev a6 class 03,00,00 hdr 00
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:0a:0: chip 104c,ac1c card 1000,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 00:0a:1: chip 104c,ac1c card 1800,0000 rev 01 class 06,07,00 hdr 82
(II) PCI: 00:0e:0: chip 125d,1978 card 103c,0009 rev 10 class 04,01,00 hdr 80
(II) PCI: 00:0e:1: chip 125d,1978 card 103c,0009 rev 10 class 07,80,00 hdr 80
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-CardBus bridge:
(II) Bus 1: bridge is at (0:10:0), (0,1,4), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 1 I/O range:
    [0] -1    0    0x00001000 - 0x000010ff (0x100) IX[B]
    [1] -1    0    0x00001400 - 0x000014ff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0x22000000 - 0x23ffffff (0x2000000) MX[B]
(II) Bus 1 prefetchable memory range:
    [0] -1    0    0x20000000 - 0x21ffffff (0x2000000) MX[B]
(II) PCI-to-CardBus bridge:
(II) Bus 5: bridge is at (0:10:1), (0,5,8), BCTRL: 0x05c0 (VGA_EN is cleared)
(II) Bus 5 I/O range:
    [0] -1    0    0x00001800 - 0x000018ff (0x100) IX[B]
    [1] -1    0    0x00001c00 - 0x00001cff (0x100) IX[B]
(II) Bus 5 non-prefetchable memory range:
    [0] -1    0    0x26000000 - 0x27ffffff (0x2000000) MX[B]
(II) Bus 5 prefetchable memory range:
    [0] -1    0    0x24000000 - 0x25ffffff (0x2000000) MX[B]
(--) PCI:*(0:2:0) Silicon Motion, Inc. SM810 LynxE rev 166, Mem @ 0xfd000000/24
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[B]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
    [0] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [1] -1    0    0x0000f400 - 0x0000f4ff (0x100) IX[B]
    [2] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[B]
    [3] -1    0    0x0000fcc0 - 0x0000fcdf (0x20) IX[B]
    [4] -1    0    0x0000fcf0 - 0x0000fcff (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [1] -1    0    0x0000f400 - 0x0000f4ff (0x100) IX[B]
    [2] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[B]
    [3] -1    0    0x0000fcc0 - 0x0000fcdf (0x20) IX[B]
    [4] -1    0    0x0000fcf0 - 0x0000fcff (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [7] -1    0    0x0000f400 - 0x0000f4ff (0x100) IX[B]
    [8] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[B]
    [9] -1    0    0x0000fcc0 - 0x0000fcdf (0x20) IX[B]
    [10] -1    0    0x0000fcf0 - 0x0000fcff (0x10) IX[B]
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
(II) LoadModule: "siliconmotion"
(II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.4.1
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
(II) Silicon Motion: driver (version 1.4.1) for Silicon Motion Lynx chipsets:
    Lynx, LynxE, Lynx3D, LynxEM, LynxEM+, Lynx3DM, Cougar3DR
(II) Primary Device is: PCI 00:02:0
(--) Chipset LynxE found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [5] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [6] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [7] -1    0    0x0000f400 - 0x0000f4ff (0x100) IX[B]
    [8] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[B]
    [9] -1    0    0x0000fcc0 - 0x0000fcdf (0x20) IX[B]
    [10] -1    0    0x0000fcf0 - 0x0000fcff (0x10) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [5] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [6] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [7] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [8] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [9] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [10] -1    0    0x0000f400 - 0x0000f4ff (0x100) IX[B]
    [11] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[B]
    [12] -1    0    0x0000fcc0 - 0x0000fcdf (0x20) IX[B]
    [13] -1    0    0x0000fcf0 - 0x0000fcff (0x10) IX[B]
    [14] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [15] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.0
(**) Silicon MotionDepth 24, (--) framebuffer bpp 24
(==) Silicon MotionRGB weight 888
(==) Silicon MotionDefault visual is TrueColor
(==) Silicon MotionUsing Hardware Cursor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) Silicon MotionPrimary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules/libvbe.so
(II) Silicon MotionVESA BIOS detected
(II) Silicon MotionVESA VBE Version 2.0
(II) Silicon MotionVESA VBE Total Mem: 1664 kB
(II) Silicon MotionVESA VBE OEM: Silicon Motion SM810 VGA BIOS
(II) Silicon MotionVESA VBE OEM Software Rev: 2.0
(II) Silicon MotionVESA VBE OEM Vendor: SM810
(II) Silicon MotionVESA VBE OEM Product: SM810
(II) Silicon MotionVESA VBE OEM Product Rev: 
(--) Silicon MotionChipset: "LynxE"
(II) Silicon MotionCursor Offset: FFFFFC00 Reserved: 001AF800
(II) Silicon MotionDSTN Panel Size = 800x600
(II) Silicon MotionvgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Reloading /usr/lib/xorg/modules/libi2c.so
(II) Silicon MotionI2C bus "I2C bus" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) Silicon MotionVESA VBE DDC supported
(II) Silicon MotionVESA VBE DDC Level none
(II) Silicon MotionVESA VBE DDC transfer in appr. 0 sec.
(II) Silicon MotionVESA VBE DDC read successfully
(==) Silicon MotionUsing gamma correction (1.0, 1.0, 1.0)
(--) Silicon Motionvideoram: 2048kB
(--) Silicon MotionDetected current MCLK value of 54.409 MHz
(II) Silicon MotionGeneric Monitor: Using hsync range of 28.00-51.00 kHz
(II) Silicon MotionGeneric Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) Silicon MotionClock range:  20.00 to 135.00 MHz
(II) Silicon MotionMode: 640x350 24-bpp, 85.079948Hz
(II) Silicon MotionNot using default mode "640x350" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x175" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x400 24-bpp, 85.079948Hz
(II) Silicon MotionNot using default mode "640x400" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x200" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 720x400 24-bpp, 85.038902Hz
(II) Silicon MotionNot using default mode "720x400" (vrefresh out of range)
(II) Silicon MotionNot using default mode "360x200" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 24-bpp, 60.000000Hz
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 24-bpp, 72.808800Hz
(II) Silicon MotionNot using default mode "640x480" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 24-bpp, 75.000000Hz
(II) Silicon MotionNot using default mode "640x480" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 640x480 24-bpp, 85.008308Hz
(II) Silicon MotionNot using default mode "640x480" (vrefresh out of range)
(II) Silicon MotionNot using default mode "320x240" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 56.250000Hz
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 60.316540Hz
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 72.187569Hz
(II) Silicon MotionNot using default mode "800x600" (vrefresh out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 75.000000Hz
(II) Silicon MotionNot using default mode "800x600" (vrefresh out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 800x600 24-bpp, 85.136887Hz
(II) Silicon MotionNot using default mode "800x600" (hsync out of range)
(II) Silicon MotionNot using default mode "400x300" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "512x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1152x864" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x960" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x960" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x480" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x1024" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x1024" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x1024" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1792x1344" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1792x1344" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "896x672" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1856x1392" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1856x1392" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1440" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1440" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) Silicon MotionMode: 832x624 24-bpp, 74.551270Hz
(II) Silicon MotionNot using default mode "832x624" (exceeds panel dimensions)
(II) Silicon MotionNot using default mode "416x312" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1280x800" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "640x400" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1152x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "576x384" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1152x864" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "576x432" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1400x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1400x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1400x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1400x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "700x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1440x900" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "720x450" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1600x1024" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "800x512" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1680x1050" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "840x525" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1200" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x600" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "1920x1440" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) Silicon MotionNot using default mode "2048x1536" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "2048x1536" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "2048x1536" (insufficient memory for mode)
(II) Silicon MotionNot using default mode "1024x768" (insufficient memory for mode)
(II) Silicon MotionNot using mode "1024x768" (no mode of this name)
(II) Silicon MotionMode: 800x600 24-bpp, 60.316540Hz
(II) Silicon MotionMode: 640x480 24-bpp, 60.000000Hz
(II) Silicon MotionMode: 800x600 24-bpp, 56.250000Hz
(--) Silicon MotionVirtual size is 800x600 (pitch 800)
(**) Silicon Motion*Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) Silicon MotionModeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) Silicon Motion*Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) Silicon MotionModeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync
(**) Silicon Motion Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) Silicon MotionModeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync
(==) Silicon MotionDPI set to (75, 75)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 1.2.0
    ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 7.1.1, module version = 0.1.0
    ABI class: X.Org Video Driver, version 1.0
(--) Depth 24 pixmap format is 24 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B]
    [1] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
    [2] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [3] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [4] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [5] -1    0    0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
    [6] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [7] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [8] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [9] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [10] -1    0    0x00000000 - 0x000000ff (0x100) IX[B]
    [11] -1    0    0x0000f400 - 0x0000f4ff (0x100) IX[B]
    [12] -1    0    0x0000f800 - 0x0000f8ff (0x100) IX[B]
    [13] -1    0    0x0000fcc0 - 0x0000fcdf (0x20) IX[B]
    [14] -1    0    0x0000fcf0 - 0x0000fcff (0x10) IX[B]
    [15] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [16] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(==) Silicon MotionWrite-combining range (0xfd000000,0x200000)
(II) Silicon MotionCursor Offset: 001FFC00 Reserved: 001AF800
(II) Silicon MotionDSTN Panel Size = 800x600
(II) Silicon MotionvgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) Silicon MotionPrimary V_BIOS segment is: 0xc000
(II) Silicon MotionCurrent mode 0x58.
(II) Silicon MotionSetting mode 0x58
(II) Silicon MotionFrameBuffer Box: 0,0 - 800,736
(II) Silicon MotionUsing XFree86 Acceleration Architecture (XAA)
    Screen to screen bit blits
    Solid filled rectangles
    8x8 mono pattern filled rectangles
    8x8 color pattern filled rectangles
    CPU to Screen color expansion
    Solid Horizontal and Vertical Lines
    Offscreen Pixmaps
    Setting up tile and stipple cache:
        4 128x128 slots
        32 8x8 color pattern slots
(**) Option "dpms"
(**) Silicon MotionDPMS enabled
(II) Silicon MotionI2C device "I2C bus:SAA 7111A" registered at address 0x48.
(II) Silicon MotionI2C device "I2C bus:SAA 7111A" removed.
(==) RandR enabled
(II) Setting vga for screen 0.
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
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
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
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
    No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!


```Due to reduced RAM, I am trying to install a command-line system Ubuntu 9.10 from the desktop alternate CD.


It installs well, network working.
                                    
[SIZE=2]Followed [https://help.ubuntu.com/community/Installation/InstallationLowMemorySystems](https://help.ubuntu.com/community/Installation/InstallationLowMemorySystems) instructions for installing X server[/SIZE]
 

 [SIZE=2]1)    Installed X.org following the instructions (sudo aptitude install xorg)[/SIZE]
 

 [SIZE=2]2) ran 'startx' from terminal window, errored out.  Here is the failed Xorg.0.log:[/SIZE]


```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu-hp 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=93132f14-c64a-4b65-b316-a03732a20eb6 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 19 09:25:30 2010
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 126f:0810:126f:0810 Silicon Motion, Inc. SM810 LynxE rev 166, Mem @ 0xfd000000/16777216
(==) Using default built-in configuration (30 lines)
(==) --- Start of built-in configuration ---
    Section "Device"
        Identifier    "Builtin Default siliconmotion Device 0"
        Driver    "siliconmotion"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default siliconmotion Screen 0"
        Device    "Builtin Default siliconmotion Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default vesa Device 0"
        Driver    "vesa"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default vesa Screen 0"
        Device    "Builtin Default vesa Device 0"
    EndSection
    Section "Device"
        Identifier    "Builtin Default fbdev Device 0"
        Driver    "fbdev"
    EndSection
    Section "Screen"
        Identifier    "Builtin Default fbdev Screen 0"
        Device    "Builtin Default fbdev Device 0"
    EndSection
    Section "ServerLayout"
        Identifier    "Builtin Default Layout"
        Screen    "Builtin Default siliconmotion Screen 0"
        Screen    "Builtin Default vesa Screen 0"
        Screen    "Builtin Default fbdev Screen 0"
    EndSection
(==) --- End of built-in configuration ---
(==) ServerLayout "Builtin Default Layout"
(**) |-->Screen "Builtin Default siliconmotion Screen 0" (0)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default siliconmotion Device 0"
(==) No monitor specified for screen "Builtin Default siliconmotion Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default vesa Screen 0" (1)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default vesa Device 0"
(==) No monitor specified for screen "Builtin Default vesa Screen 0".
    Using a default monitor configuration.
(**) |-->Screen "Builtin Default fbdev Screen 0" (2)
(**) |   |-->Monitor "<default monitor>"
(**) |   |-->Device "Builtin Default fbdev Device 0"
(==) No monitor specified for screen "Builtin Default fbdev Screen 0".
    Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
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
    compiled for 1.6.4, module version = 1.0.0
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
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "siliconmotion"
(II) Loading /usr/lib/xorg/modules/drivers//siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.7.2
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.6.3, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
(II) SMI: driver (version 1.7.2) for Silicon Motion Lynx chipsets: Lynx,
    LynxE, Lynx3D, LynxEM, LynxEM+, Lynx3DM, Cougar3DR, MSOC
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for siliconmotion
(--) Assigning device section with no busID to primary device
(--) Chipset LynxE found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux//libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.0.2
    ABI class: X.Org Video Driver, version 5.0
(EE) open /dev/fb0: No such file or directory
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) SMI(0): Creating default Display subsection in Screen section
    "Builtin Default siliconmotion Screen 0" for depth/fbbpp 24/32
(==) SMI(0): Depth 24, (--) framebuffer bpp 32
(==) SMI(0): RGB weight 888
(==) SMI(0): Default visual is TrueColor
(==) SMI(0): PCI Burst enabled
(==) SMI(0): PCI Retry enabled
(==) SMI(0): Using Hardware Cursor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) SMI(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) SMI(0): VESA BIOS detected
(II) SMI(0): VESA VBE Version 0.0
(II) SMI(0): VESA VBE Total Mem: 1664 kB
(II) SMI(0): VESA VBE OEM: Sÿ
(--) SMI(0): Chipset: "LynxE"
(==) SMI(0): Dual head disabled
(==) SMI(0): Using XAA acceleration architecture
(--) SMI(0): videoram: 2048kB
(II) SMI(0): Cursor Offset: 001FFC00
(II) SMI(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) SMI(0): Reserved: 001AF800
(II) SMI(0): DSTN Panel Size = 800x600
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) SMI(0): I2C bus "I2C bus" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(==) SMI(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SMI(0): MCLK = 54.409
(II) SMI(0): Output LVDS has no monitor section
(II) SMI(0): Not using default mode "640x350" (vrefresh out of range)
(II) SMI(0): Not using default mode "640x400" (vrefresh out of range)
(II) SMI(0): Not using default mode "720x400" (vrefresh out of range)
(II) SMI(0): Not using default mode "640x480" (exceeds panel dimensions)
(II) SMI(0): Not using default mode "640x480" (vrefresh out of range)
(II) SMI(0): Not using default mode "640x480" (vrefresh out of range)
(II) SMI(0): Not using default mode "640x480" (vrefresh out of range)
(II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
(II) SMI(0): Not using default mode "800x600" (hsync out of range)
(II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
(II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
(II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
(II) SMI(0): Not using default mode "1024x768" (hsync out of range)
(II) SMI(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SMI(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SMI(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1280x960" (hsync out of range)
(II) SMI(0): Not using default mode "1280x960" (vrefresh out of range)
(II) SMI(0): Not using default mode "1280x1024" (hsync out of range)
(II) SMI(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) SMI(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) SMI(0): Not using default mode "1600x1200" (hsync out of range)
(II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) SMI(0): Not using default mode "1792x1344" (hsync out of range)
(II) SMI(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) SMI(0): Not using default mode "1856x1392" (hsync out of range)
(II) SMI(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) SMI(0): Not using default mode "1920x1440" (hsync out of range)
(II) SMI(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) SMI(0): Not using default mode "832x624" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (hsync out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1360x768" (hsync out of range)
(II) SMI(0): Not using default mode "1360x768" (hsync out of range)
(II) SMI(0): Not using default mode "1400x1050" (hsync out of range)
(II) SMI(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1440x900" (hsync out of range)
(II) SMI(0): Not using default mode "1600x1024" (hsync out of range)
(II) SMI(0): Not using default mode "1680x1050" (hsync out of range)
(II) SMI(0): Not using default mode "1680x1050" (hsync out of range)
(II) SMI(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1920x1080" (hsync out of range)
(II) SMI(0): Not using default mode "1920x1200" (hsync out of range)
(II) SMI(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) SMI(0): Not using default mode "2048x1536" (hsync out of range)
(II) SMI(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) SMI(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) SMI(0): Printing probed modes for output LVDS
(II) SMI(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) SMI(0): Output LVDS connected
(II) SMI(0): Using fuzzy aspect match for initial modes
(II) SMI(0): Output LVDS using initial mode 800x600
(EE) SMI(0): Not enough video memory for the configured screen size (800x800) and color depth.
(II) UnloadModule: "siliconmotion"
(II) UnloadModule: "vbe"
(II) Unloading /usr/lib/xorg/modules//libvbe.so
(II) UnloadModule: "int10"
(II) Unloading /usr/lib/xorg/modules//libint10.so
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log


```[SIZE=2]3)    ran 'sudo X -configure' to get xorg.conf.new generated[/SIZE]
 

 [SIZE=2]4) moved working xorg.conf from 6.10 installation, to 9.10 installation
[/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]5)    compared permissions between the xorg.conf.new and the 6.10 xorg.con file. Permissions were the same -rw-r--r--  but I was owner and group.  Changed owner to 'root' and group to 'root'[/SIZE]
 

 [SIZE=2]9)    ran 'sudo cp xorg.conf /etc/X11' to move file from my home directory to X11 directory[/SIZE]
 

 [SIZE=2]10)    ran 'startx' which failed.[/SIZE]


[SIZE=2]Here is the failed xorg.0.log on 9.10 using the xorg.conf from the 6.10 install:[/SIZE]


```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ubuntu-hp 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=93132f14-c64a-4b65-b316-a03732a20eb6 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
    Before reporting problems, check [http://wiki.x.org]("http://wiki.x.org/")
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 19 09:39:07 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Silicon Motion, Inc. SM810 LynxE"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/X11/fonts/misc" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi/" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/Type1" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/100dpi" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/75dpi" does not exist.
    Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
    Entry deleted from font path.
(**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Generic Keyboard
(WW) Disabling Configured Mouse
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0:0:2:0) 126f:0810:126f:0810 Silicon Motion, Inc. SM810 LynxE rev 166, Mem @ 0xfd000000/16777216
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded. This was enabled by default and also specified in the config file.
(II) "dri2" will be loaded by default.
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.1.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "siliconmotion"
(II) Loading /usr/lib/xorg/modules/drivers//siliconmotion_drv.so
(II) Module siliconmotion: vendor="X.Org Foundation"
    compiled for 1.6.1.901, module version = 1.7.2
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 1.0.0
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(II) SMI: driver (version 1.7.2) for Silicon Motion Lynx chipsets: Lynx,
    LynxE, Lynx3D, LynxEM, LynxEM+, Lynx3DM, Cougar3DR, MSOC
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for siliconmotion
(--) Chipset LynxE found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[B]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[B]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[B]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[B]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[B]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[B]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[B]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[B]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[B]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[B]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.4, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(**) SMI(0): Depth 24, (--) framebuffer bpp 32
(==) SMI(0): RGB weight 888
(==) SMI(0): Default visual is TrueColor
(==) SMI(0): PCI Burst enabled
(==) SMI(0): PCI Retry enabled
(==) SMI(0): Using Hardware Cursor
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SMI(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) SMI(0): VESA BIOS detected
(II) SMI(0): VESA VBE Version 0.0
(II) SMI(0): VESA VBE Total Mem: 1664 kB
(II) SMI(0): VESA VBE OEM: Sÿ
(--) SMI(0): Chipset: "LynxE"
(==) SMI(0): Dual head disabled
(==) SMI(0): Using XAA acceleration architecture
(--) SMI(0): videoram: 2048kB
(II) SMI(0): Cursor Offset: 001FFC00
(II) SMI(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) SMI(0): Reserved: 001AF800
(II) SMI(0): DSTN Panel Size = 800x600
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) SMI(0): I2C bus "I2C bus" initialized.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(==) SMI(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SMI(0): MCLK = 54.409
(II) SMI(0): Output LVDS using monitor section Generic Monitor
(II) SMI(0): Not using default mode "640x350" (vrefresh out of range)
(II) SMI(0): Not using default mode "640x400" (vrefresh out of range)
(II) SMI(0): Not using default mode "720x400" (vrefresh out of range)
(II) SMI(0): Not using default mode "640x480" (exceeds panel dimensions)
(II) SMI(0): Not using default mode "640x480" (vrefresh out of range)
(II) SMI(0): Not using default mode "640x480" (vrefresh out of range)
(II) SMI(0): Not using default mode "640x480" (vrefresh out of range)
(II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
(II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
(II) SMI(0): Not using default mode "800x600" (vrefresh out of range)
(II) SMI(0): Not using default mode "1024x768" (exceeds panel dimensions)
(II) SMI(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SMI(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SMI(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1280x960" (hsync out of range)
(II) SMI(0): Not using default mode "1280x960" (vrefresh out of range)
(II) SMI(0): Not using default mode "1280x1024" (hsync out of range)
(II) SMI(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) SMI(0): Not using default mode "1280x1024" (vrefresh out of range)
(II) SMI(0): Not using default mode "1600x1200" (hsync out of range)
(II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) SMI(0): Not using default mode "1600x1200" (vrefresh out of range)
(II) SMI(0): Not using default mode "1792x1344" (hsync out of range)
(II) SMI(0): Not using default mode "1792x1344" (vrefresh out of range)
(II) SMI(0): Not using default mode "1856x1392" (hsync out of range)
(II) SMI(0): Not using default mode "1856x1392" (vrefresh out of range)
(II) SMI(0): Not using default mode "1920x1440" (hsync out of range)
(II) SMI(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) SMI(0): Not using default mode "832x624" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (hsync out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1152x864" (vrefresh out of range)
(II) SMI(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) SMI(0): Not using default mode "1360x768" (exceeds panel dimensions)
(II) SMI(0): Not using default mode "1400x1050" (hsync out of range)
(II) SMI(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1400x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1440x900" (hsync out of range)
(II) SMI(0): Not using default mode "1600x1024" (hsync out of range)
(II) SMI(0): Not using default mode "1680x1050" (hsync out of range)
(II) SMI(0): Not using default mode "1680x1050" (hsync out of range)
(II) SMI(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1680x1050" (vrefresh out of range)
(II) SMI(0): Not using default mode "1920x1080" (hsync out of range)
(II) SMI(0): Not using default mode "1920x1200" (hsync out of range)
(II) SMI(0): Not using default mode "1920x1440" (vrefresh out of range)
(II) SMI(0): Not using default mode "2048x1536" (hsync out of range)
(II) SMI(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) SMI(0): Not using default mode "2048x1536" (vrefresh out of range)
(II) SMI(0): Printing probed modes for output LVDS
(II) SMI(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) SMI(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
(II) SMI(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) SMI(0): Output LVDS connected
(II) SMI(0): Using fuzzy aspect match for initial modes
(II) SMI(0): Output LVDS using initial mode 800x600
(EE) SMI(0): Not enough video memory for the configured screen size (800x800) and color depth.
(II) UnloadModule: "siliconmotion"
(II) UnloadModule: "vbe"
(II) UnloadModule: "int10"
(II) UnloadModule: "vgahw"
(II) Unloading /usr/lib/xorg/modules//libvgahw.so
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org]("http://wiki.x.org/")
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
```

---

### Post by audiomick on 2010-01-19
Hi.
I can't help you with your problem, I'm sorry, but here's a tip for posting.
If you put code tags around those blocks of output using the # button in the post window, it makes a nice box with a scroll bar around the text and makes the post lots easier to deal with for someone reading it. If you want to edit and add them, you have to click on "go advanced" to get the # button.

Good luck with your problem

---

### Post by jwmueller5 on 2010-01-19
Thank you.  That makes it much easier to read.  I had seen that done in posts but didn't know how to do it.

---

