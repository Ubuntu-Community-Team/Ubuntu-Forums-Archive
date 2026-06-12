---
title: "need help Intel G43/G45 express chipset and 11.10"
date: 2011-11-27
forum: Installation &amp; Upgrades
---

### Post by drillerccg on 2011-11-27
Hi,

Trying to setup the dual boot with Windows 7 and 11.10. was getting the black screen during the setup but used the nomodeset and this thread 

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
to see at least get some graphics and install the 11.10. The problem is that it is very low quality and low resolution. Have searched but not coming up with anything. Would appreciate some help.

I also used the acpi_osi= in the grub but that turned the screen black again.

---

### Post by drillerccg on 2011-11-27
stuck here, anyone has any ideas?

---

### Post by drillerccg on 2011-11-28
I hope I don't get banned but am still stuck. This is an HP all in one 200. I may only need drivers for this stupid thing.

---

### Post by MAFoElffen on 2011-11-28
> **drillerccg said:**
> I hope I don't get banned but am still stuck. This is an HP all in one 200. I may only need drivers for this stupid thing.
Please boot on a LiveCD, start a terminal session and post this:
```

lspci -vnn | grep VGA

```
You can run "Try" on the LiveCD right?

Heading out the door for the morning, but will check back soon.

---

### Post by drillerccg on 2011-11-28
> **MAFoElffen said:**
> Please boot on a LiveCD, start a terminal session and post this:
```

lspci -vnn | grep VGA

```You can run "Try" on the LiveCD right?

Heading out the door for the morning, but will check back soon.

I actually have the OS installed as dual boot using nomodeset settings in the grub so I ran it in the terminal:

```
jp@jp-HP-Pavilion-All-in-One-200-5100t-Intel:~$ lspci -vnn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03) (prog-if 00 [VGA controller])
jp@jp-HP-Pavilion-All-in-One-200-5100t-Intel:~$
```

It seems like if I could increase the resolution to 1600x1200 It will be ok, but that's just a guess.

---

### Post by MAFoElffen on 2011-11-28
> **drillerccg said:**
> I actually have the OS installed as dual boot using nomodeset settings in the grub so I ran it in the terminal:

jp@jp-HP-Pavilion-All-in-One-200-5100t-Intel:~$ lspci -vnn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e22] (rev 03) (prog-if 00 [VGA controller])
jp@jp-HP-Pavilion-All-in-One-200-5100t-Intel:~$

It seems like if I could increase the resolution to 1600x1200 It will be ok, but that's just a guess.
On boot parameters (such as nomodeset) try instead " i915.modeset=0 " or i915.modeset=1" 

Please post your /var/log/Xorg.0.log file and please make sure this time that after you paste it into your post > Select it > Press the " # " icon in the posting toolbar to put the text within CODE tags.  It's a long file and that code tag will save space in a post and adds scroll bars to make it easier to read.

Your chipset is supported by the xserver-xorg-video-intel driver... But doesn't seem to be using it for some reason... It can be overridden (but normally shouldn't need to be.) 

You didn't have to use any boot option with the LiveCD right?  Was this a new fresh install?

---

