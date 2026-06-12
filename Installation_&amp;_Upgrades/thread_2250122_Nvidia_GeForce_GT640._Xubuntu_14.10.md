---
title: "Nvidia GeForce GT640. Xubuntu 14.10"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by Tristan_Williams on 2014-10-26
I have an eVGA GeForce GT640.

It took some work to get it working in 14.04, but once I got the right driver installed, it worked perfectly. I don't remember which driver I had to use to get it to work.

Thursday, when 14.10 was released, I upgraded, and everything went perfectly except the graphics card. Now Blender doesn't recognize it, so there aren't any CUDA options available.
Also, going to settings and selecting "NVIDIA X Server Settings" gives a message that says:

"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."
I tried running 'nvidia-xconfig', but that command is not found, and I do have nvidia-current installed.
I have tried using ppa:xorg-edgers/ppa, but none of those work either.

So since it doesn't work, there are faint lines travelling down the screen constantly, and I'm not able to do much in Blender since I'll have to render with CPU.



What can I do?

---

### Post by papibe on 2014-10-26
Hi Tristan_Williams.

I'd recommend cleaning the driver and reinstalling it.

Try this:
[LIST]
[*]Remove (rename actually) your Xorg config file:```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
[*]Get the list of Nvidia packages currently installed:```
dpkg -l  | grep nvidia
```
[*]Start purging the nvidia-* packages using this structure:```
sudo apt-get purge nvidia-304
```
[*]Remove all packages separately except for these two:```
nvidia-cg-toolkit
nvidia-common
```
[*]Then reconfigure nvidia common:```
sudo dpkg-reconfigure nvidia-common
```
[*]Install the kernel headers:```
sudo apt-get install linux-headers-generic
```
[*]At this point you can reboot, and you'll be using by default the Open Source driver (nouveau).
[*]Open 'Software Updater' and install all pending updates.
[*]Go to 'Additional drivers' and reinstall the recommend Nvidia driver from there.
[*]When finish, create a new X conf file:```
sudo nvidia-xconfig
```
[/LIST]
Now restart so that the Nvidia driver can take effect.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Tristan_Williams on 2014-10-26
I tried the first command, and turns out I don't even have an /etc/X11/xorg.conf
All I have is /etc/X11/xorg.conf.10232014 and /etc/X11/xorg.conf.backup

---

### Post by papibe on 2014-10-26
I see no problem. Did you continue with the rest of them?

Regards.

---

### Post by Tristan_Williams on 2014-10-26
Yes, until the last part.

```

Tristan ~ $  sudo nvidia-xconfig
[sudo] password for Tristan: 
sudo: nvidia-xconfig: command not found

```

---

### Post by papibe on 2014-10-26
That doesn't look good. As the Nvidia driver hasn't been installed yet.

Did you do this step?
> **papibe said:**
> Go to 'Additional drivers' and reinstall the recommend Nvidia driver from there.
If you did, then something went wrong. Could you run these commands and post back the results?
```
dpkg -l | grep nvidia

apt-cache policy nvidia-current

lspci -nnk | grep -iA2 vga

lsmod | grep -E 'nvidia|nouveau'

```
Regards.

---

### Post by Tristan_Williams on 2014-10-26
```

Tristan ~ $  dpkg -l | grep nvidia
ii  nvidia-331-updates                          331.89-0ubuntu5                                                  amd64        NVIDIA binary driver - version 331.89
ii  nvidia-331-updates-uvm                      331.89-0ubuntu5                                                  amd64        NVIDIA Unified Memory kernel module
ii  nvidia-cg-dev:amd64                         3.1.0013-1                                                       amd64        Cg Toolkit - GPU Shader Authoring Language (headers)
ii  nvidia-cg-toolkit                           3.1.0013-1                                                       amd64        Cg Toolkit - GPU Shader Authoring Language
ii  nvidia-common                               1:0.2.98.4                                                       amd64        transitional package for ubuntu-drivers-common
ii  nvidia-opencl-icd-331-updates               331.89-0ubuntu5                                                  amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.6.7                                                            amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             343.13-0ubuntu1~xedgers14.10.1                                   amd64        Tool for configuring the NVIDIA graphics driver

```

```

Tristan ~ $  apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 304.123-0ubuntu5
  Version table:
     304.123-0ubuntu5 0
        500 http://us.archive.ubuntu.com/ubuntu/ utopic/restricted amd64 Packages
     304.123-0ubuntu1~xedgers14.10.1 0
        500 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ utopic/main amd64 Packages

```

```

Tristan ~ $  lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GT 640] [10de:0fc1] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:2647]
    Kernel driver in use: nouveau
01:00.1 Audio device [0403]: NVIDIA Corporation GK107 HDMI Audio Controller [10de:0e1b] (rev a1)
    Subsystem: eVga.com. Corp. Device [3842:2647]
    Kernel driver in use: snd_hda_intel
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 02)

```

```

Tristan ~ $  lsmod | grep -E 'nvidia|nouveau'
nouveau              1234845  3 
mxm_wmi                13021  1 nouveau
wmi                    19193  2 mxm_wmi,nouveau
video                  20128  1 nouveau
ttm                    89406  1 nouveau
drm_kms_helper         61627  1 nouveau
drm                   310919  6 ttm,drm_kms_helper,nouveau
i2c_algo_bit           13406  1 nouveau


```

---

### Post by papibe on 2014-10-26
Thanks.

The proprietary driver is installed, but it's not being used. At the moment the open source driver is loaded (nouvevau).

Let's check the Xorg log for information. Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [pastebin.ubuntu.com]("http://pastebin.ubuntu.com/"), and then post back the link.

Regards.

EDIT: I'll continue tomorrow. Good Night.

---

### Post by Tristan_Williams on 2014-10-26
> **papibe said:**
> Thanks.

The proprietary driver is installed, but it's not being used. At the moment the open source driver is loaded (nouvevau).

Let's check the Xorg log for information. Could you post the content of this file?
```
/var/log/Xorg.0.log
```
Please paste it here: [pastebin.ubuntu.com]("http://pastebin.ubuntu.com/"), and then post back the link.

Regards.

EDIT: I'll continue tomorrow. Good Night.

```

