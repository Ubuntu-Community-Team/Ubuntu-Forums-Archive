---
title: "NVIDIA xserver problems loss of dual monitors Ubuntu 11.10"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by David Crockett on 2011-10-19
Hi all,

I have updated to Ubuntu 11.10 and dual monitor system now does not work. Everything work just fine in 11.04.  I have the following NVida card (it is a bit old) as reported by lspci

01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro NVS 280 SD] (rev a2)

I downloaded and installed the recommended 3rd party driver as recommended by the Additional Drivers installer.    

The main monitor works Ok, however when you go to Displays in the Systems settings, it tells you that the monitor is unknown and it does not seem to see the second monitor.   However at start up and shut down, the ubuntu logo will show up on the second monitor.   

From the software center I downloaded the Nividia X server settings program
It seems to know that there are two monitors and can identify them.   However, When i go to the X server display configuration option, I get the following report:

[B]Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.[/B]

It recognizes what Nvidia card but gives me the following report:

Please  see the attached screen shot.

It does not seem to know the busId.   

I am at a loss as to what to do.

Please help.

Regards,
DC

---

### Post by Nogothrim on 2011-10-20
I'm having the same problem with a NVIDIA Geforce 7300 GO (laptop) with 173 and 96 drivers. With nvidia-current gnome-shell does not repaint at all and unity2d has horrible video tearing.

---

### Post by David Crockett on 2011-10-20
The main monitor appears to be working pretty well.   However, as you drag the windows about they tend to lag behind a bit.    

Cheers,
DC

---

### Post by gator_2011 on 2011-10-21
Alternate solution: Ok so Ubuntu 11.10 desktop has issues with NVIDIA video cards, even when you get them working you get errors on boot up and you cant adjust your display settings from the display because your monitor shows up as a single monitor. I found that if I install Ubuntu Server 11.04 and then apt-get update/upgrade and apt-get install ubuntu-desktop and up date the gui the default video card driver allows for dual screens and doesn't error at all, it also gives you the ability to change your settings for display in the normal display settings of the OS.

---

### Post by MAFoElffen on 2011-10-21
> **gator_2011 said:**
> Alternate solution: Ok so Ubuntu 11.10 desktop has issues with NVIDIA video cards, even when you get them working you get errors on boot up and you cant adjust your display settings from the display because your monitor shows up as a single monitor. I found that if I install Ubuntu Server 11.04 and then apt-get update/upgrade and apt-get install ubuntu-desktop and up date the gui the default video card driver allows for dual screens and doesn't error at all, it also gives you the ability to change your settings for display in the normal display settings of the OS.
I do that in testing just for giggles... BUT then process scheduling on the Server Edition is for server/background processes and secondary on Desktop/foreground processes.  It works, but not as well as running a desktop on a Desktop Edition.  Been testing Oneiric since last June with 5 boxes running nVidia, 1 ATI, 1 Intel GPUs.

@David Crockett
Please post your /etc/X11/xorg.conf and /var/log/xorg.0.log. Be sure you post them within CODE tags...  The xorg.conf should show us how your card is configured and if there is anything odd about your "dual monitor" setup.  The Xorg log should show both your monitors connected and what kind of data it's passing back.

Trust the nvidia-settings applet over the default Monitors applet.  The later has some bugs on reading multiple monitors at the moment.

---

### Post by gator_2011 on 2011-10-22
> **MAFoElffen said:**
> I do that in testing just for giggles... BUT then process scheduling on the Server Edition is for server/background processes and secondary on Desktop/foreground processes.  It works, but not as well as running a desktop on a Desktop Edition.  Been testing Oneiric since last June with 5 boxes running nVidia, 1 ATI, 1 Intel GPUs.

@David Crockett
Please post your /etc/X11/xorg.conf and /var/log/xorg.0.log. Be sure you post them within CODE tags...  The xorg.conf should show us how your card is configured and if there is anything odd about your "dual monitor" setup.  The Xorg log should show both your monitors connected and what kind of data it's passing back.

Trust the nvidia-settings applet over the default Monitors applet.  The later has some bugs on reading multiple monitors at the moment.


I do not have an Xorg.conf file at all... I did a locate to make sure. This is what I have in the /etc/X11 directory:

:/etc/X11$ ls
app-defaults  default-display-manager           fonts    X      xkb     Xreset.d    Xsession    Xsession.options
cursors       default-display-manager.dpkg-tmp  rgb.txt  xinit  Xreset  Xresources  Xsession.d  Xwrapper.config


LOG FILE::


