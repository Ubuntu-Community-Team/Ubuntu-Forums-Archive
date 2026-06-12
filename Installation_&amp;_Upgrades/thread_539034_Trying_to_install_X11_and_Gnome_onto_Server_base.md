---
title: "Trying to install X11 and Gnome onto Server base"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by raheesom on 2007-08-30
Where do I start??

I would have used  the  workstation install but it doesn't handle  mirrored LVM disks like I've got, the server install handles the disks fine.

So I'm trying to install X11 and Gnome on top of the Fiesty Server install.

X11 is failing to load with a fonts issue.   The fonts its looking for are not installed.

I've compared the Fiesty LiveCD setup to my server setup, the font directories _are_ different!
First, my /etc/X11/xorg.conf font paths tto  not match with whats in the file strructure.
xorg.conf gives the font paths as  /usr/share/fonts/X11/****
The actual directory structure gives the dircecttories as /usr/share/X11/fonts/****, except there are no 
font directories!  The only directories under "X111/fonts/" is util and encodings.

Xorg cannot find the font directories specified, therefore resots to the compiled in directories which are also wrong, therefore Xorg  (X11) failes to load!

How can I get the fonts installed into the directories that _are_ in the file structure??
(where do I get  the fonts from and how do I install them??

The font directories I need to fill are :
/misc, /cyrillic, /100dpi/:unscaled, /75dpi/:unscaled, Type1, /100dpi, /75dpi.

If anyone wants, I can post the /var/log/Xorg.0.log file here, but it basically says much the same as I'm saying here.

---

### Post by Pumalite on 2007-08-30
Have you tried just: sudo apt-get install gnome-desktop?

---

### Post by raheesom on 2007-08-31
Well, originally I installed Gnome first (then X11 when I realised that Gnome did not install X11 on its 
own - I would think X11 is a dependancy wouldn't you??).   

On my native install (not LiveCD) I have not yet got the Gnome desktop to show at all.

I can install Gnome again --- previously I think I used the command sudo apt-get install gnome , not "gnome-desktop".


Should I have installed X11 first then Gnome second originally? Would the fonts have instsalled properly 
that way?   Do the fonts come from tGnome, not from X11?

sorry re typos -- I can't see the fonts well on this editor at all!  I'm using FFox on Mac   The fonts/cursor are out of sync.   Can't see anything sometiimes!

---

### Post by Pumalite on 2007-08-31
I might be wrong, but up to now, I thought doing sudo apt-get install gnome-desktop. you got everything related to a graphical user interface. (therefore xorg.conf which is within X11)

---

### Post by raheesom on 2007-08-31
I tried reinstalling Gnome using "sudo apt-get iinstall Gnome-desktop-environment".  This reinstalled Gnome, but I'm now back to where I started from....  Both X11 and Gnome installed, no fonts working on X11!!

I'm going to paste in the /var/log/Xorg.0.log file to show what happens when X11 tries to lod:

(I found some fonts dirs after Gnome installed , I created  a fonts.dir file (sudo  mkfontsdir)  but the  "fonts.dir" files are all empty (no fonts definitions in them).  therefore they don't work in the Xorg.conf file.   I assume the fonts are not valid X11 fonts??)


======================================================

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux rah-ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64
Build Date: 04 April 2007
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Aug 31 15:21:04 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "nVidia Corporation NV18 [GeForce4 MX 4000]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/truetype".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/truetype").
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/type1".
	Entry deleted from font path.
	(Run 'mkfontdir' on "/usr/share/fonts/type1").
(WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
	Entry deleted from font path.
(WW) FontPath is completely invalid.  Using compiled-in default.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/X11R6/lib/X11/fonts/misc,
	/usr/share/fonts/X11/cyrillic,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/X11R6/lib/X11/fonts/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7a16e0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.1
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:06:0: chip 1022,7460 card 0000,0000 rev 07 class 06,04,00 hdr 01

<snip>

(II) PCI: 05:00:0: chip 10de,0185 card 1043,8197 rev c1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:6:0), (0,3,3), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 3 I/O range:
	[0] -1	0	0x0000a000 - 0x0000a0ff (0x100) IX[B]
	[1] -1	0	0x0000a400 - 0x0000a4ff (0x100) IX[B]
	[2] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
	[3] -1	0	0x0000ac00 - 0x0000acff (0x100) IX[B]
	[4] -1	0	0x0000b000 - 0x0000b0ff (0x100) IX[B]
	[5] -1	0	0x0000b400 - 0x0000b4ff (0x100) IX[B]
	[6] -1	0	0x0000b800 - 0x0000b8ff (0x100) IX[B]
	[7] -1	0	0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 3 non-prefetchable memory range:
	[0] -1	0	0xfc700000 - 0xfc8fffff (0x200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:10:0), (0,2,2), BCTRL: 0x0005 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfc600000 - 0xfc6fffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xe4300000 - 0xe43fffff (0x100000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:11:0), (0,1,1), BCTRL: 0x0005 (VGA_EN is cleared)
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:24:0), (0,0,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Host-to-PCI bridge:
(II) Bus 4: bridge is at (4:0:0), (4,4,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 4 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 4 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 4 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 5: bridge is at (4:1:0), (4,5,5), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 5 non-prefetchable memory range:
	[0] -1	0	0xfca00000 - 0xfeafffff (0x2100000) MX[B]
(II) Bus 5 prefetchable memory range:
	[0] -1	0	0xe4500000 - 0xec4fffff (0x8000000) MX[B]
(--) PCI:*(5:0:0) nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] rev 193, Mem @ 0xfd000000/24, 0xe8000000/26, BIOS @ 0xfeae0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf0000000 to 0xefffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xf0000000 - 0xefffffff (0x0) MX[B]O
	[1] -1	0	0xfc8f8000 - 0xfc8fbfff (0x4000) MX[B]

<snip>
	
	[26] -1	0	0x0000c400 - 0x0000c41f (0x20) IX[B]
	[27] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[28] -1	0	0x0000a800 - 0x0000a8ff (0x100) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts//libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 7.2.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.1.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:37:27 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 05:00:0
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 1.1
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]

<snip>

	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
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
(II) NVIDIA(0): NVIDIA GPU GeForce4 MX 4000 at PCI:5:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 65536 kBytes
(--) NVIDIA(0): VideoBIOS: 04.18.20.47.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce4 MX 4000 at PCI:5:0:0:
(--) NVIDIA(0):     HSD AG191 (CRT-0)
(--) NVIDIA(0): HSD AG191 (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(WW) NVIDIA(0): 
(WW) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
(WW) NVIDIA(0):     will be used as the requested mode.
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (85, 86); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xebffffff (0x4000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]

<snip>

	[34] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[35] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "nvidia-auto-select"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/misc, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/:unscaled, removing from list!
Could not init font path element /usr/share/fonts/X11/Type1, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi, removing from list!
Could not init font path element /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, removing from list!

Fatal server error:
could not open default font 'fixed'

======================================================

---

### Post by Pumalite on 2007-08-31
Sorry, but I'm out of my depth here. Somebody else will have to help you. Patience, somebody will chime in.

---

### Post by raheesom on 2007-08-31
Yup, I'm out of my depth as well!!  :)

I'm also trying Ubuntu "Launchpad" for ideas......  I wonder why Feisty Server install does not offer a Gnome install??  I must request that!

---

### Post by louieb on 2007-08-31
Here you go. I've used this to put a desktop on server installs before. works just fine.
[HOWTO: Leightweight Gnome - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=298818&highlight=xorg+gdm+gnome-core")

---

### Post by raheesom on 2007-08-31
louieb

Thanks for the contribution;  I'll follow your suggestions and see how far I get....

So, it looks like ubuntu server install is not supposed to have a GUI put onto it easily??

---

### Post by maybeway36 on 2007-08-31
Did you install the whole "xorg" metapackage? You could also try "ubuntu-desktop".

---

### Post by louieb on 2007-08-31
> **raheesom said:**
> ... looks like ubuntu server install is not supposed to have a GUI put onto it easily??
Actually if you want the full blown Ubuntu desktop It can be quite easy It just takes a while. I take it the only reason you went with the server install is to use LVM. IF so this is what I'd do

Do a fresh server install
then run the follow commands[LIST]
[*]sudo aptitiude update[LIST]
[*]This  syncs your install with the repositories[/LIST] 
[*]sudo aptitude dist-upgrade[LIST]
[*]This installs any updates to the server software since the CD was released[/LIST] 
[*]sudo aptitude install ubuntu-desktop[LIST]
[*]This  installs the full blown Ubuntu Desktop much the same as using the alternate CD. You have to hang around while it does this. It going to ask some questions while it sets up xorg.[/LIST] [/LIST]

---

### Post by raheesom on 2007-09-03
Thanks Loui,


I followed the suggestions about doing  a ubuntu desktop install.

This seems to have worked; I can now get into Gnome.
Interesting how you have to know the right modules to install  the full desktop.

Anyway, just thought I'd let you know that I've got there.....

Although one minor problem remains.....  the machine gets to the grub menu, after that until the Gnome login screen the monitor cannot show anything (on screen eror msg saying "signal out of monitor parameters" or something similar.)

Its not a massive problem, cause I can now use the machine, but it would be nice to get that issue out the way.

I assume that somehow the screen resolution is incorrectly set, or fonts not working??

---

### Post by louieb on 2007-09-03
> **raheesom said:**
> ... "signal out of monitor parameters"...
My Display says "input not supported".  anyway try a  temporary edit next time you boot. Press **e** to edit the entry and remove the **quiet splash** from the kernel line. Probably has something to do with a thing called frame buffering. If it works just make the same change to /boot/grub/menu.lst to make it stick. [BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

---

