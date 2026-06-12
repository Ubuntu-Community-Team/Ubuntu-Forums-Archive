---
title: "Audigy 2 Mess!! (newbie)"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by scaramonga on 2005-05-14
OK......tried the fix from this thread............to get sound from my Audigy 2.......

[http://ubuntuforums.org/showthread.php?t=21211&highlight=audigy](http://ubuntuforums.org/showthread.php?t=21211&highlight=audigy)

All ok up till I execute this command..............

sudo ./configure --with-cards=emu10k1 --with-sequencer=yes

The result is this................

```
/usr/src/alsa-driver-1.0.8$  sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
checking for gcc... gcc
checking for C compiler default output... a.out
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
checking for current directory... /usr/src/alsa-driver-1.0.8
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "yes"
cat: /usr/src/linux/include/linux/kmod.h: No such file or directory
checking for kernel linux/compiler.h... "no"
checking for kernel linux/pm.h... "no"
checking for kernel linux/spinlock.h... "no"
checking for kernel linux/irq.h... "no"
checking for kernel linux/threads.h... "no"
checking for kernel linux/rwsem.h... "no"
checking for kernel linux/gameport.h... "no"
checking for kernel linux/devfs_fs_kernel.h... "no"
checking for kernel linux/highmem.h... "no"
checking for kernel linux/workqueue.h... "no"
checking for kernel linux/dma-mapping.h... "no"
checking for kernel asm/hw_irq.h... "no"
checking for kernel linux/device.h... "no"
checking for kernel linux/jiffies.h... "no"
checking for kernel linux/compat.h... "no"
checking for kernel linux/adb.h... "no"
checking for kernel linux/cuda.h... "no"
checking for kernel linux/pmu.h... "no"
checking for kernel linux/moduleparam.h... "no"
checking for kernel linux/syscalls.h... "no"
checking for kernel linux/firmware.h... "no"
checking for exported symbol dump_stack... grep: /usr/src/linux/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "no"
checking for PCI support in kernel... "no"
checking for I2C driver in kernel... unknown
checking for firmware loader... unknown
checking for SGI/MIPS (HAL2) architecture... "no"
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... "unknown"
checking for SMP... "no"
checking for ISA PnP driver in kernel... no
checking for PnP driver in kernel... no
checking for ISA PnP support... yes
checking for strlcpy... "no"
checking for snprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for tty->count is the atomic type... "no"
checking for remap_pfn_range... "no"
checking for new remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for acpi_register_gsi... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
checking for driver version... 1.0.8
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for Procfs support... "no"
checking for USB support... "no"
checking for USB module support... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "no"
checking for PCMCIA module support... "no"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "no"
checking for parallel port module support... "no"
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard emu10k1
```

?????..............

When I type "alsamixer" it returns not a command..........infact anything to do with alsa is the same!!...........

Have tried reinstalling the alsa package.....no difference!!

Volume control lets me pick Audigy Alsa Sound etc...........but thats it!.........

Any ideas peeps??  :???:

---

### Post by scaramonga on 2005-05-15
Guess not?........... ](*,)  :-?

---

### Post by JorisK on 2005-05-15
[QUOTE=scaramonga]OK......tried the fix from this thread............to get sound from my Audigy 2.......

