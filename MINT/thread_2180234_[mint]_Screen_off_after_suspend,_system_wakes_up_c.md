---
title: "[mint] Screen off after suspend, system wakes up correctly"
date: 2013-10-12
forum: MINT
---

### Post by wojtasekskorcz on 2013-10-12
Hello!
This is a post I originally posted on Linux Mint forums ([here]("http://forums.linuxmint.com/viewtopic.php?f=49&t=147242")), as this is the distribution I'm using now. As I didn't get too much of a response there and the issue is quite low-level (I presume, distro independent), I thought I should try here. Hope you'll bear with me and I'll be most grateful for any help!

So, here's the post:

I have problem when suspending (or hibernating) my Mint 14. My laptop is MSI GE600, with i5 430m processor (with integrated Intel graphics card on it) and ATI graphics card (which I disabled in BIOS). Suspending the laptop works fine, the problem occurs when I want to resume from suspend. The whole machine resumes, but the screen remains turned off (no backlight). I can blindly operate on the machine after suspend, execute commands, etc. I tried various solutions found on google, but nothing seems to work.


Could you help me? I think it's a blessing in disguise that my computer is operative after resume, only I can't see anything. Maybe this would help tracing the issue, dumping some logs, just tell me what I should check to debug it. Here are some specs:


```
$ uname -a
Linux msi 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```


```
$ inxi -G
Graphics:  Card: Intel Core Processor Integrated Graphics Controller 
           X.Org: 1.13.0 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.0hz 
           GLX Renderer: Mesa DRI Intel Ironlake Mobile GLX Version: 2.1 Mesa 9.0.3
```


```
$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=d518b4b3-e57c-42bd-abbd-040a3df080dd
```


```
$ cat /etc/fstab | grep swap
UUID=d518b4b3-e57c-42bd-abbd-040a3df080dd swap swap sw 0 0
```


As I said before, I only have the integrated graphics card enabled in BIOS. With such configuration, suspend also doesn't work on Windows, the effect is exactly the same as on Linux. Oddly, when I turn on switchable graphics in BIOS and then suspend on Windows, it resumes properly. I can't use switchable graphics on Mint though, always had problems with that. Actually, I really like keeping my ATI card disabled in BIOS.


**EDIT**
One more thing I thought of:
```
$ cat /var/log/pm-suspend.log | grep Fail
Having NetworkManager put all interaces to sleep...Failed.
Having NetworkManager wake interfaces back up...Failed.
Having NetworkManager put all interaces to sleep...Failed.
Having NetworkManager wake interfaces back up...Failed.
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Having NetworkManager wake interfaces back up...Failed.
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Having NetworkManager wake interfaces back up...Failed.
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Having NetworkManager wake interfaces back up...Failed.
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Having NetworkManager wake interfaces back up...Failed.
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Having NetworkManager wake interfaces back up...Failed.
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Having NetworkManager wake interfaces back up...Failed.
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Having NetworkManager wake interfaces back up...Failed.
Having NetworkManager put all interaces to sleep...Failed.
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory
Having NetworkManager wake interfaces back up...Failed.
```