[    22.351] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    22.351] X Protocol Version 11, Revision 0
[    22.351] Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
[    22.351] Current Operating System: Linux NASA-MAINFRAME 3.0.0-12-server #20-Ubuntu SMP Fri Oct 7 16:36:30 UTC 2011 x86_64
[    22.351] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-server root=UUID=6edae002-5b7c-480d-acb2-525448184912 ro quiet
[    22.351] Build Date: 13 October 2011  05:44:30PM
[    22.351] xorg-server 2:1.10.4-1ubuntu4.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    22.351] Current version of pixman: 0.22.2
[    22.351] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    22.351] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.351] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 22 11:43:30 2011
[    22.394] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.394] (==) No Layout section.  Using the first Screen section.
[    22.394] (==) No screen section available. Using defaults.
[    22.394] (**) |-->Screen "Default Screen Section" (0)
[    22.394] (**) |   |-->Monitor "<default monitor>"
[    22.395] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.395] (==) Automatically adding devices
[    22.395] (==) Automatically enabling devices
[    22.395] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.395] 	Entry deleted from font path.
[    22.395] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.395] 	Entry deleted from font path.
[    22.395] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.395] 	Entry deleted from font path.
[    22.395] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.395] 	Entry deleted from font path.
[    22.395] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.395] 	Entry deleted from font path.
[    22.395] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.395] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.395] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.395] (II) Loader magic: 0x7e0220
[    22.395] (II) Module ABI versions:
[    22.395] 	X.Org ANSI C Emulation: 0.4
[    22.395] 	X.Org Video Driver: 10.0
[    22.395] 	X.Org XInput driver : 12.3
[    22.395] 	X.Org Server Extension : 5.0
[    22.396] (--) PCI:*(0:2:0:0) 10de:0140:1682:2118 rev 162, Mem @ 0xf4000000/67108864, 0xd8000000/134217728, 0xfa000000/16777216, BIOS @ 0x????????/131072
[    22.396] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.396] (II) LoadModule: "extmod"
[    22.481] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.481] (II) Module extmod: vendor="X.Org Foundation"
[    22.481] 	compiled for 1.10.4, module version = 1.0.0
[    22.481] 	Module class: X.Org Server Extension
[    22.481] 	ABI class: X.Org Server Extension, version 5.0
[    22.481] (II) Loading extension MIT-SCREEN-SAVER
[    22.481] (II) Loading extension XFree86-VidModeExtension
[    22.481] (II) Loading extension XFree86-DGA
[    22.481] (II) Loading extension DPMS
[    22.481] (II) Loading extension XVideo
[    22.481] (II) Loading extension XVideo-MotionCompensation
[    22.481] (II) Loading extension X-Resource
[    22.481] (II) LoadModule: "dbe"
[    22.481] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.481] (II) Module dbe: vendor="X.Org Foundation"
[    22.481] 	compiled for 1.10.4, module version = 1.0.0
[    22.481] 	Module class: X.Org Server Extension
[    22.481] 	ABI class: X.Org Server Extension, version 5.0
[    22.481] (II) Loading extension DOUBLE-BUFFER
[    22.481] (II) LoadModule: "glx"
[    22.482] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    22.482] (II) Module glx: vendor="X.Org Foundation"
[    22.482] 	compiled for 1.10.4, module version = 1.0.0
[    22.482] 	ABI class: X.Org Server Extension, version 5.0
[    22.482] (==) AIGLX enabled
[    22.482] (II) Loading extension GLX
[    22.482] (II) LoadModule: "record"
[    22.482] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.482] (II) Module record: vendor="X.Org Foundation"
[    22.482] 	compiled for 1.10.4, module version = 1.13.0
[    22.482] 	Module class: X.Org Server Extension
[    22.482] 	ABI class: X.Org Server Extension, version 5.0
[    22.482] (II) Loading extension RECORD
[    22.482] (II) LoadModule: "dri"
[    22.483] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.483] (II) Module dri: vendor="X.Org Foundation"
[    22.483] 	compiled for 1.10.4, module version = 1.0.0
[    22.483] 	ABI class: X.Org Server Extension, version 5.0
[    22.483] (II) Loading extension XFree86-DRI
[    22.483] (II) LoadModule: "dri2"
[    22.483] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.483] (II) Module dri2: vendor="X.Org Foundation"
[    22.483] 	compiled for 1.10.4, module version = 1.2.0
[    22.483] 	ABI class: X.Org Server Extension, version 5.0
[    22.483] (II) Loading extension DRI2
[    22.483] (==) Matched nvidia as autoconfigured driver 0
[    22.483] (==) Matched nouveau as autoconfigured driver 1
[    22.483] (==) Matched nv as autoconfigured driver 2
[    22.483] (==) Matched vesa as autoconfigured driver 3
[    22.483] (==) Matched fbdev as autoconfigured driver 4
[    22.483] (==) Assigned the driver to the xf86ConfigLayout
[    22.483] (II) LoadModule: "nvidia"
[    22.484] (WW) Warning, couldn't open module nvidia
[    22.484] (II) UnloadModule: "nvidia"
[    22.484] (II) Unloading nvidia
[    22.484] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    22.484] (II) LoadModule: "nouveau"
[    22.485] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.485] (II) Module nouveau: vendor="X.Org Foundation"
[    22.485] 	compiled for 1.10.1, module version = 0.0.16
[    22.485] 	Module class: X.Org Video Driver
[    22.485] 	ABI class: X.Org Video Driver, version 10.0
[    22.485] (II) LoadModule: "nv"
[    22.486] (WW) Warning, couldn't open module nv
[    22.486] (II) UnloadModule: "nv"
[    22.486] (II) Unloading nv
[    22.486] (EE) Failed to load module "nv" (module does not exist, 0)
[    22.486] (II) LoadModule: "vesa"
[    22.486] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.486] (II) Module vesa: vendor="X.Org Foundation"
[    22.486] 	compiled for 1.10.2, module version = 2.3.0
[    22.486] 	Module class: X.Org Video Driver
[    22.486] 	ABI class: X.Org Video Driver, version 10.0
[    22.486] (II) LoadModule: "fbdev"
[    22.486] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.487] (II) Module fbdev: vendor="X.Org Foundation"
[    22.487] 	compiled for 1.10.0, module version = 0.4.2
[    22.487] 	ABI class: X.Org Video Driver, version 10.0
[    22.487] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    22.487] (II) NOUVEAU driver for NVIDIA chipset families :
[    22.487] 	RIVA TNT        (NV04)
[    22.487] 	RIVA TNT2       (NV05)
[    22.487] 	GeForce 256     (NV10)
[    22.487] 	GeForce 2       (NV11, NV15)
[    22.487] 	GeForce 4MX     (NV17, NV18)
[    22.487] 	GeForce 3       (NV20)
[    22.487] 	GeForce 4Ti     (NV25, NV28)
[    22.487] 	GeForce FX      (NV3x)
[    22.487] 	GeForce 6       (NV4x)
[    22.487] 	GeForce 7       (G7x)
[    22.487] 	GeForce 8       (G8x)
[    22.487] 	GeForce GTX 200 (NVA0)
[    22.487] 	GeForce GTX 400 (NVC0)
[    22.487] (II) VESA: driver for VESA chipsets: vesa
[    22.487] (II) FBDEV: driver for framebuffer: fbdev
[    22.487] (++) using VT number 7

