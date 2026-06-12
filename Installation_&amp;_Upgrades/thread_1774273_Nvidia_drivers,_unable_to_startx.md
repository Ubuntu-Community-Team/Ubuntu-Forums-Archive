---
title: "Nvidia drivers, unable to startx"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by pravinkenator on 2011-06-03
Hello, 

I have a Tesla C870 and Geforce 8500 GT Graphic card in my system. I tried installing the Nvidia graphic card drivers from the nvidia website(NVIDIA-Linux-x86-270.41.19). The installation was successful. But, I'm not able to start the xserver ... ! I'm running ubuntu 10.10 ... Can some one please help me in this ..!

I'm pasting the log of the xserver with this post.


```
[   781.466] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   781.466] X Protocol Version 11, Revision 0
[   781.466] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[   781.466] Current Operating System: Linux XFX-nForce 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686
[   781.467] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic root=UUID=cd91cf06-a77d-4cc8-b117-425a1a0fc622 ro quiet splash
[   781.467] Build Date: 09 January 2011  12:14:58PM
[   781.467] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[   781.467] Current version of pixman: 0.18.4
[   781.467]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   781.467] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   781.468] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  3 14:15:26 2011
[   781.468] (==) Using config file: "/etc/X11/xorg.conf"
[   781.469] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   781.469] (==) ServerLayout "Layout0"
[   781.469] (**) |-->Screen "Screen0" (0)
[   781.469] (**) |   |-->Monitor "Monitor0"
[   781.469] (**) |   |-->Device "Device0"
[   781.469] (**) |-->Input Device "Keyboard0"
[   781.469] (**) |-->Input Device "Mouse0"
[   781.469] (==) Automatically adding devices
[   781.469] (==) Automatically enabling devices
[   781.469] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   781.469]     Entry deleted from font path.
[   781.469] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   781.469] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   781.469] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   781.469] (WW) Disabling Keyboard0
[   781.469] (WW) Disabling Mouse0
[   781.469] (II) Loader magic: 0x81f9b00
[   781.469] (II) Module ABI versions:
[   781.470]     X.Org ANSI C Emulation: 0.4
[   781.470]     X.Org Video Driver: 8.0
[   781.470]     X.Org XInput driver : 11.0
[   781.470]     X.Org Server Extension : 4.0
[   781.471] (--) PCI:*(0:1:0:0) 10de:0421:1acc:8494 rev 161, Mem @ 0xdc000000/16777216, 0xc0000000/268435456, 0xda000000/33554432, I/O @ 0x00009c00/128, BIOS @ 0x????????/131072
[   781.471] (--) PCI: (0:2:0:0) 10de:0197:10de:048d rev 162, Mem @ 0xd8000000/16777216, 0xb0000000/268435456, 0xd6000000/33554432, I/O @ 0x00008c00/128, BIOS @ 0x????????/131072
[   781.471] (II) Open ACPI successful (/var/run/acpid.socket)
[   781.471] (II) LoadModule: "extmod"
[   781.471] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   781.471] (II) Module extmod: vendor="X.Org Foundation"
[   781.471]     compiled for 1.9.0, module version = 1.0.0
[   781.471]     Module class: X.Org Server Extension
[   781.471]     ABI class: X.Org Server Extension, version 4.0
[   781.471] (II) Loading extension MIT-SCREEN-SAVER
[   781.471] (II) Loading extension XFree86-VidModeExtension
[   781.471] (II) Loading extension XFree86-DGA
[   781.471] (II) Loading extension DPMS
[   781.471] (II) Loading extension XVideo
[   781.471] (II) Loading extension XVideo-MotionCompensation
[   781.471] (II) Loading extension X-Resource
[   781.471] (II) LoadModule: "dbe"
[   781.471] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   781.471] (II) Module dbe: vendor="X.Org Foundation"
[   781.471]     compiled for 1.9.0, module version = 1.0.0
[   781.471]     Module class: X.Org Server Extension
[   781.471]     ABI class: X.Org Server Extension, version 4.0
[   781.471] (II) Loading extension DOUBLE-BUFFER
[   781.471] (II) LoadModule: "glx"
[   781.472] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   781.489] (II) Module glx: vendor="NVIDIA Corporation"
[   781.489]     compiled for 4.0.2, module version = 1.0.0
[   781.489]     Module class: X.Org Server Extension
[   781.489] (II) NVIDIA GLX Module  270.41.19  Mon May 16 23:49:08 PDT 2011
[   781.489] (II) Loading extension GLX
[   781.489] (II) LoadModule: "record"
[   781.489] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   781.489] (II) Module record: vendor="X.Org Foundation"
[   781.489]     compiled for 1.9.0, module version = 1.13.0
[   781.489]     Module class: X.Org Server Extension
[   781.489]     ABI class: X.Org Server Extension, version 4.0
[   781.489] (II) Loading extension RECORD
[   781.489] (II) LoadModule: "dri"
[   781.489] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   781.489] (II) Module dri: vendor="X.Org Foundation"
[   781.489]     compiled for 1.9.0, module version = 1.0.0
[   781.489]     ABI class: X.Org Server Extension, version 4.0
[   781.489] (II) Loading extension XFree86-DRI
[   781.489] (II) LoadModule: "dri2"
[   781.489] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   781.490] (II) Module dri2: vendor="X.Org Foundation"
[   781.490]     compiled for 1.9.0, module version = 1.2.0
[   781.490]     ABI class: X.Org Server Extension, version 4.0
[   781.490] (II) Loading extension DRI2
[   781.490] (II) LoadModule: "nvidia"
[   781.490] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   781.490] (II) Module nvidia: vendor="NVIDIA Corporation"
[   781.490]     compiled for 4.0.2, module version = 1.0.0
[   781.490]     Module class: X.Org Video Driver
[   781.490] (II) NVIDIA dlloader X Driver  270.41.19  Mon May 16 23:33:05 PDT 2011
[   781.490] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   781.490] (--) using VT number 8

[   781.500] (II) Loading sub module "fb"
[   781.500] (II) LoadModule: "fb"
[   781.500] (II) Loading /usr/lib/xorg/modules/libfb.so
[   781.501] (II) Module fb: vendor="X.Org Foundation"
[   781.501]     compiled for 1.9.0, module version = 1.0.0
[   781.501]     ABI class: X.Org ANSI C Emulation, version 0.4
[   781.501] (II) Loading sub module "wfb"
[   781.501] (II) LoadModule: "wfb"
[   781.501] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   781.501] (II) Module wfb: vendor="X.Org Foundation"
[   781.501]     compiled for 1.9.0, module version = 1.0.0
[   781.501]     ABI class: X.Org ANSI C Emulation, version 0.4
[   781.501] (II) Loading sub module "ramdac"
[   781.501] (II) LoadModule: "ramdac"
[   781.501] (II) Module "ramdac" already built-in
[   781.501] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   781.501] (==) NVIDIA(0): RGB weight 888
[   781.501] (==) NVIDIA(0): Default visual is TrueColor
[   781.501] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   781.983] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[   781.985] (II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
[   781.985] (--) NVIDIA(0): Memory: 524288 kBytes
[   781.985] (--) NVIDIA(0): VideoBIOS: 60.86.37.00.35
[   781.985] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   781.985] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[   781.985] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0
[   781.985] (--) NVIDIA(0):     CRT-1
[   781.985] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[   782.025] (II) NVIDIA(0): Assigned Display Device: CRT-1
[   782.025] (==) NVIDIA(0): 
[   782.026] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   782.026] (==) NVIDIA(0):     will be used as the requested mode.
[   782.026] (==) NVIDIA(0): 
[   782.026] (II) NVIDIA(0): Validated modes:
[   782.026] (II) NVIDIA(0):     "nvidia-auto-select"
[   782.026] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[   782.056] (WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
[   782.056] (WW) NVIDIA(0):     from CRT-1's EDID.
[   782.056] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[   782.056] (--) Depth 24 pixmap format is 32 bpp
[   782.093] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
[   782.094] (EE) NVIDIA(GPU-1):     check your system's kernel log for additional error
[   782.094] (EE) NVIDIA(GPU-1):     messages and refer to Chapter 8: Common Problems in the
[   782.094] (EE) NVIDIA(GPU-1):     README for additional information.
[   782.094] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device!
[   782.094] 
Backtrace:
[   782.094] 0: X (xorg_backtrace+0x3b) [0x80ef31b]
[   782.094] 1: X (0x8048000+0x5d00d) [0x80a500d]
[   782.094] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x2d140c]
[   782.094] Segmentation fault at address (nil)
[   782.094] 
Caught signal 11 (Segmentation fault). Server aborting
[   782.094] 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   782.094] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   782.094] 
[   782.106]  ddxSigGiveUp: Closing log

```

