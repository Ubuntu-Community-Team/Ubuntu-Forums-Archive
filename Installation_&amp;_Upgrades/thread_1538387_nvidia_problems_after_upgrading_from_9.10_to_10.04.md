---
title: "nvidia problems after upgrading from 9.10 to 10.04"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by mcsmith on 2010-07-25
I've recently updated my system from 9.10 to 10.04, and am experiencing problems with the video driver.  I've tried to follow the solutions offered to others who have faced similar problems, but I've not been successful.  Here's my setup:

System:         HP xw6000
Processors:     2 x Intel Xeon 2.667 GHz
Video Adapter:  nVidia NV25GL [Quadro4 750 XGL]
OS software:    Ubuntu 10.04 32-bit (upgraded from 9.10)

I've tried the legacy nVidia driver (96.43.17-0ubuntu1, as delivered by Ubuntu), and Nouveau, and neither are working.  Trying to fix the problem may have resulted in actually making things worse.  At present, my system boots up to a text login.  When I try to manually start X, I get:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux xw6000 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686
Kernel command line: root=UUID=e4740f9c-b883-4ddb-a449-8b743fea248d ro quiet splash 
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 24 22:47:37 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(EE) Failed to load module "nvidia" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit:  No such file or directory (errno 2):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

The contents of /var/log/Xorg.0.log are:

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux xw6000 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686
Kernel command line: root=UUID=e4740f9c-b883-4ddb-a449-8b743fea248d ro quiet splash 
Build Date: 16 June 2010  09:31:32AM
xorg-server 2:1.7.6-2ubuntu7.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jul 24 17:01:53 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
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
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(--) using VT number 8

(--) PCI:*(0:1:0:0) 10de:0259:10de:0139 nVidia Corporation NV25GL [Quadro4 750 XGL] rev 163, Mem @ 0xf1000000/16777216, 0xe8000000/134217728, 0xf0200000/524288, BIOS @ 0x????????/131072
(--) PCI: (0:5:10:0) 14f1:8800:7063:5500 Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder rev 5, Mem @ 0xdf000000/16777216
(--) PCI: (0:5:11:0) 4444:0016:0070:0009 Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder rev 1, Mem @ 0xe4000000/67108864
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
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
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
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

 ddxSigGiveUp: Closing log

```

At this point I'm just wanting to get X running again.  Taking a pragmatic approach, I'll be happy with either Nouveau or nVidia drivers.  (I don't have a specific need for 3D graphics.)  Since I've hacked around on the system to get either driver to work, I think I've got reminants of both drivers lurking on my system.  I'd like to get rid of the stuff that I don't need (and which may be causing me problems).

Any suggestions?

Thanks,

Mike

---

### Post by efflandt on 2010-07-25
What module(s) does **sudo lspci -v** from text console show that your video is using?

Your old xorg.conf might not be compatible.  Rename (sudo mv) xorg.conf to some other name.  That is not needed for the default nouveau driver. Although, if something nvidia specific loads during boot, that may put you into low graphics mode in X until you sort it out.  Then you could go to System > Hardware Drivers and see what it suggests to activate.

I have a different card (GT220), but the default xorg.conf when I activated nvidia(195) is really simple:

```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Default Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection
```If you have a suitable nvidia version, **sudo nvidia-xconfig** (from text console with X not running) may generate an appropriate xorg.conf.

---

### Post by mcsmith on 2010-07-25
The results of **sudo lspci -v** are:

```

00:00.0 Host bridge: Intel Corporation E7505 Memory Controller Hub (rev 03)
	Subsystem: Hewlett-Packard Company Device 00cc
	Flags: bus master, fast devsel, latency 0
	Memory at f4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [40] Vendor Specific Information <?>
	Capabilities: [a0] AGP version 3.0
	Kernel driver in use: agpgart-intel
	Kernel modules: e7xxx_edac, intel-agp

00:01.0 PCI bridge: Intel Corporation E7505/E7205 PCI-to-AGP Bridge (rev 03)
	Flags: bus master, 66MHz, fast devsel, latency 64
	Memory at f8000000 (32-bit, prefetchable) [size=64M]
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
	Memory behind bridge: f1000000-f21fffff
	Prefetchable memory behind bridge: e8000000-f02fffff
	Capabilities: [60] AGP3 <?>
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
	Subsystem: Hewlett-Packard Company Device 00cc
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 3440 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
	Subsystem: Hewlett-Packard Company Device 00cc
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 3460 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
	Subsystem: Hewlett-Packard Company Device 00cc
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 3480 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Hewlett-Packard Company Device 00cc
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at e3300000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=0080
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=64
	I/O behind bridge: 00001000-00002fff
	Memory behind bridge: df000000-e32fffff
	Prefetchable memory behind bridge: e3e00000-e7ffffff
	Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
	Flags: bus master, medium devsel, latency 0
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Hewlett-Packard Company Device 00cc
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 34c0 [size=16]
	Memory at 40100000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: ata_piix

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 00c3
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 3000 [size=256]
	I/O ports at 3400 [size=64]
	Memory at e3300400 (32-bit, non-prefetchable) [size=512]
	Memory at e3300600 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

01:00.0 VGA compatible controller: nVidia Corporation NV25GL [Quadro4 750 XGL] (rev a3)
	Subsystem: nVidia Corporation Device 0139
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 5
	Memory at f1000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e8000000 (32-bit, prefetchable) [size=128M]
	Memory at f0200000 (32-bit, prefetchable) [size=512K]
	[virtual] Expansion ROM at f0000000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
	Capabilities: [44] AGP version 2.0
	Kernel modules: nvidia-96, nvidiafb, rivafb, nouveau

