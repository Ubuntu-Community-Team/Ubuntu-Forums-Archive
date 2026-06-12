---
title: "Support for ATI Mobility Radeon HD 3650"
date: 2009-02-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bardu on 2009-02-20
Hi there,

Ubuntu 8.10 freezes after booting from CD on my new Toshiba A350 64 bit with ATI Mobility Radeon HD 3650  graphics card.

In the hope Ubuntu 9.04 alpha 4 will include the newest driver from freedesktop.org, which include, to my knowledge, a driver for my graphics card, I download alpha 4. After booting from CD I get the message 
> 
"Ubuntu is running in low-graphics mode ... (EE) RADEON(0): Acceleration initialization failed."


The same happens with the boot option xdriver=vesa.
 
So, it seem to me there is still no support for ATI Mobility Radeon HD 3650.

Can someone shed some light on that?

Thanks,
Stephan

---

### Post by pascalS on 2009-02-21
Hi,

you should try the radeon driver.

add the driver line in section Device of your /etc/X11/xorg.conf file
Section "Device"
        Identifier      "Configured Video Device"
        driver          "radeon"
EndSection

you will not have the glx acceleration, but, hopefully, the good resolution

---

### Post by TomaszD on 2009-02-21
The radeon driver is just another name for the ati driver. This is in fact the same driver. Maybe you meant the radeonhd driver?

---

### Post by tormod on 2009-02-28
"Acceleration initialization failed" is not as critical as it sounds. Should work (although slowly) without as well. Please file a bug against xserver-xorg-video-ati attaching the log.

---

### Post by shelvingguy on 2009-03-02
I am having a similar issue with the Mobility Radeon HD 3650.  All of the drivers (radeon / radeonhd / ati / fglrx) crash X on reboot.

I have been struggling with this for weeks with no results.  I came back to ubuntu to give it another go with envyng.  Alas, I am still back to vesa.  For some reason, after installing envyng, it will not detect the ati driver, installed or not (I tried both).

Has anyone had any success running this card? 

Thanks.

---

