---
title: "[drm] Failed toopen DRM device for pci:xxxx:xx:xx.x"
date: 2020-06-27
forum: Installation &amp; Upgrades
---

### Post by nilesj on 2020-06-27
Hello,

After a recent reboot I am no longer able to startx on Ubuntu Studio 20.04.  I had this same problem while installing it and managed to fix it with a combination of reinstalling nvidia drivers over and over and dumb luck, but this time I am hopelessly stuck and don't know where to check next.

Xord.0.log:
```
[   704.554] 
X.Org X Server 1.20.8
X Protocol Version 11, Revision 0
[   704.562] Build Operating System: Linux 4.4.0-179-generic x86_64 Ubuntu
[   704.565] Current Operating System: Linux Hostname 5.4.0-39-lowlatency #43-Ubuntu SMP PREEMPT Fri Jun 19 11:21:20 UTC 2020 x86_64
[   704.565] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.4.0-39-lowlatency root=UUID=99fad966-85c2-457b-af2e-0e9668cace38 ro quiet splash vt.handoff=1
[   704.573] Build Date: 21 May 2020  08:22:15AM
[   704.576] xorg-server 2:1.20.8-2ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[   704.579] Current version of pixman: 0.38.4
[   704.585]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   704.585] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   704.596] (==) Log file: "/home/xxxx/.local/share/xorg/Xorg.0.log", Time: Sat Jun 27 09:19:19 2020
[   704.599] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   704.599] (==) No Layout section.  Using the first Screen section.
[   704.599] (==) No screen section available. Using defaults.
[   704.599] (**) |-->Screen "Default Screen Section" (0)
[   704.599] (**) |   |-->Monitor "<default monitor>"
[   704.599] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   704.599] (==) Automatically adding devices
[   704.599] (==) Automatically enabling devices
[   704.599] (==) Automatically adding GPU devices
[   704.599] (==) Automatically binding GPU devices
[   704.599] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   704.599] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   704.599]     Entry deleted from font path.
[   704.599] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   704.599]     Entry deleted from font path.
[   704.599] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   704.599]     Entry deleted from font path.
[   704.600] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   704.600]     Entry deleted from font path.
[   704.600] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   704.600]     Entry deleted from font path.
[   704.600] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   704.600] (==) ModulePath set to "/usr/lib/xorg/modules"
[   704.600] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   704.600] (II) Loader magic: 0x556942bc4020
[   704.600] (II) Module ABI versions:
[   704.600]     X.Org ANSI C Emulation: 0.4
[   704.600]     X.Org Video Driver: 24.1
[   704.600]     X.Org XInput driver : 24.1
[   704.600]     X.Org Server Extension : 10.0
[   704.600] (++) using VT number 2


[   704.602] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_33
[   704.602] (II) xfree86: Adding drm device (/dev/dri/card0)
[   704.603] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 11 paused 0
[   704.611] (--) PCI:*(3@0:0:0) 10de:1244:3842:1556 rev 161, Mem @ 0xf6000000/33554432, 0xe8000000/134217728, 0xf0000000/67108864, I/O @ 0x0000e000/128, BIOS @ 0x????????/131072
[   704.611] (--) PCI: (9@0:0:0) 1a03:2000:15d9:0832 rev 48, Mem @ 0xf9000000/16777216, 0xfa000000/131072, I/O @ 0x0000b000/128
[   704.611] (II) LoadModule: "glx"
[   704.611] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   704.612] (II) Module glx: vendor="X.Org Foundation"
[   704.612]     compiled for 1.20.8, module version = 1.0.0
[   704.612]     ABI class: X.Org Server Extension, version 10.0
[   704.732] (==) Matched ast as autoconfigured driver 0
[   704.732] (==) Matched nouveau as autoconfigured driver 1
[   704.732] (==) Matched modesetting as autoconfigured driver 2
[   704.732] (==) Matched fbdev as autoconfigured driver 3
[   704.732] (==) Matched vesa as autoconfigured driver 4
[   704.732] (==) Assigned the driver to the xf86ConfigLayout
[   704.732] (II) LoadModule: "ast"
[   704.732] (WW) Warning, couldn't open module ast
[   704.732] (EE) Failed to load module "ast" (module does not exist, 0)
[   704.732] (II) LoadModule: "nouveau"
[   704.732] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   704.732] (II) Module nouveau: vendor="X.Org Foundation"
[   704.732]     compiled for 1.20.3, module version = 1.0.16
[   704.732]     Module class: X.Org Video Driver
[   704.732]     ABI class: X.Org Video Driver, version 24.0
[   704.732] (II) LoadModule: "modesetting"
[   704.732] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   704.732] (II) Module modesetting: vendor="X.Org Foundation"
[   704.732]     compiled for 1.20.8, module version = 1.20.8
[   704.732]     Module class: X.Org Video Driver
[   704.732]     ABI class: X.Org Video Driver, version 24.1
[   704.732] (II) LoadModule: "fbdev"
[   704.732] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   704.732] (II) Module fbdev: vendor="X.Org Foundation"
[   704.732]     compiled for 1.20.1, module version = 0.5.0
[   704.732]     Module class: X.Org Video Driver
[   704.732]     ABI class: X.Org Video Driver, version 24.0
[   704.732] (II) LoadModule: "vesa"
[   704.732] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   704.732] (II) Module vesa: vendor="X.Org Foundation"
[   704.732]     compiled for 1.20.4, module version = 2.4.0
[   704.732]     Module class: X.Org Video Driver
[   704.732]     ABI class: X.Org Video Driver, version 24.0
[   704.851] (==) Matched ast as autoconfigured driver 0
[   704.851] (==) Matched nouveau as autoconfigured driver 1
[   704.851] (==) Matched modesetting as autoconfigured driver 2
[   704.851] (==) Matched fbdev as autoconfigured driver 3
[   704.851] (==) Matched vesa as autoconfigured driver 4
[   704.851] (==) Assigned the driver to the xf86ConfigLayout
[   704.851] (II) LoadModule: "ast"
[   704.851] (WW) Warning, couldn't open module ast
[   704.851] (EE) Failed to load module "ast" (module does not exist, 0)
[   704.851] (II) LoadModule: "nouveau"
[   704.851] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   704.851] (II) Module nouveau: vendor="X.Org Foundation"
[   704.851]     compiled for 1.20.3, module version = 1.0.16
[   704.851]     Module class: X.Org Video Driver
[   704.851]     ABI class: X.Org Video Driver, version 24.0
[   704.851] (II) UnloadModule: "nouveau"
[   704.851] (II) Unloading nouveau
[   704.851] (II) Failed to load module "nouveau" (already loaded, 0)
[   704.851] (II) LoadModule: "modesetting"
[   704.851] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   704.851] (II) Module modesetting: vendor="X.Org Foundation"
[   704.851]     compiled for 1.20.8, module version = 1.20.8
[   704.851]     Module class: X.Org Video Driver
[   704.851]     ABI class: X.Org Video Driver, version 24.1
[   704.851] (II) UnloadModule: "modesetting"
[   704.851] (II) Unloading modesetting
[   704.851] (II) Failed to load module "modesetting" (already loaded, 0)
[   704.851] (II) LoadModule: "fbdev"
[   704.851] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   704.851] (II) Module fbdev: vendor="X.Org Foundation"
[   704.851]     compiled for 1.20.1, module version = 0.5.0
[   704.851]     Module class: X.Org Video Driver
[   704.851]     ABI class: X.Org Video Driver, version 24.0
[   704.851] (II) UnloadModule: "fbdev"
[   704.851] (II) Unloading fbdev
[   704.851] (II) Failed to load module "fbdev" (already loaded, 0)
[   704.851] (II) LoadModule: "vesa"
[   704.851] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   704.851] (II) Module vesa: vendor="X.Org Foundation"
[   704.851]     compiled for 1.20.4, module version = 2.4.0
[   704.851]     Module class: X.Org Video Driver
[   704.851]     ABI class: X.Org Video Driver, version 24.0
[   704.851] (II) UnloadModule: "vesa"
[   704.851] (II) Unloading vesa
[   704.851] (II) Failed to load module "vesa" (already loaded, 0)
[   704.851] (II) NOUVEAU driver Date:   Mon Jan 28 23:25:58 2019 -0500
[   704.851] (II) NOUVEAU driver for NVIDIA chipset families :
[   704.851]     RIVA TNT            (NV04)
[   704.851]     RIVA TNT2           (NV05)
[   704.851]     GeForce 256         (NV10)
[   704.851]     GeForce 2           (NV11, NV15)
[   704.851]     GeForce 4MX         (NV17, NV18)
[   704.851]     GeForce 3           (NV20)
[   704.851]     GeForce 4Ti         (NV25, NV28)
[   704.851]     GeForce FX          (NV3x)
[   704.851]     GeForce 6           (NV4x)
[   704.851]     GeForce 7           (G7x)
[   704.851]     GeForce 8           (G8x)
[   704.851]     GeForce 9           (G9x)
[   704.851]     GeForce GTX 2xx/3xx (GT2xx)
[   704.851]     GeForce GTX 4xx/5xx (GFxxx)
[   704.851]     GeForce GTX 6xx/7xx (GKxxx)
[   704.851]     GeForce GTX 9xx     (GMxxx)
[   704.851]     GeForce GTX 10xx    (GPxxx)
[   704.851] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   704.851] (II) FBDEV: driver for framebuffer: fbdev
[   704.851] (II) VESA: driver for VESA chipsets: vesa
[   704.851] xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
[   704.964] (EE) [drm] Failed to open DRM device for pci:0000:03:00.0: -19
[   704.964] (WW) Falling back to old probe method for modesetting
[   704.964] (II) modeset(1): using default device
[   704.964] (II) Loading sub module "fbdevhw"
[   704.964] (II) LoadModule: "fbdevhw"
[   704.964] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   704.964] (II) Module fbdevhw: vendor="X.Org Foundation"
[   704.964]     compiled for 1.20.8, module version = 0.0.2
[   704.964]     ABI class: X.Org Video Driver, version 24.1
[   704.964] (**) FBDEV(2): claimed PCI slot 3@0:0:0
[   704.964] (II) FBDEV(2): using default device
[   704.964] (II) modeset(G0): using drv /dev/dri/card0
[   704.964] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[   704.964] (EE) Screen 0 deleted because of no matching config section.
[   704.964] (II) UnloadModule: "modesetting"
[   704.964] (EE) 
Fatal server error:
[   704.964] (EE) Cannot run in framebuffer mode. Please specify busIDs        for all framebuffer devices
[   704.964] (EE) 
[   704.964] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   704.964] (EE) Please also check the log file at "/home/xxxxx/.local/share/xorg/Xorg.0.log" for additional information.
[   704.964] (EE) 
[   704.970] (EE) Server terminated with error (1). Closing log file.

```