Tristan ~ $  cat /var/log/Xorg.0.log
[    22.604] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[    22.604] X Protocol Version 11, Revision 0
[    22.604] Build Operating System: Linux 3.13.0-32-generic x86_64 Ubuntu
[    22.604] Current Operating System: Linux Tristans-Desktop 3.16.0-23-generic #31-Ubuntu SMP Tue Oct 21 17:56:17 UTC 2014 x86_64
[    22.604] Kernel command line: BOOT_IMAGE=/vmlinuz-3.16.0-23-generic root=/dev/mapper/xubuntu--vg-root ro quiet splash vt.handoff=7
[    22.604] Build Date: 06 August 2014  01:37:28PM
[    22.604] xorg-server 2:1.16.0+git20140806+server-1.16-branch.a793483e-0ubuntu0sarvatt (For technical support please see http://www.ubuntu.com/support) 
[    22.604] Current version of pixman: 0.32.4
[    22.604]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    22.604] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.604] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Oct 26 22:16:12 2014
[    22.629] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.630] (==) No Layout section.  Using the first Screen section.
[    22.630] (==) No screen section available. Using defaults.
[    22.630] (**) |-->Screen "Default Screen Section" (0)
[    22.630] (**) |   |-->Monitor "<default monitor>"
[    22.630] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    22.631] (==) Automatically adding devices
[    22.631] (==) Automatically enabling devices
[    22.631] (==) Automatically adding GPU devices
[    22.631] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.631]     Entry deleted from font path.
[    22.631] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.631]     Entry deleted from font path.
[    22.631] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.631]     Entry deleted from font path.
[    22.631] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    built-ins
[    22.631] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.631] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.631] (II) Loader magic: 0x7f0326cbed80
[    22.631] (II) Module ABI versions:
[    22.631]     X.Org ANSI C Emulation: 0.4
[    22.631]     X.Org Video Driver: 18.0
[    22.631]     X.Org XInput driver : 21.0
[    22.631]     X.Org Server Extension : 8.0
[    22.631] (II) xfree86: Adding drm device (/dev/dri/card0)
[    22.632] (--) PCI:*(0:1:0:0) 10de:0fc1:3842:2647 rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000dc00/128, BIOS @ 0x????????/524288
[    22.632] (II) LoadModule: "glx"
[    22.633] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.731] (II) Module glx: vendor="X.Org Foundation"
[    22.731]     compiled for 1.16.0, module version = 1.0.0
[    22.731]     ABI class: X.Org Server Extension, version 8.0
[    22.731] (==) AIGLX enabled
[    22.731] (==) Matched nvidia as autoconfigured driver 0
[    22.731] (==) Matched nouveau as autoconfigured driver 1
[    22.731] (==) Matched nvidia as autoconfigured driver 2
[    22.731] (==) Matched nouveau as autoconfigured driver 3
[    22.731] (==) Matched modesetting as autoconfigured driver 4
[    22.731] (==) Matched fbdev as autoconfigured driver 5
[    22.731] (==) Matched vesa as autoconfigured driver 6
[    22.731] (==) Assigned the driver to the xf86ConfigLayout
[    22.731] (II) LoadModule: "nvidia"
[    22.731] (WW) Warning, couldn't open module nvidia
[    22.731] (II) UnloadModule: "nvidia"
[    22.731] (II) Unloading nvidia
[    22.731] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    22.731] (II) LoadModule: "nouveau"
[    22.731] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.742] (II) Module nouveau: vendor="X.Org Foundation"
[    22.742]     compiled for 1.16.0, module version = 1.0.11
[    22.742]     Module class: X.Org Video Driver
[    22.742]     ABI class: X.Org Video Driver, version 18.0
[    22.742] (II) LoadModule: "modesetting"
[    22.742] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.742] (II) Module modesetting: vendor="X.Org Foundation"
[    22.742]     compiled for 1.16.0, module version = 0.9.0
[    22.742]     Module class: X.Org Video Driver
[    22.742]     ABI class: X.Org Video Driver, version 18.0
[    22.742] (II) LoadModule: "fbdev"
[    22.743] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.743] (II) Module fbdev: vendor="X.Org Foundation"
[    22.743]     compiled for 1.16.0, module version = 0.4.4
[    22.743]     Module class: X.Org Video Driver
[    22.743]     ABI class: X.Org Video Driver, version 18.0
[    22.743] (II) LoadModule: "vesa"
[    22.743] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.743] (II) Module vesa: vendor="X.Org Foundation"
[    22.743]     compiled for 1.16.0, module version = 2.3.3
[    22.743]     Module class: X.Org Video Driver
[    22.743]     ABI class: X.Org Video Driver, version 18.0
[    22.743] (==) Matched nvidia as autoconfigured driver 0
[    22.743] (==) Matched nouveau as autoconfigured driver 1
[    22.743] (==) Matched nvidia as autoconfigured driver 2
[    22.743] (==) Matched nouveau as autoconfigured driver 3
[    22.743] (==) Matched modesetting as autoconfigured driver 4
[    22.743] (==) Matched fbdev as autoconfigured driver 5
[    22.743] (==) Matched vesa as autoconfigured driver 6
[    22.743] (==) Assigned the driver to the xf86ConfigLayout
[    22.743] (II) LoadModule: "nvidia"
[    22.743] (WW) Warning, couldn't open module nvidia
[    22.743] (II) UnloadModule: "nvidia"
[    22.743] (II) Unloading nvidia
[    22.743] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    22.743] (II) LoadModule: "nouveau"
[    22.743] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.743] (II) Module nouveau: vendor="X.Org Foundation"
[    22.743]     compiled for 1.16.0, module version = 1.0.11
[    22.743]     Module class: X.Org Video Driver
[    22.743]     ABI class: X.Org Video Driver, version 18.0
[    22.744] (II) UnloadModule: "nouveau"
[    22.744] (II) Unloading nouveau
[    22.744] (II) Failed to load module "nouveau" (already loaded, 0)
[    22.744] (II) LoadModule: "modesetting"
[    22.744] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    22.744] (II) Module modesetting: vendor="X.Org Foundation"
[    22.744]     compiled for 1.16.0, module version = 0.9.0
[    22.744]     Module class: X.Org Video Driver
[    22.744]     ABI class: X.Org Video Driver, version 18.0
[    22.744] (II) UnloadModule: "modesetting"
[    22.744] (II) Unloading modesetting
[    22.744] (II) Failed to load module "modesetting" (already loaded, 0)
[    22.744] (II) LoadModule: "fbdev"
[    22.744] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.744] (II) Module fbdev: vendor="X.Org Foundation"
[    22.744]     compiled for 1.16.0, module version = 0.4.4
[    22.744]     Module class: X.Org Video Driver
[    22.744]     ABI class: X.Org Video Driver, version 18.0
[    22.744] (II) UnloadModule: "fbdev"
[    22.744] (II) Unloading fbdev
[    22.744] (II) Failed to load module "fbdev" (already loaded, 0)
[    22.744] (II) LoadModule: "vesa"
[    22.744] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.744] (II) Module vesa: vendor="X.Org Foundation"
[    22.744]     compiled for 1.16.0, module version = 2.3.3
[    22.744]     Module class: X.Org Video Driver
[    22.744]     ABI class: X.Org Video Driver, version 18.0
[    22.744] (II) UnloadModule: "vesa"
[    22.744] (II) Unloading vesa
[    22.744] (II) Failed to load module "vesa" (already loaded, 0)
[    22.744] (II) NOUVEAU driver 
[    22.744] (II) NOUVEAU driver for NVIDIA chipset families :
[    22.744]     RIVA TNT        (NV04)
[    22.744]     RIVA TNT2       (NV05)
[    22.744]     GeForce 256     (NV10)
[    22.744]     GeForce 2       (NV11, NV15)
[    22.744]     GeForce 4MX     (NV17, NV18)
[    22.744]     GeForce 3       (NV20)
[    22.744]     GeForce 4Ti     (NV25, NV28)
[    22.744]     GeForce FX      (NV3x)
[    22.745]     GeForce 6       (NV4x)
[    22.745]     GeForce 7       (G7x)
[    22.745]     GeForce 8       (G8x)
[    22.745]     GeForce GTX 200 (NVA0)
[    22.745]     GeForce GTX 400 (NVC0)
[    22.745] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    22.745] (II) FBDEV: driver for framebuffer: fbdev
[    22.745] (II) VESA: driver for VESA chipsets: vesa
[    22.745] (++) using VT number 7

