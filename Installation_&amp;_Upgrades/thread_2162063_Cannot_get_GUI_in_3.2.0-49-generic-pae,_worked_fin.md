---
title: "Cannot get GUI in 3.2.0-49-generic-pae, worked fine with 3.2.0-48-generic-pae"
date: 2013-07-12
forum: Installation &amp; Upgrades
---

### Post by Psil0cybin on 2013-07-12
Hey guys I recently turned on my Acer Aspire One computer with Xubuntu 12.04 installed using Ubuntu 12.04 to get the Xubuntu-Desktop.
Everything has been working perfectly fine, until I did the recent updates (Has worked fine for quite sometime, the last couple of months my computer worked perfectly). Now when I use 3.2.0-49-generic-pae, Sometimes I get taken into a terminal concol without a desktop manager (GUI), other times I get a blackscreen, and sometimes it actually works and I can see the login screen and use the GUI, thus it seems like its unstable, I cannot figure out and diagnose the problem I have tried looking in the Xorg.0 file. When I got into Xubuntu for the first time after attempting 3 restarts, I was given a crash report and I reported the bug as this [https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1200808](https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1200808). I am wondering if maybe that is another problem Or Could that be THE problem? 

and I get the following results.
[http://pastebin.com/6TpBPqTG](http://pastebin.com/6TpBPqTG)

```
[    29.889] X.Org X Server 1.11.3
Release Date: 2011-12-16
[    29.889] X Protocol Version 11, Revision 0
[    29.889] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    29.889] Current Operating System: Linux stashb0x 3.2.0-49-generic-pae #75-Ubuntu SMP Tue Jun 18 18:00:21 UTC 2013 i686
[    29.889] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-49-generic-pae root=UUID=331d6d2c-2d1d-48e1-ad62-4e14993a393c ro quiet splash
[    29.889] Build Date: 11 April 2013  01:04:30PM
[    29.889] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[    29.889] Current version of pixman: 0.24.4
[    29.890]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.890] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.890] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 12 23:39:18 2013
[    29.891] (==) Using config file: "/etc/X11/xorg.conf"
[    29.891] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.892] (==) ServerLayout "default screen"
[    29.892] (==) No screen section available. Using defaults.
[    29.892] (**) |-->Screen "Default Screen Section" (0)
[    29.892] (**) |   |-->Monitor "<default monitor>"
[    29.893] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    29.893] (**) |   |-->Device "Card0"
[    29.893] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.894] (**) Option "AIGLX" "Off"
[    29.894] (==) Automatically adding devices
[    29.894] (==) Automatically enabling devices
[    29.894] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.894]     Entry deleted from font path.
[    29.894] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.894]     Entry deleted from font path.
[    29.894] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.894]     Entry deleted from font path.
[    29.894] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.894]     Entry deleted from font path.
[    29.894] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.895]     Entry deleted from font path.
[    29.895] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    29.895]     Entry deleted from font path.
[    29.895] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.895] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.895] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.895] (II) Loader magic: 0xb778c5a0
[    29.895] (II) Module ABI versions:
[    29.895]     X.Org ANSI C Emulation: 0.4
[    29.895]     X.Org Video Driver: 11.0
[    29.895]     X.Org XInput driver : 16.0
[    29.895]     X.Org Server Extension : 6.0
[    29.897] (--) PCI:*(0:0:2:0) 8086:0be1:1025:061f rev 9, Mem @ 0x46000000/1048576, I/O @ 0x000050d0/8
[    29.898] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.898] (II) "extmod" will be loaded by default.
[    29.898] (II) "dbe" will be loaded by default.
[    29.898] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    29.898] (II) "record" will be loaded by default.
[    29.898] (II) "dri" will be loaded by default.
[    29.898] (II) "dri2" will be loaded by default.
[    29.898] (II) LoadModule: "glx"
[    29.926] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.926] (II) Module glx: vendor="X.Org Foundation"
[    29.926]     compiled for 1.11.3, module version = 1.0.0
[    29.926]     ABI class: X.Org Server Extension, version 6.0
[    29.926] (**) AIGLX disabled
[    29.926] (II) Loading extension GLX
[    29.926] (II) LoadModule: "extmod"
[    29.927] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.927] (II) Module extmod: vendor="X.Org Foundation"
[    29.927]     compiled for 1.11.3, module version = 1.0.0
[    29.928]     Module class: X.Org Server Extension
[    29.928]     ABI class: X.Org Server Extension, version 6.0
[    29.928] (II) Loading extension MIT-SCREEN-SAVER
[    29.928] (II) Loading extension XFree86-VidModeExtension
[    29.928] (II) Loading extension XFree86-DGA
[    29.928] (II) Loading extension DPMS
[    29.928] (II) Loading extension XVideo
[    29.928] (II) Loading extension XVideo-MotionCompensation
[    29.928] (II) Loading extension X-Resource
[    29.928] (II) LoadModule: "dbe"
[    29.929] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.929] (II) Module dbe: vendor="X.Org Foundation"
[    29.929]     compiled for 1.11.3, module version = 1.0.0
[    29.929]     Module class: X.Org Server Extension
[    29.929]     ABI class: X.Org Server Extension, version 6.0
[    29.929] (II) Loading extension DOUBLE-BUFFER
[    29.929] (II) LoadModule: "record"
[    29.930] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.930] (II) Module record: vendor="X.Org Foundation"
[    29.930]     compiled for 1.11.3, module version = 1.13.0
[    29.930]     Module class: X.Org Server Extension
[    29.930]     ABI class: X.Org Server Extension, version 6.0
[    29.930] (II) Loading extension RECORD
[    29.930] (II) LoadModule: "dri"
[    29.931] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.932] (II) Module dri: vendor="X.Org Foundation"
[    29.932]     compiled for 1.11.3, module version = 1.0.0
[    29.932]     ABI class: X.Org Server Extension, version 6.0
[    29.932] (II) Loading extension XFree86-DRI
[    29.932] (II) LoadModule: "dri2"
[    29.933] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.933] (II) Module dri2: vendor="X.Org Foundation"
[    29.933]     compiled for 1.11.3, module version = 1.2.0
[    29.933]     ABI class: X.Org Server Extension, version 6.0
[    29.933] (II) Loading extension DRI2
[    29.933] (II) LoadModule: "pvr"
[    29.934] (II) Loading /usr/lib/xorg/modules/drivers/pvr_drv.so
[    29.935] (II) Module PVR: vendor="X.Org Foundation"
[    29.935]     compiled for 1.11.3, module version = 1.7.10922
[    29.935]     Module class: X.Org Video Driver
[    29.935]     ABI class: X.Org Video Driver, version 11.0
[    29.935] (II) pvr: Driver for PowerVR chipsets: PowerVR SGX
[    29.935] (++) using VT number 7


[    29.936] drmOpenDevice: node name is /dev/dri/card0
[    29.936] drmOpenDevice: open result is 8, (OK)
[    29.936] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.936] drmOpenDevice: node name is /dev/dri/card0
[    29.936] drmOpenDevice: open result is 8, (OK)
[    29.937] drmOpenByBusid: drmOpenMinor returns 8
[    29.937] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.937] drmOpenDevice: node name is /dev/dri/card0
[    29.938] drmOpenDevice: open result is 8, (OK)
[    29.938] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.938] drmOpenDevice: node name is /dev/dri/card0
[    29.938] drmOpenDevice: open result is 8, (OK)
[    29.938] drmOpenByBusid: drmOpenMinor returns 8
[    29.938] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.941] drmOpenDevice: node name is /dev/dri/card0
[    29.941] drmOpenDevice: open result is 8, (OK)
[    29.941] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.941] drmOpenDevice: node name is /dev/dri/card0
[    29.941] drmOpenDevice: open result is 8, (OK)
[    29.941] drmOpenByBusid: drmOpenMinor returns 8
[    29.941] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.941] (II) Loading /usr/lib/xorg/modules/drivers/pvr_drv.so
[    29.942] drmOpenDevice: node name is /dev/dri/card0
[    29.942] drmOpenDevice: open result is 9, (OK)
[    29.942] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.942] drmOpenDevice: node name is /dev/dri/card0
[    29.943] drmOpenDevice: open result is 9, (OK)
[    29.943] drmOpenByBusid: drmOpenMinor returns 9
[    29.943] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.943] drmOpenDevice: node name is /dev/dri/card0
[    29.943] drmOpenDevice: open result is 10, (OK)
[    29.943] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.943] drmOpenDevice: node name is /dev/dri/card0
[    29.943] drmOpenDevice: open result is 10, (OK)
[    29.943] drmOpenByBusid: drmOpenMinor returns 10
[    29.943] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    29.943] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.947] drmOpenDevice: node name is /dev/dri/card0
[    29.948] drmOpenDevice: open result is 11, (OK)
[    29.948] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.948] drmOpenDevice: node name is /dev/dri/card0
[    29.948] drmOpenDevice: open result is 11, (OK)
[    29.948] drmOpenByBusid: drmOpenMinor returns 11
[    29.948] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    29.948] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.948] drmOpenDevice: node name is /dev/dri/card0
[    29.949] drmOpenDevice: open result is 11, (OK)
[    29.949] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.949] drmOpenDevice: node name is /dev/dri/card0
[    29.949] drmOpenDevice: open result is 11, (OK)
[    29.949] drmOpenByBusid: drmOpenMinor returns 11
[    29.949] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    29.949] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    30.029] drmOpenDevice: node name is /dev/dri/card0
[    30.029] drmOpenDevice: open result is 11, (OK)
[    30.029] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    30.029] drmOpenDevice: node name is /dev/dri/card0
[    30.030] drmOpenDevice: open result is 11, (OK)
[    30.030] drmOpenByBusid: drmOpenMinor returns 11
[    30.030] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    30.030] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    30.113] (II) pvr(0): source head @cdv-v1.0.2
[    30.113] (II) pvr(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.113] (==) pvr(0): Depth 24, (==) framebuffer bpp 32
[    30.113] (==) pvr(0): RGB weight 888
[    30.113] (==) pvr(0): Default visual is TrueColor
[    30.113] (**) pvr(0): Option "FlipChain" "On"
[    30.113] (**) pvr(0): Option "SoftEXA" "Off"
[    30.113] (**) pvr(0): Option "DRIDisableVSync" "False"
[    30.113] (II) pvr(0): Flipchain enabled
[    30.180] (II) pvr(0): Output VGA1 has no monitor section
[    30.286] (II) pvr(0): Output LVDS1 has no monitor section
[    30.287] (II) pvr(0): found backlight control interface /sys/class/backlight/acpi_video0
[    30.332] (II) pvr(0): Output DVI1 has no monitor section
[    30.333] (II) pvr(0): Output DP1 has no monitor section
[    30.396] (II) pvr(0): EDID for output VGA1
[    30.502] (II) pvr(0): EDID for output LVDS1
[    30.503] (II) pvr(0): Manufacturer: AUO  Model: 61d2  Serial#: 0
[    30.503] (II) pvr(0): Year: 2009  Week: 0
[    30.503] (II) pvr(0): EDID Version: 1.3
[    30.503] (II) pvr(0): Digital Display Input
[    30.503] (II) pvr(0): Max Image Size [cm]: horiz.: 22  vert.: 13
[    30.503] (II) pvr(0): Gamma: 2.20
[    30.503] (II) pvr(0): No DPMS capabilities specified
[    30.503] (II) pvr(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    30.503] (II) pvr(0): First detailed timing is preferred mode
[    30.503] (II) pvr(0): redX: 0.590 redY: 0.345   greenX: 0.325 greenY: 0.540
[    30.503] (II) pvr(0): blueX: 0.150 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    30.503] (II) pvr(0): Manufacturer's mask: 0
[    30.503] (II) pvr(0): Supported detailed timing:
[    30.503] (II) pvr(0): clock: 49.8 MHz   Image Size:  222 x 125 mm
[    30.503] (II) pvr(0): h_active: 1024  h_sync: 1072  h_sync_end 1104 h_blank_end 1338 h_border: 0
[    30.503] (II) pvr(0): v_active: 600  v_sync: 602  v_sync_end 608 v_blanking: 620 v_border: 0
[    30.503] (II) pvr(0): Unknown vendor-specific block f
[    30.503] (II) pvr(0):  AUO
[    30.503] (II) pvr(0):  B101AW06 V1
[    30.503] (II) pvr(0): EDID (in hex):
[    30.503] (II) pvr(0):     00ffffffffffff0006afd26100000000
[    30.503] (II) pvr(0):     0013010380160d780a15859758538a26
[    30.503] (II) pvr(0):     25505400000001010101010101010101
[    30.503] (II) pvr(0):     0101010101017413003a415814203020
[    30.503] (II) pvr(0):     2600de7d000000180000000f00000000
[    30.503] (II) pvr(0):     00000000000000000020000000fe0041
[    30.503] (II) pvr(0):     554f0a202020202020202020000000fe
[    30.504] (II) pvr(0):     004231303141573036205631200a0029
[    30.504] (II) pvr(0): Not using default mode "320x240" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "400x300" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "400x300" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "512x384" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "640x480" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "640x512" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "800x600" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "576x432" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "680x384" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "680x384" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "700x525" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "720x450" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "800x512" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "840x525" (doublescan mode not supported)
[    30.505] (II) pvr(0): Not using default mode "840x525" (doublescan mode not supported)
[    30.505] (II) pvr(0): Not using default mode "960x540" (doublescan mode not supported)
[    30.505] (II) pvr(0): Not using default mode "960x600" (doublescan mode not supported)
[    30.505] (II) pvr(0): Printing probed modes for output LVDS1
[    30.505] (II) pvr(0): Modeline "1024x600"x60.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    30.505] (II) pvr(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    30.505] (II) pvr(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    30.505] (II) pvr(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    30.550] (II) pvr(0): EDID for output DVI1
[    30.551] (II) pvr(0): EDID for output DP1
[    30.551] (II) pvr(0): Output VGA1 disconnected
[    30.551] (II) pvr(0): Output LVDS1 connected
[    30.551] (II) pvr(0): Output DVI1 disconnected
[    30.551] (II) pvr(0): Output DP1 disconnected
[    30.551] (II) pvr(0): Using exact sizes for initial modes
[    30.551] (II) pvr(0): Output LVDS1 using initial mode 1024x600
[    30.551] (II) pvr(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    30.551] (--) pvr(0): Virtual size is 1024x600 (pitch 1024)
[    30.551] (**) pvr(0):  Driver mode "1024x600": 49.8 MHz (scaled from 0.0 MHz), 37.2 kHz, 60.0 Hz
[    30.551] (II) pvr(0): Modeline "1024x600"x60.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    30.551] (**) pvr(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    30.551] (II) pvr(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    30.551] (**) pvr(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    30.551] (II) pvr(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    30.551] (**) pvr(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    30.551] (II) pvr(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    30.551] (==) pvr(0): DPI set to (96, 96)
[    30.551] (II) Loading sub module "fb"
[    30.551] (II) LoadModule: "fb"
[    30.552] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.552] (II) Module fb: vendor="X.Org Foundation"
[    30.552]     compiled for 1.11.3, module version = 1.0.0
[    30.552]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.552] (II) pvr(0): [pvr] Software copy threshold : 0B
[    30.552] (II) pvr(0): [pvr] Software solid threshold : 0B
[    30.552] (II) pvr(0): [pvr] Software composite threshold : 0B
[    30.552] (II) pvr(0): [pvr] Pixmap pool size: 0B
[    30.552] (II) Loading sub module "exa"
[    30.552] (II) LoadModule: "exa"
[    30.553] (II) Loading /usr/lib/xorg/modules/libexa.so
[    30.553] (II) Module exa: vendor="X.Org Foundation"
[    30.553]     compiled for 1.11.3, module version = 2.5.0
[    30.553]     ABI class: X.Org Video Driver, version 11.0
[    30.553] PVRPreInit: done
[    30.553] (--) Depth 24 pixmap format is 32 bpp
[    30.553] (II) pvr(0): [DRI2] Setup complete
[    30.554] (II) pvr(0): [DRI2]   DRI driver: pvr
[    30.554] (II) EXA(0): Driver allocated offscreen pixmaps
[    30.554] (II) EXA(0): Driver registered support for the following operations:
[    30.554] (II)         Solid
[    30.554] (II)         Copy
[    30.554] (II)         Composite (RENDER acceleration)
[    30.572] (==) pvr(0): Backing store disabled
[    30.573] (==) pvr(0): Silken mouse enabled
[    30.574] (==) pvr(0): DPMS enabled
[    30.574] (II) pvr(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    30.574] (II) pvr(0): max backlight 9
[    30.574] (II) pvr(0): active backlight 5
[    30.574] (==) pvr(0): Direct rendering enabled
[    30.575] (II) pvr(0): Enable XVideo
[    30.606] (II) pvr(0): [dri] Created flip chain 1
[    30.606] (II) pvr(0): hotplug detection enabled
[    30.606] (--) RandR disabled
[    30.606] (II) Initializing built-in extension Generic Event Extension
[    30.606] (II) Initializing built-in extension SHAPE
[    30.606] (II) Initializing built-in extension MIT-SHM
[    30.606] (II) Initializing built-in extension XInputExtension
[    30.606] (II) Initializing built-in extension XTEST
[    30.606] (II) Initializing built-in extension BIG-REQUESTS
[    30.606] (II) Initializing built-in extension SYNC
[    30.606] (II) Initializing built-in extension XKEYBOARD
[    30.606] (II) Initializing built-in extension XC-MISC
[    30.606] (II) Initializing built-in extension SECURITY
[    30.606] (II) Initializing built-in extension XINERAMA
[    30.606] (II) Initializing built-in extension XFIXES
[    30.606] (II) Initializing built-in extension RENDER
[    30.606] (II) Initializing built-in extension RANDR
[    30.607] (II) Initializing built-in extension COMPOSITE
[    30.607] (II) Initializing built-in extension DAMAGE
[    30.676] (II) AIGLX: Loaded and initialized swrast
[    30.677] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    30.681] (II) pvr(0): Setting screen physical size to 270 x 158
[    30.712] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.720] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    30.720] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.720] (II) LoadModule: "evdev"
[    30.752] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.753] (II) Module evdev: vendor="X.Org Foundation"
[    30.753]     compiled for 1.11.3, module version = 2.7.0
[    30.753]     Module class: X.Org XInput Driver
[    30.753]     ABI class: X.Org XInput driver, version 16.0
[    30.753] (II) Using input driver 'evdev' for 'Power Button'
[    30.753] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.753] (**) Power Button: always reports core events
[    30.753] (**) evdev: Power Button: Device: "/dev/input/event3"
[    30.753] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.754] (--) evdev: Power Button: Found keys
[    30.754] (II) evdev: Power Button: Configuring as keyboard
[    30.754] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    30.754] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.754] (**) Option "xkb_rules" "evdev"
[    30.754] (**) Option "xkb_model" "pc105"
[    30.754] (**) Option "xkb_layout" "us"
[    30.756] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    30.756] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.756] (II) Using input driver 'evdev' for 'Video Bus'
[    30.756] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.756] (**) Video Bus: always reports core events
[    30.756] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    30.756] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.756] (--) evdev: Video Bus: Found keys
[    30.756] (II) evdev: Video Bus: Configuring as keyboard
[    30.756] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event7"
[    30.756] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    30.756] (**) Option "xkb_rules" "evdev"
[    30.756] (**) Option "xkb_model" "pc105"
[    30.756] (**) Option "xkb_layout" "us"
[    30.758] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.758] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.758] (II) Using input driver 'evdev' for 'Power Button'
[    30.758] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.758] (**) Power Button: always reports core events
[    30.758] (**) evdev: Power Button: Device: "/dev/input/event0"
[    30.759] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.759] (--) evdev: Power Button: Found keys
[    30.759] (II) evdev: Power Button: Configuring as keyboard
[    30.759] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    30.759] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    30.759] (**) Option "xkb_rules" "evdev"
[    30.759] (**) Option "xkb_model" "pc105"
[    30.759] (**) Option "xkb_layout" "us"
[    30.761] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    30.761] (II) No input driver specified, ignoring this device.
[    30.761] (II) This device may have been added with another device file.
[    30.761] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    30.762] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    30.762] (II) Using input driver 'evdev' for 'Sleep Button'
[    30.762] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.762] (**) Sleep Button: always reports core events
[    30.762] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    30.762] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    30.762] (--) evdev: Sleep Button: Found keys
[    30.762] (II) evdev: Sleep Button: Configuring as keyboard
[    30.762] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    30.762] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    30.762] (**) Option "xkb_rules" "evdev"
[    30.762] (**) Option "xkb_model" "pc105"
[    30.762] (**) Option "xkb_layout" "us"
[    30.764] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event10)
[    30.764] (II) No input driver specified, ignoring this device.
[    30.764] (II) This device may have been added with another device file.
[    30.765] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event11)
[    30.765] (II) No input driver specified, ignoring this device.
[    30.765] (II) This device may have been added with another device file.
[    30.766] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[    30.766] (II) No input driver specified, ignoring this device.
[    30.766] (II) This device may have been added with another device file.
[    30.767] (II) config/udev: Adding input device WebCam (/dev/input/event5)
[    30.767] (**) WebCam: Applying InputClass "evdev keyboard catchall"
[    30.767] (II) Using input driver 'evdev' for 'WebCam'
[    30.767] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.767] (**) WebCam: always reports core events
[    30.767] (**) evdev: WebCam: Device: "/dev/input/event5"
[    30.767] (--) evdev: WebCam: Vendor 0x402 Product 0x7675
[    30.767] (--) evdev: WebCam: Found keys
[    30.767] (II) evdev: WebCam: Configuring as keyboard
[    30.767] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input5/event5"
[    30.767] (II) XINPUT: Adding extended input device "WebCam" (type: KEYBOARD, id 10)
[    30.767] (**) Option "xkb_rules" "evdev"
[    30.767] (**) Option "xkb_model" "pc105"
[    30.768] (**) Option "xkb_layout" "us"
[    30.769] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    30.769] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.769] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    30.769] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.770] (**) AT Translated Set 2 keyboard: always reports core events
[    30.770] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    30.770] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    30.770] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    30.770] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    30.770] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    30.770] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    30.770] (**) Option "xkb_rules" "evdev"
[    30.770] (**) Option "xkb_model" "pc105"
[    30.770] (**) Option "xkb_layout" "us"
[    30.772] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    30.772] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    30.772] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    30.772] (II) LoadModule: "synaptics"
[    30.773] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.773] (II) Module synaptics: vendor="X.Org Foundation"
[    30.773]     compiled for 1.11.3, module version = 1.6.2
[    30.773]     Module class: X.Org XInput Driver
[    30.773]     ABI class: X.Org XInput driver, version 16.0
[    30.773] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    30.773] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.774] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.774] (**) Option "Device" "/dev/input/event8"
[    30.856] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5612
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4618
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.856] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.896] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input8/event8"
[    30.896] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    30.896] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    30.896] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    30.896] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    30.897] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    30.897] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    30.897] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    30.897] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    30.897] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.898] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    30.898] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.908] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event6)
[    30.908] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    30.908] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    30.908] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.908] (**) Acer WMI hotkeys: always reports core events
[    30.908] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event6"
[    30.908] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    30.908] (--) evdev: Acer WMI hotkeys: Found keys
[    30.909] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    30.909] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    30.909] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 13)
[    30.909] (**) Option "xkb_rules" "evdev"
[    30.909] (**) Option "xkb_model" "pc105"
[    30.909] (**) Option "xkb_layout" "us"
[    32.402] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    32.402] (II) pvr(0): Printing DDC gathered Modelines:
[    32.402] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    33.490] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    33.490] (II) pvr(0): Printing DDC gathered Modelines:
[    33.490] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    45.118] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    45.118] (II) pvr(0): Printing DDC gathered Modelines:
[    45.118] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    45.333] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    45.333] (II) pvr(0): Printing DDC gathered Modelines:
[    45.334] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    47.050] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    47.050] (II) pvr(0): Printing DDC gathered Modelines:
[    47.050] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    47.265] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    47.266] (II) pvr(0): Printing DDC gathered Modelines:
[    47.266] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    51.770] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    51.770] (II) pvr(0): Printing DDC gathered Modelines:
[    51.770] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    52.014] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    52.014] (II) pvr(0): Printing DDC gathered Modelines:
[    52.014] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    52.234] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    52.234] (II) pvr(0): Printing DDC gathered Modelines:
[    52.234] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    92.898] (II) PM Event received: Capability Changed
[    93.924] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    93.924] (II) pvr(0): Printing DDC gathered Modelines:
[    93.924] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[   145.116] (II) pvr(0): EDID vendor "AUO", prod id 25042
[   145.116] (II) pvr(0): Printing DDC gathered Modelines:
[   145.116] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
```

I was wondering if there is something I can diagnose the problem instead of resorting to using 3.2.0-48-generic-pae.
I tried the IRC and the friendly people on there told me I should diagnose the problem as soon as possible instead of resorting to using a previous version of the kernel.

As I am new I require some help, so that I can make my dcomputer stable again and run smoothly without hipcups instead of restarting and hoping for the best and having to shut down and restart till it just randomly works or going back to previous versions of linux.

Thanks inadvance
-Psil0

---

### Post by Psil0cybin on 2013-07-13
Hey guys I recently turned on my Acer Aspire One computer with Xubuntu 12.04 installed using Ubuntu 12.04 to get the Xubuntu-Desktop.
Everything has been working perfectly fine, until I did the recent updates (Has worked fine for quite sometime, the last couple of months my computer worked perfectly). Now when I use 3.2.0-49-generic-pae, Sometimes I get taken into a terminal concol without a desktop manager (GUI), other times I get a blackscreen, and sometimes it actually works and I can see the login screen and use the GUI, thus it seems like its unstable, I cannot figure out and diagnose the problem I have tried looking in the Xorg.0 file. When I got into Xubuntu for the first time after attempting 3 restarts, I was given a crash report and I reported the bug as this [https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1200808](https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1200808). I am wondering if maybe that is another problem Or Could that be THE problem? 

and I get the following results.
[http://pastebin.com/6TpBPqTG](http://pastebin.com/6TpBPqTG)

```
[    29.889] X.Org X Server 1.11.3
Release Date: 2011-12-16
[    29.889] X Protocol Version 11, Revision 0
[    29.889] Build Operating System: Linux 2.6.42-37-generic i686 Ubuntu
[    29.889] Current Operating System: Linux stashb0x 3.2.0-49-generic-pae #75-Ubuntu SMP Tue Jun 18 18:00:21 UTC 2013 i686
[    29.889] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-49-generic-pae root=UUID=331d6d2c-2d1d-48e1-ad62-4e14993a393c ro quiet splash
[    29.889] Build Date: 11 April 2013  01:04:30PM
[    29.889] xorg-server 2:1.11.4-0ubuntu10.13 (For technical support please see http://www.ubuntu.com/support) 
[    29.889] Current version of pixman: 0.24.4
[    29.890]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.890] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.890] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 12 23:39:18 2013
[    29.891] (==) Using config file: "/etc/X11/xorg.conf"
[    29.891] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.892] (==) ServerLayout "default screen"
[    29.892] (==) No screen section available. Using defaults.
[    29.892] (**) |-->Screen "Default Screen Section" (0)
[    29.892] (**) |   |-->Monitor "<default monitor>"
[    29.893] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    29.893] (**) |   |-->Device "Card0"
[    29.893] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.894] (**) Option "AIGLX" "Off"
[    29.894] (==) Automatically adding devices
[    29.894] (==) Automatically enabling devices
[    29.894] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.894]     Entry deleted from font path.
[    29.894] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.894]     Entry deleted from font path.
[    29.894] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.894]     Entry deleted from font path.
[    29.894] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.894]     Entry deleted from font path.
[    29.894] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.895]     Entry deleted from font path.
[    29.895] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    29.895]     Entry deleted from font path.
[    29.895] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.895] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.895] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.895] (II) Loader magic: 0xb778c5a0
[    29.895] (II) Module ABI versions:
[    29.895]     X.Org ANSI C Emulation: 0.4
[    29.895]     X.Org Video Driver: 11.0
[    29.895]     X.Org XInput driver : 16.0
[    29.895]     X.Org Server Extension : 6.0
[    29.897] (--) PCI:*(0:0:2:0) 8086:0be1:1025:061f rev 9, Mem @ 0x46000000/1048576, I/O @ 0x000050d0/8
[    29.898] (II) Open ACPI successful (/var/run/acpid.socket)
[    29.898] (II) "extmod" will be loaded by default.
[    29.898] (II) "dbe" will be loaded by default.
[    29.898] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    29.898] (II) "record" will be loaded by default.
[    29.898] (II) "dri" will be loaded by default.
[    29.898] (II) "dri2" will be loaded by default.
[    29.898] (II) LoadModule: "glx"
[    29.926] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    29.926] (II) Module glx: vendor="X.Org Foundation"
[    29.926]     compiled for 1.11.3, module version = 1.0.0
[    29.926]     ABI class: X.Org Server Extension, version 6.0
[    29.926] (**) AIGLX disabled
[    29.926] (II) Loading extension GLX
[    29.926] (II) LoadModule: "extmod"
[    29.927] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    29.927] (II) Module extmod: vendor="X.Org Foundation"
[    29.927]     compiled for 1.11.3, module version = 1.0.0
[    29.928]     Module class: X.Org Server Extension
[    29.928]     ABI class: X.Org Server Extension, version 6.0
[    29.928] (II) Loading extension MIT-SCREEN-SAVER
[    29.928] (II) Loading extension XFree86-VidModeExtension
[    29.928] (II) Loading extension XFree86-DGA
[    29.928] (II) Loading extension DPMS
[    29.928] (II) Loading extension XVideo
[    29.928] (II) Loading extension XVideo-MotionCompensation
[    29.928] (II) Loading extension X-Resource
[    29.928] (II) LoadModule: "dbe"
[    29.929] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    29.929] (II) Module dbe: vendor="X.Org Foundation"
[    29.929]     compiled for 1.11.3, module version = 1.0.0
[    29.929]     Module class: X.Org Server Extension
[    29.929]     ABI class: X.Org Server Extension, version 6.0
[    29.929] (II) Loading extension DOUBLE-BUFFER
[    29.929] (II) LoadModule: "record"
[    29.930] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    29.930] (II) Module record: vendor="X.Org Foundation"
[    29.930]     compiled for 1.11.3, module version = 1.13.0
[    29.930]     Module class: X.Org Server Extension
[    29.930]     ABI class: X.Org Server Extension, version 6.0
[    29.930] (II) Loading extension RECORD
[    29.930] (II) LoadModule: "dri"
[    29.931] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    29.932] (II) Module dri: vendor="X.Org Foundation"
[    29.932]     compiled for 1.11.3, module version = 1.0.0
[    29.932]     ABI class: X.Org Server Extension, version 6.0
[    29.932] (II) Loading extension XFree86-DRI
[    29.932] (II) LoadModule: "dri2"
[    29.933] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    29.933] (II) Module dri2: vendor="X.Org Foundation"
[    29.933]     compiled for 1.11.3, module version = 1.2.0
[    29.933]     ABI class: X.Org Server Extension, version 6.0
[    29.933] (II) Loading extension DRI2
[    29.933] (II) LoadModule: "pvr"
[    29.934] (II) Loading /usr/lib/xorg/modules/drivers/pvr_drv.so
[    29.935] (II) Module PVR: vendor="X.Org Foundation"
[    29.935]     compiled for 1.11.3, module version = 1.7.10922
[    29.935]     Module class: X.Org Video Driver
[    29.935]     ABI class: X.Org Video Driver, version 11.0
[    29.935] (II) pvr: Driver for PowerVR chipsets: PowerVR SGX
[    29.935] (++) using VT number 7


[    29.936] drmOpenDevice: node name is /dev/dri/card0
[    29.936] drmOpenDevice: open result is 8, (OK)
[    29.936] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.936] drmOpenDevice: node name is /dev/dri/card0
[    29.936] drmOpenDevice: open result is 8, (OK)
[    29.937] drmOpenByBusid: drmOpenMinor returns 8
[    29.937] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.937] drmOpenDevice: node name is /dev/dri/card0
[    29.938] drmOpenDevice: open result is 8, (OK)
[    29.938] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.938] drmOpenDevice: node name is /dev/dri/card0
[    29.938] drmOpenDevice: open result is 8, (OK)
[    29.938] drmOpenByBusid: drmOpenMinor returns 8
[    29.938] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.941] drmOpenDevice: node name is /dev/dri/card0
[    29.941] drmOpenDevice: open result is 8, (OK)
[    29.941] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.941] drmOpenDevice: node name is /dev/dri/card0
[    29.941] drmOpenDevice: open result is 8, (OK)
[    29.941] drmOpenByBusid: drmOpenMinor returns 8
[    29.941] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.941] (II) Loading /usr/lib/xorg/modules/drivers/pvr_drv.so
[    29.942] drmOpenDevice: node name is /dev/dri/card0
[    29.942] drmOpenDevice: open result is 9, (OK)
[    29.942] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.942] drmOpenDevice: node name is /dev/dri/card0
[    29.943] drmOpenDevice: open result is 9, (OK)
[    29.943] drmOpenByBusid: drmOpenMinor returns 9
[    29.943] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.943] drmOpenDevice: node name is /dev/dri/card0
[    29.943] drmOpenDevice: open result is 10, (OK)
[    29.943] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.943] drmOpenDevice: node name is /dev/dri/card0
[    29.943] drmOpenDevice: open result is 10, (OK)
[    29.943] drmOpenByBusid: drmOpenMinor returns 10
[    29.943] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    29.943] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.947] drmOpenDevice: node name is /dev/dri/card0
[    29.948] drmOpenDevice: open result is 11, (OK)
[    29.948] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.948] drmOpenDevice: node name is /dev/dri/card0
[    29.948] drmOpenDevice: open result is 11, (OK)
[    29.948] drmOpenByBusid: drmOpenMinor returns 11
[    29.948] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    29.948] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    29.948] drmOpenDevice: node name is /dev/dri/card0
[    29.949] drmOpenDevice: open result is 11, (OK)
[    29.949] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    29.949] drmOpenDevice: node name is /dev/dri/card0
[    29.949] drmOpenDevice: open result is 11, (OK)
[    29.949] drmOpenByBusid: drmOpenMinor returns 11
[    29.949] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    29.949] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    30.029] drmOpenDevice: node name is /dev/dri/card0
[    30.029] drmOpenDevice: open result is 11, (OK)
[    30.029] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[    30.029] drmOpenDevice: node name is /dev/dri/card0
[    30.030] drmOpenDevice: open result is 11, (OK)
[    30.030] drmOpenByBusid: drmOpenMinor returns 11
[    30.030] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[    30.030] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[    30.113] (II) pvr(0): source head @cdv-v1.0.2
[    30.113] (II) pvr(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.113] (==) pvr(0): Depth 24, (==) framebuffer bpp 32
[    30.113] (==) pvr(0): RGB weight 888
[    30.113] (==) pvr(0): Default visual is TrueColor
[    30.113] (**) pvr(0): Option "FlipChain" "On"
[    30.113] (**) pvr(0): Option "SoftEXA" "Off"
[    30.113] (**) pvr(0): Option "DRIDisableVSync" "False"
[    30.113] (II) pvr(0): Flipchain enabled
[    30.180] (II) pvr(0): Output VGA1 has no monitor section
[    30.286] (II) pvr(0): Output LVDS1 has no monitor section
[    30.287] (II) pvr(0): found backlight control interface /sys/class/backlight/acpi_video0
[    30.332] (II) pvr(0): Output DVI1 has no monitor section
[    30.333] (II) pvr(0): Output DP1 has no monitor section
[    30.396] (II) pvr(0): EDID for output VGA1
[    30.502] (II) pvr(0): EDID for output LVDS1
[    30.503] (II) pvr(0): Manufacturer: AUO  Model: 61d2  Serial#: 0
[    30.503] (II) pvr(0): Year: 2009  Week: 0
[    30.503] (II) pvr(0): EDID Version: 1.3
[    30.503] (II) pvr(0): Digital Display Input
[    30.503] (II) pvr(0): Max Image Size [cm]: horiz.: 22  vert.: 13
[    30.503] (II) pvr(0): Gamma: 2.20
[    30.503] (II) pvr(0): No DPMS capabilities specified
[    30.503] (II) pvr(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    30.503] (II) pvr(0): First detailed timing is preferred mode
[    30.503] (II) pvr(0): redX: 0.590 redY: 0.345   greenX: 0.325 greenY: 0.540
[    30.503] (II) pvr(0): blueX: 0.150 blueY: 0.145   whiteX: 0.313 whiteY: 0.329
[    30.503] (II) pvr(0): Manufacturer's mask: 0
[    30.503] (II) pvr(0): Supported detailed timing:
[    30.503] (II) pvr(0): clock: 49.8 MHz   Image Size:  222 x 125 mm
[    30.503] (II) pvr(0): h_active: 1024  h_sync: 1072  h_sync_end 1104 h_blank_end 1338 h_border: 0
[    30.503] (II) pvr(0): v_active: 600  v_sync: 602  v_sync_end 608 v_blanking: 620 v_border: 0
[    30.503] (II) pvr(0): Unknown vendor-specific block f
[    30.503] (II) pvr(0):  AUO
[    30.503] (II) pvr(0):  B101AW06 V1
[    30.503] (II) pvr(0): EDID (in hex):
[    30.503] (II) pvr(0):     00ffffffffffff0006afd26100000000
[    30.503] (II) pvr(0):     0013010380160d780a15859758538a26
[    30.503] (II) pvr(0):     25505400000001010101010101010101
[    30.503] (II) pvr(0):     0101010101017413003a415814203020
[    30.503] (II) pvr(0):     2600de7d000000180000000f00000000
[    30.503] (II) pvr(0):     00000000000000000020000000fe0041
[    30.503] (II) pvr(0):     554f0a202020202020202020000000fe
[    30.504] (II) pvr(0):     004231303141573036205631200a0029
[    30.504] (II) pvr(0): Not using default mode "320x240" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "400x300" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "400x300" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "512x384" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "640x480" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "640x512" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "800x600" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "576x432" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "680x384" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "680x384" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "700x525" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "720x450" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "800x512" (doublescan mode not supported)
[    30.504] (II) pvr(0): Not using default mode "840x525" (doublescan mode not supported)
[    30.505] (II) pvr(0): Not using default mode "840x525" (doublescan mode not supported)
[    30.505] (II) pvr(0): Not using default mode "960x540" (doublescan mode not supported)
[    30.505] (II) pvr(0): Not using default mode "960x600" (doublescan mode not supported)
[    30.505] (II) pvr(0): Printing probed modes for output LVDS1
[    30.505] (II) pvr(0): Modeline "1024x600"x60.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    30.505] (II) pvr(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    30.505] (II) pvr(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    30.505] (II) pvr(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    30.550] (II) pvr(0): EDID for output DVI1
[    30.551] (II) pvr(0): EDID for output DP1
[    30.551] (II) pvr(0): Output VGA1 disconnected
[    30.551] (II) pvr(0): Output LVDS1 connected
[    30.551] (II) pvr(0): Output DVI1 disconnected
[    30.551] (II) pvr(0): Output DP1 disconnected
[    30.551] (II) pvr(0): Using exact sizes for initial modes
[    30.551] (II) pvr(0): Output LVDS1 using initial mode 1024x600
[    30.551] (II) pvr(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    30.551] (--) pvr(0): Virtual size is 1024x600 (pitch 1024)
[    30.551] (**) pvr(0):  Driver mode "1024x600": 49.8 MHz (scaled from 0.0 MHz), 37.2 kHz, 60.0 Hz
[    30.551] (II) pvr(0): Modeline "1024x600"x60.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    30.551] (**) pvr(0):  Default mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    30.551] (II) pvr(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    30.551] (**) pvr(0):  Default mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    30.551] (II) pvr(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    30.551] (**) pvr(0):  Default mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    30.551] (II) pvr(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    30.551] (==) pvr(0): DPI set to (96, 96)
[    30.551] (II) Loading sub module "fb"
[    30.551] (II) LoadModule: "fb"
[    30.552] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.552] (II) Module fb: vendor="X.Org Foundation"
[    30.552]     compiled for 1.11.3, module version = 1.0.0
[    30.552]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.552] (II) pvr(0): [pvr] Software copy threshold : 0B
[    30.552] (II) pvr(0): [pvr] Software solid threshold : 0B
[    30.552] (II) pvr(0): [pvr] Software composite threshold : 0B
[    30.552] (II) pvr(0): [pvr] Pixmap pool size: 0B
[    30.552] (II) Loading sub module "exa"
[    30.552] (II) LoadModule: "exa"
[    30.553] (II) Loading /usr/lib/xorg/modules/libexa.so
[    30.553] (II) Module exa: vendor="X.Org Foundation"
[    30.553]     compiled for 1.11.3, module version = 2.5.0
[    30.553]     ABI class: X.Org Video Driver, version 11.0
[    30.553] PVRPreInit: done
[    30.553] (--) Depth 24 pixmap format is 32 bpp
[    30.553] (II) pvr(0): [DRI2] Setup complete
[    30.554] (II) pvr(0): [DRI2]   DRI driver: pvr
[    30.554] (II) EXA(0): Driver allocated offscreen pixmaps
[    30.554] (II) EXA(0): Driver registered support for the following operations:
[    30.554] (II)         Solid
[    30.554] (II)         Copy
[    30.554] (II)         Composite (RENDER acceleration)
[    30.572] (==) pvr(0): Backing store disabled
[    30.573] (==) pvr(0): Silken mouse enabled
[    30.574] (==) pvr(0): DPMS enabled
[    30.574] (II) pvr(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    30.574] (II) pvr(0): max backlight 9
[    30.574] (II) pvr(0): active backlight 5
[    30.574] (==) pvr(0): Direct rendering enabled
[    30.575] (II) pvr(0): Enable XVideo
[    30.606] (II) pvr(0): [dri] Created flip chain 1
[    30.606] (II) pvr(0): hotplug detection enabled
[    30.606] (--) RandR disabled
[    30.606] (II) Initializing built-in extension Generic Event Extension
[    30.606] (II) Initializing built-in extension SHAPE
[    30.606] (II) Initializing built-in extension MIT-SHM
[    30.606] (II) Initializing built-in extension XInputExtension
[    30.606] (II) Initializing built-in extension XTEST
[    30.606] (II) Initializing built-in extension BIG-REQUESTS
[    30.606] (II) Initializing built-in extension SYNC
[    30.606] (II) Initializing built-in extension XKEYBOARD
[    30.606] (II) Initializing built-in extension XC-MISC
[    30.606] (II) Initializing built-in extension SECURITY
[    30.606] (II) Initializing built-in extension XINERAMA
[    30.606] (II) Initializing built-in extension XFIXES
[    30.606] (II) Initializing built-in extension RENDER
[    30.606] (II) Initializing built-in extension RANDR
[    30.607] (II) Initializing built-in extension COMPOSITE
[    30.607] (II) Initializing built-in extension DAMAGE
[    30.676] (II) AIGLX: Loaded and initialized swrast
[    30.677] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    30.681] (II) pvr(0): Setting screen physical size to 270 x 158
[    30.712] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    30.720] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    30.720] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.720] (II) LoadModule: "evdev"
[    30.752] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.753] (II) Module evdev: vendor="X.Org Foundation"
[    30.753]     compiled for 1.11.3, module version = 2.7.0
[    30.753]     Module class: X.Org XInput Driver
[    30.753]     ABI class: X.Org XInput driver, version 16.0
[    30.753] (II) Using input driver 'evdev' for 'Power Button'
[    30.753] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.753] (**) Power Button: always reports core events
[    30.753] (**) evdev: Power Button: Device: "/dev/input/event3"
[    30.753] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.754] (--) evdev: Power Button: Found keys
[    30.754] (II) evdev: Power Button: Configuring as keyboard
[    30.754] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    30.754] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    30.754] (**) Option "xkb_rules" "evdev"
[    30.754] (**) Option "xkb_model" "pc105"
[    30.754] (**) Option "xkb_layout" "us"
[    30.756] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    30.756] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    30.756] (II) Using input driver 'evdev' for 'Video Bus'
[    30.756] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.756] (**) Video Bus: always reports core events
[    30.756] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    30.756] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    30.756] (--) evdev: Video Bus: Found keys
[    30.756] (II) evdev: Video Bus: Configuring as keyboard
[    30.756] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input7/event7"
[    30.756] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    30.756] (**) Option "xkb_rules" "evdev"
[    30.756] (**) Option "xkb_model" "pc105"
[    30.756] (**) Option "xkb_layout" "us"
[    30.758] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    30.758] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    30.758] (II) Using input driver 'evdev' for 'Power Button'
[    30.758] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.758] (**) Power Button: always reports core events
[    30.758] (**) evdev: Power Button: Device: "/dev/input/event0"
[    30.759] (--) evdev: Power Button: Vendor 0 Product 0x1
[    30.759] (--) evdev: Power Button: Found keys
[    30.759] (II) evdev: Power Button: Configuring as keyboard
[    30.759] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    30.759] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    30.759] (**) Option "xkb_rules" "evdev"
[    30.759] (**) Option "xkb_model" "pc105"
[    30.759] (**) Option "xkb_layout" "us"
[    30.761] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    30.761] (II) No input driver specified, ignoring this device.
[    30.761] (II) This device may have been added with another device file.
[    30.761] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    30.762] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    30.762] (II) Using input driver 'evdev' for 'Sleep Button'
[    30.762] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.762] (**) Sleep Button: always reports core events
[    30.762] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    30.762] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    30.762] (--) evdev: Sleep Button: Found keys
[    30.762] (II) evdev: Sleep Button: Configuring as keyboard
[    30.762] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    30.762] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    30.762] (**) Option "xkb_rules" "evdev"
[    30.762] (**) Option "xkb_model" "pc105"
[    30.762] (**) Option "xkb_layout" "us"
[    30.764] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event10)
[    30.764] (II) No input driver specified, ignoring this device.
[    30.764] (II) This device may have been added with another device file.
[    30.765] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event11)
[    30.765] (II) No input driver specified, ignoring this device.
[    30.765] (II) This device may have been added with another device file.
[    30.766] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event9)
[    30.766] (II) No input driver specified, ignoring this device.
[    30.766] (II) This device may have been added with another device file.
[    30.767] (II) config/udev: Adding input device WebCam (/dev/input/event5)
[    30.767] (**) WebCam: Applying InputClass "evdev keyboard catchall"
[    30.767] (II) Using input driver 'evdev' for 'WebCam'
[    30.767] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.767] (**) WebCam: always reports core events
[    30.767] (**) evdev: WebCam: Device: "/dev/input/event5"
[    30.767] (--) evdev: WebCam: Vendor 0x402 Product 0x7675
[    30.767] (--) evdev: WebCam: Found keys
[    30.767] (II) evdev: WebCam: Configuring as keyboard
[    30.767] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-3/1-3:1.0/input/input5/event5"
[    30.767] (II) XINPUT: Adding extended input device "WebCam" (type: KEYBOARD, id 10)
[    30.767] (**) Option "xkb_rules" "evdev"
[    30.767] (**) Option "xkb_model" "pc105"
[    30.768] (**) Option "xkb_layout" "us"
[    30.769] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    30.769] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    30.769] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    30.769] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.770] (**) AT Translated Set 2 keyboard: always reports core events
[    30.770] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    30.770] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    30.770] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    30.770] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    30.770] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    30.770] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    30.770] (**) Option "xkb_rules" "evdev"
[    30.770] (**) Option "xkb_model" "pc105"
[    30.770] (**) Option "xkb_layout" "us"
[    30.772] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[    30.772] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    30.772] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    30.772] (II) LoadModule: "synaptics"
[    30.773] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.773] (II) Module synaptics: vendor="X.Org Foundation"
[    30.773]     compiled for 1.11.3, module version = 1.6.2
[    30.773]     Module class: X.Org XInput Driver
[    30.773]     ABI class: X.Org XInput driver, version 16.0
[    30.773] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    30.773] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    30.774] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.774] (**) Option "Device" "/dev/input/event8"
[    30.856] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5612
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4618
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    30.856] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.856] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.896] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input8/event8"
[    30.896] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    30.896] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    30.896] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    30.896] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    30.897] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    30.897] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    30.897] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    30.897] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    30.897] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.898] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    30.898] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.908] (II) config/udev: Adding input device Acer WMI hotkeys (/dev/input/event6)
[    30.908] (**) Acer WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    30.908] (II) Using input driver 'evdev' for 'Acer WMI hotkeys'
[    30.908] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    30.908] (**) Acer WMI hotkeys: always reports core events
[    30.908] (**) evdev: Acer WMI hotkeys: Device: "/dev/input/event6"
[    30.908] (--) evdev: Acer WMI hotkeys: Vendor 0 Product 0
[    30.908] (--) evdev: Acer WMI hotkeys: Found keys
[    30.909] (II) evdev: Acer WMI hotkeys: Configuring as keyboard
[    30.909] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    30.909] (II) XINPUT: Adding extended input device "Acer WMI hotkeys" (type: KEYBOARD, id 13)
[    30.909] (**) Option "xkb_rules" "evdev"
[    30.909] (**) Option "xkb_model" "pc105"
[    30.909] (**) Option "xkb_layout" "us"
[    32.402] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    32.402] (II) pvr(0): Printing DDC gathered Modelines:
[    32.402] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    33.490] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    33.490] (II) pvr(0): Printing DDC gathered Modelines:
[    33.490] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    45.118] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    45.118] (II) pvr(0): Printing DDC gathered Modelines:
[    45.118] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    45.333] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    45.333] (II) pvr(0): Printing DDC gathered Modelines:
[    45.334] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    47.050] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    47.050] (II) pvr(0): Printing DDC gathered Modelines:
[    47.050] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    47.265] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    47.266] (II) pvr(0): Printing DDC gathered Modelines:
[    47.266] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    51.770] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    51.770] (II) pvr(0): Printing DDC gathered Modelines:
[    51.770] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    52.014] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    52.014] (II) pvr(0): Printing DDC gathered Modelines:
[    52.014] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    52.234] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    52.234] (II) pvr(0): Printing DDC gathered Modelines:
[    52.234] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[    92.898] (II) PM Event received: Capability Changed
[    93.924] (II) pvr(0): EDID vendor "AUO", prod id 25042
[    93.924] (II) pvr(0): Printing DDC gathered Modelines:
[    93.924] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
[   145.116] (II) pvr(0): EDID vendor "AUO", prod id 25042
[   145.116] (II) pvr(0): Printing DDC gathered Modelines:
[   145.116] (II) pvr(0): Modeline "1024x600"x0.0   49.80  1024 1072 1104 1338  600 602 608 620 -hsync -vsync (37.2 kHz)
```

I was wondering if there is something I can diagnose the problem instead of resorting to using 3.2.0-48-generic-pae.
I tried the IRC and the friendly people on there told me I should diagnose the problem as soon as possible instead of resorting to using a previous version of the kernel.

As I am new I require some help, so that I can make my dcomputer stable again and run smoothly without hipcups instead of restarting and hoping for the best and having to shut down and restart till it just randomly works or going back to previous versions of linux.

Thanks inadvance
-Psil0

---

### Post by Old_Grey_Wolf on 2013-07-13
Threads merged. Please do not start duplicate threads.

---

### Post by Psil0cybin on 2013-07-18
Okay thank you, does anyone have an Idea?

---

### Post by Psil0cybin on 2013-07-18
Problem Solved!
Some update, caused another graphic driver to become enabled. Disabling it, fixed the problem.

---

