---
title: "NVIDIA drivers"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by c2483 on 2009-10-26
nvidia-glx-185 still does not work for me in karmic rc
it boots up fine and I hear the startup sound but the the screen goes black, looks like the monitor goes into standby mode.  I hoped this would be fixed by now.  I'm stuck using nouveau.  I have an LCD and a 7600gt.
185 is the only one I tried with rc.  I tried them all however with the beta including 190.32 but all did not work.  Is there any solution?

---

### Post by dino99 on 2009-10-27
i'm using 190.42 without problem.
Maybe try to reinstall driver, what do you see in xorg.0.log ?

[http://www.x.org/wiki/ConfigurationHelp](http://www.x.org/wiki/ConfigurationHelp)

deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) karmic main

---

### Post by c2483 on 2009-10-27
ok, I did that and installed nvidia-190-libvdpau and nvidia-settings-190 and changed my xorg.conf from Driver "nouveau" to 
Driver "nvidia" then rebooted but all I get is a console that says no module nvidia found and no screens found.

It works like this with my old driver
```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nouveau"
	#Option	"NoLogo"	"True"
EndSection

```

but not like this
```

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
	#Option	"NoLogo"	"True"
EndSection

```

---

### Post by c2483 on 2009-10-27
I guess I forgot nvidia-glx-190
same result as before

---

### Post by Dougie187 on 2009-10-27
have you tried manually installing the nvidia drivers?

---

### Post by dino99 on 2009-10-27
packages installed:

nvidia-190-libvdpau
nvidia-settings-190
nvidia-190-kernel-source
nvidia-common
nvidia-190-modaliases
nvidia-glx-190

need also: build-essential to install from sources.

Proposed solution:

- change to nouveau or nv
- reboot
- remove / purge nvidia*
- reboot

- reinstall all the nvidia packages above
- go to system --> administration --> driver : choose & activate 190
- reboot
- look at xorg.0.log to see if errors exist

---

### Post by dino99 on 2009-10-27
with karmic, xorg.conf is not needed ( and can be deleted) if you don't need tweakings for multi graphic cards or multi monitors or particular settings.

---

### Post by c2483 on 2009-10-27
I'll try this and see what happens
> **dino99 said:**
> packages installed:

nvidia-190-libvdpau
nvidia-settings-190
nvidia-190-kernel-source
nvidia-common
nvidia-190-modaliases
nvidia-glx-190

need also: build-essential to install from sources.

Proposed solution:

- change to nouveau or nv
- remove / purge nvidia*
- reboot

- reinstall all the nvidia packages above
- go to system --> administration --> driver : choose & activate 190
- reboot
- look at xorg.0.log to see if errors exist

---

### Post by c2483 on 2009-10-27
I did that, tried with and without an xorg.conf, just boot into ubuntu then the screen turns off

---

### Post by ibuclaw on 2009-10-27
```
sudo nvidia-bug-report.sh
```

And attach the file generated to your next post.

Regards
Iain

---

