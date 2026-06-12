---
title: "External monitor problem after upgrade to 11.10"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by dome1970 on 2011-10-28
I upgraded from Ubuntu 11.04 to 11.10 on my Asus f6e (with Intel Corporation Mobile GM965/GL960  Integrated Graphics Controller). The external monitor I've always used now only works as
dual monitor or clone, whereas when it should work as the only display everything gets unreadable and fuzzy due to thick white horizontal lines.  However it used to work perfectly with 11.04. Perhaps it is similar to this:  [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/830949](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/830949). In any case: can I do something about this problem?
Thanks,

dome1970

---

### Post by JosephC on 2012-02-20
Same here. Last night it worked for no conceivable reason whatsoever, but today the external monitor is back to utter corruption. I can't explain the randomness, but it's worth mentioning that it only accidentally worked once. I have tried to replicate what I did last night (which was unrelated, as far as I can tell), which was to install Cinnamon. Regardless, it doesn't work now. Hope someone fixes it for Oneiric. It works fine in Precise, but Precise is not even a little stable as of yet.

Good luck. This is just a show of solidarity!

---

### Post by MAFoElffen on 2012-02-20
> **dome1970 said:**
> I upgraded from Ubuntu 11.04 to 11.10 on my Asus f6e (with Intel Corporation Mobile GM965/GL960  Integrated Graphics Controller). The external monitor I've always used now only works as
dual monitor or clone, whereas when it should work as the only display everything gets unreadable and fuzzy due to thick white horizontal lines.  However it used to work perfectly with 11.04. Perhaps it is similar to this:  [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/830949](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/830949). In any case: can I do something about this problem?
Thanks,
dome1970
Both of you...  Connect your external monitor's and boot. Shutdown. Disconnect your externals and reboot.

Then please post your /var/log/Xorg.1.log files.  (Xorg.0.log is current, 1 is 1 previous, etc.)

What I would like to check is if Xorg sees the internal display and external monitor, what ports are assigned to them and what data the internal and external displays are passing back.

Other Info that log will tell me is the specific video chipset and what driver is being used.

---

### Post by dome1970 on 2012-03-02
OK, here is my /var/log/Xorg.1.log following "Connect your external monitor's and boot. Shutdown. Disconnect your externals and reboot." Thanks [MAFoElffen]("http://ubuntuforums.org/member.php?u=1044547") for your help,
dome1970


