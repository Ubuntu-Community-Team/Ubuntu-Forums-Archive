---
title: "Resolution issues after update"
date: 2016-02-08
forum: Installation &amp; Upgrades
---

### Post by Pengatom on 2016-02-08
I have a HP Elitebook 2540p running ubuntu 14.04.3 LTS (lsb_release -a)
When I turned it on today the screen resolution was very low, so I checked the System Settings -> Displays, and I can't set it to higher than 1024 x 768.
I searched for some info on how to change/check the graphics driver, and since its an intel, it should apparently be built in.

```
sudo apt-get install xserver-xorg-video-intel
The following packages have unmet dependencies: xserver-xorg-video-intel : Depends: xorg-video-abi-15
                            Depends: xserver-xorg-core (>= 2:1.14.99.902)
E: Unable to correct problems, you have held broken packages.
```

```
dpkg --get-selections | grep hold
```

Doesn't return anything.

I'm completely lost here...

---

### Post by matt_symes on 2016-02-08
Hi

Welcome to the forums.

Let's check your sources first.

Please post the output of (copy and paste it into the terminal)

```
grep "^[^#]" /etc/apt/sources.list{,.d/*}
```

Please paste the output between code tags like this

[noparse]```
terminal output
```[/noparse]

to get output like this

```
terminal output
```

I've edited your last post.

Kind regards

---

### Post by Pengatom on 2016-02-09
Hi,

Thanks. Here is the terminal output:
```
/etc/apt/sources.list:deb http://no.archive.ubuntu.com/ubuntu/ trusty main restricted/etc/apt/sources.list:deb-src http://no.archive.ubuntu.com/ubuntu/ trusty main restricted
/etc/apt/sources.list:deb http://no.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb-src http://no.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
/etc/apt/sources.list:deb http://no.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb-src http://no.archive.ubuntu.com/ubuntu/ trusty universe
/etc/apt/sources.list:deb http://no.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb-src http://no.archive.ubuntu.com/ubuntu/ trusty-updates universe
/etc/apt/sources.list:deb http://no.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb-src http://no.archive.ubuntu.com/ubuntu/ trusty multiverse
/etc/apt/sources.list:deb http://no.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb-src http://no.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
/etc/apt/sources.list:deb http://no.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://no.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu trusty main
/etc/apt/sources.list.d/falk-t-j-qtsixa-trusty.list:deb http://ppa.launchpad.net/falk-t-j/qtsixa/ubuntu trusty main
/etc/apt/sources.list.d/gazebo-latest.list:deb http://packages.osrfoundation.org/gazebo/ubuntu trusty main
/etc/apt/sources.list.d/ros-latest.list:deb http://packages.ros.org/ros/ubuntu trusty main
/etc/apt/sources.list.d/ros-latest.list.save:deb http://packages.ros.org/ros/ubuntu trusty main
```

It was working okay before, assume there is an issue with updates gone wrong...

---

### Post by matt_symes on 2016-02-09
Hi

Robotics software ? Nice.

Your sources look fine.

Can you post the output of

```
dpkg -l xserver-xorg-core
```

```
uname -r
```

```
xrandr
```

```
apt-mark showhold
```

and 

```
cat /var/log/Xorg.0.log
```

Do you have the same resolution problems if you boot into an older kernel from the grub menu ?

Kind regards

---

### Post by Pengatom on 2016-02-09
Hi,

I here are the outputs that you requested, only have ssh access to it, and there is currently no monitor connected.
I'll update it as soon as I have the chance.

 ```
 dpkg -l xserver-xorg-core
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version             Architecture        Description
+++-=============================-===================-===================-===============================================================
un  xserver-xorg-core             <none>              <none>              (no description available)
```

```
 uname -r
3.19.0-49-generic
```

xrandr - I'll need to look at this when I'm back home. - No monitor connected

```
apt-mark showhold
"nothing"
```

