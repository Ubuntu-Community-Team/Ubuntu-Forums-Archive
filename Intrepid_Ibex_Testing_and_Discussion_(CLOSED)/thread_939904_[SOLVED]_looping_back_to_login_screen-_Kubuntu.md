---
title: "[SOLVED] looping back to login screen- Kubuntu"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pjnsmb on 2008-10-06
Help please- I am going mad trying without success to solve this !

I have successfully run Ubuntu 8.04.1 . 

Trying a clean install of Alpha and Beta Ubuntu 8.10 on a separate partition has proved unsuccessful for either attempt  in as much as I have never been able to get past a black screen prior to the login screen showing.

I have now tried a fresh install of Kubuntu 8.04.1 followed by an upgrade to 8.10.

This has got me to the stage that I can get as far as the login screen without trouble.

Once I try and login though the login screen changes to a large white rectangle box on a black screen for a second and then returns back to the login screen again. 

I seem to think it's a graphics problem - though I am fairly new to Linux.............

I have tried booting in recovery mode, and all it's options, without success.

from terminal I have tried - sudo dpkg-reconfigure xserver-xorg
   and    -sudo dpkg-reconfigure phigh xserver-xorg  

This is the info in my xorg.conf file :

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


Not a lot of information in there -

can someone advise me if it looks correct and how to proceed forwards to be able to log in  ?

thanks for any advice given.....................

---

### Post by milton1 on 2008-10-06
If that is all the info in your xorg.conf, then it would seem x is failing utterly due to lack of proper settings. Your device section needs hardware and driver information, and your monitor needs hardware information. What video card are you using? what driver? check to see if you have the video drivers installed at all. (drop to a shell and execute the following to see output of included video drivers) ```
 dpkg -l | grep xserver-xorg-video 
```

---

### Post by pjnsmb on 2008-10-06
I seem to have the video drivers installed 
using your command lists 12 or more drivers including 2 for Intel.
I have an Intel i845 video card and it looks like the correct drivers are installed for the card.............

---

### Post by milton1 on 2008-10-06
ok, then you need a line in the device section of xorg.conf that says ```
 Driver "i810"
BusID "PCI:0:2:0" 
``` Your BusID may be different, this is the physical address of the graphics card. I am surprised that these entries are not included in your xorg.conf. They should have been included in the default setup. If reconfiguring did not help, I would suggest a more extreme effort of trying to reinstall the video drivers, or even X.

---

### Post by pjnsmb on 2008-10-06
adding those lines has sent me initially to tty1 on a normal startup and then after a couple of restarts back to the original login screen without any change ?
I would appreciate your help on reinstalling drivers or X though..............

---

### Post by pjnsmb on 2008-10-07
when I run   "sudo dpkg-reconfigure xserver-xorg" all I get to amend is keyboard settings - nothing shows for screen or video settings !

Can anyone throw any light on this problem please ?

---

### Post by pjnsmb on 2008-10-08
OK

After reading other threads I appreciate that the xorg.conf file does not now show all the info like the old way.

After I enter my password and press "enter" the login screen moves on to show KDE 4.1 screen trying to load 4 or 5 coloured boxes -but then immediately reverts back to the login screen................

I have tried xfix from recovery mode and updated from apt from console but I am no further forward in getting past the login screen...............

Any ideas from you experts ?

thanks  in anticipation

---

### Post by marttali on 2008-10-08
few things that might help:
1. instead of apt-get, try to use aptitude for update
2. after update run sudo depmod -a
3. do this:
mv /home/myusername/.kde /home/myusename/.kdebac
ln -s /home/myusername/.kde4 /home/myusername/.kde
4. if it doesn't help, check logs (in var/log)
5. if you manage to log in, remove *-kde4 packages

---

### Post by pjnsmb on 2008-10-08
no success yet !

not quite sure which logs would help -and cannot make sense of them anyway !

But :

Xorg.0.log