---

### Post by highspider on 2011-12-06
I got the same problem I think
with NVIDIA-Linux-x86-285.05.09.run

can login and you start-x with
```
startx
```also for gnome-X status 
```
service gdm status
```start the X
```
sudo service gdm start
```



your could also try reinstalling the driver
```

wget http://uk.download.nvidia.com/XFree86/Linux-x86/270.41.19/NVIDIA-Linux-x86-270.41.19.run
sudo NVIDIA-Linux-x86-270.41.19.run

```

---

### Post by highspider on 2011-12-06
the above wget is for your driver. (incase you lost it)
Yeap Same error took awhile to get back here:)

I found that after reboot Im screwed with same error every time.  
A temporary solution is to reinstall the driver and then use .

```
startx
```this gets me back in the computer with x but I have to do it on each restart. 

or also in your case try disabling one of video cards in bios. 

BUMP

---

### Post by MAFoElffen on 2011-12-06
> **pravinkenator said:**
> Hello, 

I have a Tesla C870 and Geforce 8500 GT Graphic card in my system. I  tried installing the Nvidia graphic card drivers from the nvidia  website(NVIDIA-Linux-x86-270.41.19). The installation was successful.  But, I'm not able to start the xserver ... ! I'm running ubuntu 10.10  ... Can some one please help me in this ..!

