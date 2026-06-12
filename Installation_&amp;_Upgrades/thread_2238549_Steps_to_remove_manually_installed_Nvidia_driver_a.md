---
title: "Steps to remove manually installed Nvidia driver and install Nouveau"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2014-08-08
I am currently on 12.04.5 x64.  I have been using Nvidia driver 334.21 that I manually installed.  Now I would like to remove the Nvidia driver and install Nouveau.  I know the command to remove the Nvidia driver, but I am not sure when or how to install the Nouveau driver.  Do I install the Nouveau driver before I remove the Nvidia driver (seems to me I should).  Do I have to reconfigure X in any way to get the system to load the proper driver?

I know there are Nvidia proprietary drivers, but none show when I look for them in Applications>System Tools>System Settings>Additional Drivers.  I have "Proprietary drivers for devices" checked in System Sources.  Should I install the latest one of these (providing I can find them) rather than Nouveau?

Any help would be appreciated.

---

### Post by ajgreeny on 2014-08-08
I have never needed a nvidia driver, but I think if you simply remove the proprietary one currently in use, and also any **/etc/X11/xorg.conf** file that it may have produced (not at all sure if it does make an xorg.conf file), then reboot, or even just restart the xsession, it should be the nouveau driver that takes over.

You can easily check if the nouveau driver is still installed with the software-centre or better, in my opinion, synaptic.

---

### Post by grahammechanical on 2014-08-08
On machines with Nvidia graphic adapters Nouveau is the open source video driver. If we remove the Nvidia proprietary video driver and then reboot we will be running on Nouveau. Check About this computer. If the Details page says Gallium, then that is Nouveau.

When we go to Additional Drivers we must be connected to the internet and we must allow time for it to check. It should show 4 Nvidia drivers not including the one manually installed and also X.Org X Server - Nouveau display driver from xserver-xorg-video-nouveau (open source).

Regards.

---

### Post by cscj01 on 2014-08-08
> **grahammechanical said:**
> On machines with Nvidia graphic adapters Nouveau is the open source video driver. If we remove the Nvidia proprietary video driver and then reboot we will be running on Nouveau. Check About this computer. If the Details page says Gallium, then that is Nouveau.

When we go to Additional Drivers we must be connected to the internet and we must allow time for it to check. It should show 4 Nvidia drivers not including the one manually installed and also X.Org X Server - Nouveau display driver from xserver-xorg-video-nouveau (open source).

Regards.
The Details page does say Gallium.  Synaptic shows xserver-xorg-video-nouveau-lts-trusty (1:1.0.10-1ubuntu2~precise1) is installed.  So I presume I am now using the Nouveau driver, and I can remove the manually installed Nvidia driver..

I have checked the Additional Drivers and the search completes and says that there are none.  As I mentioned in my first post, I have "Proprietary drivers for devices" checked in System Sources.  Is there something I can do to gain access to the ones you suggest should show?

---

### Post by cscj01 on 2014-08-09
I removed the Nvidia driver and now I get a message that I am running in low res graphics mode.  If I check Applications>System Tools>System Settings>Details, it now shows> Graphics    VESA: GM107 Board - 20100050That has changed from before when it showed Gallium.  My xorg.conf file shows > 
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSectionI am at a loss becuase Synaptic shows I have a Nouveau driver installed.  Do I need to remove the xorg.conf file and reboot to get the system to load the correct driver?

---

### Post by ubfan1 on 2014-08-09
Try renaming the xorg.conf file and reboot.  (or putting in the nouveau driver instead of nvidia, but getting rid of the file should work).

---