```
 cat /var/log/Xorg.0.log
[     6.354]
X.Org X Server 1.17.1
Release Date: 2015-02-10
[     6.354] X Protocol Version 11, Revision 0
[     6.354] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[     6.354] Current Operating System: Linux Yoda 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:24:31 UTC 2016 x86_64
[     6.355] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-49-generic root=UUID=fbdba3cd-ff74-47fb-ad6a-b6b4aae534e0 ro quiet splash vt.handoff=7
[     6.355] Build Date: 11 September 2015  10:33:14AM
[     6.355] xorg-server 2:1.17.1-0ubuntu3.1~trusty1 (For technical support please see http://www.ubuntu.com/support)
[     6.355] Current version of pixman: 0.30.2
[     6.355]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[     6.355] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     6.355] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Feb  9 08:19:42 2016
[     6.355] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     6.356] (==) No Layout section.  Using the first Screen section.
[     6.356] (==) No screen section available. Using defaults.
[     6.356] (**) |-->Screen "Default Screen Section" (0)
[     6.356] (**) |   |-->Monitor "<default monitor>"
[     6.356] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[     6.356] (==) Automatically adding devices
[     6.356] (==) Automatically enabling devices
[     6.356] (==) Automatically adding GPU devices
[     6.356] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     6.356]    Entry deleted from font path.
[     6.356] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     6.356]    Entry deleted from font path.
[     6.356] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     6.356]    Entry deleted from font path.
[     6.356] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     6.356]    Entry deleted from font path.
[     6.356] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     6.356]    Entry deleted from font path.
[     6.356] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[     6.356] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     6.356] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[     6.356] (II) Loader magic: 0x56231fb77c60
[     6.356] (II) Module ABI versions:
[     6.356]    X.Org ANSI C Emulation: 0.4
[     6.356]    X.Org Video Driver: 19.0
[     6.356]    X.Org XInput driver : 21.0
[     6.356]    X.Org Server Extension : 9.0
[     6.356] (II) xfree86: Adding drm device (/dev/dri/card0)
[     6.358] (--) PCI:*(0:0:2:0) 8086:0046:103c:7008 rev 2, Mem @ 0xd0000000/4194304, 0xc0000000/268435456, I/O @ 0x00005058/8
[     6.358] (II) LoadModule: "glx"
[     6.359] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     6.369] (II) Module glx: vendor="X.Org Foundation"
[     6.369]    compiled for 1.17.1, module version = 1.0.0
[     6.369]    ABI class: X.Org Server Extension, version 9.0
[     6.369] (==) AIGLX enabled
[     6.369] (==) Matched intel as autoconfigured driver 0
[     6.369] (==) Matched intel as autoconfigured driver 1
[     6.369] (==) Matched modesetting as autoconfigured driver 2
[     6.369] (==) Matched fbdev as autoconfigured driver 3
[     6.369] (==) Matched vesa as autoconfigured driver 4
[     6.369] (==) Assigned the driver to the xf86ConfigLayout
[     6.369] (II) LoadModule: "intel"
[     6.369] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     6.370] (II) Module intel: vendor="X.Org Foundation"
[     6.370]    compiled for 1.17.1, module version = 2.99.917
[     6.370]    Module class: X.Org Video Driver
[     6.370]    ABI class: X.Org Video Driver, version 19.0
[     6.370] (II) LoadModule: "modesetting"
[     6.370] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     6.370] (II) Module modesetting: vendor="X.Org Foundation"
[     6.370]    compiled for 1.17.1, module version = 1.17.1
[     6.370]    Module class: X.Org Video Driver
[     6.370]    ABI class: X.Org Video Driver, version 19.0
[     6.370] (II) LoadModule: "fbdev"
[     6.370] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     6.370] (II) Module fbdev: vendor="X.Org Foundation"
[     6.370]    compiled for 1.17.1, module version = 0.4.4
[     6.370]    Module class: X.Org Video Driver
[     6.370]    ABI class: X.Org Video Driver, version 19.0
[     6.370] (II) LoadModule: "vesa"
[     6.371] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     6.371] (II) Module vesa: vendor="X.Org Foundation"
[     6.371]    compiled for 1.17.1, module version = 2.3.3
[     6.371]    Module class: X.Org Video Driver
[     6.371]    ABI class: X.Org Video Driver, version 19.0
[     6.371] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
        i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
        915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
        Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
        GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[     6.371] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[     6.371] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[     6.371] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[     6.371] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     6.371] (II) FBDEV: driver for framebuffer: fbdev
[     6.371] (II) VESA: driver for VESA chipsets: vesa
[     6.371] (++) using VT number 7


[     6.371] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20141121
[     6.371] (II) intel(0): SNA compiled: xserver-xorg-video-intel-lts-vivid 2:2.99.917-1~exp1ubuntu2.2~trusty1 (Timo Aaltonen <tjaalton@debian.org>)
[     6.371] (II) intel(0): SNA compiled for use with valgrind
[     6.371] (WW) Falling back to old probe method for modesetting
[     6.371] (WW) Falling back to old probe method for fbdev
[     6.371] (II) Loading sub module "fbdevhw"
[     6.371] (II) LoadModule: "fbdevhw"
[     6.371] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     6.371] (II) Module fbdevhw: vendor="X.Org Foundation"
[     6.371]    compiled for 1.17.1, module version = 0.0.2
[     6.371]    ABI class: X.Org Video Driver, version 19.0
[     6.371] (WW) Falling back to old probe method for vesa
[     6.372] (--) intel(0): Integrated Graphics Chipset: Intel(R) HD Graphics
[     6.372] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2
[     6.372] (II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[     6.372] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[     6.372] (==) intel(0): RGB weight 888
[     6.372] (==) intel(0): Default visual is TrueColor
[     6.372] (II) intel(0): Output eDP1 has no monitor section
[     6.372] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[     6.372] (II) intel(0): Enabled output eDP1
[     6.372] (II) intel(0): Output VGA1 has no monitor section
[     6.372] (II) intel(0): Enabled output VGA1
[     6.372] (II) intel(0): Output HDMI1 has no monitor section
[     6.372] (II) intel(0): Enabled output HDMI1
[     6.372] (II) intel(0): Output DP1 has no monitor section
[     6.372] (II) intel(0): Enabled output DP1
[     6.372] (II) intel(0): Output HDMI2 has no monitor section
[     6.372] (II) intel(0): Enabled output HDMI2
[     6.372] (II) intel(0): Output DP2 has no monitor section
[     6.372] (II) intel(0): Enabled output DP2
[     6.372] (--) intel(0): Using a maximum size of 256x256 for hardware cursors
[     6.372] (II) intel(0): Output VIRTUAL1 has no monitor section
[     6.372] (II) intel(0): Enabled output VIRTUAL1
[     6.372] (--) intel(0): Output eDP1 using initial mode 1280x800 on pipe 0
[     6.373] (==) intel(0): TearFree disabled
[     6.373] (==) intel(0): DPI set to (96, 96)
[     6.373] (II) Loading sub module "dri2"
[     6.373] (II) LoadModule: "dri2"
[     6.373] (II) Module "dri2" already built-in
[     6.373] (II) Loading sub module "present"
[     6.373] (II) LoadModule: "present"
[     6.373] (II) Module "present" already built-in
[     6.373] (II) UnloadModule: "modesetting"
[     6.373] (II) Unloading modesetting
[     6.373] (II) UnloadModule: "fbdev"
[     6.373] (II) Unloading fbdev
[     6.373] (II) UnloadSubModule: "fbdevhw"
[     6.373] (II) Unloading fbdevhw
[     6.373] (II) UnloadModule: "vesa"
[     6.373] (II) Unloading vesa
[     6.373] (==) Depth 24 pixmap format is 32 bpp
[     6.373] (II) intel(0): SNA initialized with Ironlake (gen5) backend
[     6.373] (==) intel(0): Backing store enabled
[     6.373] (==) intel(0): Silken mouse enabled
[     6.373] (II) intel(0): HW Cursor enabled
[     6.373] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     6.373] (==) intel(0): DPMS enabled
[     6.374] (==) intel(0): display hotplug detection enabled
[     6.374] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[     6.374] (II) intel(0): [DRI2] Setup complete
[     6.374] (II) intel(0): [DRI2]   DRI driver: i965
[     6.374] (II) intel(0): [DRI2]   VDPAU driver: i965
[     6.374] (II) intel(0): direct rendering: DRI2 enabled
[     6.374] (II) intel(0): hardware support for Present enabled
[     6.374] (--) RandR disabled
[     6.385] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     6.385] (II) AIGLX: enabled GLX_ARB_create_context
[     6.385] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     6.385] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     6.385] (II) AIGLX: enabled GLX_INTEL_swap_event
[     6.385] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     6.385] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     6.385] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     6.385] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     6.385] (II) AIGLX: Loaded and initialized i965
[     6.385] (II) GLX: Initialized DRI2 GL provider for screen 0
[     6.392] (II) intel(0): switch to mode 1280x800@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[     6.402] (II) intel(0): Setting screen physical size to 338 x 211
[     6.409] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     6.411] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     6.411] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     6.411] (II) LoadModule: "evdev"
[     6.412] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     6.414] (II) Module evdev: vendor="X.Org Foundation"
[     6.414]    compiled for 1.17.1, module version = 2.9.0
[     6.414]    Module class: X.Org XInput Driver
[     6.414]    ABI class: X.Org XInput driver, version 21.0
[     6.414] (II) Using input driver 'evdev' for 'Power Button'
[     6.414] (**) Power Button: always reports core events
[     6.414] (**) evdev: Power Button: Device: "/dev/input/event2"
[     6.414] (--) evdev: Power Button: Vendor 0 Product 0x1
[     6.414] (--) evdev: Power Button: Found keys
[     6.414] (II) evdev: Power Button: Configuring as keyboard
[     6.414] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     6.414] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     6.414] (**) Option "xkb_rules" "evdev"
[     6.414] (**) Option "xkb_model" "pc105"
[     6.414] (**) Option "xkb_layout" "no"
[     6.416] (II) XKB: reuse xkmfile /var/lib/xkb/server-5F8E417E6ED2D276BE32A8CA0E3DB916C21A8CA2.xkm
[     6.417] (II) config/udev: Adding input device Video Bus (/dev/input/event8)
[     6.417] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[     6.417] (II) Using input driver 'evdev' for 'Video Bus'
[     6.417] (**) Video Bus: always reports core events
[     6.417] (**) evdev: Video Bus: Device: "/dev/input/event8"
[     6.417] (--) evdev: Video Bus: Vendor 0 Product 0x6
[     6.417] (--) evdev: Video Bus: Found keys
[     6.417] (II) evdev: Video Bus: Configuring as keyboard
[     6.417] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input14/event8"
[     6.417] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     6.417] (**) Option "xkb_rules" "evdev"
[     6.417] (**) Option "xkb_model" "pc105"
[     6.417] (**) Option "xkb_layout" "no"
[     6.417] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[     6.417] (II) No input driver specified, ignoring this device.
[     6.417] (II) This device may have been added with another device file.
[     6.417] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[     6.417] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[     6.417] (II) Using input driver 'evdev' for 'Sleep Button'
[     6.417] (**) Sleep Button: always reports core events
[     6.417] (**) evdev: Sleep Button: Device: "/dev/input/event0"
[     6.417] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[     6.417] (--) evdev: Sleep Button: Found keys
[     6.417] (II) evdev: Sleep Button: Configuring as keyboard
[     6.417] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[     6.417] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)
[     6.417] (**) Option "xkb_rules" "evdev"
[     6.417] (**) Option "xkb_model" "pc105"
[     6.417] (**) Option "xkb_layout" "no"
[     6.418] (II) config/udev: Adding input device HP Webcam [2 MP Macro] (/dev/input/event7)
[     6.418] (**) HP Webcam [2 MP Macro]: Applying InputClass "evdev keyboard catchall"
[     6.418] (II) Using input driver 'evdev' for 'HP Webcam [2 MP Macro]'
[     6.418] (**) HP Webcam [2 MP Macro]: always reports core events
[     6.418] (**) evdev: HP Webcam [2 MP Macro]: Device: "/dev/input/event7"
[     6.418] (--) evdev: HP Webcam [2 MP Macro]: Vendor 0x4f2 Product 0xb163
[     6.418] (--) evdev: HP Webcam [2 MP Macro]: Found keys
[     6.418] (II) evdev: HP Webcam [2 MP Macro]: Configuring as keyboard
[     6.418] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input13/event7"
[     6.418] (II) XINPUT: Adding extended input device "HP Webcam [2 MP Macro]" (type: KEYBOARD, id 9)
[     6.418] (**) Option "xkb_rules" "evdev"
[     6.418] (**) Option "xkb_model" "pc105"
[     6.418] (**) Option "xkb_layout" "no"
[     6.419] (II) config/udev: Adding input device HDA Intel MID Mic (/dev/input/event9)
[     6.419] (II) No input driver specified, ignoring this device.
[     6.419] (II) This device may have been added with another device file.
[     6.419] (II) config/udev: Adding input device HDA Intel MID Line (/dev/input/event10)
[     6.419] (II) No input driver specified, ignoring this device.
[     6.419] (II) This device may have been added with another device file.
[     6.419] (II) config/udev: Adding input device HDA Intel MID Headphone (/dev/input/event11)
[     6.419] (II) No input driver specified, ignoring this device.
[     6.419] (II) This device may have been added with another device file.
[     6.419] (II) config/udev: Adding input device HDA Intel MID Dock Headphone (/dev/input/event12)
[     6.419] (II) No input driver specified, ignoring this device.
[     6.419] (II) This device may have been added with another device file.
[     6.419] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=3 (/dev/input/event13)
[     6.419] (II) No input driver specified, ignoring this device.
[     6.419] (II) This device may have been added with another device file.
[     6.419] (II) config/udev: Adding input device HDA Intel MID HDMI/DP,pcm=7 (/dev/input/event14)
[     6.419] (II) No input driver specified, ignoring this device.
[     6.419] (II) This device may have been added with another device file.
[     6.420] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[     6.420] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     6.420] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     6.420] (**) AT Translated Set 2 keyboard: always reports core events
[     6.420] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[     6.420] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     6.420] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     6.420] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     6.420] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[     6.420] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[     6.420] (**) Option "xkb_rules" "evdev"
[     6.420] (**) Option "xkb_model" "pc105"
[     6.420] (**) Option "xkb_layout" "no"
[     6.420] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event4)
[     6.420] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[     6.420] (II) Using input driver 'evdev' for 'PS/2 Generic Mouse'
[     6.420] (**) PS/2 Generic Mouse: always reports core events
[     6.420] (**) evdev: PS/2 Generic Mouse: Device: "/dev/input/event4"
[     6.420] (--) evdev: PS/2 Generic Mouse: Vendor 0x2 Product 0x1
[     6.420] (--) evdev: PS/2 Generic Mouse: Found 3 mouse buttons
[     6.420] (--) evdev: PS/2 Generic Mouse: Found relative axes
[     6.420] (--) evdev: PS/2 Generic Mouse: Found x and y relative axes
[     6.420] (II) evdev: PS/2 Generic Mouse: Configuring as mouse
[     6.420] (**) evdev: PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[     6.420] (**) evdev: PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     6.420] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input8/event4"
[     6.420] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE, id 11)
[     6.420] (II) evdev: PS/2 Generic Mouse: initialized for relative axes.
[     6.420] (**) PS/2 Generic Mouse: (accel) keeping acceleration scheme 1
[     6.420] (**) PS/2 Generic Mouse: (accel) acceleration profile 0
[     6.420] (**) PS/2 Generic Mouse: (accel) acceleration factor: 2.000
[     6.420] (**) PS/2 Generic Mouse: (accel) acceleration threshold: 4
[     6.421] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse0)
[     6.421] (II) No input driver specified, ignoring this device.
[     6.421] (II) This device may have been added with another device file.
[     6.421] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event6)
[     6.421] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[     6.421] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[     6.421] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[     6.421] (II) LoadModule: "synaptics"
[     6.421] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[     6.421] (II) Module synaptics: vendor="X.Org Foundation"
[     6.421]    compiled for 1.17.1, module version = 1.8.99
[     6.421]    Module class: X.Org XInput Driver
[     6.421]    ABI class: X.Org XInput driver, version 21.0
[     6.421] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[     6.421] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     6.421] (**) Option "Device" "/dev/input/event6"
[     6.452] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[     6.452] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5808 (res 74)
[     6.452] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 5372 (res 182)
[     6.452] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[     6.452] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[     6.452] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[     6.452] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[     6.452] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     6.452] (**) SynPS/2 Synaptics TouchPad: always reports core events
[     6.464] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio4/input/input11/event6"
[     6.464] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[     6.464] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[     6.464] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[     6.464] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.034
[     6.464] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[     6.464] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[     6.464] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[     6.464] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[     6.464] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[     6.464] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[     6.464] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[     6.464] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/event5)
[     6.464] (II) No input driver specified, ignoring this device.
[     6.464] (II) This device may have been added with another device file.
[     6.465] (II) config/udev: Adding input device ST LIS3LV02DL Accelerometer (/dev/input/js0)
[     6.465] (II) No input driver specified, ignoring this device.
[     6.465] (II) This device may have been added with another device file.
[     6.466] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event15)
[     6.466] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     6.466] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[     6.466] (**) HP WMI hotkeys: always reports core events
[     6.466] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event15"
[     6.466] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[     6.466] (--) evdev: HP WMI hotkeys: Found keys
[     6.466] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[     6.466] (**) Option "config_info" "udev:/sys/devices/virtual/input/input21/event15"
[     6.466] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[     6.466] (**) Option "xkb_rules" "evdev"
[     6.466] (**) Option "xkb_model" "pc105"
[     6.466] (**) Option "xkb_layout" "no"
[     7.030] (II) XKB: reuse xkmfile /var/lib/xkb/server-11E5978A89165D56F1B4A2145DB8D0A1B3FE4475.xkm
[     7.032] (II) XKB: reuse xkmfile /var/lib/xkb/server-11E5978A89165D56F1B4A2145DB8D0A1B3FE4475.xkm
[     7.252] (II) intel(0): EDID vendor "LGD", prod id 591
[     7.252] (II) intel(0): Printing DDC gathered Modelines:
[     7.252] (II) intel(0): Modeline "1280x800"x0.0   69.30  1280 1304 1336 1408  800 804 808 820 -hsync -vsync (49.2 kHz eP)
[     7.252] (II) intel(0): Modeline "1280x800"x0.0   47.20  1280 1304 1336 1408  800 813 817 832 -hsync -vsync (33.5 kHz e)
[     7.356] (II) XKB: reuse xkmfile /var/lib/xkb/server-11E5978A89165D56F1B4A2145DB8D0A1B3FE4475.xkm
[     7.361] (II) XKB: reuse xkmfile /var/lib/xkb/server-11E5978A89165D56F1B4A2145DB8D0A1B3FE4475.xkm
[     7.475] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.603] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.604] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.606] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.608] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.609] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.611] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.613] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.614] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.616] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.618] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.619] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.621] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.622] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.624] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.626] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.627] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.629] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.631] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.633] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.634] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.636] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.637] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.639] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.641] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.643] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.645] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.647] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.648] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.650] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.652] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.653] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.655] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.657] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.658] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.660] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.662] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.663] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.665] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.666] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.668] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.669] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.671] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.673] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.674] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.676] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.678] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.679] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.681] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     7.682] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.010] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.013] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.016] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.019] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.022] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.026] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.029] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.031] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.033] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.036] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.039] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.041] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.043] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.045] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.046] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.049] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.052] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.054] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.056] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.059] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.062] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.065] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.067] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.071] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.073] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.092] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.095] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.099] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.101] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.107] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.110] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.113] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.116] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.118] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.120] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.122] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.123] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.125] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.127] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.128] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.131] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.132] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.134] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.135] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.137] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.139] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.140] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.142] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.144] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.145] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.360] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.363] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.366] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.368] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.370] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.371] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.373] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.375] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.376] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.378] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.380] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.382] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.384] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.386] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.387] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.389] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.391] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.392] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.394] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.396] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.398] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.400] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.402] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.403] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.405] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.407] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.408] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.410] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.412] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.414] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.416] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.417] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.419] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.421] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.422] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.424] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.426] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.427] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.429] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.431] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.433] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.435] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.437] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.438] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.440] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.442] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.443] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.445] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.447] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[     9.449] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[    30.890] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[    32.249] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[    33.204] (II) XKB: reuse xkmfile /var/lib/xkb/server-9AF05B81A022680931B04D3AE0911EDCB7F19018.xkm
[    37.535] (II) XKB: reuse xkmfile /var/lib/xkb/server-AB379AD6E33C158C1D3820462F295515872E2E01.xkm
[    37.546] (II) XKB: reuse xkmfile /var/lib/xkb/server-AB379AD6E33C158C1D3820462F295515872E2E01.xkm
[    38.526] (II) XKB: reuse xkmfile /var/lib/xkb/server-4D3EB6EA34F376D8E9EFC1841D3AD46466E8A695.xkm



```

