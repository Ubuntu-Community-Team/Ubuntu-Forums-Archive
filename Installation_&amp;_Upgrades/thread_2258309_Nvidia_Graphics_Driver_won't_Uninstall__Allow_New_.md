---
title: "Nvidia Graphics Driver won't Uninstall / Allow New Driver to install"
date: 2014-12-26
forum: Installation &amp; Upgrades
---

### Post by ChaoticFlounder on 2014-12-26
Hi Guys ... and to the Ladies that are on here as well,

I am having trouble installing a new graphics driver on my machine.  I have been doing a fair bit of searching around and I believe I am missing the xorg.conf file and have a xorg.conf.failsafe file instead in the /etc/X11 directory.  Anyways, the long and short of it is I am unable to uninstall driver 340.65 or install any other nvidia driver as it gets hung up on nvidia driver 340.  I am "newish to medium" in Ubuntu experience and may have done something in the process of getting to where I am in messing up the 340.65 installation.  The card I have is a GTX680 and I understand that certain command line returns will give you the necessary information to properly diagnose the problem, but I do not know what they are atm.  Please let me know if you know what the problem is or if there is anything i can do to help resolve it.

Thanks,

C

---

### Post by MAFoElffen on 2014-12-26
Wait-- You say you have old nVidia drivers installed, but there is no /etc/X11/xorg.conf file present? If not present, then there is nothing there saying to use those drivers.

Or are you saying you are installing new drivers (somehow- see below) and at present, don't have an xorg.conf file yet?

If so, then which flavor of nvidia drivers did you install? The Ubuntu nvidia driver package? Or nVidia's binary driver installer?

Please post the results of:
```

lspci -vvn | grep -i VGA
ls /etc/X11/xorg.*
cat /var/log.Xorg.0.log

```

---

### Post by ChaoticFlounder on 2014-12-26
Thanks for the quick reply MAFoElffen,

Currently I believe I have the 340.65 binary driver installed from the Ubuntu repositories.  I have had it on here since about the time it came out and have been noticing little quirks in the display ever since.  Today I decided to see if I could solve the problem and discovered what I mentioned earlier.  Here are the returns of the commands listed below, in their respective orders...

1.
```
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
03:00.0 0300: 10de:1180 (rev a1) (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+


```

2.
```
/etc/X11/xorg.conf.failsafe
```

3.
```
cat: /var/log.Xorg.0.log: No such file or directory
```

---

### Post by MAFoElffen on 2014-12-26
Sorry, not enough coffee and I typo'ed the last. Should have been:
```

cat /var/log/Xorg.0.log

```
What model Nvidia card do you say you have?

To confirm that:
```

sudo apt-get install lshw
#and post the results of 
sudo lshw -numeric -class video

```

---

### Post by ChaoticFlounder on 2014-12-26
No worries,

I appreciate the help :)

