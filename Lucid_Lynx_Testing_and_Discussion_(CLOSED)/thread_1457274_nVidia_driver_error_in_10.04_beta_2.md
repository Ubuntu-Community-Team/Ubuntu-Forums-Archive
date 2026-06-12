---
title: "nVidia driver error in 10.04 beta 2"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Scunnered on 2010-04-18
Can someone please offer guidance in respect of the above.  I have downloaded 10.04 beta 2 and was offered the driver download which I duly accepted.

When I downloaded the nVidia accelerated graphics driver (version current)(recommended) an error message was displayed referring me to /var/log/jockey.log.  Having found this I attempted to post the information into a new thread only to be informed that I had far too much information and it could / would not be accepted.

I would like to post this to the correct area of the forum and would also like to show the log details.  How do I best achieve this aim?

Thanking you in anticipation

---

### Post by klemes on 2010-04-18
Maybe you could post some more information.
Like what type of video card are you running,what version of driver are you using,and is the xserver actually running OK?(meaning do you actually get into the graphic environment or not?),
And maybe you could start by providing your /var/log/Xorg.0.log please?

---

### Post by Scunnered on 2010-04-18
Thanks for your reply. 

I had an accident with my laptop today and had to resort to an old system and don't realy know what my graphics card is as it was bought so long ago.

When the nVidia driver was offered I opted for the recommended one.

The log details you have requested are :

```
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux scunnered-desktop 2.6.32-19-generic #28-Ubuntu SMP Wed Mar 31 17:46:20 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-19-generic root=UUID=101cc819-1e7e-409c-be62-bd19e50fe89c ro quiet splash
Build Date: 30 March 2010  08:17:06PM
xorg-server 2:1.7.6-2ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Apr 18 16:37:22 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:5:0) 10de:0242:105b:0d04 nVidia Corporation C51G [GeForce 6100] rev 162, Mem @ 0xfb000000/16777216, 0xe0000000/268435456, 0xfc000000/16777216, BIOS @ 0x????????/131072
(II) Open ACPI successful (/var/run/acpid.socket)
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Thu Mar 11 23:39:48 PST 2010
(II) Loading extension GLX
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.36.15  Thu Mar 11 22:01:49 PST 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00@00:05:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) Apr 18 16:37:23 NVIDIA(0): Enabling RENDER acceleration
(II) Apr 18 16:37:23 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Apr 18 16:37:23 NVIDIA(0):     enabled.
(II) Apr 18 16:37:24 NVIDIA(0): NVIDIA GPU GeForce 6100 (C51) at PCI:0:5:0 (GPU-0)
(--) Apr 18 16:37:24 NVIDIA(0): Memory: 262144 kBytes
(--) Apr 18 16:37:24 NVIDIA(0): VideoBIOS: 05.51.28.45.17
(--) Apr 18 16:37:24 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Apr 18 16:37:24 NVIDIA(0): Connected display device(s) on GeForce 6100 at PCI:0:5:0:
(--) Apr 18 16:37:24 NVIDIA(0):     HSD HG221A (CRT-0)
(--) Apr 18 16:37:24 NVIDIA(0): HSD HG221A (CRT-0): 350.0 MHz maximum pixel clock
(II) Apr 18 16:37:24 NVIDIA(0): Assigned Display Device: CRT-0
(==) Apr 18 16:37:24 NVIDIA(0): 
(==) Apr 18 16:37:24 NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(==) Apr 18 16:37:24 NVIDIA(0):     will be used as the requested mode.
(==) Apr 18 16:37:24 NVIDIA(0): 
(II) Apr 18 16:37:24 NVIDIA(0): Validated modes:
(II) Apr 18 16:37:24 NVIDIA(0):     "nvidia-auto-select"
(II) Apr 18 16:37:24 NVIDIA(0): Virtual screen size determined to be 1680 x 1050
(--) Apr 18 16:37:24 NVIDIA(0): DPI set to (88, 88); computed from "UseEdidDpi" X config
(--) Apr 18 16:37:24 NVIDIA(0):     option
(==) Apr 18 16:37:24 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Apr 18 16:37:24 NVIDIA(0): Initialized GPU GART.
(II) Apr 18 16:37:24 NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) Apr 18 16:37:24 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Apr 18 16:37:24 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(==) NVIDIA(0): DPMS enabled
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
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/event3)
(**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev keyboard catchall"
(**) Logitech 2.4GHz Cordless Desktop: always reports core events
(**) Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event3"
(II) Logitech 2.4GHz Cordless Desktop: Found keys
(II) Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/event4)
(**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev pointer catchall"
(**) Logitech 2.4GHz Cordless Desktop: Applying InputClass "evdev keyboard catchall"
(**) Logitech 2.4GHz Cordless Desktop: always reports core events
(**) Logitech 2.4GHz Cordless Desktop: Device: "/dev/input/event4"
(II) Logitech 2.4GHz Cordless Desktop: Found 10 mouse buttons
(II) Logitech 2.4GHz Cordless Desktop: Found scroll wheel(s)
(II) Logitech 2.4GHz Cordless Desktop: Found relative axes
(II) Logitech 2.4GHz Cordless Desktop: Found x and y relative axes
(II) Logitech 2.4GHz Cordless Desktop: Found absolute axes
(II) Logitech 2.4GHz Cordless Desktop: Found keys
(II) Logitech 2.4GHz Cordless Desktop: Configuring as mouse
(II) Logitech 2.4GHz Cordless Desktop: Configuring as keyboard
(**) Logitech 2.4GHz Cordless Desktop: YAxisMapping: buttons 4 and 5
(**) Logitech 2.4GHz Cordless Desktop: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech 2.4GHz Cordless Desktop" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "evdev"
(**) Option "xkb_layout" "gb"
(II) Logitech 2.4GHz Cordless Desktop: initialized for relative axes.
(WW) Logitech 2.4GHz Cordless Desktop: ignoring absolute axes.
(II) config/udev: Adding input device Logitech 2.4GHz Cordless Desktop (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring) 

```
I hope this is of assistance