### Post by drillerccg on 2011-11-28
```
[    26.069] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    26.069] X Protocol Version 11, Revision 0
[    26.069] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    26.069] Current Operating System: Linux jp-HP-Pavilion-All-in-One-200-5100t-Intel 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686
[    26.070] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=81678a69-235f-413d-bd5d-d946acfa3664 ro quiet splash i915.modeset=0
[    26.070] Build Date: 19 October 2011  05:09:41AM
[    26.070] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    26.070] Current version of pixman: 0.22.2
[    26.070]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    26.070] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.070] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov 28 17:41:13 2011
[    26.070] (==) Using config file: "/etc/X11/xorg.conf"
[    26.070] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.077] (==) No Layout section.  Using the first Screen section.
[    26.077] (**) |-->Screen "Default Screen" (0)
[    26.077] (**) |   |-->Monitor "Configured Monitor"
[    26.077] (**) |   |-->Device "Configured Video Device"
[    26.077] (==) Automatically adding devices
[    26.077] (==) Automatically enabling devices
[    26.077] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.077]     Entry deleted from font path.
[    26.077] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.077]     Entry deleted from font path.
[    26.077] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.077]     Entry deleted from font path.
[    26.077] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.077]     Entry deleted from font path.
[    26.077] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.077]     Entry deleted from font path.
[    26.077] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    26.077] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.077] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.077] (II) Loader magic: 0x823ada0
[    26.077] (II) Module ABI versions:
[    26.077]     X.Org ANSI C Emulation: 0.4
[    26.077]     X.Org Video Driver: 10.0
[    26.077]     X.Org XInput driver : 12.3
[    26.077]     X.Org Server Extension : 5.0
[    26.078] (--) PCI:*(0:0:2:0) 8086:2e22:103c:2aa2 rev 3, Mem @ 0xfe400000/4194304, 0xe0000000/268435456, I/O @ 0x0000dc00/8
[    26.078] (--) PCI: (0:0:2:1) 8086:2e23:103c:2aa2 rev 3, Mem @ 0xfe300000/1048576
[    26.078] (II) Open ACPI successful (/var/run/acpid.socket)
[    26.078] (II) LoadModule: "extmod"
[    26.079] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    26.079] (II) Module extmod: vendor="X.Org Foundation"
[    26.079]     compiled for 1.10.4, module version = 1.0.0
[    26.079]     Module class: X.Org Server Extension
[    26.079]     ABI class: X.Org Server Extension, version 5.0
[    26.079] (II) Loading extension MIT-SCREEN-SAVER
[    26.079] (II) Loading extension XFree86-VidModeExtension
[    26.079] (II) Loading extension XFree86-DGA
[    26.079] (II) Loading extension DPMS
[    26.079] (II) Loading extension XVideo
[    26.079] (II) Loading extension XVideo-MotionCompensation
[    26.079] (II) Loading extension X-Resource
[    26.079] (II) LoadModule: "dbe"
[    26.082] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    26.082] (II) Module dbe: vendor="X.Org Foundation"
[    26.082]     compiled for 1.10.4, module version = 1.0.0
[    26.082]     Module class: X.Org Server Extension
[    26.082]     ABI class: X.Org Server Extension, version 5.0
[    26.082] (II) Loading extension DOUBLE-BUFFER
[    26.082] (II) LoadModule: "glx"
[    26.082] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.083] (II) Module glx: vendor="X.Org Foundation"
[    26.083]     compiled for 1.10.4, module version = 1.0.0
[    26.083]     ABI class: X.Org Server Extension, version 5.0
[    26.083] (==) AIGLX enabled
[    26.083] (II) Loading extension GLX
[    26.083] (II) LoadModule: "record"
[    26.083] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    26.083] (II) Module record: vendor="X.Org Foundation"
[    26.083]     compiled for 1.10.4, module version = 1.13.0
[    26.083]     Module class: X.Org Server Extension
[    26.083]     ABI class: X.Org Server Extension, version 5.0
[    26.083] (II) Loading extension RECORD
[    26.083] (II) LoadModule: "dri"
[    26.083] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    26.083] (II) Module dri: vendor="X.Org Foundation"
[    26.083]     compiled for 1.10.4, module version = 1.0.0
[    26.083]     ABI class: X.Org Server Extension, version 5.0
[    26.083] (II) Loading extension XFree86-DRI
[    26.083] (II) LoadModule: "dri2"
[    26.084] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    26.084] (II) Module dri2: vendor="X.Org Foundation"
[    26.084]     compiled for 1.10.4, module version = 1.2.0
[    26.084]     ABI class: X.Org Server Extension, version 5.0
[    26.084] (II) Loading extension DRI2
[    26.084] (II) LoadModule: "vesa"
[    26.084] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.084] (II) Module vesa: vendor="X.Org Foundation"
[    26.084]     compiled for 1.10.2, module version = 2.3.0
[    26.084]     Module class: X.Org Video Driver
[    26.084]     ABI class: X.Org Video Driver, version 10.0
[    26.084] (II) VESA: driver for VESA chipsets: vesa
[    26.084] (++) using VT number 7

[    26.084] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.084] (II) Loading sub module "vbe"
[    26.084] (II) LoadModule: "vbe"
[    26.085] (II) Loading /usr/lib/xorg/modules/libvbe.so
[    26.085] (II) Module vbe: vendor="X.Org Foundation"
[    26.085]     compiled for 1.10.4, module version = 1.1.0
[    26.085]     ABI class: X.Org Video Driver, version 10.0
[    26.085] (II) Loading sub module "int10"
[    26.085] (II) LoadModule: "int10"
[    26.085] (II) Loading /usr/lib/xorg/modules/libint10.so
[    26.085] (II) Module int10: vendor="X.Org Foundation"
[    26.085]     compiled for 1.10.4, module version = 1.0.0
[    26.085]     ABI class: X.Org Video Driver, version 10.0
[    26.085] (II) VESA(0): initializing int10
[    26.085] (II) VESA(0): Bad V_BIOS checksum
[    26.085] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    26.085] (II) VESA(0): VESA BIOS detected
[    26.085] (II) VESA(0): VESA VBE Version 3.0
[    26.085] (II) VESA(0): VESA VBE Total Mem: 32704 kB
[    26.085] (II) VESA(0): VESA VBE OEM: Intel(R)Eaglelake Graphics Chipset Accelerated VGA BIOS
[    26.085] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    26.085] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    26.085] (II) VESA(0): VESA VBE OEM Product: Intel(R)Eaglelake Graphics Controller
[    26.086] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    26.151] (II) VESA(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    26.151] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    26.151] (==) VESA(0): RGB weight 888
[    26.151] (==) VESA(0): Default visual is TrueColor
[    26.151] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    26.151] (II) Loading sub module "ddc"
[    26.151] (II) LoadModule: "ddc"
[    26.151] (II) Module "ddc" already built-in
[    26.153] (II) VESA(0): VESA VBE DDC supported
[    26.153] (II) VESA(0): VESA VBE DDC Level 2
[    26.153] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    26.169] (II) VESA(0): VESA VBE DDC read successfully
[    26.169] (II) VESA(0): Manufacturer: HWP  Model: 4101  Serial#: 257
[    26.170] (II) VESA(0): Year: 2009  Week: 30
[    26.170] (II) VESA(0): EDID Version: 1.3
[    26.170] (II) VESA(0): Digital Display Input
[    26.170] (II) VESA(0): Max Image Size [cm]: horiz.: 47  vert.: 27
[    26.170] (II) VESA(0): Gamma: 2.20
[    26.170] (II) VESA(0): No DPMS capabilities specified
[    26.170] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.170] (II) VESA(0): First detailed timing is preferred mode
[    26.170] (II) VESA(0): redX: 0.637 redY: 0.349   greenX: 0.333 greenY: 0.605
[    26.170] (II) VESA(0): blueX: 0.148 blueY: 0.061   whiteX: 0.313 whiteY: 0.329
[    26.170] (II) VESA(0): Manufacturer's mask: 0
[    26.170] (II) VESA(0): Supported detailed timing:
[    26.170] (II) VESA(0): clock: 136.0 MHz   Image Size:  470 x 270 mm
[    26.170] (II) VESA(0): h_active: 1920  h_sync: 1980  h_sync_end 2040 h_blank_end 2060 h_border: 0
[    26.170] (II) VESA(0): v_active: 1080  v_sync: 1090  v_sync_end 1098 v_blanking: 1100 v_border: 0
[    26.170] (II) VESA(0):  Rhine
[    26.170] (II) VESA(0):  HP
[    26.170] (II) VESA(0):  M215HW01 V6
[    26.170] (II) VESA(0): EDID (in hex):
[    26.170] (II) VESA(0):     00ffffffffffff0022f0014101010000
[    26.170] (II) VESA(0):     1e130103802f1b780a1425a359559b26
[    26.170] (II) VESA(0):     0f505400000001010101010101010101
[    26.170] (II) VESA(0):     0101010101012035808c703814403c3c
[    26.170] (II) VESA(0):     a800d60e11000018000000fe00526869
[    26.170] (II) VESA(0):     6e650a20202020202020000000fe0048
[    26.170] (II) VESA(0):     500a20202020202020202020000000fe
[    26.170] (II) VESA(0):     004d323135485730312056360a200020
[    26.170] (II) VESA(0): EDID vendor "HWP", prod id 16641
[    26.170] (II) VESA(0): Printing DDC gathered Modelines:
[    26.170] (II) VESA(0): Modeline "1920x1080"x0.0  136.00  1920 1980 2040 2060  1080 1090 1098 1100 -hsync -vsync (66.0 kHz)
[    26.170] (II) VESA(0): Searching for matching VESA mode(s):
[    26.170] Mode: 160 (0x0)
[    26.170]     ModeAttributes: 0x0
[    26.170]     WinAAttributes: 0x0
[    26.170]     WinBAttributes: 0x0
[    26.170]     WinGranularity: 0
[    26.170]     WinSize: 0
[    26.170]     WinASegment: 0x0
[    26.170]     WinBSegment: 0x0
[    26.170]     WinFuncPtr: 0x0
[    26.170]     BytesPerScanline: 0
[    26.170]     XResolution: 0
[    26.170]     YResolution: 0
[    26.170]     XCharSize: 0
[    26.170]     YCharSize: 0
[    26.170]     NumberOfPlanes: 0
[    26.170]     BitsPerPixel: 0
[    26.170]     NumberOfBanks: 0
[    26.170]     MemoryModel: 0
[    26.170]     BankSize: 0
[    26.170]     NumberOfImages: 0
[    26.170]     RedMaskSize: 0
[    26.170]     RedFieldPosition: 0
[    26.170]     GreenMaskSize: 0
[    26.170]     GreenFieldPosition: 0
[    26.170]     BlueMaskSize: 0
[    26.170]     BlueFieldPosition: 0
[    26.170]     RsvdMaskSize: 0
[    26.170]     RsvdFieldPosition: 0
[    26.170]     DirectColorModeInfo: 0
[    26.170]     PhysBasePtr: 0x0
[    26.170]     LinBytesPerScanLine: 0
[    26.170]     BnkNumberOfImagePages: 0
[    26.170]     LinNumberOfImagePages: 0
[    26.170]     LinRedMaskSize: 0
[    26.170]     LinRedFieldPosition: 0
[    26.170]     LinGreenMaskSize: 0
[    26.170]     LinGreenFieldPosition: 0
[    26.170]     LinBlueMaskSize: 0
[    26.170]     LinBlueFieldPosition: 0
[    26.170]     LinRsvdMaskSize: 0
[    26.170]     LinRsvdFieldPosition: 0
[    26.170]     MaxPixelClock: 0
[    26.172] Mode: 161 (0x0)
[    26.172]     ModeAttributes: 0x0
[    26.172]     WinAAttributes: 0x0
[    26.172]     WinBAttributes: 0x0
[    26.172]     WinGranularity: 0
[    26.172]     WinSize: 0
[    26.172]     WinASegment: 0x0
[    26.172]     WinBSegment: 0x0
[    26.172]     WinFuncPtr: 0x0
[    26.172]     BytesPerScanline: 0
[    26.172]     XResolution: 0
[    26.172]     YResolution: 0
[    26.172]     XCharSize: 0
[    26.172]     YCharSize: 0
[    26.172]     NumberOfPlanes: 0
[    26.172]     BitsPerPixel: 0
[    26.172]     NumberOfBanks: 0
[    26.172]     MemoryModel: 0
[    26.172]     BankSize: 0
[    26.172]     NumberOfImages: 0
[    26.172]     RedMaskSize: 0
[    26.172]     RedFieldPosition: 0
[    26.172]     GreenMaskSize: 0
[    26.172]     GreenFieldPosition: 0
[    26.172]     BlueMaskSize: 0
[    26.172]     BlueFieldPosition: 0
[    26.172]     RsvdMaskSize: 0
[    26.172]     RsvdFieldPosition: 0
[    26.172]     DirectColorModeInfo: 0
[    26.172]     PhysBasePtr: 0x0
[    26.172]     LinBytesPerScanLine: 0
[    26.172]     BnkNumberOfImagePages: 0
[    26.172]     LinNumberOfImagePages: 0
[    26.172]     LinRedMaskSize: 0
[    26.172]     LinRedFieldPosition: 0
[    26.172]     LinGreenMaskSize: 0
[    26.172]     LinGreenFieldPosition: 0
[    26.172]     LinBlueMaskSize: 0
[    26.172]     LinBlueFieldPosition: 0
[    26.172]     LinRsvdMaskSize: 0
[    26.172]     LinRsvdFieldPosition: 0
[    26.172]     MaxPixelClock: 0
[    26.172] Mode: 162 (0x0)
[    26.172]     ModeAttributes: 0x0
[    26.172]     WinAAttributes: 0x0
[    26.172]     WinBAttributes: 0x0
[    26.172]     WinGranularity: 0
[    26.172]     WinSize: 0
[    26.172]     WinASegment: 0x0
[    26.172]     WinBSegment: 0x0
[    26.172]     WinFuncPtr: 0x0
[    26.172]     BytesPerScanline: 0
[    26.172]     XResolution: 0
[    26.173]     YResolution: 0
[    26.173]     XCharSize: 0
[    26.173]     YCharSize: 0
[    26.173]     NumberOfPlanes: 0
[    26.173]     BitsPerPixel: 0
[    26.173]     NumberOfBanks: 0
[    26.173]     MemoryModel: 0
[    26.173]     BankSize: 0
[    26.173]     NumberOfImages: 0
[    26.173]     RedMaskSize: 0
[    26.173]     RedFieldPosition: 0
[    26.173]     GreenMaskSize: 0
[    26.173]     GreenFieldPosition: 0
[    26.173]     BlueMaskSize: 0
[    26.173]     BlueFieldPosition: 0
[    26.173]     RsvdMaskSize: 0
[    26.173]     RsvdFieldPosition: 0
[    26.173]     DirectColorModeInfo: 0
[    26.173]     PhysBasePtr: 0x0
[    26.173]     LinBytesPerScanLine: 0
[    26.173]     BnkNumberOfImagePages: 0
[    26.173]     LinNumberOfImagePages: 0
[    26.173]     LinRedMaskSize: 0
[    26.173]     LinRedFieldPosition: 0
[    26.173]     LinGreenMaskSize: 0
[    26.173]     LinGreenFieldPosition: 0
[    26.173]     LinBlueMaskSize: 0
[    26.173]     LinBlueFieldPosition: 0
[    26.173]     LinRsvdMaskSize: 0
[    26.173]     LinRsvdFieldPosition: 0
[    26.173]     MaxPixelClock: 0
[    26.173] Mode: 163 (0x0)
[    26.173]     ModeAttributes: 0x0
[    26.173]     WinAAttributes: 0x0
[    26.173]     WinBAttributes: 0x0
[    26.173]     WinGranularity: 0
[    26.173]     WinSize: 0
[    26.173]     WinASegment: 0x0
[    26.173]     WinBSegment: 0x0
[    26.173]     WinFuncPtr: 0x0
[    26.173]     BytesPerScanline: 0
[    26.173]     XResolution: 0
[    26.173]     YResolution: 0
[    26.173]     XCharSize: 0
[    26.173]     YCharSize: 0
[    26.173]     NumberOfPlanes: 0
[    26.173]     BitsPerPixel: 0
[    26.173]     NumberOfBanks: 0
[    26.173]     MemoryModel: 0
[    26.173]     BankSize: 0
[    26.173]     NumberOfImages: 0
[    26.173]     RedMaskSize: 0
[    26.173]     RedFieldPosition: 0
[    26.173]     GreenMaskSize: 0
[    26.173]     GreenFieldPosition: 0
[    26.173]     BlueMaskSize: 0
[    26.173]     BlueFieldPosition: 0
[    26.173]     RsvdMaskSize: 0
[    26.173]     RsvdFieldPosition: 0
[    26.173]     DirectColorModeInfo: 0
[    26.173]     PhysBasePtr: 0x0
[    26.173]     LinBytesPerScanLine: 0
[    26.173]     BnkNumberOfImagePages: 0
[    26.173]     LinNumberOfImagePages: 0
[    26.173]     LinRedMaskSize: 0
[    26.173]     LinRedFieldPosition: 0
[    26.173]     LinGreenMaskSize: 0
[    26.173]     LinGreenFieldPosition: 0
[    26.173]     LinBlueMaskSize: 0
[    26.173]     LinBlueFieldPosition: 0
[    26.173]     LinRsvdMaskSize: 0
[    26.173]     LinRsvdFieldPosition: 0
[    26.173]     MaxPixelClock: 0
[    26.173] Mode: 164 (0x0)
[    26.173]     ModeAttributes: 0x0
[    26.173]     WinAAttributes: 0x0
[    26.173]     WinBAttributes: 0x0
[    26.173]     WinGranularity: 0
[    26.173]     WinSize: 0
[    26.173]     WinASegment: 0x0
[    26.175]     WinBSegment: 0x0
[    26.175]     WinFuncPtr: 0x0
[    26.175]     BytesPerScanline: 0
[    26.175]     XResolution: 0
[    26.175]     YResolution: 0
[    26.175]     XCharSize: 0
[    26.175]     YCharSize: 0
[    26.175]     NumberOfPlanes: 0
[    26.175]     BitsPerPixel: 0
[    26.175]     NumberOfBanks: 0
[    26.175]     MemoryModel: 0
[    26.175]     BankSize: 0
[    26.175]     NumberOfImages: 0
[    26.175]     RedMaskSize: 0
[    26.175]     RedFieldPosition: 0
[    26.175]     GreenMaskSize: 0
[    26.175]     GreenFieldPosition: 0
[    26.175]     BlueMaskSize: 0
[    26.175]     BlueFieldPosition: 0
[    26.175]     RsvdMaskSize: 0
[    26.175]     RsvdFieldPosition: 0
[    26.175]     DirectColorModeInfo: 0
[    26.175]     PhysBasePtr: 0x0
[    26.175]     LinBytesPerScanLine: 0
[    26.175]     BnkNumberOfImagePages: 0
[    26.175]     LinNumberOfImagePages: 0
[    26.175]     LinRedMaskSize: 0
[    26.175]     LinRedFieldPosition: 0
[    26.175]     LinGreenMaskSize: 0
[    26.175]     LinGreenFieldPosition: 0
[    26.175]     LinBlueMaskSize: 0
[    26.175]     LinBlueFieldPosition: 0
[    26.175]     LinRsvdMaskSize: 0
[    26.175]     LinRsvdFieldPosition: 0
[    26.175]     MaxPixelClock: 0
[    26.175] Mode: 165 (0x0)
[    26.175]     ModeAttributes: 0x0
[    26.175]     WinAAttributes: 0x0
[    26.175]     WinBAttributes: 0x0
[    26.175]     WinGranularity: 0
[    26.175]     WinSize: 0
[    26.175]     WinASegment: 0x0
[    26.175]     WinBSegment: 0x0
[    26.175]     WinFuncPtr: 0x0
[    26.175]     BytesPerScanline: 0
[    26.175]     XResolution: 0
[    26.175]     YResolution: 0
[    26.175]     XCharSize: 0
[    26.175]     YCharSize: 0
[    26.175]     NumberOfPlanes: 0
[    26.175]     BitsPerPixel: 0
[    26.175]     NumberOfBanks: 0
[    26.175]     MemoryModel: 0
[    26.175]     BankSize: 0
[    26.175]     NumberOfImages: 0
[    26.175]     RedMaskSize: 0
[    26.175]     RedFieldPosition: 0
[    26.175]     GreenMaskSize: 0
[    26.175]     GreenFieldPosition: 0
[    26.175]     BlueMaskSize: 0
[    26.175]     BlueFieldPosition: 0
[    26.175]     RsvdMaskSize: 0
[    26.175]     RsvdFieldPosition: 0
[    26.175]     DirectColorModeInfo: 0
[    26.175]     PhysBasePtr: 0x0
[    26.175]     LinBytesPerScanLine: 0
[    26.175]     BnkNumberOfImagePages: 0
[    26.175]     LinNumberOfImagePages: 0
[    26.175]     LinRedMaskSize: 0
[    26.175]     LinRedFieldPosition: 0
[    26.175]     LinGreenMaskSize: 0
[    26.175]     LinGreenFieldPosition: 0
[    26.175]     LinBlueMaskSize: 0
[    26.175]     LinBlueFieldPosition: 0
[    26.175]     LinRsvdMaskSize: 0
[    26.175]     LinRsvdFieldPosition: 0
[    26.175]     MaxPixelClock: 0
[    26.175] Mode: 166 (0x0)
[    26.175]     ModeAttributes: 0x0
[    26.175]     WinAAttributes: 0x0
[    26.175]     WinBAttributes: 0x0
[    26.175]     WinGranularity: 0
[    26.175]     WinSize: 0
[    26.175]     WinASegment: 0x0
[    26.175]     WinBSegment: 0x0
[    26.175]     WinFuncPtr: 0x0
[    26.175]     BytesPerScanline: 0
[    26.175]     XResolution: 0
[    26.175]     YResolution: 0
[    26.175]     XCharSize: 0
[    26.175]     YCharSize: 0
[    26.175]     NumberOfPlanes: 0
[    26.175]     BitsPerPixel: 0
[    26.175]     NumberOfBanks: 0
[    26.175]     MemoryModel: 0
[    26.175]     BankSize: 0
[    26.175]     NumberOfImages: 0
[    26.175]     RedMaskSize: 0
[    26.175]     RedFieldPosition: 0
[    26.175]     GreenMaskSize: 0
[    26.175]     GreenFieldPosition: 0
[    26.175]     BlueMaskSize: 0
[    26.175]     BlueFieldPosition: 0
[    26.175]     RsvdMaskSize: 0
[    26.175]     RsvdFieldPosition: 0
[    26.175]     DirectColorModeInfo: 0
[    26.175]     PhysBasePtr: 0x0
[    26.175]     LinBytesPerScanLine: 0
[    26.175]     BnkNumberOfImagePages: 0
[    26.175]     LinNumberOfImagePages: 0
[    26.175]     LinRedMaskSize: 0
[    26.175]     LinRedFieldPosition: 0
[    26.175]     LinGreenMaskSize: 0
[    26.175]     LinGreenFieldPosition: 0
[    26.176]     LinBlueMaskSize: 0
[    26.176]     LinBlueFieldPosition: 0
[    26.176]     LinRsvdMaskSize: 0
[    26.176]     LinRsvdFieldPosition: 0
[    26.176]     MaxPixelClock: 0
[    26.176] Mode: 167 (0x0)
[    26.176]     ModeAttributes: 0x0
[    26.176]     WinAAttributes: 0x0
[    26.176]     WinBAttributes: 0x0
[    26.176]     WinGranularity: 0
[    26.176]     WinSize: 0
[    26.176]     WinASegment: 0x0
[    26.176]     WinBSegment: 0x0
[    26.176]     WinFuncPtr: 0x0
[    26.176]     BytesPerScanline: 0
[    26.176]     XResolution: 0
[    26.176]     YResolution: 0
[    26.176]     XCharSize: 0
[    26.176]     YCharSize: 0
[    26.176]     NumberOfPlanes: 0
[    26.176]     BitsPerPixel: 0
[    26.176]     NumberOfBanks: 0
[    26.176]     MemoryModel: 0
[    26.176]     BankSize: 0
[    26.176]     NumberOfImages: 0
[    26.176]     RedMaskSize: 0
[    26.176]     RedFieldPosition: 0
[    26.176]     GreenMaskSize: 0
[    26.176]     GreenFieldPosition: 0
[    26.176]     BlueMaskSize: 0
[    26.176]     BlueFieldPosition: 0
[    26.176]     RsvdMaskSize: 0
[    26.176]     RsvdFieldPosition: 0
[    26.176]     DirectColorModeInfo: 0
[    26.176]     PhysBasePtr: 0x0
[    26.176]     LinBytesPerScanLine: 0
[    26.176]     BnkNumberOfImagePages: 0
[    26.176]     LinNumberOfImagePages: 0
[    26.176]     LinRedMaskSize: 0
[    26.176]     LinRedFieldPosition: 0
[    26.176]     LinGreenMaskSize: 0
[    26.176]     LinGreenFieldPosition: 0
[    26.176]     LinBlueMaskSize: 0
[    26.176]     LinBlueFieldPosition: 0
[    26.176]     LinRsvdMaskSize: 0
[    26.176]     LinRsvdFieldPosition: 0
[    26.176]     MaxPixelClock: 0
[    26.176] Mode: 168 (0x0)
[    26.176]     ModeAttributes: 0x0
[    26.176]     WinAAttributes: 0x0
[    26.176]     WinBAttributes: 0x0
[    26.176]     WinGranularity: 0
[    26.176]     WinSize: 0
[    26.176]     WinASegment: 0x0
[    26.176]     WinBSegment: 0x0
[    26.176]     WinFuncPtr: 0x0
[    26.176]     BytesPerScanline: 0
[    26.176]     XResolution: 0
[    26.176]     YResolution: 0
[    26.176]     XCharSize: 0
[    26.176]     YCharSize: 0
[    26.176]     NumberOfPlanes: 0
[    26.176]     BitsPerPixel: 0
[    26.176]     NumberOfBanks: 0
[    26.176]     MemoryModel: 0
[    26.176]     BankSize: 0
[    26.176]     NumberOfImages: 0
[    26.176]     RedMaskSize: 0
[    26.176]     RedFieldPosition: 0
[    26.176]     GreenMaskSize: 0
[    26.176]     GreenFieldPosition: 0
[    26.176]     BlueMaskSize: 0
[    26.176]     BlueFieldPosition: 0
[    26.176]     RsvdMaskSize: 0
[    26.176]     RsvdFieldPosition: 0
[    26.176]     DirectColorModeInfo: 0
[    26.176]     PhysBasePtr: 0x0
[    26.176]     LinBytesPerScanLine: 0
[    26.176]     BnkNumberOfImagePages: 0
[    26.176]     LinNumberOfImagePages: 0
[    26.176]     LinRedMaskSize: 0
[    26.176]     LinRedFieldPosition: 0
[    26.176]     LinGreenMaskSize: 0
[    26.176]     LinGreenFieldPosition: 0
[    26.176]     LinBlueMaskSize: 0
[    26.176]     LinBlueFieldPosition: 0
[    26.176]     LinRsvdMaskSize: 0
[    26.176]     LinRsvdFieldPosition: 0
[    26.176]     MaxPixelClock: 0
[    26.176] Mode: 13c (0x0)
[    26.177]     ModeAttributes: 0x0
[    26.177]     WinAAttributes: 0x0
[    26.177]     WinBAttributes: 0x0
[    26.177]     WinGranularity: 0
[    26.177]     WinSize: 0
[    26.177]     WinASegment: 0x0
[    26.177]     WinBSegment: 0x0
[    26.177]     WinFuncPtr: 0x0
[    26.177]     BytesPerScanline: 0
[    26.177]     XResolution: 0
[    26.177]     YResolution: 0
[    26.177]     XCharSize: 0
[    26.177]     YCharSize: 0
[    26.177]     NumberOfPlanes: 0
[    26.177]     BitsPerPixel: 0
[    26.177]     NumberOfBanks: 0
[    26.177]     MemoryModel: 0
[    26.177]     BankSize: 0
[    26.177]     NumberOfImages: 0
[    26.177]     RedMaskSize: 0
[    26.177]     RedFieldPosition: 0
[    26.177]     GreenMaskSize: 0
[    26.177]     GreenFieldPosition: 0
[    26.177]     BlueMaskSize: 0
[    26.177]     BlueFieldPosition: 0
[    26.177]     RsvdMaskSize: 0
[    26.177]     RsvdFieldPosition: 0
[    26.177]     DirectColorModeInfo: 0
[    26.177]     PhysBasePtr: 0x0
[    26.177]     LinBytesPerScanLine: 0
[    26.177]     BnkNumberOfImagePages: 0
[    26.177]     LinNumberOfImagePages: 0
[    26.177]     LinRedMaskSize: 0
[    26.177]     LinRedFieldPosition: 0
[    26.177]     LinGreenMaskSize: 0
[    26.177]     LinGreenFieldPosition: 0
[    26.177]     LinBlueMaskSize: 0
[    26.177]     LinBlueFieldPosition: 0
[    26.177]     LinRsvdMaskSize: 0
[    26.177]     LinRsvdFieldPosition: 0
[    26.177]     MaxPixelClock: 0
[    26.177] Mode: 14d (0x0)
[    26.177]     ModeAttributes: 0x0
[    26.177]     WinAAttributes: 0x0
[    26.177]     WinBAttributes: 0x0
[    26.177]     WinGranularity: 0
[    26.177]     WinSize: 0
[    26.177]     WinASegment: 0x0
[    26.177]     WinBSegment: 0x0
[    26.177]     WinFuncPtr: 0x0
[    26.177]     BytesPerScanline: 0
[    26.177]     XResolution: 0
[    26.177]     YResolution: 0
[    26.177]     XCharSize: 0
[    26.177]     YCharSize: 0
[    26.177]     NumberOfPlanes: 0
[    26.177]     BitsPerPixel: 0
[    26.177]     NumberOfBanks: 0
[    26.177]     MemoryModel: 0
[    26.177]     BankSize: 0
[    26.177]     NumberOfImages: 0
[    26.177]     RedMaskSize: 0
[    26.177]     RedFieldPosition: 0
[    26.177]     GreenMaskSize: 0
[    26.177]     GreenFieldPosition: 0
[    26.177]     BlueMaskSize: 0
[    26.177]     BlueFieldPosition: 0
[    26.177]     RsvdMaskSize: 0
[    26.177]     RsvdFieldPosition: 0
[    26.177]     DirectColorModeInfo: 0
[    26.177]     PhysBasePtr: 0x0
[    26.177]     LinBytesPerScanLine: 0
[    26.177]     BnkNumberOfImagePages: 0
[    26.177]     LinNumberOfImagePages: 0
[    26.177]     LinRedMaskSize: 0
[    26.177]     LinRedFieldPosition: 0
[    26.177]     LinGreenMaskSize: 0
[    26.177]     LinGreenFieldPosition: 0
[    26.177]     LinBlueMaskSize: 0
[    26.177]     LinBlueFieldPosition: 0
[    26.177]     LinRsvdMaskSize: 0
[    26.177]     LinRsvdFieldPosition: 0
[    26.177]     MaxPixelClock: 0
[    26.177] Mode: 15c (0x0)
[    26.177]     ModeAttributes: 0x0
[    26.178]     WinAAttributes: 0x0
[    26.178]     WinBAttributes: 0x0
[    26.178]     WinGranularity: 0
[    26.178]     WinSize: 0
[    26.178]     WinASegment: 0x0
[    26.178]     WinBSegment: 0x0
[    26.178]     WinFuncPtr: 0x0
[    26.178]     BytesPerScanline: 0
[    26.178]     XResolution: 0
[    26.178]     YResolution: 0
[    26.178]     XCharSize: 0
[    26.178]     YCharSize: 0
[    26.178]     NumberOfPlanes: 0
[    26.178]     BitsPerPixel: 0
[    26.178]     NumberOfBanks: 0
[    26.178]     MemoryModel: 0
[    26.178]     BankSize: 0
[    26.178]     NumberOfImages: 0
[    26.178]     RedMaskSize: 0
[    26.178]     RedFieldPosition: 0
[    26.178]     GreenMaskSize: 0
[    26.178]     GreenFieldPosition: 0
[    26.178]     BlueMaskSize: 0
[    26.178]     BlueFieldPosition: 0
[    26.178]     RsvdMaskSize: 0
[    26.178]     RsvdFieldPosition: 0
[    26.178]     DirectColorModeInfo: 0
[    26.178]     PhysBasePtr: 0x0
[    26.178]     LinBytesPerScanLine: 0
[    26.178]     BnkNumberOfImagePages: 0
[    26.178]     LinNumberOfImagePages: 0
[    26.178]     LinRedMaskSize: 0
[    26.178]     LinRedFieldPosition: 0
[    26.178]     LinGreenMaskSize: 0
[    26.178]     LinGreenFieldPosition: 0
[    26.178]     LinBlueMaskSize: 0
[    26.178]     LinBlueFieldPosition: 0
[    26.178]     LinRsvdMaskSize: 0
[    26.178]     LinRsvdFieldPosition: 0
[    26.178]     MaxPixelClock: 0
[    26.178] Mode: 13a (0x0)
[    26.178]     ModeAttributes: 0x0
[    26.178]     WinAAttributes: 0x0
[    26.178]     WinBAttributes: 0x0
[    26.178]     WinGranularity: 0
[    26.178]     WinSize: 0
[    26.178]     WinASegment: 0x0
[    26.178]     WinBSegment: 0x0
[    26.178]     WinFuncPtr: 0x0
[    26.178]     BytesPerScanline: 0
[    26.178]     XResolution: 0
[    26.178]     YResolution: 0
[    26.178]     XCharSize: 0
[    26.178]     YCharSize: 0
[    26.178]     NumberOfPlanes: 0
[    26.178]     BitsPerPixel: 0
[    26.178]     NumberOfBanks: 0
[    26.178]     MemoryModel: 0
[    26.178]     BankSize: 0
[    26.178]     NumberOfImages: 0
[    26.178]     RedMaskSize: 0
[    26.178]     RedFieldPosition: 0
[    26.178]     GreenMaskSize: 0
[    26.178]     GreenFieldPosition: 0
[    26.178]     BlueMaskSize: 0
[    26.178]     BlueFieldPosition: 0
[    26.178]     RsvdMaskSize: 0
[    26.178]     RsvdFieldPosition: 0
[    26.178]     DirectColorModeInfo: 0
[    26.178]     PhysBasePtr: 0x0
[    26.178]     LinBytesPerScanLine: 0
[    26.178]     BnkNumberOfImagePages: 0
[    26.178]     LinNumberOfImagePages: 0
[    26.178]     LinRedMaskSize: 0
[    26.178]     LinRedFieldPosition: 0
[    26.178]     LinGreenMaskSize: 0
[    26.178]     LinGreenFieldPosition: 0
[    26.178]     LinBlueMaskSize: 0
[    26.178]     LinBlueFieldPosition: 0
[    26.178]     LinRsvdMaskSize: 0
[    26.178]     LinRsvdFieldPosition: 0
[    26.178]     MaxPixelClock: 0
[    26.178] Mode: 14b (0x0)
[    26.178]     ModeAttributes: 0x0
[    26.178]     WinAAttributes: 0x0
[    26.178]     WinBAttributes: 0x0
[    26.178]     WinGranularity: 0
[    26.178]     WinSize: 0
[    26.178]     WinASegment: 0x0
[    26.178]     WinBSegment: 0x0
[    26.178]     WinFuncPtr: 0x0
[    26.178]     BytesPerScanline: 0
[    26.178]     XResolution: 0
[    26.178]     YResolution: 0
[    26.178]     XCharSize: 0
[    26.178]     YCharSize: 0
[    26.178]     NumberOfPlanes: 0
[    26.178]     BitsPerPixel: 0
[    26.178]     NumberOfBanks: 0
[    26.179]     MemoryModel: 0
[    26.179]     BankSize: 0
[    26.179]     NumberOfImages: 0
[    26.179]     RedMaskSize: 0
[    26.179]     RedFieldPosition: 0
[    26.179]     GreenMaskSize: 0
[    26.179]     GreenFieldPosition: 0
[    26.179]     BlueMaskSize: 0
[    26.179]     BlueFieldPosition: 0
[    26.179]     RsvdMaskSize: 0
[    26.179]     RsvdFieldPosition: 0
[    26.179]     DirectColorModeInfo: 0
[    26.179]     PhysBasePtr: 0x0
[    26.179]     LinBytesPerScanLine: 0
[    26.179]     BnkNumberOfImagePages: 0
[    26.179]     LinNumberOfImagePages: 0
[    26.179]     LinRedMaskSize: 0
[    26.179]     LinRedFieldPosition: 0
[    26.179]     LinGreenMaskSize: 0
[    26.179]     LinGreenFieldPosition: 0
[    26.179]     LinBlueMaskSize: 0
[    26.179]     LinBlueFieldPosition: 0
[    26.179]     LinRsvdMaskSize: 0
[    26.179]     LinRsvdFieldPosition: 0
[    26.179]     MaxPixelClock: 0
[    26.179] Mode: 15a (0x0)
[    26.179]     ModeAttributes: 0x0
[    26.179]     WinAAttributes: 0x0
[    26.179]     WinBAttributes: 0x0
[    26.179]     WinGranularity: 0
[    26.179]     WinSize: 0
[    26.179]     WinASegment: 0x0
[    26.179]     WinBSegment: 0x0
[    26.179]     WinFuncPtr: 0x0
[    26.179]     BytesPerScanline: 0
[    26.179]     XResolution: 0
[    26.179]     YResolution: 0
[    26.179]     XCharSize: 0
[    26.179]     YCharSize: 0
[    26.179]     NumberOfPlanes: 0
[    26.179]     BitsPerPixel: 0
[    26.179]     NumberOfBanks: 0
[    26.179]     MemoryModel: 0
[    26.179]     BankSize: 0
[    26.179]     NumberOfImages: 0
[    26.179]     RedMaskSize: 0
[    26.179]     RedFieldPosition: 0
[    26.179]     GreenMaskSize: 0
[    26.179]     GreenFieldPosition: 0
[    26.179]     BlueMaskSize: 0
[    26.179]     BlueFieldPosition: 0
[    26.179]     RsvdMaskSize: 0
[    26.179]     RsvdFieldPosition: 0
[    26.179]     DirectColorModeInfo: 0
[    26.179]     PhysBasePtr: 0x0
[    26.179]     LinBytesPerScanLine: 0
[    26.179]     BnkNumberOfImagePages: 0
[    26.179]     LinNumberOfImagePages: 0
[    26.179]     LinRedMaskSize: 0
[    26.179]     LinRedFieldPosition: 0
[    26.179]     LinGreenMaskSize: 0
[    26.179]     LinGreenFieldPosition: 0
[    26.179]     LinBlueMaskSize: 0
[    26.179]     LinBlueFieldPosition: 0
[    26.179]     LinRsvdMaskSize: 0
[    26.179]     LinRsvdFieldPosition: 0
[    26.179]     MaxPixelClock: 0
[    26.184] Mode: 107 (1280x1024)
[    26.188]     ModeAttributes: 0x9b
[    26.188]     WinAAttributes: 0x7
[    26.188]     WinBAttributes: 0x0
[    26.188]     WinGranularity: 64
[    26.188]     WinSize: 64
[    26.188]     WinASegment: 0xa000
[    26.188]     WinBSegment: 0x0
[    26.188]     WinFuncPtr: 0xc000691a
[    26.188]     BytesPerScanline: 1280
[    26.188]     XResolution: 1280
[    26.188]     YResolution: 1024
[    26.188]     XCharSize: 8
[    26.188]     YCharSize: 16
[    26.188]     NumberOfPlanes: 1
[    26.188]     BitsPerPixel: 8
[    26.188]     NumberOfBanks: 1
[    26.188]     MemoryModel: 4
[    26.188]     BankSize: 0
[    26.188]     NumberOfImages: 24
[    26.188]     RedMaskSize: 0
[    26.188]     RedFieldPosition: 0
[    26.188]     GreenMaskSize: 0
[    26.188]     GreenFieldPosition: 0
[    26.188]     BlueMaskSize: 0
[    26.188]     BlueFieldPosition: 0
[    26.188]     RsvdMaskSize: 0
[    26.188]     RsvdFieldPosition: 0
[    26.188]     DirectColorModeInfo: 0
[    26.188]     PhysBasePtr: 0xe0000000
[    26.188]     LinBytesPerScanLine: 1280
[    26.188]     BnkNumberOfImagePages: 24
[    26.188]     LinNumberOfImagePages: 24
[    26.188]     LinRedMaskSize: 0
[    26.188]     LinRedFieldPosition: 0
[    26.188]     LinGreenMaskSize: 0
[    26.188]     LinGreenFieldPosition: 0
[    26.188]     LinBlueMaskSize: 0
[    26.188]     LinBlueFieldPosition: 0
[    26.188]     LinRsvdMaskSize: 0
[    26.188]     LinRsvdFieldPosition: 0
[    26.188]     MaxPixelClock: 230000000
[    26.193] Mode: 11a (1280x1024)
[    26.193]     ModeAttributes: 0x9b
[    26.193]     WinAAttributes: 0x7
[    26.193]     WinBAttributes: 0x0
[    26.193]     WinGranularity: 64
[    26.193]     WinSize: 64
[    26.193]     WinASegment: 0xa000
[    26.193]     WinBSegment: 0x0
[    26.193]     WinFuncPtr: 0xc000691a
[    26.193]     BytesPerScanline: 2560
[    26.193]     XResolution: 1280
[    26.193]     YResolution: 1024
[    26.193]     XCharSize: 8
[    26.193]     YCharSize: 16
[    26.193]     NumberOfPlanes: 1
[    26.193]     BitsPerPixel: 16
[    26.193]     NumberOfBanks: 1
[    26.193]     MemoryModel: 6
[    26.193]     BankSize: 0
[    26.193]     NumberOfImages: 11
[    26.193]     RedMaskSize: 5
[    26.193]     RedFieldPosition: 11
[    26.193]     GreenMaskSize: 6
[    26.193]     GreenFieldPosition: 5
[    26.193]     BlueMaskSize: 5
[    26.193]     BlueFieldPosition: 0
[    26.193]     RsvdMaskSize: 0
[    26.193]     RsvdFieldPosition: 0
[    26.193]     DirectColorModeInfo: 0
[    26.193]     PhysBasePtr: 0xe0000000
[    26.193]     LinBytesPerScanLine: 2560
[    26.193]     BnkNumberOfImagePages: 11
[    26.193]     LinNumberOfImagePages: 11
[    26.193]     LinRedMaskSize: 5
[    26.193]     LinRedFieldPosition: 11
[    26.193]     LinGreenMaskSize: 6
[    26.193]     LinGreenFieldPosition: 5
[    26.193]     LinBlueMaskSize: 5
[    26.193]     LinBlueFieldPosition: 0
[    26.193]     LinRsvdMaskSize: 0
[    26.194]     LinRsvdFieldPosition: 0
[    26.194]     MaxPixelClock: 230000000
[    26.199] *Mode: 11b (1280x1024)
[    26.199]     ModeAttributes: 0x9b
[    26.199]     WinAAttributes: 0x7
[    26.199]     WinBAttributes: 0x0
[    26.199]     WinGranularity: 64
[    26.199]     WinSize: 64
[    26.199]     WinASegment: 0xa000
[    26.199]     WinBSegment: 0x0
[    26.199]     WinFuncPtr: 0xc000691a
[    26.199]     BytesPerScanline: 5120
[    26.199]     XResolution: 1280
[    26.199]     YResolution: 1024
[    26.199]     XCharSize: 8
[    26.199]     YCharSize: 16
[    26.199]     NumberOfPlanes: 1
[    26.199]     BitsPerPixel: 32
[    26.199]     NumberOfBanks: 1
[    26.199]     MemoryModel: 6
[    26.199]     BankSize: 0
[    26.199]     NumberOfImages: 5
[    26.199]     RedMaskSize: 8
[    26.199]     RedFieldPosition: 16
[    26.199]     GreenMaskSize: 8
[    26.199]     GreenFieldPosition: 8
[    26.199]     BlueMaskSize: 8
[    26.199]     BlueFieldPosition: 0
[    26.199]     RsvdMaskSize: 8
[    26.199]     RsvdFieldPosition: 24
[    26.199]     DirectColorModeInfo: 0
[    26.199]     PhysBasePtr: 0xe0000000
[    26.199]     LinBytesPerScanLine: 5120
[    26.199]     BnkNumberOfImagePages: 5
[    26.199]     LinNumberOfImagePages: 5
[    26.199]     LinRedMaskSize: 8
[    26.199]     LinRedFieldPosition: 16
[    26.199]     LinGreenMaskSize: 8
[    26.199]     LinGreenFieldPosition: 8
[    26.199]     LinBlueMaskSize: 8
[    26.199]     LinBlueFieldPosition: 0
[    26.199]     LinRsvdMaskSize: 8
[    26.199]     LinRsvdFieldPosition: 24
[    26.199]     MaxPixelClock: 230000000
[    26.204] Mode: 105 (1024x768)
[    26.204]     ModeAttributes: 0x9b
[    26.204]     WinAAttributes: 0x7
[    26.204]     WinBAttributes: 0x0
[    26.204]     WinGranularity: 64
[    26.204]     WinSize: 64
[    26.204]     WinASegment: 0xa000
[    26.204]     WinBSegment: 0x0
[    26.204]     WinFuncPtr: 0xc000691a
[    26.204]     BytesPerScanline: 1024
[    26.204]     XResolution: 1024
[    26.204]     YResolution: 768
[    26.204]     XCharSize: 8
[    26.204]     YCharSize: 16
[    26.204]     NumberOfPlanes: 1
[    26.204]     BitsPerPixel: 8
[    26.204]     NumberOfBanks: 1
[    26.204]     MemoryModel: 4
[    26.204]     BankSize: 0
[    26.204]     NumberOfImages: 41
[    26.204]     RedMaskSize: 0
[    26.204]     RedFieldPosition: 0
[    26.204]     GreenMaskSize: 0
[    26.204]     GreenFieldPosition: 0
[    26.204]     BlueMaskSize: 0
[    26.204]     BlueFieldPosition: 0
[    26.204]     RsvdMaskSize: 0
[    26.204]     RsvdFieldPosition: 0
[    26.204]     DirectColorModeInfo: 0
[    26.204]     PhysBasePtr: 0xe0000000
[    26.204]     LinBytesPerScanLine: 1024
[    26.204]     BnkNumberOfImagePages: 41
[    26.204]     LinNumberOfImagePages: 41
[    26.204]     LinRedMaskSize: 0
[    26.204]     LinRedFieldPosition: 0
[    26.204]     LinGreenMaskSize: 0
[    26.204]     LinGreenFieldPosition: 0
[    26.204]     LinBlueMaskSize: 0
[    26.204]     LinBlueFieldPosition: 0
[    26.204]     LinRsvdMaskSize: 0
[    26.204]     LinRsvdFieldPosition: 0
[    26.204]     MaxPixelClock: 230000000
[    26.209] Mode: 117 (1024x768)
[    26.209]     ModeAttributes: 0x9b
[    26.209]     WinAAttributes: 0x7
[    26.209]     WinBAttributes: 0x0
[    26.209]     WinGranularity: 64
[    26.209]     WinSize: 64
[    26.209]     WinASegment: 0xa000
[    26.209]     WinBSegment: 0x0
[    26.209]     WinFuncPtr: 0xc000691a
[    26.209]     BytesPerScanline: 2048
[    26.209]     XResolution: 1024
[    26.209]     YResolution: 768
[    26.209]     XCharSize: 8
[    26.209]     YCharSize: 16
[    26.209]     NumberOfPlanes: 1
[    26.209]     BitsPerPixel: 16
[    26.209]     NumberOfBanks: 1
[    26.209]     MemoryModel: 6
[    26.209]     BankSize: 0
[    26.209]     NumberOfImages: 20
[    26.209]     RedMaskSize: 5
[    26.209]     RedFieldPosition: 11
[    26.209]     GreenMaskSize: 6
[    26.209]     GreenFieldPosition: 5
[    26.209]     BlueMaskSize: 5
[    26.209]     BlueFieldPosition: 0
[    26.209]     RsvdMaskSize: 0
[    26.209]     RsvdFieldPosition: 0
[    26.209]     DirectColorModeInfo: 0
[    26.209]     PhysBasePtr: 0xe0000000
[    26.209]     LinBytesPerScanLine: 2048
[    26.209]     BnkNumberOfImagePages: 20
[    26.209]     LinNumberOfImagePages: 20
[    26.209]     LinRedMaskSize: 5
[    26.209]     LinRedFieldPosition: 11
[    26.209]     LinGreenMaskSize: 6
[    26.209]     LinGreenFieldPosition: 5
[    26.209]     LinBlueMaskSize: 5
[    26.209]     LinBlueFieldPosition: 0
[    26.209]     LinRsvdMaskSize: 0
[    26.209]     LinRsvdFieldPosition: 0
[    26.209]     MaxPixelClock: 230000000
[    26.214] *Mode: 118 (1024x768)
[    26.214]     ModeAttributes: 0x9b
[    26.214]     WinAAttributes: 0x7
[    26.214]     WinBAttributes: 0x0
[    26.214]     WinGranularity: 64
[    26.214]     WinSize: 64
[    26.214]     WinASegment: 0xa000
[    26.214]     WinBSegment: 0x0
[    26.214]     WinFuncPtr: 0xc000691a
[    26.214]     BytesPerScanline: 4096
[    26.214]     XResolution: 1024
[    26.214]     YResolution: 768
[    26.214]     XCharSize: 8
[    26.214]     YCharSize: 16
[    26.214]     NumberOfPlanes: 1
[    26.214]     BitsPerPixel: 32
[    26.214]     NumberOfBanks: 1
[    26.214]     MemoryModel: 6
[    26.214]     BankSize: 0
[    26.214]     NumberOfImages: 9
[    26.214]     RedMaskSize: 8
[    26.214]     RedFieldPosition: 16
[    26.214]     GreenMaskSize: 8
[    26.214]     GreenFieldPosition: 8
[    26.214]     BlueMaskSize: 8
[    26.214]     BlueFieldPosition: 0
[    26.214]     RsvdMaskSize: 8
[    26.214]     RsvdFieldPosition: 24
[    26.214]     DirectColorModeInfo: 0
[    26.214]     PhysBasePtr: 0xe0000000
[    26.214]     LinBytesPerScanLine: 4096
[    26.214]     BnkNumberOfImagePages: 9
[    26.214]     LinNumberOfImagePages: 9
[    26.214]     LinRedMaskSize: 8
[    26.214]     LinRedFieldPosition: 16
[    26.214]     LinGreenMaskSize: 8
[    26.214]     LinGreenFieldPosition: 8
[    26.214]     LinBlueMaskSize: 8
[    26.214]     LinBlueFieldPosition: 0
[    26.214]     LinRsvdMaskSize: 8
[    26.214]     LinRsvdFieldPosition: 24
[    26.214]     MaxPixelClock: 230000000
[    26.219] *Mode: 112 (640x480)
[    26.219]     ModeAttributes: 0x9b
[    26.219]     WinAAttributes: 0x7
[    26.219]     WinBAttributes: 0x0
[    26.219]     WinGranularity: 64
[    26.219]     WinSize: 64
[    26.219]     WinASegment: 0xa000
[    26.219]     WinBSegment: 0x0
[    26.219]     WinFuncPtr: 0xc000691a
[    26.219]     BytesPerScanline: 2560
[    26.219]     XResolution: 640
[    26.219]     YResolution: 480
[    26.219]     XCharSize: 8
[    26.219]     YCharSize: 16
[    26.219]     NumberOfPlanes: 1
[    26.219]     BitsPerPixel: 32
[    26.219]     NumberOfBanks: 1
[    26.219]     MemoryModel: 6
[    26.219]     BankSize: 0
[    26.219]     NumberOfImages: 25
[    26.219]     RedMaskSize: 8
[    26.219]     RedFieldPosition: 16
[    26.219]     GreenMaskSize: 8
[    26.219]     GreenFieldPosition: 8
[    26.219]     BlueMaskSize: 8
[    26.219]     BlueFieldPosition: 0
[    26.219]     RsvdMaskSize: 8
[    26.219]     RsvdFieldPosition: 24
[    26.219]     DirectColorModeInfo: 0
[    26.219]     PhysBasePtr: 0xe0000000
[    26.219]     LinBytesPerScanLine: 2560
[    26.219]     BnkNumberOfImagePages: 25
[    26.219]     LinNumberOfImagePages: 25
[    26.219]     LinRedMaskSize: 8
[    26.219]     LinRedFieldPosition: 16
[    26.219]     LinGreenMaskSize: 8
[    26.219]     LinGreenFieldPosition: 8
[    26.219]     LinBlueMaskSize: 8
[    26.219]     LinBlueFieldPosition: 0
[    26.219]     LinRsvdMaskSize: 8
[    26.219]     LinRsvdFieldPosition: 24
[    26.219]     MaxPixelClock: 230000000
[    26.224] Mode: 114 (800x600)
[    26.224]     ModeAttributes: 0x9b
[    26.224]     WinAAttributes: 0x7
[    26.224]     WinBAttributes: 0x0
[    26.224]     WinGranularity: 64
[    26.224]     WinSize: 64
[    26.224]     WinASegment: 0xa000
[    26.224]     WinBSegment: 0x0
[    26.224]     WinFuncPtr: 0xc000691a
[    26.224]     BytesPerScanline: 1600
[    26.224]     XResolution: 800
[    26.224]     YResolution: 600
[    26.224]     XCharSize: 8
[    26.224]     YCharSize: 16
[    26.224]     NumberOfPlanes: 1
[    26.224]     BitsPerPixel: 16
[    26.224]     NumberOfBanks: 1
[    26.224]     MemoryModel: 6
[    26.224]     BankSize: 0
[    26.224]     NumberOfImages: 33
[    26.224]     RedMaskSize: 5
[    26.224]     RedFieldPosition: 11
[    26.224]     GreenMaskSize: 6
[    26.224]     GreenFieldPosition: 5
[    26.224]     BlueMaskSize: 5
[    26.224]     BlueFieldPosition: 0
[    26.224]     RsvdMaskSize: 0
[    26.224]     RsvdFieldPosition: 0
[    26.224]     DirectColorModeInfo: 0
[    26.224]     PhysBasePtr: 0xe0000000
[    26.224]     LinBytesPerScanLine: 1600
[    26.224]     BnkNumberOfImagePages: 33
[    26.224]     LinNumberOfImagePages: 33
[    26.224]     LinRedMaskSize: 5
[    26.224]     LinRedFieldPosition: 11
[    26.224]     LinGreenMaskSize: 6
[    26.224]     LinGreenFieldPosition: 5
[    26.224]     LinBlueMaskSize: 5
[    26.224]     LinBlueFieldPosition: 0
[    26.224]     LinRsvdMaskSize: 0
[    26.224]     LinRsvdFieldPosition: 0
[    26.224]     MaxPixelClock: 230000000
[    26.229] *Mode: 115 (800x600)
[    26.229]     ModeAttributes: 0x9b
[    26.229]     WinAAttributes: 0x7
[    26.229]     WinBAttributes: 0x0
[    26.229]     WinGranularity: 64
[    26.229]     WinSize: 64
[    26.229]     WinASegment: 0xa000
[    26.229]     WinBSegment: 0x0
[    26.229]     WinFuncPtr: 0xc000691a
[    26.229]     BytesPerScanline: 3200
[    26.229]     XResolution: 800
[    26.229]     YResolution: 600
[    26.229]     XCharSize: 8
[    26.229]     YCharSize: 16
[    26.229]     NumberOfPlanes: 1
[    26.229]     BitsPerPixel: 32
[    26.229]     NumberOfBanks: 1
[    26.229]     MemoryModel: 6
[    26.229]     BankSize: 0
[    26.229]     NumberOfImages: 16
[    26.229]     RedMaskSize: 8
[    26.229]     RedFieldPosition: 16
[    26.229]     GreenMaskSize: 8
[    26.229]     GreenFieldPosition: 8
[    26.229]     BlueMaskSize: 8
[    26.229]     BlueFieldPosition: 0
[    26.229]     RsvdMaskSize: 8
[    26.229]     RsvdFieldPosition: 24
[    26.229]     DirectColorModeInfo: 0
[    26.229]     PhysBasePtr: 0xe0000000
[    26.229]     LinBytesPerScanLine: 3200
[    26.229]     BnkNumberOfImagePages: 16
[    26.229]     LinNumberOfImagePages: 16
[    26.229]     LinRedMaskSize: 8
[    26.229]     LinRedFieldPosition: 16
[    26.229]     LinGreenMaskSize: 8
[    26.229]     LinGreenFieldPosition: 8
[    26.229]     LinBlueMaskSize: 8
[    26.229]     LinBlueFieldPosition: 0
[    26.229]     LinRsvdMaskSize: 8
[    26.229]     LinRsvdFieldPosition: 24
[    26.229]     MaxPixelClock: 230000000
[    26.234] Mode: 101 (640x480)
[    26.234]     ModeAttributes: 0x9b
[    26.234]     WinAAttributes: 0x7
[    26.234]     WinBAttributes: 0x0
[    26.234]     WinGranularity: 64
[    26.234]     WinSize: 64
[    26.234]     WinASegment: 0xa000
[    26.234]     WinBSegment: 0x0
[    26.234]     WinFuncPtr: 0xc000691a
[    26.234]     BytesPerScanline: 640
[    26.234]     XResolution: 640
[    26.234]     YResolution: 480
[    26.234]     XCharSize: 8
[    26.234]     YCharSize: 16
[    26.234]     NumberOfPlanes: 1
[    26.234]     BitsPerPixel: 8
[    26.234]     NumberOfBanks: 1
[    26.234]     MemoryModel: 4
[    26.234]     BankSize: 0
[    26.234]     NumberOfImages: 101
[    26.234]     RedMaskSize: 0
[    26.234]     RedFieldPosition: 0
[    26.234]     GreenMaskSize: 0
[    26.234]     GreenFieldPosition: 0
[    26.234]     BlueMaskSize: 0
[    26.234]     BlueFieldPosition: 0
[    26.234]     RsvdMaskSize: 0
[    26.234]     RsvdFieldPosition: 0
[    26.234]     DirectColorModeInfo: 0
[    26.234]     PhysBasePtr: 0xe0000000
[    26.234]     LinBytesPerScanLine: 640
[    26.234]     BnkNumberOfImagePages: 101
[    26.234]     LinNumberOfImagePages: 101
[    26.234]     LinRedMaskSize: 0
[    26.234]     LinRedFieldPosition: 0
[    26.234]     LinGreenMaskSize: 0
[    26.234]     LinGreenFieldPosition: 0
[    26.234]     LinBlueMaskSize: 0
[    26.234]     LinBlueFieldPosition: 0
[    26.234]     LinRsvdMaskSize: 0
[    26.234]     LinRsvdFieldPosition: 0
[    26.234]     MaxPixelClock: 230000000
[    26.238] Mode: 103 (800x600)
[    26.238]     ModeAttributes: 0x9b
[    26.238]     WinAAttributes: 0x7
[    26.238]     WinBAttributes: 0x0
[    26.238]     WinGranularity: 64
[    26.238]     WinSize: 64
[    26.238]     WinASegment: 0xa000
[    26.239]     WinBSegment: 0x0
[    26.239]     WinFuncPtr: 0xc000691a
[    26.239]     BytesPerScanline: 832
[    26.239]     XResolution: 800
[    26.239]     YResolution: 600
[    26.239]     XCharSize: 8
[    26.239]     YCharSize: 16
[    26.239]     NumberOfPlanes: 1
[    26.239]     BitsPerPixel: 8
[    26.239]     NumberOfBanks: 1
[    26.239]     MemoryModel: 4
[    26.239]     BankSize: 0
[    26.239]     NumberOfImages: 62
[    26.239]     RedMaskSize: 0
[    26.239]     RedFieldPosition: 0
[    26.239]     GreenMaskSize: 0
[    26.239]     GreenFieldPosition: 0
[    26.239]     BlueMaskSize: 0
[    26.239]     BlueFieldPosition: 0
[    26.239]     RsvdMaskSize: 0
[    26.239]     RsvdFieldPosition: 0
[    26.239]     DirectColorModeInfo: 0
[    26.239]     PhysBasePtr: 0xe0000000
[    26.239]     LinBytesPerScanLine: 832
[    26.239]     BnkNumberOfImagePages: 62
[    26.239]     LinNumberOfImagePages: 62
[    26.239]     LinRedMaskSize: 0
[    26.239]     LinRedFieldPosition: 0
[    26.239]     LinGreenMaskSize: 0
[    26.239]     LinGreenFieldPosition: 0
[    26.239]     LinBlueMaskSize: 0
[    26.239]     LinBlueFieldPosition: 0
[    26.239]     LinRsvdMaskSize: 0
[    26.239]     LinRsvdFieldPosition: 0
[    26.239]     MaxPixelClock: 230000000
[    26.243] Mode: 111 (640x480)
[    26.243]     ModeAttributes: 0x9b
[    26.243]     WinAAttributes: 0x7
[    26.243]     WinBAttributes: 0x0
[    26.243]     WinGranularity: 64
[    26.243]     WinSize: 64
[    26.243]     WinASegment: 0xa000
[    26.243]     WinBSegment: 0x0
[    26.243]     WinFuncPtr: 0xc000691a
[    26.243]     BytesPerScanline: 1280
[    26.243]     XResolution: 640
[    26.243]     YResolution: 480
[    26.243]     XCharSize: 8
[    26.244]     YCharSize: 16
[    26.244]     NumberOfPlanes: 1
[    26.244]     BitsPerPixel: 16
[    26.244]     NumberOfBanks: 1
[    26.244]     MemoryModel: 6
[    26.244]     BankSize: 0
[    26.244]     NumberOfImages: 50
[    26.244]     RedMaskSize: 5
[    26.244]     RedFieldPosition: 11
[    26.244]     GreenMaskSize: 6
[    26.244]     GreenFieldPosition: 5
[    26.244]     BlueMaskSize: 5
[    26.244]     BlueFieldPosition: 0
[    26.244]     RsvdMaskSize: 0
[    26.244]     RsvdFieldPosition: 0
[    26.244]     DirectColorModeInfo: 0
[    26.244]     PhysBasePtr: 0xe0000000
[    26.244]     LinBytesPerScanLine: 1280
[    26.244]     BnkNumberOfImagePages: 50
[    26.244]     LinNumberOfImagePages: 50
[    26.244]     LinRedMaskSize: 5
[    26.244]     LinRedFieldPosition: 11
[    26.244]     LinGreenMaskSize: 6
[    26.244]     LinGreenFieldPosition: 5
[    26.244]     LinBlueMaskSize: 5
[    26.244]     LinBlueFieldPosition: 0
[    26.244]     LinRsvdMaskSize: 0
[    26.244]     LinRsvdFieldPosition: 0
[    26.244]     MaxPixelClock: 230000000
[    26.244] 
[    26.244] (II) VESA(0): Total Memory: 511 64KB banks (32704kB)
[    26.244] (II) VESA(0): Configured Monitor: Using hsync value of 66.02 kHz
[    26.244] (II) VESA(0): Configured Monitor: Using vrefresh value of 60.02 Hz
[    26.244] (WW) VESA(0): Unable to estimate virtual size
[    26.244] (II) VESA(0): Not using built-in mode "1280x1024" (no mode of this name)
[    26.244] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    26.244] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    26.244] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    26.244] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    26.244] (II) VESA(0): Configured Monitor: Using hsync value of 66.02 kHz
[    26.244] (II) VESA(0): Configured Monitor: Using vrefresh value of 60.02 Hz
[    26.244] (WW) VESA(0): Unable to estimate virtual size
[    26.244] (II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
[    26.244] (II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
[    26.244] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[    26.244] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    26.244] (WW) VESA(0): No valid modes left. Trying aggressive sync range...
[    26.244] (II) VESA(0): Configured Monitor: Using hsync range of 31.50-66.02 kHz
[    26.244] (II) VESA(0): Configured Monitor: Using vrefresh range of 50.00-60.02 Hz
[    26.244] (WW) VESA(0): Unable to estimate virtual size
[    26.244] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    26.244] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    26.244] (**) VESA(0): *Built-in mode "1280x1024"
[    26.244] (**) VESA(0): *Built-in mode "1024x768"
[    26.244] (**) VESA(0): *Built-in mode "800x600"
[    26.244] (**) VESA(0): Display dimensions: (470, 270) mm
[    26.244] (**) VESA(0): DPI set to (69, 96)
[    26.244] (II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (11b)
[    26.245] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    26.246] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    26.247] (**) VESA(0): Using "Shadow Framebuffer"
[    26.247] (II) Loading sub module "shadow"
[    26.247] (II) LoadModule: "shadow"
[    26.247] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    26.247] (II) Module shadow: vendor="X.Org Foundation"
[    26.247]     compiled for 1.10.4, module version = 1.1.0
[    26.247]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.247] (II) Loading sub module "fb"
[    26.247] (II) LoadModule: "fb"
[    26.247] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.247] (II) Module fb: vendor="X.Org Foundation"
[    26.247]     compiled for 1.10.4, module version = 1.0.0
[    26.247]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.247] (==) Depth 24 pixmap format is 32 bpp
[    26.247] (II) Loading sub module "int10"
[    26.247] (II) LoadModule: "int10"
[    26.248] (II) Loading /usr/lib/xorg/modules/libint10.so
[    26.248] (II) Module int10: vendor="X.Org Foundation"
[    26.248]     compiled for 1.10.4, module version = 1.0.0
[    26.248]     ABI class: X.Org Video Driver, version 10.0
[    26.248] (II) VESA(0): initializing int10
[    26.248] (II) VESA(0): Bad V_BIOS checksum
[    26.248] (II) VESA(0): Primary V_BIOS segment is: 0xc000
[    26.248] (II) VESA(0): VESA BIOS detected
[    26.248] (II) VESA(0): VESA VBE Version 3.0
[    26.248] (II) VESA(0): VESA VBE Total Mem: 32704 kB
[    26.248] (II) VESA(0): VESA VBE OEM: Intel(R)Eaglelake Graphics Chipset Accelerated VGA BIOS
[    26.248] (II) VESA(0): VESA VBE OEM Software Rev: 1.0
[    26.248] (II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
[    26.248] (II) VESA(0): VESA VBE OEM Product: Intel(R)Eaglelake Graphics Controller
[    26.248] (II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
[    26.251] (II) VESA(0): virtual address = 0xb56a6000,
    physical address = 0xe0000000, size = 33488896
[    26.545] (II) VESA(0): Setting up VESA Mode 0x11B (1280x1024)
[    26.860] (==) VESA(0): Default visual is TrueColor
[    26.861] (==) VESA(0): Backing store disabled
[    26.861] (==) VESA(0): DPMS enabled
[    26.861] (==) RandR enabled
[    26.861] (II) Initializing built-in extension Generic Event Extension
[    26.861] (II) Initializing built-in extension SHAPE
[    26.861] (II) Initializing built-in extension MIT-SHM
[    26.861] (II) Initializing built-in extension XInputExtension
[    26.861] (II) Initializing built-in extension XTEST
[    26.861] (II) Initializing built-in extension BIG-REQUESTS
[    26.861] (II) Initializing built-in extension SYNC
[    26.861] (II) Initializing built-in extension XKEYBOARD
[    26.861] (II) Initializing built-in extension XC-MISC
[    26.861] (II) Initializing built-in extension SECURITY
[    26.861] (II) Initializing built-in extension XINERAMA
[    26.861] (II) Initializing built-in extension XFIXES
[    26.861] (II) Initializing built-in extension RENDER
[    26.861] (II) Initializing built-in extension RANDR
[    26.861] (II) Initializing built-in extension COMPOSITE
[    26.861] (II) Initializing built-in extension DAMAGE
[    26.861] (II) Initializing built-in extension GESTURE
[    26.869] (II) AIGLX: Screen 0 is not DRI2 capable
[    26.869] (II) AIGLX: Screen 0 is not DRI capable
[    26.869] (II) AIGLX: Trying DRI driver /usr/lib/i386-linux-gnu/dri/swrast_dri.so
[    26.871] (II) AIGLX: Loaded and initialized swrast
[    26.871] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    26.946] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    26.955] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    26.955] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.955] (II) LoadModule: "evdev"
[    26.955] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.956] (II) Module evdev: vendor="X.Org Foundation"
[    26.956]     compiled for 1.10.2, module version = 2.6.0
[    26.956]     Module class: X.Org XInput Driver
[    26.956]     ABI class: X.Org XInput driver, version 12.3
[    26.956] (II) Using input driver 'evdev' for 'Power Button'
[    26.956] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.956] (**) Power Button: always reports core events
[    26.956] (**) Power Button: Device: "/dev/input/event1"
[    26.956] (--) Power Button: Found keys
[    26.956] (II) Power Button: Configuring as keyboard
[    26.956] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    26.956] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.956] (**) Option "xkb_rules" "evdev"
[    26.956] (**) Option "xkb_model" "pc105"
[    26.956] (**) Option "xkb_layout" "us"
[    26.957] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    26.957] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    26.957] (II) Using input driver 'evdev' for 'Video Bus'
[    26.957] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.957] (**) Video Bus: always reports core events
[    26.957] (**) Video Bus: Device: "/dev/input/event5"
[    26.957] (--) Video Bus: Found keys
[    26.957] (II) Video Bus: Configuring as keyboard
[    26.957] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input5/event5"
[    26.957] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD)
[    26.957] (**) Option "xkb_rules" "evdev"
[    26.957] (**) Option "xkb_model" "pc105"
[    26.957] (**) Option "xkb_layout" "us"
[    26.960] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    26.960] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    26.960] (II) Using input driver 'evdev' for 'Power Button'
[    26.960] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.960] (**) Power Button: always reports core events
[    26.960] (**) Power Button: Device: "/dev/input/event0"
[    26.960] (--) Power Button: Found keys
[    26.960] (II) Power Button: Configuring as keyboard
[    26.960] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    26.960] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    26.960] (**) Option "xkb_rules" "evdev"
[    26.960] (**) Option "xkb_model" "pc105"
[    26.961] (**) Option "xkb_layout" "us"
[    26.963] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event6)
[    26.963] (II) No input driver/identifier specified (ignoring)
[    26.963] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event7)
[    26.963] (II) No input driver/identifier specified (ignoring)
[    26.965] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event3)
[    26.965] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    26.966] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    26.966] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.966] (**) Logitech USB Receiver: always reports core events
[    26.966] (**) Logitech USB Receiver: Device: "/dev/input/event3"
[    26.966] (--) Logitech USB Receiver: Found keys
[    26.966] (II) Logitech USB Receiver: Configuring as keyboard
[    26.966] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input3/event3"
[    26.966] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    26.966] (**) Option "xkb_rules" "evdev"
[    26.966] (**) Option "xkb_model" "pc105"
[    26.966] (**) Option "xkb_layout" "us"
[    26.966] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/event4)
[    26.966] (**) Logitech USB Receiver: Applying InputClass "evdev pointer catchall"
[    26.966] (**) Logitech USB Receiver: Applying InputClass "evdev keyboard catchall"
[    26.966] (II) Using input driver 'evdev' for 'Logitech USB Receiver'
[    26.966] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.966] (**) Logitech USB Receiver: always reports core events
[    26.966] (**) Logitech USB Receiver: Device: "/dev/input/event4"
[    26.966] (--) Logitech USB Receiver: Found 20 mouse buttons
[    26.966] (--) Logitech USB Receiver: Found scroll wheel(s)
[    26.966] (--) Logitech USB Receiver: Found relative axes
[    26.966] (--) Logitech USB Receiver: Found x and y relative axes
[    26.967] (--) Logitech USB Receiver: Found absolute axes
[    26.967] (II) evdev-grail: failed to open grail, no gesture support
[    26.967] (--) Logitech USB Receiver: Found keys
[    26.967] (II) Logitech USB Receiver: Configuring as mouse
[    26.967] (II) Logitech USB Receiver: Configuring as keyboard
[    26.967] (II) Logitech USB Receiver: Adding scrollwheel support
[    26.967] (**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
[    26.967] (**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    26.967] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/input/input4/event4"
[    26.967] (II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
[    26.967] (**) Option "xkb_rules" "evdev"
[    26.967] (**) Option "xkb_model" "pc105"
[    26.967] (**) Option "xkb_layout" "us"
[    26.967] (II) Logitech USB Receiver: initialized for relative axes.
[    26.967] (WW) Logitech USB Receiver: ignoring absolute axes.
[    26.967] (**) Logitech USB Receiver: (accel) keeping acceleration scheme 1
[    26.967] (**) Logitech USB Receiver: (accel) acceleration profile 0
[    26.967] (**) Logitech USB Receiver: (accel) acceleration factor: 2.000
[    26.967] (**) Logitech USB Receiver: (accel) acceleration threshold: 4
[    26.967] (II) config/udev: Adding input device Logitech USB Receiver (/dev/input/mouse0)
[    26.967] (II) No input driver/identifier specified (ignoring)
[    26.968] (II) config/udev: Adding input device HP Webcam (/dev/input/event8)
[    26.968] (**) HP Webcam: Applying InputClass "evdev keyboard catchall"
[    26.968] (II) Using input driver 'evdev' for 'HP Webcam'
[    26.968] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.968] (**) HP Webcam: always reports core events
[    26.968] (**) HP Webcam: Device: "/dev/input/event8"
[    26.968] (--) HP Webcam: Found keys
[    26.968] (II) HP Webcam: Configuring as keyboard
[    26.968] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2/2-2:1.0/input/input8/event8"
[    26.968] (II) XINPUT: Adding extended input device "HP Webcam" (type: KEYBOARD)
[    26.968] (**) Option "xkb_rules" "evdev"
[    26.968] (**) Option "xkb_model" "pc105"
[    26.968] (**) Option "xkb_layout" "us"
[    26.972] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    26.972] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    26.972] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    26.972] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    26.972] (**) AT Translated Set 2 keyboard: always reports core events
[    26.972] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    26.972] (--) AT Translated Set 2 keyboard: Found keys
[    26.972] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    26.972] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    26.972] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    26.972] (**) Option "xkb_rules" "evdev"
[    26.972] (**) Option "xkb_model" "pc105"
[    26.972] (**) Option "xkb_layout" "us"
[    55.538] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
```This was a clean install on a all in one HP 200 computer that had win7 home already on it. I have dual boot in grub now. Windows comes up great. I was getting a blank screen at the install until I used nomodeset mode in grub as I mentioned in original post (link). I used F6 when installing and used nomodeset. Your help is greatly appreciated. The display is set at 1280x1024 5:4, I think 1200x1600 would fix this. Its a 20+ in monitor.

