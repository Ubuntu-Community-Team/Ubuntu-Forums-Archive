---
title: "Riva TNT2 under 11.04 - Nouveau not working, can't install Nvidia driver"
date: 2011-05-17
forum: Installation &amp; Upgrades
---

### Post by Sal Z on 2011-05-17
Hello,

I'm trying to run Lubuntu 11.04 under on a old P4 1.5 / 512 MB Ram using a Riva TNT2 video card ( Nvidia Vanta, to be more precise)

Stock 2.6.38 kernel doesn't boot to any graphical display, showing just a bash prompt after a while, and trying to install the old supported driver (71.84) from NVIDIA is impossible due to this bug with kernel > 2.6.36; see  [http://forums.gentoo.org/viewtopic-t-852938-start-0.html](http://forums.gentoo.org/viewtopic-t-852938-start-0.html) 

I've tried running a 2.6.35 kernel, but due to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746249](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746249)

I can't blacklist nouveau driver and consequently I can't install the nvidia driver.

the nouveau output on dmesg doesn't really give any help.

Any suggestion?

---

### Post by Sal Z on 2011-05-17
No idea, anybody?

anyway, the official NVIDIA 71.84 driver  is a complete no-go, it's way too problematic to let such older driver run on a recent kernel.

Any idea why the 2D nouveau driver is not working?

---

### Post by danzvash on 2011-05-17
What error are you getting with the nouveau driver?

(You should see errors towards the end of /var/log/Xorg.0.log)

Assume you're running the VESA driver as a temporary workaround.

When I try and run nouveau 2D, I get the following on my nVidia Corporation GT216 [Quadro FX 880M]:

```
[    57.977] (EE) [drm] failed to open device
[    57.977] (EE) No devices detected.
[    57.977] 
Fatal server error:
[    57.977] no screens found

```

But nvidia-current 270.41.06-0ubuntu1 from x-swat updates runs, though I think it's causing a lot of hard freezes at the moment - hence why I was trying nouveau ....

---

### Post by MAFoElffen on 2011-05-17
> **Sal Z said:**
> Hello,

I'm trying to run Lubuntu 11.04 under on a old P4 1.5 / 512 MB Ram using a Riva TNT2 video card ( Nvidia Vanta, to be more precise)

Stock 2.6.38 kernel doesn't boot to any graphical display, showing just a bash prompt after a while, and trying to install the old supported driver (71.84) from NVIDIA is impossible due to this bug with kernel > 2.6.36; see  [http://forums.gentoo.org/viewtopic-t-852938-start-0.html](http://forums.gentoo.org/viewtopic-t-852938-start-0.html) 

I've tried running a 2.6.35 kernel, but due to this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746249](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/746249)

I can't blacklist nouveau driver and consequently I can't install the nvidia driver.

the nouveau output on dmesg doesn't really give any help.

Any suggestion?
Welcome to Ubuntu.

I "have" this same card on one of my test boxes and have ran it on Nattysince apha1, This same box it now running Ocieric just fine... Albeit in Unity 2D and Gnome.

Let me qualify running fine!  Before, I installed the NV drivers for it <> Now I use the non-prorietary, what in natty testing was nvidia-experimental, now just see's as nvidia-current (but not propietary).  I thought that I needed the drivers I used before, but by the time we got through beta1, that all changed // and changed my mind on that.

Funny thing is that even though this card is not a real high end card, the graphics on it is snappy and crisp!

Now-- Why do you thing you "need" to go to stay with proprietary drivers to use with this card?

(After answering that either way... I then have more info than you would even need...)

Edit--
> old P4 1.5 / 512 MB Ram using a Riva TNT2 video card
LOL.  Wait a minute!  It this a Compaq Presario?  That "is" my test box here.

---

### Post by danzvash on 2011-05-17
@ MAFoElffen - I think you're actually running the proprietary Nvidia driver - there is no open source driver package called nvidia-current ....

