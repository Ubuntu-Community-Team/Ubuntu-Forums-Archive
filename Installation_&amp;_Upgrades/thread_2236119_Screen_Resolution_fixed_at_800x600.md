---
title: "Screen Resolution fixed at 800x600"
date: 2014-07-24
forum: Installation &amp; Upgrades
---

### Post by tom121 on 2014-07-24
Hello everyone,

I am using Ubuntu since years, but this is the first time I am really needing your help, because I can't fix the problem by myself:

I did an upgrade today from Ubuntu 12.04LTS to 14.04LTS. Well, everything worked fine, but the loading screen wasn't really showing up during the boot, so I decided to fix it with this script: [http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

Unfortunately, my screen resolution is now fixed to 800x600 and in "System Settings\Displays", it says "Built-in Displays" instead of "Philips Consumer Electronics 19''"

Could you please tell me how to revert the script?

Thanks! :)

---

### Post by QIII on 2014-07-24
Hello!

A link to how to revert the changes is given in towards the bottom of the link you provided.

Those instructions are for versions of Ubuntu that are well past End Of Life.  I would have recommended against using them on 14.04.

That being the case, it is impossible to say if the revert instructions will work.

---

### Post by tom121 on 2014-07-24
Hello,
thanks for your reply.

I already tried to revert the changes with the revert script provided, but it didn't work.

Any other ideas?

---

### Post by papibe on 2014-07-24
Hi tom121.