---

### Post by klemes on 2010-04-18
According to your Xorg.0.log you are running an NVIDIA GrForce6100 with the nvidia driver 195.36.15,and everything is just the way it is supposed to be :no xorg errors no warnings not one thing.I am afraid I don't really understand the nature of your problem but it does not seem there are any X -related problems to be found in your Xorg.0.log and X should be running fine on your listed hardware.
Please correct me if I am wrong on this one.

---

### Post by overdrank on 2010-04-18
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by Scunnered on 2010-04-18
**klemes**

Again my thanks for your reply.  

I am perfectly happy to accept what you say as everything appears to work as before. What confused me totally was the error message and the inability of the forum to accept the jockey.log.

As no doubt you have worked out a lot of Ubuntu is straight over my head however I love it.  If nothing else it is a wonderful learning experience.

As an aside I attempted to load Opera and it is playing up something horrible. So I am giving it the boot until the final 10.04 arrives.  They claim that there are old files needing updated.

Again thanks vm

---

### Post by dino99 on 2010-04-18
Try into console:

- sudo gedit /etc/X11/xorg.conf  and comment (#) every line: lucid dont need xorg.conf by default, and save it.

- sudo gedit /etc/apt/sources.list and check that every line is related to lucid (only official repo, no third party or ppa)

- sudo apt-get clean / autoclean / autoremove (one by one)

- sudo apt-get update

- sudo apt-get install -f

- sudo apt-get install  nvidia-current / nvidia-settings / nvidia-common / nvidia-current-modaliases / xserver-xorg-video-nouveau

- reboot

- then goto system - admin - hardware driver  and check that nvidia current is selected and activated.

- if you have still error, run nvidia-xconfig (will recreate a xorg.conf )

---

### Post by cariboo on 2010-04-18
> **Scunnered said:**
> **klemes**

Again my thanks for your reply.  

I am perfectly happy to accept what you say as everything appears to work as before. **What confused me totally was the error message and the inability of the forum to accept the jockey.log.**

As no doubt you have worked out a lot of Ubuntu is straight over my head however I love it.  If nothing else it is a wonderful learning experience.

As an aside I attempted to load Opera and it is playing up something horrible. So I am giving it the boot until the final 10.04 arrives.  They claim that there are old files needing updated.

Again thanks vm

You would have gotten an error message as to why you couldn't post your log file, I suspect that your total post was over 5000 characters long which is the maximum post length.

---

### Post by Scunnered on 2010-04-18
**Dino99**

This is where my inexperience really shows up. If I enter your first instruction into the terminal it displays thus :

"Section "Screen"
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
EndSection"

and you say comment # each line.  Where should I be placing the # ?

Your 2nd instruction appears to be OK as only Lucid is mentioned.  In the 3rd I assume that clean, autoclean and remove are 3 separate operations.  Why is there the need to remove?

apt-get update was the first thing that I did after installation so it this required again?

You ask me to apt-get install -f. Can you please explain what this does as this is the first time that I have seen this instruction and don't know what the -f is.

I think that the others are clear enough even for me.

Please bear with me but as I said earlier "it is a wonderful learning experience".

My sincere thanks for your kind assistance and your patience.

PS. Is there an easy way to remove Opera.  Is it as simple as sudo apt-get remove -opera?

---

### Post by dino99 on 2010-04-18
you're welcome,  ):P

that's remind me some times ago when linux was like exotic language for me #-o , was searching and asking for every things, now i'm more confortable  :-\"

So we have to learn again and again then you feel like a genius and can help the others  :lolflag:

about your questions:

- commenting is equal to put # at the beginning of a line
- you're right, its week end and i'm lazy too: every time i've put /, you have to understand to repeat the command but with the second word
- your xorg.conf seems ok
- install -f search for broken installation and try to repair it ( f stand for force)

- removing a package: if it's part of the distro , uninstalling it will remove meta-package too ( ubuntu-destop), its not important as the meta package only list the default packages)
To do this, the easiest way is to goto: system -> admin -> synaptic : search the package (opera) then select it and choose remove completly, thats all.

---

### Post by plun on 2010-04-18
Just restart and it works.....

[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/552653](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/552653)

Please also update your installation because its fixed

---

### Post by Scunnered on 2010-04-18
**cariboo907**

I suspect that as I wanted to give all the log information that by selecting all and pasting it into the post was overkill.  Following the link provided by **plun** it confirms my suspicions.
[B]
dino99[/B]

Thanks for all the explanations and guidance. It took me a bit of time in processing the instructions but I managed to do so.  That in its self is progress as earlier I would have run a mile if anyone said use the terminal.

My sincere thanks to everyone for their kind assistance

---

