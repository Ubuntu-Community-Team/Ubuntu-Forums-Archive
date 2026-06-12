---
title: "Nvidia drivers black screen error. xorg.conf seems okay."
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by Prantu on 2011-09-20
Hi everyone..I am having problems with setiing up Nvidia drivers for Ubuntu Natty on my laptop (Inspiron 15R ). Installation of drivers is successful, but on reboot I am stuck with a black screen after the Ubuntu five dots splashscreen. As a possible solution obtained from various forums, I have made a custom edid file and included it in xorg.conf and also used the BusID option in the device section. This helped me to eliminate all errors in xorg.0.log (like screens not found etc  etc), so that now there are only 2 warnings related to hotplugging and no errors. But still the problem isn't solved. I continue to get the black screen. Please help!
My xorg log file and xorg.conf are as below:

**xorg.0.log :**

> [    24.349] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    24.350] X Protocol Version 11, Revision 0
[    24.350] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    24.350] Current Operating System: Linux Workstation-1 2.6.38-11-generic #50-Ubuntu SMP Mon Sep 12 21:17:25 UTC 2011 x86_64
[    24.350] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=7acae4e2-0128-46cd-98dd-8e6ab13dc1c5 ro quiet splash vt.handoff=7
[    24.350] Build Date: 11 August 2011  03:43:05PM
[    24.350] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    24.350] Current version of pixman: 0.20.2
[    24.350]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    24.350] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.350] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 20 22:05:57 2011
[    24.350] (==) Using config file: "/etc/X11/xorg.conf"
[    24.350] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.579] (==) ServerLayout "Layout0"
[    24.579] (**) |-->Screen "Screen0" (0)
[    24.579] (**) |   |-->Monitor "Monitor0"
[    24.579] (**) |   |-->Device "Device0"
[    24.579] (**) |-->Input Device "Keyboard0"
[    24.579] (**) |-->Input Device "Mouse0"
[    24.579] (==) Automatically adding devices
[    24.579] (==) Automatically enabling devices
[    24.694] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/cyrillic,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    24.694] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.694] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    24.694] (WW) Disabling Keyboard0
[    24.694] (WW) Disabling Mouse0
[    24.694] (II) Loader magic: 0x7e17e0
[    24.694] (II) Module ABI versions:
[    24.694]     X.Org ANSI C Emulation: 0.4
[    24.694]     X.Org Video Driver: 10.0
[    24.694]     X.Org XInput driver : 12.3
[    24.694]     X.Org Server Extension : 5.0
[    24.694] (--) PCI:*(0:0:2:0) 8086:0116:1028:04ca rev 9, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    24.694] (--) PCI: (0:1:0:0) 10de:0df5:1028:04ca rev 161, Mem @ 0xf5000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    24.694] (II) Open ACPI successful (/var/run/acpid.socket)
[    24.694] (II) LoadModule: "extmod"
[    24.709] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    24.709] (II) Module extmod: vendor="X.Org Foundation"
[    24.709]     compiled for 1.10.1, module version = 1.0.0
[    24.709]     Module class: X.Org Server Extension
[    24.709]     ABI class: X.Org Server Extension, version 5.0
[    24.709] (II) Loading extension MIT-SCREEN-SAVER
[    24.709] (II) Loading extension XFree86-VidModeExtension
[    24.709] (II) Loading extension XFree86-DGA
[    24.709] (II) Loading extension DPMS
[    24.709] (II) Loading extension XVideo
[    24.709] (II) Loading extension XVideo-MotionCompensation
[    24.709] (II) Loading extension X-Resource
[    24.709] (II) LoadModule: "dbe"
[    24.709] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    24.710] (II) Module dbe: vendor="X.Org Foundation"
[    24.710]     compiled for 1.10.1, module version = 1.0.0
[    24.710]     Module class: X.Org Server Extension
[    24.710]     ABI class: X.Org Server Extension, version 5.0
[    24.710] (II) Loading extension DOUBLE-BUFFER
[    24.710] (II) LoadModule: "glx"
[    24.710] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.703] (II) Module glx: vendor="NVIDIA Corporation"
[    25.872]     compiled for 4.0.2, module version = 1.0.0
[    25.872]     Module class: X.Org Server Extension
[    25.872] (II) NVIDIA GLX Module  285.03  Mon Aug 15 02:52:52 PDT 2011
[    25.872] (II) Loading extension GLX
[    25.872] (II) LoadModule: "record"
[    25.873] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    25.873] (II) Module record: vendor="X.Org Foundation"
[    25.873]     compiled for 1.10.1, module version = 1.13.0
[    25.873]     Module class: X.Org Server Extension
[    25.873]     ABI class: X.Org Server Extension, version 5.0
[    25.873] (II) Loading extension RECORD
[    25.873] (II) LoadModule: "dri"
[    25.873] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    25.873] (II) Module dri: vendor="X.Org Foundation"
[    25.873]     compiled for 1.10.1, module version = 1.0.0
[    25.873]     ABI class: X.Org Server Extension, version 5.0
[    25.873] (II) Loading extension XFree86-DRI
[    25.873] (II) LoadModule: "dri2"
[    25.873] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    25.873] (II) Module dri2: vendor="X.Org Foundation"
[    25.873]     compiled for 1.10.1, module version = 1.2.0
[    25.873]     ABI class: X.Org Server Extension, version 5.0
[    25.873] (II) Loading extension DRI2
[    25.873] (II) LoadModule: "nvidia"
[    25.873] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    26.471] (II) Module nvidia: vendor="NVIDIA Corporation"
[    26.507]     compiled for 4.0.2, module version = 1.0.0
[    26.507]     Module class: X.Org Video Driver
[    26.643] (II) NVIDIA dlloader X Driver  285.03  Mon Aug 15 02:35:33 PDT 2011
[    26.643] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    26.681] (++) using VT number 7

