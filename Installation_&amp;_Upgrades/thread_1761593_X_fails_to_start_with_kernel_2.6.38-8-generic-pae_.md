---
title: "X fails to start with kernel 2.6.38-8-generic-pae after upgrade do 11.04"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by lads on 2011-05-18
Hello everyone,

This is more of a nuisance than anything else. I upgraded today from 10.10 to 11.04 and on the first boot X failed to start, dumping the messages you'll see below.

After a few attempts I figured that this is only happening with kernel version 2.6.38-8-generic-pae, which after the upgrade to 11.04 was set as the default boot option at GRUB. Booting with kernel 2.6.38-8-generic things go smoothly.

Is this something to be reported as a bug? Where?

Thank you,

Luís

---------

```

X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux MekanikDestruktiwKommandoh 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
Kernel command line: root=UUID=3a8fdbad-ad70-41ab-b746-abd9c6346e44 ro quiet splash 
Build Date: 19 April 2011  03:33:17PM
xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.20.2
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 18 14:30:16 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(EE) open /dev/fb0: No such file or directory
FATAL: Module fglrx not found.
(EE) fglrx(0): ACPI: DRM connection failed
(EE) fglrx(0): ACPI: DRM connection failed
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) fglrx(0): XMM failed to open CMMQS connection.(EE) fglrx(0): 
(EE) fglrx(0): XMM failed to initialize

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb78c540c]
3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDriOpenConnection+0x30) [0xb69e5120]
4: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0xb740b000+0xfc2c) [0xb741ac2c]
5: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0xb740b000+0x121fa) [0xb741d1fa]
6: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0xb740b000+0x118c7) [0xb741c8c7]
7: /usr/bin/X (InitExtensions+0x9d) [0x80d057d]
8: /usr/bin/X (0x8048000+0x1a692) [0x8062692]
9: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb75d4e37]
10: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
Segmentation fault at address 0x50

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
 ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

```

---

### Post by dino99 on 2011-05-18
all this about "fglrx" issue, so with synaptic: remove/purge it then reinstall it

if a xorg.conf exist, rename or delete it, then reboot

---

### Post by Blasphemist on 2011-05-18
I'll put this in here in the case that you don't see it in the other thread you posted in. The issue is explained in this post.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by lads on 2011-05-18
> **dino99 said:**
> all this about "fglrx" issue, so with synaptic: remove/purge it then reinstall it

if a xorg.conf exist, rename or delete it, then reboot

Hi dino99, after decrypting your message I removed and reinstalled fglrx and rebooted. The same as before.

Thanks,

Luís

---

### Post by lads on 2011-05-18
> **Blasphemist said:**
> I'll put this in here in the case that you don't see it in the other thread you posted in. The issue is explained in this post.
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Hi Jim, from yours and dino's messages I'm starting to think I should simply remove the fgrlx package.

If I do that what are the risks?

Thank you,

Luís

---

### Post by Blasphemist on 2011-05-18
I don't know if there are any risks. It does look to me like with that you will be missing kms, which could well be the problem. Please run this.
```
sudo lshw -c Display
```
That will show your gpu and it's driver. Then we can tell better how to proceed.

---

### Post by Breslau on 2011-05-19
oops wrong thread

---

### Post by lads on 2011-05-19
Hi Jim,

Here's the result:

```
$ sudo lshw -c Display
[sudo] password for lads: 
  *-display               
       description: VGA compatible controller
       product: Mobility Radeon HD 3650
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:50 memory:a0000000-bfffffff ioport:d000(size=256) memory:c0020000-c002ffff memory:c0000000-c001ffff

```

Thanks for your help,

Luís

---

### Post by Blasphemist on 2011-05-19
From what I see in this bug [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/776904](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/776904) and in this document [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver), I'd recommend installing the open source driver. See this to ensure fglrx is fully purged.
> ypically, the following manual commands will properly uninstall -fglrx:
```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo dpkg-reconfigure xserver-xorg
```
If you want desktop effects (compiz or KDE) you'll need the glx module loaded. This will not work even after purging fglrx since a hanging libglx.so file is left around. Both fglrx and xserver-xorg-core provide this file so to replace it with the correct version you'll need to reinstall xserver-xorg-core as well.
```
sudo apt-get install --reinstall xserver-xorg-core
```


