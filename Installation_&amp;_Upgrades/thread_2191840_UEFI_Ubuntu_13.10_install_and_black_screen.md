---
title: "UEFI Ubuntu 13.10 install and black screen"
date: 2013-12-04
forum: Installation &amp; Upgrades
---

### Post by The average internet guy on 2013-12-04
I have successfully installed Ubuntu 13.10 on my new Asus UX302LG laptop by disabling Secure Boot and running Boot-Repair as recommended elsewhere. Upon booting my machine I can choose from several different versions in Grub, one of which is to boot Windows 8 normally (specifically: Windows 8 UEFI  Loader), and another is to boot Ubuntu normally. Booting Windows 8 works fine, but when I try to boot Ubuntu I get the login sound, but a black screen (back light is on however). I have tried to change "quiet splash" to "nomodeset" in the Grub launch script for Ubuntu (as that was necessary in the LiveUSB installation), but that only launches a terminal interface. How can I fix the boot to properly run Ubuntu with a proper X server?

EDIT: Running Ubuntu with failsafex shows that the X server fails when launching extension GLX with the error: No screen found. What does this mean?

---

### Post by The average internet guy on 2013-12-04
For reference, this is the full /var/log/Xorg.failsafe.log if it's any use:

```
[   429.013] 
X.Org X Server 1.14.3
Release Date: 2013-09-12
[   429.014] X Protocol Version 11, Revision 0
[   429.015] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[   429.015] Current Operating System: Linux christian-UX302LG 3.11.0-14-generic #21-Ubuntu SMP Tue Nov 12 17:04:55 UTC 2013 x86_64
[   429.015] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic root=UUID=14faff40-3101-44b7-94a8-71db732808b6 ro recovery nomodeset
[   429.017] Build Date: 15 October 2013  09:23:37AM
[   429.017] xorg-server 2:1.14.3-3ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[   429.018] Current version of pixman: 0.30.2
[   429.019]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[   429.019] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   429.021] (++) Log file: "/var/log/Xorg.failsafe.log", Time: Wed Dec  4 22:22:36 2013
[   429.022] (++) Using config file: "/etc/X11/xorg.conf.failsafe"
[   429.023] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   429.023] (==) No Layout section.  Using the first Screen section.
[   429.023] (**) |-->Screen "Default Screen" (0)
[   429.023] (**) |   |-->Monitor "Configured Monitor"
[   429.023] (**) |   |-->Device "Configured Video Device"
[   429.023] (==) Automatically adding devices
[   429.023] (==) Automatically enabling devices
[   429.023] (==) Automatically adding GPU devices
[   429.023] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   429.023]     Entry deleted from font path.
[   429.023] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   429.023]     Entry deleted from font path.
[   429.023] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   429.023]     Entry deleted from font path.
[   429.023] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   429.023]     Entry deleted from font path.
[   429.023] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   429.023]     Entry deleted from font path.
[   429.023] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   429.023] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   429.023] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   429.023] (II) Loader magic: 0x7fa9970a6d20
[   429.023] (II) Module ABI versions:
[   429.023]     X.Org ANSI C Emulation: 0.4
[   429.023]     X.Org Video Driver: 14.1
[   429.023]     X.Org XInput driver : 19.1
[   429.023]     X.Org Server Extension : 7.0
[   429.024] (--) PCI:*(0:0:2:0) 8086:0a16:1043:13ad rev 9, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[   429.024] (--) PCI: (0:4:0:0) 10de:1290:1043:13ad rev 161, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[   429.024] (WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
[   429.025] Initializing built-in extension Generic Event Extension
[   429.025] Initializing built-in extension SHAPE
[   429.026] Initializing built-in extension MIT-SHM
[   429.027] Initializing built-in extension XInputExtension
[   429.027] Initializing built-in extension XTEST
[   429.028] Initializing built-in extension BIG-REQUESTS
[   429.029] Initializing built-in extension SYNC
[   429.029] Initializing built-in extension XKEYBOARD
[   429.030] Initializing built-in extension XC-MISC
[   429.030] Initializing built-in extension SECURITY
[   429.031] Initializing built-in extension XINERAMA
[   429.032] Initializing built-in extension XFIXES
[   429.032] Initializing built-in extension RENDER
[   429.033] Initializing built-in extension RANDR
[   429.033] Initializing built-in extension COMPOSITE
[   429.034] Initializing built-in extension DAMAGE
[   429.035] Initializing built-in extension MIT-SCREEN-SAVER
[   429.035] Initializing built-in extension DOUBLE-BUFFER
[   429.036] Initializing built-in extension RECORD
[   429.036] Initializing built-in extension DPMS
[   429.037] Initializing built-in extension X-Resource
[   429.038] Initializing built-in extension XVideo
[   429.038] Initializing built-in extension XVideo-MotionCompensation
[   429.039] Initializing built-in extension SELinux
[   429.039] Initializing built-in extension XFree86-VidModeExtension
[   429.040] Initializing built-in extension XFree86-DGA
[   429.041] Initializing built-in extension XFree86-DRI
[   429.041] Initializing built-in extension DRI2
[   429.041] (II) "glx" will be loaded by default.
[   429.041] (WW) "xmir" is not to be loaded by default. Skipping.
[   429.041] (II) LoadModule: "dri2"
[   429.041] (II) Module "dri2" already built-in
[   429.041] (II) LoadModule: "glamoregl"
[   429.041] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   429.042] (II) Module glamoregl: vendor="X.Org Foundation"
[   429.042]     compiled for 1.14.2.901, module version = 0.5.1
[   429.042]     ABI class: X.Org ANSI C Emulation, version 0.4
[   429.042] (II) LoadModule: "glx"
[   429.042] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   429.042] (II) Module glx: vendor="X.Org Foundation"
[   429.042]     compiled for 1.14.3, module version = 1.0.0
[   429.042]     ABI class: X.Org Server Extension, version 7.0
[   429.042] (==) AIGLX enabled
[   429.043] Loading extension GLX
[   429.043] (II) LoadModule: "vesa"
[   429.043] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   429.043] (II) Module vesa: vendor="X.Org Foundation"
[   429.043]     compiled for 1.14.1, module version = 2.3.2
[   429.043]     Module class: X.Org Video Driver
[   429.043]     ABI class: X.Org Video Driver, version 14.1
[   429.043] (II) VESA: driver for VESA chipsets: vesa
[   429.043] (--) using VT number 2


[   429.047] (II) Loading sub module "vbe"
[   429.047] (II) LoadModule: "vbe"
[   429.047] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   429.047] (II) Module vbe: vendor="X.Org Foundation"
[   429.047]     compiled for 1.14.3, module version = 1.1.0
[   429.047]     ABI class: X.Org Video Driver, version 14.1
[   429.047] (II) Loading sub module "int10"
[   429.047] (II) LoadModule: "int10"
[   429.047] (II) Loading /usr/lib/xorg/modules/libint10.so
[   429.047] (II) Module int10: vendor="X.Org Foundation"
[   429.047]     compiled for 1.14.3, module version = 1.0.0
[   429.047]     ABI class: X.Org Video Driver, version 14.1
[   429.047] (II) VESA(0): initializing int10
[   429.047] (EE) VESA(0): V_BIOS address 0xd00 out of range
[   429.047] (II) UnloadModule: "vesa"
[   429.047] (II) UnloadSubModule: "int10"
[   429.047] (II) Unloading int10
[   429.047] (II) UnloadSubModule: "vbe"
[   429.047] (II) Unloading vbe
[   429.047] (EE) Screen(s) found, but none have a usable configuration.
[   429.047] (EE) 
Fatal server error:
[   429.047] (EE) no screens found(EE) 
[   429.047] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   429.047] (EE) Please also check the log file at "/var/log/Xorg.failsafe.log" for additional information.
[   429.047] (EE) 
[   429.054] (EE) Server terminated with error (1). Closing log file.



```

