---
title: "Karmic: nvidia drivers crashed"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2010-03-24
I use the sleep function on a timer. Unfortunately recently it has become faulty and  I have found that I could not wake the computer up and so had to do resets. This seems to have caused the nvidia drivers to be damaged and I now can not use my dual screens. 

I have tried help suggested in other threads but I am not succeeding.

The xorg.0.log shows 

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux rob-desktop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686
Kernel command line: root=UUID=3fb00645-ed14-46fa-a0b4-5c384add8c90 ro quiet splash irqpoll rootflags=data=writeback 
Build Date: 04 March 2010  09:56:47AM
xorg-server 2:1.6.4-2ubuntu4.2 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 24 14:02:44 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:0392:107d:2a52 nVidia Corporation G73 [GeForce 7600 GS] rev 161, Mem @ 0xf4000000/16777216, 0xe0000000/268435456, 0xf5000000/16777216, I/O @ 0x0000a000/128, BIOS @ 0x????????/131072
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(WW) "dri2" will not be loaded unless you've specified it to be loaded elsewhere.
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded even though the default is to disable it.
(II) LoadModule: "glx"
(WW) Warning, couldn't open module glx
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (module does not exist, 0)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(WW) Warning, couldn't open module nvidia
(II) UnloadModule: "nvidia"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.
```

My first symptom shows up at Hardware drivers. When I activate nvidia-195 it downloads but fails to install with an error message: System error: installArchives() failed. I can get no further in hardware drivers.

Second symptom: 

I found this instruction elsewhere :

>  sudo add-apt-repository ppa:nvidia-vdpau/ppa && sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767 && sudo apt-get update && sudo apt-get install nvidia-glx-195 && sudo nvidia-xconfig && sudo reboot


It worked with no error:

Third Symptom: Synaptic
The following nvidia files are the only ones installed:

xserver-xorg-video-nv
nv-kernel-common
nv-settings
nv-195-kernel-source
nv-195-modaliases
nv-195-libvdpau
sensors-applet
jockey-gtk
jockey-common
libvdpau1
vdpau-driver-all
nv-common

in the missing recommendations section of synaptic it suggests I install:

nv-glx-195 but the installation  fails with the following:

> E: /var/cache/apt/archives/nvidia-glx-195_195.36.15-0ubuntu1~karmic~nvidiavdpauppa2_i386.deb: trying to overwrite '/usr/lib/libvdpau_nvidia.so', which is also in package nvidia-195-libvdpau 0

also in the missing recommendations are a number of nv-xxx-kernel-sources. I have not tried to install them.

Is it obvious to anyone what I need to do to get the glx installed and the nvidia-195 activated?

---

### Post by Robbyx on 2010-03-24
Because I need to have the two screens working I have been trying all sorts of recommendations to have them working. What should I do to correct this:

> E: /var/cache/apt/archives/nvidia-195-libvdpau_195.36.08-0ubuntu3_i386.deb: trying to overwrite '/usr/lib/libvdpau_nvidia.so', which is also in package nvidia-glx-195 0

---

### Post by Robbyx on 2010-03-24
I got it working but I do not know how. I did so much. Started the machine and the dual screens were back again. The strange thing is it worked after failing to activate the driver in hardware drivers. One of the things I did was to purge the system the other was to use EnvyNG (it did not sort out the installation but when I removed the nvidia drivers with it, it cleaned them out better than via synaptic.

---

