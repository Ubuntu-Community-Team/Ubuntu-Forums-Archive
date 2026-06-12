---
title: "Problem with old Hardware Driver"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by kaede15 on 2007-12-04
Hi everyone, I installed Xubuntu with a PCI IDE card to add a couple of HDDs. The card is a HighPoint RocketRAID 372A with 2 IDE output and the new drives are 2 IBM 120GB. I know that the card is very old but it works flawless with win2k.

Im new in Linux, a friend of mine told me that Xubuntu is great with slow machines and I have this P3 800Mhz with 512MB and a GeForce2 MX 400 sleeping in the closet, so I gave it a try. Everything works perfectly and I even installed Compiz :-) but the I get stuck after adding this expansion card.

My main objective is to use a JBOD configuration to get maximum amount of space possible [NOT RAID0 just JBOD] so the first thing I did was to create a JBOD in the bios of the expansion card. After that I checked it with the Partion Magic Pro 8 to make sure that the system sees it as a SINGLE disk and I didn't format it. Everything is ok so far.

In terminal I run the "fdisk -l" command and this came up:

[COLOR="DarkOrchid"]Disk /dev/hda[/COLOR]: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8500c898
   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4795    38515806   83  Linux
/dev/hda2            4796        4982     1502077+   f  W95 Ext'd (LBA)
/dev/hda5            4796        4982     1502046   82  Linux swap / Solaris
[COLOR="DarkOrchid"]Disk /dev/hde[/COLOR]: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000
   Device Boot      Start         End      Blocks   Id  System
[COLOR="DarkOrchid"]Disk /dev/hdg[/COLOR]: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