[http://ubuntuforums.org/showthread.php?t=21211&highlight=audigy](http://ubuntuforums.org/showthread.php?t=21211&highlight=audigy)

All ok up till I execute this command..............

sudo ./configure --with-cards=emu10k1 --with-sequencer=yes

The result is this................

```
/usr/src/alsa-driver-1.0.8$  sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
checking for gcc... gcc
checking for C compiler default output... a.out
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
checking for current directory... /usr/src/alsa-driver-1.0.8
checking cross compile...
checking for directory with kernel source... /usr/src/linux
checking for directory with kernel build...
checking for kernel version... 0.0.0
checking for GCC version... Kernel compiler:  Used compiler: gcc (GCC) 3.3.5 (Debian 1:3.3.5-8ubuntu2)

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... "no"
checking for existing ALSA module... "no"
checking for Red Hat kernel... "auto"
checking for Red Hat kernel... "no"
checking for SUSE kernel... "auto"
checking for SUSE kernel... "no"
checking to modify of kernel linux/kmod.h... "yes"
cat: /usr/src/linux/include/linux/kmod.h: No such file or directory
checking for kernel linux/compiler.h... "no"
checking for kernel linux/pm.h... "no"
checking for kernel linux/spinlock.h... "no"
checking for kernel linux/irq.h... "no"
checking for kernel linux/threads.h... "no"
checking for kernel linux/rwsem.h... "no"
checking for kernel linux/gameport.h... "no"
checking for kernel linux/devfs_fs_kernel.h... "no"
checking for kernel linux/highmem.h... "no"
checking for kernel linux/workqueue.h... "no"
checking for kernel linux/dma-mapping.h... "no"
checking for kernel asm/hw_irq.h... "no"
checking for kernel linux/device.h... "no"
checking for kernel linux/jiffies.h... "no"
checking for kernel linux/compat.h... "no"
checking for kernel linux/adb.h... "no"
checking for kernel linux/cuda.h... "no"
checking for kernel linux/pmu.h... "no"
checking for kernel linux/moduleparam.h... "no"
checking for kernel linux/syscalls.h... "no"
checking for kernel linux/firmware.h... "no"
checking for exported symbol dump_stack... grep: /usr/src/linux/kernel/ksyms.c: No such file or directory
"no"
checking for kernel module symbol versions... "no"
checking for PCI support in kernel... "no"
checking for I2C driver in kernel... unknown
checking for firmware loader... unknown
checking for SGI/MIPS (HAL2) architecture... "no"
checking for directory to store kernel modules... /lib/modules/0.0.0/misc
checking for verbose printk... on
checking for debug level... none
checking for processor type... "unknown"
checking for SMP... "no"
checking for ISA PnP driver in kernel... no
checking for PnP driver in kernel... no
checking for ISA PnP support... yes
checking for strlcpy... "no"
checking for snprintf... "no"
checking for scnprintf... "no"
checking for sscanf... "no"
checking for vmalloc_to_page... "no"
checking for old kmod... "yes"
checking for PDE... "no"
checking for pci_set_consistent_dma_mask... "no"
checking for pci_dev_present... "no"
checking for tty->count is the atomic type... "no"
checking for remap_pfn_range... "no"
checking for new remap_page_range... "no"
checking for kcalloc... "no"
checking for saved_config_space in pci_dev... "no"
checking for acpi_register_gsi... "no"
checking for old kill_fasync... "no"
checking for dma_addr_t... "no"
checking for MUTEX macros... "no"
checking for driver version... 1.0.8
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for RTC callback support in kernel... "no"
checking for Procfs support... "no"
checking for USB support... "no"
checking for USB module support... "no"
checking for kernel PCMCIA
checking for PCMCIA support... "no"
checking for PCMCIA module support... "no"
checking for PC9800 support in kernel... "no"
checking for parallel port support... "no"
checking for parallel port module support... "no"
checking for which soundcards to compile driver for... configure: error: Unsupported soundcard emu10k1
```

?????..............

When I type "alsamixer" it returns not a command..........infact anything to do with alsa is the same!!...........

Have tried reinstalling the alsa package.....no difference!!

Volume control lets me pick Audigy Alsa Sound etc...........but thats it!.........

Any ideas peeps??  :???:[/QUOTE]
 You should install the linux-headers-2.6.10-5-386 and linux-headers-2.6.10, check synaptic package manager...

But.. don't think this will guarantee work, i tried everything in that howto with a fresh install and still no sound...

---

### Post by scaramonga on 2005-05-15
>  You should install the linux-headers-2.6.10-5-386 and linux-headers-2.6.10 

Yup.........did that already buddy........... :-?

---

### Post by scaramonga on 2005-05-16
Damn!.....thx for reply m8.......was hoping to get this working eventually  :-?

---

