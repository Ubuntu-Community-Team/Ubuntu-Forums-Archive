---
title: "Isolation related computer problems - LOL"
date: 2020-05-26
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2020-05-26
During this period of isolation and no computer stores operating, the graphics card went. Bought a card online along with a second monitor. Now for the problem, when switching user or logging out, the login screen most often does not display for periods as long as an hour and if logging into the bosses (wife's) account there is another long delay while watching the cursor.  I don't have a clue and I can't take it to a local shop. I've also recently upgraded to 20.04 (same result)  Please help - " a happy wife is a happy life"

Thanks 

Graphics card GeForce GTX 1650/PCle/SSE2
Processor AMD Ryzen 2400g 
Gnome 3.36.2
Windowing X11

---

### Post by mastablasta on 2020-05-27
i installed GTX 1650 on my kids PC. never had this issue. my kids CPU is Ryzen 7 2nd gen. did you install proprietary GPU drivers?

check the additional drivers application. how to: [https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-20-04-focal-fossa-linux)

i never also found this issue on opensource nouveau drivers.

tyzen 2400G has onboard GPU, i suggest you try to turn it off in BIOS.

---

### Post by Alligator on 2020-05-27
The NVIDIA is installed correctly, took more than one attempt and the on board GPU is disabled.  The problem is with login displays, why does it take so long?

---

### Post by daniewicz on 2020-05-27
To check for hardware problems during boot: 

```
journalctl -b
```

pay attention to warnings (yellow lines) and errors (red lines (the ones that matter)

---

### Post by Alligator on 2020-05-28
These are ones dealing with BIOS and NVIDIA.  There are several in yellow dealing with gnome window manager.  Thanks for the help.

```

ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has valid Length but zero Address: 0x0000000000000000/0x1 (20190816/tbfadt-615)

ACPI BIOS Error (bug): Failure creating named object [\_SB.SMIC], AE_ALREADY_EXISTS (20190816/dswload2-323)
May 27 18:18:34 crunluath kernel: ACPI Error: AE_ALREADY_EXISTS, During name lookup/catalog (20190816/psobject-220)
May 27 18:18:34 crunluath kernel: ACPI BIOS Error (bug): Failure creating named object [\_SB.SMIB], AE_ALREADY_EXISTS (20190816/dsfield-631)

Trying to unpack rootfs image as initramfs...
Initramfs unpacking failed: Decoding failed

pci 0000:00:00.2: AMD-Vi: Unable to read/write to IOMMU perf counter.
 pci 0000:00:00.2: can't derive routing for PCI INT A
pci 0000:00:00.2: PCI INT A: not connected

 PPR NX GT IA GA PC GA_vAPIC

platform eisa.0: EISA: Cannot allocate resource for mainboard
platform eisa.0: Cannot allocate resource for EISA slot 1
platform eisa.0: Cannot allocate resource for EISA slot 2
platform eisa.0: Cannot allocate resource for EISA slot 3

platform eisa.0: Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
May 27 18:18:34 crunluath kernel: platform eisa.0: Cannot allocate resource for EISA slot 6
May 27 18:18:34 crunluath kernel: platform eisa.0: Cannot allocate resource for EISA slot 7
May 27 18:18:34 crunluath kernel: platform eisa.0: Cannot allocate resource for EISA slot 8
ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.GPP0.VGA.AFN7], AE_NOT_FOUND (20190816/psargs-330)
May 27 18:18:34 crunluath kernel: No Local Variables are initialized for Method [AFN7]
May 27 18:18:34 crunluath kernel: Initialized Arguments for Method [AFN7]:  (1 arguments defined for method invocation)
May 27 18:18:34 crunluath kernel:   Arg0:   00000000b173954f <Obj>           Integer 00000000000000FF
May 27 18:18:34 crunluath kernel: ACPI Error: Aborting method \AFN7 due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
May 27 18:18:34 crunluath kernel: ACPI Error: Aborting method \_SB.PCI0.GPP0.VGA.LCD._BCM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
May 27 18:18:34 crunluath kernel: ACPI Error: Evaluating _BCM failed (20190816/video-357)
nvidia: loading out-of-tree module taints kernel.
May 27 18:18:44 crunluath kernel: nvidia: module license 'NVIDIA' taints kernel.
May 27 18:18:44 crunluath kernel: Disabling lock debugging due to kernel taint

VRM: loading NVIDIA UNIX x86_64 Kernel Module  440.64  Fri Feb 21 01:17:26 UTC 2020

X.Org X Server 1.20.8
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: X Protocol Version 11, Revision 0
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: Build Operating System: Linux 4.4.0-177-generic x86_64 Ubuntu
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: Current Operating System: Linux crunluath 5.4.0-31-generic #35-Ubuntu SMP Thu May 7 20:20:34 UTC 2020 x86_64
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-31-generic root=UUID=ba1ded83-00f0-4bd5-8abf-6f8465db86a1 ro quiet sp>
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: Build Date: 06 April 2020  09:39:29AM
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: xorg-server 2:1.20.8-2ubuntu2 (For technical support please see http://www.ubuntu.com/support)
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: Current version of pixman: 0.38.4
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         Before reporting problems, check http://wiki.x.org
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         to make sure that you have the latest version.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: Markers: (--) probed, (**) from config file, (==) default setting,
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         (++) from command line, (!!) notice, (II) informational,
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) Log file: "/var/log/Xorg.0.log", Time: Wed May 27 18:19:17 2020
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) Using config file: "/etc/X11/xorg.conf"
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) Using system config directory "/usr/share/X11/xorg.conf.d"

(==) ServerLayout "Layout0"
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) |-->Screen "Screen0" (0)
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) |   |-->Monitor "Monitor0"
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) |   |-->Device "Device0"
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) |-->Input Device "Keyboard0"
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) |-->Input Device "Mouse0"
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) Automatically adding devices
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) Automatically enabling devices
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) Automatically adding GPU devices
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) Automatically binding GPU devices
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) Max clients allowed: 256, resource mask: 0x1fffff
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         Entry deleted from font path.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         Entry deleted from font path.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         Entry deleted from font path.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         Entry deleted from font path.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         Entry deleted from font path.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) FontPath set to:


        /usr/share/fonts/X11/misc,
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         /usr/share/fonts/X11/Type1,
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         built-ins
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) ModulePath set to "/usr/lib/xorg/modules"
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (WW) Disabling Keyboard0
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (WW) Disabling Mouse0
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Loader magic: 0x55f9b6672020
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Module ABI versions:
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         X.Org ANSI C Emulation: 0.4
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         X.Org Video Driver: 24.1
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         X.Org XInput driver : 24.1
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         X.Org Server Extension : 10.0
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (++) using VT number 1
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) systemd-logind: took control of session /org/freedesktop/login1/session/c1
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) xfree86: Adding drm device (/dev/dri/card0)
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 12 paused 0
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
May 27 18:19:17 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) PCI:*(16@0:0:0) 10de:1f82:1043:86b9 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I>
May 27 18:19:17 crunluath freshclam[1250]: Wed May 27 18:19:17 2020 -> main.cld database is up to date (version: 59, sigs: 4564902, f-level: 60, builder: sigmgr)

(II) Module glx: vendor="X.Org Foundation"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         compiled for 1.20.8, module version = 1.0.0
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         ABI class: X.Org Server Extension, version 10.0
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) LoadModule: "nvidia"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Module nvidia: vendor="NVIDIA Corporation"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         compiled for 1.6.99.901, module version = 1.0.0
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         Module class: X.Org Video Driver
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA dlloader X Driver  440.64  Fri Feb 21 00:49:33 UTC 2020
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) systemd-logind: releasing fd for 226:0
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Loading sub module "fb"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) LoadModule: "fb"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Loading /usr/lib/xorg/modules/libfb.so
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Module fb: vendor="X.Org Foundation"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         compiled for 1.20.8, module version = 1.0.0
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         ABI class: X.Org ANSI C Emulation, version 0.4
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Loading sub module "wfb"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) LoadModule: "wfb"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Loading /usr/lib/xorg/modules/libwfb.so
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Module wfb: vendor="X.Org Foundation"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         compiled for 1.20.8, module version = 1.0.0
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         ABI class: X.Org ANSI C Emulation, version 0.4
lines 1772-1794

II) Loading sub module "ramdac"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) LoadModule: "ramdac"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Module "ramdac" already built-in
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) NVIDIA(0): RGB weight 888
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) NVIDIA(0): Default visual is TrueColor
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Applying OutputClass "nvidia" options to /dev/dri/card0
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) NVIDIA(0): Enabling 2D acceleration
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Loading sub module "glxserver_nvidia"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) LoadModule: "glxserver_nvidia"
May 27 18:19:18 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/libglxserver_nvidia.so

(II) Module glxserver_nvidia: vendor="NVIDIA Corporation"
May 27 18:19:20 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         compiled for 1.6.99.901, module version = 1.0.0
May 27 18:19:20 crunluath /usr/lib/gdm3/gdm-x-session[1243]:         Module class: X.Org Server Extension

(II) NVIDIA GLX Module  440.64  Fri Feb 21 00:46:14 UTC 2020
May 27 18:19:20 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA: The X server supports PRIME Render Offload.
May 27 18:19:20 crunluath kernel: resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
May 27 18:19:20 crunluath kernel: caller os_map_kernel_space.part.0+0x73/0x80 [nvidia] mapping multiple BARs
 
Unable to get XDG user directory path for special directory &DOCUMENTS. Ignoring this location.
May 27 18:19:21 crunluath tracker-miner-f[1240]: Unable to get XDG user directory path for special directory &MUSIC. Ignoring this location.
May 27 18:19:21 crunluath tracker-miner-f[1240]: Unable to get XDG user directory path for special directory &PICTURES. Ignoring this location.
May 27 18:19:21 crunluath tracker-miner-f[1240]: Unable to get XDG user directory path for special directory &VIDEOS. Ignoring this location.
May 27 18:19:21 crunluath tracker-miner-f[1240]: Unable to get XDG user directory path for special directory &DOWNLOAD. Ignoring this location.
May 27 18:19:21 crunluath tracker-miner-f[1240]: Unable to get XDG user directory path for special directory &DOCUMENTS. Ignoring this location.
May 27 18:19:21 crunluath tracker-miner-f[1240]: Unable to get XDG user directory path for special directory &MUSIC. Ignoring this location.
May 27 18:19:21 crunluath tracker-miner-f[1240]: Unable to get XDG user directory path for special directory &PICTURES. Ignoring this location.
May 27 18:19:21 crunluath tracker-miner-f[1240]: Unable to get XDG user directory path for special directory &VIDEOS. Ignoring this location.
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:16:0:0
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(0):     DFP-0
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(0):     DFP-1 (boot)
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(0):     DFP-2
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(0):     DFP-3
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA(0): NVIDIA GPU GeForce GTX 1650 (TU117-A) at PCI:16:0:0 (GPU-0)
lines 1818-1840

(--) NVIDIA(0): Memory: 4194304 kBytes
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(0): VideoBIOS: 90.17.1c.00.ce
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA(0): Detected PCI Express Link width: 16X
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): BBY DX-24L200A12 (DFP-0): connected
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): BBY DX-24L200A12 (DFP-0): Internal TMDS
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): BBY DX-24L200A12 (DFP-0): 600.0 MHz maximum pixel clock
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0):


(--) NVIDIA(GPU-0): AUS ASUS VP278 (DFP-1): connected
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): AUS ASUS VP278 (DFP-1): Internal TMDS
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): AUS ASUS VP278 (DFP-1): 600.0 MHz maximum pixel clock
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0):
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): DFP-2: disconnected
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): DFP-2: Internal DisplayPort
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): DFP-2: 2660.0 MHz maximum pixel clock
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0):
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): DFP-3: disconnected
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): DFP-3: Internal TMDS
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0): DFP-3: 165.0 MHz maximum pixel clock
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(GPU-0):
==) NVIDIA(0):
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) NVIDIA(0):     will be used as the requested mode.
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) NVIDIA(0):
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA(0): Validated MetaModes:
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA(0):     "DFP-1:nvidia-auto-select,DFP-0:nvidia-auto-select"
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA(0): Virtual screen size determined to be 3840 x 1080
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(0): DPI set to (81, 80); computed from "UseEdidDpi" X config
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (--) NVIDIA(0):     option
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA: Using 24576.00 MB of virtual memory for indirect memory
May 27 18:19:21 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) NVIDIA:     access.

snap.hplip-printer-application.run-server.service: Main process exited, code=killed, status=11/SEGV
May 27 18:19:22 crunluath systemd[1]: snap.hplip-printer-application.run-server.service: Failed with result 'signal'.
May 27 18:19:22 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) NVIDIA(0): Disabling shared memory pixmaps
May 27 18:19:22 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) NVIDIA(0): Backing store enabled
May 27 18:19:22 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (==) NVIDIA(0): Silken mouse enabled
May 27 18:19:22 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (**) NVIDIA(0): DPMS enabled
May 27 18:19:22 crunluath /usr/lib/gdm3/gdm-x-session[1243]: (II) Loading sub module "dri2"

```

---

### Post by daniewicz on 2020-05-28
Well I see several BIOS errors but I am no smart enough to know if they are a problem.

Since we are talking about new hardware, I would suggest clearing the CMOS on the motherboard to return it to default values. Do you know how to do this? There should be a set of two pins on your motherboard labeled CLEAR CMOS (or something close) (see your motherboard manual for location). If you place a jumper across these two pins or touch a screwdriver to both pins while the board is not powered and then reboot you will return to factory defaults.

---

### Post by Alligator on 2020-05-30
I believe that I've come across the main problem.  I launched the monitor app and there is all kinds of processes running which is driving cpu's to 100% capacity.  I did a bit of research and I did a snap remove gnome-system-monitor and then sudo apt install gnome-system-monitor.  NO CHANGE.  I presume this is a bug in 20.04 - I'll keep looking.

---

### Post by Alligator on 2020-05-30
Just got a reply from the manufacture of the motherboard and the BIOS is way out of date. From 1.5 to 3.31.   Is there anyone in the Regina area that could handle this.  Not sure if I want to attempt it.

---

### Post by daniewicz on 2020-05-30
Bios flashes (updates) are much less stressful and complicated today. Not as difficult as it was back in the day. It is probably easier than you think.

I have avoided snap installs as well.

---

### Post by kurt18947 on 2020-05-31
> **daniewicz said:**
> Bios flashes (updates) are much less stressful and complicated today. Not as difficult as it was back in the day. It is probably easier than you think.

I have avoided snap installs as well.

There are often all sorts of dire warnings about not updating BIOS unless necessary but you NEED to update your BIOS. Each motherboard manufacturer is different. In my case - ASROCK - I was able to download the required file to a flash drive. Power the machine down, plug the flash drive into a USB port and power up. When the BIOS menu appears press a certain key and it finds the new BIOS file. Press go and hope you don't lose power until the process completes. The only kink I found is that the flash drive has to be formatted FAT32 and I couldn't use Gparted or Gnome-Disks to format it. The drive wasn't recognized.  I had a new flash drive so used that and it was fine. I imagine that if I formatted the flash drive on Windows that would have worked as well. There is some tiny difference between FAT32 formats using Linux and FAT 32 formats using Windows. Generally it doesn't matter, in this case it did.

---

### Post by mastablasta on 2020-06-01
for monitoring system resources usage you can use top (preinstalled) or htop in terminal.

with ryzens bios sometimes has to be upgraded for them to work correctly. 
on my motherboard that wasn't needed, however i've seen post where Ryzen issues are resolved by bios upgrade.

---

### Post by kurt18947 on 2020-06-02
There were cases where a Ryzen machine simply would not start without a BIOS upgrade. AMD had a program where they would loan pre Ryzen AM4 CPUs to Ryzen purchasers so they could install the loaner CPU, upload a recent BIOS then shut down, swap out the loaner CPU and the machine would then boot with the Ryzen CPU. This was some time ago when Ryzens were fairly new.

---

### Post by Alligator on 2020-06-02
BIOS is updated to L3.31 as per manufacture.  Most bugs related to BIOS are gone.  Below is some clips from journalctl -b.  The problem of cpu's running wild still persists, via monitor program.  Also log in screens or password prompts are slow.


```

ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
Jun 02 15:55:33 crunluath kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.GPP0.VGA.LCD._BCM.AFN7], AE_NOT_FOUND (20190816/psargs-330)
Jun 02 15:55:33 crunluath kernel: 
                                  Initialized Local Variables for Method [_BCM]:
Jun 02 15:55:33 crunluath kernel:   Local0: 00000000f9d3c2fc <Obj>           Integer 00000000000000FF
Jun 02 15:55:33 crunluath kernel:   Local1: 0000000086eec78f <Obj>           Integer 0000000000000000
Jun 02 15:55:33 crunluath kernel: Initialized Arguments for Method [_BCM]:  (1 arguments defined for method invocation)
Jun 02 15:55:33 crunluath kernel:   Arg0:   000000009963dd69 <Obj>           Integer 0000000000000064
Jun 02 15:55:33 crunluath kernel: ACPI Error: Aborting method \_SB.PCI0.GPP0.VGA.LCD._BCM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
Jun 02 15:55:33 crunluath kernel: ACPI Error: Evaluating _BCM failed (20190816/video-357)
Jun 02 15:55:33 crunluath kernel: input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input2
Jun 02 15:55:33 crunluath kernel: ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
Jun 02 15:55:33 crunluath kernel: ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.GP17.VGA.LCD._BCM.AFN7], AE_NOT_FOUND (20190816/psargs-330)


Initialized Local Variables for Method [_BCM]:
Jun 02 15:55:33 crunluath kernel:   Local0: 000000009d5e14d7 <Obj>           Integer 00000000000000FF
Jun 02 15:55:33 crunluath kernel:   Local1: 000000001e8c2e81 <Obj>           Integer 0000000000000000
Jun 02 15:55:33 crunluath kernel: Initialized Arguments for Method [_BCM]:  (1 arguments defined for method invocation)
Jun 02 15:55:33 crunluath kernel:   Arg0:   000000007f6bd489 <Obj>           Integer 0000000000000064
Jun 02 15:55:33 crunluath kernel: ACPI Error: Aborting method \_SB.PCI0.GP17.VGA.LCD._BCM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
Jun 02 15:55:33 crunluath kernel: ACPI Error: Evaluating _BCM failed (20190816/video-357)

nvidia: loading out-of-tree module taints kernel.
Jun 02 15:55:50 crunluath kernel: nvidia: module license 'NVIDIA' taints kernel.
Jun 02 15:55:50 crunluath kernel: Disabling lock debugging due to kernel taint
Jun 02 15:55:50 crunluath kernel: nvidia: module verification failed: signature and/or required key missing - tainting kernel
Jun 02 15:55:50 crunluath kernel: nvidia-nvlink: Nvlink Core is being initialized, major device number 236
Jun 02 15:55:50 crunluath kernel: nvidia 0000:01:00.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=none:owns=io+mem
Jun 02 15:55:50 crunluath kernel: NVRM: loading NVIDIA UNIX x86_64 Kernel Module  440.64  Fri Feb 21 01:17:26 UTC 2020
Jun 02 15:55:50 crunluath kernel: nvidia-modeset: Loading NVIDIA Kernel Mode Setting Driver for UNIX platforms  440.64  Fri Feb 21 00:43:19 UTC 2020
Jun 02 15:55:50 crunluath kernel: [drm] [nvidia-drm] [GPU ID 0x00000100] Loading driver

```

---

### Post by Alligator on 2020-06-04
I reinstalled 20.04 - same problem of run away cpu's. Still getting the error below, with the MB manuf. says is related to the video card.

```

ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.GPP0.VGA.LCD._BCM.AFN7], AE_NOT_FOUND (20190816/psargs-330)
Jun 03 23:15:50 Crunluath kernel: 
                                  Initialized Local Variables for Method [_BCM]:
Jun 03 23:15:50 Crunluath kernel:   Local0: 0000000058059c63 <Obj>           Integer 00000000000000FF
Jun 03 23:15:50 Crunluath kernel:   Local1: 00000000fae444b3 <Obj>           Integer 0000000000000000
Jun 03 23:15:50 Crunluath kernel: Initialized Arguments for Method [_BCM]:  (1 arguments defined for method invocation)
Jun 03 23:15:50 Crunluath kernel:   Arg0:   00000000e259097a <Obj>           Integer 0000000000000064
Jun 03 23:15:50 Crunluath kernel: ACPI Error: Aborting method \_SB.PCI0.GPP0.VGA.LCD._BCM due to previous error (AE_NOT_FOUND) (20190816/psparse-529)
Jun 03 23:15:50 Crunluath kernel: ACPI Error: Evaluating _BCM failed (20190816/video-357)

```

---

### Post by daniewicz on 2020-06-04
Is it possible the new video card is defective?

---

### Post by Alligator on 2020-06-06
Solved - problem was the "tracker" was taking over. It's been permanently removed.  Thanks everyone for their input.

---

### Post by daniewicz on 2020-06-06
What is the tracker?

---

### Post by deadflowr on 2020-06-06
> **daniewicz said:**
> What is the tracker?

If the tracker I'm thinking of it's gnome's indexing service utility.
[https://wiki.gnome.org/Projects/Tracker]("https://wiki.gnome.org/Projects/Tracker")

Seems kind of common for indexing services to run amok.
Happens for some users with baloo in kde too.

---

### Post by daniewicz on 2020-06-06
Thanks. I am a new Ubuntu user having recently switched from KDE focused Mageia. Still learning.

---

