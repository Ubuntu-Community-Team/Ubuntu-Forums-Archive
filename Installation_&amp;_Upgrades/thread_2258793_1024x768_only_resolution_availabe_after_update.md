---
title: "1024x768 only resolution availabe after update"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by patrebert on 2014-12-30
Did update on my 14.04 Intel 4790 system recently (no external graphics card) and now the only resolution available is 1024x768 on 'Built-in Display'. Have messed around with various posted 'solutions' involving cvt and xrandr with no success. Is there an official Ubuntu solution to this mess? Had been running 1920x1080.
Just installed most recent updates, no help.

---

### Post by MAFoElffen on 2014-12-31
Welcome to Ubuntu Forums!

So you have been running this system Usinf Ubuntu 14.04.x LTS at 1920x1080 resolution until when? (To try to figure out what updates may have been in that time period...)

Install this utility first:
```

sudo apt-get install lshw

```
Then post the result of:
```

xrandr -q
sudo lshw -numeric -class video
cat /etc/X11/xorg.conf
cat /var/log/Xorg.0.log

```

---

### Post by patrebert on 2015-01-31
Thanks for the response; sorry for being so long in replying. Yes, I'd been running 1920x1080 on 14.04 prior. Had done some updates during that time, whatever popped up as needing updated on more than one occasion.
Here are some other hints that I hope may be helpful:
  When I look at the display in system settings, the display is identified as 'Built-in Display' and the only resolution option is  
  1024x768. 
If I try to add mode (attempt at following various instructions I found), I get this:
rebert@rebert-4790:~$ cat xprofilexrandr --newmode "1920x1080"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode default 1920x1080
xrandr --output default --mode 1920x1080


rebert@rebert-4790:~$ source xprofile
xrandr: Failed to get size of gamma for output default
xrandr: Failed to get size of gamma for output default
xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 1024x768 (desired size 1920x1080)
rebert@rebert-4790:~$ 

At this point,  system settings lists 1920x1080 as option but won't successfully set it
(get dialog box that says "The selected configuration for displays could not be applied required virtual size does not fit available size: requested=(1920,1080), minimum=(1024,768), maximum=(1024,768)
So the problem seems pretty clear, but I can't figure out how to reset the maximum.




Here's the output requested:


rebert@rebert-4790:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768       76.0* 
rebert@rebert-4790:~$ 



rebert@rebert-4790:~$ sudo lshw -numeric -class video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:412]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
rebert@rebert-4790:~$ 



rebert@rebert-4790:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory
rebert@rebert-4790:~$ 


