---
title: "Terrible performance after upgrade to 14.04"
date: 2014-09-16
forum: Installation &amp; Upgrades
---

### Post by westeros on 2014-09-16
Hi all,After performing a release upgrade my system went terribly slow. I made the usual modifications like installing nvidia drivers etc, but nothing helped so far.Almost everything is slow. apt-get updates, booting the computer and so on. I found an weird thing though -- every time I boot the computer, it says "file not found, press enter to continue", after what it takes 2-4 minutes to load the system in an i7/16Gb RAM computer.

Also, when performing upgrades or package installations, it goes in an abnormal loop of errors like this:

 update-initramfs: Generating /boot/initrd.img-3.13.0-35-generic

cryptsetup: WARNING: failed to detect canonical device of /dev/sdb1
cryptsetup: WARNING: could not determine root device from /etc/fstab
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.


update-initramfs: Generating /boot/initrd.img-3.2.0-68-generic


cryptsetup: WARNING: failed to detect canonical device of /dev/sdb1
cryptsetup: WARNING: could not determine root device from /etc/fstab
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.0.0-19-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sdb1
cryptsetup: WARNING: could not determine root device from /etc/fstab
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sdb1
cryptsetup: WARNING: could not determine root device from /etc/fstab
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sdb1
cryptsetup: WARNING: could not determine root device from /etc/fstab
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sdb1
cryptsetup: WARNING: could not determine root device from /etc/fstab
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic


Since sdb1 is where my OS is, I suspect this can be the source of my problems. However, I don't know how to fix it.Any help is appreciated. Thanks in advance.

---

### Post by oldfred on 2014-09-16
I do not know Encryption and LVM type installs.
But you do seem to be having some issue with the LVM or encryption.

But it is updating old kernels? 2.6, 3.0 & 3.2?
I would review all the kernels you have installed and only keep a couple of recent ones.

       Check current kernel I also keep one older just in case:
#Current kernel:
uname -a

I prefer to use synaptic although you can use command line.
sudo apt-get install synaptic

 In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

 cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.8.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.8.0-{17,18,19,21,22,23,24}-generic


But some of those kernels look very old and new update may not even have those in your package list.
Then you have to just delete them with a rm command. If using rm be very careful to only delete old versions, best not to use any wildcards as a space in the wrong place can cause major issues.

---

### Post by westeros on 2014-09-16
Thanks oldfred.

I removed old kernels, although the newest one I have is this:

uname -a
Linux vader 3.2.0-68-generic #102-Ubuntu SMP Tue Aug 12 22:02:15 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

I think the boot time might give some clue, so I am attaching the bootchart image. It is taking more than 2 minutes to show the log in screen...

[IMG]http://i59.tinypic.com/mud64k.jpg[/IMG]

---

### Post by westeros on 2014-09-16
This is where the problem starts. Apparently it is related to usb ports...
Any clue on how to fix it ?