---

### Post by oldfred on 2013-12-04
Changed quote tags to code tags.

What video card/chip do you have?

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If Intel other settings may be required, depending on chip version.

---

### Post by The average internet guy on 2013-12-05
> **oldfred said:**
> Changed quote tags to code tags.

What video card/chip do you have?

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If Intel other settings may be required, depending on chip version.

Thank you for your reply. I have an integrated Intel 4400 HD and a Nvidia Geforce GT 730 2GB. 

I set nomodeset when I installed from the LiveUSB (and that fixed the black screen issue there). If I set nomodeset in grub when I boot, Ubuntu loads properly but I only have a terminal and no normal desktop.

---

### Post by The average internet guy on 2013-12-05
I now managed to get Ubuntu to work by reinstalling it again, this time with an internet connection and ticking the "Download updates while installing" (or something along those lines). I also added the "Add a kernel option" with nomodeset when I ran the repair-tool under GRUB options. That means that GRUB launches Ubuntu with both quiet splash and nomodeset, and that seemed to do the trick (or maybe Ubuntu downloaded some drivers while installing).

However, my troubles do not end here. It seems my second install attempt wiped the Windows boot files somehow, so now I can only boot Ubuntu from GRUB (I only have options to boot Ubuntu, Windows disappeared somehow) or the BIOS. From the BIOS I do have the option "Windows Boot Manager" but that only seems to launch the BIOS configuration menu. I also have 2 ubuntu options - both launching GRUB and Ubuntu correctly. How can I restore the Windows boot option in GRUB? The "Repair Windows boot files" is greyed out in repair-tool.

