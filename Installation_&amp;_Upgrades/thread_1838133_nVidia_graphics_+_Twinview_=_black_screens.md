---
title: "nVidia graphics + Twinview = black screens"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by Kentucky88 on 2011-09-03
I have an nVidia Gefore 210 card in my system which was working fine for several months.  When I enable Twinview to drive my second monitor, my main screen goes black and I have to restart the computer by hitting the power button (TwinView used to work fine on same hardware).  I've tried everything that I can think of in order to resolve this issue aside from hardware changes.  I even did a reinstall of Ubuntu 11.04 (replaced system files / left home directory), but that has not solved the problem.  I have additional drivers configured to use nvidia_current. Below is my xorg log from when the system froze.  Why is it trying to load the "nv" module?  Please let me know if you see something wrong.

[PHP]
[    16.876] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    16.876] X Protocol Version 11, Revision 0
[    16.876] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    16.876] Current Operating System: Linux boxer-System-Product-Name 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64
[    16.876] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=75c9f43c-1f90-465c-a591-299c8950f562 ro quiet splash vt.handoff=7
[    16.876] Build Date: 11 August 2011  03:43:05PM
[    16.876] xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
[    16.876] Current version of pixman: 0.20.2
[    16.876]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    16.876] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    16.876] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Sep  2 23:48:51 2011
[    16.889] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    16.889] (==) No Layout section.  Using the first Screen section.
[    16.889] (==) No screen section available. Using defaults.
[    16.889] (**) |-->Screen "Default Screen Section" (0)
[    16.889] (**) |   |-->Monitor "<default monitor>"
[    16.889] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    16.889] (==) Automatically adding devices
[    16.889] (==) Automatically enabling devices
[    16.889] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    16.889]     Entry deleted from font path.
[    16.889] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    16.889]     Entry deleted from font path.
[    16.889] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    16.890]     Entry deleted from font path.
[    16.890] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    16.890]     Entry deleted from font path.
[    16.890] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    16.890]     Entry deleted from font path.
[    16.890] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    16.890] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    16.890] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    16.890] (II) Loader magic: 0x7e17e0
[    16.890] (II) Module ABI versions:
[    16.890]     X.Org ANSI C Emulation: 0.4
[    16.890]     X.Org Video Driver: 10.0
[    16.890]     X.Org XInput driver : 12.3
[    16.890]     X.Org Server Extension : 5.0
[    16.890] (--) PCI:*(0:4:0:0) 10de:0a65:1462:2401 rev 162, Mem @ 0xfa000000/16777216, 0xd0000000/268435456, 0xce000000/33554432, I/O @ 0x0000cc00/128, BIOS @ 0x????????/524288
[    16.890] (II) Open ACPI successful (/var/run/acpid.socket)
[    16.890] (II) LoadModule: "extmod"
[    16.895] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    16.895] (II) Module extmod: vendor="X.Org Foundation"
[    16.895]     compiled for 1.10.1, module version = 1.0.0
[    16.895]     Module class: X.Org Server Extension
[    16.895]     ABI class: X.Org Server Extension, version 5.0
[    16.895] (II) Loading extension MIT-SCREEN-SAVER
[    16.895] (II) Loading extension XFree86-VidModeExtension
[    16.895] (II) Loading extension XFree86-DGA
[    16.895] (II) Loading extension DPMS
[    16.895] (II) Loading extension XVideo
[    16.895] (II) Loading extension XVideo-MotionCompensation
[    16.895] (II) Loading extension X-Resource
[    16.895] (II) LoadModule: "dbe"
[    16.895] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    16.895] (II) Module dbe: vendor="X.Org Foundation"
[    16.895]     compiled for 1.10.1, module version = 1.0.0
[    16.895]     Module class: X.Org Server Extension
[    16.895]     ABI class: X.Org Server Extension, version 5.0
[    16.895] (II) Loading extension DOUBLE-BUFFER
[    16.895] (II) LoadModule: "glx"
[    16.895] (II) Loading /usr/lib/xorg/extra-modules/libglx.so
[    16.899] (II) Module glx: vendor="NVIDIA Corporation"
[    16.899]     compiled for 4.0.2, module version = 1.0.0
[    16.899]     Module class: X.Org Server Extension
[    16.899] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:10:15 PDT 2011
[    16.899] (II) Loading extension GLX
[    16.899] (II) LoadModule: "record"
[    16.900] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    16.900] (II) Module record: vendor="X.Org Foundation"
[    16.900]     compiled for 1.10.1, module version = 1.13.0
[    16.900]     Module class: X.Org Server Extension
[    16.900]     ABI class: X.Org Server Extension, version 5.0
[    16.900] (II) Loading extension RECORD
[    16.900] (II) LoadModule: "dri"
[    16.900] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    16.900] (II) Module dri: vendor="X.Org Foundation"
[    16.900]     compiled for 1.10.1, module version = 1.0.0
[    16.900]     ABI class: X.Org Server Extension, version 5.0
[    16.900] (II) Loading extension XFree86-DRI
[    16.900] (II) LoadModule: "dri2"
[    16.900] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    16.900] (II) Module dri2: vendor="X.Org Foundation"
[    16.900]     compiled for 1.10.1, module version = 1.2.0
[    16.900]     ABI class: X.Org Server Extension, version 5.0
[    16.900] (II) Loading extension DRI2
[    16.900] (==) Matched nvidia as autoconfigured driver 0
[    16.900] (==) Matched nouveau as autoconfigured driver 1
[    16.900] (==) Matched nv as autoconfigured driver 2
[    16.900] (==) Matched vesa as autoconfigured driver 3
[    16.900] (==) Matched fbdev as autoconfigured driver 4
[    16.900] (==) Assigned the driver to the xf86ConfigLayout
[    16.900] (II) LoadModule: "nvidia"
[    16.900] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    16.900] (II) Module nvidia: vendor="NVIDIA Corporation"
[    16.900]     compiled for 4.0.2, module version = 1.0.0
[    16.900]     Module class: X.Org Video Driver
[    16.900] (II) LoadModule: "nouveau"
[    16.901] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    16.901] (II) Module nouveau: vendor="X.Org Foundation"
[    16.901]     compiled for 1.10.0, module version = 0.0.16
[    16.901]     Module class: X.Org Video Driver
[    16.901]     ABI class: X.Org Video Driver, version 10.0
[    16.901] (II) LoadModule: "nv"
[    16.901] (WW) Warning, couldn't open module nv
[    16.901] (II) UnloadModule: "nv"
[    16.901] (II) Unloading nv
[    16.901] (EE) Failed to load module "nv" (module does not exist, 0)
[    16.901] (II) LoadModule: "vesa"
[    16.901] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    16.901] (II) Module vesa: vendor="X.Org Foundation"
[    16.901]     compiled for 1.10.0, module version = 2.3.0
[    16.901]     Module class: X.Org Video Driver
[    16.901]     ABI class: X.Org Video Driver, version 10.0
[    16.901] (II) LoadModule: "fbdev"
[    16.901] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    16.901] (II) Module fbdev: vendor="X.Org Foundation"
[    16.901]     compiled for 1.10.0, module version = 0.4.2
[    16.901]     ABI class: X.Org Video Driver, version 10.0
[    16.901] (II) NVIDIA dlloader X Driver  270.41.06  Mon Apr 18 14:55:25 PDT 2011
[    16.901] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    16.901] (II) NOUVEAU driver Date:   Fri Jan 7 13:33:36 2011 +1000
[    16.901] (II) NOUVEAU driver for NVIDIA chipset families :
[    16.901]     RIVA TNT    (NV04)
[    16.901]     RIVA TNT2   (NV05)
[    16.901]     GeForce 256 (NV10)
[    16.901]     GeForce 2   (NV11, NV15)
[    16.901]     GeForce 4MX (NV17, NV18)
[    16.901]     GeForce 3   (NV20)
[    16.901]     GeForce 4Ti (NV25, NV28)
[    16.901]     GeForce FX  (NV3x)
[    16.901]     GeForce 6   (NV4x)
[    16.901]     GeForce 7   (G7x)
[    16.901]     GeForce 8   (G8x)
[    16.901] (II) VESA: driver for VESA chipsets: vesa
[    16.902] (II) FBDEV: driver for framebuffer: fbdev
[    16.902] (++) using VT number 7

