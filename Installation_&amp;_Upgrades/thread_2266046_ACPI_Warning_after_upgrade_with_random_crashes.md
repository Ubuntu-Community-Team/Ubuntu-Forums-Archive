---
title: "ACPI Warning after upgrade with random crashes"
date: 2015-02-19
forum: Installation &amp; Upgrades
---

### Post by old.dog on 2015-02-19
I am upgrading from linux mint 13 and encountered a problem with random crashes on several distributions.  I have tried mint 17, ubuntu MATE and xubuntu and all give a similar ACPI warning in dmesg.  The following is from ubuntuMATE.

```
[    5.932967] ppdev: user-space parallel port driver
[    6.340494] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    6.762143] wmi: Mapper loaded
[    6.931600] EDAC MC: Ver: 3.0.0
[    6.957630] ACPI Warning: 0x0000000000000828-0x000000000000082f SystemIO conflicts with Region \PMRG 1 (20131115/utaddress-251)
[    6.957635] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.957638] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPS0 1 (20131115/utaddress-251)
[    6.957640] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.957641] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPS0 1 (20131115/utaddress-251)
[    6.957644] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    6.957644] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    6.961807] EDAC MC0: Giving out device to module i7core_edac.c controller i7 core #0: DEV 0000:ff:03.0 (POLLED)
[    6.961834] EDAC PCI0: Giving out device to module i7core_edac controller EDAC PCI controller: DEV 0000:ff:03.0 (POLLED)
[    6.961840] EDAC i7core: Driver loaded, 1 memory controller(s) found.
[
```

My computer is an i7 930 @ 2.8 GHz with  Nvidea GeForce 9800 GTX+ on an Asus P6X58D-E motherboard.  I upgraded to the latest bios but problem persists.  Everything works fine on Mint13.

Any help will be appreciated.

---

### Post by old.dog on 2015-02-19
Correction to post.  

All distributions were new installs,  not upgrade.

---

### Post by dino99 on 2015-02-19
i have such 'conflicts' with my hardware too since kernel 3 serie is used. Its a kernel / some chipset(s) race/conflict. Sometimes bios settings can help to workaround, or by excluding those said maped conflicts zone. But your crash(es) might not be due to the acpi conflicts as the system tries to adjust the settings.
Google around " kernel+your hardware" (mainly mobo/chipset) to find discussions/workarounds/reported bugs ... or report yourself if no one have done it yet (ubuntu-bug linux)

---

### Post by old.dog on 2015-02-19
Thanks for the response 9d9.  My system worked fine on MintOS 13 which was kernel version 3.2.0-23 so it doesn't seem to be related to kernel 3 series.

I also tried to google as you suggested but haven't found anything yet.

---

### Post by Bashing-om on 2015-02-19
old.dog; Hello;

Confirm the hardware, as I find:
GeForce GTX 980 rather than '9800' .
IF this is the GTX 980, Nvidia advises from their site to use the 346 driver. That driver is not available in the ubuntu software repository. We in 'buntu land must resort to a PPA to install that driver,
what returns:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```

[INDENT][INDENT]maybe a re-direct is in order
[/INDENT][/INDENT]

---

### Post by old.dog on 2015-02-19
Hi bashing-om and thanks for the help.

My graphics card is indeed a 9800 GTX+.  I installed the driver in the ubuntu software center, (nvidia-current 304.125-0ubuntu0.0.1).  If I look at the nvidia site it looks like this version supports my card.

```
dan@winston:~$ lspci -vnn | grep VGA -A 12
03:00.0 VGA compatible controller [0300]: NVIDIA Corporation G92 [GeForce 9800 GTX+] [10de:0613] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device [3842:c879]
    Flags: bus master, fast devsel, latency 0, IRQ 24
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at cc00 [size=128]
    [virtual] Expansion ROM at fbce0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia


```
```
dan@winston:~$ sudo lshw -C display
[sudo] password for dan: 
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce 9800 GTX+]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:cc00(size=128) memory:fbce0000-fbcfffff

