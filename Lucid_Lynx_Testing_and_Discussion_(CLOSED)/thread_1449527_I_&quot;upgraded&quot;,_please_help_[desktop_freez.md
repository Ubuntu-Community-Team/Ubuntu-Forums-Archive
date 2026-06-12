---
title: "I &quot;upgraded&quot;, please help [desktop freeze]"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by willro on 2010-04-07
Ok, so heres the problem, i realize that it's still in beta which might explain why this is happening. So, i used update manager to upgrade to Lucid. But now when i boot my laptop, it loads fine, until it gets to my desktop, where about 2 seconds after it gets to the desktop, it freezes and nothing i click on will do anything. Sometimes even the mouse will freeze.

so i just want to go back to Karmic, is there a way i can downgrade without loosing all of my documents and movies?

my current plan is to boot from live CD, transfer everything onto a flashdrive and keep moving stuff over to my desktop. and then installing 9.10 over 10.04, but i had to find a lot of drivers for my wireless card and graphics processor so that is unpreffered.

---

### Post by uRock on 2010-04-08
> **willro said:**
> Ok, so heres the problem, i realize that it's still in beta which might explain why this is happening. So, i used update manager to upgrade to Lucid. But now when i boot my laptop, it loads fine, until it gets to my desktop, where about 2 seconds after it gets to the desktop, it freezes and nothing i click on will do anything. Sometimes even the mouse will freeze.

so i just want to go back to Karmic, is there a way i can downgrade without loosing all of my documents and movies?

my current plan is to boot from live CD, transfer everything onto a flashdrive and keep moving stuff over to my desktop. and then installing 9.10 over 10.04, but i had to find a lot of drivers for my wireless card and graphics processor so that is unpreffered.

Do you have a separate /home partition? If so, you will not need to back things up. If you don't then, yes you will have to back up your data before reinstalling.

Before reinstalling, can we first try to repair your current install? If yes, then you'll need to boot the machine and at the grub menu select the kernel for Lucid that has restore in its title.

Once it boots to the next menu select repair packages and see if it can repair the install.

If you try the repair method, let us know what happens.

Regards,
Ronnie

---

### Post by ndefontenay on 2010-04-08
hi.

Ubuntu 10.04 is in a beta version so a lot of problems is to be expected.

If you stay around now that you've managed to fix your wireless etc... you'll receive updates regularly.

You can open an account at launchpad.net to help us post bug reports. It's another way of enjoying ubuntu.

---

### Post by willro on 2010-04-08
> **uRock said:**
> Do you have a separate /home partition? If so, you will not need to back things up. If you don't then, yes you will have to back up your data before reinstalling.

Before reinstalling, can we first try to repair your current install? If yes, then you'll need to boot the machine and at the grub menu select the kernel for Lucid that has restore in its title.

Once it boots to the next menu select repair packages and see if it can repair the install.

If you try the repair method, let us know what happens.

Regards,
Ronnie

Thanks for actually reading my post ronnie, i don't think NDE understood anything other then wireless...

I only have 1 /home on my linux installation.

everytime i'll go do a package repair right now and be back to tell you how it went.

---

### Post by willro on 2010-04-08
when i try to dpkg, it tells me that there was 1 upgraded file found. it asks if i want to repair, i hit Y, then it goes on to say that it failed to fetch the file from the ubuntu website. all the Internet in my house is wireless, so tomorrow at school i will connect to the Internet there and try to repair.

---

### Post by uRock on 2010-04-08
Kool, let us know what happens.

Cheers,
Ronnie

---

### Post by ranch hand on 2010-04-08
After you run that and before trying to boot you will be back to the recovery menu.  Select root with internet.

Type
```

dpkg --configure -a

```if that just returns you to the root prompt this is probably a good thing.  If it runs but quits with some errors, run it again.  Keep that up until the errors look the same as the last batch.

Try this when the last command run is done. 
```

dpkg-reconfigure -a

```There will be some questions to answer there but they are pretty self explanatory.

I would also try the "dpkg fix broken packages" option again last before trying to boot.

Dpkg is the foundation of package management in Debian based OS'.  The three things that have been recommended are simply different ways to help dpkg do its job when things are not quite right.

Real handy.

---

### Post by willro on 2010-04-08
ok, so now when i boot up it takes about twice as long. but it doesn't freeze(as far as i can tell) when it finishes booting. Instead the monitor turns off.

any idea on this one?

---

### Post by ranch hand on 2010-04-08
Does the monitor really turn off?  Or is the screen just going to black?

---

### Post by willro on 2010-04-08
it turns into it's greenish black color, which is where it's at when its turned off.

---

### Post by ranch hand on 2010-04-08
You need to post some info on your box (see what I post in my signature at the bottom of this post for an example) so that we have a clue what we are working with here.

There should be a power button on the monitor and probably a light.  If the light is on the monitor is on type of thing.  Mine has two colors blue when active and orange when inactive and no color when off.

There are a couple of threads, I am sure I have seen them, in this forum on the screen going to black.  You should have a look at them.  Might be some help there.

Are you booting in with a password on the "normal" login page?

---

### Post by VMC on 2010-04-08
> **willro said:**
> ok, so now when i boot up it takes about twice as long. but it doesn't freeze(as far as i can tell) when it finishes booting. Instead the monitor turns off.

any idea on this one?

I had that once. My lcd monitor has a green light when its on, and amber and then back again to green and then bootup. 

Something with your video driver. Check *~/.xsession-error*s, for any indication.

---

### Post by ranch hand on 2010-04-08
Geeze, am  I glad to see some one else here.  I have had little problem with this type of thing.  They boot or not.  If they boot I can see the screen (well except back in 9.10 when we had to play with the xorg file for a while).

If they don't boot, brute force sometimes works.  This probably requires some actual skill.

---

### Post by willro on 2010-04-08
well, its a toshiba a135, 1gb ram, Pentium dual core processor, radion Xpress 200m.

I know that the screen is turning off because i know the difference between it just going black, and it turning off, there is a visual difference. when it's off the back of it has a greenish tint, and when it goes black, it's black.

---

### Post by sdowney717 on 2010-04-08
can you look at the log file in  /var/log/xorg.0.log?
look for EE errors.
Here is mine. linux logs everything it might give you a clue.
You may have to boot up a live CD and chroot to become the owner of your lucid install to work with the files.

```

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux scott-desktop 2.6.32-19-generic #28-Ubuntu SMP Wed Mar 31 17:46:20 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-19-generic root=UUID=4923760a-6e34-4678-b0ab-d06b151a2998 ro quiet splash
Build Date: 30 March 2010  08:17:06PM
xorg-server 2:1.7.6-2ubuntu1 (Timo Aaltonen <tjaalton@ubuntu.com>) 
Current version of pixman: 0.16.4
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Apr  5 07:20:54 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x81f0e80
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 6.0
	X.Org XInput driver : 7.0
	X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:1:0:0) 10de:06e4:196e:05cc nVidia Corporation G98 [GeForce 8400 GS] rev 161, Mem @ 0xfd000000/16777216, 0xd0000000/268435456, 0xfa000000/33554432, I/O @ 0x0000bc00/128, BIOS @ 0x????????/131072
(--) PCI: (0:5:1:0) 4444:0016:9005:0092 Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder rev 1, Mem @ 0xf4000000/67108864
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.30  Fri Dec 18 14:21:29 PST 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  195.30  Fri Dec 18 13:43:18 PST 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules/libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "CRT: 1600x1200 +0+0"
(**) Apr 05 07:20:56 NVIDIA(0): Enabling RENDER acceleration
(II) Apr 05 07:20:56 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Apr 05 07:20:56 NVIDIA(0):     enabled.
(II) Apr 05 07:20:57 NVIDIA(0): NVIDIA GPU GeForce 8400 GS (G98) at PCI:1:0:0 (GPU-0)
(--) Apr 05 07:20:57 NVIDIA(0): Memory: 524288 kBytes
(--) Apr 05 07:20:57 NVIDIA(0): VideoBIOS: 62.98.29.00.51
(II) Apr 05 07:20:57 NVIDIA(0): Detected PCI Express Link width: 16X
(--) Apr 05 07:20:57 NVIDIA(0): Interlaced video modes are supported on this GPU
(--) Apr 05 07:20:57 NVIDIA(0): Connected display device(s) on GeForce 8400 GS at PCI:1:0:0:
(--) Apr 05 07:20:57 NVIDIA(0):     Sony CPD-E540 (CRT-1)
(--) Apr 05 07:20:57 NVIDIA(0):     NVIDIA TV Encoder (TV-0)
(--) Apr 05 07:20:57 NVIDIA(0): Sony CPD-E540 (CRT-1): 400.0 MHz maximum pixel clock
(--) Apr 05 07:20:57 NVIDIA(0): NVIDIA TV Encoder (TV-0): 400.0 MHz maximum pixel clock
(--) Apr 05 07:20:57 NVIDIA(0): TV encoder: NVIDIA
(II) Apr 05 07:20:57 NVIDIA(0): Display Device found referenced in MetaMode: CRT-1
(II) Apr 05 07:20:57 NVIDIA(0): Assigned Display Device: CRT-1
(II) Apr 05 07:20:57 NVIDIA(0): Validated modes:
(II) Apr 05 07:20:57 NVIDIA(0):     "CRT:1600x1200+0+0"
(II) Apr 05 07:20:57 NVIDIA(0): Virtual screen size determined to be 1600 x 1200
(--) Apr 05 07:20:57 NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
(--) Apr 05 07:20:57 NVIDIA(0):     option
(==) Apr 05 07:20:57 NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) Apr 05 07:20:57 NVIDIA(0): Initialized GPU GART.
(II) Apr 05 07:20:57 NVIDIA(0): Setting mode "CRT:1600x1200+0+0"
(II) Loading extension NV-GLX
(II) Apr 05 07:20:58 NVIDIA(0): Initialized OpenGL Acceleration
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) Apr 05 07:20:58 NVIDIA(0): Initialized X Rendering Acceleration
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
(II) config/udev: Adding input device Power Button (/dev/input/event1)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Power Button (/dev/input/event0)
(**) Power Button: Applying InputClass "evdev keyboard catchall"
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device HDA Digital PCBeep (/dev/input/event5)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
(**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
(II) Logitech USB-PS/2 Optical Mouse: Found relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
(**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "us"
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event2)
(**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found relative axes
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: removing device Logitech USB-PS/2 Optical Mouse
(II) Logitech USB-PS/2 Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/mouse1)
(II) No input driver/identifier specified (ignoring)
(II) config/udev: Adding input device Logitech USB-PS/2 Optical Mouse (/dev/input/event4)
(**) Logitech USB-PS/2 Optical Mouse: Applying InputClass "evdev pointer catchall"
(**) Logitech USB-PS/2 Optical Mouse: always reports core events
(**) Logitech USB-PS/2 Optical Mouse: Device: "/dev/input/event4"
(II) Logitech USB-PS/2 Optical Mouse: Found 3 mouse buttons
(II) Logitech USB-PS/2 Optical Mouse: Found scroll wheel(s)
(II) Logitech USB-PS/2 Optical Mouse: Found relative axes
(II) Logitech USB-PS/2 Optical Mouse: Found x and y relative axes
(II) Logitech USB-PS/2 Optical Mouse: Configuring as mouse
(**) Logitech USB-PS/2 Optical Mouse: YAxisMapping: buttons 4 and 5
(**) Logitech USB-PS/2 Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Logitech USB-PS/2 Optical Mouse" (type: MOUSE)
(II) Logitech USB-PS/2 Optical Mouse: initialized for relative axes.
(II) XKB: reuse xkmfile /var/lib/xkb/server-F8D9B4EE1D9075AF4B1C23C75362EE93E14954A0.xkm
```

---

### Post by ranch hand on 2010-04-08
A 9.04 or 9.10 LiveCD will be easier to work with your files from.

---

### Post by sdowney717 on 2010-04-08
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509273?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509273?comments=all)
looks like there is a bug with your card
> 
[Lucid] Radeon Xpress 200M needs PCI quirk to fix or disable MSI
CancelOk

   1. Ubuntu
   2. &#8220;linux&#8221; package
   3. Bugs
   4. Bug #509273