As you can see there are 3 hdds the first one is the 40Gb disk that I use to install the OS and the hde and hdg are the new drives. The OS did not see it as a Single disk... so I figure that must be a driver problem. And google for driver:
[http://www.highpoint-tech.com/](http://www.highpoint-tech.com/) under Support --> Bios+Driver --> RocketRAID 133
Since there isn't any build for ubuntu I assumed that I have to download the Linux driver. Here is where I am totally clueless. I found the readme file:

```
This package contains Linux driver source code for HighPoint
 HPT370/370A/372/372A/372N/302/302N ATA RAID 
controllers and RocketRAID 1520  SATA RAID controllers.
 The source code is for kernel updating purposes - 
you can use this  source code to build a driver, if you cannot 
find one in HighPoint Linux driver release package. 
``` :( :confused:

```
2. Build the driver

---------------------

  

  1) Install kernel build tools (gcc, binutils, make, etc.)

  

  2) Setup the kernel source/headers

  

     To build driver modules for a specific kernel, you shall use same 

     configuration for the kernel and the driver. Otherwise, the driver may 

     be unable to load, or behave abnormally.

     

     - For Linux kernel 2.6 -

     

     On most distributions based on kernel 2.6, an exploded source tree is not

     required to build a driver against the currently in-use kernel. As long

     as the system has kernel headers setup under /lib/modules/`uname -r`/build,

     you can simply run "make" to build the driver.



     If you want to build the driver against a custom kernel source, you must

     setup the kernel source manually and run "make" under kernel source tree

     to setup kernel headers.



     - For Linux kernel 2.4 -

     

     You need a full kernel source tree to build the driver. If you are building

     a driver for the currently in-use kernel, the kernel source should match

     the version of the running kernel. In addition, you must obtain the config

     file for the running kernel:

     

        For Red Hat or Fedora Linux, you can find the stock kernel config files

        under {kernel-source-dir}/configs, named kernel-*.config. Select the one

        matches your hardware and copy it to {kernel-source-dir}/.config.

        

        For SuSE Linux, the config files for current kernel is under /boot dir

        so you can the kernel source by

        

            # cd /usr/src/linux-{kernel-version}.SuSE

            # cp /boot/vmlinuz.config .config

            # cp /boot/vmlinuz.version.h include/linux/version.h

            # cp /boot/vmlinuz.autoconf.h include/linux/autoconf.h



        For other distributions please refer to the distribution documents to 

        obtain the config file.

        

        If you are building a custom kernel and a driver, you can setup the kernel

        config by yourself, using "make config" or "make menuconfig" commands

        under kernel source directory.

        

     Once the kernel config file is ready, run following commands under kernel

     source directory to setup kernel headers:

     

            # make oldconfig

            # make dep

        

     On some Red Hat versions, {kernel-source-dir}/include/linux/modversions.h

     may be incorrect after "make dep", you need check if there is a line 

     "#include <linux/rhconfig.h>" before "#include <linux/modsetver.h>" in that

     file. If not, please add the line manually.



     Users need to install the kernel source package and setup kernel

     headers with proper configuration before building the driver.

   

     You shall use same configuration for the kernel and the driver.

     Otherwise the driver may be unable to load or work abnormally.



     If you are using stock kernel, obtain the configuration in your Linux

     distribution (e.g. the kernel configuration file for Red Hat stock kernel

     can be found under "configs" directory in kernel source tree). Copy the

     configuration file to <your-kernel-source-dir>/.config and setup the

     kernel headers using "make oldconfig" and "make dep" commands before you

     build the driver.

     

     Please refer to the documents in your Linux distribution for kernel

     configuration.



     If the kernel contains built-in IDE support for your HPT3xx controller,

     you must rebuild and install a kernel without HPT37x controller support

     before using this driver. Please refer to kernel documents for how to 

     configure/update the kernel.

     

  2) Extract the driver files to somewhere. e.g. /usr/src/hpt37x2



  3) Build the driver:



        # cd /usr/src/hpt37x2

        # make KERNELDIR=/usr/src/linux-2.6.4-52-default

        

     Available make options:

     

       KERNELDIR=...

           Specify kernel source directory. If not specified the driver will

           use /lib/modules/{kernel-version}/build/ as the default location.

           This option is needed if you have a manually configured kernel

           source tree.

           

       RR1520=

           RR1520=1 for RocketRAID 1520 SATA controller. (Default)

           RR1520=0 for HPT3xx based PATA RAID controllers.

     

       NON_RAID=

           NON_RAID=0 to build the driver with RAID support.(Default)

           NON_RAID=1 to build the driver without RAID support.



     

3. Using the driver

---------------------

    

  1) Load module "scsi_mod" and "sd_mod" if they are not built into kernel:



        # modprobe sd_mod



  2) Load the driver.

        

        # insmod ./hpt37x2.o



     For kernel 2.6, the driver module is "hpt37x2.ko". Also you need to use 

     the 2.5/2.6 module-init-tools (you can get them from

     http://www.kernel.org/pub/linux/kernel/people/rusty/modules/).

     modutils from 2.4 won't work with 2.5/2.6. 


```

ok now Im totally lost. I get the extract the files part, although i couldn't extract to that particular directory because the file roller keeps telling me that I don't have permission to do that, I extract it to my home dir. But after that I don't know how to continue:
# make KERNELDIR=/usr/src/linux-2.6.4-52-default  :confused::confused:
Xubuntu only has 2 dirs in src and none of them is linux-2.6.4-52-default

Anyone can help with this?? 
Thanks in advance!!

---

### Post by PmDematagoda on 2007-12-04
Did you simply try running:-
```

make
```

in the folder containing the driver since it states that:-

```
     - For Linux kernel 2.6 -

     

     On most distributions based on kernel 2.6, an exploded source tree is not

     required to build a driver against the currently in-use kernel. As long

     as the system has kernel headers setup under /lib/modules/`uname -r`/build,

     you can simply run "make" to build the driver.
```

Assuming that you have Ubuntu 6.06 or greater which runs on Linux Kernel 2.6, you should be able to install the driver quite easily.

---

### Post by kaede15 on 2007-12-04
thank for the quick response!!!  I input the "make" command:

```

[SIZE="2"][SIZE="1"]gcc -DDRIVER_VERSION=\"2.1.060607\" -DLIST_H_INCLUDED -DMODVERSIONS -DMODULE -DLINUX -D_LINUX_ -D__KERNEL__=1 -DCONFIG_PCI -DNO_CROSS_CTRL=1 -DSUPPORT_ARRAY -DDBG=0 -Wall -O2 -Wstrict-prototypes -fomit-frame-pointer -I. -I/lib/modules/2.6.22-14-generic/build/include -I/lib/modules/2.6.22-14-generic/build/drivers/scsi -c hpt.c -o hpt.o

hpt.c:1:26: error: linux/config.h: No such file or directory

In file included from /lib/modules/2.6.22-14-generic/build/include/asm/thread_info.h:16,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/thread_info.h:21,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/preempt.h:9,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/spinlock.h:49,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/capability.h:47,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:46,

                 from hpt.c:8:

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:83: error: requested alignment is not a constant

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h: In function ‘cpuid_count’:

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness

/lib/modules/2.6.22-14-generic/build/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:51,

                 from hpt.c:8:

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:33:3: error: #error You lose.

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

/lib/modules/2.6.22-14-generic/build/include/linux/jiffies.h:225:31: error: division by zero in #if

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/aio.h:5,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/sched.h:273,

                 from hpt.c:8:

/lib/modules/2.6.22-14-generic/build/include/linux/workqueue.h: In function ‘cancel_delayed_work’:

/lib/modules/2.6.22-14-generic/build/include/linux/workqueue.h:165: warning: dereferencing type-punned pointer will break strict-aliasing rules

In file included from hpt.c:8:

/lib/modules/2.6.22-14-generic/build/include/linux/sched.h: In function ‘dequeue_signal_lock’:

/lib/modules/2.6.22-14-generic/build/include/linux/sched.h:1337: warning: implicit declaration of function ‘local_irq_save’

/lib/modules/2.6.22-14-generic/build/include/linux/sched.h:1339: warning: implicit declaration of function ‘local_irq_restore’

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/module.h:21,

                 from hpt.c:9:

/lib/modules/2.6.22-14-generic/build/include/asm/module.h:64:2: error: #error unknown processor family

In file included from hpt.c:17:

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h: In function ‘virt_to_head_page’:

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: warning: implicit declaration of function ‘__pfn_to_page’

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: error: (Each undeclared identifier is reported only once

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: error: for each function it appears in.)

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:291: warning: initialization makes pointer from integer without a cast

In file included from hpt.c:17:

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h: In function ‘lowmem_page_address’:

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:560: warning: implicit declaration of function ‘__page_to_pfn’

/lib/modules/2.6.22-14-generic/build/include/linux/mm.h:560: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/irq.h:23,

                 from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,

                 from hpt.c:18:

/lib/modules/2.6.22-14-generic/build/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory

In file included from /lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:5,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,

                 from hpt.c:18:

/lib/modules/2.6.22-14-generic/build/include/linux/irq.h: At top level:

/lib/modules/2.6.22-14-generic/build/include/linux/irq.h:178: error: ‘NR_IRQS’ undeclared here (not in a function)

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/hardirq.h:7,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:11,

                 from hpt.c:18:

/lib/modules/2.6.22-14-generic/build/include/asm/hardirq.h:12: error: requested alignment is not a constant

In file included from hpt.c:18:

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h: In function ‘cli’:

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:221: warning: implicit declaration of function ‘local_irq_disable’

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h: In function ‘sti’:

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:225: warning: implicit declaration of function ‘local_irq_enable’

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h: In function ‘save_flags’:

/lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:229: warning: implicit declaration of function ‘local_save_flags’

In file included from hpt.c:23:

/lib/modules/2.6.22-14-generic/build/include/linux/pci.h: In function ‘pci_register_driver’:

/lib/modules/2.6.22-14-generic/build/include/linux/pci.h:604: error: ‘KBUILD_MODNAME’ undeclared (first use in this function)

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/dmapool.h:14,

                 from /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:621,

                 from hpt.c:23:

/lib/modules/2.6.22-14-generic/build/include/asm/io.h: In function ‘virt_to_phys’:

/lib/modules/2.6.22-14-generic/build/include/asm/io.h:77: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)

/lib/modules/2.6.22-14-generic/build/include/asm/io.h: In function ‘phys_to_virt’:

/lib/modules/2.6.22-14-generic/build/include/asm/io.h:95: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)

In file included from /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:767,

                 from hpt.c:23:

/lib/modules/2.6.22-14-generic/build/include/asm/pci.h: In function ‘pci_dac_dma_to_page’:

/lib/modules/2.6.22-14-generic/build/include/asm/pci.h:72: warning: return makes pointer from integer without a cast

hpt.c: In function ‘get_bdev’:

hpt.c:136: warning: implicit declaration of function ‘bdget’

hpt.c:136: warning: initialization makes pointer from integer without a cast

hpt.c:137: warning: implicit declaration of function ‘blkdev_get’

hpt.c:138: error: dereferencing pointer to incomplete type

hpt.c:141: warning: implicit declaration of function ‘blkdev_put’

In file included from hpt.c:185:

entry.c: At top level:

entry.c:20: error: ‘UTS_RELEASE’ undeclared here (not in a function)

In file included from hpt.c:185:

entry.c: In function ‘Check_Idle_Call’:

entry.c:216: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘Queue_SC’:

entry.c:225: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:228: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘Release_SC’:

entry.c:238: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:242: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:243: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:245: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘scsicmd_buf_get’:

entry.c:271: error: ‘OS_KMAP_TYPE’ undeclared (first use in this function)

entry.c:271: error: incompatible type for argument 2 of ‘kmap_atomic’

entry.c: In function ‘do_mode_sense’:

entry.c:354: error: ‘Scsi_Cmnd’ has no member named ‘bufflen’

entry.c:354: warning: initialization makes integer from pointer without a cast

entry.c:372: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘OsSendCommand’:

entry.c:439: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:455: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:521: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘internal_done’:

entry.c:608: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘hpt3xx_Command’:

entry.c:621: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:624: error: ‘CONFIG_HZ’ undeclared (first use in this function)

entry.c:624: error: invalid operands to binary *

entry.c:624: warning: assignment makes integer from pointer without a cast

entry.c:625: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:627: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘hpt3xx_Detect’:

entry.c:715: warning: ‘pci_find_device’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:477)

entry.c:747: warning: ‘pci_find_device’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:477)

entry.c:778: warning: ‘pci_find_device’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/pci.h:477)

entry.c:823: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:66)

entry.c:823: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type

entry.c:824: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:66)

entry.c:824: warning: ‘deprecated_irq_flag’ is deprecated (declared at /lib/modules/2.6.22-14-generic/build/include/linux/interrupt.h:66)

entry.c:824: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type

entry.c: In function ‘hpt3xx_Reset’:

entry.c:915: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘fOsBuildSgl’:

entry.c:1112: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1113: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1116: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1118: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1123: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1127: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1128: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1130: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1132: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘fOsCommandDone’:

entry.c:1146: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c:1157: warning: dereferencing type-punned pointer will break strict-aliasing rules

entry.c: In function ‘__check_autorebuild’:

entry.c:1700: warning: pointer targets in return differ in signedness

In file included from hpt.c:186:

hptproc.c: In function ‘get_sd_name’:

hptproc.c:503: error: dereferencing pointer to incomplete type

hptproc.c:503: error: request for member ‘disk_name’ in something not a structure or union

In file included from ioctl.c:6,

                 from hpt.c:187:

gui_lib.c: In function ‘hpt_get_controller_info’:

gui_lib.c:427: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

gui_lib.c:440: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

gui_lib.c:446: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

gui_lib.c:451: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

gui_lib.c:464: warning: pointer targets in passing argument 1 of ‘strcpy’ differ in signedness

In file included from hpt.c:187:

ioctl.c: In function ‘timer_start_for_cmd’:

ioctl.c:197: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:197: error: invalid operands to binary *

ioctl.c:197: warning: assignment makes integer from pointer without a cast

ioctl.c: In function ‘Kernel_DeviceIoControl’:

ioctl.c:476: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:476: error: invalid operands to binary *

ioctl.c:476: warning: assignment makes integer from pointer without a cast

ioctl.c: In function ‘hpt_set_array_state’:

ioctl.c:521: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:521: error: invalid operands to binary *

ioctl.c:521: warning: assignment makes integer from pointer without a cast

ioctl.c: In function ‘hpt_rescan_all’:

ioctl.c:658: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:658: error: invalid operands to binary *

ioctl.c:658: warning: assignment makes integer from pointer without a cast

ioctl.c: In function ‘hpt_rebuild_data_block’:

ioctl.c:898: error: ‘CONFIG_HZ’ undeclared (first use in this function)

ioctl.c:898: error: invalid operands to binary *

ioctl.c:898: warning: passing argument 1 of ‘schedule_timeout’ makes integer from pointer without a cast

make: *** [hpt.o] Error 1[/SIZE][/SIZE]

```

So... what just happened?? it didnt work, did it? is it beacause it was extracted in my home directory??
This is my first Linux PC so Im totally clueless!! plz HELP!!

---

### Post by kaede15 on 2007-12-04
Anyone know what just happened??

---

### Post by kaede15 on 2007-12-07
Ok, I after days of researching looks like a lot of people has problem with this driver, but no solution at all, well at least from what Ive seen.

Eventually I came up with a new solution... sort of... lets start shall we?

1. Forget the RAID function, cuz without the hpt37x2.o you cant use it BUT I did manage to use the JBOD setting [good enough for me].

2. Setup the JBOD configuration in your cards Bios first.

3. Use any Partition tool that comes with a bootable CD, I use "Partition Magic 8"  that came with Hiren's Boot CD.

4. Select the JBOD disk (you should see only 1 disk instead of 2 or more) and CREATE A NTFS LOGICAL partition with a LABEL.

5. After reboot, login to your Xubuntu desktop it should show the new partition BUT if you try to open it, it would say that cannot be mounted bla bla bla. To fix that just right click on the disk and then click on mount and then you can open it  like a normal partition. For me thats 230GB created with 2 120GB disks. Good enough for downloading stuffs 

[Tried with FAT32 first but the partition cannot exceed the 200GB limit]

Conclusion: The entire idea is to build a server that runs Samba, torrent, ED2K, KAD, FTP and HTTP and of course all data goes to my 2 old 120GB disks via HPT card. And the eyecandy compiz with my GeForce2 MX in such a low profile PC is a total bonus.
Still with this partial solution I fear that some day the data cannot be access and 230GB, just say 50GB of music or movies lost that would be a catastrophe. Therefore I would go back to Winxp and deal with it. 

Personal note: I have nothing against linux, in fact I think it is a fantastic OS and the destktop sure is way far superior than Windows. But the lack of documentation and support for some drivers makes me wonder if tomorrow I buy a new hardware the first thing I should check  if there is any support for my distro... if not.. well, you can take the chances compiling one for yourself. I don't think that is an easy task for someone new like me. Therefore I think Windows won this round for easiness of driver installation.

---

### Post by screaminglucy on 2008-01-05
I have Highpoint RocketRaid 454 which uses hpt374 driver.

I followed the howto at:
[http://stefan.freyr.org/?page_id=6]("http://stefan.freyr.org/?page_id=6")
with the latest driver from Highpoint

To get it working in the ubuntu 7.10 however I had to modify the source a little bit.

1. In entry.c I I added:

```
#define OS_KMAP_TYPE KM_BIO_SRC_IRQ 
```

to fix the OS_KMAP_TYPE undefined error

2. Commented out the include for  linux/config.h in hpt.c like so:
```
//#include <linux/config.h>
```

---

### Post by bench on 2008-04-06
Did anyone get anywhere with this?  I'm trying to compile the hpt37x2 on gutsy server(2.6.22-14-server).  I commented out the config.h entry as suggested here, but I just get a lot of compile errors - the same as the OP.

```
root@XXXXXX:/usr/src/hpt37x2# make KERNEL_DIR=/usr/src/linux-headers-2.6.22-14-server/ RR1520=0 NON_RAID=0
gcc -DDRIVER_VERSION=\"2.1.060607\" -DLIST_H_INCLUDED -DMODVERSIONS -DMODULE -DLINUX -D_LINUX_ -D__KERNEL__=1 -DCONFIG_PCI -DNO_CROSS_CTRL=1 -DDBG=0 -Wall -O2 -Wstrict-prototypes -fomit-frame-pointer -I. -I/lib/modules/2.6.22-14-server/build/include -I/lib/modules/2.6.22-14-server/build/drivers/scsi -c hpt.c -o hpt.o
In file included from /lib/modules/2.6.22-14-server/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.22-14-server/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.22-14-server/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.22-14-server/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.22-14-server/build/include/linux/capability.h:47,
                 from /lib/modules/2.6.22-14-server/build/include/linux/sched.h:46,
                 from hpt.c:8:
/lib/modules/2.6.22-14-server/build/include/asm/processor.h:83: error: âCONFIG_X86_L1_CACHE_SHIFTâ undeclared here (not in a function)
/lib/modules/2.6.22-14-server/build/include/asm/processor.h:83: error: requested alignment is not a constant
/lib/modules/2.6.22-14-server/build/include/asm/processor.h: In function âcpuid_countâ:
/lib/modules/2.6.22-14-server/build/include/asm/processor.h:618: warning: pointer targets in passing argument 1 of ânative_cpuidâ differ in signedness
/lib/modules/2.6.22-14-server/build/include/asm/processor.h:618: warning: pointer targets in passing argument 2 of ânative_cpuidâ differ in signedness
/lib/modules/2.6.22-14-server/build/include/asm/processor.h:618: warning: pointer targets in passing argument 3 of ânative_cpuidâ differ in signedness
/lib/modules/2.6.22-14-server/build/include/asm/processor.h:618: warning: pointer targets in passing argument 4 of ânative_cpuidâ differ in signedness
In file included from /lib/modules/2.6.22-14-server/build/include/linux/sched.h:51,
                 from hpt.c:8:
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:33:3: error: #error You lose.
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
/lib/modules/2.6.22-14-server/build/include/linux/jiffies.h:225:31: error: division by zero in #if
In file included from /lib/modules/2.6.22-14-server/build/include/linux/aio.h:5,
                 from /lib/modules/2.6.22-14-server/build/include/linux/sched.h:273,
                 from hpt.c:8:
/lib/modules/2.6.22-14-server/build/include/linux/workqueue.h: In function âcancel_delayed_workâ:
/lib/modules/2.6.22-14-server/build/include/linux/workqueue.h:165: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from hpt.c:8:
/lib/modules/2.6.22-14-server/build/include/linux/sched.h: In function âdequeue_signal_lockâ:
/lib/modules/2.6.22-14-server/build/include/linux/sched.h:1337: warning: implicit declaration of function âlocal_irq_saveâ
/lib/modules/2.6.22-14-server/build/include/linux/sched.h:1339: warning: implicit declaration of function âlocal_irq_restoreâ
In file included from /lib/modules/2.6.22-14-server/build/include/linux/module.h:21,
                 from hpt.c:9:
/lib/modules/2.6.22-14-server/build/include/asm/module.h:64:2: error: #error unknown processor family
In file included from hpt.c:17:
/lib/modules/2.6.22-14-server/build/include/linux/mm.h: In function âvirt_to_head_pageâ:
/lib/modules/2.6.22-14-server/build/include/linux/mm.h:291: warning: implicit declaration of function â__pfn_to_pageâ
/lib/modules/2.6.22-14-server/build/include/linux/mm.h:291: error: âCONFIG_PAGE_OFFSETâ undeclared (first use in this function)
/lib/modules/2.6.22-14-server/build/include/linux/mm.h:291: error: (Each undeclared identifier is reported only once
/lib/modules/2.6.22-14-server/build/include/linux/mm.h:291: error: for each function it appears in.)
/lib/modules/2.6.22-14-server/build/include/linux/mm.h:291: warning: initialization makes pointer from integer without a cast
In file included from hpt.c:17:
/lib/modules/2.6.22-14-server/build/include/linux/mm.h: In function âlowmem_page_addressâ:
/lib/modules/2.6.22-14-server/build/include/linux/mm.h:560: warning: implicit declaration of function â__page_to_pfnâ
/lib/modules/2.6.22-14-server/build/include/linux/mm.h:560: error: âCONFIG_PAGE_OFFSETâ undeclared (first use in this function)
In file included from /lib/modules/2.6.22-14-server/build/include/linux/irq.h:23,
                 from /lib/modules/2.6.22-14-server/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-server/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-server/build/include/linux/interrupt.h:11,
                 from hpt.c:18:
/lib/modules/2.6.22-14-server/build/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.22-14-server/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.22-14-server/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-server/build/include/linux/interrupt.h:11,
                 from hpt.c:18:
/lib/modules/2.6.22-14-server/build/include/linux/irq.h: At top level:
/lib/modules/2.6.22-14-server/build/include/linux/irq.h:178: error: âNR_IRQSâ undeclared here (not in a function)
In file included from /lib/modules/2.6.22-14-server/build/include/linux/hardirq.h:7,
                 from /lib/modules/2.6.22-14-server/build/include/linux/interrupt.h:11,
                 from hpt.c:18:
/lib/modules/2.6.22-14-server/build/include/asm/hardirq.h:12: error: requested alignment is not a constant
In file included from hpt.c:18:
/lib/modules/2.6.22-14-server/build/include/linux/interrupt.h: In function âcliâ:
/lib/modules/2.6.22-14-server/build/include/linux/interrupt.h:221: warning: implicit declaration of function âlocal_irq_disableâ
/lib/modules/2.6.22-14-server/build/include/linux/interrupt.h: In function âstiâ:
/lib/modules/2.6.22-14-server/build/include/linux/interrupt.h:225: warning: implicit declaration of function âlocal_irq_enableâ
/lib/modules/2.6.22-14-server/build/include/linux/interrupt.h: In function âsave_flagsâ:
/lib/modules/2.6.22-14-server/build/include/linux/interrupt.h:229: warning: implicit declaration of function âlocal_save_flagsâ
In file included from hpt.c:23:
/lib/modules/2.6.22-14-server/build/include/linux/pci.h: In function âpci_register_driverâ:
/lib/modules/2.6.22-14-server/build/include/linux/pci.h:604: error: âKBUILD_MODNAMEâ undeclared (first use in this function)
In file included from /lib/modules/2.6.22-14-server/build/include/linux/dmapool.h:14,
                 from /lib/modules/2.6.22-14-server/build/include/linux/pci.h:621,
                 from hpt.c:23:
/lib/modules/2.6.22-14-server/build/include/asm/io.h: In function âvirt_to_physâ:
/lib/modules/2.6.22-14-server/build/include/asm/io.h:77: error: âCONFIG_PAGE_OFFSETâ undeclared (first use in this function)
/lib/modules/2.6.22-14-server/build/include/asm/io.h: In function âphys_to_virtâ:
/lib/modules/2.6.22-14-server/build/include/asm/io.h:95: error: âCONFIG_PAGE_OFFSETâ undeclared (first use in this function)
In file included from /lib/modules/2.6.22-14-server/build/include/linux/pci.h:767,
                 from hpt.c:23:
/lib/modules/2.6.22-14-server/build/include/asm/pci.h: In function âpci_dac_dma_to_pageâ:
/lib/modules/2.6.22-14-server/build/include/asm/pci.h:72: warning: return makes pointer from integer without a cast
In file included from hpt.c:185:
entry.c: At top level:
entry.c:20: error: âUTS_RELEASEâ undeclared here (not in a function)
In file included from hpt.c:185:
entry.c: In function âCheck_Idle_Callâ:
entry.c:215: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function âQueue_SCâ:
entry.c:224: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:226: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:226: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:227: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function âRelease_SCâ:
entry.c:237: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:241: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:242: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:244: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:244: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function âscsicmd_buf_getâ:
entry.c:270: error: âOS_KMAP_TYPEâ undeclared (first use in this function)
entry.c:270: error: incompatible type for argument 2 of âkmap_atomicâ
entry.c: In function âdo_mode_senseâ:
entry.c:353: error: âScsi_Cmndâ has no member named âbufflenâ
entry.c:353: warning: initialization makes integer from pointer without a cast
entry.c:371: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function âOsSendCommandâ:
entry.c:438: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:454: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:520: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function âinternal_doneâ:
entry.c:607: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function âhpt3xx_Commandâ:
entry.c:620: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:623: error: âCONFIG_HZâ undeclared (first use in this function)
entry.c:623: error: invalid operands to binary *
entry.c:623: warning: assignment makes integer from pointer without a cast
entry.c:624: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:626: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function âhpt3xx_Detectâ:
entry.c:714: warning: âpci_find_deviceâ is deprecated (declared at /lib/modules/2.6.22-14-server/build/include/linux/pci.h:477)
entry.c:746: warning: âpci_find_deviceâ is deprecated (declared at /lib/modules/2.6.22-14-server/build/include/linux/pci.h:477)
entry.c:777: warning: âpci_find_deviceâ is deprecated (declared at /lib/modules/2.6.22-14-server/build/include/linux/pci.h:477)
entry.c:822: warning: âdeprecated_irq_flagâ is deprecated (declared at /lib/modules/2.6.22-14-server/build/include/linux/interrupt.h:66)
entry.c:822: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
entry.c:823: warning: âdeprecated_irq_flagâ is deprecated (declared at /lib/modules/2.6.22-14-server/build/include/linux/interrupt.h:66)
entry.c:823: warning: âdeprecated_irq_flagâ is deprecated (declared at /lib/modules/2.6.22-14-server/build/include/linux/interrupt.h:66)
entry.c:823: warning: passing argument 2 of ârequest_irqâ from incompatible pointer type
entry.c: In function âhpt3xx_Resetâ:
entry.c:914: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function âfOsBuildSglâ:
entry.c:1111: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1112: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1115: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1117: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1122: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1126: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1127: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1129: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1131: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function âfOsCommandDoneâ:
entry.c:1145: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c:1156: warning: dereferencing type-punned pointer will break strict-aliasing rules
entry.c: In function â__check_autorebuildâ:
entry.c:1699: warning: pointer targets in return differ in signedness
In file included from hpt.c:186:
hptproc.c: In function âget_sd_nameâ:
hptproc.c:500: warning: implicit declaration of function âget_bdevâ
hptproc.c:500: warning: initialization makes pointer from integer without a cast
hptproc.c:503: error: dereferencing pointer to incomplete type
hptproc.c:503: error: request for member âdisk_nameâ in something not a structure or union
hptproc.c:504: warning: implicit declaration of function âblkdev_putâ
hptproc.c:504: error: expected â)â before â__BDEV_RAWâ
In file included from ioctl.c:6,
                 from hpt.c:187:
gui_lib.c: In function âhpt_get_controller_infoâ:
gui_lib.c:427: warning: pointer targets in passing argument 1 of âstrcpyâ differ in signedness
gui_lib.c:440: warning: pointer targets in passing argument 1 of âstrcpyâ differ in signedness
gui_lib.c:446: warning: pointer targets in passing argument 1 of âstrcpyâ differ in signedness
gui_lib.c:451: warning: pointer targets in passing argument 1 of âstrcpyâ differ in signedness
gui_lib.c:464: warning: pointer targets in passing argument 1 of âstrcpyâ differ in signedness
gui_lib.c: In function âhpt_check_autorebuildâ:
gui_lib.c:1553: error: âMAX_ARRAY_PER_VBUSâ undeclared (first use in this function)
gui_lib.c:1553: warning: comparison between pointer and integer
gui_lib.c:1555: warning: implicit declaration of function âArrayTablesâ
gui_lib.c:1555: warning: assignment makes pointer from integer without a cast
gui_lib.c:1555: error: âunion <anonymous>â has no member named âarrayâ
gui_lib.c:1555: error: request for member âdArStampâ in something not a structure or union
gui_lib.c:1558: error: âunion <anonymous>â has no member named âarrayâ
gui_lib.c:1558: error: request for member ârf_brokenâ in something not a structure or union
In file included from hpt.c:187:
ioctl.c: In function âtimer_start_for_cmdâ:
ioctl.c:197: error: âCONFIG_HZâ undeclared (first use in this function)
ioctl.c:197: error: invalid operands to binary *
ioctl.c:197: warning: assignment makes integer from pointer without a cast
ioctl.c: In function âhpt_rescan_allâ:
ioctl.c:658: error: âCONFIG_HZâ undeclared (first use in this function)
ioctl.c:658: error: invalid operands to binary *
ioctl.c:658: warning: assignment makes integer from pointer without a cast
make: *** [hpt.o] Error 1

```

---

### Post by k1n6 on 2008-05-03
For what its worth I added the OK_KMAP_TYPE KM_BIO_SRC_IRQ

on line 8 of entry.c and then commented out the linux/config.h include in hpt.c and now it compiles just great.

I was having the same error where it would fail trying to fnid config.h.

Thanks for the help.

---

### Post by davidgloriam on 2008-05-03
I managed to get my Highpoint Rocketraid 1520 working by following the advice on [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)

---