[    22.745] (II) [drm] nouveau interface version: 1.1.2
[    22.745] (WW) Falling back to old probe method for modesetting
[    22.745] (WW) Falling back to old probe method for fbdev
[    22.745] (II) Loading sub module "fbdevhw"
[    22.745] (II) LoadModule: "fbdevhw"
[    22.745] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.745] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.745]     compiled for 1.16.0, module version = 0.0.2
[    22.745]     ABI class: X.Org Video Driver, version 18.0
[    22.746] (WW) Falling back to old probe method for vesa
[    22.746] (II) Loading sub module "dri2"
[    22.746] (II) LoadModule: "dri2"
[    22.746] (II) Module "dri2" already built-in
[    22.746] (--) NOUVEAU(0): Chipset: "NVIDIA NVE7"
[    22.746] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    22.746] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    22.746] (==) NOUVEAU(0): RGB weight 888
[    22.746] (==) NOUVEAU(0): Default visual is TrueColor
[    22.746] (==) NOUVEAU(0): Using HW cursor
[    22.746] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[    22.746] (==) NOUVEAU(0): Page flipping enabled
[    22.746] (==) NOUVEAU(0): Swap limit set to 1 [Max allowed 2]
[    22.746] (==) NOUVEAU(0): Page flipping synced to vblank by kernel.
[    22.746] (II) NOUVEAU(0): Initializing outputs ...
[    22.778] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[    22.781] (II) NOUVEAU(0): Output DVI-D-1 has no monitor section
[    22.783] (II) NOUVEAU(0): Output HDMI-1 has no monitor section
[    22.783] (II) NOUVEAU(0): 3 crtcs needed for screen.
[    22.785] (II) NOUVEAU(0): Allocated crtc nr. 0 to this screen.
[    22.785] (II) NOUVEAU(0): Allocated crtc nr. 1 to this screen.
[    22.785] (II) NOUVEAU(0): Allocated crtc nr. 2 to this screen.
[    22.785] (II) NOUVEAU(0): Allocated crtc nr. 3 to this screen.
[    22.818] (II) NOUVEAU(0): EDID for output DVI-I-1
[    22.818] (II) NOUVEAU(0): Manufacturer: LEN  Model: a0c  Serial#: 16843009
[    22.818] (II) NOUVEAU(0): Year: 2011  Week: 31
[    22.818] (II) NOUVEAU(0): EDID Version: 1.3
[    22.818] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[    22.818] (II) NOUVEAU(0): Sync:  Separate  Composite
[    22.818] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    22.818] (II) NOUVEAU(0): Gamma: 2.20
[    22.818] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    22.818] (II) NOUVEAU(0): Default color space is primary color space
[    22.818] (II) NOUVEAU(0): First detailed timing is preferred mode
[    22.818] (II) NOUVEAU(0): redX: 0.640 redY: 0.349   greenX: 0.284 greenY: 0.617
[    22.818] (II) NOUVEAU(0): blueX: 0.142 blueY: 0.067   whiteX: 0.313 whiteY: 0.329
[    22.818] (II) NOUVEAU(0): Supported established timings:
[    22.818] (II) NOUVEAU(0): 720x400@70Hz
[    22.818] (II) NOUVEAU(0): 640x480@60Hz
[    22.818] (II) NOUVEAU(0): 640x480@67Hz
[    22.818] (II) NOUVEAU(0): 640x480@72Hz
[    22.818] (II) NOUVEAU(0): 640x480@75Hz
[    22.818] (II) NOUVEAU(0): 800x600@60Hz
[    22.818] (II) NOUVEAU(0): 800x600@72Hz
[    22.818] (II) NOUVEAU(0): 800x600@75Hz
[    22.818] (II) NOUVEAU(0): 1024x768@60Hz
[    22.818] (II) NOUVEAU(0): 1024x768@70Hz
[    22.818] (II) NOUVEAU(0): 1024x768@75Hz
[    22.818] (II) NOUVEAU(0): 1280x1024@75Hz
[    22.818] (II) NOUVEAU(0): Manufacturer's mask: 0
[    22.818] (II) NOUVEAU(0): Supported standard timings:
[    22.818] (II) NOUVEAU(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    22.818] (II) NOUVEAU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    22.818] (II) NOUVEAU(0): #2: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[    22.818] (II) NOUVEAU(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    22.818] (II) NOUVEAU(0): #4: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    22.818] (II) NOUVEAU(0): #5: hsize: 1600  vsize 1000  refresh: 60  vid: 169
[    22.818] (II) NOUVEAU(0): #6: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    22.818] (II) NOUVEAU(0): #7: hsize: 1680  vsize 1050  refresh: 75  vid: 4019
[    22.818] (II) NOUVEAU(0): Supported detailed timing:
[    22.818] (II) NOUVEAU(0): clock: 146.3 MHz   Image Size:  474 x 296 mm
[    22.818] (II) NOUVEAU(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    22.818] (II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    22.818] (II) NOUVEAU(0): Ranges: V min: 50 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 215 MHz
[    22.818] (II) NOUVEAU(0): Monitor name: L2250p Wide
[    22.818] (II) NOUVEAU(0): Serial No: 6V8W8267
[    22.818] (II) NOUVEAU(0): EDID (in hex):
[    22.818] (II) NOUVEAU(0):     00ffffffffffff0030ae0c0a01010101
[    22.818] (II) NOUVEAU(0):     1f1501036c2f1e78eedc55a359489e24
[    22.818] (II) NOUVEAU(0):     115054bdcf00714f8180818c9500950f
[    22.818] (II) NOUVEAU(0):     a900b300b30f26399030621a274068b0
[    22.818] (II) NOUVEAU(0):     3600da281100001c000000fd00324b1e
[    22.818] (II) NOUVEAU(0):     5315000a202020202020000000fc004c
[    22.818] (II) NOUVEAU(0):     323235307020576964652020000000ff
[    22.818] (II) NOUVEAU(0):     0036563857383236370a2020202000ec
[    22.818] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[    22.818] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.30  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    22.818] (II) NOUVEAU(0): Modeline "1680x1050"x74.9  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.16  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
[    22.818] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.84  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.9 kHz)
[    22.818] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.818] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    22.821] (II) NOUVEAU(0): EDID for output DVI-D-1
[    22.823] (II) NOUVEAU(0): EDID for output HDMI-1
[    22.823] (II) NOUVEAU(0): Output DVI-I-1 connected
[    22.823] (II) NOUVEAU(0): Output DVI-D-1 disconnected
[    22.823] (II) NOUVEAU(0): Output HDMI-1 disconnected
[    22.823] (II) NOUVEAU(0): Using exact sizes for initial modes
[    22.823] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1680x1050
[    22.823] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    22.823] (--) NOUVEAU(0): Virtual size is 1680x1050 (pitch 0)
[    22.823] (**) NOUVEAU(0):  Driver mode "1680x1050": 146.3 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.30  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    22.823] (**) NOUVEAU(0):  Driver mode "1680x1050": 187.0 MHz (scaled from 0.0 MHz), 82.3 kHz, 74.9 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1680x1050"x74.9  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz e)
[    22.823] (**) NOUVEAU(0):  Mode "1600x1000": 133.2 MHz (scaled from 0.0 MHz), 62.1 kHz, 60.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.16  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz)
[    22.823] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    22.823] (**) NOUVEAU(0):  Mode "1280x1024": 132.8 MHz (scaled from 0.0 MHz), 76.9 kHz, 72.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.84  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.9 kHz)
[    22.823] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "1440x900": 136.8 MHz (scaled from 0.0 MHz), 70.6 kHz, 75.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
[    22.823] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    22.823] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
[    22.823] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
[    22.823] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[    22.823] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    22.823] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[    22.823] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    22.823] (==) NOUVEAU(0): DPI set to (96, 96)
[    22.823] (II) Loading sub module "fb"
[    22.823] (II) LoadModule: "fb"
[    22.823] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.824] (II) Module fb: vendor="X.Org Foundation"
[    22.824]     compiled for 1.16.0, module version = 1.0.0
[    22.824]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.824] (II) Loading sub module "shadowfb"
[    22.824] (II) LoadModule: "shadowfb"
[    22.824] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    22.824] (II) Module shadowfb: vendor="X.Org Foundation"
[    22.824]     compiled for 1.16.0, module version = 1.0.0
[    22.824]     ABI class: X.Org ANSI C Emulation, version 0.4
[    22.824] (II) UnloadModule: "modesetting"
[    22.824] (II) Unloading modesetting
[    22.824] (II) UnloadModule: "fbdev"
[    22.824] (II) Unloading fbdev
[    22.824] (II) UnloadSubModule: "fbdevhw"
[    22.824] (II) Unloading fbdevhw
[    22.824] (II) UnloadModule: "vesa"
[    22.824] (II) Unloading vesa
[    22.824] (--) Depth 24 pixmap format is 32 bpp
[    22.826] (II) NOUVEAU(0): Channel setup complete.
[    22.828] (II) NOUVEAU(0): [COPY] async initialised.
[    22.828] (II) NOUVEAU(0): [DRI2] Setup complete
[    22.828] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    22.828] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[    22.829] (II) Loading sub module "exa"
[    22.829] (II) LoadModule: "exa"
[    22.830] (II) Loading /usr/lib/xorg/modules/libexa.so
[    22.830] (II) Module exa: vendor="X.Org Foundation"
[    22.830]     compiled for 1.16.0, module version = 2.6.0
[    22.830]     ABI class: X.Org Video Driver, version 18.0
[    22.830] (II) EXA(0): Driver allocated offscreen pixmaps
[    22.830] (II) EXA(0): Driver registered support for the following operations:
[    22.830] (II)         Solid
[    22.830] (II)         Copy
[    22.830] (II)         Composite (RENDER acceleration)
[    22.830] (II)         UploadToScreen
[    22.830] (II)         DownloadFromScreen
[    22.830] (==) NOUVEAU(0): Backing store enabled
[    22.830] (==) NOUVEAU(0): Silken mouse enabled
[    22.830] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[    22.830] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    22.830] (==) NOUVEAU(0): DPMS enabled
[    22.830] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    22.831] (--) RandR disabled
[    22.836] (II) SELinux: Disabled on system
[    22.938] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    22.938] (II) AIGLX: enabled GLX_ARB_create_context
[    22.938] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    22.938] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    22.938] (II) AIGLX: enabled GLX_INTEL_swap_event
[    22.938] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    22.938] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    22.938] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    22.938] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    22.939] (II) AIGLX: Loaded and initialized nouveau
[    22.939] (II) GLX: Initialized DRI2 GL provider for screen 0
[    22.942] (II) NOUVEAU(0): NVEnterVT is called.
[    23.027] (II) NOUVEAU(0): Setting screen physical size to 444 x 277
[    23.027] resize called 1680 1050
[    23.052] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.054] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.054] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.054] (II) LoadModule: "evdev"
[    23.054] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.084] (II) Module evdev: vendor="X.Org Foundation"
[    23.084]     compiled for 1.16.0, module version = 2.9.0
[    23.084]     Module class: X.Org XInput Driver
[    23.084]     ABI class: X.Org XInput driver, version 21.0
[    23.084] (II) Using input driver 'evdev' for 'Power Button'
[    23.084] (**) Power Button: always reports core events
[    23.084] (**) evdev: Power Button: Device: "/dev/input/event1"
[    23.084] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.084] (--) evdev: Power Button: Found keys
[    23.084] (II) evdev: Power Button: Configuring as keyboard
[    23.084] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.084] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    23.084] (**) Option "xkb_rules" "evdev"
[    23.084] (**) Option "xkb_model" "pc105"
[    23.084] (**) Option "xkb_layout" "us"
[    23.085] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.085] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.085] (II) Using input driver 'evdev' for 'Power Button'
[    23.085] (**) Power Button: always reports core events
[    23.085] (**) evdev: Power Button: Device: "/dev/input/event0"
[    23.085] (--) evdev: Power Button: Vendor 0 Product 0x1
[    23.085] (--) evdev: Power Button: Found keys
[    23.085] (II) evdev: Power Button: Configuring as keyboard
[    23.085] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    23.085] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[    23.085] (**) Option "xkb_rules" "evdev"
[    23.085] (**) Option "xkb_model" "pc105"
[    23.085] (**) Option "xkb_layout" "us"
[    23.086] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event9)
[    23.086] (II) No input driver specified, ignoring this device.
[    23.086] (II) This device may have been added with another device file.
[    23.086] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event10)
[    23.086] (II) No input driver specified, ignoring this device.
[    23.086] (II) This device may have been added with another device file.
[    23.086] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event11)
[    23.086] (II) No input driver specified, ignoring this device.
[    23.086] (II) This device may have been added with another device file.
[    23.086] (II) config/udev: Adding input device DELL Dell USB Entry Keyboard (/dev/input/event2)
[    23.086] (**) DELL Dell USB Entry Keyboard: Applying InputClass "evdev keyboard catchall"
[    23.086] (II) Using input driver 'evdev' for 'DELL Dell USB Entry Keyboard'
[    23.086] (**) DELL Dell USB Entry Keyboard: always reports core events
[    23.086] (**) evdev: DELL Dell USB Entry Keyboard: Device: "/dev/input/event2"
[    23.086] (--) evdev: DELL Dell USB Entry Keyboard: Vendor 0x413c Product 0x2107
[    23.086] (--) evdev: DELL Dell USB Entry Keyboard: Found keys
[    23.086] (II) evdev: DELL Dell USB Entry Keyboard: Configuring as keyboard
[    23.086] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-1/4-1:1.0/0003:413C:2107.0001/input/input5/event2"
[    23.086] (II) XINPUT: Adding extended input device "DELL Dell USB Entry Keyboard" (type: KEYBOARD, id 8)
[    23.086] (**) Option "xkb_rules" "evdev"
[    23.086] (**) Option "xkb_model" "pc105"
[    23.086] (**) Option "xkb_layout" "us"
[    23.087] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/event3)
[    23.087] (**) PixArt USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    23.087] (II) Using input driver 'evdev' for 'PixArt USB Optical Mouse'
[    23.087] (**) PixArt USB Optical Mouse: always reports core events
[    23.087] (**) evdev: PixArt USB Optical Mouse: Device: "/dev/input/event3"
[    23.087] (--) evdev: PixArt USB Optical Mouse: Vendor 0x93a Product 0x2510
[    23.087] (--) evdev: PixArt USB Optical Mouse: Found 3 mouse buttons
[    23.087] (--) evdev: PixArt USB Optical Mouse: Found scroll wheel(s)
[    23.087] (--) evdev: PixArt USB Optical Mouse: Found relative axes
[    23.087] (--) evdev: PixArt USB Optical Mouse: Found x and y relative axes
[    23.087] (II) evdev: PixArt USB Optical Mouse: Configuring as mouse
[    23.087] (II) evdev: PixArt USB Optical Mouse: Adding scrollwheel support
[    23.087] (**) evdev: PixArt USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    23.087] (**) evdev: PixArt USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.087] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.1/usb4/4-2/4-2:1.0/0003:093A:2510.0002/input/input6/event3"
[    23.087] (II) XINPUT: Adding extended input device "PixArt USB Optical Mouse" (type: MOUSE, id 9)
[    23.087] (II) evdev: PixArt USB Optical Mouse: initialized for relative axes.
[    23.087] (**) PixArt USB Optical Mouse: (accel) keeping acceleration scheme 1
[    23.087] (**) PixArt USB Optical Mouse: (accel) acceleration profile 0
[    23.087] (**) PixArt USB Optical Mouse: (accel) acceleration factor: 2.000
[    23.087] (**) PixArt USB Optical Mouse: (accel) acceleration threshold: 4
[    23.088] (II) config/udev: Adding input device PixArt USB Optical Mouse (/dev/input/mouse0)
[    23.088] (II) No input driver specified, ignoring this device.
[    23.088] (II) This device may have been added with another device file.
[    23.088] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event7)
[    23.088] (II) No input driver specified, ignoring this device.
[    23.088] (II) This device may have been added with another device file.
[    23.088] (II) config/udev: Adding input device HDA Intel Front Headphone (/dev/input/event8)
[    23.088] (II) No input driver specified, ignoring this device.
[    23.088] (II) This device may have been added with another device file.
[    23.088] (II) config/udev: Adding input device HDA Intel Front Mic (/dev/input/event4)
[    23.088] (II) No input driver specified, ignoring this device.
[    23.088] (II) This device may have been added with another device file.
[    23.088] (II) config/udev: Adding input device HDA Intel Rear Mic (/dev/input/event5)
[    23.088] (II) No input driver specified, ignoring this device.
[    23.088] (II) This device may have been added with another device file.
[    23.089] (II) config/udev: Adding input device HDA Intel Line (/dev/input/event6)
[    23.089] (II) No input driver specified, ignoring this device.
[    23.089] (II) This device may have been added with another device file.
[    26.551] (II) NOUVEAU(0): EDID vendor "LEN", prod id 2572
[    26.551] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    26.551] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    26.551] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    26.551] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.30  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    26.551] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    26.551] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    26.551] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    26.552] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz e)
[    27.378] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.547] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.550] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.552] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.790] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    27.831] resize called 1680 1050
[    28.767] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.267] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    29.272] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    29.278] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    29.283] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    29.428] (II) NOUVEAU(0): EDID vendor "LEN", prod id 2572
[    29.428] (II) NOUVEAU(0): Using hsync ranges from config file
[    29.428] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    29.428] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    29.428] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.30  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    29.428] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[    29.428] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    29.429] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    29.429] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz e)
[    29.429] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    29.429] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz e)
[    29.584] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    35.205] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
[    39.474] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    40.023] (II) NOUVEAU(0): EDID vendor "LEN", prod id 2572
[    40.023] (II) NOUVEAU(0): Using hsync ranges from config file
[    40.023] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    40.023] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    40.023] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.30  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    40.023] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    40.023] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz e)
[    41.958] (II) NOUVEAU(0): EDID vendor "LEN", prod id 2572
[    41.958] (II) NOUVEAU(0): Using hsync ranges from config file
[    41.958] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    41.958] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    41.958] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.30  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    41.958] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    41.958] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz e)
[    41.998] resize called 1680 1050
[    42.147] (II) NOUVEAU(0): EDID vendor "LEN", prod id 2572
[    42.147] (II) NOUVEAU(0): Using hsync ranges from config file
[    42.147] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    42.147] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    42.147] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.30  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    42.147] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    42.147] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz e)
[    42.202] (II) NOUVEAU(0): EDID vendor "LEN", prod id 2572
[    42.202] (II) NOUVEAU(0): Using hsync ranges from config file
[    42.202] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    42.202] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    42.202] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.30  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    42.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1600x1000"x60.0  133.14  1600 1704 1872 2144  1000 1001 1004 1035 -hsync +vsync (62.1 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    42.202] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  187.00  1680 1800 1976 2272  1050 1053 1059 1099 -hsync +vsync (82.3 kHz e)