### Post by cscj01 on 2014-08-09
> **ubfan1 said:**
> Try renaming the xorg.conf file and reboot.  (or putting in the nouveau driver instead of nvidia, but getting rid of the file should work).
Well I renamed the xorg.conf and got exactly the same symptoms.  However, I found problems in the xorg log file.  Here it is.```
[   172.285] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   172.285] X Protocol Version 11, Revision 0
[   172.285] Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
[   172.285] Current Operating System: Linux Car-Photo-Ubuntu 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64
[   172.285] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e ro vga=769 quiet splash nomodeset vt.handoff=7
[   172.285] Build Date: 07 August 2014  11:49:36AM
[   172.285] xorg-server 2:1.15.1-0ubuntu2~precise2 (For technical support please see http://www.ubuntu.com/support) 
[   172.285] Current version of pixman: 0.30.2
[   172.285] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   172.285] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   172.285] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug  9 13:53:34 2014
[   172.285] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   172.285] (==) No Layout section.  Using the first Screen section.
[   172.285] (==) No screen section available. Using defaults.
[   172.285] (**) |-->Screen "Default Screen Section" (0)
[   172.285] (**) |   |-->Monitor "<default monitor>"
[   172.286] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   172.286] (==) Automatically adding devices
[   172.286] (==) Automatically enabling devices
[   172.286] (==) Automatically adding GPU devices
[   172.286] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   172.286] 	Entry deleted from font path.
[   172.286] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[   172.286] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   172.286] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   172.286] (II) Loader magic: 0x7ff2b8f57c20
[   172.286] (II) Module ABI versions:
[   172.286] 	X.Org ANSI C Emulation: 0.4
[   172.286] 	X.Org Video Driver: 15.0
[   172.286] 	X.Org XInput driver : 20.0
[   172.286] 	X.Org Server Extension : 8.0
[   172.287] (--) PCI:*(0:1:0:0) 10de:1380:3842:3757 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   172.287] Initializing built-in extension Generic Event Extension
[   172.287] Initializing built-in extension SHAPE
[   172.287] Initializing built-in extension MIT-SHM
[   172.287] Initializing built-in extension XInputExtension
[   172.287] Initializing built-in extension XTEST
[   172.287] Initializing built-in extension BIG-REQUESTS
[   172.287] Initializing built-in extension SYNC
[   172.288] Initializing built-in extension XKEYBOARD
[   172.288] Initializing built-in extension XC-MISC
[   172.288] Initializing built-in extension SECURITY
[   172.288] Initializing built-in extension XINERAMA
[   172.288] Initializing built-in extension XFIXES
[   172.288] Initializing built-in extension RENDER
[   172.288] Initializing built-in extension RANDR
[   172.288] Initializing built-in extension COMPOSITE
[   172.288] Initializing built-in extension DAMAGE
[   172.288] Initializing built-in extension MIT-SCREEN-SAVER
[   172.288] Initializing built-in extension DOUBLE-BUFFER
[   172.288] Initializing built-in extension RECORD
[   172.288] Initializing built-in extension DPMS
[   172.288] Initializing built-in extension X-Resource
[   172.288] Initializing built-in extension XVideo
[   172.288] Initializing built-in extension XVideo-MotionCompensation
[   172.288] Initializing built-in extension XFree86-VidModeExtension
[   172.288] Initializing built-in extension XFree86-DGA
[   172.288] Initializing built-in extension XFree86-DRI
[   172.288] Initializing built-in extension DRI2
[   172.288] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[   172.288] (II) "glx" will be loaded by default.
[   172.288] (II) LoadModule: "glx"
[   172.288] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[   172.291] (II) Module glx: vendor="NVIDIA Corporation"
[   172.291] 	compiled for 4.0.2, module version = 1.0.0
[   172.291] 	Module class: X.Org Server Extension
[   172.291] (II) NVIDIA GLX Module  173.14.39  Wed Nov 27 14:44:39 PST 2013
[   172.291] Loading extension GLX
[   172.291] (==) Matched nvidia as autoconfigured driver 0
[   172.291] (==) Matched nouveau as autoconfigured driver 1
[   172.291] (==) Matched modesetting as autoconfigured driver 2
[   172.291] (==) Matched fbdev as autoconfigured driver 3
[   172.291] (==) Matched vesa as autoconfigured driver 4
[   172.291] (==) Assigned the driver to the xf86ConfigLayout
[   172.291] (II) LoadModule: "nvidia"
[   172.291] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[   172.291] (II) Module nvidia: vendor="NVIDIA Corporation"
[   172.291] 	compiled for 4.0.2, module version = 1.0.0
[   172.291] 	Module class: X.Org Video Driver
[   172.291] (II) LoadModule: "nouveau"
[   172.291] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   172.292] (II) Module nouveau: vendor="X.Org Foundation"
[   172.292] 	compiled for 1.15.1, module version = 1.0.10
[   172.292] 	Module class: X.Org Video Driver
[   172.292] 	ABI class: X.Org Video Driver, version 15.0
[   172.292] (II) LoadModule: "modesetting"
[   172.292] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   172.292] (II) Module modesetting: vendor="X.Org Foundation"
[   172.292] 	compiled for 1.15.1, module version = 0.8.1
[   172.292] 	Module class: X.Org Video Driver
[   172.292] 	ABI class: X.Org Video Driver, version 15.0
[   172.292] (II) LoadModule: "fbdev"
[   172.292] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   172.292] (II) Module fbdev: vendor="X.Org Foundation"
[   172.292] 	compiled for 1.15.1, module version = 0.4.4
[   172.292] 	Module class: X.Org Video Driver
[   172.292] 	ABI class: X.Org Video Driver, version 15.0
[   172.292] (II) LoadModule: "vesa"
[   172.292] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   172.292] (II) Module vesa: vendor="X.Org Foundation"
[   172.292] 	compiled for 1.15.1, module version = 2.3.3
[   172.292] 	Module class: X.Org Video Driver
[   172.292] 	ABI class: X.Org Video Driver, version 15.0
[   172.292] (II) NVIDIA dlloader X Driver  173.14.39  Wed Nov 27 14:34:40 PST 2013
[   172.292] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[   172.292] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[   172.292] (II) NOUVEAU driver for NVIDIA chipset families :
[   172.292] 	RIVA TNT        (NV04)
[   172.292] 	RIVA TNT2       (NV05)
[   172.292] 	GeForce 256     (NV10)
[   172.292] 	GeForce 2       (NV11, NV15)
[   172.292] 	GeForce 4MX     (NV17, NV18)
[   172.292] 	GeForce 3       (NV20)
[   172.292] 	GeForce 4Ti     (NV25, NV28)
[   172.292] 	GeForce FX      (NV3x)
[   172.292] 	GeForce 6       (NV4x)
[   172.292] 	GeForce 7       (G7x)
[   172.292] 	GeForce 8       (G8x)
[   172.292] 	GeForce GTX 200 (NVA0)
[   172.292] 	GeForce GTX 400 (NVC0)
[   172.292] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   172.292] (II) FBDEV: driver for framebuffer: fbdev
[   172.292] (II) VESA: driver for VESA chipsets: vesa
[   172.292] (++) using VT number 7

[   172.292] (II) Loading sub module "fb"
[   172.292] (II) LoadModule: "fb"
[   172.293] (II) Loading /usr/lib/xorg/modules/libfb.so
[   172.293] (II) Module fb: vendor="X.Org Foundation"
[   172.293] 	compiled for 1.15.1, module version = 1.0.0
[   172.293] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   172.293] (II) Loading sub module "wfb"
[   172.293] (II) LoadModule: "wfb"
[   172.293] (II) Loading /usr/lib/xorg/modules/libwfb.so
[   172.293] (II) Module wfb: vendor="X.Org Foundation"
[   172.293] 	compiled for 1.15.1, module version = 1.0.0
[   172.293] 	ABI class: X.Org ANSI C Emulation, version 0.4
[   172.293] (II) Loading sub module "ramdac"
[   172.293] (II) LoadModule: "ramdac"
[   172.293] (II) Module "ramdac" already built-in
[   172.293] (WW) Falling back to old probe method for modesetting
[   172.293] (EE) open /dev/dri/card0: No such file or directory
[   172.293] (WW) Falling back to old probe method for fbdev
[   172.293] (II) Loading sub module "fbdevhw"
[   172.293] (II) LoadModule: "fbdevhw"
[   172.293] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   172.293] (II) Module fbdevhw: vendor="X.Org Foundation"
[   172.293] 	compiled for 1.15.1, module version = 0.0.2
[   172.293] 	ABI class: X.Org Video Driver, version 15.0
[   172.293] (WW) Falling back to old probe method for vesa
[   172.293] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   172.293] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[   172.293] (==) NVIDIA(0): RGB weight 888
[   172.293] (==) NVIDIA(0): Default visual is TrueColor
[   172.293] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[   172.293] (**) NVIDIA(0): Enabling RENDER acceleration
[   172.293] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[   172.293] (II) NVIDIA(0):     enabled.
[   172.305] (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
[   172.305] (EE) NVIDIA(0):  *** Aborting ***
[   172.305] (II) UnloadModule: "nvidia"
[   172.305] (II) UnloadSubModule: "wfb"
[   172.305] (II) UnloadSubModule: "fb"
[   172.305] (EE) Screen(s) found, but none have a usable configuration.
[   172.305] (EE) 
Fatal server error:
[   172.305] (EE) no screens found(EE) 
[   172.305] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[   172.305] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   172.305] (EE) 
[   172.312] (EE) Server terminated with error (1). Closing log file.
```I'm not up on this, so perhaps someone might look at it and tell me what I can do to correct the problem.  In the meantime, I'm going to change "nvidia" in the xorg.conf file to "nouveau" and see what happens.