### Post by tormod on 2009-03-03
[https://bugs.launchpad.net/bugs/336348](https://bugs.launchpad.net/bugs/336348)

---

### Post by shelvingguy on 2009-03-04
Tormod,

I should have indicated that I am a linux noob.  Could you help me out with a quick install description, and point me to the file I should use for amd64 / Ubuntu 8.1.

Thank you.

---

### Post by tormod on 2009-03-04
> **shelvingguy said:**
> Tormod,

I should have indicated that I am a linux noob.  Could you help me out with a quick install description, and point me to the file I should use for amd64 / Ubuntu 8.1.

Thank you.
As I noted in the bug report, please test the packages in my PPA [https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa) . For Ubuntu 8.10 only download the packages marked "Intrepid" in the Series column, you'll need both the -radeon and -ati packages for amd64 (*_amd64.deb).

In a Terminal window, first do "cd Desktop" since for instance Firefox will download to the Desktop folder, then:
 sudo dpkg -i xserver-xorg-video-*
Afterwards, log out and in again to have the new driver started. Of course, you'll have to remove any "vesa" reference in your xorg.conf first.

---

### Post by tormod on 2009-03-04
Those on Intel 32 bits should get the *_i386.deb packages. At the time of writing, these are still in the build queue (should be done in an hour).

---

### Post by shelvingguy on 2009-03-04
I did something wrong, I think.  How do I start the new driver?  I am sure that's what I missed.

I ran -dpkg -i xserver-xorg-video-* and removed vesa from xorg.conf.  I rebooted and it started up in safe mode because it could not detect a driver.

Thanks.

---

### Post by bardu on 2009-03-04
Tormod,

my problem is I can't use Ubuntu 8.10 on my machine at all, freezing after booting.

So, when I use 9.04 alpha 5 I can't install the drivers due to dependency problems.

Are there drivers for 9.04 available too?

---

### Post by shelvingguy on 2009-03-04
I tried again.  This time I removed everything to do with fglrx.  I wrote radeonhd into xorg.conf, but still no good.  I would include the error message, but I am not sure where it hides.

---

### Post by tormod on 2009-03-05
> **bardu said:**
> Are there drivers for 9.04 available too?
Yes, they are in the "Jaunty" series.

---

### Post by tormod on 2009-03-05
> **shelvingguy said:**
> I tried again.  This time I removed everything to do with fglrx.  I wrote radeonhd into xorg.conf, but still no good.  I would include the error message, but I am not sure where it hides.
You should not write "radeonhd" into xorg.conf, because you are using the radeon (ati) driver. Either write "ati" or leave it out, because "ati" is default for your card.

But of course make sure you have got rid of anything fglrx. [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by shelvingguy on 2009-03-05
Thanks for trying to help with this.  I tried to remove fglrx and I changed xorg.conf to ati.  It still boots to an unresponsive black screen.  If I pull the ati out of xorg.conf, and leave it blank, it boots into low graphics mode.

Am I missing something?

---

### Post by tormod on 2009-03-05
> **shelvingguy said:**
> Thanks for trying to help with this.  I tried to remove fglrx and I changed xorg.conf to ati.  It still boots to an unresponsive black screen.  If I pull the ati out of xorg.conf, and leave it blank, it boots into low graphics mode.

Am I missing something?
Please check the Xorg.0.log and Xorg.0.log.old to see what is going on. I am surprised that "ati" vs nothing makes a change.

---

### Post by shelvingguy on 2009-03-05
Here is the Xorg.0.log.old.

I don't think I can make sense of it.  Does it mean the driver is not where it expects it to be?  Have I installed it incorrectly?

The Xorg.0.log file (when the driver section in xorg.conf is blank "") seems to default to vesa.

> X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux jeff-laptop 2.6.27-13-generic #1 SMP Thu Feb 26 07:31:49 UTC 2009 x86_64
Build Date: 24 October 2008  09:06:49AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@crested.buildd)
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar  5 20:16:34 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7b7320
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 4.1
        X.Org XInput driver : 2.1
        X.Org Server Extension : 1.1
        X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7
        X.Org Server Extension : 1.1
        X.Org Font Renderer : 0.6
(II) Loader running on linux
(++) using VT number 7

(--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3650 rev 0, Mem @ 0xc0000000/536870912, 0xbfef0000/65536, I/O @ 0x00002000/256, BI$
(II) System resource ranges:
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[B]
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x00000000 (0x1) IX[B]
(II) LoadModule: "extmod"

(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"

(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1

        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"

(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.5.2, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.6
(II) Loading font FreeType
(II) LoadModule: "record"

(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension RECORD
(II) LoadModule: "dri"

(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.5.2, module version = 1.0.0
        ABI class: X.Org Server Extension, version 1.1
(II) Loading extension XFree86-DRI
(EE) No drivers available.

Fatal server error:
no screens found


---

### Post by bardu on 2009-03-05
Hi,

I seem to miss something too. In the "Jaunty" series I have found and downloaded 4 packages ending "_amd64.deb".

But installation fails because of a missing package:
> ubuntu@ubuntu:~/Desktop$ sudo dpkg -i xserver-xorg-video-*
(Reading database ... 104133 files and directories currently installed.)
Preparing to replace xserver-xorg-video-ati 1:6.11.0-1ubuntu1 (using xserver-xorg-video-ati_6.11.0.99+git20090305.5dc4b69f-0ubuntu0tormod_amd64.deb) ...
Unpacking replacement xserver-xorg-video-ati ...
Preparing to replace xserver-xorg-video-ati-dbg 1:6.11.0.99+git20090305.5dc4b69f-0ubuntu0tormod (using xserver-xorg-video-ati-dbg_6.11.0.99+git20090305.5dc4b69f-0ubuntu0tormod_amd64.deb) ...
Unpacking replacement xserver-xorg-video-ati-dbg ...
Preparing to replace xserver-xorg-video-radeon 1:6.11.0-1ubuntu1 (using xserver-xorg-video-radeon_6.11.0.99+git20090305.5dc4b69f-0ubuntu0tormod_amd64.deb) ...
Unpacking replacement xserver-xorg-video-radeon ...
Preparing to replace xserver-xorg-video-radeon-dbg 1:6.11.0.99+git20090305.5dc4b69f-0ubuntu0tormod (using xserver-xorg-video-radeon-dbg_6.11.0.99+git20090305.5dc4b69f-0ubuntu0tormod_amd64.deb) ...
Unpacking replacement xserver-xorg-video-radeon-dbg ...
dpkg: dependency problems prevent configuration of xserver-xorg-video-ati-dbg:
 xserver-xorg-video-ati-dbg depends on xserver-xorg-video-mach64-dbg; however:
  Package xserver-xorg-video-mach64-dbg is not installed.
 xserver-xorg-video-ati-dbg depends on xserver-xorg-video-r128-dbg; however:
  Package xserver-xorg-video-r128-dbg is not installed.
dpkg: error processing xserver-xorg-video-ati-dbg (--install):
 dependency problems - leaving unconfigured
Setting up xserver-xorg-video-radeon (1:6.11.0.99+git20090305.5dc4b69f-0ubuntu0tormod) ...
Processing triggers for man-db ...
Setting up xserver-xorg-video-radeon-dbg (1:6.11.0.99+git20090305.5dc4b69f-0ubuntu0tormod) ...
Setting up xserver-xorg-video-ati (1:6.11.0.99+git20090305.5dc4b69f-0ubuntu0tormod) ...
Errors were encountered while processing:
 xserver-xorg-video-ati-dbg
ubuntu@ubuntu:~/Desktop$ 


What do I wrong? I'm still on liveDVD.

---

### Post by CarpKing on 2009-03-05
> **tormod said:**
> As I noted in the bug report, please test the packages in my PPA [https://launchpad.net/~tormodvolden/+archive/ppa](https://launchpad.net/~tormodvolden/+archive/ppa) . For Ubuntu 8.10 only download the packages marked "Intrepid" in the Series column, you'll need both the -radeon and -ati packages for amd64 (*_amd64.deb).

Sorry for being a little offtopic, but will those packages work with the standard Intrepid X, Mesa, etc?  They say "all dependencies satisfied," but I just wanted to make sure there were no issues I should be aware of, and I haven't had much luck with Google on the matter.

---

### Post by tormod on 2009-03-06
> **bardu said:**
> Hi,

I seem to miss something too. In the "Jaunty" series I have found and downloaded 4 packages ending "_amd64.deb".

But installation fails because of a missing package:


What do I wrong? I'm still on liveDVD.

Do not install the -dbg packages because they apparently have a broken dependency.

---

### Post by tormod on 2009-03-06
> **shelvingguy said:**
> Here is the Xorg.0.log.old.

I don't think I can make sense of it.  Does it mean the driver is not where it expects it to be?  Have I installed it incorrectly?

The Xorg.0.log file (when the driver section in xorg.conf is blank "") seems to default to vesa.

It seems like you have not installed the driver. You will need the -radeon and -ati packages.

---

### Post by tormod on 2009-03-06
> **CarpKing said:**
> Sorry for being a little offtopic, but will those packages work with the standard Intrepid X, Mesa, etc?  They say "all dependencies satisfied," but I just wanted to make sure there were no issues I should be aware of, and I haven't had much luck with Google on the matter.
Yes, the drivers in my PPA are built for the standard distribution, with no dependencies. Of course, the binaries inside one source package will depend on each other, for instance, you will need to install both the -ati package and the -radeon package of same version.

There are sometimes some mesa and xorg-server packages in the PPA, but they have no API changes and do not create new dependencies.

---

### Post by shelvingguy on 2009-03-06
I reinstalled both the -ati and -radeon this morning.  It is a slightly different black screen (no cursor in upper left) but still unresponsive black screen.

The Xorg.0.log.old is the same.  It is not finding the drivers.

I am pretty sure I am installing them as you indicated in a previous post.  Do you know why they are not recognized?

Thanks.


> **shelvingguy said:**
> Here is the Xorg.0.log.old.

I don't think I can make sense of it.  Does it mean the driver is not where it expects it to be?  Have I installed it incorrectly?

The Xorg.0.log file (when the driver section in xorg.conf is blank "") seems to default to vesa.

---

### Post by tormod on 2009-03-06
> **shelvingguy said:**
> I reinstalled both the -ati and -radeon this morning.  It is a slightly different black screen (no cursor in upper left) but still unresponsive black screen.

The Xorg.0.log.old is the same.  It is not finding the drivers.

I am pretty sure I am installing them as you indicated in a previous post.  Do you know why they are not recognized?

Thanks.
I'd suggest you file a bug and attach the logs as well as "lspci -vvnn" and "ls -l /usr/lib/xorg/modules/drivers" output. Please also try Jaunty, because bugs in Jaunty have high priority and can be fixed quickly now before release.

It is strange, because not finding drivers should give you the console back, and not an unresponsive black screen.

---

### Post by shelvingguy on 2009-03-06
I upgraded to Jaunty and submitted the bug report with Xorg.0.log and the output from lspci -vvnn and ls -l /usr/lib/xorg/modules/drivers.  I hope I sent it to the right place.

Something different happened after the upgrade.  After the boot fails, it offers an error indicating that an x session is already running and should it start another one, or try again to start another session on :0.  Does it think I am running dual monitors?

In case you can make sense of it, I'll throw in the Xorg.0.log and other stuff (edit - bug link added [https://bugs.launchpad.net/bugs/338895]("https://bugs.launchpad.net/bugs/338895"))

Thanks.

---

### Post by tormod on 2009-03-06
> **shelvingguy said:**
> I upgraded to Jaunty and submitted the bug report with Xorg.0.log and the output from lspci -vvnn and ls -l /usr/lib/xorg/modules/drivers.  I hope I sent it to the right place.

Bug link?

If you filed a bug, there is no reason to paste in your full logs here, you may edit your post to make the thread readable again.

> 
Something different happened after the upgrade.  After the boot fails, it offers an error indicating that an x session is already running and should it start another one, or try again to start another session on :0.  Does it think I am running dual monitors?

In case you can make sense of it, I'll throw in the Xorg.0.log and other stuff.

Thanks.
```
Mode 1366x768 - 1474 790 0
[    1.656272] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    1.656285] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00ff 0xffffffff
[    1.656296] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 69860000
best_freq: 4294967295
best_feedback_div: 1_
best_ref_div: 1
best_post_div: 1

Fatal server error:
Couldn't find valid PLL dividers
```

This is [https://bugs.launchpad.net/bugs/336348](https://bugs.launchpad.net/bugs/336348) - reported by Bardu. It should be fixed in my PPA packages, did you install them?

In your /usr/lib/xorg/modules/drivers I noticed the radeon_drv.so and the ati_drv.so had quite different timestamps, but I haven't checked the contents of the amd64 packages to see if they are the same.

---

### Post by shelvingguy on 2009-03-06
Here's the link: [https://bugs.launchpad.net/bugs/338895]("https://bugs.launchpad.net/bugs/338895").

I did try your latest PPA packages (date March 5), but I'll check again.

As for the time stamps, that's above my head.

Thanks for the tip on editing the post and bearing with a noob.

---

### Post by joshbeetle on 2009-03-07
I also have a Toshiba Satellite A355.  From the lspci output it seems identical to shelvingguy's system.

I first installed 8.10.  With 8.10 I had to run with the vesa driver or the system would go to an unresponsive black screen.  I tried a number or drivers (original ati, fglrx, and updated ati driver noted in this thread).  Whenever I looked at an Xorg.0.log.old it always ended in this:

```
(EE) RADEON(0): Idle timed out, resetting engine...
(EE) RADEON(0): Idle timed out, resetting engine...
(EE) RADEON(0): Idle timed out, resetting engine...
(EE) RADEON(0): Idle timed out, resetting engine...
(EE) RADEON(0): Idle timed out, resetting engine...
...
```

The number of messages would increase the longer I waited before cycling the system.  Unfortunately I never saved a full log file.

Next I installed 9.04 alpha 5.  On 9.04 the system is able to boot with the ati driver.  The ati driver crashes with the error from bug #336348 and X is automatically restarted with the vesa driver.

After I install the updated ATI driver bug #336348 goes away, but I'm back to the same problem I had on 8.10.  Here is my complete Xorg.0.log.old:

```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux satellite 2.6.28-8-generic #28-Ubuntu SMP Fri Mar 6 00:09:20 UTC 2009 x86_64
Build Date: 07 March 2009  02:19:24AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.021472] (--) probed, [    0.021495] (**) from config file, [    0.021508] (==) default setting,
	[    0.021520] (++) from command line, [    0.021532] (!!) notice, [    0.021544] (II) informational,
	[    0.021556] (WW) warning, [    0.021568] (EE) error, [    0.021580] (NI) not implemented, [    0.021592] (??) unknown.
[    0.021716] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Mar  7 03:21:01 2009
[    0.022631] (==) Using config file: "/etc/X11/xorg.conf"
[    0.022816] (==) No Layout section.  Using the first Screen section.
[    0.022844] (**) |-->Screen "Default Screen" (0)
[    0.023150] (**) |   |-->Monitor "Configured Monitor"
[    0.023522] (**) |   |-->Device "Configured Video Device"
[    0.023557] (==) Automatically adding devices
[    0.023574] (==) Automatically enabling devices
[    0.085852] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.174650] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.174686] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.174702] (II) Cannot locate a core pointer device.
[    0.174712] (II) Cannot locate a core keyboard device.
[    0.174720] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.174740] (II) Loader magic: 0xb40
[    0.174750] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.174784] (II) Loader running on linux
[    0.174800] (++) using VT number 7

[    0.201026] (--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3650 rev 0, Mem @ 0xc0000000/536870912, 0xbfef0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    0.201225] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.201243] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.201344] (II) LoadModule: "extmod"
[    0.228159] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.228376] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.228402] (II) Loading extension MIT-SCREEN-SAVER
[    0.228409] (II) Loading extension XFree86-VidModeExtension
[    0.228415] (II) Loading extension XFree86-DGA
[    0.228422] (II) Loading extension DPMS
[    0.228428] (II) Loading extension XVideo
[    0.228435] (II) Loading extension XVideo-MotionCompensation
[    0.228442] (II) Loading extension X-Resource
[    0.228448] (II) LoadModule: "dbe"
[    0.228665] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.228746] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.228772] (II) Loading extension DOUBLE-BUFFER
[    0.228779] (II) LoadModule: "glx"
[    0.228989] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.229139] (II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.229180] (==) AIGLX enabled
[    0.229191] (II) Loading extension GLX
[    0.229201] (II) LoadModule: "record"
[    0.229409] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.229485] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.229510] (II) Loading extension RECORD
[    0.229517] (II) LoadModule: "dri"
[    0.229726] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.260036] (II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.260080] (II) Loading extension XFree86-DRI
[    0.260095] (II) LoadModule: "dri2"
[    0.260393] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.266713] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.266781] (II) Loading extension DRI2
[    0.266843] (II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
[    0.267346] (II) Matched radeon from file name radeon.ids
[    0.267933] (==) Matched radeon for the autoconfigured driver
[    0.267955] (==) Assigned the driver to the xf86ConfigLayout
[    0.267967] (II) LoadModule: "radeon"
[    0.268193] (II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
[    0.298298] (II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.5.99.902, module version = 6.11.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
[    0.299460] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
	ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
	ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
	ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
	ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
	ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
	ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
	ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
	ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics
[    0.305576] (II) Primary Device is: PCI 01@00:00:0
[    0.336894] (II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.337114] (II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
[    0.369221] (II) Setting vga for screen 0.
[    0.369710] (II) RADEON(0): TOTO SAYS 00000000bfef0000
[    0.369741] (II) RADEON(0): MMIO registers at 0x00000000bfef0000: size 64KB
[    0.369834] (II) RADEON(0): PCI bus 1 card 0 func 0
[    0.398770] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    0.398796] (==) RADEON(0): Depth 24, [    0.398807] (--) framebuffer bpp 32
[    0.398819] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    0.398833] (==) RADEON(0): Default visual is TrueColor
[    0.398886] (II) Loading sub module "vgahw"
[    0.398899] (II) LoadModule: "vgahw"
[    0.399023] (II) Loading /usr/lib/xorg/modules//libvgahw.so
[    0.399180] (II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
[    0.399243] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    0.399258] (==) RADEON(0): RGB weight 888
[    0.399270] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    0.399291] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 3650" (ChipID = 0x9591)
[    0.399309] (WW) RADEON(0): R600 support is mostly incomplete and very experimental
[    0.399320] (--) RADEON(0): Linear framebuffer at 0x00000000c0000000
[    0.399400] (II) RADEON(0): PCIE card detected
[    0.399481] (II) Loading sub module "int10"
[    0.399495] (II) LoadModule: "int10"
[    0.399600] (II) Loading /usr/lib/xorg/modules//libint10.so
[    0.415655] (II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
[    0.415787] (II) RADEON(0): initializing int10
[    0.416454] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    0.416616] (II) RADEON(0): ATOM BIOS detected
[    0.444846] (II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1179 SubsystemID: 0xff01
	IOBaseAddress: 0x2000
	Filename: BR29796.001 
	BIOS Bootup Message: 

Tosh_Compal_LA_M86M_DDR2 M86 GDDR2_32Mx16 256bit 1024MB 600e/500m           


[    0.444924] (II) RADEON(0): Framebuffer space used by Firmware (kb): 20
[    0.444936] (II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffb000
[    0.444946] (II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
[    0.444957] (II) RADEON(0): AtomBIOS VRAM scratch base: 0x1fffb000
[    0.444968] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    0.445026] (II) RADEON(0): Default Engine Clock: 600000
[    0.445039] (II) RADEON(0): Default Memory Clock: 500000
[    0.445049] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    0.445059] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    0.445068] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
[    0.445078] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
[    0.445088] (II) RADEON(0): Maximum Pixel Clock: 400000
[    0.445097] (II) RADEON(0): Reference Clock: 27000
[    0.445116] (II) RADEON(0): Direct rendering not officially supported on RN50/R600
[    0.445127] (II) RADEON(0): using shadow framebuffer
[    0.445136] (II) Loading sub module "shadow"
[    0.445145] (II) LoadModule: "shadow"
[    0.445269] (II) Loading /usr/lib/xorg/modules//libshadow.so
[    0.445917] (II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    0.445965] (II) RADEON(0): Detected total video RAM=4194303K, accessible=524288K (PCI BAR=524288K)
[    0.445978] (--) RADEON(0): Mapped VideoRAM: 524288 kByte (32 bit DDR SDRAM)
[    0.445991] (II) RADEON(0): Color tiling disabled
[    0.446001] (II) RADEON(0): Max desktop size set to 2560x1600
[    0.446011] (II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
[    0.446021] (II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
[    0.446035] (II) Loading sub module "ddc"
[    0.446046] (II) LoadModule: "ddc"
[    0.446065] (II) Module "ddc" already built-in
[    0.446074] (II) Loading sub module "i2c"
[    0.446083] (II) LoadModule: "i2c"
[    0.446101] (II) Module "i2c" already built-in
[    0.476793] (II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 500.000000
[    0.476858] (II) RADEON(0): PLL parameters: rf=2700 rd=1023 min=64800 max=120000; xclk=40000
[    0.476891] (WW) RADEON(0): LVDS Info:
XRes: 1366, YRes: 768, DotClock: 69860
HBlank: 108, HOverPlus: 48, HSyncWidth: 32
VBlank: 22, VOverPlus: 2, VSyncWidth: 5
[    0.476924] (II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
[    0.492099] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    0.492118] (II) RADEON(0): Output LVDS has no monitor section
[    0.492131] (II) RADEON(0): I2C bus "LVDS" initialized.
[    0.492148] (II) RADEON(0): Output HDMI-0 has no monitor section
[    0.492160] (II) RADEON(0): I2C bus "HDMI-0" initialized.
[    0.492175] (II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e60
[    0.492228] (II) RADEON(0): Port1:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_KLDSCP_LVTMA
  DDC reg: 0x7f68
[    0.492274] (II) RADEON(0): Port2:
  XRANDR name: HDMI-0
  Connector: HDMI-B
  DFP1: INTERNAL_UNIPHY
  DDC reg: 0x7e20
[    0.492334] (II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
[    0.492347] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    0.495076] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 0
[    0.501165] (II) RADEON(0): I2C device "LVDS:E-EDID segment register" registered at address 0x60.
[    0.501180] (II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
[    0.503896] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
finished output detect: 1
[    0.503925] (II) RADEON(0): I2C device "HDMI-0:E-EDID segment register" registered at address 0x60.
[    0.503937] (II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.
[    0.506688] (II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
finished output detect: 2
finished all detect
before xf86InitialConfiguration
[    0.509564] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
[    0.515566] (II) RADEON(0): Total number of valid Screen mode(s) added: 0
[    0.515696] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    0.515713] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    0.515723] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    0.515733] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.515743] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.515752] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.515762] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.515771] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.515780] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.515790] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.515799] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.515809] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.515819] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.515828] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.515838] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    0.515848] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    0.515858] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    0.515867] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    0.515877] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    0.515886] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    0.515926] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.515939] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.515949] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.515958] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.515968] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    0.515977] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    0.515987] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    0.515997] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    0.516007] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    0.516016] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    0.516026] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    0.516036] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.516046] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.516056] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.516065] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.516075] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.516085] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    0.516095] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    0.516105] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.516115] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.516125] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.516135] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    0.516144] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    0.516154] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    0.516164] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    0.516174] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.516183] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.516193] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.516203] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    0.516213] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    0.516223] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    0.516233] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    0.516242] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    0.516252] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    0.516264] (II) RADEON(0): Printing probed modes for output VGA-0
[    0.516281] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    0.516310] (II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    0.516330] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.516352] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.516371] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.519709] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
[    0.519738] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    0.519776] (II) RADEON(0): Added native panel mode: 1366x768
[    0.519897] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    0.519911] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    0.519942] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    0.519953] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.519963] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.519973] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.519983] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.519993] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.520003] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.520012] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.520022] (II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
[    0.520032] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.520042] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.520052] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.520062] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.520072] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    0.520082] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    0.520091] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    0.520102] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    0.520112] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    0.520122] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    0.520133] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.520142] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.520152] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.520163] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.520172] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    0.520182] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    0.520192] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    0.520202] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    0.520212] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    0.520222] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    0.520232] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    0.520242] (II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
[    0.520252] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.520262] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.520272] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.520281] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.520291] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.520301] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    0.520311] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    0.520321] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.520331] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.520340] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.520350] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    0.520360] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    0.520370] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    0.520380] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    0.520390] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.520415] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.520426] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.520436] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    0.520446] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    0.520456] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    0.520466] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    0.520476] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    0.520485] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    0.520498] (II) RADEON(0): Printing probed modes for output LVDS
[    0.520511] (II) RADEON(0): Modeline "1366x768"x60.0   69.86  1366 1414 1446 1474  768 770 775 790 (47.4 kHz)
[    0.520536] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    0.520555] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    0.520573] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    0.520591] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    0.520609] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.520627] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    0.520645] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.520664] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    0.524122] (II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
[    0.524172] (II) RADEON(0): EDID for output HDMI-0
[    0.524195] (II) RADEON(0): Output VGA-0 connected
[    0.524207] (II) RADEON(0): Output LVDS connected
[    0.524217] (II) RADEON(0): Output HDMI-0 disconnected
[    0.524239] (II) RADEON(0): Using fuzzy aspect match for initial modes
[    0.524251] (II) RADEON(0): Output VGA-0 using initial mode 1024x768
[    0.524261] (II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
[    0.524301] (==) RADEON(0): DPI set to (96, 96)
[    0.524312] (II) Loading sub module "fb"
[    0.524322] (II) LoadModule: "fb"
[    0.524458] (II) Loading /usr/lib/xorg/modules//libfb.so
[    0.524692] (II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    0.524757] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
[    0.524776] (II) Loading sub module "ramdac"
[    0.524786] (II) LoadModule: "ramdac"
[    0.524808] (II) Module "ramdac" already built-in
[    0.524821] (==) RADEON(0): Experimental R6xx/R7xx EXA support.
[    0.524833] (==) RADEON(0): Using EXA acceleration architecture
[    0.524844] (II) Loading sub module "exa"
[    0.524853] (II) LoadModule: "exa"
[    0.524943] (II) Loading /usr/lib/xorg/modules//libexa.so
[    0.688317] (II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
[    0.688552] (!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
[    0.688577] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    0.688592] (--) Depth 24 pixmap format is 32 bpp
[    0.688603] (II) do I need RAC?  No, I don't.
[    0.688617] (II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
[    0.688969] (II) RADEON(0): RADEONScreenInit c0000000 0 0
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Output CRT1 disable success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
mc fb loc is 01ff00ff
[    1.386888] (II) RADEON(0): RADEONInitMemoryMap() : 
[    1.386900] (II) RADEON(0):   mem_size         : 0xffffffff
[    1.386909] (II) RADEON(0):   MC_FB_LOCATION   : 0x01ff00ff
[    1.386919] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    1.386929] (II) RADEON(0): Depth moves disabled by default
[    1.386966] (II) RADEON(0): Allocating from a screen of 524288 kb
[    1.386978] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00801000
[    1.386990] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00805000
[    1.387000] (II) RADEON(0): Will use 8196 kb for front buffer at offset 0x00000000
[    1.387011] (II) RADEON(0): Will use 516060 kb for X Server offscreen at offset 0x00809000
[    1.413493] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    1.413536] (II) RADEON(0):   MC_FB_LOCATION   : 0x01ff00ff 0xffffffff
[    1.413548] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    1.708248] (EE) RADEON(0): Idle timed out, resetting engine...
[    1.934622] (EE) RADEON(0): Idle timed out, resetting engine...
[    2.143158] (EE) RADEON(0): Idle timed out, resetting engine...
[    2.346762] (EE) RADEON(0): Idle timed out, resetting engine...
[    2.550310] (EE) RADEON(0): Idle timed out, resetting engine...
[    2.753867] (EE) RADEON(0): Idle timed out, resetting engine...
[    2.957721] (EE) RADEON(0): Idle timed out, resetting engine...
[    3.161292] (EE) RADEON(0): Idle timed out, resetting engine...
[    3.364854] (EE) RADEON(0): Idle timed out, resetting engine...
[    3.568407] (EE) RADEON(0): Idle timed out, resetting engine...
[    3.771960] (EE) RADEON(0): Idle timed out, resetting engine...
[    3.975522] (EE) RADEON(0): Idle timed out, resetting engine...
[    4.179076] (EE) RADEON(0): Idle timed out, resetting engine...
[    4.382629] (EE) RADEON(0): Idle timed out, resetting engine...
[    4.586211] (EE) RADEON(0): Idle timed out, resetting engine...
[    4.793159] (EE) RADEON(0): Idle timed out, resetting engine...
[    5.003869] (EE) RADEON(0): Idle timed out, resetting engine...
[    5.212454] (EE) RADEON(0): Idle timed out, resetting engine...
[    5.416290] (EE) RADEON(0): Idle timed out, resetting engine...
[    5.619891] (EE) RADEON(0): Idle timed out, resetting engine...
[    5.823563] (EE) RADEON(0): Idle timed out, resetting engine...
[    6.027252] (EE) RADEON(0): Idle timed out, resetting engine...
[    6.230892] (EE) RADEON(0): Idle timed out, resetting engine...
[    6.434558] (EE) RADEON(0): Idle timed out, resetting engine...
[    6.640381] (EE) RADEON(0): Idle timed out, resetting engine...
[    6.845266] (EE) RADEON(0): Idle timed out, resetting engine...
[    7.048837] (EE) RADEON(0): Idle timed out, resetting engine...
[    7.254409] (EE) RADEON(0): Idle timed out, resetting engine...
[    7.458023] (EE) RADEON(0): Idle timed out, resetting engine...
[    7.661541] (EE) RADEON(0): Idle timed out, resetting engine...
[    7.865112] (EE) RADEON(0): Idle timed out, resetting engine...
[    8.068685] (EE) RADEON(0): Idle timed out, resetting engine...
[    8.273611] (EE) RADEON(0): Idle timed out, resetting engine...
[    8.477212] (EE) RADEON(0): Idle timed out, resetting engine...
[    8.680850] (EE) RADEON(0): Idle timed out, resetting engine...
[    8.884393] (EE) RADEON(0): Idle timed out, resetting engine...
[    9.088001] (EE) RADEON(0): Idle timed out, resetting engine...
[    9.291573] (EE) RADEON(0): Idle timed out, resetting engine...
[    9.495151] (EE) RADEON(0): Idle timed out, resetting engine...
[    9.698738] (EE) RADEON(0): Idle timed out, resetting engine...
[    9.902358] (EE) RADEON(0): Idle timed out, resetting engine...
[   10.105928] (EE) RADEON(0): Idle timed out, resetting engine...
[   10.309466] (EE) RADEON(0): Idle timed out, resetting engine...
[   10.513037] (EE) RADEON(0): Idle timed out, resetting engine...
[   10.716620] (EE) RADEON(0): Idle timed out, resetting engine...
[   10.920189] (EE) RADEON(0): Idle timed out, resetting engine...
[   11.123808] (EE) RADEON(0): Idle timed out, resetting engine...
[   11.327352] (EE) RADEON(0): Idle timed out, resetting engine...
[   11.531012] (EE) RADEON(0): Idle timed out, resetting engine...
[   11.734637] (EE) RADEON(0): Idle timed out, resetting engine...
[   11.938196] (EE) RADEON(0): Idle timed out, resetting engine...
[   12.141750] (EE) RADEON(0): Idle timed out, resetting engine...
[   12.345341] (EE) RADEON(0): Idle timed out, resetting engine...
[   12.548891] (EE) RADEON(0): Idle timed out, resetting engine...
[   12.752569] (EE) RADEON(0): Idle timed out, resetting engine...
[   12.956460] (EE) RADEON(0): Idle timed out, resetting engine...
[   13.160099] (EE) RADEON(0): Idle timed out, resetting engine...
[   13.363671] (EE) RADEON(0): Idle timed out, resetting engine...
[   13.567292] (EE) RADEON(0): Idle timed out, resetting engine...
[   13.770847] (EE) RADEON(0): Idle timed out, resetting engine...
[   13.974456] (EE) RADEON(0): Idle timed out, resetting engine...
[   14.178057] (EE) RADEON(0): Idle timed out, resetting engine...
[   14.382031] (EE) RADEON(0): Idle timed out, resetting engine...
[   14.585915] (EE) RADEON(0): Idle timed out, resetting engine...
[   14.791746] (EE) RADEON(0): Idle timed out, resetting engine...
[   15.000686] (EE) RADEON(0): Idle timed out, resetting engine...
[   15.204570] (EE) RADEON(0): Idle timed out, resetting engine...
[   15.408424] (EE) RADEON(0): Idle timed out, resetting engine...
[   15.615048] (EE) RADEON(0): Idle timed out, resetting engine...
[   15.820530] (EE) RADEON(0): Idle timed out, resetting engine...
[   16.024216] (EE) RADEON(0): Idle timed out, resetting engine...
[   16.229267] (EE) RADEON(0): Idle timed out, resetting engine...
[   16.433272] (EE) RADEON(0): Idle timed out, resetting engine...
[   16.636865] (EE) RADEON(0): Idle timed out, resetting engine...
[   16.840594] (EE) RADEON(0): Idle timed out, resetting engine...
[   17.044191] (EE) RADEON(0): Idle timed out, resetting engine...
[   17.247742] (EE) RADEON(0): Idle timed out, resetting engine...
[   17.451306] (EE) RADEON(0): Idle timed out, resetting engine...
[   17.654909] (EE) RADEON(0): Idle timed out, resetting engine...
[   17.860172] (EE) RADEON(0): Idle timed out, resetting engine...
[   18.063774] (EE) RADEON(0): Idle timed out, resetting engine...
[   18.267444] (EE) RADEON(0): Idle timed out, resetting engine...
[   18.471037] (EE) RADEON(0): Idle timed out, resetting engine...
[   18.674640] (EE) RADEON(0): Idle timed out, resetting engine...
[   18.883118] (EE) RADEON(0): Idle timed out, resetting engine...
[   19.088020] (EE) RADEON(0): Idle timed out, resetting engine...
[   19.292282] (EE) RADEON(0): Idle timed out, resetting engine...
[   19.495991] (EE) RADEON(0): Idle timed out, resetting engine...
[   19.705764] (EE) RADEON(0): Idle timed out, resetting engine...
[   19.909464] (EE) RADEON(0): Idle timed out, resetting engine...
[   20.113120] (EE) RADEON(0): Idle timed out, resetting engine...
[   20.316847] (EE) RADEON(0): Idle timed out, resetting engine...
[   20.521440] (EE) RADEON(0): Idle timed out, resetting engine...
[   20.725047] (EE) RADEON(0): Idle timed out, resetting engine...
[   20.928618] (EE) RADEON(0): Idle timed out, resetting engine...
[   21.132198] (EE) RADEON(0): Idle timed out, resetting engine...
[   21.335729] (EE) RADEON(0): Idle timed out, resetting engine...
[   21.539443] (EE) RADEON(0): Idle timed out, resetting engine...
[   21.743110] (EE) RADEON(0): Idle timed out, resetting engine...
[   21.946621] (EE) RADEON(0): Idle timed out, resetting engine...
[   22.150208] (EE) RADEON(0): Idle timed out, resetting engine...
[   22.353838] (EE) RADEON(0): Idle timed out, resetting engine...
[   22.557412] (EE) RADEON(0): Idle timed out, resetting engine...
[   22.760943] (EE) RADEON(0): Idle timed out, resetting engine...
[   22.964500] (EE) RADEON(0): Idle timed out, resetting engine...
[   23.168037] (EE) RADEON(0): Idle timed out, resetting engine...
[   23.371628] (EE) RADEON(0): Idle timed out, resetting engine...
[   23.575266] (EE) RADEON(0): Idle timed out, resetting engine...
[   23.778912] (EE) RADEON(0): Idle timed out, resetting engine...
[   23.982483] (EE) RADEON(0): Idle timed out, resetting engine...
[   24.186036] (EE) RADEON(0): Idle timed out, resetting engine...
[   24.389592] (EE) RADEON(0): Idle timed out, resetting engine...
[   24.593154] (EE) RADEON(0): Idle timed out, resetting engine...
[   24.796783] (EE) RADEON(0): Idle timed out, resetting engine...
[   25.000347] (EE) RADEON(0): Idle timed out, resetting engine...
[   25.203888] (EE) RADEON(0): Idle timed out, resetting engine...
[   25.407445] (EE) RADEON(0): Idle timed out, resetting engine...
[   25.611022] (EE) RADEON(0): Idle timed out, resetting engine...
[   25.814578] (EE) RADEON(0): Idle timed out, resetting engine...
[   26.018309] (EE) RADEON(0): Idle timed out, resetting engine...
[   26.221952] (EE) RADEON(0): Idle timed out, resetting engine...
[   26.425487] (EE) RADEON(0): Idle timed out, resetting engine...
[   26.629047] (EE) RADEON(0): Idle timed out, resetting engine...
[   26.832689] (EE) RADEON(0): Idle timed out, resetting engine...
[   27.036293] (EE) RADEON(0): Idle timed out, resetting engine...
[   27.239879] (EE) RADEON(0): Idle timed out, resetting engine...
[   27.443420] (EE) RADEON(0): Idle timed out, resetting engine...
[   27.646979] (EE) RADEON(0): Idle timed out, resetting engine...
[   27.850630] (EE) RADEON(0): Idle timed out, resetting engine...
[   28.054328] (EE) RADEON(0): Idle timed out, resetting engine...
[   28.258081] (EE) RADEON(0): Idle timed out, resetting engine...
[   28.461624] (EE) RADEON(0): Idle timed out, resetting engine...
[   28.665145] (EE) RADEON(0): Idle timed out, resetting engine...
[   28.869533] (EE) RADEON(0): Idle timed out, resetting engine...
[   29.073129] (EE) RADEON(0): Idle timed out, resetting engine...
[   29.276656] (EE) RADEON(0): Idle timed out, resetting engine...
[   29.480240] (EE) RADEON(0): Idle timed out, resetting engine...
[   29.683848] (EE) RADEON(0): Idle timed out, resetting engine...
[   29.887439] (EE) RADEON(0): Idle timed out, resetting engine...
[   30.090995] (EE) RADEON(0): Idle timed out, resetting engine...
[   30.294535] (EE) RADEON(0): Idle timed out, resetting engine...
[   30.498088] (EE) RADEON(0): Idle timed out, resetting engine...
[   30.701600] (EE) RADEON(0): Idle timed out, resetting engine...
[   30.905214] (EE) RADEON(0): Idle timed out, resetting engine...
[   31.108760] (EE) RADEON(0): Idle timed out, resetting engine...
[   31.312325] (EE) RADEON(0): Idle timed out, resetting engine...
[   31.515889] (EE) RADEON(0): Idle timed out, resetting engine...
[   31.719459] (EE) RADEON(0): Idle timed out, resetting engine...
[   31.923105] (EE) RADEON(0): Idle timed out, resetting engine...
[   32.126670] (EE) RADEON(0): Idle timed out, resetting engine...
[   32.330203] (EE) RADEON(0): Idle timed out, resetting engine...
[   32.533796] (EE) RADEON(0): Idle timed out, resetting engine...
[   32.737371] (EE) RADEON(0): Idle timed out, resetting engine...
[   32.940880] (EE) RADEON(0): Idle timed out, resetting engine...
[   33.144420] (EE) RADEON(0): Idle timed out, resetting engine...
[   33.347945] (EE) RADEON(0): Idle timed out, resetting engine...
[   33.551515] (EE) RADEON(0): Idle timed out, resetting engine...
[   33.755078] (EE) RADEON(0): Idle timed out, resetting engine...
[   33.958591] (EE) RADEON(0): Idle timed out, resetting engine...
[   34.162172] (EE) RADEON(0): Idle timed out, resetting engine...
[   34.365703] (EE) RADEON(0): Idle timed out, resetting engine...
[   34.569230] (EE) RADEON(0): Idle timed out, resetting engine...
[   34.772797] (EE) RADEON(0): Idle timed out, resetting engine...
[   34.976368] (EE) RADEON(0): Idle timed out, resetting engine...
[   35.179901] (EE) RADEON(0): Idle timed out, resetting engine...
[   35.383407] (EE) RADEON(0): Idle timed out, resetting engine...
[   35.586980] (EE) RADEON(0): Idle timed out, resetting engine...
[   35.790536] (EE) RADEON(0): Idle timed out, resetting engine...
[   35.994121] (EE) RADEON(0): Idle timed out, resetting engine...
[   36.197702] (EE) RADEON(0): Idle timed out, resetting engine...
[   36.401254] (EE) RADEON(0): Idle timed out, resetting engine...
[   36.604895] (EE) RADEON(0): Idle timed out, resetting engine...
[   36.808582] (EE) RADEON(0): Idle timed out, resetting engine...
[   37.012209] (EE) RADEON(0): Idle timed out, resetting engine...
[   37.215805] (EE) RADEON(0): Idle timed out, resetting engine...
[   37.419515] (EE) RADEON(0): Idle timed out, resetting engine...
[   37.623159] (EE) RADEON(0): Idle timed out, resetting engine...
[   37.826746] (EE) RADEON(0): Idle timed out, resetting engine...
[   38.030320] (EE) RADEON(0): Idle timed out, resetting engine...
[   38.233914] (EE) RADEON(0): Idle timed out, resetting engine...
[   38.437449] (EE) RADEON(0): Idle timed out, resetting engine...
[   38.640963] (EE) RADEON(0): Idle timed out, resetting engine...
[   38.844541] (EE) RADEON(0): Idle timed out, resetting engine...
[   39.048072] (EE) RADEON(0): Idle timed out, resetting engine...
[   39.251584] (EE) RADEON(0): Idle timed out, resetting engine...
[   39.455115] (EE) RADEON(0): Idle timed out, resetting engine...
[   39.658657] (EE) RADEON(0): Idle timed out, resetting engine...
[   39.862166] (EE) RADEON(0): Idle timed out, resetting engine...
[   40.065704] (EE) RADEON(0): Idle timed out, resetting engine...
[   40.269219] (EE) RADEON(0): Idle timed out, resetting engine...
[   40.472746] (EE) RADEON(0): Idle timed out, resetting engine...
[   40.676268] (EE) RADEON(0): Idle timed out, resetting engine...
[   40.879852] (EE) RADEON(0): Idle timed out, resetting engine...
[   41.083467] (EE) RADEON(0): Idle timed out, resetting engine...
[   41.287081] (EE) RADEON(0): Idle timed out, resetting engine...
[   41.490615] (EE) RADEON(0): Idle timed out, resetting engine...
[   41.694190] (EE) RADEON(0): Idle timed out, resetting engine...
[   41.897813] (EE) RADEON(0): Idle timed out, resetting engine...
[   42.101358] (EE) RADEON(0): Idle timed out, resetting engine...
[   42.304860] (EE) RADEON(0): Idle timed out, resetting engine...
[   42.508406] (EE) RADEON(0): Idle timed out, resetting engine...
[   42.712061] (EE) RADEON(0): Idle timed out, resetting engine...
[   42.915725] (EE) RADEON(0): Idle timed out, resetting engine...
[   43.119384] (EE) RADEON(0): Idle timed out, resetting engine...
[   43.322937] (EE) RADEON(0): Idle timed out, resetting engine...
[   43.526485] (EE) RADEON(0): Idle timed out, resetting engine...
[   43.730020] (EE) RADEON(0): Idle timed out, resetting engine...
[   43.933541] (EE) RADEON(0): Idle timed out, resetting engine...
[   44.137120] (EE) RADEON(0): Idle timed out, resetting engine...
[   44.340629] (EE) RADEON(0): Idle timed out, resetting engine...
[   44.544197] (EE) RADEON(0): Idle timed out, resetting engine...
[   44.747729] (EE) RADEON(0): Idle timed out, resetting engine...
[   44.951266] (EE) RADEON(0): Idle timed out, resetting engine...
[   45.154784] (EE) RADEON(0): Idle timed out, resetting engine...
[   45.358329] (EE) RADEON(0): Idle timed out, resetting engine...
[   45.561913] (EE) RADEON(0): Idle timed out, resetting engine...
[   45.765505] (EE) RADEON(0): Idle timed out, resetting engine...
[   45.969079] (EE) RADEON(0): Idle timed out, resetting engine...
[   46.172636] (EE) RADEON(0): Idle timed out, resetting engine...
[   46.376146] (EE) RADEON(0): Idle timed out, resetting engine...
[   46.579679] (EE) RADEON(0): Idle timed out, resetting engine...
[   46.783277] (EE) RADEON(0): Idle timed out, resetting engine...
[   46.986879] (EE) RADEON(0): Idle timed out, resetting engine...
[   47.190444] (EE) RADEON(0): Idle timed out, resetting engine...
[   47.393962] (EE) RADEON(0): Idle timed out, resetting engine...
[   47.597469] (EE) RADEON(0): Idle timed out, resetting engine...
[   47.801024] (EE) RADEON(0): Idle timed out, resetting engine...
[   48.004620] (EE) RADEON(0): Idle timed out, resetting engine...
[   48.208220] (EE) RADEON(0): Idle timed out, resetting engine...
[   48.411786] (EE) RADEON(0): Idle timed out, resetting engine...
[   48.615296] (EE) RADEON(0): Idle timed out, resetting engine...
[   48.818943] (EE) RADEON(0): Idle timed out, resetting engine...
[   49.022530] (EE) RADEON(0): Idle timed out, resetting engine...
[   49.226086] (EE) RADEON(0): Idle timed out, resetting engine...
[   49.429652] (EE) RADEON(0): Idle timed out, resetting engine...
[   49.633186] (EE) RADEON(0): Idle timed out, resetting engine...
[   49.836704] (EE) RADEON(0): Idle timed out, resetting engine...
[   50.040265] (EE) RADEON(0): Idle timed out, resetting engine...
[   50.243791] (EE) RADEON(0): Idle timed out, resetting engine...
[   50.447325] (EE) RADEON(0): Idle timed out, resetting engine...
[   50.650891] (EE) RADEON(0): Idle timed out, resetting engine...
[   50.854432] (EE) RADEON(0): Idle timed out, resetting engine...
[   51.057990] (EE) RADEON(0): Idle timed out, resetting engine...
[   51.261497] (EE) RADEON(0): Idle timed out, resetting engine...
[   51.465103] (EE) RADEON(0): Idle timed out, resetting engine...
[   51.668652] (EE) RADEON(0): Idle timed out, resetting engine...
[   51.872224] (EE) RADEON(0): Idle timed out, resetting engine...
[   52.075731] (EE) RADEON(0): Idle timed out, resetting engine...
[   52.279300] (EE) RADEON(0): Idle timed out, resetting engine...
[   52.482828] (EE) RADEON(0): Idle timed out, resetting engine...
[   52.686403] (EE) RADEON(0): Idle timed out, resetting engine...
[   52.890001] (EE) RADEON(0): Idle timed out, resetting engine...
[   53.093568] (EE) RADEON(0): Idle timed out, resetting engine...
[   53.297187] (EE) RADEON(0): Idle timed out, resetting engine...
[   53.500752] (EE) RADEON(0): Idle timed out, resetting engine...
[   53.704256] (EE) RADEON(0): Idle timed out, resetting engine...
[   53.907800] (EE) RADEON(0): Idle timed out, resetting engine...
[   54.111346] (EE) RADEON(0): Idle timed out, resetting engine...
[   54.314890] (EE) RADEON(0): Idle timed out, resetting engine...
[   54.518452] (EE) RADEON(0): Idle timed out, resetting engine...
[   54.722034] (EE) RADEON(0): Idle timed out, resetting engine...
[   54.925619] (EE) RADEON(0): Idle timed out, resetting engine...
[   55.129178] (EE) RADEON(0): Idle timed out, resetting engine...
[   55.332749] (EE) RADEON(0): Idle timed out, resetting engine...
[   55.536275] (EE) RADEON(0): Idle timed out, resetting engine...
[   55.739804] (EE) RADEON(0): Idle timed out, resetting engine...
[   55.943337] (EE) RADEON(0): Idle timed out, resetting engine...
[   56.146873] (EE) RADEON(0): Idle timed out, resetting engine...
[   56.350568] (EE) RADEON(0): Idle timed out, resetting engine...
[   56.554252] (EE) RADEON(0): Idle timed out, resetting engine...
[   56.758001] (EE) RADEON(0): Idle timed out, resetting engine...
[   56.961743] (EE) RADEON(0): Idle timed out, resetting engine...
[   57.165515] (EE) RADEON(0): Idle timed out, resetting engine...
[   57.369269] (EE) RADEON(0): Idle timed out, resetting engine...
[   57.572987] (EE) RADEON(0): Idle timed out, resetting engine...
[   57.776663] (EE) RADEON(0): Idle timed out, resetting engine...
[   57.980371] (EE) RADEON(0): Idle timed out, resetting engine...
[   58.184137] (EE) RADEON(0): Idle timed out, resetting engine...
[   58.387965] (EE) RADEON(0): Idle timed out, resetting engine...
[   58.591770] (EE) RADEON(0): Idle timed out, resetting engine...
[   58.795756] (EE) RADEON(0): Idle timed out, resetting engine...
[   58.999970] (EE) RADEON(0): Idle timed out, resetting engine...
[   59.203536] (EE) RADEON(0): Idle timed out, resetting engine...
[   59.407064] (EE) RADEON(0): Idle timed out, resetting engine...
[   59.610616] (EE) RADEON(0): Idle timed out, resetting engine...
[   59.814211] (EE) RADEON(0): Idle timed out, resetting engine...
[   60.017755] (EE) RADEON(0): Idle timed out, resetting engine...
[   60.221339] (EE) RADEON(0): Idle timed out, resetting engine...
[   60.424877] (EE) RADEON(0): Idle timed out, resetting engine...
[   60.628441] (EE) RADEON(0): Idle timed out, resetting engine...
[   60.832015] (EE) RADEON(0): Idle timed out, resetting engine...
[   61.035623] (EE) RADEON(0): Idle timed out, resetting engine...
[   61.239260] (EE) RADEON(0): Idle timed out, resetting engine...
[   61.442885] (EE) RADEON(0): Idle timed out, resetting engine...
[   61.646405] (EE) RADEON(0): Idle timed out, resetting engine...
[   61.849964] (EE) RADEON(0): Idle timed out, resetting engine...
[   62.053537] (EE) RADEON(0): Idle timed out, resetting engine...
[   62.257073] (EE) RADEON(0): Idle timed out, resetting engine...
[   62.460639] (EE) RADEON(0): Idle timed out, resetting engine...
[   62.664341] (EE) RADEON(0): Idle timed out, resetting engine...
[   62.883298] (EE) RADEON(0): Idle timed out, resetting engine...
[   63.086839] (EE) RADEON(0): Idle timed out, resetting engine...
[   63.290442] (EE) RADEON(0): Idle timed out, resetting engine...
[   63.493983] (EE) RADEON(0): Idle timed out, resetting engine...
```

---

### Post by Max Roswell on 2009-03-12
Wouldn't you know it?  I got so frustrated with the display problems 8.10 was causing me on my old machine that I went out and bought a new one...a Toshiba Satellite A355.

:-k

I think maybe the gods don't want me to use Ubuntu.  I think maybe that's the problem.

---

### Post by shelvingguy on 2009-03-12
I was feeling the same way.  I got hooked on Linux on an old Dell laptop, but the on board Intel Chipset had compatibility issues.

So, I went out and got a shiny new Satellite A355 with dual booting in mind.  That was more than I month ago and I still have to use vesa to get a GUI. If I knew then what I know now, I would have researched my hardware before buying it.  Noob lesson learned.  It turns out some of the more recent ATI video cards have compatibility issues and that the manufacturer might not be that concerned if their hardware works with linux. 

On the bright side, the developers seem engaged and optimistic that a resolution is not to far away.

There is a bug posted here: [https://bugs.launchpad.net/bugs/341681]("https://bugs.launchpad.net/bugs/341681")

I think it would help if you posted your situation there also.

---

### Post by ninjie on 2009-03-12
Oh Blast.  I read through all of these posts hoping for a fix.  I currently use a Lenovo t500 and am experiencing the same issues as you lot.

I switched to Ubuntu 64 for its better performance with regard to my VMs but I cant enable acceleration.  

...Will an older version of Ubuntu recognize this GFX Card?  Is there anyway around this issue?

---

### Post by Max Roswell on 2009-03-12
> **shelvingguy said:**
> I was feeling the same way.  I got hooked on Linux on an old Dell laptop, but the on board Intel Chipset had compatibility issues...

I think it would help if you posted your situation there also.


I will if and when I try to install Ubuntu.  I *just* bought the new machine.  Honestly, it's frustrating.  The response to my old display problem was, "Oh, yeah, that's a cheap graphics card that sucks.  You should get a better one."  Now that I have a better one, it's "Oh, yeah, that's ATI, they don't release drivers."

So I guess Ubuntu just works...on mid-range NVidia cards.

---

### Post by shelvingguy on 2009-03-12
I agree with you.  It has been frustrating.  On the other hand, I've learned more about linux in the last couple of months than I ever knew about windows.  I enjoy that.  Plus, there is some great software out there that I would not be willing or able to purchase commercially.

---

### Post by Max Roswell on 2009-03-12
I agree with you there.  I have learned a lot each time something new goes sideways on me.  But man, it gets old.

In this case, I guess I really should have done more research on my purchase if running Ubuntu was important to me, and to be totally fair, a little Googling tells me that nobody's got these cards working in any distro. Still frustrating to go from one display problem to another.  

Once someone gets this working, I'll probably come back to the Linux fold.  In the meantime, I guess it's time to re-acquaint myself with Windows.

---

### Post by tormod on 2009-03-12
I would be optimistic about these cards. There is a lot of development going on for the R600 (and R700) series chipsets these days. We hope to get some of the newest stuff into Jaunty after the alpha-6 freeze is lifted.

---

### Post by joshbeetle on 2009-03-12
I went back to Intrepid and installed the radeonhd driver using the instructions on [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD).  The radeonhd driver fails quickly but doesn't cause X to hang.  It's the best behaving driver I've found.  It allows me to continue in low graphics mode.

After removing 2GB of RAM I can start X successfully with the radeonhd driver and the proper screen resolution.  I bet some of the other drivers may also work after removing some RAM.

I tried leaving all my memory in and setting the mem=2048M boot option, but that wasn't enough for me.  I had to physically remove the memory.

This has been a known issue with Asus laptops (see [http://www.x.org/wiki/radeonhd#head-d0cfd39d1b149a43f0c1d862f21f4b3ddcb43ae2](http://www.x.org/wiki/radeonhd#head-d0cfd39d1b149a43f0c1d862f21f4b3ddcb43ae2)) but it apparently is a problem on Toshiba laptops as well.

---

### Post by Max Roswell on 2009-03-13
> **tormod said:**
> I would be optimistic about these cards. There is a lot of development going on for the R600 (and R700) series chipsets these days. We hope to get some of the newest stuff into Jaunty after the alpha-6 freeze is lifted.

Well, that does give me hope, then.  I feel so passive/aggressive..."I don't *want* to use Windows - look what you're making me do!  THIS IS WHY WE CAN'T HAVE NICE THINGS!"

But seriously...please keep us updated in this thread.  Thank you for the hard work!

---

### Post by krazyd on 2009-03-13
The open source radeon driver just got released with EXA acceleration and Xv video acceleration on R600/R700 (ie HD2xxx - 4xxx): [http://lists.x.org/archives/xorg-driver-ati/2009-March/008886.html](http://lists.x.org/archives/xorg-driver-ati/2009-March/008886.html)

This isn't 3D, but fast 2D and tear-free video.

---

### Post by tormod on 2009-03-15
> **krazyd said:**
> The open source radeon driver just got released with EXA acceleration and Xv video acceleration on R600/R700
Most of this 6.12 release is already in Jaunty (and all of it in my PPA). But proper acceleration depends on updated drm kernel modules also, which will come to the Jaunty kernel soon.

Meanwhile, you can try out the drm-snapshot packages from the xorg-edgers PPA, and build the drm modules as described on the PPA page (even if the instructions say not to do it for Jaunty...)*. I do not have r600/r700 hardware to test, but at least running these drm modules does not seem to blow up my R400 computer.

However, the initialisation (and 2D) problems people are seeing might not be fixed by new drm modules.

*) after installation you should see "Initialized drm 1.1.0 20090314r6xx7xx" in dmesg.

---

### Post by factotum218 on 2009-03-15
I also have this card on an Acer Aspire 6530.
Same issue as well. Blank screen. I got something out of an opensuse 11.1 live cd although without the 3d acceleration. It was something at least.

So did I hear this right? If I pull 2Gb of my 4Gb of ram I could have working 3d acceleration?
I dont mind doing it, I barely use 1gb (in linux anyways). Can anyone confirm this?

I've been sitting here bashing my head against a wall for the last month after getting this card and being stuck in vista. It's driving me absolutely nuts!!

---

### Post by tormod on 2009-03-16
> **factotum218 said:**
> So did I hear this right? If I pull 2Gb of my 4Gb of ram I could have working 3d acceleration?
No, only 2D acceleration (EXA and xv video etc) for now, on your card.

---

### Post by shelvingguy on 2009-03-16
Tormod - Should I try pulling 2GB of RAM to see if it gets the "ati" driver working?

---

### Post by tormod on 2009-03-16
> **shelvingguy said:**
> Tormod - Should I try pulling 2GB of RAM to see if it gets the "ati" driver working?
If it is not too much trouble, please try.

---

### Post by markbuntu on 2009-03-16
I have a HD3650 PCIx, not mobility. It is working just fine with the radeonhd driver from the jaunty repo so there is hope for you guys.

---

### Post by shelvingguy on 2009-03-16
Tormod:

I pulled one of the 2GB RAM chips and rebooted with the ati driver.  It worked.  I'm not sure how to assess the performance.  But, for the first time since I bought this computer, I have linux in the native resolution.

I'll attach the log to the bug.

Can you tell me what this means relative to the bug?

Thanks.

---

### Post by factotum218 on 2009-03-17
So, pull out half my ram, run 32bit on a 64bit system to run Linux?

I only say that because I think it's funny and am still considering it. Haven't played any games since Neverwinter Nights came out.

---

### Post by shelvingguy on 2009-03-17
I'm not an expert by any stretch, and have not clue why it works. But, removing the RAM is the only thing that has let this card get past black screen.

---

### Post by zika on 2009-03-17
> **markbuntu said:**
> I have a HD3650 PCIx, not mobility. It is working just fine with the radeonhd driver from the jaunty repo so there is hope for you guys.
I have ASUS ah 3650 (a.k.a. ATI HD 3650 512M). two questions:

1. what do You mean with:"just fine"?
2. how did You change to "radeonhd"? ```
sudo apt-get xserver-xorg-video-radeonhd
```and in xorg.conf:```
Section "Device"
    Identifier    "Configured Video Device"
        Driver           "radeonhd"
...
EndSection
```that scenario does not work in my case. that is why I'm asking, to get some help ... :) I get just non-usable X. radeon (with known restrictions) works ...

**update:** I was wrong saying that radeonhd doesn't work with my card. What was wrong was method of trying it. Method given above doesn't work. It created a file /home/zika/xorg.conf.new which should be moved to /etc/X11/xorg.conf and ... radeonhd works!

**update:** No, it doesn't work after reboot :( Back to radeon ...

---

### Post by markbuntu on 2009-03-17
> **zika said:**
> I have ASUS ah 3650 (a.k.a. ATI HD 3650 512M). two questions:

1. what do You mean with:"just fine"?
2. how did You change to "radeonhd"? ```
sudo apt-get xserver-xorg-video-radeonhd
```and in xorg.conf:```
Section "Device"
	Identifier	"Configured Video Device"
        Driver           "radeonhd"
...
EndSection
```

that scenario does not work in my case. that is why I'm asking, to get some help ... :) I get just non-usable X. radeon (with known restrictions) works ...

Well, I used synaptic instead of apt-get but basically yes, that is all I did. Get the driver and then change that line in xorg.conf and restart x. 
No 3D of course but I do have my desktop across both my monitors now using System/Preferences/Display to configure it. I was using the VESA driver before changing and have all updates.

My card is a VisionTek PCIx2 HD36501GB on a BiostarTA790GXA2+ mobo with a AMD6000x2 cpu and 6GB 800 DDR2 ram. The on-board 3300 gpu is not being used and both monitors are on the HD3650, a 24 inch 1920x1200 and a 19 inch 1280x1024.

I also have a HD3450 that I am going to try to use in combination with the 3300 on the mobo when I have a bunch of free time and fglrx gets fixed. My eventual goal is to have 6 monitors, 2 on each gpu.

---

### Post by zika on 2009-03-17
> **markbuntu said:**
> Well, I used synaptic instead of apt-get but basically yes, that is all I did. Get the driver and then change that line in xorg.conf and restart x.
actually I did use synaptic also but it was easier to write that command than to explain ... :) no, it doesn't work with my card ... it didn't work either, earlier, with Ibex. no radeonhd for me ...

**update:**I've just added Tormod's radeon ppa to my source list and upgraded. I can see a speed increase. As far as I'm concerned that ppa stays in my source list ... :)

**update:**I've managed to use radeonhd, look at my post above. It is a good thing, sometimes, to be persistent in cleaning log files ... :) That was written in /var/log/Xorg.99.log ... never would have thought to look in a file like that, even to look for a file like that ... :)

**update:** No, it doesn't work after reboot :sad: Back to radeon ...

**first of all, I am not even sure that radeonhd would get me any benefit. if You think it will not we can drop this pursuit altogether. but, if it can, then let us go on ... :)**

maybe someone can help me with radeond. xorg.conf that I tried radeonhd with is:```
Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load  "glx"
    Load  "dri"
    Load  "extmod"
    Load  "dri2"
    Load  "dbe"
    Load  "record"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "offscreensize"          # [<str>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "ignoreconnector"        # [<str>]
        #Option     "forcereduced"           # [<bool>]
        #Option     "forcedpi"               # <i>
        #Option     "useconfiguredmonitor"     # [<bool>]
        #Option     "HPD"                    # <str>
        #Option     "NoRandr"                # [<bool>]
        #Option     "RROutputOrder"          # [<str>]
        #Option     "DRI"                    # [<bool>]
        #Option     "TVMode"                 # [<str>]
        #Option     "ScaleType"              # [<str>]
        #Option     "UseAtomBIOS"            # [<bool>]
        #Option     "AtomBIOS"               # [<str>]
        #Option     "UnverifiedFeatures"     # [<bool>]
        #Option     "Audio"                  # [<bool>]
        #Option     "HDMI"                   # [<str>]
        #Option     "COHERENT"               # [<str>]
    Identifier  "Card0"
    Driver      "radeonhd"
    VendorName  "ATI Technologies Inc"
    BoardName   "Mobility Radeon HD 3600 Series"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection
```is there anything that You see that is wrong. I did not create that file, it was created somehow in my home directory ... I tried to comment-out all but one SubSection "Display" but it did not help. it doesn't work with simple changing "radeon" into "radeonhd". if radeonhd is installed on machine than if I omit Driver "radeon" in Section "Device" than I get low graphics mode offered. it bugs me, there must be a simple thing I'm overlooking ...
this is the log file from which I learned where that xorg.conf was stored ... ```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux zika-desktop 2.6.28-10-generic #33-Ubuntu SMP Mon Mar 16 23:49:27 UTC 2009 x86_64
Build Date: 07 March 2009  02:19:24AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: [    0.000817] (--) probed, [    0.000826] (**) from config file, [    0.000833] (==) default setting,
    [    0.000839] (++) from command line, [    0.000845] (!!) notice, [    0.000851] (II) informational,
    [    0.000857] (WW) warning, [    0.000863] (EE) error, [    0.000868] (NI) not implemented, [    0.000874] (??) unknown.
[    0.000926] (==) Log file: "/var/log/Xorg.99.log", Time: Wed Mar 18 12:14:24 2009
[    0.000943] (II) Loader magic: 0xb40
[    0.000948] (II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
[    0.000965] (II) Loader running on linux
[    0.000991] (--) using VT number 8

[    0.799121] (--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3600 Series rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
List of video drivers:
    apm
    cirrus
    chips
    s3virge
    radeonhd
    sis
    i128
    ark
    sisusb
    vmware
    voodoo
    ati
    openchrome
    trident
    radeon
    siliconmotion
    s3
    savage
    neomagic
    nv
    i810
    tseng
    mga
    mach64
    rendition
    intel
    r128
    v4l
    tdfx
    fbdev
    vesa
[    0.817988] (II) LoadModule: "apm"
[    0.818158] (II) Loading /usr/lib/xorg/modules/drivers//apm_drv.so
[    0.828914] (II) Module apm: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.828951] (II) LoadModule: "cirrus"
[    0.829065] (II) Loading /usr/lib/xorg/modules/drivers//cirrus_drv.so
[    0.833213] (II) Module cirrus: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.833242] (II) LoadModule: "chips"
[    0.833368] (II) Loading /usr/lib/xorg/modules/drivers//chips_drv.so
[    0.834676] (II) Module chips: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.834706] (II) LoadModule: "s3virge"
[    0.834815] (II) Loading /usr/lib/xorg/modules/drivers//s3virge_drv.so
[    0.840863] (II) Module s3virge: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.10.2
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.840896] (II) LoadModule: "radeonhd"
[    0.841077] (II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
[    0.841314] (II) Module radeonhd: vendor="AMD GPG"
    compiled for 1.6.0, module version = 1.2.4
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.841340] (II) LoadModule: "sis"
[    0.841461] (II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
[    0.859074] (II) Module sis: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 0.10.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.870028] (II) LoadModule: "i128"
[    0.870164] (II) Loading /usr/lib/xorg/modules/drivers//i128_drv.so
[    0.878332] (II) Module i128: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.3.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.878363] (II) LoadModule: "ark"
[    0.878482] (II) Loading /usr/lib/xorg/modules/drivers//ark_drv.so
[    0.878903] (II) Module ark: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 0.7.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.878930] (II) LoadModule: "sisusb"
[    0.879044] (II) Loading /usr/lib/xorg/modules/drivers//sisusb_drv.so
[    0.879902] (II) Module sisusb: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 0.9.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.879946] (II) LoadModule: "vmware"
[    0.880070] (II) Loading /usr/lib/xorg/modules/drivers//vmware_drv.so
[    0.883791] (II) Module vmware: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 10.16.5
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.883824] (II) LoadModule: "voodoo"
[    0.883955] (II) Loading /usr/lib/xorg/modules/drivers//voodoo_drv.so
[    0.884437] (II) Module voodoo: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.1.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.884467] (II) LoadModule: "ati"
[    0.884594] (II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
[    0.891933] (II) Module ati: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 6.12.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.891959] (II) LoadModule: "openchrome"
[    0.892093] (II) Loading /usr/lib/xorg/modules/drivers//openchrome_drv.so
[    0.910183] (II) Module openchrome: vendor="http://openchrome.org/"
    compiled for 1.5.99.902, module version = 0.2.903
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.910223] (II) LoadModule: "trident"
[    0.910366] (II) Loading /usr/lib/xorg/modules/drivers//trident_drv.so
[    0.923156] (II) Module trident: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.923484] (II) LoadModule: "radeon"
[    0.923629] (II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
[    0.923793] (II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 6.12.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.923822] (II) LoadModule: "siliconmotion"
[    0.923969] (II) Loading /usr/lib/xorg/modules/drivers//siliconmotion_drv.so
[    0.925133] (II) Module siliconmotion: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.7.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.925164] (II) LoadModule: "s3"
[    0.925311] (II) Loading /usr/lib/xorg/modules/drivers//s3_drv.so
[    0.926119] (II) Module s3: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 0.6.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.926156] (II) LoadModule: "savage"
[    0.926294] (II) Loading /usr/lib/xorg/modules/drivers//savage_drv.so
[    0.927422] (II) Module savage: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.927651] (II) LoadModule: "neomagic"
[    0.927813] (II) Loading /usr/lib/xorg/modules/drivers//neomagic_drv.so
[    0.928677] (II) Module neomagic: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.2.2
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.928709] (II) LoadModule: "nv"
[    0.928848] (II) Loading /usr/lib/xorg/modules/drivers//nv_drv.so
[    0.955934] (II) Module nv: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.1.12
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.955963] (II) LoadModule: "i810"
[    0.956107] (II) Loading /usr/lib/xorg/modules/drivers//i810_drv.so
[    0.991897] (II) Module i810: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.6.3
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.991936] (II) LoadModule: "tseng"
[    0.992095] (II) Loading /usr/lib/xorg/modules/drivers//tseng_drv.so
[    0.992829] (II) Module tseng: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.1.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.992860] (II) LoadModule: "mga"
[    0.993019] (II) Loading /usr/lib/xorg/modules/drivers//mga_drv.so
[    1.006089] (II) Module mga: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.4.9
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    1.006444] (II) LoadModule: "mach64"
[    1.006593] (II) Loading /usr/lib/xorg/modules/drivers//mach64_drv.so
[    1.007760] (II) Module mach64: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 6.8.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    1.008243] (II) LoadModule: "rendition"
[    1.008391] (II) Loading /usr/lib/xorg/modules/drivers//rendition_drv.so
[    1.013363] (II) Module rendition: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 4.2.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    1.013394] (II) LoadModule: "intel"
[    1.013546] (II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
[    1.013581] (II) Module intel: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.6.3
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    1.013599] (II) UnloadModule: "intel"
[    1.013604] (II) Unloading /usr/lib/xorg/modules/drivers//intel_drv.so
[    1.013611] (II) Failed to load module "intel" (already loaded, 0)
[    1.013615] (II) LoadModule: "r128"
[    1.013759] (II) Loading /usr/lib/xorg/modules/drivers//r128_drv.so
[    1.014918] (II) Module r128: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 6.8.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    1.014950] (II) LoadModule: "v4l"
[    1.015113] (II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
[    1.015492] (II) Module v4l: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 0.1.1
    ABI class: X.Org Video Driver, version 5.0
[    1.015524] (II) LoadModule: "tdfx"
[    1.015678] (II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
[    1.016722] (II) Module tdfx: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.4.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    1.016753] (II) LoadModule: "fbdev"
[    1.016898] (II) Loading /usr/lib/xorg/modules/drivers//fbdev_drv.so
[    1.018872] (II) Module fbdev: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 0.4.0
    ABI class: X.Org Video Driver, version 5.0
[    1.018898] (II) LoadModule: "vesa"
[    1.019011] (II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
[    1.019095] (II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 2.2.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    1.019152] (II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
[    1.020372] (II) Primary Device is: PCI 01@00:00:0
[    1.020379] (WW) Falling back to old probe method for apm
[    1.020390] (WW) Falling back to old probe method for cirrus
[    1.020397] (II) Loading sub module "cirrus_laguna"
[    1.020401] (II) LoadModule: "cirrus_laguna"
[    1.020577] (II) Loading /usr/lib/xorg/modules/drivers//cirrus_laguna.so
[    1.026770] (II) Module cirrus_laguna: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
[    1.026799] (II) Loading sub module "cirrus_alpine"
[    1.026803] (II) LoadModule: "cirrus_alpine"
[    1.026936] (II) Loading /usr/lib/xorg/modules/drivers//cirrus_alpine.so
[    1.027442] (II) Module cirrus_alpine: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
[    1.027471] (WW) Falling back to old probe method for s3virge
[    1.027528] (II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
    RV505 : Radeon X1550, X1550 64bit.
    RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
    RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
    R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
    RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
    RV535 : Radeon X1300, X1650.
    RV550 : Radeon X2300 HD.
    RV560 : Radeon X1650.
    RV570 : Radeon X1950, X1950 GT; FireGL V7400.
    R580  : Radeon X1900, X1950; AMD Stream Processor.
    R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
    RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
    RV620 : Radeon HD 3450, HD 3470.
    RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
        FireGL V3600/V5600.
    RV635 : Radeon HD 3650, HD 3670.
    RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
    R680  : Radeon HD 3870 X2.
    M52   : Mobility Radeon X1300.
    M54   : Mobility Radeon X1400; M54-GL.
    M56   : Mobility Radeon X1600; Mobility FireGL V5200.
    M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
    M62   : Mobility Radeon X1350.
    M64   : Mobility Radeon X1450, X2300.
    M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
    M68   : Mobility Radeon X1900.
    M71   : Mobility Radeon HD 2300.
    M72   : Mobility Radeon HD 2400; Radeon E2400.
    M74   : Mobility Radeon HD 2400 XT.
    M76   : Mobility Radeon HD 2600;
        (Gemini ATI) Mobility Radeon HD 2600 XT.
    M82   : Mobility Radeon HD 3400.
    M86   : Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700.
    M88   : Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2.
    RS600 : Radeon Xpress 1200, Xpress 1250.
    RS690 : Radeon X1200, X1250, X1270.
    RS740 : RS740, RS740M.
    RS780 : Radeon HD 3100/3200/3300 Series.
    RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
    R700  : Radeon R700.
    M98   : Radeon M98 Mobility.
    RV730 : Radeon HD4670, HD4650.
    M96   : Radeon M96 Mobility.
    RV710 : Radeon HD4570, HD4350.

[    1.027556] (II) RADEONHD: version 1.2.4, built from non-git sources

[    1.027562] (WW) Falling back to old probe method for sis
[    1.027572] (WW) Falling back to old probe method for i128
[    1.027580] (WW) Falling back to old probe method for ark
[    1.027587] (WW) Falling back to old probe method for sisusb
[    1.027593] (WW) Falling back to old probe method for voodoo
[    1.027603] (WW) Falling back to old probe method for trident
[    1.027650] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
    ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
    ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
    ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
    ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
    ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
    ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI Mobility Radeon 4500 Series, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
    ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
    ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
    ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
    ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
    ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
    ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics
[    1.031308] (WW) Falling back to old probe method for siliconmotion
[    1.031316] (WW) Falling back to old probe method for s3
[    1.031329] (WW) Falling back to old probe method for neomagic
[    1.031339] (WW) Falling back to old probe method for tseng
[    1.031358] (WW) Falling back to old probe method for v4l
[    1.031363] (II) v4l driver for Video4Linux
[    1.031369] (II) FBDEV: driver for framebuffer: fbdev
[    1.031387] (II) VESA: driver for VESA chipsets: vesa
[    1.103807] (++) Using config file: "/xorg.conf.new"
[    1.103964] (==) ServerLayout "X.org Configured"
[    1.103972] (**) |-->Screen "Screen0" (0)
[    1.103977] (**) |   |-->Monitor "Monitor0"
[    1.104172] (**) |   |-->Device "Card0"
[    1.104179] (**) |-->Input Device "Mouse0"
[    1.104184] (**) |-->Input Device "Keyboard0"
[    1.104201] (==) Automatically adding devices
[    1.104206] (==) Automatically enabling devices
[    1.104245] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
[    1.104293] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
[    1.104333] (**) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    1.104338] (**) ModulePath set to "/usr/lib/xorg/modules"
[    1.104347] (WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
[    1.104352] (WW) Disabling Mouse0
[    1.104356] (WW) Disabling Keyboard0
[    1.119726] (II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
[    1.120308] (II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
[    1.135389] (II) Setting vga for screen 0.


Xorg detected your mouse at device /dev/input/mice.
Please check your config if the mouse is still not
operational, as by default Xorg tries to autodetect
the protocol.

Your xorg.conf file is /xorg.conf.new

To test the server, run 'X -config /xorg.conf.new'

 ddxSigGiveUp: Closing log
```this is the Xorg.0.log (with radeon) when X works:```
X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux zika-desktop 2.6.28-10-generic #33-Ubuntu SMP Mon Mar 16 23:49:27 UTC 2009 x86_64
Build Date: 07 March 2009  02:19:24AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: [    0.080398] (--) probed, [    0.080408] (**) from config file, [    0.080414] (==) default setting,
    [    0.080420] (++) from command line, [    0.080438] (!!) notice, [    0.080444] (II) informational,
    [    0.080450] (WW) warning, [    0.080456] (EE) error, [    0.080462] (NI) not implemented, [    0.080468] (??) unknown.
[    0.080521] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 18 12:30:55 2009
[    0.082080] (==) Using config file: "/etc/X11/xorg.conf"
[    0.082170] (==) No Layout section.  Using the first Screen section.
[    0.082179] (**) |-->Screen "Default Screen" (0)
[    0.096305] (**) |   |-->Monitor "Configured Monitor"
[    0.096511] (**) |   |-->Device "Configured Video Device"
[    0.096530] (==) Automatically adding devices
[    0.096537] (==) Automatically enabling devices
[    0.211345] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
[    0.373039] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    0.373058] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.373067] (II) Cannot locate a core pointer device.
[    0.373073] (II) Cannot locate a core keyboard device.
[    0.373078] (II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.373088] (II) Loader magic: 0xb40
[    0.373093] (II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
[    0.373111] (II) Loader running on linux
[    0.373119] (++) using VT number 7

[    0.402501] (--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3600 Series rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    0.402696] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.402717] (II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
[    0.403286] (II) LoadModule: "extmod"
[    0.428036] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.428239] (II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.428264] (II) Loading extension MIT-SCREEN-SAVER
[    0.428270] (II) Loading extension XFree86-VidModeExtension
[    0.428276] (II) Loading extension XFree86-DGA
[    0.428280] (II) Loading extension DPMS
[    0.428284] (II) Loading extension XVideo
[    0.428291] (II) Loading extension XVideo-MotionCompensation
[    0.428295] (II) Loading extension X-Resource
[    0.428301] (II) LoadModule: "dbe"
[    0.428512] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.428585] (II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.428608] (II) Loading extension DOUBLE-BUFFER
[    0.428614] (II) LoadModule: "glx"
[    0.428792] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.428942] (II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.428965] (==) AIGLX enabled
[    0.428975] (II) Loading extension GLX
[    0.428981] (II) LoadModule: "record"
[    0.429175] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.429252] (II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.429274] (II) Loading extension RECORD
[    0.429279] (II) LoadModule: "dri"
[    0.429459] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.429624] (II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.429646] (II) Loading extension XFree86-DRI
[    0.429673] (II) LoadModule: "dri2"
[    0.429862] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.429937] (II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.429956] (II) Loading extension DRI2
[    0.429963] (II) LoadModule: "radeon"
[    0.430083] (II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
[    0.430239] (II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 6.12.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.430272] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
    ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
    ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
    ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
    ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
    ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
    ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI Mobility Radeon 4500 Series, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
    ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
    ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
    ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
    ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
    ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
    ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics
[    0.434215] (II) Primary Device is: PCI 01@00:00:0
[    0.449755] (II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
[    0.450254] (II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
[    0.465222] (II) Setting vga for screen 0.
[    0.465247] (II) RADEON(0): Built from git commit a6855c370194b6df307ea33724fe17a85d67607e
[    0.465260] (II) RADEON(0): TOTO SAYS 00000000feaf0000
[    0.465282] (II) RADEON(0): MMIO registers at 0x00000000feaf0000: size 64KB
[    0.465326] (II) RADEON(0): PCI bus 1 card 0 func 0
[    0.479857] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    0.479871] (==) RADEON(0): Depth 24, [    0.479876] (--) framebuffer bpp 32
[    0.479883] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    0.479890] (==) RADEON(0): Default visual is TrueColor
[    0.479922] (II) Loading sub module "vgahw"
[    0.479928] (II) LoadModule: "vgahw"
[    0.480003] (II) Loading /usr/lib/xorg/modules//libvgahw.so
[    0.480117] (II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
[    0.480157] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    0.480165] (==) RADEON(0): RGB weight 888
[    0.480170] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    0.480182] (--) RADEON(0): Chipset: "ATI Radeon HD 3600 XT" (ChipID = 0x9598)
[    0.480192] (WW) RADEON(0): R600 support is mostly incomplete and very experimental
[    0.480197] (--) RADEON(0): Linear framebuffer at 0x00000000d0000000
[    0.480243] (II) RADEON(0): PCIE card detected
[    0.480306] (II) Loading sub module "int10"
[    0.480313] (II) LoadModule: "int10"
[    0.480358] (II) Loading /usr/lib/xorg/modules//libint10.so
[    0.480474] (II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
[    0.480494] (II) RADEON(0): initializing int10
[    0.486489] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    0.487308] (II) RADEON(0): ATOM BIOS detected
[    0.487322] (II) RADEON(0): ATOM BIOS Rom: 
    SubsystemVendorID: 0x1043 SubsystemID: 0x01da
    IOBaseAddress: 0xd000
    Filename: SV28760.bin 
    BIOS Bootup Message:  
9598.10.88.0.3.AS01                                  
                        
[    0.487347] (II) RADEON(0): Framebuffer space used by Firmware (kb): 20
[    0.487352] (II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffb000
[    0.487357] (II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
[    0.487363] (II) RADEON(0): AtomBIOS VRAM scratch base: 0x1fffb000
[    0.487368] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    0.487393] (II) RADEON(0): Default Engine Clock: 725000
[    0.487399] (II) RADEON(0): Default Memory Clock: 500000
[    0.487404] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    0.487408] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    0.487413] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
[    0.487417] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
[    0.487422] (II) RADEON(0): Maximum Pixel Clock: 400000
[    0.487427] (II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
[    0.636942] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    0.636961] (II) RADEON(0): using shadow framebuffer
[    0.636966] (II) Loading sub module "shadow"
[    0.636970] (II) LoadModule: "shadow"
[    0.637059] (II) Loading /usr/lib/xorg/modules//libshadow.so
[    0.637174] (II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.4
[    0.637200] (II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
[    0.637209] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
[    0.637216] (II) RADEON(0): Color tiling disabled
[    0.637221] (II) RADEON(0): Max desktop size set to 2560x1600
[    0.637226] (II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
[    0.637231] (II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
[    0.637240] (II) Loading sub module "ddc"
[    0.637244] (II) LoadModule: "ddc"
[    0.637254] (II) Module "ddc" already built-in
[    0.637259] (II) Loading sub module "i2c"
[    0.637263] (II) LoadModule: "i2c"
[    0.637272] (II) Module "i2c" already built-in
[    0.637301] (II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 725.000000, mclk: 500.000000
[    0.637352] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
[    0.637379] (II) RADEON(0): Output DVI-1 using monitor section Configured Monitor
[    0.652146] (II) RADEON(0): I2C bus "DVI-1" initialized.
[    0.652186] (II) RADEON(0): Output DVI-0 has no monitor section
[    0.652194] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    0.652203] (II) RADEON(0): Port0:
  XRANDR name: DVI-1
  Connector: DVI-D
  DFP1: INTERNAL_UNIPHY
  DDC reg: 0x7e50
[    0.652232] (II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT1: INTERNAL_KLDSCP_DAC1
  DFP2: INTERNAL_KLDSCP_LVTMA
  DDC reg: 0x7e40
[    0.652274] (II) RADEON(0): I2C device "DVI-1:E-EDID segment register" registered at address 0x60.
[    0.652280] (II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
[    0.655057] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
finished output detect: 0
[    0.655082] (II) RADEON(0): I2C device "DVI-0:E-EDID segment register" registered at address 0x60.
[    0.655088] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    0.709197] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    0.709204] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    0.709210] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    0.709216] (II) RADEON(0): Year: 2008  Week: 21
[    0.709220] (II) RADEON(0): EDID Version: 1.3
[    0.709225] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.709235] (II) RADEON(0): Sync:  Separate
[    0.709245] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.709255] (II) RADEON(0): Gamma: 2.20
[    0.709266] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    0.709297] (II) RADEON(0): First detailed timing is preferred mode
[    0.709302] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    0.709313] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    0.709324] (II) RADEON(0): Supported VESA Video Modes:
[    0.709328] (II) RADEON(0): 720x400@70Hz
[    0.709332] (II) RADEON(0): 640x480@60Hz
[    0.709337] (II) RADEON(0): 640x480@67Hz
[    0.709341] (II) RADEON(0): 640x480@72Hz
[    0.709345] (II) RADEON(0): 640x480@75Hz
[    0.709349] (II) RADEON(0): 800x600@56Hz
[    0.709353] (II) RADEON(0): 800x600@60Hz
[    0.709357] (II) RADEON(0): 800x600@72Hz
[    0.709361] (II) RADEON(0): 800x600@75Hz
[    0.709365] (II) RADEON(0): 832x624@75Hz
[    0.709369] (II) RADEON(0): 1024x768@60Hz
[    0.709374] (II) RADEON(0): 1024x768@70Hz
[    0.709378] (II) RADEON(0): 1024x768@75Hz
[    0.709382] (II) RADEON(0): 1280x1024@75Hz
[    0.709386] (II) RADEON(0): 1152x870@75Hz
[    0.709390] (II) RADEON(0): Manufacturer's mask: 10
[    0.709395] (II) RADEON(0): Supported Future Video Modes:
[    0.709399] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    0.709404] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.709409] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.709414] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.709419] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    0.709424] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    0.709429] (II) RADEON(0): Supported additional Video Mode:
[    0.709433] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.709443] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.709451] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.709460] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    0.709468] (II) RADEON(0): Serial No: LAV0C1284022
[    0.709472] (II) RADEON(0): Monitor name: X223W  Q
[    0.709477] (II) RADEON(0): EDID (in hex):
[    0.709485] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    0.709492] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    0.709499] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    0.709505] (II) RADEON(0):     950f9040010121399030621a274068b0
[    0.709512] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    0.709519] (II) RADEON(0):     5411000a202020202020000000ff004c
[    0.709525] (II) RADEON(0):     41563043313238343032320a000000fc
[    0.709532] (II) RADEON(0):     0058323233572020510a20202020000a
finished output detect: 1
finished all detect
before xf86InitialConfiguration
[    0.712385] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
[    0.712401] (II) RADEON(0): EDID for output DVI-1
[    0.766421] (II) RADEON(0): EDID for output DVI-0
[    0.766426] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    0.766434] (II) RADEON(0): Year: 2008  Week: 21
[    0.766439] (II) RADEON(0): EDID Version: 1.3
[    0.766443] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.766453] (II) RADEON(0): Sync:  Separate
[    0.766461] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.766477] (II) RADEON(0): Gamma: 2.20
[    0.766485] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    0.766499] (II) RADEON(0): First detailed timing is preferred mode
[    0.766503] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    0.766513] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    0.766523] (II) RADEON(0): Supported VESA Video Modes:
[    0.766527] (II) RADEON(0): 720x400@70Hz
[    0.766531] (II) RADEON(0): 640x480@60Hz
[    0.766535] (II) RADEON(0): 640x480@67Hz
[    0.766539] (II) RADEON(0): 640x480@72Hz
[    0.766543] (II) RADEON(0): 640x480@75Hz
[    0.766555] (II) RADEON(0): 800x600@56Hz
[    0.766560] (II) RADEON(0): 800x600@60Hz
[    0.766564] (II) RADEON(0): 800x600@72Hz
[    0.766568] (II) RADEON(0): 800x600@75Hz
[    0.766572] (II) RADEON(0): 832x624@75Hz
[    0.766576] (II) RADEON(0): 1024x768@60Hz
[    0.766580] (II) RADEON(0): 1024x768@70Hz
[    0.766584] (II) RADEON(0): 1024x768@75Hz
[    0.766588] (II) RADEON(0): 1280x1024@75Hz
[    0.766592] (II) RADEON(0): 1152x870@75Hz
[    0.766596] (II) RADEON(0): Manufacturer's mask: 10
[    0.766600] (II) RADEON(0): Supported Future Video Modes:
[    0.766605] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    0.766610] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.766615] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.766620] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.766625] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    0.766630] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    0.766635] (II) RADEON(0): Supported additional Video Mode:
[    0.766639] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.766648] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.766656] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.766664] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    0.766672] (II) RADEON(0): Serial No: LAV0C1284022
[    0.766676] (II) RADEON(0): Monitor name: X223W  Q
[    0.766681] (II) RADEON(0): EDID (in hex):
[    0.766688] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    0.766701] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    0.766713] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    0.766726] (II) RADEON(0):     950f9040010121399030621a274068b0
[    0.766739] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    0.766752] (II) RADEON(0):     5411000a202020202020000000ff004c
[    0.766765] (II) RADEON(0):     41563043313238343032320a000000fc
[    0.766778] (II) RADEON(0):     0058323233572020510a20202020000a
[    0.766789] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    0.766794] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    0.766798] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    0.766803] (II) RADEON(0): Year: 2008  Week: 21
[    0.766808] (II) RADEON(0): EDID Version: 1.3
[    0.766812] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.766821] (II) RADEON(0): Sync:  Separate
[    0.766830] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.766839] (II) RADEON(0): Gamma: 2.20
[    0.766844] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    0.766858] (II) RADEON(0): First detailed timing is preferred mode
[    0.766862] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    0.766874] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    0.766883] (II) RADEON(0): Supported VESA Video Modes:
[    0.766887] (II) RADEON(0): 720x400@70Hz
[    0.766891] (II) RADEON(0): 640x480@60Hz
[    0.766895] (II) RADEON(0): 640x480@67Hz
[    0.766899] (II) RADEON(0): 640x480@72Hz
[    0.766903] (II) RADEON(0): 640x480@75Hz
[    0.766907] (II) RADEON(0): 800x600@56Hz
[    0.766911] (II) RADEON(0): 800x600@60Hz
[    0.766916] (II) RADEON(0): 800x600@72Hz
[    0.766920] (II) RADEON(0): 800x600@75Hz
[    0.766924] (II) RADEON(0): 832x624@75Hz
[    0.766928] (II) RADEON(0): 1024x768@60Hz
[    0.766932] (II) RADEON(0): 1024x768@70Hz
[    0.766936] (II) RADEON(0): 1024x768@75Hz
[    0.766940] (II) RADEON(0): 1280x1024@75Hz
[    0.766944] (II) RADEON(0): 1152x870@75Hz
[    0.766948] (II) RADEON(0): Manufacturer's mask: 10
[    0.766952] (II) RADEON(0): Supported Future Video Modes:
[    0.766956] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    0.766961] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.766975] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.766980] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.766985] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    0.766990] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    0.766995] (II) RADEON(0): Supported additional Video Mode:
[    0.766999] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.767010] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.767018] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.767025] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    0.767033] (II) RADEON(0): Serial No: LAV0C1284022
[    0.767038] (II) RADEON(0): Monitor name: X223W  Q
[    0.767042] (II) RADEON(0): EDID (in hex):
[    0.767049] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    0.767057] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    0.767069] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    0.767082] (II) RADEON(0):     950f9040010121399030621a274068b0
[    0.767095] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    0.767108] (II) RADEON(0):     5411000a202020202020000000ff004c
[    0.767121] (II) RADEON(0):     41563043313238343032320a000000fc
[    0.767133] (II) RADEON(0):     0058323233572020510a20202020000a
[    0.767147] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    0.767191] (II) RADEON(0): Printing probed modes for output DVI-0
[    0.767199] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    0.767209] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    0.767223] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    0.767232] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    0.767244] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    0.767256] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    0.767265] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    0.767281] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    0.767298] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    0.767309] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    0.767321] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.767337] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    0.767349] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    0.767366] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    0.767382] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.767398] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    0.767415] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    0.767432] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    0.767448] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    0.767465] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.767490] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    0.767508] (II) RADEON(0): Output DVI-1 disconnected
[    0.767513] (II) RADEON(0): Output DVI-0 connected
[    0.767521] (II) RADEON(0): Using exact sizes for initial modes
[    0.767526] (II) RADEON(0): Output DVI-0 using initial mode 1680x1050
after xf86InitialConfiguration
[    0.767552] (==) RADEON(0): DPI set to (96, 96)
[    0.767557] (II) Loading sub module "fb"
[    0.767561] (II) LoadModule: "fb"
[    0.767640] (II) Loading /usr/lib/xorg/modules//libfb.so
[    0.767798] (II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
[    0.767822] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
[    0.767829] (II) Loading sub module "ramdac"
[    0.767833] (II) LoadModule: "ramdac"
[    0.767844] (II) Module "ramdac" already built-in
[    0.767852] (==) RADEON(0): Will attempt to use R6xx/R7xx EXA support if DRI is enabled.
[    0.767858] (II) Loading sub module "exa"
[    0.767863] (II) LoadModule: "exa"
[    0.767909] (II) Loading /usr/lib/xorg/modules//libexa.so
[    0.767998] (II) Module exa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.4.0
    ABI class: X.Org Video Driver, version 5.0
[    0.768107] (!!) RADEON(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
[    0.768115] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    0.768124] (--) Depth 24 pixmap format is 32 bpp
[    0.768128] (II) do I need RAC?  No, I don't.
[    0.768135] (II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
[    0.768790] (II) RADEON(0): RADEONScreenInit d0000000 0 0
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
mc fb loc is 00ef00d0
[    0.890455] (II) RADEON(0): RADEONInitMemoryMap() : 
[    0.890461] (II) RADEON(0):   mem_size         : 0x20000000
[    0.890466] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0
[    0.890471] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    0.890476] (II) RADEON(0): Depth moves disabled by default
[    0.890493] (II) RADEON(0): Allocating from a screen of 262144 kb
[    0.890499] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00af0000
[    0.890504] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00af4000
[    0.890509] (II) RADEON(0): Will use 11200 kb for front buffer at offset 0x00000000
[    0.890515] (II) RADEON(0): Will use 250912 kb for X Server offscreen at offset 0x00af8000
[    0.926883] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.926898] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ff00e0
[    0.926904] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    0.936989] (==) RADEON(0): Backing store disabled
[    0.936996] (WW) RADEON(0): Direct rendering disabled
[    0.937004] (EE) RADEON(0): Acceleration initialization failed
[    0.937012] (II) RADEON(0): Acceleration disabled
[    0.937020] (II) RADEON(0): DPMS enabled
[    0.937028] (==) RADEON(0): Silken mouse enabled
[    0.937509] (II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
Output DIG dpms success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1680x1050 - 2240 1089 10
[    0.937745] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.937750] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ef00d0
[    0.937754] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 146250000
best_freq: 146250000
best_feedback_div: 65
best_ref_div: 2
best_post_div: 6
[    0.949456] (II) RADEON(0): crtc(0) Clock: mode 146250, PLL 146250
[    0.949461] (II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x41(65), pdiv 6
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output DIG dpms success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
[    0.952601] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Lock CRTC 0 success
Unlock CRTC 0 success
[    0.952869] (--) RandR disabled
[    0.967598] (II) Initializing built-in extension Generic Event Extension
[    0.967610] (II) Initializing built-in extension SHAPE
[    0.967615] (II) Initializing built-in extension MIT-SHM
[    0.967620] (II) Initializing built-in extension XInputExtension
[    0.967624] (II) Initializing built-in extension XTEST
[    0.967629] (II) Initializing built-in extension BIG-REQUESTS
[    0.967633] (II) Initializing built-in extension SYNC
[    0.967637] (II) Initializing built-in extension XKEYBOARD
[    0.967641] (II) Initializing built-in extension XC-MISC
[    0.967645] (II) Initializing built-in extension SECURITY
[    0.967648] (II) Initializing built-in extension XINERAMA
[    0.967652] (II) Initializing built-in extension XFIXES
[    0.967656] (II) Initializing built-in extension RENDER
[    0.967660] (II) Initializing built-in extension RANDR
[    0.967664] (II) Initializing built-in extension COMPOSITE
[    0.967668] (II) Initializing built-in extension DAMAGE
[    0.975134] (II) AIGLX: Screen 0 is not DRI2 capable
[    0.975154] (II) AIGLX: Screen 0 is not DRI capable
[    1.054181] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    1.054198] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    1.054546] (II) RADEON(0): Setting screen physical size to 474 x 296
[    1.446156] (II) config/hal: Adding input device AT Translated Set 2 keyboard
[    1.446216] (II) LoadModule: "evdev"
[    1.446328] (II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
[    1.466215] (II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
[    1.466275] (**) AT Translated Set 2 keyboard: always reports core events
[    1.466285] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    1.477676] (II) AT Translated Set 2 keyboard: Found keys
[    1.477683] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    1.477703] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    1.477726] (**) Option "xkb_rules" "evdev"
[    1.477737] (**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
[    1.477748] (**) Option "xkb_model" "pc105"
[    1.477757] (**) AT Translated Set 2 keyboard: xkb_model: "pc105"
[    1.477765] (**) Option "xkb_layout" "rs"
[    1.477774] (**) AT Translated Set 2 keyboard: xkb_layout: "rs"
[    1.477782] (**) Option "xkb_variant" "latin"
[    1.477791] (**) AT Translated Set 2 keyboard: xkb_variant: "latin"
[    1.477798] (**) Option "xkb_options" "grp:alts_toggle,grp:sclk_toggle,grp_led:scroll"
[    1.477807] (**) AT Translated Set 2 keyboard: xkb_options: "grp:alts_toggle,grp:sclk_toggle,grp_led:scroll"
[    1.542339] (II) config/hal: Adding input device Macintosh mouse button emulation
[    1.542381] (**) Macintosh mouse button emulation: always reports core events
[    1.542388] (**) Macintosh mouse button emulation: Device: "/dev/input/event2"
[    1.557671] (II) Macintosh mouse button emulation: Found 3 mouse buttons
[    1.557678] (II) Macintosh mouse button emulation: Found x and y relative axes
[    1.557683] (II) Macintosh mouse button emulation: Configuring as mouse
[    1.557695] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    1.557701] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    1.557715] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    1.557746] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    1.557752] (**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
[    1.557762] (**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
[    1.557773] (**) Macintosh mouse button emulation: (accel) set acceleration profile 0
[    1.559200] (II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
[    1.559300] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    1.559308] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
[    1.569670] (II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    1.569676] (II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    1.569681] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    1.569690] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    1.569704] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    1.569716] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    1.569739] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    1.569745] (**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
[    1.569752] (**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
[    1.569762] (**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0
[    7.618232] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
[    7.618288] (II) RADEON(0): EDID for output DVI-1
[    7.673338] (II) RADEON(0): EDID for output DVI-0
[    7.673347] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    7.673353] (II) RADEON(0): Year: 2008  Week: 21
[    7.673359] (II) RADEON(0): EDID Version: 1.3
[    7.673364] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    7.673375] (II) RADEON(0): Sync:  Separate
[    7.673404] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    7.673415] (II) RADEON(0): Gamma: 2.20
[    7.673426] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    7.673445] (II) RADEON(0): First detailed timing is preferred mode
[    7.673450] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    7.673461] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    7.673472] (II) RADEON(0): Supported VESA Video Modes:
[    7.673476] (II) RADEON(0): 720x400@70Hz
[    7.673481] (II) RADEON(0): 640x480@60Hz
[    7.673485] (II) RADEON(0): 640x480@67Hz
[    7.673489] (II) RADEON(0): 640x480@72Hz
[    7.673493] (II) RADEON(0): 640x480@75Hz
[    7.673497] (II) RADEON(0): 800x600@56Hz
[    7.673502] (II) RADEON(0): 800x600@60Hz
[    7.673506] (II) RADEON(0): 800x600@72Hz
[    7.673510] (II) RADEON(0): 800x600@75Hz
[    7.673514] (II) RADEON(0): 832x624@75Hz
[    7.673518] (II) RADEON(0): 1024x768@60Hz
[    7.673522] (II) RADEON(0): 1024x768@70Hz
[    7.673527] (II) RADEON(0): 1024x768@75Hz
[    7.673531] (II) RADEON(0): 1280x1024@75Hz
[    7.673536] (II) RADEON(0): 1152x870@75Hz
[    7.673539] (II) RADEON(0): Manufacturer's mask: 10
[    7.673544] (II) RADEON(0): Supported Future Video Modes:
[    7.673549] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    7.673555] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    7.673560] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    7.673565] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    7.673570] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    7.673576] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    7.673581] (II) RADEON(0): Supported additional Video Mode:
[    7.673586] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    7.673596] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    7.673605] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    7.673613] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    7.673622] (II) RADEON(0): Serial No: LAV0C1284022
[    7.673627] (II) RADEON(0): Monitor name: X223W  Q
[    7.673631] (II) RADEON(0): EDID (in hex):
[    7.673639] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    7.673646] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    7.673659] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    7.673666] (II) RADEON(0):     950f9040010121399030621a274068b0
[    7.673679] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    7.673686] (II) RADEON(0):     5411000a202020202020000000ff004c
[    7.673699] (II) RADEON(0):     41563043313238343032320a000000fc
[    7.673712] (II) RADEON(0):     0058323233572020510a20202020000a
[    7.673725] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    7.673757] (II) RADEON(0): Using EDID range info for horizontal sync
[    7.673761] (II) RADEON(0): Using EDID range info for vertical refresh
[    7.673766] (II) RADEON(0): Printing DDC gathered Modelines:
[    7.673772] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    7.673783] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    7.673793] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    7.673802] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    7.673810] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    7.673818] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    7.673835] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    7.673851] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    7.673868] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    7.673877] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    7.673889] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    7.673900] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    7.673916] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    7.673932] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    7.673940] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    7.673956] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    7.673972] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    7.673980] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    7.673996] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    7.674013] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    7.674029] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    7.674045] (II) RADEON(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    7.674069] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    7.674074] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    7.674079] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    7.674084] (II) RADEON(0): Year: 2008  Week: 21
[    7.674089] (II) RADEON(0): EDID Version: 1.3
[    7.674094] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    7.674104] (II) RADEON(0): Sync:  Separate
[    7.674113] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    7.674125] (II) RADEON(0): Gamma: 2.20
[    7.674130] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    7.674144] (II) RADEON(0): First detailed timing is preferred mode
[    7.674148] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    7.674161] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    7.674170] (II) RADEON(0): Supported VESA Video Modes:
[    7.674174] (II) RADEON(0): 720x400@70Hz
[    7.674178] (II) RADEON(0): 640x480@60Hz
[    7.674182] (II) RADEON(0): 640x480@67Hz
[    7.674187] (II) RADEON(0): 640x480@72Hz
[    7.674191] (II) RADEON(0): 640x480@75Hz
[    7.674195] (II) RADEON(0): 800x600@56Hz
[    7.674199] (II) RADEON(0): 800x600@60Hz
[    7.674203] (II) RADEON(0): 800x600@72Hz
[    7.674207] (II) RADEON(0): 800x600@75Hz
[    7.674211] (II) RADEON(0): 832x624@75Hz
[    7.674215] (II) RADEON(0): 1024x768@60Hz
[    7.674219] (II) RADEON(0): 1024x768@70Hz
[    7.674223] (II) RADEON(0): 1024x768@75Hz
[    7.674227] (II) RADEON(0): 1280x1024@75Hz
[    7.674231] (II) RADEON(0): 1152x870@75Hz
[    7.674235] (II) RADEON(0): Manufacturer's mask: 10
[    7.674240] (II) RADEON(0): Supported Future Video Modes:
[    7.674244] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    7.674249] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    7.674254] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    7.674259] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    7.674264] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    7.674269] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    7.674282] (II) RADEON(0): Supported additional Video Mode:
[    7.674286] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    7.674295] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    7.674303] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    7.674312] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    7.674320] (II) RADEON(0): Serial No: LAV0C1284022
[    7.674325] (II) RADEON(0): Monitor name: X223W  Q
[    7.674329] (II) RADEON(0): EDID (in hex):
[    7.674336] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    7.674349] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    7.674355] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    7.674368] (II) RADEON(0):     950f9040010121399030621a274068b0
[    7.674374] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    7.674387] (II) RADEON(0):     5411000a202020202020000000ff004c
[    7.674395] (II) RADEON(0):     41563043313238343032320a000000fc
[    7.674408] (II) RADEON(0):     0058323233572020510a20202020000a
[    7.674415] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    7.674450] (II) RADEON(0): Printing probed modes for output DVI-0
[    7.674455] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    7.674468] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    7.674477] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    7.674493] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    7.674502] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    7.674518] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    7.674530] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    7.674546] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    7.674562] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    7.674578] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    7.674591] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    7.674605] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    7.674622] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    7.674638] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    7.674646] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    7.674662] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    7.674670] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    7.674687] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    7.674703] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    7.674717] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    7.674726] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    7.678511] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
[    7.678531] (II) RADEON(0): EDID for output DVI-1
[    7.733308] (II) RADEON(0): EDID for output DVI-0
[    7.733317] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    7.733324] (II) RADEON(0): Year: 2008  Week: 21
[    7.733329] (II) RADEON(0): EDID Version: 1.3
[    7.733334] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    7.733344] (II) RADEON(0): Sync:  Separate
[    7.733354] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    7.733364] (II) RADEON(0): Gamma: 2.20
[    7.733373] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    7.733390] (II) RADEON(0): First detailed timing is preferred mode
[    7.733395] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    7.733405] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    7.733415] (II) RADEON(0): Supported VESA Video Modes:
[    7.733420] (II) RADEON(0): 720x400@70Hz
[    7.733424] (II) RADEON(0): 640x480@60Hz
[    7.733428] (II) RADEON(0): 640x480@67Hz
[    7.733432] (II) RADEON(0): 640x480@72Hz
[    7.733437] (II) RADEON(0): 640x480@75Hz
[    7.733441] (II) RADEON(0): 800x600@56Hz
[    7.733445] (II) RADEON(0): 800x600@60Hz
[    7.733449] (II) RADEON(0): 800x600@72Hz
[    7.733453] (II) RADEON(0): 800x600@75Hz
[    7.733457] (II) RADEON(0): 832x624@75Hz
[    7.733461] (II) RADEON(0): 1024x768@60Hz
[    7.733465] (II) RADEON(0): 1024x768@70Hz
[    7.733470] (II) RADEON(0): 1024x768@75Hz
[    7.733474] (II) RADEON(0): 1280x1024@75Hz
[    7.733478] (II) RADEON(0): 1152x870@75Hz
[    7.733482] (II) RADEON(0): Manufacturer's mask: 10
[    7.733486] (II) RADEON(0): Supported Future Video Modes:
[    7.733491] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    7.733496] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    7.733502] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    7.733507] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    7.733512] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    7.733517] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    7.733522] (II) RADEON(0): Supported additional Video Mode:
[    7.733526] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    7.733536] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    7.733544] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    7.733552] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    7.733560] (II) RADEON(0): Serial No: LAV0C1284022
[    7.733565] (II) RADEON(0): Monitor name: X223W  Q
[    7.733570] (II) RADEON(0): EDID (in hex):
[    7.733577] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    7.733584] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    7.733597] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    7.733609] (II) RADEON(0):     950f9040010121399030621a274068b0
[    7.733616] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    7.733629] (II) RADEON(0):     5411000a202020202020000000ff004c
[    7.733635] (II) RADEON(0):     41563043313238343032320a000000fc
[    7.733651] (II) RADEON(0):     0058323233572020510a20202020000a
[    7.733657] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    7.733683] (II) RADEON(0): Using hsync ranges from config file
[    7.733688] (II) RADEON(0): Using vrefresh ranges from config file
[    7.733693] (II) RADEON(0): Printing DDC gathered Modelines:
[    7.733698] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    7.733709] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    7.733717] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    7.733734] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    7.733743] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    7.733763] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    7.733776] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    7.733784] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    7.733800] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    7.733811] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    7.733823] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    7.733831] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    7.733847] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    7.733863] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    7.733879] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    7.733889] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    7.733905] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    7.733921] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    7.733936] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    7.733947] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    7.733963] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    7.733978] (II) RADEON(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    7.733993] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    7.733998] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    7.734003] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    7.734008] (II) RADEON(0): Year: 2008  Week: 21
[    7.734012] (II) RADEON(0): EDID Version: 1.3
[    7.734017] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    7.734027] (II) RADEON(0): Sync:  Separate
[    7.734036] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    7.734053] (II) RADEON(0): Gamma: 2.20
[    7.734057] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    7.734072] (II) RADEON(0): First detailed timing is preferred mode
[    7.734076] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    7.734088] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    7.734097] (II) RADEON(0): Supported VESA Video Modes:
[    7.734101] (II) RADEON(0): 720x400@70Hz
[    7.734105] (II) RADEON(0): 640x480@60Hz
[    7.734109] (II) RADEON(0): 640x480@67Hz
[    7.734113] (II) RADEON(0): 640x480@72Hz
[    7.734118] (II) RADEON(0): 640x480@75Hz
[    7.734122] (II) RADEON(0): 800x600@56Hz
[    7.734126] (II) RADEON(0): 800x600@60Hz
[    7.734130] (II) RADEON(0): 800x600@72Hz
[    7.734134] (II) RADEON(0): 800x600@75Hz
[    7.734138] (II) RADEON(0): 832x624@75Hz
[    7.734142] (II) RADEON(0): 1024x768@60Hz
[    7.734146] (II) RADEON(0): 1024x768@70Hz
[    7.734151] (II) RADEON(0): 1024x768@75Hz
[    7.734154] (II) RADEON(0): 1280x1024@75Hz
[    7.734159] (II) RADEON(0): 1152x870@75Hz
[    7.734163] (II) RADEON(0): Manufacturer's mask: 10
[    7.734167] (II) RADEON(0): Supported Future Video Modes:
[    7.734171] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    7.734186] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    7.734192] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    7.734196] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    7.734201] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    7.734206] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    7.734211] (II) RADEON(0): Supported additional Video Mode:
[    7.734215] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    7.734227] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    7.734235] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    7.734243] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    7.734251] (II) RADEON(0): Serial No: LAV0C1284022
[    7.734255] (II) RADEON(0): Monitor name: X223W  Q
[    7.734259] (II) RADEON(0): EDID (in hex):
[    7.734266] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    7.734279] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    7.734286] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    7.734299] (II) RADEON(0):     950f9040010121399030621a274068b0
[    7.734308] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    7.734321] (II) RADEON(0):     5411000a202020202020000000ff004c
[    7.734334] (II) RADEON(0):     41563043313238343032320a000000fc
[    7.734347] (II) RADEON(0):     0058323233572020510a20202020000a
[    7.734358] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    7.734390] (II) RADEON(0): Printing probed modes for output DVI-0
[    7.734395] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    7.734404] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    7.734421] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    7.734436] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    7.734447] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    7.734459] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    7.734467] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    7.734483] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    7.734493] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    7.734510] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    7.734521] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    7.734538] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    7.734554] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    7.734564] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    7.734573] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    7.734589] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    7.734601] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    7.734617] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    7.734633] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    7.734650] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    7.734670] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    7.737948] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
[    7.737967] (II) RADEON(0): EDID for output DVI-1
[    7.792396] (II) RADEON(0): EDID for output DVI-0
[    7.792402] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    7.792407] (II) RADEON(0): Year: 2008  Week: 21
[    7.792412] (II) RADEON(0): EDID Version: 1.3
[    7.792416] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    7.792426] (II) RADEON(0): Sync:  Separate
[    7.792436] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    7.792446] (II) RADEON(0): Gamma: 2.20
[    7.792452] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    7.792470] (II) RADEON(0): First detailed timing is preferred mode
[    7.792475] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    7.792484] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    7.792496] (II) RADEON(0): Supported VESA Video Modes:
[    7.792501] (II) RADEON(0): 720x400@70Hz
[    7.792505] (II) RADEON(0): 640x480@60Hz
[    7.792509] (II) RADEON(0): 640x480@67Hz
[    7.792513] (II) RADEON(0): 640x480@72Hz
[    7.792518] (II) RADEON(0): 640x480@75Hz
[    7.792522] (II) RADEON(0): 800x600@56Hz
[    7.792526] (II) RADEON(0): 800x600@60Hz
[    7.792530] (II) RADEON(0): 800x600@72Hz
[    7.792534] (II) RADEON(0): 800x600@75Hz
[    7.792538] (II) RADEON(0): 832x624@75Hz
[    7.792542] (II) RADEON(0): 1024x768@60Hz
[    7.792546] (II) RADEON(0): 1024x768@70Hz
[    7.792550] (II) RADEON(0): 1024x768@75Hz
[    7.792554] (II) RADEON(0): 1280x1024@75Hz
[    7.792559] (II) RADEON(0): 1152x870@75Hz
[    7.792563] (II) RADEON(0): Manufacturer's mask: 10
[    7.792567] (II) RADEON(0): Supported Future Video Modes:
[    7.792572] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    7.792577] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    7.792582] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    7.792587] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    7.792592] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    7.792596] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    7.792601] (II) RADEON(0): Supported additional Video Mode:
[    7.792606] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    7.792615] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    7.792623] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    7.792631] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    7.792639] (II) RADEON(0): Serial No: LAV0C1284022
[    7.792644] (II) RADEON(0): Monitor name: X223W  Q
[    7.792648] (II) RADEON(0): EDID (in hex):
[    7.792655] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    7.792666] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    7.792680] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    7.792686] (II) RADEON(0):     950f9040010121399030621a274068b0
[    7.792699] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    7.792707] (II) RADEON(0):     5411000a202020202020000000ff004c
[    7.792720] (II) RADEON(0):     41563043313238343032320a000000fc
[    7.792733] (II) RADEON(0):     0058323233572020510a20202020000a
[    7.792738] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    7.792762] (II) RADEON(0): Using hsync ranges from config file
[    7.792766] (II) RADEON(0): Using vrefresh ranges from config file
[    7.792771] (II) RADEON(0): Printing DDC gathered Modelines:
[    7.792776] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    7.792785] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    7.792808] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    7.792825] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    7.792832] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    7.792848] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    7.792862] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    7.792879] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    7.792895] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    7.792911] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    7.792923] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    7.792939] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    7.792955] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    7.792965] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    7.792977] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    7.792988] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    7.793000] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    7.793016] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    7.793024] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    7.793035] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    7.793045] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    7.793061] (II) RADEON(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    7.793080] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    7.793085] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    7.793089] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    7.793094] (II) RADEON(0): Year: 2008  Week: 21
[    7.793098] (II) RADEON(0): EDID Version: 1.3
[    7.793104] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    7.793113] (II) RADEON(0): Sync:  Separate
[    7.793122] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    7.793133] (II) RADEON(0): Gamma: 2.20
[    7.793138] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    7.793152] (II) RADEON(0): First detailed timing is preferred mode
[    7.793156] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    7.793166] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    7.793175] (II) RADEON(0): Supported VESA Video Modes:
[    7.793179] (II) RADEON(0): 720x400@70Hz
[    7.793183] (II) RADEON(0): 640x480@60Hz
[    7.793187] (II) RADEON(0): 640x480@67Hz
[    7.793191] (II) RADEON(0): 640x480@72Hz
[    7.793195] (II) RADEON(0): 640x480@75Hz
[    7.793199] (II) RADEON(0): 800x600@56Hz
[    7.793203] (II) RADEON(0): 800x600@60Hz
[    7.793207] (II) RADEON(0): 800x600@72Hz
[    7.793211] (II) RADEON(0): 800x600@75Hz
[    7.793215] (II) RADEON(0): 832x624@75Hz
[    7.793219] (II) RADEON(0): 1024x768@60Hz
[    7.793223] (II) RADEON(0): 1024x768@70Hz
[    7.793238] (II) RADEON(0): 1024x768@75Hz
[    7.793242] (II) RADEON(0): 1280x1024@75Hz
[    7.793246] (II) RADEON(0): 1152x870@75Hz
[    7.793250] (II) RADEON(0): Manufacturer's mask: 10
[    7.793255] (II) RADEON(0): Supported Future Video Modes:
[    7.793259] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    7.793264] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    7.793269] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    7.793274] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    7.793279] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    7.793284] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    7.793289] (II) RADEON(0): Supported additional Video Mode:
[    7.793293] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    7.793305] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    7.793312] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    7.793320] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    7.793328] (II) RADEON(0): Serial No: LAV0C1284022
[    7.793332] (II) RADEON(0): Monitor name: X223W  Q
[    7.793337] (II) RADEON(0): EDID (in hex):
[    7.793343] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    7.793356] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    7.793369] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    7.793376] (II) RADEON(0):     950f9040010121399030621a274068b0
[    7.793388] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    7.793395] (II) RADEON(0):     5411000a202020202020000000ff004c
[    7.793408] (II) RADEON(0):     41563043313238343032320a000000fc
[    7.793416] (II) RADEON(0):     0058323233572020510a20202020000a
[    7.793426] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    7.793459] (II) RADEON(0): Printing probed modes for output DVI-0
[    7.793466] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    7.793478] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    7.793495] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    7.793506] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    7.793523] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    7.793534] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    7.793545] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    7.793561] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    7.793577] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    7.793592] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    7.793603] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    7.793620] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    7.793636] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    7.793645] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    7.793657] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    7.793665] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    7.793681] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    7.793698] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    7.793707] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    7.793722] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    7.793730] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
[ 5105.656219] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[ 5105.656226] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ff00e0 0x00ef00d0
[ 5105.656232] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00000000
[ 5105.666296] (II) RADEON(0): avivo_restore !
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
[ 5106.363068] (II) Open ACPI successful (/var/run/acpid.socket)
Output DIG dpms success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1680x1050 - 2240 1089 10
[ 5106.368123] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[ 5106.368128] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ff00e0
[ 5106.368134] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 146250000
best_freq: 146250000
best_feedback_div: 65
best_ref_div: 2
best_post_div: 6
[ 5106.379854] (II) RADEON(0): crtc(0) Clock: mode 146250, PLL 146250
[ 5106.379862] (II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x41(65), pdiv 6
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output DIG dpms success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
[ 5106.505682] (II) AT Translated Set 2 keyboard: Device reopened after 1 attempts.
[ 5106.521673] (II) Macintosh mouse button emulation: Device reopened after 1 attempts.
[ 5106.533661] (II) ImPS/2 Generic Wheel Mouse: Device reopened after 1 attempts.
```and this Xorg.0.log (with radeonhd) when it hangs and end up in offering low graphics mode```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux zika-desktop 2.6.28-10-generic #33-Ubuntu SMP Mon Mar 16 23:49:27 UTC 2009 x86_64
Build Date: 07 March 2009  02:19:24AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: [    0.000667] (--) probed, [    0.000676] (**) from config file, [    0.000682] (==) default setting,
    [    0.000688] (++) from command line, [    0.000694] (!!) notice, [    0.000700] (II) informational,
    [    0.000706] (WW) warning, [    0.000712] (EE) error, [    0.000717] (NI) not implemented, [    0.000723] (??) unknown.
[    0.000772] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 18 12:29:41 2009
[    0.000813] (==) Using config file: "/etc/X11/xorg.conf"
[    0.000884] (==) No Layout section.  Using the first Screen section.
[    0.000893] (**) |-->Screen "Default Screen" (0)
[    0.000900] (**) |   |-->Monitor "Configured Monitor"
[    0.001109] (**) |   |-->Device "Configured Video Device"
[    0.001128] (==) Automatically adding devices
[    0.001134] (==) Automatically enabling devices
[    0.001163] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
[    0.001207] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    0.001213] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.001219] (II) Cannot locate a core pointer device.
[    0.001224] (II) Cannot locate a core keyboard device.
[    0.001228] (II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.001236] (II) Loader magic: 0xb40
[    0.001242] (II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
[    0.001260] (II) Loader running on linux
[    0.001267] (++) using VT number 7

[    0.029877] (--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3600 Series rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    0.030044] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.030072] (II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
[    0.030543] (II) LoadModule: "extmod"
[    0.030871] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.031049] (II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.031074] (II) Loading extension MIT-SCREEN-SAVER
[    0.031079] (II) Loading extension XFree86-VidModeExtension
[    0.031084] (II) Loading extension XFree86-DGA
[    0.031088] (II) Loading extension DPMS
[    0.031092] (II) Loading extension XVideo
[    0.031097] (II) Loading extension XVideo-MotionCompensation
[    0.031101] (II) Loading extension X-Resource
[    0.031106] (II) LoadModule: "dbe"
[    0.031296] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.031374] (II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.031402] (II) Loading extension DOUBLE-BUFFER
[    0.031407] (II) LoadModule: "glx"
[    0.031584] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.031727] (II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.031750] (==) AIGLX enabled
[    0.031760] (II) Loading extension GLX
[    0.031766] (II) LoadModule: "record"
[    0.031954] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.032032] (II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.032054] (II) Loading extension RECORD
[    0.032058] (II) LoadModule: "dri"
[    0.032236] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.032383] (II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.032404] (II) Loading extension XFree86-DRI
[    0.032411] (II) LoadModule: "dri2"
[    0.032594] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.032665] (II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.032683] (II) Loading extension DRI2
[    0.032697] (II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
[    0.032799] (II) Matched radeonhd from file name radeonhd.ids
[    0.032908] (II) Matched radeon from file name radeon.ids
[    0.033243] (==) Matched radeonhd for the autoconfigured driver
[    0.033250] (==) Assigned the driver to the xf86ConfigLayout
[    0.033255] (II) LoadModule: "radeonhd"
[    0.033398] (II) Loading /usr/lib/xorg/modules/drivers//radeonhd_drv.so
[    0.033565] (II) Module radeonhd: vendor="AMD GPG"
    compiled for 1.6.0, module version = 1.2.4
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.033594] (II) RADEONHD: X driver for the following AMD GPG (ATI) graphics devices:
    RV505 : Radeon X1550, X1550 64bit.
    RV515 : Radeon X1300, X1550, X1600; FireGL V3300, V3350.
    RV516 : Radeon X1300, X1550, X1550 64-bit, X1600; FireMV 2250.
    R520  : Radeon X1800; FireGL V5300, V7200, V7300, V7350.
    RV530 : Radeon X1300 XT, X1600, X1600 Pro, X1650; FireGL V3400, V5200.
    RV535 : Radeon X1300, X1650.
    RV550 : Radeon X2300 HD.
    RV560 : Radeon X1650.
    RV570 : Radeon X1950, X1950 GT; FireGL V7400.
    R580  : Radeon X1900, X1950; AMD Stream Processor.
    R600  : Radeon HD 2900 GT/Pro/XT; FireGL V7600/V8600/V8650.
    RV610 : Radeon HD 2350, HD 2400 Pro/XT, HD 2400 Pro AGP; FireGL V4000.
    RV620 : Radeon HD 3450, HD 3470.
    RV630 : Radeon HD 2600 LE/Pro/XT, HD 2600 Pro/XT AGP; Gemini RV630;
        FireGL V3600/V5600.
    RV635 : Radeon HD 3650, HD 3670.
    RV670 : Radeon HD 3690, 3850, HD 3870, FireGL V7700, FireStream 9170.
    R680  : Radeon HD 3870 X2.
    M52   : Mobility Radeon X1300.
    M54   : Mobility Radeon X1400; M54-GL.
    M56   : Mobility Radeon X1600; Mobility FireGL V5200.
    M58   : Mobility Radeon X1800, X1800 XT; Mobility FireGL V7100, V7200.
    M62   : Mobility Radeon X1350.
    M64   : Mobility Radeon X1450, X2300.
    M66   : Mobility Radeon X1700, X1700 XT; FireGL V5250.
    M68   : Mobility Radeon X1900.
    M71   : Mobility Radeon HD 2300.
    M72   : Mobility Radeon HD 2400; Radeon E2400.
    M74   : Mobility Radeon HD 2400 XT.
    M76   : Mobility Radeon HD 2600;
        (Gemini ATI) Mobility Radeon HD 2600 XT.
    M82   : Mobility Radeon HD 3400.
    M86   : Mobility Radeon HD 3650, HD 3670, Mobility FireGL V5700.
    M88   : Mobility Radeon HD 3850, HD 3850 X2, HD 3870, HD3870 X2.
    RS600 : Radeon Xpress 1200, Xpress 1250.
    RS690 : Radeon X1200, X1250, X1270.
    RS740 : RS740, RS740M.
    RS780 : Radeon HD 3100/3200/3300 Series.
    RV770 : Radeon HD 4800 Series; Everest, K2, Denali ATI FirePro.
    R700  : Radeon R700.
    M98   : Radeon M98 Mobility.
    RV730 : Radeon HD4670, HD4650.
    M96   : Radeon M96 Mobility.
    RV710 : Radeon HD4570, HD4350.

[    0.033634] (II) RADEONHD: version 1.2.4, built from non-git sources

[    0.034306] (II) Primary Device is: PCI 01@00:00:0
[    0.049429] (II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
[    0.050017] (II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
[    0.065170] (II) Setting vga for screen 0.
[    0.065217] (II) RADEONHD(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    0.065228] (==) RADEONHD(0): Depth 24, [    0.065232] (--) framebuffer bpp 32
[    0.065257] (**) RADEONHD(0): Selected ShadowFB.
[    0.065267] (II) RADEONHD(0): Unknown card detected: 0x9598:0x1043:0x01DA.
    If - and only if - your card does not work or does not work optimally
    please contact radeonhd@opensuse.org to help rectify this.
    Use the subject: 0x9598:0x1043:0x01DA: <name of board>
    and *please* describe the problems you are seeing
    in your message.
[    0.065278] (--) RADEONHD(0): Detected an RV635 on an unidentified card
[    0.065310] (II) RADEONHD(0): Mapped IO @ 0xfeaf0000 to 0x7fe8fedf8000 (size 0x00010000)
[    0.065360] (II) RADEONHD(0): PCIE Card Detected
[    0.065374] (II) RADEONHD(0): Getting BIOS copy from legacy VBIOS location
[    0.066195] (II) RADEONHD(0): ATOM BIOS Rom: 
    SubsystemVendorID: 0x1043 SubsystemID: 0x01da
    IOBaseAddress: 0xd000
    Filename: SV28760.bin 
    BIOS Bootup Message:  
9598.10.88.0.3.AS01                                  
                        
[    0.066226] (II) RADEONHD(0): Analog TV Default Mode: 1
[    0.066232] (II) RADEONHD(0): Found default TV Mode NTSC
[    0.066239] (II) RADEONHD(0): The detected amount of videoram exceeds the PCI BAR aperture.
[    0.066243] (II) RADEONHD(0): Using only 262144kB of the total 524288kB.
[    0.066248] (--) RADEONHD(0): VideoRAM: 262144 kByte
[    0.066255] (II) RADEONHD(0): Framebuffer space used by Firmware (kb): 20
[    0.066261] (II) RADEONHD(0): Start of VRAM area used by Firmware: 0x1fffb000
[    0.066266] (II) RADEONHD(0): AtomBIOS requests 20kB of VRAM scratch space
[    0.066270] (II) RADEONHD(0): AtomBIOS VRAM scratch base: 0x1fffb000
[    0.066275] (WW) RADEONHD(0): rhdAtomAllocateFbScratch: FW FB scratch area 536850432 (size: 20480) extends beyond available framebuffer size 268435456
[    0.066282] (II) RADEONHD(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    0.066305] (II) RADEONHD(0): Default Engine Clock: 725000
[    0.066312] (II) RADEONHD(0): Default Memory Clock: 500000
[    0.066317] (II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    0.066323] (II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
[    0.066331] (II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Input: 13500
[    0.066336] (II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Input: 1000
[    0.066342] (II) RADEONHD(0): Maximum Pixel Clock: 400000
[    0.066347] (II) RADEONHD(0): Reference Clock: 27000
[    0.066357] (II) RADEONHD(0): Direct rendering not officially supported on R600 and up
[    0.066363] (II) Loading sub module "i2c"
[    0.066367] (II) LoadModule: "i2c"
[    0.066382] (II) Module "i2c" already built-in
[    0.066390] (II) RADEONHD(0): Reference Clock: 27000
[    0.066397] (II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f90
[    0.066403] (II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
[    0.066420] (II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f90
[    0.066426] (II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
[    0.066445] (II) RADEONHD(0): I2C bus "RHD I2C line 0" initialized.
[    0.066451] (II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f94
[    0.066457] (II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
[    0.066462] (II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f94
[    0.066468] (II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
[    0.066474] (II) RADEONHD(0): I2C bus "RHD I2C line 1" initialized.
[    0.066479] (II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f98
[    0.066487] (II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
[    0.066495] (II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f98
[    0.066501] (II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
[    0.066507] (II) RADEONHD(0): I2C bus "RHD I2C line 2" initialized.
[    0.066512] (II) RADEONHD(0): GPIO_I2C_Clk_Mask: 0x1f88
[    0.066518] (II) RADEONHD(0): GPIO_I2C_Clk_Mask_Shift: 0x0
[    0.066524] (II) RADEONHD(0): GPIO_I2C_Data_Mask: 0x1f88
[    0.066529] (II) RADEONHD(0): GPIO_I2C_Data_Mask_Shift: 0x8
[    0.066535] (II) RADEONHD(0): I2C bus "RHD I2C line 3" initialized.
[    0.066539] (II) Loading sub module "ddc"
[    0.066543] (II) LoadModule: "ddc"
[    0.066551] (II) Module "ddc" already built-in
[    0.066559] (II) RADEONHD(0): Detected VGA mode.
[    0.066577] (II) RADEONHD(0): Minimum Pixel ClockPLL Frequency Output: 0
[    0.066582] (II) RADEONHD(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    0.066588] (II) RADEONHD(0): Maximum Pixel Clock: 400000
[    0.066593] (II) RADEONHD(0): Reference Clock: 27000
[    0.066608] (II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00000000 (size = 0x00004000)
[    0.066615] (II) RADEONHD(0): FB: Allocated Cursor Image at offset 0x00004000 (size = 0x00004000)
[    0.066666] (II) RADEONHD(0): Connector[0] {RHD_CONNECTOR_DVI_SINGLE, "HDMI_TYPE_A DFP1 CRT2", RHD_DDC_1, RHD_HPD_0, { RHD_OUTPUT_UNIPHYA, RHD_OUTPUT_DACB } }
[    0.066674] (II) RADEONHD(0): Connector[1] {RHD_CONNECTOR_TV, "7PIN_DIN TV1 CV", RHD_DDC_0, RHD_HPD_NONE, { RHD_OUTPUT_DACB, RHD_OUTPUT_NONE } }
[    0.066680] (II) RADEONHD(0): Connector[2] {RHD_CONNECTOR_DVI, "DUAL_LINK_DVI_I CRT1 DFP2", RHD_DDC_0, RHD_HPD_1, { RHD_OUTPUT_KLDSKP_LVTMA, RHD_OUTPUT_DACA } }
[    0.066763] (--) RADEONHD(0): Attaching Output UNIPHY_A to Connector DVI-I 1
[    0.066772] (--) RADEONHD(0): Attaching Output DAC B to Connector DVI-I 1
[    0.066780] (--) RADEONHD(0): Attaching Output DAC B to Connector TV 7PIN_DIN
[    0.066790] (--) RADEONHD(0): Attaching Output UNIPHY_KLDSKP_LVTMA to Connector DVI-I 2
[    0.066797] (--) RADEONHD(0): Attaching Output DAC A to Connector DVI-I 2
[    0.066882] (II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/digital for Output UNIPHY_A
[    0.066888] (II) RADEONHD(0): RandR: Adding RRoutput DVI-I_1/analog for Output DAC B
[    0.066893] (II) RADEONHD(0): RandR: Adding RRoutput TV_7PIN_DIN for Output DAC B
[    0.066898] (II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/digital for Output UNIPHY_KLDSKP_LVTMA
[    0.066902] (II) RADEONHD(0): RandR: Adding RRoutput DVI-I_2/analog for Output DAC A
[    0.066912] (II) RADEONHD(0): Output DVI-I_1/digital using monitor section Configured Monitor
[    0.066922] (II) RADEONHD(0): Output DVI-I_1/digital has no monitor section
[    0.066931] (II) RADEONHD(0): Output DVI-I_1/analog has no monitor section
[    0.066936] (II) RADEONHD(0): Output TV_7PIN_DIN has no monitor section
[    0.066942] (II) RADEONHD(0): Output DVI-I_2/digital has no monitor section
[    0.066947] (II) RADEONHD(0): Output DVI-I_2/analog has no monitor section
[    0.067002] (II) RADEONHD(0): EDID for output DVI-I_1/digital
[    0.067014] (II) RADEONHD(0): EDID for output DVI-I_1/analog
[    0.067022] (II) RADEONHD(0): EDID for output TV_7PIN_DIN
[    0.067030] (II) RADEONHD(0): EDID for output DVI-I_2/digital
[    0.067037] (II) RADEONHD(0): EDID for output DVI-I_2/analog
[    0.067042] (II) RADEONHD(0): Output DVI-I_1/digital disconnected
[    0.067047] (II) RADEONHD(0): Output DVI-I_1/analog disconnected
[    0.067059] (II) RADEONHD(0): Output TV_7PIN_DIN disconnected
[    0.067063] (II) RADEONHD(0): Output DVI-I_2/digital disconnected
[    0.067068] (II) RADEONHD(0): Output DVI-I_2/analog disconnected
[    0.067074] (WW) RADEONHD(0): No outputs definitely connected, trying again...
[    0.067079] (II) RADEONHD(0): Output DVI-I_1/digital disconnected
[    0.067085] (II) RADEONHD(0): Output DVI-I_1/analog disconnected
[    0.067089] (II) RADEONHD(0): Output TV_7PIN_DIN disconnected
[    0.067094] (II) RADEONHD(0): Output DVI-I_2/digital disconnected
[    0.067098] (II) RADEONHD(0): Output DVI-I_2/analog disconnected
[    0.067106] (WW) RADEONHD(0): Unable to find initial modes
[    0.067113] (EE) RADEONHD(0): RandR: No valid modes. Disabling RandR support.
[    0.067231] (EE) RADEONHD(0): Failed to detect a connected monitor
[    0.067257] (II) RADEONHD(0): Destroying UNIPHY_A

Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x26) [0x4f1916]
1: /usr/X11R6/bin/X(xf86SigHandler+0x41) [0x485a91]
2: /lib/libc.so.6 [0x7fe8fc93c040]
3: /usr/lib/xorg/modules/drivers//radeonhd_drv.so(RHDAudioUnregisterHdmi+0x4d) [0x7fe8fab9fcfd]
4: /usr/lib/xorg/modules/drivers//radeonhd_drv.so(RHDHdmiDestroy+0x42) [0x7fe8fabb34f2]
5: /usr/lib/xorg/modules/drivers//radeonhd_drv.so [0x7fe8fabacc38]
6: /usr/lib/xorg/modules/drivers//radeonhd_drv.so(RHDOutputsDestroy+0x5c) [0x7fe8fabc085c]
7: /usr/lib/xorg/modules/drivers//radeonhd_drv.so [0x7fe8fabae122]
8: /usr/lib/xorg/modules/drivers//radeonhd_drv.so [0x7fe8fabb0449]
9: /usr/X11R6/bin/X(InitOutput+0xdbc) [0x46f9cc]
10: /usr/X11R6/bin/X(main+0x20e) [0x433c2e]
11: /lib/libc.so.6(__libc_start_main+0xe6) [0x7fe8fc9275a6]
12: /usr/X11R6/bin/X [0x433269]
Saw signal 11.  Server aborting.
 ddxSigGiveUp: Closing log
```**last I hear there is fglrx driver available. I looked in Synaptic and there it is. sadly, the only people that talk about it were not able to utilize it ...** [http://ubuntuforums.org/showpost.php?p=6916608 ]("http://ubuntuforums.org/showpost.php?p=6916608")[http://ubuntuforums.org/showpost.php?p=6915639](http://ubuntuforums.org/showpost.php?p=6915639)

**last update for this post:** xorg-driver-fglrx is in Your Synaptic and ready for install. it worked for me and for all that had problems in threads mentioned above. the only thing that has to be done (known for us having ATI) is:```
sudo aticonfig --initial -f
sudo aticonfig --overlay-type=Xv(optional)
```

---

### Post by tormod on 2009-03-19
The r6xx/r7xx drm support has now been added to the Jaunty kernel 2.6.28-11 so the xorg-edgers drm-snapshot is not needed any longer. Plain Jaunty should give you EXA and video acceleration for practically all ATI cards (using the default -ati/-radeon driver and the default, minimal xorg.conf).

---

### Post by zika on 2009-03-19
> **tormod said:**
> The r6xx/r7xx drm support has now been added to the Jaunty kernel 2.6.28-11 so the xorg-edgers drm-snapshot is not needed any longer. Plain Jaunty should give you EXA and video acceleration for practically all ATI cards (using the default -ati/-radeon driver and the default, minimal xorg.conf).
so, we can get back from fglrx to radeon? with the same speed? with compiz?

**update:** to answer myself :) (after uninstalling fglrx driver and everything that came with it)
(back to radeon: by all means yes)
(speed: numbers say no, feeling say yes)
(compiz: no if You uninstall everything that came with fglrx, according to some posters, yes if You leave fglrx-kernel-source, i.e. leave dkms module fglrx in kernel, I did nor try this). 
so, I'm back to radeon after less than 6(six) hours of testing fglrx ... and feeling free ... :)
(every time I try fglrx I get feeling in Ubuntu that I'm kind of "in Windows" ... do not know why but that is the fact ... )

**@tormod: **thank You for all the work You invested in open-source drivers ... !

---

### Post by shelvingguy on 2009-03-19
tormod - I have not had a chance to test it yet.  But, should this update allow me to add back the other half of my RAM.

I'm using "ati" with my ATI Mobility Radeon HD 3650.

I will test it later today, but I thought I would ask if anyone has tried it with success.

Thanks.

---

### Post by zika on 2009-03-19
> **shelvingguy said:**
> tormod - I have not had a chance to test it yet.  But, should this update allow me to add back the other half of my RAM.

I'm using "ati" with my ATI Mobility Radeon HD 3650.

I will test it later today, but I thought I would ask if anyone has tried it with success.

Thanks.
on my ASUS ah 3650 (a.k.a. ATI HD 3650) it works like a charm. from my posts You could see that I was testing fglrx for less than 6 hours and got back. I'm on radeon from first moment in Jaunty and for several months back on Ibex. this newest version is faster than fglrx (not in numbers but on simple feeling). 3G memory on AMD Phenom X3.

---

### Post by shelvingguy on 2009-03-19
zika - Is your card Mobility Radeon HD 3650?  I'm no expert, but it appears to make a difference.  Thanks.

---

### Post by zika on 2009-03-19
> **shelvingguy said:**
> zika - Is your card Mobility Radeon HD 3650?  I'm no expert, but it appears to make a difference.  Thanks.
ASUS ah 3650 (a.k.a. ATI HD 3650) rv635.
lshw gives:```

id:
  display
  description:   VGA compatible controller
  product:   Mobility Radeon HD 3600 Series
  vendor:   ATI Technologies Inc
  physical id: 
  0
  bus info: 
  pci@0000:02:00.0
  version:   00
  width:   64 bits
  clock:   33MHz
  capabilities:   pm pciexpress msi cap_list
```

---

### Post by shelvingguy on 2009-03-19
Fiddlesticks!

I put the RAM back and it does not work.  I tried ati and radeon and both boot to an unresponsive black screen.  Do you have 4GB of RAM in your machine?

Xorg.0.log is attached.

[HTML]X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux jeff-laptop 2.6.28-10-generic #33-Ubuntu SMP Mon Mar 16 23:49:27 UTC 2009 x86_64
Build Date: 07 March 2009  02:19:24AM
xorg-server 2:1.6.0-0ubuntu1 (buildd@crested.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: [    0.010072] (--) probed, [    0.010091] (**) from config file, [    0.010104] (==) default setting,
	[    0.010116] (++) from command line, [    0.010129] (!!) notice, [    0.010141] (II) informational,
	[    0.010153] (WW) warning, [    0.010164] (EE) error, [    0.010176] (NI) not implemented, [    0.010188] (??) unknown.
[    0.010323] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Mar 19 14:22:53 2009
[    0.011065] (==) Using config file: "/etc/X11/xorg.conf"
[    0.011255] (==) No Layout section.  Using the first Screen section.
[    0.011281] (**) |-->Screen "Default Screen" (0)
[    0.011455] (**) |   |-->Monitor "Configured Monitor"
[    0.011813] (**) |   |-->Device "Configured Video Device"
[    0.011846] (==) Automatically adding devices
[    0.011859] (==) Automatically enabling devices
[    0.072278] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
[    0.152064] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    0.152097] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.152113] (II) Cannot locate a core pointer device.
[    0.152123] (II) Cannot locate a core keyboard device.
[    0.152132] (II) The server relies on HAL to provide the list of input devices.
	If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.152151] (II) Loader magic: 0xb40
[    0.152161] (II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
[    0.152195] (II) Loader running on linux
[    0.152210] (++) using VT number 7

[    0.191090] (--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3650 rev 0, Mem @ 0xc0000000/536870912, 0xbfef0000/65536, I/O @ 0x00002000/256, BIOS @ 0x????????/131072
[    0.191386] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.191415] (II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.191580] (II) LoadModule: "extmod"
[    0.205354] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.205699] (II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.205760] (II) Loading extension MIT-SCREEN-SAVER
[    0.205772] (II) Loading extension XFree86-VidModeExtension
[    0.205783] (II) Loading extension XFree86-DGA
[    0.205793] (II) Loading extension DPMS
[    0.205802] (II) Loading extension XVideo
[    0.205816] (II) Loading extension XVideo-MotionCompensation
[    0.205826] (II) Loading extension X-Resource
[    0.205839] (II) LoadModule: "dbe"
[    0.206234] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.206411] (II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.206466] (II) Loading extension DOUBLE-BUFFER
[    0.206480] (II) LoadModule: "glx"
[    0.206854] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.207145] (II) Module glx: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.207213] (==) AIGLX enabled
[    0.207233] (II) Loading extension GLX
[    0.207249] (II) LoadModule: "record"
[    0.207611] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.207741] (II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
[    0.207782] (II) Loading extension RECORD
[    0.207793] (II) LoadModule: "dri"
[    0.208134] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.248716] (II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.248792] (II) Loading extension XFree86-DRI
[    0.248813] (II) LoadModule: "dri2"
[    0.249227] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.259306] (II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
[    0.259367] (II) Loading extension DRI2
[    0.259384] (II) LoadModule: "ati"
[    0.259670] (II) Loading /usr/lib/xorg/modules/drivers//ati_drv.so
[    0.291203] (II) Module ati: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
[    0.291287] (II) LoadModule: "radeon"
[    0.291588] (II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
[    0.346690] (II) Module radeon: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 6.12.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
[    0.347528] (II) RADEON: Driver for ATI Radeon chipsets:
	ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
	ATI Radeon Mobility X300 (M24) 3152 (PCIE),
	ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
	ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
	ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
	ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
	ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
	ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
	ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
	ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
	ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
	ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
	ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
	ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
	ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
	ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
	ATI Radeon X800PRO (R420) JI (AGP),
	ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
	ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
	ATI Radeon Mobility 9800 (M18) JN (AGP),
	ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
	ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
	ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
	ATI Radeon Mobility M7 LW (AGP),
	ATI Mobility FireGL 7800 M7 LX (AGP),
	ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
	ATI FireGL Mobility 9000 (M9) Ld (AGP),
	ATI Radeon Mobility 9000 (M9) Lf (AGP),
	ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
	ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
	ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
	ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
	ATI Radeon 9800XT NJ (AGP),
	ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
	ATI Radeon Mobility 9600 (M10) NQ (AGP),
	ATI Radeon Mobility 9600 (M11) NR (AGP),
	ATI Radeon Mobility 9600 (M10) NS (AGP),
	ATI FireGL Mobility T2 (M10) NT (AGP),
	ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
	ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
	ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
	ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
	ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
	ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
	ATI Radeon Mobility X300 (M22) 5460 (PCIE),
	ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
	ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
	ATI Radeon X800PRO (R423) UI (PCIE),
	ATI Radeon X800LE (R423) UJ (PCIE),
	ATI Radeon X800SE (R423) UK (PCIE),
	ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
	ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
	ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
	ATI FireGL unknown (R423) UR (PCIE),
	ATI FireGL unknown (R423) UT (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility FireGL V5000 (M26) (PCIE),
	ATI Mobility Radeon X700 XL (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Mobility Radeon X700 (M26) (PCIE),
	ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
	ATI Radeon Mobility 9100 IGP (U3) 5835,
	ATI Radeon XPRESS 200 5954 (PCIE),
	ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
	ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
	ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
	ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
	ATI Radeon XPRESS 200M 5975 (PCIE),
	ATI Radeon XPRESS 200 5A41 (PCIE),
	ATI Radeon XPRESS 200M 5A42 (PCIE),
	ATI Radeon XPRESS 200 5A61 (PCIE),
	ATI Radeon XPRESS 200M 5A62 (PCIE),
	ATI Radeon X300 (RV370) 5B60 (PCIE),
	ATI Radeon X600 (RV370) 5B62 (PCIE),
	ATI Radeon X550 (RV370) 5B63 (PCIE),
	ATI FireGL V3100 (RV370) 5B64 (PCIE),
	ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
	ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
	ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
	ATI Mobility Radeon X800 XT (M28) (PCIE),
	ATI Mobility FireGL V5100 (M28) (PCIE),
	ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
	ATI Radeon X850 XT PE (R480) (PCIE),
	ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
	ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
	ATI Radeon X850 XT (R480) (PCIE),
	ATI Radeon X800XT (R423) 5D57 (PCIE),
	ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
	ATI Radeon X700 PRO (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
	ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
	ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
	ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
	ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
	ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
	ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
	ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
	ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
	ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
	ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
	ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
	ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
	ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
	ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
	ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
	ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
	ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
	ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
	ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
	ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
	ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
	ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
	ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
	ATI Mobility Radeon X1700, ATI Radeon X2300HD,
	ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
	ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
	ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
	ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
	ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
	ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
	ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
	ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
	ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
	ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
	ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
	ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
	ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
	ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
	ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
	ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
	ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
	ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
	ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
	ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
	ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
	ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
	ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
	ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
	ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
	ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
	ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
	ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
	ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
	ATI Mobility Radeon HD 3850 X2, ATI RV670,
	ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
	ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
	ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
	ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
	ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
	ATI Mobility Radeon 4500 Series, ATI RV630,
	ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
	ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
	ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
	ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
	ATI FireGL V3600, ATI Radeon HD 2600 LE,
	ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
	ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
	ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
	ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
	ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
	ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
	ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
	ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
	ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
	ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
	ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics
[    0.353646] (II) Primary Device is: PCI 01@00:00:0
[    0.383504] (II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
[    0.383704] (II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
[    0.412960] (II) Setting vga for screen 0.
[    0.413370] (II) RADEON(0): Built from git commit a6855c370194b6df307ea33724fe17a85d67607e
[    0.413398] (II) RADEON(0): TOTO SAYS 00000000bfef0000
[    0.413410] (II) RADEON(0): MMIO registers at 0x00000000bfef0000: size 64KB
[    0.413502] (II) RADEON(0): PCI bus 1 card 0 func 0
[    0.445251] (II) RADEON(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
[    0.445287] (==) RADEON(0): Depth 24, [    0.445298] (--) framebuffer bpp 32
[    0.445311] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    0.445325] (==) RADEON(0): Default visual is TrueColor
[    0.445376] (II) Loading sub module "vgahw"
[    0.445388] (II) LoadModule: "vgahw"
[    0.445530] (II) Loading /usr/lib/xorg/modules//libvgahw.so
[    0.445698] (II) Module vgahw: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 0.1.0
	ABI class: X.Org Video Driver, version 5.0
[    0.445765] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    0.445781] (==) RADEON(0): RGB weight 888
[    0.445792] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    0.445807] (--) RADEON(0): Chipset: "ATI Mobility Radeon HD 3650" (ChipID = 0x9591)
[    0.445825] (WW) RADEON(0): R600 support is mostly incomplete and very experimental
[    0.445836] (--) RADEON(0): Linear framebuffer at 0x00000000c0000000
[    0.445924] (II) RADEON(0): PCIE card detected
[    0.446011] (II) Loading sub module "int10"
[    0.446025] (II) LoadModule: "int10"
[    0.446114] (II) Loading /usr/lib/xorg/modules//libint10.so
[    0.470607] (II) Module int10: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 5.0
[    0.470674] (II) RADEON(0): initializing int10
[    0.471293] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    0.471455] (II) RADEON(0): ATOM BIOS detected
[    0.472065] (II) RADEON(0): ATOM BIOS Rom: 
	SubsystemVendorID: 0x1179 SubsystemID: 0xff01
	IOBaseAddress: 0x2000
	Filename: BR29796.001 
	BIOS Bootup Message: 

Tosh_Compal_LA_M86M_DDR2 M86 GDDR2_32Mx16 256bit 1024MB 600e/500m           


[    0.472118] (II) RADEON(0): Framebuffer space used by Firmware (kb): 20
[    0.472130] (II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffb000
[    0.472140] (II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
[    0.472151] (II) RADEON(0): AtomBIOS VRAM scratch base: 0x1fffb000
[    0.472161] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    0.472202] (II) RADEON(0): Default Engine Clock: 600000
[    0.472215] (II) RADEON(0): Default Memory Clock: 500000
[    0.472225] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    0.472235] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    0.472245] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
[    0.472254] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
[    0.472264] (II) RADEON(0): Maximum Pixel Clock: 400000
[    0.472274] (II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card1
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card2
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card3
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card4
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card5
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card6
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card7
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card8
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card9
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card10
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card11
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card12
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card13
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card14
drmOpenByBusid: drmOpenMinor returns -1
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: node name is /dev/dri/card14
[    0.808441] (EE) RADEON(0): [dri] RADEONDRIGetVersion failed to open the DRM
[dri] Disabling DRI.
[    0.808487] (II) RADEON(0): using shadow framebuffer
[    0.808498] (II) Loading sub module "shadow"
[    0.808507] (II) LoadModule: "shadow"
[    0.808646] (II) Loading /usr/lib/xorg/modules//libshadow.so
[    0.892614] (II) Module shadow: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    0.892693] (II) RADEON(0): Detected total video RAM=4194303K, accessible=524288K (PCI BAR=524288K)
[    0.892708] (--) RADEON(0): Mapped VideoRAM: 524288 kByte (32 bit DDR SDRAM)
[    0.892722] (II) RADEON(0): Color tiling disabled
[    0.892732] (II) RADEON(0): Max desktop size set to 2560x1600
[    0.892742] (II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
[    0.892752] (II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
[    0.892773] (II) Loading sub module "ddc"
[    0.892785] (II) LoadModule: "ddc"
[    0.892811] (II) Module "ddc" already built-in
[    0.892821] (II) Loading sub module "i2c"
[    0.892829] (II) LoadModule: "i2c"
[    0.892847] (II) Module "i2c" already built-in
[    0.913724] (II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 600.000000, mclk: 500.000000
[    0.913795] (II) RADEON(0): PLL parameters: rf=2700 rd=1023 min=64800 max=120000; xclk=40000
[    0.913826] (WW) RADEON(0): LVDS Info:
XRes: 1366, YRes: 768, DotClock: 69860
HBlank: 108, HOverPlus: 48, HSyncWidth: 32
VBlank: 22, VOverPlus: 2, VSyncWidth: 5
[    0.913871] (II) RADEON(0): Output VGA-0 using monitor section Configured Monitor
[    0.936530] (II) RADEON(0): I2C bus "VGA-0" initialized.
[    0.936579] (II) RADEON(0): Output LVDS has no monitor section
[    0.936594] (II) RADEON(0): I2C bus "LVDS" initialized.
[    0.936617] (II) RADEON(0): Output HDMI-0 has no monitor section
[    0.936630] (II) RADEON(0): I2C bus "HDMI-0" initialized.
[    0.936647] (II) RADEON(0): Port0:
  XRANDR name: VGA-0
  Connector: VGA
  CRT1: INTERNAL_KLDSCP_DAC1
  DDC reg: 0x7e60
[    0.936704] (II) RADEON(0): Port1:
  XRANDR name: LVDS
  Connector: LVDS
  LCD1: INTERNAL_KLDSCP_LVTMA
  DDC reg: 0x7f68
[    0.936751] (II) RADEON(0): Port2:
  XRANDR name: HDMI-0
  Connector: HDMI-B
  DFP1: INTERNAL_UNIPHY
  DDC reg: 0x7e20
[    0.936816] (II) RADEON(0): I2C device "VGA-0:E-EDID segment register" registered at address 0x60.
[    0.936831] (II) RADEON(0): I2C device "VGA-0:ddc2" registered at address 0xA0.
[    0.939575] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
finished output detect: 0
[    0.945646] (II) RADEON(0): I2C device "LVDS:E-EDID segment register" registered at address 0x60.
[    0.945660] (II) RADEON(0): I2C device "LVDS:ddc2" registered at address 0xA0.
[    0.948400] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
finished output detect: 1
[    0.948429] (II) RADEON(0): I2C device "HDMI-0:E-EDID segment register" registered at address 0x60.
[    0.948441] (II) RADEON(0): I2C device "HDMI-0:ddc2" registered at address 0xA0.
[    0.951200] (II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
finished output detect: 2
finished all detect
before xf86InitialConfiguration
[    0.954032] (II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
Dac detection success
[    0.960090] (II) RADEON(0): Total number of valid Screen mode(s) added: 0
[    0.960211] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    0.960227] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    0.960237] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    0.960247] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.960257] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.960267] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.960276] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.960285] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.960295] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.960304] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.960313] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.960324] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.960333] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.960343] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.960352] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    0.960362] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    0.960371] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    0.960381] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    0.960391] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    0.960400] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    0.960409] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.960419] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.960429] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.960438] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.960447] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    0.960457] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    0.960466] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    0.960476] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    0.960485] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    0.960495] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    0.960504] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    0.960514] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.960523] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.960532] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.960542] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.960551] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.960561] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    0.960571] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    0.960580] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.960590] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.960599] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.960609] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    0.960643] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    0.960655] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    0.960664] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    0.960674] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.960684] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.960693] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.960702] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    0.960712] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    0.960722] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    0.960731] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    0.960741] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    0.960750] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    0.960762] (II) RADEON(0): Printing probed modes for output VGA-0
[    0.960778] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    0.960806] (II) RADEON(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz)
[    0.960826] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.960844] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.960862] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.963613] (II) RADEON(0): Output: LVDS, Detected Monitor Type: 0
[    0.963631] (II) RADEON(0): Query for AtomBIOS Get Panel EDID: failed
[    0.963663] (II) RADEON(0): Added native panel mode: 1366x768
[    0.963774] (II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
[    0.963787] (II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
[    0.963797] (II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
[    0.963807] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.963816] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.963826] (II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
[    0.963835] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.963845] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.963854] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.963864] (II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
[    0.963873] (II) RADEON(0): Not using default mode "1024x768" (hsync out of range)
[    0.963883] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.963892] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.963902] (II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)
[    0.963911] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.963921] (II) RADEON(0): Not using default mode "1280x960" (hsync out of range)
[    0.963930] (II) RADEON(0): Not using default mode "1280x960" (vrefresh out of range)
[    0.963940] (II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
[    0.963950] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    0.963959] (II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)
[    0.963969] (II) RADEON(0): Not using default mode "1600x1200" (hsync out of range)
[    0.963979] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.963988] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.963998] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.964024] (II) RADEON(0): Not using default mode "1600x1200" (vrefresh out of range)
[    0.964035] (II) RADEON(0): Not using default mode "1792x1344" (hsync out of range)
[    0.964045] (II) RADEON(0): Not using default mode "1792x1344" (vrefresh out of range)
[    0.964054] (II) RADEON(0): Not using default mode "1856x1392" (hsync out of range)
[    0.964064] (II) RADEON(0): Not using default mode "1856x1392" (vrefresh out of range)
[    0.964073] (II) RADEON(0): Not using default mode "1920x1440" (hsync out of range)
[    0.964083] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    0.964092] (II) RADEON(0): Not using default mode "832x624" (vrefresh out of range)
[    0.964102] (II) RADEON(0): Not using default mode "1152x864" (hsync out of range)
[    0.964111] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.964121] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.964130] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.964139] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.964148] (II) RADEON(0): Not using default mode "1152x864" (vrefresh out of range)
[    0.964158] (II) RADEON(0): Not using default mode "1360x768" (monitor doesn't support reduced blanking)
[    0.964167] (II) RADEON(0): Not using default mode "1400x1050" (hsync out of range)
[    0.964177] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.964187] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.964196] (II) RADEON(0): Not using default mode "1400x1050" (vrefresh out of range)
[    0.964205] (II) RADEON(0): Not using default mode "1440x900" (hsync out of range)
[    0.964215] (II) RADEON(0): Not using default mode "1600x1024" (hsync out of range)
[    0.964225] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    0.964234] (II) RADEON(0): Not using default mode "1680x1050" (hsync out of range)
[    0.964243] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.964253] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.964262] (II) RADEON(0): Not using default mode "1680x1050" (vrefresh out of range)
[    0.964272] (II) RADEON(0): Not using default mode "1920x1080" (hsync out of range)
[    0.964281] (II) RADEON(0): Not using default mode "1920x1200" (hsync out of range)
[    0.964291] (II) RADEON(0): Not using default mode "1920x1440" (vrefresh out of range)
[    0.964300] (II) RADEON(0): Not using default mode "2048x1536" (hsync out of range)
[    0.964310] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    0.964319] (II) RADEON(0): Not using default mode "2048x1536" (vrefresh out of range)
[    0.964330] (II) RADEON(0): Printing probed modes for output LVDS
[    0.964342] (II) RADEON(0): Modeline "1366x768"x60.0   69.86  1366 1414 1446 1474  768 770 775 790 (47.4 kHz)
[    0.964362] (II) RADEON(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz)
[    0.964380] (II) RADEON(0): Modeline "1280x720"x59.9   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync (44.8 kHz)
[    0.964397] (II) RADEON(0): Modeline "1152x768"x59.8   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync (47.7 kHz)
[    0.964414] (II) RADEON(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz)
[    0.964431] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.964449] (II) RADEON(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz)
[    0.964466] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.964483] (II) RADEON(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz)
[    0.967214] (II) RADEON(0): Output: HDMI-0, Detected Monitor Type: 0
invalid output device for dac detection
[    0.967254] (II) RADEON(0): EDID for output HDMI-0
[    0.967278] (II) RADEON(0): Output VGA-0 connected
[    0.967290] (II) RADEON(0): Output LVDS connected
[    0.967300] (II) RADEON(0): Output HDMI-0 disconnected
[    0.967319] (II) RADEON(0): Using fuzzy aspect match for initial modes
[    0.967330] (II) RADEON(0): Output VGA-0 using initial mode 1024x768
[    0.967340] (II) RADEON(0): Output LVDS using initial mode 1024x768
after xf86InitialConfiguration
[    0.967379] (==) RADEON(0): DPI set to (96, 96)
[    0.967388] (II) Loading sub module "fb"
[    0.967398] (II) LoadModule: "fb"
[    0.967533] (II) Loading /usr/lib/xorg/modules//libfb.so
[    0.967762] (II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
[    0.967801] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
[    0.967815] (II) Loading sub module "ramdac"
[    0.967824] (II) LoadModule: "ramdac"
[    0.967845] (II) Module "ramdac" already built-in
[    0.967857] (==) RADEON(0): Will attempt to use R6xx/R7xx EXA support if DRI is enabled.
[    0.967868] (II) Loading sub module "exa"
[    0.967878] (II) LoadModule: "exa"
[    0.967964] (II) Loading /usr/lib/xorg/modules//libexa.so
[    0.997887] (II) Module exa: vendor="X.Org Foundation"
	compiled for 1.6.0, module version = 2.4.0
	ABI class: X.Org Video Driver, version 5.0
[    0.998183] (!!) RADEON(0): For information on using the multimedia capabilities
	of this adapter, please see http://gatos.sf.net.
[    0.998209] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    0.998228] (--) Depth 24 pixmap format is 32 bpp
[    0.998241] (II) do I need RAC?  No, I don't.
[    0.998255] (II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[5] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[6] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[7] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[8] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[9] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[10] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
[    0.998569] (II) RADEON(0): RADEONScreenInit c0000000 0 0
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Output CRT1 disable success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
mc fb loc is 01ff00ff
[    1.680040] (II) RADEON(0): RADEONInitMemoryMap() : 
[    1.680053] (II) RADEON(0):   mem_size         : 0xffffffff
[    1.680063] (II) RADEON(0):   MC_FB_LOCATION   : 0x01ff00ff
[    1.680073] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    1.680083] (II) RADEON(0): Depth moves disabled by default
[    1.680124] (II) RADEON(0): Allocating from a screen of 524288 kb
[    1.680138] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00801000
[    1.680149] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00805000
[    1.680160] (II) RADEON(0): Will use 8196 kb for front buffer at offset 0x00000000
[    1.680171] (II) RADEON(0): Will use 516060 kb for X Server offscreen at offset 0x00809000
[    1.728803] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    1.728847] (II) RADEON(0):   MC_FB_LOCATION   : 0x01ff00ff 0xffffffff
[    1.728859] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    1.739072] (==) RADEON(0): Backing store disabled
[    1.739108] (WW) RADEON(0): Direct rendering disabled
[    1.739128] (EE) RADEON(0): Acceleration initialization failed
[    1.739149] (II) RADEON(0): Acceleration disabled
[    1.739165] (II) RADEON(0): DPMS enabled
[    1.739182] (==) RADEON(0): Silken mouse enabled
[    1.739696] (II) RADEON(0): Textured video requires CP on R5xx/R6xx/R7xx/IGP
Output CRT1 disable success
Output DIG dpms success
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Output DIG dpms success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1366x768 - 1474 790 0
[    2.600191] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    2.600204] (II) RADEON(0):   MC_FB_LOCATION   : 0x01ff00ff 0xffffffff
[    2.600214] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
freq: 69860000
best_freq: 69860140
best_feedback_div: 370
best_ref_div: 13
best_post_div: 11
[    2.612427] (II) RADEON(0): crtc(0) Clock: mode 69860, PLL 69860
[    2.612441] (II) RADEON(0): crtc(0) PLL  : refdiv 13, fbdiv 0x172(370), pdiv 11
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success[/HTML]