```

---

### Post by papibe on 2014-10-27
```
(EE) Failed to load module "nvidia" (module does not exist, 0)
```
This confirms the facts that the system tries to use the nvidia driver and it fails.

Did you purge the proper nvidia packages? In post #2, 'nvidia-304' was an example. In your case you should have done:
```
sudo apt-get purge nvidia-331-updates
sudo apt-get purge nvidia-331-updates-uvm
sudo apt-get purge nvidia-cg-dev:amd64
sudo apt-get purge nvidia-cg-toolkit
sudo apt-get purge nvidia-opencl-icd-331-updates
sudo apt-get purge nvidia-prime
sudo apt-get purge nvidia-settings

```
(this time I'm including cg-toolkit, so the only nvidia package that should survive is nvidia-common)

Could you run this command and post back the results?
```
grep -i nvidia /var/log/dpkg.log
```
Regards.

---

### Post by Tristan_Williams on 2014-10-27
I tried to do 'sudo apt-get purge nvidia-331-updates', but I get the following error:

```

Tristan ~ $  sudo apt-get purge nvidia-331-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-331-updates
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 182 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 298466 files and directories currently installed.)
Removing nvidia-331-updates (331.89-0ubuntu5) ...
stop: Unknown job: nvidia-persistenced
userdel: user nvidia-persistenced is currently used by process 1826
dpkg: error processing package nvidia-331-updates (--remove):
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-331-updates
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The exact same thing happens for all of the packages you listed for removal.

Checking synaptic, I notice that 'nvidia-331-updates' and nvidia-331-updates-uvm' are not installed.
Both of the nvidia-cg-* packages were installed, and I removed them using Synaptic.
The nvidia-prime package was also installed, and so was nvidia-settings.
All of them were removed successfully, except for nvidia-331-updates. Which gives the following error:
```

(synaptic:4969): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 298391 files and directories currently installed.)
Removing nvidia-331-updates (331.89-0ubuntu5) ...
stop: Unknown job: nvidia-persistenced
userdel: user nvidia-persistenced is currently used by process 1826
dpkg: error processing package nvidia-331-updates (--remove):
 subprocess installed post-removal script returned error exit status 8
Errors were encountered while processing:
 nvidia-331-updates
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```


