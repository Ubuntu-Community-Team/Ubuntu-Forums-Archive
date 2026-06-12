---
title: "Install almost worked but screen resolution too high"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by Davethemaster on 2010-12-06
Hi, first post and first day of using Ubuntu 10.10. The installation went okay (to start with) on my newly formatted hard drive (after death of Windows XP), but I got an error about 3/4 of the way through. The system said something about starting the desktop to try to resolve or fault find the problem. So I now have a desktop with access to all the menu system. I am feeling my way around slowly getting used to the environment. I think there are bits missing from the install but with no frame of reference I cannot tell what exactly is wrong. 

One obvious problem is my Monitor screen resolution. In Monitor preferences it is set as 'unknown monitor'.  The detect monitor button does nothing and the resolution is set as 2048 x 1536 which is just too small to see properly on the screen. I am currently using zoom to increase within a window to use at all. I have tried opening a terminal and using the xrandr command which reports the following:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 2048 x 1536, current 2048 x 1536, maximum 2048 x 1536.
default connected 2048x1536+0+0 0mm x 0mm
   2048x1536       0.0* 

My Monitor is a LG Flatron F900P (exact model is F8910G-UL.
Do I have to reinstall the driver? If so where and how do I do this?

Many thanks for any help offered.

---

### Post by realzippy on 2010-12-06
Welcome to the Forum!!

Which resolution do you want?

*"Do I have to reinstall the driver?"*

Which driver did you install?

...can you please post your **Xorg.0.log** content?
(System/Administration/LogFileViewer)

---

### Post by Davethemaster on 2010-12-06
Thanks for the welcome and response.

Resolution on my laptop is 1280 x 800, which seems okay I guess.

Sorry just to clarify, I have not installed any drivers for my monitor (reinstall was the wrong term) as I cannot find any for my old monitor online.

Not sure if I can publish this Xorg.0.System log as it runs to 2795 lines. Or can I attach it in some way?

---

### Post by realzippy on 2010-12-06
Please run those commands

```
xrandr --newmode test 83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
```

```
xrandr --addmode default test
```

```
xrandr --output default --mode test
```

...can you post the output?

Attachments,of course,right to the smiley,paperclip symbol.

---

### Post by Davethemaster on 2010-12-07
Okay here are the results:

dave@dave-Evo-D310:~$ xrandr --newmode test 83.50 1280 1352 1480 1680 800 803 809 831 -hsync +vsync
xrandr: Failed to get size of gamma for output default
dave@dave-Evo-D310:~$ xrandr --addmode default test
xrandr: Failed to get size of gamma for output default
dave@dave-Evo-D310:~$ xrandr --output default --mode test
xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed
dave@dave-Evo-D310:~$ 

Does not look too encouraging I guess. I have also been delayed in posting by several system crashes often included with the following which always is displayed just before the desktop loads up at boot:

  	 	 	 	p { margin-bottom: 0.21cm; }  (Process: 226) :GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)


I should also mention that I have a Intel 845G chipset. Am I doomed?

---

### Post by Davethemaster on 2010-12-07
Here is that log file you asked for by the way:

[    54.680] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[    54.680] X Protocol Version 11, Revision 0
[    54.680] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[    54.680] Current Operating System: Linux dave-Evo-D310 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686
[    54.680] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=6cc7d408-4976-4406-bfc3-cee8c86b5fc4 ro quiet splash
[    54.680] Build Date: 16 September 2010  05:39:22PM
[    54.680] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    54.680] Current version of pixman: 0.18.4
[    54.680]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[    54.680] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    54.680] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec  7 21:34:32 2010
[    54.777] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    54.938] (==) No Layout section.  Using the first Screen section.
[    54.938] (==) No screen section available. Using defaults.
[    54.939] (**) |-->Screen "Default Screen Section" (0)
[    54.939] (**) |   |-->Monitor "<default monitor>"
[    54.939] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    54.939] (==) Automatically adding devices
[    54.939] (==) Automatically enabling devices
[    54.939] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    54.939]     Entry deleted from font path.
[    55.004] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    55.004] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    55.004] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    55.004] (II) Loader magic: 0x81f8e00
[    55.004] (II) Module ABI versions:
[    55.004]     X.Org ANSI C Emulation: 0.4
[    55.004]     X.Org Video Driver: 8.0
[    55.004]     X.Org XInput driver : 11.0
[    55.004]     X.Org Server Extension : 4.0
[    55.005] (--) PCI:*(0:0:2:0) 8086:2562:0e11:00c5 rev 1, Mem @ 0xf0000000/134217728, 0xfc400000/524288
[    55.005] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[    55.005] (II) LoadModule: "extmod"
[    55.043] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    55.071] (II) Module extmod: vendor="X.Org Foundation"
[    55.071]     compiled for 1.9.0, module version = 1.0.0
[    55.071]     Module class: X.Org Server Extension
[    55.071]     ABI class: X.Org Server Extension, version 4.0
[    55.071] (II) Loading extension MIT-SCREEN-SAVER
[    55.071] (II) Loading extension XFree86-VidModeExtension
[    55.071] (II) Loading extension XFree86-DGA
[    55.072] (II) Loading extension DPMS
[    55.072] (II) Loading extension XVideo
[    55.072] (II) Loading extension XVideo-MotionCompensation
[    55.072] (II) Loading extension X-Resource
[    55.072] (II) LoadModule: "dbe"
[    55.072] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    55.084] (II) Module dbe: vendor="X.Org Foundation"
[    55.084]     compiled for 1.9.0, module version = 1.0.0
[    55.084]     Module class: X.Org Server Extension
[    55.084]     ABI class: X.Org Server Extension, version 4.0
[    55.084] (II) Loading extension DOUBLE-BUFFER
[    55.084] (II) LoadModule: "glx"
[    55.085] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    55.121] (II) Module glx: vendor="X.Org Foundation"
[    55.121]     compiled for 1.9.0, module version = 1.0.0
[    55.121]     ABI class: X.Org Server Extension, version 4.0
[    55.135] (==) AIGLX enabled
[    55.135] (II) Loading extension GLX
[    55.135] (II) LoadModule: "record"
[    55.136] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    55.182] (II) Module record: vendor="X.Org Foundation"
[    55.182]     compiled for 1.9.0, module version = 1.13.0
[    55.182]     Module class: X.Org Server Extension
[    55.182]     ABI class: X.Org Server Extension, version 4.0
[    55.182] (II) Loading extension RECORD
[    55.182] (II) LoadModule: "dri"
[    55.183] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    55.201] (II) Module dri: vendor="X.Org Foundation"
[    55.201]     compiled for 1.9.0, module version = 1.0.0
[    55.201]     ABI class: X.Org Server Extension, version 4.0
[    55.201] (II) Loading extension XFree86-DRI
[    55.201] (II) LoadModule: "dri2"
[    55.202] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    55.203] (II) Module dri2: vendor="X.Org Foundation"
[    55.203]     compiled for 1.9.0, module version = 1.2.0
[    55.204]     ABI class: X.Org Server Extension, version 4.0
[    55.204] (II) Loading extension DRI2
[    55.204] (==) Matched vesa as autoconfigured driver 0
[    55.204] (==) Matched fbdev as autoconfigured driver 1
[    55.204] (==) Assigned the driver to the xf86ConfigLayout
[    55.204] (II) LoadModule: "vesa"
[    55.204] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    55.219] (II) Module vesa: vendor="X.Org Foundation"
[    55.219]     compiled for 1.8.99.905, module version = 2.3.0
[    55.219]     Module class: X.Org Video Driver
[    55.219]     ABI class: X.Org Video Driver, version 8.0
[    55.219] (II) LoadModule: "fbdev"
[    55.219] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    55.233] (II) Module fbdev: vendor="X.Org Foundation"
[    55.233]     compiled for 1.8.99.905, module version = 0.4.2
[    55.233]     ABI class: X.Org Video Driver, version 8.0
[    55.233] (II) VESA: driver for VESA chipsets: vesa
[    55.233] (II) FBDEV: driver for framebuffer: fbdev
[    55.233] (++) using VT number 7