---

### Post by cscj01 on 2014-08-09
I renamed the xorg.conf file I had renamed and changed "nvidia" to "nouveau".  Here is the xorg log.```
[    21.914] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    21.914] X Protocol Version 11, Revision 0
[    21.914] Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
[    21.914] Current Operating System: Linux Car-Photo-Ubuntu 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64
[    21.914] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e ro vga=769 quiet splash nomodeset vt.handoff=7
[    21.914] Build Date: 07 August 2014  11:49:36AM
[    21.914] xorg-server 2:1.15.1-0ubuntu2~precise2 (For technical support please see http://www.ubuntu.com/support) 
[    21.914] Current version of pixman: 0.30.2
[    21.914] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    21.914] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.914] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug  9 14:17:15 2014
[    21.971] (==) Using config file: "/etc/X11/xorg.conf"
[    21.971] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.382] (==) No Layout section.  Using the first Screen section.
[    22.382] (**) |-->Screen "Default Screen" (0)
[    22.382] (**) |   |-->Monitor "<default monitor>"
[    22.434] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    22.434] (**) |   |-->Device "Default Device"
[    22.434] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    22.434] (==) Automatically adding devices
[    22.434] (==) Automatically enabling devices
[    22.434] (==) Automatically adding GPU devices
[    22.550] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.550] 	Entry deleted from font path.
[    22.614] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    22.614] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.614] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.614] (II) Loader magic: 0x7fe925479c20
[    22.614] (II) Module ABI versions:
[    22.614] 	X.Org ANSI C Emulation: 0.4
[    22.614] 	X.Org Video Driver: 15.0
[    22.614] 	X.Org XInput driver : 20.0
[    22.614] 	X.Org Server Extension : 8.0
[    22.615] (--) PCI:*(0:1:0:0) 10de:1380:3842:3757 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    22.665] Initializing built-in extension Generic Event Extension
[    22.665] Initializing built-in extension SHAPE
[    22.665] Initializing built-in extension MIT-SHM
[    22.665] Initializing built-in extension XInputExtension
[    22.665] Initializing built-in extension XTEST
[    22.665] Initializing built-in extension BIG-REQUESTS
[    22.665] Initializing built-in extension SYNC
[    22.665] Initializing built-in extension XKEYBOARD
[    22.665] Initializing built-in extension XC-MISC
[    22.665] Initializing built-in extension SECURITY
[    22.665] Initializing built-in extension XINERAMA
[    22.665] Initializing built-in extension XFIXES
[    22.665] Initializing built-in extension RENDER
[    22.665] Initializing built-in extension RANDR
[    22.665] Initializing built-in extension COMPOSITE
[    22.665] Initializing built-in extension DAMAGE
[    22.665] Initializing built-in extension MIT-SCREEN-SAVER
[    22.665] Initializing built-in extension DOUBLE-BUFFER
[    22.665] Initializing built-in extension RECORD
[    22.665] Initializing built-in extension DPMS
[    22.665] Initializing built-in extension X-Resource
[    22.665] Initializing built-in extension XVideo
[    22.665] Initializing built-in extension XVideo-MotionCompensation
[    22.665] Initializing built-in extension XFree86-VidModeExtension
[    22.665] Initializing built-in extension XFree86-DGA
[    22.665] Initializing built-in extension XFree86-DRI
[    22.665] Initializing built-in extension DRI2
[    22.665] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    22.665] (II) LoadModule: "glx"
[    22.729] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    22.997] (II) Module glx: vendor="NVIDIA Corporation"
[    22.997] 	compiled for 4.0.2, module version = 1.0.0
[    22.997] 	Module class: X.Org Server Extension
[    22.997] (II) NVIDIA GLX Module  173.14.39  Wed Nov 27 14:44:39 PST 2013
[    22.997] Loading extension GLX
[    22.997] (II) LoadModule: "nouveau"
[    23.087] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    23.111] (II) Module nouveau: vendor="X.Org Foundation"
[    23.111] 	compiled for 1.15.1, module version = 1.0.10
[    23.111] 	Module class: X.Org Video Driver
[    23.111] 	ABI class: X.Org Video Driver, version 15.0
[    23.111] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    23.111] (II) NOUVEAU driver for NVIDIA chipset families :
[    23.111] 	RIVA TNT        (NV04)
[    23.111] 	RIVA TNT2       (NV05)
[    23.111] 	GeForce 256     (NV10)
[    23.111] 	GeForce 2       (NV11, NV15)
[    23.111] 	GeForce 4MX     (NV17, NV18)
[    23.111] 	GeForce 3       (NV20)
[    23.111] 	GeForce 4Ti     (NV25, NV28)
[    23.111] 	GeForce FX      (NV3x)
[    23.111] 	GeForce 6       (NV4x)
[    23.111] 	GeForce 7       (G7x)
[    23.111] 	GeForce 8       (G8x)
[    23.111] 	GeForce GTX 200 (NVA0)
[    23.111] 	GeForce GTX 400 (NVC0)
[    23.111] (++) using VT number 7

[    23.111] (EE) [drm] KMS not enabled
[    23.111] (EE) No devices detected.
[    23.111] (==) Matched nvidia as autoconfigured driver 0
[    23.111] (==) Matched nouveau as autoconfigured driver 1
[    23.111] (==) Matched modesetting as autoconfigured driver 2
[    23.111] (==) Matched fbdev as autoconfigured driver 3
[    23.111] (==) Matched vesa as autoconfigured driver 4
[    23.111] (==) Assigned the driver to the xf86ConfigLayout
[    23.111] (II) LoadModule: "nvidia"
[    23.111] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    23.150] (II) Module nvidia: vendor="NVIDIA Corporation"
[    23.150] 	compiled for 4.0.2, module version = 1.0.0
[    23.150] 	Module class: X.Org Video Driver
[    23.177] (II) LoadModule: "nouveau"
[    23.178] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    23.178] (II) Module nouveau: vendor="X.Org Foundation"
[    23.178] 	compiled for 1.15.1, module version = 1.0.10
[    23.178] 	Module class: X.Org Video Driver
[    23.178] 	ABI class: X.Org Video Driver, version 15.0
[    23.178] (II) UnloadModule: "nouveau"
[    23.178] (II) Unloading nouveau
[    23.178] (II) Failed to load module "nouveau" (already loaded, 32745)
[    23.178] (II) LoadModule: "modesetting"
[    23.178] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    23.196] (II) Module modesetting: vendor="X.Org Foundation"
[    23.196] 	compiled for 1.15.1, module version = 0.8.1
[    23.196] 	Module class: X.Org Video Driver
[    23.196] 	ABI class: X.Org Video Driver, version 15.0
[    23.196] (II) LoadModule: "fbdev"
[    23.196] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    23.204] (II) Module fbdev: vendor="X.Org Foundation"
[    23.204] 	compiled for 1.15.1, module version = 0.4.4
[    23.204] 	Module class: X.Org Video Driver
[    23.204] 	ABI class: X.Org Video Driver, version 15.0
[    23.204] (II) LoadModule: "vesa"
[    23.204] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    23.313] (II) Module vesa: vendor="X.Org Foundation"
[    23.313] 	compiled for 1.15.1, module version = 2.3.3
[    23.313] 	Module class: X.Org Video Driver
[    23.313] 	ABI class: X.Org Video Driver, version 15.0
[    23.313] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    23.313] (II) NOUVEAU driver for NVIDIA chipset families :
[    23.313] 	RIVA TNT        (NV04)
[    23.313] 	RIVA TNT2       (NV05)
[    23.313] 	GeForce 256     (NV10)
[    23.313] 	GeForce 2       (NV11, NV15)
[    23.313] 	GeForce 4MX     (NV17, NV18)
[    23.313] 	GeForce 3       (NV20)
[    23.313] 	GeForce 4Ti     (NV25, NV28)
[    23.313] 	GeForce FX      (NV3x)
[    23.313] 	GeForce 6       (NV4x)
[    23.313] 	GeForce 7       (G7x)
[    23.313] 	GeForce 8       (G8x)
[    23.313] 	GeForce GTX 200 (NVA0)
[    23.313] 	GeForce GTX 400 (NVC0)
[    23.332] (II) NVIDIA dlloader X Driver  173.14.39  Wed Nov 27 14:34:40 PST 2013
[    23.332] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    23.332] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    23.332] (II) FBDEV: driver for framebuffer: fbdev
[    23.332] (II) VESA: driver for VESA chipsets: vesa
[    23.332] (++) using VT number 7

[    23.332] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    23.332] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    23.332] (EE) [drm] KMS not enabled
[    23.333] (II) Loading sub module "fb"
[    23.333] (II) LoadModule: "fb"
[    23.445] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.480] (II) Module fb: vendor="X.Org Foundation"
[    23.480] 	compiled for 1.15.1, module version = 1.0.0
[    23.480] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.480] (II) Loading sub module "wfb"
[    23.480] (II) LoadModule: "wfb"
[    23.480] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    23.484] (II) Module wfb: vendor="X.Org Foundation"
[    23.484] 	compiled for 1.15.1, module version = 1.0.0
[    23.484] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.484] (II) Loading sub module "ramdac"
[    23.484] (II) LoadModule: "ramdac"
[    23.484] (II) Module "ramdac" already built-in
[    23.484] (WW) Falling back to old probe method for modesetting
[    23.484] (EE) open /dev/dri/card0: No such file or directory
[    23.484] (WW) Falling back to old probe method for fbdev
[    23.484] (II) Loading sub module "fbdevhw"
[    23.484] (II) LoadModule: "fbdevhw"
[    23.485] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    23.633] (II) Module fbdevhw: vendor="X.Org Foundation"
[    23.633] 	compiled for 1.15.1, module version = 0.0.2
[    23.633] 	ABI class: X.Org Video Driver, version 15.0
[    23.633] (WW) Falling back to old probe method for vesa
[    23.737] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    23.737] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    23.737] (==) NVIDIA(0): RGB weight 888
[    23.737] (==) NVIDIA(0): Default visual is TrueColor
[    23.737] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    23.737] (**) NVIDIA(0): Option "NoLogo" "True"
[    23.846] (**) NVIDIA(0): Enabling RENDER acceleration
[    23.846] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    23.846] (II) NVIDIA(0):     enabled.
[    23.903] (EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
[    23.903] (EE) NVIDIA(0):  *** Aborting ***
[    23.903] (II) UnloadModule: "nvidia"
[    23.903] (II) UnloadSubModule: "wfb"
[    23.903] (II) UnloadSubModule: "fb"
[    23.903] (EE) Screen(s) found, but none have a usable configuration.
[    23.903] (EE) 
Fatal server error:
[    23.903] (EE) no screens found(EE) 
[    23.903] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    23.903] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    23.903] (EE) 
[    23.907] (EE) Server terminated with error (1). Closing log file.
```Looks the same to me, and the system is starting tin Low-graphics mode just as before.  Also Vesa shows as the driver in Applications>System Tools>System Settings>Details.  So I am making no progress at all.