05:02.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
	Subsystem: Hewlett-Packard Company Device 00cc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 21
	Memory at e3200000 (64-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e3f80000 [disabled] [size=64K]
	Capabilities: [40] PCI-X non-bridge device
	Capabilities: [48] Power Management version 2
	Capabilities: [50] Vital Product Data <?>
	Capabilities: [58] Message Signalled Interrupts: Mask- 64bit+ Queue=0/3 Enable-
	Kernel driver in use: tg3
	Kernel modules: tg3

05:0a.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Subsystem: pcHDTV Device 5500
	Flags: bus master, medium devsel, latency 66, IRQ 18
	Memory at df000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: cx8800
	Kernel modules: cx8800

05:0a.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
	Subsystem: pcHDTV Device 5500
	Flags: bus master, medium devsel, latency 66, IRQ 18
	Memory at e0000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: cx88_audio
	Kernel modules: cx88-alsa

05:0a.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
	Subsystem: pcHDTV Device 5500
	Flags: bus master, medium devsel, latency 66, IRQ 18
	Memory at e1000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2
	Kernel driver in use: cx88-mpeg driver manager
	Kernel modules: cx8802

05:0a.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
	Subsystem: pcHDTV Device 5500
	Flags: bus master, medium devsel, latency 66, IRQ 10
	Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [4c] Power Management version 2

05:0b.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. Device 0009
	Flags: bus master, medium devsel, latency 64, IRQ 21
	Memory at e4000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ivtv
	Kernel modules: ivtv

05:0c.0 SCSI storage controller: Adaptec AIC-7902 U320 (rev 03)
	Subsystem: Hewlett-Packard Company Device 00cc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	I/O ports at 1000 [disabled] [size=256]
	Memory at e3210000 (64-bit, non-prefetchable) [size=8K]
	I/O ports at 1400 [disabled] [size=256]
	[virtual] Expansion ROM at e3e00000 [disabled] [size=512K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [94] PCI-X non-bridge device
	Kernel driver in use: aic79xx
	Kernel modules: aic79xx

05:0c.1 SCSI storage controller: Adaptec AIC-7902 U320 (rev 03)
	Subsystem: Hewlett-Packard Company Device 00cc
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 1800 [disabled] [size=256]
	Memory at e3212000 (64-bit, non-prefetchable) [size=8K]
	I/O ports at 1c00 [disabled] [size=256]
	[virtual] Expansion ROM at e3e80000 [disabled] [size=512K]
	Capabilities: [dc] Power Management version 2
	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
	Capabilities: [94] PCI-X non-bridge device
	Kernel driver in use: aic79xx
	Kernel modules: aic79xx

05:0d.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
	Subsystem: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at 2010 [size=8]
	I/O ports at 2020 [size=4]
	I/O ports at 2018 [size=8]
	I/O ports at 2024 [size=4]
	I/O ports at 2000 [size=16]
	Memory at e3214000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at e3f00000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 2
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil

```

I made a little progress, I got a low resolution ( 1024x768 ) display running.  I believe this was using Nouveau, because System > Hardware Drivers offered me the choice of activating the nvidia 96 driver.  When I did that, I found myself back to the text only display.  After removing nvidia-96 and nvidia-settings, I'm back to the low resolution GUI again.  I re-installed nvidia-96 and nvidia-settings as follows:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  plasma-dataengines-workspace kdepim-runtime libprocessui4 libtaskmanager4 libqimageblitz4 libkscreensaver5 libsolidcontrolifaces4 plasma-widgets-workspace
  libplasma-geolocation-interface4 libksgrd4 kdebase-workspace-bin libkworkspace4 libplasmagenericshell4 libkfontinst4 libkephal4 kdebase-workspace-data ksysguardd
  libplasmaclock4 libweather-ion4 kdebase-workspace-kgreet-plugins libsolidcontrol4 akonadi-server libplasma-applet-system-monitor4 libprocesscore4
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  nvidia-96 nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/8,232kB of archives.
After this operation, 24.3MB of additional disk space will be used.
Selecting previously deselected package nvidia-96.
(Reading database ... 312126 files and directories currently installed.)
Unpacking nvidia-96 (from .../nvidia-96_96.43.17-0ubuntu1_i386.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up nvidia-96 (96.43.17-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-96/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/share/man/man1/nvidia-smi.1.gz because associated file /usr/share/man/man1/alt-nvidia-96-smi.1.gz (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/nvidia-smi because associated file /usr/lib/nvidia-96/bin/nvidia-smi (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-96-96.43.17 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-24-generic
Building for architecture i686
Building initial module for 2.6.32-24-generic
Done.

nvidia-96.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-24-generic/updates/dkms/

depmod......

DKMS: install Completed.

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Processing triggers for python-support ...

mcsmith@xw6000:~$ dpkg --list | grep nvidia
ii  nvidia-96                                  96.43.17-0ubuntu1                                          NVIDIA binary Xorg driver, kernel module and
rc  nvidia-glx                                 1:96.43.05+2.6.24.14-21.51                                 NVIDIA binary XFree86 4.x/X.Org driver
ii  nvidia-settings                            195.36.08-0ubuntu2                                         Tool of configuring the NVIDIA graphics driv

```

Unfortunately, with the nvidia packages installed, I'm back to the text login.  I didn't have a /etc/X11/xorg.conf in place, so I used **sudo nvidia-xconfig** to create one.  After rebooting, I *think* a GUI was presented (I heard the tones that accompany the login screen), but my monitor just displayed an "out of range" error message.

Any ideas?

---

### Post by mcsmith on 2010-07-25
Well, I've got a stable Nouveau setup running, however, I'm still faced with 1024x768 resolution.

Any clues on how to switch to the native resolution of my display, which is 1920x1200, and is what was working back in 9.10?

Thanks,

Mike

---

