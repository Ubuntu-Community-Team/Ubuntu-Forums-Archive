---
title: "Blank Screen after login Intel i915 on 13.10."
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by Polar Humenn on 2013-11-09
I just built this box with a Haswell with 4600 graphics and installed Kubuntu 13.10 right off the bat running Kernel 3.11.0-12-generic. The only way I can get a visible desktop is to turn off KMS setting GRUB_CMDLINE_LINUX="nomodeset" in /etc/default/grub, update-grub, and reboot. However, this is not optimal, since I xrandr will not recognize my other HDMI ports. I figure the i915 driver is missing the boat or a modeline on the monitor or something. I do not have an "/etc/X11/xorg.conf" file. 

I'm running lightdm. In both scenarios, one booted with "nomodeset" and one without, I get the initial login screen and the KDE initialization screen starts. With "nomodeset", about halfway through the screen flicks off for a second, but comes right back, and I have my kde session visible. If I  boot it without "nomodeset", the screen flicks off at the point, but never comes back, the DVI signal goes dead, and my monitor sleeps. However, the desktop environment is coming up. I hear the tone, etc.

When I <ctrl-alt>F1 my monitor wakes up and I log on. I can see all the kde processes running as if it were a normal session. It seems that the DVI signal just dropped, or it cannot find a proper resolution. I've got an ENVISION 20" widescreen monitor that has 1680x1050 Max Resolution.

I've upgraded to Kernel3.11.0-13-generic, but still the same problem. I'll post xrandr -q and Xorg.0.log below. And those were collected with KMS enabled, i.e. booted without "nomodeset". On and from lscpi:
```
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)

```

Any insight? Running with "nomodeset" is getting me by, but my xrandr only shows one "default" video output so I won't be able to use 2 or 3 monitors.
 
Cheers,
-Polar