---

### Post by zika on 2009-03-20
is this the place that makes the difference:```
[    0.420812] (II) AIGLX: [COLOR=Red]**Screen 0 is not DRI2 capable**[/COLOR]
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    0.427620] (EE) AIGLX error: Calling driver entry point failed
[    0.429178] (EE) AIGLX: **[COLOR=Red]reverting to software rendering[/COLOR]**
[    0.437985] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    0.437997] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    0.438366] (II) RADEON(0): Setting screen physical size to 474 x 296
```ATI Mobility Radeon HD 3650: no compiz with radeon-driver.

here is the whole Xorg.0.log:```

X.Org X Server 1.6.0
Release Date: 2009-2-25
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-16-server x86_64 Ubuntu
Current Operating System: Linux zika-desktop 2.6.28-11-generic #35-Ubuntu SMP Wed Mar 18 21:55:34 UTC 2009 x86_64
Build Date: 19 March 2009  07:23:39AM
xorg-server 2:1.6.0-0ubuntu3 (buildd@crested.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: [    0.001220] (--) probed, [    0.001237] (**) from config file, [    0.001258] (==) default setting,
    [    0.001274] (++) from command line, [    0.001286] (!!) notice, [    0.001302] (II) informational,
    [    0.001315] (WW) warning, [    0.001327] (EE) error, [    0.001344] (NI) not implemented, [    0.001356] (??) unknown.
[    0.001452] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Mar 20 08:13:22 2009
[    0.001531] (==) Using config file: "/etc/X11/xorg.conf"
[    0.001681] (==) No Layout section.  Using the first Screen section.
[    0.001706] (**) |-->Screen "Default Screen" (0)
[    0.001718] (**) |   |-->Monitor "Configured Monitor"
[    0.002121] (**) |   |-->Device "Configured Video Device"
[    0.002165] (==) Automatically adding devices
[    0.002177] (==) Automatically enabling devices
[    0.002233] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
[    0.002318] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
[    0.002335] (==) ModulePath set to "/usr/lib/xorg/modules"
[    0.002350] (**) Extension "Composite" is enabled
[    0.002362] (II) Cannot locate a core pointer device.
[    0.002372] (II) Cannot locate a core keyboard device.
[    0.002379] (II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
[    0.002396] (II) Loader magic: 0xb40
[    0.002404] (II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
[    0.002443] (II) Loader running on linux
[    0.002456] (++) using VT number 7

[    0.031076] (--) PCI:*(0@1:0:0) ATI Technologies Inc Mobility Radeon HD 3600 Series rev 0, Mem @ 0xd0000000/268435456, 0xfeaf0000/65536, I/O @ 0x0000d000/256, BIOS @ 0x????????/131072
[    0.031275] (II) Open ACPI successful (/var/run/acpid.socket)
[    0.031297] (II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
[    0.031874] (II) LoadModule: "extmod"
[    0.032206] (II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
[    0.032373] (II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.032395] (II) Loading extension MIT-SCREEN-SAVER
[    0.032400] (II) Loading extension XFree86-VidModeExtension
[    0.032405] (II) Loading extension XFree86-DGA
[    0.032409] (II) Loading extension DPMS
[    0.032413] (II) Loading extension XVideo
[    0.032419] (II) Loading extension XVideo-MotionCompensation
[    0.032424] (II) Loading extension X-Resource
[    0.032429] (II) LoadModule: "dbe"
[    0.032632] (II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
[    0.032709] (II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.032730] (II) Loading extension DOUBLE-BUFFER
[    0.032735] (II) LoadModule: "glx"
[    0.032928] (II) Loading /usr/lib/xorg/modules/extensions//libglx.so
[    0.033087] (II) Module glx: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.033109] (==) AIGLX enabled
[    0.033118] (II) Loading extension GLX
[    0.033126] (II) LoadModule: "record"
[    0.033336] (II) Loading /usr/lib/xorg/modules/extensions//librecord.so
[    0.033415] (II) Module record: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
[    0.033436] (II) Loading extension RECORD
[    0.033441] (II) LoadModule: "dri"
[    0.033638] (II) Loading /usr/lib/xorg/modules/extensions//libdri.so
[    0.033800] (II) Module dri: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.033822] (II) Loading extension XFree86-DRI
[    0.033829] (II) LoadModule: "dri2"
[    0.034032] (II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
[    0.034111] (II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
[    0.034129] (II) Loading extension DRI2
[    0.034142] (II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
[    0.034308] (II) Matched radeon from file name radeon.ids
[    0.034686] (==) Matched radeon for the autoconfigured driver
[    0.034693] (==) Assigned the driver to the xf86ConfigLayout
[    0.034698] (II) LoadModule: "radeon"
[    0.034833] (II) Loading /usr/lib/xorg/modules/drivers//radeon_drv.so
[    0.034991] (II) Module radeon: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 6.12.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
[    0.035021] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon 8500 AIW BC (AGP),
    ATI Radeon IGP320M (U1) 4336, ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI Radeon 9700 Pro ND (AGP),
    ATI Radeon 9700/9500Pro NE (AGP), ATI Radeon 9600TX NF (AGP),
    ATI FireGL X1 NG (AGP), ATI Radeon 9800PRO NH (AGP),
    ATI Radeon 9800 NI (AGP), ATI FireGL X2 NK (AGP),
    ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI Radeon 4800 Series,
    ATI FirePro RV770, AMD FireStream 9270, AMD FireStream 9250,
    ATI FirePro V8700 (FireGL), ATI Mobility RADEON HD 4870,
    ATI Mobility RADEON M98, ATI FirePro M7750, ATI M98, ATI M98,
    ATI M98, ATI Radeon RV730 (AGP), ATI FirePro M5750,
    ATI Radeon RV730 (AGP), ATI RV730XT [Radeon HD 4670],
    ATI RADEON E4600, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI Mobility Radeon 4500 Series, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon RV710,
    ATI Radeon HD 3470, ATI Mobility Radeon HD 3430,
    ATI Mobility Radeon HD 3400 Series, ATI Radeon HD 3450,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI Radeon HD 3450,
    ATI FirePro V3700, ATI FireMV 2450, ATI FireMV 2260, ATI FireMV 2260,
    ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Radeon HD 3600 PRO, ATI Mobility Radeon HD 3650,
    ATI Mobility Radeon HD 3670, ATI Mobility FireGL V5700,
    ATI Mobility FireGL V5725, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3100 Graphics, ATI Radeon HD 3300 Graphics
[    0.039601] (II) Primary Device is: PCI 01@00:00:0
[    0.055939] (II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [25] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [26] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [27] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [28] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [29] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [30] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [31] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [32] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [33] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [34] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [35] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
[    0.056537] (II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
[    0.072321] (II) Setting vga for screen 0.
[    0.072347] (II) RADEON(0): TOTO SAYS 00000000feaf0000
[    0.072354] (II) RADEON(0): MMIO registers at 0x00000000feaf0000: size 64KB
[    0.072388] (II) RADEON(0): PCI bus 1 card 0 func 0
[    0.087519] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
[    0.087532] (==) RADEON(0): Depth 24, [    0.087537] (--) framebuffer bpp 32
[    0.087543] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    0.087550] (==) RADEON(0): Default visual is TrueColor
[    0.087587] (**) RADEON(0): Option "AccelMethod" "EXA"
[    0.087601] (**) RADEON(0): Option "DRI" "on"
[    0.087621] (II) Loading sub module "vgahw"
[    0.087626] (II) LoadModule: "vgahw"
[    0.087687] (II) Loading /usr/lib/xorg/modules//libvgahw.so
[    0.087778] (II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
[    0.087815] (II) RADEON(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
[    0.087823] (==) RADEON(0): RGB weight 888
[    0.087828] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    0.087839] (--) RADEON(0): Chipset: "ATI Radeon HD 3600 XT" (ChipID = 0x9598)
[    0.087848] (WW) RADEON(0): R600 support is mostly incomplete and very experimental
[    0.087853] (--) RADEON(0): Linear framebuffer at 0x00000000d0000000
[    0.087902] (II) RADEON(0): PCIE card detected
[    0.087923] (II) Loading sub module "int10"
[    0.087928] (II) LoadModule: "int10"
[    0.087994] (II) Loading /usr/lib/xorg/modules//libint10.so
[    0.088106] (II) Module int10: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
[    0.088126] (II) RADEON(0): initializing int10
[    0.094054] (II) RADEON(0): Primary V_BIOS segment is: 0xc000
[    0.094912] (II) RADEON(0): ATOM BIOS detected
[    0.094924] (II) RADEON(0): ATOM BIOS Rom: 
    SubsystemVendorID: 0x1043 SubsystemID: 0x01da
    IOBaseAddress: 0xd000
    Filename: SV28760.bin 
    BIOS Bootup Message:  
9598.10.88.0.3.AS01                                  
                        
[    0.094949] (II) RADEON(0): Framebuffer space used by Firmware (kb): 20
[    0.094955] (II) RADEON(0): Start of VRAM area used by Firmware: 0x1fffb000
[    0.094960] (II) RADEON(0): AtomBIOS requests 20kB of VRAM scratch space
[    0.094965] (II) RADEON(0): AtomBIOS VRAM scratch base: 0x1fffb000
[    0.094970] (II) RADEON(0): Cannot get VRAM scratch space. Allocating in main memory instead
[    0.094995] (II) RADEON(0): Default Engine Clock: 725000
[    0.095000] (II) RADEON(0): Default Memory Clock: 500000
[    0.095005] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Output: 1200000
[    0.095010] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Output: 0
[    0.095014] (II) RADEON(0): Maximum Pixel ClockPLL Frequency Input: 13500
[    0.095018] (II) RADEON(0): Minimum Pixel ClockPLL Frequency Input: 1000
[    0.095023] (II) RADEON(0): Maximum Pixel Clock: 400000
[    0.095027] (II) RADEON(0): Reference Clock: 27000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    0.099961] (II) RADEON(0): [dri] Found DRI library version 1.3.0 and kernel module version 1.29.0
[    0.100022] (==) RADEON(0): Page Flipping disabled on r5xx and newer chips.

[    0.100028] (II) RADEON(0): Will try to use DMA for Xv image transfers
[    0.100035] (II) RADEON(0): Detected total video RAM=524288K, accessible=262144K (PCI BAR=262144K)
[    0.100044] (--) RADEON(0): Mapped VideoRAM: 262144 kByte (128 bit DDR SDRAM)
[    0.100051] (II) RADEON(0): Color tiling disabled
[    0.100078] (II) RADEON(0): Max desktop size set to 2560x1600
[    0.100084] (II) RADEON(0): For a larger or smaller max desktop size, add a Virtual line to your xorg.conf
[    0.100088] (II) RADEON(0): If you are having trouble with 3D, reduce the desktop size by adjusting the Virtual line to your xorg.conf
[    0.100095] (II) Loading sub module "ddc"
[    0.100099] (II) LoadModule: "ddc"
[    0.100115] (II) Module "ddc" already built-in
[    0.100120] (II) Loading sub module "i2c"
[    0.100123] (II) LoadModule: "i2c"
[    0.100132] (II) Module "i2c" already built-in
[    0.100159] (II) RADEON(0): ref_freq: 2700, min_out_pll: 64800, max_out_pll: 120000, min_in_pll: 100, max_in_pll: 1350, xclk: 40000, sclk: 725.000000, mclk: 500.000000
[    0.100212] (II) RADEON(0): PLL parameters: rf=2700 rd=12 min=64800 max=120000; xclk=40000
[    0.100248] (II) RADEON(0): Output DVI-1 using monitor section Configured Monitor
[    0.100262] (II) RADEON(0): I2C bus "DVI-1" initialized.
[    0.100269] (II) RADEON(0): Output DVI-0 has no monitor section
[    0.100274] (II) RADEON(0): I2C bus "DVI-0" initialized.
[    0.100281] (II) RADEON(0): Port0:
  XRANDR name: DVI-1
  Connector: DVI-D
  DFP1: INTERNAL_UNIPHY
  DDC reg: 0x7e50
[    0.100313] (II) RADEON(0): Port1:
  XRANDR name: DVI-0
  Connector: DVI-I
  CRT1: INTERNAL_KLDSCP_DAC1
  DFP2: INTERNAL_KLDSCP_LVTMA
  DDC reg: 0x7e40
[    0.100357] (II) RADEON(0): I2C device "DVI-1:E-EDID segment register" registered at address 0x60.
[    0.100363] (II) RADEON(0): I2C device "DVI-1:ddc2" registered at address 0xA0.
[    0.103137] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
finished output detect: 0
[    0.103162] (II) RADEON(0): I2C device "DVI-0:E-EDID segment register" registered at address 0x60.
[    0.103167] (II) RADEON(0): I2C device "DVI-0:ddc2" registered at address 0xA0.
[    0.157897] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    0.157906] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    0.157912] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    0.157917] (II) RADEON(0): Year: 2008  Week: 21
[    0.157922] (II) RADEON(0): EDID Version: 1.3
[    0.157927] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.157937] (II) RADEON(0): Sync:  Separate
[    0.157946] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.157956] (II) RADEON(0): Gamma: 2.20
[    0.157963] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    0.157977] (II) RADEON(0): First detailed timing is preferred mode
[    0.157982] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    0.157992] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    0.158002] (II) RADEON(0): Supported VESA Video Modes:
[    0.158007] (II) RADEON(0): 720x400@70Hz
[    0.158011] (II) RADEON(0): 640x480@60Hz
[    0.158015] (II) RADEON(0): 640x480@67Hz
[    0.158019] (II) RADEON(0): 640x480@72Hz
[    0.158023] (II) RADEON(0): 640x480@75Hz
[    0.158027] (II) RADEON(0): 800x600@56Hz
[    0.158031] (II) RADEON(0): 800x600@60Hz
[    0.158035] (II) RADEON(0): 800x600@72Hz
[    0.158039] (II) RADEON(0): 800x600@75Hz
[    0.158043] (II) RADEON(0): 832x624@75Hz
[    0.158047] (II) RADEON(0): 1024x768@60Hz
[    0.158051] (II) RADEON(0): 1024x768@70Hz
[    0.158055] (II) RADEON(0): 1024x768@75Hz
[    0.158059] (II) RADEON(0): 1280x1024@75Hz
[    0.158064] (II) RADEON(0): 1152x870@75Hz
[    0.158067] (II) RADEON(0): Manufacturer's mask: 10
[    0.158072] (II) RADEON(0): Supported Future Video Modes:
[    0.158076] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    0.158081] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.158086] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.158091] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.158096] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    0.158118] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    0.158123] (II) RADEON(0): Supported additional Video Mode:
[    0.158127] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.158136] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.158144] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.158152] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    0.158161] (II) RADEON(0): Serial No: LAV0C1284022
[    0.158165] (II) RADEON(0): Monitor name: X223W  Q
[    0.158170] (II) RADEON(0): EDID (in hex):
[    0.158177] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    0.158184] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    0.158197] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    0.158210] (II) RADEON(0):     950f9040010121399030621a274068b0
[    0.158223] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    0.158236] (II) RADEON(0):     5411000a202020202020000000ff004c
[    0.158249] (II) RADEON(0):     41563043313238343032320a000000fc
[    0.158262] (II) RADEON(0):     0058323233572020510a20202020000a
finished output detect: 1
finished all detect
before xf86InitialConfiguration
[    0.161100] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
[    0.161117] (II) RADEON(0): EDID for output DVI-1
[    0.215285] (II) RADEON(0): EDID for output DVI-0
[    0.215291] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    0.215296] (II) RADEON(0): Year: 2008  Week: 21
[    0.215301] (II) RADEON(0): EDID Version: 1.3
[    0.215305] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.215315] (II) RADEON(0): Sync:  Separate
[    0.215324] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.215340] (II) RADEON(0): Gamma: 2.20
[    0.215345] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    0.215359] (II) RADEON(0): First detailed timing is preferred mode
[    0.215363] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    0.215373] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    0.215383] (II) RADEON(0): Supported VESA Video Modes:
[    0.215387] (II) RADEON(0): 720x400@70Hz
[    0.215391] (II) RADEON(0): 640x480@60Hz
[    0.215395] (II) RADEON(0): 640x480@67Hz
[    0.215399] (II) RADEON(0): 640x480@72Hz
[    0.215403] (II) RADEON(0): 640x480@75Hz
[    0.215407] (II) RADEON(0): 800x600@56Hz
[    0.215411] (II) RADEON(0): 800x600@60Hz
[    0.215415] (II) RADEON(0): 800x600@72Hz
[    0.215419] (II) RADEON(0): 800x600@75Hz
[    0.215423] (II) RADEON(0): 832x624@75Hz
[    0.215427] (II) RADEON(0): 1024x768@60Hz
[    0.215431] (II) RADEON(0): 1024x768@70Hz
[    0.215435] (II) RADEON(0): 1024x768@75Hz
[    0.215438] (II) RADEON(0): 1280x1024@75Hz
[    0.215443] (II) RADEON(0): 1152x870@75Hz
[    0.215446] (II) RADEON(0): Manufacturer's mask: 10
[    0.215450] (II) RADEON(0): Supported Future Video Modes:
[    0.215455] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    0.215460] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.215465] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.215469] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.215474] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    0.215479] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    0.215484] (II) RADEON(0): Supported additional Video Mode:
[    0.215488] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.215497] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.215504] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.215512] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    0.215519] (II) RADEON(0): Serial No: LAV0C1284022
[    0.215531] (II) RADEON(0): Monitor name: X223W  Q
[    0.215536] (II) RADEON(0): EDID (in hex):
[    0.215542] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    0.215555] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    0.215568] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    0.215581] (II) RADEON(0):     950f9040010121399030621a274068b0
[    0.215594] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    0.215607] (II) RADEON(0):     5411000a202020202020000000ff004c
[    0.215620] (II) RADEON(0):     41563043313238343032320a000000fc
[    0.215634] (II) RADEON(0):     0058323233572020510a20202020000a
[    0.215645] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    0.215649] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    0.215654] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    0.215658] (II) RADEON(0): Year: 2008  Week: 21
[    0.215663] (II) RADEON(0): EDID Version: 1.3
[    0.215667] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.215676] (II) RADEON(0): Sync:  Separate
[    0.215685] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.215696] (II) RADEON(0): Gamma: 2.20
[    0.215701] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    0.215714] (II) RADEON(0): First detailed timing is preferred mode
[    0.215718] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    0.215727] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    0.215737] (II) RADEON(0): Supported VESA Video Modes:
[    0.215741] (II) RADEON(0): 720x400@70Hz
[    0.215744] (II) RADEON(0): 640x480@60Hz
[    0.215748] (II) RADEON(0): 640x480@67Hz
[    0.215752] (II) RADEON(0): 640x480@72Hz
[    0.215756] (II) RADEON(0): 640x480@75Hz
[    0.215760] (II) RADEON(0): 800x600@56Hz
[    0.215764] (II) RADEON(0): 800x600@60Hz
[    0.215768] (II) RADEON(0): 800x600@72Hz
[    0.215772] (II) RADEON(0): 800x600@75Hz
[    0.215776] (II) RADEON(0): 832x624@75Hz
[    0.215780] (II) RADEON(0): 1024x768@60Hz
[    0.215783] (II) RADEON(0): 1024x768@70Hz
[    0.215787] (II) RADEON(0): 1024x768@75Hz
[    0.215791] (II) RADEON(0): 1280x1024@75Hz
[    0.215795] (II) RADEON(0): 1152x870@75Hz
[    0.215799] (II) RADEON(0): Manufacturer's mask: 10
[    0.215803] (II) RADEON(0): Supported Future Video Modes:
[    0.215807] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    0.215812] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.215817] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.215822] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.215826] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    0.215831] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    0.215836] (II) RADEON(0): Supported additional Video Mode:
[    0.215840] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.215848] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.215856] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.215863] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    0.215871] (II) RADEON(0): Serial No: LAV0C1284022
[    0.215875] (II) RADEON(0): Monitor name: X223W  Q
[    0.215879] (II) RADEON(0): EDID (in hex):
[    0.215886] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    0.215898] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    0.215911] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    0.215924] (II) RADEON(0):     950f9040010121399030621a274068b0
[    0.215937] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    0.215950] (II) RADEON(0):     5411000a202020202020000000ff004c
[    0.215965] (II) RADEON(0):     41563043313238343032320a000000fc
[    0.215972] (II) RADEON(0):     0058323233572020510a20202020000a
[    0.215986] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    0.216037] (II) RADEON(0): Printing probed modes for output DVI-0
[    0.216044] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    0.216054] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    0.216063] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    0.216073] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    0.216085] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    0.216097] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    0.216111] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    0.216124] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    0.216141] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    0.216153] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    0.216164] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.216176] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    0.216188] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    0.216204] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    0.216221] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.216238] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    0.216254] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    0.216271] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    0.216288] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    0.216304] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.216316] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    0.216333] (II) RADEON(0): Output DVI-1 disconnected
[    0.216338] (II) RADEON(0): Output DVI-0 connected
[    0.216346] (II) RADEON(0): Using exact sizes for initial modes
[    0.216351] (II) RADEON(0): Output DVI-0 using initial mode 1680x1050
after xf86InitialConfiguration
[    0.216378] (==) RADEON(0): DPI set to (96, 96)
[    0.216382] (II) Loading sub module "fb"
[    0.216386] (II) LoadModule: "fb"
[    0.216464] (II) Loading /usr/lib/xorg/modules//libfb.so
[    0.216628] (II) Module fb: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.4
[    0.216652] (==) RADEON(0): Using gamma correction (1.0, 1.0, 1.0)
[    0.216659] (II) Loading sub module "ramdac"
[    0.216663] (II) LoadModule: "ramdac"
[    0.216674] (II) Module "ramdac" already built-in
[    0.216679] (==) RADEON(0): Will attempt to use R6xx/R7xx EXA support if DRI is enabled.
[    0.216686] (II) Loading sub module "exa"
[    0.216691] (II) LoadModule: "exa"
[    0.216733] (II) Loading /usr/lib/xorg/modules//libexa.so
[    0.216821] (II) Module exa: vendor="X.Org Foundation"
    compiled for 1.6.0, module version = 2.4.0
    ABI class: X.Org Video Driver, version 5.0
[    0.216954] (!!) RADEON(0): For information on using the multimedia capabilities
    of this adapter, please see http://gatos.sf.net.
[    0.216976] (!!) RADEON(0): MergedFB support has been removed and replaced with xrandr 1.2 support
[    0.216984] (--) Depth 24 pixmap format is 32 bpp
[    0.216989] (II) do I need RAC?  No, I don't.
[    0.216995] (II) resource ranges after preInit:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [5] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [6] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [7] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [8] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [9] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [10] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [11] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [12] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [13] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [14] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [15] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [16] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [17] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [18] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [19] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [20] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [21] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [22] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [23] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [24] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprU)
    [25] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprU)
    [26] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprU)
    [27] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [28] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [29] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [30] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [31] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [32] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [33] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [34] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [35] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [36] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [37] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [38] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [39] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [40] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
[    0.217643] (II) RADEON(0): RADEONScreenInit d0000000 0 0
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
[    0.336821] (==) RADEON(0): Using 24 bit depth buffer
mc fb loc is 00ef00d0
[    0.336837] (II) RADEON(0): RADEONInitMemoryMap() : 
[    0.336841] (II) RADEON(0):   mem_size         : 0x20000000
[    0.336846] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0
[    0.336851] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    0.336856] (II) RADEON(0): Depth moves disabled by default
[    0.336871] (II) RADEON(0): Allocating from a screen of 262080 kb
[    0.336876] (II) RADEON(0): Will use 32 kb for hardware cursor 0 at offset 0x00af0000
[    0.336882] (II) RADEON(0): Will use 32 kb for hardware cursor 1 at offset 0x00af4000
[    0.336886] (II) RADEON(0): Will use 11200 kb for front buffer at offset 0x00000000
[    0.336942] (II) RADEON(0): Will use 64 kb for PCI GART at offset 0x0fff0000
[    0.336948] (II) RADEON(0): Will use 11200 kb for back buffer at offset 0x00af8000
[    0.336953] (II) RADEON(0): Will use 11200 kb for depth buffer at offset 0x015e8000
[    0.336958] (II) RADEON(0): Will use 113664 kb for textures at offset 0x020d8000
[    0.336963] (II) RADEON(0): Will use 114784 kb for X Server offscreen at offset 0x08fd8000
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 10, (OK)
drmOpenByBusid: drmOpenMinor returns 10
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    0.342945] (II) [drm] DRM interface version 1.3
[    0.343013] (II) [drm] DRM open master succeeded.
[    0.343032] (II) RADEON(0): [drm] Using the DRM lock SAREA also for drawables.
[    0.343039] (II) RADEON(0): [drm] framebuffer handle = 0xd0000000
[    0.343064] (II) RADEON(0): [drm] added 1 reserved context for kernel
[    0.343080] (II) RADEON(0): X context handle = 0x1
[    0.343111] (II) RADEON(0): [drm] installed DRM signal handler
[    0.358556] (II) RADEON(0): [pci] 32768 kB allocated with handle 0x104a9200
[    0.358609] (II) RADEON(0): [pci] ring handle = 0x1efff000
[    0.358628] (II) RADEON(0): [pci] Ring mapped at 0x7fc197c31000
[    0.358638] (II) RADEON(0): [pci] Ring contents 0x00000000
[    0.358645] (II) RADEON(0): [pci] ring read ptr handle = 0x2f000000
[    0.358653] (II) RADEON(0): [pci] Ring read ptr mapped at 0x7fc197d42000
[    0.358659] (II) RADEON(0): [pci] Ring read ptr contents 0x00000000
[    0.358665] (II) RADEON(0): [pci] vertex/indirect buffers handle = 0x1f000000
[    0.358684] (II) RADEON(0): [pci] Vertex/indirect buffers mapped at 0x7fc183049000
[    0.358694] (II) RADEON(0): [pci] Vertex/indirect buffers contents 0x00000000
[    0.358700] (II) RADEON(0): [pci] GART texture map handle = 0x1f001000
[    0.358706] (II) RADEON(0): [pci] GART Texture map mapped at 0x7fc1813c9000
[    0.358715] (II) RADEON(0): [drm] register handle = 0xfeaf0000
[    0.358734] (II) RADEON(0): [dri] Visual configs initialized
[    0.358823] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.358830] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ff00e0
[    0.358835] (II) RADEON(0):   MC_AGP_LOCATION  : 0x003f0000
[    0.368924] (==) RADEON(0): Backing store disabled
[    0.368940] (II) RADEON(0): [DRI] installation complete
[    0.391920] (II) RADEON(0): [drm] Added 32 65536 byte vertex/indirect buffers
[    0.391947] (II) RADEON(0): [drm] Mapped 32 vertex/indirect buffers
[    0.392002] (II) RADEON(0): [drm] dma control initialized, using IRQ 18
[    0.392009] (II) RADEON(0): [drm] Initialized kernel GART heap manager, 29884416
[    0.392027] (WW) RADEON(0): DRI init changed memory map, adjusting ...
[    0.392033] (WW) RADEON(0):   MC_FB_LOCATION  was: 0x00ef00d0 is: 0x00ef00d0
[    0.392038] (WW) RADEON(0):   MC_AGP_LOCATION was: 0x003f0000 is: 0x00030000
[    0.392045] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.392049] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ef00d0
[    0.392054] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00030000
[    0.392062] (II) RADEON(0): Direct rendering enabled
[    0.392072] (II) RADEON(0): Setting EXA maxPitchBytes
[    0.392095] (II) EXA(0): Offscreen pixmap area of 117538816 bytes
[    0.392105] (II) EXA(0): Driver registered support for the following operations:
[    0.392110] (II)         Solid
[    0.392114] (II)         Copy
[    0.392118] (II)         Composite (RENDER acceleration)
[    0.392122] (II)         UploadToScreen
[    0.392126] (II)         DownloadFromScreen
[    0.392140] (II) RADEON(0): Acceleration enabled
[    0.392148] (II) RADEON(0): DPMS enabled
[    0.392156] (==) RADEON(0): Silken mouse enabled
[    0.392238] (II) RADEON(0): Set up textured video
Output DIG dpms success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
Output CRT1 disable success
Blank CRTC 0 success
Disable CRTC 0 success
Disable CRTC memreq 0 success
Mode 1680x1050 - 2240 1089 10
[    0.392495] (II) RADEON(0): RADEONRestoreMemMapRegisters() : 
[    0.392500] (II) RADEON(0):   MC_FB_LOCATION   : 0x00ef00d0 0x00ef00d0
[    0.392505] (II) RADEON(0):   MC_AGP_LOCATION  : 0x00030000
freq: 146250000
best_freq: 146250000
best_feedback_div: 65
best_ref_div: 2
best_post_div: 6
[    0.394135] (II) RADEON(0): crtc(0) Clock: mode 146250, PLL 146250
[    0.394140] (II) RADEON(0): crtc(0) PLL  : refdiv 2, fbdiv 0x41(65), pdiv 6
Set CRTC 0 PLL success
Set CRTC Timing success
Set CRTC 0 Overscan success
Not using RMX
scaler 0 setup success
Set CRTC 0 Source success
crtc 0 YUV disable setup success
Output DAC1 setup success
Output CRT1 enable success
Enable CRTC memreq 0 success
Enable CRTC 0 success
Unblank CRTC 0 success
Output DIG dpms success
Blank CRTC 1 success
Disable CRTC 1 success
Disable CRTC memreq 1 success
[    0.397324] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
Lock CRTC 0 success
Unlock CRTC 0 success
[    0.397599] (--) RandR disabled
[    0.412879] (II) Initializing built-in extension Generic Event Extension
[    0.412892] (II) Initializing built-in extension SHAPE
[    0.412896] (II) Initializing built-in extension MIT-SHM
[    0.412900] (II) Initializing built-in extension XInputExtension
[    0.412904] (II) Initializing built-in extension XTEST
[    0.412909] (II) Initializing built-in extension BIG-REQUESTS
[    0.412913] (II) Initializing built-in extension SYNC
[    0.412917] (II) Initializing built-in extension XKEYBOARD
[    0.412921] (II) Initializing built-in extension XC-MISC
[    0.412924] (II) Initializing built-in extension SECURITY
[    0.412928] (II) Initializing built-in extension XINERAMA
[    0.412932] (II) Initializing built-in extension XFIXES
[    0.412936] (II) Initializing built-in extension RENDER
[    0.412940] (II) Initializing built-in extension RANDR
[    0.412944] (II) Initializing built-in extension COMPOSITE
[    0.412948] (II) Initializing built-in extension DAMAGE
[    0.420812] (II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 11, (OK)
drmOpenByBusid: drmOpenMinor returns 11
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
[    0.427620] (EE) AIGLX error: Calling driver entry point failed[    0.429178] (EE) AIGLX: reverting to software rendering
[    0.437985] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
[    0.437997] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    0.438366] (II) RADEON(0): Setting screen physical size to 474 x 296
[    0.565007] (II) config/hal: Adding input device AT Translated Set 2 keyboard
[    0.565037] (II) LoadModule: "evdev"
[    0.565156] (II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
[    0.565280] (II) Module evdev: vendor="X.Org Foundation"
    compiled for 1.5.99.902, module version = 2.1.1
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 4.0
[    0.565335] (**) AT Translated Set 2 keyboard: always reports core events
[    0.565344] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    0.584024] (II) AT Translated Set 2 keyboard: Found keys
[    0.584038] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    0.584072] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    0.584112] (**) Option "xkb_rules" "evdev"
[    0.584132] (**) AT Translated Set 2 keyboard: xkb_rules: "evdev"
[    0.584146] (**) Option "xkb_model" "pc105"
[    0.584166] (**) AT Translated Set 2 keyboard: xkb_model: "pc105"
[    0.584178] (**) Option "xkb_layout" "rs"
[    0.584197] (**) AT Translated Set 2 keyboard: xkb_layout: "rs"
[    0.584211] (**) Option "xkb_variant" "latin"
[    0.584230] (**) AT Translated Set 2 keyboard: xkb_variant: "latin"
[    0.584242] (**) Option "xkb_options" "grp:alts_toggle,grp:sclk_toggle,grp_led:scroll"
[    0.584265] (**) AT Translated Set 2 keyboard: xkb_options: "grp:alts_toggle,grp:sclk_toggle,grp_led:scroll"
[    0.685447] (II) config/hal: Adding input device Macintosh mouse button emulation
[    0.685519] (**) Macintosh mouse button emulation: always reports core events
[    0.685535] (**) Macintosh mouse button emulation: Device: "/dev/input/event2"
[    0.703008] (II) Macintosh mouse button emulation: Found 3 mouse buttons
[    0.703027] (II) Macintosh mouse button emulation: Found x and y relative axes
[    0.703036] (II) Macintosh mouse button emulation: Configuring as mouse
[    0.703058] (**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    0.703094] (**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    0.703126] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
[    0.703183] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    0.703196] (**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
[    0.703213] (**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
[    0.703234] (**) Macintosh mouse button emulation: (accel) set acceleration profile 0
[    0.706205] (II) config/hal: Adding input device ImPS/2 Generic Wheel Mouse
[    0.706418] (**) ImPS/2 Generic Wheel Mouse: always reports core events
[    0.706443] (**) ImPS/2 Generic Wheel Mouse: Device: "/dev/input/event5"
[    0.715002] (II) ImPS/2 Generic Wheel Mouse: Found 3 mouse buttons
[    0.715017] (II) ImPS/2 Generic Wheel Mouse: Found x and y relative axes
[    0.715028] (II) ImPS/2 Generic Wheel Mouse: Configuring as mouse
[    0.715049] (**) ImPS/2 Generic Wheel Mouse: YAxisMapping: buttons 4 and 5
[    0.715061] (**) ImPS/2 Generic Wheel Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    0.715084] (II) XINPUT: Adding extended input device "ImPS/2 Generic Wheel Mouse" (type: MOUSE)
[    0.715129] (**) ImPS/2 Generic Wheel Mouse: (accel) keeping acceleration scheme 1
[    0.715140] (**) ImPS/2 Generic Wheel Mouse: (accel) filter chain progression: 2.00
[    0.715158] (**) ImPS/2 Generic Wheel Mouse: (accel) filter stage 0: 20.00 ms
[    0.715178] (**) ImPS/2 Generic Wheel Mouse: (accel) set acceleration profile 0
[    0.764008] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
[    0.764067] (II) RADEON(0): EDID for output DVI-1
[    0.819085] (II) RADEON(0): EDID for output DVI-0
[    0.819092] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    0.819098] (II) RADEON(0): Year: 2008  Week: 21
[    0.819103] (II) RADEON(0): EDID Version: 1.3
[    0.819108] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.819119] (II) RADEON(0): Sync:  Separate
[    0.819128] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.819137] (II) RADEON(0): Gamma: 2.20
[    0.819147] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    0.819160] (II) RADEON(0): First detailed timing is preferred mode
[    0.819165] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    0.819176] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    0.819187] (II) RADEON(0): Supported VESA Video Modes:
[    0.819191] (II) RADEON(0): 720x400@70Hz
[    0.819195] (II) RADEON(0): 640x480@60Hz
[    0.819199] (II) RADEON(0): 640x480@67Hz
[    0.819203] (II) RADEON(0): 640x480@72Hz
[    0.819207] (II) RADEON(0): 640x480@75Hz
[    0.819211] (II) RADEON(0): 800x600@56Hz
[    0.819215] (II) RADEON(0): 800x600@60Hz
[    0.819219] (II) RADEON(0): 800x600@72Hz
[    0.819223] (II) RADEON(0): 800x600@75Hz
[    0.819226] (II) RADEON(0): 832x624@75Hz
[    0.819230] (II) RADEON(0): 1024x768@60Hz
[    0.819234] (II) RADEON(0): 1024x768@70Hz
[    0.819238] (II) RADEON(0): 1024x768@75Hz
[    0.819242] (II) RADEON(0): 1280x1024@75Hz
[    0.819247] (II) RADEON(0): 1152x870@75Hz
[    0.819251] (II) RADEON(0): Manufacturer's mask: 10
[    0.819255] (II) RADEON(0): Supported Future Video Modes:
[    0.819260] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    0.819265] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.819270] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.819275] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.819280] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    0.819285] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    0.819290] (II) RADEON(0): Supported additional Video Mode:
[    0.819315] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.819326] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.819334] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.819342] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    0.819351] (II) RADEON(0): Serial No: LAV0C1284022
[    0.819355] (II) RADEON(0): Monitor name: X223W  Q
[    0.819359] (II) RADEON(0): EDID (in hex):
[    0.819367] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    0.819375] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    0.819386] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    0.819399] (II) RADEON(0):     950f9040010121399030621a274068b0
[    0.819412] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    0.819425] (II) RADEON(0):     5411000a202020202020000000ff004c
[    0.819438] (II) RADEON(0):     41563043313238343032320a000000fc
[    0.819451] (II) RADEON(0):     0058323233572020510a20202020000a
[    0.819467] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    0.819501] (II) RADEON(0): Using EDID range info for horizontal sync
[    0.819505] (II) RADEON(0): Using EDID range info for vertical refresh
[    0.819510] (II) RADEON(0): Printing DDC gathered Modelines:
[    0.819515] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    0.819526] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.819535] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    0.819544] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    0.819562] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    0.819570] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    0.819587] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.819604] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    0.819620] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    0.819630] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    0.819646] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    0.819663] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.819680] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    0.819696] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    0.819713] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    0.819729] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    0.819745] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    0.819762] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    0.819778] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    0.819790] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    0.819806] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    0.819823] (II) RADEON(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    0.819854] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    0.819859] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    0.819864] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    0.819869] (II) RADEON(0): Year: 2008  Week: 21
[    0.819874] (II) RADEON(0): EDID Version: 1.3
[    0.819878] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    0.819888] (II) RADEON(0): Sync:  Separate
[    0.819897] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    0.819913] (II) RADEON(0): Gamma: 2.20
[    0.819918] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    0.819931] (II) RADEON(0): First detailed timing is preferred mode
[    0.819936] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    0.819948] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    0.819960] (II) RADEON(0): Supported VESA Video Modes:
[    0.819965] (II) RADEON(0): 720x400@70Hz
[    0.819969] (II) RADEON(0): 640x480@60Hz
[    0.819973] (II) RADEON(0): 640x480@67Hz
[    0.819977] (II) RADEON(0): 640x480@72Hz
[    0.819981] (II) RADEON(0): 640x480@75Hz
[    0.819984] (II) RADEON(0): 800x600@56Hz
[    0.819988] (II) RADEON(0): 800x600@60Hz
[    0.819992] (II) RADEON(0): 800x600@72Hz
[    0.819996] (II) RADEON(0): 800x600@75Hz
[    0.820000] (II) RADEON(0): 832x624@75Hz
[    0.820003] (II) RADEON(0): 1024x768@60Hz
[    0.820007] (II) RADEON(0): 1024x768@70Hz
[    0.820011] (II) RADEON(0): 1024x768@75Hz
[    0.820015] (II) RADEON(0): 1280x1024@75Hz
[    0.820019] (II) RADEON(0): 1152x870@75Hz
[    0.820023] (II) RADEON(0): Manufacturer's mask: 10
[    0.820027] (II) RADEON(0): Supported Future Video Modes:
[    0.820032] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    0.820037] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    0.820042] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    0.820047] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    0.820052] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    0.820056] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    0.820061] (II) RADEON(0): Supported additional Video Mode:
[    0.820066] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    0.820077] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    0.820086] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    0.820093] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    0.820101] (II) RADEON(0): Serial No: LAV0C1284022
[    0.820105] (II) RADEON(0): Monitor name: X223W  Q
[    0.820109] (II) RADEON(0): EDID (in hex):
[    0.820116] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    0.820129] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    0.820142] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    0.820156] (II) RADEON(0):     950f9040010121399030621a274068b0
[    0.820168] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    0.820181] (II) RADEON(0):     5411000a202020202020000000ff004c
[    0.820194] (II) RADEON(0):     41563043313238343032320a000000fc
[    0.820207] (II) RADEON(0):     0058323233572020510a20202020000a
[    0.820219] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    0.820254] (II) RADEON(0): Printing probed modes for output DVI-0
[    0.820259] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    0.820269] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    0.820280] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    0.820289] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    0.820301] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    0.820318] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    0.820335] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    0.820343] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    0.820360] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    0.820368] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    0.820385] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    0.820402] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    0.820414] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    0.820430] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    0.820447] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    0.820464] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    0.820478] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    0.820494] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    0.820506] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    0.820523] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    0.820540] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
exaCopyDirty: Pending damage region empty!
[    9.541362] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
[    9.541396] (II) RADEON(0): EDID for output DVI-1
[    9.595445] (II) RADEON(0): EDID for output DVI-0
[    9.595452] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    9.595458] (II) RADEON(0): Year: 2008  Week: 21
[    9.595463] (II) RADEON(0): EDID Version: 1.3
[    9.595469] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    9.595479] (II) RADEON(0): Sync:  Separate
[    9.595489] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    9.595499] (II) RADEON(0): Gamma: 2.20
[    9.595509] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    9.595524] (II) RADEON(0): First detailed timing is preferred mode
[    9.595529] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    9.595540] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    9.595551] (II) RADEON(0): Supported VESA Video Modes:
[    9.595555] (II) RADEON(0): 720x400@70Hz
[    9.595559] (II) RADEON(0): 640x480@60Hz
[    9.595564] (II) RADEON(0): 640x480@67Hz
[    9.595568] (II) RADEON(0): 640x480@72Hz
[    9.595572] (II) RADEON(0): 640x480@75Hz
[    9.595576] (II) RADEON(0): 800x600@56Hz
[    9.595579] (II) RADEON(0): 800x600@60Hz
[    9.595584] (II) RADEON(0): 800x600@72Hz
[    9.595587] (II) RADEON(0): 800x600@75Hz
[    9.595591] (II) RADEON(0): 832x624@75Hz
[    9.595595] (II) RADEON(0): 1024x768@60Hz
[    9.595600] (II) RADEON(0): 1024x768@70Hz
[    9.595603] (II) RADEON(0): 1024x768@75Hz
[    9.595608] (II) RADEON(0): 1280x1024@75Hz
[    9.595612] (II) RADEON(0): 1152x870@75Hz
[    9.595615] (II) RADEON(0): Manufacturer's mask: 10
[    9.595620] (II) RADEON(0): Supported Future Video Modes:
[    9.595624] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    9.595630] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    9.595655] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    9.595660] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    9.595665] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    9.595670] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    9.595675] (II) RADEON(0): Supported additional Video Mode:
[    9.595680] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    9.595690] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    9.595698] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    9.595706] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    9.595714] (II) RADEON(0): Serial No: LAV0C1284022
[    9.595719] (II) RADEON(0): Monitor name: X223W  Q
[    9.595724] (II) RADEON(0): EDID (in hex):
[    9.595731] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    9.595738] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    9.595752] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    9.595758] (II) RADEON(0):     950f9040010121399030621a274068b0
[    9.595771] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    9.595778] (II) RADEON(0):     5411000a202020202020000000ff004c
[    9.595791] (II) RADEON(0):     41563043313238343032320a000000fc
[    9.595798] (II) RADEON(0):     0058323233572020510a20202020000a
[    9.595809] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    9.595840] (II) RADEON(0): Using hsync ranges from config file
[    9.595845] (II) RADEON(0): Using vrefresh ranges from config file
[    9.595849] (II) RADEON(0): Printing DDC gathered Modelines:
[    9.595855] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    9.595865] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    9.595875] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    9.595884] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    9.595892] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    9.595900] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    9.595908] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    9.595918] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    9.595926] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    9.595935] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    9.595943] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    9.595952] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    9.595960] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    9.595972] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    9.595984] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    9.596001] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    9.596017] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    9.596026] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    9.596042] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    9.596077] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    9.596086] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    9.596095] (II) RADEON(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    9.596109] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    9.596114] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    9.596119] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    9.596124] (II) RADEON(0): Year: 2008  Week: 21
[    9.596128] (II) RADEON(0): EDID Version: 1.3
[    9.596133] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    9.596143] (II) RADEON(0): Sync:  Separate
[    9.596151] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    9.596163] (II) RADEON(0): Gamma: 2.20
[    9.596168] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    9.596181] (II) RADEON(0): First detailed timing is preferred mode
[    9.596186] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    9.596195] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    9.596208] (II) RADEON(0): Supported VESA Video Modes:
[    9.596212] (II) RADEON(0): 720x400@70Hz
[    9.596216] (II) RADEON(0): 640x480@60Hz
[    9.596220] (II) RADEON(0): 640x480@67Hz
[    9.596224] (II) RADEON(0): 640x480@72Hz
[    9.596228] (II) RADEON(0): 640x480@75Hz
[    9.596232] (II) RADEON(0): 800x600@56Hz
[    9.596236] (II) RADEON(0): 800x600@60Hz
[    9.596240] (II) RADEON(0): 800x600@72Hz
[    9.596244] (II) RADEON(0): 800x600@75Hz
[    9.596248] (II) RADEON(0): 832x624@75Hz
[    9.596251] (II) RADEON(0): 1024x768@60Hz
[    9.596255] (II) RADEON(0): 1024x768@70Hz
[    9.596259] (II) RADEON(0): 1024x768@75Hz
[    9.596263] (II) RADEON(0): 1280x1024@75Hz
[    9.596267] (II) RADEON(0): 1152x870@75Hz
[    9.596271] (II) RADEON(0): Manufacturer's mask: 10
[    9.596275] (II) RADEON(0): Supported Future Video Modes:
[    9.596279] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    9.596285] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    9.596290] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    9.596294] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    9.596299] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    9.596304] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    9.596309] (II) RADEON(0): Supported additional Video Mode:
[    9.596313] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    9.596321] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    9.596329] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    9.596336] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    9.596344] (II) RADEON(0): Serial No: LAV0C1284022
[    9.596348] (II) RADEON(0): Monitor name: X223W  Q
[    9.596353] (II) RADEON(0): EDID (in hex):
[    9.596359] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    9.596372] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    9.596385] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    9.596398] (II) RADEON(0):     950f9040010121399030621a274068b0
[    9.596405] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    9.596418] (II) RADEON(0):     5411000a202020202020000000ff004c
[    9.596424] (II) RADEON(0):     41563043313238343032320a000000fc
[    9.596437] (II) RADEON(0):     0058323233572020510a20202020000a
[    9.596442] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    9.596475] (II) RADEON(0): Printing probed modes for output DVI-0
[    9.596481] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    9.596494] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    9.596514] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    9.596526] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    9.596538] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    9.596547] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    9.596564] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    9.596578] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    9.596586] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    9.596603] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    9.596614] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    9.596626] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    9.596643] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    9.596659] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    9.596676] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    9.596693] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    9.596709] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    9.596726] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    9.596734] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    9.596751] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    9.596767] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    9.601039] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
[    9.601088] (II) RADEON(0): EDID for output DVI-1
[    9.656308] (II) RADEON(0): EDID for output DVI-0
[    9.656321] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    9.656331] (II) RADEON(0): Year: 2008  Week: 21
[    9.656343] (II) RADEON(0): EDID Version: 1.3
[    9.656355] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    9.656374] (II) RADEON(0): Sync:  Separate
[    9.656401] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    9.656424] (II) RADEON(0): Gamma: 2.20
[    9.656440] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    9.656470] (II) RADEON(0): First detailed timing is preferred mode
[    9.656479] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    9.656503] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    9.656525] (II) RADEON(0): Supported VESA Video Modes:
[    9.656536] (II) RADEON(0): 720x400@70Hz
[    9.656545] (II) RADEON(0): 640x480@60Hz
[    9.656556] (II) RADEON(0): 640x480@67Hz
[    9.656564] (II) RADEON(0): 640x480@72Hz
[    9.656571] (II) RADEON(0): 640x480@75Hz
[    9.656579] (II) RADEON(0): 800x600@56Hz
[    9.656587] (II) RADEON(0): 800x600@60Hz
[    9.656598] (II) RADEON(0): 800x600@72Hz
[    9.656610] (II) RADEON(0): 800x600@75Hz
[    9.656617] (II) RADEON(0): 832x624@75Hz
[    9.656629] (II) RADEON(0): 1024x768@60Hz
[    9.656637] (II) RADEON(0): 1024x768@70Hz
[    9.656644] (II) RADEON(0): 1024x768@75Hz
[    9.656688] (II) RADEON(0): 1280x1024@75Hz
[    9.656701] (II) RADEON(0): 1152x870@75Hz
[    9.656717] (II) RADEON(0): Manufacturer's mask: 10
[    9.656729] (II) RADEON(0): Supported Future Video Modes:
[    9.656739] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    9.656759] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    9.656771] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    9.656789] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    9.656799] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    9.656811] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    9.656823] (II) RADEON(0): Supported additional Video Mode:
[    9.656832] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    9.656857] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    9.656873] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    9.656888] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    9.656904] (II) RADEON(0): Serial No: LAV0C1284022
[    9.656912] (II) RADEON(0): Monitor name: X223W  Q
[    9.656929] (II) RADEON(0): EDID (in hex):
[    9.656948] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    9.656964] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    9.656980] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    9.656997] (II) RADEON(0):     950f9040010121399030621a274068b0
[    9.657011] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    9.657027] (II) RADEON(0):     5411000a202020202020000000ff004c
[    9.657039] (II) RADEON(0):     41563043313238343032320a000000fc
[    9.657052] (II) RADEON(0):     0058323233572020510a20202020000a
[    9.657064] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    9.657123] (II) RADEON(0): Using hsync ranges from config file
[    9.657131] (II) RADEON(0): Using vrefresh ranges from config file
[    9.657142] (II) RADEON(0): Printing DDC gathered Modelines:
[    9.657161] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    9.657184] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    9.657206] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    9.657223] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    9.657245] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    9.657262] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    9.657282] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    9.657299] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    9.657319] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    9.657343] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    9.657361] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    9.657382] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    9.657401] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    9.657422] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    9.657443] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    9.657464] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    9.657501] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    9.657521] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    9.657539] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    9.657558] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    9.657574] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    9.657590] (II) RADEON(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    9.657618] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    9.657628] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    9.657640] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    9.657651] (II) RADEON(0): Year: 2008  Week: 21
[    9.657663] (II) RADEON(0): EDID Version: 1.3
[    9.657675] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    9.657701] (II) RADEON(0): Sync:  Separate
[    9.657726] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    9.657747] (II) RADEON(0): Gamma: 2.20
[    9.657757] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    9.657793] (II) RADEON(0): First detailed timing is preferred mode
[    9.657805] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    9.657833] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    9.657859] (II) RADEON(0): Supported VESA Video Modes:
[    9.657875] (II) RADEON(0): 720x400@70Hz
[    9.657885] (II) RADEON(0): 640x480@60Hz
[    9.657897] (II) RADEON(0): 640x480@67Hz
[    9.657911] (II) RADEON(0): 640x480@72Hz
[    9.657922] (II) RADEON(0): 640x480@75Hz
[    9.657934] (II) RADEON(0): 800x600@56Hz
[    9.657946] (II) RADEON(0): 800x600@60Hz
[    9.657957] (II) RADEON(0): 800x600@72Hz
[    9.657964] (II) RADEON(0): 800x600@75Hz
[    9.657976] (II) RADEON(0): 832x624@75Hz
[    9.657983] (II) RADEON(0): 1024x768@60Hz
[    9.657999] (II) RADEON(0): 1024x768@70Hz
[    9.658007] (II) RADEON(0): 1024x768@75Hz
[    9.658019] (II) RADEON(0): 1280x1024@75Hz
[    9.658037] (II) RADEON(0): 1152x870@75Hz
[    9.658045] (II) RADEON(0): Manufacturer's mask: 10
[    9.658057] (II) RADEON(0): Supported Future Video Modes:
[    9.658068] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    9.658081] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    9.658090] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    9.658103] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    9.658112] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    9.658124] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    9.658140] (II) RADEON(0): Supported additional Video Mode:
[    9.658148] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    9.658174] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    9.658194] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    9.658212] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    9.658233] (II) RADEON(0): Serial No: LAV0C1284022
[    9.658249] (II) RADEON(0): Monitor name: X223W  Q
[    9.658257] (II) RADEON(0): EDID (in hex):
[    9.658278] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    9.658294] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    9.658310] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    9.658323] (II) RADEON(0):     950f9040010121399030621a274068b0
[    9.658339] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    9.658354] (II) RADEON(0):     5411000a202020202020000000ff004c
[    9.658367] (II) RADEON(0):     41563043313238343032320a000000fc
[    9.658397] (II) RADEON(0):     0058323233572020510a20202020000a
[    9.658411] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    9.658471] (II) RADEON(0): Printing probed modes for output DVI-0
[    9.658489] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    9.658507] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    9.658526] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    9.658546] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    9.658566] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    9.658585] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    9.658604] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    9.658623] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    9.658642] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    9.658666] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    9.658685] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    9.658704] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    9.658721] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    9.658736] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    9.658755] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    9.658774] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    9.658792] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    9.658811] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    9.658829] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    9.658845] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    9.658862] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    9.662614] (II) RADEON(0): Output: DVI-1, Detected Monitor Type: 0
invalid output device for dac detection
[    9.662646] (II) RADEON(0): EDID for output DVI-1
[    9.717261] (II) RADEON(0): EDID for output DVI-0
[    9.717270] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    9.717275] (II) RADEON(0): Year: 2008  Week: 21
[    9.717279] (II) RADEON(0): EDID Version: 1.3
[    9.717283] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    9.717293] (II) RADEON(0): Sync:  Separate
[    9.717301] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    9.717317] (II) RADEON(0): Gamma: 2.20
[    9.717326] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    9.717339] (II) RADEON(0): First detailed timing is preferred mode
[    9.717343] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    9.717356] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    9.717368] (II) RADEON(0): Supported VESA Video Modes:
[    9.717373] (II) RADEON(0): 720x400@70Hz
[    9.717377] (II) RADEON(0): 640x480@60Hz
[    9.717381] (II) RADEON(0): 640x480@67Hz
[    9.717385] (II) RADEON(0): 640x480@72Hz
[    9.717389] (II) RADEON(0): 640x480@75Hz
[    9.717401] (II) RADEON(0): 800x600@56Hz
[    9.717405] (II) RADEON(0): 800x600@60Hz
[    9.717409] (II) RADEON(0): 800x600@72Hz
[    9.717413] (II) RADEON(0): 800x600@75Hz
[    9.717417] (II) RADEON(0): 832x624@75Hz
[    9.717421] (II) RADEON(0): 1024x768@60Hz
[    9.717425] (II) RADEON(0): 1024x768@70Hz
[    9.717429] (II) RADEON(0): 1024x768@75Hz
[    9.717433] (II) RADEON(0): 1280x1024@75Hz
[    9.717437] (II) RADEON(0): 1152x870@75Hz
[    9.717441] (II) RADEON(0): Manufacturer's mask: 10
[    9.717445] (II) RADEON(0): Supported Future Video Modes:
[    9.717450] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    9.717455] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    9.717460] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    9.717464] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    9.717469] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    9.717474] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    9.717478] (II) RADEON(0): Supported additional Video Mode:
[    9.717482] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    9.717494] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    9.717502] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    9.717509] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    9.717517] (II) RADEON(0): Serial No: LAV0C1284022
[    9.717521] (II) RADEON(0): Monitor name: X223W  Q
[    9.717526] (II) RADEON(0): EDID (in hex):
[    9.717533] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    9.717545] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    9.717557] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    9.717566] (II) RADEON(0):     950f9040010121399030621a274068b0
[    9.717574] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    9.717588] (II) RADEON(0):     5411000a202020202020000000ff004c
[    9.717601] (II) RADEON(0):     41563043313238343032320a000000fc
[    9.717607] (II) RADEON(0):     0058323233572020510a20202020000a
[    9.717612] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    9.717636] (II) RADEON(0): Using hsync ranges from config file
[    9.717641] (II) RADEON(0): Using vrefresh ranges from config file
[    9.717645] (II) RADEON(0): Printing DDC gathered Modelines:
[    9.717650] (II) RADEON(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    9.717662] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    9.717673] (II) RADEON(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    9.717682] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    9.717698] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    9.717715] (II) RADEON(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    9.717731] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    9.717748] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[    9.717758] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    9.717769] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    9.717784] (II) RADEON(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    9.717795] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    9.717812] (II) RADEON(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    9.717824] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    9.717844] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    9.717856] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    9.717872] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    9.717881] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    9.717897] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    9.717913] (II) RADEON(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    9.717930] (II) RADEON(0): Modeline "1440x900"x0.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    9.717946] (II) RADEON(0): Modeline "1400x1050"x0.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    9.717965] (II) RADEON(0): Output: DVI-0, Detected Monitor Type: 1
[    9.717970] (II) RADEON(0): EDID data from the display on output: DVI-0 ----------------------
[    9.717975] (II) RADEON(0): Manufacturer: ACR  Model: d  Serial#: 2182127395
[    9.717980] (II) RADEON(0): Year: 2008  Week: 21
[    9.717984] (II) RADEON(0): EDID Version: 1.3
[    9.717988] (II) RADEON(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[    9.717998] (II) RADEON(0): Sync:  Separate
[    9.718006] (II) RADEON(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[    9.718015] (II) RADEON(0): Gamma: 2.20
[    9.718020] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off; RGB/Color Display
[    9.718034] (II) RADEON(0): First detailed timing is preferred mode
[    9.718038] (II) RADEON(0): redX: 0.640 redY: 0.329   greenX: 0.300 greenY: 0.600
[    9.718047] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    9.718059] (II) RADEON(0): Supported VESA Video Modes:
[    9.718063] (II) RADEON(0): 720x400@70Hz
[    9.718068] (II) RADEON(0): 640x480@60Hz
[    9.718072] (II) RADEON(0): 640x480@67Hz
[    9.718076] (II) RADEON(0): 640x480@72Hz
[    9.718080] (II) RADEON(0): 640x480@75Hz
[    9.718084] (II) RADEON(0): 800x600@56Hz
[    9.718088] (II) RADEON(0): 800x600@60Hz
[    9.718092] (II) RADEON(0): 800x600@72Hz
[    9.718096] (II) RADEON(0): 800x600@75Hz
[    9.718100] (II) RADEON(0): 832x624@75Hz
[    9.718104] (II) RADEON(0): 1024x768@60Hz
[    9.718108] (II) RADEON(0): 1024x768@70Hz
[    9.718111] (II) RADEON(0): 1024x768@75Hz
[    9.718115] (II) RADEON(0): 1280x1024@75Hz
[    9.718119] (II) RADEON(0): 1152x870@75Hz
[    9.718123] (II) RADEON(0): Manufacturer's mask: 10
[    9.718127] (II) RADEON(0): Supported Future Video Modes:
[    9.718132] (II) RADEON(0): #0: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[    9.718137] (II) RADEON(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    9.718141] (II) RADEON(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[    9.718146] (II) RADEON(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[    9.718151] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 75  vid: 3989
[    9.718155] (II) RADEON(0): #6: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[    9.718160] (II) RADEON(0): Supported additional Video Mode:
[    9.718164] (II) RADEON(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[    9.718176] (II) RADEON(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[    9.718183] (II) RADEON(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[    9.718191] (II) RADEON(0): Ranges: V min: 56 V max: 77 Hz, H min: 31 H max: 84 kHz, PixClock max 170 MHz
[    9.718199] (II) RADEON(0): Serial No: LAV0C1284022
[    9.718203] (II) RADEON(0): Monitor name: X223W  Q
[    9.718207] (II) RADEON(0): EDID (in hex):
[    9.718213] (II) RADEON(0):     00ffffffffffff0004720d00239f1082
[    9.718226] (II) RADEON(0):     15120103082f1e78eade95a3544c9926
[    9.718241] (II) RADEON(0):     0f5054bfef90a940714f814001019500
[    9.718253] (II) RADEON(0):     950f9040010121399030621a274068b0
[    9.718266] (II) RADEON(0):     3600da2811000019000000fd00384d1f
[    9.718275] (II) RADEON(0):     5411000a202020202020000000ff004c
[    9.718287] (II) RADEON(0):     41563043313238343032320a000000fc
[    9.718295] (II) RADEON(0):     0058323233572020510a20202020000a
[    9.718306] (II) RADEON(0): EDID vendor "ACR", prod id 13
[    9.718338] (II) RADEON(0): Printing probed modes for output DVI-0
[    9.718344] (II) RADEON(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync -vsync (65.3 kHz)
[    9.718356] (II) RADEON(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[    9.718367] (II) RADEON(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz)
[    9.718379] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[    9.718391] (II) RADEON(0): Modeline "1440x900"x75.0  136.75  1440 1536 1688 1936  900 903 909 942 -hsync +vsync (70.6 kHz)
[    9.718399] (II) RADEON(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz)
[    9.718416] (II) RADEON(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[    9.718433] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[    9.718449] (II) RADEON(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[    9.718466] (II) RADEON(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[    9.718483] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[    9.718499] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[    9.718516] (II) RADEON(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[    9.718524] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[    9.718541] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[    9.718553] (II) RADEON(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[    9.718570] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[    9.718586] (II) RADEON(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[    9.718602] (II) RADEON(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[    9.718617] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[    9.718629] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
```