Going on to the last part of your last reply, here is the output:
```

Tristan ~ $  grep -i nvidia /var/log/dpkg.log
2014-10-23 22:52:18 upgrade nvidia-331:amd64 331.38-0ubuntu7.1 331.89-0ubuntu5
2014-10-23 22:52:18 status half-configured nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:41 status unpacked nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:41 status half-installed nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:49 status half-installed nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:56 status half-installed nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:56 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 22:52:56 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:09:52 upgrade nvidia-prime:amd64 0.6.2 0.6.7
2014-10-23 23:09:52 status half-configured nvidia-prime:amd64 0.6.2
2014-10-23 23:09:52 status unpacked nvidia-prime:amd64 0.6.2
2014-10-23 23:09:52 status half-installed nvidia-prime:amd64 0.6.2
2014-10-23 23:09:53 status half-installed nvidia-prime:amd64 0.6.2
2014-10-23 23:09:53 status half-installed nvidia-prime:amd64 0.6.2
2014-10-23 23:09:53 status unpacked nvidia-prime:amd64 0.6.7
2014-10-23 23:09:53 status unpacked nvidia-prime:amd64 0.6.7
2014-10-23 23:18:22 install nvidia-331-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-23 23:18:22 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:18:23 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:18:23 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:18:23 upgrade nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1 331.89-0ubuntu5
2014-10-23 23:18:23 status half-configured nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:23 status unpacked nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:23 status half-installed nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:23 status half-installed nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:24 status unpacked nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:18:24 status unpacked nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:18:24 upgrade nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1 331.89-0ubuntu5
2014-10-23 23:18:24 status half-configured nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:24 status unpacked nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:24 status half-installed nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:25 status half-installed nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:26 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:18:26 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:21:15 upgrade nvidia-cuda-doc:all 5.5.22-3ubuntu1 6.0.37-4
2014-10-23 23:21:15 status half-configured nvidia-cuda-doc:all 5.5.22-3ubuntu1
2014-10-23 23:21:15 status unpacked nvidia-cuda-doc:all 5.5.22-3ubuntu1
2014-10-23 23:21:15 status half-installed nvidia-cuda-doc:all 5.5.22-3ubuntu1
2014-10-23 23:21:20 status half-installed nvidia-cuda-doc:all 5.5.22-3ubuntu1
2014-10-23 23:21:20 status unpacked nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:21:20 status unpacked nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:21:20 upgrade nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1 6.0.37-4
2014-10-23 23:21:20 status half-configured nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1
2014-10-23 23:21:21 status unpacked nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1
2014-10-23 23:21:21 status half-installed nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1
2014-10-23 23:21:21 status half-installed nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1
2014-10-23 23:21:21 status unpacked nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:21:21 status unpacked nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:30:24 configure nvidia-libopencl1-331:amd64 331.89-0ubuntu5 <none>
2014-10-23 23:30:24 status unpacked nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:24 status half-configured nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:24 status installed nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:25 configure nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-23 23:30:25 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:25 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:25 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:25 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:58 configure nvidia-cuda-doc:all 6.0.37-4 <none>
2014-10-23 23:30:58 status unpacked nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:30:58 status half-configured nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:30:58 status installed nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:30:58 configure nvidia-cuda-gdb:amd64 6.0.37-4 <none>
2014-10-23 23:30:58 status unpacked nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:30:58 status half-configured nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:30:58 status installed nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:34:36 configure nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-23 23:34:36 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:34:36 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:34:36 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:35:23 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:35:25 configure nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-23 23:35:25 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:35:25 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:36:05 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:42:37 configure nvidia-prime:amd64 0.6.7 <none>
2014-10-23 23:42:37 status unpacked nvidia-prime:amd64 0.6.7
2014-10-23 23:42:37 status unpacked nvidia-prime:amd64 0.6.7
2014-10-23 23:42:37 status half-configured nvidia-prime:amd64 0.6.7
2014-10-23 23:42:38 status installed nvidia-prime:amd64 0.6.7
2014-10-24 00:05:47 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:05:47 remove nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:05:47 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status not-installed nvidia-331-uvm:amd64 <none>
2014-10-24 00:06:03 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:06:03 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:08 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:08 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:08 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:06:08 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:08 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status installed nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 remove nvidia-libopencl1-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:06:09 status half-configured nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status half-installed nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:13:05 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:13:12 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:13:12 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:13:13 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:13:13 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:24:22 install nvidia-331-updates:amd64 331.38-0ubuntu7.1 331.89-0ubuntu5
2014-10-24 00:24:22 status half-installed nvidia-331-updates:amd64 331.38-0ubuntu7.1
2014-10-24 00:24:28 status half-installed nvidia-331-updates:amd64 331.38-0ubuntu7.1
2014-10-24 00:24:34 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:24:34 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:24:34 install nvidia-331-updates-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-24 00:24:34 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:24:34 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:24:34 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:24:35 install nvidia-opencl-icd-331-updates:amd64 <none> 331.89-0ubuntu5
2014-10-24 00:24:35 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:24:36 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:24:36 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:25:16 configure nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:25:16 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:25:16 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:25:16 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:06 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:06 configure nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:26:06 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:26:06 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 configure nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:26:46 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:02 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:02 remove nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:40:02 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status not-installed nvidia-331-updates-uvm:amd64 <none>
2014-10-24 00:40:15 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:40:15 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:20 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 remove nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:40:21 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:41 install nvidia-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-24 00:40:41 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:46 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:52 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:53 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:53 install nvidia-331-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-24 00:40:53 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:53 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:53 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:54 install nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-24 00:40:54 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:55 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:55 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:57 configure nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:40:57 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:57 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:57 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:41:36 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:41:36 configure nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:41:36 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:41:36 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 configure nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:42:19 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:20 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:20 remove nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:05:20 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:32 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:32 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:32 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:33 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:33 status not-installed nvidia-331-uvm:amd64 <none>
2014-10-26 16:05:33 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:33 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:05:33 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:37 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:05:38 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:39 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:39 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:57 install nvidia-304:amd64 304.117-0ubuntu1 304.123-0ubuntu5
2014-10-26 16:05:57 status half-installed nvidia-304:amd64 304.117-0ubuntu1
2014-10-26 16:06:09 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 install nvidia-current:amd64 <none> 304.123-0ubuntu5
2014-10-26 16:06:09 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 install nvidia-opencl-icd-304:amd64 304.117-0ubuntu1 304.123-0ubuntu5
2014-10-26 16:06:09 status half-installed nvidia-opencl-icd-304:amd64 304.117-0ubuntu1
2014-10-26 16:06:10 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:10 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:14 configure nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:06:14 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:14 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:14 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:52 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:52 configure nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:06:52 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:52 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 configure nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:06:53 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:16:53 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 remove nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:16:54 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status not-installed nvidia-current:amd64 <none>
2014-10-26 16:16:55 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:16:55 remove nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:16:55 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:17 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 remove nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:17:18 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:19 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:20 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:41 install nvidia-331-updates:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:17:41 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:47 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:52 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:53 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:53 install nvidia-331-updates-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-26 16:17:53 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:17:53 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:17:53 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:17:54 install nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:17:54 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:55 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:55 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:59 configure nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:17:59 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:59 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:59 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:18:38 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:18:39 configure nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:18:39 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:18:39 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:19:21 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:19:22 configure nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:19:22 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:19:22 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:19:22 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:19:22 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:02 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:02 remove nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:24:02 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:14 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 status not-installed nvidia-331-updates-uvm:amd64 <none>
2014-10-26 16:24:15 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:24:15 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:20 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:22 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:22 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:23 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:23 remove nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:24:23 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:23 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:23 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:24 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:47 install nvidia-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:24:47 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:24:53 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:24:59 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:24:59 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:24:59 install nvidia-331-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-26 16:24:59 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:25:00 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:25:00 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:25:00 install nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:25:00 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:02 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:02 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:04 configure nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:25:04 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:04 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:04 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:43 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:43 configure nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:25:43 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:25:43 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 configure nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:26:26 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:33:48 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:33:48 remove nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:33:48 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status not-installed nvidia-331-uvm:amd64 <none>
2014-10-26 16:34:01 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:34:01 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:06 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:34:07 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:25 install nvidia-304:amd64 304.123-0ubuntu5 304.123-0ubuntu5
2014-10-26 16:34:25 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 install nvidia-current:amd64 <none> 304.123-0ubuntu5
2014-10-26 16:34:38 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:34:39 install nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 304.123-0ubuntu5
2014-10-26 16:34:39 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:40 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:40 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:42 configure nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:34:42 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:42 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:42 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 configure nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:35:20 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 configure nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:35:20 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:21 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:21 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:21 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 remove nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:44:34 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status not-installed nvidia-current:amd64 <none>
2014-10-26 16:44:34 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 remove nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:44:34 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 remove nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:44:38 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:39 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:39 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:54 install nvidia-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:44:54 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:00 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:05 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:05 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:06 install nvidia-331-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-26 16:45:06 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:45:06 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:45:06 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:45:06 install nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:45:06 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:08 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:08 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:09 configure nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:45:09 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:09 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:10 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:45 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:45 configure nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:45:45 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:45:45 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:46:27 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:46:28 configure nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:46:28 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:46:28 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:46:28 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:46:28 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:32 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:32 remove nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 20:05:32 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:44 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 status not-installed nvidia-331-uvm:amd64 <none>
2014-10-26 20:05:45 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 20:05:45 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:49 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 20:05:50 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:51 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:51 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:06:09 install nvidia-304:amd64 304.123-0ubuntu5 304.123-0ubuntu5
2014-10-26 20:06:09 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:21 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:21 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:22 install nvidia-current:amd64 <none> 304.123-0ubuntu5
2014-10-26 20:06:22 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:06:22 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:06:22 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:06:22 install nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 304.123-0ubuntu5
2014-10-26 20:06:22 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:23 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:23 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:25 configure nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 20:06:25 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:25 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:25 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 configure nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 20:07:00 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 configure nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 20:07:00 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:01 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 21:19:05 upgrade nvidia-settings:amd64 340.29-0ubuntu1 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:05 status half-configured nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status unpacked nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status half-installed nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status half-installed nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status half-installed nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:06 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:33 configure nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-26 21:19:33 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:33 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:33 status half-configured nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:33 status installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:57:23 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:30 remove nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 21:57:30 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:30 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:30 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:31 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:31 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:31 status not-installed nvidia-current:amd64 <none>
2014-10-26 21:57:31 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:31 remove nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 21:57:31 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:44 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 purge nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:46 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:46 status not-installed nvidia-304:amd64 <none>
2014-10-26 22:00:05 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:05 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:00:05 purge nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:00:05 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:05 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:06 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:06 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:06 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:06 status not-installed nvidia-331:amd64 <none>
2014-10-26 22:01:04 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:01:05 purge nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status not-installed nvidia-331-updates:amd64 <none>
2014-10-26 22:02:14 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 remove nvidia-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:02:15 purge nvidia-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status not-installed nvidia-340:amd64 <none>
2014-10-26 22:03:04 status installed nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:04 remove nvidia-cuda-doc:all 6.0.37-4 <none>
2014-10-26 22:03:04 status half-configured nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:04 status half-installed nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:05 status config-files nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:05 status config-files nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:05 status config-files nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:05 status not-installed nvidia-cuda-doc:all <none>
2014-10-26 22:03:39 status installed nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 remove nvidia-cuda-gdb:amd64 6.0.37-4 <none>
2014-10-26 22:03:40 status half-configured nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status half-installed nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status config-files nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status config-files nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status config-files nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status not-installed nvidia-cuda-gdb:amd64 <none>
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 remove nvidia-libopencl1-304:amd64 304.117-0ubuntu1 <none>
2014-10-26 22:04:08 purge nvidia-libopencl1-304:amd64 304.117-0ubuntu1 <none>
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status not-installed nvidia-libopencl1-304:amd64 <none>
2014-10-26 22:05:47 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 remove nvidia-libopencl1-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:05:48 purge nvidia-libopencl1-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status not-installed nvidia-libopencl1-331:amd64 <none>
2014-10-26 22:06:04 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 remove nvidia-libopencl1-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:06:05 purge nvidia-libopencl1-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status not-installed nvidia-libopencl1-340:amd64 <none>
2014-10-26 22:06:15 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 remove nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 22:06:16 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 purge nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status not-installed nvidia-opencl-icd-304:amd64 <none>
2014-10-26 22:06:59 status installed nvidia-prime:amd64 0.6.7
2014-10-26 22:06:59 remove nvidia-prime:amd64 0.6.7 <none>
2014-10-26 22:06:59 status half-configured nvidia-prime:amd64 0.6.7
2014-10-26 22:06:59 status half-installed nvidia-prime:amd64 0.6.7
2014-10-26 22:07:00 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:07:00 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:08:26 purge nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:27 status not-installed nvidia-opencl-icd-331:amd64 <none>
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 remove nvidia-opencl-icd-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:09:58 purge nvidia-opencl-icd-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status not-installed nvidia-opencl-icd-340:amd64 <none>
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:43 remove nvidia-prime:amd64 0.6.7 <none>
2014-10-26 22:10:43 purge nvidia-prime:amd64 0.6.7 <none>
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:44 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:44 status not-installed nvidia-prime:amd64 <none>
2014-10-26 22:10:58 status installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:58 remove nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-26 22:10:58 status half-configured nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:58 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:58 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 purge nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status not-installed nvidia-settings:amd64 <none>
2014-10-26 22:13:11 install nvidia-cg-dev:amd64 <none> 3.1.0013-1
2014-10-26 22:13:11 status half-installed nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:11 status unpacked nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:11 status unpacked nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:11 install nvidia-cg-toolkit:amd64 <none> 3.1.0013-1
2014-10-26 22:13:11 status half-installed nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:12 status unpacked nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:12 status unpacked nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:12 install nvidia-common:amd64 <none> 1:0.2.98.4
2014-10-26 22:13:12 status half-installed nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:12 status unpacked nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:12 status unpacked nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:14 configure nvidia-cg-dev:amd64 3.1.0013-1 <none>
2014-10-26 22:13:14 status unpacked nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:14 status half-configured nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:14 status installed nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:14 configure nvidia-cg-toolkit:amd64 3.1.0013-1 <none>
2014-10-26 22:13:14 status unpacked nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:14 status half-configured nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:14 status installed nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:14 configure nvidia-common:amd64 1:0.2.98.4 <none>
2014-10-26 22:13:14 status unpacked nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:15 status half-configured nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:15 status installed nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:20:01 install nvidia-331-updates:amd64 <none> 331.89-0ubuntu5
2014-10-26 22:20:01 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:07 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:13 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:13 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:14 install nvidia-331-updates-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-26 22:20:14 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:20:14 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:20:14 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:20:14 install nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 22:20:14 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:15 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:15 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:17 install nvidia-prime:amd64 <none> 0.6.7
2014-10-26 22:20:17 status half-installed nvidia-prime:amd64 0.6.7
2014-10-26 22:20:17 status half-installed nvidia-prime:amd64 0.6.7
2014-10-26 22:20:17 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:20:17 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:20:18 install nvidia-settings:amd64 <none> 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:18 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:18 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:19 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:19 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:23 configure nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:20:23 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:23 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:23 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:13 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:13 configure nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:21:13 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:21:13 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 configure nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:21:56 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:22:09 configure nvidia-prime:amd64 0.6.7 <none>
2014-10-26 22:22:09 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:22:09 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:22:09 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:22:09 status half-configured nvidia-prime:amd64 0.6.7
2014-10-26 22:22:09 status triggers-awaited nvidia-prime:amd64 0.6.7
2014-10-26 22:22:10 configure nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-26 22:22:10 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:22:10 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:22:10 status half-configured nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:22:10 status installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:22:11 status installed nvidia-prime:amd64 0.6.7
2014-10-27 15:54:58 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:05 remove nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:55:05 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:17 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 status not-installed nvidia-331-updates-uvm:amd64 <none>
2014-10-27 15:55:18 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:55:18 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:55:22 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:55:39 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:55:39 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:55:39 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:56:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:56:53 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:56:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:10 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:11 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:11 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:21 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:21 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:21 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:30 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:31 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:31 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:45 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:45 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:45 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:53 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:33 status installed nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 remove nvidia-cg-toolkit:amd64 3.1.0013-1 <none>
2014-10-27 16:04:33 status half-configured nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 status half-installed nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 status config-files nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 status config-files nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 status config-files nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:34 status not-installed nvidia-cg-toolkit:amd64 <none>
2014-10-27 16:04:34 status installed nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 remove nvidia-cg-dev:amd64 3.1.0013-1 <none>
2014-10-27 16:04:34 status half-configured nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status half-installed nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status config-files nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status config-files nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status config-files nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status not-installed nvidia-cg-dev:amd64 <none>
2014-10-27 16:04:34 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:34 remove nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:04:34 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:34 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 purge nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status not-installed nvidia-opencl-icd-331-updates:amd64 <none>
2014-10-27 16:04:35 status installed nvidia-prime:amd64 0.6.7
2014-10-27 16:04:35 remove nvidia-prime:amd64 0.6.7 <none>
2014-10-27 16:04:35 status half-configured nvidia-prime:amd64 0.6.7
2014-10-27 16:04:35 status half-installed nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 purge nvidia-prime:amd64 0.6.7 <none>
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status not-installed nvidia-prime:amd64 <none>
2014-10-27 16:04:36 status installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 remove nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-27 16:04:37 status half-configured nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 purge nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status not-installed nvidia-settings:amd64 <none>
2014-10-27 16:06:02 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:06:03 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:06:03 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:06:32 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:06:33 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:06:33 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:08:03 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:08:03 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:08:03 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:09:08 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:09:08 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:09:08 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5

```