Can anyone suggest where I should look next?

---

### Post by CelticWarrior on 2020-06-27
Welcome.

Update UEFI and disable Secure Boot.

---

### Post by nilesj on 2020-06-27
Thank you for the welcome and the suggestion.  No change in the logs, but I'm not 100% sure I implemented your advice correctly.  I followed the steps on [here]("https://wiki.ubuntu.com/UEFI/SecureBoot/DKMS") and used mkoutil to disable secure boot, and that seems to have worked.  I checked my BIOS and secure boot is disabled.  My system now mentions booting insecurely (I love that term) during startup.  Still no change in behavior when running startx.  Do I also need to do something with my NVIDIA drivers? Or have I maybe missed something.

---

### Post by CelticWarrior on 2020-06-27
How are you installing the Nvidia drivers? You should ONLY install them from the official repositories, not from the Nvidia binaries. If the latter, among other problems, you have to reinstall each and every time there's a kernel update.

---

### Post by nilesj on 2020-06-27
I'm using only the official repositories and installing them with

```
ubuntu-drivers autoinstall
```

---

### Post by nilesj on 2020-06-28
I tried adding nomodeset in grub and was able to get X to start in low graphics mode, so I'm confident I'm on the right track, but not making much progress.  I think I may rebuild and go back to regular Ubuntu.  I haven't been thrilled with Ubuntu Studio so far and this might be the final straw.  Thanks again!

---