---

### Post by Pengatom on 2016-02-09
Ok, so I got a monitor connected and was able to run xrandr after all.
And voila! Now it works again!

Thanks Matt!

---

### Post by matt_symes on 2016-02-09
Hi

> **Pengatom said:**
> Ok, so I got a monitor connected and was able to run xrandr after all.
And voila! Now it works again!

Thanks Matt!

If you disconnect the monitor does it still work ?

xrandr should have just produced some output (the available and current resolution), unless you attempted to set a new resolution with it.

Are you sure this is fixed ? I'm not convinced but i may be wrong.

```
un  xserver-xorg-core             <none>              <none>  
``` 

You don't have xserver-xorg-core ?

If it's not fixed, can you post the output of

```
dpkg -l | grep xorg
```

Kind regards

---

### Post by Pengatom on 2016-02-10
Hi,

I was somewhat convinced yesterday, as I tried it on two different monitors and it worked. But when I came home it didn't work, it shows the name of the previous monitor connected, and its resolution. running xrandr doesn't do anything now...
Rebooting makes it go back to unknown display with 1024x768 as max resolution

output of dpkg -l | grep xorg:
```
ii  python3-xkit                                          0.5.0ubuntu2                                        all          library for the manipulation of xorg.conf files (Python 3)
ii  vnc4server                                            4.1.1+xorg4.3.0-37ubuntu5.0.2                       amd64        Virtual network computing server software
ii  xorg                                                  1:7.7+1ubuntu8.1                                    amd64        X.Org X Window System
ii  xorg-docs-core                                        1:1.7-1                                             all          Core documentation for the X.org X Window System
ii  xorg-sgml-doctools                                    1:1.11-1                                            all          Common tools for building X.Org SGML documentation
ii  xserver-xorg-core-lts-vivid                           2:1.17.1-0ubuntu3.1~trusty1                         amd64        Xorg X server - core server
ii  xserver-xorg-input-all-lts-vivid                      1:7.7+7ubuntu3~trusty1                              amd64        X.Org X server -- input driver metapackage
ii  xserver-xorg-input-evdev-lts-vivid                    1:2.9.0-1ubuntu2~trusty1                            amd64        X.Org X server -- evdev input driver
ii  xserver-xorg-input-mouse-lts-vivid                    1:1.9.1-1~trusty1                                   amd64        X.Org X server -- mouse input driver
ii  xserver-xorg-input-synaptics-lts-vivid                1.8.1-1ubuntu1~trusty1                              amd64        Synaptics TouchPad driver for X.Org server
ii  xserver-xorg-input-vmmouse-lts-vivid                  1:13.0.0-1ubuntu1~trusty1                           amd64        X.Org X server -- VMMouse input driver to use with VMWare
ii  xserver-xorg-input-wacom-lts-vivid                    1:0.25.0-0ubuntu1.1~trusty1                         amd64        X.Org X server -- Wacom input driver
ii  xserver-xorg-lts-trusty                               3:6                                                 amd64        Transitional package for xserver-xorg
ii  xserver-xorg-lts-vivid                                1:7.7+7ubuntu3~trusty1                              amd64        X.Org X server
ii  xserver-xorg-video-all-lts-vivid                      1:7.7+7ubuntu3~trusty1                              amd64        X.Org X server -- output driver metapackage
ii  xserver-xorg-video-ati-lts-vivid                      1:7.5.0-1ubuntu2~trusty1                            amd64        X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-cirrus-lts-vivid                   1:1.5.2-2ubuntu1~trusty1                            amd64        X.Org X server -- Cirrus display driver
ii  xserver-xorg-video-fbdev-lts-vivid                    1:0.4.4-1build3~trusty1                             amd64        X.Org X server -- fbdev display driver
ii  xserver-xorg-video-intel-lts-vivid                    2:2.99.917-1~exp1ubuntu2.2~trusty1                  amd64        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-mach64-lts-vivid                   6.9.4-2ubuntu1~trusty1                              amd64        X.Org X server -- ATI Mach64 display driver
ii  xserver-xorg-video-mga-lts-vivid                      1:1.6.3-2ubuntu1~trusty1                            amd64        X.Org X server -- MGA display driver
ii  xserver-xorg-video-neomagic-lts-vivid                 1:1.2.8-1ubuntu1~trusty1                            amd64        X.Org X server -- Neomagic display driver
ii  xserver-xorg-video-nouveau-lts-vivid                  1:1.0.11-1ubuntu2build1~trusty1                     amd64        X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-openchrome-lts-vivid               1:0.3.3-1ubuntu1~trusty1                            amd64        X.Org X server -- VIA display driver
ii  xserver-xorg-video-r128-lts-vivid                     6.9.2-1ubuntu1~trusty1                              amd64        X.Org X server -- ATI r128 display driver
ii  xserver-xorg-video-radeon-lts-vivid                   1:7.5.0-1ubuntu2~trusty1                            amd64        X.Org X server -- AMD/ATI Radeon display driver
ii  xserver-xorg-video-savage-lts-vivid                   1:2.3.7-2ubuntu4~trusty1                            amd64        X.Org X server -- Savage display driver
ii  xserver-xorg-video-siliconmotion-lts-vivid            1:1.7.7-2ubuntu2~trusty1                            amd64        X.Org X server -- SiliconMotion display driver
ii  xserver-xorg-video-sisusb-lts-vivid                   1:0.9.6-2build3~trusty1                             amd64        X.Org X server -- SiS USB display driver
ii  xserver-xorg-video-tdfx-lts-vivid                     1:1.4.6-0ubuntu1~trusty1                            amd64        X.Org X server -- tdfx display driver
ii  xserver-xorg-video-trident-lts-vivid                  1:1.3.6-0ubuntu6build1~trusty1                      amd64        X.Org X server -- Trident display driver
ii  xserver-xorg-video-vesa-lts-vivid                     1:2.3.3-1build3~trusty1                             amd64        X.Org X server -- VESA display driver
ii  xserver-xorg-video-vmware-lts-vivid                   1:13.1.0-0ubuntu1build1~trusty1                     amd64        X.Org X server -- VMware display driver
```