[   24.595472] r8169 0000:03:00.0: eth1: link up
[   24.596067] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   35.503432] eth1: no IPv6 routers present
[   49.058132] type=1400 audit(1410871555.050:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1390 comm="apparmor_parser"
[   49.058273] type=1400 audit(1410871555.050:8): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1390 comm="apparmor_parser"
[   49.567798] type=1400 audit(1410871555.562:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cups-browsed" pid=1412 comm="apparmor_parser"
[   62.287541] usb 3-3: USB disconnect, device number 2
[   63.779701] usb 3-3: new low-speed USB device number 5 using xhci_hcd
[   63.799322] usb 3-3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   63.802095] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input17
[   63.802194] generic-usb 0003:0458:003A.0004: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:14.0-3/input0
[  123.650875] usb 3-3: USB disconnect, device number 5
[  125.143972] usb 3-3: new low-speed USB device number 6 using xhci_hcd
[  125.163569] usb 3-3: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[  125.166413] input: Genius Optical Mouse as /devices/pci0000:00/0000:00:14.0/usb3/3-3/3-3:1.0/input/input18
[  125.166568] generic-usb 0003:0458:003A.0005: input,hidraw0: USB HID v1.11 Mouse [Genius Optical Mouse] on usb-0000:00:14.0-3/input0
[  145.353747] type=1400 audit(1410871651.590:10): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cups-browsed" pid=1535 comm="apparmor_parser"
[  145.353957] type=1400 audit(1410871651.590:11): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1532 comm="apparmor_parser"
[  145.354113] type=1400 audit(1410871651.590:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1532 comm="apparmor_parser"
[  145.354190] type=1400 audit(1410871651.590:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1532 comm="apparmor_parser"
[  145.354352] type=1400 audit(1410871651.590:14): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1536 comm="apparmor_parser"
[  145.354495] type=1400 audit(1410871651.590:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1536 comm="apparmor_parser"
[  145.435493] type=1400 audit(1410871651.670:16): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1537 comm="apparmor_parser"
[  145.435575] type=1400 audit(1410871651.670:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi///usr/sbin/mysqld" pid=1537 comm="apparmor_parser"
[  145.472363] type=1400 audit(1410871651.706:18): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1539 comm="apparmor_parser"
[  145.536560] type=1400 audit(1410871651.774:19): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session" pid=1531 comm="apparmor_parser"
[  145.852004] init: kdm main process (1618) killed by TERM signal
[  148.612346] init: plymouth-upstart-bridge main process ended, respawning
[  148.615388] init: plymouth-upstart-bridge main process (1935) terminated with status 1
[  148.615393] init: plymouth-upstart-bridge main process ended, respawning
[  149.342042] vboxdrv: Found 8 processor cores.
[  149.342158] vboxdrv: fAsync=0 offMin=0x1ea offMax=0x11f9
[  149.342202] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  149.342204] vboxdrv: Successfully loaded version 4.3.16 (interface 0x001a0007).
[  149.568345] vboxpci: IOMMU not found (not registered)
[  151.417078] init: plymouth-stop pre-start process (2327) terminated with status 1
[  155.733429] init: nvidia-persistenced main process (2496) terminated with status 1

---

### Post by oldfred on 2014-09-16
Usually Boot Charts are too tiny to really review when posted. But in general post screen shots as attachments not in line. You can easily do that with Advanced editor and paperclip icon.

I never learned Boot Chart anyway, but do use the dmesg log file you posted. With my SSD boot on an old system, my last entry is at 23.1 sec. And when I boot an install on hard drive it usually is not more than 30 or 40 sec. My system is part 2006 and part 2009, so not very current.

You show this:
[  149.568345] vboxpci: IOMMU not found (not registered)

Is this a Gigabyte motherboard?
       turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.

      
 IOMMU for USB3 ports Gigabyte board
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)
Linux kernel enable the IOMMU &#8211; input / output memory management unit support - AMD 
[http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html](http://www.cyberciti.biz/tips/howto-turn-on-linux-software-iommu-support.html)

---

### Post by matt_symes on 2014-09-16
Hi

Not wishing to step on any toes, i just had a couple of queries.

Is it still slow if you boot directly to a shell, by-passing the init system, and is it also slow when booting to a shell using the init system ?

Anything in you xorg log file ?

Kind regards

---

### Post by westeros on 2014-09-16
My MOBO is ASUS:
# dmidecode 2.12
SMBIOS 2.7 present.


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
        Manufacturer: ASUSTeK COMPUTER INC.
        Product Name: Z87M-PLUS
        Version: Rev X.0x
        Serial Number: 130511505902601
        Asset Tag: To be filled by O.E.M.
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: To be filled by O.E.M.
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0

I have changed the mouse to another USB port and it did not help. 

The OS is also weird in general, sometimes autocomplete is slow, chromium freezes "waiting for cache"... I definitely should not have moved from precise to trusty...

---

### Post by westeros on 2014-09-16
> **matt_symes said:**
> Hi

Not wishing to step on any toes, i just had a couple of queries.

Is it still slow if you boot directly to a shell, by-passing the init system, and is it also slow when booting to a shell using the init system ?

Anything in you xorg log file ?

Kind regards

Sorry, but how can I do that ?

---

### Post by matt_symes on 2014-09-16
Hi

To boot directly into a shell, bypassing the init system you need to edit your grub command line.


[LIST]
[*]Reboot your pc to get to the grub menu. 
[*]Select your kernel to boot and press e to edit the kernel command line. 
[*]Look for the line that says 
[*]```
**linux**
``` 
[/LIST]

[LIST]
[*]and move the cursor to the end of that line and add 
[*]```
init=/bin/bash
``` 
[*]Press F10 to continue booting and time the boot.
[/LIST]

Is the boot quick or slow ?

At the shell type ```
reboot
```

I'm using KDE with Fedora and openSUSE, not with Kubuntu but i assume it is the same process for Ubuntu, Xubuntu and Lubuntu as it is for Kubuntu.

Assuming it is, you need to create an override file for kdm in /etc/init.

Your xorg file is located in /var/log/xorg.0.log.

```
gedit /var/log/xorg.0.log
```

You may want to post that here.

As oldfred suggested, try enabling the IOMMU in the BIOS.

Kind regards

---

### Post by westeros on 2014-09-16
Please find enclosed the contents of Xorg log file.
As of now I do not have a grub menu, but I will try to recover it. Also, I don't know where in my BIOS in can turn IOMMU on, but I will also search for it.
cat /var/log/Xorg.0.log
[   147.020] 
```
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   147.020] X Protocol Version 11, Revision 0
[   147.020] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[   147.020] Current Operating System: Linux vader 3.2.0-68-generic #102-Ubuntu SMP Tue Aug 12 22:02:15 UTC 2014 x86_64
[   147.020] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-68-generic root=UUID=8c9a80f7-6e6d-4900-a989-9b02985e28a2 ro quiet splash nomdmonddf nomdmonisw nomdmonddf nomdmonisw vt.handoff=7
[   147.020] Build Date: 30 July 2014  12:21:54AM
[   147.020] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   147.020] Current version of pixman: 0.30.2
[   147.020]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[   147.020] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   147.020] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Sep 16 14:42:17 2014
[   147.043] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   147.240] (==) No Layout section.  Using the first Screen section.
[   147.240] (==) No screen section available. Using defaults.
[   147.240] (**) |-->Screen "Default Screen Section" (0)
[   147.240] (**) |   |-->Monitor "<default monitor>"
[   147.240] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[   147.240] (==) Automatically adding devices
[   147.240] (==) Automatically enabling devices
[   147.240] (==) Automatically adding GPU devices
[   147.257] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   147.257]    Entry deleted from font path.
[   147.261] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,                                                                       
        /usr/share/fonts/X11/75dpi/:unscaled,                                                                        
        /usr/share/fonts/X11/Type1,                                                                                  
        /usr/share/fonts/X11/100dpi,                                                                                 
        /usr/share/fonts/X11/75dpi,                                                                                  
        built-ins                                                                                                    
[   147.261] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"                                                                                                      
[   147.261] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[   147.261] (II) Loader magic: 0x7f31cf8ebd40
[   147.261] (II) Module ABI versions:
[   147.261]    X.Org ANSI C Emulation: 0.4
[   147.261]    X.Org Video Driver: 15.0
[   147.261]    X.Org XInput driver : 20.0
[   147.261]    X.Org Server Extension : 8.0
[   147.262] (--) PCI:*(0:1:0:0) 10de:0fc1:3842:2645 rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   147.297] Initializing built-in extension Generic Event Extension
[   147.297] Initializing built-in extension SHAPE
[   147.297] Initializing built-in extension MIT-SHM
[   147.297] Initializing built-in extension XInputExtension
[   147.297] Initializing built-in extension XTEST
[   147.297] Initializing built-in extension BIG-REQUESTS
[   147.297] Initializing built-in extension SYNC
[   147.297] Initializing built-in extension XKEYBOARD
[   147.297] Initializing built-in extension XC-MISC
[   147.297] Initializing built-in extension SECURITY
[   147.297] Initializing built-in extension XINERAMA
[   147.297] Initializing built-in extension XFIXES
[   147.297] Initializing built-in extension RENDER
[   147.297] Initializing built-in extension RANDR
[   147.297] Initializing built-in extension COMPOSITE
[   147.297] Initializing built-in extension DAMAGE
[   147.297] Initializing built-in extension MIT-SCREEN-SAVER
[   147.297] Initializing built-in extension DOUBLE-BUFFER
[   147.297] Initializing built-in extension RECORD
[   147.297] Initializing built-in extension DPMS
[   147.297] Initializing built-in extension Present
[   147.297] Initializing built-in extension DRI3
[   147.297] Initializing built-in extension X-Resource
[   147.297] Initializing built-in extension XVideo
[   147.297] Initializing built-in extension XVideo-MotionCompensation
[   147.297] Initializing built-in extension SELinux
[   147.297] Initializing built-in extension XFree86-VidModeExtension
[   147.297] Initializing built-in extension XFree86-DGA
[   147.297] Initializing built-in extension XFree86-DRI
[   147.297] Initializing built-in extension DRI2
[   147.297] (II) LoadModule: "glx"
[   147.337] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   147.488] (II) Module glx: vendor="X.Org Foundation"
[   147.488]    compiled for 1.15.1, module version = 1.0.0
[   147.488]    ABI class: X.Org Server Extension, version 8.0
[   147.488] (==) AIGLX enabled
[   147.488] Loading extension GLX
[   147.488] (==) Matched nvidia as autoconfigured driver 0
[   147.488] (==) Matched nouveau as autoconfigured driver 1
[   147.488] (==) Matched modesetting as autoconfigured driver 2
[   147.488] (==) Matched fbdev as autoconfigured driver 3
[   147.488] (==) Matched vesa as autoconfigured driver 4
[   147.488] (==) Assigned the driver to the xf86ConfigLayout
[   147.488] (II) LoadModule: "nvidia"
[   147.489] (WW) Warning, couldn't open module nvidia
[   147.489] (II) UnloadModule: "nvidia"
[   147.489] (II) Unloading nvidia
[   147.489] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   147.489] (II) LoadModule: "nouveau"
[   147.489] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   147.521] (II) Module nouveau: vendor="X.Org Foundation"
[   147.521]    compiled for 1.15.1, module version = 1.0.11
[   147.521]    Module class: X.Org Video Driver
[   147.521]    ABI class: X.Org Video Driver, version 15.0
[   147.521] (II) LoadModule: "modesetting"
[   147.521] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   147.540] (II) Module modesetting: vendor="X.Org Foundation"
[   147.540]    compiled for 1.15.0, module version = 0.8.1
[   147.540]    Module class: X.Org Video Driver
[   147.540]    ABI class: X.Org Video Driver, version 15.0
[   147.540] (II) LoadModule: "fbdev"
[   147.540] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   147.540] (II) Module fbdev: vendor="X.Org Foundation"
[   147.540]    compiled for 1.15.0, module version = 0.4.4
[   147.540]    Module class: X.Org Video Driver
[   147.540]    ABI class: X.Org Video Driver, version 15.0
[   147.540] (II) LoadModule: "vesa"
[   147.540] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   147.540] (II) Module vesa: vendor="X.Org Foundation"
[   147.540]    compiled for 1.15.0, module version = 2.3.3
[   147.540]    Module class: X.Org Video Driver
[   147.540]    ABI class: X.Org Video Driver, version 15.0
[   147.540] (==) Matched nvidia as autoconfigured driver 0
[   147.540] (==) Matched nouveau as autoconfigured driver 1
[   147.540] (==) Matched modesetting as autoconfigured driver 2
[   147.540] (==) Matched fbdev as autoconfigured driver 3
[   147.540] (==) Matched vesa as autoconfigured driver 4
[   147.540] (==) Assigned the driver to the xf86ConfigLayout
[   147.540] (II) LoadModule: "nvidia"
[   147.540] (WW) Warning, couldn't open module nvidia
[   147.540] (II) UnloadModule: "nvidia"
[   147.540] (II) Unloading nvidia
[   147.540] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   147.540] (II) LoadModule: "nouveau"
[   147.540] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[   147.540] (II) Module nouveau: vendor="X.Org Foundation"
[   147.540]    compiled for 1.15.1, module version = 1.0.11
[   147.540]    Module class: X.Org Video Driver
[   147.540]    ABI class: X.Org Video Driver, version 15.0
[   147.540] (II) UnloadModule: "nouveau"
[   147.540] (II) Unloading nouveau
[   147.540] (II) Failed to load module "nouveau" (already loaded, 0)
[   147.540] (II) LoadModule: "modesetting"
[   147.540] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   147.540] (II) Module modesetting: vendor="X.Org Foundation"
[   147.540]    compiled for 1.15.0, module version = 0.8.1
[   147.540]    Module class: X.Org Video Driver
[   147.540]    ABI class: X.Org Video Driver, version 15.0
[   147.540] (II) UnloadModule: "modesetting"
[   147.540] (II) Unloading modesetting
[   147.540] (II) Failed to load module "modesetting" (already loaded, 0)
[   147.540] (II) LoadModule: "fbdev"
[   147.540] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   147.540] (II) Module fbdev: vendor="X.Org Foundation"
[   147.540]    compiled for 1.15.0, module version = 0.4.4
[   147.541]    Module class: X.Org Video Driver
[   147.541]    ABI class: X.Org Video Driver, version 15.0
[   147.541] (II) UnloadModule: "fbdev"
[   147.541] (II) Unloading fbdev
[   147.541] (II) Failed to load module "fbdev" (already loaded, 0)
[   147.541] (II) LoadModule: "vesa"
[   147.541] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   147.541] (II) Module vesa: vendor="X.Org Foundation"
[   147.541]    compiled for 1.15.0, module version = 2.3.3
[   147.541]    Module class: X.Org Video Driver
[   147.541]    ABI class: X.Org Video Driver, version 15.0
[   147.541] (II) UnloadModule: "vesa"
[   147.541] (II) Unloading vesa
[   147.541] (II) Failed to load module "vesa" (already loaded, 0)
[   147.541] (II) NOUVEAU driver 
[   147.541] (II) NOUVEAU driver for NVIDIA chipset families :
[   147.541]    RIVA TNT        (NV04)
[   147.541]    RIVA TNT2       (NV05)
[   147.541]    GeForce 256     (NV10)
[   147.541]    GeForce 2       (NV11, NV15)
[   147.541]    GeForce 4MX     (NV17, NV18)
[   147.541]    GeForce 3       (NV20)
[   147.541]    GeForce 4Ti     (NV25, NV28)
[   147.541]    GeForce FX      (NV3x)
[   147.541]    GeForce 6       (NV4x)
[   147.541]    GeForce 7       (G7x)
[   147.541]    GeForce 8       (G8x)
[   147.541]    GeForce GTX 200 (NVA0)
[   147.541]    GeForce GTX 400 (NVC0)
[   147.541] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   147.541] (II) FBDEV: driver for framebuffer: fbdev
[   147.541] (II) VESA: driver for VESA chipsets: vesa
[   147.541] (++) using VT number 7


[   147.541] (EE) [drm] KMS not enabled
[   147.541] (EE) [drm] KMS not enabled
[   147.541] (EE) open /dev/dri/card0: No such file or directory
[   147.541] (EE) open /dev/dri/card0: No such file or directory
[   147.541] (WW) Falling back to old probe method for modesetting
[   147.541] (EE) open /dev/dri/card0: No such file or directory
[   147.541] (EE) open /dev/dri/card0: No such file or directory
[   147.541] (II) Loading sub module "fbdevhw"
[   147.541] (II) LoadModule: "fbdevhw"
[   147.541] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   147.561] (II) Module fbdevhw: vendor="X.Org Foundation"
[   147.561]    compiled for 1.15.1, module version = 0.0.2
[   147.561]    ABI class: X.Org Video Driver, version 15.0
[   147.561] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[   147.561] (II) FBDEV(2): using default device
[   147.561] (WW) Falling back to old probe method for vesa
[   147.561] (EE) Screen 0 deleted because of no matching config section.
[   147.561] (II) UnloadModule: "modesetting"
[   147.561] (EE) Screen 0 deleted because of no matching config section.
[   147.561] (II) UnloadModule: "modesetting"
[   147.561] (II) FBDEV(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[   147.561] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[   147.561] (==) FBDEV(0): RGB weight 888
[   147.561] (==) FBDEV(0): Default visual is TrueColor
[   147.561] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[   147.561] (II) FBDEV(0): hardware: VESA VGA (video memory: 10816kB)
[   147.561] (II) FBDEV(0): checking modes against framebuffer device...
[   147.561] (II) FBDEV(0): checking modes against monitor...
[   147.561] (--) FBDEV(0): Virtual size is 2560x1080 (pitch 2560)
[   147.561] (**) FBDEV(0):  Built-in mode "current": 276.5 MHz, 101.7 kHz, 92.1 Hz
[   147.561] (II) FBDEV(0): Modeline "current"x0.0  276.55  2560 2592 2656 2720  1080 1084 1088 1104 -hsync -vsync -csync (101.7 kHz b)
[   147.561] (==) FBDEV(0): DPI set to (96, 96)
[   147.561] (II) Loading sub module "fb"
[   147.561] (II) LoadModule: "fb"
[   147.561] (II) Loading /usr/lib/xorg/modules/libfb.so
[   147.572] (II) Module fb: vendor="X.Org Foundation"
[   147.572]    compiled for 1.15.1, module version = 1.0.0
[   147.572]    ABI class: X.Org ANSI C Emulation, version 0.4
[   147.572] (**) FBDEV(0): using shadow framebuffer
[   147.572] (II) Loading sub module "shadow"
[   147.572] (II) LoadModule: "shadow"
[   147.572] (II) Loading /usr/lib/xorg/modules/libshadow.so
[   147.604] (II) Module shadow: vendor="X.Org Foundation"
[   147.604]    compiled for 1.15.1, module version = 1.1.0
[   147.604]    ABI class: X.Org ANSI C Emulation, version 0.4
[   147.604] (II) UnloadModule: "vesa"
[   147.604] (II) Unloading vesa
[   147.604] (==) Depth 24 pixmap format is 32 bpp
[   147.605] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   147.625] (==) FBDEV(0): Backing store enabled
[   147.626] (==) FBDEV(0): DPMS enabled
[   147.626] (==) RandR enabled
[   147.628] (II) SELinux: Disabled on system
[   147.629] (II) AIGLX: Screen 0 is not DRI2 capable
[   147.629] (EE) AIGLX: reverting to software rendering
[   148.120] (II) AIGLX: Loaded and initialized swrast
[   148.122] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[   148.322] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   148.328] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   148.328] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   148.328] (II) LoadModule: "evdev"
[   148.328] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   148.356] (II) Module evdev: vendor="X.Org Foundation"
[   148.356]    compiled for 1.15.0, module version = 2.8.2
[   148.356]    Module class: X.Org XInput Driver
[   148.356]    ABI class: X.Org XInput driver, version 20.0
[   148.356] (II) Using input driver 'evdev' for 'Power Button'
[   148.356] (**) Power Button: always reports core events
[   148.356] (**) evdev: Power Button: Device: "/dev/input/event1"
[   148.356] (--) evdev: Power Button: Vendor 0 Product 0x1
[   148.356] (--) evdev: Power Button: Found keys
[   148.356] (II) evdev: Power Button: Configuring as keyboard
[   148.356] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   148.356] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   148.356] (**) Option "xkb_rules" "evdev"
[   148.356] (**) Option "xkb_model" "a4techKB21"
[   148.356] (**) Option "xkb_layout" "br"
[   148.358] (II) XKB: reuse xkmfile /var/lib/xkb/server-20278E27F1DC9FDDFD591DABFB86C7D7989CFCCF.xkm
[   148.372] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   148.372] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   148.372] (II) Using input driver 'evdev' for 'Power Button'
[   148.372] (**) Power Button: always reports core events
[   148.372] (**) evdev: Power Button: Device: "/dev/input/event0"
[   148.372] (--) evdev: Power Button: Vendor 0 Product 0x1
[   148.372] (--) evdev: Power Button: Found keys
[   148.372] (II) evdev: Power Button: Configuring as keyboard
[   148.372] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   148.372] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   148.372] (**) Option "xkb_rules" "evdev"
[   148.372] (**) Option "xkb_model" "a4techKB21"
[   148.372] (**) Option "xkb_layout" "br"
[   148.373] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=8 (/dev/input/event14)
[   148.373] (II) No input driver specified, ignoring this device.
[   148.373] (II) This device may have been added with another device file.
[   148.373] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=7 (/dev/input/event15)
[   148.373] (II) No input driver specified, ignoring this device.
[   148.373] (II) This device may have been added with another device file.
[   148.373] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 (/dev/input/event16)
[   148.373] (II) No input driver specified, ignoring this device.
[   148.373] (II) This device may have been added with another device file.
[   148.373] (II) config/udev: Adding input device Chicony Multimedia Keyboard (/dev/input/event2)
[   148.373] (**) Chicony Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[   148.373] (II) Using input driver 'evdev' for 'Chicony Multimedia Keyboard'
[   148.373] (**) Chicony Multimedia Keyboard: always reports core events
[   148.373] (**) evdev: Chicony Multimedia Keyboard: Device: "/dev/input/event2"
[   148.373] (--) evdev: Chicony Multimedia Keyboard: Vendor 0x4f2 Product 0x736
[   148.373] (--) evdev: Chicony Multimedia Keyboard: Found keys
[   148.373] (II) evdev: Chicony Multimedia Keyboard: Configuring as keyboard
[   148.373] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-13/2-13:1.0/input/input2/event2"
[   148.373] (II) XINPUT: Adding extended input device "Chicony Multimedia Keyboard" (type: KEYBOARD, id 8)
[   148.373] (**) Option "xkb_rules" "evdev"
[   148.373] (**) Option "xkb_model" "a4techKB21"
[   148.373] (**) Option "xkb_layout" "br"
[   148.373] (II) config/udev: Adding input device Chicony Multimedia Keyboard (/dev/input/event3)
[   148.373] (**) Chicony Multimedia Keyboard: Applying InputClass "evdev keyboard catchall"
[   148.373] (II) Using input driver 'evdev' for 'Chicony Multimedia Keyboard'
[   148.373] (**) Chicony Multimedia Keyboard: always reports core events
[   148.373] (**) evdev: Chicony Multimedia Keyboard: Device: "/dev/input/event3"
[   148.373] (--) evdev: Chicony Multimedia Keyboard: Vendor 0x4f2 Product 0x736
[   148.373] (--) evdev: Chicony Multimedia Keyboard: Found keys
[   148.373] (II) evdev: Chicony Multimedia Keyboard: Configuring as keyboard
[   148.373] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-13/2-13:1.1/input/input3/event3"
[   148.373] (II) XINPUT: Adding extended input device "Chicony Multimedia Keyboard" (type: KEYBOARD, id 9)
[   148.373] (**) Option "xkb_rules" "evdev"
[   148.373] (**) Option "xkb_model" "a4techKB21"
[   148.373] (**) Option "xkb_layout" "br"
[   148.374] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/event4)
[   148.374] (**) Genius Optical Mouse: Applying InputClass "evdev pointer catchall"
[   148.374] (II) Using input driver 'evdev' for 'Genius Optical Mouse'
[   148.374] (**) Genius Optical Mouse: always reports core events
[   148.374] (**) evdev: Genius Optical Mouse: Device: "/dev/input/event4"
[   148.374] (--) evdev: Genius Optical Mouse: Vendor 0x458 Product 0x3a
[   148.374] (--) evdev: Genius Optical Mouse: Found 3 mouse buttons
[   148.374] (--) evdev: Genius Optical Mouse: Found scroll wheel(s)
[   148.374] (--) evdev: Genius Optical Mouse: Found relative axes
[   148.374] (--) evdev: Genius Optical Mouse: Found x and y relative axes
[   148.374] (II) evdev: Genius Optical Mouse: Configuring as mouse
[   148.374] (II) evdev: Genius Optical Mouse: Adding scrollwheel support
[   148.374] (**) evdev: Genius Optical Mouse: YAxisMapping: buttons 4 and 5
[   148.374] (**) evdev: Genius Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   148.374] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb2/2-14/2-14:1.0/input/input18/event4"
[   148.374] (II) XINPUT: Adding extended input device "Genius Optical Mouse" (type: MOUSE, id 10)
[   148.374] (II) evdev: Genius Optical Mouse: initialized for relative axes.
[   148.374] (**) Genius Optical Mouse: (accel) keeping acceleration scheme 1
[   148.374] (**) Genius Optical Mouse: (accel) acceleration profile 0
[   148.374] (**) Genius Optical Mouse: (accel) acceleration factor: 2.000
[   148.374] (**) Genius Optical Mouse: (accel) acceleration threshold: 4
[   148.374] (II) config/udev: Adding input device Genius Optical Mouse (/dev/input/mouse0)
[   148.374] (II) No input driver specified, ignoring this device.
[   148.374] (II) This device may have been added with another device file.
[   148.374] (II) config/udev: Adding input device HDA Intel PCH Line-Out Side (/dev/input/event10)
[   148.374] (II) No input driver specified, ignoring this device.
[   148.374] (II) This device may have been added with another device file.
[   148.374] (II) config/udev: Adding input device HDA Intel PCH Line-Out CLFE (/dev/input/event11)
[   148.374] (II) No input driver specified, ignoring this device.
[   148.374] (II) This device may have been added with another device file.
[   148.374] (II) config/udev: Adding input device HDA Intel PCH Line-Out Surround (/dev/input/event12)
[   148.374] (II) No input driver specified, ignoring this device.
[   148.374] (II) This device may have been added with another device file.
[   148.374] (II) config/udev: Adding input device HDA Intel PCH Line-Out Front (/dev/input/event13)
[   148.374] (II) No input driver specified, ignoring this device.
[   148.374] (II) This device may have been added with another device file.
[   148.374] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[   148.374] (II) No input driver specified, ignoring this device.
[   148.374] (II) This device may have been added with another device file.
[   148.374] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event7)
[   148.374] (II) No input driver specified, ignoring this device.
[   148.374] (II) This device may have been added with another device file.
[   148.375] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event8)
[   148.375] (II) No input driver specified, ignoring this device.
[   148.375] (II) This device may have been added with another device file.
[   148.375] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event9)
[   148.375] (II) No input driver specified, ignoring this device.
[   148.375] (II) This device may have been added with another device file.
[   148.375] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event5)
[   148.375] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   148.375] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[   148.375] (**) Eee PC WMI hotkeys: always reports core events
[   148.375] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event5"
[   148.375] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[   148.375] (--) evdev: Eee PC WMI hotkeys: Found keys
[   148.375] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[   148.375] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input5/event5"
[   148.375] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[   148.375] (**) Option "xkb_rules" "evdev"
[   148.375] (**) Option "xkb_model" "a4techKB21"
[   148.375] (**) Option "xkb_layout" "br"
[   148.376] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   487.618] (EE) FBDEV(0): FBIOBLANK: Invalid argument
[   487.635] (EE) FBDEV(0): FBIOBLANK: Invalid argument
```

---

### Post by matt_symes on 2014-09-16
Hi

I can't see much wrong with your xorg.0.log file. It looks to be booting quickly with no problems so, hopefully, that can be discounted.

You may need to press and hold the shift key at reboot to see the grub menu.

Kind regards

---

### Post by oldfred on 2014-09-16
Please use code tags on long text output.
You can easily add code tags with Advanced Editor and # icon.

This is a newer one but may be some of the same issues:
 Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)

---

