---
title: "ATI x700, Black Screen on startup"
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by ThatRickGuy on 2005-07-20
Hi Everyone, I'm racking my brains on this one. I've been out of the Linux world for a long time and figured I'd jump on the Ubuntu bandwagon. Anyways, I've gone though the ATI install walkthrough in the tip and tricks forum, and I'm still having no luck.

I have an ATI x700pro w/ 256megs on PCIX. I am using the flgrx drivers apt-get says are the latest. I am using an xorg.conf that so far as I can tell is an exact copy of the one in the walk through. lspci shows my ATI card is on bus 1:0:0.

The problem is as soon as the GDM loads, my video card appears to shut off, my monitor switches to 'no signal' mode, and I can't switch to a new command prompt or shutdown the GDM, although numlock/capslock still work.

Any ideas? Anything else I can mention that would shed more light on the situation?

-Rick

---

### Post by varunus on 2005-07-20
Can you boot up in recovery mode and take a look at your /var/log/Xorg.0.log?  That might have some valuable information on what's happening.

Also, can you get into the GUI with the old drivers?  If you can, you could do a failed boot, shut off, change the driver in recovery mode, boot up into the GUI, and post your /var/log/Xorg.0.log.old file here.

---

### Post by ThatRickGuy on 2005-07-20
I've never managed to get the GUI up and running. I'm not seeing anything to amazing in the log, a few fonts appear to not load, all of the load (lib) lines look okay. Actually, about 25% of the way through there is a line: 
> (WW) Ignoring request to load module GLcore and a while later I see > (II) Loading Extension XFree86-DGA even though I though I had it disabled. I'll have to double check that one. I also noticed that fglrx is seeing the DVI output as the Primary head, and the VGA output as the secondary head. I tried putting on the adapter and switching to the DVI head, but still nothing. The log file eventually lists the kernel versions which look at, then ends with > fglrx(0): [DRI] installation complete and that's it.

-Rick

---

