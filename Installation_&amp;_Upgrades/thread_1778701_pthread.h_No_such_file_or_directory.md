---
title: "pthread.h: No such file or directory"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by pauldemet on 2011-06-09
Need driver build help!! I have a driver that built successfully for Ubunutu 10.04.2 version 2.6.32. I upgraded to Ubuntu 11.04 and version 2.6.38, and now the driver will not build. I use some functions from pthread.h for interrupt support but now that include file cannot be found. If I move it and other required include files to the kernel include directory, the include files are now seen but this causes other errors with predefined values. The Makefile I use is here:
 
[SIZE=2]> 
[SIZE=2][SIZE=1]MAJOR = 110[/SIZE]
[SIZE=1]EXTRA_CFLAGS += -DMAJOR_NUM=$(MAJOR)[/SIZE]

[SIZE=1]ifneq ($(KERNELRELEASE),) # called by kbuild[/SIZE]
[SIZE=1]obj-m := uio48.o[/SIZE]
[SIZE=1]else # called from command line[/SIZE]
[SIZE=1]KERNEL_VERSION = `uname -r`[/SIZE]
[SIZE=1]KERNELDIR := /lib/modules/$(KERNEL_VERSION)/build[/SIZE]
[SIZE=1]PWD := $(shell pwd)[/SIZE]
[SIZE=1]MODULE_INSTALLDIR = /lib/modules/$(KERNEL_VERSION)/kernel/drivers/gpio/[/SIZE]

[SIZE=1]default:[/SIZE]
[SIZE=1]$(MAKE) -C $(KERNELDIR) M=$(PWD) modules[/SIZE]
[SIZE=1]uio48io.o: uio48io.c uio48.h Makefile[/SIZE]
[SIZE=1]gcc -c $(EXTRA_CFLAGS) uio48io.c[/SIZE]

[SIZE=1]all: default install poll flash[/SIZE]

[SIZE=1]install:[/SIZE]
[SIZE=1]mkdir -p $(MODULE_INSTALLDIR)[/SIZE]
[SIZE=1]rm -f $(MODULE_INSTALLDIR)uio48.ko[/SIZE]
[SIZE=1]install -c -m 0644 uio48.ko $(MODULE_INSTALLDIR)[/SIZE]
[SIZE=1]/sbin/depmod -a[/SIZE]

[SIZE=1]uninstall:[/SIZE]
[SIZE=1]rm -f $(MODULE_INSTALLDIR)uio48.ko[/SIZE]
[SIZE=1]/sbin/depmod -a[/SIZE]

[SIZE=1]flash: flash.c uio48.h uio48io.o Makefile[/SIZE]
[SIZE=1]gcc $(EXTRA_CFLAGS) -static flash.c uio48io.o -o flash[/SIZE]
[SIZE=1]chmod a+x flash[/SIZE]

[SIZE=1]poll: poll.c uio48.h uio48io.o Makefile[/SIZE]
[SIZE=1]gcc $(EXTRA_CFLAGS) -D_REENTRANT -static poll.c uio48io.o -o poll -lpthread[/SIZE]
[SIZE=1]chmod a+x poll[/SIZE]
[SIZE=1]endif[/SIZE]
 

[SIZE=1]clean:[/SIZE]
[SIZE=1]rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions /dev/uio48?[/SIZE]

[SIZE=1]spotless:[/SIZE]
[SIZE=1]rm -rf ioctl poll flash Module.* *.o *~ core .depend .*.cmd *.ko *.mod.c *.order .tmp_versions /dev/uio48?[/SIZE]
[/SIZE]
 
Has the diver build process changed? I cannot find anything that says it has. I know this is probably an easy problem but I cannot figure it out. I added -I/usr/include to the $(MAKE) command line but it didn't help either.
 
Please help!!
[/SIZE]

---