rebert@rebert-4790:~$ cat /var/log/Xorg.0.log
[     2.181] 
X.Org X Server 1.16.0
Release Date: 2014-07-16
[     2.181] X Protocol Version 11, Revision 0
[     2.181] Build Operating System: Linux 3.2.0-54-generic x86_64 Ubuntu
[     2.181] Current Operating System: Linux rebert-4790 3.16.0-29-generic #39-Ubuntu SMP Mon Dec 15 22:27:29 UTC 2014 x86_64
[     2.181] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-29-generic.efi.signed root=UUID=d3c64250-a4b3-4b94-8b90-5b6511a4f70d ro nomodeset=1 drm.debug=0xe plymouth:debug
[     2.181] Build Date: 09 December 2014  11:01:03PM
[     2.181] xorg-server 2:1.16.0-1ubuntu1.2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     2.181] Current version of pixman: 0.32.4
[     2.181] 	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
[     2.181] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     2.181] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jan 31 14:39:35 2015
[     2.181] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     2.181] (==) No Layout section.  Using the first Screen section.
[     2.181] (==) No screen section available. Using defaults.
[     2.181] (**) |-->Screen "Default Screen Section" (0)
[     2.181] (**) |   |-->Monitor "<default monitor>"
[     2.182] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[     2.182] (==) Automatically adding devices
[     2.182] (==) Automatically enabling devices
[     2.182] (==) Automatically adding GPU devices
[     2.182] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     2.182] 	Entry deleted from font path.
[     2.182] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     2.182] 	Entry deleted from font path.
[     2.182] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     2.182] 	Entry deleted from font path.
[     2.182] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     2.182] 	Entry deleted from font path.
[     2.182] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     2.182] 	Entry deleted from font path.
[     2.182] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     2.182] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     2.182] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[     2.182] (II) Loader magic: 0x7f89280ddd80
[     2.182] (II) Module ABI versions:
[     2.182] 	X.Org ANSI C Emulation: 0.4
[     2.182] 	X.Org Video Driver: 18.0
[     2.182] 	X.Org XInput driver : 21.0
[     2.182] 	X.Org Server Extension : 8.0
[     2.182] (--) PCI:*(0:0:2:0) 8086:0412:1043:8534 rev 6, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[     2.183] (II) LoadModule: "glx"
[     2.184] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     2.192] (II) Module glx: vendor="X.Org Foundation"
[     2.192] 	compiled for 1.16.0, module version = 1.0.0
[     2.192] 	ABI class: X.Org Server Extension, version 8.0
[     2.192] (==) AIGLX enabled
[     2.192] (==) Matched intel as autoconfigured driver 0
[     2.192] (==) Matched modesetting as autoconfigured driver 1
[     2.192] (==) Matched fbdev as autoconfigured driver 2
[     2.192] (==) Matched vesa as autoconfigured driver 3
[     2.192] (==) Assigned the driver to the xf86ConfigLayout
[     2.192] (II) LoadModule: "intel"
[     2.192] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     2.192] (II) Module intel: vendor="X.Org Foundation"
[     2.192] 	compiled for 1.16.0, module version = 2.99.914
[     2.192] 	Module class: X.Org Video Driver
[     2.192] 	ABI class: X.Org Video Driver, version 18.0
[     2.192] (II) LoadModule: "modesetting"
[     2.192] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     2.193] (II) Module modesetting: vendor="X.Org Foundation"
[     2.193] 	compiled for 1.16.0, module version = 0.9.0
[     2.193] 	Module class: X.Org Video Driver
[     2.193] 	ABI class: X.Org Video Driver, version 18.0
[     2.193] (II) LoadModule: "fbdev"
[     2.193] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     2.193] (II) Module fbdev: vendor="X.Org Foundation"
[     2.193] 	compiled for 1.16.0, module version = 0.4.4
[     2.193] 	Module class: X.Org Video Driver
[     2.193] 	ABI class: X.Org Video Driver, version 18.0
[     2.193] (II) LoadModule: "vesa"
[     2.193] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     2.193] (II) Module vesa: vendor="X.Org Foundation"
[     2.193] 	compiled for 1.16.0, module version = 2.3.3
[     2.193] 	Module class: X.Org Video Driver
[     2.193] 	ABI class: X.Org Video Driver, version 18.0
[     2.193] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
	i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
	915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
	Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
	GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     2.193] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     2.193] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     2.193] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     2.193] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     2.193] (II) FBDEV: driver for framebuffer: fbdev
[     2.193] (II) VESA: driver for VESA chipsets: vesa
[     2.193] (++) using VT number 7


