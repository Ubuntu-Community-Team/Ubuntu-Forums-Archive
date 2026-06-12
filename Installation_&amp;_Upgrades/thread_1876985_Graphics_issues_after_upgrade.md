---
title: "Graphics issues after upgrade"
date: 2011-11-07
forum: Installation &amp; Upgrades
---

### Post by PcMojo on 2011-11-07
I have Ubuntu Studio installed but did not post under there because I had the same issue in Kubuntu a few years ago. ( I just wish I remember how I fixed it :confused: )


I would greatly appreciate some help with my graphics problem, but keep in mind that my resolution is so low I can't do much in a gui environment. Most window buttons are off my screen. I'll probably have to fix this in Terminal.

I have Ubuntu Studio 64 bit and automatically upgraded when 11.10 came out. The graphics changed. They seemed to be "flatter" (loss of 3D?) and resolution went lower. While trying to figure out what went wrong, I noticed that I never installed the recommended Nvidia driver (173) for my GeForce 5200 fx. When I rebooted after installation my resolution is now 640X480. xrandr gives me:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480        50.0* 
   320x240        51.0  
While I knew my current resolution was 640X480 This said my *maximum* was 640X480! After researching the forums I ran 
jockey-text --list which game me:

xorg:nvidia_96 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_173 - NVIDIA accelerated graphics driver (Proprietary, Enabled, In use)
xorg:nvidia_173_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
xorg:nvidia_96_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)

I'm not really sure where to go from here. My graphics with any of my multiple Ubuntu, Kubuntu, Ubuntu Studio installs in the past have always been 2nd rate. I could never play 3d games or get 3d or enhanced desktop effects to work, but at least I could get a tolerable resolution of 1024X768. 

My questions are these:
1) what should I do to get a higher resolution?
2) what was I using before the nvidia 173 install? was it a generic driver? I have on board video, was my graphics card even being used? is that why I haven't been able to get 3d?
3) Will I ever be able to get 3d & desktop effects with this current PC?
4) If I can get 3d & desktop effects running, will it be wiped out if I do an Ubuntu kernal update or video driver update?

Thanks in advance for any help you can offer!

---

### Post by PcMojo on 2011-11-07
I've done a little trouble shooting and decided to uninstall four packages:
nvidia-settings
dkms
nvidia-173
screen-resolution-extra

My resolution is now at 1024X768, which is much better, but I don't know why. After I uninstalled them, I noticed that they were installed *after* I started having problems and the 173 driver was disabled. I was using the 173_updated. Now xrandr gives me:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)

But  jockey-text --list shows all drivers disabled
xorg:nvidia_173 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_96_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
xorg:nvidia_173_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
xorg:nvidia_96 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)

Can anybody clue me in to how my video could even be working without a driver? Does this mean my video card isn't being used and I am just working off my on-board video? Which would make sense as to why nothing 3d seems to work. Does anybody else have a nvidia GeForce 5200 FX that they have been able configure with Ubuntu?

Any help would be appreciated.

---

### Post by MAFoElffen on 2011-11-07
> **PcMojo said:**
> I've done a little trouble shooting and decided to uninstall four packages:
nvidia-settings
dkms
nvidia-173
screen-resolution-extra

My resolution is now at 1024X768, which is much better, but I don't know why. After I uninstalled them, I noticed that they were installed *after* I started having problems and the 173 driver was disabled. I was using the 173_updated. Now xrandr gives me:

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-1 disconnected (normal left inverted right x axis y axis)

But  jockey-text --list shows all drivers disabled
xorg:nvidia_173 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)
xorg:nvidia_96_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
xorg:nvidia_173_updates - NVIDIA accelerated graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
xorg:nvidia_96 - NVIDIA accelerated graphics driver (Proprietary, Disabled, Not in use)

Can anybody clue me in to how my video could even be working without a driver? Does this mean my video card isn't being used and I am just working off my on-board video? Which would make sense as to why nothing 3d seems to work. Does anybody else have a nvidia GeForce 5200 FX that they have been able configure with Ubuntu?

Any help would be appreciated.
Here you go:
```
[FONT=monospace]
[/FONT]sudo apt-get update 
sudo nvidia-installer --uninstall 
sudo apt-get remove nvidia-* 
sudo apt-get install [COLOR=Red]linux-headers-[/COLOR]'uname -r' 
sudo apt-get install nvidia-173
sudo nvidia-xconfig
sudo apt-get upgrade
sudo reboot

```The second or third command may return a file not found, which is  what we want at that point anyways, so just go on with the commands.   What that does is to purge the old drivers and ensure there is a correct  kernel header file before the later commands, which install and configure the correct  driver for you.

