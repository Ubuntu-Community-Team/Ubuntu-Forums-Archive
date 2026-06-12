---
title: "No screens found"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2007-06-10
Ok, so, last night I did sudo apt-get update && sudo apt-get dist-upgrade

I noticed that one of the packages it upgraded was the kernel.

Now after rebooting, X refuses to start.. And the whole computer locks up solid about 5 minutes after trying to start X.

Heres my X logfile
> 
X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686
Current Operating System: Linux crydee 2.6.17-11-386 #2 Fri May 18 23:37:00 UTC 2007 i686
Build Date: 07 July 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sun Jun 10 21:20:35 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Cirrus Logic GD 5464 [Laguna]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/X11/fonts/misc,
        /usr/share/X11/fonts/100dpi/:unscaled,
        /usr/share/X11/fonts/75dpi/:unscaled,
        /usr/share/X11/fonts/Type1,
        /usr/share/X11/fonts/100dpi,
        /usr/share/X11/fonts/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc/,
        /usr/share/fonts/X11/TTF/,
        /usr/share/fonts/X11/OTF,
        /usr/share/fonts/X11/Type1/,
        /usr/share/fonts/X11/CID/,
        /usr/share/fonts/X11/100dpi/,
        /usr/share/fonts/X11/75dpi/
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) Open APM successful
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.0
        X.Org XInput driver : 0.6
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "bitmap"
(II) Loading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Module bitmap: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Bitmap
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules/libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7190 card 0000,0000 rev 03 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 03 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 8086,7110 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 0000,0000 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:07:2: chip 8086,7112 card 0000,0000 rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 0000,0000 rev 02 class 06,80,00 hdr 00
(II) PCI: 00:0c:0: chip 1073,000d card 8086,5345 rev 03 class 04,01,00 hdr 00
(II) PCI: 00:0d:0: chip 10b7,9050 card 0000,0000 rev 00 class 02,00,00 hdr 00
(II) PCI: 00:0e:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 00:0f:0: chip 14f1,8800 card 0070,3401 rev 05 class 04,00,00 hdr 80
(II) PCI: 00:0f:1: chip 14f1,8811 card 0070,3401 rev 05 class 04,80,00 hdr 80
(II) PCI: 01:00:0: chip 10de,0020 card 1092,5802 rev 04 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x008c (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xf7000000 - 0xf7ffffff (0x1000000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xfc000000 - 0xfcffffff (0x1000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:15:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xf5000000/24
(--) PCI:*(1:0:0) nVidia Corporation NV4 [RIVA TNT] rev 4, Mem @ 0xf7000000/24, 0xfc000000/24
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
        [1] -1  0       0xf4008000 - 0xf40080ff (0x100) MX[B]
        [2] -1  0       0xf4000000 - 0xf4007fff (0x8000) MX[B]
        [3] -1  0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [4] -1  0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [5] -1  0       0xf7000000 - 0xf7ffffff (0x1000000) MX[B](B)
        [6] -1  0       0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
        [7] -1  0       0x00001000 - 0x000010ff (0x100) IX[B]
        [8] -1  0       0x00001400 - 0x0000143f (0x40) IX[B]
        [9] -1  0       0x00001440 - 0x0000145f (0x20) IX[B]
        [10] -1 0       0x00001460 - 0x0000146f (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
        [1] -1  0       0xf4008000 - 0xf40080ff (0x100) MX[B]
        [2] -1  0       0xf4000000 - 0xf4007fff (0x8000) MX[B]
        [3] -1  0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [4] -1  0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [5] -1  0       0xf7000000 - 0xf7ffffff (0x1000000) MX[B](B)
        [6] -1  0       0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
        [7] -1  0       0x00001000 - 0x000010ff (0x100) IX[B]
        [8] -1  0       0x00001400 - 0x0000143f (0x40) IX[B]
        [9] -1  0       0x00001440 - 0x0000145f (0x20) IX[B]
        [10] -1 0       0x00001460 - 0x0000146f (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xf6000000 - 0xf6ffffff (0x1000000) MX[B]
        [5] -1  0       0xf4008000 - 0xf40080ff (0x100) MX[B]
        [6] -1  0       0xf4000000 - 0xf4007fff (0x8000) MX[B]
        [7] -1  0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [8] -1  0       0xfc000000 - 0xfcffffff (0x1000000) MX[B](B)
        [9] -1  0       0xf7000000 - 0xf7ffffff (0x1000000) MX[B](B)
        [10] -1 0       0xf5000000 - 0xf5ffffff (0x1000000) MX[B](B)
        [11] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [12] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [13] -1 0       0x00001000 - 0x000010ff (0x100) IX[B]
        [14] -1 0       0x00001400 - 0x0000143f (0x40) IX[B]
        [15] -1 0       0x00001440 - 0x0000145f (0x20) IX[B]
        [16] -1 0       0x00001460 - 0x0000146f (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "bitmap"
(II) Reloading /usr/lib/xorg/modules/fonts/libbitmap.so
(II) Loading font Bitmap
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading sub module "drm"
(II) LoadModule: "drm"
(II) Loading /usr/lib/xorg/modules/linux/libdrm.so
(II) Module drm: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules/fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.1.1, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "type1"
(II) Loading /usr/lib/xorg/modules/fonts/libtype1.so
(II) Module type1: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.2
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font Type1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "cirrus"
(II) Loading /usr/lib/xorg/modules/drivers/cirrus_drv.so
(II) Module cirrus: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input/kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input/mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.6
(II) Wacom driver level: 47-0.7.2 $
(II) CIRRUS: driver for Cirrus chipsets: CLGD5430, CLGD5434-4, CLGD5434-8,
        CLGD5436, CLGD5446, CLGD5480, CL-GD5462, CL-GD5464, CL-GD5464BD,
        CL-GD5465, CL-GD7548
(II) Primary Device is: PCI 01:00:0
(EE) No devices detected.

Fatal server error:
no screens found


and my Xorg.conf file
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Cirrus Logic GD 5464 [Laguna]"
        Driver          "cirrus"
        BusID           "PCI:0:10:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Cirrus Logic GD 5464 [Laguna]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection


If someone would be so kind as to help me get things up and running again,  I would be most appreciative.
Milambar

---

### Post by taurus on 2007-06-10
Boot into recovery mode from GRUB menu and reconfigure X again.

```
cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.backup
dpkg-reconfigure xserver-xorg
```

---

### Post by Milambar on 2007-06-10
Done, no change, it still quits out with "no screens found".

---

### Post by ZeBadger on 2007-06-11
I have the same problem.  Since I did the  update I get no screens.

My PC just locked up too, but I'm not sure if that was me changing screens and hitting CTRL+Z on tty1, then moving back to tty7.

I've changed my driver back to "nv" from nvidia to get me here.


More info after I've had a bit more of a play.

---

### Post by ZeBadger on 2007-06-11
Here's the output
```
xauth:  creating new authority file /home/matt/.serverauth.12760

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux lounge 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 11 18:07:15 2007
(==) Using config file: "/etc/X11/xorg.conf"

FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

```

The NVIDIA driver isn't loading.
Here is my xorg.conf

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5500]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5500]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
#    Option         "UseFBDev" "true"
    Option         "RenderAccel" "True"
    Option         "BackStoring" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

My PC hasn't locked up since my last post.  Any help would be appreciated!

---

### Post by taurus on 2007-06-11
> **ZeBadger said:**
> Here's the output
```
xauth:  creating new authority file /home/matt/.serverauth.12760

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux lounge 2.6.20-16-386 #2 Thu Jun 7 20:16:13 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Jun 11 18:07:15 2007
(==) Using config file: "/etc/X11/xorg.conf"

FATAL: Error running install command for nvidia
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.

```

The NVIDIA driver isn't loading.
Here is my xorg.conf

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5500]"
 [COLOR="Blue"]   Driver         "nvidia"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5500]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
#    Option         "UseFBDev" "true"
    Option         "RenderAccel" "True"
    Option         "BackStoring" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

My PC hasn't locked up since my last post.  Any help would be appreciated!

Well, you are still using "nvidia' drive so you need to edit /etc/X11/xorg.conf

```
sudo nano -w /etc/X11/xorg.conf
```
and change it to 'nv".

```
Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5500]"
    Driver         "nv"
EndSection
```
Save it with <Ctrl>o and exit with <Ctrl>x.  Then, reboot.

```
shutdown -r now
```

---

### Post by amdfanboy on 2007-06-11
are you installing ubuntu beryl or a vid card driver prior to that error?

---

### Post by luvr on 2007-06-12
The update installed kernel 2.6.20-16.29, but Ubuntu doesn't have an nvidia kernel module available to go with the updated kernel. Not yet, anyway.

You will either have to use the **nv** module instead, or revert to the previous kernel version, until you can install the updated nvidia module.

I wonder if there's any news about when the updated module will be made available?

Or otherwise, is there a supported procedure for users to create the appropriate module themselves? I know that the nvidia web site provides the module as a download (I used to install it in this way, under other distros or under earlier Ubuntu releases); I'm suspicious, though, that this will break the Ubuntu package management system. Installing the official nvidia download over an already installed Ubuntu release of the module sounds sort of freaky to me...

---

### Post by ZeBadger on 2007-06-12
> **luvr said:**
> The update installed kernel 2.6.20-16.29, but Ubuntu doesn't have an nvidia kernel module available to go with the updated kernel. Not yet, anyway.

You will either have to use the **nv** module instead, or revert to the previous kernel version, until you can install the updated nvidia module.

I wonder if there's any news about when the updated module will be made available?

Or otherwise, is there a supported procedure for users to create the appropriate module themselves? I know that the nvidia web site provides the module as a download (I used to install it in this way, under other distros or under earlier Ubuntu releases); I'm suspicious, though, that this will break the Ubuntu package management system. Installing the official nvidia download over an already installed Ubuntu release of the module sounds sort of freaky to me...

Thanks luvr.  This is exactly the problem.  I am now using the nv module, but beryl wont work now.  Looks like I'll just have to wait for the updated nvidia package to come along.  I have tried downloading the package from the nvidia website when I had a similar problem when running the beta of fiesty... but this just really messed things up...like softlinks in some of the lib directories etc.

Thanks for your reply

---

### Post by The Afterdark on 2007-06-12
I'm having the same problem.  I have Fedora 6 already on my PC, but I'm trying to get Ubuntu 6.10 on it.  It gives me the same exact error.  I'm using an ATIC X800 Pro though.

> 
Failed to start the X Server.  It is likely taht it is not set up correctly.  Wiould you like to view the X server output to diagnose this problem?


Now that X server output gives me the following at the end:

> 
(EE) No devices detected
Fatal Error:
no screens found

then i looked into the Xorg log as well, and it shows the following two warnings before giving me the previous two errors again:

> 
(WW) ATI: PCI Mach64 in slot 1:0:0 could not be detected.
(WW) ATI: PCI Mach64 in slot 1:0:1 could not be detected.


any help?

---

### Post by luvr on 2007-06-13
> **ZeBadger said:**
> I am now using the nv module, but beryl wont work now.
That's correct: Beryl (or Compiz) require advanced 3D features, which are not supported by the open-source *"nv"* driver.

NVidia will not publish the specifications to allow development of a full-featured open-source driver, and will not go any further than to provide a binary-only driver. Trouble is, such a driver does not integrate well with the open-source philosophy behind Linux.

Still, NVidia at least provides some form of support for the advanced 3D features of their graphics adapters under Linux; until recently, they probably were the best choice on the platform. It seems, though, that both Intel and ATI are considering open-sourcing their drivers these days (but I must admit that I haven't been following their developments, so I don't really know anything about the current status--I will surely be taking a closer look next time that I'm in for a new hardware purchase).

---

### Post by luvr on 2007-06-14
> **ZeBadger said:**
> Looks like I'll just have to wait for the updated nvidia package to come along.
Hmm... Looks like the issue is a little different from what I had imagined.

Yesterday, I updated Ubuntu on my laptop to generic kernel **2.6.20-16.29** (just to see what would happen). I expected that the NVidia driver would not work (since an updated restricted-modules package was still unavailable).

To my surprise, though, everything just worked fine; I got a message that told me that there were new restricted drivers in use, and everything (including the NVidia driver and VMware Workstation) simply worked without requiring any further action from me.

On my laptop, the previous upgrade (to generic kernel **2.6.20-16.28**) had gone fine, and had installed and configured a new NVidia kernel module; apparently, once the restricted modules are successfully upgraded for 2.6.20-16, any further updates within the 2.6.20-16 range will take care of the restricted modules.

On my desktop machine, on the other hand, the upgrade to generic kernel 2.6.20-16.28 had gone wrong: The system would no longer boot successfully, having problems to correctly set up access to the SATA disk. Apparently, the restricted modules didn't get properly set up, and further upgrades within the 2.6.20-16 family cannot recover from this problem.

I think I'll try a fresh reinstall of my desktop, and update directly from the original kernel (**2.6.20-15.27**) to the most recent one (**2.6.20-16.29**). Something tells me that that may well work.

---

### Post by wedge2k on 2007-06-14
The fix for me was after: 
```
sudo apt-get install nvidia-glx
```

did

 ```
sudo modprobe -i nvidia
```

poof worked.. Nightmare just to discover that simple command.. *sigh*

Hope that helps someone

---

### Post by ZeBadger on 2007-06-15
My nvidia-glx was already the latest version.

```
sudo modprobe -i nvidia
```
Tells me  "FATAL: Module nvidia not found."

I went into the restricted drivers manager and I got an alert box saying:

```
You need to install the package

linux-restricted-modules-2.6.20-16-386

for this program to work.
```

I'm installing this through Synaptic Package manager (I've already got 2.6.20-15) , I'll report back if this fixes it.

---

### Post by ZeBadger on 2007-06-15
Okay sweet.  That sorted it.

---

### Post by luvr on 2007-06-16
> **ZeBadger said:**
> My nvidia-glx was already the latest version.
So was mine; I therefore tried
```
sudo apt-get --reinstall install nvidia-glx
```
That did reinstall the package, but the *modprobe* command kept saying *"FATAL: Module nvidia not found."*
At one point, I also got the message about having to install the *linux-restricted-modules-2.6.20-16-386* package, but that sounded wrong to me, since I'm using the **generic,** not the **386** kernel, so I didn't bother to try this out. (Perhaps I should have, then?)

Anyway, I decided to simply do a clean reinstall from the CD. After the install, I activated the restricted *nvidia* driver and enabled the compiz desktop effects.

Next, I let the system install all available updates (including the latest kernel and restricted driver packages), and that was perfectly successful. The Synaptic Package Manager now tells me that I have "linux-image-2.6.20-16-generic," version 2.6.20-16.29, and "linux-restricted-modules-2.6.20-16-generic," version 2.6.20-5-16.28 installed.

---

### Post by The Afterdark on 2007-06-16
Does anyone have a solution for ATI? :(

And btw, I did get it to finally install, but I had to boot Ubuntu Live in safe graphical mode, THEN had to install.... that seemed to work fine...
even after installation though, am i still stuck in safe graphical mode?  or should the installation have fixed that?

thanks...

---

### Post by gwolfman on 2007-08-07
> **ZeBadger said:**
> My nvidia-glx was already the latest version.

```
sudo modprobe -i nvidia
```
Tells me  "FATAL: Module nvidia not found."

I went into the restricted drivers manager and I got an alert box saying:

```
You need to install the package

linux-restricted-modules-2.6.20-16-386

for this program to work.
```

I'm installing this through Synaptic Package manager (I've already got 2.6.20-15) , I'll report back if this fixes it.
I couldn't execute the modprobe command either, and I also didn't get any reason why other than it couldn't find the nvidia module.  I don't know what you meant by "...went into the restricted drivers manager..." but I installed the linux-restricted-modules anyways for the kernel I'm running , then ran the modprobe command and it worked.  I then followed up with ```
sudo nvidia-glx-config enable
``` restarted X and it worked fine.  Why they don't mention you need the restricted modules is beyond me, but now I know.  Thanks!

---