### Post by c2483 on 2009-10-27
```
____________________________________________

Start of NVIDIA bug report log file.  Please include this file
when reporting a graphics driver bug via the nV News NVIDIA
Linux forum (see www.nvnews.net) or by sending email to
'linux-bugs@nvidia.com'.

nvidia-bug-report.sh Version: 4401223

Date: Tue Oct 27 14:31:54 EDT 2009
uname: Linux charles-pc 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

____________________________________________

/etc/issue
Ubuntu 9.10 \n \l


____________________________________________

/etc/debian_version
squeeze/sid

____________________________________________

/var/log/nvidia-installer.log does not exist

____________________________________________

/var/log/XFree86.0.log does not exist

____________________________________________

/var/log/XFree86.0.log.old does not exist

____________________________________________

/var/log/Xorg.0.log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux charles-pc 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 27 14:29:56 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
(**) |   |-->Device "Device0"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0391:3842:c553 nVidia Corporation G73 [GeForce 7600 GT] rev 161, Mem @ 0xf7000000/16777216, 0xd0000000/268435456, 0xf6000000/16777216, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.42  Tue Oct 20 21:19:30 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  190.42  Tue Oct 20 20:42:04 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Oct 27 14:29:58 NVIDIA(0): Enabling RENDER acceleration
(II) Oct 27 14:29:58 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Oct 27 14:29:58 NVIDIA(0):     enabled.
(II) Oct 27 14:30:01 NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) Oct 27 14:30:01 NVIDIA(0): Memory: 262144 kBytes
(--) Oct 27 14:30:01 NVIDIA(0): VideoBIOS: 05.73.22.18.01
(II) Oct 27 14:30:01 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Oct 27 14:30:01 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Oct 27 14:30:01 NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) Oct 27 14:30:01 NVIDIA(0):     SONY TV (CRT-1)
(--) Oct 27 14:30:01 NVIDIA(0):     LG L203WTX (DFP-0)
(--) Oct 27 14:30:01 NVIDIA(0): SONY TV (CRT-1): 400.0 MHz maximum pixel clock
(--) Oct 27 14:30:01 NVIDIA(0): LG L203WTX (DFP-0): 330.0 MHz maximum pixel clock
(--) Oct 27 14:30:01 NVIDIA(0): LG L203WTX (DFP-0): Internal Dual Link TMDS
(II) Oct 27 14:30:01 NVIDIA(0): Assigned Display Device: CRT-1
(==) Oct 27 14:30:01 NVIDIA(0): 
(==) Oct 27 14:30:01 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Oct 27 14:30:01 NVIDIA(0):     will be used as the requested mode.
(==) Oct 27 14:30:01 NVIDIA(0): 
(II) Oct 27 14:30:01 NVIDIA(0): Validated modes:
(II) Oct 27 14:30:01 NVIDIA(0):     "nvidia-auto-select"
(II) Oct 27 14:30:01 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) Oct 27 14:30:01 NVIDIA(0): DPI set to (30, 30); computed from "UseEdidDpi" X config
(--) Oct 27 14:30:01 NVIDIA(0):     option
(==) Oct 27 14:30:01 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Oct 27 14:30:01 NVIDIA(0): Initialized GPU GART.
(II) Oct 27 14:30:01 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Oct 27 14:30:01 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Oct 27 14:30:01 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device   USB Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event4"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device   USB Keyboard
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event3"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event5"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB Optical Mouse: initialized for relative axes.

____________________________________________

/etc/X11/xorg.conf
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
EndSection


____________________________________________

/var/log/Xorg.0.log.old

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux charles-pc 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 27 13:50:50 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
(**) |   |-->Device "Device0"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0391:3842:c553 nVidia Corporation G73 [GeForce 7600 GT] rev 161, Mem @ 0xf7000000/16777216, 0xd0000000/268435456, 0xf6000000/16777216, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers//nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 0.0.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) NOUVEAU driver Date:   Thu Aug 20 18:44:38 2009 +0200
(II) NOUVEAU driver for NVIDIA chipset families :
	RIVA TNT    (NV04)
	RIVA TNT2   (NV05)
	GeForce 256 (NV10)
	GeForce 2   (NV11, NV15)
	GeForce 4MX (NV17, NV18)
	GeForce 3   (NV20)
	GeForce 4Ti (NV25, NV28)
	GeForce FX  (NV3x)
	GeForce 6   (NV4x)
	GeForce 7   (G7x)
	GeForce 8   (G8x)
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(--) NOUVEAU(0): Chipset: "NVIDIA NV4B"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NOUVEAU(0): Initializing int10
(II) NOUVEAU(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) NOUVEAU(0): [drm] nouveau interface version: 0.0.15
(--) NOUVEAU(0): [drm] kernel modesetting not available
(II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
(==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(==) NOUVEAU(0): Using HW cursor
(--) NOUVEAU(0): Linear framebuffer at 0xD0000000
(--) NOUVEAU(0): MMIO registers at 0xF7000000
(II) NOUVEAU(0): Initial CRTC_OWNER is 4
(II) NOUVEAU(0): Attempting to load BIOS image from PROM
(II) NOUVEAU(0): ... appears to be valid
(II) NOUVEAU(0): BIT BIOS found
(II) NOUVEAU(0): Bios version 05.73.22.18
(II) NOUVEAU(0): Found Display Configuration Block version 3.0
(!!) NOUVEAU(0): Raw DCB entry 0: 01000300 00000028
(!!) NOUVEAU(0): Raw DCB entry 1: 03000302 00000000
(!!) NOUVEAU(0): Raw DCB entry 2: 04011310 00000028
(!!) NOUVEAU(0): Raw DCB entry 3: 04011312 00000000
(!!) NOUVEAU(0): Raw DCB entry 4: 020223f1 00c0c080
(--) NOUVEAU(0): Parsing VBIOS init table 0 at offset 0xDE3C
(--) NOUVEAU(0): Parsing VBIOS init table 1 at offset 0xE4B6
(--) NOUVEAU(0): Parsing VBIOS init table 2 at offset 0xEB4C
(--) NOUVEAU(0): Parsing VBIOS init table 3 at offset 0xECCC
(--) NOUVEAU(0): Parsing VBIOS init table 4 at offset 0xEE26
(II) NOUVEAU(0): Output DVI-I-0 has no monitor section
(II) NOUVEAU(0): I2C bus "DVI-I-0" initialized.
(II) NOUVEAU(0): Output DVI-I-1 has no monitor section
(II) NOUVEAU(0): I2C bus "DVI-I-1" initialized.
(II) NOUVEAU(0): I2C device "DVI-I-0:E-EDID segment register" registered at address 0x60.
(II) NOUVEAU(0): I2C device "DVI-I-0:ddc2" registered at address 0xA0.
(II) NOUVEAU(0): EDID for output DVI-I-0
(II) NOUVEAU(0): Manufacturer: GSM  Model: 4e40  Serial#: 179771
(II) NOUVEAU(0): Year: 2006  Week: 2
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): GTF timings supported
(II) NOUVEAU(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.615
(II) NOUVEAU(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x870@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 85 Hz, H min: 28 H max: 83 kHz, PixClock max 140 MHz
(II) NOUVEAU(0): Monitor name: L203WTX
(II) NOUVEAU(0): Monitor name: 
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff001e6d404e3bbe0200
(II) NOUVEAU(0): 	02100103ee2b1b78eac605a3574a9d25
(II) NOUVEAU(0): 	125054a76b808180714f615945593140
(II) NOUVEAU(0): 	0101010101017c2e90a0601a1e403020
(II) NOUVEAU(0): 	3600b20e1100001a000000fd0038551c
(II) NOUVEAU(0): 	530e000a202020202020000000fc004c
(II) NOUVEAU(0): 	3230335754580a2020202020000000fc
(II) NOUVEAU(0): 	000a2020202020202020202020200099
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Using EDID range info for horizontal sync
(II) NOUVEAU(0): Using EDID range info for vertical refresh
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Printing probed modes for output DVI-I-0
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): I2C device "DVI-I-1:E-EDID segment register" registered at address 0x60.
(II) NOUVEAU(0): I2C device "DVI-I-1:ddc2" registered at address 0xA0.
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): Manufacturer: SNY  Model: 5401  Serial#: 16843009
(II) NOUVEAU(0): Year: 2008  Week: 1
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NOUVEAU(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 57 V max: 63 Hz, H min: 30 H max: 80 kHz, PixClock max 150 MHz
(II) NOUVEAU(0): Monitor name: SONY TV
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff004dd9015401010101
(II) NOUVEAU(0): 	0112010308a05a780a0dc9a057479827
(II) NOUVEAU(0): 	12484c21080081800101010101010101
(II) NOUVEAU(0): 	010101010101023a801871382d40582c
(II) NOUVEAU(0): 	450040846300001e662150b051001b30
(II) NOUVEAU(0): 	4070360040846300001e000000fd0039
(II) NOUVEAU(0): 	3f1e500f000a202020202020000000fc
(II) NOUVEAU(0): 	00534f4e592054560a20202020200080
(II) NOUVEAU(0): EDID vendor "SNY", prod id 21505
(II) NOUVEAU(0): Printing probed modes for output DVI-I-1
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Output DVI-I-0 connected
(II) NOUVEAU(0): Output DVI-I-1 connected
(II) NOUVEAU(0): Using fuzzy aspect match for initial modes
(II) NOUVEAU(0): Output DVI-I-0 using initial mode 1024x768
(II) NOUVEAU(0): Output DVI-I-1 using initial mode 1024x768
(--) NOUVEAU(0): VideoRAM: 262144 kBytes
(==) NOUVEAU(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NOUVEAU(0): Virtual size is 1024x768 (pitch 1024)
(**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NOUVEAU(0):  Default mode "800x600": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NOUVEAU(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NOUVEAU(0):  Default mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NOUVEAU(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NOUVEAU(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NOUVEAU(0):  Default mode "720x400": 35.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NOUVEAU(0):  Default mode "640x400": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Default mode "640x350": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(**) NOUVEAU(0):  Default mode "1600x1024": 103.1 MHz (scaled from 0.0 MHz), 62.0 kHz, 60.2 Hz
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(**) NOUVEAU(0):  Default mode "1400x1050": 122.0 MHz (scaled from 0.0 MHz), 64.9 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NOUVEAU(0):  Default mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) NOUVEAU(0):  Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NOUVEAU(0):  Default mode "1360x768": 84.8 MHz (scaled from 0.0 MHz), 47.7 kHz, 59.8 Hz
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 121.5 MHz (scaled from 0.0 MHz), 77.5 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 105.0 MHz (scaled from 0.0 MHz), 67.6 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NOUVEAU(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NOUVEAU(0): Display dimensions: (430, 270) mm
(**) NOUVEAU(0): DPI set to (60, 72)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NOUVEAU(0): Opened GPU channel 1
(II) NOUVEAU(0): [drm] Using the DRM lock SAREA also for drawables.
(II) NOUVEAU(0): [drm] framebuffer handle = 0x2fff9000
(II) NOUVEAU(0): [drm] added 1 reserved context for kernel
(II) NOUVEAU(0): X context handle = 0x1
(II) NOUVEAU(0): [drm] installed DRM signal handler
(II) NOUVEAU(0): Allocated 125MiB VRAM for offscreen pixmaps
(II) NOUVEAU(0): AGPGART: 64MiB available
(II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
(II) NOUVEAU(0): Saving VGA fonts
(II) NOUVEAU(0): Saving crtcs
(II) NOUVEAU(0): Saving encoders
(II) EXA(0): Offscreen pixmap area of 131072000 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) NOUVEAU(0): Backing store disabled
(==) NOUVEAU(0): Silken mouse enabled
(II) NOUVEAU(0): [DRI] installation complete
(II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
(II) NOUVEAU(0): [XvMC] Extension initialized.
(II) NOUVEAU(0): NVEnterVT is called.
(II) NOUVEAU(0): Saving VGA fonts
(II) NOUVEAU(0): Saving crtcs
(II) NOUVEAU(0): Saving encoders
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 0)
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 1)
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 2)
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 3)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): CTRC mode on CRTC 0:
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Output mode on CRTC 0:
(II) NOUVEAU(0): Modeline "1024x768"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): vpll: n 22 m 5 log2p 0
(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): 0xD1FB: Parsing digital output script table
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 0 on tmds encoder (output 1)
(II) NOUVEAU(0): Output DVI-I-0 is running on CRTC 0 using output A
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): CTRC mode on CRTC 1:
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Output mode on CRTC 1:
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): vpll: n 53 m 11 log2p 1
(II) NOUVEAU(0): nv_output_mode_set called for encoder 2
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 2)
(II) NOUVEAU(0): Output DVI-I-1 is running on CRTC 1 using output C
(II) NOUVEAU(0): DPMS enabled
(II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 434 x 270
resize called 1024 768
(II) config/hal: Adding input device   USB Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event4"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device   USB Keyboard
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event3"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event5"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) NOUVEAU(0): EDID for output DVI-I-0
(II) NOUVEAU(0): Manufacturer: GSM  Model: 4e40  Serial#: 179771
(II) NOUVEAU(0): Year: 2006  Week: 2
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): GTF timings supported
(II) NOUVEAU(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.615
(II) NOUVEAU(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x870@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 85 Hz, H min: 28 H max: 83 kHz, PixClock max 140 MHz
(II) NOUVEAU(0): Monitor name: L203WTX
(II) NOUVEAU(0): Monitor name: 
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff001e6d404e3bbe0200
(II) NOUVEAU(0): 	02100103ee2b1b78eac605a3574a9d25
(II) NOUVEAU(0): 	125054a76b808180714f615945593140
(II) NOUVEAU(0): 	0101010101017c2e90a0601a1e403020
(II) NOUVEAU(0): 	3600b20e1100001a000000fd0038551c
(II) NOUVEAU(0): 	530e000a202020202020000000fc004c
(II) NOUVEAU(0): 	3230335754580a2020202020000000fc
(II) NOUVEAU(0): 	000a2020202020202020202020200099
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Printing probed modes for output DVI-I-0
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): Manufacturer: SNY  Model: 5401  Serial#: 16843009
(II) NOUVEAU(0): Year: 2008  Week: 1
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NOUVEAU(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 57 V max: 63 Hz, H min: 30 H max: 80 kHz, PixClock max 150 MHz
(II) NOUVEAU(0): Monitor name: SONY TV
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff004dd9015401010101
(II) NOUVEAU(0): 	0112010308a05a780a0dc9a057479827
(II) NOUVEAU(0): 	12484c21080081800101010101010101
(II) NOUVEAU(0): 	010101010101023a801871382d40582c
(II) NOUVEAU(0): 	450040846300001e662150b051001b30
(II) NOUVEAU(0): 	4070360040846300001e000000fd0039
(II) NOUVEAU(0): 	3f1e500f000a202020202020000000fc
(II) NOUVEAU(0): 	00534f4e592054560a20202020200080
(II) NOUVEAU(0): EDID vendor "SNY", prod id 21505
(II) NOUVEAU(0): Printing probed modes for output DVI-I-1
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-0
(II) NOUVEAU(0): Manufacturer: GSM  Model: 4e40  Serial#: 179771
(II) NOUVEAU(0): Year: 2006  Week: 2
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): GTF timings supported
(II) NOUVEAU(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.615
(II) NOUVEAU(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x870@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 85 Hz, H min: 28 H max: 83 kHz, PixClock max 140 MHz
(II) NOUVEAU(0): Monitor name: L203WTX
(II) NOUVEAU(0): Monitor name: 
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff001e6d404e3bbe0200
(II) NOUVEAU(0): 	02100103ee2b1b78eac605a3574a9d25
(II) NOUVEAU(0): 	125054a76b808180714f615945593140
(II) NOUVEAU(0): 	0101010101017c2e90a0601a1e403020
(II) NOUVEAU(0): 	3600b20e1100001a000000fd0038551c
(II) NOUVEAU(0): 	530e000a202020202020000000fc004c
(II) NOUVEAU(0): 	3230335754580a2020202020000000fc
(II) NOUVEAU(0): 	000a2020202020202020202020200099
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Printing probed modes for output DVI-I-0
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): Manufacturer: SNY  Model: 5401  Serial#: 16843009
(II) NOUVEAU(0): Year: 2008  Week: 1
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NOUVEAU(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 57 V max: 63 Hz, H min: 30 H max: 80 kHz, PixClock max 150 MHz
(II) NOUVEAU(0): Monitor name: SONY TV
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff004dd9015401010101
(II) NOUVEAU(0): 	0112010308a05a780a0dc9a057479827
(II) NOUVEAU(0): 	12484c21080081800101010101010101
(II) NOUVEAU(0): 	010101010101023a801871382d40582c
(II) NOUVEAU(0): 	450040846300001e662150b051001b30
(II) NOUVEAU(0): 	4070360040846300001e000000fd0039
(II) NOUVEAU(0): 	3f1e500f000a202020202020000000fc
(II) NOUVEAU(0): 	00534f4e592054560a20202020200080
(II) NOUVEAU(0): EDID vendor "SNY", prod id 21505
(II) NOUVEAU(0): Printing probed modes for output DVI-I-1
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-0
(II) NOUVEAU(0): Manufacturer: GSM  Model: 4e40  Serial#: 179771
(II) NOUVEAU(0): Year: 2006  Week: 2
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): GTF timings supported
(II) NOUVEAU(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.615
(II) NOUVEAU(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x870@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 85 Hz, H min: 28 H max: 83 kHz, PixClock max 140 MHz
(II) NOUVEAU(0): Monitor name: L203WTX
(II) NOUVEAU(0): Monitor name: 
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff001e6d404e3bbe0200
(II) NOUVEAU(0): 	02100103ee2b1b78eac605a3574a9d25
(II) NOUVEAU(0): 	125054a76b808180714f615945593140
(II) NOUVEAU(0): 	0101010101017c2e90a0601a1e403020
(II) NOUVEAU(0): 	3600b20e1100001a000000fd0038551c
(II) NOUVEAU(0): 	530e000a202020202020000000fc004c
(II) NOUVEAU(0): 	3230335754580a2020202020000000fc
(II) NOUVEAU(0): 	000a2020202020202020202020200099
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Printing probed modes for output DVI-I-0
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): Manufacturer: SNY  Model: 5401  Serial#: 16843009
(II) NOUVEAU(0): Year: 2008  Week: 1
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NOUVEAU(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 57 V max: 63 Hz, H min: 30 H max: 80 kHz, PixClock max 150 MHz
(II) NOUVEAU(0): Monitor name: SONY TV
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff004dd9015401010101
(II) NOUVEAU(0): 	0112010308a05a780a0dc9a057479827
(II) NOUVEAU(0): 	12484c21080081800101010101010101
(II) NOUVEAU(0): 	010101010101023a801871382d40582c
(II) NOUVEAU(0): 	450040846300001e662150b051001b30
(II) NOUVEAU(0): 	4070360040846300001e000000fd0039
(II) NOUVEAU(0): 	3f1e500f000a202020202020000000fc
(II) NOUVEAU(0): 	00534f4e592054560a20202020200080
(II) NOUVEAU(0): EDID vendor "SNY", prod id 21505
(II) NOUVEAU(0): Printing probed modes for output DVI-I-1
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
resize called 3600 1080
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 1)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): CTRC mode on CRTC 0:
(II) NOUVEAU(0): Modeline "640x480"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Output mode on CRTC 0:
(II) NOUVEAU(0): Modeline "640x480"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): vpll: n 22 m 5 log2p 0
(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): 0xD1FB: Parsing digital output script table
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 0 on tmds encoder (output 1)
(II) NOUVEAU(0): Output DVI-I-0 is running on CRTC 0 using output A
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 2)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): CTRC mode on CRTC 1:
(II) NOUVEAU(0): Modeline "640x480"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Output mode on CRTC 1:
(II) NOUVEAU(0): Modeline "640x480"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): vpll: n 53 m 11 log2p 1
(II) NOUVEAU(0): nv_output_mode_set called for encoder 2
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 2)
(II) NOUVEAU(0): Output DVI-I-1 is running on CRTC 1 using output C
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 1)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): CTRC mode on CRTC 0:
(II) NOUVEAU(0): Modeline "(null)"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Output mode on CRTC 0:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): vpll: n 22 m 5 log2p 0
(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): 0xD1FB: Parsing digital output script table
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 0 on tmds encoder (output 1)
(II) NOUVEAU(0): Output DVI-I-0 is running on CRTC 0 using output A
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 2)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): CTRC mode on CRTC 1:
(II) NOUVEAU(0): Modeline "(null)"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Output mode on CRTC 1:
(II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): vpll: n 11 m 2 log2p 0
(II) NOUVEAU(0): nv_output_mode_set called for encoder 2
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 2)
(II) NOUVEAU(0): Output DVI-I-1 is running on CRTC 1 using output C
(II)   USB Keyboard: Close
(II) UnloadModule: "evdev"
(II)   USB Keyboard: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) NOUVEAU(0): [drm] removed 1 reserved context for kernel
(II) NOUVEAU(0): NVLeaveVT is called.
(II) NOUVEAU(0): Restoring encoders
(II) NOUVEAU(0): 0xD1FB: Parsing digital output script table
(II) NOUVEAU(0): 0xD236: Parsing digital output script table
(II) NOUVEAU(0): Restoring crtcs
(II) NOUVEAU(0): Restoring VGA fonts
(II) NOUVEAU(0): Restoring CRTC_OWNER to 4.
(II) NOUVEAU(0): Closed GPU channel 1
 ddxSigGiveUp: Closing log

____________________________________________

/etc/X11/xorg.conf
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
EndSection


____________________________________________

ldd /usr/bin/glxinfo

	linux-vdso.so.1 =>  (0x00007fff7aada000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0x00007fa457a19000)
	libm.so.6 => /lib/libm.so.6 (0x00007fa457795000)
	libc.so.6 => /lib/libc.so.6 (0x00007fa457426000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007fa4570f0000)
	libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0x00007fa455c93000)
	libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0x00007fa457d10000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007fa455a81000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007fa45587d000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fa457c11000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007fa455661000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007fa45545e000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007fa455259000)

____________________________________________

/usr/bin/lspci -d "10de:*" -v -xxx

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [40] HyperTransport: Host or Secondary Interface
00: de 10 a3 03 06 00 b0 00 a2 00 00 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 00 00 00
40: 08 00 01 20 22 00 00 00 10 32 3f 00 03 01 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 21 49 44 44 13 01 00 00 00 00 00 00 10 00 00 00
70: 07 05 22 00 00 00 00 00 81 01 85 01 00 00 00 00
80: 00 00 00 00 00 00 00 00 70 00 00 80 00 00 00 00
90: 1f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 08 00 00 00 00
b0: cb 10 00 02 00 ff 00 00 00 00 00 00 00 00 00 00
c0: 11 11 00 00 00 33 33 13 03 00 00 00 00 50 07 00
d0: 01 0a 00 00 00 00 00 00 ff ff 71 07 10 00 00 00
e0: 08 00 01 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
f0: 00 e4 ff ff 00 00 00 00 00 00 00 00 00 00 00 00

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 ac 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 10 00 21 21 16 00 11 11 00 00 04 00 00 00
60: 21 08 12 06 de 8f e1 1f 08 42 48 18 22 8f 00 20
70: 10 32 54 0a 10 00 00 00 20 00 00 00 2f 00 3d 01
80: 00 00 00 00 00 00 00 00 00 00 50 3f 90 7f 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 01 00 00 00 80 f9 fd 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 c7 02 28 00 00 00 00 00 00 00 00 00

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 aa 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 00 00 4d e0 20 c1 00 00 02 00 4d e0 12 00
50: 00 00 00 00 4d 20 e0 be 01 00 00 00 48 20 d1 be
60: 62 00 10 ce ff ff 00 00 01 00 02 00 ff ff 00 00
70: 02 00 01 00 32 00 10 80 03 2c 1c 80 03 2c 1c 00
80: 00 00 00 80 01 00 00 00 77 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 01 20 00 71 00 00 00 00 31 65 07 00
c0: ff ff ff ff ff bf ff ff 00 00 00 00 77 80 77 00
d0: 00 21 09 00 01 00 00 00 00 00 00 00 00 00 00 00
e0: 80 00 63 00 92 14 00 00 80 00 49 91 64 02 13 00
f0: 1b 1b 1b 1b 00 ff 21 00 99 99 aa aa 00 00 0f 80

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0
00: de 10 a9 03 06 00 a0 00 a1 00 00 05 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 04 20 1c 90 04 20 1c a0
50: 04 18 1c 90 04 20 1c 90 04 28 1c 90 04 18 1c 80
60: 04 20 1c 80 04 28 1c 80 04 30 1c 80 04 38 1c 80
70: 02 20 1c 80 3f 41 30 c0 00 00 00 00 3e 30 40 c9
80: 01 00 00 00 45 30 47 c9 02 1f 1c 80 40 10 00 40
90: 8d da 01 09 00 00 00 00 11 00 00 00 00 00 00 00
a0: 00 00 80 99 80 00 00 00 19 00 a8 61 00 00 00 00
b0: 00 00 00 00 d6 1e 00 00 00 00 02 00 01 8c 01 8c
c0: ff ff ff ff 00 00 00 00 10 00 00 00 00 00 00 00
d0: 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 10 10 18 00 00 40 01 00 00 00 00 00 00 00

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0
00: de 10 ab 03 06 00 a0 00 a1 00 00 05 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 22 88 10 04 22 80 02 0a a0 00 02 0a a1 10 42 0a
60: 85 08 11 08 84 08 31 02 22 90 b5 18 8c 31 a5 1c
70: 6b a5 b4 12 29 31 51 08 85 10 63 0a a5 90 52 0c
80: 87 18 53 0c 62 04 31 08 00 00 00 00 00 00 00 00
90: 20 80 01 00 43 08 01 00 00 00 00 00 00 00 00 00
a0: 06 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 10 00 00 00 00 00
e0: 01 00 00 00 22 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
00: de 10 a8 03 04 00 a0 00 a2 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 10 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b5 03 02 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 f0 0f 3f 00 00 00 00 00 00 00 00 00 00 00 00
50: 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b4 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 11 00 00 00
50: 00 00 00 00 60 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: ff ff ff ff ff ff ff ff 10 21 00 00 ac 00 20 00
c0: 10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 ad 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 01 00 00 3f 44 04 00 00 00 00 00 00 00 00 00
50: 08 f8 f0 a0 0c 0c 04 7e 0c 00 00 00 02 2b 7f 04
60: 65 00 52 00 00 00 00 00 00 00 00 00 33 00 20 00
70: 47 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 3f 63 00 00 00 02 00 00 00 00 00 00 00 2a 0c 55
90: 35 c9 23 30 60 a5 95 45 0d 2e 22 76 03 05 33 0e
a0: 00 00 15 15 f0 11 03 00 20 00 27 12 00 00 00 00
b0: 00 80 00 80 00 80 00 80 00 80 00 80 00 80 00 80
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 31 26 61 24 31 26 61 24 31 26 61 24 31 26 61 24
e0: 03 00 00 00 10 08 71 0f f1 01 00 00 11 11 70 11
f0: 10 18 ff 08 08 10 03 04 01 00 00 00 63 03 77 40

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 ae 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 ff ff 07 00 00 00 00 00 57 f2 00 80
60: 01 01 00 00 10 10 00 00 01 01 00 00 10 10 00 00
70: 01 10 a0 ee 00 00 00 00 01 10 a0 ee 00 00 00 00
80: 01 08 00 13 23 40 f0 03 18 28 80 00 20 60 70 00
90: 13 00 00 18 13 20 00 08 00 20 00 08 00 20 00 08
a0: 00 20 00 08 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 0c 30 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 1b 06 82 81 20 00 00 00 01 01 00 00
d0: 5a 08 00 01 04 00 10 00 00 00 20 00 00 00 30 00
e0: ed 05 c0 4d 5b 05 55 96 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 af 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: d0 00 00 00 00 00 00 00 78 1e 50 84 cb 02 00 06
50: 44 00 00 00 43 00 08 11 ff ff ff ff ff ff 7f ff
60: ff ff 03 04 0e 00 00 00 28 80 78 00 00 00 00 00
70: 01 01 01 01 08 00 b1 3c 0a 22 07 07 50 00 f2 02
80: 95 13 00 00 21 f2 ce fb e1 00 50 00 00 00 00 00
90: 08 00 3f 70 08 00 1f 0c 08 0f 17 00 08 0f 18 00
a0: 50 00 00 00 30 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: ff ff 00 02 00 00 00 00 00 00 00 00 00 00 00 00

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b0 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 31 51 00 00 66 66 00 00 66 66 00 00 66 66 00 00
70: 66 66 00 00 66 66 00 00 66 66 00 00 ff ff ff ff
80: ff ff dd bb 00 30 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 55 55 55 55 55 55 55 55 99 99 99 99
a0: 22 22 22 22 ae 0a e0 00 08 09 0e 0f 08 09 09 08
b0: 09 09 0b 0c 0b 09 08 08 00 01 02 00 00 07 00 00
c0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
d0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
e0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
f0: 00 07 00 00 00 07 00 00 00 07 00 00 00 00 00 00

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b1 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 73 7f 00 00 ff ff 03 00 98 3a 30 80 80 01 00 02
50: 00 00 00 00 1f 1f 00 00 0f 0f 0f 0f f0 f1 41 00
60: 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f f0 f1 41 00
70: 0f 0f 0f 0f 0f 0f 0f 0f 07 00 00 00 0f 0f 00 00
80: 0f 0f 00 00 f0 f1 41 00 0f 0f 0f 0f 0f 0f 0f 0f
90: 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f
a0: 0f 0f 0f 0f f0 f1 41 02 0f 0f 0f 0f 0f 0f 0f 0f
b0: 09 06 00 00 44 44 44 11 44 44 44 44 44 44 44 00
c0: 00 00 00 04 00 00 00 04 00 00 00 00 00 00 00 00
d0: 00 00 00 00 0f 0f 00 00 0f 0f 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 44 00 00 00 44 00 00 00
f0: ff ff 00 02 00 00 00 00 0f 0f 0f 0f 0f 0f 0f 0f

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b2 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: f9 01 a0 0a 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b3 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 55 55 55 55 00 00 00 00 55 55 55 55
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 07 00 00 00 07 00 00
80: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
90: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
a0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
b0: 00 07 00 00 00 07 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 07 07 07 07 88 88 88 88 88 88 88 88
d0: 00 00 00 00 00 00 00 00 40 40 40 40 88 88 77 00
e0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
f0: 00 00 00 00 88 88 88 88 88 88 88 88 00 01 02 00

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b6 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 08 00 00 00 00 20 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 9a e3 bd 1f ca 5d 4f 0c 76 1b e6 c9 92 f1 22 75
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0
00: de 10 bc 03 06 00 a0 00 a1 00 00 05 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 ba 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: ff ff 0f 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 44 44 44 11 44 44 44 44 44 44 44 00 00 00 00 04
a0: 00 00 00 04 00 00 00 00 00 00 00 00 00 00 00 00
b0: 44 44 44 00 44 04 44 04 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 44 44 44 00 44 04 44 04
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 40 40 40 40 40 40 40 40 40 40 40 40 40 40 40 40
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f5f00000-f7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Subsystem: nVidia Corporation Device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00: de 10 b7 03 07 04 10 00 a1 00 04 06 10 00 01 00
10: 00 00 00 00 00 00 00 00 00 01 01 00 d1 d1 00 00
20: f0 f5 f0 f7 01 d0 f1 df 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 00 1a 00
40: 0d 48 00 00 de 10 55 0c 01 50 02 f8 00 00 00 00
50: 05 60 83 00 0c 30 e0 fe 00 00 00 00 49 41 00 00
60: 08 80 00 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 10 00 41 01 01 80 00 00 10 28 00 00 01 35 11 00
90: 00 00 01 31 00 00 00 00 c0 01 48 01 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Subsystem: nVidia Corporation Device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00: de 10 b9 03 04 04 10 00 a1 00 04 06 10 00 01 00
10: 00 00 00 00 00 00 00 00 00 02 02 00 f1 01 00 00
20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 00 02 00
40: 0d 48 00 00 de 10 55 0c 01 50 02 f8 00 00 00 00
50: 05 60 83 00 0c 30 e0 fe 00 00 00 00 51 41 00 00
60: 08 80 00 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 10 00 41 01 01 80 00 00 10 28 00 00 11 34 11 03
90: 10 00 11 10 00 00 00 00 c0 01 49 01 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Subsystem: nVidia Corporation Device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00: de 10 bb 03 04 04 10 00 a1 00 04 06 10 00 01 00
10: 00 00 00 00 00 00 00 00 00 03 03 00 f1 01 00 00
20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 00 02 00
40: 0d 48 00 00 de 10 55 0c 01 50 02 f8 00 00 00 00
50: 05 60 83 00 0c 30 e0 fe 00 00 00 00 59 41 00 00
60: 08 80 00 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 10 00 41 01 01 80 00 00 10 28 00 00 11 34 11 02
90: 00 00 11 10 00 00 00 00 c0 01 48 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping Enable- Fixed-
00: de 10 70 02 06 00 b0 00 a2 00 00 05 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 00 00 00 00
40: 62 14 50 73 08 e0 e9 01 22 20 00 00 d0 00 00 00
50: 23 00 7f 80 03 00 00 00 00 00 03 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 06 06 05 00
70: 44 44 44 00 50 01 00 00 11 00 00 00 11 11 55 00
80: 23 55 55 00 fa 00 64 0c 03 00 00 00 7f 00 00 00
90: 70 00 00 80 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 01 01 01 01 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 80 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 08 00 00 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=128]
00: de 10 60 02 0f 00 a0 00 a3 00 01 06 00 00 80 00
10: 01 4f 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 62 14 50 73 00 00 d0 fe fa 3e ff 00 fa 3e ff 00
50: fa 3e ff 00 00 5a 62 02 00 00 00 01 00 00 fe bf
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f9 ff
70: 10 00 ff ff cd 00 00 00 00 00 04 19 60 00 0c 00
80: 09 d0 00 12 08 01 00 00 c0 00 00 01 00 00 00 00
90: 00 00 00 00 00 00 00 00 21 47 65 b7 ef cd 00 00
a0: 01 00 10 80 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 0a 7f 0a 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 02 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 5000 [size=64]
	I/O ports at 6000 [size=64]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2
00: de 10 64 02 01 00 b0 00 a3 00 05 0c 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 50 00 00 01 60 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 00 00
40: 62 14 50 73 01 00 02 c0 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 01 40 00 00 01 44 00 00 01 48 00 00 00 00 00 00
70: 01 00 00 00 00 00 00 00 00 00 00 00 01 20 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: d4 30 80 01 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 10 10 04 00 00 a0 00 00 80 38 00 00 46 44 44 11
f0: 5a ff 5f bf 00 00 00 c0 10 00 00 00 00 00 00 00

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: 66MHz, fast devsel
00: de 10 72 02 00 04 a0 00 a3 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 00 00 00 00 00 00 10 00 00 10 00 00 10 10
50: 10 10 10 10 00 00 00 00 00 00 00 00 00 00 00 00
60: 02 03 00 00 12 00 00 00 02 00 00 00 10 01 12 00
70: 32 33 00 00 03 00 00 00 00 00 00 00 12 01 00 00
80: 10 00 00 00 00 00 00 00 00 00 00 00 30 02 00 00
90: 00 00 00 00 01 20 00 00 01 00 00 00 00 09 00 00
a0: 01 02 00 00 00 10 00 00 05 00 00 00 01 00 00 00
b0: 00 10 00 80 01 00 00 80 00 00 00 00 02 00 00 00
c0: 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f5eff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
00: de 10 6d 02 07 00 b0 00 a3 10 03 0c 00 00 80 00
10: 00 f0 ef f5 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 05 01 03 01
40: 62 14 50 73 01 00 02 fe 00 00 00 00 00 00 00 00
50: 18 00 00 00 1d 47 40 00 10 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f5efec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd
00: de 10 6e 02 06 00 b0 00 a3 20 03 0c 00 00 80 00
10: 00 ec ef f5 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 07 02 03 01
40: 62 14 50 73 0a 80 98 20 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 20 20 01 00 00 60 18 85 03 3c 0a 01 00 00 00 00
70: 00 00 08 05 00 10 20 80 89 3d b6 22 77 25 84 00
80: 01 00 02 fe 00 00 00 00 00 00 00 00 15 16 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 01 00 00 00 00 00 08 c0 00 00 00 00 00 00 00 00
b0: 33 00 11 22 00 00 00 00 ff 00 00 00 00 00 00 00
c0: 10 10 2d 0d 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd
00: de 10 65 02 05 00 b0 00 a1 8a 01 01 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: a1 ff 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 00 00 03 01
40: 62 14 50 73 01 00 02 00 00 00 00 00 00 00 00 00
50: 03 f0 01 00 00 00 00 00 99 20 99 20 22 00 20 20
60: 00 c6 00 c0 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 5e 20 00 00 04 10 00 20 7a 20
90: 00 00 02 14 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at c800 [size=8]
	I/O ports at c480 [size=4]
	I/O ports at c400 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c000 [size=16]
	Memory at f5efd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: sata_nv
00: de 10 66 02 07 00 b0 00 a1 85 01 01 00 00 00 00
10: 01 c8 00 00 81 c4 00 00 01 c4 00 00 81 c0 00 00
20: 01 c0 00 00 00 d0 ef f5 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 0a 01 03 01
40: 62 14 50 73 01 b0 02 00 00 00 00 00 00 00 00 00
50: 07 00 00 00 00 00 00 00 00 00 00 20 40 00 00 20
60: 00 00 00 c7 51 0c 00 00 00 0f 06 42 00 00 00 00
70: 2c 78 c4 40 01 10 00 00 01 10 00 00 20 00 20 00
80: 00 00 00 c0 00 10 ab bf 00 00 c0 80 9f a4 93 c2
90: 00 00 a1 13 00 00 00 00 06 00 06 10 00 00 01 01
a0: 14 10 00 2b 00 00 00 00 00 00 00 00 33 33 00 02
b0: 05 cc 84 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 0a 00 0a 00 08 00 02 a8
d0: 0a 00 02 0c 42 00 00 00 00 00 00 00 00 00 10 e0
e0: 0a 00 02 0a 42 00 00 00 00 00 00 00 0f 00 10 00
f0: 00 00 00 00 00 00 00 00 00 00 0c 00 00 00 00 00

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at bc00 [size=8]
	I/O ports at b880 [size=4]
	I/O ports at b800 [size=8]
	I/O ports at b480 [size=4]
	I/O ports at b400 [size=16]
	Memory at f5efc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: sata_nv
00: de 10 67 02 07 00 b0 00 a1 85 01 01 00 00 00 00
10: 01 bc 00 00 81 b8 00 00 01 b8 00 00 81 b4 00 00
20: 01 b4 00 00 00 c0 ef f5 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 03 01
40: 62 14 50 73 01 b0 02 00 00 00 00 00 00 00 00 00
50: 07 00 00 00 00 00 00 00 00 20 00 20 44 20 00 20
60: 00 c6 00 c7 51 0c 00 00 00 0f 06 42 00 00 00 00
70: 2c 78 c4 40 01 10 00 00 01 10 00 00 20 00 20 00
80: 00 00 00 c0 00 c0 7b 20 00 00 08 a0 00 70 46 20
90: 00 00 10 b0 00 00 00 00 06 00 06 10 00 00 01 01
a0: 14 10 00 2b 00 00 00 00 00 00 00 00 33 33 00 02
b0: 05 cc 84 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 0a 00 0a 00 08 00 02 a8
d0: 0a 00 02 0c 42 00 00 00 00 00 00 00 0f 00 f0 e7
e0: 0a 00 02 0a 42 00 00 00 00 00 00 00 00 00 d0 86
f0: 00 00 00 00 00 00 00 00 00 00 0c 00 00 00 00 00

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f8000000-febfffff
	Capabilities: [b8] Subsystem: nVidia Corporation Device cb84
	Capabilities: [8c] HyperTransport: MSI Mapping Enable- Fixed-
00: de 10 6f 02 07 00 b0 00 a2 01 04 06 00 00 81 00
10: 00 00 00 00 00 00 00 00 00 04 04 40 e0 e0 80 02
20: 00 f8 b0 fe f0 ff 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 b8 00 00 00 00 00 00 00 00 00 02 02
40: 00 00 03 00 01 00 02 00 05 00 00 00 00 00 4c 00
50: 00 00 fe bf 00 00 00 00 fe 1f ff 1f 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 fe 3f 01 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 08 00 00 a8
90: 00 00 e0 fe 00 00 00 00 00 00 00 00 00 00 00 00
a0: 06 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 ff ff 00 00 0d 8c 00 00 de 10 84 cb
c0: de 10 84 cb 03 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f5efb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at b080 [size=8]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
00: de 10 69 02 07 00 b0 00 a3 00 80 06 00 00 00 00
10: 00 b0 ef f5 81 b0 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 05 01 01 14
40: 62 14 50 73 01 00 02 fe 00 01 00 00 0b 00 00 10
50: 05 6c 84 01 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 0f 00 00 00 08 00 02 a8
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 11 00 00 00 42 01 00 00 00 00 00 00

01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)
	Subsystem: eVga.com. Corp. Device c553
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f6000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at f5fe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Kernel driver in use: nvidia
	Kernel modules: nouveau, nvidia, nvidiafb
00: de 10 91 03 07 00 10 00 a1 00 00 03 00 00 00 00
10: 00 00 00 f7 0c 00 00 d0 00 00 00 00 04 00 00 f6
20: 00 00 00 00 01 dc 00 00 00 00 00 00 42 38 53 c5
30: 00 00 00 00 60 00 00 00 00 00 00 00 0a 01 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 01 00 00 00 01 00 00 00 ce d6 23 00 00 00 00 00
60: 01 68 02 00 00 00 00 00 05 78 80 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 10 00 01 00 00 05 00 00
80: 10 28 00 00 01 4d 01 00 08 00 01 11 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


____________________________________________

/usr/bin/lspci -t

-[0000:00]-+-00.0
           +-00.1
           +-00.2
           +-00.3
           +-00.4
           +-00.5
           +-00.6
           +-00.7
           +-01.0
           +-01.1
           +-01.2
           +-01.3
           +-01.4
           +-01.5
           +-01.6
           +-02.0
           +-02.1
           +-02.2
           +-03.0-[0000:01]----00.0
           +-06.0-[0000:02]--
           +-07.0-[0000:03]--
           +-09.0
           +-0a.0
           +-0a.1
           +-0a.2
           +-0b.0
           +-0b.1
           +-0d.0
           +-0e.0
           +-0f.0
           +-10.0-[0000:04]----07.0
           \-14.0

____________________________________________

/usr/sbin/dmidecode

# dmidecode 2.9
SMBIOS 2.5 present.
54 structures occupying 1991 bytes.
Table at 0x000FB4F0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: V1.7
	Release Date: 07/29/2008
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.13

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: MSI
	Product Name: MS-7350
	Version: 1.0
	Serial Number: To Be Filled By O.E.M.
	UUID: Not Present
	Wake-up Type: Power Switch
	SKU Number: To Be Filled By O.E.M.
	Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: MSI
	Product Name: MS-7350
	Version: 1.0
	Serial Number: To be filled by O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: To Be Filled By O.E.M.
	Type: Desktop
	Lock: Not Present
	Version: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Other
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Unknown
	Manufacturer: Intel            
	ID: F2 06 00 00 FF FB EB BF
	Version: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz     
	Voltage: 1.3 V
	External Clock: 267 MHz
	Max Speed: 1866 MHz
	Current Speed: 1869 MHz
	Status: Populated, Enabled
	Upgrade: Socket 478
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 2
	Core Enabled: 2
	Thread Count: 2
	Characteristics:
		64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 2048 KB
	Maximum Size: 2048 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Disabled, Not Socketed, Level 3
	Operational Mode: Unknown
	Location: Internal
	Installed Size: 0 KB
	Maximum Size: 0 KB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0008, DMI type 5, 24 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 4096 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		SIMM
		DIMM
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 4
		0x0009
		0x000A
		0x000B
		0x000C
	Enabled Error Correcting Capabilities:
		None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 1 0
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM3
	Bank Connections: 3 2
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM2
	Bank Connections: 5 4
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM4
	Bank Connections: 7 6
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS2Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4A1
	Internal Connector Type: None
	External Reference Designator: LPT 1
	External Connector Type: DB-25 male
	Port Type: Parallel Port ECP/EPP

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A1
	Internal Connector Type: None
	External Reference Designator: COM A
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Mic In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Line In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6B1 - AUX IN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6B2 - CDIN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J2 - PRI IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J1 - SEC IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4J1 - FLOPPY
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H1 - FRONT PNL
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1B1 - CHASSIS REAR FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2F1 - CPU FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8B4 - FRONT FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G2 - FNT USB
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6C3 - FP AUD
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G1 - CONFIG
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8C1 - SCSI LED
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9J2 - INTRUDER
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G4 - ITP
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2H1 - MAIN POWER
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0025, DMI type 9, 13 bytes
System Slot Information
	Designation: PCIE
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Short
	ID: 0
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0026, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0027, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:   To Be Filled By O.E.M.

Handle 0x0028, DMI type 11, 5 bytes
OEM Strings
	String 1: To Be Filled By O.E.M.

Handle 0x0029, DMI type 12, 5 bytes
System Configuration Options
	Option 1: To Be Filled By O.E.M.

Handle 0x002A, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x002B, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 16 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x002C, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Array Handle: 0x002B
	Partition Width: 0

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK0
	Type: SDRAM
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x002E, DMI type 126, 19 bytes
Inactive

Handle 0x002F, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM3
	Bank Locator: BANK1
	Type: SDRAM
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

Handle 0x0030, DMI type 126, 19 bytes
Inactive

Handle 0x0031, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK2
	Type: SDRAM
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer2
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: PartNum2

Handle 0x0032, DMI type 126, 19 bytes
Inactive

Handle 0x0033, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM4
	Bank Locator: BANK3
	Type: SDRAM
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer3
	Serial Number: SerNum3
	Asset Tag: AssetTagNum3
	Part Number: PartNum3

Handle 0x0034, DMI type 126, 19 bytes
Inactive

Handle 0x0035, DMI type 127, 4 bytes
End Of Table


____________________________________________

/sbin/modinfo nvidia | grep vermagic

vermagic:       2.6.31-14-generic SMP mod_unload modversions 

____________________________________________

Scanning kernel log files for NVRM messages:

  /var/log/messages:
Oct 25 22:29:31 charles-pc kernel: [  883.996998] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
Oct 25 22:32:01 charles-pc kernel: [    7.161051] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
Oct 25 22:33:52 charles-pc kernel: [    6.636208] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
Oct 27 10:43:52 charles-pc kernel: [   11.958000] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 10:46:00 charles-pc kernel: [    6.634315] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 10:48:48 charles-pc kernel: [    5.496438] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 10:49:54 charles-pc kernel: [    5.900681] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 13:30:36 charles-pc kernel: [    6.423969] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 13:36:03 charles-pc kernel: [    6.769397] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 13:37:37 charles-pc kernel: [    6.484657] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 13:41:59 charles-pc kernel: [   11.554507] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 14:30:02 charles-pc kernel: [    6.455250] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
/var/log/kernel.log is not readable

____________________________________________

dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffc0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffc0000 - 00000000bffce000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffce000 - 00000000c0000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbffc0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009b000 (usable)
[    0.000000]  modified: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bffc0000 (usable)
[    0.000000]  modified: 00000000bffc0000 - 00000000bffce000 (ACPI data)
[    0.000000]  modified: 00000000bffce000 - 00000000c0000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bffc0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bffc0000 page 4k
[    0.000000] kernel direct mapping tables up to bffc0000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 13000-19000
[    0.000000] RAMDISK: 3786f000 - 37fefd5f
[    0.000000] ACPI: RSDP 00000000000f8f30 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bffc0000 0003C (v01 A M I  OEMRSDT  07000829 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bffc0200 00084 (v02 A M I  OEMFACP  07000829 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bffc0450 0480B (v01  1ADKV 1ADKV000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bffce000 00040
[    0.000000] ACPI: APIC 00000000bffc0390 00080 (v01 A M I  OEMAPIC  07000829 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bffc0410 0003C (v01 A M I  OEMMCFG  07000829 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bffce040 00061 (v01 A M I  AMI_OEM  07000829 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bffc4c60 00038 (v01 A M I  OEMHPET0 07000829 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bffce4b0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]
[    0.000000]   bootmap [0000000000019000 -  0000000000040fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003786f000 - 0037fefd5f]          RAMDISK ==> [003786f000 - 0037fefd5f]
[    0.000000]   #4 [000009b000 - 0000100000]    BIOS reserved ==> [000009b000 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3180]              BRK ==> [00019e3000 - 00019e3180]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 0000014000]          PGTABLE ==> [0000013000 - 0000014000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000bffc0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048395
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 108 pages reserved
[    0.000000]   DMA zone: 3815 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767992 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bffc0000 - 00000000bffce000
[    0.000000] PM: Registered nosave memory: 00000000bffce000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff80000
[    0.000000] PM: Registered nosave memory: 00000000fff80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ec00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030367
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4051756k/5242880k available (5313k kernel code, 1049300k absent, 141824k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1866.630 MHz processor.
[    0.000015] spurious 8259A interrupt: IRQ7.
[    0.001268] Console: colour VGA+ 80x25
[    0.001271] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3733.26 BogoMIPS (lpj=18666300)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM1)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.012464] Setting APIC routing to flat
[    0.013005] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.113032] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3733.35 BogoMIPS (lpj=18666757)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM1)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.271127] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[    0.271138] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280019] Brought up 2 CPUs
[    0.280023] Total of 2 processors activated (7466.61 BogoMIPS).
[    0.280129] CPU0 attaching sched-domain:
[    0.280132]  domain 0: span 0-1 level MC
[    0.280135]   groups: 0 1
[    0.280141] CPU1 attaching sched-domain:
[    0.280143]  domain 0: span 0-1 level MC
[    0.280145]   groups: 1 0
[    0.280217] Booting paravirtualized kernel on bare hardware
[    0.280217] regulator: core version 0.5
[    0.280217] Time: 18:29:44  Date: 10/27/09
[    0.280217] NET: Registered protocol family 16
[    0.280230] ACPI: bus type pci registered
[    0.280301] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.280304] PCI: Not using MMCONFIG.
[    0.280306] PCI: Using configuration type 1 for base access
[    0.281236] bio: create slab <bio-0> at 0
[    0.281236] ACPI: EC: Look up EC in DSDT
[    0.292181] ACPI: Interpreter enabled
[    0.292185] ACPI: (supports S0 S1 S3 S4 S5)
[    0.292209] ACPI: Using IOAPIC for interrupt routing
[    0.292260] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.296648] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.304177] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.312028] ACPI Warning: Incorrect checksum in table [OEMB] - E1, should be E0 20090521 tbutils-246
[    0.312164] ACPI: No dock devices found.
[    0.312747] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.313667] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313671] pci 0000:00:03.0: PME# disabled
[    0.313727] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313731] pci 0000:00:06.0: PME# disabled
[    0.313783] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313786] pci 0000:00:07.0: PME# disabled
[    0.314043] pci 0000:00:0a.0: reg 10 io port: [0x4f00-0x4f7f]
[    0.314158] pci 0000:00:0a.1: reg 20 io port: [0x5000-0x503f]
[    0.314167] pci 0000:00:0a.1: reg 24 io port: [0x6000-0x603f]
[    0.314205] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.314213] pci 0000:00:0a.1: PME# disabled
[    0.314337] pci 0000:00:0b.0: reg 10 32bit mmio: [0xf5eff000-0xf5efffff]
[    0.314396] pci 0000:00:0b.0: supports D1 D2
[    0.314399] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.314404] pci 0000:00:0b.0: PME# disabled
[    0.314454] pci 0000:00:0b.1: reg 10 32bit mmio: [0xf5efec00-0xf5efecff]
[    0.314520] pci 0000:00:0b.1: supports D1 D2
[    0.314522] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.314527] pci 0000:00:0b.1: PME# disabled
[    0.314607] pci 0000:00:0d.0: reg 20 io port: [0xffa0-0xffaf]
[    0.314696] pci 0000:00:0e.0: reg 10 io port: [0xc800-0xc807]
[    0.314704] pci 0000:00:0e.0: reg 14 io port: [0xc480-0xc483]
[    0.314712] pci 0000:00:0e.0: reg 18 io port: [0xc400-0xc407]
[    0.314720] pci 0000:00:0e.0: reg 1c io port: [0xc080-0xc083]
[    0.314729] pci 0000:00:0e.0: reg 20 io port: [0xc000-0xc00f]
[    0.314737] pci 0000:00:0e.0: reg 24 32bit mmio: [0xf5efd000-0xf5efdfff]
[    0.314838] pci 0000:00:0f.0: reg 10 io port: [0xbc00-0xbc07]
[    0.314846] pci 0000:00:0f.0: reg 14 io port: [0xb880-0xb883]
[    0.314854] pci 0000:00:0f.0: reg 18 io port: [0xb800-0xb807]
[    0.314862] pci 0000:00:0f.0: reg 1c io port: [0xb480-0xb483]
[    0.314870] pci 0000:00:0f.0: reg 20 io port: [0xb400-0xb40f]
[    0.314878] pci 0000:00:0f.0: reg 24 32bit mmio: [0xf5efc000-0xf5efcfff]
[    0.315062] pci 0000:00:14.0: reg 10 32bit mmio: [0xf5efb000-0xf5efbfff]
[    0.315071] pci 0000:00:14.0: reg 14 io port: [0xb080-0xb087]
[    0.315121] pci 0000:00:14.0: supports D1 D2
[    0.315123] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.315129] pci 0000:00:14.0: PME# disabled
[    0.315188] pci 0000:01:00.0: reg 10 32bit mmio: [0xf7000000-0xf7ffffff]
[    0.315197] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.315206] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf6000000-0xf6ffffff]
[    0.315212] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.315218] pci 0000:01:00.0: reg 30 32bit mmio: [0xf5fe0000-0xf5ffffff]
[    0.315308] pci 0000:00:03.0: bridge io port: [0xd000-0xdfff]
[    0.315312] pci 0000:00:03.0: bridge 32bit mmio: [0xf5f00000-0xf7ffffff]
[    0.315317] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.315531] pci 0000:04:07.0: reg 10 io port: [0xec00-0xec1f]
[    0.315547] pci 0000:04:07.0: reg 14 64bit mmio: [0xfea00000-0xfebfffff]
[    0.315563] pci 0000:04:07.0: reg 1c 64bit mmio: [0xf8000000-0xfbffffff]
[    0.315610] pci 0000:04:07.0: supports D1 D2
[    0.315668] pci 0000:00:10.0: transparent bridge
[    0.315673] pci 0000:00:10.0: bridge io port: [0xe000-0xefff]
[    0.315677] pci 0000:00:10.0: bridge 32bit mmio: [0xf8000000-0xfebfffff]
[    0.315700] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.315941] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.316069] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.316137] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PB._PRT]
[    0.316202] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.329031] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.329243] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *10
[    0.329448] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.329654] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.329858] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10
[    0.330081] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.330286] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.330491] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.330695] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.330898] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *7
[    0.331110] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.331320] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.331524] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.331728] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.331932] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.332135] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.332339] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[    0.332549] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *11
[    0.332795] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.332982] SCSI subsystem initialized
[    0.333012] libata version 3.00 loaded.
[    0.333012] usbcore: registered new interface driver usbfs
[    0.333012] usbcore: registered new interface driver hub
[    0.333012] usbcore: registered new device driver usb
[    0.333012] ACPI: WMI: Mapper loaded
[    0.333012] PCI: Using ACPI for IRQ routing
[    0.360009] Bluetooth: Core ver 2.15
[    0.360027] NET: Registered protocol family 31
[    0.360027] Bluetooth: HCI device and connection manager initialized
[    0.360027] Bluetooth: HCI socket layer initialized
[    0.360027] NetLabel: Initializing
[    0.360027] NetLabel:  domain hash size = 128
[    0.360027] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.360043] NetLabel:  unlabeled traffic allowed by default
[    0.360110] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.360117] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.400092] pnp: PnP ACPI init
[    0.400106] ACPI: bus type pnp registered
[    0.404563] pnp: PnP ACPI: found 14 devices
[    0.404566] ACPI: ACPI bus type pnp unregistered
[    0.404580] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.404583] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.404586] system 00:06: ioport range 0x4000-0x407f has been reserved
[    0.404589] system 00:06: ioport range 0x4080-0x40ff has been reserved
[    0.404592] system 00:06: ioport range 0x4400-0x447f has been reserved
[    0.404595] system 00:06: ioport range 0x4480-0x44ff has been reserved
[    0.404599] system 00:06: ioport range 0x4800-0x487f has been reserved
[    0.404602] system 00:06: ioport range 0x4880-0x48ff has been reserved
[    0.404608] system 00:06: ioport range 0x2000-0x207f has been reserved
[    0.404611] system 00:06: ioport range 0x2080-0x20ff has been reserved
[    0.404615] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.404622] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.404625] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.404632] system 00:0b: ioport range 0xa00-0xadf has been reserved
[    0.404635] system 00:0b: ioport range 0xae0-0xaef has been reserved
[    0.404640] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.404646] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.404649] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.404653] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.404656] system 00:0d: iomem range 0x100000-0xbfffffff could not be reserved
[    0.404659] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.409371] AppArmor: AppArmor Filesystem Enabled
[    0.409420] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.409423] pci 0000:00:03.0:   IO window: 0xd000-0xdfff
[    0.409427] pci 0000:00:03.0:   MEM window: 0xf5f00000-0xf7ffffff
[    0.409431] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.409436] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.409438] pci 0000:00:06.0:   IO window: disabled
[    0.409441] pci 0000:00:06.0:   MEM window: disabled
[    0.409445] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.409448] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.409450] pci 0000:00:07.0:   IO window: disabled
[    0.409454] pci 0000:00:07.0:   MEM window: disabled
[    0.409457] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.409460] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.409464] pci 0000:00:10.0:   IO window: 0xe000-0xefff
[    0.409470] pci 0000:00:10.0:   MEM window: 0xf8000000-0xfebfffff
[    0.409475] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.409486] pci 0000:00:03.0: setting latency timer to 64
[    0.409493] pci 0000:00:06.0: setting latency timer to 64
[    0.409499] pci 0000:00:07.0: setting latency timer to 64
[    0.409506] pci 0000:00:10.0: setting latency timer to 64
[    0.409511] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.409513] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.409516] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.409519] pci_bus 0000:01: resource 1 mem: [0xf5f00000-0xf7ffffff]
[    0.409522] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.409525] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.409527] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xfebfffff]
[    0.409529] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.409532] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.409569] NET: Registered protocol family 2
[    0.409764] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.411178] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.414784] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.415236] TCP: Hash tables configured (established 524288 bind 65536)
[    0.415239] TCP reno registered
[    0.415366] NET: Registered protocol family 1
[    0.415439] Trying to unpack rootfs image as initramfs...
[    0.501256] Switched to high resolution mode on CPU 1
[    0.510099] Switched to high resolution mode on CPU 0
[    0.611024] Freeing initrd memory: 7683k freed
[    0.614432] Scanning for low memory corruption every 60 seconds
[    0.614583] audit: initializing netlink socket (disabled)
[    0.614600] type=2000 audit(1256668183.610:1): initialized
[    0.625398] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.626936] VFS: Disk quotas dquot_6.5.2
[    0.626998] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.627628] fuse init (API version 7.12)
[    0.627714] msgmni has been set to 7928
[    0.627936] alg: No test for stdrng (krng)
[    0.627951] io scheduler noop registered
[    0.627953] io scheduler anticipatory registered
[    0.627956] io scheduler deadline registered
[    0.627996] io scheduler cfq registered (default)
[    0.640157] pci 0000:01:00.0: Boot video device
[    0.640364]   alloc irq_desc for 24 on node 0
[    0.640366]   alloc kstat_irqs on node 0
[    0.640376] pcieport-driver 0000:00:03.0: irq 24 for MSI/MSI-X
[    0.640382] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    0.640513]   alloc irq_desc for 25 on node 0
[    0.640515]   alloc kstat_irqs on node 0
[    0.640522] pcieport-driver 0000:00:06.0: irq 25 for MSI/MSI-X
[    0.640528] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    0.640658]   alloc irq_desc for 26 on node 0
[    0.640660]   alloc kstat_irqs on node 0
[    0.640666] pcieport-driver 0000:00:07.0: irq 26 for MSI/MSI-X
[    0.640672] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    0.640754] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.640784] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.640915] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.640919] ACPI: Power Button [PWRF]
[    0.640982] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.640985] ACPI: Power Button [PWRB]
[    0.641607] ACPI: SSDT 00000000bffce0b0 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.641901] processor LNXCPU:00: registered as cooling_device0
[    0.642263] ACPI: SSDT 00000000bffce2b0 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.642544] processor LNXCPU:01: registered as cooling_device1
[    0.647275] Linux agpgart interface v0.103
[    0.647284] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.647421] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.647742] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.648854] brd: module loaded
[    0.649318] loop: module loaded
[    0.649391] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.649670] sata_nv 0000:00:0e.0: version 3.5
[    0.649961] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.649965]   alloc irq_desc for 23 on node 0
[    0.649967]   alloc kstat_irqs on node 0
[    0.649973] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.649976] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.650040] sata_nv 0000:00:0e.0: setting latency timer to 64
[    0.650164] scsi0 : sata_nv
[    0.650252] scsi1 : sata_nv
[    0.650394] ata1: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc000 irq 23
[    0.650398] ata2: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xc008 irq 23
[    0.650721] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    0.650724]   alloc irq_desc for 22 on node 0
[    0.650726]   alloc kstat_irqs on node 0
[    0.650731] sata_nv 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    0.650734] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    0.650772] sata_nv 0000:00:0f.0: setting latency timer to 64
[    0.650888] scsi2 : sata_nv
[    0.650952] scsi3 : sata_nv
[    0.651092] ata3: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 22
[    0.651096] ata4: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 22
[    0.651324] pata_amd 0000:00:0d.0: version 0.4.1
[    0.651358] pata_amd 0000:00:0d.0: setting latency timer to 64
[    0.651436] scsi4 : pata_amd
[    0.651499] scsi5 : pata_amd
[    0.653012] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.653015] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.653770] Fixed MDIO Bus: probed
[    0.653804] PPP generic driver version 2.4.2
[    0.653909] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.654234] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.654238]   alloc irq_desc for 21 on node 0
[    0.654240]   alloc kstat_irqs on node 0
[    0.654245] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.654257] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.654261] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.654312] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.654346] ehci_hcd 0000:00:0b.1: debug port 1
[    0.654352] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    0.654372] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xf5efec00
[    0.670050] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.670143] usb usb1: configuration #1 chosen from 1 choice
[    0.670180] hub 1-0:1.0: USB hub found
[    0.670189] hub 1-0:1.0: 8 ports detected
[    0.670277] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.670605] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    0.670608]   alloc irq_desc for 20 on node 0
[    0.670610]   alloc kstat_irqs on node 0
[    0.670615] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.670626] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.670630] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.670663] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.670689] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xf5eff000
[    0.732119] usb usb2: configuration #1 chosen from 1 choice
[    0.732149] hub 2-0:1.0: USB hub found
[    0.732159] hub 2-0:1.0: 8 ports detected
[    0.732239] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732352] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.734292] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.734298] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.734370] mice: PS/2 mouse device common for all mice
[    0.734472] rtc_cmos 00:02: RTC can wake from S4
[    0.734506] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.734545] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.734641] device-mapper: uevent: version 1.0.3
[    0.734725] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.734795] device-mapper: multipath: version 1.1.0 loaded
[    0.734799] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.734968] cpuidle: using governor ladder
[    0.734971] cpuidle: using governor menu
[    0.735377] TCP cubic registered
[    0.735506] NET: Registered protocol family 10
[    0.735964] lo: Disabled Privacy Extensions
[    0.736264] NET: Registered protocol family 17
[    0.736282] Bluetooth: L2CAP ver 2.13
[    0.736285] Bluetooth: L2CAP socket layer initialized
[    0.736288] Bluetooth: SCO (Voice Link) ver 0.6
[    0.736291] Bluetooth: SCO socket layer initialized
[    0.736322] Bluetooth: RFCOMM TTY layer initialized
[    0.736325] Bluetooth: RFCOMM socket layer initialized
[    0.736327] Bluetooth: RFCOMM ver 1.11
[    0.736924] PM: Resume from disk failed.
[    0.736937] registered taskstats version 1
[    0.737088]   Magic number: 13:888:494
[    0.737167] rtc_cmos 00:02: setting system clock to 2009-10-27 18:29:44 UTC (1256668184)
[    0.737170] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.737172] EDD information not available.
[    0.810098] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.811342] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.830793] ata5.00: ATAPI: LITE-ON LTR-48246S, SS0E, max UDMA/33
[    0.830813] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c600) ACPI=0x701f (60:900:0x11)
[    0.831091] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    0.831095] ata3.00: 488397168 sectors, multi 16: LBA48 
[    0.831733] ata1.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    0.831736] ata1.00: 488397168 sectors, multi 16: LBA48 
[    0.871155] ata3.00: configured for UDMA/133
[    0.871183] ata1.00: configured for UDMA/133
[    0.871215] ata5.00: configured for UDMA/33
[    0.871291] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[    0.871412] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.871451] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.871499] sd 0:0:0:0: [sda] Write Protect is off
[    0.871502] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.871528] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.871664]  sda:
[    0.882934] ata2: SATA link down (SStatus 0 SControl 300)
[    0.882972]  sda1 sda2 sda3
[    0.883024] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[    0.883132] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.883167] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.883215] sd 2:0:0:0: [sdb] Write Protect is off
[    0.883218] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.883243] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.883363]  sdb:
[    0.896963] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.898444]  sdb1
[    0.898655] sd 2:0:0:0: [sdb] Attached SCSI disk
[    0.990054] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.040092] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.060353] ata4.00: ATAPI: ATAPI   iHAS422   8, 4L11, max UDMA/100
[    1.100344] ata4.00: configured for UDMA/100
[    1.102786] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS422   8      4L11 PQ: 0 ANSI: 5
[    1.109290] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.109294] Uniform CD-ROM driver Revision: 3.20
[    1.109380] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.109432] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.120141] scsi 4:0:0:0: CD-ROM            LITE-ON  LTR-48246S       SS0E PQ: 0 ANSI: 5
[    1.140838] usb 1-2: configuration #1 chosen from 1 choice
[    1.140936] hub 1-2:1.0: USB hub found
[    1.141031] hub 1-2:1.0: 7 ports detected
[    1.141155] hub 1-2:1.0: insufficient power available to use all downstream ports
[    1.169527] sr1: scsi3-mmc drive: 221x/48x writer cd/rw xa/form2 cdda tray
[    1.169608] sr 4:0:0:0: Attached scsi CD-ROM sr1
[    1.169652] sr 4:0:0:0: Attached scsi generic sg3 type 5
[    1.373299] ata6.00: ATA-7: ST3400620A, 3.AAE, max UDMA/100
[    1.373303] ata6.00: 781422768 sectors, multi 16: LBA48 
[    1.373325] ata6: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc000c600) ACPI=0x3f01f (20:900:0x11)
[    1.465003] ata6.00: configured for UDMA/100
[    1.465083] scsi 5:0:0:0: Direct-Access     ATA      ST3400620A       3.AA PQ: 0 ANSI: 5
[    1.465212] sd 5:0:0:0: [sdc] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    1.465220] sd 5:0:0:0: Attached scsi generic sg4 type 0
[    1.465262] sd 5:0:0:0: [sdc] Write Protect is off
[    1.465265] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.465290] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.465413]  sdc: sdc1
[    1.504857] sd 5:0:0:0: [sdc] Attached SCSI disk
[    1.504884] Freeing unused kernel memory: 660k freed
[    1.505096] Write protecting the kernel read-only data: 7580k
[    1.600020] usb 2-4: new low speed USB device using ohci_hcd and address 2
[    1.630504] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.630839] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    1.630845] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    1.630851] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.630898] nv_probe: set workaround bit for reversed mac addr
[    1.854165] usb 2-4: configuration #1 chosen from 1 choice
[    1.863013] usbcore: registered new interface driver hiddev
[    1.876428] input:   USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input3
[    1.876493] generic-usb 0003:1241:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:0b.0-4/input0
[    1.901149] input:   USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.1/input/input4
[    1.901211] generic-usb 0003:1241:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:0b.0-4/input1
[    1.901229] usbcore: registered new interface driver usbhid
[    1.901232] usbhid: v2.6:USB HID core driver
[    2.161179] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:19:db:4c:cf:40
[    2.161184] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    2.190418] usb 2-5: new low speed USB device using ohci_hcd and address 3
[    2.448168] usb 2-5: configuration #1 chosen from 1 choice
[    2.458347] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/input/input5
[    2.458423] generic-usb 0003:046D:C018.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:0b.0-5/input0
[    2.600011] usb 1-2.6: new high speed USB device using ehci_hcd and address 5
[    2.774120] usb 1-2.6: rejected 1 configuration due to insufficient available bus power
[    2.774123] usb 1-2.6: no configuration chosen from 1 choice
[    3.259833] PM: Starting manual resume from disk
[    3.259840] PM: Resume from partition 8:2
[    3.259842] PM: Checking hibernation image.
[    3.260090] PM: Resume from disk failed.
[    3.278858] EXT4-fs (sda1): barriers enabled
[    3.292203] kjournald2 starting: pid 451, dev sda1:8, commit interval 5 seconds
[    3.292215] EXT4-fs (sda1): delayed allocation enabled
[    3.292218] EXT4-fs: file extents enabled
[    3.294254] EXT4-fs: mballoc enabled
[    3.294267] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.784123] type=1505 audit(1256668187.542:2): operation="profile_load" pid=474 name=/usr/share/gdm/guest-session/Xsession
[    3.794594] type=1505 audit(1256668187.552:3): operation="profile_load" pid=475 name=/sbin/dhclient3
[    3.795422] type=1505 audit(1256668187.552:4): operation="profile_load" pid=475 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.795835] type=1505 audit(1256668187.552:5): operation="profile_load" pid=475 name=/usr/lib/connman/scripts/dhclient-script
[    3.832301] type=1505 audit(1256668187.592:6): operation="profile_load" pid=476 name=/usr/bin/evince
[    3.844233] type=1505 audit(1256668187.602:7): operation="profile_load" pid=476 name=/usr/bin/evince-previewer
[    3.851263] type=1505 audit(1256668187.612:8): operation="profile_load" pid=476 name=/usr/bin/evince-thumbnailer
[    3.867940] type=1505 audit(1256668187.622:9): operation="profile_load" pid=478 name=/usr/lib/cups/backend/cups-pdf
[    3.868870] type=1505 audit(1256668187.622:10): operation="profile_load" pid=478 name=/usr/sbin/cupsd
[    4.856397] Adding 8418052k swap on /dev/sda2.  Priority:-1 extents:1 across:8418052k 
[    5.023389] udev: starting version 147
[    5.163447] EXT4-fs (sda1): internal journal on sda1:8
[    5.415670] EXT4-fs (sdc1): barriers enabled
[    5.434712] kjournald2 starting: pid 751, dev sdc1:8, commit interval 5 seconds
[    5.449819] EXT4-fs (sdc1): internal journal on sdc1:8
[    5.449825] EXT4-fs (sdc1): delayed allocation enabled
[    5.449829] EXT4-fs: file extents enabled
[    5.462048] EXT4-fs: mballoc enabled
[    5.462065] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[    5.468204] EXT4-fs (sdb1): barriers enabled
[    5.468636] kjournald2 starting: pid 756, dev sdb1:8, commit interval 5 seconds
[    5.468857] EXT4-fs (sdb1): internal journal on sdb1:8
[    5.468862] EXT4-fs (sdb1): delayed allocation enabled
[    5.468865] EXT4-fs: file extents enabled
[    5.484510] EXT4-fs: mballoc enabled
[    5.484527] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[    5.792917] EXT4-fs (sda3): barriers enabled
[    5.793122] kjournald2 starting: pid 810, dev sda3:8, commit interval 5 seconds
[    5.793399] EXT4-fs (sda3): internal journal on sda3:8
[    5.793403] EXT4-fs (sda3): delayed allocation enabled
[    5.793406] EXT4-fs: file extents enabled
[    5.810239] EXT4-fs: mballoc enabled
[    5.810253] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    6.196231] nvidia: module license 'NVIDIA' taints kernel.
[    6.196235] Disabling lock debugging due to kernel taint
[    6.205837] lp: driver loaded but no devices found
[    6.452095] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 19
[    6.452101]   alloc irq_desc for 19 on node 0
[    6.452104]   alloc kstat_irqs on node 0
[    6.452111] nvidia 0000:01:00.0: PCI INT A -> Link[LNEA] -> GSI 19 (level, low) -> IRQ 19
[    6.452121] nvidia 0000:01:00.0: setting latency timer to 64
[    6.455250] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
[    6.463849] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[    6.463870] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x6000
[    6.496782] [drm] Initialized drm 1.1.0 20060810
[    6.838087] nvidia 0000:01:00.0: setting latency timer to 64
[    6.840536] nouveau 0000:01:00.0: Detected an NV40 generation card (0x04b100a2)
[    6.841023] [drm] Initialized nouveau 0.0.15 v2.6.31-rc6-539-ged53f9fcabd42f004 for 0000:01:00.0 on minor 0
[    7.412391] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[    7.412396]   alloc irq_desc for 18 on node 0
[    7.412399]   alloc kstat_irqs on node 0
[    7.412406] SB-XFi 0000:04:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[    8.340394] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.508877] __ratelimit: 3 callbacks suppressed
[    9.508880] type=1505 audit(1256668193.262:12): operation="profile_replace" pid=974 name=/usr/share/gdm/guest-session/Xsession
[    9.510639] type=1505 audit(1256668193.272:13): operation="profile_replace" pid=975 name=/sbin/dhclient3
[    9.511414] type=1505 audit(1256668193.272:14): operation="profile_replace" pid=975 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.511830] type=1505 audit(1256668193.272:15): operation="profile_replace" pid=975 name=/usr/lib/connman/scripts/dhclient-script
[    9.515151] type=1505 audit(1256668193.272:16): operation="profile_replace" pid=976 name=/usr/bin/evince
[    9.527030] type=1505 audit(1256668193.282:17): operation="profile_replace" pid=976 name=/usr/bin/evince-previewer
[    9.534336] type=1505 audit(1256668193.292:18): operation="profile_replace" pid=976 name=/usr/bin/evince-thumbnailer
[    9.544603] type=1505 audit(1256668193.302:19): operation="profile_replace" pid=978 name=/usr/lib/cups/backend/cups-pdf
[    9.545490] type=1505 audit(1256668193.302:20): operation="profile_replace" pid=978 name=/usr/sbin/cupsd
[    9.547974] type=1505 audit(1256668193.302:21): operation="profile_replace" pid=979 name=/usr/sbin/tcpdump
[   10.178279] usplash:414 freeing invalid memtype ffffffffd0000000-ffffffffe0000000
[   20.049892] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.049896] vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hwardware performance
[   20.049897] vboxdrv: counter framework which can generate NMIs is active. You have to prevent
[   20.049899] vboxdrv: the usage of hardware performance counters by
[   20.049900] vboxdrv:   echo 2 > /proc/sys/kernel/perf_counter_paranoid
[   20.049904] vboxdrv: Found 2 processor cores.
[   20.049954] VBoxDrv: dbg - g_abExecMemory=ffffffffa0b56420
[   20.049990] vboxdrv: fAsync=0 offMin=0x48a offMax=0x19fa
[   20.050030] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.050033] vboxdrv: Successfully loaded version 3.0.8 (interface 0x000e0000).
[   20.275236] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0cf51c0
[   20.277703] VBoxNetAdp: dbg - g_abExecMemory=ffffffffa0d0eac0
[   20.458902] ppdev: user-space parallel port driver
[   21.665849] CPU0 attaching NULL sched-domain.
[   21.665855] CPU1 attaching NULL sched-domain.
[   21.700141] CPU0 attaching sched-domain:
[   21.700145]  domain 0: span 0-1 level MC
[   21.700149]   groups: 0 1
[   21.700154]   domain 1: span 0-1 level CPU
[   21.700157]    groups: 0-1 (__cpu_power = 2048)
[   21.700164] CPU1 attaching sched-domain:
[   21.700166]  domain 0: span 0-1 level MC
[   21.700169]   groups: 1 0
[   21.700184]   domain 1: span 0-1 level CPU
[   21.700186]    groups: 0-1 (__cpu_power = 2048)
[   22.950027] eth0: no IPv6 routers present
[   23.764027] CPU0 attaching NULL sched-domain.
[   23.764033] CPU1 attaching NULL sched-domain.
[   23.800240] CPU0 attaching sched-domain:
[   23.800244]  domain 0: span 0-1 level MC
[   23.800248]   groups: 0 1
[   23.800255] CPU1 attaching sched-domain:
[   23.800257]  domain 0: span 0-1 level MC
[   23.800260]   groups: 1 0
[   80.580851] npviewer.bin[2181]: segfault at f4bf3044 ip 00000000f6fe1ded sp 00000000ffaa7570 error 4 in libpthread-2.10.1.so[f6fda000+15000]
____________________________________________

Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
____________________________________________

Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
____________________________________________

xset -q:

xset:  unable to open display ""
____________________________________________

nvidia-settings -q all:


ERROR: The control display is undefined; please run `nvidia-settings
       --help` for usage information.

____________________________________________

/proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash

____________________________________________

/proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping	: 2
cpu MHz		: 1603.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 3733.26
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping	: 2
cpu MHz		: 1870.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 3733.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


____________________________________________

/proc/interrupts
           CPU0       CPU1       
  0:         24          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  7:          1          0   IO-APIC-edge    
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 14:       1273          0   IO-APIC-edge      pata_amd
 15:        154          0   IO-APIC-edge      pata_amd
 18:         53          0   IO-APIC-fasteoi   ctxfi
 19:       2199          0   IO-APIC-fasteoi   nvidia
 20:        952          0   IO-APIC-fasteoi   ohci_hcd:usb2
 21:         61          0   IO-APIC-fasteoi   ehci_hcd:usb1
 22:       1995          0   IO-APIC-fasteoi   sata_nv
 23:      15274          0   IO-APIC-fasteoi   sata_nv, eth0
NMI:          0          0   Non-maskable interrupts
LOC:      22175      24198   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:         59         70   Rescheduling interrupts
CAL:         22        144   Function call interrupts
TLB:        475        528   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          1          1   Machine check polls
ERR:          1
MIS:          0

____________________________________________

/proc/meminfo
MemTotal:        4060100 kB
MemFree:         2980432 kB
Buffers:           27848 kB
Cached:           227928 kB
SwapCached:            0 kB
Active:           735664 kB
Inactive:         174700 kB
Active(anon):     658016 kB
Inactive(anon):        0 kB
Active(file):      77648 kB
Inactive(file):   174700 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       8418052 kB
SwapFree:        8418052 kB
Dirty:                88 kB
Writeback:             0 kB
AnonPages:        654736 kB
Mapped:            69876 kB
Slab:              32624 kB
SReclaimable:      15560 kB
SUnreclaim:        17064 kB
PageTables:        17752 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    10448100 kB
Committed_AS:    1099288 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      348412 kB
VmallocChunk:   34359387131 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       14080 kB
DirectMap2M:     4179968 kB

____________________________________________

/proc/modules
binfmt_misc 10220 1 - Live 0xffffffffa0d20000
ppdev 8232 0 - Live 0xffffffffa0d1b000
vboxnetadp 93292 0 - Live 0xffffffffa0d02000
vboxnetflt 100300 0 - Live 0xffffffffa0ce7000
vboxdrv 1708492 1 vboxnetflt, Live 0xffffffffa0b43000
iptable_filter 3872 0 - Live 0xffffffffa0b40000
ip_tables 21200 1 iptable_filter, Live 0xffffffffa0b35000
x_tables 25832 1 ip_tables, Live 0xffffffffa0b29000
snd_ctxfi 99016 2 - Live 0xffffffffa0b0b000
psmouse 57124 0 - Live 0xffffffffa0af8000
snd_pcm_oss 44704 0 - Live 0xffffffffa0ae8000
snd_mixer_oss 18976 1 snd_pcm_oss, Live 0xffffffffa0ade000
serio_raw 6596 0 - Live 0xffffffffa0ad7000
snd_pcm 93160 2 snd_ctxfi,snd_pcm_oss, Live 0xffffffffa0abb000
snd_seq_dummy 3460 0 - Live 0xffffffffa0ab5000
snd_seq_oss 33440 0 - Live 0xffffffffa0aaa000
snd_seq_midi 8192 0 - Live 0xffffffffa09c2000
snd_rawmidi 27360 1 snd_seq_midi, Live 0xffffffffa0aa1000
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi, Live 0xffffffffa0a9c000
snd_seq 60608 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa0a8b000
snd_timer 26992 2 snd_pcm,snd_seq, Live 0xffffffffa0a82000
nouveau 643940 0 - Live 0xffffffffa09df000
snd_seq_device 8308 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa09d7000
ttm 50032 1 nouveau, Live 0xffffffffa09c5000
snd 77096 13 snd_ctxfi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa09ad000
drm 197632 2 nouveau,ttm, Live 0xffffffffa0977000
i2c_algo_bit 7076 1 nouveau, Live 0xffffffffa096c000
i2c_nforce2 8168 0 - Live 0xffffffffa0011000
soundcore 9088 1 snd, Live 0xffffffffa096f000
lp 11908 0 - Live 0xffffffffa0967000
snd_page_alloc 10928 1 snd_pcm, Live 0xffffffffa095f000
nvidia 9620040 24 - Live 0xffffffffa002d000 (P)
parport 40528 2 ppdev,lp, Live 0xffffffffa0021000
usbhid 43968 0 - Live 0xffffffffa0014000
forcedeth 61292 0 - Live 0xffffffffa0000000

____________________________________________

/proc/version
Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009

____________________________________________

/proc/pci does not exist

____________________________________________

/proc/iomem
00000000-0000ffff : reserved
00010000-0009afff : System RAM
0009b000-0009ffff : reserved
000c0000-000cffff : pnp 00:0d
000e0000-000fffff : reserved
00100000-bffbffff : System RAM
  01000000-01530738 : Kernel code
  01530739-0182156f : Kernel data
  018d3000-019e2ccb : Kernel bss
bffc0000-bffcdfff : ACPI Tables
bffce000-bfffffff : ACPI Non-volatile Storage
d0000000-dfffffff : PCI Bus 0000:01
  d0000000-dfffffff : 0000:01:00.0
e0000000-efffffff : PCI MMCONFIG 0 [00-ff]
  e0000000-efffffff : pnp 00:0c
f5efb000-f5efbfff : 0000:00:14.0
  f5efb000-f5efbfff : forcedeth
f5efc000-f5efcfff : 0000:00:0f.0
  f5efc000-f5efcfff : sata_nv
f5efd000-f5efdfff : 0000:00:0e.0
  f5efd000-f5efdfff : sata_nv
f5efec00-f5efecff : 0000:00:0b.1
  f5efec00-f5efecff : ehci_hcd
f5eff000-f5efffff : 0000:00:0b.0
  f5eff000-f5efffff : ohci_hcd
f5f00000-f7ffffff : PCI Bus 0000:01
  f5fe0000-f5ffffff : 0000:01:00.0
  f6000000-f6ffffff : 0000:01:00.0
  f7000000-f7ffffff : 0000:01:00.0
    f7000000-f7ffffff : nvidia
f8000000-febfffff : PCI Bus 0000:04
  f8000000-fbffffff : 0000:04:07.0
    f8000000-fbffffff : XFi
  fea00000-febfffff : 0000:04:07.0
    fea00000-febfffff : XFi
fec00000-fec00fff : IOAPIC 0
  fec00000-fec00fff : reserved
fed00000-fed003ff : HPET 0
fee00000-fee00fff : Local APIC
  fee00000-fee00fff : reserved
    fee00000-fee00fff : pnp 00:08
fee01000-feefffff : pnp 00:06
fff80000-ffffffff : reserved
100000000-13fffffff : System RAM

____________________________________________

/proc/mtrr
reg00: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg01: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable

____________________________________________

/proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
GCC version:  gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 

____________________________________________

/proc/driver/nvidia/cards/0
Model: 		 GeForce 7600 GT
IRQ:   		 19
Video BIOS: 	 05.73.22.18.01
Card Type: 	 PCI-E
DMA Size: 	 39 bits
DMA Mask: 	 0x7fffffffff
Bus Location: 	 01.00.0

____________________________________________

/proc/driver/nvidia/warnings/README
The NVIDIA graphics driver tries to detect potential problems
with the host system and warns about them using the system's
logging mechanisms. Important warning message are also logged
to dedicated text files in this directory.

____________________________________________

/proc/driver/nvidia/registry
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegistryDwords: ""

____________________________________________

/proc/asound/cards
 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 Unknown

____________________________________________

/proc/asound/pcm
00-00: ctxfi : Front/WaveIn : playback 8 : capture 1
00-01: ctxfi : Surround : playback 8
00-02: ctxfi : Center/LFE : playback 8
00-03: ctxfi : Side : playback 8
00-04: ctxfi : IEC958 Non-audio : playback 1

____________________________________________

/proc/asound/modules
 0 snd_ctxfi

____________________________________________

/proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 4]: digital audio playback
  5: [ 0- 3]: digital audio playback
  6: [ 0- 2]: digital audio playback
  7: [ 0- 1]: digital audio playback
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0]   : control

____________________________________________

/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

____________________________________________

/proc/asound/timers
G0: system timer : 10000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-0-2: PCM playback 0-0-2 : SLAVE
P0-0-4: PCM playback 0-0-4 : SLAVE
P0-0-6: PCM playback 0-0-6 : SLAVE
P0-0-8: PCM playback 0-0-8 : SLAVE
P0-0-10: PCM playback 0-0-10 : SLAVE
P0-0-12: PCM playback 0-0-12 : SLAVE
P0-0-14: PCM playback 0-0-14 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-1-2: PCM playback 0-1-2 : SLAVE
P0-1-4: PCM playback 0-1-4 : SLAVE
P0-1-6: PCM playback 0-1-6 : SLAVE
P0-1-8: PCM playback 0-1-8 : SLAVE
P0-1-10: PCM playback 0-1-10 : SLAVE
P0-1-12: PCM playback 0-1-12 : SLAVE
P0-1-14: PCM playback 0-1-14 : SLAVE
P0-2-0: PCM playback 0-2-0 : SLAVE
P0-2-2: PCM playback 0-2-2 : SLAVE
P0-2-4: PCM playback 0-2-4 : SLAVE
P0-2-6: PCM playback 0-2-6 : SLAVE
P0-2-8: PCM playback 0-2-8 : SLAVE
P0-2-10: PCM playback 0-2-10 : SLAVE
P0-2-12: PCM playback 0-2-12 : SLAVE
P0-2-14: PCM playback 0-2-14 : SLAVE
P0-3-0: PCM playback 0-3-0 : SLAVE
P0-3-2: PCM playback 0-3-2 : SLAVE
P0-3-4: PCM playback 0-3-4 : SLAVE
P0-3-6: PCM playback 0-3-6 : SLAVE
P0-3-8: PCM playback 0-3-8 : SLAVE
P0-3-10: PCM playback 0-3-10 : SLAVE
P0-3-12: PCM playback 0-3-12 : SLAVE
P0-3-14: PCM playback 0-3-14 : SLAVE
P0-4-0: PCM playback 0-4-0 : SLAVE

____________________________________________

/proc/asound/hwdep does not exist

____________________________________________

End of NVIDIA bug report log file.
```

