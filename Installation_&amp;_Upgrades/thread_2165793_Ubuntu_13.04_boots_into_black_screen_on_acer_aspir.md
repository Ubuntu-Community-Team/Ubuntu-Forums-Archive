---
title: "Ubuntu 13.04 boots into black screen on acer aspire M3"
date: 2013-08-06
forum: Installation &amp; Upgrades
---

### Post by tom-cornelis7 on 2013-08-06
Hi all,

I finished the installation of ubuntu 13.04 on a Acer aspire M3-581PTG (with NVIDIA GeForce GT 730M).
When choosing the default startup, the screen gets black but I can still hear the login sound.
If I opt for a startup in failesafeX from the recovery menu, I end up with the error:

[I]Fatal server error:
no screens found (EE)[/I]

And if I take the "resume" option from the recovery menu, I fall back on the terminal with this message:

[I]login: initctl: Event failed

[/I]I tried (re)installing nVidia drivers, but nothing seems to work. Does anyone has good advice on this?

Thanks,
Tom

---

### Post by tom-cornelis7 on 2013-08-06
After some googling, I tried to add the

acpi_backlight=vendor

boot option when booting ubuntu.
With this option I get to the login screen, although the screen is resize just before it and the full width is not used.
I can login, but I have only the mouse, no unity or something to click on.
The only thing I could do is pushing the power button, which gives me the option between restart/shutdown/...

[FONT=arial][SIZE=3][SIZE=2][/SIZE][/SIZE][/FONT]

---

### Post by oldfred on 2013-08-06
If you just have mouse can you do this:

 When you see you are in the desktop but no icon or bar, right click to change desktop background
When the window appear, click all settings, now you see the system settings window.
Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD

Is your laptop a dual video system? And can you set whether Intel or nVidia?
      
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)

---

### Post by tom-cornelis7 on 2013-08-06
Thanks,

That's a smart way to get in the system settings. However when I arrive at the additional drivers tab, it is empty and I can't do something.
The laptop has both intel and nVidia, but I couldn't found how to select on of the two.
I'll try to look into your links, hopefully they contain a solution.

---

### Post by oldfred on 2013-08-06
You may be booting with Intel video which does not have a driver. Is that a setting in your UEFI/BIOS on which video mode to use?

This would proably be in addition to the boot parameter you already discovered.

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

      
 For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

   Asus i3 with Intel graphics, 
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

---

### Post by tom-cornelis7 on 2013-08-07
There is no setting in UEFI/BIOS to control video settings.
None of your suggestions did work.