```
(WW) Failed to open protocol names file /etc/X11/xserver/protocol.txt
X.Org X Server 1.5.1
Release Date: 23 September 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server i686 Ubuntu
Current Operating System: Linux peter-desktop 2.6.27-4-generic #1 SMP Wed Sep 24 01:30:51 UTC 2008 i686
Build Date: 06 October 2008  03:13:08PM
xorg-server 2:1.5.1-1ubuntu2 (buildd@rothera.buildd) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct  8 11:14:08 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d8a40
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 4.1
	X.Org XInput driver : 2.1
	X.Org Server Extension : 1.1
	X.Org Font Renderer : 0.6
(II) Loader running on linux
(--) using VT number 7

(--) PCI:*(0@0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 1, Mem @ 0xe8000000/0, 0xfeb80000/0
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
	compiled for 1.5.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
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
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.5.1, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"

(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 2.4.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 4.1
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
	965GM, 965GME/GLE, G33, Q35, Q33,
	Mobile Intel® GM45 Express Chipset,
	Intel Integrated Graphics Device, G45/G43, Q45/Q43
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"

(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"

(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 0.1.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(--) intel(0): Linear framebuffer at 0xE8000000
(--) intel(0): IO registers at addr 0xFEB80000
(II) intel(0): 1 display pipe available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "int10"
(II) LoadModule: "int10"

(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 832 kB
(II) intel(0): VESA VBE OEM: Intel(r)845G/845GL/845GE/845GV Graphics Chip Accelerated VGA BIOS

(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)845G/845GL/845GE/845GV Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"

(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"

(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"

(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"

(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"

(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
	compiled for 1.5.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 4.1
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): EDID vendor "DEL", prod id 40970
(II) intel(0): Using EDID range info for horizontal sync
(II) intel(0): Using EDID range info for vertical refresh
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): Modeline "1152x864"x75.0  104.99  1152 1224 1352 1552  864 865 868 902 -hsync +vsync (67.7 kHz)
(II) intel(0): Modeline "1280x1024"x60.0  108.88  1280 1360 1496 1712  1024 1025 1028 1060 -hsync +vsync (63.6 kHz)
(II) intel(0): EDID vendor "DEL", prod id 40970
(II) intel(0): Output VGA connected
(II) intel(0): Using exact sizes for initial modes
(II) intel(0): Output VGA using initial mode 1280x1024
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 892 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Intel XvMC decoder disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(**) intel(0): Display dimensions: (340, 270) mm
(**) intel(0): DPI set to (119, 150)
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "exa"
(II) LoadModule: "exa"

(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
	compiled for 1.5.1, module version = 2.4.0
	ABI class: X.Org Video Driver, version 4.1
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61180 (LVDS) changed from 0x0000b011 to 0x0000b001
(WW) intel(0): LVDS before: disabled, pipe A, 18 bit, 1 channel
(WW) intel(0): LVDS after: disabled, pipe A, 18 bit, 1 channel
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 491008 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 1964028 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(==) intel(0): VideoRam: 131072 KB
(II) intel(0): Attempting memory allocation with tiled buffers.
(WW) intel(0): Failed to allocate texture space.
(II) intel(0): Tiled allocation failed.
(II) intel(0): Attempting memory allocation with untiled buffers.
(II) intel(0): Untiled allocation successful.
(II) intel(0): [drm] Registers = 0xfeb80000
(II) intel(0): [drm] ring buffer = 0xe8000000
(II) intel(0): [drm] mapped front buffer at 0xe80e0000, handle = 0xe80e0000
(II) intel(0): [drm] mapped back buffer at 0xea7f0000, handle = 0xea7f0000
(II) intel(0): [drm] mapped depth buffer at 0xeb1b4000, handle = 0xeb1b4000
(II) intel(0): [drm] mapped classic textures at 0xebb78000, handle = 0xebb78000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(II) EXA(0): Offscreen pixmap area of 30720000 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x000df000 (pgoffset 223)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x000e0000 (pgoffset 224)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x00aa4000 (pgoffset 2724)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x027f0000 (pgoffset 10224)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x031b4000 (pgoffset 12724)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x03b78000 (pgoffset 15224)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00024fff: HW cursors (20 kB)
(II) intel(0): 0x00025000-0x0002cfff: logical 3D context (32 kB)
(II) intel(0): 0x000df000:            end of stolen memory
(II) intel(0): 0x000df000-0x000dffff: overlay registers (4 kB, 0x0000000032b80000 physical
)
(II) intel(0): 0x000e0000-0x00aa3fff: front buffer (10000 kB)
(II) intel(0): 0x00aa4000-0x027effff: exa offscreen (30000 kB)
(II) intel(0): 0x027f0000-0x031b3fff: back buffer (10000 kB)
(II) intel(0): 0x031b4000-0x03b77fff: depth buffer (10000 kB)
(II) intel(0): 0x03b78000-0x05b77fff: classic textures (32768 kB)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) AIGLX: enabled GLX_MESA_copy_sub_buffer
(II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
(II) AIGLX: enabled GLX_texture_from_pixmap with driver support
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 270
Error in I830WaitLpRing(), timeout for 2 seconds
pgetbl_ctl: 0x7ffe0001 getbl_err: 0x00000021
ipeir: 0x00000000 iphdr: 0x54f00006
LP ring tail: 0x000012a0 head: 0x000012c4 len: 0x0001f001 start 0x00000000
eir: 0x0000 esr: 0x0010 emr: 0xff7b
instdone: 0xff41 instpm: 0x0000
memmode: 0x00000000 instps: 0x00000031
hwstam: 0xfffe ier: 0x0002 imr: 0x053c iir: 0x00c0
Ring at virtual 0xaf964000 head 0x12c4 tail 0x12a0 count 32759
Ring at virtual 0xaf964000 head 0x12c4 tail 0x12a0 count 32759
Ring at virtual 0xaf964000 head 0x12c4 tail 0x12a0 count 32759
Ring at virtual 0xaf964000 head 0x12c4 tail 0x12a0 count 32759
Ring at virtual 0xaf964000 head 0x12c4 tail 0x12a0 count 32759
Ring at virtual 0xaf964000 head 0x12c4 tail 0x12a0 count 32759
Ring at virtual 0xaf964000 head 0x12c4 tail 0x12a0 count 32759
Ring at virtual 0xaf964000 head 0x12c4 tail 0x12a0 count 32759
Ring at virtual 0xaf964000 head 0x12c4 tail 0x12a0 count 32759
	000011e0: 00000000	MI_NOOP                                  1
	000011e4: 00000000	MI_NOOP                                  1
	000011e8: 00000000	MI_NOOP                                  1
	000011ec: 00000000	MI_NOOP                                  1
	000011f0: 00000000	MI_NOOP                                  1

	000011f4: 00000000	MI_NOOP                                  1
	000011f8: 00000000	MI_NOOP                                  1
	000011fc: 00000000	MI_NOOP                                  1
	00001200: 00000000	MI_NOOP                                  1
	00001204: 00000000	MI_NOOP                                  1
	00001208: 00000000	MI_NOOP                                  1
	0000120c: 00000000	MI_NOOP                                  1
	00001210: 00000000	MI_NOOP                                  1
	00001214: 00000000	MI_NOOP                                  1
	00001218: 00000000	MI_NOOP                                  1
	0000121c: 00000000	MI_NOOP                                  1
	00001220: 00000000	MI_NOOP                                  1
	00001224: 00000000	MI_NOOP                                  1
	00001228: 00000000	MI_NOOP                                  1
	0000122c: 00000000	MI_NOOP                                  1
	00001230: 00000000	MI_NOOP                                  1
	00001234: 00000000	MI_NOOP                                  1
	00001238: 00000000	MI_NOOP                                  1
	0000123c: 00000000	MI_NOOP                                  1
	00001240: 00000000	MI_NOOP                                  1
	00001244: 00000000	MI_NOOP                                  1
	00001248: 00000000	MI_NOOP                                  1
	0000124c: 00000000	MI_NOOP                                  1
	00001250: 00000000	MI_NOOP                                  1
	00001254: 00000000	MI_NOOP                                  1
	00001258: 00000000	MI_NOOP                                  1
	0000125c: 00000000	MI_NOOP                                  1
	00001260: 00000000	MI_NOOP                                  1
	00001264: 00000000	MI_NOOP                                  1
	00001268: 00000000	MI_NOOP                                  1
	0000126c: 00000000	MI_NOOP                                  1
	00001270: 00000000	MI_NOOP                                  1
	00001274: 00000000	MI_NOOP                                  1
	00001278: 00000000	MI_NOOP                                  1
	0000127c: 00000000	MI_NOOP                                  1
	00001280: 00000000	MI_NOOP                                  1
	00001284: 00000000	MI_NOOP                                  1
	00001288: 00000000	MI_NOOP                                  1
	0000128c: 00000000	MI_NOOP                                  1
	00001290: 00000000	MI_NOOP                                  1
	00001294: 00000000	MI_NOOP                                  1
	00001298: 00000000	MI_NOOP                                  1
	0000129c: 00000000	MI_NOOP                                  1
	000012a0: 00000000	MI_NOOP                                  1
	000012a4: 00000000	MI_NOOP                                  1
	000012a8: 00000000	MI_NOOP                                  1
	000012ac: 00000000	MI_NOOP                                  1
	000012b0: 00000000	MI_NOOP                                  1
	000012b4: 00000000	MI_NOOP                                  1
	000012b8: 00000000	MI_NOOP                                  1
	000012bc: 00000000	MI_NOOP                                  1
	000012c0: 00000000	MI_NOOP                                  1
Ring end
space: 28 wanted 32
(II) intel(0): [drm] removed 1 reserved context for kernel
(II) intel(0): [drm] unmapping 8192 bytes of SAREA 0xf8958000 at 0xb7b33000
(II) intel(0): [drm] Closed DRM master.

Fatal server error:
lockup

(II) AIGLX: Suspending AIGLX clients for VT switch

Backtrace:
0: /usr/bin/X11/X(xf86SigHandler+0x79) [0x80c3069]
1: [0xb80fc400]
2: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7b74b50]
3: /usr/bin/X11/X [0x80d6b0a]
4: /usr/lib/xorg/modules/extensions//libglx.so [0xb7c2ad69]
5: /usr/bin/X11/X(AbortDDX+0x79) [0x80a8b69]
6: /usr/bin/X11/X(AbortServer+0x28) [0x813c308]
7: /usr/bin/X11/X(FatalError+0x63) [0x813c913]
8: /usr/lib/xorg/modules/drivers//intel_drv.so(I830WaitLpRing+0x201) [0xb7b691d1]
9: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb7b91b78]
10: /usr/lib/xorg/modules//libexa.so(exaFillRegionTiled+0x36f) [0xb7a7817f]
11: /usr/lib/xorg/modules//libexa.so [0xb7a786a8]
12: /usr/bin/X11/X [0x8177904]
13: /usr/bin/X11/X(miPaintWindow+0x231) [0x8110801]
14: /usr/bin/X11/X(miWindowExposures+0x142) [0x8110b72]
15: /usr/lib/xorg/modules/extensions//libdri.so(DRIWindowExposures+0x97) [0xb7be1e17]
16: /usr/bin/X11/X [0x80d84ff]
17: /usr/bin/X11/X(MapWindow+0x303) [0x8077573]
18: /usr/bin/X11/X(InitRootWindow+0x100) [0x80777c0]
19: /usr/bin/X11/X(main+0x416) [0x8071d26]
20: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7d01685]
21: /usr/bin/X11/X [0x8071171]
Saw signal 11.  Server aborting.
(II) AIGLX: Suspending AIGLX clients for VT switch
```




Can anyone see my problem(s) in this ?

thanks

---

### Post by pjnsmb on 2008-10-09
Success ! at last Yipeeeeeeeeeeeeeeeeeeeeeeeeeee............

After much experimenting I have got things sorted by :

Amending xorg.conf =

driver to "intel"
DefaultColorDepth to 16



As so }

```
Section "Device"
Identifier  "Card0"

Driver      "intel"

#	Identifier	"Configured Video Device"

EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Screen 0"
	Monitor		"Monitor 0"
	DefaultColorDepth 16
	SubSection "Display"
		Depth	8
	EndSubSection
	SubSection "Display"
		Depth	15
	EndSubSection
	SubSection "Display"
		Depth	16
	EndSubSection
	SubSection "Display"
		Depth	16
	EndSubSection


EndSection

```


It's the only configuration that will work- but great I'm up and running and typing from Kubuntu.............

---

### Post by tarps87 on 2008-10-17
Thank you pjnsmb, I've been trying to fix this for about a week. Trust it to be the one thing I didn't change :)

---

