---
title: "Automatic crash report generation [FAIL] - Ubuntu cannot boot."
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by drews_blunted on 2012-02-23
Hello. I have just built a new computer with a AMD FX proccessor, New NVIDIA pci express geforce card, gigabyte motherboard.

I am having a booting issue with my ubuntu install.

Grub loads fine it starts the graphical boot in a high resolution then stops goes to console and lists this below: 

fsck from util-linux 2.19.1
/dev/sda1: clean, 187482/3670016 files, 1952862/14653440 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting Bridge socket events into upstart	[74G[ OK ]
 * Starting configure network device security	[74G[ OK ]
 * Starting configure network device	[74G[ OK ]
 * Starting AppArmor profiles       	[80G 
	[74G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Checking for running unattended-upgrades: 
 * Stopping System V initialisation compatibility	[74G[ OK ]
 * Starting System V runlevel compatibility	[74G[ OK ]

 *** Stopping automatic crash report generation	[74G[	[31mfail [39;49m]**
 * Starting deferred execution scheduler		[74G[ OK ]
 * Starting regular background program processing daemon	[74G[ OK ]
 * Starting ACPI daemon		[74G[ OK ]
 * Starting save kernel messages	[74G[ OK ]
 * Starting CPU interrupts balancing daemon	[74G[ OK ]
 * Stopping save kernel messages	[74G[ OK ]
 * Starting bluetooth       	[80G 
	[74G[ OK ]
	[33m*	[39;49m PulseAudio configured for per-user sessions
saned disabled; edit /etc/default/saned
 * Starting anac(h)ronistic cron	[74G[ OK ]
 * Stopping anac(h)ronistic cron	[74G[ OK ]
 * Checking battery state...       	[80G 
	[74G[ OK ]
 * Stopping System V runlevel compatibility	[74G[ OK ]


After it lists this in the console my computer is basicaly at a standstill and doesnt do anything, so i figure it must be frozen or not able to boot.

Ive done some research to look into this issue, i searched for other people who got the fail warning i did for the automatic crash report. Some sudgested that i remove apport. I have tryed this and disabled it etc and it was not affecting my system at all. The only work around i have found to get my system to boot is to load ubuntu with the **nomodeset** option in grub.

I would like my system to properly boot is anyone else having this problem or is there anything i could try or info i could tell developers to try and address this issue? Any help would be greatly appreciated. 

Thankyou.

---

### Post by drews_blunted on 2012-02-24
I think what i am dealing with is a bug in ubuntu. 
I found this link below that sounds like a similar problem.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/888373](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/888373)

Anyone found a workaround for this bug?

---

### Post by drews_blunted on 2012-02-24
Ok, well im sort of at a dead end now. Ubuntu will not load without the nomodeset command added to my grub. 

I still see this problem occure even when i purge all nvidia drivers from my system reinstall x and reconfigure x. it doesnt seem to matter what my video card is, for some reason my system just will not start.

---

### Post by MAFoElffen on 2012-02-24
> **drews_blunted said:**
> I think what i am dealing with is a bug in ubuntu. 
I found this link below that sounds like a similar problem.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/888373](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-nouveau/+bug/888373)

Anyone found a workaround for this bug?
Please go back to the 1st post and Edit your title to "Hung at "Stopping System V runlevel compatibility"

Here is what is going on.  When a Debian based Linux system hangs at either "Checking Battery State" or "Stopping System V runlevel compatibility" then this has happened successfully- Then the kernel has booted and the base system is running.  XServer has booted until it tried to boot a graphics driver and either it wasn't there or was bad/corrupted. It then hangs there... The timeline being while displaying one of those two messages.

Solution- depends which Video Card.  I'm suspecting ATI or NVidia. Since you thought it was Nouveau, I'm leaning NVidia... but you tell me which.

---

### Post by drews_blunted on 2012-02-24
Thanks for your response and your ideas on the problem.

I have a GeForce GTX 560 Ti installed. I have the nvidia drivers installed.

---

### Post by drews_blunted on 2012-02-24
Ok, i have made some success in fixing my issue.

I started googling for "Geforce 550 ti ubuntu" and i came accross the fact that since its such a new card that you need to have the latest drivers. 

I did this by typing:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

my video card is now working much better and with 3d acceleration. The ubuntu install will boot in full high resolution. The only problem now is that i still have my grub edited to have the **nomodeset** command. When i remove it, the system still fails to boot and freezes?

I guess i have a usable workaround. but im unsure now what nomodeset means and if this will be a problem going forward.

---

### Post by MAFoElffen on 2012-02-24
> **drews_blunted said:**
> Ok, i have made some success in fixing my issue.

I started googling for "Geforce 550 ti ubuntu" and i came accross the fact that since its such a new card that you need to have the latest drivers. 

I did this by typing:

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

my video card is now working much better and with 3d acceleration. The ubuntu install will boot in full high resolution. The only problem now is that i still have my grub edited to have the **nomodeset** command. When i remove it, the system still fails to boot and freezes?

I guess i have a usable workaround. but im unsure now what nomodeset means and if this will be a problem going forward.
The way to check that would be to remove nomodeset temporarily (grub menu, e, edit it out, cntrl-x)... and let it hang.

Reboot, Post your /var/log/Xorg.1.log file.  The xorg log file goes 0 as current, 1 as 1 previous, 2 as 2 previous, etc. That should should where it had a problem... 

My understanding is that "nomodeset" as a startup option with nvidia tells xorg to ignore the need for a video driver and use something generic, such as VESA or Nouveau... It also tells the chipset to take VESA calls.  Usually you have to use nomodeset with ATI or Nvidia temporarily- just "until" you get the chipsets drivers installed...  Then it isn't needed any more.

So having to still use "nomodeset"... Something is not right yet.

---

### Post by drews_blunted on 2012-02-24
[     8.716] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[     8.716] X Protocol Version 11, Revision 0
[     8.716] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[     8.716] Current Operating System: Linux andrew-GA-990FXA-UD5 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686
[     8.716] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=7c77943a-0433-4e12-9d5d-394016db698f ro quiet splash vt.handoff=7 nomodeset
[     8.716] Build Date: 19 October 2011  05:09:41AM
[     8.716] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     8.716] Current version of pixman: 0.22.2
[     8.716] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[     8.716] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     8.716] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 24 00:37:07 2012
[     8.716] (==) Using config file: "/etc/X11/xorg.conf"
[     8.716] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     8.717] (==) ServerLayout "Layout0"
[     8.717] (**) |-->Screen "Screen0" (0)
[     8.717] (**) |   |-->Monitor "Monitor0"
[     8.717] (**) |   |-->Device "Device0"
[     8.717] (**) |-->Input Device "Keyboard0"
[     8.717] (**) |-->Input Device "Mouse0"
[     8.717] (==) Automatically adding devices
[     8.717] (==) Automatically enabling devices
[     8.717] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     8.717] 	Entry deleted from font path.
[     8.717] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     8.717] 	Entry deleted from font path.
[     8.717] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     8.717] 	Entry deleted from font path.
[     8.717] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     8.717] 	Entry deleted from font path.
[     8.717] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     8.717] 	Entry deleted from font path.
[     8.717] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[     8.718] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     8.718] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     8.718] (WW) Disabling Keyboard0
[     8.718] (WW) Disabling Mouse0
[     8.718] (II) Loader magic: 0x823ada0
[     8.718] (II) Module ABI versions:
[     8.718] 	X.Org ANSI C Emulation: 0.4
[     8.718] 	X.Org Video Driver: 10.0
[     8.718] 	X.Org XInput driver : 12.3
[     8.718] 	X.Org Server Extension : 5.0
[     8.719] (--) PCI:*(0:1:0:0) 10de:1200:3842:1561 rev 161, Mem @ 0xf8000000/33554432, 0xd0000000/134217728, 0xdc000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[     8.719] (II) Open ACPI successful (/var/run/acpid.socket)
[     8.719] (II) LoadModule: "extmod"
[     8.720] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     8.720] (II) Module extmod: vendor="X.Org Foundation"
[     8.720] 	compiled for 1.10.4, module version = 1.0.0
[     8.720] 	Module class: X.Org Server Extension
[     8.720] 	ABI class: X.Org Server Extension, version 5.0
[     8.720] (II) Loading extension MIT-SCREEN-SAVER
[     8.720] (II) Loading extension XFree86-VidModeExtension
[     8.720] (II) Loading extension XFree86-DGA
[     8.720] (II) Loading extension DPMS
[     8.720] (II) Loading extension XVideo
[     8.720] (II) Loading extension XVideo-MotionCompensation
[     8.720] (II) Loading extension X-Resource
[     8.720] (II) LoadModule: "dbe"
[     8.720] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     8.720] (II) Module dbe: vendor="X.Org Foundation"
[     8.720] 	compiled for 1.10.4, module version = 1.0.0
[     8.721] 	Module class: X.Org Server Extension
[     8.721] 	ABI class: X.Org Server Extension, version 5.0
[     8.721] (II) Loading extension DOUBLE-BUFFER
[     8.721] (II) LoadModule: "glx"
[     8.721] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[     8.870] (II) Module glx: vendor="NVIDIA Corporation"
[     8.870] 	compiled for 4.0.2, module version = 1.0.0
[     8.870] 	Module class: X.Org Server Extension
[     8.870] (II) NVIDIA GLX Module  295.20  Mon Feb  6 20:47:25 PST 2012
[     8.870] (II) Loading extension GLX
[     8.870] (II) LoadModule: "record"
[     8.871] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     8.871] (II) Module record: vendor="X.Org Foundation"
[     8.871] 	compiled for 1.10.4, module version = 1.13.0
[     8.871] 	Module class: X.Org Server Extension
[     8.871] 	ABI class: X.Org Server Extension, version 5.0
[     8.871] (II) Loading extension RECORD
[     8.871] (II) LoadModule: "dri"
[     8.871] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     8.871] (II) Module dri: vendor="X.Org Foundation"
[     8.871] 	compiled for 1.10.4, module version = 1.0.0
[     8.871] 	ABI class: X.Org Server Extension, version 5.0
[     8.871] (II) Loading extension XFree86-DRI
[     8.871] (II) LoadModule: "dri2"
[     8.872] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     8.872] (II) Module dri2: vendor="X.Org Foundation"
[     8.872] 	compiled for 1.10.4, module version = 1.2.0
[     8.872] 	ABI class: X.Org Server Extension, version 5.0
[     8.872] (II) Loading extension DRI2
[     8.872] (II) LoadModule: "nvidia"
[     8.872] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     8.875] (II) Module nvidia: vendor="NVIDIA Corporation"
[     8.875] 	compiled for 4.0.2, module version = 1.0.0
[     8.875] 	Module class: X.Org Video Driver
[     8.876] (II) NVIDIA dlloader X Driver  295.20  Mon Feb  6 20:27:19 PST 2012
[     8.877] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     8.877] (++) using VT number 7

[     8.877] (II) Loading sub module "fb"
[     8.877] (II) LoadModule: "fb"
[     8.877] (II) Loading /usr/lib/xorg/modules/libfb.so
[     8.877] (II) Module fb: vendor="X.Org Foundation"
[     8.877] 	compiled for 1.10.4, module version = 1.0.0
[     8.877] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     8.877] (II) Loading sub module "wfb"
[     8.877] (II) LoadModule: "wfb"
[     8.878] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     8.878] (II) Module wfb: vendor="X.Org Foundation"
[     8.878] 	compiled for 1.10.4, module version = 1.0.0
[     8.878] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     8.878] (II) Loading sub module "ramdac"
[     8.878] (II) LoadModule: "ramdac"
[     8.878] (II) Module "ramdac" already built-in
[     8.878] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     8.878] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     8.878] (II) Loading /usr/lib/xorg/modules/libfb.so
[     8.878] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     8.878] (==) NVIDIA(0): RGB weight 888
[     8.878] (==) NVIDIA(0): Default visual is TrueColor
[     8.878] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     8.878] (**) NVIDIA(0): Enabling 2D acceleration
[    10.307] (II) NVIDIA(GPU-0): Display (HP w2408 (CRT-0)) does not support NVIDIA 3D Vision
[    10.307] (II) NVIDIA(GPU-0):     stereo.
[    10.308] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 560 Ti (GF114) at PCI:1:0:0 (GPU-0)
[    10.308] (--) NVIDIA(0): Memory: 1048576 kBytes
[    10.308] (--) NVIDIA(0): VideoBIOS: 70.24.2e.00.62
[    10.308] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    10.308] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    10.308] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 560 Ti at
[    10.308] (--) NVIDIA(0):     PCI:1:0:0
[    10.308] (--) NVIDIA(0):     HP w2408 (CRT-0)
[    10.308] (--) NVIDIA(0): HP w2408 (CRT-0): 400.0 MHz maximum pixel clock
[    10.333] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    10.333] (**) NVIDIA(0):     device HP w2408 (CRT-0) (Using EDID frequencies has been
[    10.333] (**) NVIDIA(0):     enabled on all display devices.)
[    10.348] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    10.348] (==) NVIDIA(0): 
[    10.348] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    10.348] (==) NVIDIA(0):     will be used as the requested mode.
[    10.348] (==) NVIDIA(0): 
[    10.348] (II) NVIDIA(0): Validated modes:
[    10.348] (II) NVIDIA(0):     "nvidia-auto-select"
[    10.348] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    10.385] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[    10.385] (--) NVIDIA(0):     option
[    10.385] (--) Depth 24 pixmap format is 32 bpp
[    10.385] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[    10.385] (II) NVIDIA:     access.
[    10.395] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    10.430] (II) Loading extension NV-GLX
[    10.497] (==) NVIDIA(0): Disabling shared memory pixmaps
[    10.497] (==) NVIDIA(0): Backing store disabled
[    10.497] (==) NVIDIA(0): Silken mouse enabled
[    10.497] (**) NVIDIA(0): DPMS enabled
[    10.497] (II) Loading extension NV-CONTROL
[    10.497] (II) Loading extension XINERAMA
[    10.497] (II) Loading sub module "dri2"
[    10.497] (II) LoadModule: "dri2"
[    10.497] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    10.497] (II) Module dri2: vendor="X.Org Foundation"
[    10.497] 	compiled for 1.10.4, module version = 1.2.0
[    10.497] 	ABI class: X.Org Server Extension, version 5.0
[    10.497] (II) NVIDIA(0): [DRI2] Setup complete
[    10.497] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    10.497] (==) RandR enabled
[    10.497] (II) Initializing built-in extension Generic Event Extension
[    10.497] (II) Initializing built-in extension SHAPE
[    10.497] (II) Initializing built-in extension MIT-SHM
[    10.497] (II) Initializing built-in extension XInputExtension
[    10.497] (II) Initializing built-in extension XTEST
[    10.497] (II) Initializing built-in extension BIG-REQUESTS
[    10.497] (II) Initializing built-in extension SYNC
[    10.497] (II) Initializing built-in extension XKEYBOARD
[    10.497] (II) Initializing built-in extension XC-MISC
[    10.497] (II) Initializing built-in extension SECURITY
[    10.497] (II) Initializing built-in extension XINERAMA
[    10.498] (II) Initializing built-in extension XFIXES
[    10.498] (II) Initializing built-in extension RENDER
[    10.498] (II) Initializing built-in extension RANDR
[    10.498] (II) Initializing built-in extension COMPOSITE
[    10.498] (II) Initializing built-in extension DAMAGE
[    10.498] (II) Initializing built-in extension GESTURE
[    10.499] (II) Initializing extension GLX
[    10.520] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.528] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    10.528] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.528] (II) LoadModule: "evdev"
[    10.528] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.529] (II) Module evdev: vendor="X.Org Foundation"
[    10.529] 	compiled for 1.10.2, module version = 2.6.0
[    10.529] 	Module class: X.Org XInput Driver
[    10.529] 	ABI class: X.Org XInput driver, version 12.3
[    10.529] (II) Using input driver 'evdev' for 'Power Button'
[    10.529] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.529] (**) Power Button: always reports core events
[    10.529] (**) Power Button: Device: "/dev/input/event1"
[    10.529] (--) Power Button: Found keys
[    10.529] (II) Power Button: Configuring as keyboard
[    10.529] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    10.529] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    10.529] (**) Option "xkb_rules" "evdev"
[    10.529] (**) Option "xkb_model" "pc105"
[    10.529] (**) Option "xkb_layout" "us"
[    10.531] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    10.531] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.531] (II) Using input driver 'evdev' for 'Power Button'
[    10.531] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.531] (**) Power Button: always reports core events
[    10.531] (**) Power Button: Device: "/dev/input/event0"
[    10.531] (--) Power Button: Found keys
[    10.531] (II) Power Button: Configuring as keyboard
[    10.531] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    10.531] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    10.531] (**) Option "xkb_rules" "evdev"
[    10.531] (**) Option "xkb_model" "pc105"
[    10.531] (**) Option "xkb_layout" "us"
[    10.532] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event6)
[    10.532] (II) No input driver/identifier specified (ignoring)
[    10.533] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event7)
[    10.533] (II) No input driver/identifier specified (ignoring)
[    10.533] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event8)
[    10.533] (II) No input driver/identifier specified (ignoring)
[    10.533] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event9)
[    10.533] (II) No input driver/identifier specified (ignoring)
[    10.537] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event2)
[    10.537] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[    10.537] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[    10.537] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.537] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[    10.537] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event2"
[    10.537] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[    10.537] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[    10.537] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/input/input2/event2"
[    10.537] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[    10.537] (**) Option "xkb_rules" "evdev"
[    10.537] (**) Option "xkb_model" "pc105"
[    10.537] (**) Option "xkb_layout" "us"
[    10.538] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event3)
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev pointer catchall"
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[    10.538] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[    10.538] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event3"
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 9 mouse buttons
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y relative axes
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[    10.538] (II) evdev-grail: failed to open grail, no gesture support
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[    10.538] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[    10.538] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[    10.538] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Adding scrollwheel support
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.538] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.1/input/input3/event3"
[    10.538] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[    10.538] (**) Option "xkb_rules" "evdev"
[    10.538] (**) Option "xkb_model" "pc105"
[    10.538] (**) Option "xkb_layout" "us"
[    10.538] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for relative axes.
[    10.538] (WW) Microsoft Microsoft® 2.4GHz Transceiver v6.0: ignoring absolute axes.
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration profile 0
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration factor: 2.000
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration threshold: 4
[    10.538] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/mouse0)
[    10.538] (II) No input driver/identifier specified (ignoring)
[    10.539] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event4)
[    10.539] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[    10.539] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[    10.539] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.539] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[    10.539] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event4"
[    10.539] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 1 mouse buttons
[    10.539] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[    10.539] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[    10.539] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[    10.540] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y absolute axes
[    10.540] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[    10.540] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[    10.540] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[    10.540] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Adding scrollwheel support
[    10.540] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[    10.540] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.540] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.2/input/input4/event4"
[    10.540] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[    10.540] (**) Option "xkb_rules" "evdev"
[    10.540] (**) Option "xkb_model" "pc105"
[    10.540] (**) Option "xkb_layout" "us"
[    10.540] (EE) Microsoft Microsoft® 2.4GHz Transceiver v6.0: failed to initialize for relative axes.
[    10.542] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[    10.542] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[    10.542] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for absolute axes.
[    10.542] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
[    10.542] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration profile 0
[    10.542] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration factor: 2.000
[    10.542] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration threshold: 4
[    10.542] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/js0)
[    10.542] (II) No input driver/identifier specified (ignoring)
[    10.545] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event5)
[    10.545] (II) No input driver/identifier specified (ignoring)
[    21.649] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   263.044] (II) config/udev: removing device Microsoft Microsoft® 2.4GHz Transceiver v6.0
[   263.044] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Close
[   263.044] (II) UnloadModule: "evdev"
[   263.044] (II) Unloading evdev
[   263.252] (II) config/udev: removing device Microsoft Microsoft® 2.4GHz Transceiver v6.0
[   263.253] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Close
[   263.253] (II) UnloadModule: "evdev"
[   263.253] (II) Unloading evdev
[   263.396] (II) config/udev: removing device Microsoft Microsoft® 2.4GHz Transceiver v6.0
[   263.396] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Close
[   263.397] (II) UnloadModule: "evdev"
[   263.397] (II) Unloading evdev
[   267.508] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event2)
[   267.508] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[   267.508] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[   267.508] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   267.508] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[   267.508] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event2"
[   267.509] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[   267.509] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[   267.509] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:16.0/usb7/7-2/7-2:1.0/input/input10/event2"
[   267.509] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[   267.509] (**) Option "xkb_rules" "evdev"
[   267.509] (**) Option "xkb_model" "pc105"
[   267.509] (**) Option "xkb_layout" "us"
[   267.510] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event4)
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[   267.510] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[   267.510] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event4"
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 1 mouse buttons
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y absolute axes
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[   267.510] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[   267.510] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[   267.510] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Adding scrollwheel support
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   267.510] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:16.0/usb7/7-2/7-2:1.2/input/input12/event4"
[   267.510] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[   267.510] (**) Option "xkb_rules" "evdev"
[   267.510] (**) Option "xkb_model" "pc105"
[   267.510] (**) Option "xkb_layout" "us"
[   267.511] (EE) Microsoft Microsoft® 2.4GHz Transceiver v6.0: failed to initialize for relative axes.
[   267.513] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[   267.513] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[   267.513] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for absolute axes.
[   267.513] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
[   267.513] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration profile 0
[   267.513] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration factor: 2.000
[   267.513] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration threshold: 4
[   267.516] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/js0)
[   267.517] (II) No input driver/identifier specified (ignoring)
[   267.518] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event3)
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev pointer catchall"
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[   267.518] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[   267.518] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event3"
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 9 mouse buttons
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y relative axes
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[   267.518] (II) evdev-grail: failed to open grail, no gesture support
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[   267.518] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[   267.518] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[   267.518] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Adding scrollwheel support
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   267.519] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:16.0/usb7/7-2/7-2:1.1/input/input11/event3"
[   267.519] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[   267.519] (**) Option "xkb_rules" "evdev"
[   267.519] (**) Option "xkb_model" "pc105"
[   267.519] (**) Option "xkb_layout" "us"
[   267.519] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for relative axes.
[   267.519] (WW) Microsoft Microsoft® 2.4GHz Transceiver v6.0: ignoring absolute axes.
[   267.519] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
[   267.519] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration profile 0
[   267.519] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration factor: 2.000
[   267.519] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration threshold: 4
[   267.519] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/mouse0)
[   267.519] (II) No input driver/identifier specified (ignoring)

