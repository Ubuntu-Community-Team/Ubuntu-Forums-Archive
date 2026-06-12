---
title: "CItrix reciever Application invisable"
date: 2016-09-23
forum: Installation &amp; Upgrades
---

### Post by bram1221 on 2016-09-23
Hey,

After another thread with great guy`s that wanna help -> [https://ubuntuforums.org/showthread.php?t=2337077](https://ubuntuforums.org/showthread.php?t=2337077)
i have reinstall everything and at this point Citrix Reciever doenst work. 
When i`ll open a a full Desktop from citrix reciever everythings fine. But when i open a application trough citrix reciever its invisable look at attachement.

[ATTACH=CONFIG]271319[/ATTACH]

When i look at the log i see these errors:

```
sep 23 09:33:47 laptop gnome-session[1845]: (gnome-software:1999): Gs-WARNING **: failed to get updates: no results to showsep 23 09:34:00 laptop gnome-session[1845]: (gnome-shell:1897): Gtk-WARNING **: _XEMBED_INFO property has wrong type
sep 23 09:34:00 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_register_x_window: assertion 'g_hash_table_lookup (display->xids, xwindowp) == NULL' failed
sep 23 09:34:00 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_register_x_window: assertion 'g_hash_table_lookup (display->xids, xwindowp) == NULL' failed
sep 23 09:34:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_register_x_window: assertion 'g_hash_table_lookup (display->xids, xwindowp) == NULL' failed
sep 23 09:34:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_RAISE_ABOVE: window 0x24000e7 not in stack
sep 23 09:34:04 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_RAISE_ABOVE: window 0x24000e7 not in stack
sep 23 09:34:04 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_RAISE_ABOVE: window 0x24000fb not in stack
sep 23 09:34:09 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_RAISE_ABOVE: window 0x24000fb not in stack
sep 23 09:34:31 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_register_x_window: assertion 'g_hash_table_lookup (display->xids, xwindowp) == NULL' failed
sep 23 09:34:31 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_register_x_window: assertion 'g_hash_table_lookup (display->xids, xwindowp) == NULL' failed
sep 23 09:34:31 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_register_x_window: assertion 'g_hash_table_lookup (display->xids, xwindowp) == NULL' failed
sep 23 09:34:31 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_register_x_window: assertion 'g_hash_table_lookup (display->xids, xwindowp) == NULL' failed
sep 23 09:34:32 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) != NULL' failed
sep 23 09:34:32 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) != NULL' failed
sep 23 09:34:32 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) != NULL' failed
sep 23 09:34:32 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_register_x_window: assertion 'g_hash_table_lookup (display->xids, xwindowp) == NULL' failed
sep 23 09:34:32 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_register_x_window: assertion 'g_hash_table_lookup (display->xids, xwindowp) == NULL' failed
sep 23 09:34:33 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) != NULL' failed
sep 23 09:34:33 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) != NULL' failed
sep 23 09:34:33 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) != NULL' failed
sep 23 09:35:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_RAISE_ABOVE: window 0x240011d not in stack
sep 23 09:35:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_LOWER_BELOW: sibling window 0x240011d not in stack
sep 23 09:35:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) != NULL' failed
sep 23 09:35:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_RAISE_ABOVE: window 0x240011d not in stack
sep 23 09:35:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_LOWER_BELOW: sibling window 0x240011d not in stack
sep 23 09:35:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) != NULL' failed
sep 23 09:35:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_RAISE_ABOVE: window 0x240011d not in stack
sep 23 09:35:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-WARNING **: STACK_OP_LOWER_BELOW: sibling window 0x240011d not in stack
sep 23 09:35:02 laptop gnome-session[1845]: (gnome-shell:1897): mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) != NULL' failed



```

i have the same problem with citrix 13.4 and 13.3

Edit Update:

Teamviewer works well on primary laptop monitor. When moving to External Monitor nothings works i cannot click any button. When i move the window back to primary screen everythings fine again xD

---

### Post by mhejek on 2016-09-27
i got this too 
> mutter-CRITICAL **: meta_display_unregister_x_window: assertion 'g_hash_table_lookup (display->xids, &xwindow) 

i play ctrader program under wine with .net
 its run well
the problem is sometimes ive to close that aplication after got not responding

im running gubuntu 16 with wine 1.9.19

---

### Post by bram1221 on 2016-09-27
I only have this problem when i connect the second monitor. Wheni only use the laptop screen everythings works.

Even with citrix reciever and teamviewer(wine)

x11 log