---

### Post by Gyokuro on 2014-08-09
Hi

Looking at your xorg.log it seems that the system tries to load NVidia drivers and is unable to load the nvidia kernel glue driver. What do you mean you have installed the driver manually as normally you can uninstall it via:

sudo apt-get purge nvidia-current

another thing is you have not mentioned which NVidia card get used and therefore it's possible that nouveau do not support your card. Could you please post the missing parts?

- HTH

---

### Post by ubfan1 on 2014-08-09
Another thing to look at:  Remove any old ppas you might have set up (xswat... etc.), redo the sudo apt-get update, explicitly purge all nvidia packages:
dpkg -l |fgrep nvidia     then sudo apt-get purge nvidia*.    Now you can try nouveau, or reinstall the nvidia-current (Looks like you might be running an old 173... driver from your log). and see what version you get.

---

### Post by cscj01 on 2014-08-09
to Gyokuro:

I installed a .run file that I downloaded from the Nvidia web site because there was no proprietary driver available to me except nvidia-173  and that did not support my graphics card, and it was listed in Synaptic and not in Additional Drivers.  Additional Drivers contained nothing.  And yes, I let the search complete.  I have an EVA Geforce GTX 750 TI.  I have since uninstalled the driver that I downloaded from Nvidia.> **ubfan1 said:**
> Another thing to look at:  Remove any old ppas you might have set up (xswat... etc.), redo the sudo apt-get update, explicitly purge all nvidia packages:
dpkg -l |fgrep nvidia     then sudo apt-get purge nvidia*.    Now you can try nouveau, or reinstall the nvidia-current (Looks like you might be running an old 173... driver from your log). and see what version you get.
I have used ppa-purge to completely remove all PPA's, and I have removed them from Software Sources.  I uninstalled nvidia-173 and purged all nvidia files.  I then rebooted with no change in behavior.  I can only install nvidia-173 because all others have a dependency on xorg-video-abi-11 or xorg-video-abi-12 xorg-video-abi-13 or xorg-video-abi-14 and none of these show in Synaptic so that I could even attempt to install them.  Here is the latest xorg log.```
[    23.780] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    23.780] X Protocol Version 11, Revision 0
[    23.780] Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
[    23.780] Current Operating System: Linux Car-Photo-Ubuntu 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:51:20 UTC 2014 x86_64
[    23.780] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=b61632e9-7186-4ec9-9e4c-214c01d39a4e ro vga=769 quiet splash nomodeset vt.handoff=7
[    23.780] Build Date: 07 August 2014  11:49:36AM
[    23.780] xorg-server 2:1.15.1-0ubuntu2~precise2 (For technical support please see http://www.ubuntu.com/support) 
[    23.780] Current version of pixman: 0.30.2
[    23.780] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    23.780] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    23.780] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Aug  9 20:26:48 2014
[    23.835] (==) Using config file: "/etc/X11/xorg.conf"
[    23.835] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.115] (==) No Layout section.  Using the first Screen section.
[    24.115] (**) |-->Screen "Default Screen" (0)
[    24.115] (**) |   |-->Monitor "<default monitor>"
[    24.175] (==) No device specified for screen "Default Screen".
	Using the first device section listed.