**EDIT2**
I've just tried a solution with setting "nomodeset" kernel parameter and my screen is brought back to life after suspend! Problem is, using this parameter I can't use the graphical interface. The message I get from Xorg is (logs from "/var/log/Xorg.0.log"):
```
[    37.750] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    37.750] X Protocol Version 11, Revision 0
[    37.750] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[    37.750] Current Operating System: Linux msi 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64
[    37.750] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-17-generic root=UUID=783bf0dc-94c6-4d01-ac3a-8a69ce19e0fa ro resume=UUID=d518b4b3-e57c-42bd-abbd-040a3df080dd quiet splash nomodeset vt.handoff=7
[    37.750] Build Date: 11 April 2013  12:53:36PM
[    37.750] xorg-server 2:1.13.0-0ubuntu6.2 (For technical support please see http://www.ubuntu.com/support) 
[    37.750] Current version of pixman: 0.26.0
[    37.750]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    37.750] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    37.750] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 11 15:53:32 2013
[    37.750] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    37.750] (==) No Layout section.  Using the first Screen section.
[    37.750] (==) No screen section available. Using defaults.
[    37.750] (**) |-->Screen "Default Screen Section" (0)
[    37.750] (**) |   |-->Monitor "<default monitor>"
[    37.750] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    37.751] (==) Automatically adding devices
[    37.751] (==) Automatically enabling devices
[    37.751] (==) Automatically adding GPU devices
[    37.751] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    37.751]     Entry deleted from font path.
[    37.751] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    37.751]     Entry deleted from font path.
[    37.751] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    37.751]     Entry deleted from font path.
[    37.751] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    37.751]     Entry deleted from font path.
[    37.751] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    37.751]     Entry deleted from font path.
[    37.751] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    37.751]     Entry deleted from font path.
[    37.751] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    37.751] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    37.751] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    37.751] (II) Loader magic: 0x7fdb92fe2c40
[    37.751] (II) Module ABI versions:
[    37.751]     X.Org ANSI C Emulation: 0.4
[    37.751]     X.Org Video Driver: 13.0
[    37.751]     X.Org XInput driver : 18.0
[    37.751]     X.Org Server Extension : 7.0
[    37.751] (II) config/udev: Adding drm device (/dev/dri/card0)
[    37.752] (--) PCI:*(0:0:2:0) 8086:0046:1462:1037 rev 18, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x0000e080/8
[    37.752] (II) Open ACPI successful (/var/run/acpid.socket)
[    37.752] Initializing built-in extension Generic Event Extension
[    37.752] Initializing built-in extension SHAPE
[    37.752] Initializing built-in extension MIT-SHM
[    37.752] Initializing built-in extension XInputExtension
[    37.752] Initializing built-in extension XTEST
[    37.752] Initializing built-in extension BIG-REQUESTS
[    37.752] Initializing built-in extension SYNC
[    37.752] Initializing built-in extension XKEYBOARD
[    37.752] Initializing built-in extension XC-MISC
[    37.752] Initializing built-in extension SECURITY
[    37.752] Initializing built-in extension XINERAMA
[    37.752] Initializing built-in extension XFIXES
[    37.752] Initializing built-in extension RENDER
[    37.752] Initializing built-in extension RANDR
[    37.752] Initializing built-in extension COMPOSITE
[    37.752] Initializing built-in extension DAMAGE
[    37.752] Initializing built-in extension MIT-SCREEN-SAVER
[    37.752] Initializing built-in extension DOUBLE-BUFFER
[    37.752] Initializing built-in extension RECORD
[    37.752] Initializing built-in extension DPMS
[    37.752] Initializing built-in extension X-Resource
[    37.752] Initializing built-in extension XVideo
[    37.752] Initializing built-in extension XVideo-MotionCompensation
[    37.752] Initializing built-in extension XFree86-VidModeExtension
[    37.752] Initializing built-in extension XFree86-DGA
[    37.752] Initializing built-in extension XFree86-DRI
[    37.752] Initializing built-in extension DRI2
[    37.752] (II) LoadModule: "glx"
[    37.753] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    37.753] (II) Module glx: vendor="X.Org Foundation"
[    37.753]     compiled for 1.13.0, module version = 1.0.0
[    37.753]     ABI class: X.Org Server Extension, version 7.0
[    37.753] (==) AIGLX enabled
[    37.753] Loading extension GLX
[    37.753] (==) Matched intel as autoconfigured driver 0
[    37.753] (==) Matched intel as autoconfigured driver 1
[    37.753] (==) Matched vesa as autoconfigured driver 2
[    37.753] (==) Matched modesetting as autoconfigured driver 3
[    37.753] (==) Matched fbdev as autoconfigured driver 4
[    37.753] (==) Assigned the driver to the xf86ConfigLayout
[    37.753] (II) LoadModule: "intel"
[    37.753] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    37.753] (II) Module intel: vendor="X.Org Foundation"
[    37.753]     compiled for 1.13.0, module version = 2.20.9
[    37.753]     Module class: X.Org Video Driver
[    37.753]     ABI class: X.Org Video Driver, version 13.0
[    37.753] (II) LoadModule: "vesa"
[    37.753] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    37.753] (II) Module vesa: vendor="X.Org Foundation"
[    37.753]     compiled for 1.12.99.902, module version = 2.3.2
[    37.753]     Module class: X.Org Video Driver
[    37.753]     ABI class: X.Org Video Driver, version 13.0
[    37.753] (II) LoadModule: "modesetting"
[    37.754] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    37.754] (II) Module modesetting: vendor="X.Org Foundation"
[    37.754]     compiled for 1.13.0, module version = 0.5.0
[    37.754]     Module class: X.Org Video Driver
[    37.754]     ABI class: X.Org Video Driver, version 13.0
[    37.754] (II) LoadModule: "fbdev"
[    37.754] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    37.754] (II) Module fbdev: vendor="X.Org Foundation"
[    37.754]     compiled for 1.12.99.902, module version = 0.4.3
[    37.754]     Module class: X.Org Video Driver
[    37.754]     ABI class: X.Org Video Driver, version 13.0
[    37.754] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
    965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
    4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
    Sandybridge Desktop (GT1), Sandybridge Desktop (GT2),
    Sandybridge Desktop (GT2+), Sandybridge Mobile (GT1),
    Sandybridge Mobile (GT2), Sandybridge Mobile (GT2+),
    Sandybridge Server, Ivybridge Mobile (GT1), Ivybridge Mobile (GT2),
    Ivybridge Desktop (GT1), Ivybridge Desktop (GT2), Ivybridge Server,
    Ivybridge Server (GT2), Haswell Desktop (GT1), Haswell Desktop (GT2),
    Haswell Desktop (GT2+), Haswell Mobile (GT1), Haswell Mobile (GT2),
    Haswell Mobile (GT2+), Haswell Server (GT1), Haswell Server (GT2),
    Haswell Server (GT2+), Haswell SDV Desktop (GT1),
    Haswell SDV Desktop (GT2), Haswell SDV Desktop (GT2+),
    Haswell SDV Mobile (GT1), Haswell SDV Mobile (GT2),
    Haswell SDV Mobile (GT2+), Haswell SDV Server (GT1),
    Haswell SDV Server (GT2), Haswell SDV Server (GT2+),
    Haswell ULT Desktop (GT1), Haswell ULT Desktop (GT2),
    Haswell ULT Desktop (GT2+), Haswell ULT Mobile (GT1),
    Haswell ULT Mobile (GT2), Haswell ULT Mobile (GT2+),
    Haswell ULT Server (GT1), Haswell ULT Server (GT2),
    Haswell ULT Server (GT2+), Haswell CRW Desktop (GT1),
    Haswell CRW Desktop (GT2), Haswell CRW Desktop (GT2+),
    Haswell CRW Mobile (GT1), Haswell CRW Mobile (GT2),
    Haswell CRW Mobile (GT2+), Haswell CRW Server (GT1),
    Haswell CRW Server (GT2), Haswell CRW Server (GT2+),
    ValleyView PO board
[    37.754] (II) VESA: driver for VESA chipsets: vesa
[    37.754] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    37.754] (II) FBDEV: driver for framebuffer: fbdev
[    37.754] (++) using VT number 7


[    37.757] (II) intel(0): using device path '/dev/dri/card0'
[    37.757] (WW) Falling back to old probe method for vesa
[    37.757] (WW) Falling back to old probe method for modesetting
[    37.757] (WW) Falling back to old probe method for fbdev
[    37.757] (II) Loading sub module "fbdevhw"
[    37.757] (II) LoadModule: "fbdevhw"
[    37.757] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    37.757] (II) Module fbdevhw: vendor="X.Org Foundation"
[    37.757]     compiled for 1.13.0, module version = 0.0.2
[    37.757]     ABI class: X.Org Video Driver, version 13.0
[    37.757] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    37.757] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    37.757] (==) intel(0): RGB weight 888
[    37.757] (==) intel(0): Default visual is TrueColor
[    37.757] (--) intel(0): Integrated Graphics Chipset: Intel(R) Arrandale
[    37.757] (**) intel(0): Relaxed fencing enabled
[    37.757] (**) intel(0): Wait on SwapBuffers? enabled
[    37.757] (**) intel(0): Triple buffering? enabled
[    37.757] (**) intel(0): Framebuffer tiled
[    37.757] (**) intel(0): Pixmaps tiled
[    37.757] (**) intel(0): 3D buffers tiled
[    37.757] (**) intel(0): SwapBuffers wait enabled
[    37.757] (==) intel(0): video overlay key set to 0x101fe
[    37.757] (EE) intel(0): failed to get resources: Invalid argument
[    37.757] (II) UnloadModule: "intel"
[    37.757] (EE) Screen(s) found, but none have a usable configuration.
[    37.757] 
Fatal server error:
[    37.757] no screens found
[    37.757] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[    37.757] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    37.757] (EE) 
[    37.761] Server terminated with error (1). Closing log file.
```