cat /var/log/Xorg.0.log
```
[     3.745]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     3.745] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.745] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec 26 13:57:17 2014
[     3.746] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.746] (==) No Layout section.  Using the first Screen section.
[     3.746] (==) No screen section available. Using defaults.
[     3.746] (**) |-->Screen "Default Screen Section" (0)
[     3.746] (**) |   |-->Monitor "<default monitor>"
[     3.746] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     3.746] (==) Automatically adding devices
[     3.746] (==) Automatically enabling devices
[     3.746] (==) Automatically adding GPU devices
[     3.746] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.746]     Entry deleted from font path.
[     3.746] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.746]     Entry deleted from font path.
[     3.746] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.746]     Entry deleted from font path.
[     3.746] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.746]     Entry deleted from font path.
[     3.746] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.746]     Entry deleted from font path.
[     3.746] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     3.746] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.746] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.746] (II) Loader magic: 0x7fd913eb3d40
[     3.746] (II) Module ABI versions:
[     3.746]     X.Org ANSI C Emulation: 0.4
[     3.746]     X.Org Video Driver: 15.0
[     3.746]     X.Org XInput driver : 20.0
[     3.746]     X.Org Server Extension : 8.0
[     3.746] (II) xfree86: Adding drm device (/dev/dri/card0)
[     3.747] (II) xfree86: Adding drm device (/dev/dri/card1)
[     3.748] (--) PCI: (0:0:2:0) 8086:0162:1849:0162 rev 9, Mem @ 0xf6400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[     3.748] (--) PCI:*(0:3:0:0) 10de:1180:3842:2683 rev 161, Mem @ 0xf5000000/16777216, 0xe0000000/134217728, 0xe8000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     3.748] Initializing built-in extension Generic Event Extension
[     3.748] Initializing built-in extension SHAPE
[     3.748] Initializing built-in extension MIT-SHM
[     3.748] Initializing built-in extension XInputExtension
[     3.748] Initializing built-in extension XTEST
[     3.748] Initializing built-in extension BIG-REQUESTS
[     3.748] Initializing built-in extension SYNC
[     3.748] Initializing built-in extension XKEYBOARD
[     3.748] Initializing built-in extension XC-MISC
[     3.749] Initializing built-in extension SECURITY
[     3.749] Initializing built-in extension XINERAMA
[     3.749] Initializing built-in extension XFIXES
[     3.749] Initializing built-in extension RENDER
[     3.749] Initializing built-in extension RANDR
[     3.749] Initializing built-in extension COMPOSITE
[     3.749] Initializing built-in extension DAMAGE
[     3.749] Initializing built-in extension MIT-SCREEN-SAVER
[     3.749] Initializing built-in extension DOUBLE-BUFFER
[     3.749] Initializing built-in extension RECORD
[     3.749] Initializing built-in extension DPMS
[     3.749] Initializing built-in extension Present
[     3.749] Initializing built-in extension DRI3
[     3.749] Initializing built-in extension X-Resource
[     3.749] Initializing built-in extension XVideo
[     3.749] Initializing built-in extension XVideo-MotionCompensation
[     3.749] Initializing built-in extension SELinux
[     3.749] Initializing built-in extension XFree86-VidModeExtension
[     3.749] Initializing built-in extension XFree86-DGA
[     3.749] Initializing built-in extension XFree86-DRI
[     3.749] Initializing built-in extension DRI2
[     3.749] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[     3.749] (II) "glx" will be loaded by default.
[     3.749] (WW) "xmir" is not to be loaded by default. Skipping.
[     3.749] (II) LoadModule: "glx"
[     3.749] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     3.756] (II) Module glx: vendor="NVIDIA Corporation"
[     3.756]     compiled for 4.0.2, module version = 1.0.0
[     3.756]     Module class: X.Org Server Extension
[     3.756] (II) NVIDIA GLX Module  340.65  Tue Dec  2 09:10:06 PST 2014
[     3.756] Loading extension GLX
[     3.756] (==) Matched nvidia as autoconfigured driver 0
[     3.756] (==) Matched nouveau as autoconfigured driver 1
[     3.756] (==) Matched intel as autoconfigured driver 2
[     3.756] (==) Matched nvidia as autoconfigured driver 3
[     3.756] (==) Matched nouveau as autoconfigured driver 4
[     3.756] (==) Matched modesetting as autoconfigured driver 5
[     3.756] (==) Matched fbdev as autoconfigured driver 6
[     3.756] (==) Matched vesa as autoconfigured driver 7
[     3.756] (==) Assigned the driver to the xf86ConfigLayout
[     3.756] (II) LoadModule: "nvidia"
[     3.756] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     3.756] (II) Module nvidia: vendor="NVIDIA Corporation"
[     3.756]     compiled for 4.0.2, module version = 1.0.0
[     3.756]     Module class: X.Org Video Driver
[     3.756] (II) LoadModule: "nouveau"
[     3.756] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     3.757] (II) Module nouveau: vendor="X.Org Foundation"
[     3.757]     compiled for 1.15.1, module version = 1.0.11
[     3.757]     Module class: X.Org Video Driver
[     3.757]     ABI class: X.Org Video Driver, version 15.0
[     3.757] (II) LoadModule: "intel"
[     3.757] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.758] (II) Module intel: vendor="X.Org Foundation"
[     3.758]     compiled for 1.15.1, module version = 2.99.916
[     3.758]     Module class: X.Org Video Driver
[     3.758]     ABI class: X.Org Video Driver, version 15.0
[     3.758] (II) LoadModule: "modesetting"
[     3.758] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     3.758] (II) Module modesetting: vendor="X.Org Foundation"
[     3.758]     compiled for 1.15.0, module version = 0.8.1
[     3.758]     Module class: X.Org Video Driver
[     3.758]     ABI class: X.Org Video Driver, version 15.0
[     3.758] (II) LoadModule: "fbdev"
[     3.758] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.758] (II) Module fbdev: vendor="X.Org Foundation"
[     3.758]     compiled for 1.15.0, module version = 0.4.4
[     3.758]     Module class: X.Org Video Driver
[     3.759]     ABI class: X.Org Video Driver, version 15.0
[     3.759] (II) LoadModule: "vesa"
[     3.759] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.759] (II) Module vesa: vendor="X.Org Foundation"
[     3.759]     compiled for 1.15.0, module version = 2.3.3
[     3.759]     Module class: X.Org Video Driver
[     3.759]     ABI class: X.Org Video Driver, version 15.0
[     3.759] (II) NVIDIA dlloader X Driver  340.65  Tue Dec  2 08:47:36 PST 2014
[     3.759] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     3.759] (II) NOUVEAU driver 
[     3.759] (II) NOUVEAU driver for NVIDIA chipset families :
[     3.759]     RIVA TNT        (NV04)
[     3.759]     RIVA TNT2       (NV05)
[     3.759]     GeForce 256     (NV10)
[     3.759]     GeForce 2       (NV11, NV15)
[     3.759]     GeForce 4MX     (NV17, NV18)
[     3.759]     GeForce 3       (NV20)
[     3.759]     GeForce 4Ti     (NV25, NV28)
[     3.759]     GeForce FX      (NV3x)
[     3.759]     GeForce 6       (NV4x)
[     3.759]     GeForce 7       (G7x)
[     3.759]     GeForce 8       (G8x)
[     3.759]     GeForce GTX 200 (NVA0)
[     3.759]     GeForce GTX 400 (NVC0)
[     3.759] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     3.759] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     3.759] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     3.759] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     3.759] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     3.759] (II) FBDEV: driver for framebuffer: fbdev
[     3.759] (II) VESA: driver for VESA chipsets: vesa
[     3.759] (++) using VT number 7

[     3.759] (II) Loading sub module "fb"
[     3.759] (II) LoadModule: "fb"
[     3.759] (II) Loading /usr/lib/xorg/modules/libfb.so
[     3.759] (II) Module fb: vendor="X.Org Foundation"
[     3.759]     compiled for 1.15.1, module version = 1.0.0
[     3.759]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.759] (WW) Unresolved symbol: fbGetGCPrivateKey
[     3.759] (II) Loading sub module "wfb"
[     3.759] (II) LoadModule: "wfb"
[     3.760] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     3.760] (II) Module wfb: vendor="X.Org Foundation"
[     3.760]     compiled for 1.15.1, module version = 1.0.0
[     3.760]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.760] (II) Loading sub module "ramdac"
[     3.760] (II) LoadModule: "ramdac"
[     3.760] (II) Module "ramdac" already built-in
[     3.760] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[     3.760] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.916+git20141215.99537089-0ubuntu0sarvatt~trusty (Robert Hooker <sarvatt@ubuntu.com>)
[     3.760] (II) intel(G0): SNA compiled for use with valgrind
[     3.760] (WW) Falling back to old probe method for modesetting
[     3.760] (WW) Falling back to old probe method for fbdev
[     3.760] (II) Loading sub module "fbdevhw"
[     3.760] (II) LoadModule: "fbdevhw"
[     3.761] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     3.761] (II) Module fbdevhw: vendor="X.Org Foundation"
[     3.761]     compiled for 1.15.1, module version = 0.0.2
[     3.761]     ABI class: X.Org Video Driver, version 15.0
[     3.761] (WW) Falling back to old probe method for vesa
[     3.761] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     3.761] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[     3.761] (==) NVIDIA(0): RGB weight 888
[     3.761] (==) NVIDIA(0): Default visual is TrueColor
[     3.761] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     3.761] (**) NVIDIA(0): Enabling 2D acceleration
[     4.825] (II) NVIDIA(0): Display (Ancor Communications Inc VW246 (DFP-3)) does not
[     4.825] (II) NVIDIA(0):     support NVIDIA 3D Vision stereo.
[     4.825] (II) NVIDIA(GPU-0): Found DRM driver nvidia-drm (20130102)
[     4.826] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 680 (GK104) at PCI:3:0:0 (GPU-0)
[     4.826] (--) NVIDIA(0): Memory: 2097152 kBytes
[     4.826] (--) NVIDIA(0): VideoBIOS: 80.04.09.00.b7
[     4.826] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     4.829] (--) NVIDIA(0): Valid display device(s) on GeForce GTX 680 at PCI:3:0:0
[     4.829] (--) NVIDIA(0):     CRT-0
[     4.829] (--) NVIDIA(0):     DFP-0
[     4.829] (--) NVIDIA(0):     DFP-1
[     4.829] (--) NVIDIA(0):     DFP-2
[     4.829] (--) NVIDIA(0):     Ancor Communications Inc VW246 (DFP-3) (boot, connected)
[     4.829] (--) NVIDIA(0):     DFP-4
[     4.829] (--) NVIDIA(GPU-0): CRT-0: 400.0 MHz maximum pixel clock
[     4.829] (--) NVIDIA(0): DFP-0: Internal TMDS
[     4.829] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[     4.829] (--) NVIDIA(0): DFP-1: Internal TMDS
[     4.829] (--) NVIDIA(GPU-0): DFP-1: 165.0 MHz maximum pixel clock
[     4.829] (--) NVIDIA(0): DFP-2: Internal TMDS
[     4.829] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[     4.829] (--) NVIDIA(0): Ancor Communications Inc VW246 (DFP-3): Internal TMDS
[     4.829] (--) NVIDIA(GPU-0): Ancor Communications Inc VW246 (DFP-3): 330.0 MHz maximum pixel clock
[     4.829] (--) NVIDIA(0): DFP-4: Internal DisplayPort
[     4.829] (--) NVIDIA(GPU-0): DFP-4: 960.0 MHz maximum pixel clock
[     4.829] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[     4.829] (**) NVIDIA(0):     device Ancor Communications Inc VW246 (DFP-3) (Using EDID
[     4.829] (**) NVIDIA(0):     frequencies has been enabled on all display devices.)
[     4.830] (==) NVIDIA(0): 
[     4.830] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     4.830] (==) NVIDIA(0):     will be used as the requested mode.
[     4.830] (==) NVIDIA(0): 
[     4.830] (II) NVIDIA(0): Validated MetaModes:
[     4.830] (II) NVIDIA(0):     "DFP-3:nvidia-auto-select"
[     4.830] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[     4.855] (--) NVIDIA(0): DPI set to (92, 91); computed from "UseEdidDpi" X config
[     4.855] (--) NVIDIA(0):     option
[     4.855] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4000
[     4.855] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx
[     4.855] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[     4.855] (==) intel(G0): RGB weight 888
[     4.855] (==) intel(G0): Default visual is TrueColor
[     4.855] (II) intel(G0): Output VGA1 has no monitor section
[     4.855] (II) intel(G0): Enabled output VGA1
[     4.855] (II) intel(G0): Output HDMI1 has no monitor section
[     4.855] (II) intel(G0): Enabled output HDMI1
[     4.855] (II) intel(G0): Output DP1 has no monitor section
[     4.855] (II) intel(G0): Enabled output DP1
[     4.855] (--) intel(G0): Using a maximum size of 64x64 for hardware cursors
[     4.855] (II) intel(G0): Output VIRTUAL1 has no monitor section
[     4.855] (II) intel(G0): Enabled output VIRTUAL1
[     4.855] (==) intel(G0): TearFree disabled
[     4.855] (==) intel(G0): DPI set to (96, 96)
[     4.855] (II) Loading sub module "dri2"
[     4.855] (II) LoadModule: "dri2"
[     4.855] (II) Module "dri2" already built-in
[     4.855] (II) Loading sub module "present"
[     4.855] (II) LoadModule: "present"
[     4.855] (WW) Warning, couldn't open module present
[     4.855] (II) UnloadModule: "present"
[     4.855] (II) Unloading present
[     4.855] (EE) intel: Failed to load module "present" (module does not exist, 0)
[     4.855] (II) UnloadModule: "nouveau"
[     4.855] (II) Unloading nouveau
[     4.855] (II) UnloadModule: "modesetting"
[     4.855] (II) Unloading modesetting
[     4.855] (II) UnloadModule: "fbdev"
[     4.855] (II) Unloading fbdev
[     4.855] (II) UnloadSubModule: "fbdevhw"
[     4.855] (II) Unloading fbdevhw
[     4.855] (II) UnloadModule: "vesa"
[     4.855] (II) Unloading vesa
[     4.855] (--) Depth 24 pixmap format is 32 bpp
[     4.856] (II) intel(G0): SNA initialized with Ivybridge (gen7, gt2) backend
[     4.856] (==) intel(G0): Backing store enabled
[     4.856] (==) intel(G0): Silken mouse enabled
[     4.856] (II) intel(G0): HW Cursor enabled
[     4.856] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     4.856] (==) intel(G0): DPMS enabled
[     4.856] (==) intel(G0): display hotplug detection enabled
[     4.856] (II) intel(G0): [DRI2] Setup complete
[     4.856] (II) intel(G0): [DRI2]   DRI driver: i965
[     4.856] (II) intel(G0): [DRI2]   VDPAU driver: i965
[     4.856] (II) intel(G0): direct rendering: DRI2 enabled
[     4.856] (II) NVIDIA: Using 3072.00 MB of virtual memory for indirect memory
[     4.856] (II) NVIDIA:     access.
[     4.860] (II) NVIDIA(0): Setting mode "DFP-3:nvidia-auto-select"
[     4.898] Loading extension NV-GLX
[     4.917] (==) NVIDIA(0): Disabling shared memory pixmaps
[     4.917] (==) NVIDIA(0): Backing store enabled
[     4.917] (==) NVIDIA(0): Silken mouse enabled
[     4.917] (==) NVIDIA(0): DPMS enabled
[     4.917] Loading extension NV-CONTROL
[     4.918] Loading extension XINERAMA
[     4.918] (II) Loading sub module "dri2"
[     4.918] (II) LoadModule: "dri2"
[     4.918] (II) Module "dri2" already built-in
[     4.918] (II) NVIDIA(0): [DRI2] Setup complete
[     4.918] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     4.918] (--) RandR disabled
[     4.921] (II) SELinux: Disabled on system
[     4.921] (II) Initializing extension GLX
[     4.931] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     4.933] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     4.933] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.933] (II) LoadModule: "evdev"
[     4.933] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     4.935] (II) Module evdev: vendor="X.Org Foundation"
[     4.935]     compiled for 1.15.0, module version = 2.8.2
[     4.935]     Module class: X.Org XInput Driver
[     4.935]     ABI class: X.Org XInput driver, version 20.0
[     4.935] (II) Using input driver 'evdev' for 'Power Button'
[     4.935] (**) Power Button: always reports core events
[     4.935] (**) evdev: Power Button: Device: "/dev/input/event1"
[     4.935] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.935] (--) evdev: Power Button: Found keys
[     4.935] (II) evdev: Power Button: Configuring as keyboard
[     4.935] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     4.935] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     4.935] (**) Option "xkb_rules" "evdev"
[     4.935] (**) Option "xkb_model" "pc105"
[     4.935] (**) Option "xkb_layout" "us"
[     4.935] (II) config/udev: Adding input device Video Bus (/dev/input/event2)
[     4.935] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     4.935] (II) Using input driver 'evdev' for 'Video Bus'
[     4.935] (**) Video Bus: always reports core events
[     4.935] (**) evdev: Video Bus: Device: "/dev/input/event2"
[     4.935] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     4.935] (--) evdev: Video Bus: Found keys
[     4.935] (II) evdev: Video Bus: Configuring as keyboard
[     4.935] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5/event2"
[     4.935] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     4.935] (**) Option "xkb_rules" "evdev"
[     4.935] (**) Option "xkb_model" "pc105"
[     4.935] (**) Option "xkb_layout" "us"
[     4.935] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     4.935] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     4.935] (II) Using input driver 'evdev' for 'Power Button'
[     4.935] (**) Power Button: always reports core events
[     4.935] (**) evdev: Power Button: Device: "/dev/input/event0"
[     4.935] (--) evdev: Power Button: Vendor 0 Product 0x1
[     4.935] (--) evdev: Power Button: Found keys
[     4.935] (II) evdev: Power Button: Configuring as keyboard
[     4.935] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     4.935] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     4.935] (**) Option "xkb_rules" "evdev"
[     4.935] (**) Option "xkb_model" "pc105"
[     4.935] (**) Option "xkb_layout" "us"
[     4.935] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/0000:02:08.0/0000:03:00.0/drm/card0
[     4.935] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     4.936] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event14)
[     4.936] (II) No input driver specified, ignoring this device.
[     4.936] (II) This device may have been added with another device file.
[     4.936] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event13)
[     4.936] (II) No input driver specified, ignoring this device.
[     4.936] (II) This device may have been added with another device file.
[     4.936] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event12)
[     4.936] (II) No input driver specified, ignoring this device.
[     4.936] (II) This device may have been added with another device file.
[     4.936] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event11)
[     4.936] (II) No input driver specified, ignoring this device.
[     4.936] (II) This device may have been added with another device file.
[     4.936] (II) config/udev: Adding drm device (/dev/dri/card1) card1 /sys/devices/pci0000:00/0000:00:02.0/drm/card1
[     4.936] (II) config/udev: Ignoring already known drm device (/dev/dri/card1)
[     4.936] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event6)
[     4.936] (II) No input driver specified, ignoring this device.
[     4.936] (II) This device may have been added with another device file.
[     4.936] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event5)
[     4.936] (II) No input driver specified, ignoring this device.
[     4.936] (II) This device may have been added with another device file.
[     4.936] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event4)
[     4.936] (II) No input driver specified, ignoring this device.
[     4.936] (II) This device may have been added with another device file.
[     4.936] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event3)
[     4.936] (II) No input driver specified, ignoring this device.
[     4.936] (II) This device may have been added with another device file.
[     4.937] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event10)
[     4.937] (II) No input driver specified, ignoring this device.
[     4.937] (II) This device may have been added with another device file.
[     4.937] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event9)
[     4.937] (II) No input driver specified, ignoring this device.
[     4.937] (II) This device may have been added with another device file.
[     4.937] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event8)
[     4.937] (II) No input driver specified, ignoring this device.
[     4.937] (II) This device may have been added with another device file.
[     4.937] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event7)
[     4.937] (II) No input driver specified, ignoring this device.
[     4.937] (II) This device may have been added with another device file.
[     4.937] (II) config/udev: Adding input device Corsair Corsair Vengeance K90 Keyboard (/dev/input/event15)
[     4.937] (**) Corsair Corsair Vengeance K90 Keyboard: Applying InputClass "evdev keyboard catchall"
[     4.937] (II) Using input driver 'evdev' for 'Corsair Corsair Vengeance K90 Keyboard'
[     4.937] (**) Corsair Corsair Vengeance K90 Keyboard: always reports core events
[     4.937] (**) evdev: Corsair Corsair Vengeance K90 Keyboard: Device: "/dev/input/event15"
[     4.937] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Vendor 0x1b1c Product 0x1b02
[     4.937] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Found keys
[     4.937] (II) evdev: Corsair Corsair Vengeance K90 Keyboard: Configuring as keyboard
[     4.937] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.7/0000:08:00.0/0000:09:07.0/0000:0e:00.0/usb5/5-1/5-1:1.0/input/input18/event15"
[     4.937] (II) XINPUT: Adding extended input device "Corsair Corsair Vengeance K90 Keyboard" (type: KEYBOARD, id 9)
[     4.937] (**) Option "xkb_rules" "evdev"
[     4.937] (**) Option "xkb_model" "pc105"
[     4.937] (**) Option "xkb_layout" "us"
[     4.937] (II) config/udev: Adding input device Corsair Corsair Vengeance K90 Keyboard (/dev/input/event16)
[     4.937] (**) Corsair Corsair Vengeance K90 Keyboard: Applying InputClass "evdev keyboard catchall"
[     4.937] (II) Using input driver 'evdev' for 'Corsair Corsair Vengeance K90 Keyboard'
[     4.937] (**) Corsair Corsair Vengeance K90 Keyboard: always reports core events
[     4.937] (**) evdev: Corsair Corsair Vengeance K90 Keyboard: Device: "/dev/input/event16"
[     4.937] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Vendor 0x1b1c Product 0x1b02
[     4.937] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Found 1 mouse buttons
[     4.937] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Found scroll wheel(s)
[     4.937] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Found relative axes
[     4.937] (II) evdev: Corsair Corsair Vengeance K90 Keyboard: Forcing relative x/y axes to exist.
[     4.938] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Found absolute axes
[     4.938] (II) evdev: Corsair Corsair Vengeance K90 Keyboard: Forcing absolute x/y axes to exist.
[     4.938] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Found keys
[     4.938] (II) evdev: Corsair Corsair Vengeance K90 Keyboard: Configuring as mouse
[     4.938] (II) evdev: Corsair Corsair Vengeance K90 Keyboard: Configuring as keyboard
[     4.938] (II) evdev: Corsair Corsair Vengeance K90 Keyboard: Adding scrollwheel support
[     4.938] (**) evdev: Corsair Corsair Vengeance K90 Keyboard: YAxisMapping: buttons 4 and 5
[     4.938] (**) evdev: Corsair Corsair Vengeance K90 Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.938] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.7/0000:08:00.0/0000:09:07.0/0000:0e:00.0/usb5/5-1/5-1:1.1/input/input19/event16"
[     4.938] (II) XINPUT: Adding extended input device "Corsair Corsair Vengeance K90 Keyboard" (type: KEYBOARD, id 10)
[     4.938] (**) Option "xkb_rules" "evdev"
[     4.938] (**) Option "xkb_model" "pc105"
[     4.938] (**) Option "xkb_layout" "us"
[     4.938] (II) evdev: Corsair Corsair Vengeance K90 Keyboard: initialized for relative axes.
[     4.938] (WW) evdev: Corsair Corsair Vengeance K90 Keyboard: ignoring absolute axes.
[     4.938] (**) Corsair Corsair Vengeance K90 Keyboard: (accel) keeping acceleration scheme 1
[     4.938] (**) Corsair Corsair Vengeance K90 Keyboard: (accel) acceleration profile 0
[     4.938] (**) Corsair Corsair Vengeance K90 Keyboard: (accel) acceleration factor: 2.000
[     4.938] (**) Corsair Corsair Vengeance K90 Keyboard: (accel) acceleration threshold: 4
[     4.938] (II) config/udev: Adding input device Corsair Corsair Vengeance K90 Keyboard (/dev/input/event17)
[     4.938] (**) Corsair Corsair Vengeance K90 Keyboard: Applying InputClass "evdev keyboard catchall"
[     4.938] (II) Using input driver 'evdev' for 'Corsair Corsair Vengeance K90 Keyboard'
[     4.938] (**) Corsair Corsair Vengeance K90 Keyboard: always reports core events
[     4.938] (**) evdev: Corsair Corsair Vengeance K90 Keyboard: Device: "/dev/input/event17"
[     4.938] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Vendor 0x1b1c Product 0x1b02
[     4.938] (--) evdev: Corsair Corsair Vengeance K90 Keyboard: Found keys
[     4.938] (II) evdev: Corsair Corsair Vengeance K90 Keyboard: Configuring as keyboard
[     4.938] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.7/0000:08:00.0/0000:09:07.0/0000:0e:00.0/usb5/5-1/5-1:1.2/input/input20/event17"
[     4.938] (II) XINPUT: Adding extended input device "Corsair Corsair Vengeance K90 Keyboard" (type: KEYBOARD, id 11)
[     4.938] (**) Option "xkb_rules" "evdev"
[     4.938] (**) Option "xkb_model" "pc105"
[     4.938] (**) Option "xkb_layout" "us"
[     4.938] (II) config/udev: Adding input device ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp (/dev/input/event18)
[     4.938] (**) ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: Applying InputClass "evdev keyboard catchall"
[     4.938] (II) Using input driver 'evdev' for 'ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp'
[     4.938] (**) ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: always reports core events
[     4.938] (**) evdev: ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: Device: "/dev/input/event18"
[     4.938] (--) evdev: ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: Vendor 0xd8c Product 0x13c
[     4.938] (--) evdev: ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: Found 1 mouse buttons
[     4.938] (--) evdev: ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: Found keys
[     4.938] (II) evdev: ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: Forcing relative x/y axes to exist.
[     4.938] (II) evdev: ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: Configuring as mouse
[     4.938] (II) evdev: ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: Configuring as keyboard
[     4.938] (**) evdev: ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: YAxisMapping: buttons 4 and 5
[     4.938] (**) evdev: ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     4.938] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1c.7/0000:08:00.0/0000:09:07.0/0000:0e:00.0/usb5/5-3/5-3:1.3/input/input21/event18"
[     4.938] (II) XINPUT: Adding extended input device "ETHER ELECTRONICS CO.,LTD. ASTRO Gaming USB MixAmp" (type: KEYBOARD, id 12)
[     4.938] (**) Option "xkb_rules" "evdev"
[     4.938] (**) Option "xkb_model" "pc105"
[     4.938] (**) Option "xkb_layout" "us"
[     5.216] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc VW246 (DFP-3)) does not
[     5.216] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[     5.452] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc VW246 (DFP-3)) does not
[     5.452] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    17.748] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc VW246 (DFP-3)) does not
[    17.748] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    17.901] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc VW246 (DFP-3)) does not
[    17.901] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    17.917] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.061] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc VW246 (DFP-3)) does not
[    19.061] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    19.091] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.098] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    19.135] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc VW246 (DFP-3)) does not
[    19.135] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    19.714] (II) XKB: reuse xkmfile /var/lib/xkb/server-34CEB476A3CB596DA76FD7010A029F76732EF824.xkm
[    22.153] (II) config/udev: Adding input device La-VIEW Technology SteelSeries   (/dev/input/event19)
[    22.153] (**) La-VIEW Technology SteelSeries  : Applying InputClass "evdev pointer catchall"
[    22.153] (II) Using input driver 'evdev' for 'La-VIEW Technology SteelSeries  '
[    22.153] (**) La-VIEW Technology SteelSeries  : always reports core events
[    22.153] (**) evdev: La-VIEW Technology SteelSeries  : Device: "/dev/input/event19"
[    22.153] (--) evdev: La-VIEW Technology SteelSeries  : Vendor 0x1038 Product 0x1361
[    22.153] (--) evdev: La-VIEW Technology SteelSeries  : Found 12 mouse buttons
[    22.153] (--) evdev: La-VIEW Technology SteelSeries  : Found scroll wheel(s)
[    22.153] (--) evdev: La-VIEW Technology SteelSeries  : Found relative axes
[    22.153] (--) evdev: La-VIEW Technology SteelSeries  : Found x and y relative axes
[    22.153] (II) evdev: La-VIEW Technology SteelSeries  : Configuring as mouse
[    22.153] (II) evdev: La-VIEW Technology SteelSeries  : Adding scrollwheel support
[    22.153] (**) evdev: La-VIEW Technology SteelSeries  : YAxisMapping: buttons 4 and 5
[    22.153] (**) evdev: La-VIEW Technology SteelSeries  : EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.153] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input22/event19"
[    22.153] (II) XINPUT: Adding extended input device "La-VIEW Technology SteelSeries  " (type: MOUSE, id 13)
[    22.154] (II) evdev: La-VIEW Technology SteelSeries  : initialized for relative axes.
[    22.155] (**) La-VIEW Technology SteelSeries  : (accel) keeping acceleration scheme 1
[    22.155] (**) La-VIEW Technology SteelSeries  : (accel) acceleration profile 0
[    22.155] (**) La-VIEW Technology SteelSeries  : (accel) acceleration factor: 2.000
[    22.155] (**) La-VIEW Technology SteelSeries  : (accel) acceleration threshold: 4
[    22.155] (II) config/udev: Adding input device La-VIEW Technology SteelSeries   (/dev/input/event20)
[    22.155] (**) La-VIEW Technology SteelSeries  : Applying InputClass "evdev keyboard catchall"
[    22.155] (II) Using input driver 'evdev' for 'La-VIEW Technology SteelSeries  '
[    22.155] (**) La-VIEW Technology SteelSeries  : always reports core events
[    22.155] (**) evdev: La-VIEW Technology SteelSeries  : Device: "/dev/input/event20"
[    22.155] (--) evdev: La-VIEW Technology SteelSeries  : Vendor 0x1038 Product 0x1361
[    22.155] (--) evdev: La-VIEW Technology SteelSeries  : Found keys
[    22.155] (II) evdev: La-VIEW Technology SteelSeries  : Configuring as keyboard
[    22.155] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.1/input/input23/event20"
[    22.155] (II) XINPUT: Adding extended input device "La-VIEW Technology SteelSeries  " (type: KEYBOARD, id 14)
[    22.155] (**) Option "xkb_rules" "evdev"
[    22.155] (**) Option "xkb_model" "pc105"
[    22.155] (**) Option "xkb_layout" "us"
[    22.156] (II) config/udev: Adding input device La-VIEW Technology SteelSeries   (/dev/input/mouse0)
[    22.156] (II) No input driver specified, ignoring this device.
[    22.156] (II) This device may have been added with another device file.
[    22.162] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.687] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc VW246 (DFP-3)) does not
[    29.687] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.
[    34.835] (II) NVIDIA(GPU-0): Display (Ancor Communications Inc VW246 (DFP-3)) does not
[    34.835] (II) NVIDIA(GPU-0):     support NVIDIA 3D Vision stereo.


```