[    22.487] drmOpenDevice: node name is /dev/dri/card0
[    22.487] drmOpenDevice: open result is 11, (OK)
[    22.487] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    22.487] drmOpenDevice: node name is /dev/dri/card0
[    22.487] drmOpenDevice: open result is 11, (OK)
[    22.487] drmOpenByBusid: drmOpenMinor returns 11
[    22.487] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    22.487] (II) [drm] nouveau interface version: 0.0.16
[    22.488] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.488] (WW) Falling back to old probe method for vesa
[    22.488] (WW) Falling back to old probe method for fbdev
[    22.488] (II) Loading sub module "fbdevhw"
[    22.488] (II) LoadModule: "fbdevhw"
[    22.488] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.488] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.488] 	compiled for 1.10.4, module version = 0.0.2
[    22.488] 	ABI class: X.Org Video Driver, version 10.0
[    22.488] (II) Loading sub module "dri"
[    22.488] (II) LoadModule: "dri"
[    22.489] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.489] (II) Module dri: vendor="X.Org Foundation"
[    22.489] 	compiled for 1.10.4, module version = 1.0.0
[    22.489] 	ABI class: X.Org Server Extension, version 5.0
[    22.489] (II) NOUVEAU(0): Loaded DRI module
[    22.489] drmOpenDevice: node name is /dev/dri/card0
[    22.489] drmOpenDevice: open result is 12, (OK)
[    22.489] drmOpenDevice: node name is /dev/dri/card0
[    22.489] drmOpenDevice: open result is 12, (OK)
[    22.489] drmOpenByBusid: Searching for BusID pci:0000:02:00.0
[    22.489] drmOpenDevice: node name is /dev/dri/card0
[    22.489] drmOpenDevice: open result is 12, (OK)
[    22.489] drmOpenByBusid: drmOpenMinor returns 12
[    22.489] drmOpenByBusid: drmGetBusid reports pci:0000:02:00.0
[    22.489] (II) [drm] DRM interface version 1.4
[    22.489] (II) [drm] DRM open master succeeded.
[    22.489] (--) NOUVEAU(0): Chipset: "NVIDIA NV43"
[    22.489] (II) NOUVEAU(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.489] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    22.489] (==) NOUVEAU(0): RGB weight 888
[    22.489] (==) NOUVEAU(0): Default visual is TrueColor
[    22.489] (==) NOUVEAU(0): Using HW cursor
[    22.489] (==) NOUVEAU(0): GLX sync to VBlank disabled.
[    22.489] (==) NOUVEAU(0): Page flipping enabled
[    22.597] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[    22.632] (II) NOUVEAU(0): Output DVI-I-2 has no monitor section
[    22.744] (II) NOUVEAU(0): Output TV-1 has no monitor section
[    23.409] (II) NOUVEAU(0): EDID for output DVI-I-1
[    23.410] (II) NOUVEAU(0): Manufacturer: SAM  Model: 372  Serial#: 1297691186
[    23.410] (II) NOUVEAU(0): Year: 2008  Week: 48
[    23.410] (II) NOUVEAU(0): EDID Version: 1.3
[    23.410] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    23.410] (II) NOUVEAU(0): Sync:  Separate  Composite  SyncOnGreen
[    23.410] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 44  vert.: 30
[    23.410] (II) NOUVEAU(0): Gamma: 2.20
[    23.410] (II) NOUVEAU(0): DPMS capabilities: Off; RGB/Color Display
[    23.410] (II) NOUVEAU(0): First detailed timing is preferred mode
[    23.410] (II) NOUVEAU(0): redX: 0.649 redY: 0.335   greenX: 0.283 greenY: 0.605
[    23.410] (II) NOUVEAU(0): blueX: 0.151 blueY: 0.073   whiteX: 0.312 whiteY: 0.329
[    23.410] (II) NOUVEAU(0): Supported established timings:
[    23.410] (II) NOUVEAU(0): 720x400@70Hz
[    23.410] (II) NOUVEAU(0): 640x480@60Hz
[    23.410] (II) NOUVEAU(0): 640x480@67Hz
[    23.410] (II) NOUVEAU(0): 640x480@72Hz
[    23.410] (II) NOUVEAU(0): 640x480@75Hz
[    23.410] (II) NOUVEAU(0): 800x600@56Hz
[    23.410] (II) NOUVEAU(0): 800x600@60Hz
[    23.410] (II) NOUVEAU(0): 800x600@72Hz
[    23.410] (II) NOUVEAU(0): 800x600@75Hz
[    23.410] (II) NOUVEAU(0): 832x624@75Hz
[    23.410] (II) NOUVEAU(0): 1024x768@60Hz
[    23.410] (II) NOUVEAU(0): 1024x768@70Hz
[    23.410] (II) NOUVEAU(0): 1024x768@75Hz
[    23.410] (II) NOUVEAU(0): 1280x1024@75Hz
[    23.410] (II) NOUVEAU(0): 1152x864@75Hz
[    23.410] (II) NOUVEAU(0): Manufacturer's mask: 0
[    23.410] (II) NOUVEAU(0): Supported standard timings:
[    23.410] (II) NOUVEAU(0): #0: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    23.410] (II) NOUVEAU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    23.410] (II) NOUVEAU(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    23.410] (II) NOUVEAU(0): #3: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    23.410] (II) NOUVEAU(0): Supported detailed timing:
[    23.410] (II) NOUVEAU(0): clock: 119.0 MHz   Image Size:  459 x 296 mm
[    23.410] (II) NOUVEAU(0): h_active: 1680  h_sync: 1728  h_sync_end 1760 h_blank_end 1840 h_border: 0
[    23.410] (II) NOUVEAU(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1080 v_border: 0
[    23.410] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 81 kHz, PixClock max 145 MHz
[    23.410] (II) NOUVEAU(0): Monitor name: SyncMaster
[    23.410] (II) NOUVEAU(0): Serial No: HCGQB06299
[    23.410] (II) NOUVEAU(0): EDID (in hex):
[    23.410] (II) NOUVEAU(0): 	00ffffffffffff004c2d72033232594d
[    23.410] (II) NOUVEAU(0): 	301201030e2c1e782a78f1a655489b26
[    23.410] (II) NOUVEAU(0): 	125054bfef80b30081808140714f0101
[    23.410] (II) NOUVEAU(0): 	0101010101017c2e90a0601a1e403020
[    23.410] (II) NOUVEAU(0): 	3600cb281100001a000000fd00384b1e
[    23.410] (II) NOUVEAU(0): 	510e000a202020202020000000fc0053
[    23.410] (II) NOUVEAU(0): 	796e634d61737465720a2020000000ff
[    23.410] (II) NOUVEAU(0): 	00484347514230363239390a2020001c
[    23.410] (II) NOUVEAU(0): EDID vendor "SAM", prod id 882
[    23.410] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[    23.410] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[    23.410] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    23.410] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.410] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    23.411] (II) NOUVEAU(0): Printing probed modes for output DVI-I-1
[    23.411] (II) NOUVEAU(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    23.411] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    23.444] (II) NOUVEAU(0): EDID for output DVI-I-2
[    23.444] (II) NOUVEAU(0): Printing probed modes for output DVI-I-2
[    23.444] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.444] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.444] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.444] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    23.444] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    23.556] (II) NOUVEAU(0): EDID for output TV-1
[    23.556] (II) NOUVEAU(0): Output DVI-I-1 connected
[    23.556] (II) NOUVEAU(0): Output DVI-I-2 connected
[    23.556] (II) NOUVEAU(0): Output TV-1 disconnected
[    23.556] (II) NOUVEAU(0): Using fuzzy aspect match for initial modes
[    23.556] (II) NOUVEAU(0): Output DVI-I-1 using initial mode 1024x768
[    23.556] (II) NOUVEAU(0): Output DVI-I-2 using initial mode 1024x768
[    23.556] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    23.556] (--) NOUVEAU(0): Virtual size is 1024x768 (pitch 0)
[    23.556] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[    23.556] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    23.556] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[    23.556] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    23.556] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[    23.556] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    23.556] (**) NOUVEAU(0):  Driver mode "848x480": 33.8 MHz (scaled from 0.0 MHz), 31.0 kHz, 60.0 Hz
[    23.556] (II) NOUVEAU(0): Modeline "848x480"x60.0   33.75  848 864 976 1088  480 486 494 517 +hsync +vsync (31.0 kHz)
[    23.556] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 59.9 Hz
[    23.556] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz)
[    23.556] (**) NOUVEAU(0): Display dimensions: (440, 300) mm
[    23.556] (**) NOUVEAU(0): DPI set to (59, 65)
[    23.556] (II) Loading sub module "fb"
[    23.556] (II) LoadModule: "fb"
[    23.556] (II) Loading /usr/lib/xorg/modules/libfb.so
[    23.557] (II) Module fb: vendor="X.Org Foundation"
[    23.557] 	compiled for 1.10.4, module version = 1.0.0
[    23.557] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.557] (II) Loading sub module "exa"
[    23.557] (II) LoadModule: "exa"
[    23.557] (II) Loading /usr/lib/xorg/modules/libexa.so
[    23.557] (II) Module exa: vendor="X.Org Foundation"
[    23.557] 	compiled for 1.10.4, module version = 2.5.0
[    23.557] 	ABI class: X.Org Video Driver, version 10.0
[    23.557] (II) Loading sub module "shadowfb"
[    23.557] (II) LoadModule: "shadowfb"
[    23.557] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    23.558] (II) Module shadowfb: vendor="X.Org Foundation"
[    23.558] 	compiled for 1.10.4, module version = 1.0.0
[    23.558] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    23.558] (II) UnloadModule: "vesa"
[    23.558] (II) Unloading vesa
[    23.558] (II) UnloadModule: "fbdev"
[    23.558] (II) Unloading fbdev
[    23.558] (II) UnloadModule: "fbdevhw"
[    23.558] (II) Unloading fbdevhw
[    23.558] (--) Depth 24 pixmap format is 32 bpp
[    23.558] (II) NOUVEAU(0): Opened GPU channel 1
[    23.559] (II) NOUVEAU(0): [DRI2] Setup complete
[    23.559] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    23.559] (II) NOUVEAU(0): GART: 512MiB available
[    23.561] (II) NOUVEAU(0): GART: Allocated 16MiB as a scratch buffer
[    23.561] (II) EXA(0): Driver allocated offscreen pixmaps
[    23.561] (II) EXA(0): Driver registered support for the following operations:
[    23.561] (II)         Solid
[    23.561] (II)         Copy
[    23.561] (II)         Composite (RENDER acceleration)
[    23.561] (II)         UploadToScreen
[    23.561] (II)         DownloadFromScreen
[    23.561] (==) NOUVEAU(0): Backing store disabled
[    23.561] (==) NOUVEAU(0): Silken mouse enabled
[    23.561] (II) NOUVEAU(0): [XvMC] Associated with NV40 texture adapter.
[    23.561] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    23.562] (==) NOUVEAU(0): DPMS enabled
[    23.562] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    23.562] (--) RandR disabled
[    23.562] (II) Initializing built-in extension Generic Event Extension
[    23.562] (II) Initializing built-in extension SHAPE
[    23.562] (II) Initializing built-in extension MIT-SHM
[    23.562] (II) Initializing built-in extension XInputExtension
[    23.562] (II) Initializing built-in extension XTEST
[    23.562] (II) Initializing built-in extension BIG-REQUESTS
[    23.562] (II) Initializing built-in extension SYNC
[    23.562] (II) Initializing built-in extension XKEYBOARD
[    23.562] (II) Initializing built-in extension XC-MISC
[    23.562] (II) Initializing built-in extension SECURITY
[    23.562] (II) Initializing built-in extension XINERAMA
[    23.562] (II) Initializing built-in extension XFIXES
[    23.562] (II) Initializing built-in extension RENDER
[    23.562] (II) Initializing built-in extension RANDR
[    23.562] (II) Initializing built-in extension COMPOSITE
[    23.562] (II) Initializing built-in extension DAMAGE
[    23.562] (II) Initializing built-in extension GESTURE
[    23.573] (II) AIGLX: Trying DRI driver /usr/lib/x86_64-linux-gnu/dri/nouveau_dri.so
[    23.590] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    23.590] (II) AIGLX: enabled GLX_INTEL_swap_event
[    23.590] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    23.590] (II) AIGLX: enabled GLX_SGI_make_current_read
[    23.590] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    23.591] (II) AIGLX: Loaded and initialized nouveau
[    23.591] (II) GLX: Initialized DRI2 GL provider for screen 0
[    23.593] (II) NOUVEAU(0): NVEnterVT is called.
[    23.594] (II) NOUVEAU(0): Setting screen physical size to 270 x 203
[    23.594] resize called 1024 768
[    23.605] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.617] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.617] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.617] (II) LoadModule: "evdev"
[    23.618] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.619] (II) Module evdev: vendor="X.Org Foundation"
[    23.619] 	compiled for 1.10.2, module version = 2.6.0
[    23.619] 	Module class: X.Org XInput Driver
[    23.619] 	ABI class: X.Org XInput driver, version 12.3
[    23.619] (II) Using input driver 'evdev' for 'Power Button'
[    23.619] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.619] (**) Power Button: always reports core events
[    23.619] (**) Power Button: Device: "/dev/input/event1"
[    23.619] (--) Power Button: Found keys
[    23.619] (II) Power Button: Configuring as keyboard
[    23.619] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.619] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.619] (**) Option "xkb_rules" "evdev"
[    23.619] (**) Option "xkb_model" "pc105"
[    23.619] (**) Option "xkb_layout" "us"
[    23.624] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.624] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.624] (II) Using input driver 'evdev' for 'Power Button'
[    23.624] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.624] (**) Power Button: always reports core events
[    23.624] (**) Power Button: Device: "/dev/input/event0"
[    23.624] (--) Power Button: Found keys
[    23.624] (II) Power Button: Configuring as keyboard
[    23.624] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    23.624] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.624] (**) Option "xkb_rules" "evdev"
[    23.624] (**) Option "xkb_model" "pc105"
[    23.624] (**) Option "xkb_layout" "us"
[    23.626] (II) config/udev: Adding input device Generic USB K/B (/dev/input/event2)
[    23.626] (**) Generic USB K/B: Applying InputClass "evdev keyboard catchall"
[    23.626] (II) Using input driver 'evdev' for 'Generic USB K/B'
[    23.626] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.627] (**) Generic USB K/B: always reports core events
[    23.627] (**) Generic USB K/B: Device: "/dev/input/event2"
[    23.627] (--) Generic USB K/B: Found keys
[    23.627] (II) Generic USB K/B: Configuring as keyboard
[    23.627] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.0/input/input2/event2"
[    23.627] (II) XINPUT: Adding extended input device "Generic USB K/B" (type: KEYBOARD)
[    23.627] (**) Option "xkb_rules" "evdev"
[    23.627] (**) Option "xkb_model" "pc105"
[    23.627] (**) Option "xkb_layout" "us"
[    23.628] (II) config/udev: Adding input device Generic USB K/B (/dev/input/event3)
[    23.628] (**) Generic USB K/B: Applying InputClass "evdev pointer catchall"
[    23.628] (**) Generic USB K/B: Applying InputClass "evdev keyboard catchall"
[    23.628] (II) Using input driver 'evdev' for 'Generic USB K/B'
[    23.628] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.628] (**) Generic USB K/B: always reports core events
[    23.628] (**) Generic USB K/B: Device: "/dev/input/event3"
[    23.628] (--) Generic USB K/B: Found 3 mouse buttons
[    23.628] (--) Generic USB K/B: Found scroll wheel(s)
[    23.628] (--) Generic USB K/B: Found relative axes
[    23.628] (--) Generic USB K/B: Found x and y relative axes
[    23.628] (--) Generic USB K/B: Found keys
[    23.628] (II) Generic USB K/B: Configuring as mouse
[    23.628] (II) Generic USB K/B: Configuring as keyboard
[    23.628] (II) Generic USB K/B: Adding scrollwheel support
[    23.628] (**) Generic USB K/B: YAxisMapping: buttons 4 and 5
[    23.628] (**) Generic USB K/B: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.628] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.1/input/input3/event3"
[    23.628] (II) XINPUT: Adding extended input device "Generic USB K/B" (type: KEYBOARD)
[    23.628] (**) Option "xkb_rules" "evdev"
[    23.628] (**) Option "xkb_model" "pc105"
[    23.628] (**) Option "xkb_layout" "us"
[    23.629] (II) Generic USB K/B: initialized for relative axes.
[    23.629] (**) Generic USB K/B: (accel) keeping acceleration scheme 1
[    23.629] (**) Generic USB K/B: (accel) acceleration profile 0
[    23.629] (**) Generic USB K/B: (accel) acceleration factor: 2.000
[    23.629] (**) Generic USB K/B: (accel) acceleration threshold: 4
[    23.629] (II) config/udev: Adding input device Generic USB K/B (/dev/input/mouse0)
[    23.629] (II) No input driver/identifier specified (ignoring)
[    23.630] (II) config/udev: Adding input device Generic USB K/B (/dev/input/event4)
[    23.630] (**) Generic USB K/B: Applying InputClass "evdev pointer catchall"
[    23.630] (II) Using input driver 'evdev' for 'Generic USB K/B'
[    23.630] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.630] (**) Generic USB K/B: always reports core events
[    23.630] (**) Generic USB K/B: Device: "/dev/input/event4"
[    23.630] (--) Generic USB K/B: Found 9 mouse buttons
[    23.630] (--) Generic USB K/B: Found scroll wheel(s)
[    23.630] (--) Generic USB K/B: Found relative axes
[    23.630] (--) Generic USB K/B: Found x and y relative axes
[    23.630] (II) Generic USB K/B: Configuring as mouse
[    23.630] (II) Generic USB K/B: Adding scrollwheel support
[    23.630] (**) Generic USB K/B: YAxisMapping: buttons 4 and 5
[    23.630] (**) Generic USB K/B: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.630] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.1/2-3.1:1.2/input/input4/event4"
[    23.630] (II) XINPUT: Adding extended input device "Generic USB K/B" (type: MOUSE)
[    23.630] (II) Generic USB K/B: initialized for relative axes.
[    23.630] (**) Generic USB K/B: (accel) keeping acceleration scheme 1
[    23.630] (**) Generic USB K/B: (accel) acceleration profile 0
[    23.630] (**) Generic USB K/B: (accel) acceleration factor: 2.000
[    23.630] (**) Generic USB K/B: (accel) acceleration threshold: 4
[    23.631] (II) config/udev: Adding input device Generic USB K/B (/dev/input/mouse1)
[    23.631] (II) No input driver/identifier specified (ignoring)
[   511.692] (II) config/udev: Adding input device Dell Premium USB Optical Mouse (/dev/input/mouse2)
[   511.692] (II) No input driver/identifier specified (ignoring)
[   511.695] (II) config/udev: Adding input device Dell Premium USB Optical Mouse (/dev/input/event5)
[   511.695] (**) Dell Premium USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[   511.695] (II) Using input driver 'evdev' for 'Dell Premium USB Optical Mouse'
[   511.695] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   511.695] (**) Dell Premium USB Optical Mouse: always reports core events
[   511.695] (**) Dell Premium USB Optical Mouse: Device: "/dev/input/event5"
[   511.696] (--) Dell Premium USB Optical Mouse: Found 14 mouse buttons
[   511.696] (--) Dell Premium USB Optical Mouse: Found scroll wheel(s)
[   511.696] (--) Dell Premium USB Optical Mouse: Found relative axes
[   511.696] (--) Dell Premium USB Optical Mouse: Found x and y relative axes
[   511.696] (II) Dell Premium USB Optical Mouse: Configuring as mouse
[   511.696] (II) Dell Premium USB Optical Mouse: Adding scrollwheel support
[   511.696] (**) Dell Premium USB Optical Mouse: YAxisMapping: buttons 4 and 5
[   511.696] (**) Dell Premium USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   511.696] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-3/2-3.2/2-3.2:1.0/input/input5/event5"
[   511.696] (II) XINPUT: Adding extended input device "Dell Premium USB Optical Mouse" (type: MOUSE)
[   511.696] (II) Dell Premium USB Optical Mouse: initialized for relative axes.
[   511.696] (**) Dell Premium USB Optical Mouse: (accel) keeping acceleration scheme 1
[   511.696] (**) Dell Premium USB Optical Mouse: (accel) acceleration profile 0
[   511.696] (**) Dell Premium USB Optical Mouse: (accel) acceleration factor: 2.000
[   511.696] (**) Dell Premium USB Optical Mouse: (accel) acceleration threshold: 4
[   519.505] resize called 2704 1050
[   532.167] (II) XKB: reuse xkmfile /var/lib/xkb/server-9A8405F3FE0A780485714A4B6DD41909C2CF9F83.xkm