[    55.233] (EE) VESA: Kernel modesetting driver in use, refusing to load
[    55.234] (WW) Falling back to old probe method for vesa
[    55.234] (II) Loading sub module "fbdevhw"
[    55.234] (II) LoadModule: "fbdevhw"
[    55.242] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    55.263] (II) Module fbdevhw: vendor="X.Org Foundation"
[    55.263]     compiled for 1.9.0, module version = 0.0.2
[    55.263]     ABI class: X.Org Video Driver, version 8.0
[    55.263] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[    55.263] (II) FBDEV(0): using default device
[    55.263] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    55.263] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    55.263] (==) FBDEV(0): RGB weight 888
[    55.263] (==) FBDEV(0): Default visual is TrueColor
[    55.263] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    55.263] (II) FBDEV(0): hardware: inteldrmfb (video memory: 12288kB)
[    55.264] (II) FBDEV(0): checking modes against framebuffer device...
[    55.264] (II) FBDEV(0): checking modes against monitor...
[    55.264] (--) FBDEV(0): Virtual size is 2048x1536 (pitch 2048)
[    55.264] (**) FBDEV(0):  Built-in mode "current"
[    55.264] (==) FBDEV(0): DPI set to (96, 96)
[    55.264] (II) Loading sub module "fb"
[    55.264] (II) LoadModule: "fb"
[    55.264] (II) Loading /usr/lib/xorg/modules/libfb.so
[    55.282] (II) Module fb: vendor="X.Org Foundation"
[    55.282]     compiled for 1.9.0, module version = 1.0.0
[    55.282]     ABI class: X.Org ANSI C Emulation, version 0.4
[    55.282] (**) FBDEV(0): using shadow framebuffer
[    55.282] (II) Loading sub module "shadow"
[    55.282] (II) LoadModule: "shadow"
[    55.282] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    55.323] (II) Module shadow: vendor="X.Org Foundation"
[    55.323]     compiled for 1.9.0, module version = 1.1.0
[    55.323]     ABI class: X.Org ANSI C Emulation, version 0.4
[    55.323] (==) Depth 24 pixmap format is 32 bpp
[    55.504] (==) FBDEV(0): Backing store disabled
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.505] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.506] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.507] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.508] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.509] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.510] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.511] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.511] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.511] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.511] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.511] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.511] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    55.511] (==) FBDEV(0): DPMS enabled
[    55.511] (==) RandR enabled
[    55.511] (II) Initializing built-in extension Generic Event Extension
[    55.511] (II) Initializing built-in extension SHAPE
[    55.511] (II) Initializing built-in extension MIT-SHM
[    55.511] (II) Initializing built-in extension XInputExtension
[    55.511] (II) Initializing built-in extension XTEST
[    55.511] (II) Initializing built-in extension BIG-REQUESTS
[    55.511] (II) Initializing built-in extension SYNC
[    55.511] (II) Initializing built-in extension XKEYBOARD
[    55.511] (II) Initializing built-in extension XC-MISC
[    55.511] (II) Initializing built-in extension SECURITY
[    55.511] (II) Initializing built-in extension XINERAMA
[    55.511] (II) Initializing built-in extension XFIXES
[    55.511] (II) Initializing built-in extension RENDER
[    55.511] (II) Initializing built-in extension RANDR
[    55.511] (II) Initializing built-in extension COMPOSITE
[    55.511] (II) Initializing built-in extension DAMAGE
[    55.511] (II) Initializing built-in extension GESTURE
[    55.601] (II) AIGLX: Screen 0 is not DRI2 capable
[    55.601] (II) AIGLX: Screen 0 is not DRI capable
[    55.606] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    55.607] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    55.812] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    55.867] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    55.867] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    55.867] (II) LoadModule: "evdev"
[    55.868] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    56.140] (II) Module evdev: vendor="X.Org Foundation"
[    56.140]     compiled for 1.9.0, module version = 2.3.2
[    56.140]     Module class: X.Org XInput Driver
[    56.140]     ABI class: X.Org XInput driver, version 11.0
[    56.140] (**) Power Button: always reports core events
[    56.140] (**) Power Button: Device: "/dev/input/event1"
[    56.140] (II) Power Button: Found keys
[    56.140] (II) Power Button: Configuring as keyboard
[    56.140] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    56.140] (**) Option "xkb_rules" "evdev"
[    56.140] (**) Option "xkb_model" "evdev"
[    56.140] (**) Option "xkb_layout" "gb"
[    56.144] (II) XKB: reuse xkmfile /var/lib/xkb/server-C1F82522E3F958F13C2D6D2C62551E135092F235.xkm
[    56.165] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    56.165] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    56.165] (**) Power Button: always reports core events
[    56.165] (**) Power Button: Device: "/dev/input/event0"
[    56.165] (II) Power Button: Found keys
[    56.165] (II) Power Button: Configuring as keyboard
[    56.165] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    56.165] (**) Option "xkb_rules" "evdev"
[    56.165] (**) Option "xkb_model" "evdev"
[    56.165] (**) Option "xkb_layout" "gb"
[    56.167] (II) config/udev: Adding input device PS/2+USB Mouse (/dev/input/event3)
[    56.167] (**) PS/2+USB Mouse: Applying InputClass "evdev pointer catchall"
[    56.168] (**) PS/2+USB Mouse: always reports core events
[    56.168] (**) PS/2+USB Mouse: Device: "/dev/input/event3"
[    56.168] (II) PS/2+USB Mouse: Found 9 mouse buttons
[    56.168] (II) PS/2+USB Mouse: Found scroll wheel(s)
[    56.168] (II) PS/2+USB Mouse: Found relative axes
[    56.168] (II) PS/2+USB Mouse: Found x and y relative axes
[    56.168] (II) PS/2+USB Mouse: Configuring as mouse
[    56.168] (**) PS/2+USB Mouse: YAxisMapping: buttons 4 and 5
[    56.168] (**) PS/2+USB Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    56.168] (II) XINPUT: Adding extended input device "PS/2+USB Mouse" (type: MOUSE)
[    56.168] (II) PS/2+USB Mouse: initialized for relative axes.
[    56.169] (II) config/udev: Adding input device PS/2+USB Mouse (/dev/input/mouse0)
[    56.169] (II) No input driver/identifier specified (ignoring)
[    56.175] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    56.175] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    56.175] (**) AT Translated Set 2 keyboard: always reports core events
[    56.175] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    56.175] (II) AT Translated Set 2 keyboard: Found keys
[    56.175] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    56.175] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    56.175] (**) Option "xkb_rules" "evdev"
[    56.175] (**) Option "xkb_model" "evdev"
[    56.175] (**) Option "xkb_layout" "gb"