If you still do not get all your resolutions back, then post your /var/log/Xorg.0.log

Tell me how it goes.

---

### Post by PcMojo on 2011-11-09
I copied your commands and pasted them into terminal. As you said, some came back "file not found".  sudo apt-get install 'uname -r'   seemed to do something then the last line read something like " E:   uname -r package not found.  
After reboot, all linux options lead me to a black screen. :confused:
 I am now writing to you from Windows. :(   If I choose my current Ubuntu or Current recovery version in the Grub menu, the monitor goes black and I never get a login. Also, I have 8 lights on my monitor (Brightness, contrast, etc) and they start blinking in a repeating pattern (4&5, 6&3, 7&2, 8&1, 7&2, 6&3, 5&4 etc). When I choose the older version of Ubuntu from the Grub menu, it goes black but doesn't include the cool lightshow. While the blinking lights are pretty cool, the novelty has worn out and I would much rather have Ubuntu back. :lol: 

Any suggestions? ](*,)

---

### Post by MAFoElffen on 2011-11-09
> **PcMojo said:**
> I copied your commands and pasted them into terminal. As you said, some came back "file not found".  sudo apt-get install 'uname -r'   seemed to do something then the last line read something like " E:   uname -r package not found.  
After reboot, all linux options lead me to a black screen. :confused:
 I am now writing to you from Windows. :(   If I choose my current Ubuntu or Current recovery version in the Grub menu, the monitor goes black and I never get a login. Also, I have 8 lights on my monitor (Brightness, contrast, etc) and they start blinking in a repeating pattern (4&5, 6&3, 7&2, 8&1, 7&2, 6&3, 5&4 etc). When I choose the older version of Ubuntu from the Grub menu, it goes black but doesn't include the cool lightshow. While the blinking lights are pretty cool, the novelty has worn out and I would much rather have Ubuntu back. :lol: 

Any suggestions? ](*,)
My typo- sorry. Changed/corrected my last post. Please try again.

If it doesn't work--> Boot from a LiveCD, find your install and post the /var/log/Xorg.0.log file.

---

