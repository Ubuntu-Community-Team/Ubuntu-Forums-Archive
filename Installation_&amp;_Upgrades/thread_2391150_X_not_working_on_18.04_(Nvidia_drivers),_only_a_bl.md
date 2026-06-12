---
title: "X not working on 18.04 (Nvidia drivers), only a black screen  displayed"
date: 2018-05-06
forum: Installation &amp; Upgrades
---

### Post by egandt on 2018-05-06
Simply put while X "starts" on my laptop I get no display and nothing can be drawn (I get a black screen or a black screen with a cursor flashing), but nothing else.
I've tried lightdm and sddm both behave the same.
I've tried removing the xorg.conf from /etc/X11/ and rebuilding no success.
I've tired clearing /usr/share/X11/xorg.conf.d/ only to make matter worse.

Normally when X does not work you know why and it crashes in this case it is starting, but doing nothing.  The log file is of no help either.
I've even tried removing and reinstalling Nvidia 390 drivers without success.

I can do init 3 and then manually run X (that crashes) or startx with works.  However this is not display and while I can export DISPLAY=:0.0 and tehn run xterm it is not shown anywhere.
It is as if there is a second display that is being used (but there is no such display).

Running X processes:
```

root@laptop:~# ps -ef | grep X
root      1446  1412  0 11:07 tty7     00:00:00 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      2482  2468  0 11:14 pts/0    00:00:00 grep --color=auto X
root@laptop:~# ps -ef | grep lightdm
root      1412     1  0 11:07 ?        00:00:00 /usr/sbin/lightdm
root      1446  1412  0 11:07 tty7     00:00:00 /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch
root      1562  1412  0 11:07 ?        00:00:00 lightdm --session-child 17 20
lightdm   1583     1  0 11:07 ?        00:00:00 /lib/systemd/systemd --user
lightdm   1584  1583  0 11:07 ?        00:00:00 (sd-pam)
lightdm   1615  1562  0 11:07 ?        00:00:00 /bin/sh /usr/lib/lightdm/lightdm-greeter-session /usr/sbin/lightdm-gtk-greeter
lightdm   1616  1615  0 11:07 ?        00:00:00 /usr/sbin/lightdm-gtk-greeter
lightdm   1619  1583  0 11:07 ?        00:00:00 /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
lightdm   1620  1583  0 11:07 ?        00:00:00 /usr/lib/at-spi2-core/at-spi-bus-launcher
lightdm   1625  1620  0 11:07 ?        00:00:00 /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-address 3
lightdm   1627  1583  0 11:07 ?        00:00:00 /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
lightdm   1631  1583  0 11:07 ?        00:00:00 /usr/lib/gvfs/gvfsd
lightdm   1636  1583  0 11:07 ?        00:00:00 /usr/lib/gvfs/gvfsd-fuse /run/user/117/gvfs -f -o big_writes
root      2355  1412  0 11:08 ?        00:00:00 lightdm --session-child 13 20
root      2484  2468  0 11:14 pts/0    00:00:00 grep --color=auto lightdm

```
As you can see both lightdm and X are running, but nothing is presented on screen  to use I have to work from a second machine to do anything.


