---
title: "VirtualBox kernel module fails for 2.6.27-7-generic"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by brianbourke75 on 2008-10-21
I have recently upgraded to 8.10 and for the most part things have gone fairly smoothly with the exception of VirtualBox (OSE).  I am having issues compiling the kernel module for 2.6.27-7-generic.  I have attempted to use the dkms methodology ...

 sudo dkms -m vboxdrv -v 2.0.2 -k 2.6.27-7-generic 

but this has failed.  Reading the make log produced, there appeared to be a kernel header missing (namely linux/bounds.h).  After poking around, i have read to try to "make prepare" the kernel source for external modules, but this has also failed.

brian@flitwick:/usr/src/linux-headers-2.6.27-7$ sudo make prepare
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[1]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make: *** [prepare0] Error 2

I am now unsure of how to continue... any help would be greatly appreciated.  

Brian

---

### Post by polig4e on 2008-10-30
I have the same problem when trying to compile Syntek WEBCAM modules, as it is not working on Ubuntu 8.10

I downloaded 8.10 release candidated - it didn't work. Today I upgraded the kernel using Update Manager, as 8.10 was released - again got the same error.

sudo make -f Makefile.standalone 

make -C /lib/modules/2.6.27-7-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'. Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [driver] Error 2

---

### Post by trampas on 2008-10-31
I have just ran into the same problem with 8.10 and VirtualBox. 

Trampas

---

### Post by chrisdeckard on 2008-10-31
My assumption is that you need more than just kernel header files, but that you need the actual kernel source.

> sudo apt-get install linux-source

-Chris

---

### Post by trampas on 2008-11-06
Chris, thanks for the help, but that did not work. I enabled the Pre-Released updates from the software sources then I was able to install the VirtualBox binary. 

Trampas

---

### Post by brianbourke75 on 2008-11-06
Well, I was able to rebuild the kernel module with the latest and greatest kernel source and headers in interpid by doing a full clean and build again.

Brian

---

### Post by james65535 on 2009-01-24
I'm somewhat new to linux, exactly how did you go about fixing this problem?

(trying to build mac80211)

---

### Post by brianbourke75 on 2009-01-24
Oh geeze, unfortunately I was forced to move onto VMware because I needed the DirectX implementation for my work project, so I don't exactly remember, but I will give it my best try.

first grap all the of kernel headers and source

sudo apt-get install linux-headers-2.6.27-7-generic
sudo apt-get install linux-source

then recompile the kernel module

sudo dkms build -m vboxdrv -v 2.0.2 -k 2.6.27-7-generic 

take it with a grain of salt, but that is vaguely what I remember doing.

Brian

---