### Post by ThatRickGuy on 2005-07-20
Well, I had a type-o on the DGA issue, but still no dice :(

-Rick

---

### Post by ThatRickGuy on 2005-07-20
Finally got my Xorg.0.log file up on the web. The joys of CLI.

[http://www.ringdev.com/Xorg.0.log](http://www.ringdev.com/Xorg.0.log)

If you see anything suspisious, please let me know!

-Rick

---

### Post by ThatRickGuy on 2005-07-20
Also put my xorg.conf file up at:

[http://www.ringdev.com/xorg.conf](http://www.ringdev.com/xorg.conf)

Thanks,

-Rick

---

### Post by varunus on 2005-07-20
I'll take a look and see what I can do...until then, try something:

Open up your /etc/X11/xorg.conf using "sudo nano" from a console in recovery mode and try changing the Driver line in the device section to say:

Driver "vesa"

This might let you get into a GUI, but with no graphical acceleration.  (Which is better than nothing.)

---

### Post by ThatRickGuy on 2005-07-20
Thanks! Switching to Vesa drivers managed to get Gnome up and running, but I can already see some pretty poor performance. Any idea where to go from here to get the fglrx drivers going?

-Rick

---

### Post by varunus on 2005-07-20
Well, there are a few things you could try from here.  (I can't see anything wrong with your xorg.conf or your log file aside from the PCI:1:0:1 error, so its strange that X isnt coming up.)  I'd recommend trying the newest ATI drivers (version 8.14.13) by using the howto in the Hoary Tips and Tricks section of the forum (Its called HOWTO: ATI Drivers 8.14.13 or something like that).

At least with a GUI, you should have better luck...sorry I couldn't be of more help.  You could also google and see if anyone has the same problems.

---

### Post by ThatRickGuy on 2005-07-20
The AIT card shows up on 1:0:0 and 1:0:1 on lspci. I'm guessing the difference is primary/secondary heads since the card has SVGA/DVI output. I'll look into the newer drivers. I was having a heck of a time trying them while attempting to remember text commands and learn new ones.

-Rick

---

### Post by varunus on 2005-07-21
Despite the howto saying not to, you could also always try fglrxconfig just for kicks.  Who knows, it might make a working xorg.conf...Or at least, you could copy the device sections from the one the utility makes into your regular xorg.conf.

---

### Post by ThatRickGuy on 2005-07-21
Where is the fglrxconfig app? I had been using dpkg-reconfigure xserver-xorg to get the original xorg.conf set up.

-Rick

---

### Post by varunus on 2005-07-22
One of the ATI driver synaptic packages has the utility in it.  (It might be fglrx-settings, or something.  You can always search now that you have the GUI...you may want to try a newer version of the driver than the Synaptic one though, there's a nice howto in the Tips and Tricks section.)

---

### Post by ThatRickGuy on 2005-07-22
I ran the fglrxconfig app last night, it spit out a XFree config file, I talked to a ubuntu buddy on gaim and he said I could just rename that file to xorg.conf and it should work the same. But I get the same result, black screen, then no signal. Next I tried downloading the latest xorg drivers from ATI, uncompressed them from root (they already had the file structure for bin/usr/etc), and same thing, black screen for a second, then no signal.

I saw someone recommend something about linux headers? (sudo apt-get install linux-kernel-headers) so I guess I'll try that tonight. And someone also mentioned converting the ATI rpm to a deb pakage, what tool do I use to do that?

Also, ATI has some kind of installer program on their site for Linux, is there anyway to get that thing to run on Ubuntu/Gnome?

-Rick

---

### Post by varunus on 2005-07-22
Here's a howto that talks about how to use the ATI installer from their website in Ubuntu:  [http://www.ubuntuforums.org/showthread.php?t=32495](http://www.ubuntuforums.org/showthread.php?t=32495)

Good luck.

---

### Post by ThatRickGuy on 2005-07-22
Thanks! That's on my goals for tonight.

-Rick

---

### Post by ThatRickGuy on 2005-07-22
Well, made some progress. Tried running the ati driver .run pakage. Got an error about miss-matched something or other. Juding by what others had said I needed to get the header files for my kernal. So I got the latest i686 smp kernal and headers, rebooted, selected the 686smp kernal and tried again. this time I got a rather unhelpful pill of errors:

[PHP][Message] Kernel Module : Trying to install a precompiled kernel module.
[Message] Kernel Module : Precompiled kernel module version mismatched.
[Message] Kernel Module : Found kernel module build environment, generating kernel module now.
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
make -C /lib/modules/2.6.10-5-686-smp/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
/usr/src/linux-headers-2.6.10-5-686-smp/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.10-5-686-smp/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686-smp'
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
/bin/sh: gcc: command not found
  CC [M]  /lib/modules/fglrx/build_mod/2.6.x/agp3.o
/bin/sh: gcc: command not found
make[2]: *** [/lib/modules/fglrx/build_mod/2.6.x/agp3.o] Error 127
make[1]: *** [_module_/lib/modules/fglrx/build_mod/2.6.x] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686-smp'
make: *** [kmod_build] Error 2
build failed with return value 2
[Error] Kernel Module : Failed to compile kernel module - please consult readme.[/PHP]

Any thoughts?

-Rick

---

### Post by ThatRickGuy on 2005-07-22
doh, I'm dumb. apt-get install gcc maybe? hehe

-Rick

---

### Post by ThatRickGuy on 2005-07-22
hrm, still no signal...

The ATI driver.run install completed successfully though.

-Rick

---

### Post by ThatRickGuy on 2005-07-22
Well, some bits of the log, this part looks interesting:
```

(II) fglrx(0): driver needs X.org 6.8.x
(II) fglrx(0): detected X.org 6.8.2
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: open result is -1, (Unknown error 999)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID PCI:1:0:0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenByBusid: drmOpenMinor returns 7
drmOpenByBusid: drmGetBusid reports 
drmOpenDevice: node name is /dev/dri/card1
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card2
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card3
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card4
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card5
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card6
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card7
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card8
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card9
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card10
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card11
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card12
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card13
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card14
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: open result is -1, (No such device)
drmOpenDevice: Open failed
drmOpenByBusid: drmOpenMinor returns -1023
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 7, (OK)
drmGetBusid returned ''
(II) fglrx(0): [drm] loaded kernel module for "fglrx" driver
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:1:0:0"
(II) fglrx(0): [drm] added 8192 byte SAREA at 0xf8a85000
(II) fglrx(0): [drm] mapped SAREA 0xf8a85000 to 0xb7db1000
(II) fglrx(0): [drm] framebuffer handle = 0xc0000000
(II) fglrx(0): [drm] added 1 reserved context for kernel
(II) fglrx(0): DRIScreenInit done

```

This part is also interesting:
```

(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.14.13
(II) fglrx(0):     Date: Jun  8 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(II) fglrx(0): Kernel Module version matches driver.
(II) fglrx(0): Kernel Module Build Time Information:
(II) fglrx(0):     Build-Kernel UTS_RELEASE:        2.6.10-5-686-smp
(II) fglrx(0):     Build-Kernel MODVERSIONS:        no
(II) fglrx(0):     Build-Kernel __SMP__:            no
(II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000

```

Everything looks good, but why is Build-Kernel  __SMP__: no?

-Rick

---

### Post by ThatRickGuy on 2005-07-23
Well, just ran the fglrx.uninstall.sh, deleted every reference to fglrx from my hard drive, grabbed the ati....run script/file from ATI's web page, reinstalled, verified the xorg.conf was set up correctly, rebooted, and still, black screen. One of my buddies said Mandriva was more ATI friendly (he too has an ATI x700) so I figure I'll give that a try, maybe I'll be back for breezy, see what's improved.

-Rick

---