---

### Post by Bert Mariën on 2009-03-21
> **bardu said:**
> Hi there,

Ubuntu 8.10 freezes after booting from CD on my new Toshiba A350 64 bit with ATI Mobility Radeon HD 3650  graphics card.

In the hope Ubuntu 9.04 alpha 4 will include the newest driver from freedesktop.org, which include, to my knowledge, a driver for my graphics card, I download alpha 4. After booting from CD I get the message 


The same happens with the boot option xdriver=vesa.
 
So, it seem to me there is still no support for ATI Mobility Radeon HD 3650.

Can someone shed some light on that?

Thanks,
Stephan

The problem is well known.
Read this:
[http://www.phoronix.com/vr.php?view=13559](http://www.phoronix.com/vr.php?view=13559)

---

### Post by laxdad8992 on 2009-03-25
Has anyone reported the 4G/2G question to the Xorg people? I would think that should give them a pretty good clue about the issue. I am experiencing a bit of trepidation about opening up the laptop to take out the memory (warranty-wise). Also, it bothers me that I looked specifically for a machine that had 4G to give it some "snap".

---

### Post by shelvingguy on 2009-03-25
I have been battling with this issue for about 2 months.  I just recently found out about the 2G/4G "resolution"--which I am still using to run Ubuntu.  

Up until the RAM deal came to light, it seemed people were engaged with the issue.  In the last couple of weeks, it seems that the ATI driver issue has fallen off of the radar.  There have been fewer responses to posts and bugs.

I have not seen anyone answer the question of why the ATI driver works with one RAM module removed.

---

### Post by laxdad8992 on 2009-03-25
Well, now I tried removing a memory module, and viola! I have finally gotten this thing to run with the open source radeonhd driver in the native screen resolution (1366x768). To whoever first discovered this, a huge THANK YOU. I have not tried games, etc, but for now having the screen look right (far better than vesa) is quite nice.

I still want to know if/when xorg will look into why the extra memory causes it to hang...

---

### Post by markbuntu on 2009-03-27
I just looked at the ati driver release notes and the mobility HD3650 is conspicously absent from the list of supported cards/chips for their proprietary linux driver fglrx. Hmmm...

---

### Post by bardu on 2009-03-27
For those who don't want to remove 2G of RAM could try downloading [http://www.virtualbox.org]("http://www.virtualbox.org"), split the memory equally to 2G and run Ubuntu 9.04 Beta as guest OS on Windows Vista.

Toshiba A350, with all its power, is just asking for virtualization, but I had to learn that it is not supporting it. There are no settings in the BIOS to turn on/off virtualization. And VirtualBox can't install Ubuntu for that reason.

Ubuntu 9.04 BETA freezes after booting on Toshiba A350 with a blank screen, as mentioned early in this thread, and there is no way to submit the Xorg.0.log.

I still hope the Xorg team can fix this issue soon.

---

### Post by factotum218 on 2009-03-28
> **bardu said:**
> For those who don't want to remove 2G of RAM could try downloading [http://www.virtualbox.org]("http://www.virtualbox.org"), split the memory equally to 2G and run Ubuntu 9.04 Beta as guest OS on Windows Vista.

Toshiba A350, with all its power, is just asking for virtualization, but I had to learn that it is not supporting it. There are no settings in the BIOS to turn on/off virtualization. And VirtualBox can't install Ubuntu for that reason.


I tried Virtualbox on my Acer laptop. Same thing. Virtualbox was a no go on Vista 64 with Debian, Ubuntu, and Slackware. Somehow Opensuse 11.1 runs flawlessly albeit in 2D both live cd and install. I'd rather be Slacking to be honest, but apt is a favorite. Mepis 8 live CD also worked.

I figure what the heck, no need to starve while you waiting or figuring things out.

---

### Post by uBeer on 2009-03-29
I just wanted to let you know that my 64 bit system with radeon mobility 3650 works quite ok. I've got 3 Gigs of ram in this machine (so not the 4 or 2 gigs you guys were talking about) and it works fine.

Only downside seems to be that with the 64 bit version it doesn't suspend and resume properly.

And about the support notion: it is supported, but as a radeon 3xxx series. Not as a mobility card.

---

### Post by shelvingguy on 2009-03-29
That's the second time I've heard that the ATI Mobility Radeon HD 3650 works in a machine with 3GB of RAM.

I would be game to try Virtualbox, but it doesn't sound like it would be an improvement over running the full install with only one of my two 2GB RAM modules.

It seems the work on this has bug has stopped.  My questions are not longer being responded to.  Up until Jaunty got going, there seemed to be more interest in fixing this bug.

Maybe there are just not enough of these cards to justify the time investment.  I'm losing patience.  I want to use the full capabilities of my hardware.

---

### Post by zika on 2009-03-29
> **uBeer said:**
> I just wanted to let you know that my 64 bit system with radeon mobility 3650 works quite ok. I've got 3 Gigs of ram in this machine (so not the 4 or 2 gigs you guys were talking about) and it works fine.

Only downside seems to be that with the 64 bit version it doesn't suspend and resume properly.

And about the support notion: it is supported, but as a radeon 3xxx series. Not as a mobility card.
AMD Phenom X#, 3Gigs, Asus ah 3650 (a.k.a. ATI HD 3650 Radeon) with working 64bit HH, II, JJ, 2.6.28, 2.6.29, all the memory reported with suspend, hybernate and everything ... just writing from it ... ;)

---

### Post by factotum218 on 2009-03-29
Ugh, it works, it doesn't, it works, it doesn't. Fun.
Just not ready to invest time for a data backup and reinstall to find out if it does or not.

<offtopic>
Wait and see I guess. Give me time to finish up Fallout 3 and figure out how to pull text out of an InDesign file. I update a newspaper site and they don't proof anything until after the pages are laid out. Got a free copy of InDesign out of it, which is kinda cool but it's really really damn frustrating.
</offtopic>

---

### Post by bardu on 2009-03-29
> Maybe there are just not enough of these cards to justify the time investment.

At least here in Canada there are many laptops available from different manufacturers with this graphics card.

> I'm losing patience.  

Me too. 

> I would be game to try Virtualbox, but it doesn't sound like it would be an improvement over running the full install with only one of my two 2GB RAM modules.

If you are still on Vista put back your other 2GB, download VirtualBox and assign 2GB as base memory size in the installation wizard for Ubuntu as guest OS. Then click "Start" in VirtualBox and run Ubuntu from LiveCD and see whether this works for you. Make sure Intel VT (Virtualization Technology) is enable, if not turn it on in the BIOS. You must also turn it on in VirtualBox under Details -> General -> VT-x/AMD-V.

You can also download and run "Processor Check for 64-Bit Compatibility" from [http://www.vmware.com/download/ws/drivers_tools.html]("http://www.vmware.com/download/ws/drivers_tools.html") to see whether your laptop supports virtualization.

---

### Post by factotum218 on 2009-03-29
> **bardu said:**
> 
You can also download and run "Processor Check for 64-Bit Compatibility" from [http://www.vmware.com/download/ws/drivers_tools.html]("http://www.vmware.com/download/ws/drivers_tools.html") to see whether your laptop supports virtualization.

Thanks for the info, awesome!

I feel like I'm back in 1998 again. Nothing I want to try will work and I'm stuck with Windows LOL. Ah how nostalgic.

[B]
And from the Jaunty release notes:[/B]
[I]The latest X.Org server, version 1.6, is available in Jaunty. A number of video cards have been transitioned to free drivers as part of this update.

The -ati driver has received numerous fixes and performance improvements. It now uses the EXA acceleration method by default. 2D acceleration support for the newest R6xx/R7xx family of cards is also available. 3D support is available up to R5xx cards for -ati. An updated -fglrx proprietary driver is available for R6xx/R7xx users who need 3D support. 
[/I]

Not sure where the AMD Radeon Mobility card fits into any of these, but I'm going to take a guess here..
If I look back at the previous posts I'll find something that will more or less translate the above release note into saying there is now 3D support for this card, I'll try it, and then it will fall on its face. Murphys law ya'know

---

### Post by shelvingguy on 2009-03-30
bardu - It seems we have very similar machines and card issues.  Outside of being able to have all 4GB of RAM installed (for vista), does running ubuntu in Virtualbox have any advantages over running it on its' own partition?

---

### Post by bardu on 2009-03-30
shelvingguy - it depends on your needs. Usually, I have Ubuntu installed and just run Windows as guest OS, because I have little need for Windows primarily just for testing. I prefer virtualization over dual boot, since you can run two or more OS's at the same time and you can share folders, which is pretty handy for a developer.

---

### Post by Krelis on 2009-03-31
I ran into similar problems (unresponsive black screen), with similar hardware (toshiba a350-10a, p8400, mobility hd 3650, 4gb ram). Removing 2gb of ram worked for me too. xorg.0.log files are a bit different though, posted a bug on launchpad regarding the radeonhd driver, so more details there:

[https://bugs.launchpad.net/bugs/352050](https://bugs.launchpad.net/bugs/352050)

Hopefully it will work later on, ran into the problem only weeks ago so i have some patience left ;)

---

### Post by factotum218 on 2009-03-31
UUUGggghhhh!!

Ah well I tried.

Grabbed the 9.04 beta 32-bit on a 64-bit system with 4 gigs of ram intact and tried running it live. Got as far as a spinning cursor. While that was going on I was getting a steady stream of errors that more or less tell me that my burner makes great coasters. Wonderful. SQUASHFS errors.

But on the plus side I guess that means there is some support for the card at least. Seriously, if I could get 3d support working on this card i'd be dancing in the streets and signing up for commercial support just to send them a few bones to help out (since I'm pretty much development inept outside of bash scripts and php).

---

### Post by tormod on 2009-04-01
> **factotum218 said:**
> UUUGggghhhh!!
Stop burning plastic - boot from USB sticks :)

---

### Post by factotum218 on 2009-04-02
> **tormod said:**
> Stop burning plastic - boot from USB sticks :)