Could you run these commands, and post back the results (you can copy/paste the text)?
```
apt-cache policy v86d

grep -vE '^#|^$' /etc/default/grub

cat /etc/initramfs-tools/modules

[ -f /etc/initramfs-tools/conf.d/splash ] && cat /etc/initramfs-tools/conf.d/splash

cat /var/log/Xorg.0.log

lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by tom121 on 2014-07-25
Hey,

here is the output:

```
tom@Henri-PC:~$ apt-cache policy v86d
v86d:
  Installed: (none)
  Candidate: 0.1.10-1
  Version table:
     0.1.10-1 0
        500 [http://lu.archive.ubuntu.com/ubuntu/](http://lu.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
tom@Henri-PC:~$ grep -vE '^#|^$' /etc/default/grub
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""
GRUB_GFXMODE=1366x768-24
tom@Henri-PC:~$ cat /etc/initramfs-tools/modules
# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
uvesafb mode_option=1366x768-24 mtrr=3 scroll=ywrap
tom@Henri-PC:~$ 
tom@Henri-PC:~$ [ -f /etc/initramfs-tools/conf.d/splash ] && cat /etc/initramfs-tools/conf.d/splash

tom@Henri-PC:~$ 
tom@Henri-PC:~$ cat /var/log/Xorg.0.log
[   142.957] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   142.957] X Protocol Version 11, Revision 0
[   142.957] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[   142.957] Current Operating System: Linux Henri-PC 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686
[   142.957] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-32-generic root=UUID=c6a2acb1-138d-40b2-ac11-047299f7826e ro quiet splash nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap vt.handoff=7
[   142.957] Build Date: 16 April 2014  01:40:08PM
[   142.957] xorg-server 2:1.15.1-0ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   142.957] Current version of pixman: 0.30.2
[   142.957]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   142.957] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   142.957] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jul 25 12:42:07 2014
[   142.957] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   142.958] (==) No Layout section.  Using the first Screen section.
[   142.958] (==) No screen section available. Using defaults.
[   142.958] (**) |-->Screen "Default Screen Section" (0)
[   142.958] (**) |   |-->Monitor "<default monitor>"
[   142.958] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   142.958] (==) Automatically adding devices
[   142.958] (==) Automatically enabling devices
[   142.958] (==) Automatically adding GPU devices
[   142.958] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   142.958]     Entry deleted from font path.
[   142.958] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   142.958]     Entry deleted from font path.
[   142.958] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   142.958]     Entry deleted from font path.
[   142.958] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   142.958]     Entry deleted from font path.
[   142.958] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   142.958]     Entry deleted from font path.
[   142.958] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   142.958] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   142.958] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   142.958] (II) Loader magic: 0xb77c86c0
[   142.958] (II) Module ABI versions:
[   142.958]     X.Org ANSI C Emulation: 0.4
[   142.958]     X.Org Video Driver: 15.0
[   142.958]     X.Org XInput driver : 20.0
[   142.958]     X.Org Server Extension : 8.0
[   142.959] (--) PCI:*(0:0:2:0) 8086:0102:1458:d000 rev 9, Mem @ 0xfb800000/4194304, 0xe0000000/268435456, I/O @ 0x0000ff00/64
[   142.959] Initializing built-in extension Generic Event Extension
[   142.959] Initializing built-in extension SHAPE
[   142.959] Initializing built-in extension MIT-SHM
[   142.959] Initializing built-in extension XInputExtension
[   142.959] Initializing built-in extension XTEST
[   142.959] Initializing built-in extension BIG-REQUESTS
[   142.960] Initializing built-in extension SYNC
[   142.960] Initializing built-in extension XKEYBOARD
[   142.960] Initializing built-in extension XC-MISC
[   142.960] Initializing built-in extension SECURITY
[   142.960] Initializing built-in extension XINERAMA
[   142.960] Initializing built-in extension XFIXES
[   142.960] Initializing built-in extension RENDER
[   142.960] Initializing built-in extension RANDR
[   142.960] Initializing built-in extension COMPOSITE
[   142.960] Initializing built-in extension DAMAGE
[   142.960] Initializing built-in extension MIT-SCREEN-SAVER
[   142.960] Initializing built-in extension DOUBLE-BUFFER
[   142.960] Initializing built-in extension RECORD
[   142.960] Initializing built-in extension DPMS
[   142.960] Initializing built-in extension Present
[   142.960] Initializing built-in extension DRI3
[   142.960] Initializing built-in extension X-Resource
[   142.960] Initializing built-in extension XVideo
[   142.960] Initializing built-in extension XVideo-MotionCompensation
[   142.960] Initializing built-in extension SELinux
[   142.960] Initializing built-in extension XFree86-VidModeExtension
[   142.960] Initializing built-in extension XFree86-DGA
[   142.960] Initializing built-in extension XFree86-DRI
[   142.960] Initializing built-in extension DRI2
[   142.960] (II) LoadModule: "glx"
[   142.960] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   142.961] (II) Module glx: vendor="X.Org Foundation"
[   142.961]     compiled for 1.15.1, module version = 1.0.0
[   142.961]     ABI class: X.Org Server Extension, version 8.0
[   142.961] (==) AIGLX enabled
[   142.961] Loading extension GLX
[   142.961] (==) Matched intel as autoconfigured driver 0
[   142.961] (==) Matched modesetting as autoconfigured driver 1
[   142.961] (==) Matched fbdev as autoconfigured driver 2
[   142.961] (==) Matched vesa as autoconfigured driver 3
[   142.961] (==) Assigned the driver to the xf86ConfigLayout
[   142.961] (II) LoadModule: "intel"
[   142.961] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   142.961] (II) Module intel: vendor="X.Org Foundation"
[   142.961]     compiled for 1.15.0, module version = 2.99.910
[   142.961]     Module class: X.Org Video Driver
[   142.961]     ABI class: X.Org Video Driver, version 15.0
[   142.961] (II) LoadModule: "modesetting"
[   142.961] (WW) Warning, couldn't open module modesetting
[   142.961] (II) UnloadModule: "modesetting"
[   142.961] (II) Unloading modesetting
[   142.961] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   142.961] (II) LoadModule: "fbdev"
[   142.961] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   142.961] (II) Module fbdev: vendor="X.Org Foundation"
[   142.961]     compiled for 1.15.0, module version = 0.4.4
[   142.961]     Module class: X.Org Video Driver
[   142.961]     ABI class: X.Org Video Driver, version 15.0
[   142.961] (II) LoadModule: "vesa"
[   142.962] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   142.962] (II) Module vesa: vendor="X.Org Foundation"
[   142.962]     compiled for 1.15.0, module version = 2.3.3
[   142.962]     Module class: X.Org Video Driver
[   142.962]     ABI class: X.Org Video Driver, version 15.0
[   142.962] (==) Matched intel as autoconfigured driver 0
[   142.962] (==) Matched modesetting as autoconfigured driver 1
[   142.962] (==) Matched fbdev as autoconfigured driver 2
[   142.962] (==) Matched vesa as autoconfigured driver 3
[   142.962] (==) Assigned the driver to the xf86ConfigLayout
[   142.962] (II) LoadModule: "intel"
[   142.962] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   142.962] (II) Module intel: vendor="X.Org Foundation"
[   142.962]     compiled for 1.15.0, module version = 2.99.910
[   142.962]     Module class: X.Org Video Driver
[   142.962]     ABI class: X.Org Video Driver, version 15.0
[   142.962] (II) UnloadModule: "intel"
[   142.962] (II) Unloading intel
[   142.962] (II) Failed to load module "intel" (already loaded, -1216902346)
[   142.962] (II) LoadModule: "modesetting"
[   142.962] (WW) Warning, couldn't open module modesetting
[   142.962] (II) UnloadModule: "modesetting"
[   142.962] (II) Unloading modesetting
[   142.962] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   142.962] (II) LoadModule: "fbdev"
[   142.962] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   142.962] (II) Module fbdev: vendor="X.Org Foundation"
[   142.962]     compiled for 1.15.0, module version = 0.4.4
[   142.962]     Module class: X.Org Video Driver
[   142.962]     ABI class: X.Org Video Driver, version 15.0
[   142.962] (II) UnloadModule: "fbdev"
[   142.962] (II) Unloading fbdev
[   142.962] (II) Failed to load module "fbdev" (already loaded, 0)
[   142.962] (II) LoadModule: "vesa"
[   142.963] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   142.963] (II) Module vesa: vendor="X.Org Foundation"
[   142.963]     compiled for 1.15.0, module version = 2.3.3
[   142.963]     Module class: X.Org Video Driver
[   142.963]     ABI class: X.Org Video Driver, version 15.0
[   142.963] (II) UnloadModule: "vesa"
[   142.963] (II) Unloading vesa
[   142.963] (II) Failed to load module "vesa" (already loaded, 0)
[   142.963] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   142.963] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[   142.963] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[   142.963] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[   142.963] (II) FBDEV: driver for framebuffer: fbdev
[   142.963] (II) VESA: driver for VESA chipsets: vesa
[   142.963] (++) using VT number 7

