---
title: "broken x-server after upgrade to efty"
date: 2006-11-02
forum: Installation &amp; Upgrades
---

### Post by gweber on 2006-11-02
Hi,

I just upgraded to efty (sudo update-manager -c). Unfortunately my x-server seems to be broken. GDM still starts up, but my Xorg.0.log shows the following entries (after pasting iit, I decided to write my further investigations in front of the log file ;)) ). It ends with "Could not init font path"... The path is there, the files fonts.alias and fonts.dir exist. The weird thing about this stuff is, that it is working with startx as root, but not with startx as user... Also kdm and xdm show up with proper fonts (gdm does not), but if I login afterwards, the fonts get messed up as user, but not as root). I thought it's probably a user file mis-configuration and deleted all .gnome* .gconf* and .k* files, but no improvement... I already tried to re-install all kind of packages which include something like xorg in their name...

I had the same problem on a friend's machine *during* the upgrade, but ut was gone, once it was finished.

Any further suggestions?

Cheers,

   Gernot

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux wetap53 2.6.17-10-386 #2 Fri Oct 13 
18:41:40 UTC 2006 i686
Build Date: 07 July 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown
.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  2 18:28:22 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "DELL 1704FPV"
(**) |   |-->Device "ATI Technologies, Inc. Rage 128 Pro Ultra TF"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) FontPath set to:
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
(II) Open ACPI successful (/var/run/acpid.socket)
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
(II) PCI: 00:00:0: chip 8086,2560 card 1028,0142 rev 01 class 06,00,
00 hdr 00
(II) PCI: 00:01:0: chip 8086,2561 card 0000,0000 rev 01 class 06,04,
00 hdr 01
(II) PCI: 00:1d:0: chip 8086,24c2 card 1028,0142 rev 01 class 0c,03,
00 hdr 80
(II) PCI: 00:1d:1: chip 8086,24c4 card 1028,0142 rev 01 class 0c,03,
00 hdr 00
(II) PCI: 00:1d:2: chip 8086,24c7 card 1028,0142 rev 01 class 0c,03,
00 hdr 00
(II) PCI: 00:1d:7: chip 8086,24cd card 1028,0142 rev 01 class 0c,03,
20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 81 class 06,04,
00 hdr 01
(II) PCI: 00:1f:0: chip 8086,24c0 card 0000,0000 rev 01 class 06,01,
00 hdr 80
(II) PCI: 00:1f:1: chip 8086,24cb card 1028,0142 rev 01 class 01,01,
8a hdr 00
(II) PCI: 00:1f:3: chip 8086,24c3 card 1028,0142 rev 01 class 0c,05,
00 hdr 00
(II) PCI: 00:1f:5: chip 8086,24c5 card 1028,0142 rev 01 class 04,01,
00 hdr 00
(II) PCI: 01:00:0: chip 1002,5446 card 1002,0408 rev 00 class 03,00,
00 hdr 00
(II) PCI: 02:08:0: chip 8086,1039 card 1028,0142 rev 81 class 02,00,
00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is 
set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is 
set)
(II) Bus 1 I/O range:
        [0] -1  0       0x0000e000 - 0x0000e0ff (0x100) IX[B]
        [1] -1  0       0x0000e400 - 0x0000e4ff (0x100) IX[B]
        [2] -1  0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [3] -1  0       0x0000ec00 - 0x0000ecff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xff800000 - 0xff9fffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is
 cleared)
(II) Bus 2 I/O range:
        [0] -1  0       0x0000d000 - 0x0000d0ff (0x100) IX[B]
        [1] -1  0       0x0000d400 - 0x0000d4ff (0x100) IX[B]
        [2] -1  0       0x0000d800 - 0x0000d8ff (0x100) IX[B]
        [3] -1  0       0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xff600000 - 0xff7fffff (0x200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN
 is set)