Bah, I so hoped this was solved now since it worked on two other monitors...

---

### Post by matt_symes on 2016-02-10
Hi

> **Pengatom said:**
> Hi,

I was somewhat convinced yesterday, as I tried it on two different monitors and it worked. But when I came home it didn't work, it shows the name of the previous monitor connected, and its resolution. running xrandr doesn't do anything now...
Rebooting makes it go back to unknown display with 1024x768 as max resolution

So it's a specific monitor that is displaying the resolution at 1024x768 ? ... and this monitor is your external monitor at home ?

When you connect it to other monitors it displays the correct resolution ? It always displays the correct resolution ?

Are you connecting all these external monitors to the same port; the display port (DP1) ? 

Does it display the correct resolution when not connected to any monitor ?

Is the default resolution of the HP Elitebook 2540p 1024x768 ?

I'm just trying to understand exactly what you're doing and where the problem lies so please answer the above questions.

> dpkg -l | grep xorg:
```

<snip
ii  xserver-xorg-core-lts-vivid                           2:1.17.1-0ubuntu3.1~trusty1                         amd64        Xorg X server - core server
<snip>
ii  xserver-xorg-video-intel-lts-vivid                    2:2.99.917-1~exp1ubuntu2.2~trusty1                  amd64        X.Org X server -- Intel i8xx, i9xx display driver
<snip>

```

