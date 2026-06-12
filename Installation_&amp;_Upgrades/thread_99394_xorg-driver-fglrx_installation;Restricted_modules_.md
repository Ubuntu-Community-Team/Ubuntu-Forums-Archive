---
title: "xorg-driver-fglrx installation;Restricted modules available to a custom compiled kern"
date: 2005-12-05
forum: Installation &amp; Upgrades
---

### Post by manolo on 2005-12-05
In order to compile ALSA modules, libraries, etc
(To be able to use 5.1 sound), I have custom compiled
and installed a 2.6.12 kernel:
{
Synaptic linux-686-smp (linux-image-2.6.12-10-686-smp)
  Note Includes:
    linux-image-2.6.12-10-686-smp 2.6.12-10.24
    linux-restricted-modules-2.6.12-10-686-smp 2.6.12.4-11.1

Synaptic linux-source-2.6.12 with ubuntu patches

Linux-source compiled with make-kpkg.

Resulting kernel-image installed: kernel-image-2.6.12.02
}

Everything works fine. Now I want to install a 3D ATI video
driver for my Ati Radeon 9200 card according to instructions
in the Ubuntu.5.10StartingGuide (As root):
{
Synaptic xorg-driver-fglrx (Ati driver)
  Note includes:
    xorg-driver-fglrx 6.8.0-8.16.20-0ubuntu16.1

echo fglrx | tee -a /etc/modules

depmod -a ; modprobe fglrx
  Error message: FATAL: Module fglrx not found.

........
}

fglrx kernel module is in directory:
/lib/linux-restricted-modules/2.6.12-10-686-smp/fglrx
but modprobe looks for it in the running kernel modules:
'/lib/modules/2.6.12.02' and does not find it (It isn't in
'/lib/modules/2.6.12-10-686-smp' either).

Is the module not available because I am using a custom
compiled kernel?

Which is the mechanism that allows restricted-modules to
be seen by the kernel/modprobe?

What should I do to make restricted-modules available to
my custom compiled kernel?


Many thanks in advance.

---

### Post by metoo on 2005-12-06
Yes, kernel modules must match the running kernel.
However, for my selfcompiled lirc modules, it is OK to copy them manually to the directory of the running kernel after updating the kernel.
But this will only work as long as the major number will stay the same.
Currently it is 2.6.12 . So the modules compiled for 2.6.12-8 will work in 2.6.12-10 which leads me to the assuption, that the kernel internally only sees the 2.6.12 and the rest is a ubuntu package add on.

The restricted modules are in
/lib/modules/yourkernel/volatile/...
Copy the fglrx.ko module to this place.

Another option that I used to compile the lirc module is to use the ubuntu kernel, download the source, get the config from /boot, re-compile (make bzImage) but DO NOT INSTALL, just copy the modules manually over into the /lib/modules/yourkernel/... directory. You may have to tweak the Alsa source of the kernel before that.
It takes ages to build all the modules, but probably less than to configure the kernel first to your needs.

Is it proven, that you have to compile Alsa yourself? I have digital and 5.1 (6 channel analog) output running here, but I'm not sure, that 5.1 is actually surround sound.
Often you have to tell your application (like mplayer) to use 5.1 to get it as output.

---