```

---

### Post by Bashing-om on 2015-02-19
old.dog; Sorry, redirected my thoughts;

to:
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
The 340.xx driver supports the following set of GPUs. >> GeForce 9800 GTX/9800 GTX+

Maybe purge the (nvidia-current 304.125-0ubuntu0.0.1) and try and install from PPA ? Best I recall the latest driver in the software repository is earlier than the 334 version. I welcome a correction here as I maybe slightly outdated.

worth a shot
[INDENT][INDENT][INDENT]see what results
[/INDENT][/INDENT][/INDENT]

---

### Post by old.dog on 2015-02-20
Well, I had much trouble getting the newer graphics driver installed but finally succeeded.  I tried both the 340.xx and the 346.xx versions from [HTML]https://launchpad.net/~garhuy/+archive/ubuntu/nvidia-lts[/HTML] but still have the ACPI warnings.  I am not sure if they are something I should be concerned about or not.  So far, I haven't had any crashes but they are random so I will need to watch it for a while.

In the mean time, any other suggestions would be appreciated.

---

### Post by Bashing-om on 2015-02-21
old.dog; Well ..

Thoughts:
1) Is there a driver conflict ? What driver(s) is installed ?
```

dpkg -l | grep nvidia

```

2) Did a proprietary driver build, and which one ?
```

cat /var/log/Xorg.0.log
sudo lshw -C display

```
we also look in that log to see what it relates in respect to the ACPI warnings .

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT]read the directions
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by old.dog on 2015-03-11
Hi bashing-om and thanks again.  Sorry for the delay but I was so frustrated I had to walk away from it for a while.  :p

```
dan@winston ~ $ dpkg -l | grep nvidia
ii  nvidia-304-updates                          304.125-0ubuntu0.0.1                                amd64        NVIDIA legacy binary driver - version 304.125
ii  nvidia-current-updates                      304.125-0ubuntu0.0.1                                amd64        Transitional package for nvidia-current-updates

```

```
dan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, dan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extension : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extension
[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)
(**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extensdan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extension : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extensiondan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extension : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extension
[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)

[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)
ion : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extension
[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4dan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, dan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extension : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extension
[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)
(**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extensdan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extension : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extensiondan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extension : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extension
[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)

[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)
ion : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extension
[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[  bashing-om  31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)

[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[  bashing-om  31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.dan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, dan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extension : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extension
[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)
(**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extensdan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extension : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extensiondan@winston ~ $ cat /var/log/Xorg.0.log
[    29.507] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    29.507] X Protocol Version 11, Revision 0
[    29.507] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    29.507] Current Operating System: Linux winston 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64
[    29.507] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-37-generic root=UUID=00234171-99bc-468b-b2d7-e2cf2d346bba ro quiet splash
[    29.507] Build Date: 30 July 2014  12:21:54AM
[    29.507] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[    29.507] Current version of pixman: 0.30.2
[    29.507]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    29.507] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    29.507] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 11 08:09:34 2015
[    29.530] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    29.539] (==) No Layout section.  Using the first Screen section.
[    29.539] (==) No screen section available. Using defaults.
[    29.539] (**) |-->Screen "Default Screen Section" (0)
[    29.539] (**) |   |-->Monitor "<default monitor>"
[    29.539] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    29.539] (==) Automatically adding devices
[    29.539] (==) Automatically enabling devices
[    29.539] (==) Automatically adding GPU devices
[    29.539] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    29.539]     Entry deleted from font path.
[    29.539] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    29.539] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    29.539] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    29.539] (II) Loader magic: 0x7fb399ff7d40
[    29.539] (II) Module ABI versions:
[    29.539]     X.Org ANSI C Emulation: 0.4
[    29.539]     X.Org Video Driver: 15.0
[    29.539]     X.Org XInput driver : 20.0
[    29.539]     X.Org Server Extension : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extension
[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)