```
[INDENT]# DISPLAY=:0 xrandr -q
Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 32767 x 32767[/INDENT]
[INDENT]VGA1 disconnected (normal left inverted right x axis y axis)[/INDENT]
[INDENT]DP1 disconnected (normal left inverted right x axis y axis)[/INDENT]
[INDENT]HDMI1 connected (normal left inverted right x axis y axis)[/INDENT]
[INDENT]   1680x1050      60.0 +[/INDENT]
[INDENT]   1280x1024      75.0     60.0  [/INDENT]
[INDENT]   1440x900       75.0     59.9  [/INDENT]
[INDENT]   1280x960       60.0  [/INDENT]
[INDENT]   1152x864       75.0  [/INDENT]
[INDENT]   1024x768       75.1     70.1     60.0  [/INDENT]
[INDENT]   832x624        74.6  [/INDENT]
[INDENT]   800x600        72.2     75.0     60.3     56.2  [/INDENT]
[INDENT]   640x480        75.0     72.8     66.7     60.0  [/INDENT]
[INDENT]   720x400        70.1  [/INDENT]
[INDENT]DP2 disconnected (normal left inverted right x axis y axis)[/INDENT]
[INDENT]HDMI2 disconnected (normal left inverted right x axis y axis)[/INDENT]
[INDENT]DP3 disconnected (normal left inverted right x axis y axis)[/INDENT]
[INDENT]HDMI3 disconnected (normal left inverted right x axis y axis)[/INDENT]
[INDENT]VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/INDENT]

```
The Xorg.0.log is:
```

[     3.893] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[     3.893] X Protocol Version 11, Revision 0
[     3.893] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[     3.893] Current Operating System: Linux adiron 3.11.0-13-generic #20-Ubuntu SMP Wed Oct 23 07:38:26 UTC 2013 x86_64
[     3.893] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-13-generic root=UUID=d2a987ff-b5d8-442a-9e36-5b74942348de ro splash vt.handoff=7
[     3.893] Build Date: 15 October 2013  09:23:37AM
[     3.893] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see http://www.ubuntu.com/support) 
[     3.893] Current version of pixman: 0.30.2
[     3.893]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[     3.893] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.893] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Nov  9 13:42:44 2013
[     3.893] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.893] (==) No Layout section.  Using the first Screen section.
[     3.893] (==) No screen section available. Using defaults.
[     3.893] (**) |-->Screen "Default Screen Section" (0)
[     3.893] (**) |   |-->Monitor "<default monitor>"
[     3.893] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[     3.893] (==) Automatically adding devices
[     3.893] (==) Automatically enabling devices
[     3.893] (==) Automatically adding GPU devices
[     3.893] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.893]    Entry deleted from font path.
[     3.893] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.893]    Entry deleted from font path.
[     3.893] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.893]    Entry deleted from font path.
[     3.893] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.893]    Entry deleted from font path.
[     3.893] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.893]    Entry deleted from font path.
[     3.893] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[     3.893] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.893] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.893] (II) Loader magic: 0x7f01f4fe4d20
[     3.893] (II) Module ABI versions:
[     3.893]    X.Org ANSI C Emulation: 0.4
[     3.893]    X.Org Video Driver: 14.1
[     3.893]    X.Org XInput driver : 19.1
[     3.893]    X.Org Server Extension : 7.0
[     3.893] (II) xfree86: Adding drm device (/dev/dri/card0)
[     3.894] (--) PCI:*(0:0:2:0) 8086:0412:1458:d000 rev 6, Mem @ 0xf0000000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[     3.894] (II) Open ACPI successful (/var/run/acpid.socket)
[     3.894] Initializing built-in extension Generic Event Extension
[     3.894] Initializing built-in extension SHAPE
[     3.894] Initializing built-in extension MIT-SHM
[     3.894] Initializing built-in extension XInputExtension
[     3.894] Initializing built-in extension XTEST
[     3.894] Initializing built-in extension BIG-REQUESTS
[     3.894] Initializing built-in extension SYNC
[     3.894] Initializing built-in extension XKEYBOARD
[     3.894] Initializing built-in extension XC-MISC
[     3.894] Initializing built-in extension SECURITY
[     3.894] Initializing built-in extension XINERAMA
[     3.894] Initializing built-in extension XFIXES
[     3.894] Initializing built-in extension RENDER
[     3.894] Initializing built-in extension RANDR
[     3.894] Initializing built-in extension COMPOSITE
[     3.894] Initializing built-in extension DAMAGE
[     3.894] Initializing built-in extension MIT-SCREEN-SAVER
[     3.894] Initializing built-in extension DOUBLE-BUFFER
[     3.894] Initializing built-in extension RECORD
[     3.894] Initializing built-in extension DPMS
[     3.894] Initializing built-in extension X-Resource
[     3.894] Initializing built-in extension XVideo
[     3.894] Initializing built-in extension XVideo-MotionCompensation
[     3.894] Initializing built-in extension SELinux
[     3.894] Initializing built-in extension XFree86-VidModeExtension
[     3.894] Initializing built-in extension XFree86-DGA
[     3.894] Initializing built-in extension XFree86-DRI
[     3.894] Initializing built-in extension DRI2
[     3.894] (II) "glx" will be loaded by default.
[     3.894] (WW) "xmir" is not to be loaded by default. Skipping.
[     3.894] (II) LoadModule: "dri2"
[     3.894] (II) Module "dri2" already built-in
[     3.894] (II) LoadModule: "glamoregl"
[     3.895] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[     3.905] (II) Module glamoregl: vendor="X.Org Foundation"
[     3.905]    compiled for 1.14.3, module version = 0.5.1
[     3.905]    ABI class: X.Org ANSI C Emulation, version 0.4
[     3.905] (II) LoadModule: "glx"
[     3.905] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.905] (II) Module glx: vendor="X.Org Foundation"
[     3.905]    compiled for 1.14.3, module version = 1.0.0
[     3.905]    ABI class: X.Org Server Extension, version 7.0
[     3.905] (==) AIGLX enabled
[     3.905] Loading extension GLX
[     3.905] (==) Matched intel as autoconfigured driver 0
[     3.905] (==) Matched intel as autoconfigured driver 1
[     3.905] (==) Matched vesa as autoconfigured driver 2
[     3.905] (==) Matched modesetting as autoconfigured driver 3
[     3.905] (==) Matched fbdev as autoconfigured driver 4
[     3.905] (==) Assigned the driver to the xf86ConfigLayout
[     3.905] (II) LoadModule: "intel"
[     3.905] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     3.906] (II) Module intel: vendor="X.Org Foundation"
[     3.906]    compiled for 1.14.3, module version = 2.99.904
[     3.906]    Module class: X.Org Video Driver
[     3.906]    ABI class: X.Org Video Driver, version 14.1
[     3.906] (II) LoadModule: "vesa"
[     3.906] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.906] (II) Module vesa: vendor="X.Org Foundation"
[     3.906]    compiled for 1.14.1, module version = 2.3.2
[     3.906]    Module class: X.Org Video Driver
[     3.906]    ABI class: X.Org Video Driver, version 14.1
[     3.906] (II) LoadModule: "modesetting"
[     3.906] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     3.906] (II) Module modesetting: vendor="X.Org Foundation"
[     3.906]    compiled for 1.14.1, module version = 0.8.0
[     3.906]    Module class: X.Org Video Driver
[     3.906]    ABI class: X.Org Video Driver, version 14.1
[     3.906] (II) LoadModule: "fbdev"
[     3.906] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.906] (II) Module fbdev: vendor="X.Org Foundation"
[     3.906]    compiled for 1.14.1, module version = 0.4.3
[     3.906]    Module class: X.Org Video Driver
[     3.906]    ABI class: X.Org Video Driver, version 14.1
[     3.906] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
        HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
        HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
        HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
        HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[     3.907] (II) VESA: driver for VESA chipsets: vesa
[     3.907] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     3.907] (II) FBDEV: driver for framebuffer: fbdev
[     3.907] (++) using VT number 7


[     3.907] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.904-0ubuntu2 (Timo Aaltonen <tjaalton@ubuntu.com>)
[     3.908] (WW) Falling back to old probe method for vesa
[     3.908] (WW) Falling back to old probe method for modesetting
[     3.908] (WW) Falling back to old probe method for fbdev
[     3.908] (II) Loading sub module "fbdevhw"
[     3.908] (II) LoadModule: "fbdevhw"
[     3.908] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     3.908] (II) Module fbdevhw: vendor="X.Org Foundation"
[     3.908]    compiled for 1.14.3, module version = 0.0.2
[     3.908]    ABI class: X.Org Video Driver, version 14.1
[     3.909] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[     3.909] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     3.909] (==) intel(0): RGB weight 888
[     3.909] (==) intel(0): Default visual is TrueColor
[     3.909] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[     3.909] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[     3.909] (**) intel(0): Framebuffer tiled
[     3.909] (**) intel(0): Pixmaps tiled
[     3.909] (**) intel(0): "Tear free" disabled
[     3.909] (**) intel(0): Forcing per-crtc-pixmaps? no
[     3.909] (II) intel(0): Output VGA1 has no monitor section
[     3.909] (II) intel(0): Output DP1 has no monitor section
[     3.909] (II) intel(0): Output HDMI1 has no monitor section
[     3.909] (II) intel(0): Output DP2 has no monitor section
[     3.909] (II) intel(0): Output HDMI2 has no monitor section
[     3.909] (II) intel(0): Output DP3 has no monitor section
[     3.909] (II) intel(0): Output HDMI3 has no monitor section
[     3.909] (II) intel(0): Output VIRTUAL1 has no monitor section
[     3.909] (--) intel(0): Output HDMI1 using initial mode 1680x1050 on pipe 0
[     3.909] (==) intel(0): DPI set to (96, 96)
[     3.909] (II) Loading sub module "dri2"
[     3.909] (II) LoadModule: "dri2"
[     3.909] (II) Module "dri2" already built-in
[     3.909] (II) UnloadModule: "vesa"
[     3.909] (II) Unloading vesa
[     3.909] (II) UnloadModule: "modesetting"
[     3.909] (II) Unloading modesetting
[     3.909] (II) UnloadModule: "fbdev"
[     3.909] (II) Unloading fbdev
[     3.909] (II) UnloadSubModule: "fbdevhw"
[     3.909] (II) Unloading fbdevhw
[     3.909] (==) Depth 24 pixmap format is 32 bpp
[     3.910] (II) intel(0): SNA initialized with Haswell (gen7.5, gt2) backend
[     3.910] (==) intel(0): Backing store disabled
[     3.910] (==) intel(0): Silken mouse enabled
[     3.911] (II) intel(0): HW Cursor enabled
[     3.911] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     3.911] (==) intel(0): DPMS enabled
[     3.911] (II) intel(0): [DRI2] Setup complete
[     3.911] (II) intel(0): [DRI2]   DRI driver: i965
[     3.911] (II) intel(0): direct rendering: DRI2 Enabled
[     3.911] (==) intel(0): hotplug detection: "enabled"
[     3.911] (--) RandR disabled
[     3.914] (II) SELinux: Disabled on system
[     3.927] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     3.927] (II) AIGLX: enabled GLX_INTEL_swap_event
[     3.927] (II) AIGLX: enabled GLX_ARB_create_context
[     3.927] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     3.927] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     3.927] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     3.927] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     3.927] (II) AIGLX: Loaded and initialized i965
[     3.927] (II) GLX: Initialized DRI2 GL provider for screen 0
[     3.929] (II) intel(0): switch to mode 1680x1050@60.0 on pipe 0 using HDMI1, position (0, 0), rotation normal
[     3.944] (II) intel(0): Setting screen physical size to 444 x 277
[     3.948] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.950] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     3.950] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.950] (II) LoadModule: "evdev"
[     3.951] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.951] (II) Module evdev: vendor="X.Org Foundation"
[     3.951]    compiled for 1.14.1, module version = 2.7.3
[     3.951]    Module class: X.Org XInput Driver
[     3.951]    ABI class: X.Org XInput driver, version 19.1
[     3.951] (II) Using input driver 'evdev' for 'Power Button'
[     3.951] (**) Power Button: always reports core events
[     3.951] (**) evdev: Power Button: Device: "/dev/input/event1"
[     3.951] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.951] (--) evdev: Power Button: Found keys
[     3.951] (II) evdev: Power Button: Configuring as keyboard
[     3.951] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     3.951] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.951] (**) Option "xkb_rules" "evdev"
[     3.951] (**) Option "xkb_model" "pc105"
[     3.951] (**) Option "xkb_layout" "us"
[     3.951] (II) config/udev: Adding input device Video Bus (/dev/input/event4)
[     3.951] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     3.951] (II) Using input driver 'evdev' for 'Video Bus'
[     3.951] (**) Video Bus: always reports core events
[     3.951] (**) evdev: Video Bus: Device: "/dev/input/event4"
[     3.951] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     3.951] (--) evdev: Video Bus: Found keys
[     3.951] (II) evdev: Video Bus: Configuring as keyboard
[     3.951] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input4/event4"
[     3.951] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     3.951] (**) Option "xkb_rules" "evdev"
[     3.951] (**) Option "xkb_model" "pc105"
[     3.951] (**) Option "xkb_layout" "us"
[     3.952] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.952] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.952] (II) Using input driver 'evdev' for 'Power Button'
[     3.952] (**) Power Button: always reports core events
[     3.952] (**) evdev: Power Button: Device: "/dev/input/event0"
[     3.952] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.952] (--) evdev: Power Button: Found keys
[     3.952] (II) evdev: Power Button: Configuring as keyboard
[     3.952] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     3.952] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     3.952] (**) Option "xkb_rules" "evdev"
[     3.952] (**) Option "xkb_model" "pc105"
[     3.952] (**) Option "xkb_layout" "us"
[     3.952] (II) config/udev: Adding drm device (/dev/dri/card0)
[     3.952] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     3.952] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=8 (/dev/input/event7)
[     3.952] (II) No input driver specified, ignoring this device.
[     3.952] (II) This device may have been added with another device file.
[     3.952] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=7 (/dev/input/event8)
[     3.952] (II) No input driver specified, ignoring this device.
[     3.952] (II) This device may have been added with another device file.
[     3.952] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=3 (/dev/input/event9)
[     3.952] (II) No input driver specified, ignoring this device.
[     3.952] (II) This device may have been added with another device file.
[     3.952] (II) config/udev: Adding input device sonixj (/dev/input/event6)
[     3.952] (**) sonixj: Applying InputClass "evdev keyboard catchall"
[     3.952] (II) Using input driver 'evdev' for 'sonixj'
[     3.952] (**) sonixj: always reports core events
[     3.952] (**) evdev: sonixj: Device: "/dev/input/event6"
[     3.952] (--) evdev: sonixj: Vendor 0x45e Product 0xf5
[     3.952] (--) evdev: sonixj: Found keys
[     3.952] (II) evdev: sonixj: Configuring as keyboard
[     3.952] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/input/input6/event6"
[     3.952] (II) XINPUT: Adding extended input device "sonixj" (type: KEYBOARD, id 9)
[     3.952] (**) Option "xkb_rules" "evdev"
[     3.952] (**) Option "xkb_model" "pc105"
[     3.952] (**) Option "xkb_layout" "us"
[     3.953] (II) config/udev: Adding input device BTC USB Multimedia Keyboard (/dev/input/event2)
[     3.953] (**) BTC USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[     3.953] (II) Using input driver 'evdev' for 'BTC USB Multimedia Keyboard'
[     3.953] (**) BTC USB Multimedia Keyboard: always reports core events
[     3.953] (**) evdev: BTC USB Multimedia Keyboard: Device: "/dev/input/event2"
[     3.953] (--) evdev: BTC USB Multimedia Keyboard: Vendor 0x46e Product 0x52ce
[     3.953] (--) evdev: BTC USB Multimedia Keyboard: Found keys
[     3.953] (II) evdev: BTC USB Multimedia Keyboard: Configuring as keyboard
[     3.953] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.0/input/input2/event2"
[     3.953] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD, id 10)
[     3.953] (**) Option "xkb_rules" "evdev"
[     3.953] (**) Option "xkb_model" "pc105"
[     3.953] (**) Option "xkb_layout" "us"
[     3.953] (II) config/udev: Adding input device BTC USB Multimedia Keyboard (/dev/input/event3)
[     3.953] (**) BTC USB Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[     3.953] (II) Using input driver 'evdev' for 'BTC USB Multimedia Keyboard'
[     3.953] (**) BTC USB Multimedia Keyboard: always reports core events
[     3.953] (**) evdev: BTC USB Multimedia Keyboard: Device: "/dev/input/event3"
[     3.953] (--) evdev: BTC USB Multimedia Keyboard: Vendor 0x46e Product 0x52ce
[     3.953] (--) evdev: BTC USB Multimedia Keyboard: Found keys
[     3.953] (II) evdev: BTC USB Multimedia Keyboard: Configuring as keyboard
[     3.953] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-7/3-7:1.1/input/input3/event3"
[     3.953] (II) XINPUT: Adding extended input device "BTC USB Multimedia Keyboard" (type: KEYBOARD, id 11)
[     3.953] (**) Option "xkb_rules" "evdev"
[     3.953] (**) Option "xkb_model" "pc105"
[     3.953] (**) Option "xkb_layout" "us"
[     3.953] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/event5)
[     3.953] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[     3.953] (II) Using input driver 'evdev' for 'Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)'
[     3.953] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
[     3.953] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event5"
[     3.953] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Vendor 0x45e Product 0x40
[     3.953] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
[     3.953] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[     3.953] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found relative axes
[     3.953] (--) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
[     3.953] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
[     3.953] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Adding scrollwheel support
[     3.953] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[     3.953] (**) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.953] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-9/3-9:1.0/input/input5/event5"
[     3.953] (II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE, id 12)
[     3.953] (II) evdev: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.
[     3.954] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[     3.954] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[     3.954] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[     3.954] (**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[     3.954] (II) config/udev: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[     3.954] (II) No input driver specified, ignoring this device.
[     3.954] (II) This device may have been added with another device file.
[     3.954] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event10)
[     3.954] (II) No input driver specified, ignoring this device.
[     3.954] (II) This device may have been added with another device file.
[     3.954] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event11)
[     3.954] (II) No input driver specified, ignoring this device.
[     3.954] (II) This device may have been added with another device file.
[     3.954] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event12)
[     3.954] (II) No input driver specified, ignoring this device.
[     3.954] (II) This device may have been added with another device file.
[     3.954] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event13)
[     3.954] (II) No input driver specified, ignoring this device.
[     3.954] (II) This device may have been added with another device file.
[     3.954] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event14)
[     3.954] (II) No input driver specified, ignoring this device.
[     3.954] (II) This device may have been added with another device file.
[     3.954] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event15)
[     3.954] (II) No input driver specified, ignoring this device.
[     3.954] (II) This device may have been added with another device file.
[     3.954] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event16)
[     3.954] (II) No input driver specified, ignoring this device.
[     3.954] (II) This device may have been added with another device file.
[    11.102] (II) intel(0): EDID vendor "EPI", prod id 8193
[    11.102] (II) intel(0): Using EDID range info for horizontal sync
[    11.102] (II) intel(0): Using EDID range info for vertical refresh
[    11.102] (II) intel(0): Printing DDC gathered Modelines:
[    11.102] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    11.102] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    11.102] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    11.102] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    11.102] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    11.102] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    11.102] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    11.102] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    11.102] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    11.102] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    11.102] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    11.102] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    11.102] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    11.102] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    11.102] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    11.102] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    11.102] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    11.102] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    11.102] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    11.102] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    11.250] (II) intel(0): EDID vendor "EPI", prod id 8193
[    11.250] (II) intel(0): Using hsync ranges from config file
[    11.250] (II) intel(0): Using vrefresh ranges from config file
[    11.250] (II) intel(0): Printing DDC gathered Modelines:
[    11.250] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    11.250] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    11.250] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    11.250] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    11.250] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    11.250] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    11.250] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    11.250] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    11.250] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    11.250] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    11.250] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    11.250] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    11.250] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    11.250] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    11.250] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    11.250] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    11.250] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    11.250] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    11.250] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    11.250] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    13.794] (II) intel(0): EDID vendor "EPI", prod id 8193
[    13.794] (II) intel(0): Using hsync ranges from config file
[    13.794] (II) intel(0): Using vrefresh ranges from config file
[    13.794] (II) intel(0): Printing DDC gathered Modelines:
[    13.794] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    13.794] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    13.794] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    13.794] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    13.794] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    13.794] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    13.794] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    13.794] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    13.794] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    13.794] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    13.794] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    13.794] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    13.794] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    13.794] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    13.794] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    13.794] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    13.794] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    13.794] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    13.794] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    13.794] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    13.938] (II) intel(0): EDID vendor "EPI", prod id 8193
[    13.938] (II) intel(0): Using hsync ranges from config file
[    13.938] (II) intel(0): Using vrefresh ranges from config file
[    13.938] (II) intel(0): Printing DDC gathered Modelines:
[    13.938] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    13.938] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    13.938] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    13.938] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    13.938] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    13.938] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    13.938] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    13.938] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    13.938] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    13.938] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    13.938] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    13.938] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    13.938] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    13.938] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    13.938] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    13.938] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    13.938] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    13.938] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    13.938] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    13.938] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    14.082] (II) intel(0): EDID vendor "EPI", prod id 8193
[    14.082] (II) intel(0): Using hsync ranges from config file
[    14.082] (II) intel(0): Using vrefresh ranges from config file
[    14.082] (II) intel(0): Printing DDC gathered Modelines:
[    14.082] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    14.082] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    14.082] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    14.082] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    14.082] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    14.082] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    14.082] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    14.082] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    14.082] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    14.082] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    14.082] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    14.082] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    14.082] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    14.082] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    14.082] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    14.082] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    14.082] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    14.082] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    14.082] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    14.082] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    14.226] (II) intel(0): EDID vendor "EPI", prod id 8193
[    14.226] (II) intel(0): Using hsync ranges from config file
[    14.226] (II) intel(0): Using vrefresh ranges from config file
[    14.226] (II) intel(0): Printing DDC gathered Modelines:
[    14.226] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    14.226] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    14.226] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    14.226] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    14.226] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    14.226] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    14.226] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    14.226] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    14.226] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    14.226] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    14.226] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    14.226] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    14.226] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    14.226] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    14.226] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    14.226] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    14.226] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    14.226] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    14.226] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    14.226] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    14.534] (II) intel(0): EDID vendor "EPI", prod id 8193
[    14.534] (II) intel(0): Using hsync ranges from config file
[    14.534] (II) intel(0): Using vrefresh ranges from config file
[    14.534] (II) intel(0): Printing DDC gathered Modelines:
[    14.534] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    14.534] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    14.534] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    14.534] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    14.534] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    14.534] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    14.534] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    14.534] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    14.534] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    14.534] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    14.534] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    14.534] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    14.534] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    14.534] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    14.534] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    14.534] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    14.534] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    14.534] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    14.534] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    14.534] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    14.674] (II) intel(0): EDID vendor "EPI", prod id 8193
[    14.674] (II) intel(0): Using hsync ranges from config file
[    14.674] (II) intel(0): Using vrefresh ranges from config file
[    14.674] (II) intel(0): Printing DDC gathered Modelines:
[    14.674] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    14.674] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    14.674] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    14.674] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    14.674] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    14.674] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    14.674] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    14.674] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    14.674] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    14.674] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    14.674] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    14.674] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    14.674] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    14.674] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    14.674] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    14.674] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    14.674] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    14.674] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    14.674] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    14.674] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    16.226] (II) intel(0): EDID vendor "EPI", prod id 8193
[    16.226] (II) intel(0): Using hsync ranges from config file
[    16.226] (II) intel(0): Using vrefresh ranges from config file
[    16.226] (II) intel(0): Printing DDC gathered Modelines:
[    16.226] (II) intel(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[    16.226] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    16.226] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    16.226] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    16.226] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    16.226] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    16.226] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    16.226] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    16.226] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    16.226] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    16.226] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    16.226] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    16.226] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    16.226] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    16.226] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    16.226] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    16.226] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    16.226] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    16.226] (II) intel(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz e)
[    16.226] (II) intel(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz e)
[    25.516] (II) AIGLX: Suspending AIGLX clients for VT switch



```