---

### Post by gator_2011 on 2011-10-22
> **MAFoElffen said:**
> I do that in testing just for giggles... BUT then process scheduling on the Server Edition is for server/background processes and secondary on Desktop/foreground processes.  It works, but not as well as running a desktop on a Desktop Edition.  Been testing Oneiric since last June with 5 boxes running nVidia, 1 ATI, 1 Intel GPUs.

@David Crockett
Please post your /etc/X11/xorg.conf and /var/log/xorg.0.log. Be sure you post them within CODE tags...  The xorg.conf should show us how your card is configured and if there is anything odd about your "dual monitor" setup.  The Xorg log should show both your monitors connected and what kind of data it's passing back.

Trust the nvidia-settings applet over the default Monitors applet.  The later has some bugs on reading multiple monitors at the moment.

When I try to install a NVidia driver I loose GUI altogether... This build isnt working long term though, I will have to try to install the NVidia driver again any suggestions?

---

### Post by MAFoElffen on 2011-10-22
Okay... Sorry, this may end up as log-winded.  You have a basic problem. You have many options... Maybe too many.

What did I find? You don't have an Xorg.conf file, so Xorg has to decide on it's own what driver to use, which it picked the Nouveau driver.  I can see this in your log, because it tried to load the xorg-xserver-video-nv but failed because it couldn't find it (it should have).  If you had installed an NVidia driver, either via Ubuntu or from NVidia, you would have had an xorg.conf file and it would be using it.