[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)
ion : 8.0
[    29.539] (II) xfree86: Adding drm device (/dev/dri/card0)
[    29.542] (--) PCI:*(0:3:0:0) 10de:0613:3842:c879 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xf8000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/131072
[    29.542] Initializing built-in extension Generic Event Extension
[    29.542] Initializing built-in extension SHAPE
[    29.542] Initializing built-in extension MIT-SHM
[    29.542] Initializing built-in extension XInputExtension
[    29.542] Initializing built-in extension XTEST
[    29.542] Initializing built-in extension BIG-REQUESTS
[    29.542] Initializing built-in extension SYNC
[    29.542] Initializing built-in extension XKEYBOARD
[    29.542] Initializing built-in extension XC-MISC
[    29.542] Initializing built-in extension SECURITY
[    29.542] Initializing built-in extension XINERAMA
[    29.542] Initializing built-in extension XFIXES
[    29.542] Initializing built-in extension RENDER
[    29.542] Initializing built-in extension RANDR
[    29.542] Initializing built-in extension COMPOSITE
[    29.542] Initializing built-in extension DAMAGE
[    29.542] Initializing built-in extension MIT-SCREEN-SAVER
[    29.542] Initializing built-in extension DOUBLE-BUFFER
[    29.542] Initializing built-in extension RECORD
[    29.542] Initializing built-in extension DPMS
[    29.542] Initializing built-in extension Present
[    29.542] Initializing built-in extension DRI3
[    29.542] Initializing built-in extension X-Resource
[    29.542] Initializing built-in extension XVideo
[    29.542] Initializing built-in extension XVideo-MotionCompensation
[    29.542] Initializing built-in extension SELinux
[    29.542] Initializing built-in extension XFree86-VidModeExtension
[    29.542] Initializing built-in extension XFree86-DGA
[    29.542] Initializing built-in extension XFree86-DRI
[    29.542] Initializing built-in extension DRI2
[    29.542] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    29.542] (II) "glx" will be loaded by default.
[    29.542] (WW) "xmir" is not to be loaded by default. Skipping.
[    29.542] (II) LoadModule: "glx"
[    29.562] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    30.125] (II) Module glx: vendor="NVIDIA Corporation"
[    30.125]     compiled for 4.0.2, module version = 1.0.0
[    30.125]     Module class: X.Org Server Extension
[    30.125] (II) NVIDIA GLX Module  304.125  Mon Dec  1 20:22:48 PST 2014
[    30.125] Loading extension GLX
[    30.125] (==) Matched nvidia as autoconfigured driver 0
[    30.125] (==) Matched nouveau as autoconfigured driver 1
[    30.125] (==) Matched nvidia as autoconfigured driver 2
[    30.125] (==) Matched nouveau as autoconfigured driver 3
[    30.125] (==) Matched modesetting as autoconfigured driver 4
[    30.125] (==) Matched fbdev as autoconfigured driver 5
[    30.125] (==) Matched vesa as autoconfigured driver 6
[    30.125] (==) Assigned the driver to the xf86ConfigLayout
[    30.125] (II) LoadModule: "nvidia"
[    30.125] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    30.201] (II) Module nvidia: vendor="NVIDIA Corporation"
[    30.201]     compiled for 4.0.2, module version = 1.0.0
[    30.201]     Module class: X.Org Video Driver
[    30.209] (II) LoadModule: "nouveau"
[    30.209] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    30.222] (II) Module nouveau: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 1.0.10
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "modesetting"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    30.222] (II) Module modesetting: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.8.1
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "fbdev"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    30.222] (II) Module fbdev: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 0.4.4
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.222] (II) LoadModule: "vesa"
[    30.222] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    30.222] (II) Module vesa: vendor="X.Org Foundation"
[    30.222]     compiled for 1.15.0, module version = 2.3.3
[    30.222]     Module class: X.Org Video Driver
[    30.222]     ABI class: X.Org Video Driver, version 15.0
[    30.223] (II) NVIDIA dlloader X Driver  304.125  Mon Dec  1 20:00:30 PST 2014
[    30.223] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    30.231] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    30.231] (II) NOUVEAU driver for NVIDIA chipset families :
[    30.231]     RIVA TNT        (NV04)
[    30.231]     RIVA TNT2       (NV05)
[    30.231]     GeForce 256     (NV10)
[    30.231]     GeForce 2       (NV11, NV15)
[    30.231]     GeForce 4MX     (NV17, NV18)
[    30.231]     GeForce 3       (NV20)
[    30.231]     GeForce 4Ti     (NV25, NV28)
[    30.231]     GeForce FX      (NV3x)
[    30.231]     GeForce 6       (NV4x)
[    30.231]     GeForce 7       (G7x)
[    30.231]     GeForce 8       (G8x)
[    30.231]     GeForce GTX 200 (NVA0)
[    30.231]     GeForce GTX 400 (NVC0)
[    30.231] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    30.231] (II) FBDEV: driver for framebuffer: fbdev
[    30.231] (II) VESA: driver for VESA chipsets: vesa
[    30.231] (++) using VT number 7