I realize you did not ask me to post this but this is the return line when I input the command:  
sudo apt-get install lshw

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lshw is already the newest version.
The following packages were automatically installed and are no longer required:
  bbswitch-dkms cli-common libgdiplus libgif4 libglib2.0-cil libgtk2.0-cil
  libmono-cairo4.0-cil libmono-corlib4.0-cil libmono-corlib4.5-cil
  libmono-csharp4.0c-cil libmono-i18n-west4.0-cil libmono-i18n4.0-cil
  libmono-posix4.0-cil libmono-security4.0-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-drawing4.0-cil libmono-system-security4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libvdpau1
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-headers-generic linux-image-3.13.0-32-generic
  linux-image-extra-3.13.0-32-generic linux-image-generic mono-4.0-gac
  mono-gac mono-runtime mono-runtime-common mono-runtime-sgen python-ply
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-340
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 269 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 303526 files and directories currently installed.)
Removing nvidia-340 (340.65-0ubuntu1~xedgers14.04.1) ...
stop: Unknown job: nvidia-persistenced
userdel: user nvidia-persistenced is currently used by process 1364
dpkg: error processing package nvidia-340 (--remove):
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-340
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

the output above is similar to what I was getting when trying to remove the nvidia-340 driver or install a new one


sudo lshw -numeric -class video        returns...