### Post by PcMojo on 2011-11-09
No Joy. The changed line errored out with a package not found.  Running a Kubuntu Live CD now. Here is the Xorg.0.log (although it's pretty long):


[    21.153] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    21.153] X Protocol Version 11, Revision 0
[    21.153] Build Operating System: Linux 2.6.24-29-server x86_64 Ubuntu
[    21.154] Current Operating System: Linux ubstud 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64
[    21.154] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-12-generic root=UUID=947a4131-beeb-45d6-89a9-e7676c9cf82e ro quiet splash vt.handoff=7
[    21.154] Build Date: 19 October 2011  05:21:26AM
[    21.154] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[    21.154] Current version of pixman: 0.22.2
[    21.154] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[    21.154] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    21.154] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov  9 02:04:32 2011
[    21.154] (==) Using config file: "/etc/X11/xorg.conf"
[    21.154] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    21.154] (==) ServerLayout "Layout0"
[    21.154] (**) |-->Screen "Screen0" (0)
[    21.154] (**) |   |-->Monitor "Monitor0"
[    21.155] (**) |   |-->Device "Device0"
[    21.155] (**) |-->Input Device "Keyboard0"
[    21.155] (**) |-->Input Device "Mouse0"
[    21.155] (==) Automatically adding devices
[    21.155] (==) Automatically enabling devices
[    21.155] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    21.155] 	Entry deleted from font path.
[    21.155] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    21.155] 	Entry deleted from font path.
[    21.155] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    21.155] 	Entry deleted from font path.
[    21.155] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    21.155] 	Entry deleted from font path.
[    21.155] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    21.155] 	Entry deleted from font path.
[    21.155] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    21.155] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    21.155] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    21.155] (WW) Disabling Keyboard0
[    21.155] (WW) Disabling Mouse0
[    21.155] (II) Loader magic: 0x7e0220
[    21.155] (II) Module ABI versions:
[    21.155] 	X.Org ANSI C Emulation: 0.4
[    21.155] 	X.Org Video Driver: 10.0
[    21.155] 	X.Org XInput driver : 12.3
[    21.155] 	X.Org Server Extension : 5.0
[    21.158] (--) PCI:*(0:1:0:0) 10de:0322:1682:1351 rev 161, Mem @ 0xe0000000/16777216, 0xd8000000/134217728, BIOS @ 0x????????/131072
[    21.172] (II) Open ACPI successful (/var/run/acpid.socket)
[    21.172] (II) LoadModule: "extmod"
[    21.194] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    21.194] (II) Module extmod: vendor="X.Org Foundation"
[    21.194] 	compiled for 1.10.4, module version = 1.0.0
[    21.194] 	Module class: X.Org Server Extension
[    21.194] 	ABI class: X.Org Server Extension, version 5.0
[    21.194] (II) Loading extension MIT-SCREEN-SAVER
[    21.194] (II) Loading extension XFree86-VidModeExtension
[    21.194] (II) Loading extension XFree86-DGA
[    21.194] (II) Loading extension DPMS
[    21.194] (II) Loading extension XVideo
[    21.194] (II) Loading extension XVideo-MotionCompensation
[    21.194] (II) Loading extension X-Resource
[    21.194] (II) LoadModule: "dbe"
[    21.195] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    21.195] (II) Module dbe: vendor="X.Org Foundation"
[    21.195] 	compiled for 1.10.4, module version = 1.0.0
[    21.195] 	Module class: X.Org Server Extension
[    21.195] 	ABI class: X.Org Server Extension, version 5.0
[    21.195] (II) Loading extension DOUBLE-BUFFER
[    21.195] (II) LoadModule: "glx"
[    21.195] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    21.440] (II) Module glx: vendor="NVIDIA Corporation"
[    21.440] 	compiled for 4.0.2, module version = 1.0.0
[    21.440] 	Module class: X.Org Server Extension
[    21.440] (II) NVIDIA GLX Module  173.14.30  Sat Apr 16 22:45:09 PDT 2011
[    21.440] (II) Loading extension GLX
[    21.441] (II) LoadModule: "record"
[    21.441] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    21.441] (II) Module record: vendor="X.Org Foundation"
[    21.441] 	compiled for 1.10.4, module version = 1.13.0
[    21.441] 	Module class: X.Org Server Extension
[    21.441] 	ABI class: X.Org Server Extension, version 5.0
[    21.441] (II) Loading extension RECORD
[    21.441] (II) LoadModule: "dri"
[    21.442] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    21.442] (II) Module dri: vendor="X.Org Foundation"
[    21.442] 	compiled for 1.10.4, module version = 1.0.0
[    21.442] 	ABI class: X.Org Server Extension, version 5.0
[    21.442] (II) Loading extension XFree86-DRI
[    21.442] (II) LoadModule: "dri2"
[    21.442] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    21.443] (II) Module dri2: vendor="X.Org Foundation"
[    21.443] 	compiled for 1.10.4, module version = 1.2.0
[    21.443] 	ABI class: X.Org Server Extension, version 5.0
[    21.443] (II) Loading extension DRI2
[    21.443] (II) LoadModule: "nvidia"
[    21.443] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    21.472] (II) Module nvidia: vendor="NVIDIA Corporation"
[    21.472] 	compiled for 4.0.2, module version = 1.0.0
[    21.472] 	Module class: X.Org Video Driver
[    21.489] (II) NVIDIA dlloader X Driver  173.14.30  Sat Apr 16 22:18:29 PDT 2011
[    21.499] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    21.499] (++) using VT number 7

