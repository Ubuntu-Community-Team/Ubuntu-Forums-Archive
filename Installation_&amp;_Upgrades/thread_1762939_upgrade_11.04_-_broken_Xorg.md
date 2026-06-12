---
title: "upgrade 11.04 - broken Xorg"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by heap1 on 2011-05-19
Hello,
i recently upgraded from 10.4 to 11.04, what happened is my X completly got broken. First strange thing was that i had laptop display + some unknow display in display setting. When i edit XY and deleted fbdev the unknown monitor dissapeared. 

But there is another problem, when i attach my extrnal lcd the workspace has strange behaviour / external display has 3/4 of black the laptopt one has half display black... 

Thanks 

Log if fully of messages bellow (when i attach extrnal lcd) + xorg.0 attached.

[  1319.790] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1319.790] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1319.790] (II) intel(0): Printing DDC gathered Modelines:
[  1319.790] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1320.574] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled





[    34.557] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    34.571] X Protocol Version 11, Revision 0
[    34.571] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    34.571] Current Operating System: Linux phear 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64
[    34.571] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=2560e2f4-72eb-48af-a5f8-3ab707baf6ae ro quiet nosplash
[    34.571] Build Date: 19 April 2011  03:40:45PM
[    34.571] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    34.571] Current version of pixman: 0.20.2
[    34.571] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    34.571] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    34.571] (==) Log file: "/var/log/Xorg.0.log", Time: Tue May 17 18:56:48 2011
[    34.571] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    34.776] (==) No Layout section.  Using the first Screen section.
[    34.777] (==) No screen section available. Using defaults.
[    34.777] (**) |-->Screen "Default Screen Section" (0)
[    34.777] (**) |   |-->Monitor "<default monitor>"
[    34.777] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    34.777] (==) Automatically adding devices
[    34.777] (==) Automatically enabling devices
[    34.777] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    34.777] 	Entry deleted from font path.
[    34.778] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    34.778] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    34.778] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    34.778] (II) Loader magic: 0x7e0280
[    34.778] (II) Module ABI versions:
[    34.778] 	X.Org ANSI C Emulation: 0.4
[    34.778] 	X.Org Video Driver: 10.0
[    34.778] 	X.Org XInput driver : 12.3
[    34.778] 	X.Org Server Extension : 5.0
[    34.778] (--) PCI:*(0:0:2:0) 8086:0046:103c:149b rev 18, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00003030/8
[    34.778] (II) Open ACPI successful (/var/run/acpid.socket)
[    34.778] (II) LoadModule: "extmod"
[    34.793] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    34.890] (II) Module extmod: vendor="X.Org Foundation"
[    34.890] 	compiled for 1.10.1, module version = 1.0.0
[    34.890] 	Module class: X.Org Server Extension
[    34.890] 	ABI class: X.Org Server Extension, version 5.0
[    34.890] (II) Loading extension MIT-SCREEN-SAVER
[    34.890] (II) Loading extension XFree86-VidModeExtension
[    34.890] (II) Loading extension XFree86-DGA
[    34.890] (II) Loading extension DPMS
[    34.890] (II) Loading extension XVideo
[    34.890] (II) Loading extension XVideo-MotionCompensation
[    34.890] (II) Loading extension X-Resource
[    34.890] (II) LoadModule: "dbe"
[    34.891] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    34.893] (II) Module dbe: vendor="X.Org Foundation"
[    34.893] 	compiled for 1.10.1, module version = 1.0.0
[    34.893] 	Module class: X.Org Server Extension
[    34.893] 	ABI class: X.Org Server Extension, version 5.0
[    34.893] (II) Loading extension DOUBLE-BUFFER
[    34.893] (II) LoadModule: "glx"
[    34.893] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    34.912] (II) Module glx: vendor="X.Org Foundation"
[    34.912] 	compiled for 1.10.1, module version = 1.0.0
[    34.912] 	ABI class: X.Org Server Extension, version 5.0
[    34.912] (==) AIGLX enabled
[    34.912] (II) Loading extension GLX
[    35.037] (II) LoadModule: "record"
[    35.038] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    35.058] (II) Module record: vendor="X.Org Foundation"
[    35.058] 	compiled for 1.10.1, module version = 1.13.0
[    35.058] 	Module class: X.Org Server Extension
[    35.058] 	ABI class: X.Org Server Extension, version 5.0
[    35.058] (II) Loading extension RECORD
[    35.058] (II) LoadModule: "dri"
[    35.058] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    35.082] (II) Module dri: vendor="X.Org Foundation"
[    35.082] 	compiled for 1.10.1, module version = 1.0.0
[    35.082] 	ABI class: X.Org Server Extension, version 5.0
[    35.082] (II) Loading extension XFree86-DRI
[    35.082] (II) LoadModule: "dri2"
[    35.082] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    35.084] (II) Module dri2: vendor="X.Org Foundation"
[    35.084] 	compiled for 1.10.1, module version = 1.2.0
[    35.084] 	ABI class: X.Org Server Extension, version 5.0
[    35.084] (II) Loading extension DRI2
[    35.084] (==) Matched intel as autoconfigured driver 0
[    35.084] (==) Matched vesa as autoconfigured driver 1
[    35.084] (==) Matched fbdev as autoconfigured driver 2
[    35.084] (==) Assigned the driver to the xf86ConfigLayout
[    35.084] (II) LoadModule: "intel"
[    35.084] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    35.280] (II) Module intel: vendor="X.Org Foundation"
[    35.280] 	compiled for 1.10.1, module version = 2.14.0
[    35.280] 	Module class: X.Org Video Driver
[    35.280] 	ABI class: X.Org Video Driver, version 10.0
[    35.280] (II) LoadModule: "vesa"
[    35.280] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    35.294] (II) Module vesa: vendor="X.Org Foundation"
[    35.294] 	compiled for 1.10.0, module version = 2.3.0
[    35.294] 	Module class: X.Org Video Driver
[    35.294] 	ABI class: X.Org Video Driver, version 10.0
[    35.294] (II) LoadModule: "fbdev"
[    35.294] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    35.317] (II) Module fbdev: vendor="X.Org Foundation"
[    35.317] 	compiled for 1.10.0, module version = 0.4.2
[    35.317] 	ABI class: X.Org Video Driver, version 10.0
[    35.317] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[    35.318] (II) VESA: driver for VESA chipsets: vesa
[    35.318] (II) FBDEV: driver for framebuffer: fbdev
[    35.318] (++) using VT number 7

