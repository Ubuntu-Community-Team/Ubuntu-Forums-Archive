---
title: "compiling epcam from source"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by lonemangx on 2011-05-13
I have a PD1001 creative webcam and found the epcam(v1.3.2) driver unfortunately there are no binaries and I have to compile it from source. Here is what the install file says:
```
To install epcam linux driver follow this:

1. Download the source files that are included in epcam-src-<version>.tar.gz
2. Open a terminal
3. Go the directory where you downloaded epcam-src-<version>.tar.gz
4. Make sure you have kernel development packages installed, otherwise you won't be able to build the driver from source files.
5. Type in your terminal each of the following commands:

	tar xfvz epcam-src-<version>.tar.gz
	make
	sudo make install
	sudo modprobe epcam

To deinstall the driver:

	sudo rmmod epcam
	sudo make uninstall

To clean up files created during the build:

	make clean
```

But I do get build errors:
```
Building EPCAM driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build  M=/home/homer/Downloads/epcam-src-1.3.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
  CC [M]  /home/homer/Downloads/epcam-src-1.3.2/drivers/usb/epcam.o
In file included from /home/homer/Downloads/epcam-src-1.3.2/drivers/usb/epcam.c:89:0:
/home/homer/Downloads/epcam-src-1.3.2/drivers/usb/epcam.h:5:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[2]: *** [/home/homer/Downloads/epcam-src-1.3.2/drivers/usb/epcam.o] Error 1
make[1]: *** [_module_/home/homer/Downloads/epcam-src-1.3.2] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [default] Error 2
```

I think the drivers should be into a specific directory because I can't find linux/videodev.h in the source folder. How do I know I have read/write access to the kernel source tree? What are the steps to modify the read/write access to kernel source tree? I am building this in the Downloads folder. I already have the build-essential and linux-headers installed. I have successfully compiled programs before like opencv, what's the difference now? What are the steps necessary to successfully compile this one?

---

### Post by lonemangx on 2011-05-14
I didn't find videodev.h inside  [FONT="Courier New"]'/usr/src/linux-headers-2.6.38-8-generic/include/linux'[/FONT] but I found videodev2.h. When I changed the source to include videodev2.h instead I get some function errors. Is there a way to get the videodev.h somehow? I'm building this on natty.

---