---

### Post by MAFoElffen on 2012-02-25
> **drews_blunted said:**
> ```
[     8.716] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[     8.716] X Protocol Version 11, Revision 0
[     8.716] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[     8.716] Current Operating System: Linux andrew-GA-990FXA-UD5 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686
[     8.716] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-16-generic root=UUID=7c77943a-0433-4e12-9d5d-394016db698f ro quiet splash vt.handoff=7 nomodeset
[     8.716] Build Date: 19 October 2011  05:09:41AM
[     8.716] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     8.716] Current version of pixman: 0.22.2
[     8.716]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     8.716] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     8.716] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb 24 00:37:07 2012
[     8.716] (==) Using config file: "/etc/X11/xorg.conf"
[     8.716] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     8.717] (==) ServerLayout "Layout0"
[     8.717] (**) |-->Screen "Screen0" (0)
[     8.717] (**) |   |-->Monitor "Monitor0"
[     8.717] (**) |   |-->Device "Device0"
[     8.717] (**) |-->Input Device "Keyboard0"
[     8.717] (**) |-->Input Device "Mouse0"
[     8.717] (==) Automatically adding devices
[     8.717] (==) Automatically enabling devices
[     8.717] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     8.717]     Entry deleted from font path.
[     8.717] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     8.717]     Entry deleted from font path.
[     8.717] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     8.717]     Entry deleted from font path.
[     8.717] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     8.717]     Entry deleted from font path.
[     8.717] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     8.717]     Entry deleted from font path.
[     8.717] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[     8.718] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     8.718] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     8.718] (WW) Disabling Keyboard0
[     8.718] (WW) Disabling Mouse0
[     8.718] (II) Loader magic: 0x823ada0
[     8.718] (II) Module ABI versions:
[     8.718]     X.Org ANSI C Emulation: 0.4
[     8.718]     X.Org Video Driver: 10.0
[     8.718]     X.Org XInput driver : 12.3
[     8.718]     X.Org Server Extension : 5.0
[     8.719] (--) PCI:*(0:1:0:0) 10de:1200:3842:1561 rev 161, Mem @ 0xf8000000/33554432, 0xd0000000/134217728, 0xdc000000/67108864, I/O @ 0x0000ef00/128, BIOS @ 0x????????/524288
[     8.719] (II) Open ACPI successful (/var/run/acpid.socket)
[     8.719] (II) LoadModule: "extmod"
[     8.720] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[     8.720] (II) Module extmod: vendor="X.Org Foundation"
[     8.720]     compiled for 1.10.4, module version = 1.0.0
[     8.720]     Module class: X.Org Server Extension
[     8.720]     ABI class: X.Org Server Extension, version 5.0
[     8.720] (II) Loading extension MIT-SCREEN-SAVER
[     8.720] (II) Loading extension XFree86-VidModeExtension
[     8.720] (II) Loading extension XFree86-DGA
[     8.720] (II) Loading extension DPMS
[     8.720] (II) Loading extension XVideo
[     8.720] (II) Loading extension XVideo-MotionCompensation
[     8.720] (II) Loading extension X-Resource
[     8.720] (II) LoadModule: "dbe"
[     8.720] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[     8.720] (II) Module dbe: vendor="X.Org Foundation"
[     8.720]     compiled for 1.10.4, module version = 1.0.0
[     8.721]     Module class: X.Org Server Extension
[     8.721]     ABI class: X.Org Server Extension, version 5.0
[     8.721] (II) Loading extension DOUBLE-BUFFER
[     8.721] (II) LoadModule: "glx"
[     8.721] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[     8.870] (II) Module glx: vendor="NVIDIA Corporation"
[     8.870]     compiled for 4.0.2, module version = 1.0.0
[     8.870]     Module class: X.Org Server Extension
[     8.870] (II) NVIDIA GLX Module  295.20  Mon Feb  6 20:47:25 PST 2012
[     8.870] (II) Loading extension GLX
[     8.870] (II) LoadModule: "record"
[     8.871] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[     8.871] (II) Module record: vendor="X.Org Foundation"
[     8.871]     compiled for 1.10.4, module version = 1.13.0
[     8.871]     Module class: X.Org Server Extension
[     8.871]     ABI class: X.Org Server Extension, version 5.0
[     8.871] (II) Loading extension RECORD
[     8.871] (II) LoadModule: "dri"
[     8.871] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[     8.871] (II) Module dri: vendor="X.Org Foundation"
[     8.871]     compiled for 1.10.4, module version = 1.0.0
[     8.871]     ABI class: X.Org Server Extension, version 5.0
[     8.871] (II) Loading extension XFree86-DRI
[     8.871] (II) LoadModule: "dri2"
[     8.872] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[     8.872] (II) Module dri2: vendor="X.Org Foundation"
[     8.872]     compiled for 1.10.4, module version = 1.2.0
[     8.872]     ABI class: X.Org Server Extension, version 5.0
[     8.872] (II) Loading extension DRI2
[     8.872] (II) LoadModule: "nvidia"
[     8.872] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     8.875] (II) Module nvidia: vendor="NVIDIA Corporation"
[     8.875]     compiled for 4.0.2, module version = 1.0.0
[     8.875]     Module class: X.Org Video Driver
[     8.876] (II) NVIDIA dlloader X Driver  295.20  Mon Feb  6 20:27:19 PST 2012
[     8.877] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     8.877] (++) using VT number 7

[     8.877] (II) Loading sub module "fb"
[     8.877] (II) LoadModule: "fb"
[     8.877] (II) Loading /usr/lib/xorg/modules/libfb.so
[     8.877] (II) Module fb: vendor="X.Org Foundation"
[     8.877]     compiled for 1.10.4, module version = 1.0.0
[     8.877]     ABI class: X.Org ANSI C Emulation, version 0.4
[     8.877] (II) Loading sub module "wfb"
[     8.877] (II) LoadModule: "wfb"
[     8.878] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     8.878] (II) Module wfb: vendor="X.Org Foundation"
[     8.878]     compiled for 1.10.4, module version = 1.0.0
[     8.878]     ABI class: X.Org ANSI C Emulation, version 0.4
[     8.878] (II) Loading sub module "ramdac"
[     8.878] (II) LoadModule: "ramdac"
[     8.878] (II) Module "ramdac" already built-in
[     8.878] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     8.878] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     8.878] (II) Loading /usr/lib/xorg/modules/libfb.so
[     8.878] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     8.878] (==) NVIDIA(0): RGB weight 888
[     8.878] (==) NVIDIA(0): Default visual is TrueColor
[     8.878] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     8.878] (**) NVIDIA(0): Enabling 2D acceleration
[    10.307] (II) NVIDIA(GPU-0): Display (HP w2408 (CRT-0)) does not support NVIDIA 3D Vision
[    10.307] (II) NVIDIA(GPU-0):     stereo.
[    10.308] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 560 Ti (GF114) at PCI:1:0:0 (GPU-0)
[    10.308] (--) NVIDIA(0): Memory: 1048576 kBytes
[    10.308] (--) NVIDIA(0): VideoBIOS: 70.24.2e.00.62
[    10.308] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    10.308] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    10.308] (--) NVIDIA(0): Connected display device(s) on GeForce GTX 560 Ti at
[    10.308] (--) NVIDIA(0):     PCI:1:0:0
[    10.308] (--) NVIDIA(0):     HP w2408 (CRT-0)
[    10.308] (--) NVIDIA(0): HP w2408 (CRT-0): 400.0 MHz maximum pixel clock
[    10.333] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    10.333] (**) NVIDIA(0):     device HP w2408 (CRT-0) (Using EDID frequencies has been
[    10.333] (**) NVIDIA(0):     enabled on all display devices.)
[    10.348] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    10.348] (==) NVIDIA(0): 
[    10.348] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    10.348] (==) NVIDIA(0):     will be used as the requested mode.
[    10.348] (==) NVIDIA(0): 
[    10.348] (II) NVIDIA(0): Validated modes:
[    10.348] (II) NVIDIA(0):     "nvidia-auto-select"
[    10.348] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    10.385] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[    10.385] (--) NVIDIA(0):     option
[    10.385] (--) Depth 24 pixmap format is 32 bpp
[    10.385] (II) NVIDIA: Using 1024.00 MB of virtual memory for indirect memory
[    10.385] (II) NVIDIA:     access.
[    10.395] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    10.430] (II) Loading extension NV-GLX
[    10.497] (==) NVIDIA(0): Disabling shared memory pixmaps
[    10.497] (==) NVIDIA(0): Backing store disabled
[    10.497] (==) NVIDIA(0): Silken mouse enabled
[    10.497] (**) NVIDIA(0): DPMS enabled
[    10.497] (II) Loading extension NV-CONTROL
[    10.497] (II) Loading extension XINERAMA
[    10.497] (II) Loading sub module "dri2"
[    10.497] (II) LoadModule: "dri2"
[    10.497] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    10.497] (II) Module dri2: vendor="X.Org Foundation"
[    10.497]     compiled for 1.10.4, module version = 1.2.0
[    10.497]     ABI class: X.Org Server Extension, version 5.0
[    10.497] (II) NVIDIA(0): [DRI2] Setup complete
[    10.497] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    10.497] (==) RandR enabled
[    10.497] (II) Initializing built-in extension Generic Event Extension
[    10.497] (II) Initializing built-in extension SHAPE
[    10.497] (II) Initializing built-in extension MIT-SHM
[    10.497] (II) Initializing built-in extension XInputExtension
[    10.497] (II) Initializing built-in extension XTEST
[    10.497] (II) Initializing built-in extension BIG-REQUESTS
[    10.497] (II) Initializing built-in extension SYNC
[    10.497] (II) Initializing built-in extension XKEYBOARD
[    10.497] (II) Initializing built-in extension XC-MISC
[    10.497] (II) Initializing built-in extension SECURITY
[    10.497] (II) Initializing built-in extension XINERAMA
[    10.498] (II) Initializing built-in extension XFIXES
[    10.498] (II) Initializing built-in extension RENDER
[    10.498] (II) Initializing built-in extension RANDR
[    10.498] (II) Initializing built-in extension COMPOSITE
[    10.498] (II) Initializing built-in extension DAMAGE
[    10.498] (II) Initializing built-in extension GESTURE
[    10.499] (II) Initializing extension GLX
[    10.520] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.528] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    10.528] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.528] (II) LoadModule: "evdev"
[    10.528] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.529] (II) Module evdev: vendor="X.Org Foundation"
[    10.529]     compiled for 1.10.2, module version = 2.6.0
[    10.529]     Module class: X.Org XInput Driver
[    10.529]     ABI class: X.Org XInput driver, version 12.3
[    10.529] (II) Using input driver 'evdev' for 'Power Button'
[    10.529] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.529] (**) Power Button: always reports core events
[    10.529] (**) Power Button: Device: "/dev/input/event1"
[    10.529] (--) Power Button: Found keys
[    10.529] (II) Power Button: Configuring as keyboard
[    10.529] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    10.529] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    10.529] (**) Option "xkb_rules" "evdev"
[    10.529] (**) Option "xkb_model" "pc105"
[    10.529] (**) Option "xkb_layout" "us"
[    10.531] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    10.531] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.531] (II) Using input driver 'evdev' for 'Power Button'
[    10.531] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.531] (**) Power Button: always reports core events
[    10.531] (**) Power Button: Device: "/dev/input/event0"
[    10.531] (--) Power Button: Found keys
[    10.531] (II) Power Button: Configuring as keyboard
[    10.531] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    10.531] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    10.531] (**) Option "xkb_rules" "evdev"
[    10.531] (**) Option "xkb_model" "pc105"
[    10.531] (**) Option "xkb_layout" "us"
[    10.532] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=9 (/dev/input/event6)
[    10.532] (II) No input driver/identifier specified (ignoring)
[    10.533] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event7)
[    10.533] (II) No input driver/identifier specified (ignoring)
[    10.533] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event8)
[    10.533] (II) No input driver/identifier specified (ignoring)
[    10.533] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event9)
[    10.533] (II) No input driver/identifier specified (ignoring)
[    10.537] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event2)
[    10.537] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[    10.537] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[    10.537] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.537] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[    10.537] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event2"
[    10.537] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[    10.537] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[    10.537] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.0/input/input2/event2"
[    10.537] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[    10.537] (**) Option "xkb_rules" "evdev"
[    10.537] (**) Option "xkb_model" "pc105"
[    10.537] (**) Option "xkb_layout" "us"
[    10.538] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event3)
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev pointer catchall"
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[    10.538] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[    10.538] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event3"
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 9 mouse buttons
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y relative axes
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[    10.538] (II) evdev-grail: failed to open grail, no gesture support
[    10.538] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[    10.538] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[    10.538] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[    10.538] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Adding scrollwheel support
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.538] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.1/input/input3/event3"
[    10.538] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[    10.538] (**) Option "xkb_rules" "evdev"
[    10.538] (**) Option "xkb_model" "pc105"
[    10.538] (**) Option "xkb_layout" "us"
[    10.538] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for relative axes.
[    10.538] (WW) Microsoft Microsoft® 2.4GHz Transceiver v6.0: ignoring absolute axes.
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration profile 0
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration factor: 2.000
[    10.538] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration threshold: 4
[    10.538] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/mouse0)
[    10.538] (II) No input driver/identifier specified (ignoring)
[    10.539] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event4)
[    10.539] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[    10.539] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[    10.539] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.539] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[    10.539] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event4"
[    10.539] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 1 mouse buttons
[    10.539] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[    10.539] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[    10.539] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[    10.540] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y absolute axes
[    10.540] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[    10.540] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[    10.540] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[    10.540] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Adding scrollwheel support
[    10.540] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[    10.540] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    10.540] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-3/4-3:1.2/input/input4/event4"
[    10.540] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[    10.540] (**) Option "xkb_rules" "evdev"
[    10.540] (**) Option "xkb_model" "pc105"
[    10.540] (**) Option "xkb_layout" "us"
[    10.540] (EE) Microsoft Microsoft® 2.4GHz Transceiver v6.0: failed to initialize for relative axes.
[    10.542] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[    10.542] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[    10.542] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for absolute axes.
[    10.542] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
[    10.542] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration profile 0
[    10.542] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration factor: 2.000
[    10.542] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration threshold: 4
[    10.542] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/js0)
[    10.542] (II) No input driver/identifier specified (ignoring)
[    10.545] (II) config/udev: Adding input device HDA ATI SB Headphone (/dev/input/event5)
[    10.545] (II) No input driver/identifier specified (ignoring)
[    21.649] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   263.044] (II) config/udev: removing device Microsoft Microsoft® 2.4GHz Transceiver v6.0
[   263.044] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Close
[   263.044] (II) UnloadModule: "evdev"
[   263.044] (II) Unloading evdev
[   263.252] (II) config/udev: removing device Microsoft Microsoft® 2.4GHz Transceiver v6.0
[   263.253] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Close
[   263.253] (II) UnloadModule: "evdev"
[   263.253] (II) Unloading evdev
[   263.396] (II) config/udev: removing device Microsoft Microsoft® 2.4GHz Transceiver v6.0
[   263.396] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Close
[   263.397] (II) UnloadModule: "evdev"
[   263.397] (II) Unloading evdev
[   267.508] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event2)
[   267.508] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[   267.508] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[   267.508] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   267.508] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[   267.508] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event2"
[   267.509] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[   267.509] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[   267.509] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:16.0/usb7/7-2/7-2:1.0/input/input10/event2"
[   267.509] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[   267.509] (**) Option "xkb_rules" "evdev"
[   267.509] (**) Option "xkb_model" "pc105"
[   267.509] (**) Option "xkb_layout" "us"
[   267.510] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event4)
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[   267.510] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[   267.510] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event4"
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 1 mouse buttons
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y absolute axes
[   267.510] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[   267.510] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[   267.510] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[   267.510] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Adding scrollwheel support
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[   267.510] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   267.510] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:16.0/usb7/7-2/7-2:1.2/input/input12/event4"
[   267.510] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[   267.510] (**) Option "xkb_rules" "evdev"
[   267.510] (**) Option "xkb_model" "pc105"
[   267.510] (**) Option "xkb_layout" "us"
[   267.511] (EE) Microsoft Microsoft® 2.4GHz Transceiver v6.0: failed to initialize for relative axes.
[   267.513] (WW) Touch X valuator does not match pointer X valuator, pointer emulation may be incorrect
[   267.513] (WW) Touch Y valuator does not match pointer Y valuator, pointer emulation may be incorrect
[   267.513] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for absolute axes.
[   267.513] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
[   267.513] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration profile 0
[   267.513] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration factor: 2.000
[   267.513] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration threshold: 4
[   267.516] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/js0)
[   267.517] (II) No input driver/identifier specified (ignoring)
[   267.518] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/event3)
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev pointer catchall"
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Applying InputClass "evdev keyboard catchall"
[   267.518] (II) Using input driver 'evdev' for 'Microsoft Microsoft® 2.4GHz Transceiver v6.0'
[   267.518] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: always reports core events
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Device: "/dev/input/event3"
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found 9 mouse buttons
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found scroll wheel(s)
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found relative axes
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found x and y relative axes
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found absolute axes
[   267.518] (II) evdev-grail: failed to open grail, no gesture support
[   267.518] (--) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Found keys
[   267.518] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as mouse
[   267.518] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Configuring as keyboard
[   267.518] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: Adding scrollwheel support
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: YAxisMapping: buttons 4 and 5
[   267.518] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   267.519] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:16.0/usb7/7-2/7-2:1.1/input/input11/event3"
[   267.519] (II) XINPUT: Adding extended input device "Microsoft Microsoft® 2.4GHz Transceiver v6.0" (type: KEYBOARD)
[   267.519] (**) Option "xkb_rules" "evdev"
[   267.519] (**) Option "xkb_model" "pc105"
[   267.519] (**) Option "xkb_layout" "us"
[   267.519] (II) Microsoft Microsoft® 2.4GHz Transceiver v6.0: initialized for relative axes.
[   267.519] (WW) Microsoft Microsoft® 2.4GHz Transceiver v6.0: ignoring absolute axes.
[   267.519] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) keeping acceleration scheme 1
[   267.519] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration profile 0
[   267.519] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration factor: 2.000
[   267.519] (**) Microsoft Microsoft® 2.4GHz Transceiver v6.0: (accel) acceleration threshold: 4
[   267.519] (II) config/udev: Adding input device Microsoft Microsoft® 2.4GHz Transceiver v6.0 (/dev/input/mouse0)
[   267.519] (II) No input driver/identifier specified (ignoring)
```
Same driver I'm using. Everything is loading fine.  I guess keep using your workaround, use the thread tools and mark this as "Solved". Yes a "new" card.

---

