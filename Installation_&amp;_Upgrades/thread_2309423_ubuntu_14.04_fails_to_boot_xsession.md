---
title: "ubuntu 14.04 fails to boot xsession"
date: 2016-01-10
forum: Installation &amp; Upgrades
---

### Post by chuzzlewit69 on 2016-01-10
Hi,

I should have learned y lesson by now but was fiddling about building software from sources and was getting a little frustrated when something wouldn't build and installed a few dependencies absent mindedly. When I restarted my system I can't boot into a graphical environment:(

This is as far as I get:
1) GRUB menu appears as normal
2) Ubuntu Studio splash screen appears briefly, then disappears
3) Single cursor appears in top left corner (not blinking)
4) Ubuntu GUI login does NOT appear
5) I can log in to a tty terminal using CTRL+ALT+F1-F6; but can't seem to get into a GUI
6) once logged into tty the display keeps reverting to the cursor in the top left until I hit CTRL+ALT+F1-F6 again to revert back to the terminal session I'm already logged in to.

Checked some of my logs and this caught my eye from the Xorg.0.log:
```
[    10.402] (II) LoadModule: "glx"
[    10.402] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    10.402] (EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so: libGL.so.1: cannot open shared object file: No such file or directory
[    10.402] (II) UnloadModule: "glx"
[    10.402] (II) Unloading glx
[    10.402] (EE) Failed to load module "glx" (loader failed, 7)
```

My laptop screen is on its way out and occasionally craps but I am able to boot into an Ubuntu Studio Live USB and Fedora 21 build (which I have on a separate partition on my hard drive) so I'm pretty sure its not a hardware problem.

I've a feeling I might have installed/removed something related to libGL, but unsure how to fix this. I have managed to apt-get update//upgrade my system successfully. I've also searched this and the Ubuntu Stack Exchange Forum but can't find anything of much use - other than to check the boot and Xorg logs.

Has anyone got any ideas?!

Cheers

Martyn