This is what X logs on startup (again I see no errors):
```

[     8.498] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[     8.498] X Protocol Version 11, Revision 0
[     8.498] Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
[     8.498] Current Operating System: Linux egandt-laptop 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64
[     8.498] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-20-generic root=UUID=b35a2de4-8ca4-4a05-afba-a1bc1e1d2a9e ro
[     8.498] Build Date: 13 April 2018  08:07:36PM
[     8.498] xorg-server 2:1.19.6-1ubuntu4 (For technical support please see http://www.ubuntu.com/support) 
[     8.498] Current version of pixman: 0.34.0
[     8.498] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[     8.498] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     8.498] (==) Log file: "/var/log/Xorg.0.log", Time: Sun May  6 11:02:03 2018
[     8.498] (==) Using config file: "/etc/X11/xorg.conf"
[     8.498] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     8.500] (==) ServerLayout "Layout0"
[     8.500] (**) |-->Screen "Screen0" (0)
[     8.500] (**) |   |-->Monitor "Monitor0"
[     8.501] (**) |   |-->Device "Device0"
[     8.501] (**) |   |-->GPUDevice "Device0"
[     8.501] (**) |-->Input Device "Keyboard0"
[     8.501] (**) |-->Input Device "Mouse0"
[     8.501] (==) Automatically adding devices
[     8.501] (==) Automatically enabling devices
[     8.501] (==) Automatically adding GPU devices
[     8.501] (==) Automatically binding GPU devices
[     8.501] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     8.503] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     8.503] 	Entry deleted from font path.
[     8.503] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     8.503] 	Entry deleted from font path.
[     8.503] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     8.503] 	Entry deleted from font path.
[     8.504] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     8.504] 	Entry deleted from font path.
[     8.504] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     8.504] 	Entry deleted from font path.
[     8.504] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[     8.504] (==) ModulePath set to "/usr/lib/xorg/modules"
[     8.504] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     8.504] (WW) Disabling Keyboard0
[     8.504] (WW) Disabling Mouse0
[     8.504] (II) Loader magic: 0x563e49a49020
[     8.504] (II) Module ABI versions:
[     8.504] 	X.Org ANSI C Emulation: 0.4
[     8.504] 	X.Org Video Driver: 23.0
[     8.504] 	X.Org XInput driver : 24.1
[     8.504] 	X.Org Server Extension : 10.0
[     8.504] (++) using VT number 7

[     8.504] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     8.505] (II) xfree86: Adding drm device (/dev/dri/card1)
[     8.505] (II) xfree86: Adding drm device (/dev/dri/card0)
[     8.510] (**) OutputClass "nvidia" ModulePath extended to "/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
[     8.510] (**) OutputClass "Nvidia Prime" ModulePath extended to "/x86_64-linux-gnu/nvidia/xorg,/usr/lib/x86_64-linux-gnu/nvidia/xorg,/usr/lib/xorg/modules"
[     8.510] (**) OutputClass "Nvidia Prime" setting /dev/dri/card1 as PrimaryGPU
[     8.510] (--) PCI: (0:0:2:0) 8086:591b:1558:8503 rev 4, Mem @ 0xdd000000/16777216, 0xa0000000/536870912, I/O @ 0x0000f000/64, BIOS @ 0x????????/131072
[     8.510] (--) PCI:*(0:1:0:0) 10de:1c20:1558:8503 rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     8.510] (II) LoadModule: "glx"
[     8.511] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/libglx.so
[     8.542] (II) Module glx: vendor="NVIDIA Corporation"
[     8.542] 	compiled for 4.0.2, module version = 1.0.0
[     8.542] 	Module class: X.Org Server Extension
[     8.543] (II) NVIDIA GLX Module  390.48  Wed Mar 21 23:42:56 PDT 2018
[     8.543] (II) LoadModule: "nvidia"
[     8.543] (II) Loading /usr/lib/x86_64-linux-gnu/nvidia/xorg/nvidia_drv.so
[     8.547] (II) Module nvidia: vendor="NVIDIA Corporation"
[     8.547] 	compiled for 4.0.2, module version = 1.0.0
[     8.547] 	Module class: X.Org Video Driver
[     8.547] (II) NVIDIA dlloader X Driver  390.48  Wed Mar 21 23:18:15 PDT 2018
[     8.547] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     8.554] (II) Loading sub module "fb"
[     8.554] (II) LoadModule: "fb"
[     8.556] (II) Loading /usr/lib/xorg/modules/libfb.so
[     8.556] (II) Module fb: vendor="X.Org Foundation"
[     8.556] 	compiled for 1.19.6, module version = 1.0.0
[     8.556] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     8.556] (II) Loading sub module "wfb"
[     8.556] (II) LoadModule: "wfb"
[     8.556] (II) Loading /usr/lib/xorg/modules/libwfb.so
[     8.557] (II) Module wfb: vendor="X.Org Foundation"
[     8.557] 	compiled for 1.19.6, module version = 1.0.0
[     8.557] 	ABI class: X.Org ANSI C Emulation, version 0.4
[     8.557] (II) Loading sub module "ramdac"
[     8.557] (II) LoadModule: "ramdac"
[     8.557] (II) Module "ramdac" already built-in
[     8.558] (**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
[     8.558] (==) NVIDIA(0): RGB weight 888
[     8.558] (==) NVIDIA(0): Default visual is TrueColor
[     8.558] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[     8.559] (II) Applying OutputClass "nvidia" options to /dev/dri/card1
[     8.559] (II) Applying OutputClass "Nvidia Prime" options to /dev/dri/card1
[     8.559] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration"
[     8.559] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[     8.559] (**) NVIDIA(0): Enabling 2D acceleration
[     9.087] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[     9.087] (--) NVIDIA(0):     DFP-0
[     9.087] (--) NVIDIA(0):     DFP-1
[     9.087] (--) NVIDIA(0):     DFP-2
[     9.093] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 1060 (GP106-A) at PCI:1:0:0 (GPU-0)
[     9.093] (--) NVIDIA(0): Memory: 6291456 kBytes
[     9.093] (--) NVIDIA(0): VideoBIOS: 86.06.4f.00.03
[     9.093] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[     9.093] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     9.093] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     9.093] (--) NVIDIA(GPU-0): DFP-0: 165.0 MHz maximum pixel clock
[     9.093] (--) NVIDIA(GPU-0): 
[     9.093] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.093] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[     9.093] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[     9.093] (--) NVIDIA(GPU-0): 
[     9.093] (--) NVIDIA(GPU-0): DFP-2: disconnected
[     9.093] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[     9.093] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[     9.093] (--) NVIDIA(GPU-0): 
[     9.093] (==) NVIDIA(0): 
[     9.093] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[     9.093] (==) NVIDIA(0):     will be used as the requested mode.
[     9.093] (==) NVIDIA(0): 
[     9.094] (--) NVIDIA(0): No enabled display devices found; starting anyway because
[     9.094] (--) NVIDIA(0):     AllowEmptyInitialConfiguration is enabled
[     9.094] (II) NVIDIA(0): Validated MetaModes:
[     9.094] (II) NVIDIA(0):     "NULL"
[     9.094] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[     9.094] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[     9.094] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[     9.094] (--) Depth 24 pixmap format is 32 bpp
[     9.094] (II) NVIDIA: Using 24576.00 MB of virtual memory for indirect memory
[     9.094] (II) NVIDIA:     access.
[     9.128] (II) NVIDIA(0): Setting mode "NULL"
[     9.134] (==) NVIDIA(0): Disabling shared memory pixmaps
[     9.134] (==) NVIDIA(0): Backing store enabled
[     9.134] (==) NVIDIA(0): Silken mouse enabled
[     9.135] (**) NVIDIA(0): DPMS enabled
[     9.135] (WW) NVIDIA(0): Option "PrimaryGPU" is not used
[     9.135] (II) Loading sub module "dri2"
[     9.135] (II) LoadModule: "dri2"
[     9.135] (II) Module "dri2" already built-in
[     9.135] (II) NVIDIA(0): [DRI2] Setup complete
[     9.135] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[     9.135] (--) RandR disabled
[     9.137] (II) SELinux: Disabled on system
[     9.137] (II) Initializing extension GLX
[     9.137] (II) Indirect GLX disabled.
[     9.173] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[     9.173] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     9.173] (II) LoadModule: "libinput"
[     9.174] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[     9.176] (II) Module libinput: vendor="X.Org Foundation"
[     9.176] 	compiled for 1.19.6, module version = 0.27.1
[     9.176] 	Module class: X.Org XInput Driver
[     9.176] 	ABI class: X.Org XInput driver, version 24.1
[     9.176] (II) Using input driver 'libinput' for 'Power Button'
[     9.176] (**) Power Button: always reports core events
[     9.176] (**) Option "Device" "/dev/input/event3"
[     9.176] (**) Option "_source" "server/udev"
[     9.176] (II) event3  - Power Button: is tagged by udev as: Keyboard
[     9.176] (II) event3  - Power Button: device is a keyboard
[     9.176] (II) event3  - Power Button: device removed
[     9.196] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[     9.196] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     9.196] (**) Option "xkb_model" "pc105"
[     9.196] (**) Option "xkb_layout" "us"
[     9.196] (II) event3  - Power Button: is tagged by udev as: Keyboard
[     9.196] (II) event3  - Power Button: device is a keyboard
[     9.197] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[     9.197] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[     9.197] (II) Using input driver 'libinput' for 'Video Bus'
[     9.197] (**) Video Bus: always reports core events
[     9.197] (**) Option "Device" "/dev/input/event5"
[     9.197] (**) Option "_source" "server/udev"
[     9.197] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[     9.197] (II) event5  - Video Bus: device is a keyboard
[     9.197] (II) event5  - Video Bus: device removed
[     9.216] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input11/event5"
[     9.216] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     9.216] (**) Option "xkb_model" "pc105"
[     9.216] (**) Option "xkb_layout" "us"
[     9.216] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[     9.216] (II) event5  - Video Bus: device is a keyboard
[     9.216] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[     9.216] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[     9.216] (II) Using input driver 'libinput' for 'Video Bus'
[     9.216] (**) Video Bus: always reports core events
[     9.216] (**) Option "Device" "/dev/input/event6"
[     9.216] (**) Option "_source" "server/udev"
[     9.217] (II) event6  - Video Bus: is tagged by udev as: Keyboard
[     9.217] (II) event6  - Video Bus: device is a keyboard
[     9.217] (II) event6  - Video Bus: device removed
[     9.240] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:12/LNXVIDEO:01/input/input12/event6"
[     9.240] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[     9.240] (**) Option "xkb_model" "pc105"
[     9.240] (**) Option "xkb_layout" "us"
[     9.240] (II) event6  - Video Bus: is tagged by udev as: Keyboard
[     9.240] (II) event6  - Video Bus: device is a keyboard
[     9.240] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     9.240] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     9.240] (II) Using input driver 'libinput' for 'Power Button'
[     9.240] (**) Power Button: always reports core events
[     9.240] (**) Option "Device" "/dev/input/event0"
[     9.240] (**) Option "_source" "server/udev"
[     9.240] (II) event0  - Power Button: is tagged by udev as: Keyboard
[     9.240] (II) event0  - Power Button: device is a keyboard
[     9.241] (II) event0  - Power Button: device removed
[     9.264] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[     9.264] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[     9.264] (**) Option "xkb_model" "pc105"
[     9.264] (**) Option "xkb_layout" "us"
[     9.264] (II) event0  - Power Button: is tagged by udev as: Keyboard
[     9.264] (II) event0  - Power Button: device is a keyboard
[     9.264] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[     9.264] (II) No input driver specified, ignoring this device.
[     9.264] (II) This device may have been added with another device file.
[     9.264] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[     9.264] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[     9.264] (II) Using input driver 'libinput' for 'Sleep Button'
[     9.264] (**) Sleep Button: always reports core events
[     9.264] (**) Option "Device" "/dev/input/event1"
[     9.264] (**) Option "_source" "server/udev"
[     9.265] (II) event1  - Sleep Button: is tagged by udev as: Keyboard
[     9.265] (II) event1  - Sleep Button: device is a keyboard
[     9.265] (II) event1  - Sleep Button: device removed
[     9.280] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[     9.280] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[     9.280] (**) Option "xkb_model" "pc105"
[     9.280] (**) Option "xkb_layout" "us"
[     9.280] (II) event1  - Sleep Button: is tagged by udev as: Keyboard
[     9.280] (II) event1  - Sleep Button: device is a keyboard
[     9.280] (II) config/udev: Adding input device Chicony USB 2.0 Camera: Chicony (/dev/input/event8)
[     9.280] (**) Chicony USB 2.0 Camera: Chicony: Applying InputClass "libinput keyboard catchall"
[     9.280] (II) Using input driver 'libinput' for 'Chicony USB 2.0 Camera: Chicony'
[     9.280] (**) Chicony USB 2.0 Camera: Chicony: always reports core events
[     9.280] (**) Option "Device" "/dev/input/event8"
[     9.280] (**) Option "_source" "server/udev"
[     9.281] (II) event8  - Chicony USB 2.0 Camera: Chicony: is tagged by udev as: Keyboard
[     9.281] (II) event8  - Chicony USB 2.0 Camera: Chicony: device is a keyboard
[     9.281] (II) event8  - Chicony USB 2.0 Camera: Chicony: device removed
[     9.312] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2/1-2:1.0/input/input15/event8"
[     9.312] (II) XINPUT: Adding extended input device "Chicony USB 2.0 Camera: Chicony" (type: KEYBOARD, id 11)
[     9.312] (**) Option "xkb_model" "pc105"
[     9.312] (**) Option "xkb_layout" "us"
[     9.312] (II) event8  - Chicony USB 2.0 Camera: Chicony: is tagged by udev as: Keyboard
[     9.312] (II) event8  - Chicony USB 2.0 Camera: Chicony: device is a keyboard
[     9.312] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event9)
[     9.312] (II) No input driver specified, ignoring this device.
[     9.312] (II) This device may have been added with another device file.
[     9.313] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[     9.313] (II) No input driver specified, ignoring this device.
[     9.313] (II) This device may have been added with another device file.
[     9.313] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[     9.313] (II) No input driver specified, ignoring this device.
[     9.313] (II) This device may have been added with another device file.
[     9.313] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event12)
[     9.313] (II) No input driver specified, ignoring this device.
[     9.313] (II) This device may have been added with another device file.
[     9.313] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event13)
[     9.313] (II) No input driver specified, ignoring this device.
[     9.313] (II) This device may have been added with another device file.
[     9.313] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=9 (/dev/input/event14)
[     9.313] (II) No input driver specified, ignoring this device.
[     9.313] (II) This device may have been added with another device file.
[     9.313] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=10 (/dev/input/event15)
[     9.313] (II) No input driver specified, ignoring this device.
[     9.313] (II) This device may have been added with another device file.
[     9.314] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[     9.314] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[     9.314] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[     9.314] (**) AT Translated Set 2 keyboard: always reports core events
[     9.314] (**) Option "Device" "/dev/input/event4"
[     9.314] (**) Option "_source" "server/udev"
[     9.314] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[     9.314] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[     9.314] (II) event4  - AT Translated Set 2 keyboard: device removed
[     9.328] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[     9.328] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[     9.328] (**) Option "xkb_model" "pc105"
[     9.328] (**) Option "xkb_layout" "us"
[     9.328] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[     9.328] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[     9.328] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[     9.328] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "libinput touchpad catchall"
[     9.328] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     9.328] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     9.328] (II) LoadModule: "synaptics"
[     9.328] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     9.330] (II) Module synaptics: vendor="X.Org Foundation"
[     9.330] 	compiled for 1.19.3, module version = 1.9.0
[     9.330] 	Module class: X.Org XInput Driver
[     9.330] 	ABI class: X.Org XInput driver, version 24.1
[     9.330] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     9.330] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     9.330] (**) Option "Device" "/dev/input/event7"
[     9.368] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1266 - 5674 (res 45)
[     9.368] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1086 - 4764 (res 70)
[     9.368] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     9.368] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     9.368] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     9.368] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     9.368] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     9.368] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     9.400] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event7"
[     9.400] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[     9.400] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     9.400] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     9.400] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[     9.400] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     9.400] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     9.400] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     9.400] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     9.400] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     9.400] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[     9.400] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     9.411] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     9.411] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     9.411] (--) NVIDIA(GPU-0): DFP-0: 165.0 MHz maximum pixel clock
[     9.411] (--) NVIDIA(GPU-0): 
[     9.411] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.411] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[     9.411] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[     9.411] (--) NVIDIA(GPU-0): 
[     9.411] (--) NVIDIA(GPU-0): DFP-2: disconnected
[     9.411] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[     9.411] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[     9.411] (--) NVIDIA(GPU-0): 
[     9.417] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     9.417] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     9.417] (--) NVIDIA(GPU-0): DFP-0: 165.0 MHz maximum pixel clock
[     9.417] (--) NVIDIA(GPU-0): 
[     9.417] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.417] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[     9.417] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[     9.417] (--) NVIDIA(GPU-0): 
[     9.418] (--) NVIDIA(GPU-0): DFP-2: disconnected
[     9.418] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[     9.418] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[     9.418] (--) NVIDIA(GPU-0): 
[     9.418] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     9.418] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     9.418] (--) NVIDIA(GPU-0): DFP-0: 165.0 MHz maximum pixel clock
[     9.418] (--) NVIDIA(GPU-0): 
[     9.418] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.418] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[     9.418] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[     9.418] (--) NVIDIA(GPU-0): 
[     9.418] (--) NVIDIA(GPU-0): DFP-2: disconnected
[     9.418] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[     9.418] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[     9.418] (--) NVIDIA(GPU-0): 
[     9.427] (--) NVIDIA(GPU-0): DFP-0: disconnected
[     9.427] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[     9.427] (--) NVIDIA(GPU-0): DFP-0: 165.0 MHz maximum pixel clock
[     9.427] (--) NVIDIA(GPU-0): 
[     9.427] (--) NVIDIA(GPU-0): DFP-1: disconnected
[     9.427] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[     9.427] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[     9.427] (--) NVIDIA(GPU-0): 
[     9.427] (--) NVIDIA(GPU-0): DFP-2: disconnected
[     9.427] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[     9.427] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[     9.427] (--) NVIDIA(GPU-0): 
[    25.406] (II) event3  - Power Button: device removed
[    25.420] (II) event5  - Video Bus: device removed
[    25.436] (II) event6  - Video Bus: device removed
[    25.452] (II) event0  - Power Button: device removed
[    25.468] (II) event1  - Sleep Button: device removed
[    25.484] (II) event8  - Chicony USB 2.0 Camera: Chicony: device removed
[    25.516] (II) event4  - AT Translated Set 2 keyboard: device removed
[    38.336] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    38.336] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    38.336] (--) NVIDIA(GPU-0): DFP-0: 165.0 MHz maximum pixel clock
[    38.337] (--) NVIDIA(GPU-0): 
[    38.337] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    38.337] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    38.337] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    38.337] (--) NVIDIA(GPU-0): 
[    38.337] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    38.337] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    38.337] (--) NVIDIA(GPU-0): DFP-2: 165.0 MHz maximum pixel clock
[    38.337] (--) NVIDIA(GPU-0): 
[    38.351] (II) NVIDIA(0): Setting mode "NULL"
[    38.387] (II) event3  - Power Button: is tagged by udev as: Keyboard
[    38.387] (II) event3  - Power Button: device is a keyboard
[    38.387] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[    38.387] (II) event5  - Video Bus: device is a keyboard
[    38.387] (II) event6  - Video Bus: is tagged by udev as: Keyboard
[    38.387] (II) event6  - Video Bus: device is a keyboard
[    38.387] (II) event0  - Power Button: is tagged by udev as: Keyboard
[    38.387] (II) event0  - Power Button: device is a keyboard
[    38.388] (II) event1  - Sleep Button: is tagged by udev as: Keyboard
[    38.388] (II) event1  - Sleep Button: device is a keyboard
[    38.388] (II) event8  - Chicony USB 2.0 Camera: Chicony: is tagged by udev as: Keyboard
[    38.388] (II) event8  - Chicony USB 2.0 Camera: Chicony: device is a keyboard
[    38.388] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[    38.388] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard
[    38.388] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    41.831] (II) event3  - Power Button: device removed
[    41.844] (II) event5  - Video Bus: device removed
[    41.860] (II) event6  - Video Bus: device removed
[    41.876] (II) event0  - Power Button: device removed
[    41.892] (II) event1  - Sleep Button: device removed
[    41.908] (II) event8  - Chicony USB 2.0 Camera: Chicony: device removed
[    41.940] (II) event4  - AT Translated Set 2 keyboard: device removed
[    82.553] (II) config/udev: Adding input device MX Master (/dev/input/mouse1)
[    82.554] (II) No input driver specified, ignoring this device.
[    82.554] (II) This device may have been added with another device file.
[    82.595] (II) config/udev: Adding input device MX Master (/dev/input/event16)
[    82.595] (**) MX Master: Applying InputClass "libinput pointer catchall"
[    82.595] (**) MX Master: Applying InputClass "libinput keyboard catchall"
[    82.595] (II) Using input driver 'libinput' for 'MX Master'
[    82.595] (**) MX Master: always reports core events
[    82.595] (**) Option "Device" "/dev/input/event16"
[    82.595] (**) Option "_source" "server/udev"
[    82.595] (II) event16 - MX Master: is tagged by udev as: Keyboard Mouse
[    82.595] (II) event16 - MX Master: device is a pointer
[    82.595] (II) event16 - MX Master: device is a keyboard
[    82.595] (II) event16 - MX Master: device removed
[    82.616] (II) libinput: MX Master: needs a virtual subdevice
[    82.616] (**) Option "config_info" "udev:/sys/devices/virtual/misc/uhid/0005:046D:B017.0001/input/input23/event16"
[    82.616] (II) XINPUT: Adding extended input device "MX Master" (type: MOUSE, id 14)
[    82.616] (**) Option "AccelerationScheme" "none"
[    82.616] (**) MX Master: (accel) selected scheme none/0
[    82.616] (**) MX Master: (accel) acceleration factor: 2.000
[    82.616] (**) MX Master: (accel) acceleration threshold: 4
[    82.616] (**) MX Master: Applying InputClass "libinput pointer catchall"
[    82.616] (**) MX Master: Applying InputClass "libinput keyboard catchall"
[    82.616] (II) Using input driver 'libinput' for 'MX Master'
[    82.616] (**) MX Master: always reports core events
[    82.616] (**) Option "Device" "/dev/input/event16"
[    82.616] (**) Option "_source" "_driver/libinput"
[    82.616] (II) libinput: MX Master: is a virtual subdevice
[    82.616] (EE) libinput: MX Master: Parent device not available
[    82.616] (II) event16 - MX Master: is tagged by udev as: Keyboard Mouse
[    82.616] (II) event16 - MX Master: device is a pointer
[    82.616] (II) event16 - MX Master: device is a keyboard
[    82.616] (II) event16 - MX Master: device removed
[    82.636] (**) Option "config_info" "udev:/sys/devices/virtual/misc/uhid/0005:046D:B017.0001/input/input23/event16"
[    82.636] (II) XINPUT: Adding extended input device "MX Master" (type: KEYBOARD, id 15)
[    82.636] (**) Option "xkb_model" "pc105"
[    82.636] (**) Option "xkb_layout" "us"
[    82.636] (WW) Option "xkb_variant" requires a string value
[    82.636] (WW) Option "xkb_options" requires a string value

```