[    16.902] (II) Loading sub module "fb"
[    16.902] (II) LoadModule: "fb"
[    16.902] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.902] (II) Module fb: vendor="X.Org Foundation"
[    16.902]     compiled for 1.10.1, module version = 1.0.0
[    16.902]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.902] (II) Loading sub module "wfb"
[    16.902] (II) LoadModule: "wfb"
[    16.902] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.902] (II) Module wfb: vendor="X.Org Foundation"
[    16.902]     compiled for 1.10.1, module version = 1.0.0
[    16.902]     ABI class: X.Org ANSI C Emulation, version 0.4
[    16.902] (II) Loading sub module "ramdac"
[    16.902] (II) LoadModule: "ramdac"
[    16.902] (II) Module "ramdac" already built-in
[    16.902] (II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
[    16.902] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    16.902] (II) Loading /usr/lib/xorg/modules/libfb.so
[    16.902] (WW) Falling back to old probe method for vesa
[    16.902] (WW) Falling back to old probe method for fbdev
[    16.902] (II) Loading sub module "fbdevhw"
[    16.902] (II) LoadModule: "fbdevhw"
[    16.902] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    16.902] (II) Module fbdevhw: vendor="X.Org Foundation"
[    16.902]     compiled for 1.10.1, module version = 0.0.2
[    16.902]     ABI class: X.Org Video Driver, version 10.0
[    16.902] (II) NVIDIA(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    16.902] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    16.902] (==) NVIDIA(0): RGB weight 888
[    16.902] (==) NVIDIA(0): Default visual is TrueColor
[    16.902] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    17.519] (II) NVIDIA(GPU-0): Display (Samsung SyncMaster (CRT-1)) does not support NVIDIA
[    17.519] (II) NVIDIA(GPU-0):     3D Vision stereo.
[    17.552] (II) NVIDIA(GPU-0): Display (HP 2509 (DFP-0)) does not support NVIDIA 3D Vision
[    17.552] (II) NVIDIA(GPU-0):     stereo.
[    17.553] (II) NVIDIA(0): NVIDIA GPU GeForce 210 (GT218) at PCI:4:0:0 (GPU-0)
[    17.553] (--) NVIDIA(0): Memory: 524288 kBytes
[    17.553] (--) NVIDIA(0): VideoBIOS: 70.18.7a.00.00
[    17.553] (II) NVIDIA(0): Detected PCI Express Link width: 16X
[    17.553] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    17.553] (--) NVIDIA(0): Connected display device(s) on GeForce 210 at PCI:4:0:0
[    17.553] (--) NVIDIA(0):     Samsung SyncMaster (CRT-1)
[    17.553] (--) NVIDIA(0):     HP 2509 (DFP-0)
[    17.553] (--) NVIDIA(0): Samsung SyncMaster (CRT-1): 400.0 MHz maximum pixel clock
[    17.553] (--) NVIDIA(0): HP 2509 (DFP-0): 330.0 MHz maximum pixel clock
[    17.553] (--) NVIDIA(0): HP 2509 (DFP-0): Internal Dual Link TMDS
[    17.629] (II) NVIDIA(0): Assigned Display Device: DFP-0
[    17.629] (==) NVIDIA(0): 
[    17.632] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    17.632] (==) NVIDIA(0):     will be used as the requested mode.
[    17.632] (==) NVIDIA(0): 
[    17.632] (II) NVIDIA(0): Validated modes:
[    17.632] (II) NVIDIA(0):     "nvidia-auto-select"
[    17.632] (II) NVIDIA(0): Virtual screen size determined to be 1920 x 1080
[    17.671] (--) NVIDIA(0): DPI set to (88, 88); computed from "UseEdidDpi" X config
[    17.671] (--) NVIDIA(0):     option
[    17.671] (II) UnloadModule: "nouveau"
[    17.671] (II) Unloading nouveau
[    17.672] (II) UnloadModule: "vesa"
[    17.672] (II) Unloading vesa
[    17.672] (II) UnloadModule: "fbdev"
[    17.672] (II) Unloading fbdev
[    17.672] (II) UnloadModule: "fbdevhw"
[    17.672] (II) Unloading fbdevhw
[    17.672] (--) Depth 24 pixmap format is 32 bpp
[    17.672] (II) NVIDIA: Using 768.00 MB of virtual memory for indirect memory access.
[    17.680] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    17.821] (II) Loading extension NV-GLX
[    17.863] (==) NVIDIA(0): Disabling shared memory pixmaps
[    17.863] (==) NVIDIA(0): Backing store disabled
[    17.863] (==) NVIDIA(0): Silken mouse enabled
[    17.864] (==) NVIDIA(0): DPMS enabled
[    17.864] (II) Loading extension NV-CONTROL
[    17.864] (II) Loading extension XINERAMA
[    17.864] (II) Loading sub module "dri2"
[    17.864] (II) LoadModule: "dri2"
[    17.864] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    17.864] (II) Module dri2: vendor="X.Org Foundation"
[    17.864]     compiled for 1.10.1, module version = 1.2.0
[    17.864]     ABI class: X.Org Server Extension, version 5.0
[    17.864] (II) NVIDIA(0): [DRI2] Setup complete
[    17.864] (==) RandR enabled
[    17.864] (II) Initializing built-in extension Generic Event Extension
[    17.864] (II) Initializing built-in extension SHAPE
[    17.864] (II) Initializing built-in extension MIT-SHM
[    17.864] (II) Initializing built-in extension XInputExtension
[    17.864] (II) Initializing built-in extension XTEST
[    17.864] (II) Initializing built-in extension BIG-REQUESTS
[    17.864] (II) Initializing built-in extension SYNC
[    17.864] (II) Initializing built-in extension XKEYBOARD
[    17.864] (II) Initializing built-in extension XC-MISC
[    17.864] (II) Initializing built-in extension SECURITY
[    17.864] (II) Initializing built-in extension XINERAMA
[    17.864] (II) Initializing built-in extension XFIXES
[    17.864] (II) Initializing built-in extension RENDER
[    17.864] (II) Initializing built-in extension RANDR
[    17.864] (II) Initializing built-in extension COMPOSITE
[    17.864] (II) Initializing built-in extension DAMAGE
[    17.864] (II) Initializing built-in extension GESTURE
[    17.865] (II) Initializing extension GLX
[    17.881] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    17.885] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    17.885] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.885] (II) LoadModule: "evdev"
[    17.886] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.886] (II) Module evdev: vendor="X.Org Foundation"
[    17.886]     compiled for 1.10.0.902, module version = 2.6.0
[    17.886]     Module class: X.Org XInput Driver
[    17.886]     ABI class: X.Org XInput driver, version 12.3
[    17.886] (II) Using input driver 'evdev' for 'Power Button'
[    17.886] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.886] (**) Power Button: always reports core events
[    17.886] (**) Power Button: Device: "/dev/input/event1"
[    17.950] (--) Power Button: Found keys
[    17.950] (II) Power Button: Configuring as keyboard
[    17.950] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    17.950] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    17.950] (**) Option "xkb_rules" "evdev"
[    17.950] (**) Option "xkb_model" "pc105"
[    17.950] (**) Option "xkb_layout" "us"
[    17.952] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    17.952] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    17.952] (II) Using input driver 'evdev' for 'Power Button'
[    17.952] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    17.952] (**) Power Button: always reports core events
[    17.952] (**) Power Button: Device: "/dev/input/event0"
[    18.030] (--) Power Button: Found keys
[    18.030] (II) Power Button: Configuring as keyboard
[    18.030] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    18.030] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    18.030] (**) Option "xkb_rules" "evdev"
[    18.030] (**) Option "xkb_model" "pc105"
[    18.030] (**) Option "xkb_layout" "us"
[    18.032] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Mouse® 1.0A (/dev/input/event2)
[    18.032] (**) Microsoft Microsoft Wireless Optical Mouse® 1.0A: Applying InputClass "evdev pointer catchall"
[    18.032] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wireless Optical Mouse® 1.0A'
[    18.032] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.032] (**) Microsoft Microsoft Wireless Optical Mouse® 1.0A: always reports core events
[    18.032] (**) Microsoft Microsoft Wireless Optical Mouse® 1.0A: Device: "/dev/input/event2"
[    18.110] (--) Microsoft Microsoft Wireless Optical Mouse® 1.0A: Found 9 mouse buttons
[    18.110] (--) Microsoft Microsoft Wireless Optical Mouse® 1.0A: Found scroll wheel(s)
[    18.110] (--) Microsoft Microsoft Wireless Optical Mouse® 1.0A: Found relative axes
[    18.110] (--) Microsoft Microsoft Wireless Optical Mouse® 1.0A: Found x and y relative axes
[    18.110] (II) Microsoft Microsoft Wireless Optical Mouse® 1.0A: Configuring as mouse
[    18.110] (II) Microsoft Microsoft Wireless Optical Mouse® 1.0A: Adding scrollwheel support
[    18.110] (**) Microsoft Microsoft Wireless Optical Mouse® 1.0A: YAxisMapping: buttons 4 and 5
[    18.110] (**) Microsoft Microsoft Wireless Optical Mouse® 1.0A: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    18.110] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0/usb9/9-3/9-3:1.0/input/input2/event2"
[    18.110] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wireless Optical Mouse® 1.0A" (type: MOUSE)
[    18.110] (II) Microsoft Microsoft Wireless Optical Mouse® 1.0A: initialized for relative axes.
[    18.110] (**) Microsoft Microsoft Wireless Optical Mouse® 1.0A: (accel) keeping acceleration scheme 1
[    18.110] (**) Microsoft Microsoft Wireless Optical Mouse® 1.0A: (accel) acceleration profile 0
[    18.110] (**) Microsoft Microsoft Wireless Optical Mouse® 1.0A: (accel) acceleration factor: 2.000
[    18.110] (**) Microsoft Microsoft Wireless Optical Mouse® 1.0A: (accel) acceleration threshold: 4
[    18.110] (II) config/udev: Adding input device Microsoft Microsoft Wireless Optical Mouse® 1.0A (/dev/input/mouse0)
[    18.110] (II) No input driver/identifier specified (ignoring)
[    18.111] (II) config/udev: Adding input device HID 045e:000b (/dev/input/event3)
[    18.111] (**) HID 045e:000b: Applying InputClass "evdev keyboard catchall"
[    18.111] (II) Using input driver 'evdev' for 'HID 045e:000b'
[    18.111] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    18.111] (**) HID 045e:000b: always reports core events
[    18.111] (**) HID 045e:000b: Device: "/dev/input/event3"
[    18.150] (--) HID 045e:000b: Found keys
[    18.150] (II) HID 045e:000b: Configuring as keyboard
[    18.150] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0/usb9/9-4/9-4:1.0/input/input3/event3"
[    18.150] (II) XINPUT: Adding extended input device "HID 045e:000b" (type: KEYBOARD)
[    18.150] (**) Option "xkb_rules" "evdev"
[    18.150] (**) Option "xkb_model" "pc105"
[    18.150] (**) Option "xkb_layout" "us"
[    18.151] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event4)
[    18.151] (II) No input driver/identifier specified (ignoring)
[    83.388] (II) NVIDIA(0): Setting mode
[    83.388] (II) NVIDIA(0):     "CRT-1:nvidia-auto-select@1680x1050+1920+0,DFP-0:nvidia-auto-select@1920x1080+0+0"
[    94.391] (EE) NVIDIA(0): WAIT: (E, 0, 0x857d, 0)
[/PHP]

---

### Post by Kentucky88 on 2011-09-03
I still have the problem described above, but I did some more experimenting and found that if I switch drivers from the Nvidia closed source to the "Experimental 3D support.." (which I think is nouveau project drivers), I can get TwinView working with no major problems...except that the 3D performance sucks.  I can't even get OpenGL working with it.

What are the config files related to the graphical system configuration?  I know that /etc/X11/xorg.conf is one piece of the puzzle...where else should I check?  For example, the xorg.log file that I posted above states that [COLOR=#000000][COLOR=#0000BB]

The directory [/COLOR][COLOR=#DD0000]"/usr/share/fonts/X11/cyrillic" [/COLOR][COLOR=#0000BB]does not exist

What file(s) specifies that path?
[/COLOR][/COLOR]

---

