---
title: "Ubuntu 10.04 to 10.10"
date: 2011-01-24
forum: Installation &amp; Upgrades
---

### Post by PysKo_ on 2011-01-24
Hello i am having a problem with my just recently upgraded ubuntu 10.10 ive search google and forums for well over 4 hours with no luck so im asking here. Now i know nvidia 96 has problems with xorg 1.9 but i installed the updated nvidia 96 driver that supports xorg 1.9 through maverick-proposed and i dont have nvidia control panel under system->preferences and if i types sudo nvidia-settings in terminal i get it says im not running an nvidia driver but the hardware driver reports it as activated but not in use and nvidia settings also tells me to run nvidia-xconfig but it says this when i do sudo: nvidia-xconfig: command not found

Any ideas whats going on ? Any help would be greatly appreciated.

---

### Post by mörgæs on 2011-01-25
Hi, welcome to the fora.

How did the machine work with 10.04?

---

### Post by theozzlives on 2011-01-25
> **PysKo_ said:**
> Hello i am having a problem with my just recently upgraded ubuntu 10.10 ive search google and forums for well over 4 hours with no luck so im asking here. Now i know nvidia 96 has problems with xorg 1.9 but i installed the updated nvidia 96 driver that supports xorg 1.9 through maverick-proposed and i dont have nvidia control panel under system->preferences and if i types sudo nvidia-settings in terminal i get it says im not running an nvidia driver but the hardware driver reports it as activated but not in use and nvidia settings also tells me to run nvidia-xconfig but it says this when i do sudo: nvidia-xconfig: command not found

Any ideas whats going on ? Any help would be greatly appreciated.

