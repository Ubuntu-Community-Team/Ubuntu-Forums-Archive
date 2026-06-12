---
title: "several issues with 11.10 installation"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2011-10-14
Hi,

I installed 11.10 on two machines, a Dell M380 and a Dell M50 laptop. The first was an upgrade from 11.04 while the second was a clean install. I have several problems, that are:

M380:
1. If I start in "Ubuntu" mode, the screen is essentially frozen and partially white. On the other hand if I start in "Ubuntu2" mode, then it seems OK. I installed the additional Nvidia proprietary driver but it didn't help.

2. It seems that something is broken with the vncviewer when using a tunnel through SSH. After typing something like: "vncviewer -via user@host1 host2:1" I get:
```

Fri Oct 14 12:20:46 2011
 CConn:       connected to host localhost port 5599
*** stack smashing detected ***: vncviewer terminated
======= Backtrace: =========
/lib/i386-linux-gnu/libc.so.6(__fortify_fail+0x45)[0x1f78d5]
/lib/i386-linux-gnu/libc.so.6(+0xe7887)[0x1f7887]
vncviewer[0x8082f91]
vncviewer[0x807e534]
vncviewer[0x805064b]
vncviewer[0x805a056]
/lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xf3)[0x129113]
vncviewer[0x804c6b1]
======= Memory map: ========
00110000-00286000 r-xp 00000000 08:11 5767195    /lib/i386-linux-gnu/libc-2.13.so
00286000-00288000 r--p 00176000 08:11 5767195    /lib/i386-linux-gnu/libc-2.13.so
00288000-00289000 rw-p 00178000 08:11 5767195    /lib/i386-linux-gnu/libc-2.13.so
00289000-0028c000 rw-p 00000000 00:00 0 
0028c000-0028f000 r-xp 00000000 08:11 5767204    /lib/i386-linux-gnu/libdl-2.13.so
0028f000-00290000 r--p 00002000 08:11 5767204    /lib/i386-linux-gnu/libdl-2.13.so
00290000-00291000 rw-p 00003000 08:11 5767204    /lib/i386-linux-gnu/libdl-2.13.so
00296000-002a7000 r-xp 00000000 08:11 5767614    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
002a7000-002a8000 r--p 00010000 08:11 5767614    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
002a8000-002a9000 rw-p 00011000 08:11 5767614    /usr/lib/i386-linux-gnu/libXext.so.6.4.0
002a9000-002d1000 r-xp 00000000 08:11 5767205    /lib/i386-linux-gnu/libm-2.13.so
002d1000-002d2000 r--p 00028000 08:11 5767205    /lib/i386-linux-gnu/libm-2.13.so
002d2000-002d3000 rw-p 00029000 08:11 5767205    /lib/i386-linux-gnu/libm-2.13.so
002d3000-002dc000 r-xp 00000000 08:11 5768767    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
002dc000-002dd000 r--p 00008000 08:11 5768767    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
002dd000-002de000 rw-p 00009000 08:11 5768767    /usr/lib/i386-linux-gnu/libXrender.so.1.3.0
002de000-002e9000 r-xp 00000000 08:11 5767214    /lib/i386-linux-gnu/libnss_files-2.13.so
002e9000-002ea000 r--p 0000a000 08:11 5767214    /lib/i386-linux-gnu/libnss_files-2.13.so
002ea000-002eb000 rw-p 0000b000 08:11 5767214    /lib/i386-linux-gnu/libnss_files-2.13.so
005de000-005df000 r-xp 00000000 00:00 0          [vdso]
006b6000-006d3000 r-xp 00000000 08:11 5767309    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
006d3000-006d4000 r--p 0001c000 08:11 5767309    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
006d4000-006d5000 rw-p 0001d000 08:11 5767309    /usr/lib/i386-linux-gnu/libxcb.so.1.1.0
00705000-00836000 r-xp 00000000 08:11 5767437    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00836000-00837000 ---p 00131000 08:11 5767437    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00837000-00838000 r--p 00131000 08:11 5767437    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
00838000-0083a000 rw-p 00132000 08:11 5767437    /usr/lib/i386-linux-gnu/libX11.so.6.3.0
0083a000-0083b000 rw-p 00000000 00:00 0 
00871000-00875000 r-xp 00000000 08:11 5768968    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
00875000-00876000 r--p 00003000 08:11 5768968    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
00876000-00877000 rw-p 00004000 08:11 5768968    /usr/lib/i386-linux-gnu/libXfixes.so.3.1.0
00911000-0092f000 r-xp 00000000 08:11 5767187    /lib/i386-linux-gnu/ld-2.13.so
0092f000-00930000 r--p 0001d000 08:11 5767187    /lib/i386-linux-gnu/ld-2.13.so
00930000-00931000 rw-p 0001e000 08:11 5767187    /lib/i386-linux-gnu/ld-2.13.so
00a15000-00a28000 r-xp 00000000 08:11 5767762    /lib/i386-linux-gnu/libz.so.1.2.3.4
00a28000-00a29000 r--p 00012000 08:11 5767762    /lib/i386-linux-gnu/libz.so.1.2.3.4
00a29000-00a2a000 rw-p 00013000 08:11 5767762    /lib/i386-linux-gnu/libz.so.1.2.3.4
00b63000-00b65000 r-xp 00000000 08:11 5767299    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00b65000-00b66000 r--p 00001000 08:11 5767299    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00b66000-00b67000 rw-p 00002000 08:11 5767299    /usr/lib/i386-linux-gnu/libXau.so.6.0.0
00ba3000-00bbf000 r-xp 00000000 08:11 5767188    /lib/i386-linux-gnu/libgcc_s.so.1
00bbf000-00bc0000 r--p 0001b000 08:11 5767188    /lib/i386-linux-gnu/libgcc_s.so.1
00bc0000-00bc1000 rw-p 0001c000 08:11 5767188    /lib/i386-linux-gnu/libgcc_s.so.1
00c00000-00cde000 r-xp 00000000 08:11 5767646    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00cde000-00cdf000 ---p 000de000 08:11 5767646    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00cdf000-00ce3000 r--p 000de000 08:11 5767646    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00ce3000-00ce4000 rw-p 000e2000 08:11 5767646    /usr/lib/i386-linux-gnu/libstdc++.so.6.0.16
00ce4000-00ceb000 rw-p 00000000 00:00 0 
00e9b000-00ea0000 r-xp 00000000 08:11 5767304    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
00ea0000-00ea1000 r--p 00004000 08:11 5767304    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
00ea1000-00ea2000 rw-p 00005000 08:11 5767304    /usr/lib/i386-linux-gnu/libXdmcp.so.6.0.0
00f63000-00f6c000 r-xp 00000000 08:11 5768535    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00f6c000-00f6d000 r--p 00008000 08:11 5768535    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
00f6d000-00f6e000 rw-p 00009000 08:11 5768535    /usr/lib/i386-linux-gnu/libXcursor.so.1.0.2
08048000-08099000 r-xp 00000000 08:11 4031       /usr/bin/xvnc4viewer
0809a000-0809b000 r--p 00051000 08:11 4031       /usr/bin/xvnc4viewer
0809b000-0809c000 rw-p 00052000 08:11 4031       /usr/bin/xvnc4viewer
0809c000-0809d000 rw-p 00000000 00:00 0 
09b4b000-09b6c000 rw-p 00000000 00:00 0          [heap]
b7782000-b7787000 rw-p 00000000 00:00 0 
b77a2000-b77a4000 rw-p 00000000 00:00 0 
bf9a7000-bf9c8000 rw-p 00000000 00:00 0          [stack]

```M50:
The install went OK, but when I boot the screen is black. I can get on the console by typing ctrl-alt-Fx and log on for rebooting, but the screen is alway black.