**EDIT3**
I've tried using a newer kernel, but no luck here either, the symptoms are the same:
```
$ uname -a
Linux msi 3.11.4-031104-generic #201310081221 SMP Tue Oct 8 16:21:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```


I also tried manually turning off the screen before suspending and turning it on again after resume, but it also doesn't work. Before I suspend I can turn the screen on/off properly. After suspending it's constantly blank (no backlight) and I can't do anything about it.


```
 // screen working properly after boot
$ xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 353mm x 198mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


$ xrandr --output LVDS1 --off
$ xrandr -q
Screen 0: minimum 320 x 200, current 320 x 200, maximum 8192 x 8192
LVDS1 connected (normal left inverted right x axis y axis)
   1366x768       60.0 +
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


// screen is relit, everything works fine
$ xrandr --output LVDS1 --auto
$ xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 353mm x 198mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


$ sudo pm-suspend
// trying to resume here, the system wakes up, screen is blank


$ xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 353mm x 198mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)


$ xrandr --output LVDS1 --auto
// screen still blank
$ xrandr -q
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 353mm x 198mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
```

**EDIT4**
I followed the [instructions]("https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen#Problem:__Black_screen_after_resume") on Ubuntu Wiki regarding this issue and here are the results. Seems that RRScreenChangeNotify was sent when resuming, but the screen is still blank. Could it be gnome-settings-daemon bug, as is suggested on the wiki?


```
001:<:07f9: 24: Request(20): GetProperty delete=true(0x01) window=0x00c0000c property=0x147("UTF8_STRING") type=any(0x0) long-offset=0x00000000 long-length=0x1fffffff
001:>:07f9: Event PropertyNotify(28) window=0x00c0000c atom=0x147("UTF8_STRING") time=0x0042b9fe state=Deleted(0x01)
001:>:07f9:52: Reply to GetProperty: type=0x147("UTF8_STRING") bytes-after=0x00000000 data=0x52,0x52,0x53,0x63,0x72,0x65,0x65,0x6e,0x43,0x68,0x61,0x6e,0x67,0x65,0x4e,0x6f,0x74,0x69,0x66,0x79;
001:<:07fa: 24: Request(20): GetProperty delete=true(0x01) window=0x00c0000c property=0x225(unrecognized atom) type=any(0x0) long-offset=0x00000000 long-length=0x1fffffff
001:>:07fa: Event PropertyNotify(28) window=0x00c0000c atom=0x225(unrecognized atom) time=0x0042b9fe state=Deleted(0x01)
001:>:07fa:52: Reply to GetProperty: type=0x225(unrecognized atom) bytes-after=0x00000000 data=0x52,0x52,0x53,0x63,0x72,0x65,0x65,0x6e,0x43,0x68,0x61,0x6e,0x67,0x65,0x4e,0x6f,0x74,0x69,0x66,0x79;
001:<:07fb: 24: Request(20): GetProperty delete=true(0x01) window=0x00c0000c property=0x1f("STRING") type=any(0x0) long-offset=0x00000000 long-length=0x1fffffff
001:>:07fb: Event PropertyNotify(28) window=0x00c0000c atom=0x1f("STRING") time=0x0042b9fe state=Deleted(0x01)
001:>:07fb:52: Reply to GetProperty: type=0x1f("STRING") bytes-after=0x00000000 data='RRScreenChangeNotify'
001:<:07fc: 24: Request(20): GetProperty delete=true(0x01) window=0x00c0000c property=0x224(unrecognized atom) type=any(0x0) long-offset=0x00000000 long-length=0x1fffffff
001:>:07fc: Event PropertyNotify(28) window=0x00c0000c atom=0x224(unrecognized atom) time=0x0042b9fe state=Deleted(0x01)
001:>:07fc:52: Reply to GetProperty: type=0x224(unrecognized atom) bytes-after=0x00000000 data=0x52,0x52,0x53,0x63,0x72,0x65,0x65,0x6e,0x43,0x68,0x61,0x6e,0x67,0x65,0x4e,0x6f,0x74,0x69,0x66,0x79;
001:<:07fd: 24: Request(20): GetProperty delete=true(0x01) window=0x00c0000c property=0x1a8("SAVE_TARGETS") type=any(0x0) long-offset=0x00000000 long-length=0x1fffffff
001:>:07fd: Event PropertyNotify(28) window=0x00c0000c atom=0x1a8("SAVE_TARGETS") time=0x0042b9ff state=Deleted(0x01)
001:>:07fd:32: Reply to GetProperty: type=0x1a7("NULL") bytes-after=0x00000000 data=;
001:<:07fe: 24: Request(20): GetProperty delete=true(0x01) window=0x00c0000c property=0x1aa("TIMESTAMP") type=any(0x0) long-offset=0x00000000 long-length=0x1fffffff
001:>:07fe: Event PropertyNotify(28) window=0x00c0000c atom=0x1aa("TIMESTAMP") time=0x0042b9ff state=Deleted(0x01)
001:>:07fe:36: Reply to GetProperty: type=0x13("INTEGER") bytes-after=0x00000000 data=0x0041c6f5;
001:<:07ff: 16: Request(22): SetSelectionOwner owner=0x00c0000c selection=0x1a1("CLIPBOARD") time=0x0042b9c9
001:<:0800: 28: Request(18): ChangeProperty mode=Replace(0x00) window=0x036000f9 property=0x217(unrecognized atom) type=0x4("ATOM") data=0x1a7("NULL");
001:<:0801: 44: Request(25): SendEvent propagate=false(0x00) destination=0x036000f9 event-mask=0
```