```
cat /var/log/Xorg.0.log[    16.660] (--) Log file renamed from "/var/log/Xorg.pid-1426.log" to "/var/log/Xorg.0.log"
[    16.660] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[    16.660] X Protocol Version 11, Revision 0
[    16.660] Build Operating System: Linux 3.13.0-92-generic x86_64 Ubuntu
[    16.660] Current Operating System: Linux bizarro 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64
[    16.660] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-38-generic root=UUID=ffdc838b-d311-42c5-91c0-8361a84e71ee ro quiet splash maxcpus=4 vt.handoff=7
[    16.660] Build Date: 22 July 2016  07:50:34AM
[    16.660] xorg-server 2:1.18.3-1ubuntu2.3 (For technical support please see http://www.ubuntu.com/support) 
[    16.660] Current version of pixman: 0.33.6
[    16.660] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    16.660] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.660] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 27 07:58:38 2016
[    16.660] (==) Using config file: "/etc/X11/xorg.conf"
[    16.660] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.661] (==) ServerLayout "layout"
[    16.661] (**) |-->Screen "nvidia" (0)
[    16.661] (**) |   |-->Monitor "<default monitor>"
[    16.661] (**) |   |-->Device "nvidia"
[    16.661] (**) |   |-->GPUDevice "nvidia"
[    16.661] (==) No monitor specified for screen "nvidia".
	Using a default monitor configuration.
[    16.661] (**) |-->Inactive Device "intel"
[    16.661] (==) Automatically adding devices
[    16.661] (==) Automatically enabling devices
[    16.661] (==) Automatically adding GPU devices
[    16.661] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    16.661] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.661] 	Entry deleted from font path.
[    16.661] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.661] 	Entry deleted from font path.
[    16.661] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.661] 	Entry deleted from font path.
[    16.661] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.661] 	Entry deleted from font path.
[    16.661] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.661] 	Entry deleted from font path.
[    16.661] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    16.661] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.661] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.661] (II) Loader magic: 0x5592d6cafda0
[    16.661] (II) Module ABI versions:
[    16.661] 	X.Org ANSI C Emulation: 0.4
[    16.661] 	X.Org Video Driver: 20.0
[    16.661] 	X.Org XInput driver : 22.1
[    16.661] 	X.Org Server Extension : 9.0
[    16.661] (++) using VT number 7


[    16.662] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c1
[    16.663] (II) xfree86: Adding drm device (/dev/dri/card0)
[    16.663] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 9 paused 0
[    16.663] (II) xfree86: Adding drm device (/dev/dri/card1)
[    16.663] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 10 paused 0
[    16.664] (--) PCI:*(0:0:2:0) 8086:191b:1558:6a01 rev 6, Mem @ 0x2ffe000000/16777216, 0x60000000/268435456, I/O @ 0x0000f000/64
[    16.664] (--) PCI: (0:1:0:0) 10de:1be1:1558:6a03 rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    16.664] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    16.664] (II) "glx" will be loaded by default.
[    16.664] (II) LoadModule: "glx"
[    16.664] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    16.700] (II) Module glx: vendor="NVIDIA Corporation"
[    16.700] 	compiled for 4.0.2, module version = 1.0.0
[    16.700] 	Module class: X.Org Server Extension
[    16.700] (II) NVIDIA GLX Module  367.44  Wed Aug 17 21:50:26 PDT 2016
[    16.700] (II) LoadModule: "nvidia"
[    16.700] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    16.703] (II) Module nvidia: vendor="NVIDIA Corporation"
[    16.703] 	compiled for 4.0.2, module version = 1.0.0
[    16.703] 	Module class: X.Org Video Driver
[    16.704] (II) LoadModule: "modesetting"
[    16.704] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    16.704] (II) Module modesetting: vendor="X.Org Foundation"
[    16.704] 	compiled for 1.18.3, module version = 1.18.3
[    16.704] 	Module class: X.Org Video Driver
[    16.704] 	ABI class: X.Org Video Driver, version 20.0
[    16.704] (II) NVIDIA dlloader X Driver  367.44  Wed Aug 17 21:28:13 PDT 2016
[    16.704] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    16.704] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    16.704] (II) systemd-logind: releasing fd for 226:0
[    16.705] (II) Loading sub module "fb"
[    16.705] (II) LoadModule: "fb"
[    16.705] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.706] (II) Module fb: vendor="X.Org Foundation"
[    16.706] 	compiled for 1.18.3, module version = 1.0.0
[    16.706] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    16.706] (II) Loading sub module "wfb"
[    16.706] (II) LoadModule: "wfb"
[    16.706] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.706] (II) Module wfb: vendor="X.Org Foundation"
[    16.706] 	compiled for 1.18.3, module version = 1.0.0
[    16.706] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    16.706] (II) Loading sub module "ramdac"
[    16.706] (II) LoadModule: "ramdac"
[    16.706] (II) Module "ramdac" already built-in
[    16.707] (II) modeset(G0): using drv /dev/dri/card1
[    16.707] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"nvidia" for depth/fbbpp 24/32
[    16.707] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    16.707] (==) NVIDIA(0): RGB weight 888
[    16.707] (==) NVIDIA(0): Default visual is TrueColor
[    16.707] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    16.708] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    16.708] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    16.708] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    16.708] (**) NVIDIA(0): Option "RegistryDwords" "PowerMizerEnable=0x2; PerfLevelSrc=0x2222; PowerMizerDefaultAC=0x2"
[    16.708] (**) NVIDIA(0): Enabling 2D acceleration
[    17.265] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    17.265] (--) NVIDIA(0):     DFP-0
[    17.265] (--) NVIDIA(0):     DFP-1
[    17.265] (--) NVIDIA(0):     DFP-2
[    17.265] (--) NVIDIA(0):     DFP-3 (boot)
[    17.265] (--) NVIDIA(0):     DFP-4
[    17.265] (--) NVIDIA(0): DFP-0: disconnected
[    17.265] (--) NVIDIA(0): DFP-0: Internal TMDS
[    17.265] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    17.265] (--) NVIDIA(0): 
[    17.265] (--) NVIDIA(0): DFP-1: disconnected
[    17.265] (--) NVIDIA(0): DFP-1: Internal DisplayPort
[    17.265] (--) NVIDIA(0): DFP-1: 1440.0 MHz maximum pixel clock
[    17.265] (--) NVIDIA(0): 
[    17.265] (--) NVIDIA(0): DFP-2: disconnected
[    17.265] (--) NVIDIA(0): DFP-2: Internal TMDS
[    17.265] (--) NVIDIA(0): DFP-2: 330.0 MHz maximum pixel clock
[    17.265] (--) NVIDIA(0): 
[    17.266] (--) NVIDIA(0): HP E242 (DFP-3): connected
[    17.266] (--) NVIDIA(0): HP E242 (DFP-3): Internal DisplayPort
[    17.266] (--) NVIDIA(0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    17.266] (--) NVIDIA(0): 
[    17.266] (--) NVIDIA(0): DFP-4: disconnected
[    17.266] (--) NVIDIA(0): DFP-4: Internal TMDS
[    17.266] (--) NVIDIA(0): DFP-4: 330.0 MHz maximum pixel clock
[    17.266] (--) NVIDIA(0): 
[    17.268] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 1070 (GP104-B) at PCI:1:0:0 (GPU-0)
[    17.268] (--) NVIDIA(0): Memory: 8388608 kBytes
[    17.268] (--) NVIDIA(0): VideoBIOS: 86.04.2a.00.11
[    17.268] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    17.268] (**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID for display
[    17.268] (**) NVIDIA(0):     device HP E242 (DFP-3) (Using EDID frequencies has been
[    17.268] (**) NVIDIA(0):     enabled on all display devices.)
[    17.269] (==) NVIDIA(0): 
[    17.269] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    17.269] (==) NVIDIA(0):     will be used as the requested mode.
[    17.269] (==) NVIDIA(0): 
[    17.270] (II) NVIDIA(0): Validated MetaModes:
[    17.270] (II) NVIDIA(0):     "DFP-3:nvidia-auto-select"
[    17.270] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1200
[    17.275] (--) NVIDIA(0): DPI set to (93, 95); computed from "UseEdidDpi" X config
[    17.275] (--) NVIDIA(0):     option
[    17.275] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[    17.275] (**) modeset(G0): Option "AccelMethod" "None"
[    17.275] (==) modeset(G0): RGB weight 888
[    17.275] (==) modeset(G0): Default visual is TrueColor
[    17.275] (**) modeset(G0): glamor disabled
[    17.275] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[    17.276] (II) modeset(G0): Output eDP-1 has no monitor section
[    17.278] (II) modeset(G0): Output DP-1 has no monitor section
[    17.278] (II) modeset(G0): EDID for output eDP-1
[    17.278] (II) modeset(G0): Manufacturer: LGD  Model: 46f  Serial#: 0
[    17.278] (II) modeset(G0): Year: 2014  Week: 0
[    17.278] (II) modeset(G0): EDID Version: 1.4
[    17.278] (II) modeset(G0): Digital Display Input
[    17.278] (II) modeset(G0): 6 bits per channel
[    17.278] (II) modeset(G0): Digital interface is DisplayPort
[    17.278] (II) modeset(G0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    17.278] (II) modeset(G0): Gamma: 2.20
[    17.278] (II) modeset(G0): DPMS capabilities: StandBy Suspend Off
[    17.278] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.278] (II) modeset(G0): First detailed timing is preferred mode
[    17.278] (II) modeset(G0): Preferred mode is native pixel format and refresh rate
[    17.278] (II) modeset(G0): redX: 0.640 redY: 0.345   greenX: 0.335 greenY: 0.625
[    17.278] (II) modeset(G0): blueX: 0.150 blueY: 0.052   whiteX: 0.313 whiteY: 0.329
[    17.278] (II) modeset(G0): Manufacturer's mask: 0
[    17.278] (II) modeset(G0): Supported detailed timing:
[    17.278] (II) modeset(G0): clock: 138.7 MHz   Image Size:  344 x 194 mm
[    17.278] (II) modeset(G0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    17.278] (II) modeset(G0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    17.278] (II) modeset(G0): Supported detailed timing:
[    17.278] (II) modeset(G0): clock: 110.9 MHz   Image Size:  344 x 194 mm
[    17.278] (II) modeset(G0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    17.278] (II) modeset(G0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    17.278] (II) modeset(G0):  3874Y&#65533;156WF6
[    17.278] (II) modeset(G0): Unknown vendor-specific block 0
[    17.278] (II) modeset(G0): EDID (in hex):
[    17.278] (II) modeset(G0): 	00ffffffffffff0030e46f0400000000
[    17.278] (II) modeset(G0): 	0018010495221378eadc95a35855a026
[    17.278] (II) modeset(G0): 	0d505400000001010101010101010101
[    17.278] (II) modeset(G0): 	0101010101012e3680a070381f403020
[    17.278] (II) modeset(G0): 	350058c21000001a522b80a070381f40
[    17.278] (II) modeset(G0): 	3020350058c21000001a000000fe0033
[    17.278] (II) modeset(G0): 	38373459803135365746360a00000000
[    17.278] (II) modeset(G0): 	000041319e001000000a010a20200092
[    17.279] (II) modeset(G0): Printing probed modes for output eDP-1
[    17.279] (II) modeset(G0): Modeline "1920x1080"x60.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz eP)
[    17.279] (II) modeset(G0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[    17.279] (II) modeset(G0): Modeline "1920x1080"x48.0  110.90  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (53.3 kHz e)
[    17.279] (II) modeset(G0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[    17.279] (II) modeset(G0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[    17.279] (II) modeset(G0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[    17.279] (II) modeset(G0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    17.279] (II) modeset(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    17.279] (II) modeset(G0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    17.279] (II) modeset(G0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[    17.279] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    17.279] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    17.279] (II) modeset(G0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    17.279] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    17.279] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    17.279] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    17.279] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    17.279] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    17.279] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    17.279] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    17.279] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    17.279] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    17.279] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    17.279] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    17.279] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    17.279] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    17.279] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    17.279] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    17.279] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    17.279] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    17.279] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    17.279] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    17.279] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    17.279] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    17.279] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    17.279] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    17.279] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    17.279] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    17.281] (II) modeset(G0): EDID for output DP-1
[    17.281] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.281] (==) modeset(G0): DPI set to (96, 96)
[    17.281] (II) Loading sub module "fb"
[    17.281] (II) LoadModule: "fb"
[    17.281] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.281] (II) Module fb: vendor="X.Org Foundation"
[    17.281] 	compiled for 1.18.3, module version = 1.0.0
[    17.281] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.281] (II) Loading sub module "shadow"
[    17.281] (II) LoadModule: "shadow"
[    17.281] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    17.281] (II) Module shadow: vendor="X.Org Foundation"
[    17.281] 	compiled for 1.18.3, module version = 1.1.0
[    17.281] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.281] (--) Depth 24 pixmap format is 32 bpp
[    17.282] (==) modeset(G0): Backing store enabled
[    17.282] (==) modeset(G0): Silken mouse enabled
[    17.282] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.283] (==) modeset(G0): DPMS enabled
[    17.283] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[    17.283] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[    17.568] (II) NVIDIA: Using 49152.00 MB of virtual memory for indirect memory
[    17.568] (II) NVIDIA:     access.
[    17.600] (II) NVIDIA(0): Setting mode "DFP-3:nvidia-auto-select"
[    17.638] (==) NVIDIA(0): Disabling shared memory pixmaps
[    17.638] (==) NVIDIA(0): Backing store enabled
[    17.638] (==) NVIDIA(0): Silken mouse enabled
[    17.638] (==) NVIDIA(0): DPMS enabled
[    17.638] (II) Loading sub module "dri2"
[    17.638] (II) LoadModule: "dri2"
[    17.639] (II) Module "dri2" already built-in
[    17.639] (II) NVIDIA(0): [DRI2] Setup complete
[    17.639] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    17.639] (--) RandR disabled
[    17.641] (II) SELinux: Disabled on system
[    17.642] (II) Initializing extension GLX
[    17.642] (II) Indirect GLX disabled.
[    17.643] (II) modeset(G0): Damage tracking initialized
[    17.678] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    17.678] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.678] (II) LoadModule: "evdev"
[    17.678] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.678] (II) Module evdev: vendor="X.Org Foundation"
[    17.678] 	compiled for 1.18.1, module version = 2.10.1
[    17.678] 	Module class: X.Org XInput Driver
[    17.678] 	ABI class: X.Org XInput driver, version 22.1
[    17.679] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 32 paused 0
[    17.679] (II) Using input driver 'evdev' for 'Power Button'
[    17.679] (**) Power Button: always reports core events
[    17.679] (**) evdev: Power Button: Device: "/dev/input/event3"
[    17.679] (--) evdev: Power Button: Vendor 0 Product 0x1
[    17.679] (--) evdev: Power Button: Found keys
[    17.679] (II) evdev: Power Button: Configuring as keyboard
[    17.679] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    17.679] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    17.679] (**) Option "xkb_rules" "evdev"
[    17.679] (**) Option "xkb_model" "pc105"
[    17.679] (**) Option "xkb_layout" "us"
[    17.679] (**) Option "xkb_variant" "intl"
[    17.690] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[    17.690] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.691] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 33 paused 0
[    17.691] (II) Using input driver 'evdev' for 'Video Bus'
[    17.691] (**) Video Bus: always reports core events
[    17.691] (**) evdev: Video Bus: Device: "/dev/input/event4"
[    17.691] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    17.691] (--) evdev: Video Bus: Found keys
[    17.691] (II) evdev: Video Bus: Configuring as keyboard
[    17.691] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10/event4"
[    17.691] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    17.691] (**) Option "xkb_rules" "evdev"
[    17.691] (**) Option "xkb_model" "pc105"
[    17.691] (**) Option "xkb_layout" "us"
[    17.691] (**) Option "xkb_variant" "intl"
[    17.691] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    17.691] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    17.691] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 34 paused 0
[    17.691] (II) Using input driver 'evdev' for 'Video Bus'
[    17.691] (**) Video Bus: always reports core events
[    17.691] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    17.691] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    17.691] (--) evdev: Video Bus: Found keys
[    17.691] (II) evdev: Video Bus: Configuring as keyboard
[    17.691] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/LNXVIDEO:01/input/input11/event5"
[    17.691] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    17.691] (**) Option "xkb_rules" "evdev"
[    17.691] (**) Option "xkb_model" "pc105"
[    17.691] (**) Option "xkb_layout" "us"
[    17.691] (**) Option "xkb_variant" "intl"
[    17.692] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    17.692] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.692] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 35 paused 0
[    17.692] (II) Using input driver 'evdev' for 'Power Button'
[    17.692] (**) Power Button: always reports core events
[    17.692] (**) evdev: Power Button: Device: "/dev/input/event0"
[    17.692] (--) evdev: Power Button: Vendor 0 Product 0x1
[    17.692] (--) evdev: Power Button: Found keys
[    17.692] (II) evdev: Power Button: Configuring as keyboard
[    17.692] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    17.692] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    17.692] (**) Option "xkb_rules" "evdev"
[    17.692] (**) Option "xkb_model" "pc105"
[    17.692] (**) Option "xkb_layout" "us"
[    17.692] (**) Option "xkb_variant" "intl"
[    17.692] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    17.692] (II) No input driver specified, ignoring this device.
[    17.692] (II) This device may have been added with another device file.
[    17.692] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    17.692] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    17.693] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 36 paused 0
[    17.693] (II) Using input driver 'evdev' for 'Sleep Button'
[    17.693] (**) Sleep Button: always reports core events
[    17.693] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    17.693] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    17.693] (--) evdev: Sleep Button: Found keys
[    17.693] (II) evdev: Sleep Button: Configuring as keyboard
[    17.693] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    17.693] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    17.693] (**) Option "xkb_rules" "evdev"
[    17.693] (**) Option "xkb_model" "pc105"
[    17.693] (**) Option "xkb_layout" "us"
[    17.693] (**) Option "xkb_variant" "intl"
[    17.693] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event15)
[    17.693] (II) No input driver specified, ignoring this device.
[    17.693] (II) This device may have been added with another device file.
[    17.693] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event16)
[    17.693] (II) No input driver specified, ignoring this device.
[    17.693] (II) This device may have been added with another device file.
[    17.693] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event17)
[    17.693] (II) No input driver specified, ignoring this device.
[    17.693] (II) This device may have been added with another device file.
[    17.694] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/event6)
[    17.694] (**) Logitech USB Laser Mouse: Applying InputClass "evdev pointer catchall"
[    17.748] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 37 paused 0
[    17.748] (II) Using input driver 'evdev' for 'Logitech USB Laser Mouse'
[    17.748] (**) Logitech USB Laser Mouse: always reports core events
[    17.748] (**) evdev: Logitech USB Laser Mouse: Device: "/dev/input/event6"
[    17.748] (--) evdev: Logitech USB Laser Mouse: Vendor 0x46d Product 0xc069
[    17.748] (--) evdev: Logitech USB Laser Mouse: Found 12 mouse buttons
[    17.748] (--) evdev: Logitech USB Laser Mouse: Found scroll wheel(s)
[    17.748] (--) evdev: Logitech USB Laser Mouse: Found relative axes
[    17.748] (--) evdev: Logitech USB Laser Mouse: Found x and y relative axes
[    17.748] (II) evdev: Logitech USB Laser Mouse: Configuring as mouse
[    17.748] (II) evdev: Logitech USB Laser Mouse: Adding scrollwheel support
[    17.748] (**) evdev: Logitech USB Laser Mouse: YAxisMapping: buttons 4 and 5
[    17.748] (**) evdev: Logitech USB Laser Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    17.748] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4:1.0/0003:046D:C069.0001/input/input13/event6"
[    17.748] (II) XINPUT: Adding extended input device "Logitech USB Laser Mouse" (type: MOUSE, id 11)
[    17.748] (II) evdev: Logitech USB Laser Mouse: initialized for relative axes.
[    17.748] (**) Logitech USB Laser Mouse: (accel) keeping acceleration scheme 1
[    17.748] (**) Logitech USB Laser Mouse: (accel) acceleration profile 0
[    17.748] (**) Logitech USB Laser Mouse: (accel) acceleration factor: 2.000
[    17.748] (**) Logitech USB Laser Mouse: (accel) acceleration threshold: 4
[    17.748] (II) config/udev: Adding input device Logitech USB Laser Mouse (/dev/input/mouse0)
[    17.748] (II) No input driver specified, ignoring this device.
[    17.748] (II) This device may have been added with another device file.
[    17.748] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event7)
[    17.749] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    17.749] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 38 paused 0
[    17.749] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    17.749] (**) Logitech USB Keyboard: always reports core events
[    17.749] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event7"
[    17.749] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    17.749] (--) evdev: Logitech USB Keyboard: Found keys
[    17.749] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    17.749] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.0/0003:046D:C31C.0002/input/input14/event7"
[    17.749] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 12)
[    17.749] (**) Option "xkb_rules" "evdev"
[    17.749] (**) Option "xkb_model" "pc105"
[    17.749] (**) Option "xkb_layout" "us"
[    17.749] (**) Option "xkb_variant" "intl"
[    17.749] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event8)
[    17.749] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    17.750] (II) systemd-logind: got fd for /dev/input/event8 13:72 fd 39 paused 0
[    17.750] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    17.750] (**) Logitech USB Keyboard: always reports core events
[    17.750] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event8"
[    17.750] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    17.750] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    17.750] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    17.750] (--) evdev: Logitech USB Keyboard: Found keys
[    17.750] (II) evdev: Logitech USB Keyboard: Forcing relative x/y axes to exist.
[    17.750] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    17.750] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    17.750] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5:1.1/0003:046D:C31C.0003/input/input15/event8"
[    17.750] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 13)
[    17.750] (**) Option "xkb_rules" "evdev"
[    17.750] (**) Option "xkb_model" "pc105"
[    17.750] (**) Option "xkb_layout" "us"
[    17.750] (**) Option "xkb_variant" "intl"
[    17.750] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    17.750] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    17.750] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    17.750] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    17.750] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    17.750] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    17.750] (II) No input driver specified, ignoring this device.
[    17.750] (II) This device may have been added with another device file.
[    17.750] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event11)
[    17.750] (II) No input driver specified, ignoring this device.
[    17.750] (II) This device may have been added with another device file.
[    17.751] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[    17.751] (II) No input driver specified, ignoring this device.
[    17.751] (II) This device may have been added with another device file.
[    17.751] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event13)
[    17.751] (II) No input driver specified, ignoring this device.
[    17.751] (II) This device may have been added with another device file.
[    17.751] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event14)
[    17.751] (II) No input driver specified, ignoring this device.
[    17.751] (II) This device may have been added with another device file.
[    17.751] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    17.751] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    17.751] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[    17.751] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    17.751] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    17.751] (II) LoadModule: "synaptics"
[    17.751] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    17.751] (II) Module synaptics: vendor="X.Org Foundation"
[    17.751] 	compiled for 1.18.1, module version = 1.8.2
[    17.751] 	Module class: X.Org XInput Driver
[    17.751] 	ABI class: X.Org XInput driver, version 22.1
[    17.752] (II) systemd-logind: got fd for /dev/input/event9 13:73 fd 40 paused 0
[    17.752] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    17.752] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    17.752] (**) Option "Device" "/dev/input/event9"
[    17.788] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1284 - 5656 (res 41)
[    17.788] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1128 - 4728 (res 61)
[    17.788] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    17.788] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    17.788] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    17.788] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    17.788] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    17.788] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    17.788] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input12/event9"
[    17.788] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 14)
[    17.788] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    17.788] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    17.788] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[    17.788] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    17.788] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    17.788] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    17.788] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    17.788] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    17.788] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    17.788] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    17.791] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    17.791] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    17.791] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    17.791] (--) NVIDIA(GPU-0): 
[    17.799] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.799] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.799] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.799] (--) NVIDIA(GPU-0): 
[    17.799] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    17.799] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    17.799] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    17.799] (--) NVIDIA(GPU-0): 
[    17.800] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    17.800] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    17.800] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    17.800] (--) NVIDIA(GPU-0): 
[    17.800] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    17.800] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    17.800] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    17.800] (--) NVIDIA(GPU-0): 
[    17.800] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    17.800] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    17.800] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    17.800] (--) NVIDIA(GPU-0): 
[    17.805] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.805] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.805] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.805] (--) NVIDIA(GPU-0): 
[    17.805] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    17.805] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    17.805] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    17.805] (--) NVIDIA(GPU-0): 
[    17.805] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    17.805] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    17.805] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    17.805] (--) NVIDIA(GPU-0): 
[    17.805] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    17.805] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    17.805] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    17.805] (--) NVIDIA(GPU-0): 
[    17.806] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    17.806] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    17.806] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    17.806] (--) NVIDIA(GPU-0): 
[    17.806] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.806] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.806] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.806] (--) NVIDIA(GPU-0): 
[    17.806] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    17.806] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    17.806] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    17.806] (--) NVIDIA(GPU-0): 
[    17.806] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    17.806] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    17.806] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    17.806] (--) NVIDIA(GPU-0): 
[    17.806] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    17.806] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    17.806] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    17.806] (--) NVIDIA(GPU-0): 
[    17.807] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    17.807] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    17.807] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    17.807] (--) NVIDIA(GPU-0): 
[    17.810] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    17.810] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    17.810] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    17.810] (--) NVIDIA(GPU-0): 
[    17.810] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    17.810] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    17.810] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    17.810] (--) NVIDIA(GPU-0): 
[    17.811] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    17.811] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    17.811] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    17.811] (--) NVIDIA(GPU-0): 
[    17.811] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    17.811] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    17.811] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    17.811] (--) NVIDIA(GPU-0): 
[    17.811] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    17.811] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    17.811] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    17.811] (--) NVIDIA(GPU-0): 
[    18.338] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.338] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.338] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.338] (--) NVIDIA(GPU-0): 
[    18.338] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    18.338] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    18.338] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    18.338] (--) NVIDIA(GPU-0): 
[    18.338] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    18.338] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    18.338] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    18.338] (--) NVIDIA(GPU-0): 
[    18.338] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    18.338] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    18.338] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    18.338] (--) NVIDIA(GPU-0): 
[    18.339] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    18.339] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    18.339] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    18.339] (--) NVIDIA(GPU-0): 
[    18.339] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.339] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.339] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.339] (--) NVIDIA(GPU-0): 
[    18.339] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    18.339] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    18.339] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    18.339] (--) NVIDIA(GPU-0): 
[    18.339] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    18.339] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    18.339] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    18.339] (--) NVIDIA(GPU-0): 
[    18.339] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    18.339] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    18.339] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    18.339] (--) NVIDIA(GPU-0): 
[    18.340] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    18.340] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    18.340] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    18.340] (--) NVIDIA(GPU-0): 
[    18.340] (II) modeset(G0): EDID vendor "LGD", prod id 1135
[    18.340] (II) modeset(G0): Printing DDC gathered Modelines:
[    18.340] (II) modeset(G0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz eP)
[    18.340] (II) modeset(G0): Modeline "1920x1080"x0.0  110.90  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (53.3 kHz e)
[    19.783] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    19.783] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    19.783] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    19.783] (--) NVIDIA(GPU-0): 
[    19.783] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    19.783] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    19.783] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    19.783] (--) NVIDIA(GPU-0): 
[    19.783] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    19.783] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    19.783] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    19.783] (--) NVIDIA(GPU-0): 
[    19.783] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    19.783] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    19.783] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    19.783] (--) NVIDIA(GPU-0): 
[    19.784] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    19.784] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    19.784] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    19.784] (--) NVIDIA(GPU-0): 
[    19.784] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    19.784] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    19.784] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    19.784] (--) NVIDIA(GPU-0): 
[    19.784] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    19.784] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    19.784] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    19.784] (--) NVIDIA(GPU-0): 
[    19.784] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    19.784] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    19.784] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    19.784] (--) NVIDIA(GPU-0): 
[    19.784] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    19.784] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    19.784] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    19.784] (--) NVIDIA(GPU-0): 
[    19.785] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    19.785] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    19.785] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    19.785] (--) NVIDIA(GPU-0): 
[    19.785] (II) modeset(G0): EDID vendor "LGD", prod id 1135
[    19.785] (II) modeset(G0): Printing DDC gathered Modelines:
[    19.785] (II) modeset(G0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz eP)
[    19.785] (II) modeset(G0): Modeline "1920x1080"x0.0  110.90  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (53.3 kHz e)
[    19.904] (II) NVIDIA(0): Setting mode "DP-2: nvidia-auto-select @1920x1200 +1920+0 {ViewPortIn=1920x1200, ViewPortOut=1920x1200+0+0}"
[    22.061] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    22.061] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    22.061] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    22.061] (--) NVIDIA(GPU-0): 
[    22.061] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    22.061] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    22.061] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    22.061] (--) NVIDIA(GPU-0): 
[    22.062] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    22.062] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    22.062] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    22.062] (--) NVIDIA(GPU-0): 
[    22.062] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    22.062] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    22.062] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    22.062] (--) NVIDIA(GPU-0): 
[    22.062] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    22.062] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    22.062] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    22.062] (--) NVIDIA(GPU-0): 
[    22.062] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    22.062] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    22.062] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    22.062] (--) NVIDIA(GPU-0): 
[    22.062] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    22.062] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    22.062] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    22.062] (--) NVIDIA(GPU-0): 
[    22.063] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    22.063] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    22.063] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    22.063] (--) NVIDIA(GPU-0): 
[    22.063] (--) NVIDIA(GPU-0): HP E242 (DFP-3): connected
[    22.063] (--) NVIDIA(GPU-0): HP E242 (DFP-3): Internal DisplayPort
[    22.063] (--) NVIDIA(GPU-0): HP E242 (DFP-3): 1440.0 MHz maximum pixel clock
[    22.063] (--) NVIDIA(GPU-0): 
[    22.063] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    22.063] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    22.063] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    22.063] (--) NVIDIA(GPU-0): 
[    22.064] (II) modeset(G0): EDID vendor "LGD", prod id 1135
[    22.064] (II) modeset(G0): Printing DDC gathered Modelines:
[    22.064] (II) modeset(G0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz eP)
[    22.064] (II) modeset(G0): Modeline "1920x1080"x0.0  110.90  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (53.3 kHz e)
[    27.561] (II) systemd-logind: got pause for 13:73
[    27.561] (II) systemd-logind: got pause for 13:72
[    27.561] (II) systemd-logind: got pause for 13:69
[    27.561] (II) systemd-logind: got pause for 13:65
[    27.561] (II) systemd-logind: got pause for 13:64
[    27.561] (II) systemd-logind: got pause for 226:1
[    27.561] (II) systemd-logind: got pause for 13:70
[    27.561] (II) systemd-logind: got pause for 13:71
[    27.561] (II) systemd-logind: got pause for 13:67
[    27.561] (II) systemd-logind: got pause for 13:68



```