@ Sal Z: Can't you run a recent Nvidia driver with a recent kernel?
The general installation procedure to run the latest Nvidia releases:
- enable "restricted" repo in Software Center/Synaptic
- install nvidia-current  (the current version is  270.41.06-0ubuntu1)
- reboot

(This should do the blacklisting of nouveau for you.)

By the way, that was the SOLUTION for my previous failure to run nouveau (and the "(EE) [drm] failed to open device" error) - I still had "modeset=0" in a /etc/modprobe.d/blacklist-nouveau.conf. 
[nouveau Wiki - troubleshooting]("http://nouveau.freedesktop.org/wiki/TroubleShooting#Xorgfailstostartwith.22.28EE.29.5Bdrm.5Dfailedtoopendevice.22")
Once I removed this file, X started ok with nouveau, and GL enabled.

X with nouveau 0.0.16+git20110107+b795ca6e-0ubuntu7 and GL/composite enabled:
glxgears: approx 270fps

However, I was getting some hard freezes still (the reason for me trying nouveau was to avoid the freezes I got with nvidia-current):

```
[  1933.036] [mi] EQ overflowing. The server is probably stuck in an infinite loop.
[  1933.036] 
Backtrace:
[  1933.074] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4a2626]
[  1933.074] 1: /usr/bin/X (mieqEnqueue+0x1f4) [0x4a18e4]
[  1933.074] 2: /usr/bin/X (xf86PostMotionEventM+0x97) [0x47d767]
[  1933.074] 3: /usr/bin/X (xf86PostMotionEvent+0xd0) [0x47d990]
[  1933.074] 4: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f45d35cc000+0x514a) [0x7f45d35d114a]
[  1933.074] 5: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f45d35cc000+0xb268) [0x7f45d35d7268]
[  1933.074] 6: /usr/lib/libutouch-grail.so.1 (grail_pull+0x382) [0x7f45d3dec342]
[  1933.074] 7: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f45d35cc000+0xb034) [0x7f45d35d7034]
[  1933.074] 8: /usr/lib/xorg/modules/input/synaptics_drv.so (0x7f45d35cc000+0x6d7e) [0x7f45d35d2d7e]
[  1933.074] 9: /usr/bin/X (0x400000+0x6c657) [0x46c657]
[  1933.074] 10: /usr/bin/X (0x400000+0x124bbe) [0x524bbe]
[  1933.074] 11: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f45d932b000+0xfc60) [0x7f45d933ac60]
[  1933.074] 12: /lib/x86_64-linux-gnu/libc.so.6 (ioctl+0x7) [0x7f45d8333297]
[  1933.074] 13: /lib/x86_64-linux-gnu/libdrm.so.2 (drmIoctl+0x28) [0x7f45d68cd058]
[  1933.074] 14: /lib/x86_64-linux-gnu/libdrm.so.2 (drmCommandWrite+0x1b) [0x7f45d68cf30b]
[  1933.074] 15: /lib/x86_64-linux-gnu/libdrm_nouveau.so.1 (0x7f45d628a000+0x2b87) [0x7f45d628cb87]
[  1933.074] 16: /lib/x86_64-linux-gnu/libdrm_nouveau.so.1 (nouveau_bo_map_range+0xfe) [0x7f45d628d19e]
[  1933.074] 17: /usr/lib/xorg/modules/drivers/nouveau_drv.so (0x7f45d6490000+0x6ad6) [0x7f45d6496ad6]
[  1933.074] 18: /usr/lib/xorg/modules/libexa.so (0x7f45d5e4e000+0xbf2c) [0x7f45d5e59f2c]
[  1933.074] 19: /usr/bin/X (0x400000+0x160b89) [0x560b89]
[  1933.074] 20: /usr/bin/X (0x400000+0xa54f3) [0x4a54f3]
[  1933.075] 21: /usr/bin/X (0x400000+0x2b55f) [0x42b55f]
[  1933.075] 22: /usr/bin/X (0x400000+0x2e2a9) [0x42e2a9]
[  1933.075] 23: /usr/bin/X (0x400000+0x21a7e) [0x421a7e]
[  1933.075] 24: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xff) [0x7f45d8274eff]
[  1933.075] 25: /usr/bin/X (0x400000+0x21629) [0x421629]
```