[    21.500] (II) Loading sub module "fb"
[    21.500] (II) LoadModule: "fb"
[    21.501] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.501] (II) Module fb: vendor="X.Org Foundation"
[    21.501] 	compiled for 1.10.4, module version = 1.0.0
[    21.501] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.501] (II) Loading sub module "wfb"
[    21.501] (II) LoadModule: "wfb"
[    21.501] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.513] (II) Module wfb: vendor="X.Org Foundation"
[    21.513] 	compiled for 1.10.4, module version = 1.0.0
[    21.513] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    21.513] (II) Loading sub module "ramdac"
[    21.513] (II) LoadModule: "ramdac"
[    21.513] (II) Module "ramdac" already built-in
[    21.513] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    21.513] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    21.513] (II) Loading /usr/lib/xorg/modules/libfb.so
[    21.521] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[    21.521] (==) NVIDIA(0): RGB weight 888
[    21.521] (==) NVIDIA(0): Default visual is TrueColor
[    21.521] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    21.522] (**) NVIDIA(0): Enabling RENDER acceleration
[    21.522] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    21.522] (II) NVIDIA(0):     enabled.
[    22.451] (WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid:
[    22.451] (WW) NVIDIA(GPU-0):     unrecognized EDID Header.
[    22.451] (II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:1:0:0 (GPU-0)
[    22.451] (--) NVIDIA(0): Memory: 131072 kBytes
[    22.451] (--) NVIDIA(0): VideoBIOS: 04.34.20.67.00
[    22.451] (II) NVIDIA(0): Detected AGP rate: 8X
[    22.451] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    22.451] (--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
[    22.451] (--) NVIDIA(0):     CRT-0
[    22.451] (--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
[    22.459] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    22.459] (==) NVIDIA(0): 
[    22.459] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    22.459] (==) NVIDIA(0):     will be used as the requested mode.
[    22.459] (==) NVIDIA(0): 
[    22.459] (II) NVIDIA(0): Validated modes:
[    22.459] (II) NVIDIA(0):     "nvidia-auto-select"
[    22.459] (II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
[    22.460] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    22.460] (WW) NVIDIA(0):     from CRT-0's EDID.
[    22.460] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    22.460] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    22.461] (--) Depth 24 pixmap format is 32 bpp
[    22.462] (II) NVIDIA(0): Initialized AGP GART.
[    22.465] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    22.568] (II) Loading extension NV-GLX
[    22.594] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    22.600] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    22.600] (==) NVIDIA(0): Backing store disabled
[    22.600] (==) NVIDIA(0): Silken mouse enabled
[    22.600] (**) NVIDIA(0): DPMS enabled
[    22.600] (II) Loading extension NV-CONTROL
[    22.601] (==) RandR enabled
[    22.601] (II) Initializing built-in extension Generic Event Extension
[    22.601] (II) Initializing built-in extension SHAPE
[    22.601] (II) Initializing built-in extension MIT-SHM
[    22.601] (II) Initializing built-in extension XInputExtension
[    22.601] (II) Initializing built-in extension XTEST
[    22.601] (II) Initializing built-in extension BIG-REQUESTS
[    22.601] (II) Initializing built-in extension SYNC
[    22.601] (II) Initializing built-in extension XKEYBOARD
[    22.601] (II) Initializing built-in extension XC-MISC
[    22.601] (II) Initializing built-in extension SECURITY
[    22.601] (II) Initializing built-in extension XINERAMA
[    22.601] (II) Initializing built-in extension XFIXES
[    22.601] (II) Initializing built-in extension RENDER
[    22.601] (II) Initializing built-in extension RANDR
[    22.601] (II) Initializing built-in extension COMPOSITE
[    22.601] (II) Initializing built-in extension DAMAGE
[    22.601] (II) Initializing built-in extension GESTURE
[    22.604] (II) Initializing extension GLX
[    22.686] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    22.697] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    22.697] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.697] (II) LoadModule: "evdev"
[    22.698] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.699] (II) Module evdev: vendor="X.Org Foundation"
[    22.699] 	compiled for 1.10.2, module version = 2.6.0
[    22.699] 	Module class: X.Org XInput Driver
[    22.699] 	ABI class: X.Org XInput driver, version 12.3
[    22.699] (II) Using input driver 'evdev' for 'Power Button'
[    22.699] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.699] (**) Power Button: always reports core events
[    22.699] (**) Power Button: Device: "/dev/input/event1"
[    22.699] (--) Power Button: Found keys
[    22.699] (II) Power Button: Configuring as keyboard
[    22.699] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    22.699] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.699] (**) Option "xkb_rules" "evdev"
[    22.699] (**) Option "xkb_model" "pc105"
[    22.699] (**) Option "xkb_layout" "us"
[    22.704] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    22.704] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    22.704] (II) Using input driver 'evdev' for 'Power Button'
[    22.704] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.704] (**) Power Button: always reports core events
[    22.704] (**) Power Button: Device: "/dev/input/event0"
[    22.705] (--) Power Button: Found keys
[    22.705] (II) Power Button: Configuring as keyboard
[    22.705] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    22.705] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    22.705] (**) Option "xkb_rules" "evdev"
[    22.705] (**) Option "xkb_model" "pc105"
[    22.705] (**) Option "xkb_layout" "us"
[    22.707] (II) config/udev: Adding input device Microsoft Comfort Optical Mouse 1000 (/dev/input/event2)
[    22.707] (**) Microsoft Comfort Optical Mouse 1000: Applying InputClass "evdev pointer catchall"
[    22.707] (II) Using input driver 'evdev' for 'Microsoft Comfort Optical Mouse 1000'
[    22.707] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.707] (**) Microsoft Comfort Optical Mouse 1000: always reports core events
[    22.707] (**) Microsoft Comfort Optical Mouse 1000: Device: "/dev/input/event2"
[    22.707] (--) Microsoft Comfort Optical Mouse 1000: Found 3 mouse buttons
[    22.707] (--) Microsoft Comfort Optical Mouse 1000: Found scroll wheel(s)
[    22.707] (--) Microsoft Comfort Optical Mouse 1000: Found relative axes
[    22.707] (--) Microsoft Comfort Optical Mouse 1000: Found x and y relative axes
[    22.707] (II) Microsoft Comfort Optical Mouse 1000: Configuring as mouse
[    22.707] (II) Microsoft Comfort Optical Mouse 1000: Adding scrollwheel support
[    22.707] (**) Microsoft Comfort Optical Mouse 1000: YAxisMapping: buttons 4 and 5
[    22.707] (**) Microsoft Comfort Optical Mouse 1000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.707] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb3/3-1/3-1:1.0/input/input2/event2"
[    22.707] (II) XINPUT: Adding extended input device "Microsoft Comfort Optical Mouse 1000" (type: MOUSE)
[    22.707] (II) Microsoft Comfort Optical Mouse 1000: initialized for relative axes.
[    22.707] (**) Microsoft Comfort Optical Mouse 1000: (accel) keeping acceleration scheme 1
[    22.707] (**) Microsoft Comfort Optical Mouse 1000: (accel) acceleration profile 0
[    22.707] (**) Microsoft Comfort Optical Mouse 1000: (accel) acceleration factor: 2.000
[    22.707] (**) Microsoft Comfort Optical Mouse 1000: (accel) acceleration threshold: 4
[    22.708] (II) config/udev: Adding input device Microsoft Comfort Optical Mouse 1000 (/dev/input/mouse0)
[    22.708] (II) No input driver/identifier specified (ignoring)
[    22.709] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event3)
[    22.709] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    22.709] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    22.709] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.709] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    22.709] (**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event3"
[    22.709] (--) Microsoft Comfort Curve Keyboard 2000: Found keys
[    22.709] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    22.709] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb3/3-2/3-2:1.0/input/input3/event3"
[    22.709] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
[    22.709] (**) Option "xkb_rules" "evdev"
[    22.709] (**) Option "xkb_model" "pc105"
[    22.709] (**) Option "xkb_layout" "us"
[    22.710] (II) config/udev: Adding input device Microsoft Comfort Curve Keyboard 2000 (/dev/input/event4)
[    22.710] (**) Microsoft Comfort Curve Keyboard 2000: Applying InputClass "evdev keyboard catchall"
[    22.710] (II) Using input driver 'evdev' for 'Microsoft Comfort Curve Keyboard 2000'
[    22.710] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    22.710] (**) Microsoft Comfort Curve Keyboard 2000: always reports core events
[    22.710] (**) Microsoft Comfort Curve Keyboard 2000: Device: "/dev/input/event4"
[    22.710] (--) Microsoft Comfort Curve Keyboard 2000: Found 1 mouse buttons
[    22.710] (--) Microsoft Comfort Curve Keyboard 2000: Found scroll wheel(s)
[    22.710] (--) Microsoft Comfort Curve Keyboard 2000: Found relative axes
[    22.710] (--) Microsoft Comfort Curve Keyboard 2000: Found absolute axes
[    22.710] (II) evdev-grail: failed to open grail, no gesture support
[    22.710] (--) Microsoft Comfort Curve Keyboard 2000: Found keys
[    22.710] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as mouse
[    22.710] (II) Microsoft Comfort Curve Keyboard 2000: Configuring as keyboard
[    22.710] (II) Microsoft Comfort Curve Keyboard 2000: Adding scrollwheel support
[    22.710] (**) Microsoft Comfort Curve Keyboard 2000: YAxisMapping: buttons 4 and 5
[    22.710] (**) Microsoft Comfort Curve Keyboard 2000: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    22.710] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.1/usb3/3-2/3-2:1.1/input/input4/event4"
[    22.710] (II) XINPUT: Adding extended input device "Microsoft Comfort Curve Keyboard 2000" (type: KEYBOARD)
[    22.710] (**) Option "xkb_rules" "evdev"
[    22.710] (**) Option "xkb_model" "pc105"
[    22.710] (**) Option "xkb_layout" "us"
[    22.711] (EE) Microsoft Comfort Curve Keyboard 2000: failed to initialize for relative axes.
[    22.711] (II) Microsoft Comfort Curve Keyboard 2000: initialized for absolute axes.
[    22.711] (**) Microsoft Comfort Curve Keyboard 2000: (accel) keeping acceleration scheme 1
[    22.711] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration profile 0
[    22.711] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration factor: 2.000
[    22.711] (**) Microsoft Comfort Curve Keyboard 2000: (accel) acceleration threshold: 4
[    24.323] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.


