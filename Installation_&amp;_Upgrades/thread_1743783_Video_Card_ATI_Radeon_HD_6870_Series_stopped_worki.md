---
title: "Video Card: ATI Radeon HD 6870 Series stopped working after Natty upgrade x86_64"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Mack-Limelight on 2011-04-29
I previously got my card to work via the ccchtml wiki for Maverick, During the Natty upgrade it prompted to remove 3rd party apps, and various video card drivers (I figured there was driver changes or updates). Once the upgrade was successful and reboot. The system boot stopped at the splash screen.

I tried purge and re-installing drivers and the ATI driver package,. However keep getting errors when trying to startx, and fglrxinfo always reports back /dev/null


[  2235.034] (EE) Failed to load module "fgl.renamed.libglx" (module does not exist, 0)
[  2235.088] (EE) Can't load FireGL DRM library (libfglrxdrm.so).
[  2235.368] (EE) fglrx: Failed to load module "fglrxdrm" (module does not exist, 0)
[  2235.368] (EE) fglrx(0): Failed to load DRM library
[  2235.368] (EE) fglrx(0): PreInit failed
[  2235.370] (EE) Screen(s) found, but none have a usable configuration.



```
[  2234.408] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[  2234.493] X Protocol Version 11, Revision 0
[  2234.522] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[  2234.551] Current Operating System: Linux lethal-gimmick 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64
[  2234.583] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=6190c2d1-dbe3-439d-99dd-9c5fdfbd10d8 ro quiet splash vt.handoff=7
[  2234.616] Build Date: 19 April 2011  03:40:45PM
[  2234.650] xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
[  2234.686] Current version of pixman: 0.20.2
[  2234.722] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[  2234.795] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  2234.911] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Apr 29 19:49:34 2011
[  2234.951] (==) Using config file: "/etc/X11/xorg.conf"
[  2234.991] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  2235.032] (==) ServerLayout "X.org Configured"
[  2235.032] (**) |-->Screen "Screen0" (0)
[  2235.032] (**) |   |-->Monitor "<default monitor>"
[  2235.032] (**) |   |-->Device "ATI Radeon 6870"
[  2235.032] (==) No monitor specified for screen "Screen0".
	Using a default monitor configuration.
[  2235.032] (**) |-->Input Device "Mouse0"
[  2235.032] (**) |-->Input Device "Keyboard0"
[  2235.032] (==) Automatically adding devices
[  2235.032] (==) Automatically enabling devices
[  2235.033] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2235.033] 	Entry deleted from font path.
[  2235.033] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  2235.033] 	Entry deleted from font path.
[  2235.033] (**) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins,
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  2235.033] (**) ModulePath set to "/usr/lib/X11/modules,/usr/lib/xorg/modules"
[  2235.033] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[  2235.033] (WW) Disabling Mouse0
[  2235.033] (WW) Disabling Keyboard0
[  2235.033] (II) Loader magic: 0x7e0280
[  2235.033] (II) Module ABI versions:
[  2235.033] 	X.Org ANSI C Emulation: 0.4
[  2235.033] 	X.Org Video Driver: 10.0
[  2235.033] 	X.Org XInput driver : 12.3
[  2235.033] 	X.Org Server Extension : 5.0
[  2235.034] (--) PCI:*(0:3:0:0) 1002:6738:1002:00d0 rev 0, Mem @ 0xd0000000/268435456, 0xfbcc0000/131072, I/O @ 0x0000c000/256, BIOS @ 0x????????/131072
[  2235.034] (II) Open ACPI successful (/var/run/acpid.socket)
[  2235.034] (II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
[  2235.034] (II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
[  2235.034] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[  2235.034] (II) "record" will be loaded. This was enabled by default and also specified in the config file.
[  2235.034] (II) "dri" will be loaded. This was enabled by default and also specified in the config file.
[  2235.034] (II) "dri2" will be loaded. This was enabled by default and also specified in the config file.
[  2235.034] (II) LoadModule: "fgl.renamed.libglx"
[  2235.034] (WW) Warning, couldn't open module fgl.renamed.libglx
[  2235.034] (II) UnloadModule: "fgl.renamed.libglx"
[  2235.034] (II) Unloading fgl.renamed.libglx
[  2235.034] (EE) Failed to load module "fgl.renamed.libglx" (module does not exist, 0)
[  2235.076] (II) LoadModule: "extmod"
[  2235.076] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  2235.076] (II) Module extmod: vendor="X.Org Foundation"
[  2235.076] 	compiled for 1.10.1, module version = 1.0.0
[  2235.076] 	Module class: X.Org Server Extension
[  2235.076] 	ABI class: X.Org Server Extension, version 5.0
[  2235.076] (II) Loading extension MIT-SCREEN-SAVER
[  2235.076] (II) Loading extension XFree86-VidModeExtension
[  2235.076] (II) Loading extension XFree86-DGA
[  2235.076] (II) Loading extension DPMS
[  2235.076] (II) Loading extension XVideo
[  2235.076] (II) Loading extension XVideo-MotionCompensation
[  2235.076] (II) Loading extension X-Resource
[  2235.076] (II) LoadModule: "record"
[  2235.076] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  2235.076] (II) Module record: vendor="X.Org Foundation"
[  2235.076] 	compiled for 1.10.1, module version = 1.13.0
[  2235.076] 	Module class: X.Org Server Extension
[  2235.076] 	ABI class: X.Org Server Extension, version 5.0
[  2235.076] (II) Loading extension RECORD
[  2235.076] (II) LoadModule: "glx"
[  2235.077] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  2235.077] (II) Module glx: vendor="X.Org Foundation"
[  2235.077] 	compiled for 1.10.1, module version = 1.0.0
[  2235.077] 	ABI class: X.Org Server Extension, version 5.0
[  2235.077] (==) AIGLX enabled
[  2235.077] (II) Loading extension GLX
[  2235.077] (II) LoadModule: "dri"
[  2235.077] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  2235.077] (II) Module dri: vendor="X.Org Foundation"
[  2235.077] 	compiled for 1.10.1, module version = 1.0.0
[  2235.077] 	ABI class: X.Org Server Extension, version 5.0
[  2235.077] (II) Loading extension XFree86-DRI
[  2235.077] (II) LoadModule: "dbe"
[  2235.077] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  2235.077] (II) Module dbe: vendor="X.Org Foundation"
[  2235.077] 	compiled for 1.10.1, module version = 1.0.0
[  2235.077] 	Module class: X.Org Server Extension
[  2235.077] 	ABI class: X.Org Server Extension, version 5.0
[  2235.077] (II) Loading extension DOUBLE-BUFFER
[  2235.077] (II) LoadModule: "dri2"
[  2235.077] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  2235.077] (II) Module dri2: vendor="X.Org Foundation"
[  2235.077] 	compiled for 1.10.1, module version = 1.2.0
[  2235.077] 	ABI class: X.Org Server Extension, version 5.0
[  2235.077] (II) Loading extension DRI2
[  2235.077] (II) LoadModule: "fglrx"
[  2235.077] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[  2235.087] (II) Module fglrx: vendor="FireGL - ATI Technologies Inc."
[  2235.087] 	compiled for 1.4.99.906, module version = 8.84.5
[  2235.087] 	Module class: X.Org Video Driver
[  2235.087] (II) Loading sub module "fglrxdrm"
[  2235.087] (II) LoadModule: "fglrxdrm"
[  2235.088] (WW) Warning, couldn't open module fglrxdrm
[  2235.088] (II) UnloadModule: "fglrxdrm"
[  2235.088] (II) Unloading fglrxdrm
[  2235.088] (EE) Can't load FireGL DRM library (libfglrxdrm.so).
[  2235.130] (II) ATI Proprietary Linux Driver Version Identifier:8.84.5
[  2235.130] (II) ATI Proprietary Linux Driver Release Identifier: 8.841                                
[  2235.130] (II) ATI Proprietary Linux Driver Build Date: Apr  5 2011 21:43:54
[  2235.130] (--) using VT number 8

[  2235.361] (WW) Falling back to old probe method for fglrx
[  2235.365] (II) Loading PCS database from /etc/ati/amdpcsdb
[  2235.366] (--) Chipset Supported AMD Graphics Processor (0x6738) found
[  2235.366] (WW) fglrx: No matching Device section for instance (BusID PCI:0@3:0:1) found
[  2235.366] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[  2235.366] (II) AMD Video driver is signed
[  2235.366] (II) Loading /usr/lib/xorg/modules/drivers/fglrx_drv.so
[  2235.366] (II) fglrx(0): pEnt->device->identifier=0xa51af0
[  2235.366] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === begin
[  2235.367] (II) Loading sub module "vgahw"
[  2235.367] (II) LoadModule: "vgahw"
[  2235.367] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[  2235.367] (II) Module vgahw: vendor="X.Org Foundation"
[  2235.367] 	compiled for 1.10.1, module version = 0.1.0
[  2235.367] 	ABI class: X.Org Video Driver, version 10.0
[  2235.367] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[  2235.367] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[  2235.367] (==) fglrx(0): Default visual is TrueColor
[  2235.367] (==) fglrx(0): RGB weight 888
[  2235.367] (II) fglrx(0): Using 8 bits per RGB 
[  2235.367] (==) fglrx(0): Buffer Tiling is ON
[  2235.367] (II) Loading sub module "fglrxdrm"
[  2235.367] (II) LoadModule: "fglrxdrm"
[  2235.368] (WW) Warning, couldn't open module fglrxdrm
[  2235.368] (II) UnloadModule: "fglrxdrm"
[  2235.368] (II) Unloading fglrxdrm
[  2235.368] (EE) fglrx: Failed to load module "fglrxdrm" (module does not exist, 0)
[  2235.368] (EE) fglrx(0): Failed to load DRM library
[  2235.368] (EE) fglrx(0): PreInit failed
[  2235.368] (II) fglrx(0): === [xdl_xs110_atiddxPreInit] === end
[  2235.369] SetVBEMode failed
[  2235.370] (II) UnloadModule: "fglrx"
[  2235.370] (II) Unloading fglrx
[  2235.370] (II) UnloadModule: "vgahw"
[  2235.370] (II) Unloading vgahw
[  2235.370] (EE) Screen(s) found, but none have a usable configuration.
[  2235.370] 
Fatal server error:
[  2235.370] no screens found
[  2235.370] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[  2235.370] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  2235.370] 
[  2235.885]  ddxSigGiveUp: Closing log

```