```
*-display               
       description: VGA compatible controller
       product: GK104 [GeForce GTX 680] [10DE:1180]
       vendor: NVIDIA Corporation [10DE]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:75 memory:f5000000-f5ffffff memory:e0000000-e7ffffff memory:e8000000-e9ffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: Display controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:162]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list
       configuration: driver=i915 latency=0
       resources: irq:63 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)
```

---

### Post by MAFoElffen on 2014-12-26
lshw says your nVidia card is using the nvidia driver. The Xorg says it loads nvidia drivers, but from defaults, after trial and error, not directly from an /etc/X11/xorg.conf file...

So from a terminal:
```

sudo nvidia-xconfig

```
will create one for you that points straight to the nvidia driver and then won't try using all those other drivers and fail at those, before deciding to use the correct driver...

Then reboot.

---

### Post by tokyobadger on 2014-12-26
The GTX680 is supported by the newer drivers.

The issue is with nvidia-persistenced:
```
Removing nvidia-340 (340.65-0ubuntu1~xedgers14.04.1) ... 
stop: Unknown job: nvidia-persistenced 
userdel: user nvidia-persistenced is currently used by process 1364 
dpkg: error processing package nvidia-340 (--remove):  
subprocess installed post-removal script returned error exit status 8 
Errors were encountered while processing: 
 nvidia-340
```
Try this to find the current process number for nvidia-persistenced (if you have restarted the number will be different)
```
ps ax | grep persistenced
```
That should give you 2 process numbers - the first one should reference /usr/bin/nvidia-persistenced and the second one the grep command you just ran - **below is an example from my box - use the output you see**
```
 1694 ?        Ss     0:00 /usr/bin/nvidia-persistenced --user nvidia-persistenced
 8215 pts/0    S+     0:00 grep --color=auto persistenced
```
Now kill nvidia-persistenced (in my case I would kill process 1694)
```
 sudo kill 1694
```
Next try installing the nvidia driver again (I would first purge and then reinstall) - use the driver version you want to purge and reinstall
```
sudo apt-get purge nvidia-340 && sudo apt-get install nvidia-340
```
See if that works