[   142.964] (II) Loading sub module "fbdevhw"
[   142.964] (II) LoadModule: "fbdevhw"
[   142.965] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   142.965] (II) Module fbdevhw: vendor="X.Org Foundation"
[   142.965]     compiled for 1.15.1, module version = 0.0.2
[   142.965]     ABI class: X.Org Video Driver, version 15.0
[   142.965] (**) FBDEV(0): claimed PCI slot 0@0:2:0
[   142.965] (II) FBDEV(0): using default device
[   142.965] (WW) Falling back to old probe method for vesa
[   142.965] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   142.965] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[   142.965] (==) FBDEV(0): RGB weight 888
[   142.965] (==) FBDEV(0): Default visual is TrueColor
[   142.965] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   142.965] (II) FBDEV(0): hardware: VESA VGA (video memory: 1920kB)
[   142.965] (II) FBDEV(0): checking modes against framebuffer device...
[   142.965] (II) FBDEV(0): checking modes against monitor...
[   142.965] (--) FBDEV(0): Virtual size is 800x600 (pitch 800)
[   142.965] (**) FBDEV(0):  Built-in mode "current": 48.0 MHz, 46.9 kHz, 75.1 Hz
[   142.965] (II) FBDEV(0): Modeline "current"x0.0   48.00  800 832 928 1024  600 604 608 624 -hsync -vsync -csync (46.9 kHz b)
[   142.965] (==) FBDEV(0): DPI set to (96, 96)
[   142.965] (II) Loading sub module "fb"
[   142.965] (II) LoadModule: "fb"
[   142.965] (II) Loading /usr/lib/xorg/modules/libfb.so
[   142.965] (II) Module fb: vendor="X.Org Foundation"
[   142.965]     compiled for 1.15.1, module version = 1.0.0
[   142.965]     ABI class: X.Org ANSI C Emulation, version 0.4
[   142.965] (**) FBDEV(0): using shadow framebuffer
[   142.965] (II) Loading sub module "shadow"
[   142.965] (II) LoadModule: "shadow"
[   142.966] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   142.966] (II) Module shadow: vendor="X.Org Foundation"
[   142.966]     compiled for 1.15.1, module version = 1.1.0
[   142.966]     ABI class: X.Org ANSI C Emulation, version 0.4
[   142.966] (II) UnloadModule: "vesa"
[   142.966] (II) Unloading vesa
[   142.966] (==) Depth 24 pixmap format is 32 bpp
[   142.966] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   142.966] (==) FBDEV(0): Backing store enabled
[   142.966] (==) FBDEV(0): DPMS enabled
[   142.966] (==) RandR enabled
[   142.974] (II) SELinux: Disabled on system
[   142.974] (II) AIGLX: Screen 0 is not DRI2 capable
[   142.974] (EE) AIGLX: reverting to software rendering
[   142.983] (II) AIGLX: Loaded and initialized swrast
[   142.983] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   142.990] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   142.992] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   142.992] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   142.992] (II) LoadModule: "evdev"
[   142.992] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   142.992] (II) Module evdev: vendor="X.Org Foundation"
[   142.992]     compiled for 1.15.0, module version = 2.8.2
[   142.992]     Module class: X.Org XInput Driver
[   142.992]     ABI class: X.Org XInput driver, version 20.0
[   142.992] (II) Using input driver 'evdev' for 'Power Button'
[   142.992] (**) Power Button: always reports core events
[   142.992] (**) evdev: Power Button: Device: "/dev/input/event1"
[   142.992] (--) evdev: Power Button: Vendor 0 Product 0x1
[   142.992] (--) evdev: Power Button: Found keys
[   142.992] (II) evdev: Power Button: Configuring as keyboard
[   142.992] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   142.992] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   142.992] (**) Option "xkb_rules" "evdev"
[   142.992] (**) Option "xkb_model" "pc105"
[   142.992] (**) Option "xkb_layout" "ch"
[   142.992] (**) Option "xkb_variant" "fr"
[   142.994] (II) XKB: reuse xkmfile /var/lib/xkb/server-53A4CFD27CBE694B87E57086754C176B71A8EEB5.xkm
[   142.995] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   142.995] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   142.995] (II) Using input driver 'evdev' for 'Power Button'
[   142.995] (**) Power Button: always reports core events
[   142.995] (**) evdev: Power Button: Device: "/dev/input/event0"
[   142.995] (--) evdev: Power Button: Vendor 0 Product 0x1
[   142.995] (--) evdev: Power Button: Found keys
[   142.995] (II) evdev: Power Button: Configuring as keyboard
[   142.995] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[   142.995] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   142.995] (**) Option "xkb_rules" "evdev"
[   142.995] (**) Option "xkb_model" "pc105"
[   142.995] (**) Option "xkb_layout" "ch"
[   142.995] (**) Option "xkb_variant" "fr"
[   142.995] (II) config/udev: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) (/dev/input/event2)
[   142.995] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Applying InputClass "evdev pointer catchall"
[   142.995] (II) Using input driver 'evdev' for 'Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)'
[   142.996] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): always reports core events
[   142.996] (**) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Device: "/dev/input/event2"
[   142.996] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Vendor 0x45e Product 0x39
[   142.996] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found 9 mouse buttons
[   142.996] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
[   142.996] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found relative axes
[   142.996] (--) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Found x and y relative axes
[   142.996] (II) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Configuring as mouse
[   142.996] (II) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): Adding scrollwheel support
[   142.996] (**) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
[   142.996] (**) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   142.996] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3:1.0/input/input3/event2"
[   142.996] (II) XINPUT: Adding extended input device "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" (type: MOUSE, id 8)
[   142.996] (II) evdev: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): initialized for relative axes.
[   142.996] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
[   142.996] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration profile 0
[   142.996] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration factor: 2.000
[   142.996] (**) Microsoft Microsoft 5-Button Mouse with IntelliEye(TM): (accel) acceleration threshold: 4
[   142.996] (II) config/udev: Adding input device Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) (/dev/input/mouse0)
[   142.996] (II) No input driver specified, ignoring this device.
[   142.996] (II) This device may have been added with another device file.
[   142.996] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event8)
[   142.996] (II) No input driver specified, ignoring this device.
[   142.996] (II) This device may have been added with another device file.
[   142.996] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event7)
[   142.996] (II) No input driver specified, ignoring this device.
[   142.996] (II) This device may have been added with another device file.
[   142.996] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[   142.997] (II) No input driver specified, ignoring this device.
[   142.997] (II) This device may have been added with another device file.
[   142.997] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event5)
[   142.997] (II) No input driver specified, ignoring this device.
[   142.997] (II) This device may have been added with another device file.
[   142.997] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event4)
[   142.997] (II) No input driver specified, ignoring this device.
[   142.997] (II) This device may have been added with another device file.
[   142.997] (II) config/udev: Adding input device Logitech Unifying Device. Wireless PID:2007 (/dev/input/event3)
[   142.997] (**) Logitech Unifying Device. Wireless PID:2007: Applying InputClass "evdev keyboard catchall"
[   142.997] (II) Using input driver 'evdev' for 'Logitech Unifying Device. Wireless PID:2007'
[   142.997] (**) Logitech Unifying Device. Wireless PID:2007: always reports core events
[   142.997] (**) evdev: Logitech Unifying Device. Wireless PID:2007: Device: "/dev/input/event3"
[   142.997] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Vendor 0x46d Product 0xc52b
[   142.997] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found 1 mouse buttons
[   142.997] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found scroll wheel(s)
[   142.997] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found relative axes
[   142.997] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Forcing relative x/y axes to exist.
[   142.997] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found absolute axes
[   142.997] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Forcing absolute x/y axes to exist.
[   142.997] (--) evdev: Logitech Unifying Device. Wireless PID:2007: Found keys
[   142.997] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Configuring as mouse
[   142.997] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Configuring as keyboard
[   142.997] (II) evdev: Logitech Unifying Device. Wireless PID:2007: Adding scrollwheel support
[   142.997] (**) evdev: Logitech Unifying Device. Wireless PID:2007: YAxisMapping: buttons 4 and 5
[   142.997] (**) evdev: Logitech Unifying Device. Wireless PID:2007: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   142.997] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.2/0003:046D:C52B.0004/input/input4/event3"
[   142.997] (II) XINPUT: Adding extended input device "Logitech Unifying Device. Wireless PID:2007" (type: KEYBOARD, id 9)
[   142.997] (**) Option "xkb_rules" "evdev"
[   142.997] (**) Option "xkb_model" "pc105"
[   142.997] (**) Option "xkb_layout" "ch"
[   142.997] (**) Option "xkb_variant" "fr"
[   142.997] (II) evdev: Logitech Unifying Device. Wireless PID:2007: initialized for relative axes.
[   142.997] (WW) evdev: Logitech Unifying Device. Wireless PID:2007: ignoring absolute axes.
[   142.998] (**) Logitech Unifying Device. Wireless PID:2007: (accel) keeping acceleration scheme 1
[   142.998] (**) Logitech Unifying Device. Wireless PID:2007: (accel) acceleration profile 0
[   142.998] (**) Logitech Unifying Device. Wireless PID:2007: (accel) acceleration factor: 2.000
[   142.998] (**) Logitech Unifying Device. Wireless PID:2007: (accel) acceleration threshold: 4
[   143.001] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   148.865] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   148.907] (II) XKB: reuse xkmfile /var/lib/xkb/server-1AF0F76EC1B8F17FACAF0147E4BD15990DCED925.xkm
[   148.931] (II) XKB: reuse xkmfile /var/lib/xkb/server-1AF0F76EC1B8F17FACAF0147E4BD15990DCED925.xkm
[   150.202] (II) XKB: reuse xkmfile /var/lib/xkb/server-664B7DE013F5F57C1D681EEA75F4C1AB2E855156.xkm
tom@Henri-PC:~$ 
tom@Henri-PC:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0102] (rev 09)
    Subsystem: Gigabyte Technology Co., Ltd Device [1458:d000]