Good thinking, I tried that out last night with Unetbootin and screwed something up somewhere. No active file system or something. Haven't had the chance to fix it yet.

---

### Post by syko21 on 2009-04-02
> **factotum218 said:**
> 
[B]
And from the Jaunty release notes:[/B]
[I]The latest X.Org server, version 1.6, is available in Jaunty. A number of video cards have been transitioned to free drivers as part of this update.

The -ati driver has received numerous fixes and performance improvements. It now uses the EXA acceleration method by default. 2D acceleration support for the newest R6xx/R7xx family of cards is also available. 3D support is available up to R5xx cards for -ati. An updated -fglrx proprietary driver is available for R6xx/R7xx users who need 3D support. 
[/I]

Is compiz 2D acceleration or 3D acceleration?

---

### Post by zika on 2009-04-03
> **syko21 said:**
> is compiz 2d acceleration or 3d acceleration?
it is 3D ...

---

### Post by factotum218 on 2009-04-03
I finally got around to getting 9.04 beta installed. I'm surprised, it works.....




EVEN 3D SUPPORT WITH THE SUPPLIED FGLRX DRIVERS SUPPLIED FROM THE REPO'S.

In my experience the 3560 Mobility now has 3d support, Compiz and all! Case closed for me.


Suddenly I feel like playing Neverwinter Nights...or seeing if I can get Fallout3 working

