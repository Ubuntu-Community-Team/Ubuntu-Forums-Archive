---
title: "[SOLVED] nVidia install problem Ubuntu 8.10"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by josephtorr on 2008-11-19
I used the System-->Administration--->Hardware and Drivers and install the recommended driver. Upon system Restart I get an error, I am able to switch to a basic mode to view the desktop but can't utilize Visual Effects at all. Any help would be appreciated.

Her is the :0.log
---------------------------------
5534 5262
xinit /etc/gdm/failsafeXinit /etc/X11/xorg.conf.failsafe with-gdm -- /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7 -br -once -config /etc/X11/xorg.conf.failsafe -logfile /var/log/Xorg.failsafe.log

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux joseph-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/var/log/Xorg.failsafe.log", Time: Wed Nov 19 09:26:45 2008
(++) Using config file: "/etc/X11/xorg.conf.failsafe"
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
5534 5262
-----------------------------------------------
Xorg.0.log


X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux joseph-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686
Build Date: 24 October 2008 08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd)
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Nov 19 09:26:43 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section. Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) | |-->Monitor "Configured Monitor"
(**) | |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified. Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Entry deleted from font path.
(==) FontPath set to:
/usr/share/fonts/X11/misc,
/usr/share/fonts/X11/100dpi/:unscaled,
/usr/share/fonts/X11/75dpi/:unscaled,
/usr/share/fonts/X11/Type1,
/usr/share/fonts/X11/100dpi,
/usr/share/fonts/X11/75dpi,
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81d9a40
(II) Module ABI versions:
X.Org ANSI C Emulation: 0.4
X.Org Video Driver: 4.1
X.Org XInput driver : 2.1
X.Org Server Extension : 1.1
X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) nVidia Corporation NV43 [GeForce 6600] rev 162, Mem @ 0xd4000000/0, 0xc8000000/0, 0xda000000/0, BIOS @ 0x????????/131072
(--) PCI: (0@2:6:0) Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder rev 0, Mem @ 0xf4000000/0
(II) System resource ranges:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[5] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[6] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[7] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[8] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[9] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[10] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[11] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[12] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[13] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[14] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[15] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[16] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[17] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[18] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[19] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[20] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[21] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[22] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[23] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[24] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[25] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[26] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[27] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[28] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[29] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.Org Server Extension
(II) NVIDIA GLX Module 177.80 Wed Oct 1 15:06:06 PDT 2008
(II) Loading extension GLX
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"

(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
compiled for 1.5.2, module version = 2.1.0
Module class: X.Org Font Renderer
ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.13.0
Module class: X.Org Server Extension
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"

(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
compiled for 4.0.2, module version = 1.0.0
Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver 177.80 Wed Oct 1 14:45:01 PDT 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"

(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"

(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
compiled for 1.5.2, module version = 1.0.0
ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
[0] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[1] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[2] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[3] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[4] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[5] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[6] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[7] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[8] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[9] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[10] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[11] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[12] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[13] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[14] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[15] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[16] -1 0 0xffffffff - 0xffffffff (0x1) MX[b]
[17] -1 0 0x000f0000 - 0x000fffff (0x10000) MX[b]
[18] -1 0 0x000c0000 - 0x000effff (0x30000) MX[b]
[19] -1 0 0x00000000 - 0x0009ffff (0xa0000) MX[b]
[20] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[21] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[22] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[23] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[24] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[25] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[26] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[27] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
[28] -1 0 0x0000ffff - 0x0000ffff (0x1) IX[b]
[29] -1 0 0x00000000 - 0x00000000 (0x1) IX[b]
(II) NVIDIA(0): Creating default Display subsection in Screen section
"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0): enabled.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device PCI:1:0:0.
(EE) NVIDIA(0): Please see the COMMON PROBLEMS section in the README for
(EE) NVIDIA(0): additional information.
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

------------------------------------------------------------------------

---

### Post by dabl on 2008-11-19
I've not had good luck with "Hardware and Drivers" either.  I suggest you use EnvyNG, following the guidance in the second post here:

[http://kubuntuforums.net/forums/index.php?topic=3098672.msg152816#msg152816](http://kubuntuforums.net/forums/index.php?topic=3098672.msg152816#msg152816)

except for Ubuntu it is "gdm" instead of "kdm".

:)

---

### Post by josephtorr on 2008-11-19
dabl... you're awesome... this worked.. thank you...

---