[    24.175] (**) |   |-->Device "Default Device"
[    24.175] (==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
[    24.175] (==) Automatically adding devices
[    24.175] (==) Automatically enabling devices
[    24.175] (==) Automatically adding GPU devices
[    24.374] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.374] 	Entry deleted from font path.
[    24.413] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	built-ins
[    24.413] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.413] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.413] (II) Loader magic: 0x7f280d3b6c20
[    24.413] (II) Module ABI versions:
[    24.413] 	X.Org ANSI C Emulation: 0.4
[    24.413] 	X.Org Video Driver: 15.0
[    24.413] 	X.Org XInput driver : 20.0
[    24.413] 	X.Org Server Extension : 8.0
[    24.414] (--) PCI:*(0:1:0:0) 10de:1380:3842:3757 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    24.447] Initializing built-in extension Generic Event Extension
[    24.447] Initializing built-in extension SHAPE
[    24.447] Initializing built-in extension MIT-SHM
[    24.447] Initializing built-in extension XInputExtension
[    24.447] Initializing built-in extension XTEST
[    24.447] Initializing built-in extension BIG-REQUESTS
[    24.447] Initializing built-in extension SYNC
[    24.447] Initializing built-in extension XKEYBOARD
[    24.447] Initializing built-in extension XC-MISC
[    24.447] Initializing built-in extension SECURITY
[    24.447] Initializing built-in extension XINERAMA
[    24.447] Initializing built-in extension XFIXES
[    24.447] Initializing built-in extension RENDER
[    24.447] Initializing built-in extension RANDR
[    24.447] Initializing built-in extension COMPOSITE
[    24.447] Initializing built-in extension DAMAGE
[    24.447] Initializing built-in extension MIT-SCREEN-SAVER
[    24.447] Initializing built-in extension DOUBLE-BUFFER
[    24.447] Initializing built-in extension RECORD
[    24.447] Initializing built-in extension DPMS
[    24.447] Initializing built-in extension X-Resource
[    24.447] Initializing built-in extension XVideo
[    24.447] Initializing built-in extension XVideo-MotionCompensation
[    24.447] Initializing built-in extension XFree86-VidModeExtension
[    24.447] Initializing built-in extension XFree86-DGA
[    24.447] Initializing built-in extension XFree86-DRI
[    24.447] Initializing built-in extension DRI2
[    24.447] (II) "glx" will be loaded. This was enabled by default and also specified in the config file.
[    24.447] (II) LoadModule: "glx"
[    24.541] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    24.577] (II) Module glx: vendor="X.Org Foundation"
[    24.577] 	compiled for 1.13.0, module version = 1.0.0
[    24.577] 	ABI class: X.Org Server Extension, version 7.0
[    24.577] (EE) module ABI major version (7) doesn't match the server's version (8)
[    24.577] (II) UnloadModule: "glx"
[    24.577] (II) Unloading glx
[    24.577] (EE) Failed to load module "glx" (module requirement mismatch, 0)
[    24.577] (II) LoadModule: "nouveau"
[    24.577] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    24.934] (II) Module nouveau: vendor="X.Org Foundation"
[    24.934] 	compiled for 1.15.1, module version = 1.0.10
[    24.934] 	Module class: X.Org Video Driver
[    24.934] 	ABI class: X.Org Video Driver, version 15.0
[    24.934] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    24.934] (II) NOUVEAU driver for NVIDIA chipset families :
[    24.934] 	RIVA TNT        (NV04)
[    24.934] 	RIVA TNT2       (NV05)
[    24.934] 	GeForce 256     (NV10)
[    24.934] 	GeForce 2       (NV11, NV15)
[    24.934] 	GeForce 4MX     (NV17, NV18)
[    24.934] 	GeForce 3       (NV20)
[    24.934] 	GeForce 4Ti     (NV25, NV28)
[    24.934] 	GeForce FX      (NV3x)
[    24.934] 	GeForce 6       (NV4x)
[    24.934] 	GeForce 7       (G7x)
[    24.934] 	GeForce 8       (G8x)
[    24.934] 	GeForce GTX 200 (NVA0)
[    24.934] 	GeForce GTX 400 (NVC0)
[    24.934] (++) using VT number 7

