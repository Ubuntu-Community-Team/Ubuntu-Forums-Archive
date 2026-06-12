---
title: "Upgrade 16.0.4.3 LTS and xorg settings are gone..."
date: 2017-11-02
forum: Installation &amp; Upgrades
---

### Post by rs-irrgang-u on 2017-11-02
Today I've upgrade my Ubuntu Mate 16.04.03 LTS and after, my NVidia / xorg settings are gone.
I have a GTX 670 card with 3 monitor that worked fine (with native resolutions) before this upgrade!
I've cleaned / purged all driver and reinstalled, but nothing will help. Even with **ubuntu-drivers autoinstall** it will not work!
Strange is that the /etc/X11/xorg.conf is removed always after system start, even after backcopy the backup! WTF?

This are information of my system!

**Installed driver...**
```
root@linux-pc:~# apt-isearch nvidiaii  nvidia-384            384.90-0ubuntu0 amd64           NVIDIA binary driver - version 384.90
ii  nvidia-opencl-icd-384 384.90-0ubuntu0 amd64           NVIDIA OpenCL ICD
ii  nvidia-settings       361.42-0ubuntu1 amd64           Tool for configuring the NVIDIA graphics driver


root@linux-pc:~# apt-isearch xserver-xorg-video
ii  xserver-xorg-video-al 1:7.7+13ubuntu3 amd64           X.Org X server -- output driver metapackage
ii  xserver-xorg-video-am 1.1.2-0ubuntu0. amd64           X.Org X server -- AMDGPU display driver
ii  xserver-xorg-video-at 1:7.7.0-1       amd64           X.Org X server -- AMD/ATI display driver wrappe
ii  xserver-xorg-video-fb 1:0.4.4-1build5 amd64           X.Org X server -- fbdev display driver
ii  xserver-xorg-video-in 2:2.99.917+git2 amd64           X.Org X server -- Intel i8xx, i9xx display driv
ii  xserver-xorg-video-no 1:1.0.12-1build amd64           X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-qx 0.1.4-3ubuntu3  amd64           X.Org X server -- QXL display driver
ii  xserver-xorg-video-ra 1:7.7.0-1       amd64           X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-ve 1:2.3.4-1build2 amd64           X.Org X server -- VESA display driver
ii  xserver-xorg-video-vm 1:13.1.0-2ubunt amd64           X.Org X server -- VMware display driver
```

**Loaded nvidia modules...**
```
root@linux-pc:~# lsmod | grep nvidianvidia_drm             49152  0

nvidia_modeset        843776  1 nvidia_drm

nvidia              13008896  1 nvidia_modeset

drm_kms_helper        155648  1 nvidia_drm

drm                   364544  3 drm_kms_helper,nvidia_drm
```

**lspci output for VGA...**
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [GeForce GTX 670] [10de:1189] (rev a1)    Subsystem: CardExpert Technology GK104 [GeForce GTX 670] [10b0:1189]

    Kernel driver in use: nvidia
```

**xrandr output...**
```
Screen 0: minimum 1280 x 1024, current 1280 x 1024, maximum 1280 x 1024default connected 1280x1024+0+0 0mm x 0mm

   1280x1024     77.00*
```

**Xorg.0.log... **(there is no xorg.conf, because it is removed automaticly on system start!!!)
```
[    42.178] X.Org X Server 1.18.4
Release Date: 2016-07-19
[    42.178] X Protocol Version 11, Revision 0
[    42.178] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[    42.178] Current Operating System: Linux linux-pc 4.4.0-98-generic #121-Ubuntu SMP Tue Oct 10 14:24:03 UTC 2017 x86_64
[    42.178] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-98-generic root=UUID=17978903-28f8-4f6a-9730-202a0ffb4a9d ro quiet splash vt.handoff=7
[    42.178] Build Date: 13 October 2017  01:57:05PM
[    42.178] xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support) 
[    42.178] Current version of pixman: 0.33.6
[    42.178]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    42.178] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    42.178] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  2 20:43:42 2017
[    42.267] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    42.296] (==) No Layout section.  Using the first Screen section.
[    42.296] (==) No screen section available. Using defaults.
[    42.296] (**) |-->Screen "Default Screen Section" (0)
[    42.296] (**) |   |-->Monitor "<default monitor>"
[    42.361] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    42.361] (==) Automatically adding devices
[    42.361] (==) Automatically enabling devices
[    42.361] (==) Automatically adding GPU devices
[    42.361] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    42.361] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    42.361]     Entry deleted from font path.
[    42.361] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    42.361]     Entry deleted from font path.
[    42.361] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    42.361]     Entry deleted from font path.
[    42.361] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    42.361]     Entry deleted from font path.
[    42.361] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    42.361]     Entry deleted from font path.
[    42.361] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    42.361] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    42.361] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    42.361] (II) Loader magic: 0x55cf3cc92dc0
[    42.361] (II) Module ABI versions:
[    42.361]     X.Org ANSI C Emulation: 0.4
[    42.361]     X.Org Video Driver: 20.0
[    42.361]     X.Org XInput driver : 22.1
[    42.361]     X.Org Server Extension : 9.0
[    42.362] (++) using VT number 7