**********
[  1837.595] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[  1837.595] X Protocol Version 11, Revision 0
[  1837.595] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[  1837.595] Current Operating System: Linux dome-laptop 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:49:42 UTC 2012 i686
[  1837.595] Kernel command line: root=UUID=3fd08ec9-d375-4918-abad-0895e21c2996 ro quiet splash vga=792 
[  1837.595] Build Date: 19 October 2011  05:09:41AM
[  1837.595] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  1837.595] Current version of pixman: 0.22.2
[  1837.595]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[  1837.595] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1837.595] (==) Log file: "/var/log/Xorg.1.log", Time: Thu Mar  1 22:40:24 2012
[  1837.595] (==) Using config file: "/etc/X11/xorg.conf"
[  1837.595] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  1837.595] (==) No Layout section.  Using the first Screen section.
[  1837.595] (**) |-->Screen "Default Screen" (0)
[  1837.595] (**) |   |-->Monitor "Configured Monitor"
[  1837.596] (**) |   |-->Device "Configured Video Device"
[  1837.596] (==) Automatically adding devices
[  1837.596] (==) Automatically enabling devices
[  1837.596] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  1837.596]     Entry deleted from font path.
[  1837.596] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[  1837.596] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[  1837.596] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[  1837.596] (II) Loader magic: 0x823ada0
[  1837.596] (II) Module ABI versions:
[  1837.596]     X.Org ANSI C Emulation: 0.4
[  1837.596]     X.Org Video Driver: 10.0
[  1837.596]     X.Org XInput driver : 12.3
[  1837.596]     X.Org Server Extension : 5.0
[  1837.597] (--) PCI:*(0:0:2:0) 8086:2a02:1043:14e2 rev 3, Mem @ 0xfeb00000/1048576, 0xe0000000/268435456, I/O @ 0x0000ec00/8
[  1837.597] (--) PCI: (0:0:2:1) 8086:2a03:1043:14e2 rev 3, Mem @ 0xfe900000/1048576
[  1837.597] (II) Open ACPI successful (/var/run/acpid.socket)
[  1837.597] (II) LoadModule: "extmod"
[  1837.597] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[  1837.597] (II) Module extmod: vendor="X.Org Foundation"
[  1837.597]     compiled for 1.10.4, module version = 1.0.0
[  1837.598]     Module class: X.Org Server Extension
[  1837.598]     ABI class: X.Org Server Extension, version 5.0
[  1837.598] (II) Loading extension MIT-SCREEN-SAVER
[  1837.598] (II) Loading extension XFree86-VidModeExtension
[  1837.598] (II) Loading extension XFree86-DGA
[  1837.598] (II) Loading extension DPMS
[  1837.598] (II) Loading extension XVideo
[  1837.598] (II) Loading extension XVideo-MotionCompensation
[  1837.598] (II) Loading extension X-Resource
[  1837.598] (II) LoadModule: "dbe"
[  1837.598] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[  1837.598] (II) Module dbe: vendor="X.Org Foundation"
[  1837.598]     compiled for 1.10.4, module version = 1.0.0
[  1837.598]     Module class: X.Org Server Extension
[  1837.598]     ABI class: X.Org Server Extension, version 5.0
[  1837.598] (II) Loading extension DOUBLE-BUFFER
[  1837.598] (II) LoadModule: "glx"
[  1837.598] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  1837.598] (II) Module glx: vendor="X.Org Foundation"
[  1837.598]     compiled for 1.10.4, module version = 1.0.0
[  1837.598]     ABI class: X.Org Server Extension, version 5.0
[  1837.598] (==) AIGLX enabled
[  1837.598] (II) Loading extension GLX
[  1837.598] (II) LoadModule: "record"
[  1837.598] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[  1837.598] (II) Module record: vendor="X.Org Foundation"
[  1837.598]     compiled for 1.10.4, module version = 1.13.0
[  1837.598]     Module class: X.Org Server Extension
[  1837.598]     ABI class: X.Org Server Extension, version 5.0
[  1837.598] (II) Loading extension RECORD
[  1837.598] (II) LoadModule: "dri"
[  1837.599] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[  1837.599] (II) Module dri: vendor="X.Org Foundation"
[  1837.599]     compiled for 1.10.4, module version = 1.0.0
[  1837.599]     ABI class: X.Org Server Extension, version 5.0
[  1837.599] (II) Loading extension XFree86-DRI
[  1837.599] (II) LoadModule: "dri2"
[  1837.599] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1837.599] (II) Module dri2: vendor="X.Org Foundation"
[  1837.599]     compiled for 1.10.4, module version = 1.2.0
[  1837.599]     ABI class: X.Org Server Extension, version 5.0
[  1837.599] (II) Loading extension DRI2
[  1837.599] (==) Matched intel as autoconfigured driver 0
[  1837.599] (==) Matched vesa as autoconfigured driver 1
[  1837.599] (==) Matched fbdev as autoconfigured driver 2
[  1837.599] (==) Assigned the driver to the xf86ConfigLayout
[  1837.599] (II) LoadModule: "intel"
[  1837.599] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1837.599] (II) Module intel: vendor="X.Org Foundation"
[  1837.599]     compiled for 1.10.4, module version = 2.15.901
[  1837.599]     Module class: X.Org Video Driver
[  1837.599]     ABI class: X.Org Video Driver, version 10.0
[  1837.599] (II) LoadModule: "vesa"
[  1837.600] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  1837.600] (II) Module vesa: vendor="X.Org Foundation"
[  1837.600]     compiled for 1.10.2, module version = 2.3.0
[  1837.600]     Module class: X.Org Video Driver
[  1837.600]     ABI class: X.Org Video Driver, version 10.0
[  1837.600] (II) LoadModule: "fbdev"
[  1837.600] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  1837.600] (II) Module fbdev: vendor="X.Org Foundation"
[  1837.600]     compiled for 1.10.0, module version = 0.4.2
[  1837.600]     ABI class: X.Org Video Driver, version 10.0
[  1837.600] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server
[  1837.601] (II) VESA: driver for VESA chipsets: vesa
[  1837.601] (II) FBDEV: driver for framebuffer: fbdev
[  1837.601] (++) using VT number 8

