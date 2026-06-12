---
title: "Dual boot: Win 10 boots, Ubuntu only in recovery mode + on power"
date: 2019-08-20
forum: Installation &amp; Upgrades
---

### Post by blueginpinktonic on 2019-08-20
TL,DR: New to Ubuntu, not to Linux, still fairly noob. Installed Ubuntu 18.04 as dual boot second OS on new laptop; Windows 10 boots without any hiccups from grub, but Ubuntu only boots in recovery mode and then only when connected to a power source (does not boot into recovery mode even when laptop battery 90% if not plugged in). Loved what I saw of Ubuntu and would love to get it to work properly, suspect I might be missing something stupid in the nature of a graphics issue, but also starting to wonder if I ran into an unfixable wall here, would appreciate some input.


More info:

Laptop specifics: Dell Inspiron 3580, Intel Core i5-8265U, 1.5GHz x 8; 8G RAM, 1TB HDD, Intel onboard graphics. Windows 10 preinstalled.


Drew heavily from these guides for help during installation process:
[https://tutorials.ubuntu.com/](https://tutorials.ubuntu.com/)
[https://www.dell.com/support/article/za/en/zadhs1/sln301754/how-to-install-ubuntu-and-windows-8-or-10-as-a-dual-boot-on-your-dell-pc?lang=en](https://www.dell.com/support/article/za/en/zadhs1/sln301754/how-to-install-ubuntu-and-windows-8-or-10-as-a-dual-boot-on-your-dell-pc?lang=en)


Installation process followed: backed up windows installation onto a USB, shrunk windows partition through windows, downloaded ubuntu 18.04 iso, verified using checksum 256 + echo methods, copied to USB using Rufus, booted from USB to try without install, no problems, liked it, installed using something else option to create root, home and swap partitions. Worked fine, looked good. Updated sudo, checked for drivers, downloaded codecs, enabled shell extentions, restarted, got hit with purple screen after selecting Ubuntu from grub (no text flashing, no splash/login menu, just a dark purple screen). Left it hanging >10 minutes, no response, hard reboot using power button.

Suspected a graphics driver issue so used e in grub to add nomodeset fix, was able to boot in recovery mode (laptop plugged into power source at the time). Edited the gedit to make nomodeset fix permanent, did a sudo apt update, restarted, got stuck on purple screen again. Left it a while.

Tested windows 10 - booted first time, no issues. Laptop not plugged in at this time and battery power 25% in Windows. Restarted and tried booting in recovery mode again, get a violet screen with "initializing ramdisk" message which then hangs, no splash screen.  Tried to boot from live USB - picks up, but purple screens me. Suspected USB might be problematic - tested on different laptop, boots easily. Thought low battery power might be a factor, plugged into power source, gave it some time. Booted from USB no problem into "try without installing", selected "install" and when it came up used the "reinstall Ubuntu" option. 

Ubuntu boots after reinstall. Sudo update, downloaded codecs, restarted. Purple screen on launching Ubuntu. Violet screen with "initializing ramdisk" on recovery mode. Spent some time contemplating life choices.

Plugged laptop into power, boot via recovery mode, did the check and repair files (nothing found) and boot repair just in case. Checked that Ubuntu is UEFI installed (it is). Suspect driver issue, looked at software updates, proprietary drivers is enabled but nothing available under additional drivers. Checked again, still nothing. Used checkbox to self-test in CLI, nothing found. Have by now noticed that being plugged in helps, thought Ubuntu might be drawing too much power at startup, so looked at startup applications (nothing there), disabled the auto-suspend function and did a sudo download of TLP while I'm at it (more association of ideas). Installed lightdm as display manager. Sudo update, restart. Unplug laptop (79% battery power).

Purple screen on launching Ubuntu, violet screen with initializing ramdisk in recovery mode. Hard reboot. Plug in laptop. Purple screen on launching Ubuntu. Launches via recovery mode. 


Did a lot of internet research - most of what I can find seems to apply to Nvidia graphics cards, which I do not have, or to Windows being finicky, which is also not my current problem. Also a lot of information is about hanging on the splash screen, which I don't reach most of the time. Tried going through the sticky post here, but not finding anything that seems similar to what I'm experiencing. Tried to get more information as suggested in the sticky by doing the following in the CLI:


did a  
```
sudo lspci -vvn | grep -i VGA  
and got a wall full of this:

                        
 
     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

 00:02.0 0300: 8086:3ea0 (rev 02) (prog-if 00 [VGA controller])

     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

     Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

     Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

     Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

     Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

     BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-

     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

     BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-

     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

     Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

     Control: I/O- Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

     Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

 pcilib: sysfs_read_vpd: read failed: Input/output error

     Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+

 
 
```
  

did a 
```
sudo lshw -numeric -class video 
 
  and got this:

                        display UNCLAIMED        

        description: VGA compatible controller

        product: Intel Corporation [8086:3EA0]

        vendor: Intel Corporation [8086]

        physical id: 2

        bus info: pci@0000:00:02.0

        version: 02

        width: 64 bits

        clock: 33MHz

        capabilities: pciexpress msi pm vga_controller bus_master cap_list

        configuration: latency=0

        resources: memory:c0000000-c0ffffff memory:b0000000-bfffffff ioport:4000(size=64) memory:c0000-dffff

```
  

```
did a                          cat /var/log/Xorg.0.log  
and got an overwhelmingly massive amount of info:

                        29.846]  

 X.Org X Server 1.20.4

 X Protocol Version 11, Revision 0

 [    29.846] Build Operating System: Linux 4.4.0-148-generic x86_64 Ubuntu

 [    29.846] Current Operating System: Linux jaime 5.0.0-25-generic #26~18.04.1-Ubuntu SMP Thu Aug 1 13:51:02 UTC 2019 x86_64

 [    29.846] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-5.0.0-25-generic root=UUID=15251b59-2713-4cca-8b76-2b3473f45d16 ro recovery nomodeset

 [    29.847] Build Date: 02 May 2019  08:06:54AM

 [    29.847] xorg-server-hwe-18.04 2:1.20.4-1ubuntu3~18.04.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))  

 [    29.847] Current version of pixman: 0.34.0

 [    29.847]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
     to make sure that you have the latest version.
 [    29.847] Markers: (--) probed, (**) from config file, (==) default setting,

     (++) from command line, (!!) notice, (II) informational,

     (WW) warning, (EE) error, (NI) not implemented, (??) unknown.

 [    29.847] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 20 18:14:53 2019

 [    29.933] (==) Using system config directory "/usr/share/X11/xorg.conf.d"

 [    29.953] (==) No Layout section.  Using the first Screen section.

 [    29.953] (==) No screen section available. Using defaults.
 [    29.953] (**) |-->Screen "Default Screen Section" (0)

 [    29.953] (**) |   |-->Monitor "<default monitor>"

 [    29.953] (==) No monitor specified for screen "Default Screen Section".

     Using a default monitor configuration.

 [    29.953] (==) Automatically adding devices

 [    29.953] (==) Automatically enabling devices

 [    29.954] (==) Automatically adding GPU devices

 [    29.954] (==) Automatically binding GPU devices
 [    29.954] (==) Max clients allowed: 256, resource mask: 0x1fffff

 [    30.020] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.

 [    30.020]     Entry deleted from font path.

 [    30.020] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.

 [    30.021]     Entry deleted from font path.

 [    30.021] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.

 [    30.021]     Entry deleted from font path.
 [    30.021] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
 [    30.021]     Entry deleted from font path.

 [    30.021] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.

 [    30.021]     Entry deleted from font path.

 [    30.021] (==) FontPath set to:

     /usr/share/fonts/X11/misc,

     /usr/share/fonts/X11/Type1,

     built-ins
 [    30.021] (==) ModulePath set to "/usr/lib/xorg/modules"
 [    30.021] (II) The server relies on udev to provide the list of input devices.
     If no devices become available, reconfigure udev or disable AutoAddDevices.

 [    30.021] (II) Loader magic: 0x55c999e1c020

 [    30.021] (II) Module ABI versions:

 [    30.021]     X.Org ANSI C Emulation: 0.4

 [    30.021]     X.Org Video Driver: 24.0
 [    30.021]     X.Org XInput driver : 24.1
 [    30.021]     X.Org Server Extension : 10.0
 [    30.023] (++) using VT number 7

 
 
 [    30.023] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration

 [    30.027] (--) PCI:*(0@0:2:0) 8086:3ea0:1028:08c9 rev 2, Mem @ 0xc0000000/16777216, 0xb0000000/268435456, I/O @ 0x00004000/64, BIOS @ 0x????????/131072

 [    30.027] (II) LoadModule: "glx"

 [    30.230] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
 [    30.402] (II) Module glx: vendor="X.Org Foundation"
 [    30.402]     compiled for 1.20.4, module version = 1.0.0

 [    30.402]     ABI class: X.Org Server Extension, version 10.0

 [    30.403] (==) Matched modesetting as autoconfigured driver 0

 [    30.403] (==) Matched fbdev as autoconfigured driver 1

 [    30.403] (==) Matched vesa as autoconfigured driver 2

 [    30.403] (==) Assigned the driver to the xf86ConfigLayout
 [    30.403] (II) LoadModule: "modesetting"

 [    30.403] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so

 [    30.423] (II) Module modesetting: vendor="X.Org Foundation"

 [    30.423]     compiled for 1.20.4, module version = 1.20.4

 [    30.423]     Module class: X.Org Video Driver

 [    30.423]     ABI class: X.Org Video Driver, version 24.0

 [    30.423] (II) LoadModule: "fbdev"
 [    30.424] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so

 [    30.432] (II) Module fbdev: vendor="X.Org Foundation"

 [    30.432]     compiled for 1.20.1, module version = 0.5.0

 [    30.432]     Module class: X.Org Video Driver
 [    30.432]     ABI class: X.Org Video Driver, version 24.0

 [    30.432] (II) LoadModule: "vesa"

 [    30.432] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so

 [    30.440] (II) Module vesa: vendor="X.Org Foundation"

 [    30.440]     compiled for 1.20.1, module version = 2.4.0

 [    30.440]     Module class: X.Org Video Driver

 [    30.440]     ABI class: X.Org Video Driver, version 24.0
 [    30.440] (II) modesetting: Driver for Modesetting Kernel Drivers: kms

 [    30.440] (II) FBDEV: driver for framebuffer: fbdev

 [    30.440] (II) VESA: driver for VESA chipsets: vesa

 [    30.448] (EE) open /dev/dri/card0: No such file or directory

 [    30.448] (WW) Falling back to old probe method for modesetting

 [    30.448] (EE) open /dev/dri/card0: No such file or directory

 [    30.448] (II) Loading sub module "fbdevhw"

 [    30.448] (II) LoadModule: "fbdevhw"

 [    30.448] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so

 [    30.479] (II) Module fbdevhw: vendor="X.Org Foundation"

 [    30.479]     compiled for 1.20.4, module version = 0.0.2
 [    30.479]     ABI class: X.Org Video Driver, version 24.0

 [    30.479] (**) FBDEV(1): claimed PCI slot 0@0:2:0

 [    30.479] (II) FBDEV(1): using default device

 [    30.479] (EE) Screen 0 deleted because of no matching config section.

 [    30.479] (II) UnloadModule: "modesetting"
 [    30.480] (II) FBDEV(0): Creating default Display subsection in Screen section

     "Default Screen Section" for depth/fbbpp 24/32

 [    30.480] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32

 [    30.480] (==) FBDEV(0): RGB weight 888

 [    30.480] (==) FBDEV(0): Default visual is TrueColor

 [    30.480] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)

 [    30.480] (II) FBDEV(0): hardware: EFI VGA (video memory: 4160kB)
 [    30.480] (II) FBDEV(0): checking modes against framebuffer device...

 [    30.480] (II) FBDEV(0): checking modes against monitor...

 [    30.480] (II) FBDEV(0): Virtual size is 1366x768 (pitch 1366)

 [    30.480] (**) FBDEV(0):  Built-in mode "current": 104.9 MHz, 60.5 kHz, 76.4 Hz

 [    30.480] (II) FBDEV(0): Modeline "current"x0.0  104.92  1366 1398 1566 1734  768 772 776 792 -hsync -vsync -csync (60.5 kHz b)

 [    30.480] (==) FBDEV(0): DPI set to (96, 96)

 [    30.480] (II) Loading sub module "fb"
 [    30.480] (II) LoadModule: "fb"
 [    30.480] (II) Loading /usr/lib/xorg/modules/libfb.so

 [    30.481] (II) Module fb: vendor="X.Org Foundation"

 [    30.481]     compiled for 1.20.4, module version = 1.0.0

 [    30.481]     ABI class: X.Org ANSI C Emulation, version 0.4

 [    30.481] (**) FBDEV(0): using shadow framebuffer

 [    30.481] (II) Loading sub module "shadow"

 [    30.481] (II) LoadModule: "shadow"

 [    30.481] (II) Loading /usr/lib/xorg/modules/libshadow.so

 [    30.482] (II) Module shadow: vendor="X.Org Foundation"
 [    30.482]     compiled for 1.20.4, module version = 1.1.0

 [    30.482]     ABI class: X.Org ANSI C Emulation, version 0.4

 [    30.482] (II) UnloadModule: "vesa"

 [    30.482] (II) Unloading vesa

 [    30.482] (II) FBDEV(0): FBIOBLANK: Invalid argument (Screen blanking not supported by kernel - disabling)
 [    30.547] (==) FBDEV(0): Backing store enabled

 [    30.549] (==) FBDEV(0): DPMS enabled

 [    30.549] (II) Initializing extension Generic Event Extension

 [    30.549] (II) Initializing extension SHAPE

 [    30.549] (II) Initializing extension MIT-SHM

 [    30.550] (II) Initializing extension XInputExtension

 [    30.551] (II) Initializing extension XTEST
 [    30.551] (II) Initializing extension BIG-REQUESTS

 [    30.551] (II) Initializing extension SYNC

 [    30.552] (II) Initializing extension XKEYBOARD

 [    30.552] (II) Initializing extension XC-MISC

 [    30.552] (II) Initializing extension SECURITY

 [    30.553] (II) Initializing extension XFIXES

 [    30.553] (II) Initializing extension RENDER
 [    30.553] (II) Initializing extension RANDR
 [    30.554] (II) Initializing extension COMPOSITE

 [    30.554] (II) Initializing extension DAMAGE

 [    30.554] (II) Initializing extension MIT-SCREEN-SAVER

 [    30.555] (II) Initializing extension DOUBLE-BUFFER

 [    30.555] (II) Initializing extension RECORD

 [    30.555] (II) Initializing extension DPMS
 [    30.555] (II) Initializing extension Present

 [    30.556] (II) Initializing extension DRI3

 [    30.556] (II) Initializing extension X-Resource

 [    30.556] (II) Initializing extension XVideo

 [    30.556] (II) Initializing extension XVideo-MotionCompensation

 [    30.556] (II) Initializing extension SELinux

 [    30.556] (II) SELinux: Disabled on system

 [    30.556] (II) Initializing extension GLX
 [    30.557] (II) AIGLX: Screen 0 is not DRI2 capable
 [    32.598] (II) IGLX: Loaded and initialized swrast

 [    32.598] (II) GLX: Initialized DRISWRAST GL provider for screen 0

 [    32.598] (II) Initializing extension XFree86-VidModeExtension

 [    32.599] (II) Initializing extension XFree86-DGA

 [    32.599] (II) Initializing extension XFree86-DRI

 [    32.606] (II) Initializing extension DRI2
 [    32.985] (II) config/udev: Adding input device Power Button (/dev/input/event3)
 [    32.985] (**) Power Button: Applying InputClass "libinput keyboard catchall"

 [    32.985] (II) LoadModule: "libinput"

 [    32.985] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so

 [    33.020] (II) Module libinput: vendor="X.Org Foundation"

 [    33.020]     compiled for 1.20.1, module version = 0.28.1

 [    33.020]     Module class: X.Org XInput Driver

 [    33.020]     ABI class: X.Org XInput driver, version 24.1
 [    33.020] (II) Using input driver 'libinput' for 'Power Button'

 [    33.020] (**) Power Button: always reports core events

 [    33.020] (**) Option "Device" "/dev/input/event3"

 [    33.020] (**) Option "_source" "server/udev"

 [    33.022] (II) event3  - Power Button: is tagged by udev as: Keyboard

 [    33.022] (II) event3  - Power Button: device is a keyboard
 [    33.022] (II) event3  - Power Button: device removed
 [    33.034] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"

 [    33.035] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)

 [    33.035] (**) Option "xkb_model" "pc105"

 [    33.035] (**) Option "xkb_layout" "us"

 [    33.036] (II) event3  - Power Button: is tagged by udev as: Keyboard

 [    33.036] (II) event3  - Power Button: device is a keyboard

 [    33.037] (II) config/udev: Adding input device Power Button (/dev/input/event1)

 [    33.037] (**) Power Button: Applying InputClass "libinput keyboard catchall"

 [    33.037] (II) Using input driver 'libinput' for 'Power Button'

 [    33.037] (**) Power Button: always reports core events

 [    33.037] (**) Option "Device" "/dev/input/event1"

 [    33.037] (**) Option "_source" "server/udev"

 [    33.038] (II) event1  - Power Button: is tagged by udev as: Keyboard

 [    33.038] (II) event1  - Power Button: device is a keyboard

 [    33.038] (II) event1  - Power Button: device removed

 [    33.058] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"

 [    33.058] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)

 [    33.058] (**) Option "xkb_model" "pc105"

 [    33.058] (**) Option "xkb_layout" "us"

 [    33.060] (II) event1  - Power Button: is tagged by udev as: Keyboard

 [    33.060] (II) event1  - Power Button: device is a keyboard

 [    33.061] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)

 [    33.061] (II) No input driver specified, ignoring this device.

 [    33.061] (II) This device may have been added with another device file.

 [    33.062] (II) config/udev: Adding input device Sleep Button (/dev/input/event2)

 [    33.062] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"

 [    33.062] (II) Using input driver 'libinput' for 'Sleep Button'

 [    33.062] (**) Sleep Button: always reports core events

 [    33.062] (**) Option "Device" "/dev/input/event2"

 [    33.063] (**) Option "_source" "server/udev"

 [    33.063] (II) event2  - Sleep Button: is tagged by udev as: Keyboard

 [    33.063] (II) event2  - Sleep Button: device is a keyboard

 [    33.063] (II) event2  - Sleep Button: device removed

 [    33.082] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2/event2"

 [    33.082] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 8)

 [    33.082] (**) Option "xkb_model" "pc105"

 [    33.082] (**) Option "xkb_layout" "us"

 [    33.084] (II) event2  - Sleep Button: is tagged by udev as: Keyboard

 [    33.084] (II) event2  - Sleep Button: device is a keyboard
 [    33.086] (II) config/udev: Adding input device Integrated_Webcam_HD: Integrate (/dev/input/event9)

 [    33.086] (**) Integrated_Webcam_HD: Integrate: Applying InputClass "libinput keyboard catchall"

 [    33.086] (II) Using input driver 'libinput' for 'Integrated_Webcam_HD: Integrate'
 [    33.086] (**) Integrated_Webcam_HD: Integrate: always reports core events

 [    33.086] (**) Option "Device" "/dev/input/event9"

 [    33.086] (**) Option "_source" "server/udev"

 [    33.087] (II) event9  - Integrated_Webcam_HD: Integrate: is tagged by udev as: Keyboard

 [    33.087] (II) event9  - Integrated_Webcam_HD: Integrate: device is a keyboard

 [    33.087] (II) event9  - Integrated_Webcam_HD: Integrate: device removed

 [    33.130] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input16/event9"

 [    33.130] (II) XINPUT: Adding extended input device "Integrated_Webcam_HD: Integrate" (type: KEYBOARD, id 9)

 [    33.130] (**) Option "xkb_model" "pc105"

 [    33.130] (**) Option "xkb_layout" "us"

 [    33.133] (II) event9  - Integrated_Webcam_HD: Integrate: is tagged by udev as: Keyboard

 [    33.133] (II) event9  - Integrated_Webcam_HD: Integrate: device is a keyboard

 [    33.134] (II) config/udev: Adding input device DELL08C9:00 04F3:30C4 Touchpad (/dev/input/event8)

 [    33.134] (**) DELL08C9:00 04F3:30C4 Touchpad: Applying InputClass "libinput touchpad catchall"

 [    33.135] (II) Using input driver 'libinput' for 'DELL08C9:00 04F3:30C4 Touchpad'

 [    33.135] (**) DELL08C9:00 04F3:30C4 Touchpad: always reports core events

 [    33.135] (**) Option "Device" "/dev/input/event8"

 [    33.135] (**) Option "_source" "server/udev"

 [    33.244] (II) event8  - DELL08C9:00 04F3:30C4 Touchpad: is tagged by udev as: Touchpad
 [    33.244] (II) event8  - DELL08C9:00 04F3:30C4 Touchpad: device is a touchpad

 [    33.244] (II) event8  - DELL08C9:00 04F3:30C4 Touchpad: device removed

 [    33.275] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:15.0/i2c_designware.0/i2c-0/i2c-DELL08C9:00/0018:04F3:30C4.0001/input/input14/event8"

 [    33.275] (II) XINPUT: Adding extended input device "DELL08C9:00 04F3:30C4 Touchpad" (type: TOUCHPAD, id 10)

 [    33.275] (**) Option "AccelerationScheme" "none"

 [    33.275] (**) DELL08C9:00 04F3:30C4 Touchpad: (accel) selected scheme none/0

 [    33.275] (**) DELL08C9:00 04F3:30C4 Touchpad: (accel) acceleration factor: 2.000
 [    33.275] (**) DELL08C9:00 04F3:30C4 Touchpad: (accel) acceleration threshold: 4

 [    33.278] (II) event8  - DELL08C9:00 04F3:30C4 Touchpad: is tagged by udev as: Touchpad

 [    33.278] (II) event8  - DELL08C9:00 04F3:30C4 Touchpad: device is a touchpad

 [    33.280] (II) config/udev: Adding input device DELL08C9:00 04F3:30C4 Touchpad (/dev/input/mouse1)

 [    33.280] (II) No input driver specified, ignoring this device.

 [    33.280] (II) This device may have been added with another device file.

 [    33.281] (II) config/udev: Adding input device Intel HID events (/dev/input/event6)

 [    33.281] (**) Intel HID events: Applying InputClass "libinput keyboard catchall"

 [    33.281] (II) Using input driver 'libinput' for 'Intel HID events'

 [    33.281] (**) Intel HID events: always reports core events

 [    33.281] (**) Option "Device" "/dev/input/event6"

 [    33.281] (**) Option "_source" "server/udev"

 [    33.282] (II) event6  - Intel HID events: is tagged by udev as: Keyboard

 [    33.282] (II) event6  - Intel HID events: device is a keyboard

 [    33.282] (II) event6  - Intel HID events: device removed

 [    33.306] (**) Option "config_info" "udev:/sys/devices/platform/INT33D5:00/input/input7/event6"

 [    33.306] (II) XINPUT: Adding extended input device "Intel HID events" (type: KEYBOARD, id 11)

 [    33.307] (**) Option "xkb_model" "pc105"

 [    33.307] (**) Option "xkb_layout" "us"

 [    33.308] (II) event6  - Intel HID events: is tagged by udev as: Keyboard

 [    33.308] (II) event6  - Intel HID events: device is a keyboard

 [    33.309] (II) config/udev: Adding input device Intel HID 5 button array (/dev/input/event7)

 [    33.310] (**) Intel HID 5 button array: Applying InputClass "libinput keyboard catchall"

 [    33.310] (II) Using input driver 'libinput' for 'Intel HID 5 button array'

 [    33.310] (**) Intel HID 5 button array: always reports core events

 [    33.310] (**) Option "Device" "/dev/input/event7"

 [    33.310] (**) Option "_source" "server/udev"

 [    33.311] (II) event7  - Intel HID 5 button array: is tagged by udev as: Keyboard

 [    33.311] (II) event7  - Intel HID 5 button array: device is a keyboard
 [    33.311] (II) event7  - Intel HID 5 button array: device removed

 [    33.330] (**) Option "config_info" "udev:/sys/devices/platform/INT33D5:00/input/input8/event7"

 [    33.330] (II) XINPUT: Adding extended input device "Intel HID 5 button array" (type: KEYBOARD, id 12)

 [    33.330] (**) Option "xkb_model" "pc105"

 [    33.330] (**) Option "xkb_layout" "us"

 [    33.332] (II) event7  - Intel HID 5 button array: is tagged by udev as: Keyboard
 [    33.332] (II) event7  - Intel HID 5 button array: device is a keyboard
 [    33.333] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event10)

 [    33.334] (**) Dell WMI hotkeys: Applying InputClass "libinput keyboard catchall"

 [    33.334] (II) Using input driver 'libinput' for 'Dell WMI hotkeys'

 [    33.334] (**) Dell WMI hotkeys: always reports core events

 [    33.334] (**) Option "Device" "/dev/input/event10"

 [    33.334] (**) Option "_source" "server/udev"

 [    33.335] (II) event10 - Dell WMI hotkeys: is tagged by udev as: Keyboard
 [    33.335] (II) event10 - Dell WMI hotkeys: device is a keyboard
 [    33.335] (II) event10 - Dell WMI hotkeys: device removed

 [    33.370] (**) Option "config_info" "udev:/sys/devices/platform/PNP0C14:02/wmi_bus/wmi_bus-PNP0C14:02/9DBB5994-A997-11DA-B012-B622A1EF5492/input/input12/event10"

 [    33.370] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 13)

 [    33.370] (**) Option "xkb_model" "pc105"

 [    33.370] (**) Option "xkb_layout" "us"
 [    33.373] (II) event10 - Dell WMI hotkeys: is tagged by udev as: Keyboard
 [    33.373] (II) event10 - Dell WMI hotkeys: device is a keyboard

 [    33.374] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)

 [    33.374] (**) AT Translated Set 2 keyboard: Applying InputClass "libinput keyboard catchall"

 [    33.374] (II) Using input driver 'libinput' for 'AT Translated Set 2 keyboard'

 [    33.374] (**) AT Translated Set 2 keyboard: always reports core events

 [    33.374] (**) Option "Device" "/dev/input/event4"
 [    33.374] (**) Option "_source" "server/udev"
 [    33.376] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard

 [    33.376] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard

 [    33.376] (II) event4  - AT Translated Set 2 keyboard: device removed

 [    33.394] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"

 [    33.394] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 14)

 [    33.394] (**) Option "xkb_model" "pc105"
 [    33.394] (**) Option "xkb_layout" "us"
 [    33.396] (II) event4  - AT Translated Set 2 keyboard: is tagged by udev as: Keyboard

 [    33.396] (II) event4  - AT Translated Set 2 keyboard: device is a keyboard

 [    33.398] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/event5)

 [    33.398] (**) ImPS/2 Logitech Wheel Mouse: Applying InputClass "libinput pointer catchall"

 [    33.398] (II) Using input driver 'libinput' for 'ImPS/2 Logitech Wheel Mouse'

 [    33.398] (**) ImPS/2 Logitech Wheel Mouse: always reports core events
 [    33.398] (**) Option "Device" "/dev/input/event5"

 [    33.398] (**) Option "_source" "server/udev"

 [    33.399] (II) event5  - ImPS/2 Logitech Wheel Mouse: is tagged by udev as: Mouse

 [    33.399] (II) event5  - ImPS/2 Logitech Wheel Mouse: device set to 400 DPI

 [    33.399] (II) event5  - ImPS/2 Logitech Wheel Mouse: device is a pointer

 [    33.399] (II) event5  - ImPS/2 Logitech Wheel Mouse: device removed

 [    33.442] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input6/event5"
 [    33.442] (II) XINPUT: Adding extended input device "ImPS/2 Logitech Wheel Mouse" (type: MOUSE, id 15)
 [    33.443] (**) Option "AccelerationScheme" "none"

 [    33.443] (**) ImPS/2 Logitech Wheel Mouse: (accel) selected scheme none/0

 [    33.443] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration factor: 2.000

 [    33.443] (**) ImPS/2 Logitech Wheel Mouse: (accel) acceleration threshold: 4

 [    33.445] (II) event5  - ImPS/2 Logitech Wheel Mouse: is tagged by udev as: Mouse

 [    33.445] (II) event5  - ImPS/2 Logitech Wheel Mouse: device set to 400 DPI

 [    33.445] (II) event5  - ImPS/2 Logitech Wheel Mouse: device is a pointer

 [    33.446] (II) config/udev: Adding input device ImPS/2 Logitech Wheel Mouse (/dev/input/mouse0)

 [    33.446] (II) No input driver specified, ignoring this device.

 [    33.446] (II) This device may have been added with another device file.

 [    75.194] (II) config/udev: Adding input device HDA Intel PCH Headphone Mic (/dev/input/event11)

 [    75.194] (II) No input driver specified, ignoring this device.

 [    75.194] (II) This device may have been added with another device file.

  
```


I spent a lot of time going through this, not sure how to interpret this, and am now considering that I am probably in way over my head. I previously used Cinnamon Mint and never had this kind of persistent issue, only minor ones that I could always resolve using my google skills. 

Would greatly appreciate it if someone could have a look at this and tell me whether I'm missing an obvious fix (preferred option, since I liked what I saw of Ubuntu) or if this is a permanent compatibility issue and I should just wipe Ubuntu and try a different distro instead.

---

### Post by oldfred on 2019-08-20
Please use Code Tags on longer terminal or text. Easy to add with Forum's advanced editor & # icon.
       How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Have you updated UEFI from Dell?

It looks like the Intel driver is not installed. But that should be automatic.
Your lshw should have this on configuration line:
configuration: driver=i915 latency=0
 
I do not think any of these in 3000 series systems had any video issues.
      
 Dell  Inspiron 3670 UEFI update & AHCI worked
[https://ubuntuforums.org/showthread.php?t=2412152](https://ubuntuforums.org/showthread.php?t=2412152)
Dell Inspiron 3567 Review i3 7100u (Works well)
[https://ubuntuforums.org/showthread.php?t=2364642](https://ubuntuforums.org/showthread.php?t=2364642)
Dell precison 3520 Turn off RAID & change to AHCI
[https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized](https://askubuntu.com/questions/1096492/installing-ubuntu-18-04-alongside-windows10-the-ssd-is-not-recognized) 
    

I would update UEFI and see what that does. Almost all have had to have UEFI updates. And if SSD firmware updates for SSD.
But otherwise not sure why Intel driver not automatically enabled.

If that does not work, lets see details, most related to boot issues, but may show something in boot that is causing issue. Do not run any suggested fixes, until reviewed by someone. Normally Boot-Repair works, but sometimes causes issues.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &

---

### Post by blueginpinktonic on 2019-08-21
Thank you so much for the response, and sorry about forgetting the code tags.

Updated Dell firmware and that fixed my problem. I always suspected I was missing something obvious!

---

### Post by oldfred on 2019-08-21
Please change to [Solved], above first post.

---