[    24.934] (EE) [drm] KMS not enabled
[    24.934] (EE) No devices detected.
[    24.934] (==) Matched nvidia as autoconfigured driver 0
[    24.934] (==) Matched nouveau as autoconfigured driver 1
[    24.934] (==) Matched modesetting as autoconfigured driver 2
[    24.934] (==) Matched fbdev as autoconfigured driver 3
[    24.934] (==) Matched vesa as autoconfigured driver 4
[    24.934] (==) Assigned the driver to the xf86ConfigLayout
[    24.934] (II) LoadModule: "nvidia"
[    25.227] (WW) Warning, couldn't open module nvidia
[    25.227] (II) UnloadModule: "nvidia"
[    25.227] (II) Unloading nvidia
[    25.227] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    25.227] (II) LoadModule: "nouveau"
[    25.227] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    25.227] (II) Module nouveau: vendor="X.Org Foundation"
[    25.227] 	compiled for 1.15.1, module version = 1.0.10
[    25.227] 	Module class: X.Org Video Driver
[    25.227] 	ABI class: X.Org Video Driver, version 15.0
[    25.227] (II) UnloadModule: "nouveau"
[    25.227] (II) Unloading nouveau
[    25.227] (II) Failed to load module "nouveau" (already loaded, 0)
[    25.227] (II) LoadModule: "modesetting"
[    25.227] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    25.295] (II) Module modesetting: vendor="X.Org Foundation"
[    25.295] 	compiled for 1.15.1, module version = 0.8.1
[    25.295] 	Module class: X.Org Video Driver
[    25.295] 	ABI class: X.Org Video Driver, version 15.0
[    25.295] (II) LoadModule: "fbdev"
[    25.295] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.303] (II) Module fbdev: vendor="X.Org Foundation"
[    25.303] 	compiled for 1.15.1, module version = 0.4.4
[    25.303] 	Module class: X.Org Video Driver
[    25.303] 	ABI class: X.Org Video Driver, version 15.0
[    25.303] (II) LoadModule: "vesa"
[    25.303] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.337] (II) Module vesa: vendor="X.Org Foundation"
[    25.337] 	compiled for 1.15.1, module version = 2.3.3
[    25.337] 	Module class: X.Org Video Driver
[    25.337] 	ABI class: X.Org Video Driver, version 15.0
[    25.337] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    25.337] (II) NOUVEAU driver for NVIDIA chipset families :
[    25.337] 	RIVA TNT        (NV04)
[    25.337] 	RIVA TNT2       (NV05)
[    25.337] 	GeForce 256     (NV10)
[    25.337] 	GeForce 2       (NV11, NV15)
[    25.337] 	GeForce 4MX     (NV17, NV18)
[    25.337] 	GeForce 3       (NV20)
[    25.337] 	GeForce 4Ti     (NV25, NV28)
[    25.337] 	GeForce FX      (NV3x)
[    25.337] 	GeForce 6       (NV4x)
[    25.337] 	GeForce 7       (G7x)
[    25.337] 	GeForce 8       (G8x)
[    25.337] 	GeForce GTX 200 (NVA0)
[    25.337] 	GeForce GTX 400 (NVC0)
[    25.337] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    25.337] (II) FBDEV: driver for framebuffer: fbdev
[    25.337] (II) VESA: driver for VESA chipsets: vesa
[    25.337] (++) using VT number 7