p.s. I'm running Ubuntu Studio 14.04.3 on a Clevo W740 laptop with Intel Graphics Card.
Boot Log as follows:
```
 * Starting Mount filesystems on boot[234G[ OK ] 
 * Starting Populate /dev filesystem[234G[ OK ] 
 * Starting Populate and link to /run filesystem[234G[ OK ] 
 * Stopping Populate /dev filesystem[234G[ OK ] 
 * Stopping Populate and link to /run filesystem[234G[ OK ] 
 * Stopping Track if upstart is running in a container[234G[ OK ] 
 * Starting Initialize or finalize resolvconf[234G[ OK ] 
 * Starting mount available cgroup filesystems[234G[ OK ] 
 * Starting set console keymap[234G[ OK ] 
 * Starting Signal sysvinit that virtual filesystems are mounted[234G[ OK ] 
 * Starting Signal sysvinit that virtual filesystems are mounted[234G[ OK ] 
 * Starting Bridge udev events into upstart[234G[ OK ] 
 * Starting Signal sysvinit that remote filesystems are mounted[234G[ OK ] 
 * Starting device node and kernel event manager[234G[ OK ] 
 * Starting load modules from /etc/modules[234G[ OK ] 
 * Starting cold plug devices[234G[ OK ] 
 * Starting log initial device creation[234G[ OK ] 
 * Stopping set console keymap[234G[ OK ] 
 * Starting Uncomplicated firewall[234G[ OK ] 
 * Stopping load modules from /etc/modules[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting Signal sysvinit that the rootfs is mounted[234G[ OK ] 
 * Starting configure network device[234G[ OK ] 
 * Starting Clean /tmp directory[234G[ OK ] 
 * Starting Read required files in advance (for other mountpoints)[234G[ OK ] 
 * Stopping Read required files in advance (for other mountpoints)[234G[ OK ] 
 * Stopping Clean /tmp directory[234G[ OK ] 
 * Starting Signal sysvinit that local filesystems are mounted[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting Run Click system-level hooks[234G[ OK ] 
 * Starting Enabling additional executable binary formats[234G[ OK ] 
 * Starting flush early job output to logs[234G[ OK ] 
 * Stopping Mount filesystems on boot[234G[ OK ] 
 * Stopping flush early job output to logs[234G[ OK ] 
 * Starting D-Bus system message bus[234G[ OK ] 
 * Stopping Read required files in advance[234G[ OK ] 
 * Stopping Run Click system-level hooks[234G[ OK ] 
 * Starting Mount network filesystems[234G[ OK ] 
 * Starting SMB/CIFS File Server[234G[ OK ] 
 * Starting Failsafe Boot Delay[234G[ OK ] 
 * Starting SystemD login management service[234G[ OK ] 
 * Starting system logging daemon[234G[ OK ] 
 * Starting SMB/CIFS File and Active Directory Server[234G[ OK ] 
 * Starting bluetooth daemon[234G[ OK ] 
 * Stopping Failsafe Boot Delay[234G[ OK ] 
 * Stopping Mount network filesystems[234G[ OK ] 
 * Starting System V initialisation compatibility[234G[ OK ] 
 * Starting modem connection manager[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting SMB/CIFS File and Active Directory Server[234G[[31mfail[39;49m] 
 * Starting configure network device[234G[ OK ] 
 * Starting mDNS/DNS-SD daemon[234G[ OK ] 
 * Starting network connection manager[234G[ OK ] 
 * Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated[234G[ OK ] 
 * Starting DavMail POP/IMAP/SMTP/CalDav/LDAP Exchange Gateway[234G[ OK ] 
 * Stopping Reload cups, upon starting avahi-daemon to make sure remote queues are populated[234G[ OK ] 
 * Starting set console font[234G[ OK ] 
 * Stopping set console font[234G[ OK ] 
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd 
 * Starting userspace bootsplash[234G[ OK ] 
 * Starting Send an event to indicate plymouth is up[234G[ OK ] 
 * Stopping Send an event to indicate plymouth is up[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting configure network device[234G[ OK ] 
 * Starting Bridge file events into upstart[234G[ OK ] 
 * Starting Bridge socket events into upstart[234G[ OK ] 
 * Stopping userspace bootsplash[234G[ OK ] 
 * Starting AppArmor profiles       [240G  [234G[ OK ] 
 * Setting up X socket directories...       [240G  [234G[ OK ] 
 * Stopping System V initialisation compatibility[234G[ OK ] 
 * Starting System V runlevel compatibility[234G[ OK ] 
 * Starting deferred execution scheduler[234G[ OK ] 
 * Starting regular background program processing daemon[234G[ OK ] 
 * Starting GNOME Display Manager[234G[ OK ] 
 * Starting anac(h)ronistic cron[234G[ OK ] 
 * Starting save kernel messages[234G[ OK ] 
 * Starting configure network device security[234G[ OK ] 
 * Starting crash report submission daemon[234G[ OK ] 
 * Stopping save kernel messages[234G[ OK ] 
 * Starting CPU interrupts balancing daemon[234G[ OK ] 
 * Stopping Restore Sound Card State[234G[ OK ] 
 * Starting automatic crash report generation[234G[ OK ] 
 * Starting cups-browsed - Bonjour remote printer browsing daemon[234G[ OK ] 
 * Starting configure virtual network devices[234G[ OK ] 
 * Starting ACPI daemon[234G[ OK ]
```