Bah, I so hoped this was solved now since it worked on two other monitors...

You're using the vivid hardware enablement stack for X. That makes much more sense :)

Kind regards

---

### Post by Pengatom on 2016-02-10
So it's a specific monitor that is displaying the resolution at 1024x768 ? ... and this monitor is your external monitor at home ? **Yes**

When you connect it to other monitors it displays the correct resolution ? It always displays the correct resolution ? **Yes, the ones I have tried**

Are you connecting all these external monitors to the same port; the display port (DP1) ? **Yes, VGA port**

Does it display the correct resolution when not connected to any monitor ? **The built in displays correct no matter if or which monitor is connected**

Is the default resolution of the HP Elitebook 2540p 1024x768 ? **No, its 1280 x 800**

I'm just trying to understand exactly what you're doing and where the problem lies so please answer the above questions.

You're using the vivid hardware enablement stack for X. That makes much more sense :) **Well, that is something that I installed AFTER this problem occurred, since I couldn't install **xserver-xorg-video-intel

Its just DP/VGA output on the pc/dockingstation, I'll pick up a DP/DVI converter tomorrow and try with that.

---

### Post by Pengatom on 2016-02-15
So I installed the DP/DVI converter, now it works with 1080p resolution on the monitor that previously didn't work...
Sure would like to know whats going on here so I would be able to fix it if it happens again...

