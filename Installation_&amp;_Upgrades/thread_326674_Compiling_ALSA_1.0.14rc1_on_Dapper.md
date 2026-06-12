---
title: "Compiling ALSA 1.0.14rc1 on Dapper"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by SpiralSlash on 2006-12-28
Alright, for my laptop's headphone jack to work properly, I need to upgrade to ALSA 1.0.14rc1. (Or so I have read.) I'm still a noob at mucking with stuff like this, and I've managed to get myself stuck.

I've managed to download the source, discern what configuration options I needed, install all the required files to compile it, and I've run "make menuconfig" on my linux-headers-2.6.15-27 folder and disabled ALSA in there. (Wouldn't let me compile before I did that because it detected ALSA was already installed.)

I ran make on my 1.0.14rc1 folder and it failed out with this:

[INDENT]make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-27/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/mike/alsa-driver-1.0.14rc1/acore/memalloc.o
/home/mike/alsa-driver-1.0.14rc1/acore/memalloc.c:746: fatal error: opening dependency file /home/mike/alsa-driver-1.0.14rc1/acore/.memalloc.o.d: Permission denied
compilation terminated.
make[3]: *** [/home/mike/alsa-driver-1.0.14rc1/acore/memalloc.o] Error 1
make[2]: *** [/home/mike/alsa-driver-1.0.14rc1/acore] Error 2
make[1]: *** [_module_/home/mike/alsa-driver-1.0.14rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27'
make: *** [compile] Error 2[/INDENT]What am I doing wrong here? What's the correct procedure for compiling and installing ALSA? Am I even using the right kernel source package? "sudo apt-get install kernel-source" installs kernel source for some 2.4 based kernel... I'm running Kubuntu 6.06.1, if it makes any difference.

---

### Post by po0f on 2006-12-28
SpiralSlash,

You should just need linux-headers-`uname -r` if you are compiling kernel *modules*, you only require linux-source-`uname -r` if you plan on recompiling the whole kernel.

What are the permissions on /home/mike/alsa-driver-1.0.14rc1?  You are getting a "permission denied" error, but the directory is under your home.  Did you unpack the tarball you downloaded as root?  Try `sudo make` instead.

---

### Post by SpiralSlash on 2006-12-28
The folder properties says that user Mike is the owner, so I guess I unpacked it under Mike.

This is what I get when trying 'sudo make':

[INDENT]make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27'

  WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-27/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/mike/alsa-driver-1.0.14rc1/acore/memalloc.o
/bin/sh: scripts/genksyms/genksyms: No such file or directory
make[3]: *** [/home/mike/alsa-driver-1.0.14rc1/acore/memalloc.o] Error 1
make[2]: *** [/home/mike/alsa-driver-1.0.14rc1/acore] Error 2
make[1]: *** [_module_/home/mike/alsa-driver-1.0.14rc1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-27'
make: *** [compile] Error 2[/INDENT]

It's a slightly different error than before, but I still am not sure what exactly it means.

---

### Post by dannyboy79 on 2006-12-28
well I am no linux guru but apparently some script that is trying to run is stateing that the folder or file scripts/genksyms/genksyms doesn't exist. this would be a problem wouldn't it? i only came in here to see how this was going as I may want to compile the newest alsa also because I have sound coming out of my left speaker only and have tried everything to fix it to no avail! so this may be my last resort. let me know how you fix the WARNING: Symbol version dump /usr/src/linux-headers-2.6.15-27/Module.symvers
is missing; modules will have no dependencies and modversions. issue because I believe I have headers installed as well for when I had to install the nvidia driver.

---