---

### Post by MAFoElffen on 2014-12-26
tokyo bagder--
But if you install nvidia from the commandline (like I give instructions for a the bottom of the first post of my sticky), Without XServer running (as nVidia recommends when installing their drivers), then no part of  any nVidia (or other grahics driver) is running in any process... Make sense?

I'm all for the automated process that the Additional Drivers utilty adds, but there's always many ways to do the same thing... so many backup/alternatives...

Me? I use the binaries from nVidia and their installer. That is problematic (hit and miss) on if it is going to work out between system updates.... But I've so used to that, that I just expect that things break eventually. After 25 years of working with XServer, things happen and you deal with them.

---

### Post by ChaoticFlounder on 2014-12-26
MAFoElffen & tokyobadger,

I was able to get the proper driver installed.  Before I saw your posts, I ended up doing kinda what tokyo said.  I actually went in and physically deleted the nvidia-persistenced folder and the xorg.conf.failsafe file and was able to purge the system of the nvidia drivers after this.  Then I was able to do a clean install and currently have nvidia-331 installed.  I had nvidia-340 installed but had a small quirk when I would bring up gedit and look at physical code lines.  I have a steelseries sensei mouse and when I would scroll up and down a little bit the screen seemed to start flicking up and down really quickly and autonomously.  I tried a little bit to get the same action to occur with the 331 driver but haven't seen it yet.  Not certain if the aforementioned is due to operator error, my mouse, or the driver but it is the reason I went down this path to begin with.

