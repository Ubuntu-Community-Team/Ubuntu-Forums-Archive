---
title: "switch back to opensource graphics card driver (is it mesa?)"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by alansandbucket on 2013-04-28
i installed nvidia-current through the command line and now the bars on my screen dont appear. i uninstalled the nvidia-current driver and the bars still dont appear. did i uninstall it incorrectly? what should i do?

---

### Post by MAFoElffen on 2013-04-28
try this:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo apt-get remove nvidia-current
sudo apt-get --purge nvidia-current
sudo service lightdm restart

```Doing the first line will get you where you need to be- Just skipping over the driver. Doing the top two lines will remove the driver but leave the package there. Doing the top 3 lines will remove all traces and get you back to where you were before installing it. The 4th line just restarts the DM.

Then it should default back to the opensource nouveau driver

---

### Post by alansandbucket on 2013-04-28
i get a message saying
cannot stat /etc/X11/xorg.conf no such file

---

### Post by MAFoElffen on 2013-04-28
That first line was to make sure xorg.conf was rename to something else. If it is already renamed or gone... then it is not using the nvidia driver.

Please post your /var/log/Xorg.0.log file...

---

### Post by alansandbucket on 2013-04-28
here is my log file:
[    28.383] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[    28.383] X Protocol Version 11, Revision 0
[    28.383] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    28.383] Current Operating System: Linux alan-Lenovo-IdeaPad-P580 3.5.0-27-generic #46-Ubuntu SMP Mon Mar 25 19:58:17 UTC 2013 x86_64
[    28.383] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-27-generic root=UUID=70dd1bfc-d3fb-4459-a2c1-c3fb4f8c73b7 ro quiet splash
[    28.383] Build Date: 17 April 2013  10:43:13PM
[    28.383] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    28.383] Current version of pixman: 0.28.2
[    28.383]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    28.383] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.383] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 28 17:23:01 2013
[    28.442] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.443] (==) No Layout section.  Using the first Screen section.
[    28.443] (==) No screen section available. Using defaults.
[    28.443] (**) |-->Screen "Default Screen Section" (0)
[    28.443] (**) |   |-->Monitor "<default monitor>"
[    28.443] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.443] (==) Automatically adding devices
[    28.443] (==) Automatically enabling devices
[    28.443] (==) Automatically adding GPU devices
[    28.443] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.443]     Entry deleted from font path.
[    28.443] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.443]     Entry deleted from font path.
[    28.443] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.443]     Entry deleted from font path.
[    28.443] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.443]     Entry deleted from font path.
[    28.443] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.443]     Entry deleted from font path.
[    28.443] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    28.443]     Entry deleted from font path.
[    28.443] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    28.443] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.443] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.443] (II) Loader magic: 0x7f7d49f88d20
[    28.443] (II) Module ABI versions:
[    28.443]     X.Org ANSI C Emulation: 0.4
[    28.443]     X.Org Video Driver: 13.1
[    28.443]     X.Org XInput driver : 18.0
[    28.443]     X.Org Server Extension : 7.0
[    28.443] (II) config/udev: Adding drm device (/dev/dri/card0)
[    28.444] (--) PCI:*(0:0:2:0) 8086:0166:17aa:3901 rev 9, Mem @ 0xd3400000/4194304, 0xe0000000/268435456, I/O @ 0x00004000/64
[    28.444] (--) PCI: (0:1:0:0) 10de:0de9:17aa:3901 rev 161, Mem @ 0xd2000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[    28.444] (II) Open ACPI successful (/var/run/acpid.socket)
[    28.444] Initializing built-in extension Generic Event Extension
[    28.444] Initializing built-in extension SHAPE
[    28.444] Initializing built-in extension MIT-SHM
[    28.444] Initializing built-in extension XInputExtension
[    28.444] Initializing built-in extension XTEST
[    28.444] Initializing built-in extension BIG-REQUESTS
[    28.444] Initializing built-in extension SYNC
[    28.444] Initializing built-in extension XKEYBOARD
[    28.444] Initializing built-in extension XC-MISC
[    28.444] Initializing built-in extension SECURITY
[    28.444] Initializing built-in extension XINERAMA
[    28.444] Initializing built-in extension XFIXES
[    28.444] Initializing built-in extension RENDER
[    28.444] Initializing built-in extension RANDR
[    28.444] Initializing built-in extension COMPOSITE
[    28.444] Initializing built-in extension DAMAGE
[    28.444] Initializing built-in extension MIT-SCREEN-SAVER
[    28.444] Initializing built-in extension DOUBLE-BUFFER
[    28.444] Initializing built-in extension RECORD
[    28.444] Initializing built-in extension DPMS
[    28.444] Initializing built-in extension X-Resource
[    28.444] Initializing built-in extension XVideo
[    28.444] Initializing built-in extension XVideo-MotionCompensation
[    28.444] Initializing built-in extension SELinux
[    28.444] Initializing built-in extension XFree86-VidModeExtension
[    28.444] Initializing built-in extension XFree86-DGA
[    28.444] Initializing built-in extension XFree86-DRI
[    28.444] Initializing built-in extension DRI2
[    28.444] (II) LoadModule: "glx"
[    28.508] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    29.711] (II) Module glx: vendor="NVIDIA Corporation"
[    29.711]     compiled for 4.0.2, module version = 1.0.0
[    29.711]     Module class: X.Org Server Extension
[    29.711] (II) NVIDIA GLX Module  304.88  Wed Mar 27 14:46:57 PDT 2013
[    29.711] Loading extension GLX
[    29.711] (==) Matched intel as autoconfigured driver 0
[    29.711] (==) Matched intel as autoconfigured driver 1
[    29.711] (==) Matched vesa as autoconfigured driver 2
[    29.711] (==) Matched modesetting as autoconfigured driver 3
[    29.711] (==) Matched fbdev as autoconfigured driver 4
[    29.711] (==) Assigned the driver to the xf86ConfigLayout
[    29.711] (II) LoadModule: "intel"
[    29.711] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    29.724] (II) Module intel: vendor="X.Org Foundation"
[    29.724]     compiled for 1.13.3, module version = 2.21.6
[    29.724]     Module class: X.Org Video Driver
[    29.724]     ABI class: X.Org Video Driver, version 13.1
[    29.724] (II) LoadModule: "vesa"
[    29.724] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    29.725] (II) Module vesa: vendor="X.Org Foundation"
[    29.725]     compiled for 1.12.99.902, module version = 2.3.2
[    29.725]     Module class: X.Org Video Driver
[    29.725]     ABI class: X.Org Video Driver, version 13.0
[    29.725] (II) LoadModule: "modesetting"
[    29.725] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    29.725] (II) Module modesetting: vendor="X.Org Foundation"
[    29.725]     compiled for 1.13.3, module version = 0.7.0
[    29.725]     Module class: X.Org Video Driver
[    29.725]     ABI class: X.Org Video Driver, version 13.1
[    29.725] (II) LoadModule: "fbdev"
[    29.725] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    29.725] (II) Module fbdev: vendor="X.Org Foundation"
[    29.725]     compiled for 1.12.99.902, module version = 0.4.3
[    29.725]     Module class: X.Org Video Driver
[    29.725]     ABI class: X.Org Video Driver, version 13.0
[    29.725] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    29.725] (II) VESA: driver for VESA chipsets: vesa
[    29.725] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    29.725] (II) FBDEV: driver for framebuffer: fbdev
[    29.725] (++) using VT number 7

[    29.725] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.21.6-0ubuntu4 (Bryce Harrington <bryce@ubuntu.com>)
[    29.725] (WW) Falling back to old probe method for vesa
[    29.725] (WW) Falling back to old probe method for modesetting
[    29.725] (WW) Falling back to old probe method for fbdev
[    29.725] (II) Loading sub module "fbdevhw"
[    29.725] (II) LoadModule: "fbdevhw"
[    29.726] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    29.726] (II) Module fbdevhw: vendor="X.Org Foundation"
[    29.726]     compiled for 1.13.3, module version = 0.0.2
[    29.726]     ABI class: X.Org Video Driver, version 13.1
[    29.726] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    29.726] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    29.726] (==) intel(0): RGB weight 888
[    29.726] (==) intel(0): Default visual is TrueColor
[    29.726] (--) intel(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
[    29.726] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[    29.726] (**) intel(0): Framebuffer tiled
[    29.726] (**) intel(0): Pixmaps tiled
[    29.726] (**) intel(0): "Tear free" disabled
[    29.726] (**) intel(0): Forcing per-crtc-pixmaps? no
[    29.726] (II) intel(0): Output LVDS1 has no monitor section
[    29.726] (--) intel(0): found backlight control interface acpi_video1 (type 'firmware')
[    29.726] (II) intel(0): Output VGA1 has no monitor section
[    29.727] (II) intel(0): Output HDMI1 has no monitor section
[    29.776] (II) intel(0): Output DP1 has no monitor section
[    29.776] (II) intel(0): EDID for output LVDS1
[    29.776] (II) intel(0): Manufacturer: LGD  Model: 34b  Serial#: 0
[    29.776] (II) intel(0): Year: 2011  Week: 0
[    29.776] (II) intel(0): EDID Version: 1.3
[    29.776] (II) intel(0): Digital Display Input
[    29.776] (II) intel(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    29.776] (II) intel(0): Gamma: 2.20
[    29.776] (II) intel(0): No DPMS capabilities specified
[    29.776] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    29.776] (II) intel(0): First detailed timing is preferred mode
[    29.776] (II) intel(0): redX: 0.587 redY: 0.349   greenX: 0.336 greenY: 0.563
[    29.776] (II) intel(0): blueX: 0.157 blueY: 0.120   whiteX: 0.313 whiteY: 0.329
[    29.776] (II) intel(0): Manufacturer's mask: 0
[    29.776] (II) intel(0): Supported detailed timing:
[    29.776] (II) intel(0): clock: 69.3 MHz   Image Size:  345 x 194 mm
[    29.776] (II) intel(0): h_active: 1366  h_sync: 1398  h_sync_end 1430 h_blank_end 1470 h_border: 0
[    29.776] (II) intel(0): v_active: 768  v_sync: 773  v_sync_end 776 v_blanking: 786 v_border: 0
[    29.776] (II) intel(0):  LG Display
[    29.776] (II) intel(0):  LP156WH3-TLE1
[    29.776] (II) intel(0): EDID (in hex):
[    29.776] (II) intel(0):     00ffffffffffff0030e44b0300000000
[    29.776] (II) intel(0):     00150103802313780a51759659569028
[    29.776] (II) intel(0):     1e505400000001010101010101010101
[    29.776] (II) intel(0):     010101010101121b5668500012302020
[    29.776] (II) intel(0):     530059c2100000190000000000000000
[    29.776] (II) intel(0):     00000000000000000000000000fe004c
[    29.776] (II) intel(0):     4720446973706c61790a2020000000fe
[    29.776] (II) intel(0):     004c503135365748332d544c4531004e
[    29.776] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    29.776] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    29.776] (II) intel(0): Printing probed modes for output LVDS1
[    29.776] (II) intel(0): Modeline "1366x768"x60.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[    29.776] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    29.776] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    29.776] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    29.776] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    29.776] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    29.776] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    29.776] (II) intel(0): EDID for output VGA1
[    29.777] (II) intel(0): EDID for output HDMI1
[    29.824] (II) intel(0): EDID for output DP1
[    29.824] (II) intel(0): Output LVDS1 connected
[    29.824] (II) intel(0): Output VGA1 disconnected
[    29.824] (II) intel(0): Output HDMI1 disconnected
[    29.824] (II) intel(0): Output DP1 disconnected
[    29.824] (II) intel(0): Using exact sizes for initial modes
[    29.824] (II) intel(0): Output LVDS1 using initial mode 1366x768
[    29.824] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    29.824] (==) intel(0): DPI set to (96, 96)
[    29.824] (II) Loading sub module "dri2"
[    29.824] (II) LoadModule: "dri2"
[    29.824] (II) Module "dri2" already built-in
[    29.824] (II) UnloadModule: "vesa"
[    29.824] (II) Unloading vesa
[    29.824] (II) UnloadModule: "modesetting"
[    29.824] (II) Unloading modesetting
[    29.824] (II) UnloadModule: "fbdev"
[    29.824] (II) Unloading fbdev
[    29.824] (II) UnloadSubModule: "fbdevhw"
[    29.824] (II) Unloading fbdevhw
[    29.824] (==) Depth 24 pixmap format is 32 bpp
[    29.824] (II) intel(0): SNA initialized with IvyBridge backend
[    29.824] (==) intel(0): Backing store disabled
[    29.824] (==) intel(0): Silken mouse enabled
[    29.824] (II) intel(0): HW Cursor enabled
[    29.824] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    29.825] (==) intel(0): DPMS enabled
[    29.825] (II) intel(0): [DRI2] Setup complete
[    29.825] (II) intel(0): [DRI2]   DRI driver: i965
[    29.825] (II) intel(0): direct rendering: DRI2 Enabled
[    29.825] (==) intel(0): hotplug detection: "enabled"
[    29.826] (--) RandR disabled
[    29.828] (II) SELinux: Disabled on system
[    29.853] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[    29.853] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[    29.864] (II) intel(0): Setting screen physical size to 361 x 203
[    29.868] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.881] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    29.881] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.881] (II) LoadModule: "evdev"
[    29.899] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.907] (II) Module evdev: vendor="X.Org Foundation"
[    29.908]     compiled for 1.13.3, module version = 2.7.3
[    29.908]     Module class: X.Org XInput Driver
[    29.908]     ABI class: X.Org XInput driver, version 18.0
[    29.908] (II) Using input driver 'evdev' for 'Power Button'
[    29.908] (**) Power Button: always reports core events
[    29.908] (**) evdev: Power Button: Device: "/dev/input/event3"
[    29.908] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.908] (--) evdev: Power Button: Found keys
[    29.908] (II) evdev: Power Button: Configuring as keyboard
[    29.908] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    29.908] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.908] (**) Option "xkb_rules" "evdev"
[    29.908] (**) Option "xkb_model" "pc105"
[    29.908] (**) Option "xkb_layout" "us"
[    29.908] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[    29.908] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.908] (II) Using input driver 'evdev' for 'Video Bus'
[    29.908] (**) Video Bus: always reports core events
[    29.908] (**) evdev: Video Bus: Device: "/dev/input/event9"
[    29.908] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    29.908] (--) evdev: Video Bus: Found keys
[    29.908] (II) evdev: Video Bus: Configuring as keyboard
[    29.908] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input9/event9"
[    29.908] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    29.908] (**) Option "xkb_rules" "evdev"
[    29.908] (**) Option "xkb_model" "pc105"
[    29.908] (**) Option "xkb_layout" "us"
[    29.908] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.908] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.908] (II) Using input driver 'evdev' for 'Power Button'
[    29.908] (**) Power Button: always reports core events
[    29.908] (**) evdev: Power Button: Device: "/dev/input/event0"
[    29.908] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.908] (--) evdev: Power Button: Found keys
[    29.908] (II) evdev: Power Button: Configuring as keyboard
[    29.908] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0C:00/input/input0/event0"
[    29.908] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    29.908] (**) Option "xkb_rules" "evdev"
[    29.908] (**) Option "xkb_model" "pc105"
[    29.908] (**) Option "xkb_layout" "us"
[    29.909] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    29.909] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    29.909] (II) Using input driver 'evdev' for 'Sleep Button'
[    29.909] (**) Sleep Button: always reports core events
[    29.909] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    29.909] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    29.909] (--) evdev: Sleep Button: Found keys
[    29.909] (II) evdev: Sleep Button: Configuring as keyboard
[    29.909] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0E:00/input/input1/event1"
[    29.909] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    29.909] (**) Option "xkb_rules" "evdev"
[    29.909] (**) Option "xkb_model" "pc105"
[    29.909] (**) Option "xkb_layout" "us"
[    29.909] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[    29.909] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.909] (II) Using input driver 'evdev' for 'Video Bus'
[    29.909] (**) Video Bus: always reports core events
[    29.909] (**) evdev: Video Bus: Device: "/dev/input/event8"
[    29.909] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    29.909] (--) evdev: Video Bus: Found keys
[    29.909] (II) evdev: Video Bus: Configuring as keyboard
[    29.909] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:34/LNXVIDEO:00/input/input8/event8"
[    29.909] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 10)
[    29.909] (**) Option "xkb_rules" "evdev"
[    29.909] (**) Option "xkb_model" "pc105"
[    29.909] (**) Option "xkb_layout" "us"
[    29.909] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    29.909] (II) No input driver specified, ignoring this device.
[    29.909] (II) This device may have been added with another device file.
[    29.909] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    29.909] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    29.910] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event10)
[    29.910] (II) No input driver specified, ignoring this device.
[    29.910] (II) This device may have been added with another device file.
[    29.910] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event11)
[    29.910] (II) No input driver specified, ignoring this device.
[    29.910] (II) This device may have been added with another device file.
[    29.910] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event12)
[    29.910] (II) No input driver specified, ignoring this device.
[    29.910] (II) This device may have been added with another device file.
[    29.910] (II) config/udev: Adding input device Lenovo EasyCamera (/dev/input/event6)
[    29.910] (**) Lenovo EasyCamera: Applying InputClass "evdev keyboard catchall"
[    29.910] (II) Using input driver 'evdev' for 'Lenovo EasyCamera'
[    29.910] (**) Lenovo EasyCamera: always reports core events
[    29.910] (**) evdev: Lenovo EasyCamera: Device: "/dev/input/event6"
[    29.910] (--) evdev: Lenovo EasyCamera: Vendor 0x4f2 Product 0xb2e1
[    29.910] (--) evdev: Lenovo EasyCamera: Found keys
[    29.910] (II) evdev: Lenovo EasyCamera: Configuring as keyboard
[    29.910] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input6/event6"
[    29.910] (II) XINPUT: Adding extended input device "Lenovo EasyCamera" (type: KEYBOARD, id 11)
[    29.910] (**) Option "xkb_rules" "evdev"
[    29.910] (**) Option "xkb_model" "pc105"
[    29.910] (**) Option "xkb_layout" "us"
[    29.910] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    29.910] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.910] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.910] (**) AT Translated Set 2 keyboard: always reports core events
[    29.910] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    29.910] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.910] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.910] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.910] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    29.910] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    29.910] (**) Option "xkb_rules" "evdev"
[    29.910] (**) Option "xkb_model" "pc105"
[    29.910] (**) Option "xkb_layout" "us"
[    29.910] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    29.910] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    29.910] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    29.910] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    29.910] (II) LoadModule: "synaptics"
[    29.911] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.911] (II) Module synaptics: vendor="X.Org Foundation"
[    29.911]     compiled for 1.13.1.901, module version = 1.6.2
[    29.911]     Module class: X.Org XInput Driver
[    29.911]     ABI class: X.Org XInput driver, version 18.0
[    29.911] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    29.911] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.911] (**) Option "Device" "/dev/input/event7"
[    29.911] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    29.911] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5664
[    29.911] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4682
[    29.911] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    29.911] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    29.911] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    29.911] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    29.911] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    29.911] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.911] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.911] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    29.911] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    29.911] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    29.911] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    29.911] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.038
[    29.911] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    29.911] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    29.911] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    29.911] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    29.911] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    29.911] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    29.911] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    29.912] (II) config/udev: Adding input device Ideapad extra buttons (/dev/input/event5)
[    29.912] (**) Ideapad extra buttons: Applying InputClass "evdev keyboard catchall"
[    29.912] (II) Using input driver 'evdev' for 'Ideapad extra buttons'
[    29.912] (**) Ideapad extra buttons: always reports core events
[    29.912] (**) evdev: Ideapad extra buttons: Device: "/dev/input/event5"
[    29.912] (--) evdev: Ideapad extra buttons: Vendor 0 Product 0
[    29.912] (--) evdev: Ideapad extra buttons: Found keys
[    29.912] (II) evdev: Ideapad extra buttons: Configuring as keyboard
[    29.912] (**) Option "config_info" "udev:/sys/devices/platform/ideapad/input/input5/event5"
[    29.912] (II) XINPUT: Adding extended input device "Ideapad extra buttons" (type: KEYBOARD, id 14)
[    29.912] (**) Option "xkb_rules" "evdev"
[    29.912] (**) Option "xkb_model" "pc105"
[    29.912] (**) Option "xkb_layout" "us"
[    31.705] (II) intel(0): EDID vendor "LGD", prod id 843
[    31.705] (II) intel(0): Printing DDC gathered Modelines:
[    31.705] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[    34.174] (II) intel(0): EDID vendor "LGD", prod id 843
[    34.174] (II) intel(0): Printing DDC gathered Modelines:
[    34.174] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[    42.818] (II) intel(0): EDID vendor "LGD", prod id 843
[    42.818] (II) intel(0): Printing DDC gathered Modelines:
[    42.818] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[    43.390] (II) intel(0): EDID vendor "LGD", prod id 843
[    43.390] (II) intel(0): Printing DDC gathered Modelines:
[    43.390] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[    44.358] (II) intel(0): EDID vendor "LGD", prod id 843
[    44.358] (II) intel(0): Printing DDC gathered Modelines:
[    44.358] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[    64.895] (II) intel(0): EDID vendor "LGD", prod id 843
[    64.895] (II) intel(0): Printing DDC gathered Modelines:
[    64.895] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[   694.664] (II) PM Event received: Capability Changed
[   694.680] (II) intel(0): EDID vendor "LGD", prod id 843
[   694.680] (II) intel(0): Printing DDC gathered Modelines:
[   694.680] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[   694.772] (II) intel(0): EDID vendor "LGD", prod id 843
[   694.772] (II) intel(0): Printing DDC gathered Modelines:
[   694.772] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[   695.300] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[   698.586] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[   703.424] (II) Open ACPI successful (/var/run/acpid.socket)
[   703.425] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[   703.440] (II) intel(0): EDID vendor "LGD", prod id 843
[   703.440] (II) intel(0): Printing DDC gathered Modelines:
[   703.440] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[   703.505] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   704.623] (II) intel(0): EDID vendor "LGD", prod id 843
[   704.623] (II) intel(0): Printing DDC gathered Modelines:
[   704.623] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[   739.852] (II) PM Event received: Capability Changed
[   739.870] (II) intel(0): EDID vendor "LGD", prod id 843
[   739.870] (II) intel(0): Printing DDC gathered Modelines:
[   739.870] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[   739.923] (II) intel(0): EDID vendor "LGD", prod id 843
[   739.923] (II) intel(0): Printing DDC gathered Modelines:
[   739.923] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[   740.451] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[   742.146] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[   747.017] (II) Open ACPI successful (/var/run/acpid.socket)
[   747.017] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[   747.033] (II) intel(0): EDID vendor "LGD", prod id 843
[   747.033] (II) intel(0): Printing DDC gathered Modelines:
[   747.033] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[   747.097] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[   747.962] (II) intel(0): EDID vendor "LGD", prod id 843
[   747.962] (II) intel(0): Printing DDC gathered Modelines:
[   747.962] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[  1217.696] (II) intel(0): EDID vendor "LGD", prod id 843
[  1217.696] (II) intel(0): Printing DDC gathered Modelines:
[  1217.696] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[  1409.763] (II) PM Event received: Capability Changed
[  1409.779] (II) intel(0): EDID vendor "LGD", prod id 843
[  1409.779] (II) intel(0): Printing DDC gathered Modelines:
[  1409.779] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[  1409.831] (II) intel(0): EDID vendor "LGD", prod id 843
[  1409.831] (II) intel(0): Printing DDC gathered Modelines:
[  1409.831] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[  1410.363] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  1412.026] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  1417.008] (II) Open ACPI successful (/var/run/acpid.socket)
[  1417.009] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  1417.024] (II) intel(0): EDID vendor "LGD", prod id 843
[  1417.024] (II) intel(0): Printing DDC gathered Modelines:
[  1417.024] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[  1417.089] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1418.249] (II) intel(0): EDID vendor "LGD", prod id 843
[  1418.249] (II) intel(0): Printing DDC gathered Modelines:
[  1418.249] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[  1499.867] (II) PM Event received: Capability Changed
[  1499.883] (II) intel(0): EDID vendor "LGD", prod id 843
[  1499.884] (II) intel(0): Printing DDC gathered Modelines:
[  1499.884] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[  1499.934] (II) intel(0): EDID vendor "LGD", prod id 843
[  1499.934] (II) intel(0): Printing DDC gathered Modelines:
[  1499.934] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[  1500.467] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  1502.301] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  1507.084] (II) Open ACPI successful (/var/run/acpid.socket)
[  1507.084] (II) intel(0): switch to mode 1366x768 on crtc 3 (pipe 0)
[  1507.100] (II) intel(0): EDID vendor "LGD", prod id 843
[  1507.100] (II) intel(0): Printing DDC gathered Modelines:
[  1507.100] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)
[  1507.166] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1508.195] (II) intel(0): EDID vendor "LGD", prod id 843
[  1508.195] (II) intel(0): Printing DDC gathered Modelines:
[  1508.195] (II) intel(0): Modeline "1366x768"x0.0   69.30  1366 1398 1430 1470  768 773 776 786 -hsync -vsync (47.1 kHz eP)

---

### Post by MAFoElffen on 2013-04-28
Please post the results of:
```

lspci -vnn | grep -i VGA

```
Reason? 1st post you said you had previously loaded driver nvidia-current and it didn't work out for you... and needed to uninstall it. That would lead me to assume that you knew what Video GPU you had- an nVidia. Yet your Xorg log said it found an Intel GPU... leading me to believe that either you have an optimus (hybrid-graphic's) with both Intel and NVidia switch graphics or that you have at least one Intel GPU.  

That command will ID all GPU's in your system. 

If both, it is currently swithed to the low graphics Intel chip. If, then install the bumblebee package to deal with switched graphics systems.

If not... in fact either way, if you use the intel GPU... you have to use a kernel earlier than 3.5.2 because of an Intel source bug in the drivers from Intel. This is an upstream "Intel Corp" problem from the source they released that affected all it's Linux graphics drivers... Not just Ubuntu. The Edgers ppa has a driver for them that works (sort-of), but it is still in testing and yet unstable.

---

### Post by alansandbucket on 2013-04-29
here are the results
00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 630M] [10de:0de9] (rev a1) (prog-if 00 [VGA controller])

---