Thanks,

Daniel

---

### Post by kralisec on 2011-10-14
Hello Daniel,

I can't help for point 1 (for me my second screen was not even seen, nvidia-173 on Dell D620: I finally totally purge nvidia driver and all looks fine know)

For point 2: I face exactly the same crash: installing package xtightvncviewer solve my problem,
I just replace vncviewer -listen with xtightvncviewer -listen and it works fine :D



Good day,
Laurent.

---

### Post by danielsender on 2011-10-14
Yes, the xtightvncviewer alternative worked, thanks. With respect to the M50 problem, I'm attaching the Xorg.0.log here:
```

[    51.779] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    51.779] X Protocol Version 11, Revision 0
[    51.779] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    51.779] Current Operating System: Linux kidhug 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686
[    51.779] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=67e485e0-aa01-44ad-b18f-48462d9c906e ro recovery nomodeset
[    51.779] Build Date: 29 September 2011  12:48:48AM
[    51.779] xorg-server 2:1.10.4-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[    51.779] Current version of pixman: 0.22.2
[    51.779]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    51.779] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    51.790] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 14 14:06:09 2011
[    51.790] (==) Using config file: "/etc/X11/xorg.conf"
[    51.790] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    51.791] (==) No Layout section.  Using the first Screen section.
[    51.791] (**) |-->Screen "Default Screen" (0)
[    51.791] (**) |   |-->Monitor "<default monitor>"
[    51.791] (==) No device specified for screen "Default Screen".
    Using the first device section listed.
[    51.791] (**) |   |-->Device "Default Device"
[    51.791] (==) No monitor specified for screen "Default Screen".
    Using a default monitor configuration.
[    51.791] (==) Automatically adding devices
[    51.791] (==) Automatically enabling devices
[    51.792] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    51.792]     Entry deleted from font path.
[    51.792] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    51.792]     Entry deleted from font path.
[    51.792] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    51.792]     Entry deleted from font path.
[    51.792] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    51.792]     Entry deleted from font path.
[    51.792] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    51.792]     Entry deleted from font path.
[    51.792] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    51.792] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    51.792] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    51.792] (II) Loader magic: 0x823ada0
[    51.792] (II) Module ABI versions:
[    51.792]     X.Org ANSI C Emulation: 0.4
[    51.792]     X.Org Video Driver: 10.0
[    51.792]     X.Org XInput driver : 12.3
[    51.792]     X.Org Server Extension : 5.0
[    51.793] (--) PCI:*(0:1:0:0) 10de:017c:1028:00d5 rev 163, Mem @ 0xfc000000/16777216, 0xe0000000/134217728, 0xdff80000/524288, BIOS @ 0x????????/131072
[    51.796] (II) Open ACPI successful (/var/run/acpid.socket)
[    51.796] (II) LoadModule: "extmod"
[    51.798] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    51.798] (II) Module extmod: vendor="X.Org Foundation"
[    51.798]     compiled for 1.10.4, module version = 1.0.0
[    51.798]     Module class: X.Org Server Extension
[    51.798]     ABI class: X.Org Server Extension, version 5.0
[    51.798] (II) Loading extension MIT-SCREEN-SAVER
[    51.798] (II) Loading extension XFree86-VidModeExtension
[    51.798] (II) Loading extension XFree86-DGA
[    51.798] (II) Loading extension DPMS
[    51.798] (II) Loading extension XVideo
[    51.798] (II) Loading extension XVideo-MotionCompensation
[    51.798] (II) Loading extension X-Resource
[    51.798] (II) LoadModule: "dbe"
[    51.799] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    51.799] (II) Module dbe: vendor="X.Org Foundation"
[    51.799]     compiled for 1.10.4, module version = 1.0.0
[    51.799]     Module class: X.Org Server Extension
[    51.799]     ABI class: X.Org Server Extension, version 5.0
[    51.799] (II) Loading extension DOUBLE-BUFFER
[    51.799] (II) LoadModule: "glx"
[    51.799] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    51.862] (II) Module glx: vendor="NVIDIA Corporation"
[    51.862]     compiled for 4.0.2, module version = 1.0.0
[    51.862]     Module class: X.Org Server Extension
[    51.862] (II) NVIDIA GLX Module  96.43.20  Sun Jul 17 23:48:16 PDT 2011
[    51.862] (II) Loading extension GLX
[    51.862] (II) LoadModule: "record"
[    51.863] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    51.863] (II) Module record: vendor="X.Org Foundation"
[    51.863]     compiled for 1.10.4, module version = 1.13.0
[    51.863]     Module class: X.Org Server Extension
[    51.863]     ABI class: X.Org Server Extension, version 5.0
[    51.863] (II) Loading extension RECORD
[    51.863] (II) LoadModule: "dri"
[    51.866] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    51.867] (II) Module dri: vendor="X.Org Foundation"
[    51.867]     compiled for 1.10.4, module version = 1.0.0
[    51.867]     ABI class: X.Org Server Extension, version 5.0
[    51.867] (II) Loading extension XFree86-DRI
[    51.867] (II) LoadModule: "dri2"
[    51.868] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    51.868] (II) Module dri2: vendor="X.Org Foundation"
[    51.868]     compiled for 1.10.4, module version = 1.2.0
[    51.868]     ABI class: X.Org Server Extension, version 5.0
[    51.868] (II) Loading extension DRI2
[    51.868] (==) Matched nvidia as autoconfigured driver 0
[    51.868] (==) Matched nouveau as autoconfigured driver 1
[    51.868] (==) Matched nv as autoconfigured driver 2
[    51.868] (==) Matched vesa as autoconfigured driver 3
[    51.868] (==) Matched fbdev as autoconfigured driver 4
[    51.868] (==) Assigned the driver to the xf86ConfigLayout
[    51.868] (II) LoadModule: "nvidia"
[    51.868] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    51.870] (II) Module nvidia: vendor="NVIDIA Corporation"
[    51.870]     compiled for 4.0.2, module version = 1.0.0
[    51.870]     Module class: X.Org Video Driver
[    51.870] (II) LoadModule: "nouveau"
[    51.871] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    51.871] (II) Module nouveau: vendor="X.Org Foundation"
[    51.871]     compiled for 1.10.1, module version = 0.0.16
[    51.871]     Module class: X.Org Video Driver
[    51.871]     ABI class: X.Org Video Driver, version 10.0
[    51.871] (II) LoadModule: "nv"
[    51.880] (WW) Warning, couldn't open module nv
[    51.880] (II) UnloadModule: "nv"
[    51.880] (II) Unloading nv
[    51.880] (EE) Failed to load module "nv" (module does not exist, 0)
[    51.880] (II) LoadModule: "vesa"
[    51.881] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    51.881] (II) Module vesa: vendor="X.Org Foundation"
[    51.881]     compiled for 1.10.2, module version = 2.3.0
[    51.881]     Module class: X.Org Video Driver
[    51.881]     ABI class: X.Org Video Driver, version 10.0
[    51.881] (II) LoadModule: "fbdev"
[    51.882] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    51.882] (II) Module fbdev: vendor="X.Org Foundation"
[    51.882]     compiled for 1.10.0, module version = 0.4.2
[    51.882]     ABI class: X.Org Video Driver, version 10.0
[    51.882] (II) NVIDIA dlloader X Driver  96.43.20  Sun Jul 17 23:35:47 PDT 2011
[    51.882] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    51.882] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    51.882] (II) NOUVEAU driver for NVIDIA chipset families :
[    51.882]     RIVA TNT        (NV04)
[    51.882]     RIVA TNT2       (NV05)
[    51.882]     GeForce 256     (NV10)
[    51.882]     GeForce 2       (NV11, NV15)
[    51.882]     GeForce 4MX     (NV17, NV18)
[    51.883]     GeForce 3       (NV20)
[    51.883]     GeForce 4Ti     (NV25, NV28)
[    51.883]     GeForce FX      (NV3x)
[    51.883]     GeForce 6       (NV4x)
[    51.883]     GeForce 7       (G7x)
[    51.883]     GeForce 8       (G8x)
[    51.883]     GeForce GTX 200 (NVA0)
[    51.883]     GeForce GTX 400 (NVC0)
[    51.883] (II) VESA: driver for VESA chipsets: vesa
[    51.883] (II) FBDEV: driver for framebuffer: fbdev
[    51.883] (++) using VT number 7

[    51.885] (II) Loading sub module "fb"
[    51.885] (II) LoadModule: "fb"
[    51.885] (II) Loading /usr/lib/xorg/modules/libfb.so
[    51.886] (II) Module fb: vendor="X.Org Foundation"
[    51.886]     compiled for 1.10.4, module version = 1.0.0
[    51.886]     ABI class: X.Org ANSI C Emulation, version 0.4
[    51.886] (II) Loading sub module "ramdac"
[    51.886] (II) LoadModule: "ramdac"
[    51.886] (II) Module "ramdac" already built-in
[    51.886] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    51.886] (II) Loading /usr/lib/xorg/modules/libfb.so
[    51.886] (WW) Falling back to old probe method for vesa
[    51.886] (WW) Falling back to old probe method for fbdev
[    51.886] (II) Loading sub module "fbdevhw"
[    51.886] (II) LoadModule: "fbdevhw"
[    51.887] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    51.887] (II) Module fbdevhw: vendor="X.Org Foundation"
[    51.887]     compiled for 1.10.4, module version = 0.0.2
[    51.887]     ABI class: X.Org Video Driver, version 10.0
[    51.891] (EE) open /dev/fb0: No such file or directory
[    51.891] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    51.891] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    51.892] (==) NVIDIA(0): RGB weight 888
[    51.892] (==) NVIDIA(0): Default visual is TrueColor
[    51.892] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    51.892] (**) NVIDIA(0): Option "NoLogo" "True"
[    51.892] (**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
[    51.892] (**) NVIDIA(0): Enabling RENDER acceleration
[    51.892] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    51.892] (II) NVIDIA(0):     enabled.
[    52.514] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    52.515] (II) NVIDIA(0): NVIDIA GPU Quadro4 500 GoGL at PCI:1:0:0 (GPU-0)
[    52.515] (--) NVIDIA(0): Memory: 65536 kBytes
[    52.515] (--) NVIDIA(0): VideoBIOS: 04.17.00.22.f8
[    52.515] (II) NVIDIA(0): Detected AGP rate: 4X
[    52.515] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    52.515] (--) NVIDIA(0): Connected display device(s) on Quadro4 500 GoGL at PCI:1:0:0:
[    52.515] (--) NVIDIA(0):     CRT-0
[    52.515] (--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
[    52.515] (--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
[    52.515] (--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 224.0 MHz maximum pixel
[    52.515] (--) NVIDIA(0):     clock
[    52.515] (--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
[    52.522] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    52.523] (WW) NVIDIA(0): 
[    52.523] (WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    52.523] (WW) NVIDIA(0):     will be used as the requested mode.
[    52.523] (WW) NVIDIA(0): 
[    52.523] (II) NVIDIA(0): Validated modes:
[    52.523] (II) NVIDIA(0):     "nvidia-auto-select"
[    52.523] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    52.523] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    52.523] (WW) NVIDIA(0):     from CRT-0's EDID.
[    52.523] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    52.523] (WW) NVIDIA(0): UBB is incompatible with the Composite extension.  Disabling
[    52.523] (WW) NVIDIA(0):     UBB.
[    52.523] (II) UnloadModule: "nouveau"
[    52.523] (II) Unloading nouveau
[    52.523] (II) UnloadModule: "vesa"
[    52.523] (II) Unloading vesa
[    52.523] (II) UnloadModule: "fbdev"
[    52.523] (II) Unloading fbdev
[    52.523] (II) UnloadModule: "fbdevhw"
[    52.523] (II) Unloading fbdevhw
[    52.523] (--) Depth 24 pixmap format is 32 bpp
[    52.526] (II) NVIDIA(0): Initialized GART.
[    52.551] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    52.721] (II) Loading extension NV-GLX
[    52.734] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    52.735] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    52.735] (==) NVIDIA(0): Backing store disabled
[    52.735] (==) NVIDIA(0): Silken mouse enabled
[    52.735] (==) NVIDIA(0): DPMS enabled
[    52.736] (II) Loading extension NV-CONTROL
[    52.736] (==) RandR enabled
[    52.736] (II) Initializing built-in extension Generic Event Extension
[    52.736] (II) Initializing built-in extension SHAPE
[    52.736] (II) Initializing built-in extension MIT-SHM
[    52.736] (II) Initializing built-in extension XInputExtension
[    52.736] (II) Initializing built-in extension XTEST
[    52.736] (II) Initializing built-in extension BIG-REQUESTS
[    52.736] (II) Initializing built-in extension SYNC
[    52.736] (II) Initializing built-in extension XKEYBOARD
[    52.736] (II) Initializing built-in extension XC-MISC
[    52.736] (II) Initializing built-in extension SECURITY
[    52.736] (II) Initializing built-in extension XINERAMA
[    52.736] (II) Initializing built-in extension XFIXES
[    52.736] (II) Initializing built-in extension RENDER
[    52.736] (II) Initializing built-in extension RANDR
[    52.736] (II) Initializing built-in extension COMPOSITE
[    52.736] (II) Initializing built-in extension DAMAGE
[    52.736] (II) Initializing built-in extension GESTURE
[    52.753] (II) Initializing extension GLX
[    52.849] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    52.878] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    52.878] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    52.878] (II) LoadModule: "evdev"
[    52.879] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.881] (II) Module evdev: vendor="X.Org Foundation"
[    52.881]     compiled for 1.10.2, module version = 2.6.0
[    52.881]     Module class: X.Org XInput Driver
[    52.881]     ABI class: X.Org XInput driver, version 12.3
[    52.881] (II) Using input driver 'evdev' for 'Video Bus'
[    52.881] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.881] (**) Video Bus: always reports core events
[    52.881] (**) Video Bus: Device: "/dev/input/event6"
[    52.882] (--) Video Bus: Found keys
[    52.882] (II) Video Bus: Configuring as keyboard
[    52.882] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A03:00/device:16/LNXVIDEO:00/input/input6/event6"
[    52.882] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    52.882] (**) Option "xkb_rules" "evdev"
[    52.882] (**) Option "xkb_model" "pc105"
[    52.882] (**) Option "xkb_layout" "us"
[    52.899] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    52.900] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    52.900] (II) Using input driver 'evdev' for 'Power Button'
[    52.900] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.900] (**) Power Button: always reports core events
[    52.900] (**) Power Button: Device: "/dev/input/event1"
[    52.900] (--) Power Button: Found keys
[    52.900] (II) Power Button: Configuring as keyboard
[    52.900] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    52.900] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    52.900] (**) Option "xkb_rules" "evdev"
[    52.900] (**) Option "xkb_model" "pc105"
[    52.900] (**) Option "xkb_layout" "us"
[    52.901] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    52.902] (II) No input driver/identifier specified (ignoring)
[    52.902] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[    52.902] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    52.902] (II) Using input driver 'evdev' for 'Sleep Button'
[    52.902] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.903] (**) Sleep Button: always reports core events
[    52.903] (**) Sleep Button: Device: "/dev/input/event2"
[    52.903] (--) Sleep Button: Found keys
[    52.903] (II) Sleep Button: Configuring as keyboard
[    52.903] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2/event2"
[    52.903] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[    52.903] (**) Option "xkb_rules" "evdev"
[    52.903] (**) Option "xkb_model" "pc105"
[    52.903] (**) Option "xkb_layout" "us"
[    52.907] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    52.907] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    52.907] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    52.907] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.908] (**) Logitech USB Receiver: always reports core events
[    52.909] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    52.909] (--) Logitech USB Receiver: Found keys
[    52.909] (II) Logitech USB Receiver: Configuring as keyboard
[    52.909] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb2/2-1/2-1:1.0/input/input4/event4"
[    52.909] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    52.909] (**) Option "xkb_rules" "evdev"
[    52.909] (**) Option "xkb_model" "pc105"
[    52.909] (**) Option "xkb_layout" "us"
[    52.911] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[    52.911] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    52.911] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    52.911] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    52.911] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.911] (**) Logitech USB Receiver: always reports core events
[    52.911] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[    52.912] (--) Logitech USB Receiver: Found 20 mouse buttons
[    52.912] (--) Logitech USB Receiver: Found scroll wheel(s)
[    52.912] (--) Logitech USB Receiver: Found relative axes
[    52.912] (--) Logitech USB Receiver: Found x and y relative axes
[    52.912] (--) Logitech USB Receiver: Found keys
[    52.912] (II) Logitech USB Receiver: Configuring as mouse
[    52.912] (II) Logitech USB Receiver: Configuring as keyboard
[    52.912] (II) Logitech USB Receiver: Adding scrollwheel support
[    52.912] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    52.912] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    52.912] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.2/usb2/2-1/2-1:1.1/input/input5/event5"
[    52.912] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    52.912] (**) Option "xkb_rules" "evdev"
[    52.912] (**) Option "xkb_model" "pc105"
[    52.912] (**) Option "xkb_layout" "us"
[    52.913] (II) Logitech USB Receiver: initialized for relative axes.
[    52.913] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    52.913] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    52.913] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    52.913] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    52.914] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    52.914] (II) No input driver/identifier specified (ignoring)
[    52.925] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    52.925] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    52.925] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    52.925] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.925] (**) AT Translated Set 2 keyboard: always reports core events
[    52.925] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    52.926] (--) AT Translated Set 2 keyboard: Found keys
[    52.926] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    52.926] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    52.926] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    52.926] (**) Option "xkb_rules" "evdev"
[    52.926] (**) Option "xkb_model" "pc105"
[    52.926] (**) Option "xkb_layout" "us"
[    52.927] (II) config/udev: Adding input device DualPoint Stick (/dev/input/event7)
[    52.927] (**) DualPoint Stick: Applying InputClass "evdev pointer catchall"
[    52.927] (**) DualPoint Stick: Applying InputClass "trackpoint catchall"
[    52.927] (II) Using input driver 'evdev' for 'DualPoint Stick'
[    52.927] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    52.927] (**) DualPoint Stick: always reports core events
[    52.928] (**) DualPoint Stick: Device: "/dev/input/event7"
[    52.928] (--) DualPoint Stick: Found 3 mouse buttons
[    52.928] (--) DualPoint Stick: Found relative axes
[    52.928] (--) DualPoint Stick: Found x and y relative axes
[    52.928] (II) DualPoint Stick: Configuring as mouse
[    52.928] (**) Option "Emulate3Buttons" "true"
[    52.928] (**) Option "EmulateWheel" "true"
[    52.928] (**) Option "EmulateWheelButton" "2"
[    52.928] (**) Option "YAxisMapping" "4 5"
[    52.928] (**) DualPoint Stick: YAxisMapping: buttons 4 and 5
[    52.928] (**) Option "XAxisMapping" "6 7"
[    52.928] (**) DualPoint Stick: XAxisMapping: buttons 6 and 7
[    52.928] (**) DualPoint Stick: EmulateWheelButton: 2, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    52.928] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input7/event7"
[    52.928] (II) XINPUT: Adding extended input device "DualPoint Stick" (type: MOUSE)
[    52.928] (II) DualPoint Stick: initialized for relative axes.
[    52.928] (**) DualPoint Stick: (accel) keeping acceleration scheme 1
[    52.928] (**) DualPoint Stick: (accel) acceleration profile 0
[    52.929] (**) DualPoint Stick: (accel) acceleration factor: 2.000
[    52.929] (**) DualPoint Stick: (accel) acceleration threshold: 4
[    52.929] (II) config/udev: Adding input device DualPoint Stick (/dev/input/mouse1)
[    52.929] (II) No input driver/identifier specified (ignoring)
[    52.930] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/event8)
[    52.930] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "evdev touchpad catchall"
[    52.930] (**) AlpsPS/2 ALPS DualPoint TouchPad: Applying InputClass "touchpad catchall"
[    52.930] (II) LoadModule: "synaptics"
[    52.931] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    52.931] (II) Module synaptics: vendor="X.Org Foundation"
[    52.931]     compiled for 1.10.4, module version = 1.4.1
[    52.931]     Module class: X.Org XInput Driver
[    52.931]     ABI class: X.Org XInput driver, version 12.3
[    52.931] (II) Using input driver 'synaptics' for 'AlpsPS/2 ALPS DualPoint TouchPad'
[    52.931] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    52.931] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    52.931] (**) Option "Device" "/dev/input/event8"
[    52.932] (--) AlpsPS/2 ALPS DualPoint TouchPad: x-axis range 0 - 1023
[    52.932] (--) AlpsPS/2 ALPS DualPoint TouchPad: y-axis range 0 - 767
[    52.932] (--) AlpsPS/2 ALPS DualPoint TouchPad: pressure range 0 - 127
[    52.932] (--) AlpsPS/2 ALPS DualPoint TouchPad: buttons: left right middle
[    52.932] (--) AlpsPS/2 ALPS DualPoint TouchPad: invalid finger width range.  defaulting to 0 - 16
[    52.932] (--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    52.932] (**) AlpsPS/2 ALPS DualPoint TouchPad: always reports core events
[    52.932] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event8"
[    52.932] (II) XINPUT: Adding extended input device "AlpsPS/2 ALPS DualPoint TouchPad" (type: TOUCHPAD)
[    52.932] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    52.932] (**) AlpsPS/2 ALPS DualPoint TouchPad: MaxSpeed is now 1.75
[    52.932] (**) AlpsPS/2 ALPS DualPoint TouchPad: AccelFactor is now 0.156
[    52.932] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) keeping acceleration scheme 1
[    52.933] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration profile 1
[    52.933] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration factor: 2.000
[    52.933] (**) AlpsPS/2 ALPS DualPoint TouchPad: (accel) acceleration threshold: 4
[    52.933] (II) AlpsPS/2 ALPS DualPoint TouchPad: failed to open grail, no gesture support
[    52.933] (--) AlpsPS/2 ALPS DualPoint TouchPad: touchpad found
[    52.934] (II) config/udev: Adding input device AlpsPS/2 ALPS DualPoint TouchPad (/dev/input/mouse2)
[    52.934] (II) No input driver/identifier specified (ignoring)
[    55.147] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   398.963] (II) config/udev: removing device Logitech USB Receiver
[   398.963] (II) Logitech USB Receiver: Close
[   398.963] (II) UnloadModule: "evdev"
[   398.963] (II) Unloading evdev
[   398.986] (II) config/udev: removing device Logitech USB Receiver
[   398.987] (II) Logitech USB Receiver: Close
[   398.987] (II) UnloadModule: "evdev"
[   398.987] (II) Unloading evdev

```One more thing: on the m380 which is + or - working, is it possible to have the toolbar with the "File", "Edit", etc. options attached to each window rather than a global one?

Thanks,

Daniel

---

### Post by danielsender on 2011-10-17
No ideas no the M50?

I just discovered that unity is not working behind a vncserver, the wall paper comes up but the buttons not... sigh...

Daniel

---

### Post by danielsender on 2011-10-17
OK, I found the problem with my M50, see the line 'Option  "UseDisplayDevice"      "DFP"' that indicates that the flat panel display is to be used as the screen. All other issues are still unsolved.

```

Section "Screen"
        Identifier      "Default Screen"
        Option  "AddARGBGLXVisuals"     "True"
        Option  "UseDisplayDevice"      "DFP"
EndSection

Section "Device"
        Identifier      "Default Device"
        Option  "NoLogo"        "True"
EndSection

```

---