MAFoElffen,

I went ahead and ran your command:  
```
sudo nvidia-xconfig
```
and rebooted...

looking in the folder ... ```
ls /etc/X11/xorg.*
``` now returns...

```
/etc/X11/xorg.conf
/etc/X11/xorg.conf.12262014
/etc/X11/xorg.conf.nvidia-xconfig-original

```

baffles me, btw what exactly does the xconfig do?  what is this xorg.conf file used for?

Anyways, thanks for all your help.

C

---

### Post by tokyobadger on 2014-12-26
[quote="ChaoticFlounder"]I was able to get the proper driver installed.[/quote]
Great news :-)
[quote="ChaoticFlounder"]when I would scroll up and down a little bit the screen seemed to start flicking up and down really quickly and autonomously.[/quote]
[There has been a well-known bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/269904") in Compiz under Nvidia that has required an agreement to be reached for Nvidia to release their patch under terms acceptable to Compiz - let's see when the patched Compiz comes down the pipes

As to your question what is xorg.conf - it's the configuration file for the display server (what makes the graphics come up on your monitor) - it tells xorg what monitor you have, the resolution, the video card, the driver, keyboard, mouse etc - it used to be quite a task to get it manually tweaked just right - these days auto-detection works pretty well and you only really need to mess with it if you're a Radeon user on proprietary drivers (afaik) or you have a more complex set-up like SLI, multiple monitors etc.

---

### Post by MAFoElffen on 2014-12-26
xorg.conf is the configuration file for Xorg Xserver. It tells Xserver which drivers to use and how to use them. If you look at it in gedit, there will be various sections... The device section(s) deals which the video card(s) and which driver to use for that card... Other sectione are for input devices, monitor sections, screen section and server section. Used screen and server sections can assemble various devices and monitors to lay them out...

You can run without an xorg.conf... but the XServer will use various drivers and probe various hardware and once they fail, use another. Problem is that sometimes, when something "fails," it doesn't always fail in a predictable manner, so doesn't recover gracefully and hangs. So an Xorg.conf file that points to what is there and how it should be configured, helps point to how it should be.

But your last post on the xorg.conf.xxxx with the date appended to the end... is what nvidia's nvidia-xconfig utility does to backup and existing xorg.conf file (with the date it was backed up, before being replaced). That tells me that you did have an xorg.conf file present, when you told me there was none.

As for removing your xorg.conf.failsafe file... that is not a good idea. That file "was not" an nvidia specific file, and you should not have needed to remove that. That file was a generic fallback file, for xorg XServer to use if there is a problem. That is what the recovery menu uses for low graphics mode, if there you have to go to the recvery menu and boot into low-graphics mode. That is not a biggy, as long as you remeber that if something does happen to your graphics after an updatre, boot into a grub menu, boot into a text console mode, rename your xorg.conf file, with an extension so that when xorg starts, that it doesn't find that specific file (xorg.conf)... then boot into a graphics mode, passing nomodeset as a boot option (directions for all those in post #2 of my sticky)... Those are things that you might learn as being an nVidia owner. Radeon has it's own , similar kinds of techniques.

No worries about rushing to reinstall that file. It will get rienstalled the next time Xorg XServer gets updated. So don't fuss when you see that there again.

nVidia is easier than it used to be. Your card is somewhat new. Give it about 6 months and it will be fully stable via nvidia-current. The Ubuntu mainline packages for them have gotten much better about being more stable with system updates.

---

