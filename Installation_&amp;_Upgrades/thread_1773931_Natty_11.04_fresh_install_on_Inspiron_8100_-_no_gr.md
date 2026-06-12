---
title: "Natty 11.04 fresh install on Inspiron 8100 - no graphics"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2011-06-02
I think I posted this on the wrong group. Please allow me to repeat it here. I had Maverick 10.10 running fine on an Inspiron 8100 that has a NVIDIA GeForce2Go graphic card. I did a fresh install of Natty 11.04 (not an upgrade) from the live CD. Apparently everything went fine, however when I restarted the machine, it went through a few messages in the console and stopped there. I got out of there by clicking ctrl+alt+F4, and after logging on I typed "startx" and it said that the nvidia nor nouveau modules were found (see attached Xorg.0.log). I checked that the "xserver-xorg-video-nouveau" and "libdrm-nouveau1a" were installed. I don't particularly care about having the 3D driver from NVIDIA, I just want some graphics. Thanks.

Daniel

```

[   150.363] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[   150.363] X Protocol Version 11, Revision 0
[   150.363] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   150.363] Current Operating System: Linux agnes 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686
[   150.363] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic root=UUID=c73ec0ed-a3d7-40c1-a24c-cb824170c69d ro quiet splash vt.handoff=7
[   150.363] Build Date: 21 May 2011  11:38:35AM
[   150.363] xorg-server 2:1.10.1-1ubuntu1.1 (For technical support please see http://www.ubuntu.com/support) 
[   150.363] Current version of pixman: 0.20.2
[   150.363]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   150.363] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   150.364] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun  2 11:38:45 2011
[   150.365] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   150.365] (==) No Layout section.  Using the first Screen section.
[   150.366] (==) No screen section available. Using defaults.
[   150.366] (**) |-->Screen "Default Screen Section" (0)
[   150.366] (**) |   |-->Monitor "<default monitor>"
[   150.366] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   150.367] (==) Automatically adding devices
[   150.367] (==) Automatically enabling devices
[   150.367] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   150.367]     Entry deleted from font path.
[   150.367] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   150.367]     Entry deleted from font path.
[   150.367] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   150.367]     Entry deleted from font path.
[   150.367] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   150.367]     Entry deleted from font path.
[   150.367] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   150.367]     Entry deleted from font path.
[   150.367] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   150.367] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   150.367] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   150.367] (II) Loader magic: 0x81ffde0
[   150.368] (II) Module ABI versions:
[   150.368]     X.Org ANSI C Emulation: 0.4
[   150.368]     X.Org Video Driver: 10.0
[   150.368]     X.Org XInput driver : 12.3
[   150.368]     X.Org Server Extension : 5.0
[   150.369] (--) PCI:*(0:1:0:0) 10de:0112:1028:00e6 rev 178, Mem @ 0xfc000000/16777216, 0xe0000000/134217728, BIOS @ 0x????????/65536
[   150.370] (II) Open ACPI successful (/var/run/acpid.socket)
[   150.370] (II) LoadModule: "extmod"
[   150.372] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   150.372] (II) Module extmod: vendor="X.Org Foundation"
[   150.372]     compiled for 1.10.1, module version = 1.0.0
[   150.372]     Module class: X.Org Server Extension
[   150.372]     ABI class: X.Org Server Extension, version 5.0
[   150.372] (II) Loading extension MIT-SCREEN-SAVER
[   150.373] (II) Loading extension XFree86-VidModeExtension
[   150.373] (II) Loading extension XFree86-DGA
[   150.373] (II) Loading extension DPMS
[   150.373] (II) Loading extension XVideo
[   150.373] (II) Loading extension XVideo-MotionCompensation
[   150.373] (II) Loading extension X-Resource
[   150.373] (II) LoadModule: "dbe"
[   150.374] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   150.374] (II) Module dbe: vendor="X.Org Foundation"
[   150.374]     compiled for 1.10.1, module version = 1.0.0
[   150.374]     Module class: X.Org Server Extension
[   150.374]     ABI class: X.Org Server Extension, version 5.0
[   150.374] (II) Loading extension DOUBLE-BUFFER
[   150.374] (II) LoadModule: "glx"
[   150.375] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   150.375] (II) Module glx: vendor="X.Org Foundation"
[   150.375]     compiled for 1.10.1, module version = 1.0.0
[   150.375]     ABI class: X.Org Server Extension, version 5.0
[   150.375] (==) AIGLX enabled
[   150.375] (II) Loading extension GLX
[   150.375] (II) LoadModule: "record"
[   150.376] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   150.377] (II) Module record: vendor="X.Org Foundation"
[   150.377]     compiled for 1.10.1, module version = 1.13.0
[   150.377]     Module class: X.Org Server Extension
[   150.377]     ABI class: X.Org Server Extension, version 5.0
[   150.377] (II) Loading extension RECORD
[   150.377] (II) LoadModule: "dri"
[   150.377] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   150.378] (II) Module dri: vendor="X.Org Foundation"
[   150.378]     compiled for 1.10.1, module version = 1.0.0
[   150.378]     ABI class: X.Org Server Extension, version 5.0
[   150.378] (II) Loading extension XFree86-DRI
[   150.378] (II) LoadModule: "dri2"
[   150.379] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   150.379] (II) Module dri2: vendor="X.Org Foundation"
[   150.379]     compiled for 1.10.1, module version = 1.2.0
[   150.379]     ABI class: X.Org Server Extension, version 5.0
[   150.379] (II) Loading extension DRI2
[   150.379] (==) Matched nvidia as autoconfigured driver 0
[   150.379] (==) Matched nouveau as autoconfigured driver 1
[   150.379] (==) Matched nv as autoconfigured driver 2
[   150.379] (==) Matched vesa as autoconfigured driver 3
[   150.380] (==) Matched fbdev as autoconfigured driver 4
[   150.380] (==) Assigned the driver to the xf86ConfigLayout
[   150.380] (II) LoadModule: "nvidia"
[   150.382] (WW) Warning, couldn't open module nvidia
[   150.382] (II) UnloadModule: "nvidia"
[   150.382] (II) Unloading nvidia
[   150.382] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   150.382] (II) LoadModule: "nouveau"
[   150.383] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   150.384] (II) Module nouveau: vendor="X.Org Foundation"
[   150.384]     compiled for 1.10.0, module version = 0.0.16
[   150.384]     Module class: X.Org Video Driver
[   150.384]     ABI class: X.Org Video Driver, version 10.0
[   150.384] (II) LoadModule: "nv"
[   150.386] (WW) Warning, couldn't open module nv
[   150.386] (II) UnloadModule: "nv"
[   150.386] (II) Unloading nv
[   150.386] (EE) Failed to load module "nv" (module does not exist, 0)
[   150.386] (II) LoadModule: "vesa"
[   150.387] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   150.388] (II) Module vesa: vendor="X.Org Foundation"
[   150.388]     compiled for 1.10.0, module version = 2.3.0
[   150.388]     Module class: X.Org Video Driver
[   150.388]     ABI class: X.Org Video Driver, version 10.0
[   150.388] (II) LoadModule: "fbdev"
[   150.389] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   150.389] (II) Module fbdev: vendor="X.Org Foundation"
[   150.389]     compiled for 1.10.0, module version = 0.4.2
[   150.389]     ABI class: X.Org Video Driver, version 10.0
[   150.389] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[   150.389] (II) NOUVEAU driver for NVIDIA chipset families :
[   150.389]     RIVA TNT    (NV04)
[   150.390]     RIVA TNT2   (NV05)
[   150.390]     GeForce 256 (NV10)
[   150.390]     GeForce 2   (NV11, NV15)
[   150.390]     GeForce 4MX (NV17, NV18)
[   150.390]     GeForce 3   (NV20)
[   150.390]     GeForce 4Ti (NV25, NV28)
[   150.390]     GeForce FX  (NV3x)
[   150.390]     GeForce 6   (NV4x)
[   150.390]     GeForce 7   (G7x)
[   150.390]     GeForce 8   (G8x)
[   150.390] (II) VESA: driver for VESA chipsets: vesa
[   150.390] (II) FBDEV: driver for framebuffer: fbdev
[   150.391] (--) using VT number 8

[   150.398] drmOpenDevice: node name is /dev/dri/card0
[   150.398] drmOpenDevice: open result is 8, (OK)
[   150.398] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   150.398] drmOpenDevice: node name is /dev/dri/card0
[   150.398] drmOpenDevice: open result is 8, (OK)
[   150.398] drmOpenByBusid: drmOpenMinor returns 8
[   150.399] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   150.399] (II) [drm] nouveau interface version: 0.0.16
[   150.399] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   150.399] (WW) Falling back to old probe method for vesa
[   150.399] (WW) Falling back to old probe method for fbdev
[   150.399] (II) Loading sub module "fbdevhw"
[   150.399] (II) LoadModule: "fbdevhw"
[   150.400] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   150.400] (II) Module fbdevhw: vendor="X.Org Foundation"
[   150.400]     compiled for 1.10.1, module version = 0.0.2
[   150.400]     ABI class: X.Org Video Driver, version 10.0
[   150.400] (II) Loading sub module "dri"
[   150.400] (II) LoadModule: "dri"
[   150.401] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   150.401] (II) Module dri: vendor="X.Org Foundation"
[   150.401]     compiled for 1.10.1, module version = 1.0.0
[   150.401]     ABI class: X.Org Server Extension, version 5.0
[   150.401] (II) NOUVEAU(0): Loaded DRI module
[   150.401] drmOpenDevice: node name is /dev/dri/card0
[   150.402] drmOpenDevice: open result is 9, (OK)
[   150.402] drmOpenDevice: node name is /dev/dri/card0
[   150.402] drmOpenDevice: open result is 9, (OK)
[   150.402] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[   150.402] drmOpenDevice: node name is /dev/dri/card0
[   150.402] drmOpenDevice: open result is 9, (OK)
[   150.402] drmOpenByBusid: drmOpenMinor returns 9
[   150.402] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[   150.402] (II) [drm] DRM interface version 1.4
[   150.402] (II) [drm] DRM open master succeeded.
[   150.402] (--) NOUVEAU(0): Chipset: "NVIDIA NV11"
[   150.402] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   150.402] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[   150.402] (==) NOUVEAU(0): RGB weight 888
[   150.402] (==) NOUVEAU(0): Default visual is TrueColor
[   150.403] (==) NOUVEAU(0): Using HW cursor
[   150.403] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[   150.460] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[   150.572] (II) NOUVEAU(0): Output LVDS-1 has no monitor section
[   150.621] (II) NOUVEAU(0): EDID for output VGA-1
[   150.734] (II) NOUVEAU(0): EDID for output LVDS-1
[   150.734] (II) NOUVEAU(0): Manufacturer: LCD  Model: 6600  Serial#: 16843009
[   150.734] (II) NOUVEAU(0): Year: 2002  Week: 16
[   150.734] (II) NOUVEAU(0): EDID Version: 1.3
[   150.734] (II) NOUVEAU(0): Digital Display Input
[   150.734] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 30  vert.: 23
[   150.734] (II) NOUVEAU(0): Gamma defined in extension block
[   150.734] (II) NOUVEAU(0): No DPMS capabilities specified
[   150.734] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   150.734] (II) NOUVEAU(0): First detailed timing is preferred mode
[   150.734] (II) NOUVEAU(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[   150.734] (II) NOUVEAU(0): blueX: 0.155 blueY: 0.155   whiteX: 0.315 whiteY: 0.330
[   150.734] (II) NOUVEAU(0): Manufacturer's mask: 0
[   150.734] (II) NOUVEAU(0): Supported standard timings:
[   150.735] (II) NOUVEAU(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[   150.735] (II) NOUVEAU(0): Supported detailed timing:
[   150.735] (II) NOUVEAU(0): clock: 162.0 MHz   Image Size:  305 x 229 mm
[   150.735] (II) NOUVEAU(0): h_active: 1600  h_sync: 1664  h_sync_end 1856 h_blank_end 2160 h_border: 0
[   150.735] (II) NOUVEAU(0): v_active: 1200  v_sync: 1201  v_sync_end 1204 v_blanking: 1250 v_border: 0
[   150.735] (II) NOUVEAU(0): Ranges: V min: 59 V max: 61 Hz, H min: 70 H max: 75 kHz, PixClock max 175 MHz
[   150.735] (II) NOUVEAU(0): Monitor name: LTM15C166
[   150.735] (II) NOUVEAU(0): Serial No: 8AC2D005661
[   150.735] (II) NOUVEAU(0): EDID (in hex):
[   150.735] (II) NOUVEAU(0):     00ffffffffffff003064006601010101
[   150.735] (II) NOUVEAU(0):     100c0103801e17ff0a87fe94574f8c27
[   150.735] (II) NOUVEAU(0):     275054000000a9400101010101010101
[   150.735] (II) NOUVEAU(0):     010101010101483f403062b0324040c0
[   150.735] (II) NOUVEAU(0):     130031e51000001e000000fd003b3d46
[   150.735] (II) NOUVEAU(0):     4b11000a202020202020000000fc004c
[   150.735] (II) NOUVEAU(0):     544d3135433136360a202020000000ff
[   150.735] (II) NOUVEAU(0):     0038414332443030353636310a20001d
[   150.736] (II) NOUVEAU(0): Printing probed modes for output LVDS-1
[   150.736] (II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[   150.736] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[   150.736] (II) NOUVEAU(0): Output VGA-1 disconnected
[   150.736] (II) NOUVEAU(0): Output LVDS-1 connected
[   150.737] (II) NOUVEAU(0): Using exact sizes for initial modes
[   150.737] (II) NOUVEAU(0): Output LVDS-1 using initial mode 1600x1200
[   150.737] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   150.737] (--) NOUVEAU(0): Virtual size is 1600x1200 (pitch 0)
[   150.737] (**) NOUVEAU(0):  Driver mode "1600x1200": 162.0 MHz (scaled from 0.0 MHz), 75.0 kHz, 60.0 Hz
[   150.737] (II) NOUVEAU(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[   150.737] (**) NOUVEAU(0):  Driver mode "1600x1200": 161.0 MHz (scaled from 0.0 MHz), 74.5 kHz, 59.9 Hz
[   150.737] (II) NOUVEAU(0): Modeline "1600x1200"x59.9  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync (74.5 kHz)
[   150.737] (**) NOUVEAU(0):  Driver mode "1400x1050": 121.8 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
[   150.737] (II) NOUVEAU(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[   150.737] (**) NOUVEAU(0):  Driver mode "1280x1024": 109.0 MHz (scaled from 0.0 MHz), 63.7 kHz, 59.9 Hz
[   150.737] (II) NOUVEAU(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz)
[   150.737] (**) NOUVEAU(0):  Driver mode "1280x960": 101.2 MHz (scaled from 0.0 MHz), 59.7 kHz, 59.9 Hz
[   150.737] (II) NOUVEAU(0): Modeline "1280x960"x59.9  101.25  1280 1360 1488 1696  960 963 967 996 -hsync +vsync (59.7 kHz)
[   150.737] (**) NOUVEAU(0):  Driver mode "1152x864": 81.8 MHz (scaled from 0.0 MHz), 53.8 kHz, 60.0 Hz
[   150.738] (II) NOUVEAU(0): Modeline "1152x864"x60.0   81.75  1152 1216 1336 1520  864 867 871 897 -hsync +vsync (53.8 kHz)
[   150.738] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[   150.738] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[   150.738] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[   150.738] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[   150.738] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[   150.738] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[   150.738] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[   150.738] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz)
[   150.738] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[   150.738] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz)
[   150.738] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[   150.738] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz)
[   150.738] (==) NOUVEAU(0): DPI set to (96, 96)
[   150.738] (II) Loading sub module "fb"
[   150.738] (II) LoadModule: "fb"
[   150.739] (II) Loading /usr/lib/xorg/modules/libfb.so
[   150.740] (II) Module fb: vendor="X.Org Foundation"
[   150.740]     compiled for 1.10.1, module version = 1.0.0
[   150.740]     ABI class: X.Org ANSI C Emulation, version 0.4
[   150.740] (II) Loading sub module "exa"
[   150.740] (II) LoadModule: "exa"
[   150.741] (II) Loading /usr/lib/xorg/modules/libexa.so
[   150.742] (II) Module exa: vendor="X.Org Foundation"
[   150.742]     compiled for 1.10.1, module version = 2.5.0
[   150.742]     ABI class: X.Org Video Driver, version 10.0
[   150.742] (II) Loading sub module "shadowfb"
[   150.742] (II) LoadModule: "shadowfb"
[   150.743] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[   150.743] (II) Module shadowfb: vendor="X.Org Foundation"
[   150.743]     compiled for 1.10.1, module version = 1.0.0
[   150.743]     ABI class: X.Org ANSI C Emulation, version 0.4
[   150.743] (II) UnloadModule: "vesa"
[   150.743] (II) Unloading vesa
[   150.743] (II) UnloadModule: "fbdev"
[   150.743] (II) Unloading fbdev
[   150.743] (II) UnloadModule: "fbdevhw"
[   150.743] (II) Unloading fbdevhw
[   150.743] (--) Depth 24 pixmap format is 32 bpp
[   150.745] (II) NOUVEAU(0): Opened GPU channel 1
[   150.745] (II) NOUVEAU(0): [DRI2] Setup complete
[   150.745] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau_vieux
[   150.746] (EE) NOUVEAU(0): Error allocating scanout buffer: 0
[   150.746] 
Fatal server error:
[   150.746] AddScreen/ScreenInit failed for driver 0
[   150.747] 
[   150.747] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   150.747] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   150.747] 
[   150.761]  ddxSigGiveUp: Closing log

```

