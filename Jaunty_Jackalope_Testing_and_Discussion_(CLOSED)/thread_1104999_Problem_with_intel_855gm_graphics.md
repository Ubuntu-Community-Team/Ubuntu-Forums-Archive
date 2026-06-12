---
title: "Problem with intel 855gm graphics"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Gujs on 2009-03-24
Hi,

I have a problem with xserver and intel 855gm graphics. xserver is always started in failsafe mode. For now I didn't change xorg.conf file beacuse I don't know yet how to do this.

I tried it also with 8.04 ubuntu and it is working well with it so it must be something wrong in newer intel driver.

Here is my lspci:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:04.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:04.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

```

Here is ubuntu 9.04 xorg log:
```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.28-10-generic #32-Ubuntu SMP Mon Mar 16 02:49:09 UTC 2009 i686
Build Date: 07 March 2009  02:18:57AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@rothera.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: [    0.006611] (--) probed, [    0.006645] (**) from config file, [    0.006664] (==) default setting,
        [    0.006681] (++) from command line, [    0.006698] (!!) notice, [    0.006716] (II) informational,
        [    0.006733] (WW) warning, [    0.006750] (EE) error, [    0.006767] (NI) not implemented, [    0.006784] (??) unknown.
[    0.007000] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 24 11:51:49 2009
[    0.007149] (==) Using config file: "/etc/X11/xorg.conf"
[    0.007397] (==) No Layout section.  Using the first Screen section.
[    0.007463] (**) |-->Screen "Default Screen" (0)
[    0.007487] (**) |   |-->Monitor "Configured Monitor"
[    0.008305] (**) |   |-->Device "Configured Video Device"
[    0.008382] (==) Automatically adding devices
[    0.008399] (==) Automatically enabling devices
[    0.008662] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
[    0.008926] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    0.008945] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.008960] (II) Cannot locate a core pointer device.
[    0.008974] (II) Cannot locate a core keyboard device.
[    0.008986] (II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.009023] (II) Loader magic: 0x3bc0
[    0.009039] (II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
[    0.009090] (II) Loader running on linux
[    0.009114] (++) using VT number 7

[    0.355404] (--) PCI:*(0@0:2:0) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xd8000000/134217728, 0xe8180000/524288, I/O @ 0x0000cc00/8
[    0.366323] (--) PCI: (0@0:2:1) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe0000000/134217728, 0xe8100000/524288
[    0.366854] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.366934] (II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
[    0.367205] (II) LoadModule: "extmod"
[    0.472997] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.473599] (II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
[    0.473680] (II) Loading extension MIT-SCREEN-SAVER
[    0.473698] (II) Loading extension XFree86-VidModeExtension
[    0.473713] (II) Loading extension XFree86-DGA
[    0.473731] (II) Loading extension DPMS
[    0.473746] (II) Loading extension XVideo
[    0.473763] (II) Loading extension XVideo-MotionCompensation
[    0.473777] (II) Loading extension X-Resource
[    0.473798] (II) LoadModule: "dbe"
[    0.474705] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.474962] (II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
[    0.475034] (II) Loading extension DOUBLE-BUFFER
[    0.475052] (II) LoadModule: "glx"
[    0.475989] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.476443] (II) Module glx: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
[    0.476526] (==) AIGLX enabled
[    0.476560] (II) Loading extension GLX
[    0.476584] (II) LoadModule: "record"
[    0.477524] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.477813] (II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
[    0.477886] (II) Loading extension RECORD
[    0.477903] (II) LoadModule: "dri"
[    0.478784] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.479325] (II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
[    0.479398] (II) Loading extension XFree86-DRI
[    0.483828] (II) LoadModule: "dri2"
[    0.484886] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.485227] (II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
[    0.485295] (II) Loading extension DRI2
[    0.485366] (II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
[    0.504273] (II) Matched intel from file name intel.ids
[    0.506332] (==) Matched intel for the autoconfigured driver
[    0.506360] (==) Assigned the driver to the xf86ConfigLayout
[    0.506381] (II) LoadModule: "intel"
[    0.506961] (II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
[    0.507934] (II) Module intel: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 2.6.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
[    0.508055] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33,
        Mobile IntelÂŽ GM45 Express Chipset,
        Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
[    0.509381] (II) Primary Device is: PCI 00@00:02:0
[    0.579632] (II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
[    0.579984] (II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
[    0.620299] (II) Loading sub module "vgahw"
[    0.620333] (II) LoadModule: "vgahw"
[    0.620625] (II) Loading /usr/lib/xorg/modules//libvgahw.so
[    0.620992] (II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 5.0
[    0.621134] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
[    0.621163] (==) intel(0): Depth 24, [    0.621177] (--) framebuffer bpp 32
[    0.621196] (==) intel(0): RGB weight 888
[    0.621218] (==) intel(0): Default visual is TrueColor
[    0.621376] (II) intel(0): Integrated Graphics Chipset: Intel(R) 852GM
[    0.621402] (--) intel(0): Chipset: "852GM/855GM"
[    0.621421] (--) intel(0): Linear framebuffer at 0xD8000000
[    0.621438] (--) intel(0): IO registers at addr 0xE8180000
[    0.621459] (WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
[    0.625872] (==) intel(0): Using EXA for acceleration
[    0.626077] (II) intel(0): 2 display pipes available.
[    0.626102] (II) Loading sub module "ddc"
[    0.626116] (II) LoadModule: "ddc"
[    0.626157] (II) Module "ddc" already built-in
[    0.626172] (II) Loading sub module "i2c"
[    0.626185] (II) LoadModule: "i2c"
[    0.626213] (II) Module "i2c" already built-in
[    0.626289] (II) intel(0): Output VGA using monitor section Configured Monitor
[    0.626342] (II) intel(0): I2C bus "DVODDC_D" initialized.
[    0.626361] (II) Loading sub module "sil164"
[    0.626375] (II) LoadModule: "sil164"
[    0.627042] (II) Loading /usr/lib/xorg/modules/drivers//sil164.so
[    0.627309] (II) Module sil164: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.627399] (II) intel(0): I2C bus "DVOI2C_E" initialized.
[    0.628152] (II) Loading sub module "ch7xxx"
[    0.628175] (II) LoadModule: "ch7xxx"
[    0.628654] (II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
[    0.628883] (II) Module ch7xxx: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.628967] (II) intel(0): I2C bus "DVOI2C_E" removed.
[    0.628989] (II) intel(0): I2C bus "DVOI2C_E" initialized.
[    0.629651] (II) Loading sub module "ivch"
[    0.629667] (II) LoadModule: "ivch"
[    0.630197] (II) Loading /usr/lib/xorg/modules/drivers//ivch.so
[    0.630434] (II) Module ivch: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.630520] (II) intel(0): I2C bus "DVOI2C_E" removed.
[    0.630542] (II) intel(0): I2C bus "DVOI2C_B" initialized.
[    0.631234] (II) Loading sub module "tfp410"
[    0.631248] (II) LoadModule: "tfp410"
[    0.631953] (II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
[    0.632200] (II) Module tfp410: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.632282] (II) intel(0): I2C bus "DVOI2C_B" removed.
[    0.632304] (II) intel(0): I2C bus "DVOI2C_E" initialized.
[    0.632966] (II) Loading sub module "ch7017"
[    0.632980] (II) LoadModule: "ch7017"
[    0.633436] (II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
[    0.633669] (II) Module ch7017: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.633752] (II) intel(0): I2C bus "DVOI2C_E" removed.
[    0.633774] (II) intel(0): I2C bus "DVOI2C_E" initialized.
[    0.634436] (II) intel(0): I2C bus "DVOI2C_E" removed.
[    0.634452] (II) intel(0): I2C bus "DVODDC_D" removed.
[    0.944968] (II) intel(0): I2C bus "CRTDDC_A" initialized.
[    0.945680] (II) intel(0): I2C bus "CRTDDC_A" removed.
[    1.041300] (II) intel(0): EDID for output VGA
[    1.041360] (II) intel(0): Output VGA disconnected
[    1.041385] (WW) intel(0): No outputs definitely connected, trying again...
[    1.041404] (II) intel(0): Output VGA disconnected
[    1.041427] (WW) intel(0): Unable to find initial modes
[    1.041448] (EE) intel(0): No valid modes.
[    1.387185] (II) UnloadModule: "intel"
[    1.387248] (II) UnloadModule: "ch7017"
[    1.387264] (II) Unloading /usr/lib/xorg/modules/drivers//ch7017.so
[    1.387289] (II) UnloadModule: "tfp410"
[    1.387304] (II) Unloading /usr/lib/xorg/modules/drivers//tfp410.so
[    1.387318] (II) UnloadModule: "ivch"
[    1.387332] (II) Unloading /usr/lib/xorg/modules/drivers//ivch.so
[    1.387346] (II) UnloadModule: "ch7xxx"
[    1.387359] (II) Unloading /usr/lib/xorg/modules/drivers//ch7xxx.so
[    1.387373] (II) UnloadModule: "sil164"
[    1.387386] (II) Unloading /usr/lib/xorg/modules/drivers//sil164.so
[    1.387400] (II) UnloadModule: "vgahw"
[    1.387413] (II) Unloading /usr/lib/xorg/modules//libvgahw.so
[    1.387453] (EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

```


And here is ubuntu 8.04 xorg log which is working:
```
This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux TST-linux 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM

        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 24 12:29:22 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
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
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
        Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
        Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 2.0
        X.Org XInput driver : 2.0
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,3580 card 8086,3580 rev 02 class 06,00,00 hdr 80
(II) PCI: 00:00:1: chip 8086,3584 card 8086,3584 rev 02 class 08,80,00 hdr 00
(II) PCI: 00:00:3: chip 8086,3585 card 8086,3585 rev 02 class 08,80,00 hdr 80
(II) PCI: 00:02:0: chip 8086,3582 card 8086,3582 rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,3582 card 8086,3582 rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1d:0: chip 8086,24c2 card 8086,24c2 rev 02 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 8086,24c2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 8086,24c2 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 8086,24cd rev 02 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 82 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 8086,24c2 rev 02 class 01,01,8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 8086,24c2 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 4943,4552 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:01:0: chip 10ec,8139 card 10ec,8139 rev 10 class 02,00,00 hdr 00
(II) PCI: 01:04:0: chip 1106,3038 card 1106,3038 rev 62 class 0c,03,00 hdr 80
(II) PCI: 01:04:1: chip 1106,3038 card 1106,3038 rev 62 class 0c,03,00 hdr 80
(II) PCI: 01:04:2: chip 1106,3104 card 1106,3104 rev 65 class 0c,03,20 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 1 I/O range:
        [0] -1  0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [1] -1  0       0x0000b400 - 0x0000b4ff (0x100) IX[B]
        [2] -1  0       0x0000b800 - 0x0000b8ff (0x100) IX[B]
        [3] -1  0       0x0000bc00 - 0x0000bcff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xe8000000 - 0xe80fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xd8000000/27, 0xe8180000/19, I/O @ 0xcc00/3
(--) PCI: (0:2:1) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe0000000/27, 0xe8100000/19
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
(II) Active PCI resource ranges:
        [0] -1  0       0xe8001000 - 0xe80010ff (0x100) MX[B]
        [1] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [2] -1  0       0xe8202000 - 0xe82020ff (0x100) MX[B]
        [3] -1  0       0xe8201000 - 0xe82011ff (0x200) MX[B]
        [4] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [5] -1  0       0xe8200000 - 0xe82003ff (0x400) MX[B]
        [6] -1  0       0xe8100000 - 0xe817ffff (0x80000) MX[B](B)
        [7] -1  0       0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
        [8] -1  0       0xe8180000 - 0xe81fffff (0x80000) MX[B](B)
        [9] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [10] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
        [11] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[B]
        [12] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [13] -1 0       0x0000d800 - 0x0000d83f (0x40) IX[B]
        [14] -1 0       0x0000d400 - 0x0000d4ff (0x100) IX[B]
        [15] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [16] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [17] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [18] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [19] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [20] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [21] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [23] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [24] -1 0       0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xe8001000 - 0xe80010ff (0x100) MX[B]
        [1] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [2] -1  0       0xe8202000 - 0xe82020ff (0x100) MX[B]
        [3] -1  0       0xe8201000 - 0xe82011ff (0x200) MX[B]
        [4] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [5] -1  0       0xe8200000 - 0xe82003ff (0x400) MX[B]
        [6] -1  0       0xe8100000 - 0xe817ffff (0x80000) MX[B](B)
        [7] -1  0       0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
        [8] -1  0       0xe8180000 - 0xe81fffff (0x80000) MX[B](B)
        [9] -1  0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [10] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
        [11] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[B]
        [12] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [13] -1 0       0x0000d800 - 0x0000d83f (0x40) IX[B]
        [14] -1 0       0x0000d400 - 0x0000d4ff (0x100) IX[B]
        [15] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [16] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [17] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [18] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [19] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [20] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [21] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [22] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [23] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [24] -1 0       0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe8001000 - 0xe80010ff (0x100) MX[B]
        [5] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [6] -1  0       0xe8202000 - 0xe82020ff (0x100) MX[B]
        [7] -1  0       0xe8201000 - 0xe82011ff (0x200) MX[B]
        [8] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [9] -1  0       0xe8200000 - 0xe82003ff (0x400) MX[B]
        [10] -1 0       0xe8100000 - 0xe817ffff (0x80000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
        [12] -1 0       0xe8180000 - 0xe81fffff (0x80000) MX[B](B)
        [13] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
        [17] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[B]
        [18] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [19] -1 0       0x0000d800 - 0x0000d83f (0x40) IX[B]
        [20] -1 0       0x0000d400 - 0x0000d4ff (0x100) IX[B]
        [21] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [22] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [23] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [24] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [25] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [26] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [27] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [28] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [29] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [30] -1 0       0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
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
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.4.0.90, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 2.2.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.4.0, module version = 1.2.3
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.4.0, module version = 1.2.2
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(--) Chipset 852GM/855GM found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe8001000 - 0xe80010ff (0x100) MX[B]
        [5] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [6] -1  0       0xe8202000 - 0xe82020ff (0x100) MX[B]
        [7] -1  0       0xe8201000 - 0xe82011ff (0x200) MX[B]
        [8] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [9] -1  0       0xe8200000 - 0xe82003ff (0x400) MX[B]
        [10] -1 0       0xe8100000 - 0xe817ffff (0x80000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
        [12] -1 0       0xe8180000 - 0xe81fffff (0x80000) MX[B](B)
        [13] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
        [17] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[B]
        [18] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [19] -1 0       0x0000d800 - 0x0000d83f (0x40) IX[B]
        [20] -1 0       0x0000d400 - 0x0000d4ff (0x100) IX[B]
        [21] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [22] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [23] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [24] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [25] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [26] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [27] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [28] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [29] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [30] -1 0       0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe8001000 - 0xe80010ff (0x100) MX[B]
        [5] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [6] -1  0       0xe8202000 - 0xe82020ff (0x100) MX[B]
        [7] -1  0       0xe8201000 - 0xe82011ff (0x200) MX[B]
        [8] -1  0       0x20000000 - 0x200003ff (0x400) MX[B]
        [9] -1  0       0xe8200000 - 0xe82003ff (0x400) MX[B]
        [10] -1 0       0xe8100000 - 0xe817ffff (0x80000) MX[B](B)
        [11] -1 0       0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
        [12] -1 0       0xe8180000 - 0xe81fffff (0x80000) MX[B](B)
        [13] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [14] 1  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [15] 1  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [16] 1  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [17] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [18] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [19] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
        [20] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[B]
        [21] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [22] -1 0       0x0000d800 - 0x0000d83f (0x40) IX[B]
        [23] -1 0       0x0000d400 - 0x0000d4ff (0x100) IX[B]
        [24] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [25] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [26] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [27] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [28] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [29] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [30] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [31] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [32] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [33] -1 0       0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
        [34] 1  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [35] 1  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.1.0
        ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 0.1.0
        ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 852GM
(--) intel(0): Chipset: "852GM/855GM"
(--) intel(0): Linear framebuffer at 0xD8000000
(--) intel(0): IO registers at addr 0xE8180000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): Output LVDS has no monitor section
(II) intel(0): I2C bus "LVDSDDC_C" initialized.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) intel(0): initializing int10
(WW) intel(0): Bad V_BIOS checksum
(II) intel(0): Primary V_BIOS segment is: 0xc000
(II) intel(0): VESA BIOS detected
(II) intel(0): VESA VBE Version 3.0
(II) intel(0): VESA VBE Total Mem: 32576 kB
(II) intel(0): VESA VBE OEM: Intel(r)852GM/852GME/855GM/855GME Graphics Chip Accelerated VGA BIOS
(II) intel(0): VESA VBE OEM Software Rev: 1.0
(II) intel(0): VESA VBE OEM Vendor: Intel Corporation
(II) intel(0): VESA VBE OEM Product: Intel(r)852GM/852GME/855GM/855GME Graphics Controller
(II) intel(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"
(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org Video Driver, version 2.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): Output VGA disconnected
(II) intel(0): Output LVDS connected
(II) intel(0): Output LVDS using initial mode 1280x800
(II) intel(0): Monitoring connected displays enabled
(II) intel(0): detected 128 kB GTT.
(II) intel(0): detected 32636 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
        compiled for 1.4.0.90, module version = 2.2.0
        ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x71024 (PIPEBSTAT) changed from 0x80000202 to 0x80000242
(WW) intel(0): PIPEBSTAT before: status: FIFO_UNDERRUN VSYNC_INT_STATUS VBLANK_INT_STATUS
(WW) intel(0): PIPEBSTAT after: status: FIFO_UNDERRUN VSYNC_INT_STATUS LBLC_EVENT_STATUS VBLANK_INT_STATUS
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 1   0       0xe8180000 - 0xe81fffff (0x80000) MS[B]
        [1] 1   0       0xd8000000 - 0xdfffffff (0x8000000) MS[B]
        [2] -1  0       0x00100000 - 0x1fffffff (0x1ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xe8001000 - 0xe80010ff (0x100) MX[B]
        [7] -1  0       0xe8000000 - 0xe80000ff (0x100) MX[B]
        [8] -1  0       0xe8202000 - 0xe82020ff (0x100) MX[B]
        [9] -1  0       0xe8201000 - 0xe82011ff (0x200) MX[B]
        [10] -1 0       0x20000000 - 0x200003ff (0x400) MX[B]
        [11] -1 0       0xe8200000 - 0xe82003ff (0x400) MX[B]
        [12] -1 0       0xe8100000 - 0xe817ffff (0x80000) MX[B](B)
        [13] -1 0       0xe0000000 - 0xe7ffffff (0x8000000) MX[B](B)
        [14] -1 0       0xe8180000 - 0xe81fffff (0x80000) MX[B](B)
        [15] -1 0       0xd8000000 - 0xdfffffff (0x8000000) MX[B](B)
        [16] 1  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [17] 1  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [18] 1  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [19] 1  0       0x0000cc00 - 0x0000cc07 (0x8) IS[B]
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [21] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [22] -1 0       0x0000b800 - 0x0000b81f (0x20) IX[B]
        [23] -1 0       0x0000b400 - 0x0000b41f (0x20) IX[B]
        [24] -1 0       0x0000b000 - 0x0000b0ff (0x100) IX[B]
        [25] -1 0       0x0000d800 - 0x0000d83f (0x40) IX[B]
        [26] -1 0       0x0000d400 - 0x0000d4ff (0x100) IX[B]
        [27] -1 0       0x00000500 - 0x0000051f (0x20) IX[B]
        [28] -1 0       0x0000f000 - 0x0000f00f (0x10) IX[B]
        [29] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [30] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [31] -1 0       0x000001f0 - 0x000001f0 (0x1) IX[B]
        [32] -1 0       0x000001f0 - 0x000001f7 (0x8) IX[B]
        [33] -1 0       0x0000c800 - 0x0000c81f (0x20) IX[B]
        [34] -1 0       0x0000c400 - 0x0000c41f (0x20) IX[B]
        [35] -1 0       0x0000c000 - 0x0000c01f (0x20) IX[B]
        [36] -1 0       0x0000cc00 - 0x0000cc07 (0x8) IX[B](B)
        [37] 1  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [38] 1  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) intel(0): Kernel reported 104704 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 418812 kB available
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) [drm] loaded kernel module for "i915" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) intel(0): [drm] Using the DRM lock SAREA also for drawables.
(II) intel(0): [drm] framebuffer mapped by ddx driver
(II) intel(0): [drm] added 1 reserved context for kernel
(II) intel(0): X context handle = 0x1
(II) intel(0): [drm] installed DRM signal handler
(==) intel(0): VideoRam: 131072 KB
(**) intel(0): Framebuffer compression enabled
(**) intel(0): Tiling enabled
(II) intel(0): Attempting memory allocation with tiled buffers.
(WW) intel(0): xf86AllocateGARTMemory: allocation of 1536 pages failed
        (Cannot allocate memory)
(WW) intel(0): Allocation error, framebuffer compression disabled
(WW) intel(0): xf86AllocateGARTMemory: allocation of 10 pages failed
        (Cannot allocate memory)
(II) intel(0): Success.
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(II) intel(0): [drm] Registers = 0xe8180000
(II) intel(0): [drm] ring buffer = 0xd8000000
(II) intel(0): [drm] mapped front buffer at 0xda000000, handle = 0xda000000
(II) intel(0): [drm] mapped back buffer at 0xdb000000, handle = 0xdb000000
(II) intel(0): [drm] mapped depth buffer at 0xdc000000, handle = 0xdc000000
(II) intel(0): [drm] mapped classic textures at 0xdd000000, handle = 0xdd000000
(II) intel(0): [drm] Initialized kernel agp heap manager, 33554432
(II) intel(0): [dri] visual configs initialized
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xd8000000,0x8000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 31457280 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): [DRI] installation complete
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01fdf000 (pgoffset 8159)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x01fe0000 (pgoffset 8160)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x01fe4000 (pgoffset 8164)
(II) intel(0): xf86BindGARTMemory: bind key 3 at 0x01fe5000 (pgoffset 8165)
(II) intel(0): xf86BindGARTMemory: bind key 4 at 0x01fe9000 (pgoffset 8169)
(II) intel(0): xf86BindGARTMemory: bind key 5 at 0x02000000 (pgoffset 8192)
(II) intel(0): xf86BindGARTMemory: bind key 6 at 0x03000000 (pgoffset 12288)
(II) intel(0): xf86BindGARTMemory: bind key 7 at 0x04000000 (pgoffset 16384)
(II) intel(0): xf86BindGARTMemory: bind key 8 at 0x05000000 (pgoffset 20480)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00027fff: logical 3D context (32 kB)
(II) intel(0): 0x00028000-0x01e27fff: exa offscreen (30720 kB)
(II) intel(0): 0x01fdf000:            end of stolen memory
(II) intel(0): 0x01fdf000-0x01fdffff: Core cursor (4 kB, 0x000000001d77b000 physical
)
(II) intel(0): 0x01fe0000-0x01fe3fff: ARGB cursor (16 kB, 0x000000001d5b4000 physical
)
(II) intel(0): 0x01fe4000-0x01fe4fff: Core cursor (4 kB, 0x000000001c2e2000 physical
)
(II) intel(0): 0x01fe5000-0x01fe8fff: ARGB cursor (16 kB, 0x000000001d594000 physical
)
(II) intel(0): 0x01fe9000-0x01fe9fff: overlay registers (4 kB, 0x000000001c286000 physical
)
(II) intel(0): 0x02000000-0x02ffffff: front buffer (10240 kB) X tiled
(II) intel(0): 0x03000000-0x03ffffff: back buffer (10240 kB) X tiled
(II) intel(0): 0x04000000-0x04ffffff: depth buffer (10240 kB) X tiled
(II) intel(0): 0x05000000-0x06ffffff: classic textures (32768 kB)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is off
(II) intel(0):   Display plane A is now disabled and connected to pipe A.
(II) intel(0):   Pipe B is on
(II) intel(0):   Display plane B is now enabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe none
(II) intel(0):   Output LVDS is connected to pipe B
(II) intel(0): [drm] dma control initialized, using IRQ 16
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Enabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/i915_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 211
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "sk"
(**) Generic Keyboard: XkbLayout: "sk"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.
SetClientVersion: 0 9
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): fbc disabled on plane a
(II) intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "LVDSDDC_C:ddc2" removed.

```

Now I would need someone to help me configure xorg.conf file to get intel 855gm work with ubuntu 9.04.

---

### Post by glasen on 2009-03-24
Hi,

Try this content for your xorg.conf :

```
Section "Device"
        Identifier      "Intel"
        Driver  "intel"
        Option  "Legacy3D"   "False"
EndSection
```

This works for my 855GM. Nothing more is needed.

---

### Post by Gujs on 2009-03-24
Hi, thanks for help, but it still doesn't work. My xorg.conf file looks like this:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "Legacy3D"      "False"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```


And xorg.log:

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux user-desktop 2.6.28-10-generic #32-Ubuntu SMP Mon Mar 16 02:49:09 UTC 2009 i686
Build Date: 07 March 2009  02:18:57AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@rothera.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: [    0.002657] (--) probed, [    0.002691] (**) from config file, [    0.002712] (==) default setting,
        [    0.002733] (++) from command line, [    0.002754] (!!) notice, [    0.002774] (II) informational,
        [    0.002795] (WW) warning, [    0.002815] (EE) error, [    0.002835] (NI) not implemented, [    0.002856] (??) unknown.
[    0.003041] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Mar 24 16:19:54 2009
[    0.003160] (==) Using config file: "/etc/X11/xorg.conf"
[    0.003410] (==) No Layout section.  Using the first Screen section.
[    0.003442] (**) |-->Screen "Default Screen" (0)
[    0.003464] (**) |   |-->Monitor "Configured Monitor"
[    0.004268] (**) |   |-->Device "Configured Video Device"
[    0.004356] (==) Automatically adding devices
[    0.004376] (==) Automatically enabling devices
[    0.004572] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
[    0.004705] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
[    0.004726] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.004744] (II) Cannot locate a core pointer device.
[    0.004759] (II) Cannot locate a core keyboard device.
[    0.004774] (II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.004811] (II) Loader magic: 0x3bc0
[    0.004829] (II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
[    0.004888] (II) Loader running on linux
[    0.004912] (++) using VT number 7

[    0.252083] (--) PCI:*(0@0:2:0) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xd8000000/134217728, 0xe8180000/524288, I/O @ 0x0000cc00/8
[    0.252275] (--) PCI: (0@0:2:1) Intel Corporation 82852/855GM Integrated Graphics Device rev 2, Mem @ 0xe0000000/134217728, 0xe8100000/524288
[    0.252740] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.252815] (II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
[    0.253121] (II) LoadModule: "extmod"
[    0.254328] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.254817] (II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
[    0.254902] (II) Loading extension MIT-SCREEN-SAVER
[    0.254922] (II) Loading extension XFree86-VidModeExtension
[    0.254938] (II) Loading extension XFree86-DGA
[    0.254959] (II) Loading extension DPMS
[    0.254976] (II) Loading extension XVideo
[    0.254995] (II) Loading extension XVideo-MotionCompensation
[    0.255011] (II) Loading extension X-Resource
[    0.255030] (II) LoadModule: "dbe"
[    0.255792] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.256017] (II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
[    0.256098] (II) Loading extension DOUBLE-BUFFER
[    0.256120] (II) LoadModule: "glx"
[    0.256862] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.257319] (II) Module glx: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
[    0.257410] (==) AIGLX enabled
[    0.257447] (II) Loading extension GLX
[    0.257474] (II) LoadModule: "record"
[    0.258268] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.258518] (II) Module record: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
[    0.258597] (II) Loading extension RECORD
[    0.258618] (II) LoadModule: "dri"
[    0.259370] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.259819] (II) Module dri: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
[    0.259899] (II) Loading extension XFree86-DRI
[    0.259931] (II) LoadModule: "dri2"
[    0.260686] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.260930] (II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
[    0.260999] (II) Loading extension DRI2
[    0.261023] (II) LoadModule: "intel"
[    0.261518] (II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
[    0.262284] (II) Module intel: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 2.6.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 5.0
[    0.262407] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
        965GM, 965GME/GLE, G33, Q35, Q33,
        Mobile IntelÂŽ GM45 Express Chipset,
        Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
[    0.263770] (II) Primary Device is: PCI 00@00:02:0
[    0.299966] (II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
[    0.300344] (II) resource ranges after probing:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [5] 0   0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [6] 0   0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [7] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [8] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
        [9] 0   0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [10] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
[    0.335026] (II) Loading sub module "vgahw"
[    0.335059] (II) LoadModule: "vgahw"
[    0.335327] (II) Loading /usr/lib/xorg/modules//libvgahw.so
[    0.335629] (II) Module vgahw: vendor="X.Org Foundation"
        compiled for 1.6.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 5.0
[    0.335771] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen" for depth/fbbpp 24/32
[    0.335801] (==) intel(0): Depth 24, [    0.335818] (--) framebuffer bpp 32
[    0.335841] (==) intel(0): RGB weight 888
[    0.335864] (==) intel(0): Default visual is TrueColor
[    0.335932] (**) intel(0): Option "Legacy3D" "False"
[    0.336061] (II) intel(0): Integrated Graphics Chipset: Intel(R) 852GM
[    0.336089] (--) intel(0): Chipset: "852GM/855GM"
[    0.336112] (--) intel(0): Linear framebuffer at 0xD8000000
[    0.336132] (--) intel(0): IO registers at addr 0xE8180000
[    0.336155] (WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
[    0.340513] (==) intel(0): Using EXA for acceleration
[    0.340693] (II) intel(0): 2 display pipes available.
[    0.340720] (II) Loading sub module "ddc"
[    0.340737] (II) LoadModule: "ddc"
[    0.340781] (II) Module "ddc" already built-in
[    0.340844] (II) Loading sub module "i2c"
[    0.340862] (II) LoadModule: "i2c"
[    0.340895] (II) Module "i2c" already built-in
[    0.340970] (II) intel(0): Output VGA using monitor section Configured Monitor
[    0.341024] (II) intel(0): I2C bus "DVODDC_D" initialized.
[    0.341046] (II) Loading sub module "sil164"
[    0.341061] (II) LoadModule: "sil164"
[    0.341553] (II) Loading /usr/lib/xorg/modules/drivers//sil164.so
[    0.341793] (II) Module sil164: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.341889] (II) intel(0): I2C bus "DVOI2C_E" initialized.
[    0.342558] (II) Loading sub module "ch7xxx"
[    0.342575] (II) LoadModule: "ch7xxx"
[    0.343115] (II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
[    0.343320] (II) Module ch7xxx: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.343412] (II) intel(0): I2C bus "DVOI2C_E" removed.
[    0.343438] (II) intel(0): I2C bus "DVOI2C_E" initialized.
[    0.344099] (II) Loading sub module "ivch"
[    0.344116] (II) LoadModule: "ivch"
[    0.344645] (II) Loading /usr/lib/xorg/modules/drivers//ivch.so
[    0.344849] (II) Module ivch: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.344940] (II) intel(0): I2C bus "DVOI2C_E" removed.
[    0.344965] (II) intel(0): I2C bus "DVOI2C_B" initialized.
[    0.345702] (II) Loading sub module "tfp410"
[    0.345724] (II) LoadModule: "tfp410"
[    0.346181] (II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
[    0.346392] (II) Module tfp410: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.346481] (II) intel(0): I2C bus "DVOI2C_B" removed.
[    0.346507] (II) intel(0): I2C bus "DVOI2C_E" initialized.
[    0.347170] (II) Loading sub module "ch7017"
[    0.347187] (II) LoadModule: "ch7017"
[    0.347780] (II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
[    0.347993] (II) Module ch7017: vendor="X.Org Foundation"
        compiled for 1.5.99.902, module version = 1.0.0
        ABI class: X.Org Video Driver, version 5.0
[    0.348085] (II) intel(0): I2C bus "DVOI2C_E" removed.
[    0.348110] (II) intel(0): I2C bus "DVOI2C_E" initialized.
[    0.348773] (II) intel(0): I2C bus "DVOI2C_E" removed.
[    0.348792] (II) intel(0): I2C bus "DVODDC_D" removed.
[    0.610696] (II) intel(0): I2C bus "CRTDDC_A" initialized.
[    0.611403] (II) intel(0): I2C bus "CRTDDC_A" removed.
[    0.707330] (II) intel(0): EDID for output VGA
[    0.707388] (II) intel(0): Output VGA disconnected
[    0.707414] (WW) intel(0): No outputs definitely connected, trying again...
[    0.707435] (II) intel(0): Output VGA disconnected
[    0.707459] (WW) intel(0): Unable to find initial modes
[    0.707483] (EE) intel(0): No valid modes.
[    1.051802] (II) UnloadModule: "intel"
[    1.051859] (II) UnloadModule: "ch7017"
[    1.051878] (II) Unloading /usr/lib/xorg/modules/drivers//ch7017.so
[    1.051904] (II) UnloadModule: "tfp410"
[    1.051921] (II) Unloading /usr/lib/xorg/modules/drivers//tfp410.so
[    1.051939] (II) UnloadModule: "ivch"
[    1.051955] (II) Unloading /usr/lib/xorg/modules/drivers//ivch.so
[    1.051972] (II) UnloadModule: "ch7xxx"
[    1.051988] (II) Unloading /usr/lib/xorg/modules/drivers//ch7xxx.so
[    1.052005] (II) UnloadModule: "sil164"
[    1.052021] (II) Unloading /usr/lib/xorg/modules/drivers//sil164.so
[    1.052038] (II) UnloadModule: "vgahw"
[    1.052054] (II) Unloading /usr/lib/xorg/modules//libvgahw.so
[    1.052079] (EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


```

What I know for now is, that my xorg.conf is missing screen settings. But I don't know why previous intel driver in Ubuntu 8.04 didn't need this screen configuration.

I am using touchscreen terminal with LCD 1280x800 resolution. Now I have to figure out, how to configure screen section for this LCD.

---

### Post by glasen on 2009-03-24
It seems that the Xserver does not find any display on your notebook. My xorg.conf only helps against the famous "BO Front Buffer"-Bug.

Can you please post your complete hardware configuration.

---

### Post by Gujs on 2009-03-24
This is Jaotech touchscreen terminal with 15" wide screen LCD 1280x800 resolution. It has 600MHz Intel Celeron CPU and 512MB of mamory.

lspci:
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:04.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:04.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:04.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

```

lsusb:
```
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 049f:0051 Compaq Computer Corp. KU-0133 Easy Access Interner Keyboard
Bus 002 Device 003: ID 0ca6:0010 Castles Technology Co., Ltd EZUSB PC/SC Smart Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

cpuinfo:
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Genuine Intel(R) processor               600MHz
stepping        : 5
cpu MHz         : 598.054
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe up bts
bogomips        : 1196.10
clflush size    : 64
power management:

```

dmesg:
```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-10-generic (buildd@lansones) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu3) ) #32-Ubuntu SMP Mon Mar 16 02:49:09 UTC 2009 (Ubuntu 2.6.28-10.32-generic)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  BIOS-e820: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001dff3000 - 000000001e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.2 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x1dff0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000001dff0000 (usable)
[    0.000000]  modified: 000000001dff0000 - 000000001dff3000 (ACPI NVS)
[    0.000000]  modified: 000000001dff3000 - 000000001e000000 (ACPI data)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 1dff0000 @ 10000-16000
[    0.000000] RAMDISK: 1d898000 - 1dfdf90f
[    0.000000] ACPI: RSDP 000F6700, 0014 (r0 IntelR)
[    0.000000] ACPI: RSDT 1DFF3000, 002C (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1DFF3040, 0074 (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1DFF30C0, 3B61 (r1 INTELR AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1DFF0000, 0040
[    0.000000] ACPI: APIC 1DFF6C40, 005A (r1 IntelR AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 479MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1dff0000
[    0.000000]   low ram: 00000000 - 1dff0000
[    0.000000]   bootmap 00012000 - 00015c00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001dff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000086b52c]    TEXT DATA BSS ==> [0000100000 - 000086b52c]
[    0.000000]   #4 [001d898000 - 001dfdf90f]          RAMDISK ==> [001d898000 - 001dfdf90f]
[    0.000000]   #5 [000086c000 - 0000870000]    INIT_PG_TABLE ==> [000086c000 - 0000870000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #8 [0000012000 - 0000016000]          BOOTMAP ==> [0000012000 - 0000016000]
[    0.000000] found SMP MP-table at [c00f4ca0] 000f4ca0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001dff0
[    0.000000]   HighMem  0x0001dff0 -> 0x0001dff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001dff0
[    0.000000] On node 0 totalpages: 122751
[    0.000000] free_area_init_node: node 0, pgdat c06c0d80, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 928 pages used for memmap
[    0.000000]   Normal zone: 117840 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 1e000000:e0c00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 121791
[    0.000000] Kernel command line: root=UUID=48597cf5-737c-4e0f-b2c2-4d94a38c49e3 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops
[    0.000000] Detected 598.054 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.004000] allocated 2456960 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 468960k/491456k available (4068k kernel code, 21796k reserved, 2203k data, 528k init, 0k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xde7f0000 - 0xff3fe000   ( 524 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xddff0000   ( 479 MB)
[    0.004000]       .init : 0xc0727000 - 0xc07ab000   ( 528 kB)
[    0.004000]       .data : 0xc04f914f - 0xc071fe60   (2203 kB)
[    0.004000]       .text : 0xc0100000 - 0xc04f914f   (4068 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.004018] Calibrating delay loop (skipped), value calculated using timer frequency.. 1196.10 BogoMIPS (lpj=2392216)
[    0.004063] Security Framework initialized
[    0.004077] SELinux:  Disabled at boot.
[    0.004128] AppArmor: AppArmor initialized
[    0.004148] Mount-cache hash table entries: 512
[    0.004460] Initializing cgroup subsys ns
[    0.004472] Initializing cgroup subsys cpuacct
[    0.004480] Initializing cgroup subsys memory
[    0.004490] Initializing cgroup subsys freezer
[    0.004525] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004534] CPU: L2 cache: 512K
[    0.004557] Checking 'hlt' instruction... OK.
[    0.021625] SMP alternatives: switching to UP code
[    0.317411] Freeing SMP alternatives: 18k freed
[    0.317421] ACPI: Core revision 20080926
[    0.322540] ACPI: Checking initramfs for custom DSDT
[    1.368363] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.408062] CPU0: Genuine Intel(R) processor               600MHz stepping 05
[    1.412003] Brought up 1 CPUs
[    1.412003] Total of 1 processors activated (1196.10 BogoMIPS).
[    1.412003] CPU0 attaching NULL sched-domain.
[    1.412003] net_namespace: 776 bytes
[    1.412003] Booting paravirtualized kernel on bare hardware
[    1.412003] Time: 15:19:22  Date: 03/24/09
[    1.412003] regulator: core version 0.5
[    1.412003] NET: Registered protocol family 16
[    1.412003] EISA bus registered
[    1.412003] ACPI: bus type pci registered
[    1.435969] PCI: PCI BIOS revision 2.10 entry at 0xfa9f0, last bus=1
[    1.435977] PCI: Using configuration type 1 for base access
[    1.447932] ACPI: EC: Look up EC in DSDT
[    1.462268] ACPI: Interpreter enabled
[    1.462280] ACPI: (supports S0 S1 S4 S5)
[    1.462344] ACPI: Using IOAPIC for interrupt routing
[    1.476124] ACPI: No dock devices found.
[    1.476167] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    1.476499] pci 0000:00:02.0: reg 10 32bit mmio: [0xd8000000-0xdfffffff]
[    1.476511] pci 0000:00:02.0: reg 14 32bit mmio: [0xe8180000-0xe81fffff]
[    1.476524] pci 0000:00:02.0: reg 18 io port: [0xcc00-0xcc07]
[    1.476554] pci 0000:00:02.0: supports D1
[    1.476588] pci 0000:00:02.1: reg 10 32bit mmio: [0xe0000000-0xe7ffffff]
[    1.476600] pci 0000:00:02.1: reg 14 32bit mmio: [0xe8100000-0xe817ffff]
[    1.476634] pci 0000:00:02.1: supports D1
[    1.476733] pci 0000:00:1d.0: reg 20 io port: [0xc000-0xc01f]
[    1.476806] pci 0000:00:1d.1: reg 20 io port: [0xc400-0xc41f]
[    1.476875] pci 0000:00:1d.2: reg 20 io port: [0xc800-0xc81f]
[    1.476944] pci 0000:00:1d.7: reg 10 32bit mmio: [0xe8200000-0xe82003ff]
[    1.477002] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.477013] pci 0000:00:1d.7: PME# disabled
[    1.477074] * The chipset may have PM-Timer Bug. Due to workarounds for a bug,
[    1.477078] * this clock source is slow. If you are sure your timer does not have
[    1.477083] * this bug, please use "acpi_pm_good" to disable the workaround
[    1.477136] HPET not enabled in BIOS. You might try hpet=force boot option
[    1.477152] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH4 ACPI/GPIO/TCO
[    1.477162] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH4 GPIO
[    1.477194] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    1.477207] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    1.477220] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    1.477232] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    1.477246] pci 0000:00:1f.1: reg 20 io port: [0xf000-0xf00f]
[    1.477259] pci 0000:00:1f.1: reg 24 32bit mmio: [0x000000-0x0003ff]
[    1.477327] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    1.477385] pci 0000:00:1f.5: reg 10 io port: [0xd400-0xd4ff]
[    1.477398] pci 0000:00:1f.5: reg 14 io port: [0xd800-0xd83f]
[    1.477411] pci 0000:00:1f.5: reg 18 32bit mmio: [0xe8201000-0xe82011ff]
[    1.477425] pci 0000:00:1f.5: reg 1c 32bit mmio: [0xe8202000-0xe82020ff]
[    1.477459] pci 0000:00:1f.5: PME# supported from D0 D3hot D3cold
[    1.477468] pci 0000:00:1f.5: PME# disabled
[    1.477528] pci 0000:01:01.0: reg 10 io port: [0xb000-0xb0ff]
[    1.477542] pci 0000:01:01.0: reg 14 32bit mmio: [0xe8000000-0xe80000ff]
[    1.477586] pci 0000:01:01.0: supports D1 D2
[    1.477593] pci 0000:01:01.0: PME# supported from D1 D2 D3hot D3cold
[    1.477602] pci 0000:01:01.0: PME# disabled
[    1.477670] pci 0000:01:04.0: reg 20 io port: [0xb400-0xb41f]
[    1.477697] pci 0000:01:04.0: supports D1 D2
[    1.477704] pci 0000:01:04.0: PME# supported from D0 D1 D2 D3hot
[    1.477713] pci 0000:01:04.0: PME# disabled
[    1.477777] pci 0000:01:04.1: reg 20 io port: [0xb800-0xb81f]
[    1.477805] pci 0000:01:04.1: supports D1 D2
[    1.477811] pci 0000:01:04.1: PME# supported from D0 D1 D2 D3hot
[    1.477820] pci 0000:01:04.1: PME# disabled
[    1.477864] pci 0000:01:04.2: reg 10 32bit mmio: [0xe8001000-0xe80010ff]
[    1.477913] pci 0000:01:04.2: supports D1 D2
[    1.477919] pci 0000:01:04.2: PME# supported from D0 D1 D2 D3hot
[    1.477928] pci 0000:01:04.2: PME# disabled
[    1.477984] pci 0000:00:1e.0: transparent bridge
[    1.477994] pci 0000:00:1e.0: bridge io port: [0xb000-0xbfff]
[    1.478005] pci 0000:00:1e.0: bridge 32bit mmio: [0xe8000000-0xe80fffff]
[    1.478025] bus 00 -> node 0
[    1.478048] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.478768] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    1.500690] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    1.501044] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    1.501390] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    1.501734] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    1.502079] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    1.502437] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    1.502787] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    1.503136] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[    1.503675] ACPI: WMI: Mapper loaded
[    1.504704] SCSI subsystem initialized
[    1.504801] libata version 3.00 loaded.
[    1.505141] usbcore: registered new interface driver usbfs
[    1.505263] usbcore: registered new interface driver hub
[    1.505399] usbcore: registered new device driver usb
[    1.506387] PCI: Using ACPI for IRQ routing
[    1.506681] Bluetooth: Core ver 2.13
[    1.506681] NET: Registered protocol family 31
[    1.506681] Bluetooth: HCI device and connection manager initialized
[    1.506681] Bluetooth: HCI socket layer initialized
[    1.506681] NET: Registered protocol family 8
[    1.506681] NET: Registered protocol family 20
[    1.506681] NetLabel: Initializing
[    1.506681] NetLabel:  domain hash size = 128
[    1.506681] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.506681] NetLabel:  unlabeled traffic allowed by default
[    1.506681] AppArmor: AppArmor Filesystem Enabled
[    1.506681] pnp: PnP ACPI init
[    1.506681] ACPI: bus type pnp registered
[    1.516578] pnp: PnP ACPI: found 12 devices
[    1.516585] ACPI: ACPI bus type pnp unregistered
[    1.516596] PnPBIOS: Disabled by ACPI PNP
[    1.516628] system 00:01: ioport range 0xb78-0xb7b has been reserved
[    1.516637] system 00:01: ioport range 0xf78-0xf7b has been reserved
[    1.516646] system 00:01: ioport range 0xa78-0xa7b has been reserved
[    1.516655] system 00:01: ioport range 0xe78-0xe7b has been reserved
[    1.516664] system 00:01: ioport range 0xbbc-0xbbf has been reserved
[    1.516673] system 00:01: ioport range 0xfbc-0xfbf has been reserved
[    1.516682] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    1.516707] system 00:09: ioport range 0x400-0x4bf could not be reserved
[    1.516728] system 00:0b: iomem range 0xd0000-0xd3fff has been reserved
[    1.516737] system 00:0b: iomem range 0xf0000-0xf7fff could not be reserved
[    1.516746] system 00:0b: iomem range 0xf8000-0xfbfff could not be reserved
[    1.516755] system 00:0b: iomem range 0xfc000-0xfffff could not be reserved
[    1.516765] system 00:0b: iomem range 0x1dff0000-0x1dffffff could not be reserved
[    1.516775] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    1.516784] system 00:0b: iomem range 0x100000-0x1dfeffff could not be reserved
[    1.516794] system 00:0b: iomem range 0xfec00000-0xfecfffff has been reserved
[    1.516803] system 00:0b: iomem range 0xfee00000-0xfeefffff has been reserved
[    1.516813] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[    1.516823] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    1.516840] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    1.552943] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    1.552953] pci 0000:00:1e.0:   IO window: 0xb000-0xbfff
[    1.552965] pci 0000:00:1e.0:   MEM window: 0xe8000000-0xe80fffff
[    1.552975] pci 0000:00:1e.0:   PREFETCH window: disabled
[    1.553001] pci 0000:00:1e.0: setting latency timer to 64
[    1.553012] bus: 00 index 0 io port: [0x00-0xffff]
[    1.553019] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    1.553027] bus: 01 index 0 io port: [0xb000-0xbfff]
[    1.553035] bus: 01 index 1 mmio: [0xe8000000-0xe80fffff]
[    1.553042] bus: 01 index 2 mmio: [0x0-0x0]
[    1.553049] bus: 01 index 3 io port: [0x00-0xffff]
[    1.553056] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    1.553085] NET: Registered protocol family 2
[    1.553499] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    1.554257] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    1.554426] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    1.554593] TCP: Hash tables configured (established 16384 bind 16384)
[    1.554600] TCP reno registered
[    1.554835] NET: Registered protocol family 1
[    1.555168] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    2.586049]  it is
[    3.681378] Freeing initrd memory: 7454k freed
[    3.681981] cpufreq: No nForce2 chipset.
[    3.683052] audit: initializing netlink socket (disabled)
[    3.683090] type=2000 audit(1237907964.680:1): initialized
[    3.712123] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    3.720133] VFS: Disk quotas dquot_6.5.1
[    3.720426] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    3.723637] fuse init (API version 7.10)
[    3.724193] msgmni has been set to 931
[    3.724764] alg: No test for stdrng (krng)
[    3.724799] io scheduler noop registered
[    3.724805] io scheduler anticipatory registered
[    3.724812] io scheduler deadline registered
[    3.724876] io scheduler cfq registered (default)
[    3.724922] pci 0000:00:02.0: Boot video device
[    3.732411] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    3.732504] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    3.733195] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    3.733204] ACPI: Power Button (FF) [PWRF]
[    3.733418] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    3.733427] ACPI: Power Button (CM) [PWRB]
[    3.733630] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    3.733646] ACPI: Sleep Button (CM) [SLPB]
[    3.733934] fan PNP0C0B:00: registered as cooling_device0
[    3.733952] ACPI: Fan [FAN] (on)
[    3.734763] processor ACPI_CPU:00: registered as cooling_device1
[    3.734777] ACPI: Processor [CPU0] (supports 2 throttling states)
[    3.740616] thermal LNXTHERM:01: registered as thermal_zone0
[    3.741593] ACPI: Thermal Zone [THRM] (40 C)
[    3.741933] isapnp: Scanning for PnP cards...
[    4.095834] isapnp: No Plug & Play device found
[    4.104889] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    4.105086] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.105292] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    4.106429] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    4.106857] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    4.111713] brd: module loaded
[    4.113898] loop: module loaded
[    4.114517] Fixed MDIO Bus: probed
[    4.114536] PPP generic driver version 2.4.2
[    4.114938] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    4.115109] Driver 'sd' needs updating - please use bus_type methods
[    4.115205] Driver 'sr' needs updating - please use bus_type methods
[    4.115715] ata_piix 0000:00:1f.1: version 2.12
[    4.115754] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.115844] ata_piix 0000:00:1f.1: setting latency timer to 64
[    4.115992] scsi0 : ata_piix
[    4.116528] scsi1 : ata_piix
[    4.118626] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    4.118635] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xf008 irq 15
[    4.436483] ata2.00: ATA-6: TOSHIBA MK4032GAX, AD101A, max UDMA/100
[    4.436493] ata2.00: 78140160 sectors, multi 16: LBA48
[    4.444481] ata2.00: configured for UDMA/100
[    4.444753] scsi 1:0:0:0: Direct-Access     ATA      TOSHIBA MK4032GA AD10 PQ: 0 ANSI: 5
[    4.445299] sd 1:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    4.445347] sd 1:0:0:0: [sda] Write Protect is off
[    4.445355] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.445427] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.445616] sd 1:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    4.445658] sd 1:0:0:0: [sda] Write Protect is off
[    4.445665] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.445735] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.445747]  sda: sda1 sda2 < sda5 >
[    4.501086] sd 1:0:0:0: [sda] Attached SCSI disk
[    4.501374] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    4.506760] usbcore: registered new interface driver libusual
[    4.507007] usbcore: registered new interface driver usbserial
[    4.507105] USB Serial support registered for generic
[    4.507211] usbcore: registered new interface driver usbserial_generic
[    4.507219] usbserial: USB Serial Driver core
[    4.507630] PNP: No PS/2 controller found. Probing ports directly.
[    4.509791] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.509805] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.510632] mice: PS/2 mouse device common for all mice
[    4.511420] rtc_cmos 00:03: RTC can wake from S4
[    4.511629] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.511665] rtc0: alarms up to one month, 242 bytes nvram
[    4.512084] device-mapper: uevent: version 1.0.3
[    4.512481] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.512610] device-mapper: multipath: version 1.0.5 loaded
[    4.512619] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.513006] EISA: Probing bus 0 at eisa.0
[    4.513070] EISA: Detected 0 cards.
[    4.513131] cpuidle: using governor ladder
[    4.513137] cpuidle: using governor menu
[    4.515133] TCP cubic registered
[    4.515659] NET: Registered protocol family 10
[    4.517058] lo: Disabled Privacy Extensions
[    4.518163] NET: Registered protocol family 17
[    4.518308] Bluetooth: L2CAP ver 2.11
[    4.518314] Bluetooth: L2CAP socket layer initialized
[    4.518322] Bluetooth: SCO (Voice Link) ver 0.6
[    4.518328] Bluetooth: SCO socket layer initialized
[    4.518381] Bluetooth: RFCOMM socket layer initialized
[    4.518403] Bluetooth: RFCOMM TTY layer initialized
[    4.518409] Bluetooth: RFCOMM ver 1.10
[    4.518521] Using IPI No-Shortcut mode
[    4.519017] registered taskstats version 1
[    4.519337]   Magic number: 1:646:336
[    4.519384] tty tty57: hash matches
[    4.519486] rtc_cmos 00:03: setting system clock to 2009-03-24 15:19:25 UTC (1237907965)
[    4.519495] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.519502] EDD information not available.
[    4.520176] Freeing unused kernel memory: 528k freed
[    4.520525] Write protecting the kernel text: 4072k
[    4.520643] Write protecting the kernel read-only data: 1524k
[    5.555618] uhci_hcd: USB Universal Host Controller Interface driver
[    5.555771] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.555791] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.555800] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.555998] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    5.556114] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000c000
[    5.556375] usb usb1: configuration #1 chosen from 1 choice
[    5.556460] hub 1-0:1.0: USB hub found
[    5.556480] hub 1-0:1.0: 2 ports detected
[    5.556761] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.556775] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.556784] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.556929] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    5.556976] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000c400
[    5.557208] usb usb2: configuration #1 chosen from 1 choice
[    5.557285] hub 2-0:1.0: USB hub found
[    5.557304] hub 2-0:1.0: 2 ports detected
[    5.557550] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.557565] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.557573] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.557694] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    5.557743] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000c800
[    5.557984] usb usb3: configuration #1 chosen from 1 choice
[    5.558062] hub 3-0:1.0: USB hub found
[    5.558079] hub 3-0:1.0: 2 ports detected
[    5.558323] uhci_hcd 0000:01:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.558338] uhci_hcd 0000:01:04.0: UHCI Host Controller
[    5.558487] uhci_hcd 0000:01:04.0: new USB bus registered, assigned bus number 4
[    5.558520] uhci_hcd 0000:01:04.0: irq 19, io base 0x0000b400
[    5.558755] usb usb4: configuration #1 chosen from 1 choice
[    5.558834] hub 4-0:1.0: USB hub found
[    5.558852] hub 4-0:1.0: 2 ports detected
[    5.559091] uhci_hcd 0000:01:04.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    5.559105] uhci_hcd 0000:01:04.1: UHCI Host Controller
[    5.559239] uhci_hcd 0000:01:04.1: new USB bus registered, assigned bus number 5
[    5.559272] uhci_hcd 0000:01:04.1: irq 16, io base 0x0000b800
[    5.559504] usb usb5: configuration #1 chosen from 1 choice
[    5.559587] hub 5-0:1.0: USB hub found
[    5.559604] hub 5-0:1.0: 2 ports detected
[    5.579386] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.579396] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    5.579490] ehci_hcd 0000:00:1d.7: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    5.579565] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.579575] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.579781] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 6
[    5.583713] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.583753] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xe8200000
[    5.620878] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    5.620946] 8139cp 0000:01:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    5.633666] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.633931] usb usb6: configuration #1 chosen from 1 choice
[    5.634031] hub 6-0:1.0: USB hub found
[    5.634056] hub 6-0:1.0: 6 ports detected
[    5.634370] ehci_hcd 0000:01:04.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    5.634437] ehci_hcd 0000:01:04.2: EHCI Host Controller
[    5.634615] ehci_hcd 0000:01:04.2: new USB bus registered, assigned bus number 7
[    5.634706] ehci_hcd 0000:01:04.2: irq 17, io mem 0xe8001000
[    5.642189] 8139too Fast Ethernet driver 0.9.28
[    5.644062] ehci_hcd 0000:01:04.2: USB 2.0 started, EHCI 1.00
[    5.644334] usb usb7: configuration #1 chosen from 1 choice
[    5.644423] hub 7-0:1.0: USB hub found
[    5.644450] hub 7-0:1.0: 4 ports detected
[    5.645340] 8139too 0000:01:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.647655] eth0: RealTek RTL8139 at 0xb000, 00:04:5f:86:25:ef, IRQ 17
[    5.647663] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    6.352379] usb 1-1: new low speed USB device using uhci_hcd and address 2
[    6.361700] PM: Starting manual resume from disk
[    6.361711] PM: Resume from partition 8:5
[    6.361716] PM: Checking hibernation image.
[    6.364406] PM: Resume from disk failed.
[    6.412130] kjournald starting.  Commit interval 5 seconds
[    6.412158] EXT3-fs: mounted filesystem with ordered data mode.
[    6.531283] usb 1-1: configuration #1 chosen from 1 choice
[    6.772046] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    6.952061] usb 2-1: configuration #1 chosen from 1 choice
[    7.192044] usb 2-2: new full speed USB device using uhci_hcd and address 3
[    7.366012] usb 2-2: configuration #1 chosen from 1 choice
[    7.608122] usb 4-1: new low speed USB device using uhci_hcd and address 2
[    7.816809] usb 4-1: configuration #1 chosen from 1 choice
[   12.520231] udev: starting version 140
[   12.787293] Linux agpgart interface v0.103
[   12.844752] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   12.845106] agpgart-intel 0000:00:00.0: detected 32636K stolen memory
[   12.846794] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[   12.876126] parport_pc 00:08: reported by Plug and Play ACPI
[   12.876184] parport0: PC-style at 0x310 [PCSPP,TRISTATE]
[   12.993449] usbcore: registered new interface driver hiddev
[   13.010710] input: Logitech USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1:1.0/input/input4
[   13.040499] generic-usb 0003:046D:C00C.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Mouse] on usb-0000:00:1d.0-1/input0
[   13.057420] input: CHICONY Compaq USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input5
[   13.083172] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.088491] generic-usb 0003:049F:0051.0002: input,hidraw1: USB HID v1.10 Keyboard [CHICONY Compaq USB Keyboard] on usb-0000:00:1d.1-1/input0
[   13.097244] intel_rng: FWH not detected
[   13.121616] input: CHICONY Compaq USB Keyboard as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.1/input/input6
[   13.152881] generic-usb 0003:049F:0051.0003: input,hiddev96,hidraw2: USB HID v1.10 Device [CHICONY Compaq USB Keyboard] on usb-0000:00:1d.1-1/input1
[   13.152949] usbcore: registered new interface driver usbhid
[   13.153019] usbhid: v2.6:USB HID core driver
[   13.286679] iTCO_vendor_support: vendor-support=0
[   13.358771] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   13.360156] iTCO_wdt: Found a ICH4 TCO device (Version=1, TCOBASE=0x0460)
[   13.360367] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   13.428719] input: eGalax Inc. as /devices/pci0000:00/0000:00:1e.0/0000:01:04.0/usb4/4-1/4-1:1.0/input/input7
[   13.460468] usbcore: registered new interface driver usbtouchscreen
[   13.527547] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   13.930119] Intel ICH 0000:00:1f.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[   13.930333] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.122343] ppdev: user-space parallel port driver
[   14.252112] intel8x0_measure_ac97_clock: measured 52578 usecs
[   14.252122] intel8x0: clocking to 48000
[   14.646692] lp0: using parport0 (polling).
[   14.866574] Adding 1397612k swap on /dev/sda5.  Priority:-1 extents:1 across:1397612k
[   15.463575] EXT3 FS on sda1, internal journal
[   16.904138] type=1505 audit(1237907977.884:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2402
[   17.199772] type=1505 audit(1237907978.176:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2406
[   17.200290] type=1505 audit(1237907978.180:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2406
[   17.200493] type=1505 audit(1237907978.180:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2406
[   17.200664] type=1505 audit(1237907978.180:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2406
[   17.850933] type=1505 audit(1237907978.828:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2411
[   17.851560] type=1505 audit(1237907978.828:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2411
[   17.982238] type=1505 audit(1237907978.960:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2415
[   22.674407] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.674416] Bluetooth: BNEP filters: protocol multicast
[   22.715828] Bridge firewalling registered
[   29.020942] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

```
I don't know anything else. If you need something else, please tel me where can I find more info about hardware on linux.

---

### Post by Gujs on 2009-03-25
Hi,

I tried various different setting for screen and monitor in xorg.conf and still can't get it to work.

Is it possible to build driver from Ubuntu 8.04 for Jaunty?

---

### Post by castrojo on 2009-03-25
Have you tried moving xorg.conf out of the way and see if X just autodetects and does the right thing?

---

### Post by Gujs on 2009-03-26
I tried that and it was the same. J posted this on intel-gfx mailing list and it seem like it is a bug. Now I am waitnig for a solution from intel guys.

---