00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)
tom@Henri-PC:~$ 

```

Regards.

---

### Post by papibe on 2014-07-25
Thanks.

There are several changes that did not revert back to the default config.

Let's start installing gksudo:
```
sudo apt-get install gksu
```
Then Open the grub file:
```
gksudo gedit /etc/default/grub
```
Looks for a this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=1366x768-24,mtrr=3,scroll=ywrap"
```
and change it so it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Then look for this other line:
```
GRUB_GFXMODE=1366x768-24
```
and comment it out:
```
# GRUB_GFXMODE=1366x768-24
```
Then save the file and close it.

Now edit the initramfs-tools' modules file:
```
gksudo gedit /etc/initramfs-tools/modules
```
go to the end of the file and look for this line:
```
uvesafb mode_option=1366x768-24 mtrr=3 scroll=ywrap
```
comment out the line so it looks like this:
```
# uvesafb mode_option=1366x768-24 mtrr=3 scroll=ywrap
```
Save the file and close it.

That should do it. Restart your computer and let us know how it went.

Regards.

---

### Post by tom121 on 2014-07-25
Worked fine for me, thanks!
Jhust a little hint for other people following these instructions: there is a little typo:
> **papibe said:**
> 
Then Open the grub file:
```
gksudo gedit /etc/**defualt**/grub
```
The word in bold has to be default ;).

---

### Post by papibe on 2014-07-25
Thanks for the correction. Now it's fixed ;)

I'm glad you got your resolution back.

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how).

Best Regards.

---