The above code is i915.modeset=0, the i915.modeset=1 gave me the same blank screen, the computer is up but nothing on screen. This was what I experienced during the install hence the nomodeset was added to grub and I got everything except that the quality of graphics are pretty low. You wanted i915.modeset=0 added insttead of nomodeset right? I erased it after the grub screen came on and I entered e, and edited the boot line. Erased nomodeset and everything after it and added i915.modeset=0

---

### Post by MAFoElffen on 2011-11-28
> **drillerccg said:**
> ```
[    26.069] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
<<EDIT>>
[    26.070] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-13-generic root=UUID=81678a69-235f-413d-bd5d-d946acfa3664 ro quiet splash i915.modeset=0
<<EDIT>>
[    26.084] (II) LoadModule: "vesa"
[    26.084] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.084] (II) Module vesa: vendor="X.Org Foundation"
[    26.084]     compiled for 1.10.2, module version = 2.3.0
[    26.084]     Module class: X.Org Video Driver
[    26.084]     ABI class: X.Org Video Driver, version 10.0
[    26.084] (II) VESA: driver for VESA chipsets: vesa
[    26.084] (++) using VT number 7
[    26.084] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
<<EDIT>>
[    26.244] (--) VESA(0): Virtual size is 1280x1024 (pitch 1280)
[    26.244] (**) VESA(0): *Built-in mode "1280x1024"
[    26.244] (**) VESA(0): *Built-in mode "1024x768"
[    26.244] (**) VESA(0): *Built-in mode "800x600"
[    26.244] (**) VESA(0): Display dimensions: (470, 270) mm
[    26.244] (**) VESA(0): DPI set to (69, 96)
[    26.244] (II) VESA(0): Attempting to use 60Hz refresh for mode "1280x1024" (11b)
[    26.245] (II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
[    26.246] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
[    26.247] (**) VESA(0): Using "Shadow Framebuffer"

```
This was a clean install on a all in one HP 200 computer that had win7 home already on it. I have dual boot in grub now. Windows comes up great. I was getting a blank screen at the install until I used nomodeset mode in grub as I mentioned in original post (link). I used F6 when installing and used nomodeset. Your help is greatly appreciated. The display is set at 1280x1024 5:4, I think 1200x1600 would fix this. Its a 20+ in monitor.
And it seemed to work with "i915.modeset=0" which reports back a 1280x1024 mode (which seems wrong for DPI (69,96)... VESA modes are limtited. Still ways around that but... That option seemed to put that into a VESA mode, using the VESA driver, without even trying the xserver-xorg-video-intel driver...

Did you try " i915.modeset=1 "?

---

### Post by drillerccg on 2011-11-28
> **MAFoElffen said:**
> And it seemed to work with "i915.modeset=0" which reports back a 1280x1024 mode (which seems wrong for DPI (69,96)... VESA modes are limtited. Still ways around that but... That option seemed to put that into a VESA mode, using the VESA driver, without even trying the xserver-xorg-video-intel driver...

Did you try " i915.modeset=1 "?

sorry I edited my answer, I guess you did not see it. I used the i915.modeset=1 in grub by pusing e and editing the boot line but a no go. Blank screen. the i915.modeset=0 gave me what I had before which was exactly as nomodeset. Still only 1280x1024, nothing larger. What do I do next?

driving home, will be there in 30 minutes.

---

### Post by MAFoElffen on 2011-11-28
> **drillerccg said:**
> sorry I edited my answer, I guess you did not see it. I used the i915.modeset=1 in grub by pusing e and editing the boot line but a no go. Blank screen. the i915.modeset=0 gave me what I had before which was exactly as nomodeset. Still only 1280x1024, nothing larger. What do I do next?
Last test here. Start up gedit from a terminal:
```

gksudo gedit /etc/X11/xorg.conf

```There shouldn't be one, so it should be blank. Cut and paste this into it.
```
[FONT=monospace]
[/FONT]# /etc/X11/xorg.conf 

Section "Device"         
    Identifier      "Configured Video Device" 
            Driver          "intel" 
EndSection  

Section "Monitor"         
    Identifier      "Configured Monitor" 
EndSection  

Section "Screen"         
    Identifier      "Default Screen" 
    Monitor         "Configured Monitor"         
    Device          "Configured Video Device" 
EndSection

```Save, exit and reboot.

If that doesn't work... 
```

sudo servive lightdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg
reboot

```
If that doesn't work... The do a new/fresh/clean reinstall over it... Why? Because that video chipset "should" come up as a default with no problems with the Intel driver that is included.

---

### Post by MAFoElffen on 2011-11-28
Double Post- My cat jumped on my mouse (seriously).

---

### Post by drillerccg on 2011-11-28
> **MAFoElffen said:**
> Last test here. Start up gedit from a terminal:
```

gksudo gedit /etc/X11/xorg.conf

```There shouldn't be one, so it should be blank. Cut and paste this into it.
```
[FONT=monospace]
[/FONT]# /etc/X11/xorg.conf 

Section "Device"         
    Identifier      "Configured Video Device" 
            Driver          "intel" 
EndSection  

Section "Monitor"         
    Identifier      "Configured Monitor" 
EndSection  

Section "Screen"         
    Identifier      "Default Screen" 
    Monitor         "Configured Monitor"         
    Device          "Configured Video Device" 
EndSection

```Save, exit and reboot.

If that doesn't work... 
```

sudo servive lightdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg-reconfigure xserver-xorg
reboot

```If that doesn't work... The do a new/fresh/clean reinstall over it... Why? Because that video chipset "should" come up as a default with no problems with the Intel driver that is included.


sorry I forgot to say that I did this. I have a xorg.conf file because I used this page trying to solve it. [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

it was for mavrick (10.10) but I thought it would help 11.10 too. It didn't obviously. The first section manually enabling did not work so I used the vesa one. I am now going to erase what is in that file and do as you said. Stay tuned, please... Thank you.

---

### Post by drillerccg on 2011-11-28
as it did before with creating a xorg.conf file, the computer starts booting, then goes into a black screen that has a lot of processes start and stop (printed on screen) and then gets stuck at some audio process and not do anything. When I temporary edit grub and erase nomodeset from the boot line, again just a blank screen. I am now going to try to get to a prompt from linux recovery option in the grub to try your last choice before re-installing everything. Stay tuned, thanks.

---

### Post by drillerccg on 2011-11-28
so it did not work at all. I will do a clean install. One question though, my last install from live CD was giving me a blank screen hence the nomodeset setting from the live CD option (by pressing any key when the keyboard logo appears at the bottom and pressing F6 other options and choosing nomodeset, used this link [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132))

What would I do now becasue I think the same thing is going to happen. Thanks for all your help and your time. Will report back.

---

### Post by MAFoElffen on 2011-11-28
> **drillerccg said:**
> so it did not work at all. I will do a clean install. One question though, my last install from live CD was giving me a blank screen hence the nomodeset setting from the live CD option (by pressing any key when the keyboard logo appears at the bottom and pressing F6 other options and choosing nomodeset, used this link [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132))

What would I do now becasue I think the same thing is going to happen. Thanks for all your help and your time. Will report back.
Okay... see you do need to use VESA with a few extra twists.

Keep your xorg.conf, but change the driver listed in the device section to vesa...  Until a fix gets to you.  In the meanwhile- you really need to go to launchpad and file a bug.  There's probably already one similar there.

Then I need some data from your machine to come up with some custom modes for you and your hardware. Install this utility first:
```

sudo apt-get install hwinfo

```The post the results of 
```

sudo hwinfo --frambuffer
sudo hwinfo --monitor
xranr -q

```

---

### Post by drillerccg on 2011-11-28
So I shouldn't do the re-install with nomodeset? here is the info you asked for.

```
Usage: hwinfo [options]
Probe for hardware.
  --short        just a short listing
  --log logfile  write info to logfile
  --debug level  set debuglevel
  --version      show libhd version
  --dump-db n    dump hardware data base, 0: external, 1: internal
  --hw_item      probe for hw_item
  hw_item is one of:
   all, bios, block, bluetooth, braille, bridge, camera, cdrom, chipcard,
   cpu, disk, dsl, dvb, fingerprint, floppy, framebuffer, gfxcard, hub,
   ide, isapnp, isdn, joystick, keyboard, memory, modem, monitor, mouse,
   netcard, network, partition, pci, pcmcia, pcmcia-ctrl, pppoe, printer,
   scanner, scsi, smp, sound, storage-ctrl, sys, tape, tv, usb, usb-ctrl,
   vbe, wlan, zip

  Note: debug info is shown only in the log file. (If you specify a
  log file the debug level is implicitly set to a reasonable value.)
jp@jp-HP-Pavilion-All-in-One-200-5100t-Intel:~$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 2420: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
34: None 00.0: 10002 LCD Monitor                                
  [Created at monitor.95]
  Unique ID: rdCR.xIyOHmFiaoF
  Hardware Class: monitor
  Model: "HP LCD Monitor"
  Vendor: HWP "HP"
  Device: eisa 0x4101 
  Resolution: 1920x1080@60Hz
  Size: 470x270 mm
  Detailed Timings #0:
     Resolution: 1920x1080
     Horizontal: 1920 1980 2040 2060 (+60 +120 +140) -hsync
       Vertical: 1080 1090 1098 1100 (+10 +18 +20) -vsync
    Frequencies: 136.00 MHz, 66.02 kHz, 60.02 Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
jp@jp-HP-Pavilion-All-in-One-200-5100t-Intel:~$ xranr -q

```

---

### Post by MAFoElffen on 2011-11-28
No... No reinstall.  You're right, it looks like it would end up the same... 

And I fatfingered the first command. It should have been:
[code'
sudo hwinfo --framebuffer
[code]
"xranr -q" didn't return anything?

So what resolutions would you be happy with?

---

### Post by drillerccg on 2011-11-29
> **MAFoElffen said:**
> No... No reinstall.  You're right, it looks like it would end up the same... 

And I fatfingered the first command. It should have been:
[code'
sudo hwinfo --framebuffer
```

"xranr -q" didn't return anything?

So what resolutions would you be happy with?


The Windows 7 boot option is set at:

1920x1080  32 bit and 60hz and the graphics look great.

the xranr did-q did not return anything. I don't have a xorg.conf anymore, I think I renamed it per your instruction above. Should I get a VESA one in there? Here is the output again with correct code:

[CODE]> hal.1: read hal dataprocess 2651: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.DxYftecIvTA
  Hardware Class: framebuffer
  Model: "Intel(R)Eaglelake Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R)Eaglelake Graphics Controller"
  SubVendor: "Intel(R)Eaglelake Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 31 MB + 960 kB
  Memory Range: 0xe0000000-0xe1feffff (rw)
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
jp@jp-HP-Pavilion-All-in-One-200-5100t-Intel:~$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 2657: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
34: None 00.0: 10002 LCD Monitor                                
  [Created at monitor.95]
  Unique ID: rdCR.xIyOHmFiaoF
  Hardware Class: monitor
  Model: "HP LCD Monitor"
  Vendor: HWP "HP"
  Device: eisa 0x4101 
  Resolution: 1920x1080@60Hz
  Size: 470x270 mm
  Detailed Timings #0:
     Resolution: 1920x1080
     Horizontal: 1920 1980 2040 2060 (+60 +120 +140) -hsync
       Vertical: 1080 1090 1098 1100 (+10 +18 +20) -vsync
    Frequencies: 136.00 MHz, 66.02 kHz, 60.02 Hz
  Config Status: cfg=new, avail=yes, need=no, active=unknown

jp@jp-HP-Pavilion-All-in-One-200-5100t-Intel:~$ xranr -q
No command 'xranr' found, did you mean:
 Command 'xrandr' from package 'x11-xserver-utils' (main)
xranr: command not found
jp@jp-HP-Pavilion-All-in-One-200-5100t-Intel:~$ 
```

---

### Post by MAFoElffen on 2011-11-29
> **drillerccg said:**
> The Windows 7 boot option is set at:

1920x1080  32 bit and 60hz and the graphics look great.

the xranr did-q did not return anything. I don't have a xorg.conf anymore, I think I renamed it per your instruction above. Should I get a VESA one in there? Here is the output again with correct code:


Please try 
```

xrandr -q

```After that, try this:
```

# /etc/X11/xorg.conf 
# mafoelffen 2011.11.28

Section "Device"         
    Identifier      "Configured Video Device" 
    Driver          "vesa" 
EndSection  

Section "Monitor"         
    Identifier      "Configured Monitor" 
    Modeline "1920x1080 66.02"  192.25  1920 2056 2256 2592  1080 1083 1088 1124 -hsync +vsync
    Option "PreferredMode"   "1920x1080 66.02"
    DisplaySize 470 270
EndSection  

Section "Screen"         
    Identifier      "Default Screen" 
    Monitor         "Configured Monitor"         
    Device          "Configured Video Device" 
    SubSection "Display"
          Depth     32
          Modes     "1920x1080" "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection

```

---

### Post by drillerccg on 2011-11-29
I assume you want me to use that as my xorg.conf file, right? This did not work using ```
gksudo gedit /etc/X11/xorg.conf
``` and then pasting your code in there. It froze at boo time. I deleted the file from ubuntu recovery in grub and it came back up. [COLOR=Red]Do I need to get nomodeset off of grub to boot with this new xorg.conf?[/COLOR]

It appears that the screen only comes up with nomodest in grub. Any other changes or a xorg.conf file it freezes or gives a blank screen. Pretty frustrating. 

Also in the mode line I added " and a space between the first two settings. I think it was a typo but I could be wrong. Doing that gave me a black screen with writings on it last line saned disabled: edit /etc/default/saned

Also, replacing intel for vesa in your code with nomodeset in grub brought the screen back but still in the lower resolution. 

here is the other one


```
xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      61.0* 
   1024x768       61.0  
   800x600        61.0 
```

---

### Post by MAFoElffen on 2011-11-30
> **drillerccg said:**
> I assume you want me to use that as my xorg.conf file, right? This did not work using ```
gksudo gedit /etc/X11/xorg.conf
``` and then pasting your code in there. It froze at boo time. I deleted the file from ubuntu recovery in grub and it came back up. [COLOR=Red]Do I need to get nomodeset off of grub to boot with this new xorg.conf?[/COLOR]

It appears that the screen only comes up with nomodest in grub. Any other changes or a xorg.conf file it freezes or gives a blank screen. Pretty frustrating. 

Also in the mode line I added " and a space between the first two settings. I think it was a typo but I could be wrong. Doing that gave me a black screen with writings on it last line saned disabled: edit /etc/default/saned

Also, replacing intel for vesa in your code with nomodeset in grub brought the screen back but still in the lower resolution. 

here is the other one


```
xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1280 x 1024, maximum 1280 x 1024
default connected 1280x1024+0+0 0mm x 0mm
   1280x1024      61.0* 
   1024x768       61.0  
   800x600        61.0 
```
Corrected My last post.... Muti-tasking at moment on another project-- Text based CLI ditro.

---

### Post by drillerccg on 2011-11-30
> **MAFoElffen said:**
> Corrected My last post.... Muti-tasking at moment on another project-- Text based CLI ditro.

so in the grub at the linux/boot line, after quiet splash if I have the nomodeset with your xorg.conf code, it stays the same resolution and the 1920x1080 does not kick in

if I erase the nomodeset vt.handoff=7, the screen goes black

any suggestions?

I only have this computer for only a few more hours and have to give it back to the owner.

[COLOR=Red]edit:[/COLOR] I had to give the computer back. They will survive I guess with low res graphics until a fix shows up. I just wish they would not put out an upgrade every six months. I think they should have beta testers and just release the LTS to the public. This 11.10 IMHO is a piece of garbage, with Unity and all. Thank god for the 
```
  sudo apt-get install gnome-session-fallback
```to get rid of unity.

---

### Post by diogosiebert on 2012-01-21
I have an HP 200-5110br (I think is the basecally the brasilian versior of  the PC you are having problems) and I was able to find a solution. 

The problem is that the intel driver is not loaded by the Xorg and it seams that the source of the problem it is actually in the kernel. Then to solve the problem I upgraded the Kernel to the 3.2 version. 

```
sudo apt-add-repository ppa:francisbrwn9/kernels && sudo apt-get update && sudo apt-get dist-upgrade -y
```

I pretty sure that will solve your problem and I hope my english is understandable.

---