---

### Post by Bobhuber on 2011-06-02
[QUOTE=danielsender;10895173]I think I posted this on the wrong group. Please allow me to repeat it here. I had Maverick 10.10 running fine on an Inspiron 8100 that has a NVIDIA GeForce2Go graphic card. I did a fresh install of Natty 11.04 (not an upgrade) from the live CD. Apparently everything went fine, however when I restarted the machine, it went through a few messages in the console and stopped there. I got out of there by clicking ctrl+alt+F4, and after logging on I typed "startx" and it said that the nvidia nor nouveau modules were found (see attached Xorg.0.log). I checked that the "xserver-xorg-video-nouveau" and "libdrm-nouveau1a" were installed. I don't particularly care about having the 3D driver from NVIDIA, I just want some graphics. Thanks.

Install the Nvidia drivers with the system or proprietary drivers. I assume you meant GT220

---

### Post by JohnBonne on 2011-06-02
I have an old desktop I am thinking about adding a Linux based O/S to. It has the same graphics card and I have asked around for advice. They say I may have problems with Unity being too demanding. Just my two cents, but maybe a less power demanding operating system would be  better for you.

---

### Post by danielsender on 2011-06-06
I have the solution thanks to alex buell at munted and also the posting [http://ubuntuforums.org/showthread.php?t=1760671](http://ubuntuforums.org/showthread.php?t=1760671). It's simply to add the following options in grub to the boot command:

GRUB_CMDLINE_LINUX="video=LVDS-1:1600x1200 nouveau.noaccel=1"

---

