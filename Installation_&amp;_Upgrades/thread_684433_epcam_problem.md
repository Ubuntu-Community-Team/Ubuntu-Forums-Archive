---
title: "epcam problem"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by Misbah Naveed on 2008-02-01
Hi
I am installing creative webcam model no PD1001 and chipset EP800 on RHEL4 and kernel version-2.6.9-42.after extracting epcam-src.0.7.3 source,at comipling time i get this error. 


root@localhost usb]# make
   Building EPCAM driver for 2.5/2.6 kernel.
   PLEASE IGNORE THE "Overriding SUBDIRS" WARNING
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/drivers/usb modules
make[1]: Entering directory `/usr/src/kernels/2.6.9-42.EL-i686'
make[2]: *** No rule to make target `/home/drivers/usb/drivers/usb/epcam.s', needed by `/home/drivers/usb/drivers/usb/epcam.o'.  Stop.
make[1]: *** [_module_/home/drivers/usb] Error 2
make[1]: Leaving directory `/usr/src/kernels/2.6.9-42.EL-i686'
make: *** [default] Error 2
 can someone pls help me what i do now?

---