I'm pasting the log of the xserver with this post.


```
[   781.466] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   781.466] X Protocol Version 11, Revision 0
[   781.466] Build Operating System: Linux 2.6.24-28-server i686 Ubuntu
[   781.466] Current Operating System: Linux XFX-nForce 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686
[   781.467] Kernel command line:  BOOT_IMAGE=/boot/vmlinuz-2.6.35-28-generic  root=UUID=cd91cf06-a77d-4cc8-b117-425a1a0fc622 ro quiet splash
[   781.467] Build Date: 09 January 2011  12:14:58PM
[   781.467] xorg-server 2:1.9.0-0ubuntu7.3 (For technical support please see http://www.ubuntu.com/support) 
[   781.467] Current version of pixman: 0.18.4
[   781.467]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   781.467] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   781.468] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jun  3 14:15:26 2011
[   781.468] (==) Using config file: "/etc/X11/xorg.conf"
[   781.469] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   781.469] (==) ServerLayout "Layout0"
[   781.469] (**) |-->Screen "Screen0" (0)
[   781.469] (**) |   |-->Monitor "Monitor0"
[   781.469] (**) |   |-->Device "Device0"
[   781.469] (**) |-->Input Device "Keyboard0"
[   781.469] (**) |-->Input Device "Mouse0"
[   781.469] (==) Automatically adding devices
[   781.469] (==) Automatically enabling devices
[   781.469] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   781.469]     Entry deleted from font path.
[   781.469] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[   781.469] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   781.469] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[   781.469] (WW) Disabling Keyboard0
[   781.469] (WW) Disabling Mouse0
[   781.469] (II) Loader magic: 0x81f9b00
[   781.469] (II) Module ABI versions:
[   781.470]     X.Org ANSI C Emulation: 0.4
[   781.470]     X.Org Video Driver: 8.0
[   781.470]     X.Org XInput driver : 11.0
[   781.470]     X.Org Server Extension : 4.0
[   781.471] (--) PCI:*(0:1:0:0) 10de:0421:1acc:8494 rev 161, Mem @  0xdc000000/16777216, 0xc0000000/268435456, 0xda000000/33554432, I/O @  0x00009c00/128, BIOS @ 0x????????/131072
[   781.471] (--) PCI: (0:2:0:0) 10de:0197:10de:048d rev 162, Mem @  0xd8000000/16777216, 0xb0000000/268435456, 0xd6000000/33554432, I/O @  0x00008c00/128, BIOS @ 0x????????/131072
[   781.471] (II) Open ACPI successful (/var/run/acpid.socket)
[   781.471] (II) LoadModule: "extmod"
[   781.471] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   781.471] (II) Module extmod: vendor="X.Org Foundation"
[   781.471]     compiled for 1.9.0, module version = 1.0.0
[   781.471]     Module class: X.Org Server Extension
[   781.471]     ABI class: X.Org Server Extension, version 4.0
[   781.471] (II) Loading extension MIT-SCREEN-SAVER
[   781.471] (II) Loading extension XFree86-VidModeExtension
[   781.471] (II) Loading extension XFree86-DGA
[   781.471] (II) Loading extension DPMS
[   781.471] (II) Loading extension XVideo
[   781.471] (II) Loading extension XVideo-MotionCompensation
[   781.471] (II) Loading extension X-Resource
[   781.471] (II) LoadModule: "dbe"
[   781.471] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   781.471] (II) Module dbe: vendor="X.Org Foundation"
[   781.471]     compiled for 1.9.0, module version = 1.0.0
[   781.471]     Module class: X.Org Server Extension
[   781.471]     ABI class: X.Org Server Extension, version 4.0
[   781.471] (II) Loading extension DOUBLE-BUFFER
[   781.471] (II) LoadModule: "glx"
[   781.472] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   781.489] (II) Module glx: vendor="NVIDIA Corporation"
[   781.489]     compiled for 4.0.2, module version = 1.0.0
[   781.489]     Module class: X.Org Server Extension
[   781.489] (II) NVIDIA GLX Module  270.41.19  Mon May 16 23:49:08 PDT 2011
[   781.489] (II) Loading extension GLX
[   781.489] (II) LoadModule: "record"
[   781.489] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   781.489] (II) Module record: vendor="X.Org Foundation"
[   781.489]     compiled for 1.9.0, module version = 1.13.0
[   781.489]     Module class: X.Org Server Extension
[   781.489]     ABI class: X.Org Server Extension, version 4.0
[   781.489] (II) Loading extension RECORD
[   781.489] (II) LoadModule: "dri"
[   781.489] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   781.489] (II) Module dri: vendor="X.Org Foundation"
[   781.489]     compiled for 1.9.0, module version = 1.0.0
[   781.489]     ABI class: X.Org Server Extension, version 4.0
[   781.489] (II) Loading extension XFree86-DRI
[   781.489] (II) LoadModule: "dri2"
[   781.489] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   781.490] (II) Module dri2: vendor="X.Org Foundation"
[   781.490]     compiled for 1.9.0, module version = 1.2.0
[   781.490]     ABI class: X.Org Server Extension, version 4.0
[   781.490] (II) Loading extension DRI2
[   781.490] (II) LoadModule: "nvidia"
[COLOR=Teal][   781.490] (II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
[   781.490] (II) Module nvidia: vendor="NVIDIA Corporation"
[   781.490]     compiled for 4.0.2, module version = 1.0.0
[   781.490]     Module class: X.Org Video Driver
[   781.490] (II) NVIDIA dlloader X Driver  270.41.19  Mon May 16 23:33:05 PDT 2011
[   781.490] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   781.490] (--) using VT number 8
[/COLOR]
[   781.500] (II) Loading sub module "fb"
[   781.500] (II) LoadModule: "fb"
[   781.500] (II) Loading /usr/lib/xorg/modules/libfb.so
[   781.501] (II) Module fb: vendor="X.Org Foundation"
[   781.501]     compiled for 1.9.0, module version = 1.0.0
[   781.501]     ABI class: X.Org ANSI C Emulation, version 0.4
[   781.501] (II) Loading sub module "wfb"
[   781.501] (II) LoadModule: "wfb"
[   781.501] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   781.501] (II) Module wfb: vendor="X.Org Foundation"
[   781.501]     compiled for 1.9.0, module version = 1.0.0
[   781.501]     ABI class: X.Org ANSI C Emulation, version 0.4
[   781.501] (II) Loading sub module "ramdac"
[   781.501] (II) LoadModule: "ramdac"
[   781.501] (II) Module "ramdac" already built-in
[   781.501] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[   781.501] (==) NVIDIA(0): RGB weight 888
[   781.501] (==) NVIDIA(0): Default visual is TrueColor
[   781.501] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[COLOR=Red][   781.983] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-1
[/COLOR][COLOR=Teal][   781.985] (II) NVIDIA(0): NVIDIA GPU GeForce 8500 GT (G86) at PCI:1:0:0 (GPU-0)
[/COLOR][   781.985] (--) NVIDIA(0): Memory: 524288 kBytes
[   781.985] (--) NVIDIA(0): VideoBIOS: 60.86.37.00.35
[   781.985] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[   781.985] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[COLOR=Green][   781.985] (--) NVIDIA(0): Connected display device(s) on GeForce 8500 GT at PCI:1:0:0
[/COLOR][   781.985] (--) NVIDIA(0):     CRT-1
[   781.985] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[   782.025] (II) NVIDIA(0): Assigned Display Device: CRT-1
[   782.025] (==) NVIDIA(0): 
[   782.026] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[   782.026] (==) NVIDIA(0):     will be used as the requested mode.
[   782.026] (==) NVIDIA(0): 
[   782.026] (II) NVIDIA(0): Validated modes:
[   782.026] (II) NVIDIA(0):     "nvidia-auto-select"
[   782.026] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[COLOR=Red][   782.056] (WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
[   782.056] (WW) NVIDIA(0):     from CRT-1's EDID.
[/COLOR][   782.056] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[   782.056] (--) Depth 24 pixmap format is 32 bpp
[COLOR=Red][   782.093] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA GPU at PCI:2:0:0.  Please
[   782.094] (EE) NVIDIA(GPU-1):     check your system's kernel log for additional error
[   782.094] (EE) NVIDIA(GPU-1):     messages and refer to Chapter 8: Common Problems in the
[   782.094] (EE) NVIDIA(GPU-1):     README for additional information.
[   782.094] (EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device!
[   782.094] 
Backtrace:
[   782.094] 0: X (xorg_backtrace+0x3b) [0x80ef31b]
[   782.094] 1: X (0x8048000+0x5d00d) [0x80a500d]
[   782.094] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0x2d140c]
[   782.094] Segmentation fault at address (nil)
[   782.094] 
Caught signal 11 (Segmentation fault). Server aborting
[   782.094] 
[/COLOR]Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   782.094] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   782.094] 
[   782.106]  ddxSigGiveUp: Closing log

```
***Please stop for a moment...*** Please post your /var/log/nvidia-installer.log file. The xorg.0.log shows that the modules are all loading until poof... BUT, it also shows something else...