---

### Post by bram1221 on 2016-09-28
Update: 

Plugin the second monitor after login everythings works perfect.

```
cat /var/log/Xorg.0.log[    17.192] (--) Log file renamed from "/var/log/Xorg.pid-1369.log" to "/var/log/Xorg.0.log"
[    17.193] 
X.Org X Server 1.18.3
Release Date: 2016-04-04
[    17.193] X Protocol Version 11, Revision 0
[    17.193] Build Operating System: Linux 3.13.0-92-generic x86_64 Ubuntu
[    17.193] Current Operating System: Linux bizarro 4.4.0-38-generic #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016 x86_64
[    17.193] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-38-generic root=UUID=ffdc838b-d311-42c5-91c0-8361a84e71ee ro quiet splash maxcpus=4 vt.handoff=7
[    17.193] Build Date: 22 July 2016  07:50:34AM
[    17.193] xorg-server 2:1.18.3-1ubuntu2.3 (For technical support please see http://www.ubuntu.com/support) 
[    17.193] Current version of pixman: 0.33.6
[    17.193] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    17.193] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    17.193] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Sep 28 13:13:24 2016
[    17.193] (==) Using config file: "/etc/X11/xorg.conf"
[    17.193] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    17.195] (==) ServerLayout "layout"
[    17.195] (**) |-->Screen "nvidia" (0)
[    17.195] (**) |   |-->Monitor "<default monitor>"
[    17.195] (**) |   |-->Device "nvidia"
[    17.195] (**) |   |-->GPUDevice "nvidia"
[    17.195] (==) No monitor specified for screen "nvidia".
	Using a default monitor configuration.
[    17.195] (**) |-->Inactive Device "intel"
[    17.195] (==) Automatically adding devices
[    17.195] (==) Automatically enabling devices
[    17.195] (==) Automatically adding GPU devices
[    17.195] (==) Max clients allowed: 256, resource mask: 0x1fffff
[    17.196] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    17.196] 	Entry deleted from font path.
[    17.196] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    17.196] 	Entry deleted from font path.
[    17.196] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    17.196] 	Entry deleted from font path.
[    17.197] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    17.197] 	Entry deleted from font path.
[    17.197] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    17.197] 	Entry deleted from font path.
[    17.197] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	built-ins
[    17.197] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    17.197] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    17.197] (II) Loader magic: 0x5642c27ccda0
[    17.197] (II) Module ABI versions:
[    17.197] 	X.Org ANSI C Emulation: 0.4
[    17.197] 	X.Org Video Driver: 20.0
[    17.197] 	X.Org XInput driver : 22.1
[    17.197] 	X.Org Server Extension : 9.0
[    17.198] (++) using VT number 7


[    17.199] (II) systemd-logind: took control of session /org/freedesktop/login1/session/c1
[    17.199] (II) xfree86: Adding drm device (/dev/dri/card0)
[    17.199] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 9 paused 0
[    17.199] (II) xfree86: Adding drm device (/dev/dri/card1)
[    17.199] (II) systemd-logind: got fd for /dev/dri/card1 226:1 fd 10 paused 0
[    17.200] (--) PCI:*(0:0:2:0) 8086:191b:1558:6a01 rev 6, Mem @ 0x2ffe000000/16777216, 0x60000000/268435456, I/O @ 0x0000f000/64
[    17.200] (--) PCI: (0:1:0:0) 10de:1be1:1558:6a03 rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xd0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    17.200] (WW) "glamoregl" will not be loaded unless you've specified it to be loaded elsewhere.
[    17.200] (II) "glx" will be loaded by default.
[    17.200] (II) LoadModule: "glx"
[    17.201] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[    17.240] (II) Module glx: vendor="NVIDIA Corporation"
[    17.240] 	compiled for 4.0.2, module version = 1.0.0
[    17.240] 	Module class: X.Org Server Extension
[    17.240] (II) NVIDIA GLX Module  370.28  Thu Sep  1 19:14:30 PDT 2016
[    17.241] (II) LoadModule: "nvidia"
[    17.241] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    17.245] (II) Module nvidia: vendor="NVIDIA Corporation"
[    17.245] 	compiled for 4.0.2, module version = 1.0.0
[    17.245] 	Module class: X.Org Video Driver
[    17.246] (II) LoadModule: "modesetting"
[    17.246] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    17.247] (II) Module modesetting: vendor="X.Org Foundation"
[    17.247] 	compiled for 1.18.3, module version = 1.18.3
[    17.247] 	Module class: X.Org Video Driver
[    17.247] 	ABI class: X.Org Video Driver, version 20.0
[    17.247] (II) NVIDIA dlloader X Driver  370.28  Thu Sep  1 18:51:40 PDT 2016
[    17.247] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    17.247] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    17.247] (II) systemd-logind: releasing fd for 226:0
[    17.248] (II) Loading sub module "fb"
[    17.248] (II) LoadModule: "fb"
[    17.249] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.249] (II) Module fb: vendor="X.Org Foundation"
[    17.249] 	compiled for 1.18.3, module version = 1.0.0
[    17.249] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.249] (II) Loading sub module "wfb"
[    17.249] (II) LoadModule: "wfb"
[    17.250] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    17.251] (II) Module wfb: vendor="X.Org Foundation"
[    17.251] 	compiled for 1.18.3, module version = 1.0.0
[    17.251] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.251] (II) Loading sub module "ramdac"
[    17.251] (II) LoadModule: "ramdac"
[    17.251] (II) Module "ramdac" already built-in
[    17.253] (II) modeset(G0): using drv /dev/dri/card1
[    17.253] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"nvidia" for depth/fbbpp 24/32
[    17.253] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    17.253] (==) NVIDIA(0): RGB weight 888
[    17.253] (==) NVIDIA(0): Default visual is TrueColor
[    17.253] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.254] (**) NVIDIA(0): Option "ConstrainCursor" "off"
[    17.254] (**) NVIDIA(0): Option "AllowEmptyInitialConfiguration" "on"
[    17.254] (**) NVIDIA(0): Option "IgnoreDisplayDevices" "CRT"
[    17.254] (**) NVIDIA(0): Option "RegistryDwords" "PowerMizerEnable=0x2; PerfLevelSrc=0x2222; PowerMizerDefaultAC=0x2"
[    17.254] (**) NVIDIA(0): Enabling 2D acceleration
[    17.799] (--) NVIDIA(0): Valid display device(s) on GPU-0 at PCI:1:0:0
[    17.800] (--) NVIDIA(0):     DFP-0
[    17.800] (--) NVIDIA(0):     DFP-1
[    17.800] (--) NVIDIA(0):     DFP-2
[    17.800] (--) NVIDIA(0):     DFP-3
[    17.800] (--) NVIDIA(0):     DFP-4
[    17.800] (--) NVIDIA(0): DFP-0: disconnected
[    17.800] (--) NVIDIA(0): DFP-0: Internal TMDS
[    17.800] (--) NVIDIA(0): DFP-0: 330.0 MHz maximum pixel clock
[    17.800] (--) NVIDIA(0): 
[    17.800] (--) NVIDIA(0): DFP-1: disconnected
[    17.800] (--) NVIDIA(0): DFP-1: Internal DisplayPort
[    17.800] (--) NVIDIA(0): DFP-1: 1440.0 MHz maximum pixel clock
[    17.800] (--) NVIDIA(0): 
[    17.800] (--) NVIDIA(0): DFP-2: disconnected
[    17.800] (--) NVIDIA(0): DFP-2: Internal TMDS
[    17.800] (--) NVIDIA(0): DFP-2: 330.0 MHz maximum pixel clock
[    17.800] (--) NVIDIA(0): 
[    17.800] (--) NVIDIA(0): DFP-3: disconnected
[    17.800] (--) NVIDIA(0): DFP-3: Internal DisplayPort
[    17.800] (--) NVIDIA(0): DFP-3: 1440.0 MHz maximum pixel clock
[    17.800] (--) NVIDIA(0): 
[    17.800] (--) NVIDIA(0): DFP-4: disconnected
[    17.800] (--) NVIDIA(0): DFP-4: Internal TMDS
[    17.800] (--) NVIDIA(0): DFP-4: 330.0 MHz maximum pixel clock
[    17.800] (--) NVIDIA(0): 
[    17.801] (II) NVIDIA(0): NVIDIA GPU GeForce GTX 1070 (GP104-B) at PCI:1:0:0 (GPU-0)
[    17.801] (--) NVIDIA(0): Memory: 8388608 kBytes
[    17.802] (--) NVIDIA(0): VideoBIOS: 86.04.2a.00.11
[    17.802] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    17.802] (==) NVIDIA(0): 
[    17.802] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    17.802] (==) NVIDIA(0):     will be used as the requested mode.
[    17.802] (==) NVIDIA(0): 
[    17.802] (--) NVIDIA(0): No enabled display devices found; starting anyway because
[    17.802] (--) NVIDIA(0):     AllowEmptyInitialConfiguration is enabled
[    17.802] (II) NVIDIA(0): Validated MetaModes:
[    17.802] (II) NVIDIA(0):     "NULL"
[    17.802] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    17.802] (WW) NVIDIA(0): Unable to get display device for DPI computation.
[    17.802] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    17.802] (==) modeset(G0): Depth 24, (==) framebuffer bpp 32
[    17.802] (**) modeset(G0): Option "AccelMethod" "None"
[    17.802] (==) modeset(G0): RGB weight 888
[    17.802] (==) modeset(G0): Default visual is TrueColor
[    17.802] (**) modeset(G0): glamor disabled
[    17.802] (II) modeset(G0): ShadowFB: preferred YES, enabled YES
[    17.802] (II) modeset(G0): Output eDP-1 has no monitor section
[    17.805] (II) modeset(G0): Output DP-1 has no monitor section
[    17.805] (II) modeset(G0): EDID for output eDP-1
[    17.805] (II) modeset(G0): Manufacturer: LGD  Model: 46f  Serial#: 0
[    17.805] (II) modeset(G0): Year: 2014  Week: 0
[    17.805] (II) modeset(G0): EDID Version: 1.4
[    17.805] (II) modeset(G0): Digital Display Input
[    17.805] (II) modeset(G0): 6 bits per channel
[    17.805] (II) modeset(G0): Digital interface is DisplayPort
[    17.805] (II) modeset(G0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    17.805] (II) modeset(G0): Gamma: 2.20
[    17.805] (II) modeset(G0): DPMS capabilities: StandBy Suspend Off
[    17.805] (II) modeset(G0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    17.805] (II) modeset(G0): First detailed timing is preferred mode
[    17.805] (II) modeset(G0): Preferred mode is native pixel format and refresh rate
[    17.805] (II) modeset(G0): redX: 0.640 redY: 0.345   greenX: 0.335 greenY: 0.625
[    17.805] (II) modeset(G0): blueX: 0.150 blueY: 0.052   whiteX: 0.313 whiteY: 0.329
[    17.805] (II) modeset(G0): Manufacturer's mask: 0
[    17.805] (II) modeset(G0): Supported detailed timing:
[    17.805] (II) modeset(G0): clock: 138.7 MHz   Image Size:  344 x 194 mm
[    17.805] (II) modeset(G0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    17.805] (II) modeset(G0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    17.805] (II) modeset(G0): Supported detailed timing:
[    17.805] (II) modeset(G0): clock: 110.9 MHz   Image Size:  344 x 194 mm
[    17.805] (II) modeset(G0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[    17.805] (II) modeset(G0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1111 v_border: 0
[    17.805] (II) modeset(G0):  3874Y&#65533;156WF6
[    17.805] (II) modeset(G0): Unknown vendor-specific block 0
[    17.805] (II) modeset(G0): EDID (in hex):
[    17.805] (II) modeset(G0): 	00ffffffffffff0030e46f0400000000
[    17.805] (II) modeset(G0): 	0018010495221378eadc95a35855a026
[    17.805] (II) modeset(G0): 	0d505400000001010101010101010101
[    17.805] (II) modeset(G0): 	0101010101012e3680a070381f403020
[    17.805] (II) modeset(G0): 	350058c21000001a522b80a070381f40
[    17.805] (II) modeset(G0): 	3020350058c21000001a000000fe0033
[    17.805] (II) modeset(G0): 	38373459803135365746360a00000000
[    17.805] (II) modeset(G0): 	000041319e001000000a010a20200092
[    17.805] (II) modeset(G0): Printing probed modes for output eDP-1
[    17.805] (II) modeset(G0): Modeline "1920x1080"x60.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz eP)
[    17.805] (II) modeset(G0): Modeline "1920x1080"x59.9  138.50  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.6 kHz d)
[    17.805] (II) modeset(G0): Modeline "1920x1080"x48.0  110.90  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (53.3 kHz e)
[    17.805] (II) modeset(G0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz d)
[    17.805] (II) modeset(G0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz d)
[    17.805] (II) modeset(G0): Modeline "1600x1024"x60.2  103.12  1600 1600 1656 1664  1024 1024 1029 1030 +hsync +vsync (62.0 kHz d)
[    17.805] (II) modeset(G0): Modeline "1400x1050"x60.0  122.00  1400 1488 1640 1880  1050 1052 1064 1082 +hsync +vsync (64.9 kHz d)
[    17.805] (II) modeset(G0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz d)
[    17.805] (II) modeset(G0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    17.805] (II) modeset(G0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz d)
[    17.805] (II) modeset(G0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    17.805] (II) modeset(G0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    17.805] (II) modeset(G0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    17.805] (II) modeset(G0): Modeline "1024x768"x120.1  133.47  1024 1100 1212 1400  768 768 770 794 doublescan -hsync +vsync (95.3 kHz d)
[    17.805] (II) modeset(G0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    17.805] (II) modeset(G0): Modeline "960x720"x120.0  117.00  960 1024 1128 1300  720 720 722 750 doublescan -hsync +vsync (90.0 kHz d)
[    17.805] (II) modeset(G0): Modeline "928x696"x120.1  109.15  928 976 1088 1264  696 696 698 719 doublescan -hsync +vsync (86.4 kHz d)
[    17.805] (II) modeset(G0): Modeline "896x672"x120.0  102.40  896 960 1060 1224  672 672 674 697 doublescan -hsync +vsync (83.7 kHz d)
[    17.805] (II) modeset(G0): Modeline "960x600"x120.0   77.00  960 984 1000 1040  600 601 604 617 doublescan +hsync -vsync (74.0 kHz d)
[    17.806] (II) modeset(G0): Modeline "960x540"x120.0   69.25  960 984 1000 1040  540 541 544 555 doublescan +hsync -vsync (66.6 kHz d)
[    17.806] (II) modeset(G0): Modeline "800x600"x120.0   81.00  800 832 928 1080  600 600 602 625 doublescan +hsync +vsync (75.0 kHz d)
[    17.806] (II) modeset(G0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    17.806] (II) modeset(G0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    17.806] (II) modeset(G0): Modeline "840x525"x120.0   73.12  840 892 980 1120  525 526 529 544 doublescan -hsync +vsync (65.3 kHz d)
[    17.806] (II) modeset(G0): Modeline "840x525"x119.8   59.50  840 864 880 920  525 526 529 540 doublescan +hsync -vsync (64.7 kHz d)
[    17.806] (II) modeset(G0): Modeline "800x512"x120.3   51.56  800 800 828 832  512 512 514 515 doublescan +hsync +vsync (62.0 kHz d)
[    17.806] (II) modeset(G0): Modeline "700x525"x120.0   61.00  700 744 820 940  525 526 532 541 doublescan +hsync +vsync (64.9 kHz d)
[    17.806] (II) modeset(G0): Modeline "640x512"x120.0   54.00  640 664 720 844  512 512 514 533 doublescan +hsync +vsync (64.0 kHz d)
[    17.806] (II) modeset(G0): Modeline "720x450"x119.8   53.25  720 760 836 952  450 451 454 467 doublescan -hsync +vsync (55.9 kHz d)
[    17.806] (II) modeset(G0): Modeline "640x480"x120.0   54.00  640 688 744 900  480 480 482 500 doublescan +hsync +vsync (60.0 kHz d)
[    17.806] (II) modeset(G0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    17.806] (II) modeset(G0): Modeline "680x384"x119.6   42.38  680 716 784 888  384 385 390 399 doublescan -hsync +vsync (47.7 kHz d)
[    17.806] (II) modeset(G0): Modeline "680x384"x119.9   36.00  680 704 720 760  384 385 390 395 doublescan +hsync -vsync (47.4 kHz d)
[    17.806] (II) modeset(G0): Modeline "576x432"x120.1   40.81  576 608 668 760  432 432 434 447 doublescan -hsync +vsync (53.7 kHz d)
[    17.806] (II) modeset(G0): Modeline "512x384"x120.0   32.50  512 524 592 672  384 385 388 403 doublescan -hsync -vsync (48.4 kHz d)
[    17.806] (II) modeset(G0): Modeline "400x300"x120.6   20.00  400 420 484 528  300 300 302 314 doublescan +hsync +vsync (37.9 kHz d)
[    17.806] (II) modeset(G0): Modeline "400x300"x112.7   18.00  400 412 448 512  300 300 301 312 doublescan +hsync +vsync (35.2 kHz d)
[    17.806] (II) modeset(G0): Modeline "320x240"x120.1   12.59  320 328 376 400  240 245 246 262 doublescan -hsync -vsync (31.5 kHz d)
[    17.808] (II) modeset(G0): EDID for output DP-1
[    17.808] (II) modeset(G0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    17.808] (==) modeset(G0): DPI set to (96, 96)
[    17.808] (II) Loading sub module "fb"
[    17.808] (II) LoadModule: "fb"
[    17.808] (II) Loading /usr/lib/xorg/modules/libfb.so
[    17.808] (II) Module fb: vendor="X.Org Foundation"
[    17.808] 	compiled for 1.18.3, module version = 1.0.0
[    17.808] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.808] (II) Loading sub module "shadow"
[    17.808] (II) LoadModule: "shadow"
[    17.808] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    17.808] (II) Module shadow: vendor="X.Org Foundation"
[    17.808] 	compiled for 1.18.3, module version = 1.1.0
[    17.808] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    17.808] (--) Depth 24 pixmap format is 32 bpp
[    17.809] (==) modeset(G0): Backing store enabled
[    17.809] (==) modeset(G0): Silken mouse enabled
[    17.809] (II) modeset(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    17.810] (==) modeset(G0): DPMS enabled
[    17.810] (WW) modeset(G0): Option "AllowEmptyInitialConfiguration" is not used
[    17.810] (WW) modeset(G0): Option "IgnoreDisplayDevices" is not used
[    18.090] (II) NVIDIA: Using 49152.00 MB of virtual memory for indirect memory
[    18.090] (II) NVIDIA:     access.
[    18.165] (II) NVIDIA(0): Setting mode "NULL"
[    18.177] (==) NVIDIA(0): Disabling shared memory pixmaps
[    18.177] (==) NVIDIA(0): Backing store enabled
[    18.177] (==) NVIDIA(0): Silken mouse enabled
[    18.177] (==) NVIDIA(0): DPMS enabled
[    18.177] (II) Loading sub module "dri2"
[    18.177] (II) LoadModule: "dri2"
[    18.177] (II) Module "dri2" already built-in
[    18.177] (II) NVIDIA(0): [DRI2] Setup complete
[    18.177] (II) NVIDIA(0): [DRI2]   VDPAU driver: nvidia
[    18.177] (--) RandR disabled
[    18.180] (II) SELinux: Disabled on system
[    18.181] (II) Initializing extension GLX
[    18.181] (II) Indirect GLX disabled.
[    18.182] (II) modeset(G0): Damage tracking initialized
[    18.228] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    18.228] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.228] (II) LoadModule: "evdev"
[    18.229] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.230] (II) Module evdev: vendor="X.Org Foundation"
[    18.230] 	compiled for 1.18.1, module version = 2.10.1
[    18.230] 	Module class: X.Org XInput Driver
[    18.230] 	ABI class: X.Org XInput driver, version 22.1
[    18.230] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 32 paused 0
[    18.230] (II) Using input driver 'evdev' for 'Power Button'
[    18.230] (**) Power Button: always reports core events
[    18.230] (**) evdev: Power Button: Device: "/dev/input/event3"
[    18.230] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.230] (--) evdev: Power Button: Found keys
[    18.230] (II) evdev: Power Button: Configuring as keyboard
[    18.230] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    18.230] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    18.230] (**) Option "xkb_rules" "evdev"
[    18.230] (**) Option "xkb_model" "pc105"
[    18.230] (**) Option "xkb_layout" "us"
[    18.230] (**) Option "xkb_variant" "intl"
[    18.241] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    18.241] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.242] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 33 paused 0
[    18.242] (II) Using input driver 'evdev' for 'Video Bus'
[    18.242] (**) Video Bus: always reports core events
[    18.242] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    18.242] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.242] (--) evdev: Video Bus: Found keys
[    18.242] (II) evdev: Video Bus: Configuring as keyboard
[    18.242] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10/event5"
[    18.242] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    18.242] (**) Option "xkb_rules" "evdev"
[    18.242] (**) Option "xkb_model" "pc105"
[    18.242] (**) Option "xkb_layout" "us"
[    18.242] (**) Option "xkb_variant" "intl"
[    18.242] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    18.242] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    18.242] (II) systemd-logind: got fd for /dev/input/event6 13:70 fd 34 paused 0
[    18.243] (II) Using input driver 'evdev' for 'Video Bus'
[    18.243] (**) Video Bus: always reports core events
[    18.243] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    18.243] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    18.243] (--) evdev: Video Bus: Found keys
[    18.243] (II) evdev: Video Bus: Configuring as keyboard
[    18.243] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:11/LNXVIDEO:01/input/input11/event6"
[    18.243] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    18.243] (**) Option "xkb_rules" "evdev"
[    18.243] (**) Option "xkb_model" "pc105"
[    18.243] (**) Option "xkb_layout" "us"
[    18.243] (**) Option "xkb_variant" "intl"
[    18.243] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    18.243] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    18.243] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 35 paused 0
[    18.243] (II) Using input driver 'evdev' for 'Power Button'
[    18.243] (**) Power Button: always reports core events
[    18.243] (**) evdev: Power Button: Device: "/dev/input/event0"
[    18.243] (--) evdev: Power Button: Vendor 0 Product 0x1
[    18.243] (--) evdev: Power Button: Found keys
[    18.243] (II) evdev: Power Button: Configuring as keyboard
[    18.243] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    18.243] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    18.243] (**) Option "xkb_rules" "evdev"
[    18.243] (**) Option "xkb_model" "pc105"
[    18.243] (**) Option "xkb_layout" "us"
[    18.243] (**) Option "xkb_variant" "intl"
[    18.244] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    18.244] (II) No input driver specified, ignoring this device.
[    18.244] (II) This device may have been added with another device file.
[    18.244] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    18.244] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    18.244] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 36 paused 0
[    18.244] (II) Using input driver 'evdev' for 'Sleep Button'
[    18.244] (**) Sleep Button: always reports core events
[    18.244] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    18.244] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    18.244] (--) evdev: Sleep Button: Found keys
[    18.244] (II) evdev: Sleep Button: Configuring as keyboard
[    18.244] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    18.244] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 10)
[    18.244] (**) Option "xkb_rules" "evdev"
[    18.244] (**) Option "xkb_model" "pc105"
[    18.244] (**) Option "xkb_layout" "us"
[    18.244] (**) Option "xkb_variant" "intl"
[    18.245] (II) config/udev: Adding input device Logitech M705 (/dev/input/event7)
[    18.245] (**) Logitech M705: Applying InputClass "evdev pointer catchall"
[    18.245] (II) systemd-logind: got fd for /dev/input/event7 13:71 fd 37 paused 0
[    18.245] (II) Using input driver 'evdev' for 'Logitech M705'
[    18.245] (**) Logitech M705: always reports core events
[    18.245] (**) evdev: Logitech M705: Device: "/dev/input/event7"
[    18.245] (--) evdev: Logitech M705: Vendor 0x46d Product 0x101b
[    18.245] (--) evdev: Logitech M705: Found 20 mouse buttons
[    18.245] (--) evdev: Logitech M705: Found scroll wheel(s)
[    18.245] (--) evdev: Logitech M705: Found relative axes
[    18.245] (--) evdev: Logitech M705: Found x and y relative axes
[    18.245] (II) evdev: Logitech M705: Configuring as mouse
[    18.245] (II) evdev: Logitech M705: Adding scrollwheel support
[    18.245] (**) evdev: Logitech M705: YAxisMapping: buttons 4 and 5
[    18.245] (**) evdev: Logitech M705: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.245] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.5/1-5.5:1.2/0003:046D:C52B.0003/0003:046D:101B.0004/input/input13/event7"
[    18.245] (II) XINPUT: Adding extended input device "Logitech M705" (type: MOUSE, id 11)
[    18.245] (II) evdev: Logitech M705: initialized for relative axes.
[    18.245] (**) Logitech M705: (accel) keeping acceleration scheme 1
[    18.245] (**) Logitech M705: (accel) acceleration profile 0
[    18.245] (**) Logitech M705: (accel) acceleration factor: 2.000
[    18.245] (**) Logitech M705: (accel) acceleration threshold: 4
[    18.246] (II) config/udev: Adding input device Logitech M705 (/dev/input/mouse0)
[    18.246] (II) No input driver specified, ignoring this device.
[    18.246] (II) This device may have been added with another device file.
[    18.246] (II) config/udev: Adding input device Logitech M705 (/dev/input/event8)
[    18.246] (**) Logitech M705: Applying InputClass "evdev pointer catchall"
[    18.246] (II) systemd-logind: got fd for /dev/input/event8 13:72 fd 38 paused 0
[    18.246] (II) Using input driver 'evdev' for 'Logitech M705'
[    18.246] (**) Logitech M705: always reports core events
[    18.246] (**) evdev: Logitech M705: Device: "/dev/input/event8"
[    18.246] (--) evdev: Logitech M705: Vendor 0x46d Product 0x101b
[    18.246] (--) evdev: Logitech M705: Found 20 mouse buttons
[    18.246] (--) evdev: Logitech M705: Found scroll wheel(s)
[    18.246] (--) evdev: Logitech M705: Found relative axes
[    18.246] (--) evdev: Logitech M705: Found x and y relative axes
[    18.246] (II) evdev: Logitech M705: Configuring as mouse
[    18.246] (II) evdev: Logitech M705: Adding scrollwheel support
[    18.246] (**) evdev: Logitech M705: YAxisMapping: buttons 4 and 5
[    18.246] (**) evdev: Logitech M705: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.246] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.5/1-5.5:1.2/0003:046D:C52B.0003/0003:046D:101B.0006/input/input14/event8"
[    18.246] (II) XINPUT: Adding extended input device "Logitech M705" (type: MOUSE, id 12)
[    18.247] (II) evdev: Logitech M705: initialized for relative axes.
[    18.247] (**) Logitech M705: (accel) keeping acceleration scheme 1
[    18.247] (**) Logitech M705: (accel) acceleration profile 0
[    18.247] (**) Logitech M705: (accel) acceleration factor: 2.000
[    18.247] (**) Logitech M705: (accel) acceleration threshold: 4
[    18.247] (II) config/udev: Adding input device Logitech M705 (/dev/input/mouse1)
[    18.247] (II) No input driver specified, ignoring this device.
[    18.247] (II) This device may have been added with another device file.
[    18.247] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event10)
[    18.247] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.248] (II) systemd-logind: got fd for /dev/input/event10 13:74 fd 39 paused 0
[    18.248] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    18.248] (**) Logitech USB Keyboard: always reports core events
[    18.248] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event10"
[    18.248] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    18.248] (--) evdev: Logitech USB Keyboard: Found keys
[    18.248] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    18.248] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.6/1-5.6:1.0/0003:046D:C31C.0007/input/input17/event10"
[    18.248] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 13)
[    18.248] (**) Option "xkb_rules" "evdev"
[    18.248] (**) Option "xkb_model" "pc105"
[    18.248] (**) Option "xkb_layout" "us"
[    18.248] (**) Option "xkb_variant" "intl"
[    18.248] (II) config/udev: Adding input device Logitech USB Keyboard (/dev/input/event11)
[    18.248] (**) Logitech USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    18.249] (II) systemd-logind: got fd for /dev/input/event11 13:75 fd 40 paused 0
[    18.249] (II) Using input driver 'evdev' for 'Logitech USB Keyboard'
[    18.249] (**) Logitech USB Keyboard: always reports core events
[    18.249] (**) evdev: Logitech USB Keyboard: Device: "/dev/input/event11"
[    18.249] (--) evdev: Logitech USB Keyboard: Vendor 0x46d Product 0xc31c
[    18.249] (--) evdev: Logitech USB Keyboard: Found absolute axes
[    18.249] (II) evdev: Logitech USB Keyboard: Forcing absolute x/y axes to exist.
[    18.249] (--) evdev: Logitech USB Keyboard: Found keys
[    18.249] (II) evdev: Logitech USB Keyboard: Forcing relative x/y axes to exist.
[    18.249] (II) evdev: Logitech USB Keyboard: Configuring as mouse
[    18.249] (II) evdev: Logitech USB Keyboard: Configuring as keyboard
[    18.249] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-5/1-5.6/1-5.6:1.1/0003:046D:C31C.0008/input/input18/event11"
[    18.249] (II) XINPUT: Adding extended input device "Logitech USB Keyboard" (type: KEYBOARD, id 14)
[    18.249] (**) Option "xkb_rules" "evdev"
[    18.249] (**) Option "xkb_model" "pc105"
[    18.249] (**) Option "xkb_layout" "us"
[    18.249] (**) Option "xkb_variant" "intl"
[    18.249] (II) evdev: Logitech USB Keyboard: initialized for absolute axes.
[    18.249] (**) Logitech USB Keyboard: (accel) keeping acceleration scheme 1
[    18.249] (**) Logitech USB Keyboard: (accel) acceleration profile 0
[    18.249] (**) Logitech USB Keyboard: (accel) acceleration factor: 2.000
[    18.249] (**) Logitech USB Keyboard: (accel) acceleration threshold: 4
[    18.249] (II) config/udev: Adding input device Chicony USB 2.0 Camera (/dev/input/event12)
[    18.249] (**) Chicony USB 2.0 Camera: Applying InputClass "evdev keyboard catchall"
[    18.250] (II) systemd-logind: got fd for /dev/input/event12 13:76 fd 41 paused 0
[    18.250] (II) Using input driver 'evdev' for 'Chicony USB 2.0 Camera'
[    18.250] (**) Chicony USB 2.0 Camera: always reports core events
[    18.250] (**) evdev: Chicony USB 2.0 Camera: Device: "/dev/input/event12"
[    18.250] (--) evdev: Chicony USB 2.0 Camera: Vendor 0x4f2 Product 0xb5a7
[    18.250] (--) evdev: Chicony USB 2.0 Camera: Found keys
[    18.250] (II) evdev: Chicony USB 2.0 Camera: Configuring as keyboard
[    18.250] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-9/1-9:1.0/input/input19/event12"
[    18.250] (II) XINPUT: Adding extended input device "Chicony USB 2.0 Camera" (type: KEYBOARD, id 15)
[    18.250] (**) Option "xkb_rules" "evdev"
[    18.250] (**) Option "xkb_model" "pc105"
[    18.250] (**) Option "xkb_layout" "us"
[    18.250] (**) Option "xkb_variant" "intl"
[    18.250] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event13)
[    18.250] (II) No input driver specified, ignoring this device.
[    18.250] (II) This device may have been added with another device file.
[    18.250] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event14)
[    18.250] (II) No input driver specified, ignoring this device.
[    18.250] (II) This device may have been added with another device file.
[    18.250] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event15)
[    18.250] (II) No input driver specified, ignoring this device.
[    18.250] (II) This device may have been added with another device file.
[    18.251] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event16)
[    18.251] (II) No input driver specified, ignoring this device.
[    18.251] (II) This device may have been added with another device file.
[    18.251] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event17)
[    18.251] (II) No input driver specified, ignoring this device.
[    18.251] (II) This device may have been added with another device file.
[    18.251] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    18.251] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    18.251] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 42 paused 0
[    18.251] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    18.251] (**) AT Translated Set 2 keyboard: always reports core events
[    18.251] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    18.251] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    18.251] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    18.251] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    18.251] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    18.251] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 16)
[    18.251] (**) Option "xkb_rules" "evdev"
[    18.251] (**) Option "xkb_model" "pc105"
[    18.251] (**) Option "xkb_layout" "us"
[    18.251] (**) Option "xkb_variant" "intl"
[    18.252] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event9)
[    18.252] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    18.252] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchscreen catchall"
[    18.252] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    18.252] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    18.252] (II) LoadModule: "synaptics"
[    18.252] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    18.252] (II) Module synaptics: vendor="X.Org Foundation"
[    18.252] 	compiled for 1.18.1, module version = 1.8.2
[    18.252] 	Module class: X.Org XInput Driver
[    18.252] 	ABI class: X.Org XInput driver, version 22.1
[    18.253] (II) systemd-logind: got fd for /dev/input/event9 13:73 fd 43 paused 0
[    18.253] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    18.253] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.253] (**) Option "Device" "/dev/input/event9"
[    18.296] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1284 - 5656 (res 41)
[    18.296] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1128 - 4728 (res 61)
[    18.296] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    18.296] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    18.296] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    18.296] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    18.296] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    18.296] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    18.296] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input12/event9"
[    18.296] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 17)
[    18.296] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    18.296] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    18.296] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[    18.296] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    18.296] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    18.296] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    18.296] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    18.296] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    18.296] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse2)
[    18.296] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    18.326] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.327] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.327] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.327] (--) NVIDIA(GPU-0): 
[    18.327] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    18.327] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    18.327] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    18.327] (--) NVIDIA(GPU-0): 
[    18.327] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    18.327] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    18.327] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    18.327] (--) NVIDIA(GPU-0): 
[    18.327] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    18.327] (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
[    18.327] (--) NVIDIA(GPU-0): DFP-3: 1440.0 MHz maximum pixel clock
[    18.327] (--) NVIDIA(GPU-0): 
[    18.327] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    18.327] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    18.327] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    18.327] (--) NVIDIA(GPU-0): 
[    18.331] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.331] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.331] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.331] (--) NVIDIA(GPU-0): 
[    18.331] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    18.331] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    18.331] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    18.331] (--) NVIDIA(GPU-0): 
[    18.331] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    18.331] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    18.331] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    18.331] (--) NVIDIA(GPU-0): 
[    18.331] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    18.331] (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
[    18.331] (--) NVIDIA(GPU-0): DFP-3: 1440.0 MHz maximum pixel clock
[    18.331] (--) NVIDIA(GPU-0): 
[    18.331] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    18.331] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    18.331] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    18.331] (--) NVIDIA(GPU-0): 
[    18.331] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.331] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.331] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.331] (--) NVIDIA(GPU-0): 
[    18.332] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    18.332] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    18.332] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    18.332] (--) NVIDIA(GPU-0): 
[    18.332] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    18.332] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    18.332] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    18.332] (--) NVIDIA(GPU-0): 
[    18.332] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    18.332] (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
[    18.332] (--) NVIDIA(GPU-0): DFP-3: 1440.0 MHz maximum pixel clock
[    18.332] (--) NVIDIA(GPU-0): 
[    18.332] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    18.332] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    18.332] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    18.332] (--) NVIDIA(GPU-0): 
[    18.335] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.335] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.335] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.335] (--) NVIDIA(GPU-0): 
[    18.335] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    18.335] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    18.335] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    18.336] (--) NVIDIA(GPU-0): 
[    18.336] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    18.336] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    18.336] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    18.336] (--) NVIDIA(GPU-0): 
[    18.336] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    18.336] (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
[    18.336] (--) NVIDIA(GPU-0): DFP-3: 1440.0 MHz maximum pixel clock
[    18.336] (--) NVIDIA(GPU-0): 
[    18.336] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    18.336] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    18.336] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    18.336] (--) NVIDIA(GPU-0): 
[    18.912] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.912] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.912] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.912] (--) NVIDIA(GPU-0): 
[    18.912] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    18.912] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    18.912] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    18.912] (--) NVIDIA(GPU-0): 
[    18.912] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    18.912] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    18.912] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    18.912] (--) NVIDIA(GPU-0): 
[    18.912] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    18.912] (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
[    18.912] (--) NVIDIA(GPU-0): DFP-3: 1440.0 MHz maximum pixel clock
[    18.912] (--) NVIDIA(GPU-0): 
[    18.912] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    18.912] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    18.912] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    18.912] (--) NVIDIA(GPU-0): 
[    18.912] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    18.912] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    18.912] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    18.912] (--) NVIDIA(GPU-0): 
[    18.913] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    18.913] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    18.913] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    18.913] (--) NVIDIA(GPU-0): 
[    18.913] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    18.913] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    18.913] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    18.913] (--) NVIDIA(GPU-0): 
[    18.913] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    18.913] (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
[    18.913] (--) NVIDIA(GPU-0): DFP-3: 1440.0 MHz maximum pixel clock
[    18.913] (--) NVIDIA(GPU-0): 
[    18.913] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    18.913] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    18.913] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    18.913] (--) NVIDIA(GPU-0): 
[    18.913] (II) modeset(G0): EDID vendor "LGD", prod id 1135
[    18.913] (II) modeset(G0): Printing DDC gathered Modelines:
[    18.913] (II) modeset(G0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz eP)
[    18.913] (II) modeset(G0): Modeline "1920x1080"x0.0  110.90  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (53.3 kHz e)
[    20.675] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    20.675] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    20.675] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    20.675] (--) NVIDIA(GPU-0): 
[    20.675] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    20.675] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    20.675] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    20.675] (--) NVIDIA(GPU-0): 
[    20.675] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    20.675] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    20.675] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    20.675] (--) NVIDIA(GPU-0): 
[    20.675] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    20.675] (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
[    20.675] (--) NVIDIA(GPU-0): DFP-3: 1440.0 MHz maximum pixel clock
[    20.675] (--) NVIDIA(GPU-0): 
[    20.676] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    20.676] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    20.676] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    20.676] (--) NVIDIA(GPU-0): 
[    20.676] (--) NVIDIA(GPU-0): DFP-0: disconnected
[    20.676] (--) NVIDIA(GPU-0): DFP-0: Internal TMDS
[    20.676] (--) NVIDIA(GPU-0): DFP-0: 330.0 MHz maximum pixel clock
[    20.676] (--) NVIDIA(GPU-0): 
[    20.676] (--) NVIDIA(GPU-0): DFP-1: disconnected
[    20.676] (--) NVIDIA(GPU-0): DFP-1: Internal DisplayPort
[    20.676] (--) NVIDIA(GPU-0): DFP-1: 1440.0 MHz maximum pixel clock
[    20.676] (--) NVIDIA(GPU-0): 
[    20.676] (--) NVIDIA(GPU-0): DFP-2: disconnected
[    20.676] (--) NVIDIA(GPU-0): DFP-2: Internal TMDS
[    20.676] (--) NVIDIA(GPU-0): DFP-2: 330.0 MHz maximum pixel clock
[    20.676] (--) NVIDIA(GPU-0): 
[    20.676] (--) NVIDIA(GPU-0): DFP-3: disconnected
[    20.676] (--) NVIDIA(GPU-0): DFP-3: Internal DisplayPort
[    20.676] (--) NVIDIA(GPU-0): DFP-3: 1440.0 MHz maximum pixel clock
[    20.676] (--) NVIDIA(GPU-0): 
[    20.676] (--) NVIDIA(GPU-0): DFP-4: disconnected
[    20.676] (--) NVIDIA(GPU-0): DFP-4: Internal TMDS
[    20.676] (--) NVIDIA(GPU-0): DFP-4: 330.0 MHz maximum pixel clock
[    20.676] (--) NVIDIA(GPU-0): 
[    20.677] (II) modeset(G0): EDID vendor "LGD", prod id 1135
[    20.677] (II) modeset(G0): Printing DDC gathered Modelines:
[    20.677] (II) modeset(G0): Modeline "1920x1080"x0.0  138.70  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (66.7 kHz eP)
[    20.677] (II) modeset(G0): Modeline "1920x1080"x0.0  110.90  1920 1968 2000 2080  1080 1083 1088 1111 +hsync -vsync (53.3 kHz e)
[   658.745] (II) systemd-logind: got pause for 13:70
[   658.745] (II) systemd-logind: got pause for 13:71
[   658.745] (II) systemd-logind: got pause for 13:72
[   658.745] (II) systemd-logind: got pause for 13:76
[   658.745] (II) systemd-logind: got pause for 13:64
[   658.745] (II) systemd-logind: got pause for 13:67
[   658.745] (II) systemd-logind: got pause for 13:69
[   658.745] (II) systemd-logind: got pause for 13:65
[   658.745] (II) systemd-logind: got pause for 13:75
[   658.745] (II) systemd-logind: got pause for 13:68
[   658.745] (II) systemd-logind: got pause for 13:74
[   658.745] (II) systemd-logind: got pause for 226:1
[   658.745] (II) systemd-logind: got pause for 13:73



```

---