---

### Post by MAFoElffen on 2016-02-15
Just a note-- This is what I see.

XServer, on init does a hardware probe where it searches for connected monitors and looks for the EDID of what was connected. In his initial xorg.0.log that he posted, I did not see where XSever saw a monitor or EDID... but did say that it gave a config for a default montior. So it saw something, but not all. If it did not see anything at all, it would have turned that port off. (Would not have gotten 1024x786)

Experience has shown me that a monitor can lose it's EDID in a moment... so is possible.

 If the Op does not get xrandr back from that connected monitor, but does from the other two... then it could be that  the EDID is corrupted on that monitor. XServer uses that EDID to help define the modelines of what it can do. He still needs to post his Xrandr results... which I still do not see.

If that is the problem, contact me and I'll tell of a work-around. If it is, that is not the end of the world for that monitor... but would be some work to manually define what it can do. There no secret to it, you just supply an xorg.conf that says to ignore the EDID and use user configured modelines for the resolutions he wants // that the model of monitor is capable of displaying.

Edit-- DP/DVI converter? So a plug converter or digital conversion device? Each would explain different things about that monitor.

If a plug converter, then it would have to do about the physical connection, completing the circuit to get the right info through. If a digital converter, then it has to do about the conversion device providing XServer the info of capabilities (rather than the monitor). Also if you are using a different port on that monitor, because of the converter...