It shows that the Display you have is "not" returning any EDID data back. What it's doing without that data is giving it a mode or a sync that is out of range. I have a few workarounds for that error. But first we need to know the make and model of your monitor. Then install a hardware utility called hwinfo:
```

sudo apt-get install hwinfo

```Then post the results of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor

```Something is going on, but more info is needed to figure out what. Curious why the OP didn't install 290.10 which released a few weeks ago, instead of 270.41?

---

### Post by apices on 2011-12-06
This has happened to me a few times. 
Have a look at
 [ftp://download.nvidia.com/XFree86/Linux-x86/256.44/README/commonproblems.html](ftp://download.nvidia.com/XFree86/Linux-x86/256.44/README/commonproblems.html)

From your log, it looks to me like you are running two GPU's, if so, remove one of them and try the driver install again.

1. Did you kill your xserver before installing the driver. 

2. Did you install the driver with the appropriate kernel module headers? see my blog posting on that at [http://www.techauthority.net/sitecontent/xbmc/nvidia.ko.php](http://www.techauthority.net/sitecontent/xbmc/nvidia.ko.php)  

3. Are you trying to run SLI?   if so take one of the cards out and try with just one.

4. Have you booted into 10.10 successfully before you installed the nVidia drivers?
     If so, boot using live cd and copy that xorg.conf (removable disk) and refer to [http://us.download.nvidia.com/XFree86/Linux-x86/290.10/README/editxconfig.html#ManuallyEditing1ae61](http://us.download.nvidia.com/XFree86/Linux-x86/290.10/README/editxconfig.html#ManuallyEditing1ae61)

I have been in your shoes. Ubuntu hates when you install nVidia. Another thing that you might research is disabling nouveau. See:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Removing_Nouveau_.28advanced.2BAC8-expert_users.29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Removing_Nouveau_.28advanced.2BAC8-expert_users.29)

---

### Post by gesch on 2011-12-06
For AMD64 machines: After booting into **recovery modus.** you must run as root the 
driver installation script
sudo sh ./NVIDIA-Linux-x86_64-290.10.run
Ignore all installation warnings!

Then you should be able to StartX and everything runs fine again

---

### Post by MAFoElffen on 2011-12-06
> From NVidia for Tesla C870```

Version      Release Date
-------       --------------
290.10      2011.11.22
275.36      2011.11.03
275.28      2011.09.07
173.1431  2011.08.17
285.03      2011.08.17
270.4134   2011.08.16
280.13      2011.08.01
275.21      2011.07.21
275.19      2011.07.15
270.4122  2011.06.10
270.4119  2011.05.20
275.09     2011.05.20
173.1430  2011.05.03

```I reread your Xorg log this morning after some coffee. Edited my first post. Strange.

The GeForce 8500 gets picked up and initializes fine. The Tesla doesn't and crashes X. You said you installed 270.41.19... That should have covered both cards but didn't. The xorg.conf (still not posted) should have 2 device sections with the 8500 as device0, pci:1:0.00, using driver nvidia and the Tesla as device1, PCI:2.0.00 using driver nvidia...

If there was a driver build error (still no /var/log/nvidia-installer.log) you would thiink that it would error on both cards, not just the Tesla.

I know that with Linux/Unix and SLI, I have to pull one of my cards to install my drivers.... Then I put the other card back in.

It looks like if you pulled the Tesla, that your sys would come up.  (You might want to confirm that.) What happens if you pull the Geforce 8500?

Can you please post the files and data requested in my previous post?

---