[    30.234] (II) Loading sub module "fb"
[    30.234] (II) LoadModule: "fb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libfb.so
[    30.240] (II) Module fb: vendor="X.Org Foundation"
[    30.240]     compiled for 1.15.1, module version = 1.0.0
[    30.240]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.240] (II) Loading sub module "wfb"
[    30.240] (II) LoadModule: "wfb"
[    30.240] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    30.246] (II) Module wfb: vendor="X.Org Foundation"
[    30.246]     compiled for 1.15.1, module version = 1.0.0
[    30.246]     ABI class: X.Org ANSI C Emulation, version 0.4
[    30.246] (II) Loading sub module "ramdac"
[    30.246] (II) LoadModule: "ramdac"
[    30.246] (II) Module "ramdac" already built-in
[    30.248] (WW) Falling back to old probe method for modesetting
[    30.248] (WW) Falling back to old probe method for fbdev
[    30.248] (II) Loading sub module "fbdevhw"
[    30.248] (II) LoadModule: "fbdevhw"
[    30.248] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    30.248] (II) Module fbdevhw: vendor="X.Org Foundation"
[    30.248]     compiled for 1.15.1, module version = 0.0.2
[    30.248]     ABI class: X.Org Video Driver, version 15.0
[    30.248] (EE) open /dev/fb0: No such file or directory
[    30.248] (WW) Falling back to old probe method for vesa
[    30.248] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    30.248] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    30.248] (==) NVIDIA(0): RGB weight 888
[    30.248] (==) NVIDIA(0): Default visual is TrueColor
[    30.248] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    30.249] (**) NVIDIA(0): Enabling 2D acceleration
[    31.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    31.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    31.392] (II) NVIDIA(0): NVIDIA GPU GeForce 9800 GTX+ (G92) at PCI:3:0:0 (GPU-0)
[    31.392] (--) NVIDIA(0): Memory: 524288 kBytes
[    31.392] (--) NVIDIA(0): VideoBIOS: 62.92.89.00.7c
[    31.392] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    31.392] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    31.401] (--) NVIDIA(0): Valid display device(s) on GeForce 9800 GTX+ at PCI:3:0:0
[    31.401] (--) NVIDIA(0):     Samsung T24B350 (CRT-0) (connected)
[    31.401] (--) NVIDIA(0):     CRT-1
[    31.401] (--) NVIDIA(0):     TV-0
[    31.401] (--) NVIDIA(0):     DFP-0
[    31.401] (--) NVIDIA(0):     DFP-1
[    31.401] (--) NVIDIA(0): Samsung T24B350 (CRT-0): 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): CRT-1: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV-0: 400.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): TV encoder: Unknown
[    31.401] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-0: Internal Single Link TMDS
[    31.401] (--) NVIDIA(0): DFP-1: 330.0 MHz maximum pixel clock
[    31.401] (--) NVIDIA(0): DFP-1: Internal Single Link TMDS
[    31.401] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    31.401] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    31.401] (**) NVIDIA(0):     been enabled on all display devices.)
[    31.404] (==) NVIDIA(0): 
[    31.404] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    31.404] (==) NVIDIA(0):     will be used as the requested mode.
[    31.404] (==) NVIDIA(0): 
[    31.404] (II) NVIDIA(0): Validated MetaModes:
[    31.404] (II) NVIDIA(0):     "CRT-0:nvidia-auto-select"
[    31.404] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    31.441] (--) NVIDIA(0): DPI set to (93, 94); computed from "UseEdidDpi" X config
[    31.441] (--) NVIDIA(0):     option
[    31.441] (II) UnloadModule: "nouveau"
[    31.441] (II) Unloading nouveau
[    31.442] (II) UnloadModule: "modesetting"
[    31.442] (II) Unloading modesetting
[    31.442] (II) UnloadModule: "fbdev"
[    31.442] (II) Unloading fbdev
[    31.442] (II) UnloadSubModule: "fbdevhw"
[    31.442] (II) Unloading fbdevhw
[    31.442] (II) UnloadModule: "vesa"
[    31.442] (II) Unloading vesa
[    31.442] (--) Depth 24 pixmap format is 32 bpp
[    31.442] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    31.457] (II) NVIDIA(0): Setting mode "CRT-0:nvidia-auto-select"
[    31.504] Loading extension NV-GLX
[    31.522] (==) NVIDIA(0): Disabling shared memory pixmaps
[    31.522] (==) NVIDIA(0): Backing store enabled
[    31.522] (==) NVIDIA(0): Silken mouse enabled
[    31.522] (==) NVIDIA(0): DPMS enabled
[    31.528] Loading extension NV-CONTROL
[    31.528] Loading extension XINERAMA
[    31.528] (II) Loading sub module "dri2"
[    31.528] (II) LoadModule: "dri2"
[    31.528] (II) Module "dri2" already built-in
[    31.528] (II) NVIDIA(0): [DRI2] Setup complete
[    31.528] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    31.528] (--) RandR disabled
[    31.532] (II) SELinux: Disabled on system
[    31.532] (II) Initializing extension GLX
[    31.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    31.615] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    31.615] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.615] (II) LoadModule: "evdev"
[    31.615] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    31.628] (II) Module evdev: vendor="X.Org Foundation"
[    31.628]     compiled for 1.15.0, module version = 2.8.2
[    31.628]     Module class: X.Org XInput Driver
[    31.628]     ABI class: X.Org XInput driver, version 20.0
[    31.628] (II) Using input driver 'evdev' for 'Power Button'
[    31.628] (**) Power Button: always reports core events
[    31.628] (**) evdev: Power Button: Device: "/dev/input/event1"
[    31.628] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.628] (--) evdev: Power Button: Found keys
[    31.628] (II) evdev: Power Button: Configuring as keyboard
[    31.628] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    31.628] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    31.628] (**) Option "xkb_rules" "evdev"
[    31.628] (**) Option "xkb_model" "pc105"
[    31.628] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    31.629] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    31.629] (II) Using input driver 'evdev' for 'Power Button'
[    31.629] (**) Power Button: always reports core events
[    31.629] (**) evdev: Power Button: Device: "/dev/input/event0"
[    31.629] (--) evdev: Power Button: Vendor 0 Product 0x1
[    31.629] (--) evdev: Power Button: Found keys
[    31.629] (II) evdev: Power Button: Configuring as keyboard
[    31.629] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    31.629] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    31.629] (**) Option "xkb_rules" "evdev"
[    31.629] (**) Option "xkb_model" "pc105"
[    31.629] (**) Option "xkb_layout" "us"
[    31.629] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:03.0/0000:03:00.0/drm/card0
[    31.629] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    31.629] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event3)
[    31.629] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    31.629] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    31.629] (**) USB Optical Mouse: always reports core events
[    31.629] (**) evdev: USB Optical Mouse: Device: "/dev/input/event3"
[    31.629] (--) evdev: USB Optical Mouse: Vendor 0x461 Product 0x4d0f
[    31.629] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    31.629] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    31.629] (--) evdev: USB Optical Mouse: Found relative axes
[    31.629] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    31.629] (II) evdev: USB Optical Mouse: Configuring as mouse
[    31.629] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    31.629] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    31.629] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    31.629] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2:1.0/input/input3/event3"
[    31.629] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 8)
[    31.629] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    31.630] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    31.630] (**) USB Optical Mouse: (accel) acceleration profile 0
[    31.630] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    31.630] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    31.630] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Line Out Side (/dev/input/event5)
[    31.630] (II) No input driver specified, ignoring this device.
[  bashing-om  31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event4)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.630] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event11)
[    31.630] (II) No input driver specified, ignoring this device.
[    31.630] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event10)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event9)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Front (/dev/input/event8)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)