But when I fall back on the terminal, I took some logs which could give another clue.
The xorg.0.log looks like this:
> 
[     5.021] 
X.Org X Server 1.13.4
Release Date: 2013-04-17
[     5.021] X Protocol Version 11, Revision 0
[     5.021] Build Operating System: Linux 2.6.24-32-xen x86_64 Ubuntu
[     5.022] Current Operating System: Linux tom-Aspire-M3-581PTG 3.9.11-030911-generic #201307202035 SMP Sun Jul 21 00:35:53 UTC 2013 x86_64
[     5.022] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.9.11-030911-generic root=UUID=49639ced-4b69-4315-85bc-801c8da89e88 ro recovery nomodeset
[     5.022] Build Date: 08 May 2013  02:34:03PM
[     5.022] xorg-server 2:1.13.4~git20130508+server-1.13-branch.10c42f57-0ubuntu0ricotz~raring (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
[     5.022] Current version of pixman: 0.28.2
[     5.022]     Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
[     5.022] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.022] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug  7 16:53:41 2013
[     5.023] (==) Using config file: "/etc/X11/xorg.conf"
[     5.023] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.024] (==) ServerLayout "Layout0"
[     5.024] (**) |-->Screen "Screen0" (0)
[     5.024] (**) |   |-->Monitor "Monitor0"
[     5.025] (**) |   |-->Device "Device0"
[     5.025] (**) |-->Input Device "Keyboard0"
[     5.025] (**) |-->Input Device "Mouse0"
[     5.025] (==) Automatically adding devices
[     5.025] (==) Automatically enabling devices
[     5.025] (==) Automatically adding GPU devices
[     5.026] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.026]     Entry deleted from font path.
[     5.026] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.026]     Entry deleted from font path.
[     5.026] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.026]     Entry deleted from font path.
[     5.026] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.026]     Entry deleted from font path.
[     5.026] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.026]     Entry deleted from font path.
[     5.027] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[     5.027]     Entry deleted from font path.
[     5.027] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     5.027] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     5.027] (WW) Hotplugging is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[     5.027] (WW) Disabling Keyboard0
[     5.027] (WW) Disabling Mouse0
[     5.027] (II) Loader magic: 0x7fa7485c4d20
[     5.027] (II) Module ABI versions:
[     5.027]     X.Org ANSI C Emulation: 0.4
[     5.027]     X.Org Video Driver: 13.1
[     5.027]     X.Org XInput driver : 18.0
[     5.027]     X.Org Server Extension : 7.0
[     5.028] (--) PCI:*(0:0:2:0) 8086:0166:1025:067d rev 9, Mem @ 0xe3000000/4194304, 0xd0000000/268435456, I/O @ 0x00004000/64
[     5.028] (--) PCI: (0:1:0:0) 10de:0fe1:1025:067d rev 161, Mem @ 0xe2000000/16777216, 0xb0000000/268435456, 0xc0000000/33554432, I/O @ 0x00003000/128, BIOS @ 0x????????/524288
[     5.028] (II) Open ACPI successful (/var/run/acpid.socket)
[     5.028] Initializing built-in extension Generic Event Extension
[     5.028] Initializing built-in extension SHAPE
[     5.028] Initializing built-in extension MIT-SHM
[     5.028] Initializing built-in extension XInputExtension
[     5.028] Initializing built-in extension XTEST
[     5.028] Initializing built-in extension BIG-REQUESTS
[     5.028] Initializing built-in extension SYNC
[     5.028] Initializing built-in extension XKEYBOARD
[     5.028] Initializing built-in extension XC-MISC
[     5.028] Initializing built-in extension SECURITY
[     5.028] Initializing built-in extension XINERAMA
[     5.028] Initializing built-in extension XFIXES
[     5.028] Initializing built-in extension RENDER
[     5.028] Initializing built-in extension RANDR
[     5.028] Initializing built-in extension COMPOSITE
[     5.028] Initializing built-in extension DAMAGE
[     5.028] Initializing built-in extension MIT-SCREEN-SAVER
[     5.028] Initializing built-in extension DOUBLE-BUFFER
[     5.028] Initializing built-in extension RECORD
[     5.028] Initializing built-in extension DPMS
[     5.028] Initializing built-in extension X-Resource
[     5.028] Initializing built-in extension XVideo
[     5.028] Initializing built-in extension XVideo-MotionCompensation
[     5.028] Initializing built-in extension SELinux
[     5.028] Initializing built-in extension XFree86-VidModeExtension
[     5.028] Initializing built-in extension XFree86-DGA
[     5.028] Initializing built-in extension XFree86-DRI
[     5.028] Initializing built-in extension DRI2
[     5.028] (II) LoadModule: "glx"
[     5.029] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/libglx.so
[     5.110] (II) Module glx: vendor="NVIDIA Corporation"
[     5.110]     compiled for 4.0.2, module version = 1.0.0
[     5.110]     Module class: X.Org Server Extension
[     5.110] (II) NVIDIA GLX Module  319.32  Wed Jun 19 14:55:38 PDT 2013
[     5.111] Loading extension GLX
[     5.111] (II) LoadModule: "nvidia"
[     5.111] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/nvidia_drv.so
[     5.116] (II) Module nvidia: vendor="NVIDIA Corporation"
[     5.116]     compiled for 4.0.2, module version = 1.0.0
[     5.116]     Module class: X.Org Video Driver
[     5.120] (II) NVIDIA dlloader X Driver  319.32  Wed Jun 19 14:34:12 PDT 2013
[     5.120] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.120] (++) using VT number 7

**[     5.120] (EE) No devices detected.**
[     5.120] (==) Matched intel as autoconfigured driver 0
[     5.120] (==) Matched vesa as autoconfigured driver 1
[     5.120] (==) Matched modesetting as autoconfigured driver 2
[     5.121] (==) Matched fbdev as autoconfigured driver 3
[     5.121] (==) Assigned the driver to the xf86ConfigLayout
[     5.121] (II) LoadModule: "intel"
[     5.121] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[     5.123] (II) Module intel: vendor="X.Org Foundation"
[     5.124]     compiled for 1.13.4, module version = 2.21.14
[     5.124]     Module class: X.Org Video Driver
[     5.124]     ABI class: X.Org Video Driver, version 13.1
[     5.124] (II) LoadModule: "vesa"
[     5.124] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     5.124] (II) Module vesa: vendor="X.Org Foundation"
[     5.124]     compiled for 1.12.99.902, module version = 2.3.2
[     5.124]     Module class: X.Org Video Driver
[     5.124]     ABI class: X.Org Video Driver, version 13.0
[     5.124] (II) LoadModule: "modesetting"
[     5.124] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     5.125] (II) Module modesetting: vendor="X.Org Foundation"
[     5.125]     compiled for 1.13.3, module version = 0.7.0
[     5.125]     Module class: X.Org Video Driver
[     5.125]     ABI class: X.Org Video Driver, version 13.1
[     5.125] (II) LoadModule: "fbdev"
[     5.125] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     5.126] (II) Module fbdev: vendor="X.Org Foundation"
[     5.126]     compiled for 1.12.99.902, module version = 0.4.3
[     5.126]     Module class: X.Org Video Driver
[     5.126]     ABI class: X.Org Video Driver, version 13.0
[     5.126] (II) NVIDIA dlloader X Driver  319.32  Wed Jun 19 14:34:12 PDT 2013
[     5.126] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[     5.126] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[     5.126] (II) VESA: driver for VESA chipsets: vesa
[     5.126] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     5.126] (II) FBDEV: driver for framebuffer: fbdev
[     5.126] (++) using VT number 7