---

### Post by coudy on 2014-02-13
Hi, 
I have same problem with LinuxLiteOS 1.0.8 (based on Ubuntu 12.04). My laptop is Asus A5E, and when I boot without nomodeset parameter, my LCD backlight is turned off. I can see what is on screen only when I connect external monitor. I have tried kernels from 3.2 to 3.13, but everytime same result. I have tried with initrams modules i915, intelfb. I can't get it working.

So far I didn't find solution.

---

### Post by coudy on 2014-02-13
lucky day , 
I just found solution 

this is my running config: 
/etc/default/grub:
```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet i915.modeset=1 acpi_osi=Linux acpi_backlight=vendor"
```

/etc/rc.local
```
echo "10" > /sys/class/backlight/intel_backlight/brightness
```

/etc/initramfs-tools/modules
```
i915
intel
intelfb
```
[B]
now it is working[/B]

---

### Post by dannyboy79 on 2014-02-15
FYI 
> After last (ca. 20th October 2010) update of my debian/testing systems, the xserver-xorg-video-intel stopped to work with i915 modeset set to 0. Therefore the workaround mentioned in the previous point was not applicable any more. Setting of i915 modeset to 1 still caused blank screen, as soon as the i915 module is loaded.
so most likely your solution is because of the other 2 options you're using. nomodeset does NOT work with intel i915 anymore.

---