---

### Post by autocrosser on 2009-10-27
I'm at work right now, but I'm also using the 190 driver without any problems--I'll get the sources.list from my main system in a couple of hours--you can do a update via chroot with a live if you can't get into your normal install.

---

### Post by c2483 on 2009-10-27
I installed again but with the nvidia installer.
Here is my new bug report, same thing happened, I hear the startup sound then the monitor shuts down
```
Start of NVIDIA bug report log file.  Please include this file
when reporting a graphics driver bug via the nV News NVIDIA
Linux forum (see www.nvnews.net) or by sending email to
'linux-bugs@nvidia.com'.

nvidia-bug-report.sh Version: 4401223

Date: Tue Oct 27 16:39:53 EDT 2009
uname: Linux charles-pc 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

____________________________________________

/etc/issue
Ubuntu 9.10 \n \l


____________________________________________

/etc/debian_version
squeeze/sid

____________________________________________

/var/log/nvidia-installer.log
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Tue Oct 27 16:35:59 2009
installer version: 1.0.7

option status:
  license pre-accepted    : false
  update                  : false
  force update            : false
  expert                  : false
  uninstall               : false
  driver info             : false
  precompiled interfaces  : true
  no ncurses color        : false
  query latest version    : false
  OpenGL header files     : true
  no questions            : false
  silent                  : false
  no recursion            : false
  no backup               : false
  kernel module only      : false
  sanity                  : false
  add this kernel         : false
  no runlevel check       : false
  no network              : false
  no ABI note             : false
  no RPMs                 : false
  no kernel module        : false
  force SELinux           : default
  no X server check       : false
  no cc version check     : false
  force tls               : (not specified)
  force compat32 tls      : (not specified)
  X install prefix        : (not specified)
  X library install path  : (not specified)
  X module install path   : (not specified)
  OpenGL install prefix   : (not specified)
  OpenGL install libdir   : (not specified)
  compat32 install chroot : (not specified)
  compat32 install prefix : (not specified)
  compat32 install libdir : (not specified)
  utility install prefix  : (not specified)
  utility install libdir  : (not specified)
  doc install prefix      : (not specified)
  kernel name             : (not specified)
  kernel include path     : (not specified)
  kernel source path      : (not specified)
  kernel output path      : (not specified)
  kernel install path     : (not specified)
  proc mount point        : /proc
  ui                      : (not specified)
  tmpdir                  : /tmp
  ftp mirror              : ftp://download.nvidia.com
  RPM file list           : (not specified)

Using: nvidia-installer ncurses user interface
-> License accepted.
-> Installing NVIDIA driver version 190.42.
-> Performing CC sanity check with CC="cc".
-> Performing CC version check with CC="cc".
-> Kernel source path: '/lib/modules/2.6.31-14-generic/build'
-> Kernel output path: '/lib/modules/2.6.31-14-generic/build'
-> Performing rivafb check.
-> Performing nvidiafb check.
-> Performing Xen check.
-> Cleaning kernel module build directory.
   executing: 'cd ./usr/src/nv; make clean'...
-> Building kernel module:
   executing: 'cd ./usr/src/nv; make module SYSSRC=/lib/modules/2.6.31-14-gener
   ic/build SYSOUT=/lib/modules/2.6.31-14-generic/build'...
   NVIDIA: calling KBUILD...
   make CC=cc  KBUILD_VERBOSE=1 -C /lib/modules/2.6.31-14-generic/build SUBDIRS
   =/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.tmp_ver
   sions ; rm -f /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.tm
   p_versions/*
   make -f scripts/Makefile.build obj=/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.4
   2-pkg2/usr/src/nv
     cc -Wp,-MD,/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.nv.
   o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Iinclu
   de  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include inc
   lude/linux/autoconf.h -Iubu
   ntu/include  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -
   fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-f
   ormat-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-
   red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack
   -protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-u
   nwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024
   -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-stat
   ement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/self
   gz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-
   type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-
   multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-co
   mpare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_ST
   RING=\"190.42\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(nv)"  -D
   "KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3104/NVIDIA-Linux-x86_
   64-190.42-pkg2/usr/src/nv/.tmp_nv.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.
   42-pkg2/usr/src/nv/nv.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:119,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/mtrr.h:167,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:154,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv.c:14:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
   /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/nv.c: In function
   ‘nv_kern_open’:
   /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/nv.c:2188: warnin
   g: initialization from incompatible pointer type
     cc -Wp,-MD,/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.nv_
   gvi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Ii
   nclude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include
   include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -Wno-format-security -fno-delete-null-pointer-checks
   -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -macc
   umulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sig
   n-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3
   dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-
   calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -
   fno-dwarf2-cfi-asm -I/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src
   /nv -Wall -Wimplicit -Wretur
   n-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wn
   o-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-
   compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_
   STRING=\"190.42\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -
   D"KBUILD_BASENAME=KBUILD_STR(nv_gvi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"
    -c -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.tmp_nv_gv
   i.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/nv_gvi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv_gvi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:119,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv_gvi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/mtrr.h:167,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:154,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv_gvi.c:15:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     cc -Wp,-MD,/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.nv-
   vm.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Iin
   clude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include 
   include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -Wno-format-security -fno-delete-null-pointer-checks
   -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -macc
   umulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sig
   n-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3
   dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-
   calls -Wdeclaration-after-
   statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/
   selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv -Wall -Wimplicit -Wret
   urn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -
   Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsig
   n-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSIO
   N_STRING=\"190.42\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s"
   -D"KBUILD_BASENAME=KBUILD_STR(nv_vm)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"
    -c -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.tmp_nv-vm
   .o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/nv-vm.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:119,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/mtrr.h:167,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:154,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-vm.c:14:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     cc -Wp,-MD,/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.os-
   agp.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Ii
   nclude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include
   include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -Wno-format-security -fno-delete-null-pointer-checks
   -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -macc
   umulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sig
   n-compare -fno-asynchronous-unwi
   nd-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -f
   no-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statem
   ent -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz
   3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-ty
   pe -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-mu
   ltichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-comp
   are -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRI
   NG=\"190.42\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KB
   UILD_BASENAME=KBUILD_STR(os_agp)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c
   -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.tmp_os-agp.o 
   /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/os-agp.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-agp.c:24:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-agp.c:24:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-agp.c:24:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:119,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-agp.c:24:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/mtrr.h:167,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:154,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-agp.c:24:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     cc -Wp,-MD,/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.os-
   interface.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/includ
   e  -Iinclude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -i
   nclude include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef
   -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-
   implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-
   checks -O2 -m64 -mtune=generic
    -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -
   fstack-protector -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchro
   nous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-tha
   n=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-aft
   er-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/t
   mp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv -Wall -Wimplicit -W
   return-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arit
   h -Wno-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -W
   sign-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VER
   SION_STRING=\"190.42\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=
   #s" -D"KBUILD_BASENAME=KBUILD_STR(os_interface)"  -D"KBUILD_MODNAME=KBUILD_S
   TR(nvidia)"  -c -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/n
   v/.tmp_os-interface.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-interface.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-interface.c:26:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-interface.c:26:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-interface.c:26:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:119,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-interface.c:26:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/mtrr.h:167,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:154,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-interface.c:26:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     cc -Wp,-MD,/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.os-
   registry.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include
    -Iinclude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -inc
   lude include/linux/autoconf.h -Iubuntu/incl
   ude  -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-stri
   ct-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-se
   curity -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone
   -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protecto
   r -fstack-protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tab
   les -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omi
   t-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -W
   no-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz3104/N
   VIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Ws
   witch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multicha
   r -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-compare -W
   no-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"1
   90.42\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(os_registry)"  -
   D"KBUILD_MODNAME=KBUILD_STR(nvidia)"  -c -o /tmp/selfgz3104/NVIDIA-Linux-x86
   _64-190.42-pkg2/usr/src/nv/.tmp_os-registry.o /tmp/selfgz3104/NVIDIA-Linux-x
   86_64-190.42-pkg2/usr/src/nv/os-registry.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-registry.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-registry.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-registry.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:119,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-registry.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/mtrr.h:167,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:154,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/os-registry.c:15:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     cc -Wp,-MD,/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.nv-
   i2c.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Ii
   nclude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include
   include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -Wno-format-security -fno-delete-null-pointer-checks
   -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -macc
   umulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sig
   n-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3
   dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-
   calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -
   fno-dwarf2-cfi-asm -I/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src
   /nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wpar
   entheses -Wpointer-arith -Wno-multichar -Werror -mcmodel=kernel -mno-red-zon
   e -fno-defer-pop -MD -Wsi
   gn-compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSI
   ON_STRING=\"190.42\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s
   " -D"KBUILD_BASENAME=KBUILD_STR(nv_i2c)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidi
   a)"  -c -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.tmp_n
   v-i2c.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/nv-i2c.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-i2c.c:8:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:119,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-i2c.c:8:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/mtrr.h:167,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:154,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-i2c.c:8:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     cc -Wp,-MD,/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.nva
   cpi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include  -Ii
   nclude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -include
   include/linux/autoconf.h -Iubuntu/include  -D__KERNEL__ -Wall -Wundef -Wstri
   ct-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implic
   it-function-declaration -Wno-format-security -fno-delete-null-pointer-checks
   -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -macc
   umulate-outgoing-args -fstack-protector -fstack-protector-all -pipe -Wno-sig
   n-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3
   dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-
   calls -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -
   fno-dwarf2-cfi-asm -I/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src
   /nv -Wall -Wimplicit -Wretur
   n-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wn
   o-multichar -Werror -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-
   compare -Wno-cast-qual -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_
   STRING=\"190.42\" -UDEBUG -U_DEBUG -DNDEBUG  -DMODULE -D"KBUILD_STR(s)=#s" -
   D"KBUILD_BASENAME=KBUILD_STR(nvacpi)"  -D"KBUILD_MODNAME=KBUILD_STR(nvidia)"
    -c -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.tmp_nvacp
   i.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/nvacpi.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from include/linux/sched.h:52,
                    from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/utsname.h:35,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:21,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2185: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from include/linux/dma-mapping.h:7,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/dma-mapping.h:36,
                    from include/linux/dma-mapping.h:107,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/pci.h:129,
                    from include/linux/pci.h:1112,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:92,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nvacpi.c:15:
   include/asm-generic/dma-mapping-common.h: In function ‘dma_map_page’:
   include/asm-generic/dma-mapping-common.h:77: warning: pointer of type ‘voi
   d *’ used in arithmetic
   In file included from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:119,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nvacpi.c:15:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:149: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:152: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/compat.h:14,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/mtrr.h:167,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nv-linux.h:154,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nvacpi.c:15:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h: In f
   unction ‘compat_alloc_user_space’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/compat.h:210: 
   warning: pointer of type ‘void *’ used in arithmetic
     ld -m elf_x86_64   -r -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/u
   sr/src/nv/nvidia.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/n
   v/nv-kernel.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/nv.
   o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/nv_gvi.o /tmp/s
   elfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/nv-vm.o /tmp/selfgz3104
   /NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/os-agp.o /tmp/selfgz3104/NVIDIA-
   Linux-x86_64-190.42-pkg2/usr/src/nv/os-interface.o /tmp/selfgz3104/NVIDIA-Li
   nux-x86_64-190.42-pkg2/usr/src/nv/os-registry.o /tmp/selfgz3104/NVIDIA-Linux
   -x86_64-190.42-pkg2/usr/src/nv/nv-i2c.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-
   190.42-pkg2/usr/src/nv/nvacpi.o 
   (cat /dev/null;   echo kernel//tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg
   2/usr/src/nv/nvidia.ko;) > /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/u
   sr/src/nv/modules.order
   make -f /usr/src/linux-headers-2.6.31-14-generic/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.31-14-generic/Modu
   le.symvers -I /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/Mod
   ule.symvers  -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/M
   odule.symvers -S -K /usr/src/linux-headers-2.6.31-14-generic/Module.markers 
   -M /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/Module.markers
   -w  -s
   WARNING: could not find /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/
   src/nv/.nv-kernel.o.cmd for /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/
   usr/src/nv/nv-kernel.o
     cc -Wp,-MD,/tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/src/nv/.nvi
   dia.mod.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.1/include 
   -Iinclude  -I/usr/src/linux-headers-2.6.31-14-generic/arch/x86/include -incl
   ude include/linux/autoconf.h -Iubuntu/include  -D__K
   ERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasin
   g -fno-common -Werror-implicit-function-declaration -Wno-format-security -fn
   o-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=
   kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -fstack
   -protector-all -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-
   sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-p
   ointer -fno-optimize-sibling-calls -Wdeclaration-after-statement -Wno-pointe
   r-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -I/tmp/selfgz3104/NVIDIA-Lin
   ux-x86_64-190.42-pkg2/usr/src/nv -Wall -Wimplicit -Wreturn-type -Wswitch -Wf
   ormat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror
   -mcmodel=kernel -mno-red-zone -fno-defer-pop -MD -Wsign-compare -Wno-cast-qu
   al -Wno-error -D__KERNEL__ -DMODULE -DNVRM -DNV_VERSION_STRING=\"190.42\" -U
   DEBUG -U_DEBUG -DNDEBUG  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(
   nvidia.mod)"  -D"KBUILD_MODNAME=KBU
   ILD_STR(nvidia)"  -DMODULE -c -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-
   pkg2/usr/src/nv/nvidia.mod.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2
   /usr/src/nv/nvidia.mod.c
   In file included from include/linux/bitops.h:17,
                    from include/linux/kernel.h:15,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/percpu.h:45,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/current.h:5,
                    from /usr/src/linux-headers-2.6.31-14-generic/arch/x86/incl
   ude/asm/processor.h:15,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nvidia.mod.c:1:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:64: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:102: 
   warning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘change_bit’:
   /usr/src/linux-headers-2.6.31-14-generic/arch/x86/include/asm/bitops.h:178: 
   warning: pointer of type ‘void *’ used in arithmetic
     ld -r -m elf_x86_64  --build-id -o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190
   .42-pkg2/usr/src/nv/nvidia.ko /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg
   2/usr/src/nv/nvidia.o /tmp/selfgz3104/NVIDIA-Linux-x86_64-190.42-pkg2/usr/sr
   c/nv/nvidia.mod.o
   NVIDIA: left KBUILD.
-> done.
-> Kernel module compilation complete.
-> Kernel messages:
   [   20.250163] CPU1 attaching sched-domain:
   [   20.250166]  domain 0: span 0-1 level MC
   [   20.250169]   groups: 1 0
   [   21.521210] CPU0 attaching NULL sched-domain.
   [   21.521216] CPU1 attaching NULL sched-domain.
   [   21.551480] CPU0 attaching sched-domain:
   [   21.551485]  domain 0: span 0-1 level MC
   [   21.551489]   groups: 0 1
   [   21.551494]   domain 1: span 0-1 level CPU
   [   21.551497]    groups: 0-1 (__cpu_power = 2048)
   [   21.551505] CPU1 attaching sched-domain:
   [   21.551507]  domain 0: span 0-1 level MC
   [   21.551510]   groups: 1 0
   [   21.551514]   domain 1: span 0-1 level CPU
   [   21.551517]    groups: 0-1 (__cpu_power = 2048)
   [   21.680008] eth0: no IPv6 routers present
   [  294.170256] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 1
   [  295.854579] nouveau 0000:01:00.0: nouveau_channel_free: freeing fifo 0
   [  295.855192] [TTM] Freeing bo global.
   [  295.855259] [TTM] Zone  kernel: Used memory at exit: 0 kiB.
   [  295.855269] mtrr: no MTRR for d0000000,10000000 found
   [  335.272608] nvidia: module license 'NVIDIA' taints kernel.
   [  335.272612] Disabling lock debugging due to kernel taint
   [  335.527629] nvidia 0000:01:00.0: setting latency timer to 64
   [  335.527872] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue
   Oct 20 20:25:42 PDT 2009
-> Installing both new and classic TLS OpenGL libraries.
-> Installing both new and classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility OpenGL libraries? (Answer: Yes)
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64' (190.42):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
-> Running runtime sanity check:
-> done.
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: Y
   es)
-> Your X configuration file has been successfully updated.  Installation of
   the NVIDIA Accelerated Graphics Driver for Linux-x86_64 (version: 190.42) is
   now complete.

____________________________________________

/var/log/XFree86.0.log does not exist

____________________________________________

/var/log/XFree86.0.log.old does not exist

____________________________________________

/var/log/Xorg.0.log

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux charles-pc 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 27 16:38:19 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0391:3842:c553 nVidia Corporation G73 [GeForce 7600 GT] rev 161, Mem @ 0xf7000000/16777216, 0xd0000000/268435456, 0xf6000000/16777216, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  190.42  Tue Oct 20 21:19:30 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  190.42  Tue Oct 20 20:42:04 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) Oct 27 16:38:20 NVIDIA(0): Enabling RENDER acceleration
(II) Oct 27 16:38:20 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Oct 27 16:38:20 NVIDIA(0):     enabled.
(II) Oct 27 16:38:22 NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:1:0:0 (GPU-0)
(--) Oct 27 16:38:22 NVIDIA(0): Memory: 262144 kBytes
(--) Oct 27 16:38:22 NVIDIA(0): VideoBIOS: 05.73.22.18.01
(II) Oct 27 16:38:22 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Oct 27 16:38:22 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Oct 27 16:38:22 NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:1:0:0:
(--) Oct 27 16:38:22 NVIDIA(0):     SONY TV (CRT-1)
(--) Oct 27 16:38:22 NVIDIA(0):     LG L203WTX (DFP-0)
(--) Oct 27 16:38:22 NVIDIA(0): SONY TV (CRT-1): 400.0 MHz maximum pixel clock
(--) Oct 27 16:38:22 NVIDIA(0): LG L203WTX (DFP-0): 330.0 MHz maximum pixel clock
(--) Oct 27 16:38:22 NVIDIA(0): LG L203WTX (DFP-0): Internal Dual Link TMDS
(II) Oct 27 16:38:22 NVIDIA(0): Assigned Display Device: CRT-1
(==) Oct 27 16:38:22 NVIDIA(0): 
(==) Oct 27 16:38:22 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Oct 27 16:38:22 NVIDIA(0):     will be used as the requested mode.
(==) Oct 27 16:38:22 NVIDIA(0): 
(II) Oct 27 16:38:22 NVIDIA(0): Validated modes:
(II) Oct 27 16:38:22 NVIDIA(0):     "nvidia-auto-select"
(II) Oct 27 16:38:22 NVIDIA(0): Virtual screen size determined to be 1920 x 1080
(--) Oct 27 16:38:22 NVIDIA(0): DPI set to (30, 30); computed from "UseEdidDpi" X config
(--) Oct 27 16:38:22 NVIDIA(0):     option
(==) Oct 27 16:38:22 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) Oct 27 16:38:22 NVIDIA(0): Initialized GPU GART.
(II) Oct 27 16:38:22 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Oct 27 16:38:22 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Oct 27 16:38:23 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device   USB Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event3"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device   USB Keyboard
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event4"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event5"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB Optical Mouse: initialized for relative axes.

____________________________________________

/etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Tue Oct 20 21:25:04 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


____________________________________________

/var/log/Xorg.0.log.old

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux charles-pc 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash
Build Date: 26 October 2009  05:19:56PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Oct 27 16:31:13 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No device specified for screen "Default Screen".
	Using the first device section listed.
(**) |   |-->Device "Default Device"
(==) No monitor specified for screen "Default Screen".
	Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0xb40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0391:3842:c553 nVidia Corporation G73 [GeForce 7600 GT] rev 161, Mem @ 0xf7000000/16777216, 0xd0000000/268435456, 0xf6000000/16777216, I/O @ 0x0000dc00/128, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nouveau"
(II) Loading /usr/lib/xorg/modules/drivers//nouveau_drv.so
(II) Module nouveau: vendor="X.Org Foundation"
	compiled for 1.6.3, module version = 0.0.10
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) NOUVEAU driver Date:   Thu Aug 20 18:44:38 2009 +0200
(II) NOUVEAU driver for NVIDIA chipset families :
	RIVA TNT    (NV04)
	RIVA TNT2   (NV05)
	GeForce 256 (NV10)
	GeForce 2   (NV11, NV15)
	GeForce 4MX (NV17, NV18)
	GeForce 3   (NV20)
	GeForce 4Ti (NV25, NV28)
	GeForce FX  (NV3x)
	GeForce 6   (NV4x)
	GeForce 7   (G7x)
	GeForce 8   (G8x)
(II) Primary Device is: PCI 01@00:00:0
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(--) NOUVEAU(0): Chipset: "NVIDIA NV4B"
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
(II) NOUVEAU(0): Initializing int10
(II) NOUVEAU(0): Primary V_BIOS segment is: 0xc000
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so
(II) NOUVEAU(0): Loaded DRI module
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) NOUVEAU(0): [drm] nouveau interface version: 0.0.15
(--) NOUVEAU(0): [drm] kernel modesetting not available
(II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
(==) NOUVEAU(0): RGB weight 888
(==) NOUVEAU(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
(==) NOUVEAU(0): Using HW cursor
(--) NOUVEAU(0): Linear framebuffer at 0xD0000000
(--) NOUVEAU(0): MMIO registers at 0xF7000000
(II) NOUVEAU(0): Initial CRTC_OWNER is 4
(II) NOUVEAU(0): Attempting to load BIOS image from PROM
(II) NOUVEAU(0): ... appears to be valid
(II) NOUVEAU(0): BIT BIOS found
(II) NOUVEAU(0): Bios version 05.73.22.18
(II) NOUVEAU(0): Found Display Configuration Block version 3.0
(!!) NOUVEAU(0): Raw DCB entry 0: 01000300 00000028
(!!) NOUVEAU(0): Raw DCB entry 1: 03000302 00000000
(!!) NOUVEAU(0): Raw DCB entry 2: 04011310 00000028
(!!) NOUVEAU(0): Raw DCB entry 3: 04011312 00000000
(!!) NOUVEAU(0): Raw DCB entry 4: 020223f1 00c0c080
(--) NOUVEAU(0): Parsing VBIOS init table 0 at offset 0xDE3C
(--) NOUVEAU(0): Parsing VBIOS init table 1 at offset 0xE4B6
(--) NOUVEAU(0): Parsing VBIOS init table 2 at offset 0xEB4C
(--) NOUVEAU(0): Parsing VBIOS init table 3 at offset 0xECCC
(--) NOUVEAU(0): Parsing VBIOS init table 4 at offset 0xEE26
(II) NOUVEAU(0): Output DVI-I-0 has no monitor section
(II) NOUVEAU(0): I2C bus "DVI-I-0" initialized.
(II) NOUVEAU(0): Output DVI-I-1 has no monitor section
(II) NOUVEAU(0): I2C bus "DVI-I-1" initialized.
(II) NOUVEAU(0): I2C device "DVI-I-0:E-EDID segment register" registered at address 0x60.
(II) NOUVEAU(0): I2C device "DVI-I-0:ddc2" registered at address 0xA0.
(II) NOUVEAU(0): EDID for output DVI-I-0
(II) NOUVEAU(0): Manufacturer: GSM  Model: 4e40  Serial#: 179771
(II) NOUVEAU(0): Year: 2006  Week: 2
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): GTF timings supported
(II) NOUVEAU(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.615
(II) NOUVEAU(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x870@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 85 Hz, H min: 28 H max: 83 kHz, PixClock max 140 MHz
(II) NOUVEAU(0): Monitor name: L203WTX
(II) NOUVEAU(0): Monitor name: 
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff001e6d404e3bbe0200
(II) NOUVEAU(0): 	02100103ee2b1b78eac605a3574a9d25
(II) NOUVEAU(0): 	125054a76b808180714f615945593140
(II) NOUVEAU(0): 	0101010101017c2e90a0601a1e403020
(II) NOUVEAU(0): 	3600b20e1100001a000000fd0038551c
(II) NOUVEAU(0): 	530e000a202020202020000000fc004c
(II) NOUVEAU(0): 	3230335754580a2020202020000000fc
(II) NOUVEAU(0): 	000a2020202020202020202020200099
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Using EDID range info for horizontal sync
(II) NOUVEAU(0): Using EDID range info for vertical refresh
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Printing probed modes for output DVI-I-0
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): I2C device "DVI-I-1:E-EDID segment register" registered at address 0x60.
(II) NOUVEAU(0): I2C device "DVI-I-1:ddc2" registered at address 0xA0.
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): Manufacturer: SNY  Model: 5401  Serial#: 16843009
(II) NOUVEAU(0): Year: 2008  Week: 1
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NOUVEAU(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 57 V max: 63 Hz, H min: 30 H max: 80 kHz, PixClock max 150 MHz
(II) NOUVEAU(0): Monitor name: SONY TV
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff004dd9015401010101
(II) NOUVEAU(0): 	0112010308a05a780a0dc9a057479827
(II) NOUVEAU(0): 	12484c21080081800101010101010101
(II) NOUVEAU(0): 	010101010101023a801871382d40582c
(II) NOUVEAU(0): 	450040846300001e662150b051001b30
(II) NOUVEAU(0): 	4070360040846300001e000000fd0039
(II) NOUVEAU(0): 	3f1e500f000a202020202020000000fc
(II) NOUVEAU(0): 	00534f4e592054560a20202020200080
(II) NOUVEAU(0): EDID vendor "SNY", prod id 21505
(II) NOUVEAU(0): Printing probed modes for output DVI-I-1
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Output DVI-I-0 connected
(II) NOUVEAU(0): Output DVI-I-1 connected
(II) NOUVEAU(0): Using fuzzy aspect match for initial modes
(II) NOUVEAU(0): Output DVI-I-0 using initial mode 1024x768
(II) NOUVEAU(0): Output DVI-I-1 using initial mode 1024x768
(--) NOUVEAU(0): VideoRAM: 262144 kBytes
(==) NOUVEAU(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NOUVEAU(0): Virtual size is 1024x768 (pitch 1024)
(**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(**) NOUVEAU(0):  Default mode "800x600": 56.3 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(**) NOUVEAU(0):  Default mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(**) NOUVEAU(0):  Default mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NOUVEAU(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(**) NOUVEAU(0):  Default mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(**) NOUVEAU(0):  Default mode "720x400": 35.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(**) NOUVEAU(0):  Default mode "640x400": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(**) NOUVEAU(0):  Default mode "640x350": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(**) NOUVEAU(0):  Driver mode "1680x1050": 119.0 MHz (scaled from 0.0 MHz), 64.7 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(**) NOUVEAU(0):  Default mode "1600x1024": 103.1 MHz (scaled from 0.0 MHz), 62.0 kHz, 60.2 Hz
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(**) NOUVEAU(0):  Default mode "1400x1050": 122.0 MHz (scaled from 0.0 MHz), 64.9 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(**) NOUVEAU(0):  Default mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(**) NOUVEAU(0):  Default mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(**) NOUVEAU(0):  Default mode "1360x768": 84.8 MHz (scaled from 0.0 MHz), 47.7 kHz, 59.8 Hz
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 121.5 MHz (scaled from 0.0 MHz), 77.5 kHz, 85.1 Hz
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 119.7 MHz (scaled from 0.0 MHz), 77.1 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 105.0 MHz (scaled from 0.0 MHz), 67.6 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 96.8 MHz (scaled from 0.0 MHz), 63.0 kHz, 70.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(**) NOUVEAU(0):  Default mode "1152x864": 81.6 MHz (scaled from 0.0 MHz), 53.7 kHz, 60.0 Hz
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.0 kHz, 75.0 Hz
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(**) NOUVEAU(0):  Default mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(**) NOUVEAU(0): Display dimensions: (430, 270) mm
(**) NOUVEAU(0): DPI set to (60, 72)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules//libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NOUVEAU(0): Opened GPU channel 1
(II) NOUVEAU(0): [drm] Using the DRM lock SAREA also for drawables.
(II) NOUVEAU(0): [drm] framebuffer handle = 0x2fff9000
(II) NOUVEAU(0): [drm] added 1 reserved context for kernel
(II) NOUVEAU(0): X context handle = 0x1
(II) NOUVEAU(0): [drm] installed DRM signal handler
(II) NOUVEAU(0): Allocated 125MiB VRAM for offscreen pixmaps
(II) NOUVEAU(0): AGPGART: 64MiB available
(II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
(II) NOUVEAU(0): Saving VGA fonts
(II) NOUVEAU(0): Saving crtcs
(II) NOUVEAU(0): Saving encoders
(II) EXA(0): Offscreen pixmap area of 131072000 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(II)         UploadToScreen
(II)         DownloadFromScreen
(==) NOUVEAU(0): Backing store disabled
(==) NOUVEAU(0): Silken mouse enabled
(II) NOUVEAU(0): [DRI] installation complete
(II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
(II) NOUVEAU(0): [XvMC] Extension initialized.
(II) NOUVEAU(0): NVEnterVT is called.
(II) NOUVEAU(0): Saving VGA fonts
(II) NOUVEAU(0): Saving crtcs
(II) NOUVEAU(0): Saving encoders
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 0)
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 1)
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 2)
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 3)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): CTRC mode on CRTC 0:
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Output mode on CRTC 0:
(II) NOUVEAU(0): Modeline "1024x768"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): vpll: n 22 m 5 log2p 0
(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): 0xD1FB: Parsing digital output script table
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 0 on tmds encoder (output 1)
(II) NOUVEAU(0): Output DVI-I-0 is running on CRTC 0 using output A
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): CTRC mode on CRTC 1:
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Output mode on CRTC 1:
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): vpll: n 53 m 11 log2p 1
(II) NOUVEAU(0): nv_output_mode_set called for encoder 2
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 2)
(II) NOUVEAU(0): Output DVI-I-1 is running on CRTC 1 using output C
(II) NOUVEAU(0): DPMS enabled
(II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(--) RandR disabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: dlopen of /usr/lib/dri/nouveau_dri.so failed (/usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
(II) GLX: Initialized DRISWRAST GL provider for screen 0
(II) NOUVEAU(0): Setting screen physical size to 434 x 270
resize called 1024 768
(II) config/hal: Adding input device   USB Keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event4"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device   USB Keyboard
(**)   USB Keyboard: always reports core events
(**)   USB Keyboard: Device: "/dev/input/event3"
(II)   USB Keyboard: Found keys
(II)   USB Keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "  USB Keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device Logitech USB Optical Mouse
(**) Logitech USB Optical Mouse: always reports core events
(**) Logitech USB Optical Mouse: Device: "/dev/input/event5"
(II) Logitech USB Optical Mouse: Found 3 mouse buttons
(II) Logitech USB Optical Mouse: Found x and y relative axes
(II) Logitech USB Optical Mouse: Found scroll wheel(s)
(II) Logitech USB Optical Mouse: Configuring as mouse
(**) Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE)
(**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
(**) Logitech USB Optical Mouse: (accel) filter chain progression: 2.00
(**) Logitech USB Optical Mouse: (accel) filter stage 0: 20.00 ms
(**) Logitech USB Optical Mouse: (accel) set acceleration profile 0
(II) Logitech USB Optical Mouse: initialized for relative axes.
(II) NOUVEAU(0): EDID for output DVI-I-0
(II) NOUVEAU(0): Manufacturer: GSM  Model: 4e40  Serial#: 179771
(II) NOUVEAU(0): Year: 2006  Week: 2
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): GTF timings supported
(II) NOUVEAU(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.615
(II) NOUVEAU(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x870@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 85 Hz, H min: 28 H max: 83 kHz, PixClock max 140 MHz
(II) NOUVEAU(0): Monitor name: L203WTX
(II) NOUVEAU(0): Monitor name: 
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff001e6d404e3bbe0200
(II) NOUVEAU(0): 	02100103ee2b1b78eac605a3574a9d25
(II) NOUVEAU(0): 	125054a76b808180714f615945593140
(II) NOUVEAU(0): 	0101010101017c2e90a0601a1e403020
(II) NOUVEAU(0): 	3600b20e1100001a000000fd0038551c
(II) NOUVEAU(0): 	530e000a202020202020000000fc004c
(II) NOUVEAU(0): 	3230335754580a2020202020000000fc
(II) NOUVEAU(0): 	000a2020202020202020202020200099
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Printing probed modes for output DVI-I-0
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): Manufacturer: SNY  Model: 5401  Serial#: 16843009
(II) NOUVEAU(0): Year: 2008  Week: 1
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NOUVEAU(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 57 V max: 63 Hz, H min: 30 H max: 80 kHz, PixClock max 150 MHz
(II) NOUVEAU(0): Monitor name: SONY TV
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff004dd9015401010101
(II) NOUVEAU(0): 	0112010308a05a780a0dc9a057479827
(II) NOUVEAU(0): 	12484c21080081800101010101010101
(II) NOUVEAU(0): 	010101010101023a801871382d40582c
(II) NOUVEAU(0): 	450040846300001e662150b051001b30
(II) NOUVEAU(0): 	4070360040846300001e000000fd0039
(II) NOUVEAU(0): 	3f1e500f000a202020202020000000fc
(II) NOUVEAU(0): 	00534f4e592054560a20202020200080
(II) NOUVEAU(0): EDID vendor "SNY", prod id 21505
(II) NOUVEAU(0): Printing probed modes for output DVI-I-1
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-0
(II) NOUVEAU(0): Manufacturer: GSM  Model: 4e40  Serial#: 179771
(II) NOUVEAU(0): Year: 2006  Week: 2
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): GTF timings supported
(II) NOUVEAU(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.615
(II) NOUVEAU(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x870@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 85 Hz, H min: 28 H max: 83 kHz, PixClock max 140 MHz
(II) NOUVEAU(0): Monitor name: L203WTX
(II) NOUVEAU(0): Monitor name: 
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff001e6d404e3bbe0200
(II) NOUVEAU(0): 	02100103ee2b1b78eac605a3574a9d25
(II) NOUVEAU(0): 	125054a76b808180714f615945593140
(II) NOUVEAU(0): 	0101010101017c2e90a0601a1e403020
(II) NOUVEAU(0): 	3600b20e1100001a000000fd0038551c
(II) NOUVEAU(0): 	530e000a202020202020000000fc004c
(II) NOUVEAU(0): 	3230335754580a2020202020000000fc
(II) NOUVEAU(0): 	000a2020202020202020202020200099
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Printing probed modes for output DVI-I-0
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): Manufacturer: SNY  Model: 5401  Serial#: 16843009
(II) NOUVEAU(0): Year: 2008  Week: 1
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NOUVEAU(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 57 V max: 63 Hz, H min: 30 H max: 80 kHz, PixClock max 150 MHz
(II) NOUVEAU(0): Monitor name: SONY TV
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff004dd9015401010101
(II) NOUVEAU(0): 	0112010308a05a780a0dc9a057479827
(II) NOUVEAU(0): 	12484c21080081800101010101010101
(II) NOUVEAU(0): 	010101010101023a801871382d40582c
(II) NOUVEAU(0): 	450040846300001e662150b051001b30
(II) NOUVEAU(0): 	4070360040846300001e000000fd0039
(II) NOUVEAU(0): 	3f1e500f000a202020202020000000fc
(II) NOUVEAU(0): 	00534f4e592054560a20202020200080
(II) NOUVEAU(0): EDID vendor "SNY", prod id 21505
(II) NOUVEAU(0): Printing probed modes for output DVI-I-1
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-0
(II) NOUVEAU(0): Manufacturer: GSM  Model: 4e40  Serial#: 179771
(II) NOUVEAU(0): Year: 2006  Week: 2
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Digital Display Input
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 43  vert.: 27
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off
(II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): GTF timings supported
(II) NOUVEAU(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.615
(II) NOUVEAU(0): blueX: 0.145 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 720x400@70Hz
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 640x480@75Hz
(II) NOUVEAU(0): 800x600@56Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 800x600@75Hz
(II) NOUVEAU(0): 832x624@75Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): 1024x768@75Hz
(II) NOUVEAU(0): 1280x1024@75Hz
(II) NOUVEAU(0): 1152x870@75Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 85  vid: 22881
(II) NOUVEAU(0): #3: hsize: 800  vsize 600  refresh: 85  vid: 22853
(II) NOUVEAU(0): #4: hsize: 640  vsize 480  refresh: 60  vid: 16433
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  434 x 270 mm
(II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
(II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 56 V max: 85 Hz, H min: 28 H max: 83 kHz, PixClock max 140 MHz
(II) NOUVEAU(0): Monitor name: L203WTX
(II) NOUVEAU(0): Monitor name: 
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff001e6d404e3bbe0200
(II) NOUVEAU(0): 	02100103ee2b1b78eac605a3574a9d25
(II) NOUVEAU(0): 	125054a76b808180714f615945593140
(II) NOUVEAU(0): 	0101010101017c2e90a0601a1e403020
(II) NOUVEAU(0): 	3600b20e1100001a000000fd0038551c
(II) NOUVEAU(0): 	530e000a202020202020000000fc004c
(II) NOUVEAU(0): 	3230335754580a2020202020000000fc
(II) NOUVEAU(0): 	000a2020202020202020202020200099
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Using hsync ranges from config file
(II) NOUVEAU(0): Using vrefresh ranges from config file
(II) NOUVEAU(0): Printing DDC gathered Modelines:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): EDID vendor "GSM", prod id 20032
(II) NOUVEAU(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1080" (monitor doesn't support reduced blanking)
(II) NOUVEAU(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NOUVEAU(0): Printing probed modes for output DVI-I-0
(II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz)
(II) NOUVEAU(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
(II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.1  121.50  1152 1216 1344 1568  864 865 868 911 +hsync -vsync (77.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x85.0  119.65  1152 1224 1352 1552  864 865 868 907 -hsync +vsync (77.1 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.6 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x70.0   96.77  1152 1224 1344 1536  864 865 868 900 -hsync +vsync (63.0 kHz)
(II) NOUVEAU(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.30  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
(II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
(II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "720x400"x85.0   35.50  720 756 828 936  400 401 404 446 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) NOUVEAU(0): Modeline "640x400"x85.1   31.50  640 672 736 832  400 401 404 445 -hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x350"x85.1   31.50  640 672 736 832  350 382 385 445 +hsync -vsync (37.9 kHz)
(II) NOUVEAU(0): EDID for output DVI-I-1
(II) NOUVEAU(0): Manufacturer: SNY  Model: 5401  Serial#: 16843009
(II) NOUVEAU(0): Year: 2008  Week: 1
(II) NOUVEAU(0): EDID Version: 1.3
(II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
(II) NOUVEAU(0): Sync:  Separate
(II) NOUVEAU(0): Max Image Size [cm]: horiz.: 160  vert.: 90
(II) NOUVEAU(0): Gamma: 2.20
(II) NOUVEAU(0): No DPMS capabilities specified; RGB/Color Display
(II) NOUVEAU(0): First detailed timing is preferred mode
(II) NOUVEAU(0): redX: 0.625 redY: 0.340   greenX: 0.280 greenY: 0.595
(II) NOUVEAU(0): blueX: 0.155 blueY: 0.070   whiteX: 0.283 whiteY: 0.298
(II) NOUVEAU(0): Supported established timings:
(II) NOUVEAU(0): 640x480@60Hz
(II) NOUVEAU(0): 800x600@60Hz
(II) NOUVEAU(0): 1024x768@60Hz
(II) NOUVEAU(0): Manufacturer's mask: 0
(II) NOUVEAU(0): Supported standard timings:
(II) NOUVEAU(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
(II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
(II) NOUVEAU(0): Supported detailed timing:
(II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  1600 x 900 mm
(II) NOUVEAU(0): h_active: 1360  h_sync: 1424  h_sync_end 1536 h_blank_end 1792 h_border: 0
(II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 795 v_border: 0
(II) NOUVEAU(0): Ranges: V min: 57 V max: 63 Hz, H min: 30 H max: 80 kHz, PixClock max 150 MHz
(II) NOUVEAU(0): Monitor name: SONY TV
(II) NOUVEAU(0): EDID (in hex):
(II) NOUVEAU(0): 	00ffffffffffff004dd9015401010101
(II) NOUVEAU(0): 	0112010308a05a780a0dc9a057479827
(II) NOUVEAU(0): 	12484c21080081800101010101010101
(II) NOUVEAU(0): 	010101010101023a801871382d40582c
(II) NOUVEAU(0): 	450040846300001e662150b051001b30
(II) NOUVEAU(0): 	4070360040846300001e000000fd0039
(II) NOUVEAU(0): 	3f1e500f000a202020202020000000fc
(II) NOUVEAU(0): 	00534f4e592054560a20202020200080
(II) NOUVEAU(0): EDID vendor "SNY", prod id 21505
(II) NOUVEAU(0): Printing probed modes for output DVI-I-1
(II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) NOUVEAU(0): Modeline "1360x768"x60.0   85.50  1360 1424 1536 1792  768 771 777 795 +hsync +vsync (47.7 kHz)
(II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
resize called 3600 1080
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 1)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): CTRC mode on CRTC 0:
(II) NOUVEAU(0): Modeline "640x480"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Output mode on CRTC 0:
(II) NOUVEAU(0): Modeline "640x480"x60.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): vpll: n 22 m 5 log2p 0
(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): 0xD1FB: Parsing digital output script table
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 0 on tmds encoder (output 1)
(II) NOUVEAU(0): Output DVI-I-0 is running on CRTC 0 using output A
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 2)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): CTRC mode on CRTC 1:
(II) NOUVEAU(0): Modeline "640x480"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): Output mode on CRTC 1:
(II) NOUVEAU(0): Modeline "640x480"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) NOUVEAU(0): vpll: n 53 m 11 log2p 1
(II) NOUVEAU(0): nv_output_mode_set called for encoder 2
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 2)
(II) NOUVEAU(0): Output DVI-I-1 is running on CRTC 1 using output C
(II) NOUVEAU(0): Setting dpms mode 3 on tmds encoder (output 1)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 0
(II) NOUVEAU(0): CTRC mode on CRTC 0:
(II) NOUVEAU(0): Modeline "(null)"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): Output mode on CRTC 0:
(II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
(II) NOUVEAU(0): vpll: n 22 m 5 log2p 0
(II) NOUVEAU(0): nv_output_mode_set called for encoder 1
(II) NOUVEAU(0): 0xD1FB: Parsing digital output script table
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 0
(II) NOUVEAU(0): Setting dpms mode 0 on tmds encoder (output 1)
(II) NOUVEAU(0): Output DVI-I-0 is running on CRTC 0 using output A
(II) NOUVEAU(0): Setting dpms mode 3 on vga encoder (output 2)
(II) NOUVEAU(0): Setting dpms mode 3 on CRTC 1
(II) NOUVEAU(0): CTRC mode on CRTC 1:
(II) NOUVEAU(0): Modeline "(null)"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): Output mode on CRTC 1:
(II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
(II) NOUVEAU(0): vpll: n 11 m 2 log2p 0
(II) NOUVEAU(0): nv_output_mode_set called for encoder 2
(II) NOUVEAU(0): Setting dpms mode 0 on CRTC 1
(II) NOUVEAU(0): Setting dpms mode 0 on vga encoder (output 2)
(II) NOUVEAU(0): Output DVI-I-1 is running on CRTC 1 using output C
(II) NOUVEAU(0): NVLeaveVT is called.
(II) NOUVEAU(0): Restoring encoders
(II) NOUVEAU(0): 0xD1FB: Parsing digital output script table
(II) NOUVEAU(0): 0xD236: Parsing digital output script table
(II) NOUVEAU(0): Restoring crtcs
(II) NOUVEAU(0): Restoring VGA fonts
(II) NOUVEAU(0): Restoring CRTC_OWNER to 4.
(II) Logitech USB Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II)   USB Keyboard: Close
(II) UnloadModule: "evdev"
(II)   USB Keyboard: Close
(II) UnloadModule: "evdev"
(EE) NOUVEAU(0): failed to destroy server context
(II) NOUVEAU(0): [drm] removed 1 reserved context for kernel
(II) NOUVEAU(0): Closed GPU channel 1
 ddxSigGiveUp: Closing log

____________________________________________

/etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Tue Oct 20 21:25:04 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


____________________________________________

ldd /usr/bin/glxinfo

	linux-vdso.so.1 =>  (0x00007fffca1ff000)
	libGL.so.1 => /usr/lib/libGL.so.1 (0x00007fdef24b1000)
	libm.so.6 => /lib/libm.so.6 (0x00007fdef222d000)
	libc.so.6 => /lib/libc.so.6 (0x00007fdef1ebe000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007fdef1b88000)
	libGLcore.so.1 => /usr/lib/libGLcore.so.1 (0x00007fdef072b000)
	libnvidia-tls.so.1 => /usr/lib/tls/libnvidia-tls.so.1 (0x00007fdef27a7000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007fdef0519000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007fdef0315000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fdef26a9000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007fdef00f9000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007fdeefef6000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007fdeefcf1000)

____________________________________________

/usr/bin/lspci -d "10de:*" -v -xxx

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [40] HyperTransport: Host or Secondary Interface
00: de 10 a3 03 06 00 b0 00 a2 00 00 06 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 00 00 00
40: 08 00 01 20 22 00 00 00 10 32 3f 00 03 01 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 21 49 44 44 13 01 00 00 00 00 00 00 10 00 00 00
70: 07 05 22 00 00 00 00 00 81 01 85 01 00 00 00 00
80: 00 00 00 00 00 00 00 00 70 00 00 80 00 00 00 00
90: 1f 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 08 00 00 00 00
b0: cb 10 00 02 00 ff 00 00 00 00 00 00 00 00 00 00
c0: 11 11 00 00 00 33 33 13 03 00 00 00 00 50 07 00
d0: 01 0a 00 00 00 00 00 00 ff ff 71 07 10 00 00 00
e0: 08 00 01 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
f0: 00 e4 ff ff 00 00 00 00 00 00 00 00 00 00 00 00

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 ac 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 10 00 21 21 16 00 11 11 00 00 04 00 00 00
60: 21 08 12 06 de 8f e1 1f 08 42 48 18 22 8f 00 20
70: 10 32 54 0a 10 00 00 00 20 00 00 00 2f 00 3d 01
80: 00 00 00 00 00 00 00 00 00 00 50 3f 90 7f 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 01 00 00 00 80 f9 fd 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 c7 02 28 00 00 00 00 00 00 00 00 00

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 aa 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 00 00 4d e0 20 c1 00 00 02 00 4d e0 12 00
50: 00 00 00 00 4d 20 e0 be 01 00 00 00 4b 20 da be
60: 62 00 10 ce ff ff 00 00 01 00 02 00 ff ff 00 00
70: 02 00 01 00 32 00 10 80 03 2c 1c 80 03 2c 1c 00
80: 00 00 00 80 01 00 00 00 77 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 01 20 00 71 00 00 00 00 31 65 07 00
c0: ff ff ff ff ff bf ff ff 00 00 00 00 77 80 77 00
d0: 00 21 09 00 01 00 00 00 00 00 00 00 00 00 00 00
e0: 80 00 63 00 92 14 00 00 80 00 49 91 64 02 13 00
f0: 1b 1b 1b 1b 00 ff 21 00 99 99 aa aa 00 00 0f 80

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0
00: de 10 a9 03 06 00 a0 00 a1 00 00 05 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 04 20 1c 90 04 20 1c a0
50: 04 18 1c 90 04 20 1c 90 04 28 1c 90 04 18 1c 80
60: 04 20 1c 80 04 28 1c 80 04 30 1c 80 04 38 1c 80
70: 02 20 1c 80 3f 41 30 c0 00 00 00 00 3e 30 40 c9
80: 01 00 00 00 46 30 48 c9 02 1f 1c 80 40 10 00 40
90: 8d da 01 09 00 00 00 00 11 00 00 00 00 00 00 00
a0: 00 00 80 99 80 00 00 00 19 00 a8 61 00 00 00 00
b0: 00 00 00 00 e0 1e 00 00 00 00 02 00 01 8c 01 8c
c0: ff ff ff ff 00 00 00 00 10 00 00 00 00 00 00 00
d0: 00 00 00 00 20 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 10 10 18 00 00 40 01 00 00 00 00 00 00 00

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0
00: de 10 ab 03 06 00 a0 00 a1 00 00 05 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 22 88 10 04 22 80 02 0a a0 00 02 0a a1 10 42 0a
60: 85 08 11 08 84 08 31 02 22 90 b5 18 8c 31 a5 1c
70: 6b a5 b4 12 29 31 51 08 85 10 63 0a a5 90 52 0c
80: 87 18 53 0c 62 04 31 08 00 00 00 00 00 00 00 00
90: 20 80 01 00 43 08 01 00 00 00 00 00 00 00 00 00
a0: 06 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 10 00 00 00 00 00
e0: 01 00 00 00 22 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
	Flags: bus master, 66MHz, fast devsel, latency 0
00: de 10 a8 03 04 00 a0 00 a2 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 10 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b5 03 02 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 f0 0f 3f 00 00 00 00 00 00 00 00 00 00 00 00
50: 03 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b4 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 11 00 00 00
50: 00 00 00 00 60 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: ff ff ff ff ff ff ff ff 10 21 00 00 ac 00 20 00
c0: 10 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 ad 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 01 00 00 3f 44 04 00 00 00 00 00 00 00 00 00
50: 08 f8 f0 a0 0c 0c 04 7e 0c 00 00 00 02 2b 7f 04
60: 65 00 52 00 00 00 00 00 00 00 00 00 33 00 20 00
70: 47 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 3f 63 00 00 00 02 00 00 00 00 00 00 00 2a 0c 55
90: 35 c9 23 30 60 a5 95 45 0d 2e 22 76 03 05 33 0e
a0: 00 00 15 15 f0 11 03 00 20 00 27 20 00 00 00 00
b0: 00 80 00 80 00 80 00 80 00 80 00 80 00 80 00 80
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 31 26 61 24 31 26 61 24 31 26 61 24 31 26 61 24
e0: 03 00 00 00 10 08 71 0f f1 01 00 00 11 11 70 11
f0: 10 18 ff 08 08 10 03 04 01 00 00 00 63 03 77 40

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 ae 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 ff ff 07 00 00 00 00 00 57 f2 00 80
60: 01 01 00 00 10 10 00 00 01 01 00 00 10 10 00 00
70: 01 10 a0 ee 00 00 00 00 01 10 a0 ee 00 00 00 00
80: 01 08 00 13 23 40 f0 03 18 28 80 00 20 60 70 00
90: 13 00 00 18 13 20 00 08 00 20 00 08 00 20 00 08
a0: 00 20 00 08 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 0c 30 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 1b 06 82 81 20 00 00 00 01 01 00 00
d0: 5a 08 00 01 04 00 10 00 00 00 20 00 00 00 30 00
e0: ed 05 c0 4d 5b 05 55 96 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 af 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: d0 00 00 00 00 00 00 00 78 1e 50 84 cb 02 00 06
50: 44 00 00 00 43 00 08 11 ff ff ff ff ff ff 7f ff
60: ff ff 03 04 0e 00 00 00 28 80 78 00 00 00 00 00
70: 01 01 01 01 08 00 b1 3c 0a 22 07 07 50 00 f2 02
80: 95 13 00 00 21 f2 ce fb e1 00 50 00 00 00 00 00
90: 08 00 3f 70 08 00 1f 0c 08 0f 17 00 08 0f 18 00
a0: 50 00 00 00 30 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: ff ff 00 02 00 00 00 00 00 00 00 00 00 00 00 00

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b0 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: ff ff 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 31 51 00 00 66 66 00 00 66 66 00 00 66 66 00 00
70: 66 66 00 00 66 66 00 00 66 66 00 00 ff ff ff ff
80: ff ff dd bb 00 30 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 55 55 55 55 55 55 55 55 99 99 99 99
a0: 22 22 22 22 ae 0a e0 00 08 09 0e 0f 08 09 09 08
b0: 09 09 0b 0c 0b 09 08 08 ff ff 03 00 00 07 00 00
c0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
d0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
e0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
f0: 00 07 00 00 00 07 00 00 00 07 00 00 00 00 00 00

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b1 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 73 7f 00 00 ff ff 03 00 98 3a 30 80 80 01 00 02
50: 00 00 00 00 1f 1f 00 00 0f 0f 0f 0f f0 f1 41 00
60: 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f f0 f1 41 00
70: 0f 0f 0f 0f 0f 0f 0f 0f 07 00 00 00 0f 0f 00 00
80: 0f 0f 00 00 f0 f1 41 00 0f 0f 0f 0f 0f 0f 0f 0f
90: 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f 0f
a0: 0f 0f 0f 0f f0 f1 41 02 0f 0f 0f 0f 0f 0f 0f 0f
b0: 08 06 00 00 44 44 44 11 44 44 44 44 44 44 44 00
c0: 00 00 00 04 00 00 00 04 00 00 00 00 00 00 00 00
d0: 00 00 00 00 0f 0f 00 00 0f 0f 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 44 00 00 00 44 00 00 00
f0: ff ff 00 02 00 00 00 00 0f 0f 0f 0f 0f 0f 0f 0f

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b2 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: f9 01 a0 0a 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b3 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 55 55 55 55 00 00 00 00 55 55 55 55
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 07 00 00 00 07 00 00
80: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
90: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
a0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
b0: 00 07 00 00 00 07 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 07 07 07 07 88 88 88 88 88 88 88 88
d0: 00 00 00 00 00 00 00 00 40 40 40 40 88 88 77 00
e0: 00 07 00 00 00 07 00 00 00 07 00 00 00 07 00 00
f0: 00 00 00 00 88 88 88 88 88 88 88 88 00 01 02 00

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 b6 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 08 00 00 00 00 20 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: da e3 bd 1f ca f5 4f 0c 76 1b e6 c9 92 f1 22 75
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: bus master, 66MHz, fast devsel, latency 0
00: de 10 bc 03 06 00 a0 00 a1 00 00 05 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
	Flags: 66MHz, fast devsel
00: de 10 ba 03 00 00 20 00 a1 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 00 00 00 00 00 00 00 00 ff 00 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: ff ff 0f 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 44 44 44 11 44 44 44 44 44 44 44 00 00 00 00 04
a0: 00 00 00 04 00 00 00 00 00 00 00 00 00 00 00 00
b0: 44 44 44 00 44 04 44 04 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 44 44 44 00 44 04 44 04
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 40 40 40 40 40 40 40 40 40 40 40 40 40 40 40 40
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: f5f00000-f7ffffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: [40] Subsystem: nVidia Corporation Device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00: de 10 b7 03 07 04 10 00 a1 00 04 06 10 00 01 00
10: 00 00 00 00 00 00 00 00 00 01 01 00 d1 d1 00 00
20: f0 f5 f0 f7 01 d0 f1 df 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 00 1a 00
40: 0d 48 00 00 de 10 55 0c 01 50 02 f8 00 00 00 00
50: 05 60 83 00 0c 30 e0 fe 00 00 00 00 49 41 00 00
60: 08 80 00 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 10 00 41 01 01 80 00 00 10 28 00 00 01 35 11 00
90: 00 00 01 31 00 00 00 00 c0 01 48 01 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Capabilities: [40] Subsystem: nVidia Corporation Device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00: de 10 b9 03 04 04 10 00 a1 00 04 06 10 00 01 00
10: 00 00 00 00 00 00 00 00 00 02 02 00 f1 01 00 00
20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 00 02 00
40: 0d 48 00 00 de 10 55 0c 01 50 02 f8 00 00 00 00
50: 05 60 83 00 0c 30 e0 fe 00 00 00 00 51 41 00 00
60: 08 80 00 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 10 00 41 01 01 80 00 00 10 28 00 00 11 34 11 03
90: 10 00 11 10 00 00 00 00 c0 01 49 01 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: [40] Subsystem: nVidia Corporation Device 0c55
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
	Capabilities: [60] HyperTransport: MSI Mapping Enable- Fixed-
	Capabilities: [80] Express Root Port (Slot+), MSI 00
	Capabilities: [100] Virtual Channel <?>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00: de 10 bb 03 04 04 10 00 a1 00 04 06 10 00 01 00
10: 00 00 00 00 00 00 00 00 00 03 03 00 f1 01 00 00
20: f0 ff 00 00 f1 ff 01 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 40 00 00 00 00 00 00 00 00 00 02 00
40: 0d 48 00 00 de 10 55 0c 01 50 02 f8 00 00 00 00
50: 05 60 83 00 0c 30 e0 fe 00 00 00 00 59 41 00 00
60: 08 80 00 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 10 00 41 01 01 80 00 00 10 28 00 00 11 34 11 02
90: 00 00 11 10 00 00 00 00 c0 01 48 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0
	Capabilities: [44] HyperTransport: Slave or Primary Interface
	Capabilities: [e0] HyperTransport: MSI Mapping Enable- Fixed-
00: de 10 70 02 06 00 b0 00 a2 00 00 05 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 00 00 00 00
40: 62 14 50 73 08 e0 e9 01 22 20 00 00 d0 00 00 00
50: 23 00 7f 80 03 00 00 00 00 00 03 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 06 06 05 00
70: 44 44 44 00 50 01 00 00 11 00 00 00 11 11 55 00
80: 23 55 55 00 fa 00 64 0c 03 00 00 00 7f 00 00 00
90: 70 00 00 80 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 01 01 01 01 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 80 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 08 00 00 a8 00 00 e0 fe 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0
	I/O ports at 4f00 [size=128]
00: de 10 60 02 0f 00 a0 00 a3 00 01 06 00 00 80 00
10: 01 4f 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 62 14 50 73 00 00 d0 fe fa 3e ff 00 fa 3e ff 00
50: fa 3e ff 00 00 5a 62 02 00 00 00 01 00 00 fe bf
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 f9 ff
70: 10 00 ff ff cd 00 00 00 00 00 04 19 60 00 0c 00
80: 09 d0 00 12 08 01 00 00 c0 00 00 01 00 00 00 00
90: 00 00 00 00 00 00 00 00 21 47 65 b7 ef cd 00 00
a0: 01 00 10 80 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 0a 7f 0a 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 02 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: 66MHz, fast devsel, IRQ 11
	I/O ports at 5000 [size=64]
	I/O ports at 6000 [size=64]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: nForce2_smbus
	Kernel modules: i2c-nforce2
00: de 10 64 02 01 00 b0 00 a3 00 05 0c 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 01 50 00 00 01 60 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 00 00
40: 62 14 50 73 01 00 02 c0 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 01 40 00 00 01 44 00 00 01 48 00 00 00 00 00 00
70: 01 00 00 00 00 00 00 00 00 00 00 00 01 20 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: d4 30 80 01 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 10 10 04 00 00 a0 00 00 80 38 00 00 46 44 44 11
f0: 5a ff 5f bf 00 00 00 c0 10 00 00 00 00 00 00 00

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: 66MHz, fast devsel
00: de 10 72 02 00 04 a0 00 a3 00 00 05 00 00 80 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
40: 00 00 00 00 00 00 00 00 10 00 00 10 00 00 10 10
50: 10 10 10 10 00 00 00 00 00 00 00 00 00 00 00 00
60: 02 03 00 00 12 00 00 00 02 00 00 00 10 01 12 00
70: 32 33 00 00 03 00 00 00 00 00 00 00 12 01 00 00
80: 10 00 00 00 00 00 00 00 00 00 00 00 30 02 00 00
90: 00 00 00 00 01 20 00 00 01 00 00 00 00 09 00 00
a0: 01 02 00 00 00 10 00 00 05 00 00 00 01 00 00 00
b0: 00 10 00 80 01 00 00 80 00 00 00 00 02 00 00 00
c0: 07 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f5eff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci_hcd
00: de 10 6d 02 07 00 b0 00 a3 10 03 0c 00 00 80 00
10: 00 f0 ef f5 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 05 01 03 01
40: 62 14 50 73 01 00 02 fe 00 00 00 00 00 00 00 00
50: 18 00 00 00 1d 47 40 00 10 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f5efec00 (32-bit, non-prefetchable) [size=256]
	Capabilities: [44] Debug port: BAR=1 offset=0098
	Capabilities: [80] Power Management version 2
	Kernel driver in use: ehci_hcd
00: de 10 6e 02 06 00 b0 00 a3 20 03 0c 00 00 80 00
10: 00 ec ef f5 00 00 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 07 02 03 01
40: 62 14 50 73 0a 80 98 20 00 00 00 00 00 00 00 00
50: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
60: 20 20 01 00 00 60 18 85 03 3c 0a 01 00 00 00 00
70: 00 00 08 05 00 10 20 80 89 3d b6 22 77 25 04 00
80: 01 00 02 fe 00 00 00 00 00 00 00 00 15 16 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 01 00 00 00 00 00 08 c0 00 00 00 00 00 00 00 00
b0: 33 00 11 22 00 00 00 00 ff 00 00 00 00 00 00 00
c0: 10 10 2d 0d 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
	I/O ports at ffa0 [size=16]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: pata_amd
00: de 10 65 02 05 00 b0 00 a1 8a 01 01 00 00 00 00
10: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
20: a1 ff 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 00 00 03 01
40: 62 14 50 73 01 00 02 00 00 00 00 00 00 00 00 00
50: 03 f0 01 00 00 00 00 00 99 20 99 20 22 00 20 20
60: 00 c6 00 c0 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 f7 23 00 00 04 10 00 e0 30 20
90: 00 00 02 14 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 10 00 00 00 00 00 00 00

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	I/O ports at c800 [size=8]
	I/O ports at c480 [size=4]
	I/O ports at c400 [size=8]
	I/O ports at c080 [size=4]
	I/O ports at c000 [size=16]
	Memory at f5efd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: sata_nv
00: de 10 66 02 07 00 b0 00 a1 85 01 01 00 00 00 00
10: 01 c8 00 00 81 c4 00 00 01 c4 00 00 81 c0 00 00
20: 01 c0 00 00 00 d0 ef f5 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 0a 01 03 01
40: 62 14 50 73 01 b0 02 00 00 00 00 00 00 00 00 00
50: 07 00 00 00 00 00 00 00 00 00 00 20 40 00 00 20
60: 00 00 00 c7 51 0c 00 00 00 0f 06 42 00 00 00 00
70: 2c 78 c4 40 01 10 00 00 01 10 00 00 20 00 20 00
80: 00 00 00 c0 00 f0 04 21 00 00 f0 80 9f a4 93 c2
90: 00 00 a1 13 00 00 00 00 06 00 06 10 00 00 01 01
a0: 14 10 00 2c 00 00 00 00 00 00 00 00 33 33 00 02
b0: 05 cc 84 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 0a 00 0a 00 08 00 02 a8
d0: 0a 00 02 0c 42 00 00 00 00 00 00 00 00 00 10 e0
e0: 0a 00 02 0a 42 00 00 00 00 00 00 00 0f 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 0c 00 00 00 00 00

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
	I/O ports at bc00 [size=8]
	I/O ports at b880 [size=4]
	I/O ports at b800 [size=8]
	I/O ports at b480 [size=4]
	I/O ports at b400 [size=16]
	Memory at f5efc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [44] Power Management version 2
	Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
	Capabilities: [cc] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: sata_nv
00: de 10 67 02 07 00 b0 00 a1 85 01 01 00 00 00 00
10: 01 bc 00 00 81 b8 00 00 01 b8 00 00 81 b4 00 00
20: 01 b4 00 00 00 c0 ef f5 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 0b 01 03 01
40: 62 14 50 73 01 b0 02 00 00 00 00 00 00 00 00 00
50: 07 00 00 00 00 00 00 00 00 20 00 20 44 20 00 20
60: 00 c6 00 c7 51 0c 00 00 00 0f 06 42 00 00 00 00
70: 2c 78 c4 40 01 10 00 00 01 10 00 00 20 00 20 00
80: 00 00 00 c0 00 f0 30 21 00 00 08 a0 00 70 e7 23
90: 00 00 10 b0 00 00 00 00 06 00 06 10 00 00 01 01
a0: 14 10 00 2b 00 00 00 00 00 00 00 00 33 33 00 02
b0: 05 cc 84 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 0a 00 0a 00 08 00 02 a8
d0: 0a 00 02 0c 42 00 00 00 00 00 00 00 0f 00 d0 e7
e0: 0a 00 02 0a 42 00 00 00 00 00 00 00 00 00 d0 86
f0: 00 00 00 00 00 00 00 00 00 00 0c 00 00 00 00 00

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01)
	Flags: bus master, 66MHz, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=64
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: f8000000-febfffff
	Capabilities: [b8] Subsystem: nVidia Corporation Device cb84
	Capabilities: [8c] HyperTransport: MSI Mapping Enable- Fixed-
00: de 10 6f 02 07 00 b0 00 a2 01 04 06 00 00 81 00
10: 00 00 00 00 00 00 00 00 00 04 04 40 e0 e0 80 02
20: 00 f8 b0 fe f0 ff 00 00 00 00 00 00 00 00 00 00
30: 00 00 00 00 b8 00 00 00 00 00 00 00 00 00 02 02
40: 00 00 03 00 01 00 02 00 05 00 00 00 00 00 4c 00
50: 00 00 fe bf 00 00 00 00 fe 1f ff 1f 00 00 00 00
60: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 00 00 fe 3f 01 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 08 00 00 a8
90: 00 00 e0 fe 00 00 00 00 00 00 00 00 00 00 00 00
a0: 06 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 ff ff 00 00 0d 8c 00 00 de 10 84 cb
c0: de 10 84 cb 03 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
	Subsystem: Micro-Star International Co., Ltd. Device 7350
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at f5efb000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at b080 [size=8]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: forcedeth
	Kernel modules: forcedeth
00: de 10 69 02 07 00 b0 00 a3 00 80 06 00 00 00 00
10: 00 b0 ef f5 81 b0 00 00 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 62 14 50 73
30: 00 00 00 00 44 00 00 00 00 00 00 00 05 01 01 14
40: 62 14 50 73 01 00 02 fe 00 01 00 00 0b 00 00 10
50: 05 6c 84 01 00 00 00 00 00 00 00 00 00 00 00 00
60: 00 00 00 00 00 00 00 00 0f 00 00 00 08 00 02 a8
70: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
80: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 11 00 00 00 42 01 00 00 00 00 00 00

01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)
	Subsystem: eVga.com. Corp. Device c553
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f7000000 (32-bit, non-prefetchable) [size=16M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at f6000000 (64-bit, non-prefetchable) [size=16M]
	I/O ports at dc00 [size=128]
	[virtual] Expansion ROM at f5fe0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Kernel driver in use: nvidia
	Kernel modules: nouveau, nvidia, nvidiafb
00: de 10 91 03 07 00 10 00 a1 00 00 03 00 00 00 00
10: 00 00 00 f7 0c 00 00 d0 00 00 00 00 04 00 00 f6
20: 00 00 00 00 01 dc 00 00 00 00 00 00 42 38 53 c5
30: 00 00 00 00 60 00 00 00 00 00 00 00 0a 01 00 00
40: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
50: 01 00 00 00 01 00 00 00 ce d6 23 00 00 00 00 00
60: 01 68 02 00 00 00 00 00 05 78 80 00 00 00 00 00
70: 00 00 00 00 00 00 00 00 10 00 01 00 00 05 00 00
80: 10 28 00 00 01 4d 01 00 08 00 01 11 00 00 00 00
90: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
a0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
b0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
c0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
d0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
e0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


____________________________________________

/usr/bin/lspci -t

-[0000:00]-+-00.0
           +-00.1
           +-00.2
           +-00.3
           +-00.4
           +-00.5
           +-00.6
           +-00.7
           +-01.0
           +-01.1
           +-01.2
           +-01.3
           +-01.4
           +-01.5
           +-01.6
           +-02.0
           +-02.1
           +-02.2
           +-03.0-[0000:01]----00.0
           +-06.0-[0000:02]--
           +-07.0-[0000:03]--
           +-09.0
           +-0a.0
           +-0a.1
           +-0a.2
           +-0b.0
           +-0b.1
           +-0d.0
           +-0e.0
           +-0f.0
           +-10.0-[0000:04]----07.0
           \-14.0

____________________________________________

/usr/sbin/dmidecode

# dmidecode 2.9
SMBIOS 2.5 present.
54 structures occupying 1991 bytes.
Table at 0x000FB4F0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: V1.7
	Release Date: 07/29/2008
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 8.13

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: MSI
	Product Name: MS-7350
	Version: 1.0
	Serial Number: To Be Filled By O.E.M.
	UUID: Not Present
	Wake-up Type: Power Switch
	SKU Number: To Be Filled By O.E.M.
	Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: MSI
	Product Name: MS-7350
	Version: 1.0
	Serial Number: To be filled by O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: To Be Filled By O.E.M.
	Type: Desktop
	Lock: Not Present
	Version: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Other
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Unknown
	Manufacturer: Intel            
	ID: F2 06 00 00 FF FB EB BF
	Version: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz     
	Voltage: 1.3 V
	External Clock: 267 MHz
	Max Speed: 1866 MHz
	Current Speed: 1869 MHz
	Status: Populated, Enabled
	Upgrade: Socket 478
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 2
	Core Enabled: 2
	Thread Count: 2
	Characteristics:
		64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 2048 KB
	Maximum Size: 2048 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Disabled, Not Socketed, Level 3
	Operational Mode: Unknown
	Location: Internal
	Installed Size: 0 KB
	Maximum Size: 0 KB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0008, DMI type 5, 24 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 4096 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		SIMM
		DIMM
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 4
		0x0009
		0x000A
		0x000B
		0x000C
	Enabled Error Correcting Capabilities:
		None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 1 0
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM3
	Bank Connections: 3 2
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM2
	Bank Connections: 5 4
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM4
	Bank Connections: 7 6
	Current Speed: Unknown
	Type: Unknown
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS2Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4A1
	Internal Connector Type: None
	External Reference Designator: LPT 1
	External Connector Type: DB-25 male
	Port Type: Parallel Port ECP/EPP

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A1
	Internal Connector Type: None
	External Reference Designator: COM A
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Mic In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Line In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6B1 - AUX IN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6B2 - CDIN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J2 - PRI IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J1 - SEC IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4J1 - FLOPPY
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H1 - FRONT PNL
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1B1 - CHASSIS REAR FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2F1 - CPU FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8B4 - FRONT FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G2 - FNT USB
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6C3 - FP AUD
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G1 - CONFIG
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8C1 - SCSI LED
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9J2 - INTRUDER
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G4 - ITP
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2H1 - MAIN POWER
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x0025, DMI type 9, 13 bytes
System Slot Information
	Designation: PCIE
	Type: 32-bit PCI Express
	Current Usage: Available
	Length: Short
	ID: 0
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0026, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0027, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:   To Be Filled By O.E.M.

Handle 0x0028, DMI type 11, 5 bytes
OEM Strings
	String 1: To Be Filled By O.E.M.

Handle 0x0029, DMI type 12, 5 bytes
System Configuration Options
	Option 1: To Be Filled By O.E.M.

Handle 0x002A, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x002B, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 16 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x002C, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Array Handle: 0x002B
	Partition Width: 0

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK0
	Type: SDRAM
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0

Handle 0x002E, DMI type 126, 19 bytes
Inactive

Handle 0x002F, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM3
	Bank Locator: BANK1
	Type: SDRAM
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1

Handle 0x0030, DMI type 126, 19 bytes
Inactive

Handle 0x0031, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK2
	Type: SDRAM
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer2
	Serial Number: SerNum2
	Asset Tag: AssetTagNum2
	Part Number: PartNum2

Handle 0x0032, DMI type 126, 19 bytes
Inactive

Handle 0x0033, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x002B
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM4
	Bank Locator: BANK3
	Type: SDRAM
	Type Detail: Unknown
	Speed: Unknown
	Manufacturer: Manufacturer3
	Serial Number: SerNum3
	Asset Tag: AssetTagNum3
	Part Number: PartNum3

Handle 0x0034, DMI type 126, 19 bytes
Inactive

Handle 0x0035, DMI type 127, 4 bytes
End Of Table


____________________________________________

/sbin/modinfo nvidia | grep vermagic

vermagic:       2.6.31-14-generic SMP mod_unload modversions 

____________________________________________

Scanning kernel log files for NVRM messages:

  /var/log/messages:
Oct 25 22:29:31 charles-pc kernel: [  883.996998] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
Oct 25 22:32:01 charles-pc kernel: [    7.161051] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
Oct 25 22:33:52 charles-pc kernel: [    6.636208] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  185.18.36  Fri Aug 14 17:35:21 PDT 2009
Oct 27 10:43:52 charles-pc kernel: [   11.958000] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 10:46:00 charles-pc kernel: [    6.634315] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 10:48:48 charles-pc kernel: [    5.496438] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 10:49:54 charles-pc kernel: [    5.900681] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 13:30:36 charles-pc kernel: [    6.423969] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 13:36:03 charles-pc kernel: [    6.769397] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 13:37:37 charles-pc kernel: [    6.484657] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 13:41:59 charles-pc kernel: [   11.554507] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 14:30:02 charles-pc kernel: [    6.455250] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 14:33:39 charles-pc kernel: [    6.297796] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 14:35:07 charles-pc kernel: [    6.453132] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 16:36:35 charles-pc kernel: [  335.527872] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
Oct 27 16:38:14 charles-pc kernel: [    7.344240] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
/var/log/kernel.log is not readable

____________________________________________

dmesg:

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 (Ubuntu 2.6.31-14.48-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffc0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffc0000 - 00000000bffce000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffce000 - 00000000c0000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x140000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-DFFFF uncachable
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F00000000 write-back
[    0.000000]   1 base 100000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FC0000000 uncachable
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000c0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbffc0 max_arch_pfn = 0x400000000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009b000 (usable)
[    0.000000]  modified: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bffc0000 (usable)
[    0.000000]  modified: 00000000bffc0000 - 00000000bffce000 (ACPI data)
[    0.000000]  modified: 00000000bffce000 - 00000000c0000000 (ACPI NVS)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000]  modified: 0000000100000000 - 0000000140000000 (usable)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bffc0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bffc0000 page 4k
[    0.000000] kernel direct mapping tables up to bffc0000 @ 10000-15000
[    0.000000] init_memory_mapping: 0000000100000000-0000000140000000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0100000000 - 0140000000 page 2M
[    0.000000] kernel direct mapping tables up to 140000000 @ 13000-19000
[    0.000000] RAMDISK: 3786f000 - 37fefd5f
[    0.000000] ACPI: RSDP 00000000000f8f30 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 00000000bffc0000 0003C (v01 A M I  OEMRSDT  07000829 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bffc0200 00084 (v02 A M I  OEMFACP  07000829 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bffc0450 0480B (v01  1ADKV 1ADKV000 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bffce000 00040
[    0.000000] ACPI: APIC 00000000bffc0390 00080 (v01 A M I  OEMAPIC  07000829 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bffc0410 0003C (v01 A M I  OEMMCFG  07000829 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bffce040 00061 (v01 A M I  AMI_OEM  07000829 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bffc4c60 00038 (v01 A M I  OEMHPET0 07000829 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000bffce4b0 00A7C (v01 DpgPmm    CpuPm 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000140000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
[    0.000000]   NODE_DATA [0000000000014000 - 0000000000018fff]
[    0.000000]   bootmap [0000000000019000 -  0000000000040fff] pages 28
[    0.000000] (8 early reservations) ==> bootmem [0000000000 - 0140000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e2ccc]    TEXT DATA BSS ==> [0001000000 - 00019e2ccc]
[    0.000000]   #3 [003786f000 - 0037fefd5f]          RAMDISK ==> [003786f000 - 0037fefd5f]
[    0.000000]   #4 [000009b000 - 0000100000]    BIOS reserved ==> [000009b000 - 0000100000]
[    0.000000]   #5 [00019e3000 - 00019e3180]              BRK ==> [00019e3000 - 00019e3180]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000]   #7 [0000013000 - 0000014000]          PGTABLE ==> [0000013000 - 0000014000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00045fffff] PMD -> [ffff880028600000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00140000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000bffc0
[    0.000000]     0: 0x00100000 -> 0x00140000
[    0.000000] On node 0 totalpages: 1048395
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 108 pages reserved
[    0.000000]   DMA zone: 3815 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 767992 pages, LIFO batch:31
[    0.000000]   Normal zone: 3584 pages used for memmap
[    0.000000]   Normal zone: 258560 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000bffc0000 - 00000000bffce000
[    0.000000] PM: Registered nosave memory: 00000000bffce000 - 00000000c0000000
[    0.000000] PM: Registered nosave memory: 00000000c0000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff80000
[    0.000000] PM: Registered nosave memory: 00000000fff80000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ec00000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff880028022000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1030367
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.000000] Placing 64MB software IO TLB between ffff880020000000 - ffff880024000000
[    0.000000] software IO TLB at phys 0x20000000 - 0x24000000
[    0.000000] Memory: 4051756k/5242880k available (5313k kernel code, 1049300k absent, 141824k reserved, 3011k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1866.275 MHz processor.
[    0.000016] spurious 8259A interrupt: IRQ7.
[    0.001269] Console: colour VGA+ 80x25
[    0.001272] console [tty0] enabled
[    0.010000] allocated 41943040 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3732.55 BogoMIPS (lpj=18662750)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010000] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM1)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.012462] Setting APIC routing to flat
[    0.013003] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.112998] CPU0: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[    0.120000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 3733.35 BogoMIPS (lpj=18666786)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 2048K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM1)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.271137] CPU1: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz stepping 02
[    0.271148] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.280020] Brought up 2 CPUs
[    0.280024] Total of 2 processors activated (7465.90 BogoMIPS).
[    0.280130] CPU0 attaching sched-domain:
[    0.280133]  domain 0: span 0-1 level MC
[    0.280135]   groups: 0 1
[    0.280141] CPU1 attaching sched-domain:
[    0.280144]  domain 0: span 0-1 level MC
[    0.280146]   groups: 1 0
[    0.280218] Booting paravirtualized kernel on bare hardware
[    0.280218] regulator: core version 0.5
[    0.280218] Time: 20:38:06  Date: 10/27/09
[    0.280218] NET: Registered protocol family 16
[    0.280230] ACPI: bus type pci registered
[    0.280301] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.280304] PCI: Not using MMCONFIG.
[    0.280306] PCI: Using configuration type 1 for base access
[    0.281238] bio: create slab <bio-0> at 0
[    0.281238] ACPI: EC: Look up EC in DSDT
[    0.292188] ACPI: Interpreter enabled
[    0.292191] ACPI: (supports S0 S1 S3 S4 S5)
[    0.292216] ACPI: Using IOAPIC for interrupt routing
[    0.292267] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.296652] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.304365] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.312630] ACPI Warning: Incorrect checksum in table [OEMB] - E1, should be E0 20090521 tbutils-246
[    0.312767] ACPI: No dock devices found.
[    0.312883] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.313802] pci 0000:00:03.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313806] pci 0000:00:03.0: PME# disabled
[    0.313862] pci 0000:00:06.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313865] pci 0000:00:06.0: PME# disabled
[    0.313917] pci 0000:00:07.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.313921] pci 0000:00:07.0: PME# disabled
[    0.314178] pci 0000:00:0a.0: reg 10 io port: [0x4f00-0x4f7f]
[    0.314294] pci 0000:00:0a.1: reg 20 io port: [0x5000-0x503f]
[    0.314302] pci 0000:00:0a.1: reg 24 io port: [0x6000-0x603f]
[    0.314341] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.314348] pci 0000:00:0a.1: PME# disabled
[    0.314472] pci 0000:00:0b.0: reg 10 32bit mmio: [0xf5eff000-0xf5efffff]
[    0.314532] pci 0000:00:0b.0: supports D1 D2
[    0.314534] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.314539] pci 0000:00:0b.0: PME# disabled
[    0.314589] pci 0000:00:0b.1: reg 10 32bit mmio: [0xf5efec00-0xf5efecff]
[    0.314655] pci 0000:00:0b.1: supports D1 D2
[    0.314657] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.314662] pci 0000:00:0b.1: PME# disabled
[    0.314742] pci 0000:00:0d.0: reg 20 io port: [0xffa0-0xffaf]
[    0.314832] pci 0000:00:0e.0: reg 10 io port: [0xc800-0xc807]
[    0.314840] pci 0000:00:0e.0: reg 14 io port: [0xc480-0xc483]
[    0.314848] pci 0000:00:0e.0: reg 18 io port: [0xc400-0xc407]
[    0.314856] pci 0000:00:0e.0: reg 1c io port: [0xc080-0xc083]
[    0.314864] pci 0000:00:0e.0: reg 20 io port: [0xc000-0xc00f]
[    0.314872] pci 0000:00:0e.0: reg 24 32bit mmio: [0xf5efd000-0xf5efdfff]
[    0.314973] pci 0000:00:0f.0: reg 10 io port: [0xbc00-0xbc07]
[    0.314981] pci 0000:00:0f.0: reg 14 io port: [0xb880-0xb883]
[    0.314989] pci 0000:00:0f.0: reg 18 io port: [0xb800-0xb807]
[    0.314997] pci 0000:00:0f.0: reg 1c io port: [0xb480-0xb483]
[    0.315005] pci 0000:00:0f.0: reg 20 io port: [0xb400-0xb40f]
[    0.315013] pci 0000:00:0f.0: reg 24 32bit mmio: [0xf5efc000-0xf5efcfff]
[    0.315198] pci 0000:00:14.0: reg 10 32bit mmio: [0xf5efb000-0xf5efbfff]
[    0.315206] pci 0000:00:14.0: reg 14 io port: [0xb080-0xb087]
[    0.315257] pci 0000:00:14.0: supports D1 D2
[    0.315259] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.315264] pci 0000:00:14.0: PME# disabled
[    0.315324] pci 0000:01:00.0: reg 10 32bit mmio: [0xf7000000-0xf7ffffff]
[    0.315333] pci 0000:01:00.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.315342] pci 0000:01:00.0: reg 1c 64bit mmio: [0xf6000000-0xf6ffffff]
[    0.315348] pci 0000:01:00.0: reg 24 io port: [0xdc00-0xdc7f]
[    0.315353] pci 0000:01:00.0: reg 30 32bit mmio: [0xf5fe0000-0xf5ffffff]
[    0.315444] pci 0000:00:03.0: bridge io port: [0xd000-0xdfff]
[    0.315447] pci 0000:00:03.0: bridge 32bit mmio: [0xf5f00000-0xf7ffffff]
[    0.315452] pci 0000:00:03.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.315666] pci 0000:04:07.0: reg 10 io port: [0xec00-0xec1f]
[    0.315683] pci 0000:04:07.0: reg 14 64bit mmio: [0xfea00000-0xfebfffff]
[    0.315699] pci 0000:04:07.0: reg 1c 64bit mmio: [0xf8000000-0xfbffffff]
[    0.315746] pci 0000:04:07.0: supports D1 D2
[    0.315804] pci 0000:00:10.0: transparent bridge
[    0.315808] pci 0000:00:10.0: bridge io port: [0xe000-0xefff]
[    0.315813] pci 0000:00:10.0: bridge 32bit mmio: [0xf8000000-0xfebfffff]
[    0.315836] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.316076] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.316203] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[    0.316271] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PB._PRT]
[    0.316336] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.329159] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.329372] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *10
[    0.329578] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.329783] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.330002] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *10
[    0.330211] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.330416] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.330620] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.330824] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *5
[    0.331028] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *7
[    0.331239] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[    0.331449] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *0, disabled.
[    0.331653] ACPI: PCI Interrupt Link [LACI] (IRQs 20 21 22 23) *0, disabled.
[    0.331857] ACPI: PCI Interrupt Link [LMC9] (IRQs 20 21 22 23) *0, disabled.
[    0.332061] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.332264] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.332467] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *10
[    0.332677] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *11
[    0.332923] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.333110] SCSI subsystem initialized
[    0.333140] libata version 3.00 loaded.
[    0.333140] usbcore: registered new interface driver usbfs
[    0.333140] usbcore: registered new interface driver hub
[    0.333140] usbcore: registered new device driver usb
[    0.333140] ACPI: WMI: Mapper loaded
[    0.333140] PCI: Using ACPI for IRQ routing
[    0.360009] Bluetooth: Core ver 2.15
[    0.360027] NET: Registered protocol family 31
[    0.360027] Bluetooth: HCI device and connection manager initialized
[    0.360027] Bluetooth: HCI socket layer initialized
[    0.360027] NetLabel: Initializing
[    0.360027] NetLabel:  domain hash size = 128
[    0.360027] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.360043] NetLabel:  unlabeled traffic allowed by default
[    0.360110] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.360117] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.400095] pnp: PnP ACPI init
[    0.400109] ACPI: bus type pnp registered
[    0.404564] pnp: PnP ACPI: found 14 devices
[    0.404567] ACPI: ACPI bus type pnp unregistered
[    0.404580] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.404584] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.404587] system 00:06: ioport range 0x4000-0x407f has been reserved
[    0.404590] system 00:06: ioport range 0x4080-0x40ff has been reserved
[    0.404593] system 00:06: ioport range 0x4400-0x447f has been reserved
[    0.404596] system 00:06: ioport range 0x4480-0x44ff has been reserved
[    0.404600] system 00:06: ioport range 0x4800-0x487f has been reserved
[    0.404603] system 00:06: ioport range 0x4880-0x48ff has been reserved
[    0.404609] system 00:06: ioport range 0x2000-0x207f has been reserved
[    0.404612] system 00:06: ioport range 0x2080-0x20ff has been reserved
[    0.404616] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.404623] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.404626] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.404632] system 00:0b: ioport range 0xa00-0xadf has been reserved
[    0.404635] system 00:0b: ioport range 0xae0-0xaef has been reserved
[    0.404641] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.404647] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.404650] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.404653] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.404656] system 00:0d: iomem range 0x100000-0xbfffffff could not be reserved
[    0.404660] system 00:0d: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.409370] AppArmor: AppArmor Filesystem Enabled
[    0.409418] pci 0000:00:03.0: PCI bridge, secondary bus 0000:01
[    0.409422] pci 0000:00:03.0:   IO window: 0xd000-0xdfff
[    0.409426] pci 0000:00:03.0:   MEM window: 0xf5f00000-0xf7ffffff
[    0.409430] pci 0000:00:03.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.409435] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.409437] pci 0000:00:06.0:   IO window: disabled
[    0.409441] pci 0000:00:06.0:   MEM window: disabled
[    0.409444] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.409447] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.409449] pci 0000:00:07.0:   IO window: disabled
[    0.409453] pci 0000:00:07.0:   MEM window: disabled
[    0.409456] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.409459] pci 0000:00:10.0: PCI bridge, secondary bus 0000:04
[    0.409463] pci 0000:00:10.0:   IO window: 0xe000-0xefff
[    0.409469] pci 0000:00:10.0:   MEM window: 0xf8000000-0xfebfffff
[    0.409474] pci 0000:00:10.0:   PREFETCH window: disabled
[    0.409486] pci 0000:00:03.0: setting latency timer to 64
[    0.409492] pci 0000:00:06.0: setting latency timer to 64
[    0.409498] pci 0000:00:07.0: setting latency timer to 64
[    0.409505] pci 0000:00:10.0: setting latency timer to 64
[    0.409510] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.409513] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.409516] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.409518] pci_bus 0000:01: resource 1 mem: [0xf5f00000-0xf7ffffff]
[    0.409521] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.409524] pci_bus 0000:04: resource 0 io:  [0xe000-0xefff]
[    0.409526] pci_bus 0000:04: resource 1 mem: [0xf8000000-0xfebfffff]
[    0.409529] pci_bus 0000:04: resource 3 io:  [0x00-0xffff]
[    0.409531] pci_bus 0000:04: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.409568] NET: Registered protocol family 2
[    0.409762] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.411182] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.414786] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.415237] TCP: Hash tables configured (established 524288 bind 65536)
[    0.415240] TCP reno registered
[    0.415367] NET: Registered protocol family 1
[    0.415438] Trying to unpack rootfs image as initramfs...
[    0.501285] Switched to high resolution mode on CPU 1
[    0.510124] Switched to high resolution mode on CPU 0
[    0.611054] Freeing initrd memory: 7683k freed
[    0.614462] Scanning for low memory corruption every 60 seconds
[    0.614612] audit: initializing netlink socket (disabled)
[    0.614629] type=2000 audit(1256675885.610:1): initialized
[    0.625899] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.627437] VFS: Disk quotas dquot_6.5.2
[    0.627498] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.628128] fuse init (API version 7.12)
[    0.628214] msgmni has been set to 7928
[    0.628437] alg: No test for stdrng (krng)
[    0.628451] io scheduler noop registered
[    0.628454] io scheduler anticipatory registered
[    0.628456] io scheduler deadline registered
[    0.628497] io scheduler cfq registered (default)
[    0.640157] pci 0000:01:00.0: Boot video device
[    0.640364]   alloc irq_desc for 24 on node 0
[    0.640366]   alloc kstat_irqs on node 0
[    0.640375] pcieport-driver 0000:00:03.0: irq 24 for MSI/MSI-X
[    0.640382] pcieport-driver 0000:00:03.0: setting latency timer to 64
[    0.640513]   alloc irq_desc for 25 on node 0
[    0.640515]   alloc kstat_irqs on node 0
[    0.640522] pcieport-driver 0000:00:06.0: irq 25 for MSI/MSI-X
[    0.640528] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    0.640657]   alloc irq_desc for 26 on node 0
[    0.640660]   alloc kstat_irqs on node 0
[    0.640666] pcieport-driver 0000:00:07.0: irq 26 for MSI/MSI-X
[    0.640672] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    0.640754] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.640783] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.640914] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.640918] ACPI: Power Button [PWRF]
[    0.640981] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.640984] ACPI: Power Button [PWRB]
[    0.641607] ACPI: SSDT 00000000bffce0b0 001F3 (v01 DpgPmm  P001Ist 00000011 INTL 20051117)
[    0.641901] processor LNXCPU:00: registered as cooling_device0
[    0.642264] ACPI: SSDT 00000000bffce2b0 001F3 (v01 DpgPmm  P002Ist 00000012 INTL 20051117)
[    0.642545] processor LNXCPU:01: registered as cooling_device1
[    0.647271] Linux agpgart interface v0.103
[    0.647280] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.647417] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.647738] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.648850] brd: module loaded
[    0.649315] loop: module loaded
[    0.649388] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.649665] sata_nv 0000:00:0e.0: version 3.5
[    0.649957] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    0.649962]   alloc irq_desc for 23 on node 0
[    0.649963]   alloc kstat_irqs on node 0
[    0.649969] sata_nv 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    0.649972] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    0.650038] sata_nv 0000:00:0e.0: setting latency timer to 64
[    0.650162] scsi0 : sata_nv
[    0.650250] scsi1 : sata_nv
[    0.650392] ata1: SATA max UDMA/133 cmd 0xc800 ctl 0xc480 bmdma 0xc000 irq 23
[    0.650396] ata2: SATA max UDMA/133 cmd 0xc400 ctl 0xc080 bmdma 0xc008 irq 23
[    0.650720] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[    0.650723]   alloc irq_desc for 22 on node 0
[    0.650725]   alloc kstat_irqs on node 0
[    0.650730] sata_nv 0000:00:0f.0: PCI INT A -> Link[LSA1] -> GSI 22 (level, low) -> IRQ 22
[    0.650732] sata_nv 0000:00:0f.0: Using SWNCQ mode
[    0.650771] sata_nv 0000:00:0f.0: setting latency timer to 64
[    0.650886] scsi2 : sata_nv
[    0.650950] scsi3 : sata_nv
[    0.651091] ata3: SATA max UDMA/133 cmd 0xbc00 ctl 0xb880 bmdma 0xb400 irq 22
[    0.651095] ata4: SATA max UDMA/133 cmd 0xb800 ctl 0xb480 bmdma 0xb408 irq 22
[    0.651322] pata_amd 0000:00:0d.0: version 0.4.1
[    0.651357] pata_amd 0000:00:0d.0: setting latency timer to 64
[    0.651435] scsi4 : pata_amd
[    0.651498] scsi5 : pata_amd
[    0.653010] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.653014] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.653771] Fixed MDIO Bus: probed
[    0.653806] PPP generic driver version 2.4.2
[    0.653910] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.654235] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 21
[    0.654238]   alloc irq_desc for 21 on node 0
[    0.654240]   alloc kstat_irqs on node 0
[    0.654245] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[LUB2] -> GSI 21 (level, low) -> IRQ 21
[    0.654257] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.654261] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.654312] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.654346] ehci_hcd 0000:00:0b.1: debug port 1
[    0.654353] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    0.654372] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xf5efec00
[    0.670052] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.670144] usb usb1: configuration #1 chosen from 1 choice
[    0.670181] hub 1-0:1.0: USB hub found
[    0.670190] hub 1-0:1.0: 8 ports detected
[    0.670278] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.670606] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[    0.670610]   alloc irq_desc for 20 on node 0
[    0.670612]   alloc kstat_irqs on node 0
[    0.670617] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[LUB0] -> GSI 20 (level, low) -> IRQ 20
[    0.670628] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.670632] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.670665] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.670691] ohci_hcd 0000:00:0b.0: irq 20, io mem 0xf5eff000
[    0.732120] usb usb2: configuration #1 chosen from 1 choice
[    0.732150] hub 2-0:1.0: USB hub found
[    0.732160] hub 2-0:1.0: 8 ports detected
[    0.732240] uhci_hcd: USB Universal Host Controller Interface driver
[    0.732353] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.734578] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.734585] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.734658] mice: PS/2 mouse device common for all mice
[    0.734760] rtc_cmos 00:02: RTC can wake from S4
[    0.734794] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.734833] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    0.734929] device-mapper: uevent: version 1.0.3
[    0.735013] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.735084] device-mapper: multipath: version 1.1.0 loaded
[    0.735088] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.735256] cpuidle: using governor ladder
[    0.735258] cpuidle: using governor menu
[    0.735667] TCP cubic registered
[    0.735796] NET: Registered protocol family 10
[    0.736255] lo: Disabled Privacy Extensions
[    0.736554] NET: Registered protocol family 17
[    0.736572] Bluetooth: L2CAP ver 2.13
[    0.736575] Bluetooth: L2CAP socket layer initialized
[    0.736578] Bluetooth: SCO (Voice Link) ver 0.6
[    0.736580] Bluetooth: SCO socket layer initialized
[    0.736613] Bluetooth: RFCOMM TTY layer initialized
[    0.736616] Bluetooth: RFCOMM socket layer initialized
[    0.736618] Bluetooth: RFCOMM ver 1.11
[    0.737216] PM: Resume from disk failed.
[    0.737229] registered taskstats version 1
[    0.737380]   Magic number: 13:756:650
[    0.737386] scsi_host host4: hash matches
[    0.737389] scsi host4: hash matches
[    0.737428] processor LNXCPU:03: hash matches
[    0.737466] rtc_cmos 00:02: setting system clock to 2009-10-27 20:38:06 UTC (1256675886)
[    0.737469] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.737471] EDD information not available.
[    0.810100] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.811345] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    0.830795] ata5.00: ATAPI: LITE-ON LTR-48246S, SS0E, max UDMA/33
[    0.830815] ata5: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc000c600) ACPI=0x701f (60:900:0x11)
[    0.831098] ata3.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    0.831102] ata3.00: 488397168 sectors, multi 16: LBA48 
[    0.831734] ata1.00: ATA-7: WDC WD2500KS-00MJB0, 02.01C03, max UDMA/133
[    0.831737] ata1.00: 488397168 sectors, multi 16: LBA48 
[    0.871137] ata3.00: configured for UDMA/133
[    0.871187] ata1.00: configured for UDMA/133
[    0.871219] ata5.00: configured for UDMA/33
[    0.871296] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[    0.871416] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.871455] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.871503] sd 0:0:0:0: [sda] Write Protect is off
[    0.871506] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.871532] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.871668]  sda:
[    0.882939] ata2: SATA link down (SStatus 0 SControl 300)
[    0.882959]  sda1 sda2 sda3
[    0.883022] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500KS-00M 02.0 PQ: 0 ANSI: 5
[    0.883128] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    0.883163] sd 2:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    0.883210] sd 2:0:0:0: [sdb] Write Protect is off
[    0.883213] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.883239] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.883358]  sdb: sdb1
[    0.893751] sd 2:0:0:0: [sdb] Attached SCSI disk
[    0.897558] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.990055] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    1.040099] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.060357] ata4.00: ATAPI: ATAPI   iHAS422   8, 4L11, max UDMA/100
[    1.100348] ata4.00: configured for UDMA/100
[    1.102770] scsi 3:0:0:0: CD-ROM            ATAPI    iHAS422   8      4L11 PQ: 0 ANSI: 5
[    1.109287] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.109291] Uniform CD-ROM driver Revision: 3.20
[    1.109377] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.109429] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.120944] scsi 4:0:0:0: CD-ROM            LITE-ON  LTR-48246S       SS0E PQ: 0 ANSI: 5
[    1.140927] usb 1-2: configuration #1 chosen from 1 choice
[    1.141047] hub 1-2:1.0: USB hub found
[    1.141126] hub 1-2:1.0: 7 ports detected
[    1.141249] hub 1-2:1.0: insufficient power available to use all downstream ports
[    1.169531] sr1: scsi3-mmc drive: 221x/48x writer cd/rw xa/form2 cdda tray
[    1.169611] sr 4:0:0:0: Attached scsi CD-ROM sr1
[    1.169656] sr 4:0:0:0: Attached scsi generic sg3 type 5
[    1.367923] ata6.00: ATA-7: ST3400620A, 3.AAE, max UDMA/100
[    1.367927] ata6.00: 781422768 sectors, multi 16: LBA48 
[    1.367949] ata6: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc000c600) ACPI=0x3f01f (20:900:0x11)
[    1.451303] ata6.00: configured for UDMA/100
[    1.451383] scsi 5:0:0:0: Direct-Access     ATA      ST3400620A       3.AA PQ: 0 ANSI: 5
[    1.451516] sd 5:0:0:0: [sdc] 781422768 512-byte logical blocks: (400 GB/372 GiB)
[    1.451522] sd 5:0:0:0: Attached scsi generic sg4 type 0
[    1.451566] sd 5:0:0:0: [sdc] Write Protect is off
[    1.451569] sd 5:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.451595] sd 5:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.451721]  sdc: sdc1
[    1.491169] sd 5:0:0:0: [sdc] Attached SCSI disk
[    1.491197] Freeing unused kernel memory: 660k freed
[    1.491408] Write protecting the kernel read-only data: 7580k
[    1.604807] usb 2-4: new low speed USB device using ohci_hcd and address 2
[    1.616638] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.616962] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 23
[    1.616968] forcedeth 0000:00:14.0: PCI INT A -> Link[LMAC] -> GSI 23 (level, low) -> IRQ 23
[    1.616974] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.617026] nv_probe: set workaround bit for reversed mac addr
[    1.843382] usb 2-4: configuration #1 chosen from 1 choice
[    1.851226] usbcore: registered new interface driver hiddev
[    1.864639] input:   USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.0/input/input3
[    1.864707] generic-usb 0003:1241:1603.0001: input,hidraw0: USB HID v1.10 Keyboard [  USB Keyboard] on usb-0000:00:0b.0-4/input0
[    1.889382] input:   USB Keyboard as /devices/pci0000:00/0000:00:0b.0/usb2/2-4/2-4:1.1/input/input4
[    1.889449] generic-usb 0003:1241:1603.0002: input,hidraw1: USB HID v1.10 Device [  USB Keyboard] on usb-0000:00:0b.0-4/input1
[    1.889468] usbcore: registered new interface driver usbhid
[    1.889471] usbhid: v2.6:USB HID core driver
[    2.141197] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:19:db:4c:cf:40
[    2.141202] forcedeth 0000:00:14.0: highdma pwrctl gbit lnktim desc-v3
[    2.180780] usb 2-5: new low speed USB device using ohci_hcd and address 3
[    2.406487] usb 2-5: configuration #1 chosen from 1 choice
[    2.416671] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:0b.0/usb2/2-5/2-5:1.0/input/input5
[    2.416745] generic-usb 0003:046D:C018.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:0b.0-5/input0
[    2.500150] usb 1-2.6: new high speed USB device using ehci_hcd and address 5
[    2.633487] usb 1-2.6: rejected 1 configuration due to insufficient available bus power
[    2.633490] usb 1-2.6: no configuration chosen from 1 choice
[    3.276375] PM: Starting manual resume from disk
[    3.276379] PM: Resume from partition 8:2
[    3.276381] PM: Checking hibernation image.
[    3.276534] PM: Resume from disk failed.
[    3.296527] EXT4-fs (sda1): barriers enabled
[    3.309821] kjournald2 starting: pid 450, dev sda1:8, commit interval 5 seconds
[    3.309840] EXT4-fs (sda1): delayed allocation enabled
[    3.309844] EXT4-fs: file extents enabled
[    3.311918] EXT4-fs: mballoc enabled
[    3.311933] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.793530] type=1505 audit(1256675889.553:2): operation="profile_load" pid=473 name=/usr/share/gdm/guest-session/Xsession
[    3.804009] type=1505 audit(1256675889.563:3): operation="profile_load" pid=474 name=/sbin/dhclient3
[    3.804835] type=1505 audit(1256675889.563:4): operation="profile_load" pid=474 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    3.805248] type=1505 audit(1256675889.563:5): operation="profile_load" pid=474 name=/usr/lib/connman/scripts/dhclient-script
[    3.841739] type=1505 audit(1256675889.603:6): operation="profile_load" pid=475 name=/usr/bin/evince
[    3.853667] type=1505 audit(1256675889.613:7): operation="profile_load" pid=475 name=/usr/bin/evince-previewer
[    3.860706] type=1505 audit(1256675889.613:8): operation="profile_load" pid=475 name=/usr/bin/evince-thumbnailer
[    3.877354] type=1505 audit(1256675889.633:9): operation="profile_load" pid=477 name=/usr/lib/cups/backend/cups-pdf
[    3.878285] type=1505 audit(1256675889.633:10): operation="profile_load" pid=477 name=/usr/sbin/cupsd
[    4.864291] Adding 8418052k swap on /dev/sda2.  Priority:-1 extents:1 across:8418052k 
[    4.980403] EXT4-fs (sda1): internal journal on sda1:8
[    5.126492] udev: starting version 147
[    5.482033] EXT4-fs (sdc1): barriers enabled
[    5.505077] kjournald2 starting: pid 720, dev sdc1:8, commit interval 5 seconds
[    5.505229] EXT4-fs (sdc1): internal journal on sdc1:8
[    5.505233] EXT4-fs (sdc1): delayed allocation enabled
[    5.505237] EXT4-fs: file extents enabled
[    5.517114] EXT4-fs: mballoc enabled
[    5.517129] EXT4-fs (sdc1): mounted filesystem with ordered data mode
[    5.522580] EXT4-fs (sdb1): barriers enabled
[    5.522950] kjournald2 starting: pid 722, dev sdb1:8, commit interval 5 seconds
[    5.523162] EXT4-fs (sdb1): internal journal on sdb1:8
[    5.523167] EXT4-fs (sdb1): delayed allocation enabled
[    5.523170] EXT4-fs: file extents enabled
[    5.538694] EXT4-fs: mballoc enabled
[    5.538712] EXT4-fs (sdb1): mounted filesystem with ordered data mode
[    5.711022] EXT4-fs (sda3): barriers enabled
[    5.732050] kjournald2 starting: pid 741, dev sda3:8, commit interval 5 seconds
[    5.732325] EXT4-fs (sda3): internal journal on sda3:8
[    5.732329] EXT4-fs (sda3): delayed allocation enabled
[    5.732332] EXT4-fs: file extents enabled
[    5.748751] EXT4-fs: mballoc enabled
[    5.748765] EXT4-fs (sda3): mounted filesystem with ordered data mode
[    6.567646] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x5000
[    6.567669] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x6000
[    7.088727] nvidia: module license 'NVIDIA' taints kernel.
[    7.088731] Disabling lock debugging due to kernel taint
[    7.175065] lp: driver loaded but no devices found
[    7.344005] ACPI: PCI Interrupt Link [LNEA] enabled at IRQ 19
[    7.344010]   alloc irq_desc for 19 on node 0
[    7.344013]   alloc kstat_irqs on node 0
[    7.344020] nvidia 0000:01:00.0: PCI INT A -> Link[LNEA] -> GSI 19 (level, low) -> IRQ 19
[    7.344027] nvidia 0000:01:00.0: setting latency timer to 64
[    7.344240] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
[    7.573381] [drm] Initialized drm 1.1.0 20060810
[    7.705855] nvidia 0000:01:00.0: setting latency timer to 64
[    7.708430] nouveau 0000:01:00.0: Detected an NV40 generation card (0x04b100a2)
[    7.708922] [drm] Initialized nouveau 0.0.15 v2.6.31-rc6-539-ged53f9fcabd42f004 for 0000:01:00.0 on minor 0
[    8.205621] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 18
[    8.205627]   alloc irq_desc for 18 on node 0
[    8.205629]   alloc kstat_irqs on node 0
[    8.205636] SB-XFi 0000:04:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[    9.843169] __ratelimit: 3 callbacks suppressed
[    9.843172] type=1505 audit(1256675895.602:12): operation="profile_replace" pid=958 name=/usr/share/gdm/guest-session/Xsession
[    9.844958] type=1505 audit(1256675895.602:13): operation="profile_replace" pid=959 name=/sbin/dhclient3
[    9.845714] type=1505 audit(1256675895.602:14): operation="profile_replace" pid=959 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    9.846129] type=1505 audit(1256675895.602:15): operation="profile_replace" pid=959 name=/usr/lib/connman/scripts/dhclient-script
[    9.849581] type=1505 audit(1256675895.602:16): operation="profile_replace" pid=960 name=/usr/bin/evince
[    9.862384] type=1505 audit(1256675895.622:17): operation="profile_replace" pid=960 name=/usr/bin/evince-previewer
[    9.869492] type=1505 audit(1256675895.622:18): operation="profile_replace" pid=960 name=/usr/bin/evince-thumbnailer
[    9.879317] type=1505 audit(1256675895.632:19): operation="profile_replace" pid=1024 name=/usr/lib/cups/backend/cups-pdf
[    9.880392] type=1505 audit(1256675895.642:20): operation="profile_replace" pid=1024 name=/usr/sbin/cupsd
[    9.883264] type=1505 audit(1256675895.642:21): operation="profile_replace" pid=1025 name=/usr/sbin/tcpdump
[   12.221052] usplash:413 freeing invalid memtype ffffffffd0000000-ffffffffe0000000
[   13.374116] ip_tables: (C) 2000-2006 Netfilter Core Team
[   20.053934] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.053937] vboxdrv: Successfully done.
[   20.053939] vboxdrv: Found 2 processor cores.
[   20.053989] VBoxDrv: dbg - g_abExecMemory=ffffffffa0b44420
[   20.054021] vboxdrv: fAsync=0 offMin=0x3fe offMax=0xe07
[   20.054060] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   20.054062] vboxdrv: Successfully loaded version 3.0.8 (interface 0x000e0000).
[   20.271256] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa0ce31c0
[   20.273730] VBoxNetAdp: dbg - g_abExecMemory=ffffffffa0cfcac0
[   20.350073] eth0: no IPv6 routers present
[   20.395283] ppdev: user-space parallel port driver
[   21.451102] CPU0 attaching NULL sched-domain.
[   21.451108] CPU1 attaching NULL sched-domain.
[   21.480083] CPU0 attaching sched-domain:
[   21.480087]  domain 0: span 0-1 level MC
[   21.480090]   groups: 0 1
[   21.480095]   domain 1: span 0-1 level CPU
[   21.480098]    groups: 0-1 (__cpu_power = 2048)
[   21.480104] CPU1 attaching sched-domain:
[   21.480106]  domain 0: span 0-1 level MC
[   21.480109]   groups: 1 0
[   21.480112]   domain 1: span 0-1 level CPU
[   21.480115]    groups: 0-1 (__cpu_power = 2048)
[   23.337166] CPU0 attaching NULL sched-domain.
[   23.337172] CPU1 attaching NULL sched-domain.
[   23.360205] CPU0 attaching sched-domain:
[   23.360209]  domain 0: span 0-1 level MC
[   23.360213]   groups: 0 1
[   23.360220] CPU1 attaching sched-domain:
[   23.360222]  domain 0: span 0-1 level MC
[   23.360225]   groups: 1 0
____________________________________________

Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
____________________________________________

Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.4.1-4ubuntu8' --with-bugurl=file:///usr/share/doc/gcc-4.4/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --enable-multiarch --enable-linker-build-id --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --with-gxx-include-dir=/usr/include/c++/4.4 --program-suffix=-4.4 --enable-nls --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --disable-werror --with-arch-32=i486 --with-tune=generic --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 
____________________________________________

xset -q:

xset:  unable to open display ""
____________________________________________

nvidia-settings -q all:


ERROR: The control display is undefined; please run `nvidia-settings
       --help` for usage information.

____________________________________________

/proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=03d69833-2099-4a8c-8bc3-a4c46ecf7862 ro quiet splash

____________________________________________

/proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping	: 2
cpu MHz		: 1603.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 3732.55
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz
stepping	: 2
cpu MHz		: 1870.000
cache size	: 2048 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm lahf_lm tpr_shadow
bogomips	: 3733.35
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:


____________________________________________

/proc/interrupts
           CPU0       CPU1       
  0:         24          0   IO-APIC-edge      timer
  1:          2          0   IO-APIC-edge      i8042
  4:          2          0   IO-APIC-edge    
  7:          1          0   IO-APIC-edge    
  8:          1          0   IO-APIC-edge      rtc0
  9:          0          0   IO-APIC-fasteoi   acpi
 12:          4          0   IO-APIC-edge      i8042
 14:       1006          0   IO-APIC-edge      pata_amd
 15:        158          0   IO-APIC-edge      pata_amd
 18:         55          0   IO-APIC-fasteoi   ctxfi
 19:       1931          0   IO-APIC-fasteoi   nvidia
 20:        252          0   IO-APIC-fasteoi   ohci_hcd:usb2
 21:         57          0   IO-APIC-fasteoi   ehci_hcd:usb1
 22:       1699          0   IO-APIC-fasteoi   sata_nv
 23:      14945          0   IO-APIC-fasteoi   sata_nv, eth0
NMI:          0          0   Non-maskable interrupts
LOC:      13245      14410   Local timer interrupts
SPU:          0          0   Spurious interrupts
CNT:          0          0   Performance counter interrupts
PND:          0          0   Performance pending work
RES:         33         81   Rescheduling interrupts
CAL:         57        112   Function call interrupts
TLB:        637        697   TLB shootdowns
TRM:          0          0   Thermal event interrupts
THR:          0          0   Threshold APIC interrupts
MCE:          0          0   Machine check exceptions
MCP:          1          1   Machine check polls
ERR:          1
MIS:          0

____________________________________________

/proc/meminfo
MemTotal:        4060100 kB
MemFree:         3045248 kB
Buffers:           28660 kB
Cached:           221668 kB
SwapCached:            0 kB
Active:           652220 kB
Inactive:         191376 kB
Active(anon):     596768 kB
Inactive(anon):        0 kB
Active(file):      55452 kB
Inactive(file):   191376 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       8418052 kB
SwapFree:        8418052 kB
Dirty:                64 kB
Writeback:             0 kB
AnonPages:        593284 kB
Mapped:            71820 kB
Slab:              33320 kB
SReclaimable:      15976 kB
SUnreclaim:        17344 kB
PageTables:        18640 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    10448100 kB
Committed_AS:    1098504 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      348412 kB
VmallocChunk:   34359387131 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       12032 kB
DirectMap2M:     4182016 kB

____________________________________________

/proc/modules
binfmt_misc 10220 1 - Live 0xffffffffa0d0e000
ppdev 8232 0 - Live 0xffffffffa0d09000
vboxnetadp 93292 0 - Live 0xffffffffa0cf0000
vboxnetflt 100300 0 - Live 0xffffffffa0cd5000
vboxdrv 1708492 1 vboxnetflt, Live 0xffffffffa0b31000
iptable_filter 3872 0 - Live 0xffffffffa0b2e000
ip_tables 21200 1 iptable_filter, Live 0xffffffffa0b23000
x_tables 25832 1 ip_tables, Live 0xffffffffa0b17000
psmouse 57124 0 - Live 0xffffffffa0b04000
serio_raw 6596 0 - Live 0xffffffffa0afd000
snd_ctxfi 99016 2 - Live 0xffffffffa0adf000
snd_pcm_oss 44704 0 - Live 0xffffffffa0acf000
snd_mixer_oss 18976 1 snd_pcm_oss, Live 0xffffffffa0ac8000
snd_pcm 93160 2 snd_ctxfi,snd_pcm_oss, Live 0xffffffffa0aaf000
snd_seq_dummy 3460 0 - Live 0xffffffffa004b000
snd_seq_oss 33440 0 - Live 0xffffffffa0aa4000
nouveau 643940 0 - Live 0xffffffffa0a04000
ttm 50032 1 nouveau, Live 0xffffffffa09f2000
snd_seq_midi 8192 0 - Live 0xffffffffa0079000
drm 197632 2 nouveau,ttm, Live 0xffffffffa09bc000
i2c_algo_bit 7076 1 nouveau, Live 0xffffffffa002b000
snd_rawmidi 27360 1 snd_seq_midi, Live 0xffffffffa09b3000
lp 11908 0 - Live 0xffffffffa09ae000
nvidia 9620328 24 - Live 0xffffffffa007c000 (P)
snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi, Live 0xffffffffa0074000
i2c_nforce2 8168 0 - Live 0xffffffffa0043000
parport 40528 2 ppdev,lp, Live 0xffffffffa0068000
snd_seq 60608 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event, Live 0xffffffffa0057000
snd_timer 26992 2 snd_pcm,snd_seq, Live 0xffffffffa004e000
snd_seq_device 8308 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq, Live 0xffffffffa0046000
snd 77096 13 snd_ctxfi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device, Live 0xffffffffa002e000
soundcore 9088 1 snd, Live 0xffffffffa0026000
snd_page_alloc 10928 1 snd_pcm, Live 0xffffffffa0021000
usbhid 43968 0 - Live 0xffffffffa0014000
forcedeth 61292 0 - Live 0xffffffffa0000000

____________________________________________

/proc/version
Linux version 2.6.31-14-generic (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009

____________________________________________

/proc/pci does not exist

____________________________________________

/proc/iomem
00000000-0000ffff : reserved
00010000-0009afff : System RAM
0009b000-0009ffff : reserved
000c0000-000cffff : pnp 00:0d
000e0000-000fffff : reserved
00100000-bffbffff : System RAM
  01000000-01530738 : Kernel code
  01530739-0182156f : Kernel data
  018d3000-019e2ccb : Kernel bss
bffc0000-bffcdfff : ACPI Tables
bffce000-bfffffff : ACPI Non-volatile Storage
d0000000-dfffffff : PCI Bus 0000:01
  d0000000-dfffffff : 0000:01:00.0
e0000000-efffffff : PCI MMCONFIG 0 [00-ff]
  e0000000-efffffff : pnp 00:0c
f5efb000-f5efbfff : 0000:00:14.0
  f5efb000-f5efbfff : forcedeth
f5efc000-f5efcfff : 0000:00:0f.0
  f5efc000-f5efcfff : sata_nv
f5efd000-f5efdfff : 0000:00:0e.0
  f5efd000-f5efdfff : sata_nv
f5efec00-f5efecff : 0000:00:0b.1
  f5efec00-f5efecff : ehci_hcd
f5eff000-f5efffff : 0000:00:0b.0
  f5eff000-f5efffff : ohci_hcd
f5f00000-f7ffffff : PCI Bus 0000:01
  f5fe0000-f5ffffff : 0000:01:00.0
  f6000000-f6ffffff : 0000:01:00.0
  f7000000-f7ffffff : 0000:01:00.0
    f7000000-f7ffffff : nvidia
f8000000-febfffff : PCI Bus 0000:04
  f8000000-fbffffff : 0000:04:07.0
    f8000000-fbffffff : XFi
  fea00000-febfffff : 0000:04:07.0
    fea00000-febfffff : XFi
fec00000-fec00fff : IOAPIC 0
  fec00000-fec00fff : reserved
fed00000-fed003ff : HPET 0
fee00000-fee00fff : Local APIC
  fee00000-fee00fff : reserved
    fee00000-fee00fff : pnp 00:08
fee01000-feefffff : pnp 00:06
fff80000-ffffffff : reserved
100000000-13fffffff : System RAM

____________________________________________

/proc/mtrr
reg00: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg01: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg02: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable

____________________________________________

/proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86_64 Kernel Module  190.42  Tue Oct 20 20:25:42 PDT 2009
GCC version:  gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) 

____________________________________________

/proc/driver/nvidia/cards/0
Model: 		 GeForce 7600 GT
IRQ:   		 19
Video BIOS: 	 05.73.22.18.01
Card Type: 	 PCI-E
DMA Size: 	 39 bits
DMA Mask: 	 0x7fffffffff
Bus Location: 	 01.00.0

____________________________________________

/proc/driver/nvidia/warnings/README
The NVIDIA graphics driver tries to detect potential problems
with the host system and warns about them using the system's
logging mechanisms. Important warning message are also logged
to dedicated text files in this directory.

____________________________________________

/proc/driver/nvidia/registry
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0
RegistryDwords: ""

____________________________________________

/proc/asound/cards
 0 [XFi            ]: SB-XFi - Creative X-Fi
                      Creative X-Fi 20K1 Unknown

____________________________________________

/proc/asound/pcm
00-00: ctxfi : Front/WaveIn : playback 8 : capture 1
00-01: ctxfi : Surround : playback 8
00-02: ctxfi : Center/LFE : playback 8
00-03: ctxfi : Side : playback 8
00-04: ctxfi : IEC958 Non-audio : playback 1

____________________________________________

/proc/asound/modules
 0 snd_ctxfi

____________________________________________

/proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 4]: digital audio playback
  5: [ 0- 3]: digital audio playback
  6: [ 0- 2]: digital audio playback
  7: [ 0- 1]: digital audio playback
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0]   : control

____________________________________________

/proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.20.

____________________________________________

/proc/asound/timers
G0: system timer : 10000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-0-2: PCM playback 0-0-2 : SLAVE
P0-0-4: PCM playback 0-0-4 : SLAVE
P0-0-6: PCM playback 0-0-6 : SLAVE
P0-0-8: PCM playback 0-0-8 : SLAVE
P0-0-10: PCM playback 0-0-10 : SLAVE
P0-0-12: PCM playback 0-0-12 : SLAVE
P0-0-14: PCM playback 0-0-14 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-1-2: PCM playback 0-1-2 : SLAVE
P0-1-4: PCM playback 0-1-4 : SLAVE
P0-1-6: PCM playback 0-1-6 : SLAVE
P0-1-8: PCM playback 0-1-8 : SLAVE
P0-1-10: PCM playback 0-1-10 : SLAVE
P0-1-12: PCM playback 0-1-12 : SLAVE
P0-1-14: PCM playback 0-1-14 : SLAVE
P0-2-0: PCM playback 0-2-0 : SLAVE
P0-2-2: PCM playback 0-2-2 : SLAVE
P0-2-4: PCM playback 0-2-4 : SLAVE
P0-2-6: PCM playback 0-2-6 : SLAVE
P0-2-8: PCM playback 0-2-8 : SLAVE
P0-2-10: PCM playback 0-2-10 : SLAVE
P0-2-12: PCM playback 0-2-12 : SLAVE
P0-2-14: PCM playback 0-2-14 : SLAVE
P0-3-0: PCM playback 0-3-0 : SLAVE
P0-3-2: PCM playback 0-3-2 : SLAVE
P0-3-4: PCM playback 0-3-4 : SLAVE
P0-3-6: PCM playback 0-3-6 : SLAVE
P0-3-8: PCM playback 0-3-8 : SLAVE
P0-3-10: PCM playback 0-3-10 : SLAVE
P0-3-12: PCM playback 0-3-12 : SLAVE
P0-3-14: PCM playback 0-3-14 : SLAVE
P0-4-0: PCM playback 0-4-0 : SLAVE

____________________________________________

/proc/asound/hwdep does not exist

____________________________________________

End of NVIDIA bug report log file.
```

---

### Post by autocrosser on 2009-10-27
Chroot into your install or use a way to get in "normally"--the sources you want to install the "testing" 190 drivers:```

deb http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main
deb-src http://ppa.launchpad.net/thefirstm/karmic-testing/ubuntu karmic main
deb http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/xsplash-team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/xsplash-team/ppa/ubuntu karmic main

```

Hope that helps!!!!

---

### Post by c2483 on 2009-10-28
I've tried them all.  My monitor just suspends once ubuntu starts.

---