[    31.631] (II) config/udev: Adding input device HDA Intel Line Out Surround (/dev/input/event7)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device HDA Intel Line Out CLFE (/dev/input/event6)
[    31.631] (II) No input driver specified, ignoring this device.
[    31.631] (II) This device may have been added with another device file.
[    31.631] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    31.631] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    31.631] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    31.631] (**) AT Translated Set 2 keyboard: always reports core events
[    31.631] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    31.631] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    31.631] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    31.631] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    31.632] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 9)
[    31.632] (**) Option "xkb_rules" "evdev"
[    31.632] (**) Option "xkb_model" "pc105"
[    31.632] (**) Option "xkb_layout" "us"
[    51.133] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.133] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.133] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.133] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.133] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.215] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.215] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.215] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.215] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.215] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.297] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.297] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.297] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.297] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.297] (**) NVIDIA(0):     been enabled on all display devices.)
[    51.382] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    51.382] (II) NVIDIA(GPU-0):     Vision stereo.
[    51.382] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    51.382] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    51.382] (**) NVIDIA(0):     been enabled on all display devices.)
[    52.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-8AA988DD479FAABEC4FC3CCCF4CC29B4948840B4.xkm
[    52.897] (II) NVIDIA(GPU-0): Display (Samsung T24B350 (CRT-0)) does not support NVIDIA 3D
[    52.897] (II) NVIDIA(GPU-0):     Vision stereo.
[    52.897] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    52.897] (**) NVIDIA(0):     device Samsung T24B350 (CRT-0) (Using EDID frequencies has
[    52.897] (**) NVIDIA(0):     been enabled on all display devices.)