So I tried disabling hardware acceleration by adding nouveau.noaccel=1 to the kernel boot options in the GRUB boot editor.

Now the GL extensions are still being loaded
```
[    24.967] (II) "glx" will be loaded by default.
[    25.025] (II) LoadModule: "glx"
[    25.025] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.092] (II) Module glx: vendor="X.Org Foundation"
[    25.092] (==) AIGLX enabled
[    25.092] (II) Loading extension GLX

```

but at least the freezes are gone - at the expense of about 90% of the performance:

X with nouveau, GL enabled, no hardware acceleration:
glxgears: approx 15fps

---

### Post by danzvash on 2011-05-17
Just for completeness' sake - to get smoother 2D performance with nouveau, at the expense of (slow) 3D/GL/composite capability, just make sure the following is in /etc/X11/xorg.conf:

```
Section "Module"
    Disable     "glx"
EndSection
```

---

### Post by Sal Z on 2011-05-18
Unortunately I can't run the default nvidia driver, nvidia-current just prints a quite eloquent error saying that my video card is not supported, starting from release 71.84.


the error message from X11 is the following:

```
[    21.117] (EE) NOUVEAU(0): Error allocating scanout buffer: 0
[    21.117] 
Fatal server error:
[    21.117] AddScreen/ScreenInit failed for driver 0
[    21.117] 
[    21.117] 
```
I've attached the whole log, in any case.

Actually there is no specific reason for keeping the nvidia driver, At this point I think I will just keep vesa.

MAFoElffen: Nope, they are some really old IBM NetVista pcs (I'm trying to recover an old lab for a school). They were running windows 2000 and had not been turned on since 2001 :|

---

### Post by wandalalakers on 2011-05-18
Good grief, that's 10 years.

> **Sal Z said:**
> They were running windows 2000 and had not been turned on since **[COLOR="Red"][SIZE="2"]2001[/SIZE][/COLOR]** :|

---

### Post by Sal Z on 2011-05-18
Yep, they were literally covered in dust, and most hdd and cdrom drives were not working.

Despite all of this, Lubuntu 11.04 is working amazingly well. The difference in performance with the original OEM windows 2000 installation is outstanding. Except for the video card, everything is working fine.

...unfortunately it seems now that management has no intention on using Lubuntu, they just asked me to use Windows XP on the working machines instead :|

---

### Post by MAFoElffen on 2011-05-18
> **danzvash said:**
> @ MAFoElffen - I think you're actually running the proprietary Nvidia driver - there is no open source driver package called nvidia-current ....

This is the best driver I found so for that card for using Natty- and yes it is open-source through Ubuntu.  

Right now though that box is running:
```

mafoelffen@maferr02:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
mafoelffen@maferr02:~$ 

```I've been using that opensource driver for that card since... about 3-4 months?  Beofre that I was using the proprietary.

---

### Post by MAFoElffen on 2011-05-18
> **pcdoctor said:**
> Good grief, that's 10 years.
LOL, I just got a new test box last night that is running Windows 2000/Millennium.  About 11-12 years old/Pentium 2.

I think it's going to get a different mobo though.  I like the case. The current in it takes forever to even boot!

---

### Post by danzvash on 2011-05-26
@MAFoElffen: Just out of curiosity: could you do a 
```

dpkg -l | grep nvidia
```

and then maybe a 
```
apt-cache search nvidia-current
```

Even in oneiric I can't find the package that you're referencing (or anywhere at packages.ubuntu.com), and that could indicate a bug in Jockey ...

---