---

### Post by Elfy on 2013-10-12
*Thread moved to **Other OS/Distro Support**.*

---

### Post by Toz on 2013-10-12
Perhaps your backlight interface is turned down and just needs to be manually turned up. What does the following command return:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
...it would be helpful if you could get the results of that command before and after a suspend attempt. To do so, (as root) create the file **/etc/pm/sleep.d/backlight** with the following content:
```
#!/bin/bash
case $1 in
   suspend|hibernate)
      for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done;;
   resume|thaw)
      for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done;;
esac
```
...and make the file executable. Once you've recovered your system, post back the full contents of /var/log/pm-suspend.log.



You might also want to look at trying some quirks. To test them, you would manually initiate a suspend and pass a quirk like:
```
sudo pm-suspend --quirk-dpms-on
```
From **man pm-suspend**, these quirks are available:
```
       --quirk-dpms-on
           This option forces the video hardware to turn on the screen during
           resume. Most video adapters turn on the screen themselves, but if
           you get a blank screen on resume that can be turned back on by
           moving the mouse or typing then this option may be useful.

       --quirk-dpms-suspend
           This option forces the video hardware to turn off the screen when
           suspending. Most video adapters seem to do this correctly, but some
           do not, which wastes lots of power. If your screen is still on
           after successfully suspending you may need to use this option.

       --quirk-radeon-off
           This option forces Radeon hardware to turn off the display during
           suspend and turn it back on during resume. You only need to do this
           on some old ThinkPads of the '30 series (T30, X31, R32,... ) with
           Radeon video hardware.

       --quirk-s3-bios
           This option calls the video BIOS during S3 resume. Unfortunately,
           it is not always allowed to call the video BIOS at this point, so
           sometimes adding this option can actually break resume on some
           systems.

       --quirk-s3-mode
           This option initializes the video card into a VGA text mode, and
           then uses the BIOS to set the video mode. On some systems S3 BIOS
           only initializes the video BIOS to text mode, and so both S3 BIOS
           and S3 MODE are needed.

       --quirk-vbe-post
           This option will attempt to reinitialize the video card when
           resuming from suspend, using the same code the system BIOS uses at
           boot in order to initialize the video hardware. Not all video cards
           need this, and using this option on systems where it is not needed
           can cause a system to lock up when resuming.

       --quirk-vbemode-restore
           This option will save and restore the current VESA mode which may
           be necessary to avoid X screen corruption. Using this feature on
           Intel graphics hardware is probably a bad idea.

       --quirk-vbestate-restore
           This option saves and restores some low level hardware state which
           may be invalid after suspend.

       --quirk-vga-mode-3
           This option will try to force the video card into a standard text
           mode on resume.

       --quirk-save-pci
           Save the PCI config space for the VGA card.

```
...the ones with the most potential would be:
--quirk-dpms-on
 --quirk-s3-bios
--quirk-vbe-post
--quirk-vbestate-restore

---

### Post by wojtasekskorcz on 2013-10-12
Toz, thank you for your reply! Here are the details you asked for:

```
$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
0
0
8
```

Logs after creating the script in /etc/pm/sleep.d/backlight:

```
$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Sat Oct 12 16:23:02 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux msi 3.11.4-031104-generic #201310081221 SMP Tue Oct 8 16:21:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320461  3 vboxpci,vboxnetadp,vboxnetflt
vsock                  35045  0 
bnep                   23966  2 
rfcomm                 74589  0 
bluetooth             391564  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17711  0 
joydev                 17613  0 
uvcvideo               82247  0 
videobuf2_core         40785  1 uvcvideo
videodev              138443  2 uvcvideo,videobuf2_core
arc4                   12573  2 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
iwldvm                244436  0 
mac80211              619109  1 iwldvm
snd_hda_codec_hdmi     41736  1 
snd_hda_codec_realtek    56305  1 
snd_hda_intel          53038  5 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
psmouse               104064  0 
iwlwifi               171131  1 iwldvm
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
i915                  682899  9 
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
msi_wmi                13354  0 
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13413  0 
sparse_keymap          13890  1 msi_wmi
cfg80211              494624  3 iwldvm,mac80211,iwlwifi
drm_kms_helper         53178  1 i915
mac_hid                13253  0 
mei_me                 18418  0 
drm                   302332  5 i915,drm_kms_helper
snd                    69657  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    78448  1 mei_me
soundcore              12680  1 snd
wmi                    19256  1 msi_wmi
intel_ips              18520  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13564  1 i915
lpc_ich                21163  0 
video                  19574  1 i915
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   105794  2 hid_generic,usbhid
ums_realtek            18336  0 
usb_storage            66567  1 ums_realtek
r8169                  73111  0 
ahci                   30063  3 
libahci                32088  1 ahci
mii                    13981  1 r8169
             total       used       free     shared    buffers     cached
Mem:       3834560    2220436    1614124          0     132764     916684
-/+ buffers/cache:    1170988    2663572
Swap:      4192252          0    4192252


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module iwlwifi...Done.


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/backlight suspend suspend:


/etc/pm/sleep.d/backlight suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Oct 12 16:23:03 CEST 2013: performing suspend
Sat Oct 12 16:23:14 CEST 2013: Awake.
Sat Oct 12 16:23:14 CEST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /etc/pm/sleep.d/backlight resume suspend:
/sys/class/backlight/acpi_video0
0
0
8


/etc/pm/sleep.d/backlight resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Oct 12 16:23:14 CEST 2013: Finished.
```

As to those quirks, I've tried many different combinations of those but none of them worked. I've spent the whole day yesterday trying to make it work.

Thank you in advance!

---

