---
title: "Blacklisting nouveau module to get nvidia drivers to work?"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by t.rei on 2010-03-10
Hi,

Just wanted to start this thread after not finding anything to really help me with this issue, and I tried *alot*.

The problem was that I could not install the proprietary nvidia drivers after a dist-upgrade a few days ago that did get me plymouth but in the process loaded the nouveau drivers on boot.

So everytime I tried to install the proprietary ones (excuse me for actually gaming on linux - so havin 3d and wine running is mandatory) I got the following error:
```

ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.

```

So after much trial and error the only thing that got me to working nvidia drivers (and not working plymouth wich is the smaller one of the problems) was to add nouveau to the bottom of my **/etc/modprobe.d/blacklist.conf** reboot and install the nvidia drivers through the installer.

Now my dearest eve-online is working again. *cheer* but the prettyness of plymouth is gone. 

I hope this answer might help some chap who runs into the same issue, or - even better - gets noticed by one of you who knows a better way to do it.

As far as I understand it's the **vga16fb** module that is insufficient to run a proper graphical plymouth. Not blacklisting the nouveau module makes it load this one instead, giving you pretty graphics on boot and 'working' X with the nouveau driver in xorg.conf (or empty xorg.conf) but no 3d acceleration.

System:
```

$ uname -r
2.6.32-16-generic-pae
$ lspci |grep nV
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9600M GS] (rev a1)
$ lsmod |grep nvi
nvidia               8877607  40 
agpgart                31820  2 nvidia,intel_agp
```
last dist-upgrade 22:30 CET

---

### Post by joske on 2010-03-10
Why bother with plymouth, as lucid boots so fast? 

Maybe you could make a startup script that runs just before X comes up, and rmmods the nouveau module? Don't know if that'll actually work... Does plymouth run in FB or X?

---

### Post by t.rei on 2010-03-11
Hi, appearantly plymouth runs on the fb. 'rmmoding' the nouveau module unfortunately does not work without complications, as it is used by several other modules even when X is not running.

So right now I'm just keeping it blacklisted and plymouth uninstalled. I hope I get to test a new install in a few days on a second hd, and see if this might be due to some upgrade mess. 

Strangely: since I ditched nouveau and plymouth my suspend to ram starts working again without screwing up X and the console afterwards. \o/

---

### Post by cyberkilla on 2010-03-11
FYI, if you install the nVidia drivers from the repository, they DO seem to blacklist nouveau, and a few other drivers.

If I have nVidia drivers installed, I can't modprobe nouveau and the boot fails if I set xorg.conf to use it.

---

### Post by SevenMachines on 2010-03-11
the repository drivers should blacklist nouveau/nvidia depending on which one you've activated. if your not using repository drivers you may want to do something similar, for example, heres what the repository ones do with nvidia active

/etc/modprobe.d/nvidia-graphics-drivers.conf:

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96
alias nvidia nvidia-current

---

### Post by t.rei on 2010-03-11
Well there certainly is a lack of smoothness in choice of drivers. ;)

But since plymouth, nouveau and the whole process are still under rather radical development I guess thats something to live with, as long as the problems are known and maybe workarounds/fixes/ideas get shared, no?

I'm fairly certain that this is not a state to start a LTS release with, yet. But it very well might become one. :)

---

### Post by SevenMachines on 2010-03-11
theres been a bit of a change in the way the nouveau drivers and associated bits and pieces are being introduced in the last few days so there may be a bit of a settling down period, but if you still have problems with acitivating/de-activating drivers using jockey then certainly file a bug, as i understand it it's something that the developers are very keen to make entirely seamless

---

### Post by t.rei on 2010-03-12
I took the module off the blacklist today to test.

Still no luck. Also I noticed my dual-screen does not work anymore with the same nvidia-drivers that used to work rather smoothly. (190.53 - xserver: 1.7.5)

---