---

### Post by papibe on 2014-10-27
Try this before purging the packages:
```
sudo killall nvidia-persistenced
```
Regards.

---

### Post by Tristan_Williams on 2014-10-27
That worked. All packages are removed now

Here's the output from that command

```

Tristan ~ $  grep -i nvidia /var/log/dpkg.log
2014-10-23 22:52:18 upgrade nvidia-331:amd64 331.38-0ubuntu7.1 331.89-0ubuntu5
2014-10-23 22:52:18 status half-configured nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:41 status unpacked nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:41 status half-installed nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:49 status half-installed nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:56 status half-installed nvidia-331:amd64 331.38-0ubuntu7.1
2014-10-23 22:52:56 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 22:52:56 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:09:52 upgrade nvidia-prime:amd64 0.6.2 0.6.7
2014-10-23 23:09:52 status half-configured nvidia-prime:amd64 0.6.2
2014-10-23 23:09:52 status unpacked nvidia-prime:amd64 0.6.2
2014-10-23 23:09:52 status half-installed nvidia-prime:amd64 0.6.2
2014-10-23 23:09:53 status half-installed nvidia-prime:amd64 0.6.2
2014-10-23 23:09:53 status half-installed nvidia-prime:amd64 0.6.2
2014-10-23 23:09:53 status unpacked nvidia-prime:amd64 0.6.7
2014-10-23 23:09:53 status unpacked nvidia-prime:amd64 0.6.7
2014-10-23 23:18:22 install nvidia-331-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-23 23:18:22 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:18:23 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:18:23 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:18:23 upgrade nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1 331.89-0ubuntu5
2014-10-23 23:18:23 status half-configured nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:23 status unpacked nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:23 status half-installed nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:23 status half-installed nvidia-libopencl1-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:24 status unpacked nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:18:24 status unpacked nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:18:24 upgrade nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1 331.89-0ubuntu5
2014-10-23 23:18:24 status half-configured nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:24 status unpacked nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:24 status half-installed nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:25 status half-installed nvidia-opencl-icd-331:amd64 331.38-0ubuntu7.1
2014-10-23 23:18:26 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:18:26 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:21:15 upgrade nvidia-cuda-doc:all 5.5.22-3ubuntu1 6.0.37-4
2014-10-23 23:21:15 status half-configured nvidia-cuda-doc:all 5.5.22-3ubuntu1
2014-10-23 23:21:15 status unpacked nvidia-cuda-doc:all 5.5.22-3ubuntu1
2014-10-23 23:21:15 status half-installed nvidia-cuda-doc:all 5.5.22-3ubuntu1
2014-10-23 23:21:20 status half-installed nvidia-cuda-doc:all 5.5.22-3ubuntu1
2014-10-23 23:21:20 status unpacked nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:21:20 status unpacked nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:21:20 upgrade nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1 6.0.37-4
2014-10-23 23:21:20 status half-configured nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1
2014-10-23 23:21:21 status unpacked nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1
2014-10-23 23:21:21 status half-installed nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1
2014-10-23 23:21:21 status half-installed nvidia-cuda-gdb:amd64 5.5.22-3ubuntu1
2014-10-23 23:21:21 status unpacked nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:21:21 status unpacked nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:30:24 configure nvidia-libopencl1-331:amd64 331.89-0ubuntu5 <none>
2014-10-23 23:30:24 status unpacked nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:24 status half-configured nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:24 status installed nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:25 configure nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-23 23:30:25 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:25 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:25 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:25 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-23 23:30:58 configure nvidia-cuda-doc:all 6.0.37-4 <none>
2014-10-23 23:30:58 status unpacked nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:30:58 status half-configured nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:30:58 status installed nvidia-cuda-doc:all 6.0.37-4
2014-10-23 23:30:58 configure nvidia-cuda-gdb:amd64 6.0.37-4 <none>
2014-10-23 23:30:58 status unpacked nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:30:58 status half-configured nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:30:58 status installed nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-23 23:34:36 configure nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-23 23:34:36 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:34:36 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:34:36 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:35:23 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-23 23:35:25 configure nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-23 23:35:25 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:35:25 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:36:05 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-23 23:42:37 configure nvidia-prime:amd64 0.6.7 <none>
2014-10-23 23:42:37 status unpacked nvidia-prime:amd64 0.6.7
2014-10-23 23:42:37 status unpacked nvidia-prime:amd64 0.6.7
2014-10-23 23:42:37 status half-configured nvidia-prime:amd64 0.6.7
2014-10-23 23:42:38 status installed nvidia-prime:amd64 0.6.7
2014-10-24 00:05:47 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:05:47 remove nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:05:47 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 status not-installed nvidia-331-uvm:amd64 <none>
2014-10-24 00:06:03 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:03 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:06:03 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:08 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:08 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:08 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:06:08 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:08 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status installed nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 remove nvidia-libopencl1-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:06:09 status half-configured nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status half-installed nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:06:09 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-24 00:13:05 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:13:12 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:13:12 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:13:13 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:13:13 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:24:22 install nvidia-331-updates:amd64 331.38-0ubuntu7.1 331.89-0ubuntu5
2014-10-24 00:24:22 status half-installed nvidia-331-updates:amd64 331.38-0ubuntu7.1
2014-10-24 00:24:28 status half-installed nvidia-331-updates:amd64 331.38-0ubuntu7.1
2014-10-24 00:24:34 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:24:34 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:24:34 install nvidia-331-updates-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-24 00:24:34 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:24:34 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:24:34 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:24:35 install nvidia-opencl-icd-331-updates:amd64 <none> 331.89-0ubuntu5
2014-10-24 00:24:35 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:24:36 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:24:36 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:25:16 configure nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:25:16 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:25:16 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:25:16 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:06 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:06 configure nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:26:06 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:26:06 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 configure nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:26:46 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:26:46 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:02 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:02 remove nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:40:02 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 status not-installed nvidia-331-updates-uvm:amd64 <none>
2014-10-24 00:40:15 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:15 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:40:15 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:20 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 remove nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:40:21 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:21 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-24 00:40:41 install nvidia-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-24 00:40:41 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:46 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:52 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:53 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:53 install nvidia-331-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-24 00:40:53 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:53 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:53 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:40:54 install nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-24 00:40:54 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:55 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:55 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:57 configure nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:40:57 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:57 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:40:57 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:41:36 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-24 00:41:36 configure nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:41:36 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:41:36 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 configure nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-24 00:42:19 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-24 00:42:19 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:20 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:20 remove nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:05:20 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:32 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:32 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:32 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:33 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:05:33 status not-installed nvidia-331-uvm:amd64 <none>
2014-10-26 16:05:33 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:33 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:05:33 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:37 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:05:38 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:38 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:39 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:39 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:05:57 install nvidia-304:amd64 304.117-0ubuntu1 304.123-0ubuntu5
2014-10-26 16:05:57 status half-installed nvidia-304:amd64 304.117-0ubuntu1
2014-10-26 16:06:09 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 install nvidia-current:amd64 <none> 304.123-0ubuntu5
2014-10-26 16:06:09 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:09 install nvidia-opencl-icd-304:amd64 304.117-0ubuntu1 304.123-0ubuntu5
2014-10-26 16:06:09 status half-installed nvidia-opencl-icd-304:amd64 304.117-0ubuntu1
2014-10-26 16:06:10 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:10 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:14 configure nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:06:14 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:14 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:14 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:52 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:52 configure nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:06:52 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:52 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 configure nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:06:53 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:06:53 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:16:53 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 remove nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:16:54 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:16:54 status not-installed nvidia-current:amd64 <none>
2014-10-26 16:16:55 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:16:55 remove nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:16:55 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:17 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 remove nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:17:18 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:18 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:19 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:20 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:17:41 install nvidia-331-updates:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:17:41 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:47 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:52 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:53 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:53 install nvidia-331-updates-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-26 16:17:53 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:17:53 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:17:53 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:17:54 install nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:17:54 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:55 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:55 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:59 configure nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:17:59 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:59 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:17:59 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:18:38 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:18:39 configure nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:18:39 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:18:39 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:19:21 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:19:22 configure nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:19:22 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:19:22 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:19:22 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:19:22 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:02 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:02 remove nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:24:02 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:14 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 status not-installed nvidia-331-updates-uvm:amd64 <none>
2014-10-26 16:24:15 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:15 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:24:15 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:20 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:22 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:22 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:23 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:23 remove nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:24:23 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:23 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:23 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:24 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 16:24:47 install nvidia-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:24:47 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:24:53 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:24:59 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:24:59 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:24:59 install nvidia-331-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-26 16:24:59 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:25:00 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:25:00 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:25:00 install nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:25:00 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:02 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:02 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:04 configure nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:25:04 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:04 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:04 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:43 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:25:43 configure nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:25:43 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:25:43 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 configure nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:26:26 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:26:26 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:33:48 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:33:48 remove nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:33:48 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 status not-installed nvidia-331-uvm:amd64 <none>
2014-10-26 16:34:01 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:01 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:34:01 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:06 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:34:07 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:07 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:34:25 install nvidia-304:amd64 304.123-0ubuntu5 304.123-0ubuntu5
2014-10-26 16:34:25 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 install nvidia-current:amd64 <none> 304.123-0ubuntu5
2014-10-26 16:34:38 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:34:38 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:34:39 install nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 304.123-0ubuntu5
2014-10-26 16:34:39 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:40 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:40 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:42 configure nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:34:42 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:42 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:34:42 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 configure nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:35:20 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:35:20 configure nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:35:20 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:21 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:21 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:35:21 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 remove nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:44:34 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 status not-installed nvidia-current:amd64 <none>
2014-10-26 16:44:34 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:34 remove nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:44:34 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 remove nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 16:44:38 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:38 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:39 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:39 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 16:44:54 install nvidia-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:44:54 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:00 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:05 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:05 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:06 install nvidia-331-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-26 16:45:06 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:45:06 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:45:06 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:45:06 install nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 16:45:06 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:08 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:08 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:09 configure nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:45:09 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:09 status unpacked nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:10 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:45 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 16:45:45 configure nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:45:45 status unpacked nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:45:45 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:46:27 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 16:46:28 configure nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 16:46:28 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:46:28 status unpacked nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:46:28 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 16:46:28 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:32 status installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:32 remove nvidia-331-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 20:05:32 status half-configured nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:44 status half-installed nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 status config-files nvidia-331-uvm:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 status not-installed nvidia-331-uvm:amd64 <none>
2014-10-26 20:05:45 status installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:45 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 20:05:45 status half-configured nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:49 status half-installed nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 status installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 20:05:50 status half-configured nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:50 status half-installed nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:51 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:05:51 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 20:06:09 install nvidia-304:amd64 304.123-0ubuntu5 304.123-0ubuntu5
2014-10-26 20:06:09 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:21 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:21 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:22 install nvidia-current:amd64 <none> 304.123-0ubuntu5
2014-10-26 20:06:22 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:06:22 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:06:22 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:06:22 install nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 304.123-0ubuntu5
2014-10-26 20:06:22 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:23 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:23 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:25 configure nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 20:06:25 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:25 status unpacked nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:06:25 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 configure nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 20:07:00 status unpacked nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 configure nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 20:07:00 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status unpacked nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:00 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 20:07:01 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 21:19:05 upgrade nvidia-settings:amd64 340.29-0ubuntu1 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:05 status half-configured nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status unpacked nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status half-installed nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status half-installed nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status half-installed nvidia-settings:amd64 340.29-0ubuntu1
2014-10-26 21:19:05 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:06 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:33 configure nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-26 21:19:33 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:33 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:33 status half-configured nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:19:33 status installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 21:57:23 status installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:30 remove nvidia-current:amd64 304.123-0ubuntu5 <none>
2014-10-26 21:57:30 status half-configured nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:30 status half-installed nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:30 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:31 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:31 status config-files nvidia-current:amd64 304.123-0ubuntu5
2014-10-26 21:57:31 status not-installed nvidia-current:amd64 <none>
2014-10-26 21:57:31 status installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:31 remove nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 21:57:31 status half-configured nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:44 status half-installed nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 purge nvidia-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:45 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:46 status config-files nvidia-304:amd64 304.123-0ubuntu5
2014-10-26 21:57:46 status not-installed nvidia-304:amd64 <none>
2014-10-26 22:00:05 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:05 remove nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:00:05 purge nvidia-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:00:05 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:05 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:06 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:06 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:06 status config-files nvidia-331:amd64 331.89-0ubuntu5
2014-10-26 22:00:06 status not-installed nvidia-331:amd64 <none>
2014-10-26 22:01:04 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:01:05 purge nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:01:05 status not-installed nvidia-331-updates:amd64 <none>
2014-10-26 22:02:14 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 remove nvidia-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:02:15 purge nvidia-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status config-files nvidia-340:amd64 340.29-0ubuntu1
2014-10-26 22:02:15 status not-installed nvidia-340:amd64 <none>
2014-10-26 22:03:04 status installed nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:04 remove nvidia-cuda-doc:all 6.0.37-4 <none>
2014-10-26 22:03:04 status half-configured nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:04 status half-installed nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:05 status config-files nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:05 status config-files nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:05 status config-files nvidia-cuda-doc:all 6.0.37-4
2014-10-26 22:03:05 status not-installed nvidia-cuda-doc:all <none>
2014-10-26 22:03:39 status installed nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 remove nvidia-cuda-gdb:amd64 6.0.37-4 <none>
2014-10-26 22:03:40 status half-configured nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status half-installed nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status config-files nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status config-files nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status config-files nvidia-cuda-gdb:amd64 6.0.37-4
2014-10-26 22:03:40 status not-installed nvidia-cuda-gdb:amd64 <none>
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 remove nvidia-libopencl1-304:amd64 304.117-0ubuntu1 <none>
2014-10-26 22:04:08 purge nvidia-libopencl1-304:amd64 304.117-0ubuntu1 <none>
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status config-files nvidia-libopencl1-304:amd64 304.117-0ubuntu1
2014-10-26 22:04:08 status not-installed nvidia-libopencl1-304:amd64 <none>
2014-10-26 22:05:47 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 remove nvidia-libopencl1-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:05:48 purge nvidia-libopencl1-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status config-files nvidia-libopencl1-331:amd64 331.89-0ubuntu5
2014-10-26 22:05:48 status not-installed nvidia-libopencl1-331:amd64 <none>
2014-10-26 22:06:04 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 remove nvidia-libopencl1-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:06:05 purge nvidia-libopencl1-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status config-files nvidia-libopencl1-340:amd64 340.29-0ubuntu1
2014-10-26 22:06:05 status not-installed nvidia-libopencl1-340:amd64 <none>
2014-10-26 22:06:15 status installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 remove nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 22:06:16 status half-configured nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status half-installed nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 purge nvidia-opencl-icd-304:amd64 304.123-0ubuntu5 <none>
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status config-files nvidia-opencl-icd-304:amd64 304.123-0ubuntu5
2014-10-26 22:06:16 status not-installed nvidia-opencl-icd-304:amd64 <none>
2014-10-26 22:06:59 status installed nvidia-prime:amd64 0.6.7
2014-10-26 22:06:59 remove nvidia-prime:amd64 0.6.7 <none>
2014-10-26 22:06:59 status half-configured nvidia-prime:amd64 0.6.7
2014-10-26 22:06:59 status half-installed nvidia-prime:amd64 0.6.7
2014-10-26 22:07:00 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:07:00 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 remove nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:08:26 purge nvidia-opencl-icd-331:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:26 status config-files nvidia-opencl-icd-331:amd64 331.89-0ubuntu5
2014-10-26 22:08:27 status not-installed nvidia-opencl-icd-331:amd64 <none>
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 remove nvidia-opencl-icd-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:09:58 purge nvidia-opencl-icd-340:amd64 340.29-0ubuntu1 <none>
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status config-files nvidia-opencl-icd-340:amd64 340.29-0ubuntu1
2014-10-26 22:09:58 status not-installed nvidia-opencl-icd-340:amd64 <none>
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:43 remove nvidia-prime:amd64 0.6.7 <none>
2014-10-26 22:10:43 purge nvidia-prime:amd64 0.6.7 <none>
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:43 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:44 status config-files nvidia-prime:amd64 0.6.7
2014-10-26 22:10:44 status not-installed nvidia-prime:amd64 <none>
2014-10-26 22:10:58 status installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:58 remove nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-26 22:10:58 status half-configured nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:58 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:58 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 purge nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:10:59 status not-installed nvidia-settings:amd64 <none>
2014-10-26 22:13:11 install nvidia-cg-dev:amd64 <none> 3.1.0013-1
2014-10-26 22:13:11 status half-installed nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:11 status unpacked nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:11 status unpacked nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:11 install nvidia-cg-toolkit:amd64 <none> 3.1.0013-1
2014-10-26 22:13:11 status half-installed nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:12 status unpacked nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:12 status unpacked nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:12 install nvidia-common:amd64 <none> 1:0.2.98.4
2014-10-26 22:13:12 status half-installed nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:12 status unpacked nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:12 status unpacked nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:14 configure nvidia-cg-dev:amd64 3.1.0013-1 <none>
2014-10-26 22:13:14 status unpacked nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:14 status half-configured nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:14 status installed nvidia-cg-dev:amd64 3.1.0013-1
2014-10-26 22:13:14 configure nvidia-cg-toolkit:amd64 3.1.0013-1 <none>
2014-10-26 22:13:14 status unpacked nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:14 status half-configured nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:14 status installed nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-26 22:13:14 configure nvidia-common:amd64 1:0.2.98.4 <none>
2014-10-26 22:13:14 status unpacked nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:15 status half-configured nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:13:15 status installed nvidia-common:amd64 1:0.2.98.4
2014-10-26 22:20:01 install nvidia-331-updates:amd64 <none> 331.89-0ubuntu5
2014-10-26 22:20:01 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:07 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:13 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:13 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:14 install nvidia-331-updates-uvm:amd64 <none> 331.89-0ubuntu5
2014-10-26 22:20:14 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:20:14 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:20:14 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:20:14 install nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 331.89-0ubuntu5
2014-10-26 22:20:14 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:15 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:15 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:17 install nvidia-prime:amd64 <none> 0.6.7
2014-10-26 22:20:17 status half-installed nvidia-prime:amd64 0.6.7
2014-10-26 22:20:17 status half-installed nvidia-prime:amd64 0.6.7
2014-10-26 22:20:17 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:20:17 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:20:18 install nvidia-settings:amd64 <none> 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:18 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:18 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:19 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:19 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:20:23 configure nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:20:23 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:23 status unpacked nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:20:23 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:13 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:13 configure nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:21:13 status unpacked nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:21:13 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 configure nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-26 22:21:56 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 status unpacked nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:21:56 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-26 22:22:09 configure nvidia-prime:amd64 0.6.7 <none>
2014-10-26 22:22:09 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:22:09 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:22:09 status unpacked nvidia-prime:amd64 0.6.7
2014-10-26 22:22:09 status half-configured nvidia-prime:amd64 0.6.7
2014-10-26 22:22:09 status triggers-awaited nvidia-prime:amd64 0.6.7
2014-10-26 22:22:10 configure nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-26 22:22:10 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:22:10 status unpacked nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:22:10 status half-configured nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:22:10 status installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-26 22:22:11 status installed nvidia-prime:amd64 0.6.7
2014-10-27 15:54:58 status installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:05 remove nvidia-331-updates-uvm:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:55:05 status half-configured nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:17 status half-installed nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 status config-files nvidia-331-updates-uvm:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 status not-installed nvidia-331-updates-uvm:amd64 <none>
2014-10-27 15:55:18 status installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:55:18 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:55:18 status half-configured nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:55:22 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:55:39 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:55:39 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:55:39 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:56:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:56:53 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:56:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:10 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:11 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:11 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:21 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:21 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:21 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:30 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:31 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:31 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:45 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:45 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:45 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 15:57:53 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 15:57:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:33 status installed nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 remove nvidia-cg-toolkit:amd64 3.1.0013-1 <none>
2014-10-27 16:04:33 status half-configured nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 status half-installed nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 status config-files nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 status config-files nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:33 status config-files nvidia-cg-toolkit:amd64 3.1.0013-1
2014-10-27 16:04:34 status not-installed nvidia-cg-toolkit:amd64 <none>
2014-10-27 16:04:34 status installed nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 remove nvidia-cg-dev:amd64 3.1.0013-1 <none>
2014-10-27 16:04:34 status half-configured nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status half-installed nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status config-files nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status config-files nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status config-files nvidia-cg-dev:amd64 3.1.0013-1
2014-10-27 16:04:34 status not-installed nvidia-cg-dev:amd64 <none>
2014-10-27 16:04:34 status installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:34 remove nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:04:34 status half-configured nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:34 status half-installed nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 purge nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status config-files nvidia-opencl-icd-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:04:35 status not-installed nvidia-opencl-icd-331-updates:amd64 <none>
2014-10-27 16:04:35 status installed nvidia-prime:amd64 0.6.7
2014-10-27 16:04:35 remove nvidia-prime:amd64 0.6.7 <none>
2014-10-27 16:04:35 status half-configured nvidia-prime:amd64 0.6.7
2014-10-27 16:04:35 status half-installed nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 purge nvidia-prime:amd64 0.6.7 <none>
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status config-files nvidia-prime:amd64 0.6.7
2014-10-27 16:04:36 status not-installed nvidia-prime:amd64 <none>
2014-10-27 16:04:36 status installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 remove nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-27 16:04:37 status half-configured nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status half-installed nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 purge nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1 <none>
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status config-files nvidia-settings:amd64 343.13-0ubuntu1~xedgers14.10.1
2014-10-27 16:04:37 status not-installed nvidia-settings:amd64 <none>
2014-10-27 16:06:02 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:06:03 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:06:03 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:06:32 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:06:33 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:06:33 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:08:03 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:08:03 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:08:03 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:09:08 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:09:08 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:09:08 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:35:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:35:53 remove nvidia-331-updates:amd64 331.89-0ubuntu5 <none>
2014-10-27 16:35:53 status half-installed nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:35:54 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5
2014-10-27 16:35:54 status config-files nvidia-331-updates:amd64 331.89-0ubuntu5

```

---

### Post by papibe on 2014-10-27
Great :)

Now, reconfigure nvidia-common:
```
sudo dpkg-reconfigure nvidia-common
```
Then reboot, and try to install the nvidia driver again.

Regards.

---

### Post by Tristan_Williams on 2014-10-27
I did as you said, and it seems to have done a little bit.

The faint lines on the desktop are no longer there.
However, Blender still does not recognize it.

Are there more steps I am missing?

---

