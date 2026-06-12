---
title: "Installation of NexeonHD Frame Grabber Card"
date: 2011-09-05
forum: Installation &amp; Upgrades
---

### Post by gewinkler on 2011-09-05
Hi,

I never needed to install any drivers on a linux machine. Now I need your help!

I am running Ubuntu 11.04 32 Bit. I wanna install the drivers of a NexeonHD Frame Grabber Card. From the manufacturer I have got a dict_linux_342.tar.gz file. This is the content of this file:
dpict.a
libdpict.so.1
driver/dpdm642.c
driver/dpdm642.h
driver/dpdm642.mod.c
driver/dpdm642_load
driver/dpdm642_unload
driver/Makefile
include/dpict.h
include/dplinux.h

So I run make and get the following output:
```
make -C /lib/modules/2.6.38-11-generic-pae/build M=/home/esa/Desktop/nexeon_hd/dpict_linux_342/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
  CC [M]  /home/esa/Desktop/nexeon_hd/dpict_linux_342/driver/dpdm642.o
/home/esa/Desktop/nexeon_hd/dpict_linux_342/driver/dpdm642.c:612:5: error: unknown field ‘ioctl’ specified in initializer
/home/esa/Desktop/nexeon_hd/dpict_linux_342/driver/dpdm642.c:612:5: warning: initialization from incompatible pointer type
make[2]: *** [/home/esa/Desktop/nexeon_hd/dpict_linux_342/driver/dpdm642.o] Error 1
make[1]: *** [_module_/home/esa/Desktop/nexeon_hd/dpict_linux_342/driver] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
make: *** [all] Error 2

```OK, I choose to delete a line ```
.ioctl   =  drv_ioctl,
``` from dpdm642.c
I get the following output:
```
make -C /lib/modules/2.6.38-11-generic-pae/build M=/home/esa/Desktop/nexeon_hd/dpict_linux_342/driver modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
  CC [M]  /home/esa/Desktop/nexeon_hd/dpict_linux_342/driver/dpdm642.o
/home/esa/Desktop/nexeon_hd/dpict_linux_342/driver/dpdm642.c:326:12: warning: ‘drv_ioctl’ defined but not used
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/esa/Desktop/nexeon_hd/dpict_linux_342/driver/dpdm642.mod.o
  LD [M]  /home/esa/Desktop/nexeon_hd/dpict_linux_342/driver/dpdm642.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic-pae'

```The following files get created:
driver/dpdm642.ko
driver/dpdm642.mod.o
driver/dpdm642.o
driver/Module.symvers
driver/modules.order

Are these the required drivers? If so, where do I have to put them? 

I should add that the manufacturer confirmed that the card works with Ubuntu 11.04.

Please help me! I need this to work.

Greetings,
Georg

---

### Post by gewinkler on 2011-09-06
Ok, so I load dpdm642.ko via insmod commant. What to do with the other files_

---