Any ideas?
ERIC

---

### Post by egandt on 2018-05-08
Tracked the root cause to DisplayLink 4.2 drivers, but no idea what they are doing that triggers this.

ERIC

---

### Post by sanzante on 2018-05-08
Same problem here, I've just updated to Kubuntu 18.04. The laptop screen is not detected, but my second screen is working fine. If I unplug the second monitor laptop screen remains undetected.

Using Nvidia driver 390.48.

---

### Post by #&amp;thj^% on 2018-05-08
If related this has been an issue since 17.10 and now forward:
If you are already logged in to your Desktop, open a konsole and type:
```
sudo dpkg-reconfigure sddm
```
and select "sddm". Log out/reboot and see if things are as they should be. 
If you can not get to a Desktop session try to reach a TTY via: Keyboard combo <ctrl +F2> and run the code provided.
Good Luck

---

### Post by sanzante on 2018-05-08
Thanks for the suggestion 1fallen, but the problem remains. I've reconfigured the packaged, logout and login and same behavior. I've tried restarting sddm, no luck

When reconfiguring, dpkg asked me to select default login manager, I selected sddm.

---

### Post by #&amp;thj^% on 2018-05-08
> **sanzante said:**
> Thanks for the suggestion 1fallen, but the problem remains. I've reconfigured the packaged, logout and login and same behavior. I've tried restarting sddm, no luck

