---
title: "Nvidia GeForce FX 5500 AGP 8x card issues"
date: 2017-11-07
forum: MINT
---

### Post by coldraven on 2017-11-07
Trying to get some life out of an old desktop I bought the card in the title. I did a fresh install of Linux Mint  Cinnamon 18.2. The PC is dual core at 2Ghz with 4GB memory.
When selecting an image as wallpaper the background goes entirely cyan or white. After a reboot the wallpaper image is correctly displayed. Some other programs have an all white dialogue box. 
Rather than waste a lot of time I'd rather just install a distribution that can display properly. I also tried booting a Kubuntu Live DVD but that too had display issues. Any ideas?

P.S. I put this here in case anyone is using Windows 7
I shrank the 1TB drive into halves and did a fresh install of Win7. I then discovered that NVidia does not support this card for Win7. After a lot of searching I saw a suggestion of using the Vista drivers. The NVidia 64bit Vista driver installed and works fine in 1440 x 900 mode.

---

### Post by Bashing-om on 2017-11-07
coldraven; Hey, hey ..

That card will take the legacy 304 driver :
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

So, what do you see in the boot dialog when replacing quiet splash with nomodeset as a kernel boot parameter ?

What driver is presently loaded ?
```

lsmod | grep -i nouveau
lsmod | grep -i nvidia
sudo lshw -C display

```


[INDENT][INDENT]got to be a reason
[/INDENT][/INDENT]

---

### Post by coldraven on 2017-11-08
Hi Bashing-om, with nomdeset in grub i get a big notification on the top right of the desktop. It says "Running in software rendering mode, blah blah, high CPU usage, blah blah, problem with drivers"
Rebooting without nomodeset:
```
lsmod | grep -i nouveau
nouveau              1601536  4
mxm_wmi                16384  1 nouveau
wmi                    16384  2 mxm_wmi,nouveau
video                  40960  1 nouveau
i2c_algo_bit           16384  1 nouveau
ttm                    98304  1 nouveau
drm_kms_helper        151552  1 nouveau
drm                   352256  7 nouveau,ttm,drm_kms_helper
```

```
lsmod | grep -i nvidia 
``` returns nothing

```
sudo lshw -C display
[sudo] password for xxxxx: 
  *-display               
       description: VGA compatible controller
       product: NV34 [GeForce FX 5500]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
       resources: irq:16 memory:f8000000-f8ffffff memory:e0000000-efffffff memory:c0000-dffff
```