[    35.320] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    35.320] (WW) Falling back to old probe method for vesa
[    35.320] (WW) Falling back to old probe method for fbdev
[    35.320] (II) Loading sub module "fbdevhw"
[    35.320] (II) LoadModule: "fbdevhw"
[    35.320] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    35.340] (II) Module fbdevhw: vendor="X.Org Foundation"
[    35.341] 	compiled for 1.10.1, module version = 0.0.2
[    35.341] 	ABI class: X.Org Video Driver, version 10.0
[    35.341] drmOpenDevice: node name is /dev/dri/card0
[    35.341] drmOpenDevice: open result is 9, (OK)
[    35.341] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    35.341] drmOpenDevice: node name is /dev/dri/card0
[    35.341] drmOpenDevice: open result is 9, (OK)
[    35.341] drmOpenByBusid: drmOpenMinor returns 9
[    35.341] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    35.341] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    35.341] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    35.341] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    35.341] (==) intel(0): RGB weight 888
[    35.341] (==) intel(0): Default visual is TrueColor
[    35.341] (II) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    35.341] (--) intel(0): Chipset: "Arrandale"
[    35.341] (**) intel(0): Relaxed fencing disabled
[    35.341] (**) intel(0): Tiling enabled
[    35.341] (**) intel(0): SwapBuffers wait enabled
[    35.341] (==) intel(0): video overlay key set to 0x101fe
[    35.433] (II) intel(0): Output VGA1 has no monitor section
[    35.433] (II) intel(0): Output LVDS1 has no monitor section
[    35.433] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    35.434] (II) intel(0): Output DP1 has no monitor section
[    35.444] (II) intel(0): Output HDMI1 has no monitor section
[    35.445] (II) intel(0): Output DP2 has no monitor section
[    35.462] (II) intel(0): EDID for output VGA1
[    35.462] (II) intel(0): EDID for output LVDS1
[    35.462] (II) intel(0): Manufacturer: AUO  Model: 112c  Serial#: 0
[    35.462] (II) intel(0): Year: 2008  Week: 1
[    35.462] (II) intel(0): EDID Version: 1.3
[    35.462] (II) intel(0): Digital Display Input
[    35.462] (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 16
[    35.462] (II) intel(0): Gamma: 2.20
[    35.462] (II) intel(0): No DPMS capabilities specified
[    35.462] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    35.462] (II) intel(0): First detailed timing is preferred mode
[    35.462] (II) intel(0): redX: 0.585 redY: 0.335   greenX: 0.330 greenY: 0.575
[    35.462] (II) intel(0): blueX: 0.155 blueY: 0.130   whiteX: 0.313 whiteY: 0.329
[    35.462] (II) intel(0): Manufacturer's mask: 0
[    35.462] (II) intel(0): Supported detailed timing:
[    35.462] (II) intel(0): clock: 69.3 MHz   Image Size:  293 x 164 mm
[    35.462] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1456 h_border: 0
[    35.462] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 793 v_border: 0
[    35.462] (II) intel(0): Supported detailed timing:
[    35.462] (II) intel(0): clock: 69.3 MHz   Image Size:  293 x 164 mm
[    35.462] (II) intel(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1696 h_border: 0
[    35.462] (II) intel(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 1020 v_border: 0
[    35.462] (II) intel(0): Stereo: left channel on sync
[    35.462] side-by-side interleaved(II) intel(0):  AUO
[    35.462] (II) intel(0):  B133XW01 V1
[    35.462] (II) intel(0): EDID (in hex):
[    35.462] (II) intel(0): 	00ffffffffffff0006af2c1100000000
[    35.462] (II) intel(0): 	01120103801d10780af9d59555549327
[    35.462] (II) intel(0): 	21505400000001010101010101010101
[    35.462] (II) intel(0): 	010101010101121b565a500019303020
[    35.462] (II) intel(0): 	360025a410000018121b564a5100fc30
[    35.462] (II) intel(0): 	3020360025a410000020000000fe0041
[    35.462] (II) intel(0): 	554f0a202020202020202020000000fe
[    35.462] (II) intel(0): 	004231333358573031205631200a00b8
[    35.462] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    35.462] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    35.463] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    35.463] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    35.463] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    35.463] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    35.463] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    35.463] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    35.463] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    35.463] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    35.463] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    35.463] (II) intel(0): Printing probed modes for output LVDS1
[    35.463] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    35.463] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    35.463] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz)
[    35.463] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    35.463] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    35.463] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    35.463] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    35.464] (II) intel(0): EDID for output DP1
[    35.473] (II) intel(0): EDID for output HDMI1
[    35.474] (II) intel(0): EDID for output DP2
[    35.474] (II) intel(0): Output VGA1 disconnected
[    35.474] (II) intel(0): Output LVDS1 connected
[    35.474] (II) intel(0): Output DP1 disconnected
[    35.474] (II) intel(0): Output HDMI1 disconnected
[    35.474] (II) intel(0): Output DP2 disconnected
[    35.474] (II) intel(0): Using exact sizes for initial modes
[    35.474] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    35.474] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    35.474] (II) intel(0): Kernel page flipping support detected, enabling
[    35.474] (==) intel(0): DPI set to (96, 96)
[    35.474] (II) Loading sub module "fb"
[    35.474] (II) LoadModule: "fb"
[    35.475] (II) Loading /usr/lib/xorg/modules/libfb.so
[    35.725] (II) Module fb: vendor="X.Org Foundation"
[    35.725] 	compiled for 1.10.1, module version = 1.0.0
[    35.725] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    35.725] (II) UnloadModule: "vesa"
[    35.725] (II) Unloading vesa
[    35.725] (II) UnloadModule: "fbdev"
[    35.725] (II) Unloading fbdev
[    35.725] (II) UnloadModule: "fbdevhw"
[    35.725] (II) Unloading fbdevhw
[    35.725] (==) Depth 24 pixmap format is 32 bpp
[    35.725] (==) intel(0): VideoRam: 262144 KB
[    35.725] (II) intel(0): [DRI2] Setup complete
[    35.725] (II) intel(0): [DRI2]   DRI driver: i965
[    35.725] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    35.774] (II) UXA(0): Driver registered support for the following operations:
[    35.774] (II)         solid
[    35.774] (II)         copy
[    35.774] (II)         composite (RENDER acceleration)
[    35.774] (II)         put_image
[    35.774] (II)         get_image
[    35.774] (==) intel(0): Backing store disabled
[    35.774] (==) intel(0): Silken mouse enabled
[    35.774] (II) intel(0): Initializing HW Cursor
[    35.820] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    35.822] (==) intel(0): DPMS enabled
[    35.822] (==) intel(0): Intel XvMC decoder enabled
[    35.822] (II) intel(0): Set up textured video
[    35.822] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    35.822] (II) intel(0): direct rendering: DRI2 Enabled
[    35.822] (==) intel(0): hotplug detection: "enabled"
[    35.823] (--) RandR disabled
[    35.823] (II) Initializing built-in extension Generic Event Extension
[    35.823] (II) Initializing built-in extension SHAPE
[    35.823] (II) Initializing built-in extension MIT-SHM
[    35.823] (II) Initializing built-in extension XInputExtension
[    35.823] (II) Initializing built-in extension XTEST
[    35.823] (II) Initializing built-in extension BIG-REQUESTS
[    35.823] (II) Initializing built-in extension SYNC
[    35.823] (II) Initializing built-in extension XKEYBOARD
[    35.823] (II) Initializing built-in extension XC-MISC
[    35.823] (II) Initializing built-in extension SECURITY
[    35.823] (II) Initializing built-in extension XINERAMA
[    35.823] (II) Initializing built-in extension XFIXES
[    35.823] (II) Initializing built-in extension RENDER
[    35.823] (II) Initializing built-in extension RANDR
[    35.823] (II) Initializing built-in extension COMPOSITE
[    35.823] (II) Initializing built-in extension DAMAGE
[    35.823] (II) Initializing built-in extension GESTURE
[    35.840] (II) AIGLX: Trying DRI driver /usr/lib/dri/i965_dri.so
[    36.210] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    36.210] (II) AIGLX: enabled GLX_INTEL_swap_event
[    36.210] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    36.210] (II) AIGLX: enabled GLX_SGI_make_current_read
[    36.210] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    36.210] (II) AIGLX: Loaded and initialized i965
[    36.210] (II) GLX: Initialized DRI2 GL provider for screen 0
[    36.211] (II) intel(0): Setting screen physical size to 361 x 203
[    36.530] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    36.548] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    36.548] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    36.548] (II) LoadModule: "evdev"
[    36.549] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.745] (II) Module evdev: vendor="X.Org Foundation"
[    36.745] 	compiled for 1.10.0.902, module version = 2.6.0
[    36.745] 	Module class: X.Org XInput Driver
[    36.745] 	ABI class: X.Org XInput driver, version 12.3
[    36.745] (II) Using input driver 'evdev' for 'Power Button'
[    36.745] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.745] (**) Power Button: always reports core events
[    36.745] (**) Power Button: Device: "/dev/input/event2"
[    36.800] (--) Power Button: Found keys
[    36.800] (II) Power Button: Configuring as keyboard
[    36.800] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    36.800] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    36.800] (**) Option "xkb_rules" "evdev"
[    36.801] (**) Option "xkb_model" "pc105"
[    36.801] (**) Option "xkb_layout" "us"
[    36.802] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    36.802] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    36.802] (II) Using input driver 'evdev' for 'Video Bus'
[    36.802] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.802] (**) Video Bus: always reports core events
[    36.802] (**) Video Bus: Device: "/dev/input/event4"
[    36.830] (--) Video Bus: Found keys
[    36.830] (II) Video Bus: Configuring as keyboard
[    36.830] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input4/event4"
[    36.830] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    36.830] (**) Option "xkb_rules" "evdev"
[    36.830] (**) Option "xkb_model" "pc105"
[    36.830] (**) Option "xkb_layout" "us"
[    36.834] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    36.834] (II) No input driver/identifier specified (ignoring)
[    36.835] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[    36.835] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    36.835] (II) Using input driver 'evdev' for 'Sleep Button'
[    36.835] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.835] (**) Sleep Button: always reports core events
[    36.835] (**) Sleep Button: Device: "/dev/input/event0"
[    36.870] (--) Sleep Button: Found keys
[    36.870] (II) Sleep Button: Configuring as keyboard
[    36.870] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[    36.870] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    36.870] (**) Option "xkb_rules" "evdev"
[    36.870] (**) Option "xkb_model" "pc105"
[    36.870] (**) Option "xkb_layout" "us"
[    36.873] (II) config/udev: Adding input device HP Webcam [2 MP Fixed] (/dev/input/event7)
[    36.873] (**) HP Webcam [2 MP Fixed]: Applying InputClass "evdev keyboard catchall"
[    36.873] (II) Using input driver 'evdev' for 'HP Webcam [2 MP Fixed]'
[    36.873] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.873] (**) HP Webcam [2 MP Fixed]: always reports core events
[    36.873] (**) HP Webcam [2 MP Fixed]: Device: "/dev/input/event7"
[    36.950] (--) HP Webcam [2 MP Fixed]: Found keys
[    36.950] (II) HP Webcam [2 MP Fixed]: Configuring as keyboard
[    36.950] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7/event7"
[    36.950] (II) XINPUT: Adding extended input device "HP Webcam [2 MP Fixed]" (type: KEYBOARD)
[    36.950] (**) Option "xkb_rules" "evdev"
[    36.950] (**) Option "xkb_model" "pc105"
[    36.950] (**) Option "xkb_layout" "us"
[    36.951] (II) config/udev: Adding input device HDA Intel Mic at Ext Right Jack (/dev/input/event10)
[    36.951] (II) No input driver/identifier specified (ignoring)
[    36.951] (II) config/udev: Adding input device HDA Intel HP Out at Ext Right Jack (/dev/input/event11)
[    36.951] (II) No input driver/identifier specified (ignoring)
[    36.952] (II) config/udev: Adding input device Genius       NetScroll+Mini Traveler (/dev/input/event5)
[    36.953] (**) Genius       NetScroll+Mini Traveler: Applying InputClass "evdev pointer catchall"
[    36.953] (II) Using input driver 'evdev' for 'Genius       NetScroll+Mini Traveler'
[    36.953] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.953] (**) Genius       NetScroll+Mini Traveler: always reports core events
[    36.953] (**) Genius       NetScroll+Mini Traveler: Device: "/dev/input/event5"
[    36.990] (--) Genius       NetScroll+Mini Traveler: Found 3 mouse buttons
[    36.990] (--) Genius       NetScroll+Mini Traveler: Found scroll wheel(s)
[    36.990] (--) Genius       NetScroll+Mini Traveler: Found relative axes
[    36.990] (--) Genius       NetScroll+Mini Traveler: Found x and y relative axes
[    36.990] (II) Genius       NetScroll+Mini Traveler: Configuring as mouse
[    36.990] (II) Genius       NetScroll+Mini Traveler: Adding scrollwheel support
[    36.990] (**) Genius       NetScroll+Mini Traveler: YAxisMapping: buttons 4 and 5
[    36.990] (**) Genius       NetScroll+Mini Traveler: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    36.991] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input5/event5"
[    36.991] (II) XINPUT: Adding extended input device "Genius       NetScroll+Mini Traveler" (type: MOUSE)
[    36.991] (II) Genius       NetScroll+Mini Traveler: initialized for relative axes.
[    36.991] (**) Genius       NetScroll+Mini Traveler: (accel) keeping acceleration scheme 1
[    36.991] (**) Genius       NetScroll+Mini Traveler: (accel) acceleration profile 0
[    36.991] (**) Genius       NetScroll+Mini Traveler: (accel) acceleration factor: 2.000
[    36.991] (**) Genius       NetScroll+Mini Traveler: (accel) acceleration threshold: 4
[    36.991] (II) config/udev: Adding input device Genius       NetScroll+Mini Traveler (/dev/input/mouse0)
[    36.991] (II) No input driver/identifier specified (ignoring)
[    36.993] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    36.994] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    36.994] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    36.994] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    36.994] (**) AT Translated Set 2 keyboard: always reports core events
[    36.994] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    37.030] (--) AT Translated Set 2 keyboard: Found keys
[    37.030] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    37.030] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    37.030] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    37.030] (**) Option "xkb_rules" "evdev"
[    37.030] (**) Option "xkb_model" "pc105"
[    37.030] (**) Option "xkb_layout" "us"
[    37.030] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    37.030] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    37.031] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    37.031] (II) LoadModule: "synaptics"
[    37.031] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    37.057] (II) Module synaptics: vendor="X.Org Foundation"
[    37.057] 	compiled for 1.10.0.902, module version = 1.3.99
[    37.057] 	Module class: X.Org XInput Driver
[    37.057] 	ABI class: X.Org XInput driver, version 12.3
[    37.057] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    37.057] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    37.057] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    37.057] (**) Option "Device" "/dev/input/event9"
[    37.241] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5590
[    37.242] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4686
[    37.242] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    37.242] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[    37.242] (--) SynPS/2 Synaptics TouchPad: buttons: left right
[    37.242] (--) SynPS/2 Synaptics TouchPad: invalid finger width range.  defaulting to 0 - 16
[    37.371] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    37.372] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    37.441] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input9/event9"
[    37.441] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[    37.442] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    37.442] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    37.442] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    37.442] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    37.442] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    37.442] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    37.442] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    37.552] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[    37.552] (--) SynPS/2 Synaptics TouchPad: touchpad found
[    37.552] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    37.552] (II) No input driver/identifier specified (ignoring)
[    37.552] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event8)
[    37.552] (II) No input driver/identifier specified (ignoring)
[    37.552] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[    37.552] (II) No input driver/identifier specified (ignoring)
[    37.555] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event6)
[    37.555] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    37.555] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    37.555] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    37.555] (**) HP WMI hotkeys: always reports core events
[    37.556] (**) HP WMI hotkeys: Device: "/dev/input/event6"
[    37.592] (--) HP WMI hotkeys: Found keys
[    37.592] (II) HP WMI hotkeys: Configuring as keyboard
[    37.592] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    37.592] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD)
[    37.592] (**) Option "xkb_rules" "evdev"
[    37.592] (**) Option "xkb_model" "pc105"
[    37.592] (**) Option "xkb_layout" "us"
[    42.769] (II) intel(0): EDID vendor "AUO", prod id 4396
[    42.769] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    42.769] (II) intel(0): Printing DDC gathered Modelines:
[    42.769] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    42.799] (II) intel(0): EDID vendor "AUO", prod id 4396
[    42.799] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    42.799] (II) intel(0): Printing DDC gathered Modelines:
[    42.799] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    42.828] (II) intel(0): EDID vendor "AUO", prod id 4396
[    42.828] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    42.828] (II) intel(0): Printing DDC gathered Modelines:
[    42.828] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    42.858] (II) intel(0): EDID vendor "AUO", prod id 4396
[    42.858] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    42.858] (II) intel(0): Printing DDC gathered Modelines:
[    42.858] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    65.471] (II) intel(0): EDID vendor "AUO", prod id 4396
[    65.471] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    65.471] (II) intel(0): Printing DDC gathered Modelines:
[    65.471] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    65.501] (II) intel(0): EDID vendor "AUO", prod id 4396
[    65.501] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    65.501] (II) intel(0): Printing DDC gathered Modelines:
[    65.501] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    65.530] (II) intel(0): EDID vendor "AUO", prod id 4396
[    65.530] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    65.530] (II) intel(0): Printing DDC gathered Modelines:
[    65.530] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    65.579] (II) intel(0): EDID vendor "AUO", prod id 4396
[    65.579] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    65.579] (II) intel(0): Printing DDC gathered Modelines:
[    65.579] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    68.394] (II) intel(0): EDID vendor "AUO", prod id 4396
[    68.394] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    68.394] (II) intel(0): Printing DDC gathered Modelines:
[    68.394] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[    76.350] (II) intel(0): EDID vendor "AUO", prod id 4396
[    76.350] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[    76.350] (II) intel(0): Printing DDC gathered Modelines:
[    76.350] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   100.343] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 5806 < target_msc 5807
[   100.376] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 5808 < target_msc 5809
[   107.054] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 6208 < target_msc 6209
[   107.321] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 6224 < target_msc 6225
[   107.404] (WW) intel(0): I830DRI2FlipEventHandler: Pageflip completion has impossible msc 6229 < target_msc 6230
[   147.713] (II) intel(0): EDID vendor "AUO", prod id 4396
[   147.713] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   147.713] (II) intel(0): Printing DDC gathered Modelines:
[   147.713] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   152.778] (II) intel(0): EDID vendor "AUO", prod id 4396
[   152.778] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   152.778] (II) intel(0): Printing DDC gathered Modelines:
[   152.778] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   153.444] (II) intel(0): EDID vendor "AUO", prod id 4396
[   153.444] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   153.445] (II) intel(0): Printing DDC gathered Modelines:
[   153.445] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   153.996] (II) intel(0): Allocated new frame buffer 3328x1080 stride 13312, tiled
[   306.905] (II) intel(0): EDID vendor "AUO", prod id 4396
[   306.905] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   306.905] (II) intel(0): Printing DDC gathered Modelines:
[   306.905] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   318.859] (II) intel(0): EDID vendor "AUO", prod id 4396
[   318.859] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   318.859] (II) intel(0): Printing DDC gathered Modelines:
[   318.859] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   339.301] (II) intel(0): EDID vendor "AUO", prod id 4396
[   339.301] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   339.301] (II) intel(0): Printing DDC gathered Modelines:
[   339.301] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   339.774] (II) intel(0): EDID vendor "AUO", prod id 4396
[   339.774] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   339.774] (II) intel(0): Printing DDC gathered Modelines:
[   339.774] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   340.553] (II) intel(0): Allocated new frame buffer 3008x1200 stride 12288, tiled
[   371.683] (II) intel(0): EDID vendor "AUO", prod id 4396
[   371.683] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   371.683] (II) intel(0): Printing DDC gathered Modelines:
[   371.683] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   372.482] (II) intel(0): Allocated new frame buffer 3328x1080 stride 13312, tiled
[   434.536] (II) intel(0): EDID vendor "AUO", prod id 4396
[   434.536] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   434.536] (II) intel(0): Printing DDC gathered Modelines:
[   434.536] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   460.364] (II) intel(0): EDID vendor "AUO", prod id 4396
[   460.364] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   460.364] (II) intel(0): Printing DDC gathered Modelines:
[   460.364] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   460.831] (II) intel(0): EDID vendor "AUO", prod id 4396
[   460.831] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   460.831] (II) intel(0): Printing DDC gathered Modelines:
[   460.831] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   461.627] (II) intel(0): Allocated new frame buffer 3072x1050 stride 12288, tiled
[   467.177] (II) intel(0): EDID vendor "AUO", prod id 4396
[   467.177] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   467.177] (II) intel(0): Printing DDC gathered Modelines:
[   467.177] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   467.922] (II) intel(0): Allocated new frame buffer 3328x1080 stride 13312, tiled
[   473.176] (II) intel(0): EDID vendor "AUO", prod id 4396
[   473.176] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   473.176] (II) intel(0): Printing DDC gathered Modelines:
[   473.176] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   474.201] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[   487.314] (II) intel(0): EDID vendor "AUO", prod id 4396
[   487.314] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   487.314] (II) intel(0): Printing DDC gathered Modelines:
[   487.314] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   487.779] (II) intel(0): EDID vendor "AUO", prod id 4396
[   487.779] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   487.779] (II) intel(0): Printing DDC gathered Modelines:
[   487.779] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   488.322] (II) intel(0): Allocated new frame buffer 2944x1080 stride 11776, tiled
[   565.629] (II) intel(0): EDID vendor "AUO", prod id 4396
[   565.630] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   565.630] (II) intel(0): Printing DDC gathered Modelines:
[   565.630] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   566.371] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[   569.998] (II) intel(0): EDID vendor "AUO", prod id 4396
[   569.998] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   569.998] (II) intel(0): Printing DDC gathered Modelines:
[   569.998] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   575.063] (II) intel(0): EDID vendor "AUO", prod id 4396
[   575.063] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   575.063] (II) intel(0): Printing DDC gathered Modelines:
[   575.063] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   575.531] (II) intel(0): EDID vendor "AUO", prod id 4396
[   575.531] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   575.531] (II) intel(0): Printing DDC gathered Modelines:
[   575.531] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   580.987] (II) intel(0): EDID vendor "AUO", prod id 4396
[   580.987] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   580.987] (II) intel(0): Printing DDC gathered Modelines:
[   580.987] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   581.450] (II) intel(0): EDID vendor "AUO", prod id 4396
[   581.450] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   581.450] (II) intel(0): Printing DDC gathered Modelines:
[   581.451] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   581.977] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[   617.171] (II) intel(0): EDID vendor "AUO", prod id 4396
[   617.171] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   617.171] (II) intel(0): Printing DDC gathered Modelines:
[   617.171] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   625.022] (II) intel(0): EDID vendor "AUO", prod id 4396
[   625.022] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   625.022] (II) intel(0): Printing DDC gathered Modelines:
[   625.022] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   625.480] (II) intel(0): EDID vendor "AUO", prod id 4396
[   625.480] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   625.480] (II) intel(0): Printing DDC gathered Modelines:
[   625.480] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   626.023] (II) intel(0): Allocated new frame buffer 3328x1080 stride 13312, tiled
[   634.880] (II) intel(0): EDID vendor "AUO", prod id 4396
[   634.880] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   634.880] (II) intel(0): Printing DDC gathered Modelines:
[   634.880] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   635.647] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[   760.259] (II) intel(0): EDID vendor "AUO", prod id 4396
[   760.259] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   760.259] (II) intel(0): Printing DDC gathered Modelines:
[   760.259] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   975.986] (II) intel(0): EDID vendor "AUO", prod id 4396
[   975.986] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   975.986] (II) intel(0): Printing DDC gathered Modelines:
[   975.986] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   976.530] (II) intel(0): EDID vendor "AUO", prod id 4396
[   976.530] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   976.530] (II) intel(0): Printing DDC gathered Modelines:
[   976.530] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   976.985] (II) intel(0): EDID vendor "AUO", prod id 4396
[   976.985] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   976.985] (II) intel(0): Printing DDC gathered Modelines:
[   976.985] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   982.694] (II) intel(0): EDID vendor "AUO", prod id 4396
[   982.694] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   982.694] (II) intel(0): Printing DDC gathered Modelines:
[   982.694] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   983.159] (II) intel(0): EDID vendor "AUO", prod id 4396
[   983.159] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   983.159] (II) intel(0): Printing DDC gathered Modelines:
[   983.159] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   983.697] (II) intel(0): Allocated new frame buffer 3072x1050 stride 12288, tiled
[   993.361] (II) intel(0): EDID vendor "AUO", prod id 4396
[   993.361] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[   993.361] (II) intel(0): Printing DDC gathered Modelines:
[   993.361] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[   994.094] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[  1092.460] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1092.460] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1092.460] (II) intel(0): Printing DDC gathered Modelines:
[  1092.460] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1092.503] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1092.503] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1092.503] (II) intel(0): Printing DDC gathered Modelines:
[  1092.503] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1094.302] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1094.302] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1094.302] (II) intel(0): Printing DDC gathered Modelines:
[  1094.302] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1094.973] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1094.973] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1094.973] (II) intel(0): Printing DDC gathered Modelines:
[  1094.973] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1099.184] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1099.184] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1099.184] (II) intel(0): Printing DDC gathered Modelines:
[  1099.184] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1102.615] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1102.615] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1102.615] (II) intel(0): Printing DDC gathered Modelines:
[  1102.615] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1103.092] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1103.092] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1103.092] (II) intel(0): Printing DDC gathered Modelines:
[  1103.092] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1103.642] (II) intel(0): Allocated new frame buffer 3328x1080 stride 13312, tiled
[  1123.838] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1123.839] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1123.839] (II) intel(0): Printing DDC gathered Modelines:
[  1123.839] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1124.676] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[  1277.771] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1277.771] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1277.771] (II) intel(0): Printing DDC gathered Modelines:
[  1277.771] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1278.228] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1278.229] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1278.229] (II) intel(0): Printing DDC gathered Modelines:
[  1278.229] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1278.785] (II) intel(0): Allocated new frame buffer 3328x1080 stride 13312, tiled
[  1302.468] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1302.468] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1302.468] (II) intel(0): Printing DDC gathered Modelines:
[  1302.468] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1303.231] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[  1309.840] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1309.840] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1309.840] (II) intel(0): Printing DDC gathered Modelines:
[  1309.840] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1310.297] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1310.297] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1310.297] (II) intel(0): Printing DDC gathered Modelines:
[  1310.297] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1310.812] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[  1315.901] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1315.901] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1315.901] (II) intel(0): Printing DDC gathered Modelines:
[  1315.901] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1316.368] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1316.368] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1316.368] (II) intel(0): Printing DDC gathered Modelines:
[  1316.368] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1316.909] (II) intel(0): Allocated new frame buffer 3328x1080 stride 13312, tiled
[  1319.790] (II) intel(0): EDID vendor "AUO", prod id 4396
[  1319.790] (II) intel(0): DDCModeFromDetailedTiming: Ignoring: We don't handle stereo.
[  1319.790] (II) intel(0): Printing DDC gathered Modelines:
[  1319.790] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1456  768 771 777 793 -hsync -vsync (47.6 kHz)
[  1320.574] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled

---