My /etc/X11/xorg.conf file:

```

Section "ServerLayout"
 Identifier "X.org Configured"
 Screen 0 "Screen0" 0 0
 InputDevice "Mouse0" "CorePointer"
 InputDevice "Keyboard0" "CoreKeyboard"
 EndSection

Section "Files"
 ModulePath "/usr/lib/X11/modules"
 ModulePath "/usr/lib/xorg/modules"
 FontPath "/usr/share/fonts/X11/misc"
 FontPath "/usr/share/fonts/X11/cyrillic"
 FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
 FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
 FontPath "/usr/share/fonts/X11/Type1"
 FontPath "/usr/share/fonts/X11/100dpi"
 FontPath "/usr/share/fonts/X11/75dpi"
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 FontPath "built-ins"
 EndSection

Section "Module"
 Load "FGL.renamed.libglx"
 Load "extmod"
 Load "record"
 Load "glx"
 Load "dri"
 Load "dbe"
 Load "dri2"
 EndSection

Section "InputDevice"
 Identifier "Keyboard0"
 Driver "kbd"
 EndSection

Section "InputDevice"
 Identifier "Mouse0"
 Driver "mouse"
 Option "Protocol" "auto"
 Option "Device" "/dev/input/mice"
 Option "ZAxisMapping" "4 5 6 7"
 EndSection

Section "Monitor"
 Identifier "Monitor0"
 VendorName "Dell"
 ModelName "2007FP"
 EndSection

Section "Monitor"
 Identifier "Monitor1"
 VendorName "Dell"
 ModelName "2007FP"
 EndSection

Section "Monitor"
 Identifier "0-DFP5"
 Option "VendorName" "ATI Proprietary Driver"
 Option "ModelName" "Generic Autodetecting Monitor"
 Option "DPMS" "true"
 Option "PreferredMode" "1600x1200"
 Option "TargetRefresh" "60"
 Option "Position" "1600 0"
 Option "Rotate" "normal"
 Option "Disable" "false"
 EndSection

Section "Monitor"
 Identifier "0-DFP4"
 Option "VendorName" "ATI Proprietary Driver"
 Option "ModelName" "Generic Autodetecting Monitor"
 Option "DPMS" "true"
 Option "PreferredMode" "1600x1200"
 Option "TargetRefresh" "60"
 Option "Position" "0 0"
 Option "Rotate" "normal"
 Option "Disable" "false"
 EndSection

Section "Device"

 ### Available Driver options are:-
 ### Values: : integer, : float, : "True"/"False",
 ### : "String", : " Hz/kHz/MHz",
 ### : "%"
 ### [arg]: arg optional
 #Option "ShadowFB" # []
 #Option "Rotate" #
 #Option "fbdev" #
 #Option "debug" # []
 Identifier "ATI Radeon 6870"
 Driver "fglrx"
 Option "Monitor-DFP5" "0-DFP5"
 Option "Monitor-DFP4" "0-DFP4"
 BusID "PCI:3:0:0"
 EndSection

Section "Device"
 Identifier "amdcccle-Device[3]-1"
 Driver "fglrx"
 Option "Monitor-DFP5" "0-DFP5"
 BusID "PCI:3:0:0"
 Screen 1
 EndSection

Section "Screen"
 Identifier "Screen0"
 Device "ATI Radeon 6870"
 SubSection "Display"
 Viewport 0 0
 Virtual 3200 3200
 Depth 1
 EndSubSection
 SubSection "Display"
 Viewport 0 0
 Virtual 3200 3200
 Depth 4
 EndSubSection
 SubSection "Display"
 Viewport 0 0
 Virtual 3200 3200
 Depth 8
 EndSubSection
 SubSection "Display"
 Viewport 0 0
 Virtual 3200 3200
 Depth 15
 EndSubSection
 SubSection "Display"
 Viewport 0 0
 Virtual 3200 3200
 Depth 16
 EndSubSection
 SubSection "Display"
 Viewport 0 0
 Virtual 3200 3200
 Depth 24
 EndSubSection
 EndSection

Section "Screen"
 Identifier "amdcccle-Screen[3]-1"
 Device "amdcccle-Device[3]-1"
 DefaultDepth 24
 SubSection "Display"
 Viewport 0 0
 Depth 24
 EndSubSection
 EndSection

```

---

### Post by Mack-Limelight on 2011-05-01
Tried researching all last night and kept hitting dead ends. About to start backing up everything and try fresh install of Natty. If that doesn't work moving on to another distribution probably GhostBSD.

---

### Post by watermelons on 2012-01-04
Also having this problem. Bump!

---

### Post by MAFoElffen on 2012-01-04
> **watermelons said:**
> Also having this problem. Bump!
Have you tried reinstalling your driver?

Are yours packaged fglrx or the catalyst binary?

---