When reconfiguring, dpkg asked me to select default login manager, I selected sddm.
Yes it was a shot in the dark, but has worked for others though so I thought we would give it shot here also, as there is no harm to the system.
I had in early development ran into similar login problems with adding the Nvidia Drivers and GDM but that strays from the topic here. ;) 
I'm a big fan of tweaking my setup, again off topic but worth noting that things are very sweet with my rig now.
```
 apt policy nvidia-driver-390
nvidia-driver-390:
  Installed: 390.48-0ubuntu3
  Candidate: 390.48-0ubuntu3
  Version table:
 *** 390.48-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu bionic/restricted amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by sanzante on 2018-05-12
I've solved my issue following instructions here: [https://devtalk.nvidia.com/default/topic/1033140/kubuntu-18-04-gives-black-screen-when-sddm-starts-no-login-/?offset=6](https://devtalk.nvidia.com/default/topic/1033140/kubuntu-18-04-gives-black-screen-when-sddm-starts-no-login-/?offset=6)

In short:

1) Select nvidia sudo prime-select nvidia)
2) Make sure you have those lines at the end of /usr/share/sddm/scripts/Xsetup 
```
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto

``` 

My file now looks like this:
```
#!/bin/sh# Xsetup - run as root before the login dialog appears


if [ -e /sbin/prime-offload ]; then
    echo running NVIDIA Prime setup /sbin/prime-offload
    /sbin/prime-offload