---

### Post by Pengatom on 2016-02-17
Thanks for the input!

I got xrandr back from the monitor while it was plugged in via VGA, but I only go low resolution, not full HD...

The DP/DVI is just a cable with different ports in each end, might be some electronics in there, but there is no external power going into it, so I assume it isn't.

---

### Post by MAFoElffen on 2016-02-17
So... Here is the what... 
-You were connected from your PC (VGA port) to that monitor (before the adapter) through the monitor's VGA Port and it fails.
 -- But when your connected to two other monitors via VGA they worked, so your vga port on your PC is good...
- When you plug form your PC (DP) to your motor's DVI Port, then it works.

^Right? If the above is true, then: In a monitor with HDMI and VGA ports, the VGA is analog / The DVI is digital... The conclusion is that the analog section of the monitor is boinked, but it is still working on the digital side...

It still has some life left to it.

---

### Post by Pengatom on 2016-02-18
I don't know if this will make me banned from this forum, but, it works in, ehm, windows...
I have dual boot on the computer, and booting it into Win10, well the monitor works in full HD over VGA.

Don't know if wine uses the EDID info though...

---

### Post by QIII on 2016-02-18
Why would that get you banned?  It's a factual statement.

Now, going off on a rant with foul language would be a different matter.  :)

Remember that the fact that something works in Windows may be diagnostic, but what works in Windows is not necessarily an indication that it must work in Linux.  And yes, Wine does complicate things.

---

### Post by Pengatom on 2016-02-22
Well, after I booted into Win10, I rebooted it to Ubuntu again and continued working. Yesterday I just realized that it was still connected to the VGA port, and the monitor was displaying in full HD without any issue. Beats me!

---