This bug affects 35 people. Does this bug affect you? Edit This bug affects 35 people. Does this bug affect you? Edit 

here is another problem thread with that video card
[http://ubuntuforums.org/showthread.php?t=1450063](http://ubuntuforums.org/showthread.php?t=1450063)

a fix from that other thread
You must boot with pci=nomsi kernel option to be able to boot.
Here's the bug report for this problem (bug status is fix committed so in a couple of days this will be solved): [https://bugs.launchpad.net/ubuntu/+s...3?comments=all](https://bugs.launchpad.net/ubuntu/+s...3?comments=all)

---

### Post by willro on 2010-04-08
> **sdowney717 said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509273?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509273?comments=all)
looks like there is a bug with your card


here is another problem thread with that video card
[http://ubuntuforums.org/showthread.php?t=1450063](http://ubuntuforums.org/showthread.php?t=1450063)

a fix from that other thread
You must boot with pci=nomsi kernel option to be able to boot.
Here's the bug report for this problem (bug status is fix committed so in a couple of days this will be solved): [https://bugs.launchpad.net/ubuntu/+s...3?comments=all](https://bugs.launchpad.net/ubuntu/+s...3?comments=all)
how do i set the pci=nomsi, i've been searching but can't find a how to.

---

### Post by ranch hand on 2010-04-08
When your menu comes up hit e and you will be able to edit the menuentry.

I believe you want that in the "linux" line with the other instructions.

Ctrl+x will boot from your edited entry.

---

### Post by willro on 2010-04-10
with pci=nomsi i get as far as the purple ubuntu screen, then when thats done loading a white box pops up in the middle of it and the computer freezes.

---

### Post by ranch hand on 2010-04-10
Beats me.

The white box should be your login screen.

What happens if you boot to recovery mode and select "return to normal boot"?  If you do the text login in there and then type startx it should get you in.

---