Your 2 displays "do" show up as connected to DVI-I-1 and DVI-I-... but there isn't any configuration file present to tell xorg what to do with the second display.  If you care running the Nouveau driver then you might not have NVidia drivers installed(?)  If because you have an older card... well.

The reason I say that Is that lspci says you have an NV18GL chipset Quadro NVS 280 SD and Xorg reports it as an NV43 chipset GeForce 6xxx. So it is not completely clear which proprietary driver from NVidia driver would work for you. ...Or what model card it is.  You might want to pop the cover on your box and verify which model of NVidia card it is.

The esay way out of this is to confirm what model card you have and install NVidia Drivers for it.  You could easily install them through system settings > additional drivers. Then nvidia setting would work and you could use it to setup your displays.  nvidia-setting would then edit the xorg.conf file for you.

If you  continue to use opensource drivers, then you would have to manually configure it via a custom xorg.conf file.  If you do that, I could help you on those edits.

---

### Post by MAFoElffen on 2011-10-22
After thinking about this.  One more idea.

Look in your home directory and turn on "show hidden files ( <cntrll><h> ) and  "~/.config/"...  In the .config directory, look to see if there is a file called "monitors.xml". If there is delete it. 

Doing that may reset the system settings > Displays applet into working for you with 2 displays.

---