[     5.126] (WW) xf86OpenConsole: setpgid failed: Operation not permitted
[     5.126] (WW) xf86OpenConsole: setsid failed: Operation not permitted
[     5.129] (WW) Falling back to old probe method for modesetting
[     5.129] (EE) open /dev/dri/card0: No such file or directory
[     5.129] (WW) Falling back to old probe method for fbdev
[     5.129] (II) Loading sub module "fbdevhw"
[     5.129] (II) LoadModule: "fbdevhw"
[     5.129] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     5.130] (II) Module fbdevhw: vendor="X.Org Foundation"
[     5.130]     compiled for 1.13.4, module version = 0.0.2
[     5.130]     ABI class: X.Org Video Driver, version 13.1
[     5.130] (II) Loading sub module "vbe"
[     5.130] (II) LoadModule: "vbe"
[     5.130] (II) Loading /usr/lib/xorg/modules/libvbe.so
[     5.130] (II) Module vbe: vendor="X.Org Foundation"
[     5.130]     compiled for 1.13.4, module version = 1.1.0
[     5.130]     ABI class: X.Org Video Driver, version 13.1
[     5.130] (II) Loading sub module "int10"
[     5.130] (II) LoadModule: "int10"
[     5.130] (II) Loading /usr/lib/xorg/modules/libint10.so
[     5.131] (II) Module int10: vendor="X.Org Foundation"
[     5.131]     compiled for 1.13.4, module version = 1.0.0
[     5.131]     ABI class: X.Org Video Driver, version 13.1
[     5.131] (II) VESA(0): initializing int10
[     5.131] (EE) VESA(0): V_BIOS address 0x0 out of range
[     5.131] (II) UnloadModule: "vesa"
[     5.131] (II) UnloadSubModule: "int10"
[     5.131] (II) Unloading int10
[     5.131] (II) UnloadSubModule: "vbe"
[     5.131] (II) Unloading vbe
[B][     5.131] (EE) Screen(s) found, but none have a usable configuration.
[     5.131] 
Fatal server error:
[     5.131] no screens found
[     5.131] (EE) 
Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[     5.131] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[     5.131] (EE) 
[     5.132] Server terminated with error (1). Closing log file.[/B]


And the output of "lshw -c video" says display unclaimed:
> 
  *-display UNCLAIMED
       description: VGA compatible controller
       product: GK107M [GeForce GT 730M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e2000000-e2ffffff memory:b0000000-bfffffff memory:c0000000-c1ffffff ioport:3000(size=128) memory:c2000000-c207ffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller cap_list
       configuration: latency=0
       resources: memory:e3000000-e33fffff memory:d0000000-dfffffff ioport:4000(size=64)


I tried re(installing) nVidia drivers (differen versions), with or without bumblebee, but nothing gets it working.
Any other ideas?

Thanks,
Tom

---

### Post by oldfred on 2013-08-07
Do not know what is happening. I just have nVidia and have to use nomodeset to get into system and then install a recent nVidia driver from repository or system settings.

Bit older but has some other boot parameters.
[http://ubuntuforums.org/showthread.php?t=1991223](http://ubuntuforums.org/showthread.php?t=1991223)

Since yours is a 700 series chip, you may need the newest for at least a very recent version.
[http://www.nvidia.com/object/linux-display-amd64-319.32-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.32-driver.html)

And if you have installed different versions they may start to interfere. Best to totally uninstall all nVidia if you can get to command line.

 # only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*

---

### Post by tom-cornelis7 on 2013-08-08
I posted a question on launchpad, and thanks to an answer there I'm making progress now:
I had to remove the nvidia driver and /etc/X11/xorg.conf completely, so I would be able to use the integrated intel graphics card instead.
Now I am able to boot using the option "acpi_backlight=vendor" and I end op with a login screen with the right resolution and the xorg log has no errors anymore.

However unity is still missing, but this is probably a different problem.

---

### Post by tom-cornelis7 on 2013-08-08
I finally got everything worked, I could enable unity by:
- Opening the terminal with ctrl+alt+t
- Opening the compiz setting window by typing "ccsm"
- Enabling the unity plugin and solving the conflicts.


Thanks for helping,
Tom

---