fi
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto

```

3) Check your /etc/X11/xorg.conf. I had Driver "nvidia' in Driver section commented (not sure why). It should look like this:

I've solved my issue following instructions here: [https://devtalk.nvidia.com/default/topic/1033140/kubuntu-18-04-gives-black-screen-when-sddm-starts-no-login-/?offset=6](https://devtalk.nvidia.com/default/topic/1033140/kubuntu-18-04-gives-black-screen-when-sddm-starts-no-login-/?offset=6)

In short:

1) Select nvidia sudo prime-select nvidia)
2) Make sure you have those lines at the end of /usr/share/sddm/scripts/Xsetup 
```
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto

``` 

My file now looks like this:
```
#!/bin/sh# Xsetup - run as root before the login dialog appears


if [ -e /sbin/prime-offload ]; then
    echo running NVIDIA Prime setup /sbin/prime-offload
    /sbin/prime-offload
fi
xrandr --setprovideroutputsource modesetting NVIDIA-0
xrandr --auto

```

3) Check your /etc/X11/xorg.conf. I had Driver "nvidia' in Driver section commented (not sure why). It should look like this:
```

Section "ServerLayout"
    Identifier     "layout"
    Screen      0  "nvidia" 0 0
    Inactive       "intel"
EndSection


Section "Monitor"
    Identifier     "Monitor0"
    Modeline "1280x720_60.00"  74.48  1280 1336 1472 1664  720 721 724 746  -HSync +Vsync
EndSection


Section "Device"
    Identifier     "intel"
    Driver         "modesetting"
    Option         "AccelMethod" "none"
    BusID          "PCI:0:2:0"
EndSection


Section "Device"
    Identifier     "nvidia"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BusID          "PCI:1:0:0"
    Option         "AllowEmptyInitialConfiguration"
EndSection


Section "Screen"
    Identifier     "nvidia"
    Device         "nvidia"
    Monitor        "Monitor0"
    SubSection     "Display"
        Virtual     1920 1080
    EndSubSection
EndSection

```

---