[    25.337] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[    25.337] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[    25.337] (EE) [drm] KMS not enabled
[    25.337] (EE) open /dev/dri/card0: No such file or directory
[    25.337] (WW) Falling back to old probe method for modesetting
[    25.337] (EE) open /dev/dri/card0: No such file or directory
[    25.337] (II) Loading sub module "fbdevhw"
[    25.337] (II) LoadModule: "fbdevhw"
[    25.337] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.467] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.467] 	compiled for 1.15.1, module version = 0.0.2
[    25.467] 	ABI class: X.Org Video Driver, version 15.0
[    25.467] (**) FBDEV(1): claimed PCI slot 1@0:0:0
[    25.467] (II) FBDEV(1): using default device
[    25.467] (WW) Falling back to old probe method for vesa
[    25.467] (EE) Screen 0 deleted because of no matching config section.
[    25.467] (II) UnloadModule: "modesetting"
[    25.467] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    25.467] (**) FBDEV(0): Depth 24, (--) framebuffer bpp 32
[    25.467] (==) FBDEV(0): RGB weight 888
[    25.467] (==) FBDEV(0): Default visual is TrueColor
[    25.467] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.467] (II) FBDEV(0): hardware: VESA VGA (video memory: 320kB)
[    25.467] (II) FBDEV(0): checking modes against framebuffer device...
[    25.467] (II) FBDEV(0): checking modes against monitor...
[    25.467] (--) FBDEV(0): Virtual size is 640x480 (pitch 640)
[    25.467] (**) FBDEV(0):  Built-in mode "current": 30.7 MHz, 36.9 kHz, 73.3 Hz
[    25.467] (II) FBDEV(0): Modeline "current"x0.0   30.72  640 672 752 832  480 484 488 504 -hsync -vsync -csync (36.9 kHz b)
[    25.467] (==) FBDEV(0): DPI set to (96, 96)
[    25.467] (II) Loading sub module "fb"
[    25.467] (II) LoadModule: "fb"
[    25.467] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.010] (II) Module fb: vendor="X.Org Foundation"
[    26.010] 	compiled for 1.15.1, module version = 1.0.0
[    26.010] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.010] (**) FBDEV(0): using shadow framebuffer
[    26.010] (II) Loading sub module "shadow"
[    26.010] (II) LoadModule: "shadow"
[    26.011] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    26.106] (II) Module shadow: vendor="X.Org Foundation"
[    26.106] 	compiled for 1.15.1, module version = 1.1.0
[    26.106] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    26.106] (II) UnloadModule: "vesa"
[    26.106] (II) Unloading vesa
[    26.106] (==) Depth 24 pixmap format is 32 bpp
[    26.106] (EE) FBDEV(0): FBIOPUT_VSCREENINFO succeeded but modified mode
[    26.106] (EE) FBDEV(0): mode initialization failed
[    26.106] (EE) 
Fatal server error:
[    26.106] (EE) AddScreen/ScreenInit failed for driver 0
[    26.106] (EE) 
[    26.106] (EE) 
Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
[    26.106] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    26.106] (EE) 
[    26.110] (EE) Server terminated with error (1). Closing log file.
```

---

### Post by ubfan1 on 2014-08-10
Try installing the "nvidia-current" and let the package manager sort out the dependencies.  I use the 304 driver, which has the depends on abi you mention, but I don't see those packages either, so maybe they're optionsl ( | next to the names?).

---

### Post by cscj01 on 2014-08-10
> **ubfan1 said:**
> Try installing the "nvidia-current" and let the package manager sort out the dependencies.  I use the 304 driver, which has the depends on abi you mention, but I don't see those packages either, so maybe they're optionsl ( | next to the names?).When I try to install nvidia-current, Synaptic also wants to install nvidia-settings.  When I click Mark, I get the following message:> nvidia-current:
 Depends: nvidia-304 but it is not going to be installedIf I try to install nvidia-304, Synaptic wants to install nvidia settings.  When I click Mark, I receive the following message> Could not mark all packages for installation
or upgrade

The following packages have unresolved dependencies.
Make sure that all required repositories are added and
enabled in the preferences

nvidia-304:
 Depends: xorg-video-abi-11 or
 	xorg-video-abi-12  but it is not installable or
	xorg-video-abi-13 or
	xorg-video-abi-14I have never changed preferencies, but I checked Synaptic preferencies anyway.  On the General tab under Marking Changes, "Ask to confirm changes that also affect other packages" and "Consider recommended packages as dependencies" are checked.  Removal of packages = Completely, System upgrade = Smart Upgrade, and Reloading outdated package information = Always Ask.  On the Distribution tab, "Always prefer the highest version" is checked.

Under Repositories on the Ubuntu Software, main, universe, restricted, and multiverse are checked.
Under Other Software, Canonical Partners is active.
Under Updates, precise security, precise updates, and precise backports are checked.

Only nvidia-173 will allow me to install it.

If I search for nouveau, the following are installed:> libdrm-nouveau1a
libdrm-nouveau2
xserver-xorg-video-nouveau-lts-trusty
libdrm-nouveau1a:i386
libdrm-nouveau2:i386
I'm beginning to think I am going to have to reinstall the driver I downloaded from Nvidia to get the system to function correctly again.  That is, even if that would work now.

---

### Post by ubfan1 on 2014-08-10
I recently added the trusty packages to my 12.04, and went through some similar problems.  I use the software updater, not synaptic, and installed the "current" 304.116 drivers without any ppas.  I do NOT have any of the abi packages installed, so you should be able to "force" synaptic to install anyway. This 116 driver was NOT the 304.117 I was using on my 14.04 system, and it did NOT work.  The fix was to edit the nv-acpi.c file (I did it in both places) /usr/src/nvidia-304-304.116/nv-acpi.c and /var/lib/dkms/nvidia-304/304.116/build/nv-acpi.c, became root and ran the make.  The edit of that file was the same one as in the 117 driver, getting rid of the unknown symbol by skipping for the 3.13 kernels.  The edit was adding the #if around the call:
   302  #if LINUX_VERSION_CODE < KERNEL_VERSION(3, 13, 0)
   303          NV_ACPI_OS_WAIT_EVENTS_COMPLETE();
   304  #endif
This produced a working nvidia kernel (bugs have been filed upstream, I guess that's the fix the  xswat ppa is offering).

---

### Post by cscj01 on 2014-08-10
Well, I gave up and installed the driver (.run) file I downloaded from Nvidia.  All my problems went away.  So I will mark this as solved.  Thanks to all who offered suggestions and advice.  This experience makes me leery of upgrading to 14.04.

---