---

### Post by shelvingguy on 2009-04-07
I've been keeping up with the daily updates but, so far, I still am not able to run my HD 3650 in ubuntu with "ati", or fglrx, unless I remove 1/2 of my RAM.

I'm also not confident about VMWare Server.  I downloaded it, but it appears it to require a bit of know-how.  I seem to be running a little low on know-how.

It looks like I'll be chillin' in hardware purgatory.

---

### Post by factotum218 on 2009-04-09
Just thought I would post an update.

Im running on an Acer 6350 with a dual 64 turion and 4gb of ram.
Since I'm running it 32-bit I have 2gb available to use. No biggie.
I used the 3d driver provided by the Ubuntu repo's and compared to simple 2d drivers it's a bit buggy but still functioning.

Dragging windows is jittery and leaving trails, overall desktop performance is actually a bit slower than using the 2d ati drivers.
I never got around to trying any games out, but did get some decent FPS with glxgears at full screen.

Since then I've gone back to running the 2d drivers but now get a hash mismatch error when using apt to upgrade anything.

All in all there has been progress since 8.10, but for now I'm going to be sticking with 2d drivers.

---

### Post by zika on 2009-04-15
***for all of You having troubles with 4G RAM ...***

try adding "enable_mtrr_cleanup" to Your kernel line on bootup.

(for example: [http://www.bluequartz.us/phpBB2/viewtopic.php?t=86288&highlight=&sid=2c44ea7f5294d89474c2c41837c99364](http://www.bluequartz.us/phpBB2/viewtopic.php?t=86288&highlight=&sid=2c44ea7f5294d89474c2c41837c99364))

---

### Post by Krelis on 2009-04-15
the "enable_mtrr_cleanup" line didn't work for me. I don´t know how to use the  mtrr-uncover program mentioned in the link. On a Toshiba a350, Intel C2D P8400 cpu, 4G ram, and a Ati Mobility Radeon HD 3650 (of course) btw.

---

### Post by zika on 2009-04-15
> **Krelis said:**
> the "enable_mtrr_cleanup" line didn't work for me. I don´t know how to use the  mtrr-uncover program mentioned in the link. On a Toshiba a350, Intel C2D P8400 cpu, 4G ram, and a Ati Mobility Radeon HD 3650 (of course) btw.
sorry to hear that, well, I tried ... :)

---