(--) PCI:*(1:0:0) ATI Technologies Inc Rage 128 Pro Ultra TF rev 0, 
Mem @ 0xf8000000/26, 0xff8fc000/14, I/O @ 0xec00/8, BIOS @ 0x8000000
0/17
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(
B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf0000000 from 0xf7ffffff 
to 0xefffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xff6ff000 - 0xff6fffff (0x1000) MX[B]
        [1] -1  0       0xffa04000 - 0xffa040ff (0x100) MX[B]
        [2] -1  0       0xffa04400 - 0xffa045ff (0x200) MX[B]
        [3] -1  0       0x60000000 - 0x600003ff (0x400) MX[B]
        [4] -1  0       0xffa04800 - 0xffa04bff (0x400) MX[B]
        [5] -1  0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [6] -1  0       0xff800000 - 0xff81ffff (0x20000) MX[B](B)
        [7] -1  0       0xff8fc000 - 0xff8fffff (0x4000) MX[B](B)
        [8] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [9] -1  0       0x0000dcc0 - 0x0000dcff (0x40) IX[B]
        [10] -1 0       0x0000cc40 - 0x0000cc7f (0x40) IX[B]
        [11] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [12] -1 0       0x0000cc80 - 0x0000cc9f (0x20) IX[B]
        [13] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [14] -1 0       0x0000ff40 - 0x0000ff5f (0x20) IX[B]
        [15] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [16] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [17] -1 0       0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xff6ff000 - 0xff6fffff (0x1000) MX[B]
        [1] -1  0       0xffa04000 - 0xffa040ff (0x100) MX[B]
        [2] -1  0       0xffa04400 - 0xffa045ff (0x200) MX[B]
        [3] -1  0       0x60000000 - 0x600003ff (0x400) MX[B]
        [4] -1  0       0xffa04800 - 0xffa04bff (0x400) MX[B]
        [5] -1  0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [6] -1  0       0xff800000 - 0xff81ffff (0x20000) MX[B](B)
        [7] -1  0       0xff8fc000 - 0xff8fffff (0x4000) MX[B](B)
        [8] -1  0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [9] -1  0       0x0000dcc0 - 0x0000dcff (0x40) IX[B]
        [10] -1 0       0x0000cc40 - 0x0000cc7f (0x40) IX[B]
        [11] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [12] -1 0       0x0000cc80 - 0x0000cc9f (0x20) IX[B]
        [13] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [14] -1 0       0x0000ff40 - 0x0000ff5f (0x20) IX[B]
        [15] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [16] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [17] -1 0       0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(
B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(
B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xff6ff000 - 0xff6fffff (0x1000) MX[B]
        [5] -1  0       0xffa04000 - 0xffa040ff (0x100) MX[B]
        [6] -1  0       0xffa04400 - 0xffa045ff (0x200) MX[B]
        [7] -1  0       0x60000000 - 0x600003ff (0x400) MX[B]
        [8] -1  0       0xffa04800 - 0xffa04bff (0x400) MX[B]
        [9] -1  0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [10] -1 0       0xff800000 - 0xff81ffff (0x20000) MX[B](B)
        [11] -1 0       0xff8fc000 - 0xff8fffff (0x4000) MX[B](B)
        [12] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x0000dcc0 - 0x0000dcff (0x40) IX[B]
        [16] -1 0       0x0000cc40 - 0x0000cc7f (0x40) IX[B]
        [17] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [18] -1 0       0x0000cc80 - 0x0000cc9f (0x20) IX[B]
        [19] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [20] -1 0       0x0000ff40 - 0x0000ff5f (0x20) IX[B]
        [21] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [22] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [23] -1 0       0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
(II) LoadModule: "ati"
(II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
(II) Module ati: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 6.6.2
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
(II) ATI: ATI driver (version 6.6.2) for chipsets: ati, ativga
(II) R128: Driver for ATI Rage 128 chipsets:
        ATI Rage 128 Mobility M3 LE (PCI), ATI Rage 128 Mobility M3 
LF (AGP),
        ATI Rage 128 Mobility M4 MF (AGP), ATI Rage 128 Mobility M4 
ML (AGP),
        ATI Rage 128 Pro GL PA (AGP?), ATI Rage 128 Pro GL PB (AGP?)
,
        ATI Rage 128 Pro GL PC (AGP?), ATI Rage 128 Pro GL PD (PCI),
        ATI Rage 128 Pro GL PE (AGP?), ATI Rage 128 Pro GL PF (AGP),
        ATI Rage 128 Pro VR PG (AGP?), ATI Rage 128 Pro VR PH (AGP?)
,
        ATI Rage 128 Pro VR PI (AGP?), ATI Rage 128 Pro VR PJ (AGP?)
,
        ATI Rage 128 Pro VR PK (AGP?), ATI Rage 128 Pro VR PL (AGP?)
,
        ATI Rage 128 Pro VR PM (AGP?), ATI Rage 128 Pro VR PN (AGP?)
,
        ATI Rage 128 Pro VR PO (AGP?), ATI Rage 128 Pro VR PP (PCI),
        ATI Rage 128 Pro VR PQ (AGP?), ATI Rage 128 Pro VR PR (PCI),
        ATI Rage 128 Pro VR PS (AGP?), ATI Rage 128 Pro VR PT (AGP?)
,
        ATI Rage 128 Pro VR PU (AGP?), ATI Rage 128 Pro VR PV (AGP?)
,
        ATI Rage 128 Pro VR PW (AGP?), ATI Rage 128 Pro VR PX (AGP?)
,
        ATI Rage 128 GL RE (PCI), ATI Rage 128 GL RF (AGP),
        ATI Rage 128 RG (AGP), ATI Rage 128 VR RK (PCI),
        ATI Rage 128 VR RL (AGP), ATI Rage 128 4X SE (AGP?),
        ATI Rage 128 4X SF (AGP?), ATI Rage 128 4X SG (AGP?),
        ATI Rage 128 4X SH (AGP?), ATI Rage 128 4X SK (AGP?),
        ATI Rage 128 4X SL (AGP?), ATI Rage 128 4X SM (AGP),
        ATI Rage 128 4X SN (AGP?), ATI Rage 128 Pro ULTRA TF (AGP),
        ATI Rage 128 Pro ULTRA TL (AGP), ATI Rage 128 Pro ULTRA TR (
AGP),
        ATI Rage 128 Pro ULTRA TS (AGP?), ATI Rage 128 Pro ULTRA TT 
(AGP?),
        ATI Rage 128 Pro ULTRA TU (AGP?)
(II) RADEON: Driver for ATI Radeon chipsets: ATI Radeon QD (AGP),
        ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP
),
        ATI Radeon VE/7000 QY (AGP/PCI), ATI Radeon VE/7000 QZ (AGP/
PCI),
        ATI ES1000 515E (PCI), ATI ES1000 5969 (PCI),
        ATI Radeon Mobility M7 LW (AGP),
        ATI Mobility FireGL 7800 M7 LX (AGP),
        ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (
AGP),
        ATI Radeon IGP320 (A3) 4136, ATI Radeon IGP320M (U1) 4336,
        ATI Radeon IGP330/340/350 (A4) 4137,
        ATI Radeon IGP330M/340M/350M (U2) 4337,
        ATI Radeon 7000 IGP (A4+) 4237, ATI Radeon Mobility 7000 IGP
 4437,
        ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
        ATI Radeon 9100 QM (AGP), ATI Radeon 8500 AIW BB (AGP),
        ATI Radeon 8500 AIW BC (AGP), ATI Radeon 7500 QW (AGP/PCI),
        ATI Radeon 7500 QX (AGP/PCI), ATI Radeon 9000/PRO If (AGP/PC
I),
        ATI Radeon 9000 Ig (AGP/PCI), ATI FireGL Mobility 9000 (M9) 
Ld (AGP),
        ATI Radeon Mobility 9000 (M9) Lf (AGP),
        ATI Radeon Mobility 9000 (M9) Lg (AGP),
        ATI Radeon 9100 IGP (A5) 5834,
        ATI Radeon Mobility 9100 IGP (U3) 5835, ATI Radeon 9100 PRO 
IGP 7834,
        ATI Radeon Mobility 9200 IGP 7835, ATI Radeon 9250 5960 (AGP
),
        ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
        ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
        ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
        ATI Radeon Mobility 9200 (M9+) 5C63 (AGP), ATI Radeon 9500 A
D (AGP),
        ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
        ATI FireGL Z1 AG (AGP), ATI Radeon 9700 Pro ND (AGP),
        ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP)
,
        ATI FireGL X1 NG (AGP), ATI Radeon 9600 AP (AGP),
        ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
        ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP),
        ATI FireGL RV360 AV (AGP),
        ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
        ATI Radeon Mobility 9600 (M10) NQ (AGP),
        ATI Radeon Mobility 9600 (M11) NR (AGP),
        ATI Radeon Mobility 9600 (M10) NS (AGP),
        ATI FireGL Mobility T2 (M10) NT (AGP),
        ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon 9650,
        ATI Radeon 9800SE AH (AGP), ATI Radeon 9800 AI (AGP),
        ATI Radeon 9800 AJ (AGP), ATI FireGL X2 AK (AGP),
        ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
        ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
        ATI Radeon X600 (RV380) 3E50 (PCIE),
        ATI FireGL V3200 (RV380) 3E54 (PCIE),
        ATI Radeon Mobility X600 (M24) 3150 (PCIE),
        ATI Radeon Mobility X300 (M24) 3152 (PCIE),
        ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X300 (RV370) 5B60 
(PCIE),
        ATI Radeon X600 (RV370) 5B62 (PCIE),
        ATI Radeon X550 (RV370) 5B63 (PCIE),
        ATI FireGL V3100 (RV370) 5B64 (PCIE),
        ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
        ATI Radeon Mobility X300 (M22) 5460 (PCIE),
        ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
        ATI FireGL M22 GL 5464 (PCIE), ATI Radeon XPRESS 200 5A41 (P
CIE),
        ATI Radeon XPRESS 200M 5A42 (PCIE),
        ATI Radeon XPRESS 200 5A61 (PCIE),
        ATI Radeon XPRESS 200M 5A62 (PCIE),
        ATI Radeon XPRESS 200 5954 (PCIE),
        ATI Radeon XPRESS 200M 5955 (PCIE),
        ATI Radeon XPRESS 200 5974 (PCIE),
        ATI Radeon XPRESS 200M 5975 (PCIE), ATI FireGL V5000 (RV410)
 (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility FireGL V5000 (M26) (PCIE),
        ATI Mobility Radeon X700 XL (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Mobility Radeon X700 (M26) (PCIE),
        ATI Radeon X700 PRO (RV410) (PCIE),
        ATI Radeon X700 XT (RV410) (PCIE), ATI Radeon X700 (RV410) (
PCIE),
        ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 SE (RV410
) (PCIE),
        ATI Radeon X800 (R420) JH (AGP), ATI Radeon X800PRO (R420) J
I (AGP),
        ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK
 (AGP),
        ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AG
P),
        ATI Radeon Mobility 9800 (M18) JN (AGP),
        ATI Radeon X800XT (R420) JP (AGP), ATI Radeon X800 SE (R420)
 (AGP),
        ATI Radeon AIW X800 VE (R420) JT (AGP),
        ATI Radeon X800 (R423) UH (PCIE),
        ATI Radeon X800PRO (R423) UI (PCIE),
        ATI Radeon X800LE (R423) UJ (PCIE),
        ATI Radeon X800SE (R423) UK (PCIE),
        ATI FireGL V5100 (R423) UQ (PCIE),
        ATI FireGL unknown (R423) UR (PCIE),
        ATI FireGL unknown (R423) UT (PCIE),
        ATI Radeon X800XT (R423) 5D57 (PCIE), ATI FireGL V7100 (R423
) (PCIE),
        ATI Mobility FireGL V5100 (M28) (PCIE),
        ATI Mobility Radeon X800 (M28) (PCIE),
        ATI Mobility Radeon X800 XT (M28) (PCIE),
        ATI Radeon X800 (R430) (PCIE), ATI Radeon X800 XL (R430) (PC
IE),
        ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 XTP (R430)
 (PCIE),
        ATI Radeon X850 5D4C (PCIE),
        ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
        ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480)
 (PCIE),
        ATI Radeon X850 XT (R480) (PCIE),
        ATI Radeon X850 XT PE (R480) (PCIE),
        ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 SE (R480) 
(AGP),
        ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 XT PE (R480
) (AGP)
(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Rage 1
28 Pro Ultra TF".
(--) Chipset ATI Rage 128 Pro ULTRA TF (AGP) found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(
B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xff6ff000 - 0xff6fffff (0x1000) MX[B]
        [5] -1  0       0xffa04000 - 0xffa040ff (0x100) MX[B]
        [6] -1  0       0xffa04400 - 0xffa045ff (0x200) MX[B]
        [7] -1  0       0x60000000 - 0x600003ff (0x400) MX[B]
        [8] -1  0       0xffa04800 - 0xffa04bff (0x400) MX[B]
        [9] -1  0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [10] -1 0       0xff800000 - 0xff81ffff (0x20000) MX[B](B)
        [11] -1 0       0xff8fc000 - 0xff8fffff (0x4000) MX[B](B)
        [12] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [13] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [14] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [15] -1 0       0x0000dcc0 - 0x0000dcff (0x40) IX[B]
        [16] -1 0       0x0000cc40 - 0x0000cc7f (0x40) IX[B]
        [17] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [18] -1 0       0x0000cc80 - 0x0000cc9f (0x20) IX[B]
        [19] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [20] -1 0       0x0000ff40 - 0x0000ff5f (0x20) IX[B]
        [21] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [22] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [23] -1 0       0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
(II) Loading sub module "r128"
(II) LoadModule: "r128"
(II) Loading /usr/lib/xorg/modules/drivers/r128_drv.so
(II) Module r128: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 4.1.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 1.0
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(
B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xff6ff000 - 0xff6fffff (0x1000) MX[B]
        [5] -1  0       0xffa04000 - 0xffa040ff (0x100) MX[B]
        [6] -1  0       0xffa04400 - 0xffa045ff (0x200) MX[B]
        [7] -1  0       0x60000000 - 0x600003ff (0x400) MX[B]
        [8] -1  0       0xffa04800 - 0xffa04bff (0x400) MX[B]
        [9] -1  0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [10] -1 0       0xff800000 - 0xff81ffff (0x20000) MX[B](B)
        [11] -1 0       0xff8fc000 - 0xff8fffff (0x4000) MX[B](B)
        [12] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [13] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [14] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [15] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [17] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [18] -1 0       0x0000dcc0 - 0x0000dcff (0x40) IX[B]
        [19] -1 0       0x0000cc40 - 0x0000cc7f (0x40) IX[B]
        [20] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [21] -1 0       0x0000cc80 - 0x0000cc9f (0x20) IX[B]
        [22] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [23] -1 0       0x0000ff40 - 0x0000ff5f (0x20) IX[B]
        [24] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [25] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [26] -1 0       0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
        [27] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [28] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) R128(0): PCI bus 1 card 0 func 0
(**) R128(0): Depth 24, (--) framebuffer bpp 32
(II) R128(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmap
s)
(==) R128(0): Default visual is TrueColor
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules/libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) R128(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset 
is 0x0000
(==) R128(0): RGB weight 888
(II) R128(0): Using 8 bits per RGB (8 bit DAC)
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules/libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) R128(0): initializing int10
(II) R128(0): Primary V_BIOS segment is: 0xc000
(--) R128(0): Chipset: "ATI Rage 128 Pro ULTRA TF (AGP)" (ChipID = 0
x5446)
(--) R128(0): Linear framebuffer at 0xf8000000
(--) R128(0): MMIO registers at 0xff8fc000
(--) R128(0): BIOS at 0x80000000
(--) R128(0): VideoRAM: 16384 kByte (128-bit SDR SGRAM 1:1)
(**) R128(0): Using external CRT for display
(II) R128(0): Primary Display == Type 3
(WW) R128(0): Can't determine panel dimensions, and none specified.
        Disabling programming of FP registers.
(II) R128(0): PLL parameters: rf=2950 rd=65 min=12500 max=35000; xcl
k=13000
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules/libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules/libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) R128(0): VESA BIOS detected
(II) R128(0): VESA VBE Version 2.0
(II) R128(0): VESA VBE Total Mem: 16384 kB
(II) R128(0): VESA VBE OEM: ATI RAGE128
(II) R128(0): VESA VBE OEM Software Rev: 1.0
(II) R128(0): VESA VBE OEM Vendor: ATI Technologies Inc.
(II) R128(0): VESA VBE OEM Product: R128
(II) R128(0): VESA VBE OEM Product Rev: 01.00
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules/libddc.so
(II) R128(0): VESA VBE DDC supported
(II) R128(0): VESA VBE DDC Level 2
(II) R128(0): VESA VBE DDC transfer in appr. 2 sec.
(II) R128(0): VESA VBE DDC read successfully
(II) R128(0): Manufacturer: DEL  Model: 3015  Serial#: 1095254616
(II) R128(0): Year: 2005  Week: 3
(II) R128(0): EDID Version: 1.3
(II) R128(0): Analog Display Input,  Input Voltage Level: 0.700/0.30
0 V
(II) R128(0): Sync:  Separate  Composite  SyncOnGreen
(II) R128(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27
(II) R128(0): Gamma: 2.20
(II) R128(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Disp
lay
(II) R128(0): Default color space is primary color space
(II) R128(0): First detailed timing is preferred mode
(II) R128(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) R128(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.32
9
(II) R128(0): Supported VESA Video Modes:
(II) R128(0): 720x400@70Hz
(II) R128(0): 640x480@60Hz
(II) R128(0): 640x480@75Hz
(II) R128(0): 800x600@60Hz
(II) R128(0): 800x600@75Hz
(II) R128(0): 1024x768@60Hz
(II) R128(0): 1024x768@75Hz
(II) R128(0): 1280x1024@75Hz
(II) R128(0): Manufacturer's mask: 0
(II) R128(0): Supported Future Video Modes:
(II) R128(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) R128(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) R128(0): Supported additional Video Mode:
(II) R128(0): clock: 108.0 MHz   Image Size:  338 x 270 mm
(II) R128(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_
end 1688 h_border: 0
(II) R128(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanki
ng: 1066 v_border: 0
(II) R128(0): Serial No: H627251KAHBX
(II) R128(0): Monitor name: DELL 1704FPV
(II) R128(0): Ranges: V min: 56  V max: 76 Hz, H min: 30  H max: 81 
kHz, PixClock max 140 MHz
(==) R128(0): Using gamma correction (1.0, 1.0, 1.0)
(==) R128(0): Write-combining range (0xf8000000,0x1000000)
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules/libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.0
(II) R128(0): I2C bus "DDC" initialized.
(II) R128(0): I2C device "DDC:ddc2" registered at address 0xA0.
(II) R128(0): I2C device "DDC:ddc2" removed.
(EE) R128(0): No DFP detected
(II) R128(0): DELL 1704FPV: Using hsync range of 30.00-81.00 kHz
(II) R128(0): DELL 1704FPV: Using vrefresh range of 56.00-76.00 Hz
(II) R128(0): Clock range:  12.50 to 350.00 MHz
(II) R128(0): Not using default mode "640x350" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "320x175" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "640x400" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "320x200" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "720x400" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "360x200" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "640x480" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "320x240" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "800x600" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "400x300" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of ran
ge)
(II) R128(0): Not using default mode "512x384" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "1024x768" (vrefresh out of ran
ge)
(II) R128(0): Not using default mode "512x384" (vrefresh out of rang
e)
(WW) (1280x960,DELL 1704FPV) mode clock 148.5MHz exceeds DDC maximum
 140MHz
(II) R128(0): Not using default mode "1280x960" (hsync out of range)
(II) R128(0): Not using default mode "640x480" (hsync out of range)
(WW) (1280x1024,DELL 1704FPV) mode clock 157.5MHz exceeds DDC maximu
m 140MHz
(II) R128(0): Not using default mode "1280x1024" (hsync out of range
)
(II) R128(0): Not using default mode "640x512" (hsync out of range)
(WW) (1600x1200,DELL 1704FPV) mode clock 162MHz exceeds DDC maximum 
140MHz
(WW) (1600x1200,DELL 1704FPV) mode clock 175.5MHz exceeds DDC maximu
m 140MHz
(WW) (1600x1200,DELL 1704FPV) mode clock 189MHz exceeds DDC maximum 
140MHz
(II) R128(0): Not using default mode "1600x1200" (hsync out of range
)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,DELL 1704FPV) mode clock 202.5MHz exceeds DDC maximu
m 140MHz
(II) R128(0): Not using default mode "1600x1200" (hsync out of range
)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(WW) (1600x1200,DELL 1704FPV) mode clock 229.5MHz exceeds DDC maximu
m 140MHz
(II) R128(0): Not using default mode "1600x1200" (hsync out of range
)
(II) R128(0): Not using default mode "800x600" (hsync out of range)
(WW) (1792x1344,DELL 1704FPV) mode clock 204.8MHz exceeds DDC maximu
m 140MHz
(II) R128(0): Not using default mode "1792x1344" (hsync out of range
)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(WW) (1792x1344,DELL 1704FPV) mode clock 261MHz exceeds DDC maximum 
140MHz
(II) R128(0): Not using default mode "1792x1344" (hsync out of range
)
(II) R128(0): Not using default mode "896x672" (hsync out of range)
(WW) (1856x1392,DELL 1704FPV) mode clock 218.3MHz exceeds DDC maximu
m 140MHz
(II) R128(0): Not using default mode "1856x1392" (hsync out of range
)
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(WW) (1856x1392,DELL 1704FPV) mode clock 288MHz exceeds DDC maximum 
140MHz
(II) R128(0): Not using default mode "1856x1392" (hsync out of range
)
(WW) (928x696,DELL 1704FPV) mode clock 144MHz exceeds DDC maximum 14
0MHz
(II) R128(0): Not using default mode "928x696" (hsync out of range)
(WW) (1920x1440,DELL 1704FPV) mode clock 234MHz exceeds DDC maximum 
140MHz
(II) R128(0): Not using default mode "1920x1440" (hsync out of range
)
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(WW) (1920x1440,DELL 1704FPV) mode clock 297MHz exceeds DDC maximum 
140MHz
(II) R128(0): Not using default mode "1920x1440" (hsync out of range
)
(WW) (960x720,DELL 1704FPV) mode clock 148.5MHz exceeds DDC maximum 
140MHz
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(II) R128(0): Not using default mode "1152x768" (vrefresh out of ran
ge)
(II) R128(0): Not using default mode "576x384" (vrefresh out of rang
e)
(II) R128(0): Not using default mode "1152x864" (vrefresh out of ran
ge)
(II) R128(0): Not using default mode "576x432" (vrefresh out of rang
e)
(WW) (1400x1050,DELL 1704FPV) mode clock 151MHz exceeds DDC maximum 140MHz
(WW) (1400x1050,DELL 1704FPV) mode clock 155.8MHz exceeds DDC maximu
m 140MHz
(WW) (1400x1050,DELL 1704FPV) mode clock 184MHz exceeds DDC maximum 
140MHz
(II) R128(0): Not using default mode "1400x1050" (hsync out of range
)
(II) R128(0): Not using default mode "700x525" (hsync out of range)
(WW) (1680x1050,DELL 1704FPV) mode clock 147.14MHz exceeds DDC maxim
um 140MHz
(WW) (1920x1200,DELL 1704FPV) mode clock 193.16MHz exceeds DDC maxim
um 140MHz
(WW) (1920x1200,DELL 1704FPV) mode clock 230MHz exceeds DDC maximum 
140MHz
(II) R128(0): Not using default mode "1920x1200" (hsync out of range
)
(II) R128(0): Not using default mode "960x600" (hsync out of range)
(WW) (1920x1440,DELL 1704FPV) mode clock 341.35MHz exceeds DDC maxim
um 140MHz
(II) R128(0): Not using default mode "1920x1440" (hsync out of range
)
(WW) (960x720,DELL 1704FPV) mode clock 170.675MHz exceeds DDC maximu
m 140MHz
(II) R128(0): Not using default mode "960x720" (hsync out of range)
(WW) (2048x1536,DELL 1704FPV) mode clock 266.95MHz exceeds DDC maxim
um 140MHz
(II) R128(0): Not using default mode "2048x1536" (hsync out of range
)
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(WW) (2048x1536,DELL 1704FPV) mode clock 340.48MHz exceeds DDC maxim
um 140MHz
(II) R128(0): Not using default mode "2048x1536" (hsync out of range
)

---

### Post by gweber on 2006-11-02
Ongoing Xorg.0.log:

(WW) (1024x768,DELL 1704FPV) mode clock 170.24MHz exceeds DDC maximu
m 140MHz
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "2048x1536" (bad mode clock/int
erlace/doublescan)
(WW) (1024x768,DELL 1704FPV) mode clock 194.02MHz exceeds DDC maximu
m 140MHz
(II) R128(0): Not using default mode "1024x768" (hsync out of range)
(II) R128(0): Not using default mode "1920x1200" (width too large fo
r virtual size)
(II) R128(0): Not using default mode "1600x1200" (width too large fo
r virtual size)
(II) R128(0): Not using default mode "1600x1200" (width too large fo
r virtual size)
(II) R128(0): Not using default mode "1680x1050" (width too large fo
r virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large fo
r virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) R128(0): Not using default mode "1400x1050" (width too large fo
r virtual size)
(II) R128(0): Not using default mode "1440x900" (width too large for
 virtual size)
(--) R128(0): Virtual size is 1280x1024 (pitch 1280)
(**) R128(0): *Default mode "1280x1024": 135.0 MHz, 80.0 kHz, 75.0 H
z
(II) R128(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  102
4 1025 1028 1066 +hsync +vsync
(**) R128(0): *Default mode "1152x864": 108.0 MHz, 67.5 kHz, 75.0 Hz
(II) R128(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 
865 868 900 +hsync +vsync
(**) R128(0): *Default mode "1024x768": 78.8 MHz, 60.1 kHz, 75.1 Hz
(II) R128(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 
769 772 800 +hsync +vsync
(**) R128(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) R128(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 
604 625 +hsync +vsync
(**) R128(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) R128(0): Modeline "640x480"   31.50  640 656 720 840  480 481 4
84 500 -hsync -vsync
(**) R128(0):  Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 H
z
(II) R128(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  102
4 1025 1028 1066 +hsync +vsync
(**) R128(0):  Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x960"  108.00  1280 1376 1488 1800  960 
961 964 1000 +hsync +vsync
(**) R128(0):  Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x800"   83.46  1280 1344 1480 1680  800 
801 804 828
(**) R128(0):  Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(II) R128(0): Modeline "1280x768"   80.14  1280 1344 1480 1680  768 
769 772 795
(**) R128(0):  Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(II) R128(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 
771 777 806 -hsync -vsync
(**) R128(0):  Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(II) R128(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 
771 777 806 -hsync -vsync
(**) R128(0):  Default mode "960x600": 96.6 MHz, 74.5 kHz, 60.0 Hz (
D)
(II) R128(0): Modeline "960x600"   96.58  960 1024 1128 1296  600 60
0 602 621 doublescan
(**) R128(0):  Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(II) R128(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 
628 667 -hsync -vsync
(**) R128(0):  Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(II) R128(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 
643 666 +hsync +vsync
(**) R128(0):  Default mode "8D)
(II) R128(0): Modeline "800x600"   87.75  800 832 928 1080  600 600 
602 625 doublescan +hsync +vsync
(**) R128(0):  Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) R128(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 
605 628 +hsync +vsync
(**) R128(0):  Default mode "800x600": 81.0 MHz, 75.0 kHz, 60.0 Hz (
D)
(II) R128(0): Modeline "800x600"   81.00  800 832 928 1080  600 600 
602 625 doublescan +hsync +vsync
(**) R128(0):  Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(II) R128(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 
603 625 +hsync +vsync
(**) R128(0):  Default mode "840x525": 73.6 MHz, 65.2 kHz, 60.1 Hz (
D)
(II) R128(0): Modeline "840x525"   73.57  840 892 984 1128  525 525 
527 543 doublescan
(**) R128(0):  Default mode "700x525": 77.9 MHz, 81.5 kHz, 74.8 Hz (
D)
(II) R128(0): Modeline "700x525"   77.90  700 732 892 956  525 526 5
32 545 doublescan +hsync +vsync
(**) R128(0):  Default mode "700x525": 75.5 MHz, 77.0 kHz, 70.0 Hz (
D)
(II) R128(0): Modeline "700x525"   75.50  700 732 828 980  525 525 5
27 550 doublescan +hsync +vsync
(**) R128(0):  Default mode "700x525": 61.0 MHz, 64.9 kHz, 60.0 Hz (
D)
(II) R128(0): Modeline "700x525"   61.00  700 744 820 940  525 526 5
32 541 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x512": 67.5 MHz, 80.0 kHz, 75.0 Hz (
D)
(II) R128(0): Modeline "640x512"   67.50  640 648 720 844  512 512 5
14 533 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (
D)
(II) R128(0): Modeline "640x512"   54.00  640 664 720 844  512 512 5
14 533 doublescan +hsync +vsync
(**) R128(0):  Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (
D)
(II) R128(0): Modeline "720x450"   54.42  720 736 940 956  450 459 4
63 473 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) R128(0): Modeline "640x480"   31.50  640 664 704 832  480 489 4
91 520 -hsync -vsync
(**) R128(0):  Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(II) R128(0): Modeline "640x480"   25.20  640 656 752 800  480 490 4
92 525 -hsync -vsync
(**) R128(0):  Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (
D)
(II) R128(0): Modeline "640x480"   54.00  640 688 744 900  480 480 4
82 500 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (00x600": 87.8 MHz, 81.2 kHz, 65.0 Hz (D)
(II) R128(0): Modeline "640x400"   41.73  640 672 740 840  400 400 4
02 414 doublescan
(**) R128(0):  Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (
D)
(II) R128(0): Modeline "576x432"   54.00  576 608 672 800  432 432 4
34 450 doublescan +hsync +vsync
(**) R128(0):  Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (
D)
(II) R128(0): Modeline "640x384"   40.07  640 672 740 840  384 384 3
86 397 doublescan
(**) R128(0):  Default mode "512x384": 39.4 MHz, 60.1 kHz, 75.1 Hz (
D)
(II) R128(0): Modeline "512x384"   39.40  512 520 568 656  384 384 3
86 400 doublescan +hsync +vsync
(**) R128(0):  Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (
D)
(II) R128(0): Modeline "512x384"   37.50  512 524 592 664  384 385 3
88 403 doublescan -hsync -vsync
(**) R128(0):  Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (
D)
(II) R128(0): Modeline "512x384"   32.50  512 524 592 672  384 385 3
88 403 doublescan -hsync -vsync
(**) R128(0):  Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (
D)
(II) R128(0): Modeline "416x312"   28.64  416 432 464 576  312 312 3
14 333 doublescan -hsync -vsync
(**) R128(0):  Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (
D)
(II) R128(0): Modeline "400x300"   24.75  400 408 448 528  300 300 3
02 312 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (
D)
(II) R128(0): Modeline "400x300"   25.00  400 428 488 520  300 318 3
21 333 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (
D)
(II) R128(0): Modeline "400x300"   20.00  400 420 484 528  300 300 3
02 314 doublescan +hsync +vsync
(**) R128(0):  Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (
D)
(II) R128(0): Modeline "400x300"   18.00  400 412 448 512  300 300 3
01 312 doublescan +hsync +vsync
(**) R128(0):  Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (
D)
(II) R128(0): Modeline "320x240"   15.75  320 328 360 420  240 240 2
42 250 doublescan -hsync -vsync
(**) R128(0):  Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (
D)
(II) R128(0): Modeline "320x240"   15.75  320 332 352 416  240 244 2
45 260 doublescan -hsync -vsync
(**) R128(0):  Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) R128(0): Modeline "320x240"   12.60  320 328 376 400  240 245 2
46 262 doublescan -hsync -vsync
(++) R128(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules/libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules/libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.2.0
        ABI class: X.Org Video Driver, version 1.0
(II) Loading sub module "shadowfb"
(II) LoadModule: "shadowfb"
(II) Loading /usr/lib/xorg/modules/libshadowfb.so
(II) Module shadowfb: vendor="X.Org Foundation"
        compiled for 7.1.1, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) R128(0): Page flipping disabled
(!!) R128(0): For information on using the multimedia capabilities
        of this adapter, please see [http://gatos.sf.net](http://gatos.sf.net).
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xff8fc000 - 0xff8fffff (0x4000) MS[B]
        [1] 0   0       0xf8000000 - 0xfbffffff (0x4000000) MS[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(
B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xff6ff000 - 0xff6fffff (0x1000) MX[B]
        [7] -1  0       0xffa04000 - 0xffa040ff (0x100) MX[B]
        [8] -1  0       0xffa04400 - 0xffa045ff (0x200) MX[B]
        [9] -1  0       0x60000000 - 0x600003ff (0x400) MX[B]
        [10] -1 0       0xffa04800 - 0xffa04bff (0x400) MX[B]
        [11] -1 0       0xf0000000 - 0xefffffff (0x0) MX[B]O
        [12] -1 0       0xff800000 - 0xff81ffff (0x20000) MX[B](B)
        [13] -1 0       0xff8fc000 - 0xff8fffff (0x4000) MX[B](B)
        [14] -1 0       0xf8000000 - 0xfbffffff (0x4000000) MX[B](B)
        [15] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
        [16] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
        [17] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
        [18] 0  0       0x0000ec00 - 0x0000ecff (0x100) IS[B]
        [19] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [20] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [21] -1 0       0x0000dcc0 - 0x0000dcff (0x40) IX[B]
        [22] -1 0       0x0000cc40 - 0x0000cc7f (0x40) IX[B]
        [23] -1 0       0x0000c800 - 0x0000c8ff (0x100) IX[B]
        [24] -1 0       0x0000cc80 - 0x0000cc9f (0x20) IX[B]
        [25] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [26] -1 0       0x0000ff40 - 0x0000ff5f (0x20) IX[B]
        [27] -1 0       0x0000ff60 - 0x0000ff7f (0x20) IX[B]
        [28] -1 0       0x0000ff80 - 0x0000ff9f (0x20) IX[B]
        [29] -1 0       0x0000ec00 - 0x0000ecff (0x100) IX[B](B)
        [30] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [31] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(==) R128(0): Write-combining range (0xf8000000,0x1000000)
(II) R128(0): Memory manager initialized to (0,0) (1280,3276)
(II) R128(0): Reserved area from (0,1024) to (1280,1026)
(II) R128(0): Largest offscreen area available: 1280 x 2250
(II) R128(0): Using XFree86 Acceleration Architecture (XAA)
        Screen to screen bit blits
        Solid filled rectangles
        8x8 mono pattern filled rectangles
        Indirect CPU to Screen color expansion
        Solid Lines
        Dashed Lines
        Scanline Image Writes
        Offscreen Pixmaps
        Setting up tile and stipple cache:
                32 128x128 slots
                14 256x256 slots
                5 512x512 slots
(II) R128(0): Acceleration enabled
(==) R128(0): Backing store disabled
(==) R128(0): Silken mouse enabled
(II) R128(0): Using hardware cursor (scanline 4104)
(II) R128(0): Largest offscreen area available: 1280 x 2248
(**) Option "dpms"
(**) R128(0): DPMS enabled
(WW) R128(0): Direct rendering disabled
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eras
er)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Curs
or)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Styl
us)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: 
MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: 
KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc104)+us+level3(ralt_swi
tch)" };
    xkb_geometry             { include "pc(pc104)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing
 from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing 
from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing
 from list!

---

### Post by skunkydog on 2006-11-02
I had a similar problem.  I didn't try startx as root.  Instead I reinstalled x-windows-system core.  I can't remember if I removed it and reinstalled, but the **apt-get install x-windows-system-core** seemed to hang.  I finally just left it running over night, and it was done in the morning.

good luck

---

### Post by viper on 2006-11-02
[http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)
Check this thread out might help point you in the right direction.

---

### Post by clever forum name on 2006-11-05
I have a system with the same ATI card (RV370 5B62 [Radeon X600 (PCIE)]). Dapper was working fine thanks to good (& simple) tips on this forum:
[http://ubuntuforums.org/showthread.php?t=221320&page=3](http://ubuntuforums.org/showthread.php?t=221320&page=3)
(See the entry by ubuntu_demon).

I decided yesterday to update to Edgy. The results were ok, but not good in the xserver depot. I spent some time getting back on the horse, here's what I have learned:

The 3D performance was not as good as 6.06 so I thought I would try to fix it by uninstalling some of the sw and reinstalling. This part is not so important other than I broke the xserver installation and had to find my way back. 
The system indicated that the installation of Xserver was incomplete and my attempts to reconfigure the xserver failed due to similar errors that are not well understood by me.

I used
	$ sudo apt-get --reinstall install xserver-xorg
to get off the ground. This allowed me to reconfigure the xserver as the installation is now repaired. 
	
	$ sudo dpkg-reconfigure xserver-xorg
In my case I used all of the default settings and rebooted. This got the Xserver working and I was able to access the Gnome DT environment. 

The xserver was running, but in a generic mode (MESA). I verified that the installations of the restricted access modules and fglrx were in place. 
$sudo apt-get install linux-restricted-modules-$(uname -r)
$sudo apt-get install xorg-driver-fglrx
Both report that the modules are already installed and up to date. These both need to be here for the ATI card to function.

Moving to configuration I ran:
$sudo dpkg-reconfigure xserver-xorg
$sudo aticonfig --initial
$sudo aticonfig --overlay-type=Xv

The last step is to augment xorg.conf with the following:
Section "Extensions"
        Option "Composite" "0"
EndSection

Without this augmentation the xserver will always go with the MESA solution. If you have done everything except the last edit and your output of  
	$ fglrxinfo
reflects MESA instead of ATI, then you are close. 

Here's the bummer part. With Dapper (6.06) The performance increase after getting all this dialed in was incredible. In the edgy case (6.10) I see only about a 2x performance increase. The handy method to compare is the
	$ glxgears -printfps
I saw about 150fps with the MESA config and now I see about 250fps with the ATI sw modules in place and configured as I had them in Dapper. In my Dapper setup I was getting about 3200fps, nearly a factor of 13x more frames per second.

Now I am looking for some help to get back to 3200fps.
-CFN

P.S. I now found all this in the Ubuntu documentation. 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a)

---

### Post by gweber on 2006-11-09
> **viper said:**
> [http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177)
Check this thread out might help point you in the right direction.

Hi,

thanks. Actually I already re-installed edgy (which took me 45min instead of fiddling around with the x-server). But I had a look at your link and afair I tried everything mentioned on the page...

Anyway - thanks a lot.

Cheers,

    Gernot

---