---

### Post by lads on 2011-05-21
Hi again Jim,

I used that procedure, though apt-get tells me fglrx-modaliases isn't available anymore, it has to be replaced by fglrx. After completing the procedure I rebooted with kernel 2.6.38-8-generic-pae and the problem remains, no X there.

Pordon me if this is a dumb question, do I have to run that procedure with kernel 2.6.38-8-generic-pae? If the answer is yes then I have problem, for I do not have an internet connection without X to start my mobile broadband.

Thanks,

Luís

---

### Post by Blasphemist on 2011-05-21
> **lads said:**
> Hi again Jim,

I used that procedure, though apt-get tells me fglrx-modaliases isn't available anymore, it has to be replaced by fglrx. After completing the procedure I rebooted with kernel 2.6.38-8-generic-pae and the problem remains, no X there.

Pordon me if this is a dumb question, do I have to run that procedure with kernel 2.6.38-8-generic-pae? If the answer is yes then I have problem, for I do not have an internet connection without X to start my mobile broadband.

Thanks,

Luís
Luis, yes you did make the change in one kernel and then boot a different kernel. I believe you need to remove the pae kernel. It's purpose is support for 4+ GB memory on 32 bit systems. [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension) Do you have 4+ GB? I believe it is the default kernel for 32 bit now and for some it is causing the issue you have. [http://ubuntuforums.org/archive/index.php/t-1742199.html](http://ubuntuforums.org/archive/index.php/t-1742199.html)

In the above thread, the OP removes the pae kernel in synaptic and the generic is automatically promoted to default. I haven't found any other method of making the change but I haven't necessarily exhausted all sources for that yet. I can't tell you if that is the best way. I also think there must be a bug in or needed on this but I haven't seen it. Maybe someone else will jump in on this that knows more than we do about kernel version changes.

---

### Post by MAFoElffen on 2011-05-21
> **Blasphemist said:**
> Luis, yes you did make the change in one kernel and then boot a different kernel. I believe you need to remove the pae kernel. It's purpose is support for 4+ GB memory on 32 bit systems. [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension) Do you have 4+ GB? I believe it is the default kernel for 32 bit now and for some it is causing the issue you have. [http://ubuntuforums.org/archive/index.php/t-1742199.html](http://ubuntuforums.org/archive/index.php/t-1742199.html)

In the above thread, the OP removes the pae kernel in synaptic and the generic is automatically promoted to default. I haven't found any other method of making the change but I haven't necessarily exhausted all sources for that yet. I can't tell you if that is the best way. I also think there must be a bug in or needed on this but I haven't seen it. Maybe someone else will jump in on this that knows more than we do about kernel version changes.
That's what I thought also.  PAE "itself" is all good and well in theory. and will help out if the BIOS is recent.  The same issue exits if you are running 64bit with old BIOS'es.  You can have all the memory in the world... If the CPU doesn't have the address space to address it or the BIOS doesn't have the capability to re-map it, then then added  kernel capabilities cannot take advantage of those technologies.

On "newer" equipment, that all changes.  As for as Ubuntu goes and their naming conventions-- As far as "I know" and my experience with it... It's how it was in my last post.  And with Ubuntu, in past, the -PAE kernel extension "was" reserve for server kernels (don't know yet about the -generic + -pae kernels as these seem to be hybreds)... and the 32bit server kernel was optimized for server services and cut down on prioities for graphics and desktop services.