Output of Xorg.0.log
```
[    36.182] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[    36.182] X Protocol Version 11, Revision 0
[    36.182] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[    36.182] Current Operating System: Linux MS-7312 4.10.0-38-generic #42~16.04.1-Ubuntu SMP Tue Oct 10 16:32:20 UTC 2017 x86_64
[    36.182] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.10.0-38-generic root=UUID=6b9c3f5d-b6b2-4ef1-b657-58e7fffed84d ro quiet splash vt.handoff=7
[    36.182] Build Date: 13 October 2017  01:57:05PM
[    36.182] xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support) 
[    36.182] Current version of pixman: 0.33.6
[    36.182]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    36.182] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    36.182] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  8 17:11:21 2017
[    36.192] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    36.193] (==) No Layout section.  Using the first Screen section.
[    36.193] (==) No screen section available. Using defaults.
[    36.193] (**) |-->Screen "Default Screen Section" (0)
[    36.193] (**) |   |-->Monitor "<default monitor>"
[    36.193] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    36.193] (==) Automatically adding devices
[    36.193] (==) Automatically enabling devices
[    36.193] (==) Automatically adding GPU devices
[    36.193] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    36.194] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    36.194]     Entry deleted from font path.
[    36.194] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    36.194]     Entry deleted from font path.
[    36.194] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    36.194]     Entry deleted from font path.
[    36.194] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    36.194]     Entry deleted from font path.
[    36.194] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    36.194]     Entry deleted from font path.
[    36.194] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    36.194] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    36.194] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    36.194] (II) Loader magic: 0x5629cc71bdc0
[    36.194] (II) Module ABI versions:
[    36.194]     X.Org ANSI C Emulation: 0.4
[    36.194]     X.Org Video Driver: 20.0
[    36.194]     X.Org XInput driver : 22.1
[    36.194]     X.Org Server Extension : 9.0
[    36.197] (++) using VT number 7

[    36.197] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    36.198] (II) xfree86: Adding drm device (/dev/dri/card0)
[    36.210] (--) PCI:*(0:1:0:0) 10de:0326:0000:0000 rev 161, Mem @ 0xf8000000/16777216, 0xe0000000/268435456, BIOS @ 0x????????/131072
[    36.211] (II) LoadModule: "glx"
[    36.256] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    36.475] (II) Module glx: vendor="X.Org Foundation"
[    36.475]     compiled for 1.18.4, module version = 1.0.0
[    36.475]     ABI class: X.Org Server Extension, version 9.0
[    36.475] (==) AIGLX enabled
[    36.475] (==) Matched nvidia as autoconfigured driver 0
[    36.475] (==) Matched nouveau as autoconfigured driver 1
[    36.475] (==) Matched nvidia as autoconfigured driver 2
[    36.475] (==) Matched nouveau as autoconfigured driver 3
[    36.475] (==) Matched modesetting as autoconfigured driver 4
[    36.475] (==) Matched fbdev as autoconfigured driver 5
[    36.475] (==) Matched vesa as autoconfigured driver 6
[    36.476] (==) Assigned the driver to the xf86ConfigLayout
[    36.476] (II) LoadModule: "nvidia"
[    36.477] (WW) Warning, couldn't open module nvidia
[    36.477] (II) UnloadModule: "nvidia"
[    36.477] (II) Unloading nvidia
[    36.477] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    36.477] (II) LoadModule: "nouveau"
[    36.477] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    36.486] (II) Module nouveau: vendor="X.Org Foundation"
[    36.489]     compiled for 1.18.1, module version = 1.0.12
[    36.489]     Module class: X.Org Video Driver
[    36.489]     ABI class: X.Org Video Driver, version 20.0
[    36.489] (II) LoadModule: "modesetting"
[    36.490] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    36.490] (II) Module modesetting: vendor="X.Org Foundation"
[    36.490]     compiled for 1.18.4, module version = 1.18.4
[    36.490]     Module class: X.Org Video Driver
[    36.490]     ABI class: X.Org Video Driver, version 20.0
[    36.490] (II) LoadModule: "fbdev"
[    36.491] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    36.491] (II) Module fbdev: vendor="X.Org Foundation"
[    36.491]     compiled for 1.18.1, module version = 0.4.4
[    36.491]     Module class: X.Org Video Driver
[    36.491]     ABI class: X.Org Video Driver, version 20.0
[    36.491] (II) LoadModule: "vesa"
[    36.492] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    36.492] (II) Module vesa: vendor="X.Org Foundation"
[    36.492]     compiled for 1.18.1, module version = 2.3.4
[    36.492]     Module class: X.Org Video Driver
[    36.492]     ABI class: X.Org Video Driver, version 20.0
[    36.492] (==) Matched nvidia as autoconfigured driver 0
[    36.492] (==) Matched nouveau as autoconfigured driver 1
[    36.492] (==) Matched nvidia as autoconfigured driver 2
[    36.492] (==) Matched nouveau as autoconfigured driver 3
[    36.492] (==) Matched modesetting as autoconfigured driver 4
[    36.492] (==) Matched fbdev as autoconfigured driver 5
[    36.492] (==) Matched vesa as autoconfigured driver 6
[    36.493] (==) Assigned the driver to the xf86ConfigLayout
[    36.493] (II) LoadModule: "nvidia"
[    36.493] (WW) Warning, couldn't open module nvidia
[    36.493] (II) UnloadModule: "nvidia"
[    36.493] (II) Unloading nvidia
[    36.493] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    36.493] (II) LoadModule: "nouveau"
[    36.494] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    36.494] (II) Module nouveau: vendor="X.Org Foundation"
[    36.494]     compiled for 1.18.1, module version = 1.0.12
[    36.494]     Module class: X.Org Video Driver
[    36.494]     ABI class: X.Org Video Driver, version 20.0
[    36.494] (II) UnloadModule: "nouveau"
[    36.494] (II) Unloading nouveau
[    36.494] (II) Failed to load module "nouveau" (already loaded, 0)
[    36.494] (II) LoadModule: "modesetting"
[    36.495] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    36.495] (II) Module modesetting: vendor="X.Org Foundation"
[    36.495]     compiled for 1.18.4, module version = 1.18.4
[    36.495]     Module class: X.Org Video Driver
[    36.495]     ABI class: X.Org Video Driver, version 20.0
[    36.495] (II) UnloadModule: "modesetting"
[    36.495] (II) Unloading modesetting
[    36.495] (II) Failed to load module "modesetting" (already loaded, 0)
[    36.495] (II) LoadModule: "fbdev"
[    36.495] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    36.495] (II) Module fbdev: vendor="X.Org Foundation"
[    36.495]     compiled for 1.18.1, module version = 0.4.4
[    36.495]     Module class: X.Org Video Driver
[    36.495]     ABI class: X.Org Video Driver, version 20.0
[    36.495] (II) UnloadModule: "fbdev"
[    36.495] (II) Unloading fbdev
[    36.495] (II) Failed to load module "fbdev" (already loaded, 0)
[    36.495] (II) LoadModule: "vesa"
[    36.496] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    36.496] (II) Module vesa: vendor="X.Org Foundation"
[    36.496]     compiled for 1.18.1, module version = 2.3.4
[    36.496]     Module class: X.Org Video Driver
[    36.496]     ABI class: X.Org Video Driver, version 20.0
[    36.496] (II) UnloadModule: "vesa"
[    36.496] (II) Unloading vesa
[    36.496] (II) Failed to load module "vesa" (already loaded, 0)
[    36.496] (II) NOUVEAU driver Date:   Tue Dec 8 15:52:25 2015 +1000
[    36.496] (II) NOUVEAU driver for NVIDIA chipset families :
[    36.496]     RIVA TNT        (NV04)
[    36.496]     RIVA TNT2       (NV05)
[    36.496]     GeForce 256     (NV10)
[    36.496]     GeForce 2       (NV11, NV15)
[    36.497]     GeForce 4MX     (NV17, NV18)
[    36.497]     GeForce 3       (NV20)
[    36.497]     GeForce 4Ti     (NV25, NV28)
[    36.497]     GeForce FX      (NV3x)
[    36.497]     GeForce 6       (NV4x)
[    36.497]     GeForce 7       (G7x)
[    36.497]     GeForce 8       (G8x)
[    36.497]     GeForce GTX 200 (NVA0)
[    36.497]     GeForce GTX 400 (NVC0)
[    36.497] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    36.497] (II) FBDEV: driver for framebuffer: fbdev
[    36.497] (II) VESA: driver for VESA chipsets: vesa
[    36.498] (II) [drm] nouveau interface version: 1.3.1
[    36.498] (WW) Falling back to old probe method for modesetting
[    36.498] (WW) Falling back to old probe method for fbdev
[    36.498] (II) Loading sub module "fbdevhw"
[    36.498] (II) LoadModule: "fbdevhw"
[    36.499] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    36.499] (II) Module fbdevhw: vendor="X.Org Foundation"
[    36.499]     compiled for 1.18.4, module version = 0.0.2
[    36.499]     ABI class: X.Org Video Driver, version 20.0
[    36.499] (WW) Falling back to old probe method for vesa
[    36.500] (II) Loading sub module "dri2"
[    36.500] (II) LoadModule: "dri2"
[    36.500] (II) Module "dri2" already built-in
[    36.500] (--) NOUVEAU(0): Chipset: "NVIDIA NV34"
[    36.500] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    36.500] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    36.500] (==) NOUVEAU(0): RGB weight 888
[    36.500] (==) NOUVEAU(0): Default visual is TrueColor
[    36.500] (==) NOUVEAU(0): Using HW cursor
[    36.500] (==) NOUVEAU(0): Allowed maximum DRI level 2.
[    36.500] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[    36.500] (==) NOUVEAU(0): Page flipping enabled
[    36.500] (==) NOUVEAU(0): Swap limit set to 1 [Max allowed 2]
[    36.500] (==) NOUVEAU(0): Page flipping synced to vblank by kernel.
[    36.500] (II) NOUVEAU(0): Initializing outputs ...
[    36.530] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    36.572] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[    36.612] (II) NOUVEAU(0): Output TV-1 has no monitor section
[    36.612] (II) NOUVEAU(0): 3 crtcs needed for screen.
[    36.612] (II) NOUVEAU(0): Allocated crtc nr. 0 to this screen.
[    36.612] (II) NOUVEAU(0): Allocated crtc nr. 1 to this screen.
[    36.642] (II) NOUVEAU(0): EDID for output VGA-1
[    36.642] (II) NOUVEAU(0): Manufacturer: NUL  Model: 0  Serial#: 1
[    36.642] (II) NOUVEAU(0): Year: 2006  Week: 30
[    36.642] (II) NOUVEAU(0): EDID Version: 1.3
[    36.642] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    36.642] (II) NOUVEAU(0): Sync:  Separate
[    36.642] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 41  vert.: 26
[    36.642] (II) NOUVEAU(0): Gamma: 2.20
[    36.642] (II) NOUVEAU(0): No DPMS capabilities specified; RGB/Color Display
[    36.642] (II) NOUVEAU(0): First detailed timing is preferred mode
[    36.642] (II) NOUVEAU(0): redX: 0.599 redY: 0.348   greenX: 0.310 greenY: 0.550
[    36.642] (II) NOUVEAU(0): blueX: 0.150 blueY: 0.115   whiteX: 0.312 whiteY: 0.328
[    36.642] (II) NOUVEAU(0): Supported established timings:
[    36.642] (II) NOUVEAU(0): 720x400@70Hz
[    36.642] (II) NOUVEAU(0): 640x480@60Hz
[    36.642] (II) NOUVEAU(0): 640x480@72Hz
[    36.642] (II) NOUVEAU(0): 800x600@56Hz
[    36.642] (II) NOUVEAU(0): 800x600@60Hz
[    36.642] (II) NOUVEAU(0): 800x600@72Hz
[    36.642] (II) NOUVEAU(0): 800x600@75Hz
[    36.642] (II) NOUVEAU(0): 1024x768@60Hz
[    36.642] (II) NOUVEAU(0): 1024x768@70Hz
[    36.642] (II) NOUVEAU(0): 1024x768@75Hz
[    36.642] (II) NOUVEAU(0): Manufacturer's mask: 0
[    36.642] (II) NOUVEAU(0): Supported detailed timing:
[    36.642] (II) NOUVEAU(0): clock: 106.5 MHz   Image Size:  410 x 256 mm
[    36.642] (II) NOUVEAU(0): h_active: 1440  h_sync: 1520  h_sync_end 1672 h_blank_end 1904 h_border: 0
[    36.642] (II) NOUVEAU(0): v_active: 900  v_sync: 903  v_sync_end 909 v_blanking: 934 v_border: 0
[    36.642] (II) NOUVEAU(0):  
[    36.642] (II) NOUVEAU(0): Monitor name: M19W
[    36.642] (II) NOUVEAU(0): Serial No: 
[    36.643] (II) NOUVEAU(0): EDID (in hex):
[    36.643] (II) NOUVEAU(0):     00ffffffffffff003aac000001000000
[    36.643] (II) NOUVEAU(0):     1e10010308291a780a47a099594f8c26
[    36.643] (II) NOUVEAU(0):     1d5054abce0001010101010101010101
[    36.643] (II) NOUVEAU(0):     0101010101019a29a0d0518422305098
[    36.643] (II) NOUVEAU(0):     36009a0011000018000000fe000a2020
[    36.643] (II) NOUVEAU(0):     20202020202020202020000000fc004d
[    36.643] (II) NOUVEAU(0):     3139570a2020202020202020000000ff
[    36.643] (II) NOUVEAU(0):     000a202020202020202020202020009c
[    36.643] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[    36.643] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz eP)
[    36.643] (II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    36.643] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    36.643] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    36.643] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    36.643] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    36.643] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    36.643] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    36.643] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    36.643] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    36.643] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    36.684] (II) NOUVEAU(0): EDID for output DVI-I-1
[    36.724] (II) NOUVEAU(0): EDID for output TV-1
[    36.724] (II) NOUVEAU(0): Output VGA-1 connected
[    36.724] (II) NOUVEAU(0): Output DVI-I-1 disconnected
[    36.724] (II) NOUVEAU(0): Output TV-1 disconnected
[    36.724] (II) NOUVEAU(0): Using exact sizes for initial modes
[    36.724] (II) NOUVEAU(0): Output VGA-1 using initial mode 1440x900 +0+0
[    36.724] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    36.724] (--) NOUVEAU(0): Virtual size is 1440x900 (pitch 0)
[    36.724] (**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
[    36.724] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz eP)
[    36.724] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
[    36.724] (II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    36.724] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[    36.724] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    36.724] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    36.724] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    36.724] (**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
[    36.724] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    36.724] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    36.724] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    36.724] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    36.724] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    36.724] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    36.725] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    36.725] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
[    36.725] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    36.725] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    36.725] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    36.725] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[    36.725] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    36.725] (==) NOUVEAU(0): DPI set to (96, 96)
[    36.725] (II) Loading sub module "fb"
[    36.725] (II) LoadModule: "fb"
[    36.725] (II) Loading /usr/lib/xorg/modules/libfb.so
[    36.726] (II) Module fb: vendor="X.Org Foundation"
[    36.726]     compiled for 1.18.4, module version = 1.0.0
[    36.726]     ABI class: X.Org ANSI C Emulation, version 0.4
[    36.726] (II) Loading sub module "shadowfb"
[    36.726] (II) LoadModule: "shadowfb"
[    36.727] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    36.727] (II) Module shadowfb: vendor="X.Org Foundation"
[    36.727]     compiled for 1.18.4, module version = 1.0.0
[    36.727]     ABI class: X.Org ANSI C Emulation, version 0.4
[    36.727] (II) UnloadModule: "modesetting"
[    36.727] (II) Unloading modesetting
[    36.727] (II) UnloadModule: "fbdev"
[    36.727] (II) Unloading fbdev
[    36.727] (II) UnloadSubModule: "fbdevhw"
[    36.727] (II) Unloading fbdevhw
[    36.727] (II) UnloadModule: "vesa"
[    36.727] (II) Unloading vesa
[    36.727] (--) Depth 24 pixmap format is 32 bpp
[    36.730] (II) NOUVEAU(0): Channel setup complete.
[    36.855] (II) NOUVEAU(0): Hardware support for Present enabled
[    36.855] (II) NOUVEAU(0): [DRI2] Setup complete
[    36.855] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    36.855] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[    36.855] (II) Loading sub module "exa"
[    36.855] (II) LoadModule: "exa"
[    36.855] (II) Loading /usr/lib/xorg/modules/libexa.so
[    36.856] (II) Module exa: vendor="X.Org Foundation"
[    36.856]     compiled for 1.18.4, module version = 2.6.0
[    36.856]     ABI class: X.Org Video Driver, version 20.0
[    36.856] (II) EXA(0): Driver allocated offscreen pixmaps
[    36.856] (II) EXA(0): Driver registered support for the following operations:
[    36.856] (II)         Solid
[    36.856] (II)         Copy
[    36.856] (II)         Composite (RENDER acceleration)
[    36.856] (II)         UploadToScreen
[    36.856] (II)         DownloadFromScreen
[    36.856] (==) NOUVEAU(0): Backing store enabled
[    36.856] (==) NOUVEAU(0): Silken mouse enabled
[    36.889] (II) NOUVEAU(0): [XvMC] Associated with NV30 texture adapter.
[    36.889] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    36.889] (==) NOUVEAU(0): DPMS enabled
[    36.889] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    36.891] (--) RandR disabled
[    36.938] (II) SELinux: Disabled on system
[    38.079] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    38.079] (II) AIGLX: enabled GLX_ARB_create_context
[    38.079] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    38.079] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[    38.079] (II) AIGLX: enabled GLX_INTEL_swap_event
[    38.079] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    38.079] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    38.079] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    38.079] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[    38.079] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    38.080] (II) AIGLX: Loaded and initialized nouveau
[    38.080] (II) GLX: Initialized DRI2 GL provider for screen 0
[    38.084] (II) NOUVEAU(0): NVEnterVT is called.
[    38.084] (II) NOUVEAU(0): Setting screen physical size to 381 x 238
[    38.084] resize called 1440 900
[    38.438] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    38.438] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    38.438] (II) LoadModule: "evdev"
[    38.439] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    38.466] (II) Module evdev: vendor="X.Org Foundation"
[    38.466]     compiled for 1.18.1, module version = 2.10.1
[    38.466]     Module class: X.Org XInput Driver
[    38.466]     ABI class: X.Org XInput driver, version 22.1
[    38.466] (II) Using input driver 'evdev' for 'Power Button'
[    38.466] (**) Power Button: always reports core events
[    38.466] (**) evdev: Power Button: Device: "/dev/input/event1"
[    38.466] (--) evdev: Power Button: Vendor 0 Product 0x1
[    38.466] (--) evdev: Power Button: Found keys
[    38.466] (II) evdev: Power Button: Configuring as keyboard
[    38.466] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    38.466] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    38.466] (**) Option "xkb_rules" "evdev"
[    38.466] (**) Option "xkb_model" "pc105"
[    38.466] (**) Option "xkb_layout" "gb"
[    38.516] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    38.516] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    38.516] (II) Using input driver 'evdev' for 'Power Button'
[    38.516] (**) Power Button: always reports core events
[    38.516] (**) evdev: Power Button: Device: "/dev/input/event0"
[    38.516] (--) evdev: Power Button: Vendor 0 Product 0x1
[    38.516] (--) evdev: Power Button: Found keys
[    38.516] (II) evdev: Power Button: Configuring as keyboard
[    38.516] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    38.516] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    38.516] (**) Option "xkb_rules" "evdev"
[    38.516] (**) Option "xkb_model" "pc105"
[    38.516] (**) Option "xkb_layout" "gb"
[    38.518] (II) config/udev: Adding input device SIGMACHIP USB Keyboard (/dev/input/event2)
[    38.518] (**) SIGMACHIP USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    38.518] (II) Using input driver 'evdev' for 'SIGMACHIP USB Keyboard'
[    38.518] (**) SIGMACHIP USB Keyboard: always reports core events
[    38.518] (**) evdev: SIGMACHIP USB Keyboard: Device: "/dev/input/event2"
[    38.518] (--) evdev: SIGMACHIP USB Keyboard: Vendor 0x1c4f Product 0x16
[    38.518] (--) evdev: SIGMACHIP USB Keyboard: Found keys
[    38.518] (II) evdev: SIGMACHIP USB Keyboard: Configuring as keyboard
[    38.518] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.0/0003:1C4F:0016.0001/input/input5/event2"
[    38.518] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard" (type: KEYBOARD, id 8)
[    38.518] (**) Option "xkb_rules" "evdev"
[    38.518] (**) Option "xkb_model" "pc105"
[    38.518] (**) Option "xkb_layout" "gb"
[    38.520] (II) config/udev: Adding input device SIGMACHIP USB Keyboard (/dev/input/event3)
[    38.520] (**) SIGMACHIP USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    38.520] (II) Using input driver 'evdev' for 'SIGMACHIP USB Keyboard'
[    38.520] (**) SIGMACHIP USB Keyboard: always reports core events
[    38.520] (**) evdev: SIGMACHIP USB Keyboard: Device: "/dev/input/event3"
[    38.520] (--) evdev: SIGMACHIP USB Keyboard: Vendor 0x1c4f Product 0x16
[    38.520] (--) evdev: SIGMACHIP USB Keyboard: Found 1 mouse buttons
[    38.520] (--) evdev: SIGMACHIP USB Keyboard: Found scroll wheel(s)
[    38.520] (--) evdev: SIGMACHIP USB Keyboard: Found relative axes
[    38.520] (II) evdev: SIGMACHIP USB Keyboard: Forcing relative x/y axes to exist.
[    38.520] (--) evdev: SIGMACHIP USB Keyboard: Found absolute axes
[    38.520] (II) evdev: SIGMACHIP USB Keyboard: Forcing absolute x/y axes to exist.
[    38.520] (--) evdev: SIGMACHIP USB Keyboard: Found keys
[    38.520] (II) evdev: SIGMACHIP USB Keyboard: Configuring as mouse
[    38.520] (II) evdev: SIGMACHIP USB Keyboard: Configuring as keyboard
[    38.520] (II) evdev: SIGMACHIP USB Keyboard: Adding scrollwheel support
[    38.520] (**) evdev: SIGMACHIP USB Keyboard: YAxisMapping: buttons 4 and 5
[    38.520] (**) evdev: SIGMACHIP USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    38.520] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-1/2-1:1.1/0003:1C4F:0016.0002/input/input6/event3"
[    38.520] (II) XINPUT: Adding extended input device "SIGMACHIP USB Keyboard" (type: KEYBOARD, id 9)
[    38.520] (**) Option "xkb_rules" "evdev"
[    38.520] (**) Option "xkb_model" "pc105"
[    38.520] (**) Option "xkb_layout" "gb"
[    38.521] (II) evdev: SIGMACHIP USB Keyboard: initialized for relative axes.
[    38.521] (WW) evdev: SIGMACHIP USB Keyboard: ignoring absolute axes.
[    38.521] (**) SIGMACHIP USB Keyboard: (accel) keeping acceleration scheme 1
[    38.521] (**) SIGMACHIP USB Keyboard: (accel) acceleration profile 0
[    38.521] (**) SIGMACHIP USB Keyboard: (accel) acceleration factor: 2.000
[    38.521] (**) SIGMACHIP USB Keyboard: (accel) acceleration threshold: 4
[    38.522] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event4)
[    38.522] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    38.522] (II) Using input driver 'evdev' for 'USB Optical Mouse'
[    38.522] (**) USB Optical Mouse: always reports core events
[    38.522] (**) evdev: USB Optical Mouse: Device: "/dev/input/event4"
[    38.584] (--) evdev: USB Optical Mouse: Vendor 0x15ca Product 0xc3
[    38.584] (--) evdev: USB Optical Mouse: Found 3 mouse buttons
[    38.584] (--) evdev: USB Optical Mouse: Found scroll wheel(s)
[    38.584] (--) evdev: USB Optical Mouse: Found relative axes
[    38.584] (--) evdev: USB Optical Mouse: Found x and y relative axes
[    38.584] (II) evdev: USB Optical Mouse: Configuring as mouse
[    38.584] (II) evdev: USB Optical Mouse: Adding scrollwheel support
[    38.584] (**) evdev: USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    38.584] (**) evdev: USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    38.584] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:10.0/usb2/2-2/2-2:1.0/0003:15CA:00C3.0003/input/input7/event4"
[    38.584] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE, id 10)
[    38.584] (II) evdev: USB Optical Mouse: initialized for relative axes.
[    38.584] (**) USB Optical Mouse: (accel) keeping acceleration scheme 1
[    38.584] (**) USB Optical Mouse: (accel) acceleration profile 0
[    38.584] (**) USB Optical Mouse: (accel) acceleration factor: 2.000
[    38.584] (**) USB Optical Mouse: (accel) acceleration threshold: 4
[    38.585] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    38.585] (II) No input driver specified, ignoring this device.
[    38.585] (II) This device may have been added with another device file.
[    41.056] (II) NOUVEAU(0): EDID vendor "NUL", prod id 0
[    41.056] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    41.056] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz eP)
[    41.056] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    41.056] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    41.056] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    41.056] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    41.056] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    41.056] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    41.056] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    41.056] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    41.056] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    41.056] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    41.174] (II) NOUVEAU(0): EDID vendor "NUL", prod id 0
[    41.174] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    41.174] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz eP)
[    41.174] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    41.174] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    41.174] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    41.174] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    41.174] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    41.174] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    41.174] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    41.174] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    41.174] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    41.174] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    41.553] (II) NOUVEAU(0): EDID vendor "NUL", prod id 0
[    41.553] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    41.553] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz eP)
[    41.553] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    41.553] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    41.553] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    41.553] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    41.553] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    41.553] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    41.553] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    41.553] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    41.553] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    41.553] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    41.693] (II) NOUVEAU(0): EDID vendor "NUL", prod id 0
[    41.693] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    41.693] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz eP)
[    41.693] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    41.693] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    41.693] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    41.694] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    41.694] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    41.694] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    41.694] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    41.694] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    41.694] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    41.694] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    41.776] resize called 1440 900
[    42.556] (II) NOUVEAU(0): EDID vendor "NUL", prod id 0
[    42.556] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    42.556] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz eP)
[    42.556] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    42.556] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    42.556] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    42.556] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    42.556] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    42.556] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    42.556] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    42.556] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    42.556] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    42.556] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    45.160] (II) NOUVEAU(0): EDID vendor "NUL", prod id 0
[    45.160] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    45.160] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz eP)
[    45.160] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    45.160] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    45.160] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    45.160] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    45.160] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    45.160] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    45.160] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    45.160] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    45.160] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    45.160] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    45.412] (II) NOUVEAU(0): EDID vendor "NUL", prod id 0
[    45.412] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    45.412] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync -vsync (55.9 kHz eP)
[    45.412] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    45.412] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    45.412] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    45.412] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    45.412] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    45.412] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    45.412] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    45.412] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    45.412] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    45.412] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)

```

