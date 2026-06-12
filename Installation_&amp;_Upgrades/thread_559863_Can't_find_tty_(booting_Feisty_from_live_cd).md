---
title: "Can't find tty (booting Feisty from live cd)"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by El Bandano on 2007-09-25
I tried to install Ubuntu 7.04 on my new pc but when I tried to boot the live cd I got this error:
"can't access tty; job control turned off"
and I got a command line.

I searched the internet and I found some solutions but none of them worked:
adding "break=top", "irqpoll" and/or "pci=noacpi" to the to the boot-options,
running "modprobe ide_cd", "modprobe isofs", "modprobe piix" and/or "modprobe ide_generic" in the commandline
tell it to boot using a driver-cd (without actually having one)

I've used the cd to install Ubuntu on other pc's and it worked fine so I don't think the cd is the problem.

Someone told me it had something to do with the hardware-configuration and I was wondering if anyone knows whether this configuration could be causing problems:
MSI P35 mainbord
Intel Core2 Duo E6850 (3.00GHz)
2X 1024 MB DDRII 800Mhz RAM
NVIDIA GeForce 8800 GTS
Seagate 500GB SATA II 16MB.

Thanks,
El Bandano

---

### Post by Pumalite on 2007-09-25
Try Alternate CD. ( your Nvidia is pretty new and might be a problem)

---

### Post by El Bandano on 2007-10-05
Thanks that solved the tty-error. But then it couldn't find my CD-drive.. 
I tried the 7.10 beta this morning and I got no more errors. It probably just needed the newer drivers.

---

### Post by Pumalite on 2007-10-05
Good for you!

---