You know how that goes.  Any of that can and deos change at any moment and be completely different. (keeping me humble and flexible(... but I can only go off what people tell me on what is current, what "does" work or not (I'm continually trying to break and fix things) or from what I read.  On what I "read,"  I usually try to play with to see if it really works or not <> if it really is implemented yet downstream and "how" it was implemented in that distribution.

As for ubutnu kernels-- kernels, grub and Xorg is currently in flux and changing.  They are driving each other and we are tring to keep up and to find what works.  You think you are having problems with natty kernels? >> We are using Natty kernels as fall-back tests for the newer Eneiric kernels (current 2.6.39.2) which we are trying to work through...  Things right now are changing almost daily.  It will all work out in the end when we find what works together and all the changes catch up with each other.

---

### Post by MAFoElffen on 2011-05-21
> **lads said:**
> Hello everyone,

This is more of a nuisance than anything else. I upgraded today from 10.10 to 11.04 and on the first boot X failed to start, dumping the messages you'll see below.

After a few attempts I figured that this is only happening with kernel version 2.6.38-8-generic-pae, which after the upgrade to 11.04 was set as the default boot option at GRUB. Booting with kernel 2.6.38-8-generic things go smoothly.

Is this something to be reported as a bug? Where?

Thank you,

Luís

---------

```

X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux MekanikDestruktiwKommandoh 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
Kernel command line: root=UUID=3a8fdbad-ad70-41ab-b746-abd9c6346e44 ro quiet splash 
Build Date: 19 April 2011  03:33:17PM
xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.20.2
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 18 14:30:16 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
[COLOR=Red][B](WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
(EE) open /dev/fb0: No such file or directory
FATAL: Module fglrx not found.
(EE) fglrx(0): ACPI: DRM connection failed
(EE) fglrx(0): ACPI: DRM connection failed
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) fglrx(0): XMM failed to open CMMQS connection.(EE) fglrx(0): 
(EE) fglrx(0): XMM failed to initialize[/B][/COLOR]

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb78c540c]
3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDriOpenConnection+0x30) [0xb69e5120]
4: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0xb740b000+0xfc2c) [0xb741ac2c]
5: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0xb740b000+0x121fa) [0xb741d1fa]
6: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0xb740b000+0x118c7) [0xb741c8c7]
7: /usr/bin/X (InitExtensions+0x9d) [0x80d057d]
8: /usr/bin/X (0x8048000+0x1a692) [0x8062692]
9: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb75d4e37]
10: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
Segmentation fault at address 0x50

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
 ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

```
Lets get back on track again.

I'll be the first to tell you that I have lots of experince with graphics issues and nvidia... but Radeon card are new to me, I don't have as much experience with them and they are just "different."

What I mean by "different" is that "one technique," work-around or fix does not work for all radeon cards!

Some radeon cards are no longer supported by proprietary drivers.  Some radeon cards are not supported by open source drivers. fglrx is required on some cards and not needed on others.

Since this was an "update" styled distribution upgrade-- I can assume that it worked in 10.10 and not in 11.04.  How it was setup in 10.10 used the fglx driver.  SO what is different that would cause the problem in the newer OS:

grub / kernel / xorg // driver not capmpatible with newer technologies of the previous 3.

 - The newer grub tries to find and set the kernel to a graphics mode (new in 11.04), sometimes failing in that and setting an invialid mode.
 - The kernel takes that mode set and passes it on the Xorg...
 - Older drivers set Xorg to a mode, where now they sometimes are confused because the graphics is already set in to mode or is locked up already.

So does fglrx required on this?  Looks like it was being looked for, not being loaded and failing because of it.  Why? That's what we need to find out right?

This could have been as easy as trying to set radeon mode=0 or 1, to see if the state of KNS is affecting fglrx and the passing of external, extraneous graphics calls.

---

### Post by Blasphemist on 2011-05-21
This has for the moment grabbed my attention :) I took a walk through the internet following leads and gathering information that is helping my get my head around it. I recommend that someone with drive and issues to resolve take this as a starting place and sort out a more precise and usable path. I can't really make this my focus but am willing to try and help.

From wikipedia first. [http://en.wikipedia.org/wiki/Mode-setting](http://en.wikipedia.org/wiki/Mode-setting)
> Mode-setting is setting up the screen resolution and depth mode for the graphics card. Modern mode setting software support multiple monitors ("multi-head") and hot plugging.
> **Linux**
The Linux kernel got the prerequisite for kernel-based mode-setting by accepting GEM in version 2.6.28,[2] released December 2008. This will be replaced by a TTM (Translation Table Maps) memory manager which supports the GEM API.[3] TTM was developed for the ATI Radeon driver and VIA S3 Graphics chipsets.[4]
Support for Intel GMA graphic cards has been accepted in version 2.6.29 which was released on March 23, 2009.[5]
Support for pre-R600 ATI Radeon graphics cards has been accepted in version 2.6.31 which was released on September 9, 2009.[6] Support for R600 and R700 was in development within DRM and has been merged in version 2.6.32.[7] Support for Evergreen (R800) has been merged in version 2.6.34.
As NVIDIA did not release all the needed documentation for its graphics chip, the development is under the nouveau project which uses reverse engineering to get it to work. Nouveau has been accepted in version 2.6.33 of the kernel which was released on December 10, 2009. This will allow to use kernel-based mode-setting for NVIDIA cards with this driver
As you see, the above is not completely current it appears.

To be specific to radeon for this thread.
[http://en.wikipedia.org/wiki/Radeon](http://en.wikipedia.org/wiki/Radeon)
> **Naming scheme**

At current, ATI names each card by generation, series, and by performance.
The first number is the generation number (e.g. 5000) and is related to the chipset used by the video card.
The second number indicates the series quality in the generation, starting from:
0400 to 0600 at entry level, for media and home theatre,
0700 for low intensity video games (typically using older graphics engines, or widespread games, such as Starcraft and World of Warcraft) or high-intensity games with lowered settings, and
0800 for high-intensity games, such as Crysis or Far Cry 2.
0900 is a special denotation, first used on the Radeon 5970, relating to a dual chip or internal ATI CrossFire card.
The third digit is the relative quality, within a series- a 5850 is less powerful than a 5870. Typically, a card of a higher series will always have more processing power than a card in a lower series, even if the relative quality is better (a 5770 will be outperformed by a 5850).
Since ATI's first DirectX 9-class GPU, the company has followed a naming scheme that relates each product to a market segment.
There is more including tables on the above.
> **Drivers- Linux**
Main article: fglrx
Initially, ATI did not produce Radeon drivers for Linux, instead giving hardware specifications and documentation to Direct Rendering Infrastructure (DRI) developers under various non-disclosure agreements.
In mid 2004, however, ATI started to support Linux (XFree86, X.Org), hiring a new Linux driver team to produce fglrx. Their new proprietary Linux drivers, instead of being a port of the Windows Catalyst drivers, were based on the Linux drivers for the FireGL (the FireGL drivers worked with Radeons before, but didn't officially support them), a card geared towards graphics producers, not gamers; though the display drivers part is now based on the same sources as the ones from Windows Catalyst since version 4.x in late 2004. The proprietary Linux drivers could support R200 (Radeon 8500-9200, 9250) chips.[7] For a better display driver, the repository drivers are recommended.
The frequency of driver updates increased in late 2004, releasing Linux drivers every two months, half as often as their Windows counterparts. Then since late 2005 this has been increased to monthly releases, inline with the Windows Catalyst releases.
In 2008, ATI changed its release cycles and driver versions; now referred to as Catalyst <year>.<month>, the driver package still includes an internal 8.xx.x driver revision, but it is now monthly, sharing a common code base with the Windows driver (starting with internal release 8.43). In 2009, the Catalyst driver officially dropped support for R500 and older chips, the FOSS driver being deemed stable and complete enough. The last driver release supporting older architectures is Catalyst 9.3.
For information on alternative Open Source drivers, see below.
> **FOSS drivers**
See also: Graphics hardware and FOSS#ATI/AMD

_This section's factual accuracy may be compromised because of out-of-date information. Please help improve the article by updating it. There may be additional information on the talk page. (April 2010)_
On September 12, 2007, AMD released documentation without an NDA for the RV630 (Radeon HD 2600 PRO and Radeon HD 2600 XT) and M56 (Mobility Radeon X1600) chips for open source driver development, for its strategic open source driver development initiative.[13] This initial documentation released sufficient programming information for a skeleton display detection and modesetting driver to be released. This was version 1.0.0 of the radeonhd driver, developed in cooperation with Novell. The register reference guides for M76 (Mobility Radeon HD 2600/2700/3600/3800 series) and RS690 (AMD 690 chipset series) were also released on January 4, 2008.[14]
Most of the work is shared with the existing Xorg radeon driver that also supports older Radeon architectures.[15][16] Conceptually, radeonhd initially tried to directly hit a card's register to perform its operations, while Xorg's driver radeon makes use of AtomBIOS (an abstraction layer created by Ati to ease the programming of new video card drivers) when available. Since AtomBIOS headers have been made public by AMD and are kept up to date,[17] the argument went rather moot.[18]
As of December 2009, the DRM part of the radeon driver is now included in the mainstream Linux kernel, the first version appearing in kernel version 2.6.32, used by default on several GNU/Linux distributions.[19]
This is a person currently working on, and taking requests, updating the FOSS driver.
[http://haiku-os.org/blog/kallisti5/2011-05-13_driver_status_update_radeon_hd](http://haiku-os.org/blog/kallisti5/2011-05-13_driver_status_update_radeon_hd)
This page is for free radeon drivers using kms.
[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)
This may explain some of the power and heat issues seen in posts recently.
> **KMS Power Management Options**

Kernel 2.6.35 or newer is required. The pm code supports two basic methods:

"dynpm"
"profile"
You can select the methods via sysfs. Echo "dynpm" or "profile" to /sys/class/drm/card0/device/power_method.

The "dynpm" method dynamically changes the clocks based on the number of pending fences, so performance is ramped up when running GPU intensive apps, and ramped down when the GPU is idle. The reclocking is attemped during vertical blanking periods, but due to the timing of the reclocking functions, doesn't not always complete in the blanking period, which can lead to flicker in the display. Due to this, dynpm only works when a single head is active.

The "profile" method exposes five profiles that can be selected from:

"default"
"auto"
"low"
"mid"
"high"
Select the profile by echoing the selected profile to /sys/class/drm/card0/device/power_profile.

"default" uses the default clocks and does not change the power state. This is the default behavior.
"auto" selects between "mid" and "high" power states based on the whether the system is on battery power or not. The "low" power state are selected when the monitors are in the dpms off state.
"low" forces the gpu to be in the low power state all the time. Note that "low" can cause display problems on some laptops; this is why auto does not use "low" when displays are active.
"mid" forces the gpu to be in the "mid" power state all the time. The "low" power state is selected when the monitors are in the dpms off state.
"high" forces the gpu to be in the "high" power state all the time. The "low" power state is selected when the monitors are in the dpms off state.
The "profile" method is not as agressive as "dynpm," but is currently much more stable and flicker free and works with multiple heads active.

Power management is supported on all asics (r1xx-evergreen) that include the appropriate power state tables in the vbios; not all boards do (especially older desktop cards).

Thermal sensors are implemented via external i2c chips or via the internal thermal sensor (rv6xx-evergreen only; supported in 2.6.36 or newer); not all OEMs implement a thermal sensor. To get the temperature on asics that use i2c chips, you need to load the appropriate hwmon driver for the sensor used on your board (lm63, lm64, etc.). The drm will attempt to load the appropriate hwmon driver. On boards that use the internal thermal sensor, the drm will set up the hwmon interface automatically. When the appropriate driver is loaded, the temperatures can be accessed via lm_sensors tools or via sysfs in /sys/class/hwmon .
> **Where to get the drivers**

Xorg radeon DDX (xf86-video-ati)
Mesa 3D driver (radeon, r200, r300c/g, r600c/g)
KMS DRM (Linux Kernel)
I didn't know how to bring the above in with the links intact. The KMS DRM (Linux Kernel) link takes you to Linus's kernel tree. Some yahoo that goes by Linus Torvalds doing a lot of the work it looks like. :D Some of the logs do show issues and work arounds relating to things seen in these forums.
This link is to the most current drivers for ati from xorg, I think.
[http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/](http://cgit.freedesktop.org/xorg/driver/xf86-video-ati/)
These mesa drivers do seem current though I cannot judge when they should be used.
[http://cgit.freedesktop.org/mesa/mesa/](http://cgit.freedesktop.org/mesa/mesa/)
Among other things, this shows which radeon hd support kms (none) and which are Xserver mode setting.
[http://www.x.org/wiki/radeonhd%3Afeature](http://www.x.org/wiki/radeonhd%3Afeature)
This seems to be portal that I'd want to know about if I had radeon. It includes the bug list being worked.
[http://dri.freedesktop.org/wiki/Radeon](http://dri.freedesktop.org/wiki/Radeon)
[https://bugs.freedesktop.org/buglist.cgi?component=Drivers%2FDRI%2Fr200&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED](https://bugs.freedesktop.org/buglist.cgi?component=Drivers%2FDRI%2Fr200&bug_status=NEW&bug_status=ASSIGNED&bug_status=REOPENED)
> **Unofficial Wiki for the AMD Linux Driver**
[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)
This is the natty specific page and updated within the last couple days.
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)

---

### Post by Toz on 2011-05-21
> **lads said:**
> Hello everyone,

This is more of a nuisance than anything else. I upgraded today from 10.10 to 11.04 and on the first boot X failed to start, dumping the messages you'll see below.

After a few attempts I figured that this is only happening with kernel version 2.6.38-8-generic-pae, which after the upgrade to 11.04 was set as the default boot option at GRUB. Booting with kernel 2.6.38-8-generic things go smoothly.

Is this something to be reported as a bug? Where?

Thank you,

Luís

---------

```

X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
Current Operating System: Linux MekanikDestruktiwKommandoh 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686
Kernel command line: root=UUID=3a8fdbad-ad70-41ab-b746-abd9c6346e44 ro quiet splash 
Build Date: 19 April 2011  03:33:17PM
xorg-server 2:1.10.1-1ubuntu1 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.20.2
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 18 14:30:16 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[COLOR="Red"](EE) open /dev/fb0: No such file or directory
FATAL: Module fglrx not found.[/COLOR]
(EE) fglrx(0): ACPI: DRM connection failed
(EE) fglrx(0): ACPI: DRM connection failed
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized. 
(EE) fglrx(0): XMM failed to open CMMQS connection.(EE) fglrx(0): 
(EE) fglrx(0): XMM failed to initialize

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80eab1b]
1: /usr/bin/X (0x8048000+0x5fac8) [0x80a7ac8]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb78c540c]
3: /usr/lib/xorg/extra-modules/modules/drivers/fglrx_drv.so (swlDriOpenConnection+0x30) [0xb69e5120]
4: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0xb740b000+0xfc2c) [0xb741ac2c]
5: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0xb740b000+0x121fa) [0xb741d1fa]
6: /usr/lib/xorg/extra-modules/modules/extensions/libglx.so (0xb740b000+0x118c7) [0xb741c8c7]
7: /usr/bin/X (InitExtensions+0x9d) [0x80d057d]
8: /usr/bin/X (0x8048000+0x1a692) [0x8062692]
9: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xe7) [0xb75d4e37]
10: /usr/bin/X (0x8048000+0x1a411) [0x8062411]
Segmentation fault at address 0x50

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(EE) fglrx(0): firegl_SetSuspendResumeState FAILED -9.
 ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

```

Do you have the PAE headers installed?```
apt-cache policy linux-headers-generic-pae
```They are required to build the fglrx module when upgrading from a non-pae to a pae kernel.

---

### Post by Blasphemist on 2011-05-21
I'm just as confused as you must be Luis, so here is an attempt to sort this out.

One choice is to uninstall the pae kernel, thereby promoting the generic kernel. As long as that recommendation works, you will have a system working as it does right now when you boot the generic kernel. I think risks of the pae kernel re-appearing after an update are there but you would know what to do, I think.

When I run synaptic package manager, quick filter 2.6.38, I can tell that the headers I have installed are generic, not pae. That matches my installed kernel image. Can you tell if yours match? If the installed headers are not pae when the kernel image is, I think the post on fixing that should work. I don't know how to look at that from the command line. When you boot to the generic kernel image I don't know how that affects what you'll see. From what all has been posted, I think you had the generic kernel and the upgrade brought in the pae kernel. I don't know that to be the case. 

If your system is working well, or well enough, when booting the generic kernel, those are likely the best options.

We have had you try purging and reloading drivers already. I'm not sure just what the current state is. From my big post, this is part of the FOSS drivers section.
> The register reference guides for [COLOR="Blue"]M76 (Mobility Radeon HD 2600/2700/3600/3800 series[/COLOR]) and RS690 (AMD 690 chipset series) were also released on January 4, 2008.[14]
Most of the work is shared with the existing Xorg radeon driver that also supports older Radeon architectures.[15][16] Conceptually, radeonhd initially tried to directly hit a card's register to perform its operations, while Xorg's driver radeon makes use of AtomBIOS (an abstraction layer created by Ati to ease the programming of new video card drivers) when available. Since AtomBIOS headers have been made public by AMD and are kept up to date,[17] the argument went rather moot.[18]
As of December 2009, the DRM part of the radeon driver is now included in the mainstream Linux kernel, the first version appearing in kernel version 2.6.32, used by default on several GNU/Linux distributions.[19]
I believe this is saying that though your M76 was originally using radeon hd, now the DRM part of the radeon driver should work for your card and is now a part of the kernel. I believe they refer to your 3D core as R600. AMD seems to think you can install the Catalyst 11.5 driver that just came out. I see something on their blog about an issue with the Gnome 3 shell but it may work for you.
[http://blogs.amd.com/play/2011/05/10/the-amd-catalyst%E2%84%A2-11-5-driver-%E2%80%93-what%E2%80%99s-new/](http://blogs.amd.com/play/2011/05/10/the-amd-catalyst%E2%84%A2-11-5-driver-%E2%80%93-what%E2%80%99s-new/)
You may want to check this site. It is the Linux crew survey.
[http://www.amdsurveys.com/se.ashx?s=5A1E27D23CFE9B36](http://www.amdsurveys.com/se.ashx?s=5A1E27D23CFE9B36)
If you want to follow the book, and given the state of purging and all that we have done it might be best, follow the instructions here.
[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide)
Edit:
fglrx and Catalyst are the same thing. The be sure to fully purge thing in this [https://help.ubuntu.com/community/RadeonDriver#Require](https://help.ubuntu.com/community/RadeonDriver#Require) Natty/11.04 and Modesetting Only
is for installing the open source driver. You've done that and it didn't work so I'd go for the Catalyst 11.5 if you don't do one of the first 2 options above from other posts.

---

### Post by saiki4116 on 2011-05-25
i am also facing the issue but with virtualbox saying that no suitable module found and some other error messages,i removed virtualbox but it is checking the all the services the settings but nothing happens afterwards.

---

### Post by lads on 2011-05-29
First of all many thanks to all the folk that replied to this thread. And secondly an apology for the belated response, I'm having all sort of trouble with Ubuntu 11.04, cron stopped working, xbindkeys stopped working, banshee having hiccups, slide bars not working in a bunch of programs, buttons not accepting mouse input, X freezing when coming out of screensavers ... meanwhile I'm submitting my PhD thesis proposal :)

So today I installed the pae headers and with it ran a full update. Booted, and voilá, now I have X with the pae kernel. For the record, my hard stuff is a Sony Vaio VGN-FW31ZJ.

Thanks again to everyone for the help,

Luís

---

### Post by lads on 2011-07-27
Hello everyone,

I ran the Update Manager yesterday and it installed the 2.6.38-10-generic-pae kernel. Today when I booted I had no X. The interesting thing is that I'm a getting a totally different error:

```
modprobe vboxdrv failed
```

I'll try to re-install the ape headers again and see what happens. 

Should I open a new thread for this kernel?

Thanks.

---

### Post by lads on 2011-07-27
Hello,

Re-installing the pae headers also solved the problem for the 2.6.38-10-generic-pae kernel. It seems this operation must be repeated everytime a new kernel is installed.

Best.

---

### Post by dino99 on 2011-07-27
is dkms installed ?

---

