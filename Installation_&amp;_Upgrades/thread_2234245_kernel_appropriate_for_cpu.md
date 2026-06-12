---
title: "kernel appropriate for cpu"
date: 2014-07-13
forum: Installation &amp; Upgrades
---

### Post by johnhartel on 2014-07-13
wifi shopped then screen went blank. resterted and would not do anything so tried to install ubuntu 14.04 got a msg this kernel requires the following feattures not present on the cpu
pae
unable to boot - please use a kernel appropriate for your cpu
then tried ubutu 12 and 10 and linux lite 1.06 get the same message

---

### Post by grahammechanical on 2014-07-13
Do you think that it would help us to help you if you gave us the specifications of the hardware? How old is this machine? I can only guess that the CPU is so old that it does not have what is called PAE (Physical Address Extension). It is a modification to the CPU architecture to allow a 32 bit CPU to address more than 4GB of memory.

If this is the case, then you most certainly need a 32 bit version of Linux and a distribution that has a NON-PAE Linux kernel. Ubuntu 32 bit no longer comes with a NON-PAE kernel. It could be that your hardware is so old that it will not run a modern version of Ubuntu. There most certainly could be problems with the graphic adapter being under powered.

But all this is less than guess work because you provide so little information about your machine.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

> [COLOR=#333333][FONT=Ubuntu]The ISO image will fail to boot ([/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]"This kernel requires the following features not present on the CPU: pae."[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]) If a few lines above this text there is a warning [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]"WARNING: PAE disabled. Use parameter 'forcepae' to enable at your own risk!"[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu], then you can boot by pressing tab at the boot screen and appending the kernel parameter "forcepae" after the "-- ".[/FONT][/COLOR]

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Regards.

---

