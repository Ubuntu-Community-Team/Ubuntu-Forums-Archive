---
title: "Failed kernel installation"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by gjhicks on 2005-03-14
Hi,

Am trying to install ubuntu on a Dell Inspiron 700m, using the 4.10 C:\downloads\warty-release-install-i386.iso.

The installation, to a 3gb partition seems to go well, until I get the following error message:


Installing Ubuntu Base System

87% complete

Installing kernel

An error was returned while trying to install the kernel into target system.

Kernel package 'linux 386'


I have tried repeating the process a few times.  On one occasion, I got a list of 4 different kernels (stupidly didn't write the names down!) but (aside from then) never got the chance to select the kernel.

Any ideas?

Specially, if I get the list of kernels again, which one do I choose?

Thanks,

Geoff.

---

### Post by az on 2005-03-14
It sounds more like a cd integrity problem.

There are different packages for the kernel:  Essentially, one package it the most recent kernel and another package will always keep the same name, but point to the most recent kernel.

linux-image-386
linux-image-2.6-386
linux-image-2.6.8.1-4-386

---

### Post by gjhicks on 2005-03-14
Thanks for the reply.

Do you mean that the four kernels mentioned (you listed three, the other is called just "linux-386") actually all refer to the same kernel?

Anyway, I installed using the expert (funny really, as I am definitely no expert!) mode and got it all installed.


But now a different problem.

All seemed fine, extra packages installed, etc.

Went to re-boot and everything appeared to be loading nicely until it got to:

* Starting PCMCIA services

It just sat there and did nothing.  Eventually, a few minutes, I forced a re-boot.  Same result.

Is there a way to force the startup routine to skip a particular service?

Regards,

Geoff.

---

### Post by siDDis on 2005-03-14
try to hit ctrl-c

---

### Post by Robban59 on 2005-03-15
Hi Gjhicks,

I got the exact sam eproblem as yours, wrote here on the forum but never got any answer, my burned CD with Warty is gathering dust.

Tell me the details of your EXPERT installation, I also tried it but no success: did you use any options and which ones , in the EXPERT installation mode ? 

Thanks for all info you can give me.

BRegards/ Robban

---

### Post by gjhicks on 2005-03-15
Hi,

I just used all of the "default" options.  It seems that the four kernel options offered are actually the same - why there are four is a mystery.

Managed to get almost all installed but when doing the post-installation, copy from the warty CD bit, got hung up.

It was doing "setting up gstreamer0.8-hermes (0.8.5-1ubuntu3) and just sat there.

Had to force a re-boot.

I have tried re-burning the ISO (yes, did a MD5sum check) but no joy.

Reckon I will try another distro, this one is just too hard to get going!

Good luck!

Geoff.

---

