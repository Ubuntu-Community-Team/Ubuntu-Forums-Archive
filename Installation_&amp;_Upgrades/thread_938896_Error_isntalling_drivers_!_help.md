---
title: "Error isntalling drivers ! help"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by rokimoki on 2008-10-05
I'm installing Asus audio drivers and Xfi soundcard drivers... I get error in compiles...

**XFI Errors:**
```

Installation is in progress. Please wait...

checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /opt/Creative/XFiDrv_Linux_US-1.18/drivers
checking cross compile...
checking for directory with kernel source... /lib/modules/2.6.24-19-generic/build
checking for directory with kernel build...
checking for directory with ALSA include files... /lib/modules/2.6.24-19-generic/build/include
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.24-19-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... no
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.24-19-generic/kernel/sound
checking for ISA support in kernel... yes
checking for processor type... i586
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for Procfs support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new unlocked/compat_ioctl... no
configure: creating ./config.status
config.status: creating Makefile.conf
make: *** [all] Error 2
make: *** [install] Error 2
Installation Unsuccessful

```
**This is Installation Unsuccessful!!**
---------------
**ASUS Adio Errors:**
```

root@Al3X:/home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4# ./configure
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.24-19-generic/build
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 4.2.3 (Ubuntu 4.2.3-2ubuntu7)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking to modify of kernel linux/kmod.h... "no"
checking for kernel linux/compiler.h... "yes"
checking for kernel linux/pm.h... "yes"
checking for kernel linux/spinlock.h... "yes"
checking for kernel linux/irq.h... "yes"
checking for kernel linux/threads.h... "yes"
checking for kernel linux/rwsem.h... "yes"
checking for kernel linux/gameport.h... "yes"
checking for kernel linux/devfs_fs_kernel.h... "no"
checking for kernel linux/highmem.h... "yes"
checking for kernel linux/workqueue.h... "yes"
checking for kernel linux/dma-mapping.h... "yes"
checking for kernel asm/hw_irq.h... "yes"
checking for kernel linux/device.h... "yes"
checking for kernel linux/jiffies.h... "yes"
checking for kernel linux/compat.h... "yes"
checking for kernel linux/adb.h... "yes"
checking for kernel linux/cuda.h... "yes"
checking for kernel linux/pmu.h... "yes"
checking for exported symbol dump_stack... grep: /lib/modules/2.6.24-19-generic/build/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "yes"
checking for PCI support in kernel... "yes"
checking for Experimental drivers in kernel... "yes"
checking for SGI/MIPS (HAL2) architecture... "no"
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... i586
checking for SMP... "yes"
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... "yes"
checking for strlcpy... "no"
checking for snprintf... "no"
checking for scnprintf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for tty->count is the atomic type... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
checking for driver version... 1.0.4
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for USB support... "yes"
checking for kernel PCMCIA
checking for PCMCIA support... "yes"
checking for PC9800 support in kernel... "no"
checking for which soundcards to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
root@Al3X:/home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4# make
make[1]: se ingresa al directorio `/home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4/acore'
gcc -D__KERNEL__ -DMODULE=1 -I/home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4/include  -I/lib/modules/2.6.24-19-generic/build/include -O2 -mpreferred-stack-boundary=2 -march=i586 -D__SMP__ -DCONFIG_SMP -DLINUX -Wall -Wstrict-prototypes -fomit-frame-pointer -Wno-trigraphs -O2 -fno-strict-aliasing -fno-common -pipe -DALSA_BUILD -nostdinc -iwithprefix include  -E -D__GENKSYMS__ timer.c
| /sbin/genksyms -k 0.0.0 -p smp_  > /home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4/include/modules/acore__timer.ver.tmp
/bin/sh: /sbin/genksyms: not found
En el fichero incluído de timer.c:22:
/home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4/include/sound/driver.h:29:26: error: linux/config.h: No existe el fichero ó directorio
mv /home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4/include/modules/acore__timer.ver.tmp /home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4/include/modules/acore__timer.ver
copying file alsa-kernel/core/hwdep.c
/bin/sh: patch: not found
make[1]: *** [hwdep.c] Error 127
make[1]: se sale del directorio `/home/alejandro/Escritorio/ALC850_Linux_A27/alsa-driver-1.0.4/acore'
make: *** [compile] Error 1

```
**This is COMPILE ERROR**

Please help? :) I'm using ubuntu 8.04, any libc missing? THANKS!!

---