### Post by gator_2011 on 2011-10-23
> **MAFoElffen said:**
> After thinking about this.  One more idea.

Look in your home directory and turn on "show hidden files ( <cntrll><h> ) and  "~/.config/"...  In the .config directory, look to see if there is a file called "monitors.xml". If there is delete it. 

Doing that may reset the system settings > Displays applet into working for you with 2 displays.




I re-installed using Ubuntu Desktop 11.10 32bit, then removed the 173 driver and installed the current driver and it seems to be working very well. I don't require 64bit so I will run like this for a while... Thank you for your assistance.

---

### Post by David Crockett on 2011-10-24
Hi all,

This is my xorg.conf file.    It is rather simple  and the NVIDIA control program does not want to load it and clearly no useful modifications have been made.


Section "Screen"
	Identifier	"Default Screen"
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection



I am a bit nervous about playing around with it.   I have had disasters were it won't boot up into the desktop and I could not get the terminal to run to try to fix it.

Any advice would be appreciated.

David


D

---

### Post by MAFoElffen on 2011-10-24
> **David Crockett said:**
> This is my xorg.conf file.    It is rather simple  and the NVIDIA control program does not want to load it and clearly no useful modifications have been made.
```

Section "Screen"
    Identifier    "Default Screen"
    Option    "AddARGBGLXVisuals"    "True"
EndSection

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```
I am a bit nervous about playing around with it.   I have had disasters were it won't boot up into the desktop and I could not get the terminal to run to try to fix it.