[     2.195] (EE) open /dev/dri/card0: No such file or directory
[     2.195] (WW) Falling back to old probe method for modesetting
[     2.195] (EE) open /dev/dri/card0: No such file or directory
[     2.195] (II) Loading sub module "fbdevhw"
[     2.195] (II) LoadModule: "fbdevhw"
[     2.196] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     2.196] (II) Module fbdevhw: vendor="X.Org Foundation"
[     2.196] 	compiled for 1.16.0, module version = 0.0.2
[     2.196] 	ABI class: X.Org Video Driver, version 18.0
[     2.196] (**) FBDEV(1): claimed PCI slot 0@0:2:0
[     2.196] (II) FBDEV(1): using default device
[     2.196] (WW) Falling back to old probe method for vesa
[     2.196] (EE) Screen 0 deleted because of no matching config section.
[     2.196] (II) UnloadModule: "modesetting"
[     2.196] (II) FBDEV(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[     2.196] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[     2.196] (==) FBDEV(0): RGB weight 888
[     2.196] (==) FBDEV(0): Default visual is TrueColor
[     2.196] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[     2.196] (II) FBDEV(0): hardware: EFI VGA (video memory: 3072kB)
[     2.196] (II) FBDEV(0): checking modes against framebuffer device...
[     2.196] (II) FBDEV(0): checking modes against monitor...
[     2.196] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[     2.196] (**) FBDEV(0):  Built-in mode "current": 78.7 MHz, 59.9 kHz, 75.7 Hz
[     2.196] (II) FBDEV(0): Modeline "current"x0.0   78.65  1024 1056 1184 1312  768 772 776 792 -hsync -vsync -csync (59.9 kHz b)
[     2.196] (==) FBDEV(0): DPI set to (96, 96)
[     2.196] (II) Loading sub module "fb"
[     2.196] (II) LoadModule: "fb"
[     2.196] (II) Loading /usr/lib/xorg/modules/libfb.so
[     2.196] (II) Module fb: vendor="X.Org Foundation"
[     2.196] 	compiled for 1.16.0, module version = 1.0.0
[     2.196] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     2.196] (**) FBDEV(0): using shadow framebuffer
[     2.196] (II) Loading sub module "shadow"
[     2.196] (II) LoadModule: "shadow"
[     2.196] (II) Loading /usr/lib/xorg/modules/libshadow.so
[     2.196] (II) Module shadow: vendor="X.Org Foundation"
[     2.196] 	compiled for 1.16.0, module version = 1.1.0
[     2.196] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     2.196] (II) UnloadModule: "vesa"
[     2.196] (II) Unloading vesa
[     2.196] (==) Depth 24 pixmap format is 32 bpp
[     2.196] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[     2.198] (==) FBDEV(0): Backing store enabled
[     2.198] (==) FBDEV(0): DPMS enabled
[     2.198] (==) RandR enabled
[     2.202] (II) SELinux: Disabled on system
[     2.203] (II) AIGLX: Screen 0 is not DRI2 capable
[     2.203] (EE) AIGLX: reverting to software rendering
[     2.217] (II) AIGLX: Loaded and initialized swrast
[     2.217] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[     2.224] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     2.225] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     2.226] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     2.226] (II) LoadModule: "evdev"
[     2.226] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     2.227] (II) Module evdev: vendor="X.Org Foundation"
[     2.227] 	compiled for 1.16.0, module version = 2.9.0
[     2.227] 	Module class: X.Org XInput Driver
[     2.227] 	ABI class: X.Org XInput driver, version 21.0
[     2.227] (II) Using input driver 'evdev' for 'Power Button'
[     2.227] (**) Power Button: always reports core events
[     2.227] (**) evdev: Power Button: Device: "/dev/input/event1"
[     2.227] (--) evdev: Power Button: Vendor 0 Product 0x1
[     2.227] (--) evdev: Power Button: Found keys
[     2.227] (II) evdev: Power Button: Configuring as keyboard
[     2.227] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     2.227] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     2.227] (**) Option "xkb_rules" "evdev"
[     2.227] (**) Option "xkb_model" "pc105"
[     2.227] (**) Option "xkb_layout" "us"
[     2.227] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     2.227] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     2.227] (II) Using input driver 'evdev' for 'Power Button'
[     2.227] (**) Power Button: always reports core events
[     2.227] (**) evdev: Power Button: Device: "/dev/input/event0"
[     2.227] (--) evdev: Power Button: Vendor 0 Product 0x1
[     2.227] (--) evdev: Power Button: Found keys
[     2.227] (II) evdev: Power Button: Configuring as keyboard
[     2.227] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     2.227] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     2.227] (**) Option "xkb_rules" "evdev"
[     2.227] (**) Option "xkb_model" "pc105"
[     2.227] (**) Option "xkb_layout" "us"
[     2.227] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event7)
[     2.228] (II) No input driver specified, ignoring this device.
[     2.228] (II) This device may have been added with another device file.
[     2.228] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event8)
[     2.228] (II) No input driver specified, ignoring this device.
[     2.228] (II) This device may have been added with another device file.
[     2.228] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[     2.228] (II) No input driver specified, ignoring this device.
[     2.228] (II) This device may have been added with another device file.
[     2.228] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event2)
[     2.228] (II) No input driver specified, ignoring this device.
[     2.228] (II) This device may have been added with another device file.
[     2.228] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event3)
[     2.228] (II) No input driver specified, ignoring this device.
[     2.228] (II) This device may have been added with another device file.
[     2.228] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event4)
[     2.228] (II) No input driver specified, ignoring this device.
[     2.228] (II) This device may have been added with another device file.
[     2.228] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event5)
[     2.228] (II) No input driver specified, ignoring this device.
[     2.228] (II) This device may have been added with another device file.
[     2.228] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event6)
[     2.228] (II) No input driver specified, ignoring this device.
[     2.228] (II) This device may have been added with another device file.
[     2.229] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event10)
[     2.229] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     2.229] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     2.229] (**) Eee PC WMI hotkeys: always reports core events
[     2.229] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event10"
[     2.229] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     2.229] (--) evdev: Eee PC WMI hotkeys: Found keys
[     2.229] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     2.229] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input13/event10"
[     2.229] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 8)
[     2.229] (**) Option "xkb_rules" "evdev"
[     2.229] (**) Option "xkb_model" "pc105"
[     2.229] (**) Option "xkb_layout" "us"
[     2.231] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[    14.793] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4031 (/dev/input/mouse0)
[    14.793] (II) No input driver specified, ignoring this device.
[    14.793] (II) This device may have been added with another device file.
[    14.793] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:4031 (/dev/input/event11)
[    14.793] (**) Logitech Unifying Device. Wireless PID:4031: Applying InputClass "evdev pointer catchall"
[    14.793] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:4031'
[    14.793] (**) Logitech Unifying Device. Wireless PID:4031: always reports core events
[    14.793] (**) evdev: Logitech Unifying Device. Wireless PID:4031: Device: "/dev/input/event11"
[    14.793] (--) evdev: Logitech Unifying Device. Wireless PID:4031: Vendor 0x46d Product 0xc52b
[    14.793] (--) evdev: Logitech Unifying Device. Wireless PID:4031: Found 20 mouse buttons
[    14.793] (--) evdev: Logitech Unifying Device. Wireless PID:4031: Found scroll wheel(s)
[    14.793] (--) evdev: Logitech Unifying Device. Wireless PID:4031: Found relative axes
[    14.793] (--) evdev: Logitech Unifying Device. Wireless PID:4031: Found x and y relative axes
[    14.793] (II) evdev: Logitech Unifying Device. Wireless PID:4031: Configuring as mouse
[    14.793] (II) evdev: Logitech Unifying Device. Wireless PID:4031: Adding scrollwheel support
[    14.793] (**) evdev: Logitech Unifying Device. Wireless PID:4031: YAxisMapping: buttons 4 and 5
[    14.793] (**) evdev: Logitech Unifying Device. Wireless PID:4031: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.793] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.2/0003:046D:C52B.0003/0003:046D:C52B.0004/input/input14/event11"
[    14.793] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:4031" (type: MOUSE, id 9)
[    14.794] (II) evdev: Logitech Unifying Device. Wireless PID:4031: initialized for relative axes.
[    14.794] (**) Logitech Unifying Device. Wireless PID:4031: (accel) keeping acceleration scheme 1
[    14.794] (**) Logitech Unifying Device. Wireless PID:4031: (accel) acceleration profile 0
[    14.794] (**) Logitech Unifying Device. Wireless PID:4031: (accel) acceleration factor: 2.000
[    14.794] (**) Logitech Unifying Device. Wireless PID:4031: (accel) acceleration threshold: 4
[    14.797] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400a (/dev/input/mouse1)
[    14.797] (II) No input driver specified, ignoring this device.
[    14.797] (II) This device may have been added with another device file.
[    14.797] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:400a (/dev/input/event13)
[    14.797] (**) Logitech Unifying Device. Wireless PID:400a: Applying InputClass "evdev pointer catchall"
[    14.797] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:400a'
[    14.797] (**) Logitech Unifying Device. Wireless PID:400a: always reports core events
[    14.797] (**) evdev: Logitech Unifying Device. Wireless PID:400a: Device: "/dev/input/event13"
[    14.797] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Vendor 0x46d Product 0xc52b
[    14.797] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found 20 mouse buttons
[    14.797] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found scroll wheel(s)
[    14.797] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found relative axes
[    14.797] (--) evdev: Logitech Unifying Device. Wireless PID:400a: Found x and y relative axes
[    14.797] (II) evdev: Logitech Unifying Device. Wireless PID:400a: Configuring as mouse
[    14.797] (II) evdev: Logitech Unifying Device. Wireless PID:400a: Adding scrollwheel support
[    14.797] (**) evdev: Logitech Unifying Device. Wireless PID:400a: YAxisMapping: buttons 4 and 5
[    14.797] (**) evdev: Logitech Unifying Device. Wireless PID:400a: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.797] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.2/0003:046D:C52B.0003/0003:046D:C52B.0006/input/input16/event13"
[    14.797] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:400a" (type: MOUSE, id 10)
[    14.797] (II) evdev: Logitech Unifying Device. Wireless PID:400a: initialized for relative axes.
[    14.797] (**) Logitech Unifying Device. Wireless PID:400a: (accel) keeping acceleration scheme 1
[    14.797] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration profile 0
[    14.797] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration factor: 2.000
[    14.797] (**) Logitech Unifying Device. Wireless PID:400a: (accel) acceleration threshold: 4
[    14.824] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:2011 (/dev/input/event12)
[    14.824] (**) Logitech Unifying Device. Wireless PID:2011: Applying InputClass "evdev keyboard catchall"
[    14.824] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:2011'
[    14.824] (**) Logitech Unifying Device. Wireless PID:2011: always reports core events
[    14.824] (**) evdev: Logitech Unifying Device. Wireless PID:2011: Device: "/dev/input/event12"
[    14.824] (--) evdev: Logitech Unifying Device. Wireless PID:2011: Vendor 0x46d Product 0xc52b
[    14.824] (--) evdev: Logitech Unifying Device. Wireless PID:2011: Found 1 mouse buttons
[    14.824] (--) evdev: Logitech Unifying Device. Wireless PID:2011: Found scroll wheel(s)
[    14.824] (--) evdev: Logitech Unifying Device. Wireless PID:2011: Found relative axes
[    14.824] (II) evdev: Logitech Unifying Device. Wireless PID:2011: Forcing relative x/y axes to exist.
[    14.824] (--) evdev: Logitech Unifying Device. Wireless PID:2011: Found absolute axes
[    14.824] (II) evdev: Logitech Unifying Device. Wireless PID:2011: Forcing absolute x/y axes to exist.
[    14.824] (--) evdev: Logitech Unifying Device. Wireless PID:2011: Found keys
[    14.824] (II) evdev: Logitech Unifying Device. Wireless PID:2011: Configuring as mouse
[    14.824] (II) evdev: Logitech Unifying Device. Wireless PID:2011: Configuring as keyboard
[    14.824] (II) evdev: Logitech Unifying Device. Wireless PID:2011: Adding scrollwheel support
[    14.824] (**) evdev: Logitech Unifying Device. Wireless PID:2011: YAxisMapping: buttons 4 and 5
[    14.824] (**) evdev: Logitech Unifying Device. Wireless PID:2011: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    14.824] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.2/0003:046D:C52B.0003/0003:046D:C52B.0005/input/input15/event12"
[    14.824] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:2011" (type: KEYBOARD, id 11)
[    14.824] (**) Option "xkb_rules" "evdev"
[    14.824] (**) Option "xkb_model" "pc105"
[    14.824] (**) Option "xkb_layout" "us"
[    14.824] (II) evdev: Logitech Unifying Device. Wireless PID:2011: initialized for relative axes.
[    14.824] (WW) evdev: Logitech Unifying Device. Wireless PID:2011: ignoring absolute axes.
[    14.824] (**) Logitech Unifying Device. Wireless PID:2011: (accel) keeping acceleration scheme 1
[    14.824] (**) Logitech Unifying Device. Wireless PID:2011: (accel) acceleration profile 0
[    14.824] (**) Logitech Unifying Device. Wireless PID:2011: (accel) acceleration factor: 2.000
[    14.824] (**) Logitech Unifying Device. Wireless PID:2011: (accel) acceleration threshold: 4
[    17.417] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.690] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.701] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    18.002] (II) XKB: reuse xkmfile /var/lib/xkb/server-7C75F152E85183199599C3E0B919739C0EE668AA.xkm
rebert@rebert-4790:~$

---

