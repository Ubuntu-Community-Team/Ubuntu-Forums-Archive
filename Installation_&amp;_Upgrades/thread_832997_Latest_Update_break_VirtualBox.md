---
title: "Latest Update break VirtualBox"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by junkam on 2008-06-18
After the latest updates to Ubuntu 8 VirtualBox stopped working
I'm getting the following message

> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



I tried to reinstall the package virtualbox-ose-modules-generic but the problem still exists. 

HELP PLEASE

---

### Post by Joeb454 on 2008-06-18
From a terminal run ```
sudo /etc/init.d/vboxdrv setup
``` It should work then...you may have to reboot first, I'm not sure :)

---

### Post by junkam on 2008-06-18
When I run sudo /etc/init.d/vboxdrv setup
I get Usage: /etc/init.d/vboxdrv {start|stop|restart|status}

Doing  sudo /etc/init.d/vboxdrv restart
I get: 
* Stopping VirtualBox kernel module vboxdrv[OK ] 
 * Starting VirtualBox kernel module vboxdrv       
** * No suitable module for running kernel found.**

---

### Post by BARlotta on 2008-06-18
The virtualbox module for the new kernel is not available yet.  I am waiting for it as well.

As a workaround you can boot into the .18 kernel instead of the new .19.

---

### Post by junkam on 2008-06-18
Thank you

---

### Post by buntunub on 2008-06-18
> **Joeb454 said:**
> From a terminal run ```
sudo /etc/init.d/vboxdrv setup
``` It should work then...you may have to reboot first, I'm not sure :)

Without the new Kmod, this wont work. Not sure when I first started seeing posts about this as a fix, but it is completely wrong.

---

