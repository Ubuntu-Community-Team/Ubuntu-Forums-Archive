---
title: "ALSA-driver 1.0.13 compile error"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by icechen1 on 2007-05-20
Hi,i am trying to recompile my ALSA-driver but each ime i compile it i got a error,but when i am trying to compile the 1.0.14rc4 version of alsa-driver,it works fine.
Here is the error:
> icechen1@icechen1-laptop:/usr/src/alsa/alsa-driver-1.0.13$ sudo ./configure --with-cards=hda-intel --with-oss=yes
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.13
checking cross compile... 
checking for directory with kernel source... /lib/modules/2.6.20-15-generic/build
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.20-15-generic
checking for GCC version... Kernel compiler: gcc 4.1.2 (Ubuntu 4.1.2-0ubuntu4) Used compiler: gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
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
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.20-15-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
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
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.13
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... hda-intel
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
icechen1@icechen1-laptop:/usr/src/alsa/alsa-driver-1.0.13$ sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel --with-oss=yes 
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.13
checking cross compile... 
checking for directory with kernel source... /usr/src/linux-headers-2.6.20-15-generic
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.20-15-generic
checking for GCC version... Kernel compiler: gcc 4.1.2 (Ubuntu 4.1.2-0ubuntu4) Used compiler: gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
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
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.20-15-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
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
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.13
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... hda-intel
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
icechen1@icechen1-laptop:/usr/src/alsa/alsa-driver-1.0.13$ sudo make
make dep
make[1]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/acore'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/acore/ioctl32'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/acore/ioctl32'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/acore/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/acore/oss'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/acore/seq'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/acore/seq/instr'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/acore/seq/instr'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/acore/seq/oss'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/acore/seq/oss'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/acore/seq'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/acore'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/i2c'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/i2c/other'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/i2c/other'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/i2c'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/drivers'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/mpu401'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/mpu401'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/opl3'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/opl3'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/opl4'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/opl4'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/pcsp'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/pcsp'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/drivers/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/drivers'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa/ad1816a'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa/ad1816a'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa/ad1848'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa/ad1848'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa/cs423x'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa/cs423x'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa/es1688'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa/es1688'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa/gus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa/gus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa/msnd'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa/msnd'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa/opti9xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa/opti9xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa/sb'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa/sb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/isa/wavefront'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa/wavefront'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/isa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/synth'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/synth/emux'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/synth/emux'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/synth'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ac97'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ac97'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ali5451'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ali5451'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/asihpi'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/asihpi'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/au88x0'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/au88x0'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ca0106'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ca0106'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/cs46xx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/cs46xx'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/cs5535audio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/cs5535audio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/echoaudio'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/echoaudio'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/emu10k1'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/emu10k1'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/hda'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/hda'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ice1712'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ice1712'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/korg1212'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/korg1212'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/mixart'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/mixart'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/nm256'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/nm256'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/pcxhr'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/pcxhr'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/pdplus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/pdplus'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/riptide'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/riptide'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/rme9652'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/rme9652'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/trident'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/trident'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/vx222'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/vx222'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ymfpci'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci/ymfpci'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pci'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/aoa'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/codecs'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/codecs'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/core'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/core'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/fabrics'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/fabrics'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/soundbus'
make[4]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/aoa/soundbus'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/aoa'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/usb'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/usb/usx2y'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/usb/usx2y'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/usb'
make[2]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pcmcia'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pcmcia/pdaudiocf'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pcmcia/pdaudiocf'
make[3]: Entering directory `/usr/src/alsa/alsa-driver-1.0.13/pcmcia/vx'
make[3]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pcmcia/vx'
make[2]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13/pcmcia'
make[1]: Leaving directory `/usr/src/alsa/alsa-driver-1.0.13'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/usr/src/alsa/alsa-driver-1.0.13  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.o
In file included from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.o] Error 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.13/acore] Error 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.13] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2


---

### Post by icechen1 on 2007-05-20
Hello,i think i just fixed the issue :KS ,i used the alsa 1.0.14rc4's driver and now i get sound.
I found that my kernel is not supported by alsa-driver 1.0.13 in a file called SUPPORTED_KERNEL.

---

### Post by Ted Nancy on 2007-06-02
> **icechen1 said:**
> Hello,i think i just fixed the issue :KS ,i used the alsa 1.0.14rc4's driver and now i get sound.
I found that my kernel is not supported by alsa-driver 1.0.13 in a file called SUPPORTED_KERNEL.

What does this mean? Someone pointed me to this site for a solution to my alsa not compiling properly.

---

### Post by albox on 2007-06-10
Hi,
I really need to re-compile the 1.0.13 driver (the one I was using before upgrading to Feisty) since the 1.0.14 doesn't work. Is there a way to compile ?

Thanks ;)

---