```

```
dan@winston ~ $ sudo lshw -C display
[sudo] password for dan: 
  *-display               
       description: VGA compatible controller
       product: G92 [GeForce 9800 GTX+]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fa000000-faffffff memory:d0000000-dfffffff memory:f8000000-f9ffffff ioport:cc00(size=128) memory:fbce0000-fbcfffff


```

Additionally, I discovered another conflict message that precedes the ones listed above.  I have been concentrating on Mint17 so this and above messages came from that OS.


```
[    0.351890] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.351917] pci 0000:00:1f.0: [8086:3a16] type 00 class 0x060100
[    0.351990] pci 0000:00:1f.0: address space collision: [io  0x0800-0x087f] conflicts with ACPI CPU throttle [??? 0x00000810-0x00000815 flags 0x80000000]
[    0.351994] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
[    0.351997] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.352090] pci 0000:00:1f.2: [8086:3a22] type 00 class 0x010601


```

So far, I have tried the following things that did not eliminate the conflict:
1. Various NVIDIA drivers including the latest
2. Latest Bios
3. Several boot options.  The only one which eliminates the conflict is "acpi=off" but it causes the cpu to use only 4 of the 8 processors.
4. I have done considerable research and found similar error messages but none that I can say are the same problem.  
5. Since all works on kernel 3.2.0-23 but not on 3.13.0-37 it seems like a regression from what I have read.  However, the troubleshooting suggests compiling kernels to see where the problem arose.  That seems to be above my skill level at this time.

---

### Post by tgalati4 on 2015-03-11
How old is the power supply?  Installing a new distro could push it over the edge causing strange problems.  The ACPI warnings are common.  The fact that you can't find anything directly related to your situation could indicate a hardware problem versus a repeatable software problem.

---

### Post by Bashing-om on 2015-03-11
old.dog; Welp, ......

See tgalati4's last, As we see no fault with the Nvidia driver build, and it is installed, good possibility as tgalati4 suggests.
I really can offer no other explanation.

exit
[INDENT][INDENT][INDENT]stage left ?
[/INDENT][/INDENT][/INDENT]

---

### Post by old.dog on 2015-03-11
Thanks to both of you for the responses.  Good point!  If it is a hardware problem I won't be fixing it with software.  ;)

My power supply is a Corsair TX750W that is about five years old. It is certainly possible that the random hangs and crashes could be due to hardware problems but the conflict error messages are consistent.  I am no expert but, right now, my best guess is that when I fix the conflict I will fix the crashes.   I just need to figure out exactly what the logs are telling me.

If I find an answer I will post it here for others.

---

### Post by tgalati4 on 2015-03-12
Let's see:  i7 running at 2.8 GHz.  That's a high-performance computer.  High performance computers need really clean power.  Unless you put your PSU on an oscilloscope to check for AC ripple, all it takes is one capacitor to fail allow that noise to slip through.  High frequency noise  interferes with the high speed logic and causes lockups.  Do you have another PSU to test with?

---

### Post by old.dog on 2015-03-12
I agree with what you say 100%.  I'm retired now but spent considerable time as an engineer repairing electronic equipment.  Over time, capacitors are the component that tends to fail most often.  

Unfortunately, I don't have another power supply with sufficient power ratings to try.  And, I just haven't convinced myself to buy a new one because it works perfectly  on mint13.  I will definitely keep that in mind though.

---

### Post by tgalati4 on 2015-03-12
Boot up Mint13 using a USB stick and see how long your system stays up.  If it fails once during a week, then you can be pretty sure it's a hardware issue.

---

### Post by gordintoronto on 2015-03-13
I also get an ACPI warning, and Mint 13 is rock solid, but everything since then crashes after some number of hours -- until the 15.04 development version! I'm running Xubuntu 15.04 from a flash drive, and it has not failed in a solid week of testing. (I've rebooted for kernel upgrades, now 3.19.0-8, but that's all.)

My computer architecture is quite different from the OP: AMD Phenom II X2 CPU on a Gigabyte GA-MA770T-UD3P motherboard.

---

### Post by old.dog on 2015-03-13
Well, I am not booted from a usb stick but, I am still using Mint13 until I get this resolved.  My computer doesn't stay up continuously but I have not seen similar problems.

I loaded xubuntu 15.04 beta 1 and have different error messages that might help.  I haven't had a chance to fully review the dmesg yet but here are the "conflict" messages plus a couple lines before and after each. 

```
[    0.375976] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.376017] pci 0000:00:1d.7: System wakeup disabled by ACPI
[    0.376049] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.376125] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.376161] pci 0000:00:1f.0: [8086:3a16] type 00 class 0x060100
[    0.376235] pci 0000:00:1f.0: can't claim BAR 13 [io  0x0800-0x087f]: address conflict with ACPI CPU throttle [io  0x0810-0x0815]
[    0.376239] pci 0000:00:1f.0: quirk: [io  0x0500-0x053f] claimed by ICH6 GPIO
[    0.376242] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.376336] pci 0000:00:1f.2: [8086:3a22] type 00 class 0x010601
[    0.376353] pci 0000:00:1f.2: reg 0x10: [io  0x9c00-0x9c07]



