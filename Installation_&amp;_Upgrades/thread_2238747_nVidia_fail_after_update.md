---
title: "nVidia fail after update"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by madtyn2 on 2014-08-09
I have a 64-bit computer with Ubuntu 14.04, Gnome and nVidia. I had the official drivers from nVidia installed.

I did a reboot after a recent update and the next time I switched on the PC I found that after entering my password, the system hangs.

I tried then CTRL+ALT+F1 and when killing lightdm and doing startx I found this error (look at the screenshot).

I can't understand why this update failed. Can't find anything googling just by looking for the error message. 

[COLOR=#333333][FONT=Helvetica Neue]I got also this log file when making "Xorg -configure". There is an error at the end.

[/FONT][/COLOR]```
[FONT=Consolas] [   315.646] [/FONT] X.Org X Server 1.15.1
 Release Date: 2014-04-13
 [   315.647] X Protocol Version 11, Revision 0
 [   315.647] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
 [   315.647] Current Operating System: Linux martin 3.11.0-20-generic #35-Ubuntu SMP Fri May 2 21:32:49 UTC 2014 x86_64
 [   315.647] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-20-generic root=UUID=2718dd63-0056-4e1d-954b-d3c6d0b31b90 ro recovery nomodeset
 [   315.647] Build Date: 16 April 2014  01:36:29PM
 [   315.648] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
 [   315.648] Current version of pixman: 0.30.2
 [   315.648]   Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
 [   315.648] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
 [   315.649] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Aug 11 20:17:56 2014
 [   315.649] (II) Loader magic: 0x7f3e96be2d60
 [   315.649] (II) Module ABI versions:
 [   315.649]   X.Org ANSI C Emulation: 0.4
 [   315.649]   X.Org Video Driver: 15.0
 [   315.649]   X.Org XInput driver : 20.0
 [   315.649]   X.Org Server Extension : 8.0
 [   315.650] (--) PCI:*(0:1:0:0) 10de:0f00:1458:3544 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
 [   315.650] List of video drivers:
 [   315.651]   ati
 [   315.651]   sisusb
 [   315.651]   savage
 [   315.651]   r128
 [   315.651]   intel
 [   315.651]   mach64
 [   315.652]   radeon
 [   315.652]   modesetting
 [   315.652]   cirrus
 [   315.652]   s3
 [   315.652]   trident
 [   315.653]   openchrome
 [   315.653]   tdfx
 [   315.653]   qxl
 [   315.653]   mga
 [   315.653]   vboxvideo
 [   315.653]   siliconmotion
 [   315.654]   spiceqxl
 [   315.654]   neomagic
 [   315.654]   nvidia
 [   315.654]   sis
 [   315.654]   vesa
 [   315.654]   fbdev
 [   315.654] (II) LoadModule: "ati"
 [   315.655] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
 [   315.660] (II) Module ati: vendor="X.Org Foundation"
 [   315.660]   compiled for 1.15.1, module version = 7.3.0
 [   315.660]   Module class: X.Org Video Driver
 [   315.660]   ABI class: X.Org Video Driver, version 15.0
 [   315.660] (II) LoadModule: "sisusb"
 [   315.660] (II) Loading /usr/lib/xorg/modules/drivers/sisusb_drv.so
 [   315.668] (II) Module sisusb: vendor="X.Org Foundation"
 [   315.668]   compiled for 1.15.0, module version = 0.9.6
 [   315.668]   Module class: X.Org Video Driver
 [   315.668]   ABI class: X.Org Video Driver, version 15.0
 [   315.668] (II) LoadModule: "savage"
 [   315.668] (II) Loading /usr/lib/xorg/modules/drivers/savage_drv.so
 [   315.676] (II) Module savage: vendor="X.Org Foundation"
 [   315.676]   compiled for 1.15.0, module version = 2.3.7
 [   315.676]   Module class: X.Org Video Driver
 [   315.676]   ABI class: X.Org Video Driver, version 15.0
 [   315.676] (II) LoadModule: "r128"
 [   315.676] (II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
 [   315.689] (II) Module r128: vendor="X.Org Foundation"
 [   315.689]   compiled for 1.15.0, module version = 6.9.2
 [   315.689]   Module class: X.Org Video Driver
 [   315.689]   ABI class: X.Org Video Driver, version 15.0
 [   315.689] (II) LoadModule: "intel"
 [   315.689] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
 [   315.734] (II) Module intel: vendor="X.Org Foundation"
 [   315.734]   compiled for 1.15.0, module version = 2.99.910
 [   315.734]   Module class: X.Org Video Driver
 [   315.734]   ABI class: X.Org Video Driver, version 15.0
 [   315.734] (II) LoadModule: "mach64"
 [   315.734] (II) Loading /usr/lib/xorg/modules/drivers/mach64_drv.so
 [   315.748] (II) Module mach64: vendor="X.Org Foundation"
 [   315.748]   compiled for 1.15.0, module version = 6.9.4
 [   315.748]   Module class: X.Org Video Driver
 [   315.748]   ABI class: X.Org Video Driver, version 15.0
 [   315.748] (II) LoadModule: "radeon"
 [   315.748] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
 [   315.788] (II) Module radeon: vendor="X.Org Foundation"
 [   315.788]   compiled for 1.15.1, module version = 7.3.0
 [   315.788]   Module class: X.Org Video Driver
 [   315.788]   ABI class: X.Org Video Driver, version 15.0
 [   315.788] (II) LoadModule: "modesetting"
 [   315.788] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
 [   315.800] (II) Module modesetting: vendor="X.Org Foundation"
 [   315.800]   compiled for 1.15.0, module version = 0.8.1
 [   315.800]   Module class: X.Org Video Driver
 [   315.800]   ABI class: X.Org Video Driver, version 15.0
 [   315.800] (II) LoadModule: "cirrus"
 [   315.801] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
 [   315.806] (II) Module cirrus: vendor="X.Org Foundation"
 [   315.806]   compiled for 1.15.0, module version = 1.5.2
 [   315.806]   Module class: X.Org Video Driver
 [   315.806]   ABI class: X.Org Video Driver, version 15.0
 [   315.806] (II) LoadModule: "s3"
 [   315.806] (II) Loading /usr/lib/xorg/modules/drivers/s3_drv.so
 [   315.808] (II) Module s3: vendor="X.Org Foundation"
 [   315.808]   compiled for 1.15.0, module version = 0.6.5
 [   315.808]   Module class: X.Org Video Driver
 [   315.808]   ABI class: X.Org Video Driver, version 15.0
 [   315.808] (II) LoadModule: "trident"
 [   315.808] (II) Loading /usr/lib/xorg/modules/drivers/trident_drv.so
 [   315.820] (II) Module trident: vendor="X.Org Foundation"
 [   315.820]   compiled for 1.15.0, module version = 1.3.6
 [   315.820]   Module class: X.Org Video Driver
 [   315.820]   ABI class: X.Org Video Driver, version 15.0
 [   315.821] (II) LoadModule: "openchrome"
 [   315.821] (II) Loading /usr/lib/xorg/modules/drivers/openchrome_drv.so
 [   315.832] (II) Module openchrome: vendor="http://openchrome.org/"
 [   315.832]   compiled for 1.15.0, module version = 0.3.3
 [   315.832]   Module class: X.Org Video Driver
 [   315.832]   ABI class: X.Org Video Driver, version 15.0
 [   315.832] (II) LoadModule: "tdfx"
 [   315.833] (II) Loading /usr/lib/xorg/modules/drivers/tdfx_drv.so
 [   315.842] (II) Module tdfx: vendor="X.Org Foundation"
 [   315.842]   compiled for 1.15.0, module version = 1.4.5
 [   315.842]   Module class: X.Org Video Driver
 [   315.842]   ABI class: X.Org Video Driver, version 15.0
 [   315.842] (II) LoadModule: "qxl"
 [   315.842] (II) Loading /usr/lib/xorg/modules/drivers/qxl_drv.so
 [   315.855] (II) Module qxl: vendor="X.Org Foundation"
 [   315.855]   compiled for 1.15.0, module version = 0.1.1
 [   315.855]   Module class: X.Org Video Driver
 [   315.855]   ABI class: X.Org Video Driver, version 15.0
 [   315.855] (II) LoadModule: "mga"
 [   315.855] (II) Loading /usr/lib/xorg/modules/drivers/mga_drv.so
 [   315.869] (II) Module mga: vendor="X.Org Foundation"
 [   315.869]   compiled for 1.15.0, module version = 1.6.3
 [   315.869]   Module class: X.Org Video Driver
 [   315.869]   ABI class: X.Org Video Driver, version 15.0
 [   315.869] (II) LoadModule: "vboxvideo"
 [   315.869] (II) Loading /usr/lib/xorg/modules/drivers/vboxvideo_drv.so
 [   315.881] (II) Module vboxvideo: vendor="Oracle Corporation"
 [   315.881]   compiled for 1.15.0, module version = 1.0.1
 [   315.881]   Module class: X.Org Video Driver
 [   315.881]   ABI class: X.Org Video Driver, version 15.0
 [   315.881] (**) Load address of symbol "VBOXVIDEO" is 0x7f3e8ca8f460
 [   315.881] (II) LoadModule: "siliconmotion"
 [   315.881] (II) Loading /usr/lib/xorg/modules/drivers/siliconmotion_drv.so
 [   315.892] (II) Module siliconmotion: vendor="X.Org Foundation"
 [   315.892]   compiled for 1.15.0, module version = 1.7.7
 [   315.892]   Module class: X.Org Video Driver
 [   315.892]   ABI class: X.Org Video Driver, version 15.0
 [   315.893] (II) LoadModule: "spiceqxl"
 [   315.893] (II) Loading /usr/lib/xorg/modules/drivers/spiceqxl_drv.so
 [   316.008] (II) Module spiceqxl: vendor="X.Org Foundation"
 [   316.008]   compiled for 1.15.0, module version = 0.1.1
 [   316.008]   Module class: X.Org Video Driver
 [   316.008]   ABI class: X.Org Video Driver, version 15.0
 [   316.008] (II) LoadModule: "neomagic"
 [   316.008] (II) Loading /usr/lib/xorg/modules/drivers/neomagic_drv.so
 [   316.019] (II) Module neomagic: vendor="X.Org Foundation"
 [   316.019]   compiled for 1.15.0, module version = 1.2.8
 [   316.019]   Module class: X.Org Video Driver
 [   316.019]   ABI class: X.Org Video Driver, version 15.0
 [   316.019] (II) LoadModule: "nvidia"
 [   316.019] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
 [   316.101] (II) Module nvidia: vendor="NVIDIA Corporation"
 [   316.101]   compiled for 4.0.2, module version = 1.0.0
 [   316.101]   Module class: X.Org Video Driver
 [   316.118] (II) LoadModule: "sis"
 [   316.118] (II) Loading /usr/lib/xorg/modules/drivers/sis_drv.so
 [   316.138] (II) Module sis: vendor="X.Org Foundation"
 [   316.138]   compiled for 1.15.0, module version = 0.10.7
 [   316.138]   Module class: X.Org Video Driver
 [   316.138]   ABI class: X.Org Video Driver, version 15.0
 [   316.138] (II) LoadModule: "vesa"
 [   316.138] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
 [   316.138] (II) Module vesa: vendor="X.Org Foundation"
 [   316.138]   compiled for 1.15.0, module version = 2.3.3
 [   316.138]   Module class: X.Org Video Driver
 [   316.138]   ABI class: X.Org Video Driver, version 15.0
 [   316.138] (II) LoadModule: "fbdev"
 [   316.138] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
 [   316.140] (II) Module fbdev: vendor="X.Org Foundation"
 [   316.140]   compiled for 1.15.0, module version = 0.4.4
 [   316.140]   Module class: X.Org Video Driver
 [   316.140]   ABI class: X.Org Video Driver, version 15.0
 [   316.140] (WW) Falling back to old probe method for sisusb
 [   316.140] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
 [   316.140] (WW) Falling back to old probe method for cirrus
 [   316.140] (II) Loading sub module "cirrus_laguna"
 [   316.140] (II) LoadModule: "cirrus_laguna"
 [   316.140] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_laguna.so
 [   316.148] (II) Module cirrus_laguna: vendor="X.Org Foundation"
 [   316.148]   compiled for 1.15.0, module version = 1.0.0
 [   316.148]   ABI class: X.Org Video Driver, version 15.0
 [   316.148] (II) Loading sub module "cirrus_alpine"
 [   316.148] (II) LoadModule: "cirrus_alpine"
 [   316.148] (II) Loading /usr/lib/xorg/modules/drivers/cirrus_alpine.so
 [   316.149] (II) Module cirrus_alpine: vendor="X.Org Foundation"
 [   316.149]   compiled for 1.15.0, module version = 1.0.0
 [   316.149]   ABI class: X.Org Video Driver, version 15.0
 [   316.149] (WW) Falling back to old probe method for s3
 [   316.149] (WW) Falling back to old probe method for trident
 [   316.149] (WW) Falling back to old probe method for siliconmotion
 [   316.149] (WW) Falling back to old probe method for spiceqxl
 [   316.149] (WW) Falling back to old probe method for neomagic
 [   316.149] (II) NVIDIA dlloader X Driver  331.38  Wed Jan  8 18:51:00 PST 2014
 [   316.149] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
 [   316.149] (WW) Falling back to old probe method for sis
 [   316.149] (II) VESA: driver for VESA chipsets: vesa
 [   316.149] (II) FBDEV: driver for framebuffer: fbdev
 [   316.172] (++) Using config file: "/root/xorg.conf.new"
 [   316.172] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
 [   316.172] (==) ServerLayout "X.org Configured"
 [   316.172] (**) |-->Screen "Screen0" (0)
 [   316.172] (**) |   |-->Monitor "Monitor0"
 [   316.172] (**) |   |-->Device "Card0"
 [   316.172] (**) |-->Input Device "Mouse0"
 [   316.172] (**) |-->Input Device "Keyboard0"
 [   316.172] (==) Automatically adding devices
 [   316.172] (==) Automatically enabling devices
 [   316.172] (==) Automatically adding GPU devices
 [   316.172] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
 [   316.172]   Entry deleted from font path.
 [   316.172] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
 [   316.172] (**) ModulePath set to "/usr/lib/xorg/modules"
 [   316.172] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
 [   316.172] (WW) Disabling Mouse0
 [   316.172] (WW) Disabling Keyboard0
 [   316.172] (EE) open /dev/dri/card0: No such file or directory
 [   316.172] (WW) Falling back to old probe method for modesetting
 [   316.172] (EE) open /dev/dri/card0: No such file or directory
 [   316.172] (EE) 
 [   316.173] (EE) Backtrace:
 [   316.173] (EE) 0: Xorg (xorg_backtrace+0x48) [0x7f3e9695ec78]
 [   316.173] (EE) 1: Xorg (0x7f3e967b6000+0x1ac969) [0x7f3e96962969]
 [   316.173] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f3e958b3000+0x10340) [0x7f3e958c3340]
 [   316.174] (EE) 
 [   316.174] (EE) Segmentation fault at address 0x0
 [   316.174] (EE) 
 Fatal server error:
 [   316.174] (EE) Caught signal 11 (Segmentation fault). Server aborting
 [   316.175] (EE) 
 [   316.175] (EE) 
 Please consult the The X.Org Foundation support 
     at http://wiki.x.org
  for help. 
 [   316.176] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information. [FONT=Consolas] [   316.181] (EE) [/FONT]
```

Please some help.

---

