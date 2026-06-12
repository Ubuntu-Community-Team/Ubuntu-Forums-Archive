---
title: "Nvida 185.xx Update"
date: 2009-06-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by zenarcher on 2009-06-27
I just had an update available from the Nvidia 180.xx to the Nvidia 185.xx driver with Alpha 2.  The driver and available Nvidia packages seemed to update just fine, but after a reboot, I get the error that the Nvidia module didn't load or isn't available and that Kubuntu is going to start in the low graphics mode.  Not sure what to do, but maybe a "heads up," for anyone else who installs the update.

Cheers,
zenarcher

---

### Post by taavikko on 2009-06-27
Im running thefirstm PPA's version 190.* and it runs just fine.
Check that dkms builded the module "dkms status" for kernel you're running.

AFAIK the 2.6.31rc kernel and nvidia binary blob doesn't work together ATM.

---

### Post by zenarcher on 2009-06-27
Here's what I get from dkms status....

zenarcher@zenarcher-desktop:~$ dkms status
nvidia, 180.44, 2.6.28-13-generic, x86_64: installed
nvidia, 180.44, 2.6.28-11-generic, x86_64: installed


Cheers,
zenarcher

P.S.  Sorry, wrong computer info.  I was on my other system.  I'll get the correct info and post as soon as I can.

---

### Post by zenarcher on 2009-06-27
Not sure exactly what I did, but I fixed it!  After logging in, I saw that dkms had been interrupted for some reason....only thing I saw was some java certificate error on Mozilla.  Anyway, I ran sudo apt-get update and the Nvidia driver installed and was set up properly.  Did a reboot and all is working fine again!

Thanks,
zenarcher

---

### Post by PRGUY85 on 2009-06-27
Saw the upgrade yet I'm still getting no desktop effects out of this driver, which used to work in Jaunty.  here's a video of what happens on my desktop:

[http://www.youtube.com/watch?v=3iKQbUZv0No](http://www.youtube.com/watch?v=3iKQbUZv0No)

---

### Post by taavikko on 2009-06-27
> **PRGUY85 said:**
> Saw the upgrade yet I'm still getting no desktop effects out of this driver, which used to work in Jaunty.  here's a video of what happens on my desktop:

[http://www.youtube.com/watch?v=3iKQbUZv0No](http://www.youtube.com/watch?v=3iKQbUZv0No)

that looks more like Compiz failing rather than binary blob of nvidia.

Try starting compiz via command line "compiz --replace &"
And post the output.

---

### Post by zenarcher on 2009-06-27
Yeah, I'm using KDE effects and all is fine there.  Not using Compiz here on my test system.

Cheers,
zenarcher

---

### Post by PRGUY85 on 2009-06-27
Here is what I get:

[[IMG]http://img91.imageshack.us/img91/112/screenshotuhu.th.png[/IMG]](http://img91.imageshack.us/i/screenshotuhu.png/)

---

### Post by autocrosser on 2009-06-27
> **taavikko said:**
> Im running thefirstm PPA's version 190.* and it runs just fine.
Check that dkms builded the module "dkms status" for kernel you're running.

AFAIK the 2.6.31rc kernel and nvidia binary blob doesn't work together ATM.

Pity that he's only got 64bit built right now........

---

### Post by tad1073 on 2009-06-27
:~/Desktop$ dkms status
nvidia, 185.18.14, 2.6.30-10-generic, x86_64: installed

---

### Post by PRGUY85 on 2009-06-27
Any thoughts on the picture I posted of when I enabled compiz by terminal?

---

### Post by MacUntu on 2009-06-27
> **PRGUY85 said:**
> Any thoughts on the picture I posted of when I enabled compiz by terminal?

Well, what's the problem? Hit 'Alt', click on the terminal window and move it. :)

By the way: could you check your CPU load when manually  starting compiz like this (only if you've set 'Visual Effects' to 'None' in 'Appearance Preferences')?

---

### Post by PRGUY85 on 2009-06-28
> **MacUntu said:**
> Well, what's the problem? Hit 'Alt', click on the terminal window and move it. :)

By the way: could you check your CPU load when manually  starting compiz like this (only if you've set 'Visual Effects' to 'None' in 'Appearance Preferences')?

I can't do anything once I enable compiz.  That's my terminal output once I activate it.  it says XGL cannot be found.

---

### Post by taavikko on 2009-06-28
> **PRGUY85 said:**
> Any thoughts on the picture I posted of when I enabled compiz by terminal?

Nice wallpaper ;)

> **PRGUY85 said:**
> I can't do anything once I enable compiz.  That's my terminal output once I activate it.  it says XGL cannot be found.

Errors in the output isn't fatal, compiz should still work.
Somehow compiz failed to completely initialize and that's why you don't have the borders on the window where to drag it around.

You can move the windows by pressing alt+mouse1 to drag them around.

attach the Xorg.0.log to have a better look at your system...

---

### Post by PRGUY85 on 2009-06-28
> **taavikko said:**
> Nice wallpaper ;)



Errors in the output isn't fatal, compiz should still work.
Somehow compiz failed to completely initialize and that's why you don't have the borders on the window where to drag it around.

You can move the windows by pressing alt+mouse1 to drag them around.

attach the Xorg.0.log to have a better look at your system...

Noobish question here...when you mean attach Xorg.0.log, is that my xorg.conf output?

---

### Post by dagrump on 2009-06-28
I think it's in /var/log, & your xorg.conf would help. System spec.s couldn't hurt either. lspci output never hurts, the more to work with the better.

---

### Post by lithorus on 2009-06-29
> **dagrump said:**
> I think it's in /var/log, & your xorg.conf would help. System spec.s couldn't hurt either. lspci output never hurts, the more to work with the better.
Or just do a "sudo nvidia-bugreport.sh" and attach that file instead.

---

### Post by PRGUY85 on 2009-06-29
Xorg.0.log:

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.6.1.901 (1.6.2 RC 1)
Release Date: 2009-5-8
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux manolo-laptop 2.6.30-9-generic #10-Ubuntu SMP Fri Jun 12 13:05:04 UTC 2009 i686
Build Date: 24 June 2009  10:36:15PM
xorg-server 2:1.6.1.901-2ubuntu2 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 29 14:18:08 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
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
(II) Loader magic: 0x1bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation G72M [GeForce Go 7400] rev 161, Mem @ 0xdd000000/16777216, 0xc0000000/268435456, 0xde000000/16777216, BIOS @ 0x????????/131072
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
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.14  Wed May 27 03:09:07 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
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
	compiled for 1.6.1.901, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.14  Wed May 27 02:32:54 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.0.0
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
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce Go 7400 (G72) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.72.22.21.f5
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce Go 7400 at PCI:1:0:0:
(--) NVIDIA(0):     AUO (DFP-0)
(--) NVIDIA(0): AUO (DFP-0): 330.0 MHz maximum pixel clock
(--) NVIDIA(0): AUO (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Assigned Display Device: DFP-0
(==) NVIDIA(0): 
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) NVIDIA(0):     will be used as the requested mode.
(==) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (125, 126); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(**) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): ACPI display change hotkey events enabled: the X server is new
(II) NVIDIA(0):     enough to receive ACPI display change hotkey events.
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
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
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event4"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
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
(II) config/hal: Adding input device UVC Camera (046d:08c6)
(**) UVC Camera (046d:08c6): always reports core events
(**) UVC Camera (046d:08c6): Device: "/dev/input/event7"
(II) UVC Camera (046d:08c6): Found keys
(II) UVC Camera (046d:08c6): Configuring as keyboard
(II) XINPUT: Adding extended input device "UVC Camera (046d:08c6)" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Sleep Button
(**) Sleep Button: always reports core events
(**) Sleep Button: Device: "/dev/input/event2"
(II) Sleep Button: Found keys
(II) Sleep Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Video Bus
(**) Video Bus: always reports core events
(**) Video Bus: Device: "/dev/input/event5"
(II) Video Bus: Found keys
(II) Video Bus: Configuring as keyboard
(II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event3"
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
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.1.901, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event8"
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad: touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad: touchpad found
```

xorg.conf:

```
Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option	"AddARGBGLXVisuals"	"True"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

```

System Specs: Dell XPS M1210 with Intel Centrino Duo and nVidia GeForce Go 7400

---

### Post by dagrump on 2009-06-29
Well, I sure ain't an expert, but I don't see anything in the log. The one warning about fonts.
How did your xorg.conf file get created in it's present state? Did you edit yourself, did the installer modify it, or did you do a "sudo nvidia-xconfig"?
I would backup the existing one & try the nvidia-xconfig & reboot. That xorg just looks wrong, & then I could be all wet & you end up with the same file again.
The only other thing I can think of is a setting in the bios for amount of shared RAM, if that was set to low that might cause issues. 
Sorry, I'm not much help.

---

### Post by PRGUY85 on 2009-06-29
> **dagrump said:**
> Well, I sure ain't an expert, but I don't see anything in the log. The one warning about fonts.
How did your xorg.conf file get created in it's present state? Did you edit yourself, did the installer modify it, or did you do a "sudo nvidia-xconfig"?
I would backup the existing one & try the nvidia-xconfig & reboot. That xorg just looks wrong, & then I could be all wet & you end up with the same file again.
The only other thing I can think of is a setting in the bios for amount of shared RAM, if that was set to low that might cause issues. 
Sorry, I'm not much help.

Just installed the Nvidia drivers.  Didn't tweak xorg.conf at all.

---

### Post by dagrump on 2009-06-29
Well, the nvidia-xconfig would generate a new xorg.conf file for you. That is is easiest trick to try. Backup the old one, even though it should do it by default.

---

### Post by PRGUY85 on 2009-06-29
> **dagrump said:**
> Well, the nvidia-xconfig would generate a new xorg.conf file for you. That is is easiest trick to try. Backup the old one, even though it should do it by default.

Exactly. Just weird.  I know this is Alpha but considering no one else has this issue and I have never come cross it on Jaunty/Intrepid or other previous releases, I find it weird.

---

### Post by ktp on 2009-06-29
> **autocrosser said:**
> Pity that he's only got 64bit built right now........

[https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa)

---

### Post by autocrosser on 2009-06-29
> **ktp said:**
> [https://launchpad.net/~brandonsnider/+archive/ppa]("https://launchpad.net/%7Ebrandonsnider/+archive/ppa")

How is that one working mate?

---

### Post by PRGUY85 on 2009-06-29
Any ideas on my current compiz-less situation?

---

### Post by autocrosser on 2009-06-29
Not really sure--Interesting thought---are you using the Fusion Icon to start/stop Compiz?
Also--are you using Emerald or just the basic Metacity stuff? 
If the answer is not on both accounts, you might install the bits thru Synaptic & use Emerald---

I find that sometimes Compiz gets a "bug up its behind" & won't play pretty with Metacity---Emerald was really built for Compiz use after all.......

In any case--give that a go & post back.........

---

### Post by ktp on 2009-06-29
> **autocrosser said:**
> How is that one working mate?

The nvidia-glx-190 is working great for me here...things look sharper and quicker, than 185, for me.

---

### Post by autocrosser on 2009-06-30
Sounds good--I've needed to reboot for a couple of days now--I'll pop it in & give it a whirl.....

---

### Post by autocrosser on 2009-06-30
Very interesting--with 185, GLXgears was reporting framerates around 40000 for my SLI setup (dual 9500 GT w/1G vram each)--now the 190 looks like:

dean@linux:~/Desktop$ glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/164 the monitor refresh rate.
54087 frames in 5.0 seconds
54155 frames in 5.0 seconds
54243 frames in 5.0 seconds
54242 frames in 5.0 seconds
54259 frames in 5.0 seconds
54270 frames in 5.0 seconds
54281 frames in 5.0 seconds
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 54 requests (53 known processed) with 0 events remaining.


Very nice.......I'm going to try GLX Dragon next....

---

### Post by autocrosser on 2009-06-30
Hmmmmm---the dragon stresses everything fairly hard--results look like:```
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 9500 GT/PCI/SSE2
GL_VERSION  : 3.1.0 NVIDIA 190.09

0.7 seconds for 180 frames = 250.0 FPS
0.7 seconds for 180 frames = 260.9 FPS
0.7 seconds for 180 frames = 260.9 FPS
0.7 seconds for 180 frames = 260.9 FPS
0.7 seconds for 180 frames = 260.9 FPS
0.7 seconds for 180 frames = 257.1 FPS
0.7 seconds for 180 frames = 260.9 FPS
0.7 seconds for 180 frames = 257.1 FPS
0.7 seconds for 180 frames = 264.7 FPS
0.7 seconds for 180 frames = 253.5 FPS
dean@linux:~/Desktop/Dean's Stuff/glxdragon$ 
```

---

### Post by autocrosser on 2009-06-30
Well--It is faster, but I woke the system up this morning to major screen artifacts--tried a few things & just gave up for a bad job---went back to 185 til I see the 190 a bit more finished.....can hardly wait til it works without buggerin' my system.....

---

### Post by PRGUY85 on 2009-06-30
I am not using Emerald or Compiz icon.  I just switch to Advanced Effects on Appearance dialog.

---

### Post by autocrosser on 2009-06-30
This I know mate---I am suggesting to try using them as more advanced tools--you just might get a working Compiz out of it & be pleased with the added functionality.........

---

### Post by PRGUY85 on 2009-06-30
> **autocrosser said:**
> This I know mate---I am suggesting to try using them as more advanced tools--you just might get a working Compiz out of it & be pleased with the added functionality.........

I'll try.  I always use the Advanced Compiz effects later on.  Hope that helps.

---