And Xorg.0.log:
```
[    10.401] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    10.401] X Protocol Version 11, Revision 0
[    10.401] Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
[    10.401] Current Operating System: Linux blueman-W740SU 3.13.0-68-lowlatency #111-Ubuntu SMP PREEMPT Fri Nov 6 19:08:04 UTC 2015 x86_64
[    10.401] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-68-lowlatency root=UUID=a562c81f-7ed2-425a-89e8-d48f47660433 ro persistent quiet splash vt.handoff=7
[    10.401] Build Date: 12 February 2015  02:49:29PM
[    10.401] xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see http://www.ubuntu.com/support) 
[    10.401] Current version of pixman: 0.30.2
[    10.401]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    10.401] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    10.401] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jan 10 18:13:31 2016
[    10.401] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    10.401] (==) No Layout section.  Using the first Screen section.
[    10.401] (==) No screen section available. Using defaults.
[    10.401] (**) |-->Screen "Default Screen Section" (0)
[    10.401] (**) |   |-->Monitor "<default monitor>"
[    10.401] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    10.401] (==) Automatically adding devices
[    10.401] (==) Automatically enabling devices
[    10.401] (==) Automatically adding GPU devices
[    10.401] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    10.401]     Entry deleted from font path.
[    10.401] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[    10.401] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    10.401] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    10.401] (II) Loader magic: 0x7fab19175d40
[    10.401] (II) Module ABI versions:
[    10.401]     X.Org ANSI C Emulation: 0.4
[    10.401]     X.Org Video Driver: 15.0
[    10.401]     X.Org XInput driver : 20.0
[    10.401]     X.Org Server Extension : 8.0
[    10.401] (II) xfree86: Adding drm device (/dev/dri/card0)
[    10.402] (--) PCI:*(0:0:2:0) 8086:0d26:1558:7410 rev 8, Mem @ 0xf7800000/4194304, 0xe0000000/268435456, I/O @ 0x0000f000/64
[    10.402] Initializing built-in extension Generic Event Extension
[    10.402] Initializing built-in extension SHAPE
[    10.402] Initializing built-in extension MIT-SHM
[    10.402] Initializing built-in extension XInputExtension
[    10.402] Initializing built-in extension XTEST
[    10.402] Initializing built-in extension BIG-REQUESTS
[    10.402] Initializing built-in extension SYNC
[    10.402] Initializing built-in extension XKEYBOARD
[    10.402] Initializing built-in extension XC-MISC
[    10.402] Initializing built-in extension SECURITY
[    10.402] Initializing built-in extension XINERAMA
[    10.402] Initializing built-in extension XFIXES
[    10.402] Initializing built-in extension RENDER
[    10.402] Initializing built-in extension RANDR
[    10.402] Initializing built-in extension COMPOSITE
[    10.402] Initializing built-in extension DAMAGE
[    10.402] Initializing built-in extension MIT-SCREEN-SAVER
[    10.402] Initializing built-in extension DOUBLE-BUFFER
[    10.402] Initializing built-in extension RECORD
[    10.402] Initializing built-in extension DPMS
[    10.402] Initializing built-in extension Present
[    10.402] Initializing built-in extension DRI3
[    10.402] Initializing built-in extension X-Resource
[    10.402] Initializing built-in extension XVideo
[    10.402] Initializing built-in extension XVideo-MotionCompensation
[    10.402] Initializing built-in extension SELinux
[    10.402] Initializing built-in extension XFree86-VidModeExtension
[    10.402] Initializing built-in extension XFree86-DGA
[    10.402] Initializing built-in extension XFree86-DRI
[    10.402] Initializing built-in extension DRI2
[    10.402] (II) LoadModule: "glx"
[    10.402] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    10.402] (EE) Failed to load /usr/lib/xorg/modules/extensions/libglx.so: libGL.so.1: cannot open shared object file: No such file or directory
[    10.402] (II) UnloadModule: "glx"
[    10.402] (II) Unloading glx
[    10.402] (EE) Failed to load module "glx" (loader failed, 7)
[    10.402] (==) Matched intel as autoconfigured driver 0
[    10.402] (==) Matched intel as autoconfigured driver 1
[    10.402] (==) Matched modesetting as autoconfigured driver 2
[    10.402] (==) Matched fbdev as autoconfigured driver 3
[    10.402] (==) Matched vesa as autoconfigured driver 4
[    10.402] (==) Assigned the driver to the xf86ConfigLayout
[    10.402] (II) LoadModule: "intel"
[    10.402] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    10.403] (II) Module intel: vendor="X.Org Foundation"
[    10.403]     compiled for 1.15.1, module version = 2.99.911
[    10.403]     Module class: X.Org Video Driver
[    10.403]     ABI class: X.Org Video Driver, version 15.0
[    10.403] (II) LoadModule: "modesetting"
[    10.403] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    10.403] (II) Module modesetting: vendor="X.Org Foundation"
[    10.403]     compiled for 1.15.0, module version = 0.8.1
[    10.403]     Module class: X.Org Video Driver
[    10.403]     ABI class: X.Org Video Driver, version 15.0
[    10.403] (II) LoadModule: "fbdev"
[    10.403] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    10.403] (II) Module fbdev: vendor="X.Org Foundation"
[    10.403]     compiled for 1.15.0, module version = 0.4.4
[    10.403]     Module class: X.Org Video Driver
[    10.403]     ABI class: X.Org Video Driver, version 15.0
[    10.403] (II) LoadModule: "vesa"
[    10.403] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    10.403] (II) Module vesa: vendor="X.Org Foundation"
[    10.403]     compiled for 1.15.0, module version = 2.3.3
[    10.403]     Module class: X.Org Video Driver
[    10.403]     ABI class: X.Org Video Driver, version 15.0
[    10.403] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    10.403] (II) intel: Driver for Intel(R) HD Graphics: 2000-5000
[    10.403] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100
[    10.403] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200
[    10.403] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    10.403] (II) FBDEV: driver for framebuffer: fbdev
[    10.403] (II) VESA: driver for VESA chipsets: vesa
[    10.403] (++) using VT number 7

[    10.403] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.911-0intel1 (Andrew Lee (&#26446;&#20581;&#31179;) <andrew.lee@collabora.co.uk>)
[    10.404] (WW) Falling back to old probe method for modesetting
[    10.404] (WW) Falling back to old probe method for fbdev
[    10.404] (II) Loading sub module "fbdevhw"
[    10.404] (II) LoadModule: "fbdevhw"
[    10.404] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    10.404] (II) Module fbdevhw: vendor="X.Org Foundation"
[    10.404]     compiled for 1.15.1, module version = 0.0.2
[    10.404]     ABI class: X.Org Video Driver, version 15.0
[    10.404] (WW) Falling back to old probe method for vesa
[    10.404] (--) intel(0): Integrated Graphics Chipset: Intel(R) Iris(TM) Pro Graphics 5200
[    10.404] (--) intel(0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[    10.404] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    10.404] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    10.404] (==) intel(0): RGB weight 888
[    10.404] (==) intel(0): Default visual is TrueColor
[    10.404] (**) intel(0): Framebuffer tiled
[    10.404] (**) intel(0): Pixmaps tiled
[    10.404] (**) intel(0): "Tear free" disabled
[    10.404] (**) intel(0): Forcing per-crtc-pixmaps? no
[    10.404] (II) intel(0): Output eDP1 has no monitor section
[    10.404] (--) intel(0): Found backlight control interface acpi_video0 (type 'firmware') for output eDP1
[    10.404] (II) intel(0): Output VGA1 has no monitor section
[    10.404] (II) intel(0): Output DP1 has no monitor section
[    10.404] (II) intel(0): Output HDMI1 has no monitor section
[    10.404] (II) intel(0): Output HDMI2 has no monitor section
[    10.404] (II) intel(0): Output VIRTUAL1 has no monitor section
[    10.404] (--) intel(0): Output eDP1 using initial mode 1920x1080 on pipe 0
[    10.404] (==) intel(0): DPI set to (96, 96)
[    10.404] (II) Loading sub module "dri2"
[    10.404] (II) LoadModule: "dri2"
[    10.404] (II) Module "dri2" already built-in
[    10.404] (II) UnloadModule: "modesetting"
[    10.404] (II) Unloading modesetting
[    10.404] (II) UnloadModule: "fbdev"
[    10.404] (II) Unloading fbdev
[    10.404] (II) UnloadSubModule: "fbdevhw"
[    10.404] (II) Unloading fbdevhw
[    10.404] (II) UnloadModule: "vesa"
[    10.404] (II) Unloading vesa
[    10.405] (==) Depth 24 pixmap format is 32 bpp
[    10.405] (II) intel(0): SNA initialized with Haswell (gen7.5, gt3) backend
[    10.405] (==) intel(0): Backing store enabled
[    10.405] (==) intel(0): Silken mouse enabled
[    10.405] (II) intel(0): HW Cursor enabled
[    10.405] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    10.405] (==) intel(0): DPMS enabled
[    10.405] (II) intel(0): [DRI2] Setup complete
[    10.405] (II) intel(0): [DRI2]   DRI driver: i965
[    10.405] (II) intel(0): [DRI2]   VDPAU driver: i965
[    10.405] (II) intel(0): direct rendering: DRI2 Enabled
[    10.405] (==) intel(0): hotplug detection: "enabled"
[    10.405] (--) RandR disabled
[    10.408] (II) SELinux: Disabled on system
[    10.410] (II) intel(0): switch to mode 1920x1080@60.0 on eDP1 using pipe 0, position (0, 0), rotation normal, reflection none
[    10.426] (II) intel(0): Setting screen physical size to 508 x 285
[    10.436] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    10.438] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    10.438] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.438] (II) LoadModule: "evdev"
[    10.438] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    10.438] (II) Module evdev: vendor="X.Org Foundation"
[    10.438]     compiled for 1.15.0, module version = 2.8.2
[    10.438]     Module class: X.Org XInput Driver
[    10.438]     ABI class: X.Org XInput driver, version 20.0
[    10.438] (II) Using input driver 'evdev' for 'Power Button'
[    10.438] (**) Power Button: always reports core events
[    10.438] (**) evdev: Power Button: Device: "/dev/input/event3"
[    10.438] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.438] (--) evdev: Power Button: Found keys
[    10.438] (II) evdev: Power Button: Configuring as keyboard
[    10.438] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    10.438] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    10.438] (**) Option "xkb_rules" "evdev"
[    10.438] (**) Option "xkb_model" "pc105"
[    10.438] (**) Option "xkb_layout" "gb"
[    10.440] (II) XKB: reuse xkmfile /var/lib/xkb/server-2B4266AA55228AE7D9557A18F1965DBA19850816.xkm
[    10.440] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    10.440] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    10.440] (II) Using input driver 'evdev' for 'Video Bus'
[    10.440] (**) Video Bus: always reports core events
[    10.440] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    10.440] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    10.440] (--) evdev: Video Bus: Found keys
[    10.440] (II) evdev: Video Bus: Configuring as keyboard
[    10.440] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input14/event7"
[    10.440] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    10.440] (**) Option "xkb_rules" "evdev"
[    10.440] (**) Option "xkb_model" "pc105"
[    10.440] (**) Option "xkb_layout" "gb"
[    10.440] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    10.440] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    10.440] (II) Using input driver 'evdev' for 'Power Button'
[    10.440] (**) Power Button: always reports core events
[    10.440] (**) evdev: Power Button: Device: "/dev/input/event0"
[    10.440] (--) evdev: Power Button: Vendor 0 Product 0x1
[    10.440] (--) evdev: Power Button: Found keys
[    10.440] (II) evdev: Power Button: Configuring as keyboard
[    10.441] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    10.441] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    10.441] (**) Option "xkb_rules" "evdev"
[    10.441] (**) Option "xkb_model" "pc105"
[    10.441] (**) Option "xkb_layout" "gb"
[    10.441] (II) config/udev: Adding input device Lid Switch (/dev/input/event2)
[    10.441] (II) No input driver specified, ignoring this device.
[    10.441] (II) This device may have been added with another device file.
[    10.441] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    10.441] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    10.441] (II) Using input driver 'evdev' for 'Sleep Button'
[    10.441] (**) Sleep Button: always reports core events
[    10.441] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    10.441] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    10.441] (--) evdev: Sleep Button: Found keys
[    10.441] (II) evdev: Sleep Button: Configuring as keyboard
[    10.441] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1/event1"
[    10.441] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    10.441] (**) Option "xkb_rules" "evdev"
[    10.441] (**) Option "xkb_model" "pc105"
[    10.441] (**) Option "xkb_layout" "gb"
[    10.441] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:02.0/drm/card0
[    10.441] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    10.441] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=3 (/dev/input/event10)
[    10.441] (II) No input driver specified, ignoring this device.
[    10.441] (II) This device may have been added with another device file.
[    10.441] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=7 (/dev/input/event9)
[    10.441] (II) No input driver specified, ignoring this device.
[    10.441] (II) This device may have been added with another device file.
[    10.441] (II) config/udev: Adding input device HDA Intel HDMI HDMI/DP,pcm=8 (/dev/input/event8)
[    10.441] (II) No input driver specified, ignoring this device.
[    10.441] (II) This device may have been added with another device file.
[    10.442] (II) config/udev: Adding input device BisonCam, NB Pro (/dev/input/event6)
[    10.442] (**) BisonCam, NB Pro: Applying InputClass "evdev keyboard catchall"
[    10.442] (II) Using input driver 'evdev' for 'BisonCam, NB Pro'
[    10.442] (**) BisonCam, NB Pro: always reports core events
[    10.442] (**) evdev: BisonCam, NB Pro: Device: "/dev/input/event6"
[    10.442] (--) evdev: BisonCam, NB Pro: Vendor 0x5986 Product 0x536
[    10.442] (--) evdev: BisonCam, NB Pro: Found keys
[    10.442] (II) evdev: BisonCam, NB Pro: Configuring as keyboard
[    10.442] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-10/3-10:1.0/input/input13/event6"
[    10.442] (II) XINPUT: Adding extended input device "BisonCam, NB Pro" (type: KEYBOARD, id 10)
[    10.442] (**) Option "xkb_rules" "evdev"
[    10.442] (**) Option "xkb_model" "pc105"
[    10.442] (**) Option "xkb_layout" "gb"
[    10.442] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event12)
[    10.442] (II) No input driver specified, ignoring this device.
[    10.442] (II) This device may have been added with another device file.
[    10.442] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[    10.442] (II) No input driver specified, ignoring this device.
[    10.442] (II) This device may have been added with another device file.
[    10.442] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    10.442] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    10.442] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    10.442] (**) AT Translated Set 2 keyboard: always reports core events
[    10.442] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    10.442] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    10.442] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    10.442] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    10.442] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    10.442] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    10.442] (**) Option "xkb_rules" "evdev"
[    10.442] (**) Option "xkb_model" "pc105"
[    10.442] (**) Option "xkb_layout" "gb"
[    10.442] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    10.442] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    10.442] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    10.442] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    10.442] (II) LoadModule: "synaptics"
[    10.443] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    10.443] (II) Module synaptics: vendor="X.Org Foundation"
[    10.443]     compiled for 1.15.0, module version = 1.7.4
[    10.443]     Module class: X.Org XInput Driver
[    10.443]     ABI class: X.Org XInput driver, version 20.0
[    10.443] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    10.443] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    10.443] (**) Option "Device" "/dev/input/event5"
[    10.459] (II) synaptics: SynPS/2 Synaptics TouchPad: found clickpad property
[    10.459] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1262 - 5680 (res 46)
[    10.459] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1124 - 4728 (res 62)
[    10.459] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    10.459] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    10.459] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left double triple
[    10.459] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    10.459] (**) Option "SoftButtonAreas" "50% 0 82% 0 0 0 0 0"
[    10.459] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    10.459] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    10.468] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event5"
[    10.468] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    10.468] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    10.468] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    10.468] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.035
[    10.468] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    10.468] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    10.468] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    10.468] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    10.468] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    10.468] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    10.468] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    15.170] (II) UnloadModule: "synaptics"
[    15.170] (II) evdev: AT Translated Set 2 keyboard: Close
[    15.170] (II) UnloadModule: "evdev"
[    15.170] (II) evdev: BisonCam, NB Pro: Close
[    15.170] (II) UnloadModule: "evdev"
[    15.170] (II) evdev: Sleep Button: Close
[    15.170] (II) UnloadModule: "evdev"
[    15.170] (II) evdev: Power Button: Close
[    15.171] (II) UnloadModule: "evdev"
[    15.171] (II) evdev: Video Bus: Close
[    15.171] (II) UnloadModule: "evdev"
[    15.171] (II) evdev: Power Button: Close
[    15.171] (II) UnloadModule: "evdev"
[    15.175] (EE) Server terminated successfully (0). Closing log file.
```

---