[    26.735] (II) Loading sub module "fb"
[    26.735] (II) LoadModule: "fb"
[    26.736] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.736] (II) Module fb: vendor="X.Org Foundation"
[    26.736]     compiled for 1.10.1, module version = 1.0.0
[    26.736]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.736] (II) Loading sub module "wfb"
[    26.736] (II) LoadModule: "wfb"
[    26.736] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    26.866] (II) Module wfb: vendor="X.Org Foundation"
[    26.866]     compiled for 1.10.1, module version = 1.0.0
[    26.866]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.866] (II) Loading sub module "ramdac"
[    26.866] (II) LoadModule: "ramdac"
[    26.866] (II) Module "ramdac" already built-in
[    26.920] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[    26.921] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    26.921] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.985] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    26.985] (==) NVIDIA(0): RGB weight 888
[    26.985] (==) NVIDIA(0): Default visual is TrueColor
[    26.985] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    26.985] (**) NVIDIA(0): Option "CustomEDID" "CRT-0:/home/prakriteesh/envi.bin"
[    28.266] (II) NVIDIA(GPU-0): Display (LGD (CRT-0)) does not support NVIDIA 3D Vision
[    28.266] (II) NVIDIA(GPU-0):     stereo.
[    28.268] (II) NVIDIA(0): NVIDIA GPU GeForce GT 525M (GF108) at PCI:1:0:0 (GPU-0)
[    28.268] (--) NVIDIA(0): Memory: 1048576 kBytes
[    28.268] (--) NVIDIA(0): VideoBIOS: 70.08.56.00.0a
[    28.268] (II) NVIDIA(0): Detected PCI Express Link width: 1X
[    28.268] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    28.268] (--) NVIDIA(0): Connected display device(s) on GeForce GT 525M at PCI:1:0:0
[    28.268] (--) NVIDIA(0):     LGD (CRT-0)
[    28.268] (--) NVIDIA(0): LGD (CRT-0): 400.0 MHz maximum pixel clock
[    28.273] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
[    28.273] (**) NVIDIA(0):     enabled on all display devices.
[    28.277] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    28.277] (II) NVIDIA(0): Validated modes:
[    28.277] (II) NVIDIA(0):     "1024x768"
[    28.277] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    28.279] (--) NVIDIA(0): DPI set to (76, 102); computed from "UseEdidDpi" X config
[    28.279] (--) NVIDIA(0):     option
[    28.279] (--) Depth 24 pixmap format is 32 bpp
[    28.279] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[    28.279] (II) NVIDIA:     access.
[    28.285] (II) NVIDIA(0): Setting mode "1024x768"
[    28.409] (II) Loading extension NV-GLX
[    28.470] (==) NVIDIA(0): Disabling shared memory pixmaps
[    28.470] (==) NVIDIA(0): Backing store disabled
[    28.470] (==) NVIDIA(0): Silken mouse enabled
[    28.470] (**) NVIDIA(0): DPMS enabled
[    28.471] (II) Loading extension NV-CONTROL
[    28.471] (II) Loading extension XINERAMA
[    28.471] (II) Loading sub module "dri2"
[    28.471] (II) LoadModule: "dri2"
[    28.471] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    28.471] (II) Module dri2: vendor="X.Org Foundation"
[    28.471]     compiled for 1.10.1, module version = 1.2.0
[    28.471]     ABI class: X.Org Server Extension, version 5.0
[    28.471] (II) NVIDIA(0): [DRI2] Setup complete
[    28.471] (==) RandR enabled
[    28.471] (II) Initializing built-in extension Generic Event Extension
[    28.471] (II) Initializing built-in extension SHAPE
[    28.471] (II) Initializing built-in extension MIT-SHM
[    28.471] (II) Initializing built-in extension XInputExtension
[    28.471] (II) Initializing built-in extension XTEST
[    28.471] (II) Initializing built-in extension BIG-REQUESTS
[    28.471] (II) Initializing built-in extension SYNC
[    28.471] (II) Initializing built-in extension XKEYBOARD
[    28.471] (II) Initializing built-in extension XC-MISC
[    28.471] (II) Initializing built-in extension SECURITY
[    28.471] (II) Initializing built-in extension XINERAMA
[    28.471] (II) Initializing built-in extension XFIXES
[    28.471] (II) Initializing built-in extension RENDER
[    28.471] (II) Initializing built-in extension RANDR
[    28.471] (II) Initializing built-in extension COMPOSITE
[    28.471] (II) Initializing built-in extension DAMAGE
[    28.471] (II) Initializing built-in extension GESTURE
[    28.472] (II) Initializing extension GLX
[    28.663] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    28.669] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    28.669] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.669] (II) LoadModule: "evdev"
[    28.669] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.669] (II) Module evdev: vendor="X.Org Foundation"
[    28.669]     compiled for 1.10.0.902, module version = 2.6.0
[    28.669]     Module class: X.Org XInput Driver
[    28.669]     ABI class: X.Org XInput driver, version 12.3
[    28.669] (II) Using input driver 'evdev' for 'Power Button'
[    28.669] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.669] (**) Power Button: always reports core events
[    28.669] (**) Power Button: Device: "/dev/input/event3"
[    28.669] (--) Power Button: Found keys
[    28.669] (II) Power Button: Configuring as keyboard
[    28.669] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    28.669] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.669] (**) Option "xkb_rules" "evdev"
[    28.669] (**) Option "xkb_model" "pc105"
[    28.669] (**) Option "xkb_layout" "us"
[    28.670] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    28.670] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.670] (II) Using input driver 'evdev' for 'Video Bus'
[    28.670] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.670] (**) Video Bus: always reports core events
[    28.670] (**) Video Bus: Device: "/dev/input/event6"
[    28.670] (--) Video Bus: Found keys
[    28.670] (II) Video Bus: Configuring as keyboard
[    28.670] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6/event6"
[    28.670] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    28.670] (**) Option "xkb_rules" "evdev"
[    28.670] (**) Option "xkb_model" "pc105"
[    28.670] (**) Option "xkb_layout" "us"
[    28.671] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    28.671] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    28.671] (II) Using input driver 'evdev' for 'Video Bus'
[    28.671] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.671] (**) Video Bus: always reports core events
[    28.671] (**) Video Bus: Device: "/dev/input/event5"
[    28.672] (--) Video Bus: Found keys
[    28.672] (II) Video Bus: Configuring as keyboard
[    28.672] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:1b/LNXVIDEO:00/input/input5/event5"
[    28.672] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    28.672] (**) Option "xkb_rules" "evdev"
[    28.672] (**) Option "xkb_model" "pc105"
[    28.672] (**) Option "xkb_layout" "us"
[    28.680] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    28.680] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    28.680] (II) Using input driver 'evdev' for 'Power Button'
[    28.680] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.680] (**) Power Button: always reports core events
[    28.680] (**) Power Button: Device: "/dev/input/event1"
[    28.680] (--) Power Button: Found keys
[    28.680] (II) Power Button: Configuring as keyboard
[    28.680] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    28.680] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    28.680] (**) Option "xkb_rules" "evdev"
[    28.680] (**) Option "xkb_model" "pc105"
[    28.680] (**) Option "xkb_layout" "us"
[    28.681] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    28.681] (II) No input driver/identifier specified (ignoring)
[    28.681] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    28.681] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    28.681] (II) Using input driver 'evdev' for 'Sleep Button'
[    28.681] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.681] (**) Sleep Button: always reports core events
[    28.681] (**) Sleep Button: Device: "/dev/input/event2"
[    28.681] (--) Sleep Button: Found keys
[    28.681] (II) Sleep Button: Configuring as keyboard
[    28.681] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    28.681] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    28.681] (**) Option "xkb_rules" "evdev"
[    28.681] (**) Option "xkb_model" "pc105"
[    28.681] (**) Option "xkb_layout" "us"
[    28.683] (II) config/udev: Adding input device Laptop_Integrated_Webcam_HD (/dev/input/event7)
[    28.683] (**) Laptop_Integrated_Webcam_HD: Applying InputClass "evdev keyboard catchall"
[    28.683] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_HD'
[    28.683] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.683] (**) Laptop_Integrated_Webcam_HD: always reports core events
[    28.683] (**) Laptop_Integrated_Webcam_HD: Device: "/dev/input/event7"
[    28.690] (--) Laptop_Integrated_Webcam_HD: Found keys
[    28.690] (II) Laptop_Integrated_Webcam_HD: Configuring as keyboard
[    28.690] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input7/event7"
[    28.690] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_HD" (type: KEYBOARD)
[    28.690] (**) Option "xkb_rules" "evdev"
[    28.690] (**) Option "xkb_model" "pc105"
[    28.690] (**) Option "xkb_layout" "us"
[    28.690] (II) config/udev: Adding input device HDA Intel PCH Mic at Ext Right Jack (/dev/input/event10)
[    28.690] (II) No input driver/identifier specified (ignoring)
[    28.691] (II) config/udev: Adding input device HDA Intel PCH HP Out at Ext Right Jack (/dev/input/event11)
[    28.691] (II) No input driver/identifier specified (ignoring)
[    28.694] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    28.694] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    28.694] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    28.694] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.694] (**) AT Translated Set 2 keyboard: always reports core events
[    28.694] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    28.694] (--) AT Translated Set 2 keyboard: Found keys
[    28.694] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    28.694] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    28.694] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    28.694] (**) Option "xkb_rules" "evdev"
[    28.694] (**) Option "xkb_model" "pc105"
[    28.694] (**) Option "xkb_layout" "us"
[    28.694] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/event9)
[    28.694] (**) ImPS/2 ALPS GlidePoint: Applying InputClass "evdev pointer catchall"
[    28.694] (II) Using input driver 'evdev' for 'ImPS/2 ALPS GlidePoint'
[    28.694] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.694] (**) ImPS/2 ALPS GlidePoint: always reports core events
[    28.695] (**) ImPS/2 ALPS GlidePoint: Device: "/dev/input/event9"
[    28.700] (--) ImPS/2 ALPS GlidePoint: Found 3 mouse buttons
[    28.700] (--) ImPS/2 ALPS GlidePoint: Found scroll wheel(s)
[    28.700] (--) ImPS/2 ALPS GlidePoint: Found relative axes
[    28.700] (--) ImPS/2 ALPS GlidePoint: Found x and y relative axes
[    28.700] (II) ImPS/2 ALPS GlidePoint: Configuring as mouse
[    28.700] (II) ImPS/2 ALPS GlidePoint: Adding scrollwheel support
[    28.700] (**) ImPS/2 ALPS GlidePoint: YAxisMapping: buttons 4 and 5
[    28.700] (**) ImPS/2 ALPS GlidePoint: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    28.700] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input9/event9"
[    28.700] (II) XINPUT: Adding extended input device "ImPS/2 ALPS GlidePoint" (type: MOUSE)
[    28.700] (II) ImPS/2 ALPS GlidePoint: initialized for relative axes.
[    28.700] (**) ImPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
[    28.700] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration profile 0
[    28.700] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration factor: 2.000
[    28.700] (**) ImPS/2 ALPS GlidePoint: (accel) acceleration threshold: 4
[    28.700] (II) config/udev: Adding input device ImPS/2 ALPS GlidePoint (/dev/input/mouse0)
[    28.700] (II) No input driver/identifier specified (ignoring)
[    28.703] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event8)
[    28.703] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    28.703] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    28.703] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    28.703] (**) Dell WMI hotkeys: always reports core events
[    28.703] (**) Dell WMI hotkeys: Device: "/dev/input/event8"
[    28.703] (--) Dell WMI hotkeys: Found keys
[    28.703] (II) Dell WMI hotkeys: Configuring as keyboard
[    28.703] (**) Option "config_info" "udev:/sys/devices/virtual/input/input8/event8"
[    28.703] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD)
[    28.703] (**) Option "xkb_rules" "evdev"
[    28.703] (**) Option "xkb_model" "pc105"
[    28.703] (**) Option "xkb_layout" "us"
[    82.440] (II) Power Button: Close
[    82.440] (II) UnloadModule: "evdev"
[    82.440] (II) Unloading evdev
[    82.530] (II) Video Bus: Close
[    82.530] (II) UnloadModule: "evdev"
[    82.530] (II) Unloading evdev
[    82.610] (II) Video Bus: Close
[    82.610] (II) UnloadModule: "evdev"
[    82.610] (II) Unloading evdev
[    82.690] (II) Power Button: Close
[    82.690] (II) UnloadModule: "evdev"
[    82.690] (II) Unloading evdev
[    82.790] (II) Sleep Button: Close
[    82.790] (II) UnloadModule: "evdev"
[    82.790] (II) Unloading evdev
[    82.890] (II) Laptop_Integrated_Webcam_HD: Close
[    82.890] (II) UnloadModule: "evdev"
[    82.890] (II) Unloading evdev
[    82.970] (II) AT Translated Set 2 keyboard: Close
[    82.970] (II) UnloadModule: "evdev"
[    82.970] (II) Unloading evdev
[    83.130] (II) ImPS/2 ALPS GlidePoint: Close
[    83.130] (II) UnloadModule: "evdev"
[    83.130] (II) Unloading evdev
[    83.330] (II) Dell WMI hotkeys: Close
[    83.330] (II) UnloadModule: "evdev"
[    83.330] (II) Unloading evdev
[    83.452]  ddxSigGiveUp: Closing log

