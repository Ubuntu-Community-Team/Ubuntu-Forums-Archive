---
title: "GUI crashing after Upgrade 18.04"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by m_ghv_geo on 2018-05-16
I can't actually tell you what is wrong because I do not know.
I just upgraded my UX32VD-DH71 to 18.04 from 17.10.
Before the Upgrade I did apt-get update, apt-get upgrade, apt-get dist-upgrade and apt-get autoremove 

Upgrade was successful. However after restarting I am unable to use it.

This is the video that shows what is going on
[https://youtu.be/16AakFjjMjk](https://youtu.be/16AakFjjMjk)

I switched to different tty using [CTRL]+[ALT]+[F2] 
Screen was flickering back to previous writings.  However I managed to run apt-get update and apt-get upgrade successfully, but nothing was upgraded.

While i'll be waiting for your response I will try to install ssh server on it.

---

### Post by m_ghv_geo on 2018-05-16
Finally it stopped flickering to text.
[IMG]https://photos.app.goo.gl/WbSNGi4Lh3Ww25U96[/IMG]
[picture1]("https://photos.app.goo.gl/WbSNGi4Lh3Ww25U96")
[picture2 ]("https://photos.app.goo.gl/C2Axxcke8tSqgYwD3")
I installed SSH server run startx
It gave me this log
```
miky@ux32vd:~/.local/share/xorg$ cat Xorg.0.log[/COLOR][  3377.892] 
X.Org X Server 1.19.6
Release Date: 2017-12-20
[  3377.893] X Protocol Version 11, Revision 0
[  3377.893] Build Operating System: Linux 4.4.0-119-generic x86_64 Ubuntu
[  3377.893] Current Operating System: Linux ux32vd 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64
[  3377.893] Kernel command line: BOOT_IMAGE=/vmlinuz-4.15.0-20-generic root=UUID=e8aa7ef4-1185-46e7-995b-7c74bd669d10 ro quiet splash vt.handoff=1
[  3377.894] Build Date: 13 April 2018  08:07:36PM
[  3377.895] xorg-server 2:1.19.6-1ubuntu4 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[  3377.895] Current version of pixman: 0.34.0
[  3377.896]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[  3377.896] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  3377.899] (==) Log file: "/home/miky/.local/share/xorg/Xorg.0.log", Time: Wed May 16 14:55:37 2018
[  3377.899] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[  3377.900] (==) No Layout section.  Using the first Screen section.
[  3377.900] (==) No screen section available. Using defaults.
[  3377.900] (**) |-->Screen "Default Screen Section" (0)
[  3377.900] (**) |   |-->Monitor "<default monitor>"
[  3377.900] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[  3377.900] (==) Automatically adding devices
[  3377.900] (==) Automatically enabling devices
[  3377.900] (==) Automatically adding GPU devices
[  3377.900] (==) Automatically binding GPU devices
[  3377.900] (==) Max clients allowed: 256, resource mask: 0x1fffff
[  3377.900] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[  3377.900]    Entry deleted from font path.
[  3377.900] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[  3377.900]    Entry deleted from font path.
[  3377.900] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[  3377.900]    Entry deleted from font path.
[  3377.900] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[  3377.900]    Entry deleted from font path.
[  3377.900] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[  3377.900]    Entry deleted from font path.
[  3377.900] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[  3377.900] (==) ModulePath set to "/usr/lib/xorg/modules"
[  3377.900] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[  3377.900] (II) Loader magic: 0x55b0d6f12020
[  3377.900] (II) Module ABI versions:
[  3377.900]    X.Org ANSI C Emulation: 0.4
[  3377.900]    X.Org Video Driver: 23.0
[  3377.900]    X.Org XInput driver : 24.1
[  3377.900]    X.Org Server Extension : 10.0
[  3377.901] (++) using VT number 3

[  3377.905] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_3510
[  3377.906] (II) xfree86: Adding drm device (/dev/dri/card0)
[  3377.907] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 11 paused 0
[  3377.909] (--) PCI:*(0:0:2:0) 8086:0166:1043:1507 rev 9, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64, BIOS @ 0x????????/131072
[  3377.909] (--) PCI: (0:1:0:0) 10de:1140:1043:1507 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[  3377.909] (II) LoadModule: "glx"
[  3377.909] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[  3377.922] (II) Module glx: vendor="X.Org Foundation"
[  3377.922]    compiled for 1.19.6, module version = 1.0.0
[  3377.922]    ABI class: X.Org Server Extension, version 10.0
[  3377.922] (==) Matched modesetting as autoconfigured driver 0
[  3377.922] (==) Matched fbdev as autoconfigured driver 1
[  3377.922] (==) Matched vesa as autoconfigured driver 2
[  3377.922] (==) Assigned the driver to the xf86ConfigLayout
[  3377.922] (II) LoadModule: "modesetting"
[  3377.922] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[  3377.923] (II) Module modesetting: vendor="X.Org Foundation"
[  3377.923]    compiled for 1.19.6, module version = 1.19.6
[  3377.923]    Module class: X.Org Video Driver
[  3377.923]    ABI class: X.Org Video Driver, version 23.0
[  3377.923] (II) LoadModule: "fbdev"
[  3377.923] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[  3377.923] (II) Module fbdev: vendor="X.Org Foundation"
[  3377.923]    compiled for 1.19.3, module version = 0.4.4
[  3377.923]    Module class: X.Org Video Driver
[  3377.923]    ABI class: X.Org Video Driver, version 23.0
[  3377.923] (II) LoadModule: "vesa"
[  3377.923] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[  3377.924] (II) Module vesa: vendor="X.Org Foundation"
[  3377.924]    compiled for 1.19.3, module version = 2.3.4
[  3377.924]    Module class: X.Org Video Driver
[  3377.924]    ABI class: X.Org Video Driver, version 23.0
[  3377.924] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[  3377.924] (II) FBDEV: driver for framebuffer: fbdev
[  3377.924] (II) VESA: driver for VESA chipsets: vesa
[  3377.924] xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
[  3377.924] (II) modeset(0): using drv /dev/dri/card0
[  3377.924] (WW) Falling back to old probe method for fbdev
[  3377.924] (II) Loading sub module "fbdevhw"
[  3377.924] (II) LoadModule: "fbdevhw"
[  3377.924] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[  3377.925] (II) Module fbdevhw: vendor="X.Org Foundation"
[  3377.925]    compiled for 1.19.6, module version = 0.0.2
[  3377.925]    ABI class: X.Org Video Driver, version 23.0
[  3377.925] (EE) open /dev/fb0: Permission denied
[  3377.925] (WW) Falling back to old probe method for vesa
[  3377.925] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[  3377.925] (II) modeset(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[  3377.925] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[  3377.925] (==) modeset(0): RGB weight 888
[  3377.925] (==) modeset(0): Default visual is TrueColor
[  3377.925] (II) Loading sub module "glamoregl"
[  3377.925] (II) LoadModule: "glamoregl"
[  3377.925] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[  3377.930] (II) Module glamoregl: vendor="X.Org Foundation"
[  3377.930]    compiled for 1.19.6, module version = 1.0.0
[  3377.930]    ABI class: X.Org ANSI C Emulation, version 0.4
[  3377.930] (II) glamor: OpenGL accelerated X.org driver based.
[  3377.945] (EE) modeset(0): eglGetDisplay() failed
[  3377.946] (EE) modeset(0): glamor initialization failed
[  3377.946] (II) modeset(0): ShadowFB: preferred YES, enabled YES
[  3377.946] (II) modeset(0): Double-buffered shadow updates: off
[  3377.947] (II) modeset(0): Output eDP-1 has no monitor section
[  3377.952] (II) modeset(0): Output VGA-1 has no monitor section
[  3377.960] (II) modeset(0): Output HDMI-1 has no monitor section
[  3377.960] (II) modeset(0): Output DP-1 has no monitor section
[  3377.961] (II) modeset(0): EDID for output eDP-1
[  3377.961] (II) modeset(0): Manufacturer: CMN  Model: 1343  Serial#: 0
[  3377.961] (II) modeset(0): Year: 2011  Week: 52
[  3377.961] (II) modeset(0): EDID Version: 1.4
[  3377.961] (II) modeset(0): Digital Display Input
[  3377.961] (II) modeset(0): 8 bits per channel
[  3377.961] (II) modeset(0): Digital interface is DisplayPort
[  3377.961] (II) modeset(0): Max Image Size [cm]: horiz.: 28  vert.: 16
[  3377.961] (II) modeset(0): Gamma: 2.20
[  3377.961] (II) modeset(0): No DPMS capabilities specified
[  3377.961] (II) modeset(0): Supported color encodings: RGB 4:4:4 
[  3377.961] (II) modeset(0): First detailed timing is preferred mode
[  3377.961] (II) modeset(0): Preferred mode is native pixel format and refresh rate
[  3377.961] (II) modeset(0): redX: 0.662 redY: 0.325   greenX: 0.297 greenY: 0.589
[  3377.961] (II) modeset(0): blueX: 0.146 blueY: 0.068   whiteX: 0.312 whiteY: 0.325
[  3377.961] (II) modeset(0): Manufacturer's mask: 0
[  3377.961] (II) modeset(0): Supported detailed timing:
[  3377.961] (II) modeset(0): clock: 138.8 MHz   Image Size:  282 x 165 mm
[  3377.961] (II) modeset(0): h_active: 1920  h_sync: 1966  h_sync_end 1996 h_blank_end 2080 h_border: 0
[  3377.961] (II) modeset(0): v_active: 1080  v_sync: 1082  v_sync_end 1086 v_blanking: 1112 v_border: 0
[  3377.961] (II) modeset(0): Supported detailed timing:
[  3377.961] (II) modeset(0): clock: 92.5 MHz   Image Size:  282 x 165 mm
[  3377.961] (II) modeset(0): h_active: 1920  h_sync: 1966  h_sync_end 1996 h_blank_end 2080 h_border: 0
[  3377.961] (II) modeset(0): v_active: 1080  v_sync: 1082  v_sync_end 1086 v_blanking: 1112 v_border: 0
[  3377.961] (II) modeset(0):  CMN
[  3377.961] (II) modeset(0):  N133HSE-EA1
[  3377.961] (II) modeset(0): EDID (in hex):
[  3377.961] (II) modeset(0):   00ffffffffffff000dae431300000000
[  3377.961] (II) modeset(0):   34150104a51c10780293ada9534c9625
[  3377.961] (II) modeset(0):   114f5300000001010101010101010101
[  3377.961] (II) modeset(0):   010101010101363680a0703820402e1e
[  3377.961] (II) modeset(0):   24001aa510000018242480a070382040
[  3377.961] (II) modeset(0):   2e1e24001aa510000018000000fe0043
[  3377.961] (II) modeset(0):   4d4e0a202020202020202020000000fe
[  3377.961] (II) modeset(0):   004e3133334853452d4541310a2000cd
[  3377.961] (II) modeset(0): Printing probed modes for output eDP-1
[  3377.961] (II) modeset(0): Modeline "1920x1080"x60.0  138.78  1920 1966 1996 2080  1080 1082 1086 1112 -hsync -vsync (66.7 kHz eP)
[  3377.961] (II) modeset(0): Modeline "1920x1080"x119.9  266.50  1920 1944 1960 2000  1080 1081 1084 1111 doublescan +hsync -vsync (133.2 kHz d)
[  3377.961] (II) modeset(0): Modeline "1920x1080"x60.0  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync (67.2 kHz d)
[  3377.961] (II) modeset(0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[  3377.961] (II) modeset(0): Modeline "1920x1080"x40.0   92.52  1920 1966 1996 2080  1080 1082 1086 1112 -hsync -vsync (44.5 kHz e)
[  3377.961] (II) modeset(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[  3377.962] (II) modeset(0): Modeline "1600x900"x120.0  246.00  1600 1728 1900 2200  900 901 904 932 doublescan -hsync +vsync (111.8 kHz d)
[  3377.962] (II) modeset(0): Modeline "1600x900"x119.9  186.50  1600 1624 1640 1680  900 901 904 926 doublescan +hsync -vsync (111.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "1600x900"x59.9  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync (56.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "1600x900"x59.8   97.50  1600 1648 1680 1760  900 903 908 926 +hsync -vsync (55.4 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[  3377.962] (II) modeset(0): Modeline "1400x900"x60.0  103.50  1400 1480 1624 1848  900 903 913 934 -hsync +vsync (56.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "1400x900"x59.9   86.50  1400 1448 1480 1560  900 903 913 926 +hsync -vsync (55.4 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "1440x810"x120.0  198.12  1440 1548 1704 1968  810 811 814 839 doublescan -hsync +vsync (100.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "1440x810"x119.9  151.88  1440 1464 1480 1520  810 811 814 833 doublescan +hsync -vsync (99.9 kHz d)
[  3377.962] (II) modeset(0): Modeline "1368x768"x59.9   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsync (47.8 kHz d)
[  3377.962] (II) modeset(0): Modeline "1368x768"x59.9   72.25  1368 1416 1448 1528  768 771 781 790 +hsync -vsync (47.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x800"x120.0  174.25  1280 1380 1516 1752  800 801 804 829 doublescan -hsync +vsync (99.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x800"x119.9  134.25  1280 1304 1320 1360  800 801 804 823 doublescan +hsync -vsync (98.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x800"x59.8   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x800"x59.9   71.00  1280 1328 1360 1440  800 803 809 823 +hsync -vsync (49.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x720"x120.0  156.12  1280 1376 1512 1744  720 721 724 746 doublescan -hsync +vsync (89.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x720"x120.0  120.75  1280 1304 1320 1360  720 721 724 740 doublescan +hsync -vsync (88.8 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz d)
[  3377.962] (II) modeset(0): Modeline "1280x720"x59.7   63.75  1280 1328 1360 1440  720 723 728 741 +hsync -vsync (44.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[  3377.962] (II) modeset(0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[  3377.962] (II) modeset(0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "1024x576"x119.9   98.50  1024 1092 1200 1376  576 577 580 597 doublescan -hsync +vsync (71.6 kHz d)
[  3377.962] (II) modeset(0): Modeline "1024x576"x119.9   78.38  1024 1048 1064 1104  576 577 580 592 doublescan +hsync -vsync (71.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "1024x576"x59.9   46.50  1024 1064 1160 1296  576 579 584 599 -hsync +vsync (35.9 kHz d)
[  3377.962] (II) modeset(0): Modeline "1024x576"x59.8   42.00  1024 1072 1104 1184  576 579 584 593 +hsync -vsync (35.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "960x600"x119.9   96.62  960 1028 1128 1296  600 601 604 622 doublescan -hsync +vsync (74.6 kHz d)
[  3377.962] (II) modeset(0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "960x540"x119.9   86.50  960 1024 1124 1288  540 541 544 560 doublescan -hsync +vsync (67.2 kHz d)
[  3377.962] (II) modeset(0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[  3377.962] (II) modeset(0): Modeline "960x540"x59.6   40.75  960 992 1088 1216  540 543 548 562 -hsync +vsync (33.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "960x540"x59.8   37.25  960 1008 1040 1120  540 543 548 556 +hsync -vsync (33.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[  3377.962] (II) modeset(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[  3377.962] (II) modeset(0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "864x486"x59.9   32.50  864 888 968 1072  486 489 494 506 -hsync +vsync (30.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "864x486"x59.6   30.50  864 912 944 1024  486 489 494 500 +hsync -vsync (29.8 kHz d)
[  3377.962] (II) modeset(0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[  3377.962] (II) modeset(0): Modeline "800x450"x119.9   59.12  800 848 928 1056  450 451 454 467 doublescan -hsync +vsync (56.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "800x450"x119.6   48.75  800 824 840 880  450 451 454 463 doublescan +hsync -vsync (55.4 kHz d)
[  3377.962] (II) modeset(0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[  3377.962] (II) modeset(0): Modeline "700x450"x119.9   51.75  700 740 812 924  450 451 456 467 doublescan -hsync +vsync (56.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "700x450"x119.8   43.25  700 724 740 780  450 451 456 463 doublescan +hsync -vsync (55.4 kHz d)
[  3377.962] (II) modeset(0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[  3377.962] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "720x405"x59.5   22.50  720 744 808 896  405 408 413 422 -hsync +vsync (25.1 kHz d)
[  3377.962] (II) modeset(0): Modeline "720x405"x59.0   21.75  720 768 800 880  405 408 413 419 +hsync -vsync (24.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "684x384"x119.8   42.62  684 720 788 892  384 385 390 399 doublescan -hsync +vsync (47.8 kHz d)
[  3377.962] (II) modeset(0): Modeline "684x384"x119.7   36.12  684 708 724 764  384 385 390 395 doublescan +hsync -vsync (47.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[  3377.962] (II) modeset(0): Modeline "640x400"x119.8   41.75  640 676 740 840  400 401 404 415 doublescan -hsync +vsync (49.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "640x400"x120.0   35.50  640 664 680 720  400 401 404 411 doublescan +hsync -vsync (49.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "640x360"x119.7   37.25  640 672 736 832  360 361 364 374 doublescan -hsync +vsync (44.8 kHz d)
[  3377.962] (II) modeset(0): Modeline "640x360"x119.7   31.88  640 664 680 720  360 361 364 370 doublescan +hsync -vsync (44.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "640x360"x59.8   18.00  640 664 720 800  360 363 368 376 -hsync +vsync (22.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "640x360"x59.3   17.75  640 688 720 800  360 363 368 374 +hsync -vsync (22.2 kHz d)
[  3377.962] (II) modeset(0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[  3377.962] (II) modeset(0): Modeline "512x288"x120.0   23.25  512 532 580 648  288 289 292 299 doublescan -hsync +vsync (35.9 kHz d)
[  3377.962] (II) modeset(0): Modeline "512x288"x119.8   21.00  512 536 552 592  288 289 292 296 doublescan +hsync -vsync (35.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "480x270"x119.3   20.38  480 496 544 608  270 271 274 281 doublescan -hsync +vsync (33.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "480x270"x119.6   18.62  480 504 520 560  270 271 274 278 doublescan +hsync -vsync (33.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[  3377.962] (II) modeset(0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[  3377.962] (II) modeset(0): Modeline "432x243"x119.8   16.25  432 444 484 536  243 244 247 253 doublescan -hsync +vsync (30.3 kHz d)
[  3377.962] (II) modeset(0): Modeline "432x243"x119.1   15.25  432 456 472 512  243 244 247 250 doublescan +hsync -vsync (29.8 kHz d)
[  3377.962] (II) modeset(0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "360x202"x119.0   11.25  360 372 404 448  202 204 206 211 doublescan -hsync +vsync (25.1 kHz d)
[  3377.962] (II) modeset(0): Modeline "360x202"x118.3   10.88  360 384 400 440  202 204 206 209 doublescan +hsync -vsync (24.7 kHz d)
[  3377.962] (II) modeset(0): Modeline "320x180"x119.7    9.00  320 332 360 400  180 181 184 188 doublescan -hsync +vsync (22.5 kHz d)
[  3377.962] (II) modeset(0): Modeline "320x180"x118.6    8.88  320 344 360 400  180 181 184 187 doublescan +hsync -vsync (22.2 kHz d)
[  3377.966] (II) modeset(0): EDID for output VGA-1
[  3377.974] (II) modeset(0): EDID for output HDMI-1
[  3377.974] (II) modeset(0): EDID for output DP-1
[  3377.974] (II) modeset(0): Output eDP-1 connected
[  3377.974] (II) modeset(0): Output VGA-1 disconnected
[  3377.974] (II) modeset(0): Output HDMI-1 disconnected
[  3377.974] (II) modeset(0): Output DP-1 disconnected
[  3377.974] (II) modeset(0): Using exact sizes for initial modes
[  3377.974] (II) modeset(0): Output eDP-1 using initial mode 1920x1080 +0+0
[  3377.974] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[  3377.974] (==) modeset(0): DPI set to (96, 96)
[  3377.974] (II) Loading sub module "fb"
[  3377.974] (II) LoadModule: "fb"
[  3377.974] (II) Loading /usr/lib/xorg/modules/libfb.so
[  3377.976] (II) Module fb: vendor="X.Org Foundation"
[  3377.976]    compiled for 1.19.6, module version = 1.0.0
[  3377.976]    ABI class: X.Org ANSI C Emulation, version 0.4
[  3377.976] (II) Loading sub module "shadow"
[  3377.976] (II) LoadModule: "shadow"
[  3377.976] (II) Loading /usr/lib/xorg/modules/libshadow.so
[  3377.978] (II) Module shadow: vendor="X.Org Foundation"
[  3377.978]    compiled for 1.19.6, module version = 1.1.0
[  3377.978]    ABI class: X.Org ANSI C Emulation, version 0.4
[  3377.978] (II) UnloadModule: "fbdev"
[  3377.978] (II) Unloading fbdev
[  3377.978] (II) UnloadSubModule: "fbdevhw"
[  3377.978] (II) Unloading fbdevhw
[  3377.979] (II) UnloadModule: "vesa"
[  3377.979] (II) Unloading vesa
[  3377.980] (==) Depth 24 pixmap format is 32 bpp
[  3377.980] (==) modeset(0): Backing store enabled
[  3377.980] (==) modeset(0): Silken mouse enabled
[  3377.980] (II) modeset(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[  3378.069] (==) modeset(0): DPMS enabled
[  3378.069] (--) RandR disabled
[  3378.072] (II) SELinux: Disabled on system
[  3378.072] (II) AIGLX: Screen 0 is not DRI2 capable
[  3378.072] (EE) AIGLX: reverting to software rendering
[  3378.146] (II) IGLX: enabled GLX_MESA_copy_sub_buffer
[  3378.147] (II) IGLX: Loaded and initialized swrast
[  3378.147] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[  3378.148] (II) modeset(0): Damage tracking initialized
[  3378.148] (II) modeset(0): Setting screen physical size to 508 x 285
[  3378.190] (II) config/udev: Adding input device Asus Wireless Radio Control (/dev/input/event7)
[  3378.190] (**) Asus Wireless Radio Control: Applying InputClass "libinput keyboard catchall"
[  3378.190] (II) LoadModule: "libinput"
[  3378.190] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[  3378.192] (II) Module libinput: vendor="X.Org Foundation"
[  3378.192]    compiled for 1.19.6, module version = 0.27.1
[  3378.192]    Module class: X.Org XInput Driver
[  3378.192]    ABI class: X.Org XInput driver, version 24.1
[  3378.192] (II) Using input driver 'libinput' for 'Asus Wireless Radio Control'
[  3378.192] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 19 paused 0
[  3378.192] (**) Asus Wireless Radio Control: always reports core events
[  3378.192] (**) Option "Device" "/dev/input/event7"
[  3378.192] (**) Option "_source" "server/udev"
[  3378.193] (II) event7  - Asus Wireless Radio Control: is tagged by udev as: Keyboard
[  3378.193] (II) event7  - Asus Wireless Radio Control: device is a keyboard
[  3378.193] (II) event7  - Asus Wireless Radio Control: device removed
[  3378.193] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/ATK4001:00/input/input14/event7"
[  3378.193] (II) XINPUT: Adding extended input device "Asus Wireless Radio Control" (type: KEYBOARD, id 6)
[  3378.193] (**) Option "xkb_model" "pc105"
[  3378.193] (**) Option "xkb_layout" "us,ge"
[  3378.193] (**) Option "xkb_variant" ","
[  3378.193] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  3378.214] (II) event7  - Asus Wireless Radio Control: is tagged by udev as: Keyboard
[  3378.214] (II) event7  - Asus Wireless Radio Control: device is a keyboard
[  3378.214] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[  3378.214] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[  3378.214] (II) Using input driver 'libinput' for 'Video Bus'
[  3378.215] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 22 paused 0
[  3378.215] (**) Video Bus: always reports core events
[  3378.215] (**) Option "Device" "/dev/input/event5"
[  3378.215] (**) Option "_source" "server/udev"
[  3378.216] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[  3378.216] (II) event5  - Video Bus: device is a keyboard
[  3378.216] (II) event5  - Video Bus: device removed
[  3378.216] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input13/event5"
[  3378.216] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[  3378.216] (**) Option "xkb_model" "pc105"
[  3378.216] (**) Option "xkb_layout" "us,ge"
[  3378.216] (**) Option "xkb_variant" ","
[  3378.216] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  3378.216] (II) event5  - Video Bus: is tagged by udev as: Keyboard
[  3378.216] (II) event5  - Video Bus: device is a keyboard
[  3378.217] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[  3378.217] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[  3378.217] (II) Using input driver 'libinput' for 'Video Bus'
[  3378.218] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 23 paused 0
[  3378.218] (**) Video Bus: always reports core events
[  3378.218] (**) Option "Device" "/dev/input/event4"
[  3378.218] (**) Option "_source" "server/udev"
[  3378.218] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[  3378.218] (II) event4  - Video Bus: device is a keyboard
[  3378.218] (II) event4  - Video Bus: device removed
[  3378.219] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input12/event4"
[  3378.219] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[  3378.219] (**) Option "xkb_model" "pc105"
[  3378.219] (**) Option "xkb_layout" "us,ge"
[  3378.219] (**) Option "xkb_variant" ","
[  3378.219] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  3378.219] (II) event4  - Video Bus: is tagged by udev as: Keyboard
[  3378.219] (II) event4  - Video Bus: device is a keyboard
[  3378.220] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[  3378.220] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[  3378.220] (II) Using input driver 'libinput' for 'Power Button'
[  3378.220] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 24 paused 0
[  3378.220] (**) Power Button: always reports core events
[  3378.220] (**) Option "Device" "/dev/input/event1"
[  3378.220] (**) Option "_source" "server/udev"
[  3378.221] (II) event1  - Power Button: is tagged by udev as: Keyboard
[  3378.221] (II) event1  - Power Button: device is a keyboard
[  3378.221] (II) event1  - Power Button: device removed
[  3378.221] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[  3378.221] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[  3378.221] (**) Option "xkb_model" "pc105"
[  3378.221] (**) Option "xkb_layout" "us,ge"
[  3378.221] (**) Option "xkb_variant" ","
[  3378.221] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  3378.222] (II) event1  - Power Button: is tagged by udev as: Keyboard
[  3378.222] (II) event1  - Power Button: device is a keyboard
[  3378.222] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[  3378.222] (II) No input driver specified, ignoring this device.
[  3378.222] (II) This device may have been added with another device file.
[  3378.222] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)
[  3378.222] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[  3378.222] (II) Using input driver 'libinput' for 'Sleep Button'
[  3378.223] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 25 paused 0
[  3378.223] (**) Sleep Button: always reports core events
[  3378.223] (**) Option "Device" "/dev/input/event2"
[  3378.223] (**) Option "_source" "server/udev"
[  3378.223] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[  3378.223] (II) event2  - Sleep Button: device is a keyboard
[  3378.223] (II) event2  - Sleep Button: device removed
[  3378.223] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"
[  3378.223] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[  3378.223] (**) Option "xkb_model" "pc105"
[  3378.224] (**) Option "xkb_layout" "us,ge"
[  3378.224] (**) Option "xkb_variant" ","
[  3378.224] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  3378.224] (II) event2  - Sleep Button: is tagged by udev as: Keyboard
[  3378.224] (II) event2  - Sleep Button: device is a keyboard
[  3378.225] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event10)
[  3378.225] (II) No input driver specified, ignoring this device.
[  3378.225] (II) This device may have been added with another device file.
[  3378.225] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event11)
[  3378.225] (II) No input driver specified, ignoring this device.
[  3378.225] (II) This device may have been added with another device file.
[  3378.226] (II) config/udev: Adding input device USB2.0 HD UVC WebCam: USB2.0 HD (/dev/input/event9)
[  3378.226] (**) USB2.0 HD UVC WebCam: USB2.0 HD: Applying InputClass "libinput keyboard catchall"
[  3378.226] (II) Using input driver 'libinput' for 'USB2.0 HD UVC WebCam: USB2.0 HD'
[  3378.226] (II) systemd-logind: got fd for /dev/input/event9 13:73 fd 26 paused 0
[  3378.226] (**) USB2.0 HD UVC WebCam: USB2.0 HD: always reports core events
[  3378.226] (**) Option "Device" "/dev/input/event9"
[  3378.226] (**) Option "_source" "server/udev"
[  3378.227] (II) event9  - USB2.0 HD UVC WebCam: USB2.0 HD: is tagged by udev as: Keyboard
[  3378.227] (II) event9  - USB2.0 HD UVC WebCam: USB2.0 HD: device is a keyboard
[  3378.227] (II) event9  - USB2.0 HD UVC WebCam: USB2.0 HD: device removed
[  3378.227] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input16/event9"
[  3378.227] (II) XINPUT: Adding extended input device "USB2.0 HD UVC WebCam: USB2.0 HD" (type: KEYBOARD, id 11)
[  3378.227] (**) Option "xkb_model" "pc105"
[  3378.227] (**) Option "xkb_layout" "us,ge"
[  3378.227] (**) Option "xkb_variant" ","
[  3378.227] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  3378.228] (II) event9  - USB2.0 HD UVC WebCam: USB2.0 HD: is tagged by udev as: Keyboard
[  3378.228] (II) event9  - USB2.0 HD UVC WebCam: USB2.0 HD: device is a keyboard
[  3378.228] (II) config/udev: Adding input device Asus WMI hotkeys (/dev/input/event8)
[  3378.228] (**) Asus WMI hotkeys: Applying InputClass "libinput keyboard catchall"
[  3378.228] (II) Using input driver 'libinput' for 'Asus WMI hotkeys'
[  3378.229] (II) systemd-logind: got fd for /dev/input/event8 13:72 fd 27 paused 0
[  3378.229] (**) Asus WMI hotkeys: always reports core events
[  3378.229] (**) Option "Device" "/dev/input/event8"
[  3378.229] (**) Option "_source" "server/udev"
[  3378.229] (II) event8  - Asus WMI hotkeys: is tagged by udev as: Keyboard
[  3378.229] (II) event8  - Asus WMI hotkeys: device is a keyboard
[  3378.229] (II) event8  - Asus WMI hotkeys: device removed
[  3378.229] (**) Option "config_info" "udev:/sys/devices/platform/asus-nb-wmi/input/input15/event8"
[  3378.229] (II) XINPUT: Adding extended input device "Asus WMI hotkeys" (type: KEYBOARD, id 12)
[  3378.229] (**) Option "xkb_model" "pc105"
[  3378.229] (**) Option "xkb_layout" "us,ge"
[  3378.229] (**) Option "xkb_variant" ","
[  3378.229] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  3378.230] (II) event8  - Asus WMI hotkeys: is tagged by udev as: Keyboard
[  3378.230] (II) event8  - Asus WMI hotkeys: device is a keyboard
[  3378.230] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[  3378.230] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"
[  3378.230] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'
[  3378.231] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 28 paused 0
[  3378.231] (**) AT Translated Set 2 keyboard: always reports core events
[  3378.231] (**) Option "Device" "/dev/input/event3"
[  3378.231] (**) Option "_source" "server/udev"
[  3378.232] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[  3378.232] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[  3378.232] (II) event3  - AT Translated Set 2 keyboard: device removed
[  3378.232] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[  3378.232] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 13)
[  3378.232] (**) Option "xkb_model" "pc105"
[  3378.232] (**) Option "xkb_layout" "us,ge"
[  3378.232] (**) Option "xkb_variant" ","
[  3378.232] (**) Option "xkb_options" "grp:alt_shift_toggle,grp_led:scroll"
[  3378.232] (II) event3  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard
[  3378.232] (II) event3  - AT Translated Set 2 keyboard: device is a keyboard
[  3378.233] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/event6)
[  3378.233] (**) ETPS/2 Elantech Touchpad: Applying InputClass "libinput touchpad catchall"
[  3378.233] (II) Using input driver 'libinput' for 'ETPS/2 Elantech Touchpad'
[  3378.233] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 29 paused 0
[  3378.233] (**) ETPS/2 Elantech Touchpad: always reports core events
[  3378.233] (**) Option "Device" "/dev/input/event6"
[  3378.233] (**) Option "_source" "server/udev"
[  3378.234] (II) event6  - ETPS/2 Elantech Touchpad: is tagged by udev as: Touchpad
[  3378.234] (II) event6  - ETPS/2 Elantech Touchpad: device is a touchpad
[  3378.234] (II) event6  - ETPS/2 Elantech Touchpad: device removed
[  3378.234] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input11/event6"
[  3378.234] (II) XINPUT: Adding extended input device "ETPS/2 Elantech Touchpad" (type: TOUCHPAD, id 14)
[  3378.234] (**) Option "AccelerationScheme" "none"
[  3378.234] (**) ETPS/2 Elantech Touchpad: (accel) selected scheme none/0
[  3378.234] (**) ETPS/2 Elantech Touchpad: (accel) acceleration factor: 2.000
[  3378.234] (**) ETPS/2 Elantech Touchpad: (accel) acceleration threshold: 4
[  3378.235] (II) event6  - ETPS/2 Elantech Touchpad: is tagged by udev as: Touchpad
[  3378.235] (II) event6  - ETPS/2 Elantech Touchpad: device is a touchpad
[  3378.235] (II) config/udev: Adding input device ETPS/2 Elantech Touchpad (/dev/input/mouse0)
[  3378.235] (II) No input driver specified, ignoring this device.
[  3378.235] (II) This device may have been added with another device file.
[  3378.539] (**) Option "fd" "19"
[  3378.539] (II) event7  - Asus Wireless Radio Control: device removed
[  3378.539] (**) Option "fd" "22"
[  3378.539] (II) event5  - Video Bus: device removed
[  3378.539] (**) Option "fd" "23"
[  3378.539] (II) event4  - Video Bus: device removed
[  3378.539] (**) Option "fd" "24"
[  3378.539] (II) event1  - Power Button: device removed
[  3378.539] (**) Option "fd" "25"
[  3378.539] (II) event2  - Sleep Button: device removed
[  3378.539] (**) Option "fd" "26"
[  3378.539] (II) event9  - USB2.0 HD UVC WebCam: USB2.0 HD: device removed
[  3378.539] (**) Option "fd" "27"
[  3378.539] (II) event8  - Asus WMI hotkeys: device removed
[  3378.539] (**) Option "fd" "28"
[  3378.539] (II) event3  - AT Translated Set 2 keyboard: device removed
[  3378.539] (**) Option "fd" "29"
[  3378.539] (II) event6  - ETPS/2 Elantech Touchpad: device removed
[  3378.540] (II) UnloadModule: "libinput"
[  3378.540] (II) systemd-logind: releasing fd for 13:70
[  3378.580] (II) UnloadModule: "libinput"
[  3378.580] (II) systemd-logind: releasing fd for 13:67
[  3378.600] (II) UnloadModule: "libinput"
[  3378.600] (II) systemd-logind: releasing fd for 13:72
[  3378.624] (II) UnloadModule: "libinput"
[  3378.624] (II) systemd-logind: releasing fd for 13:73
[  3378.676] (II) UnloadModule: "libinput"
[  3378.676] (II) systemd-logind: releasing fd for 13:66
[  3378.716] (II) UnloadModule: "libinput"
[  3378.716] (II) systemd-logind: releasing fd for 13:65
[  3378.756] (II) UnloadModule: "libinput"
[  3378.756] (II) systemd-logind: releasing fd for 13:68
[  3378.772] (II) UnloadModule: "libinput"
[  3378.772] (II) systemd-logind: releasing fd for 13:69
[  3378.788] (II) UnloadModule: "libinput"
[  3378.788] (II) systemd-logind: releasing fd for 13:71
[  3380.331] (II) Server terminated successfully (0). Closing log file. 

```

---

### Post by m_ghv_geo on 2018-05-16
Resolved by
```
sudo apt-get purge bumblebee
sudo apt-get autoremove
sudo update-grub
```

---

### Post by QIII on 2018-05-16
Hello!

Congratulations on solving your issue!  Would you please use the Thread Tools dropdown to mark your thread as solved to help others find the solution?

Also, please use code tags rather than quote tags when posting terminal commands and their results.  That will preserve formatting and make your posts much easier to read.

To use quote tags you may click the # button above the text entry box, place your cursor between the tags that appear and type or paste your text.  Alternatively, type or paste your text, highlight it and then click the # button.

When using the Quick Reply button, type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] following your text.  The square brackets are required.

Thanks!

---