[    0.413554] PCI host bridge to bus 0000:ff
[    0.413557] pci_bus 0000:ff: root bus resource [io  0x0000-0xffff]
[    0.413558] pci_bus 0000:ff: root bus resource [mem 0x00000000-0xfffffffff]
[    0.413560] pci_bus 0000:ff: No busn resource found for root bus, will use [bus ff-ff]
[    0.413562] pci_bus 0000:ff: busn_res: can not insert [bus ff] under domain [bus 00-ff] (conflicts with (null) [bus 00-ff])
[    0.413567] pci 0000:ff:00.0: [8086:2c41] type 00 class 0x060000
[    0.413605] pci 0000:ff:00.1: [8086:2c01] type 00 class 0x060000


[    0.414158] pci 0000:ff:06.2: [8086:2c32] type 00 class 0x060000
[    0.414192] pci 0000:ff:06.3: [8086:2c33] type 00 class 0x060000
[    0.414239] pci_bus 0000:ff: busn_res: [bus ff] end is updated to ff
[    0.414242] pci_bus 0000:ff: busn_res: can not insert [bus ff] under domain [bus 00-ff] (conflicts with (null) [bus 00-ff])
[    0.414245] PCI: pci_cache_line_size set to 64 bytes
[    0.414316] e820: reserve RAM buffer [mem 0x0009ec00-0x0009ffff]
[    0.414317] e820: reserve RAM buffer [mem 0xbf780000-0xbfffffff]


[   24.814685] EDAC MC0: Giving out device to module i7core_edac.c controller i7 core #0: DEV 0000:ff:03.0 (POLLED)
[   24.814749] EDAC PCI0: Giving out device to module i7core_edac controller EDAC PCI controller: DEV 0000:ff:03.0 (POLLED)
[   24.814757] EDAC i7core: Driver loaded, 1 memory controller(s) found.
[   24.892125] ACPI Warning: SystemIO range 0x0000000000000828-0x000000000000082f conflicts with OpRegion 0x0000000000000800-0x000000000000084f (\PMRG) (20140926/utaddress-258)
[   24.892133] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   24.892137] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x000000000000053f (\GPS0) (20140926/utaddress-258)conflict
[   24.892140] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   24.892141] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x000000000000053f (\GPS0) (20140926/utaddress-258)
[   24.892144] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   24.892145] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   24.966055] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   24.984286] device-mapper: multipath: version 1.7.0 loaded


```

---

### Post by old.dog on 2015-03-14
I found several old OS download DVDs still laying around.  Sometimes it is good to be a pack rat.  :p  

By booting live and checking dmesg I found that the conflict appears some where between xubuntu 12.04 (kernel 3.2.0-37) and kubuntu 12.10 (3.5.0-17).

---