[    42.362] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    42.362] (II) xfree86: Adding drm device (/dev/dri/card0)
[    42.362] (--) PCI:*(0:1:0:0) 10de:1189:10b0:1189 rev 161, Mem @ 0xf2000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    42.362] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    42.362] (II) "glx" will be loaded by default.
[    42.362] (II) LoadModule: "glx"
[    42.382] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    42.582] (II) Module glx: vendor="X.Org Foundation"
[    42.582]     compiled for 1.18.4, module version = 1.0.0
[    42.582]     ABI class: X.Org Server Extension, version 9.0
[    42.582] (==) AIGLX enabled
[    42.582] (==) Matched nvidia as autoconfigured driver 0
[    42.582] (==) Matched nouveau as autoconfigured driver 1
[    42.582] (==) Matched nvidia as autoconfigured driver 2
[    42.582] (==) Matched nouveau as autoconfigured driver 3
[    42.582] (==) Matched modesetting as autoconfigured driver 4
[    42.582] (==) Matched fbdev as autoconfigured driver 5
[    42.582] (==) Matched vesa as autoconfigured driver 6
[    42.582] (==) Assigned the driver to the xf86ConfigLayout
[    42.582] (II) LoadModule: "nvidia"
[    42.582] (WW) Warning, couldn't open module nvidia
[    42.582] (II) UnloadModule: "nvidia"
[    42.582] (II) Unloading nvidia
[    42.582] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    42.582] (II) LoadModule: "nouveau"
[    42.582] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    42.623] (II) Module nouveau: vendor="X.Org Foundation"
[    42.623]     compiled for 1.18.1, module version = 1.0.12
[    42.623]     Module class: X.Org Video Driver
[    42.623]     ABI class: X.Org Video Driver, version 20.0
[    42.623] (II) LoadModule: "modesetting"
[    42.624] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    42.624] (II) Module modesetting: vendor="X.Org Foundation"
[    42.624]     compiled for 1.18.4, module version = 1.18.4
[    42.624]     Module class: X.Org Video Driver
[    42.624]     ABI class: X.Org Video Driver, version 20.0
[    42.624] (II) LoadModule: "fbdev"
[    42.624] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    42.624] (II) Module fbdev: vendor="X.Org Foundation"
[    42.624]     compiled for 1.18.1, module version = 0.4.4
[    42.624]     Module class: X.Org Video Driver
[    42.624]     ABI class: X.Org Video Driver, version 20.0
[    42.624] (II) LoadModule: "vesa"
[    42.624] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    42.624] (II) Module vesa: vendor="X.Org Foundation"
[    42.624]     compiled for 1.18.1, module version = 2.3.4
[    42.624]     Module class: X.Org Video Driver
[    42.624]     ABI class: X.Org Video Driver, version 20.0
[    42.624] (==) Matched nvidia as autoconfigured driver 0
[    42.624] (==) Matched nouveau as autoconfigured driver 1
[    42.624] (==) Matched nvidia as autoconfigured driver 2
[    42.624] (==) Matched nouveau as autoconfigured driver 3
[    42.624] (==) Matched modesetting as autoconfigured driver 4
[    42.624] (==) Matched fbdev as autoconfigured driver 5
[    42.624] (==) Matched vesa as autoconfigured driver 6
[    42.624] (==) Assigned the driver to the xf86ConfigLayout
[    42.624] (II) LoadModule: "nvidia"
[    42.624] (WW) Warning, couldn't open module nvidia
[    42.624] (II) UnloadModule: "nvidia"
[    42.624] (II) Unloading nvidia
[    42.624] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    42.624] (II) LoadModule: "nouveau"
[    42.624] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    42.624] (II) Module nouveau: vendor="X.Org Foundation"
[    42.624]     compiled for 1.18.1, module version = 1.0.12
[    42.624]     Module class: X.Org Video Driver
[    42.624]     ABI class: X.Org Video Driver, version 20.0
[    42.624] (II) UnloadModule: "nouveau"
[    42.624] (II) Unloading nouveau
[    42.624] (II) Failed to load module "nouveau" (already loaded, 0)
[    42.624] (II) LoadModule: "modesetting"
[    42.624] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    42.624] (II) Module modesetting: vendor="X.Org Foundation"
[    42.624]     compiled for 1.18.4, module version = 1.18.4
[    42.624]     Module class: X.Org Video Driver
[    42.624]     ABI class: X.Org Video Driver, version 20.0
[    42.624] (II) UnloadModule: "modesetting"
[    42.624] (II) Unloading modesetting
[    42.624] (II) Failed to load module "modesetting" (already loaded, 0)
[    42.624] (II) LoadModule: "fbdev"
[    42.624] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    42.624] (II) Module fbdev: vendor="X.Org Foundation"
[    42.624]     compiled for 1.18.1, module version = 0.4.4
[    42.624]     Module class: X.Org Video Driver
[    42.624]     ABI class: X.Org Video Driver, version 20.0
[    42.624] (II) UnloadModule: "fbdev"
[    42.624] (II) Unloading fbdev
[    42.624] (II) Failed to load module "fbdev" (already loaded, 0)
[    42.624] (II) LoadModule: "vesa"
[    42.624] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    42.624] (II) Module vesa: vendor="X.Org Foundation"
[    42.624]     compiled for 1.18.1, module version = 2.3.4
[    42.624]     Module class: X.Org Video Driver
[    42.624]     ABI class: X.Org Video Driver, version 20.0
[    42.624] (II) UnloadModule: "vesa"
[    42.624] (II) Unloading vesa
[    42.624] (II) Failed to load module "vesa" (already loaded, 0)
[    42.624] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    42.624] (II) NOUVEAU driver for NVIDIA chipset families :
[    42.624]     RIVA TNT        (NV04)
[    42.624]     RIVA TNT2       (NV05)
[    42.624]     GeForce 256     (NV10)
[    42.624]     GeForce 2       (NV11, NV15)
[    42.624]     GeForce 4MX     (NV17, NV18)
[    42.624]     GeForce 3       (NV20)
[    42.624]     GeForce 4Ti     (NV25, NV28)
[    42.624]     GeForce FX      (NV3x)
[    42.624]     GeForce 6       (NV4x)
[    42.624]     GeForce 7       (G7x)
[    42.624]     GeForce 8       (G8x)
[    42.624]     GeForce GTX 200 (NVA0)
[    42.624]     GeForce GTX 400 (NVC0)
[    42.624] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    42.624] (II) FBDEV: driver for framebuffer: fbdev
[    42.624] (II) VESA: driver for VESA chipsets: vesa
[    42.625] (EE) [drm] Failed to open DRM device for (null): -22
[    42.625] (EE) [drm] Failed to open DRM device for (null): -22
[    42.625] (EE) [drm] Failed to open DRM device for (null): -22
[    42.625] (EE) [drm] Failed to open DRM device for (null): -22
[    42.625] (EE) [drm] Failed to open DRM device for (null): -22
[    42.625] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -22
[    42.625] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -22
[    42.625] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -22
[    42.625] (EE) [drm] Failed to open DRM device for pci:0000:01:00.0: -22
[    42.625] (WW) Falling back to old probe method for modesetting
[    42.625] (II) Loading sub module "fbdevhw"
[    42.625] (II) LoadModule: "fbdevhw"
[    42.625] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    42.625] (II) Module fbdevhw: vendor="X.Org Foundation"
[    42.625]     compiled for 1.18.4, module version = 0.0.2
[    42.625]     ABI class: X.Org Video Driver, version 20.0
[    42.625] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[    42.625] (II) FBDEV(2): using default device
[    42.625] (WW) Falling back to old probe method for vesa
[    42.625] (EE) Screen 0 deleted because of no matching config section.
[    42.625] (II) UnloadModule: "modesetting"
[    42.625] (EE) Screen 0 deleted because of no matching config section.
[    42.625] (II) UnloadModule: "modesetting"
[    42.625] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    42.625] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    42.625] (==) FBDEV(0): RGB weight 888
[    42.625] (==) FBDEV(0): Default visual is TrueColor
[    42.625] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    42.625] (II) FBDEV(0): hardware: VESA VGA (video memory: 5120kB)
[    42.625] (II) FBDEV(0): checking modes against framebuffer device...
[    42.625] (II) FBDEV(0): checking modes against monitor...
[    42.625] (--) FBDEV(0): Virtual size is 1280x1024 (pitch 1280)
[    42.625] (**) FBDEV(0):  Built-in mode "current": 131.1 MHz, 80.3 kHz, 76.6 Hz
[    42.625] (II) FBDEV(0): Modeline "current"x0.0  131.09  1280 1312 1472 1632  1024 1028 1032 1048 -hsync -vsync -csync (80.3 kHz b)
[    42.625] (==) FBDEV(0): DPI set to (96, 96)
[    42.625] (II) Loading sub module "fb"
[    42.625] (II) LoadModule: "fb"
[    42.625] (II) Loading /usr/lib/xorg/modules/libfb.so
[    42.653] (II) Module fb: vendor="X.Org Foundation"
[    42.653]     compiled for 1.18.4, module version = 1.0.0
[    42.653]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.653] (**) FBDEV(0): using shadow framebuffer
[    42.653] (II) Loading sub module "shadow"
[    42.653] (II) LoadModule: "shadow"
[    42.654] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    42.654] (II) Module shadow: vendor="X.Org Foundation"
[    42.654]     compiled for 1.18.4, module version = 1.1.0
[    42.654]     ABI class: X.Org ANSI C Emulation, version 0.4
[    42.654] (II) UnloadModule: "vesa"
[    42.654] (II) Unloading vesa
[    42.654] (==) Depth 24 pixmap format is 32 bpp
[    42.654] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
[    42.851] (==) FBDEV(0): Backing store enabled
[    42.975] (==) FBDEV(0): DPMS enabled
[    43.112] (==) RandR enabled
[    43.214] (II) SELinux: Disabled on system
[    43.243] (II) AIGLX: Screen 0 is not DRI2 capable
[    43.243] (EE) AIGLX: reverting to software rendering
[    44.949] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    44.949] (II) AIGLX: Loaded and initialized swrast
[    44.949] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    45.010] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    45.010] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    45.010] (II) LoadModule: "evdev"
[    45.010] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    45.030] (II) Module evdev: vendor="X.Org Foundation"
[    45.030]     compiled for 1.18.1, module version = 2.10.1
[    45.030]     Module class: X.Org XInput Driver
[    45.030]     ABI class: X.Org XInput driver, version 22.1
[    45.030] (II) Using input driver 'evdev' for 'Power Button'
[    45.030] (**) Power Button: always reports core events
[    45.030] (**) evdev: Power Button: Device: "/dev/input/event1"
[    45.030] (--) evdev: Power Button: Vendor 0 Product 0x1
[    45.030] (--) evdev: Power Button: Found keys
[    45.030] (II) evdev: Power Button: Configuring as keyboard
[    45.030] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    45.030] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    45.030] (**) Option "xkb_rules" "evdev"
[    45.030] (**) Option "xkb_model" "pc105"
[    45.030] (**) Option "xkb_layout" "de"
[    45.040] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    45.040] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    45.040] (II) Using input driver 'evdev' for 'Power Button'
[    45.040] (**) Power Button: always reports core events
[    45.040] (**) evdev: Power Button: Device: "/dev/input/event0"
[    45.040] (--) evdev: Power Button: Vendor 0 Product 0x1
[    45.040] (--) evdev: Power Button: Found keys
[    45.040] (II) evdev: Power Button: Configuring as keyboard
[    45.040] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    45.040] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    45.040] (**) Option "xkb_rules" "evdev"
[    45.040] (**) Option "xkb_model" "pc105"
[    45.040] (**) Option "xkb_layout" "de"
[    45.041] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event9)
[    45.041] (II) No input driver specified, ignoring this device.
[    45.041] (II) This device may have been added with another device file.
[    45.041] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event10)
[    45.041] (II) No input driver specified, ignoring this device.
[    45.041] (II) This device may have been added with another device file.
[    45.041] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event11)
[    45.041] (II) No input driver specified, ignoring this device.
[    45.041] (II) This device may have been added with another device file.
[    45.041] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event12)
[    45.041] (II) No input driver specified, ignoring this device.
[    45.041] (II) This device may have been added with another device file.
[    45.041] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event2)
[    45.042] (**) A4TECH USB Device: Applying InputClass "evdev keyboard catchall"
[    45.042] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[    45.042] (**) A4TECH USB Device: always reports core events
[    45.042] (**) evdev: A4TECH USB Device: Device: "/dev/input/event2"
[    45.042] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[    45.042] (--) evdev: A4TECH USB Device: Found 1 mouse buttons
[    45.042] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[    45.042] (--) evdev: A4TECH USB Device: Found relative axes
[    45.042] (--) evdev: A4TECH USB Device: Found absolute axes
[    45.042] (--) evdev: A4TECH USB Device: Found absolute multitouch axes
[    45.042] (--) evdev: A4TECH USB Device: Fake MT device detected
[    45.042] (--) evdev: A4TECH USB Device: Found x and y absolute axes
[    45.042] (--) evdev: A4TECH USB Device: Found keys
[    45.042] (II) evdev: A4TECH USB Device: Forcing relative x/y axes to exist.
[    45.042] (II) evdev: A4TECH USB Device: Configuring as mouse
[    45.042] (II) evdev: A4TECH USB Device: Configuring as keyboard
[    45.042] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[    45.042] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[    45.042] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    45.042] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.0/0003:09DA:9090.0001/input/input5/event2"
[    45.042] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: KEYBOARD, id 8)
[    45.042] (**) Option "xkb_rules" "evdev"
[    45.042] (**) Option "xkb_model" "pc105"
[    45.042] (**) Option "xkb_layout" "de"
[    45.042] (II) evdev: A4TECH USB Device: initialized for relative axes.
[    45.042] (WW) evdev: A4TECH USB Device: ignoring absolute axes.
[    45.042] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[    45.042] (**) A4TECH USB Device: (accel) acceleration profile 0
[    45.042] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[    45.042] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[    45.042] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/js0)
[    45.042] (II) No input driver specified, ignoring this device.
[    45.042] (II) This device may have been added with another device file.
[    45.042] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/event3)
[    45.042] (**) A4TECH USB Device: Applying InputClass "evdev pointer catchall"
[    45.042] (II) Using input driver 'evdev' for 'A4TECH USB Device'
[    45.042] (**) A4TECH USB Device: always reports core events
[    45.042] (**) evdev: A4TECH USB Device: Device: "/dev/input/event3"
[    45.096] (--) evdev: A4TECH USB Device: Vendor 0x9da Product 0x9090
[    45.096] (--) evdev: A4TECH USB Device: Found 20 mouse buttons
[    45.096] (--) evdev: A4TECH USB Device: Found scroll wheel(s)
[    45.096] (--) evdev: A4TECH USB Device: Found relative axes
[    45.096] (--) evdev: A4TECH USB Device: Found x and y relative axes
[    45.096] (II) evdev: A4TECH USB Device: Configuring as mouse
[    45.096] (II) evdev: A4TECH USB Device: Adding scrollwheel support
[    45.096] (**) evdev: A4TECH USB Device: YAxisMapping: buttons 4 and 5
[    45.096] (**) evdev: A4TECH USB Device: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    45.096] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-5/3-5:1.1/0003:09DA:9090.0002/input/input6/event3"
[    45.096] (II) XINPUT: Adding extended input device "A4TECH USB Device" (type: MOUSE, id 9)
[    45.096] (II) evdev: A4TECH USB Device: initialized for relative axes.
[    45.096] (**) A4TECH USB Device: (accel) keeping acceleration scheme 1
[    45.096] (**) A4TECH USB Device: (accel) acceleration profile 0
[    45.096] (**) A4TECH USB Device: (accel) acceleration factor: 2.000
[    45.096] (**) A4TECH USB Device: (accel) acceleration threshold: 4
[    45.096] (II) config/udev: Adding input device A4TECH USB Device (/dev/input/mouse0)
[    45.096] (II) No input driver specified, ignoring this device.
[    45.096] (II) This device may have been added with another device file.
[    45.096] (II) config/udev: Adding input device HID 04b4:6014 (/dev/input/event4)
[    45.096] (**) HID 04b4:6014: Applying InputClass "evdev keyboard catchall"
[    45.096] (II) Using input driver 'evdev' for 'HID 04b4:6014'
[    45.096] (**) HID 04b4:6014: always reports core events
[    45.096] (**) evdev: HID 04b4:6014: Device: "/dev/input/event4"
[    45.096] (--) evdev: HID 04b4:6014: Vendor 0x4b4 Product 0x6014
[    45.096] (--) evdev: HID 04b4:6014: Found keys
[    45.096] (II) evdev: HID 04b4:6014: Configuring as keyboard
[    45.096] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.0/0003:04B4:6014.0003/input/input7/event4"
[    45.096] (II) XINPUT: Adding extended input device "HID 04b4:6014" (type: KEYBOARD, id 10)
[    45.096] (**) Option "xkb_rules" "evdev"
[    45.096] (**) Option "xkb_model" "pc105"
[    45.096] (**) Option "xkb_layout" "de"
[    45.097] (II) config/udev: Adding input device HID 04b4:6014 (/dev/input/event5)
[    45.097] (**) HID 04b4:6014: Applying InputClass "evdev pointer catchall"
[    45.097] (**) HID 04b4:6014: Applying InputClass "evdev keyboard catchall"
[    45.097] (II) Using input driver 'evdev' for 'HID 04b4:6014'
[    45.097] (**) HID 04b4:6014: always reports core events
[    45.097] (**) evdev: HID 04b4:6014: Device: "/dev/input/event5"
[    45.097] (--) evdev: HID 04b4:6014: Vendor 0x4b4 Product 0x6014
[    45.097] (--) evdev: HID 04b4:6014: Found 9 mouse buttons
[    45.097] (--) evdev: HID 04b4:6014: Found scroll wheel(s)
[    45.097] (--) evdev: HID 04b4:6014: Found relative axes
[    45.097] (--) evdev: HID 04b4:6014: Found x and y relative axes
[    45.097] (--) evdev: HID 04b4:6014: Found absolute axes
[    45.097] (--) evdev: HID 04b4:6014: Found absolute multitouch axes
[    45.097] (--) evdev: HID 04b4:6014: Fake MT device detected
[    45.097] (--) evdev: HID 04b4:6014: Found keys
[    45.097] (II) evdev: HID 04b4:6014: Configuring as mouse
[    45.097] (II) evdev: HID 04b4:6014: Configuring as keyboard
[    45.097] (II) evdev: HID 04b4:6014: Adding scrollwheel support
[    45.097] (**) evdev: HID 04b4:6014: YAxisMapping: buttons 4 and 5
[    45.097] (**) evdev: HID 04b4:6014: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    45.097] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-6/3-6:1.1/0003:04B4:6014.0004/input/input8/event5"
[    45.097] (II) XINPUT: Adding extended input device "HID 04b4:6014" (type: KEYBOARD, id 11)
[    45.097] (**) Option "xkb_rules" "evdev"
[    45.097] (**) Option "xkb_model" "pc105"
[    45.097] (**) Option "xkb_layout" "de"
[    45.097] (II) evdev: HID 04b4:6014: initialized for relative axes.
[    45.097] (WW) evdev: HID 04b4:6014: ignoring absolute axes.
[    45.097] (**) HID 04b4:6014: (accel) keeping acceleration scheme 1
[    45.097] (**) HID 04b4:6014: (accel) acceleration profile 0
[    45.097] (**) HID 04b4:6014: (accel) acceleration factor: 2.000
[    45.097] (**) HID 04b4:6014: (accel) acceleration threshold: 4
[    45.097] (II) config/udev: Adding input device HID 04b4:6014 (/dev/input/mouse1)
[    45.097] (II) No input driver specified, ignoring this device.
[    45.097] (II) This device may have been added with another device file.
[    45.097] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event7)
[    45.097] (II) No input driver specified, ignoring this device.
[    45.098] (II) This device may have been added with another device file.
[    45.098] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event8)
[    45.098] (II) No input driver specified, ignoring this device.
[    45.098] (II) This device may have been added with another device file.
[    45.098] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event6)
[    45.098] (II) No input driver specified, ignoring this device.
[    45.098] (II) This device may have been added with another device file.

```

So, something is bugged after upgrade ubuntu.
Why is the xorg.conf always removed after system start???

edit says:
And... btw... I can't change any monitor/resolution settings in system monitor settings or nvidia-settings!

---