[  1837.602] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[  1837.602] (WW) Falling back to old probe method for vesa
[  1837.602] (WW) Falling back to old probe method for fbdev
[  1837.602] (II) Loading sub module "fbdevhw"
[  1837.602] (II) LoadModule: "fbdevhw"
[  1837.602] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  1837.603] (II) Module fbdevhw: vendor="X.Org Foundation"
[  1837.603]     compiled for 1.10.4, module version = 0.0.2
[  1837.603]     ABI class: X.Org Video Driver, version 10.0
[  1837.603] drmOpenDevice: node name is /dev/dri/card0
[  1837.603] drmOpenDevice: open result is 14, (OK)
[  1837.603] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[  1837.603] drmOpenDevice: node name is /dev/dri/card0
[  1837.603] drmOpenDevice: open result is 14, (OK)
[  1837.603] drmOpenByBusid: drmOpenMinor returns 14
[  1837.603] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[  1837.603] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[  1837.603] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[  1837.603] (==) intel(0): RGB weight 888
[  1837.603] (==) intel(0): Default visual is TrueColor
[  1837.603] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[  1837.603] (--) intel(0): Chipset: "965GM"
[  1837.603] (**) intel(0): Relaxed fencing enabled
[  1837.603] (**) intel(0): Wait on SwapBuffers? enabled
[  1837.603] (**) intel(0): Triple buffering? enabled
[  1837.603] (**) intel(0): Framebuffer tiled
[  1837.603] (**) intel(0): Pixmaps tiled
[  1837.603] (**) intel(0): 3D buffers tiled
[  1837.603] (**) intel(0): SwapBuffers wait enabled
[  1837.603] (==) intel(0): video overlay key set to 0x101fe
[  1837.603] (II) intel(0): Output LVDS1 using monitor section Configured Monitor
[  1837.603] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[  1837.677] (II) intel(0): Output VGA1 has no monitor section
[  1837.692] (II) intel(0): Output HDMI1 has no monitor section
[  1837.693] (II) intel(0): EDID for output LVDS1
[  1837.693] (II) intel(0): Manufacturer: APP  Model: 9c5e  Serial#: 0
[  1837.693] (II) intel(0): Year: 2006  Week: 9
[  1837.693] (II) intel(0): EDID Version: 1.3
[  1837.693] (II) intel(0): Digital Display Input
[  1837.693] (II) intel(0): Max Image Size [cm]: horiz.: 29  vert.: 19
[  1837.693] (II) intel(0): Gamma: 2.20
[  1837.693] (II) intel(0): No DPMS capabilities specified
[  1837.693] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[  1837.693] (II) intel(0): First detailed timing is preferred mode
[  1837.693] (II) intel(0): redX: 0.622 redY: 0.346   greenX: 0.333 greenY: 0.528
[  1837.693] (II) intel(0): blueX: 0.164 blueY: 0.162   whiteX: 0.312 whiteY: 0.329
[  1837.693] (II) intel(0): Manufacturer's mask: 0
[  1837.693] (II) intel(0): Supported detailed timing:
[  1837.693] (II) intel(0): clock: 71.0 MHz   Image Size:  286 x 178 mm
[  1837.693] (II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1360 h_blank_end 1440 h_border: 0
[  1837.693] (II) intel(0): v_active: 800  v_sync: 803  v_sync_end 809 v_blanking: 823 v_border: 0
[  1837.693] (II) intel(0): Unknown vendor-specific block 1
[  1837.693] (II) intel(0):  N133I1-L01
[  1837.693] (II) intel(0): Monitor name: Color LCD
[  1837.693] (II) intel(0): EDID (in hex):
[  1837.693] (II) intel(0):     00ffffffffffff0006105e9c00000000
[  1837.693] (II) intel(0):     09100103801d13780a65219f5855872a
[  1837.693] (II) intel(0):     29505400000001010101010101010101
[  1837.693] (II) intel(0):     010101010101bc1b00a0502017303020
[  1837.693] (II) intel(0):     36001eb2100000180000000100061020
[  1837.693] (II) intel(0):     00000000000000000a20000000fe004e
[  1837.693] (II) intel(0):     31333349312d4c30310a2020000000fc
[  1837.693] (II) intel(0):     00436f6c6f72204c43440a2020200061
[  1837.693] (II) intel(0): EDID vendor "APP", prod id 40030
[  1837.693] (II) intel(0): Printing DDC gathered Modelines:
[  1837.693] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1837.693] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[  1837.693] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[  1837.693] (II) intel(0): Printing probed modes for output LVDS1
[  1837.693] (II) intel(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1837.693] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1837.693] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1837.693] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1837.693] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1837.751] (II) intel(0): EDID for output VGA1
[  1837.751] (II) intel(0): Manufacturer: ACI  Model: 24f2  Serial#: 16843009
[  1837.751] (II) intel(0): Year: 2010  Week: 12
[  1837.751] (II) intel(0): EDID Version: 1.3
[  1837.751] (II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[  1837.751] (II) intel(0): Signal levels configurable
[  1837.751] (II) intel(0): Sync:  Separate  Composite  SyncOnGreen
[  1837.751] (II) intel(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[  1837.751] (II) intel(0): Gamma: 2.20
[  1837.751] (II) intel(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[  1837.751] (II) intel(0): Default color space is primary color space
[  1837.751] (II) intel(0): First detailed timing is preferred mode
[  1837.751] (II) intel(0): redX: 0.640 redY: 0.340   greenX: 0.290 greenY: 0.609
[  1837.751] (II) intel(0): blueX: 0.140 blueY: 0.069   whiteX: 0.310 whiteY: 0.330
[  1837.751] (II) intel(0): Supported established timings:
[  1837.751] (II) intel(0): 720x400@70Hz
[  1837.751] (II) intel(0): 640x480@60Hz
[  1837.751] (II) intel(0): 640x480@67Hz
[  1837.751] (II) intel(0): 640x480@72Hz
[  1837.751] (II) intel(0): 640x480@75Hz
[  1837.751] (II) intel(0): 800x600@56Hz
[  1837.751] (II) intel(0): 800x600@60Hz
[  1837.751] (II) intel(0): 800x600@72Hz
[  1837.751] (II) intel(0): 800x600@75Hz
[  1837.751] (II) intel(0): 832x624@75Hz
[  1837.751] (II) intel(0): 1024x768@60Hz
[  1837.751] (II) intel(0): 1024x768@70Hz
[  1837.751] (II) intel(0): 1024x768@75Hz
[  1837.751] (II) intel(0): 1280x1024@75Hz
[  1837.751] (II) intel(0): Manufacturer's mask: 0
[  1837.751] (II) intel(0): Supported standard timings:
[  1837.751] (II) intel(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[  1837.751] (II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[  1837.751] (II) intel(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[  1837.751] (II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
[  1837.752] (II) intel(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[  1837.752] (II) intel(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[  1837.752] (II) intel(0): #6: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[  1837.752] (II) intel(0): Supported detailed timing:
[  1837.752] (II) intel(0): clock: 148.5 MHz   Image Size:  531 x 299 mm
[  1837.752] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[  1837.752] (II) intel(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[  1837.752] (II) intel(0): Ranges: V min: 56 V max: 76 Hz, H min: 31 H max: 83 kHz, PixClock max 175 MHz
[  1837.752] (II) intel(0): Monitor name: VW246
[  1837.752] (II) intel(0): Serial No: A3LMQS038555
[  1837.752] (II) intel(0): EDID (in hex):
[  1837.752] (II) intel(0):     00ffffffffffff000469f22401010101
[  1837.752] (II) intel(0):     0c1401031e351e78eec4f6a3574a9c23
[  1837.752] (II) intel(0):     114f54bfef00714f818081409500a940
[  1837.752] (II) intel(0):     b300d1c00101023a801871382d40582c
[  1837.752] (II) intel(0):     4500132b2100001e000000fd00384c1f
[  1837.752] (II) intel(0):     5311000a202020202020000000fc0056
[  1837.752] (II) intel(0):     573234360a20202020202020000000ff
[  1837.752] (II) intel(0):     0041334c4d51533033383535350a00fe
[  1837.752] (II) intel(0): Printing probed modes for output VGA1
[  1837.752] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz)
[  1837.752] (II) intel(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[  1837.752] (II) intel(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz)
[  1837.752] (II) intel(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  1837.752] (II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  1837.752] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[  1837.752] (II) intel(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  1837.752] (II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  1837.752] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
[  1837.752] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  1837.752] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  1837.752] (II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  1837.752] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  1837.752] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  1837.752] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  1837.752] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  1837.752] (II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz)
[  1837.752] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  1837.752] (II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  1837.752] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  1837.752] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  1837.768] (II) intel(0): EDID for output HDMI1
[  1837.768] (II) intel(0): Output LVDS1 connected
[  1837.768] (II) intel(0): Output VGA1 connected
[  1837.768] (II) intel(0): Output HDMI1 disconnected
[  1837.768] (II) intel(0): Using fuzzy aspect match for initial modes
[  1837.768] (II) intel(0): Output LVDS1 using initial mode 1024x768
[  1837.768] (II) intel(0): Output VGA1 using initial mode 1024x768
[  1837.768] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[  1837.768] (II) intel(0): Kernel page flipping support detected, enabling
[  1837.768] (**) intel(0): Display dimensions: (290, 190) mm
[  1837.768] (**) intel(0): DPI set to (89, 102)
[  1837.768] (II) Loading sub module "fb"
[  1837.768] (II) LoadModule: "fb"
[  1837.768] (II) Loading /usr/lib/xorg/modules/libfb.so
[  1837.768] (II) Module fb: vendor="X.Org Foundation"
[  1837.768]     compiled for 1.10.4, module version = 1.0.0
[  1837.768]     ABI class: X.Org ANSI C Emulation, version 0.4
[  1837.768] (II) Loading sub module "dri2"
[  1837.768] (II) LoadModule: "dri2"
[  1837.769] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[  1837.769] (II) Module dri2: vendor="X.Org Foundation"
[  1837.769]     compiled for 1.10.4, module version = 1.2.0
[  1837.769]     ABI class: X.Org Server Extension, version 5.0
[  1837.769] (II) UnloadModule: "vesa"
[  1837.769] (II) Unloading vesa
[  1837.769] (II) UnloadModule: "fbdev"
[  1837.769] (II) Unloading fbdev
[  1837.769] (II) UnloadModule: "fbdevhw"
[  1837.769] (II) Unloading fbdevhw
[  1837.769] (==) Depth 24 pixmap format is 32 bpp
[  1837.769] (II) intel(0): [DRI2] Setup complete
[  1837.769] (II) intel(0): [DRI2]   DRI driver: i965
[  1837.769] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[  1837.779] (II) UXA(0): Driver registered support for the following operations:
[  1837.779] (II)         solid
[  1837.779] (II)         copy
[  1837.779] (II)         composite (RENDER acceleration)
[  1837.779] (II)         put_image
[  1837.779] (II)         get_image
[  1837.779] (==) intel(0): Backing store disabled
[  1837.779] (==) intel(0): Silken mouse enabled
[  1837.779] (II) intel(0): Initializing HW Cursor
[  1838.143] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  1838.150] (==) intel(0): DPMS enabled
[  1838.150] (==) intel(0): Intel XvMC decoder enabled
[  1838.150] (II) intel(0): Set up textured video
[  1838.150] (II) intel(0): Set up overlay video
[  1838.150] (II) intel(0): [XvMC] i965_xvmc driver initialized.
[  1838.150] (II) intel(0): direct rendering: DRI2 Enabled
[  1838.150] (==) intel(0): hotplug detection: "enabled"
[  1838.150] (--) RandR disabled
[  1838.150] (II) Initializing built-in extension Generic Event Extension
[  1838.150] (II) Initializing built-in extension SHAPE
[  1838.150] (II) Initializing built-in extension MIT-SHM
[  1838.150] (II) Initializing built-in extension XInputExtension
[  1838.150] (II) Initializing built-in extension XTEST
[  1838.150] (II) Initializing built-in extension BIG-REQUESTS
[  1838.150] (II) Initializing built-in extension SYNC
[  1838.150] (II) Initializing built-in extension XKEYBOARD
[  1838.151] (II) Initializing built-in extension XC-MISC
[  1838.151] (II) Initializing built-in extension SECURITY
[  1838.151] (II) Initializing built-in extension XINERAMA
[  1838.151] (II) Initializing built-in extension XFIXES
[  1838.151] (II) Initializing built-in extension RENDER
[  1838.151] (II) Initializing built-in extension RANDR
[  1838.151] (II) Initializing built-in extension COMPOSITE
[  1838.151] (II) Initializing built-in extension DAMAGE
[  1838.151] (II) Initializing built-in extension GESTURE
[  1838.174] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/i965_dri.so
[  1838.177] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[  1838.177] (II) AIGLX: enabled GLX_INTEL_swap_event
[  1838.177] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[  1838.177] (II) AIGLX: enabled GLX_SGI_make_current_read
[  1838.177] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[  1838.177] (II) AIGLX: Loaded and initialized i965
[  1838.177] (II) GLX: Initialized DRI2 GL provider for screen 0
[  1838.178] (II) intel(0): Setting screen physical size to 270 x 203
[  1838.196] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[  1838.212] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[  1838.212] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[  1838.212] (II) LoadModule: "evdev"
[  1838.213] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1838.213] (II) Module evdev: vendor="X.Org Foundation"
[  1838.213]     compiled for 1.10.2, module version = 2.6.0
[  1838.213]     Module class: X.Org XInput Driver
[  1838.213]     ABI class: X.Org XInput driver, version 12.3
[  1838.213] (II) Using input driver 'evdev' for 'Power Button'
[  1838.213] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1838.213] (**) Power Button: always reports core events
[  1838.213] (**) Power Button: Device: "/dev/input/event2"
[  1838.213] (--) Power Button: Found keys
[  1838.213] (II) Power Button: Configuring as keyboard
[  1838.213] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[  1838.213] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[  1838.213] (**) Option "xkb_rules" "evdev"
[  1838.214] (**) Option "xkb_model" "pc105"
[  1838.214] (**) Option "xkb_layout" "it"
[  1838.217] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[  1838.218] (II) config/udev: Adding input device Video Bus (/dev/input/event9)
[  1838.218] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[  1838.218] (II) Using input driver 'evdev' for 'Video Bus'
[  1838.218] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1838.218] (**) Video Bus: always reports core events
[  1838.218] (**) Video Bus: Device: "/dev/input/event9"
[  1838.218] (--) Video Bus: Found keys
[  1838.218] (II) Video Bus: Configuring as keyboard
[  1838.218] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input9/event9"
[  1838.218] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[  1838.218] (**) Option "xkb_rules" "evdev"
[  1838.218] (**) Option "xkb_model" "pc105"
[  1838.218] (**) Option "xkb_layout" "it"
[  1838.232] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[  1838.232] (II) No input driver/identifier specified (ignoring)
[  1838.232] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[  1838.232] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[  1838.232] (II) Using input driver 'evdev' for 'Sleep Button'
[  1838.232] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1838.232] (**) Sleep Button: always reports core events
[  1838.232] (**) Sleep Button: Device: "/dev/input/event0"
[  1838.232] (--) Sleep Button: Found keys
[  1838.232] (II) Sleep Button: Configuring as keyboard
[  1838.232] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0/event0"
[  1838.232] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD)
[  1838.232] (**) Option "xkb_rules" "evdev"
[  1838.232] (**) Option "xkb_model" "pc105"
[  1838.232] (**) Option "xkb_layout" "it"
[  1838.235] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event10)
[  1838.235] (II) No input driver/identifier specified (ignoring)
[  1838.238] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[  1838.238] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  1838.238] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  1838.238] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1838.238] (**) Logitech USB Receiver: always reports core events
[  1838.238] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[  1838.238] (--) Logitech USB Receiver: Found keys
[  1838.238] (II) Logitech USB Receiver: Configuring as keyboard
[  1838.238] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input4/event4"
[  1838.238] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  1838.238] (**) Option "xkb_rules" "evdev"
[  1838.238] (**) Option "xkb_model" "pc105"
[  1838.238] (**) Option "xkb_layout" "it"
[  1838.239] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event5)
[  1838.239] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[  1838.239] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[  1838.239] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[  1838.239] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1838.239] (**) Logitech USB Receiver: always reports core events
[  1838.239] (**) Logitech USB Receiver: Device: "/dev/input/event5"
[  1838.239] (--) Logitech USB Receiver: Found 20 mouse buttons
[  1838.239] (--) Logitech USB Receiver: Found scroll wheel(s)
[  1838.239] (--) Logitech USB Receiver: Found relative axes
[  1838.239] (--) Logitech USB Receiver: Found x and y relative axes
[  1838.239] (--) Logitech USB Receiver: Found absolute axes
[  1838.239] (II) evdev-grail: failed to open grail, no gesture support
[  1838.239] (--) Logitech USB Receiver: Found keys
[  1838.239] (II) Logitech USB Receiver: Configuring as mouse
[  1838.239] (II) Logitech USB Receiver: Configuring as keyboard
[  1838.239] (II) Logitech USB Receiver: Adding scrollwheel support
[  1838.239] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[  1838.239] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[  1838.239] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.1/input/input5/event5"
[  1838.240] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[  1838.240] (**) Option "xkb_rules" "evdev"
[  1838.240] (**) Option "xkb_model" "pc105"
[  1838.240] (**) Option "xkb_layout" "it"
[  1838.240] (II) Logitech USB Receiver: initialized for relative axes.
[  1838.240] (WW) Logitech USB Receiver: ignoring absolute axes.
[  1838.240] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[  1838.240] (**) Logitech USB Receiver: (accel) acceleration profile 0
[  1838.240] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[  1838.240] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[  1838.240] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[  1838.240] (II) No input driver/identifier specified (ignoring)
[  1838.242] (II) config/udev: Adding input device USB2.0 1.3M UVC WebCam (/dev/input/event7)
[  1838.242] (**) USB2.0 1.3M UVC WebCam: Applying InputClass "evdev keyboard catchall"
[  1838.242] (II) Using input driver 'evdev' for 'USB2.0 1.3M UVC WebCam'
[  1838.242] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1838.242] (**) USB2.0 1.3M UVC WebCam: always reports core events
[  1838.242] (**) USB2.0 1.3M UVC WebCam: Device: "/dev/input/event7"
[  1838.242] (--) USB2.0 1.3M UVC WebCam: Found keys
[  1838.242] (II) USB2.0 1.3M UVC WebCam: Configuring as keyboard
[  1838.242] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.0/input/input7/event7"
[  1838.242] (II) XINPUT: Adding extended input device "USB2.0 1.3M UVC WebCam" (type: KEYBOARD)
[  1838.242] (**) Option "xkb_rules" "evdev"
[  1838.242] (**) Option "xkb_model" "pc105"
[  1838.242] (**) Option "xkb_layout" "it"
[  1838.247] (II) config/udev: Adding input device Asus Laptop extra buttons (/dev/input/event6)
[  1838.247] (**) Asus Laptop extra buttons: Applying InputClass "evdev keyboard catchall"
[  1838.247] (II) Using input driver 'evdev' for 'Asus Laptop extra buttons'
[  1838.247] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1838.247] (**) Asus Laptop extra buttons: always reports core events
[  1838.247] (**) Asus Laptop extra buttons: Device: "/dev/input/event6"
[  1838.247] (--) Asus Laptop extra buttons: Found keys
[  1838.247] (II) Asus Laptop extra buttons: Configuring as keyboard
[  1838.247] (**) Option "config_info" "udev:/sys/devices/platform/asus_laptop/input/input6/event6"
[  1838.247] (II) XINPUT: Adding extended input device "Asus Laptop extra buttons" (type: KEYBOARD)
[  1838.247] (**) Option "xkb_rules" "evdev"
[  1838.247] (**) Option "xkb_model" "pc105"
[  1838.247] (**) Option "xkb_layout" "it"
[  1838.248] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  1838.248] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[  1838.248] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[  1838.248] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[  1838.248] (**) AT Translated Set 2 keyboard: always reports core events
[  1838.248] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[  1838.248] (--) AT Translated Set 2 keyboard: Found keys
[  1838.248] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[  1838.248] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  1838.248] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[  1838.248] (**) Option "xkb_rules" "evdev"
[  1838.248] (**) Option "xkb_model" "pc105"
[  1838.248] (**) Option "xkb_layout" "it"
[  1838.249] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event8)
[  1838.249] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[  1838.249] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[  1838.249] (II) LoadModule: "synaptics"
[  1838.249] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1838.249] (II) Module synaptics: vendor="X.Org Foundation"
[  1838.249]     compiled for 1.10.4, module version = 1.4.1
[  1838.249]     Module class: X.Org XInput Driver
[  1838.249]     ABI class: X.Org XInput driver, version 12.3
[  1838.249] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[  1838.249] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[  1838.249] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1838.249] (**) Option "Device" "/dev/input/event8"
[  1838.284] (--) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
[  1838.284] (--) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
[  1838.284] (--) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[  1838.284] (--) SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[  1838.284] (--) SynPS/2 Synaptics TouchPad: buttons: left right double triple
[  1838.320] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  1838.320] (**) SynPS/2 Synaptics TouchPad: always reports core events
[  1838.352] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input8/event8"
[  1838.352] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[  1838.352] (**) SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[  1838.352] (**) SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[  1838.352] (**) SynPS/2 Synaptics TouchPad: AccelFactor is now 0.040
[  1838.352] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[  1838.352] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[  1838.352] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[  1838.352] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[  1838.352] (II) SynPS/2 Synaptics TouchPad: failed to open grail, no gesture support
[  1838.352] (--) SynPS/2 Synaptics TouchPad: touchpad found
[  1838.352] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[  1838.352] (II) No input driver/identifier specified (ignoring)
[  1838.547] (II) intel(0): EDID vendor "APP", prod id 40030
[  1838.547] (II) intel(0): Printing DDC gathered Modelines:
[  1838.547] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1838.749] (II) intel(0): EDID vendor "APP", prod id 40030
[  1838.749] (II) intel(0): Printing DDC gathered Modelines:
[  1838.749] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1839.001] (II) intel(0): EDID vendor "APP", prod id 40030
[  1839.001] (II) intel(0): Printing DDC gathered Modelines:
[  1839.001] (II) intel(0): Modeline "1280x800"x0.0   71.00  1280 1328 1360 1440  800 803 809 823 -hsync -vsync (49.3 kHz)
[  1851.452] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1851.453] (II) UnloadModule: "synaptics"
[  1851.453] (II) Unloading synaptics
[  1851.453] (II) AT Translated Set 2 keyboard: Close
[  1851.453] (II) UnloadModule: "evdev"
[  1851.453] (II) Unloading evdev
[  1851.453] (II) Asus Laptop extra buttons: Close
[  1851.453] (II) UnloadModule: "evdev"
[  1851.453] (II) Unloading evdev
[  1851.454] (II) USB2.0 1.3M UVC WebCam: Close
[  1851.454] (II) UnloadModule: "evdev"
[  1851.454] (II) Unloading evdev
[  1851.454] (II) Logitech USB Receiver: Close
[  1851.454] (II) UnloadModule: "evdev"
[  1851.454] (II) Unloading evdev
[  1851.454] (II) Logitech USB Receiver: Close
[  1851.454] (II) UnloadModule: "evdev"
[  1851.454] (II) Unloading evdev
[  1851.454] (II) Sleep Button: Close
[  1851.454] (II) UnloadModule: "evdev"
[  1851.454] (II) Unloading evdev
[  1851.454] (II) Video Bus: Close
[  1851.454] (II) UnloadModule: "evdev"
[  1851.454] (II) Unloading evdev
[  1851.454] (II) Power Button: Close
[  1851.454] (II) UnloadModule: "evdev"
[  1851.454] (II) Unloading evdev
[  1851.477]  ddxSigGiveUp: Closing log
**********

---

