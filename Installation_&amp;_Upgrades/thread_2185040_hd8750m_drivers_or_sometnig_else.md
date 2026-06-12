---
title: "hd8750m drivers or sometnig else?"
date: 2013-10-31
forum: Installation &amp; Upgrades
---

### Post by xmxx on 2013-10-31
Hi 
Im having troble with istaling amd drivers on Lenovo G500 laptop.

On ubunutu 12.04

When try to install 13.4 driver it says: Unsupported hardware
When try to 13.11beta6, 13.10.beta2, 13.9 installation is completed and after reboot it start in low resolution mode with only solution going back to Intel only GPU.

```
[   223.211] X.Org X Server 1.13.3
Release Date: 2013-03-07
[   223.211] X Protocol Version 11, Revision 0
[   223.211] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[   223.211] Current Operating System: Linux muj-2 3.8.0-32-generic #47~precise1-Ubuntu SMP Wed Oct 2 16:22:28 UTC 2013 i686
[   223.211] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-32-generic root=UUID=8ff31357-c794-4a6e-b5e1-0656eb8a1111 ro quiet splash vt.handoff=7
[   223.212] Build Date: 16 October 2013  04:46:12PM
[   223.212] xorg-server 2:1.13.3-0ubuntu6~precise3 (For technical support please see http://www.ubuntu.com/support) 
[   223.212] Current version of pixman: 0.24.4
[   223.212] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   223.212] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   223.212] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Oct 31 21:27:02 2013
[   223.213] (==) Using config file: "/etc/X11/xorg.conf"
[   223.213] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   223.213] (==) ServerLayout "aticonfig Layout"
[   223.213] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[   223.213] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[   223.214] (**) |   |-->Device "aticonfig-Device[0]-0"
[   223.214] (==) Automatically adding devices
[   223.214] (==) Automatically enabling devices
[   223.214] (==) Automatically adding GPU devices
[   223.214] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   223.214] 	Entry deleted from font path.
[   223.214] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   223.214] 	Entry deleted from font path.
[   223.214] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   223.214] 	Entry deleted from font path.
[   223.214] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   223.214] 	Entry deleted from font path.
[   223.214] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   223.214] 	Entry deleted from font path.
[   223.214] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   223.214] 	Entry deleted from font path.
[   223.214] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   223.214] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   223.214] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   223.214] (II) Loader magic: 0xb7763620
[   223.214] (II) Module ABI versions:
[   223.214] 	X.Org ANSI C Emulation: 0.4
[   223.214] 	X.Org Video Driver: 13.1
[   223.214] 	X.Org XInput driver : 18.0
[   223.214] 	X.Org Server Extension : 7.0
[   223.214] (II) config/udev: Adding drm device (/dev/dri/card0)
[   223.217] (--) PCI:*(0:0:2:0) 8086:0166:17aa:3800 rev 9, Mem @ 0xd8000000/4194304, 0xc0000000/268435456, I/O @ 0x00004000/64
[   223.217] (--) PCI: (0:1:0:0) 1002:6600:17aa:3800 rev 0, Mem @ 0xd0000000/134217728, 0xd8600000/262144, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[   223.217] (II) Open ACPI successful (/var/run/acpid.socket)
[   223.217] Initializing built-in extension Generic Event Extension
[   223.217] Initializing built-in extension SHAPE
[   223.217] Initializing built-in extension MIT-SHM
[   223.217] Initializing built-in extension XInputExtension
[   223.217] Initializing built-in extension XTEST
[   223.218] Initializing built-in extension BIG-REQUESTS
[   223.218] Initializing built-in extension SYNC
[   223.218] Initializing built-in extension XKEYBOARD
[   223.218] Initializing built-in extension XC-MISC
[   223.218] Initializing built-in extension SECURITY
[   223.218] Initializing built-in extension XINERAMA
[   223.218] Initializing built-in extension XFIXES
[   223.218] Initializing built-in extension RENDER
[   223.218] Initializing built-in extension RANDR
[   223.218] Initializing built-in extension COMPOSITE
[   223.218] Initializing built-in extension DAMAGE
[   223.218] Initializing built-in extension MIT-SCREEN-SAVER
[   223.220] Initializing built-in extension DOUBLE-BUFFER
[   223.220] Initializing built-in extension RECORD
[   223.221] Initializing built-in extension DPMS
[   223.222] Initializing built-in extension X-Resource
[   223.222] Initializing built-in extension XVideo
[   223.223] Initializing built-in extension XVideo-MotionCompensation
[   223.223] Initializing built-in extension XFree86-VidModeExtension
[   223.224] Initializing built-in extension XFree86-DGA
[   223.225] Initializing built-in extension XFree86-DRI
[   223.225] Initializing built-in extension DRI2
[   223.225] (II) "glx" will be loaded by default.
[   223.225] (II) LoadModule: "glx"
[   223.225] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   223.226] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[   223.226] 	compiled for 6.9.0, module version = 1.0.0
[   223.226] Loading extension GLX
[   223.226] (II) LoadModule: "fglrx"
[   223.226] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[   223.236] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[   223.236] 	compiled for 1.4.99.906, module version = 13.20.5
[   223.236] 	Module class: X.Org Video Driver
[   223.236] (II) Loading sub module "fglrxdrm"
[   223.236] (II) LoadModule: "fglrxdrm"
[   223.236] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[   223.236] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[   223.236] 	compiled for 1.4.99.906, module version = 13.20.5
[   223.236] (II) AMD Proprietary Linux Driver Version Identifier:13.20.5
[   223.236] (II) AMD Proprietary Linux Driver Release Identifier: UNSUPPORTED-13.20.11                 
[   223.236] (II) AMD Proprietary Linux Driver Build Date: Sep 21 2013 02:26:05
[   223.236] (--) using VT number 7


[   223.239] (WW) Falling back to old probe method for fglrx
[   223.254] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[   223.256] ukiDynamicMajor: found major device number 251
[   223.256] ukiDynamicMajor: found major device number 251
[   223.256] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   223.256] ukiOpenDevice: node name is /dev/ati/card0
[   223.256] ukiOpenDevice: open result is 10, (OK)
[   223.256] ukiOpenByBusid: ukiOpenMinor returns 10
[   223.256] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   223.299] (--) Chipset Supported AMD Graphics Processor (0x6600) found
[   223.299] (II) fglrx: intel VGA device detected, load intel driver.
[   223.299] (II) LoadModule: "intel"
[   223.299] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   223.300] (II) Module intel: vendor="X.Org Foundation"
[   223.300] 	compiled for 1.13.3, module version = 2.21.6
[   223.300] 	Module class: X.Org Video Driver
[   223.300] 	ABI class: X.Org Video Driver, version 13.1
[   223.301] (II) fglrx(0): pEnt->device->identifier=0xb7bd5748
[   223.301] (II) intel(1): pEnt->device->identifier=(nil)
[   223.301] (EE) Screen 1 deleted because of no matching config section.
[   223.301] (II) UnloadModule: "intel"
[   223.301] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[   223.301] (II) fglrx(0): PowerXpress: Discrete GPU is selected.
[   223.344] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[   223.344] (==) fglrx(0): RGB weight 888
[   223.344] (==) fglrx(0): Default visual is TrueColor
[   223.344] (**) fglrx(0): Option "Tiling" "off"
[   223.344] (**) fglrx(0): Option "LinearFramebuffer" "on"
[   223.344] (**) fglrx(0): ChipID override: 0x0166
[   223.344] (**) fglrx(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
[   223.344] (**) fglrx(0): Relaxed fencing enabled
[   223.344] (**) fglrx(0): Wait on SwapBuffers? enabled
[   223.344] (**) fglrx(0): Triple buffering? enabled
[   223.344] (**) fglrx(0): Framebuffer linear
[   223.344] (**) fglrx(0): Pixmaps linear
[   223.344] (**) fglrx(0): 3D buffers tiled
[   223.344] (**) fglrx(0): SwapBuffers wait enabled
[   223.344] (==) fglrx(0): video overlay key set to 0x101fe
[   223.345] (II) fglrx(0): Output LVDS1 using monitor section aticonfig-Monitor[0]-0
[   223.345] (--) fglrx(0): found backlight control interface /sys/class/backlight/acpi_video1
[   223.360] (II) fglrx(0): Output VGA1 has no monitor section
[   223.376] (II) fglrx(0): Output HDMI1 has no monitor section
[   223.424] (II) fglrx(0): Output DP1 has no monitor section
[   223.424] (II) fglrx(0): EDID for output LVDS1
[   223.424] (II) fglrx(0): Manufacturer: LGD  Model: 33a  Serial#: 0
[   223.424] (II) fglrx(0): Year: 2011  Week: 0
[   223.424] (II) fglrx(0): EDID Version: 1.3
[   223.424] (II) fglrx(0): Digital Display Input
[   223.424] (II) fglrx(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[   223.424] (II) fglrx(0): Gamma: 2.20
[   223.424] (II) fglrx(0): No DPMS capabilities specified
[   223.424] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   223.424] (II) fglrx(0): First detailed timing is preferred mode
[   223.424] (II) fglrx(0): redX: 0.618 redY: 0.369   greenX: 0.355 greenY: 0.603
[   223.424] (II) fglrx(0): blueX: 0.151 blueY: 0.103   whiteX: 0.313 whiteY: 0.329
[   223.424] (II) fglrx(0): Manufacturer's mask: 0
[   223.424] (II) fglrx(0): Supported detailed timing:
[   223.424] (II) fglrx(0): clock: 70.0 MHz   Image Size:  344 x 194 mm
[   223.424] (II) fglrx(0): h_active: 1366  h_sync: 1402  h_sync_end 1450 h_blank_end 1492 h_border: 0
[   223.424] (II) fglrx(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 782 v_border: 0
[   223.424] (II) fglrx(0):  LG Display
[   223.424] (II) fglrx(0):  LP156WH4-TLN2
[   223.424] (II) fglrx(0): EDID (in hex):
[   223.424] (II) fglrx(0): 	00ffffffffffff0030e43a0300000000
[   223.424] (II) fglrx(0): 	00150103802213780a61d59e5e5b9a26
[   223.424] (II) fglrx(0): 	1a505400000001010101010101010101
[   223.424] (II) fglrx(0): 	010101010101581b567e50000e302430
[   223.424] (II) fglrx(0): 	350058c2100000190000000000000000
[   223.424] (II) fglrx(0): 	00000000000000000000000000fe004c
[   223.424] (II) fglrx(0): 	4720446973706c61790a2020000000fe
[   223.424] (II) fglrx(0): 	004c503135365748342d544c4e320082
[   223.425] (II) fglrx(0): Not using default mode "320x240" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "400x300" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "400x300" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "512x384" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "640x480" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "640x512" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "800x600" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "896x672" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "928x696" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "960x720" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "576x432" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "680x384" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "680x384" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "700x525" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "720x450" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "800x512" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "840x525" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "840x525" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "960x540" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "960x600" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Not using default mode "1024x768" (doublescan mode not supported)
[   223.425] (II) fglrx(0): Printing probed modes for output LVDS1
[   223.425] (II) fglrx(0): Modeline "1366x768"x60.0   70.00  1366 1402 1450 1492  768 771 776 782 -hsync -vsync (46.9 kHz eP)
[   223.425] (II) fglrx(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[   223.425] (II) fglrx(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[   223.425] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[   223.425] (II) fglrx(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[   223.425] (II) fglrx(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[   223.425] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[   223.440] (II) fglrx(0): EDID for output VGA1
[   223.456] (II) fglrx(0): EDID for output HDMI1
[   223.504] (II) fglrx(0): EDID for output DP1
[   223.504] (II) fglrx(0): Output LVDS1 connected
[   223.504] (II) fglrx(0): Output VGA1 disconnected
[   223.504] (II) fglrx(0): Output HDMI1 disconnected
[   223.504] (II) fglrx(0): Output DP1 disconnected
[   223.504] (II) fglrx(0): Using exact sizes for initial modes
[   223.504] (II) fglrx(0): Output LVDS1 using initial mode 1366x768
[   223.504] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   223.504] (II) fglrx(0): Kernel page flipping support detected, enabling
[   223.504] (==) fglrx(0): DPI set to (96, 96)
[   223.504] (II) Loading sub module "fb"
[   223.504] (II) LoadModule: "fb"
[   223.504] (II) Loading /usr/lib/xorg/modules/libfb.so
[   223.505] (II) Module fb: vendor="X.Org Foundation"
[   223.505] 	compiled for 1.13.3, module version = 1.0.0
[   223.505] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   223.505] (II) Loading sub module "dri2"
[   223.505] (II) LoadModule: "dri2"
[   223.505] (II) Module "dri2" already built-in
[   223.505] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[   223.505] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   223.505] (==) fglrx(0): Default visual is TrueColor
[   223.505] (**) fglrx(0): Option "DPMS" "true"
[   223.505] (==) fglrx(0): RGB weight 888
[   223.505] (II) fglrx(0): Using 8 bits per RGB 
[   223.505] (==) fglrx(0): Buffer Tiling is ON
[   223.505] (II) Loading sub module "fglrxdrm"
[   223.505] (II) LoadModule: "fglrxdrm"
[   223.505] (II) Loading /usr/lib/xorg/modules/linux/libfglrxdrm.so
[   223.505] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[   223.505] 	compiled for 1.4.99.906, module version = 13.20.5
[   223.508] ukiDynamicMajor: found major device number 251
[   223.508] ukiDynamicMajor: found major device number 251
[   223.508] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   223.508] ukiOpenDevice: node name is /dev/ati/card0
[   223.508] ukiOpenDevice: open result is 13, (OK)
[   223.508] ukiOpenByBusid: ukiOpenMinor returns 13
[   223.508] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   223.509] (**) fglrx(0): NoAccel = NO
[   223.509] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[   223.509] (--) fglrx(0): Chipset: "AMD Radeon HD 8600/8700M" (Chipset = 0x6600)
[   223.509] (--) fglrx(0): (PciSubVendor = 0x17aa, PciSubDevice = 0x3800)
[   223.509] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[   223.509] (--) fglrx(0): Linear framebuffer (phys) at 0xd0000000
[   223.509] (--) fglrx(0): MMIO registers at 0xd8600000
[   223.509] (--) fglrx(0): I/O port at 0x00003000
[   223.509] (==) fglrx(0): ROM-BIOS at 0x000c0000
[   223.509] (II) fglrx(0): AC Adapter is used
[   223.509] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[   223.509] (--) fglrx(0): Video RAM: 2097152 kByte, Type: DDR3
[   223.509] (II) fglrx(0): PCIE card detected
[   223.509] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[   223.509] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[   223.529] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf400000000, MCFBSize = 0x80000000)
[   223.529] (II) fglrx(0): RandR 1.2 support is enabled!
[   223.529] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[   223.530] (==) fglrx(0): Center Mode is disabled 
[   223.530] (II) Loading sub module "fb"
[   223.530] (II) LoadModule: "fb"
[   223.530] (II) Loading /usr/lib/xorg/modules/libfb.so
[   223.530] (II) Module fb: vendor="X.Org Foundation"
[   223.530] 	compiled for 1.13.3, module version = 1.0.0
[   223.530] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   223.530] (II) Loading sub module "ddc"
[   223.530] (II) LoadModule: "ddc"
[   223.530] (II) Module "ddc" already built-in
[   223.540] (II) fglrx(0): Adapter AMD Radeon HD 8600/8700M has 2 configurable heads and 0 displays connected.
[   223.540] (==) fglrx(0):  PseudoColor visuals disabled
[   223.540] (II) Loading sub module "ramdac"
[   223.540] (II) LoadModule: "ramdac"
[   223.541] (II) Module "ramdac" already built-in
[   223.541] (==) fglrx(0): NoDRI = NO
[   223.541] (==) fglrx(0): Capabilities: 0x00000000
[   223.541] (==) fglrx(0): CapabilitiesEx: 0x00000000
[   223.541] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[   223.541] (==) fglrx(0): UseFastTLS=0
[   223.541] (II) fglrx(0): TearFreeDesktop is not supported on PowerXpress systems currently.
[   223.541] (--) Depth 24 pixmap format is 32 bpp
[   223.541] (II) LoadModule: "glesx"
[   223.541] (II) Loading /usr/lib/xorg/modules/glesx.so
[   223.543] (II) Module glesx: vendor="X.Org Foundation"
[   223.543] 	compiled for 1.4.99.906, module version = 1.0.0
[   223.543] Loading extension GLESX
[   223.543] (II) fglrx(0): [DRI2] Setup complete
[   223.543] (II) fglrx(0): [DRI2]   DRI driver: i965
[   223.543] (II) fglrx(0): Allocated new frame buffer 1408x768 stride 5632, untiled
[   223.544] (II) UXA(0): Driver registered support for the following operations:
[   223.544] (II)         solid
[   223.544] (II)         copy
[   223.544] (II)         composite (RENDER acceleration)
[   223.544] (II)         put_image
[   223.544] (II)         get_image
[   223.544] (==) fglrx(0): Backing store disabled
[   223.544] (==) fglrx(0): Silken mouse enabled
[   223.544] (II) fglrx(0): Initializing HW Cursor
[   223.544] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   223.547] (**) fglrx(0): DPMS enabled
[   223.547] (==) fglrx(0): Intel XvMC decoder enabled
[   223.547] (II) fglrx(0): Set up textured video
[   223.547] (II) fglrx(0): [XvMC] xvmc_vld driver initialized.
[   223.547] (II) fglrx(0): direct rendering: DRI2 Enabled
[   223.547] (WW) fglrx(0): Option "VendorName" is not used
[   223.547] (WW) fglrx(0): Option "ModelName" is not used
[   223.547] (WW) fglrx(0): Option "Shadow" is not used
[   223.547] (WW) fglrx(0): Option "Tiling" is not used
[   223.547] (WW) fglrx(0): Option "LinearFramebuffer" is not used
[   223.547] (==) fglrx(0): hotplug detection: "enabled"
[   223.556] Loading extension ATIFGLRXDRI
[   223.556] (II) fglrx(0): doing swlDriScreenInit
[   223.556] (II) fglrx(0): swlDriScreenInit for fglrx driver
[   223.556] ukiDynamicMajor: found major device number 251
[   223.556] ukiDynamicMajor: found major device number 251
[   223.556] ukiDynamicMajor: found major device number 251
[   223.556] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   223.556] ukiOpenDevice: node name is /dev/ati/card0
[   223.556] ukiOpenDevice: open result is 15, (OK)
[   223.556] ukiOpenByBusid: ukiOpenMinor returns 15
[   223.556] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   223.556] (II) fglrx(0): [uki] DRM interface version 1.0
[   223.556] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[   223.556] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x5000
[   223.556] (II) fglrx(0): [uki] mapped SAREA 0x5000 to 0xb56f9000
[   223.556] (II) fglrx(0): [uki] framebuffer handle = 0x6000
[   223.556] (II) fglrx(0): [uki] added 1 reserved context for kernel
[   223.556] (II) fglrx(0): swlDriScreenInit done
[   223.557] (II) fglrx(0): Kernel Module Version Information:
[   223.557] (II) fglrx(0):     Name: fglrx
[   223.557] (II) fglrx(0):     Version: 13.20.5
[   223.557] (II) fglrx(0):     Date: Sep 21 2013
[   223.557] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[   223.557] (II) fglrx(0): Kernel Module version matches driver.
[   223.557] (II) fglrx(0): Kernel Module Build Time Information:
[   223.557] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.8.0-32-generic
[   223.557] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[   223.557] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[   223.557] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[   223.557] (II) fglrx(0): [uki] register handle = 0x00007000
[   223.557] (EE) fglrx(0): Failed to open CMMQS connection.
[   223.557] (EE) 
[   223.557] (EE) Backtrace:
[   223.557] (EE) 0: /usr/bin/X (xorg_backtrace+0x49) [0xb76ebeb9]
[   223.557] (EE) 1: /usr/bin/X (0xb7534000+0x1bbcba) [0xb76efcba]
[   223.557] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb751140c]
[   223.557] (EE) 3: /usr/lib/xorg/modules/drivers/fglrx_drv.so (swlDrmFreeSurfaces+0x58) [0xb66b85a8]
[   223.558] (EE) 4: /usr/lib/xorg/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxDriCloseScreen+0x1d1) [0xb663c6b1]
[   223.558] (EE) 5: /usr/lib/xorg/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxDriScreenInit+0x87e) [0xb663bb3e]
[   223.558] (EE) 6: /usr/lib/xorg/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxScreenInit+0x1131) [0xb6634b81]
[   223.558] (EE) 7: /usr/bin/X (AddScreen+0x88) [0xb75707c8]
[   223.558] (EE) 
[   223.558] (EE) Segmentation fault at address 0x7b0
[   223.558] 
Fatal server error:
[   223.558] Caught signal 11 (Segmentation fault). Server aborting
[   223.558] 
[   223.558] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   223.559] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   223.559] (EE) 
[   223.583] Server terminated with error (1). Closing log file.
```

---

### Post by xmxx on 2013-11-04
OK in ubunutu 13.10 working out of box
halflife 2 lost coast 80fps

---

### Post by peter-lopen on 2013-11-22
> **xmxx said:**
> OK in ubunutu 13.10 working out of box
halflife 2 lost coast 80fps

What version are you using - 32bit or 64bit? Thanks.

---