You didn't type ```
sudo: nvidia-xconfig:
``` did you? If you did, try it without the colons.

---

### Post by PysKo_ on 2011-01-25
Ok somebody on another forum told me to try this > Try to become root: sudo su
Next you have to run /usr/lib/nvidia-96/bin/nvidia-xconfig not just nvidia-xconfig.
Try to edit /etc/X11/xorg.conf file. Modify driver from nvidia to nv
Next reboot machine.
 
And yes 10.04 worked fine before
 
And then this happened after i tried what he told me to do
I rebooted and I got booted to the console i ran startx and got a bunch of text ( id post logs but im not quite sure where to find them when your running from a live cd. anyway I then booted the ubuntu 10.10 live cd and went back to xorg.conf and changed it from nv to nvidia and it wont get past the boot screen now [IMG]http://www.linuxforums.org/forum/images/smilies/icon_sad.gif[/IMG]
If someone could tell me where the logs are stored id be glad to post them.

---

### Post by PysKo_ on 2011-01-26
ok ive found that the logs are stored in /var/logs so can anyone tell which ones i should post ? I really like maverick and i dont wanna have to revert to lucid unless i have to

---

### Post by PysKo_ on 2011-01-27
Ok im going to post the xorg log and see if you guys can make sense of it
> [  1179.874] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[  1179.875] X Protocol Version 11, Revision 0
[  1179.875] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[  1179.875] Current Operating System: [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]Linux[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#") ubuntu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[  1179.875] Kernel command line: file=/cdrom/preseed/ubuntu.seed  boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
[  1179.875] Build Date: 16 September 2010  05:39:22PM
[  1179.875] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [Support | Ubuntu]("http://www.ubuntu.com/support")) 
[  1179.875] Current version of pixman: 0.18.4
[  1179.875] 	Before reporting problems, check [X.Org Wiki - Home]("http://wiki.x.org/")
	to make sure that you have the latest version.
[  1179.875] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1179.875] (==) [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]Log [/FONT][/COLOR][COLOR=blue ! important][FONT=Verdana]file[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxforums.org/forum/#"): "/var/log/Xorg.0.log", Time: Wed Jan 26 10:53:14 2011
[  1179.876] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1179.876] (==) No Layout section.  Using the first Screen section.
[  1179.876] (==) No screen section available. Using defaults.
[  1179.876] (**) |-->Screen "Default Screen Section" (0)
[  1179.876] (**) |   |-->Monitor "<default monitor>"
[  1179.876] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[  1179.876] (==) Automatically adding devices
[  1179.877] (==) Automatically enabling devices
[  1179.877] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1179.877] 	Entry deleted from font path.
[  1179.877] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[  1179.877] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1179.877] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1179.877] (II) Loader magic: 0x81f8e00
[  1179.877] (II) Module ABI versions:
[  1179.877] 	X.Org ANSI C Emulation: 0.4
[  1179.877] 	X.Org Video Driver: 8.0
[  1179.877] 	X.Org XInput driver : 11.0
[  1179.877] 	X.Org Server Extension : 4.0
[  1179.878] (--) PCI:*(0:1:0:0) 10de:0171:0000:0000 rev 163, Mem @  0xfd000000/16777216, 0xe8000000/134217728, 0xf4680000/524288, BIOS @  0x????????/131072
[  1179.879] (II) Open ACPI successful (/var/run/acpid.socket)
[  1179.879] (II) LoadModule: "extmod"
[  1179.880] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1179.881] (II) Module extmod: vendor="X.Org Foundation"
[  1179.881] 	compiled for 1.9.0, module version = 1.0.0
[  1179.881] 	Module class: X.Org Server Extension
[  1179.881] 	ABI class: X.Org Server Extension, version 4.0
[  1179.881] (II) Loading extension MIT-SCREEN-SAVER
[  1179.881] (II) Loading extension XFree86-VidModeExtension
[  1179.881] (II) Loading extension XFree86-DGA
[  1179.881] (II) Loading extension DPMS
[  1179.881] (II) Loading extension XVideo
[  1179.881] (II) Loading extension XVideo-MotionCompensation
[  1179.881] (II) Loading extension X-Resource
[  1179.881] (II) LoadModule: "dbe"
[  1179.882] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1179.882] (II) Module dbe: vendor="X.Org Foundation"
[  1179.882] 	compiled for 1.9.0, module version = 1.0.0
[  1179.882] 	Module class: X.Org Server Extension
[  1179.882] 	ABI class: X.Org Server Extension, version 4.0
[  1179.882] (II) Loading extension DOUBLE-BUFFER
[  1179.882] (II) LoadModule: "glx"
[  1179.883] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1179.883] (II) Module glx: vendor="X.Org Foundation"
[  1179.883] 	compiled for 1.9.0, module version = 1.0.0
[  1179.883] 	ABI class: X.Org Server Extension, version 4.0
[  1179.883] (==) AIGLX enabled
[  1179.883] (II) Loading extension GLX
[  1179.883] (II) LoadModule: "record"
[  1179.884] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1179.884] (II) Module record: vendor="X.Org Foundation"
[  1179.884] 	compiled for 1.9.0, module version = 1.13.0
[  1179.884] 	Module class: X.Org Server Extension
[  1179.884] 	ABI class: X.Org Server Extension, version 4.0
[  1179.884] (II) Loading extension RECORD
[  1179.884] (II) LoadModule: "dri"
[  1179.885] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1179.885] (II) Module dri: vendor="X.Org Foundation"
[  1179.885] 	compiled for 1.9.0, module version = 1.0.0
[  1179.885] 	ABI class: X.Org Server Extension, version 4.0
[  1179.885] (II) Loading extension XFree86-DRI
[  1179.885] (II) LoadModule: "dri2"
[  1179.886] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1179.886] (II) Module dri2: vendor="X.Org Foundation"
[  1179.886] 	compiled for 1.9.0, module version = 1.2.0
[  1179.886] 	ABI class: X.Org Server Extension, version 4.0
[  1179.887] (II) Loading extension DRI2
[  1179.887] (==) Matched nouveau as autoconfigured driver 0
[  1179.887] (==) Matched nv as autoconfigured driver 1
[  1179.887] (==) Matched vesa as autoconfigured driver 2
[  1179.887] (==) Matched fbdev as autoconfigured driver 3
[  1179.887] (==) Assigned the driver to the xf86ConfigLayout
[  1179.887] (II) LoadModule: "nouveau"
[  1179.887] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[  1179.888] (II) Module nouveau: vendor="X.Org Foundation"
[  1179.888] 	compiled for 1.8.99.905, module version = 0.0.16
[  1179.888] 	Module class: X.Org Video Driver
[  1179.888] 	ABI class: X.Org Video Driver, version 8.0
[  1179.888] (II) LoadModule: "nv"
[  1179.888] (II) Loading /usr/lib/xorg/modules/drivers/nv_drv.so
[  1179.888] (II) Module nv: vendor="X.Org Foundation"
[  1179.888] 	compiled for 1.8.99.905, module version = 2.1.17
[  1179.889] 	Module class: X.Org Video Driver
[  1179.889] 	ABI class: X.Org Video Driver, version 8.0
[  1179.889] (II) LoadModule: "vesa"
[  1179.889] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1179.889] (II) Module vesa: vendor="X.Org Foundation"
[  1179.889] 	compiled for 1.8.99.905, module version = 2.3.0
[  1179.889] 	Module class: X.Org Video Driver
[  1179.889] 	ABI class: X.Org Video Driver, version 8.0
[  1179.889] (II) LoadModule: "fbdev"
[  1179.890] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1179.890] (II) Module fbdev: vendor="X.Org Foundation"
[  1179.890] 	compiled for 1.8.99.905, module version = 0.4.2
[  1179.890] 	ABI class: X.Org Video Driver, version 8.0
[  1179.890] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[  1179.890] (II) NOUVEAU driver for NVIDIA chipset families :
[  1179.890] 	RIVA TNT    (NV04)
[  1179.890] 	RIVA TNT2   (NV05)
[  1179.890] 	GeForce 256 (NV10)
[  1179.890] 	GeForce 2   (NV11, NV15)
[  1179.890] 	GeForce 4MX (NV17, NV1[IMG]http://www.linuxforums.org/forum/images/smilies/icon_cool.gif[/IMG]
[  1179.890] 	GeForce 3   (NV20)
[  1179.890] 	GeForce 4Ti (NV25, NV2[IMG]http://www.linuxforums.org/forum/images/smilies/icon_cool.gif[/IMG]
[  1179.890] 	GeForce FX  (NV3x)
[  1179.890] 	GeForce 6   (NV4x)
[  1179.890] 	GeForce 7   (G7x)
[  1179.891] 	GeForce 8   (G8x)
[  1179.891] (II) NOUVEAU driver Date:   Thu Aug 5 00:40:40 2010 +0200
[  1179.891] (II) NOUVEAU driver for NVIDIA chipset families :
[  1179.891] 	RIVA TNT    (NV04)
[  1179.891] 	RIVA TNT2   (NV05)
[  1179.891] 	GeForce 256 (NV10)
[  1179.891] 	GeForce 2   (NV11, NV15)
[  1179.891] 	GeForce 4MX (NV17, NV1[IMG]http://www.linuxforums.org/forum/images/smilies/icon_cool.gif[/IMG]
[  1179.891] 	GeForce 3   (NV20)
[  1179.891] 	GeForce 4Ti (NV25, NV2[IMG]http://www.linuxforums.org/forum/images/smilies/icon_cool.gif[/IMG]
[  1179.891] 	GeForce FX  (NV3x)
[  1179.891] 	GeForce 6   (NV4x)
[  1179.891] 	GeForce 7   (G7x)
[  1179.891] 	GeForce 8   (G8x)
[  1179.891] (II) VESA: driver for VESA chipsets: vesa
[  1179.891] (II) FBDEV: driver for framebuffer: fbdev
[  1179.891] (++) using VT number 7
 
[  1179.891] drmOpenDevice: node name is /dev/dri/card0
[  1179.891] drmOpenDevice: open result is 8, (OK)
[  1179.892] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[  1179.892] drmOpenDevice: node name is /dev/dri/card0
[  1179.892] drmOpenDevice: open result is 8, (OK)
[  1179.892] drmOpenByBusid: drmOpenMinor returns 8
[  1179.892] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[  1179.892] (II) [drm] nouveau interface version: 0.0.16
[  1179.892] (WW) Falling back to old probe method for vesa
[  1179.892] (WW) Falling back to old probe method for fbdev
[  1179.892] (II) Loading sub module "fbdevhw"
[  1179.892] (II) LoadModule: "fbdevhw"
[  1179.893] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1179.893] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1179.893] 	compiled for 1.9.0, module version = 0.0.2
[  1179.893] 	ABI class: X.Org Video Driver, version 8.0
[  1179.893] (II) Loading sub module "dri"
[  1179.893] (II) LoadModule: "dri"
[  1179.894] (II) Reloading /usr/lib/xorg/modules/extensions/libdri.so
[  1179.894] (II) NOUVEAU(0): Loaded DRI module
[  1179.894] drmOpenDevice: node name is /dev/dri/card0
[  1179.894] drmOpenDevice: open result is 9, (OK)
[  1179.894] drmOpenDevice: node name is /dev/dri/card0
[  1179.894] drmOpenDevice: open result is 9, (OK)
[  1179.894] drmOpenByBusid: Searching for BusID pci:0000:01:00.0
[  1179.894] drmOpenDevice: node name is /dev/dri/card0
[  1179.894] drmOpenDevice: open result is 9, (OK)
[  1179.894] drmOpenByBusid: drmOpenMinor returns 9
[  1179.894] drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[  1179.894] (II) [drm] DRM interface version 1.3
[  1179.894] (II) [drm] DRM open master succeeded.
[  1179.895] (--) NOUVEAU(0): Chipset: "NVIDIA NV17"
[  1179.895] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[  1179.895] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[  1179.895] (==) NOUVEAU(0): RGB weight 888
[  1179.895] (==) NOUVEAU(0): Default visual is TrueColor
[  1179.895] (==) NOUVEAU(0): Using HW cursor
[  1180.001] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[  1180.056] (II) NOUVEAU(0): Output TV-1 has no monitor section
[  1180.340] (II) NOUVEAU(0): Output DVI-I-2 has no monitor section
[  1180.445] (II) NOUVEAU(0): EDID for output DVI-I-1
[  1180.445] (II) NOUVEAU(0): Manufacturer: EMA  Model: 309  Serial#: 16568
[  1180.445] (II) NOUVEAU(0): Year: 2004  Week: 2
[  1180.445] (II) NOUVEAU(0): EDID Version: 1.3
[  1180.445] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[  1180.445] (II) NOUVEAU(0): Sync:  Separate
[  1180.445] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 32  vert.: 24
[  1180.445] (II) NOUVEAU(0): Gamma: 2.98
[  1180.445] (II) NOUVEAU(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[  1180.445] (II) NOUVEAU(0): First detailed timing is preferred mode
[  1180.446] (II) NOUVEAU(0): redX: 0.618 redY: 0.349   greenX: 0.280 greenY: 0.605
[  1180.446] (II) NOUVEAU(0): blueX: 0.152 blueY: 0.063   whiteX: 0.281 whiteY: 0.310
[  1180.446] (II) NOUVEAU(0): Supported established timings:
[  1180.446] (II) NOUVEAU(0): 720x400@70Hz
[  1180.446] (II) NOUVEAU(0): 640x480@60Hz
[  1180.446] (II) NOUVEAU(0): 800x600@60Hz
[  1180.446] (II) NOUVEAU(0): 800x600@75Hz
[  1180.446] (II) NOUVEAU(0): 1024x768@60Hz
[  1180.446] (II) NOUVEAU(0): 1024x768@75Hz
[  1180.446] (II) NOUVEAU(0): Manufacturer's mask: 0
[  1180.446] (II) NOUVEAU(0): Supported standard timings:
[  1180.446] (II) NOUVEAU(0): #0: hsize: 640  vsize 480  refresh: 85  vid: 22833
[  1180.446] (II) NOUVEAU(0): #1: hsize: 800  vsize 600  refresh: 85  vid: 22853
[  1180.446] (II) NOUVEAU(0): #2: hsize: 800  vsize 600  refresh: 100  vid: 26693
[  1180.446] (II) NOUVEAU(0): #3: hsize: 1024  vsize 768  refresh: 85  vid: 22881
[  1180.446] (II) NOUVEAU(0): #4: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  1180.446] (II) NOUVEAU(0): Supported detailed timing:
[  1180.446] (II) NOUVEAU(0): clock: 94.5 MHz   Image Size:  320 x 240 mm
[  1180.446] (II) NOUVEAU(0): h_active: 1024  h_sync: 1072  h_sync_end 1168 h_blank_end 1376 h_border: 0
[  1180.446] (II) NOUVEAU(0): v_active: 768  v_sync: 769  v_sync_end 772 v_blanking: 808 v_border: 0
[  1180.446] (II) NOUVEAU(0): Monitor name: eView 17f2
[  1180.446] (II) NOUVEAU(0): Ranges: V min: 50 V max: 160 Hz, H min: 30 H max: 70 kHz, PixClock max 115 MHz
[  1180.446] (II) NOUVEAU(0): Serial No: MPF4150016568
[  1180.446] (II) NOUVEAU(0): EDID (in hex):
[  1180.446] (II) NOUVEAU(0): 	00ffffffffffff0015a10903b8400000
[  1180.446] (II) NOUVEAU(0): 	020e0103082018c6ea5c119e59479b27
[  1180.446] (II) NOUVEAU(0): 	10484fa14a0031594559456861598180
[  1180.446] (II) NOUVEAU(0): 	010101010101ea240060410028303060
[  1180.446] (II) NOUVEAU(0): 	130040f01000001e000000fc00655669
[  1180.446] (II) NOUVEAU(0): 	657720313766320a2020000000fd0032
[  1180.446] (II) NOUVEAU(0): 	a01e460b000a202020202020000000ff
[  1180.446] (II) NOUVEAU(0): 	004d5046343135303031363536380057
[  1180.446] (II) NOUVEAU(0): EDID vendor "EMA", prod id 777
[  1180.446] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[  1180.446] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[  1180.446] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1180.446] (II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  1180.446] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1180.446] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1180.446] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1180.446] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "800x600"x100.0   68.18  800 848 936 1072  600 601 604 636 -hsync +vsync (63.6 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280  1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1180.447] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[  1180.447] (II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280  1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 -hsync +vsync (63.6 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1180.447] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1180.500] (II) NOUVEAU(0): EDID for output TV-1
[  1180.796] (II) NOUVEAU(0): EDID for output DVI-I-2
[  1180.796] (II) NOUVEAU(0): Output DVI-I-1 connected
[  1180.796] (II) NOUVEAU(0): Output TV-1 disconnected
[  1180.796] (II) NOUVEAU(0): Output DVI-I-2 disconnected
[  1180.796] (II) NOUVEAU(0): Using exact sizes for initial modes
[  1180.796] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1024x768
[  1180.796] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  1180.796] (--) NOUVEAU(0): Virtual size is 1024x768 (pitch 1024)
[  1180.796] (**) NOUVEAU(0):  Driver mode "1024x768": 94.5 MHz (scaled from 0.0 MHz), 68.7 kHz, 85.0 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "1024x768"x85.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  1180.796] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280  1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1180.796] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[  1180.796] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1180.796] (**) NOUVEAU(0):  Mode "800x600": 68.2 MHz (scaled from 0.0 MHz), 63.6 kHz, 100.0 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "800x600"x100.0   68.17  800 848 936 1072  600 601 604 636 -hsync +vsync (63.6 kHz)
[  1180.796] (**) NOUVEAU(0):  Driver mode "800x600": 56.2 MHz (scaled from 0.0 MHz), 53.7 kHz, 85.1 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "800x600"x85.1   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  1180.796] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1180.796] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1180.796] (**) NOUVEAU(0):  Driver mode "640x480": 36.0 MHz (scaled from 0.0 MHz), 43.3 kHz, 85.0 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "640x480"x85.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  1180.796] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1180.796] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[  1180.796] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1180.796] (**) NOUVEAU(0): Display dimensions: (320, 240) mm
[  1180.796] (**) NOUVEAU(0): DPI set to (81, 81)
[  1180.796] (II) Loading sub module "fb"
[  1180.796] (II) LoadModule: "fb"
[  1180.797] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1180.798] (II) Module fb: vendor="X.Org Foundation"
[  1180.798] 	compiled for 1.9.0, module version = 1.0.0
[  1180.798] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1180.798] (II) Loading sub module "exa"
[  1180.798] (II) LoadModule: "exa"
[  1180.799] (II) Loading /usr/lib/xorg/modules/libexa.so
[  1180.799] (II) Module exa: vendor="X.Org Foundation"
[  1180.799] 	compiled for 1.9.0, module version = 2.5.0
[  1180.799] 	ABI class: X.Org Video Driver, version 8.0
[  1180.799] (II) Loading sub module "shadowfb"
[  1180.799] (II) LoadModule: "shadowfb"
[  1180.800] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[  1180.800] (II) Module shadowfb: vendor="X.Org Foundation"
[  1180.800] 	compiled for 1.9.0, module version = 1.0.0
[  1180.800] 	ABI class: X.Org ANSI C Emulation, version 0.4
[  1180.800] (II) UnloadModule: "nv"
[  1180.800] (II) Unloading /usr/lib/xorg/modules/drivers/nv_drv.so
[  1180.800] (II) UnloadModule: "vesa"
[  1180.800] (II) Unloading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1180.800] (II) UnloadModule: "fbdev"
[  1180.800] (II) Unloading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1180.800] (II) UnloadModule: "fbdevhw"
[  1180.800] (II) Unloading /usr/lib/xorg/modules/libfbdevhw.so
[  1180.800] (--) Depth 24 pixmap format is 32 bpp
[  1180.802] (II) NOUVEAU(0): Opened GPU channel 1
[  1180.802] (II) NOUVEAU(0): [DRI2] Setup complete
[  1180.802] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau_vieux
[  1180.802] (II) NOUVEAU(0): GART: 64MiB available
[  1180.805] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[  1180.806] (II) EXA(0): Driver allocated offscreen pixmaps
[  1180.806] (II) EXA(0): Driver registered support for the following operations:
[  1180.806] (II)         Solid
[  1180.806] (II)         Copy
[  1180.806] (II)         Composite (RENDER acceleration)
[  1180.806] (II)         UploadToScreen
[  1180.806] (II)         DownloadFromScreen
[  1180.806] (==) NOUVEAU(0): Backing store disabled
[  1180.806] (==) NOUVEAU(0): Silken mouse enabled
[  1180.806] (==) NOUVEAU(0): DPMS enabled
[  1180.806] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1180.806] (--) RandR disabled
[  1180.807] (II) Initializing built-in extension Generic Event Extension
[  1180.807] (II) Initializing built-in extension SHAPE
[  1180.807] (II) Initializing built-in extension MIT-SHM
[  1180.807] (II) Initializing built-in extension XInputExtension
[  1180.807] (II) Initializing built-in extension XTEST
[  1180.807] (II) Initializing built-in extension BIG-REQUESTS
[  1180.807] (II) Initializing built-in extension SYNC
[  1180.807] (II) Initializing built-in extension XKEYBOARD
[  1180.807] (II) Initializing built-in extension XC-MISC
[  1180.807] (II) Initializing built-in extension SECURITY
[  1180.807] (II) Initializing built-in extension XINERAMA
[  1180.807] (II) Initializing built-in extension XFIXES
[  1180.807] (II) Initializing built-in extension RENDER
[  1180.807] (II) Initializing built-in extension RANDR
[  1180.807] (II) Initializing built-in extension COMPOSITE
[  1180.807] (II) Initializing built-in extension DAMAGE
[  1180.807] (II) Initializing built-in extension GESTURE
[  1180.825] (EE) AIGLX error: dlopen of  /usr/lib/dri/nouveau_vieux_dri.so failed  (/usr/lib/dri/nouveau_vieux_dri.so: cannot open shared object file: No  such file or directory)
[  1180.825] (EE) AIGLX: reverting to software rendering
[  1180.825] (II) AIGLX: Screen 0 is not DRI capable
[  1180.831] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[  1180.831] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[  1180.838] (II) NOUVEAU(0): NVEnterVT is called.
[  1180.838] (II) NOUVEAU(0): Setting screen physical size to 270 x 203
[  1180.838] resize called 1024 768
[  1180.868] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1180.883] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  1180.883] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1180.884] (II) LoadModule: "evdev"
[  1180.884] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1180.885] (II) Module evdev: vendor="X.Org Foundation"
[  1180.885] 	compiled for 1.9.0, module version = 2.3.2
[  1180.885] 	Module class: X.Org XInput Driver
[  1180.885] 	ABI class: X.Org XInput driver, version 11.0
[  1180.885] (**) Power Button: always reports core events
[  1180.885] (**) Power Button: Device: "/dev/input/event1"
[  1180.885] (II) Power Button: Found keys
[  1180.885] (II) Power Button: Configuring as keyboard
[  1180.885] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1180.885] (**) Option "xkb_rules" "evdev"
[  1180.885] (**) Option "xkb_model" "pc105"
[  1180.885] (**) Option "xkb_layout" "us"
[  1180.888] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[  1180.888] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  1180.888] (**) Sleep Button: always reports core events
[  1180.888] (**) Sleep Button: Device: "/dev/input/event0"
[  1180.888] (II) Sleep Button: Found keys
[  1180.888] (II) Sleep Button: Configuring as keyboard
[  1180.888] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  1180.888] (**) Option "xkb_rules" "evdev"
[  1180.888] (**) Option "xkb_model" "pc105"
[  1180.888] (**) Option "xkb_layout" "us"
[  1180.891] (II) config/udev: Adding input device Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse (/dev/input/event3)
[  1180.891] (**) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Applying InputClass "evdev pointer catchall"
[  1180.891] (**) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Applying InputClass "evdev keyboard catchall"
[  1180.891] (**) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: always reports core events
[  1180.891] (**) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Device: "/dev/input/event3"
[  1180.891] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Found 9 mouse buttons
[  1180.891] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Found scroll wheel(s)
[  1180.891] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Found relative axes
[  1180.891] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Found x and y relative axes
[  1180.891] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Found absolute axes
[  1180.891] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Found x and y absolute axes
[  1180.891] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Found keys
[  1180.892] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Configuring as mouse
[  1180.892] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: Configuring as keyboard
[  1180.892] (**) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: YAxisMapping: buttons 4 and 5
[  1180.892] (**) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse:  EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1180.892] (II) XINPUT: Adding extended input device "Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse" (type: KEYBOARD)
[  1180.892] (**) Option "xkb_rules" "evdev"
[  1180.892] (**) Option "xkb_model" "pc105"
[  1180.892] (**) Option "xkb_layout" "us"
[  1180.892] (II) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: initialized for relative axes.
[  1180.892] (WW) Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse: ignoring absolute axes.
[  1180.893] (II) config/udev: Adding input device Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse (/dev/input/js0)
[  1180.893] (II) No input driver/identifier specified (ignoring)
[  1180.893] (II) config/udev: Adding input device Microsoft MicrosoftÂ® SideWinderâ„¢ X3 Mouse (/dev/input/mouse0)
[  1180.893] (II) No input driver/identifier specified (ignoring)
[  1180.900] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[  1180.901] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1180.901] (**) AT Translated Set 2 keyboard: always reports core events
[  1180.901] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[  1180.901] (II) AT Translated Set 2 keyboard: Found keys
[  1180.901] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  1180.901] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  1180.901] (**) Option "xkb_rules" "evdev"
[  1180.901] (**) Option "xkb_model" "pc105"
[  1180.901] (**) Option "xkb_layout" "us"
[  1183.121] (II) NOUVEAU(0): EDID vendor "EMA", prod id 777
[  1183.121] (II) NOUVEAU(0): Using hsync ranges from config file
[  1183.121] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  1183.121] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1183.121] (II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "800x600"x100.0   68.18  800 848 936 1072  600 601 604 636 -hsync +vsync (63.6 kHz)
[  1183.121] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280  1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1183.697] (II) NOUVEAU(0): EDID vendor "EMA", prod id 777
[  1183.697] (II) NOUVEAU(0): Using hsync ranges from config file
[  1183.697] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  1183.697] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1183.697] (II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  1183.697] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1183.697] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1183.697] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1183.697] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1183.697] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1183.697] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1183.697] (II) NOUVEAU(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  1183.697] (II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  1183.697] (II) NOUVEAU(0): Modeline "800x600"x100.0   68.18  800 848 936 1072  600 601 604 636 -hsync +vsync (63.6 kHz)
[  1183.698] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280  1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1184.247] (II) NOUVEAU(0): EDID vendor "EMA", prod id 777
[  1184.247] (II) NOUVEAU(0): Using hsync ranges from config file
[  1184.247] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  1184.247] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1184.247] (II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "800x600"x100.0   68.18  800 848 936 1072  600 601 604 636 -hsync +vsync (63.6 kHz)
[  1184.247] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280  1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1184.804] (II) NOUVEAU(0): EDID vendor "EMA", prod id 777
[  1184.805] (II) NOUVEAU(0): Using hsync ranges from config file
[  1184.805] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  1184.805] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1184.805] (II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "800x600"x100.0   68.18  800 848 936 1072  600 601 604 636 -hsync +vsync (63.6 kHz)
[  1184.805] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280  1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1191.828] (II) NOUVEAU(0): EDID vendor "EMA", prod id 777
[  1191.828] (II) NOUVEAU(0): Using hsync ranges from config file
[  1191.828] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  1191.828] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1191.828] (II) NOUVEAU(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "800x600"x100.0   68.18  800 848 936 1072  600 601 604 636 -hsync +vsync (63.6 kHz)
[  1191.828] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280  1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz) 			 		

---

### Post by PysKo_ on 2011-01-29
Ok i got everything figured out and working as it should, but visual effects do not work any idea on how i could enable these ? cause when i do it says visual effects could not be enabled.

---