---

### Post by realzippy on 2010-12-07
Same resolution restriction when running the livecd ?

---

### Post by Davethemaster on 2010-12-07
Do you mean the CD that I burned the original OS too? Can I use that to run from after a full install? If so how do I do that? When I have accidently left the disk in the CD drive the computer refuses to boot at all.

---

### Post by realzippy on 2010-12-08
Yes,the ubuntu install CD also is a live CD (or have you installed from the "alternate" CD?)
Choose "try ubuntu without changes to the computer" instead of "install"...

---

### Post by Davethemaster on 2010-12-08
Just tried your advice, it just hung for a couple of hours after clicking the option to try from CD. The CD I downloaded was from the official Ubuntu site. I finally gave up and booted back to the full version. Do you think my graphics card could be the issue?

---

### Post by realzippy on 2010-12-08
...can you run the option "check CD for errors"  (or similar)?
Think your graphics device should normally work..
*edit:
ok,bunch of troubles with the intel chips in lucid (quick search),but
should be better with 2.35.xx kernel and KMS in maverick.
can you post the output of
```
cat /etc/default/grub
```

and
```
uname -r
```

BTW,is your system updated after installation ?

---

### Post by Davethemaster on 2010-12-08
I have used update manager and I am told my system is up to date.

Here is the results of the request:

dave@dave-Evo-D310:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
dave@dave-Evo-D310:~$ uname -r
2.6.35-22-generic
dave@dave-Evo-D310:~$

---

### Post by Davethemaster on 2010-12-08
By the way under 'computer' my CD drive is shown as unknown device (bit of a theme here). Also when I put a CD in, such as the Ubuntu install CD, the drive disappears from view.

I still think my on board graphic chip is not set up correctly as when I  play (for example) I player on the BBC, it is very jerky and slow to  the point of being unwatchable.

Thanks for your continued support, it is much appreciated. I don't know if I will end up with a working Linux system after all this (my gut feeling is that my hardware is either too old or that one or more components are failing) but I still like the idea of a fresh start from Microsoft.

---

### Post by realzippy on 2010-12-09
make sure the intel driver is installed:

```
sudo apt-get install xserver-xorg-video-intel

```

Then open your grub file:
```
gksudo gedit /etc/default/grub

```

change:
GRUB_CMDLINE_LINUX=""
to:
GRUB_CMDLINE_LINUX="i915.modeset=1"

close file saving changes,
then update grub:
```
sudo update-grub
```

then reboot.
Anything better?

---

### Post by Davethemaster on 2010-12-10
Okay I followed your instructions and following the reboot I got an error message just before desktop, saying that a command was not reconized. Anyway the desktop loaded and I clicked on the monitor icon to find I had a choice of displays:

1280 x 1024
1024 x 768
800 x 600
640 x 480

No options for refresh rate, rotation etc, and my monitor is still unknown.

I chose 1280 x 1024 and everything looked better. However I looked at the error and realized that I mis-typed the command ending modeset=1 (I put modest instead).

After starting again and correcting this fault, I reboot to find a window popup on the desktop stating 'could not apply stored cofiguration for monitors' There was a little more writing but the window disappeared too quickly. Anyway nothing has changed from the original configuration with this correct procedure.

Very puzzling eh?

---

### Post by Davethemaster on 2010-12-10
Just to clarify, my display has only one choice again: 2048 x 1536

---

### Post by realzippy on 2010-12-10
have you run
```
sudo update-grub
```
after correcting your typo?

---

### Post by Davethemaster on 2010-12-10
Yes that gave the result of the pop up window after boot up.

After another boot up have read the rest of message which states: 'Xserver does not support the size requested'.

---

### Post by Davethemaster on 2010-12-14
Well it seems that my toe dipping with Linux has come to a crossroads. I would love to say that I could take some positives from the experience, but unfortunately my install has not gone well. I think my hardware is just not compatible (graphics card/monitor especially) and so it is with deep regret that I must grovel to one of my IT work colleagues and er...em... acquire a copy of Windows XP.

So it just remains for me to say a big thanks to Realzippy for all the help offered (you win some......) and I bid you all fairwell!

---

### Post by realzippy on 2010-12-14
...yep,bad luck due too intel's linux graphics driver policy.If you
met "linux" with an nvidia graphics device,you might have said
"wow,that is great" and felt like a caveman when booting XP...
Anyway your intel resolution problem surely can be solved, setting up an xorg.conf file,which would have been next step..
Also Ubuntu 8.10 should work with your graphics device,if you just need any working OS for some reason...

---

### Post by realzippy on 2011-03-24
...exactly this problem hit another user and -as assumed-
we solved it by setting up a xorg.conf and adding the proper
H/Vsync values.If anybody is interested,have a look 
[here]("http://ubuntuforums.org/showthread.php?t=1713043").

---