[B]
xorg.conf :[/B]



> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 285.03  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Mon Aug 15 02:56:50 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
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
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"   
    BusID "PCI:1:0:0"
     Option "CustomEDID" "CRT-0:/home/prakriteesh/envi.bin"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
   Modes "1024x768"
    EndSubSection
EndSection


---

### Post by Henk Poley on 2011-09-21
I'm pretty sure your display is 1366x768. Why are you trying to force it to 1024x768? Also, what is the custom EDID for? Laptop panels are usually bog standard..

Try (re)moving the /etc/xorg.conf altogether.

---

### Post by MAFoElffen on 2011-09-21
> **Henk Poley said:**
> I'm pretty sure your display is 1366x768. Why are you trying to force it to 1024x768? Also, what is the custom EDID for? Laptop panels are usually bog standard..

Try (re)moving the /etc/xorg.conf altogether.
The CRT-0 refered Custom EDID would not take any effect as the Monitor Name is spec'ed as "Monitor0"...

If he removes or renames the xorg.conf--  then he will need to boot with nomodeset... but it be running without the nvidia driver.

Boot on LiveCD and get to a terminal. Post the results of 
```

lspci -nn | grep VGA

``` - Then my next question is if the driver is Ubuntu package or straight from NVidia?
 - What driver is it?
 - Does it start up in Rescue mode?

---