---

### Post by oldfred on 2013-12-05
Did you overwrite all of Windows with your second install? You should use Something else or manual install and choose the same partition(s) for / (root) and /home if you had that separate.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Usually nomodeset does not work with Intel but one of these does.
 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

---

### Post by The average internet guy on 2013-12-05
> **oldfred said:**
> Did you overwrite all of Windows with your second install? You should use Something else or manual install and choose the same partition(s) for / (root) and /home if you had that separate.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Usually nomodeset does not work with Intel but one of these does.
 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

I didn't overwrite the Windows installation (not knowingly at least), Ubuntu was originally installed on a separate partition. During my second install of Ubuntu I chose the option to erase Ubuntu and reinstall.

This is the bootinfo report: [http://paste.ubuntu.com/6525212/](http://paste.ubuntu.com/6525212/)

---

### Post by oldfred on 2013-12-05
You did not chose erase Ubuntu but erase disk and install Ubuntu. 
That erased everything.

---

### Post by The average internet guy on 2013-12-05
I feared as much. I did choose the option: Erase Ubuntu 13.10 and reinstall (see picture), little did I know that it meant "Erase everything and install Ubuntu". Bummer. Is there any way I can get my Windows 8 back if I don't have a CD?

[IMG]http://i.imgur.com/KFtK62T.jpg[/IMG]

---

### Post by oldfred on 2013-12-05
Not as a working system. Linux normally writes files all over the entire partition. Windows writes mostly at beginning and  a defrag moves all files to beginning of drive. And if any system file is overwritten you then do not have a working system.
But if you did have data that was not well backed up you may be able to recover some of it. Ubuntu is small and drive is large, so large parts of drive were not overwritten and a tool like photorec can scan entire drive for anything that looks like a file just by type. Filenames are gone, but type is internal to the way file is written. It is slow and you need a drive with enough space to copy all restored data into. When I ran photorec it also recovered the same file many times as it also found all the deleled copies. I could only do file compares to try to see which had the most current data. 

Your computer vendor may offer for a nominal charge a Windows recovery disk. It will not be a full Windows installer, but an image of drive for your system like the recovery partition. Otherwise you need to purchase a full new Windows install DVD. With UEFI the serial number is inside the UEFI, but can only be used with the vendor;s version of Windows not a new install.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

---

### Post by The average internet guy on 2013-12-05
> **oldfred said:**
> Not as a working system. Linux normally writes files all over the entire partition. Windows writes mostly at beginning and  a defrag moves all files to beginning of drive. And if any system file is overwritten you then do not have a working system.
But if you did have data that was not well backed up you may be able to recover some of it. Ubuntu is small and drive is large, so large parts of drive were not overwritten and a tool like photorec can scan entire drive for anything that looks like a file just by type. Filenames are gone, but type is internal to the way file is written. It is slow and you need a drive with enough space to copy all restored data into. When I ran photorec it also recovered the same file many times as it also found all the deleled copies. I could only do file compares to try to see which had the most current data. 

Your computer vendor may offer for a nominal charge a Windows recovery disk. It will not be a full Windows installer, but an image of drive for your system like the recovery partition. Otherwise you need to purchase a full new Windows install DVD. With UEFI the serial number is inside the UEFI, but can only be used with the vendor;s version of Windows not a new install.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

I didn't have any data on the partition as the computer was brand new. Looks like I'll have to contact ASUS for a recovery CD. I really think it can be classified as a bug that the Ubuntu installer says "Erase Ubuntu 13.10..." but really means "Erase and merge all partitions except the EFI and swap partition". Thanks for your help anyway.

To anyone reading this topic after purchasing an ASUS UX302LG: I think what worked for me was to tell GRUB to load the Linux kernel with both "quiet splash" and "nomodeset" (just set nomodeset in the auto-repair tool under advanced options, quiet splash is on by default)

---