### Post by Toz on 2013-10-12
Sorry, I had a typo in the backlight script, but there may be enough information in your post. Can you try again with this version (based on the results, I've added a backlight adjustment. Let me know if the backlight returns on resume):
```
#!/bin/bash
case $1 in
   suspend|hibernate)
      for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done;;
   resume|thaw)
      for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
      echo 8 > /sys/class/backlight/acpi_video0/brightness
      ;;
esac
```

---

### Post by wojtasekskorcz on 2013-10-12
That didn't help, ufortunately. I don't know if I stated it clearly. The screen is completely off, like if you'd use 
```
$ xrandr --output LVDS1 --off
```
Do you think increasing brightness could help here? To me it seems like it has to be switched on first, but I'm not sure about that and I don't know how to do this.

New logs:
```
$ cat /var/log/pm-suspend.logInitial commandline parameters: 
Sat Oct 12 19:47:47 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux msi 3.11.4-031104-generic #201310081221 SMP Tue Oct 8 16:21:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320461  3 vboxpci,vboxnetadp,vboxnetflt
vsock                  35045  0 
bnep                   23966  2 
rfcomm                 74589  0 
bluetooth             391564  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17711  0 
uvcvideo               82247  0 
videobuf2_core         40785  1 uvcvideo
videodev              138443  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
arc4                   12573  2 
joydev                 17613  0 
iwldvm                244436  0 
mac80211              619109  1 iwldvm
snd_hda_codec_hdmi     41736  1 
snd_hda_codec_realtek    56305  1 
i915                  682899  8 
snd_hda_intel          53038  5 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
drm_kms_helper         53178  1 i915
iwlwifi               171131  1 iwldvm
drm                   302332  4 i915,drm_kms_helper
msi_wmi                13354  0 
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse               104064  0 
cfg80211              494624  3 iwldvm,mac80211,iwlwifi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13890  1 msi_wmi
serio_raw              13413  0 
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    69657  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
i2c_algo_bit           13564  1 i915
mei_me                 18418  0 
mei                    78448  1 mei_me
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
video                  19574  1 i915
mac_hid                13253  0 
lpc_ich                21163  0 
wmi                    19256  1 msi_wmi
intel_ips              18520  0 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   105794  2 hid_generic,usbhid
ahci                   30063  3 
libahci                32088  1 ahci
r8169                  73111  0 
mii                    13981  1 r8169
             total       used       free     shared    buffers     cached
Mem:       3834560    2478148    1356412          0      62244    1539000
-/+ buffers/cache:     876904    2957656
Swap:      4192252        760    4191492


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module iwlwifi...Done.


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/backlight suspend suspend:
/sys/class/backlight/acpi_video0
0
0
8


/etc/pm/sleep.d/backlight suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Oct 12 19:47:48 CEST 2013: performing suspend
Sat Oct 12 19:47:57 CEST 2013: Awake.
Sat Oct 12 19:47:57 CEST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /etc/pm/sleep.d/backlight resume suspend:
/sys/class/backlight/acpi_video0
0
0
8
/etc/pm/sleep.d/backlight: line 7: /sys/class/backlight/acpi_video0: Is a directory


/etc/pm/sleep.d/backlight resume suspend: Returned exit code 1.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
```

Thank you!

Edit: I checked on Wikipedia and noticed that I gave the topic a wrong name. It's not about backlight, it's about the lcd screen as a whole, it's completely turned off (not just backlight-turned-off). Sorry for the misunderstanding, I'm not too savvy when it comes to hardware and English is not my first language.

---

### Post by Toz on 2013-10-12
> /etc/pm/sleep.d/backlight: line 7: /sys/class/backlight/acpi_video0: Is a directory
Can you double-check the script I wrote? I think you might be missing something.

> Edit: I checked on Wikipedia and noticed that I gave the topic a wrong name. It's not about backlight, it's about the lcd screen as a whole, it's completely turned off (not just backlight-turned-off). Sorry for the misunderstanding, I'm not too savvy when it comes to hardware and English is not my first language. 
Possibly. According to the information from the script, your backlight is turned off. Lets try fixing the script to see if it fixes the problem. If not, we can look towards the screen.

---

### Post by wojtasekskorcz on 2013-10-13
You're right! I missed "/brightness" in line 7. Very weird, as I copypasted the script. New logs:

```
$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Sun Oct 13 09:09:37 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux msi 3.11.4-031104-generic #201310081221 SMP Tue Oct 8 16:21:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320461  3 vboxpci,vboxnetadp,vboxnetflt
vsock                  35045  0 
bnep                   23966  2 
rfcomm                 74589  0 
bluetooth             391564  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17711  0 
joydev                 17613  0 
snd_hda_codec_hdmi     41736  1 
snd_hda_codec_realtek    56305  1 
arc4                   12573  2 
snd_hda_intel          53038  5 
uvcvideo               82247  0 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
iwldvm                244436  0 
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              619109  1 iwldvm
i915                  682899  9 
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
videobuf2_core         40785  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
iwlwifi               171131  1 iwldvm
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         53178  1 i915
videodev              138443  2 uvcvideo,videobuf2_core
cfg80211              494624  3 iwldvm,mac80211,iwlwifi
drm                   302332  5 i915,drm_kms_helper
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
mei_me                 18418  0 
mei                    78448  1 mei_me
snd                    69657  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse               104064  0 
mac_hid                13253  0 
serio_raw              13413  0 
i2c_algo_bit           13564  1 i915
msi_wmi                13354  0 
intel_ips              18520  0 
sparse_keymap          13890  1 msi_wmi
soundcore              12680  1 snd
lpc_ich                21163  0 
wmi                    19256  1 msi_wmi
video                  19574  1 i915
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   105794  2 hid_generic,usbhid
ums_realtek            18336  0 
usb_storage            66567  1 ums_realtek
r8169                  73111  0 
mii                    13981  1 r8169
ahci                   30063  3 
libahci                32088  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3834560    2668176    1166384          0     133336     906436
-/+ buffers/cache:    1628404    2206156
Swap:      4192252          0    4192252


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module iwlwifi...Done.


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/backlight suspend suspend:
/sys/class/backlight/acpi_video0
0
0
8


/etc/pm/sleep.d/backlight suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Oct 13 09:09:38 CEST 2013: performing suspend
Sun Oct 13 09:09:48 CEST 2013: Awake.
Sun Oct 13 09:09:48 CEST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /etc/pm/sleep.d/backlight resume suspend:
/sys/class/backlight/acpi_video0
0
0
8


/etc/pm/sleep.d/backlight resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Oct 13 09:09:49 CEST 2013: Finished.
```

As to the brightness set to 0, this value is also 0 before suspending. I usually work on minimum brightness because I'm in a quite dark environment. I tried suspending from maximum brightness and it works properly. Well, according to the logs, because the screen is still off.

```
$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Sun Oct 13 09:25:28 CEST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux msi 3.11.4-031104-generic #201310081221 SMP Tue Oct 8 16:21:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320461  3 vboxpci,vboxnetadp,vboxnetflt
vsock                  35045  0 
rfcomm                 74589  0 
bnep                   23966  2 
bluetooth             391564  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17711  0 
joydev                 17613  0 
snd_hda_codec_hdmi     41736  1 
snd_hda_codec_realtek    56305  1 
snd_hda_intel          53038  5 
arc4                   12573  2 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
uvcvideo               82247  0 
i915                  682899  9 
iwldvm                244436  0 
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_core         40785  1 uvcvideo
mac80211              619109  1 iwldvm
videodev              138443  2 uvcvideo,videobuf2_core
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
drm_kms_helper         53178  1 i915
iwlwifi               171131  1 iwldvm
videobuf2_vmalloc      13216  1 uvcvideo
msi_wmi                13354  0 
videobuf2_memops       13362  1 videobuf2_vmalloc
drm                   302332  5 i915,drm_kms_helper
psmouse               104064  0 
cfg80211              494624  3 iwldvm,mac80211,iwlwifi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13890  1 msi_wmi
serio_raw              13413  0 
snd_timer              29989  2 snd_pcm,snd_seq
i2c_algo_bit           13564  1 i915
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
intel_ips              18520  0 
mei_me                 18418  0 
snd                    69657  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mei                    78448  1 mei_me
soundcore              12680  1 snd
wmi                    19256  1 msi_wmi
lpc_ich                21163  0 
video                  19574  1 i915
mac_hid                13253  0 
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   105794  2 hid_generic,usbhid
r8169                  73111  0 
mii                    13981  1 r8169
ahci                   30063  3 
libahci                32088  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3834560    2625620    1208940          0     143912     876064
-/+ buffers/cache:    1605644    2228916
Swap:      4192252          0    4192252


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module iwlwifi...Done.


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/backlight suspend suspend:
/sys/class/backlight/acpi_video0
8
8
8


/etc/pm/sleep.d/backlight suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Oct 13 09:25:28 CEST 2013: performing suspend
Sun Oct 13 09:25:52 CEST 2013: Awake.
Sun Oct 13 09:25:52 CEST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /etc/pm/sleep.d/backlight resume suspend:
/sys/class/backlight/acpi_video0
8
8
8


/etc/pm/sleep.d/backlight resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sun Oct 13 09:25:52 CEST 2013: Finished.
```

---

### Post by Toz on 2013-10-13
3 more suggestions:

1. Can you rename /etc/pm/sleep.d/backlight to /etc/pm/sleep.d/000backlight to change its order in the run. Try again and post back the logs.

2. Create a blank file called /etc/pm/sleep.d/99video. This will negate the existing built-in script. It may be interfering.

3. Try using vbetool (make sure its installed). Use the following modified /etc/pm/sleep.d/backlight script:
```
#!/bin/bash
case $1 in
   suspend|hibernate)
      ;;
   resume|thaw)
      vbetool dpms on
      ;;
esac
```
...and again, post back logs.

---

### Post by wojtasekskorcz on 2013-10-13
> **Toz said:**
> 1. Can you rename /etc/pm/sleep.d/backlight to /etc/pm/sleep.d/000backlight to change its order in the run. Try again and post back the logs.

```
$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Sun Oct 13 18:01:34 CEST 2013: Running hooks for suspend.
Running hook /etc/pm/sleep.d/000backlight suspend suspend:
/sys/class/backlight/acpi_video0
2
2
8


/etc/pm/sleep.d/000backlight suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux msi 3.11.4-031104-generic #201310081221 SMP Tue Oct 8 16:21:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320461  3 vboxpci,vboxnetadp,vboxnetflt
vsock                  35045  0 
bnep                   23966  2 
rfcomm                 74589  0 
bluetooth             391564  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17711  0 
joydev                 17613  0 
snd_hda_codec_hdmi     41736  1 
snd_hda_codec_realtek    56305  1 
arc4                   12573  2 
snd_hda_intel          53038  5 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
iwldvm                244436  0 
uvcvideo               82247  0 
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
mac80211              619109  1 iwldvm
snd_seq_midi           13324  0 
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         40785  1 uvcvideo
iwlwifi               171131  1 iwldvm
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  682899  9 
snd                    69657  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev              138443  2 uvcvideo,videobuf2_core
cfg80211              494624  3 iwldvm,mac80211,iwlwifi
soundcore              12680  1 snd
drm_kms_helper         53178  1 i915
videobuf2_vmalloc      13216  1 uvcvideo
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
drm                   302332  5 i915,drm_kms_helper
videobuf2_memops       13362  1 videobuf2_vmalloc
mei_me                 18418  0 
msi_wmi                13354  0 
mei                    78448  1 mei_me
psmouse               104064  0 
i2c_algo_bit           13564  1 i915
sparse_keymap          13890  1 msi_wmi
serio_raw              13413  0 
wmi                    19256  1 msi_wmi
video                  19574  1 i915
lpc_ich                21163  0 
mac_hid                13253  0 
intel_ips              18520  0 
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   105794  2 hid_generic,usbhid
r8169                  73111  0 
ahci                   30063  3 
mii                    13981  1 r8169
libahci                32088  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3834560    2215512    1619048          0      44308     759280
-/+ buffers/cache:    1411924    2422636
Swap:      4192252      58688    4133564


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module iwlwifi...Done.


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Oct 13 18:01:37 CEST 2013: performing suspend
Sun Oct 13 18:01:45 CEST 2013: Awake.
Sun Oct 13 18:01:45 CEST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Running hook /etc/pm/sleep.d/000backlight resume suspend:
/sys/class/backlight/acpi_video0
2
2
8


/etc/pm/sleep.d/000backlight resume suspend: success.
Sun Oct 13 18:01:47 CEST 2013: Finished.
```


> **Toz said:**
> [COLOR=#000000]2. Create a blank file called /etc/pm/sleep.d/99video. This will negate the existing built-in script. It may be interfering.[/COLOR]
I also added "chmod +x" to the file, as all the scripts in the folder are executable. Is that alright?
```
$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Sun Oct 13 18:09:37 CEST 2013: Running hooks for suspend.
Running hook /etc/pm/sleep.d/000backlight suspend suspend:
/sys/class/backlight/acpi_video0
0
0
8


/etc/pm/sleep.d/000backlight suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux msi 3.11.4-031104-generic #201310081221 SMP Tue Oct 8 16:21:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320461  3 vboxpci,vboxnetadp,vboxnetflt
vsock                  35045  0 
bnep                   23966  2 
rfcomm                 74589  0 
bluetooth             391564  10 bnep,rfcomm
parport_pc             32866  0 
ppdev                  17711  0 
joydev                 17613  0 
snd_hda_codec_hdmi     41736  1 
snd_hda_codec_realtek    56305  1 
arc4                   12573  2 
snd_hda_intel          53038  5 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
iwldvm                244436  0 
mac80211              619109  1 iwldvm
i915                  682899  9 
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               82247  0 
snd_seq_midi           13324  0 
iwlwifi               171131  1 iwldvm
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
drm_kms_helper         53178  1 i915
videobuf2_core         40785  1 uvcvideo
videodev              138443  2 uvcvideo,videobuf2_core
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
msi_wmi                13354  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
snd_timer              29989  2 snd_pcm,snd_seq
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   302332  5 i915,drm_kms_helper
psmouse               104064  0 
snd                    69657  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13413  0 
sparse_keymap          13890  1 msi_wmi
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
lpc_ich                21163  0 
cfg80211              494624  3 iwldvm,mac80211,iwlwifi
intel_ips              18520  0 
i2c_algo_bit           13564  1 i915
mei_me                 18418  0 
mei                    78448  1 mei_me
video                  19574  1 i915
mac_hid                13253  0 
wmi                    19256  1 msi_wmi
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   105794  2 hid_generic,usbhid
ahci                   30063  3 
libahci                32088  1 ahci
r8169                  73111  0 
mii                    13981  1 r8169
             total       used       free     shared    buffers     cached
Mem:       3834560    2171744    1662816          0     137612     850612
-/+ buffers/cache:    1183520    2651040
Swap:      4192252          0    4192252


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module iwlwifi...Done.


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /etc/pm/sleep.d/99video suspend suspend:


/etc/pm/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Oct 13 18:09:38 CEST 2013: performing suspend
Sun Oct 13 18:09:45 CEST 2013: Awake.
Sun Oct 13 18:09:45 CEST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /etc/pm/sleep.d/99video resume suspend:


/etc/pm/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Running hook /etc/pm/sleep.d/000backlight resume suspend:
/sys/class/backlight/acpi_video0
0
0
8


/etc/pm/sleep.d/000backlight resume suspend: success.
Sun Oct 13 18:09:46 CEST 2013: Finished.
```


> **Toz said:**
> [COLOR=#000000]3. Try using vbetool (make sure its installed). Use the following modified /etc/pm/sleep.d/backlight script:[/COLOR][COLOR=#000000]
[/COLOR]I left the name 000backlight, does it make any change?
```
$ cat /var/log/pm-suspend.log
Initial commandline parameters: 
Sun Oct 13 18:19:05 CEST 2013: Running hooks for suspend.
Running hook /etc/pm/sleep.d/000backlight suspend suspend:


/etc/pm/sleep.d/000backlight suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux msi 3.11.4-031104-generic #201310081221 SMP Tue Oct 8 16:21:57 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320461  3 vboxpci,vboxnetadp,vboxnetflt
vsock                  35045  0 
rfcomm                 74589  0 
bnep                   23966  2 
bluetooth             391564  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17711  0 
joydev                 17613  0 
snd_hda_codec_hdmi     41736  1 
snd_hda_codec_realtek    56305  1 
uvcvideo               82247  0 
arc4                   12573  2 
videobuf2_core         40785  1 uvcvideo
videodev              138443  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
iwldvm                244436  0 
snd_hda_intel          53038  5 
snd_hda_codec         194727  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
mac80211              619109  1 iwldvm
i915                  682899  9 
snd_hwdep              13613  1 snd_hda_codec
snd_pcm               107140  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
iwlwifi               171131  1 iwldvm
drm_kms_helper         53178  1 i915
snd_rawmidi            30416  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                66061  2 snd_seq_midi,snd_seq_midi_event
drm                   302332  5 i915,drm_kms_helper
psmouse               104064  0 
msi_wmi                13354  0 
snd_timer              29989  2 snd_pcm,snd_seq
lpc_ich                21163  0 
cfg80211              494624  3 iwldvm,mac80211,iwlwifi
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13890  1 msi_wmi
serio_raw              13413  0 
i2c_algo_bit           13564  1 i915
intel_ips              18520  0 
snd                    69657  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18798  2 snd_hda_intel,snd_pcm
video                  19574  1 i915
mei_me                 18418  0 
mei                    78448  1 mei_me
mac_hid                13253  0 
wmi                    19256  1 msi_wmi
lp                     17799  0 
parport                42466  3 parport_pc,ppdev,lp
hid_generic            12548  0 
usbhid                 53329  0 
hid                   105794  2 hid_generic,usbhid
r8169                  73111  0 
mii                    13981  1 r8169
ahci                   30063  3 
libahci                32088  1 ahci
             total       used       free     shared    buffers     cached
Mem:       3834560    2271516    1563044          0     145136     872808
-/+ buffers/cache:    1253572    2580988
Swap:      4192252          0    4192252


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
Unloading kernel module iwlwifi...Done.


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
Kernel modesetting video driver detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /etc/pm/sleep.d/99video suspend suspend:


/etc/pm/sleep.d/99video suspend suspend: success.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:


/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sun Oct 13 18:19:05 CEST 2013: performing suspend
Sun Oct 13 18:19:16 CEST 2013: Awake.
Sun Oct 13 18:19:16 CEST 2013: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:


/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /etc/pm/sleep.d/99video resume suspend:


/etc/pm/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.


/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Running hook /etc/pm/sleep.d/000backlight resume suspend:


/etc/pm/sleep.d/000backlight resume suspend: success.
Sun Oct 13 18:19:16 CEST 2013: Finished.
```

Generally, nothing changed. You seem quite knowledgeable in the topic, don't you think it might be a bit more low-level problem? Like BIOS not working properly? As I said, the same happens on Windows when I enable only integrated graphics (IGD in BIOS). When I have switchable graphics enabled (SG in BIOS), windows resumes without problems. Have you experienced a case where BIOS was the culprit, not kernel or system?

---

### Post by Toz on 2013-10-13
> **wojtasekskorcz said:**
> Generally, nothing changed. You seem quite knowledgeable in the topic, don't you think it might be a bit more low-level problem? Like BIOS not working properly? As I said, the same happens on Windows when I enable only integrated graphics (IGD in BIOS). When I have switchable graphics enabled (SG in BIOS), windows resumes without problems. Have you experienced a case where BIOS was the culprit, not kernel or system?

Its sure looking like it might be a lower-level problem as you indicate. And yes, there have been instances where we have not been able to resolve the issue. Do you have the latest bios version installed? 

The other thing you might want to try is to enable the ATI card in linux. Unfortunately, I don't have any experience with ATI Hybrid graphic setups, but [this link]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") (see the section on Intel/AMD hybrid graphics) and [this link]("http://askubuntu.com/questions/286253/ubuntu-13-04-amd-intel-hybrid-switchable-graphics-not-working") might provide some help.

---

### Post by wojtasekskorcz on 2013-10-13
When I enter BIOS I can read Aptio Setup Utility 2.00.1201, Copyright (C) 2009 American Megatrends, Inc. So it certainly isn't the latest version of it. I'm a bit wary though, when it comes to updating BIOS. Tried it once on my old PC and the mobo never returned to life after that :D

I managed to get ATI working on Linux once, when I had to make a project in OpenGL, but then switched back to integrated because of power consumption issues. Never have I enabled switchable graphics though, it was always either ATI or Intel. I have a fresh Ubuntu installation on a different partition now, so I can easily try that. Will report if I manage to get it working.

Post any further suggestions if some probable solution or diagnosis occurs to you. Thank you!

---