Thanks in Advance!

---

### Post by MAFoElffen on 2011-11-09
> **PcMojo said:**
> No Joy. The changed line errored out with a package not found.  Running a Kubuntu Live CD now. Here is the Xorg.0.log (although it's pretty long):

[    24.323] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.

Thanks in Advance!
So you are booting to a black screen now, where as before you were just not getting resolutions?  Just getting a clear picture of where you are at.

Your log said everything loaded fine as for drivers.  It did say it couldn't get any EDID data back from your Display... What is the brand, model and manufacturing date of your monitor? Not getting any EDID data could be your resolution problem.  Please post your /etc/X11/xorg.conf file.

Go to the /Home/user_name/ directory, "your" user home directory and remove ~/.config/*monitors*.xml.  If not there, that's fine.

Your log also had a warining about an Xalloc memory request, which you should join this launchpad bug as it affects you:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/681945](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/681945)

---

### Post by haresear on 2011-11-09
I have a machine with an Nvidia FX5200 card with Ubuntu 11.10 installed. I was able to install and run using the nvidia-173-updates driver, but can't run Unity 3D or Gnome Shell. Unity 2D and Gnome Classic (without effects) run okay. The unity test script says my card is blacklisted, so there is not much hope for Unity 3D. Before I installed the nvidia proprietary driver, I was running with the open source driver nouveau, which worked about as well as the nvidia driver (but glxgears ran slower). That may be what you were running before you installed the nvidia driver.

Sorry, I can't help with your current black-screen problem. I did have some initial graphics problems when trying to install 11.10, and had to use the 'nomodeset' boot parameter on the kernel (linux) grub2 command line.

---

### Post by MAFoElffen on 2011-11-09
> **haresear said:**
> I have a machine with an Nvidia FX5200 card with Ubuntu 11.10 installed. I was able to install and run using the nvidia-173-updates driver, but can't run Unity 3D or Gnome Shell. Unity 2D and Gnome Classic (without effects) run okay. The unity test script says my card is blacklisted, so there is not much hope for Unity 3D. Before I installed the nvidia proprietary driver, I was running with the open source driver nouveau, which worked about as well as the nvidia driver (but glxgears ran slower). That may be what you were running before you installed the nvidia driver.

Sorry, I can't help with your current black-screen problem. I did have some initial graphics problems when trying to install 11.10, and had to use the 'nomodeset' boot parameter on the kernel (linux) grub2 command line.
He now has the correct driver loaded... Unity and Gnome shell wouldn't be an issue with him as he is running Ubuntu Studio...

---

### Post by PcMojo on 2011-11-10
@haresear     Thanks for the info! It's good to know I'm not the only one with 3d issues. I'm not convinced that I have ever used my graphics card with linux. I have never been able to run 3d games or get 3d effects. Everytime I try to improve the graphics by using drivers that didn't come with the generic install, bad things happen. If we can get it up and running again, I'm going to yank my video card and see what happens. I suspect nothing. I think the reason my grapics are so poor under linux is that it is using my on board grapics and not my grapics card.

---

### Post by PcMojo on 2011-11-10
[QUOTE=MAFoElffen;11441016]So you are booting to a black screen now, where as before you were just not getting resolutions?  Just getting a clear picture of where you are at.
-My first post was trying to get my resolution back. By my second post I was able to get the resolution back by uninstalling a few packages, but I noticed later those packages were installed after my resolution problems, so were really not the issue but coincidentally fixed the resolution issue. :confused: All of this began when my grapics looked "flatter" after the 11.10 upgrade. While working on that I tried installing a video driver hoping to improve my graphics and possibly to get 3d graphics. Upon trying your suggestion, my screen went black after the grub selection (for current Ubuntu, Recovery, and older version). And just to let you know, I've only had Ubuntu Studio installed for a few months and almost all my important files are on a NTFS partition. So if we need to reinstall, it won't be the end of the world.

What is the brand, model and manufacturing date of your monitor?  
-Envision, EN-710, April 20, 2001

Please post your /etc/X11/xorg.conf file.

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder58)  Sat Apr 16 22:49:04 PDT 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection



remove ~/.config/*monitors*.xml.  If not there, that's fine.
-It was not there.

Thanks again for the help. While you're looking at that, I'm going to go find a Forum Tutorial on how to quote! :D

---

### Post by MAFoElffen on 2011-11-10
> **PcMojo said:**
> @haresear     Thanks for the info! It's good to know I'm not the only one with 3d issues. I'm not convinced that I have ever used my graphics card with linux. I have never been able to run 3d games or get 3d effects. Everytime I try to improve the graphics by using drivers that didn't come with the generic install, bad things happen. If we can get it up and running again, I'm going to yank my video card and see what happens. I suspect nothing. I think the reason my grapics are so poor under linux is that it is using my on board grapics and not my grapics card.
I have to admit- the linux NVidia drivers for older legacy NVidia cards are lacking.  I have 3 test boxes with NVidia geoforce 2 through 4 series cards, that I had given up on for quality. I was very surprized during the Natty dev test cycle when a Nouveau Experimental 3D driver for NVidia came out... and it really worked great on those cards! On those cards, it worked better that the Nvidia driver.

On 6 series and above, the NVidia always worked better than the Nautilus driver.  If that Nautilus driver is available for your card, it will show up in the Additional drivers applet.

---

### Post by PcMojo on 2011-11-10
> If that Nautilus driver is available for your card, it will show up in the Additional drivers applet.
I didn't see it. The only two I saw were 173 and 96 (and the same two updated versions).

> NVidia geoforce 2 through 4 series cards   Mine is a Nvidia Gforce 5200 FX - does that make it a 5 series?
Is there a document showing what drivers go with which video card that you know of?

---

### Post by MAFoElffen on 2011-11-11
> **PcMojo said:**
> I didn't see it. The only two I saw were 173 and 96 (and the same two updated versions).

   Mine is a Nvidia Gforce 5200 FX - does that make it a 5 series?
Is there a document showing what drivers go with which video card that you know of?
The Nouveau Experimental driver does say it supports an NVidia FX Geforce 5200. Yes you are 5 series.

For NVidia Drivers, please read this post:
[COLOR=Red][SIZE=2][COLOR=Black][SIZE=1]**[Finding the Right NVidia Driver from the Card ID]("http://ubuntuforums.org/showpost.php?p=10910784&postcount=284")**[/SIZE][/COLOR][/SIZE][/COLOR]

From that, the rules of thumb is:
270 series = nvidia-current --> Geforce 6 series and newer
173 series = nvidia-173 --> Geforce 5 series and older
96 series = nvidia-96 --> Real old, NV1 thru geforce 4

But I always check Appendix A to make sure.

---

### Post by haresear on 2011-11-11
Yes, I can confirm from my own experience that nvidia-173 is the highest version Nvidia proprietary driver that supports the Geforce FX5200 card. I also have an on-board graphics chip, and it is disabled when the Geforce card is plugged in. I do have some 3D acceleration, but the GLX version is too low for many of the more recent apps, and they often will fall back to software rendering. If you get your desktop running again, you can install the 'mesa-utils' package and then run glxinfo to get some info on what graphics driver is running and whether you have hardware rendering. From that you should be able to tell whether the Nvidia card or the on-board graphics is being used.

---

### Post by PcMojo on 2011-11-14
I reinstalled Ubuntu Studio and it appears to be working much better. It is telling me there is an upgrade to 11.10 but that is what started this mess so I don't think I'll do it. 
@haresear  I appear to be using the Nouveau driver and the resolution is good. I don't think I can get 3d effects or play 3d games though. But I usually run into problems when I try the 173 driver (it goes to 640x480). Last time I think I used the 173 Updated as well. Maybe I've been trying to solve this from the wrong angle. Perhaps I will try finding out which cards work best with Ubuntu and try to find a used one (my mobo is about 8 yrs old).

---