In the meantime I will search for how to install the Nvidia legacy driver, thanks for replying.

Edit:You think it's the 304 driver butfrom the link to Nvidia in your post it's showing the 173.14xx driver
From a search on the Nvidia site where they unhelpfully don't use the same labels (is it a FX 5000 series????) it returns driver 384.98

Call me confused!

---

### Post by Bashing-om on 2017-11-08
coldraven; Ouch ;

You are so correct in that it is the 173 version driver .. And the bad news is that it no longer has any support .
The nouveau driver is all that is available ; and is installed.

Maybe time to upgrade the graphic's card ? ( I did, nvidia GTX710 on an old AMD CPU ) .

384 driver is suitable for the latest generation nvidia cards !

-A new card will bring new life-

---

### Post by coldraven on 2017-11-08
Thanks for clearing that up, I stupidly bought the card without first checking. I'm surrounded by dead computers, I think I'll take them all to the dump!
I will mark this as solved, at least I managed to get Win7 working.

---

### Post by mörgæs on 2017-11-08
Have you tried Lubuntu 17.10?

---

### Post by coldraven on 2017-11-08
> **mörgæs said:**
> Have you tried Lubuntu 17.10?

I did try booting with it but did not install it. (It looked OK) My intention was to give this PC to someone who is only familiar with Windows, that's why I wanted Mint.
If I do a full install I will post back with the results.

---

### Post by mörgæs on 2017-11-09
If you have lots of old stuff then Lubuntu should be the first distro to install. Much lighter than Mint.

---

### Post by coldraven on 2017-11-11
Well if anyone returns here I did install Lubuntu 17.10. It plays Youtube videos OK but still the nouveau driver does not do hardware rendering.
Here's a snip from hard_info report
```
-Display-
Resolution        : 1440x900 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
```

and the result of
```
$ sudo lshw -C display
[sudo] password for xx: 
  *-display                 
       description: VGA compatible controller
       product: NV34 [GeForce FX 5500]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=32 maxlatency=1 mingnt=5
       resources: irq:16 memory:f8000000-f8ffffff memory:e0000000-efffffff memory:c0000-dffff

```
ATM I cannot afford a better video card. 
Maybe the best if I pull out this HDD and replace it with one that has Win7 on it.

---

