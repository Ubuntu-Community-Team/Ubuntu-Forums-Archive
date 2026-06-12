---
title: "Installation does not start"
date: 2012-06-28
forum: Installation &amp; Upgrades
---

### Post by Pitel on 2012-06-28
I tried upgrading my gf's PC from some ancient version of Ubuntu to 12.04 LTS by clean installation.

But after booting the installation, I am stuck in console. Xorg crashes. Here is the log file:
```
[   359.256] 
X.Org X Server 1.11.3
Release Date: 2011-12-16
[   359.256] X Protocol Version 11, Revision 0
[   359.256] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[   359.256] Current Operating System: Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64
[   359.256] Kernel command line: file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash -- debian-installer/language=cs keyboard-configuration/layoutcode?=cz
[   359.256] Build Date: 05 April 2012  04:32:37AM
[   359.256] xorg-server 2:1.11.4-0ubuntu10 (For technical support please see http://www.ubuntu.com/support) 
[   359.256] Current version of pixman: 0.24.4
[   359.256] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   359.256] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   359.257] (==) Log file: "/var/log/Xorg.1.log", Time: Thu Jun 28 14:23:49 2012
[   359.257] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   359.257] (==) No Layout section.  Using the first Screen section.
[   359.257] (==) No screen section available. Using defaults.
[   359.257] (**) |-->Screen "Default Screen Section" (0)
[   359.257] (**) |   |-->Monitor "<default monitor>"
[   359.258] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   359.258] (==) Automatically adding devices
[   359.258] (==) Automatically enabling devices
[   359.258] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   359.258] 	Entry deleted from font path.
[   359.258] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   359.258] 	Entry deleted from font path.
[   359.258] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   359.258] 	Entry deleted from font path.
[   359.258] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   359.258] 	Entry deleted from font path.
[   359.258] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   359.258] 	Entry deleted from font path.
[   359.258] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   359.258] 	Entry deleted from font path.
[   359.258] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[   359.258] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   359.258] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   359.258] (II) Loader magic: 0x7f4a6ca55b00
[   359.258] (II) Module ABI versions:
[   359.258] 	X.Org ANSI C Emulation: 0.4
[   359.258] 	X.Org Video Driver: 11.0
[   359.258] 	X.Org XInput driver : 16.0
[   359.258] 	X.Org Server Extension : 6.0
[   359.259] (--) PCI:*(0:2:0:0) 10de:0393:1458:341b rev 161, Mem @ 0xdc000000/16777216, 0xc0000000/268435456, 0xdd000000/16777216, I/O @ 0x0000ac00/128, BIOS @ 0x????????/131072
[   359.268] (II) Open ACPI successful (/var/run/acpid.socket)
[   359.268] (II) LoadModule: "extmod"
[   359.268] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   359.269] (II) Module extmod: vendor="X.Org Foundation"
[   359.269] 	compiled for 1.11.3, module version = 1.0.0
[   359.269] 	Module class: X.Org Server Extension
[   359.269] 	ABI class: X.Org Server Extension, version 6.0
[   359.269] (II) Loading extension MIT-SCREEN-SAVER
[   359.269] (II) Loading extension XFree86-VidModeExtension
[   359.269] (II) Loading extension XFree86-DGA
[   359.269] (II) Loading extension DPMS
[   359.269] (II) Loading extension XVideo
[   359.269] (II) Loading extension XVideo-MotionCompensation
[   359.269] (II) Loading extension X-Resource
[   359.269] (II) LoadModule: "dbe"
[   359.269] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   359.269] (II) Module dbe: vendor="X.Org Foundation"
[   359.269] 	compiled for 1.11.3, module version = 1.0.0
[   359.269] 	Module class: X.Org Server Extension
[   359.269] 	ABI class: X.Org Server Extension, version 6.0
[   359.269] (II) Loading extension DOUBLE-BUFFER
[   359.269] (II) LoadModule: "glx"
[   359.270] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   359.270] (II) Module glx: vendor="X.Org Foundation"
[   359.270] 	compiled for 1.11.3, module version = 1.0.0
[   359.270] 	ABI class: X.Org Server Extension, version 6.0
[   359.270] (==) AIGLX enabled
[   359.270] (II) Loading extension GLX
[   359.270] (II) LoadModule: "record"
[   359.270] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   359.270] (II) Module record: vendor="X.Org Foundation"
[   359.270] 	compiled for 1.11.3, module version = 1.13.0
[   359.270] 	Module class: X.Org Server Extension
[   359.270] 	ABI class: X.Org Server Extension, version 6.0
[   359.270] (II) Loading extension RECORD
[   359.270] (II) LoadModule: "dri"
[   359.271] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   359.271] (II) Module dri: vendor="X.Org Foundation"
[   359.271] 	compiled for 1.11.3, module version = 1.0.0
[   359.271] 	ABI class: X.Org Server Extension, version 6.0
[   359.271] (II) Loading extension XFree86-DRI
[   359.271] (II) LoadModule: "dri2"
[   359.271] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   359.276] (II) Module dri2: vendor="X.Org Foundation"
[   359.276] 	compiled for 1.11.3, module version = 1.2.0
[   359.276] 	ABI class: X.Org Server Extension, version 6.0
[   359.276] (II) Loading extension DRI2
[   359.276] (==) Matched nvidia as autoconfigured driver 0
[   359.276] (==) Matched nouveau as autoconfigured driver 1
[   359.276] (==) Matched nv as autoconfigured driver 2
[   359.276] (==) Matched vesa as autoconfigured driver 3
[   359.276] (==) Matched fbdev as autoconfigured driver 4
[   359.276] (==) Assigned the driver to the xf86ConfigLayout
[   359.276] (II) LoadModule: "nvidia"
[   359.277] (WW) Warning, couldn't open module nvidia
[   359.277] (II) UnloadModule: "nvidia"
[   359.277] (II) Unloading nvidia
[   359.277] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   359.277] (II) LoadModule: "nouveau"
[   359.277] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   359.277] (II) Module nouveau: vendor="X.Org Foundation"
[   359.277] 	compiled for 1.11.3, module version = 0.0.16
[   359.277] 	Module class: X.Org Video Driver
[   359.277] 	ABI class: X.Org Video Driver, version 11.0
[   359.277] (II) LoadModule: "nv"
[   359.278] (WW) Warning, couldn't open module nv
[   359.278] (II) UnloadModule: "nv"
[   359.278] (II) Unloading nv
[   359.278] (EE) Failed to load module "nv" (module does not exist, 0)
[   359.278] (II) LoadModule: "vesa"
[   359.278] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   359.278] (II) Module vesa: vendor="X.Org Foundation"
[   359.278] 	compiled for 1.11.3, module version = 2.3.0
[   359.278] 	Module class: X.Org Video Driver
[   359.278] 	ABI class: X.Org Video Driver, version 11.0
[   359.278] (II) LoadModule: "fbdev"
[   359.279] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   359.279] (II) Module fbdev: vendor="X.Org Foundation"
[   359.279] 	compiled for 1.11.3, module version = 0.4.2
[   359.279] 	ABI class: X.Org Video Driver, version 11.0
[   359.279] (==) Matched nvidia as autoconfigured driver 0
[   359.279] (==) Matched nouveau as autoconfigured driver 1
[   359.279] (==) Matched nv as autoconfigured driver 2
[   359.279] (==) Matched vesa as autoconfigured driver 3
[   359.279] (==) Matched fbdev as autoconfigured driver 4
[   359.279] (==) Assigned the driver to the xf86ConfigLayout
[   359.279] (II) LoadModule: "nvidia"
[   359.280] (WW) Warning, couldn't open module nvidia
[   359.280] (II) UnloadModule: "nvidia"
[   359.280] (II) Unloading nvidia
[   359.280] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   359.280] (II) LoadModule: "nouveau"
[   359.280] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   359.280] (II) Module nouveau: vendor="X.Org Foundation"
[   359.280] 	compiled for 1.11.3, module version = 0.0.16
[   359.280] 	Module class: X.Org Video Driver
[   359.280] 	ABI class: X.Org Video Driver, version 11.0
[   359.280] (II) UnloadModule: "nouveau"
[   359.280] (II) Unloading nouveau
[   359.280] (II) Failed to load module "nouveau" (already loaded, 0)
[   359.280] (II) LoadModule: "nv"
[   359.281] (WW) Warning, couldn't open module nv
[   359.281] (II) UnloadModule: "nv"
[   359.281] (II) Unloading nv
[   359.281] (EE) Failed to load module "nv" (module does not exist, 0)
[   359.281] (II) LoadModule: "vesa"
[   359.281] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   359.281] (II) Module vesa: vendor="X.Org Foundation"
[   359.281] 	compiled for 1.11.3, module version = 2.3.0
[   359.281] 	Module class: X.Org Video Driver
[   359.281] 	ABI class: X.Org Video Driver, version 11.0
[   359.281] (II) UnloadModule: "vesa"
[   359.281] (II) Unloading vesa
[   359.281] (II) Failed to load module "vesa" (already loaded, 0)
[   359.281] (II) LoadModule: "fbdev"
[   359.281] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   359.281] (II) Module fbdev: vendor="X.Org Foundation"
[   359.281] 	compiled for 1.11.3, module version = 0.4.2
[   359.281] 	ABI class: X.Org Video Driver, version 11.0
[   359.281] (II) UnloadModule: "fbdev"
[   359.281] (II) Unloading fbdev
[   359.281] (II) Failed to load module "fbdev" (already loaded, 0)
[   359.281] (II) NOUVEAU driver Date:   Wed Nov 30 18:56:54 2011 +0100
[   359.281] (II) NOUVEAU driver for NVIDIA chipset families :
[   359.281] 	RIVA TNT        (NV04)
[   359.281] 	RIVA TNT2       (NV05)
[   359.281] 	GeForce 256     (NV10)
[   359.281] 	GeForce 2       (NV11, NV15)
[   359.281] 	GeForce 4MX     (NV17, NV18)
[   359.281] 	GeForce 3       (NV20)
[   359.281] 	GeForce 4Ti     (NV25, NV28)
[   359.281] 	GeForce FX      (NV3x)
[   359.281] 	GeForce 6       (NV4x)
[   359.281] 	GeForce 7       (G7x)
[   359.281] 	GeForce 8       (G8x)
[   359.281] 	GeForce GTX 200 (NVA0)
[   359.281] 	GeForce GTX 400 (NVC0)
[   359.281] (II) VESA: driver for VESA chipsets: vesa
[   359.281] (II) FBDEV: driver for framebuffer: fbdev
[   359.281] (++) using VT number 7

[   359.282] drmOpenDevice: node name is /dev/dri/card0
[   359.282] drmOpenDevice: open result is 8, (OK)
[   359.282] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[   359.282] drmOpenDevice: node name is /dev/dri/card0
[   359.282] drmOpenDevice: open result is 8, (OK)
[   359.282] drmOpenByBusid: drmOpenMinor returns 8
[   359.282] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[   359.282] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[   359.282] (II) [drm] nouveau interface version: 0.0.16
[   359.282] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   359.282] (WW) Falling back to old probe method for vesa
[   359.282] (WW) Falling back to old probe method for fbdev
[   359.282] (II) Loading sub module "fbdevhw"
[   359.282] (II) LoadModule: "fbdevhw"
[   359.282] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   359.283] (II) Module fbdevhw: vendor="X.Org Foundation"
[   359.283] 	compiled for 1.11.3, module version = 0.0.2
[   359.283] 	ABI class: X.Org Video Driver, version 11.0
[   359.283] (II) Loading sub module "dri"
[   359.283] (II) LoadModule: "dri"
[   359.283] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   359.283] (II) Module dri: vendor="X.Org Foundation"
[   359.283] 	compiled for 1.11.3, module version = 1.0.0
[   359.283] 	ABI class: X.Org Server Extension, version 6.0
[   359.283] (II) NOUVEAU(0): Loaded DRI module
[   359.283] drmOpenDevice: node name is /dev/dri/card0
[   359.283] drmOpenDevice: open result is 9, (OK)
[   359.283] drmOpenDevice: node name is /dev/dri/card0
[   359.283] drmOpenDevice: open result is 9, (OK)
[   359.283] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[   359.283] drmOpenDevice: node name is /dev/dri/card0
[   359.283] drmOpenDevice: open result is 9, (OK)
[   359.283] drmOpenByBusid: drmOpenMinor returns 9
[   359.283] drmOpenByBusid: Interface 1.4 failed, trying 1.1
[   359.283] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[   359.283] (II) [drm] DRM interface version 1.0
[   359.283] (EE) [drm] Could not set DRM device bus ID.
[   359.283] (EE) NOUVEAU(0): [drm] error opening the drm
[   359.283] (EE) NOUVEAU(0): 660: 
[   359.283] (II) UnloadModule: "nouveau"
[   359.283] (II) Unloading nouveau
[   359.283] (II) UnloadModule: "dri"
[   359.283] (II) Unloading dri
[   359.283] (EE) Screen(s) found, but none have a usable configuration.
[   359.283] 
Fatal server error:
[   359.283] no screens found
[   359.283] 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   359.283] Please also check the log file at "/var/log/Xorg.1.log" for additional information.
[   359.283] 
[   359.289]  ddxSigGiveUp: Closing log
[   359.289] Server terminated with error (1). Closing log file.
```

Obviously it's some issue with noveau and her older nVidia card. What now? How can I start the installation and install proprietary drivers later?

---