Any advice would be appreciated.
David
So the most basic of Xorg file would be:
```

Section "Device"
    Driver    "default"
EndSection

```
Where there is a "driver" line pointing to a particular driver...  See something missing in yours?  

The next pieces in a dual display would be a distinct monitor section for each monitor, a distinct screen section for each monitor and a screen server layout section that places the individual screens into some kind of logical order....

NVidia Settings does not work for you because you are not using NVidia drivers.  That would be a line in your device section that would say:
```

  Drivers   "nvidia"

```
Do you have NVidia Drivers installed yet?  (Giving a benefit of doubt of maybe just a bad xorg.conf file...)

---

### Post by blitzd on 2011-10-25
I was having this same issue, and installing the 'current' driver at least allowed me to get my second monitor active. 

It still won't use my 2nd monitor as the main monitor though - in fact, toggling the 'Make this the primary display for the X screen' option in the NVIDIA X Server Settings dialog and hitting apply does absolutely nothing. And, in fact - disabling my 2nd monitor and hitting apply, causes the screen to go black for a bit - but both screens come back and are still active.

These drivers are very sketchy.

Here's my xorg.conf while I'm at it:

```


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 280.13  (buildd@yellow)  Fri Aug  5 12:31:28 UTC 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LEN"
    HorizSync       61.0 - 73.2
    VertRefresh     40.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 3700M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

The login screen shows up on the external monitor, but after that the main display is the laptop again. Or maybe it's just Unity doesn't support a display setup like that?

---

### Post by MAFoElffen on 2011-10-26
> **blitzd said:**
> I was having this same issue, and installing the 'current' driver at least allowed me to get my second monitor active. 

It still won't use my 2nd monitor as the main monitor though - in fact, toggling the 'Make this the primary display for the X screen' option in the NVIDIA X Server Settings dialog and hitting apply does absolutely nothing. And, in fact - disabling my 2nd monitor and hitting apply, causes the screen to go black for a bit - but both screens come back and are still active.

These drivers are very sketchy.

Here's my xorg.conf while I'm at it:

```


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 280.13  (buildd@yellow)  Fri Aug  5 12:31:28 UTC 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LEN"
    HorizSync       61.0 - 73.2
    VertRefresh     40.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 3700M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```The login screen shows up on the external monitor, but after that the main display is the laptop again. Or maybe it's just Unity doesn't support a display setup like that?
Still working on the OP's problem... This is my weekend, so in and out until Friday. Could you do me a a favor? Could you please repost your post request in my Sticky and I'll take car of you there... Have Ideas on yours, but rushed today-- And do not want you to fall through the cracks. with not getting helped...
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

---

### Post by Menyus on 2011-10-27
I had the same problem after upgrading to Ubuntu 11.10. My system has an older nVidia 6800 XT card and I installed the current recommended driver from the proprietary driver list. My main monitor was working fine but I couldn't enable my second monitor through System Settings/Displays. I solved the problem by running 'sudo nvidia-settings' from the command line, which allowed me to enable the second monitor in twin view mode (could not make it work as separate X-screen). So now both monitors are working.

---

### Post by David Crockett on 2011-10-31
I have found no solution so far.    I find that Tomboy and Evolution are also broken and will not sync.

I am very unhappy. :(

---

### Post by blitzd on 2011-10-31
> **MAFoElffen said:**
> Still working on the OP's problem... This is my weekend, so in and out until Friday. Could you do me a a favor? Could you please repost your post request in my Sticky and I'll take car of you there... Have Ideas on yours, but rushed today-- And do not want you to fall through the cracks. with not getting helped...
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Hey MAFoElffen,

Thanks for the help offer but after a series of calamities with Ubuntu/NVidia/Fedora/openSUSE I've downgraded my laptop to Windows. 

I ran Ubuntu for a year and a half without real issues both at home and work, but my workstation setup in both locales has since become dual-monitor and that seems to be a real sticking point for many Linux distros. In trying to create install media/perform an install, I just reached the end of my rope. Brasero gets stuck on checksums still in 11.10, the usb creator doesn't create an actual working usb-install, openSUSE net install pauses randomly until the mouse is moved, openSUSE live-cd install crashes half way through with an inst-finish error, Ubuntu 11.10 install gets stuck at 'installing system' for multiple hours, and on and on and on. I spent the whole day dueling with distros, and in the end when nothing else would work I just gave up and popped Win 7 back in - and the whole thing went off without a hitch. Same thing happened back in 2006 when I first joined the forums actually, but that time I only managed to go a few months with Ubuntu. Maybe next time it'll actually stick!

---

### Post by astroaniket on 2011-11-15
> **MAFoElffen said:**
> After thinking about this.  One more idea.

Look in your home directory and turn on "show hidden files ( <cntrll><h> ) and  "~/.config/"...  In the .config directory, look to see if there is a file called "monitors.xml". If there is delete it. 

Doing that may reset the system settings > Displays applet into working for you with 2 displays.

This solved my problem. Thanks.

My config. was nvidia GEforce 8400 on HP pavilion 3005 TX. :D

---

### Post by David Crockett on 2012-01-09
Hi,

I  have still not been able to solve it. 

My  /etc/X11/xorg.conf seems to have been replaced by the following rather simple one:

Section "Screen"
Identifier "Default Screen"
Option "AddARGBGLXVisuals" "True"
EndSection

Section "Device"
Identifier "Default Device"
Option "NoLogo" "True"
EndSection


I don't know how to revise this. I have done the third party driver download thing and the NVIVIA X server settings program does not seem to know how to reconfigure my Xorg.conf file. And I do not know how to get it to do so or really how to do it manually. I have tried to do so and made a mess and ended up reinstalling Ubuntu.

 The results of the lspci command. Mine gives the following results.

crockett@cuneatus-1-0:~$ sudo lspci
[sudo] password for crockett:
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82875P/E7210 Processor to PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV18GL [Quadro NVS 280 SD] (rev a2)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller
03:06.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)

I am at a loss as to what to do. If you don't get it right it can be a real disaster.

Regards,
David

---

### Post by David Crockett on 2012-01-09
Hi all,

The NVIDIA X server settings app will not load the configuration page:

The error message is:

Unable to load X Server Display Configuration page:

Failed to query NoScanout for screen 0.

David

---

### Post by David Crockett on 2012-01-09
One more bit of information.   The NVIDIA X Server Setting app does not that there are two monitors:


It lists CRT-O (Dell U2410)  This works
         CRT-1 (Dell 1704FPV)  This does not work

The program reports the following for the graphics card tab:

Bus ID:   ?@?:?:?

Here it reports the name of model of the card, that there are two display devices and the their names.    

When you go to CRT-1 it says that the refresh rate is unknown.

---

### Post by David Crockett on 2012-05-09
12.04 solved my problems.

D:)

---

