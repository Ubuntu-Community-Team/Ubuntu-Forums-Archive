---
title: "Alsa driver installation problem"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by xtmotoman on 2013-01-06
Hi,
i need to install alsa drivers for my sound card (Trust SC-5250 with CMI8738 chip). 
I unzipped the archive alsa-driver
When I try ```
sudo ./configure --with-cards=cmipci --with-sequencer=yes ; make ; make install

```i get this error

```
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa-driver-1.0.25
checking cross compile... 
checking for directory with ALSA kernel sources... /usr/src/alsa-driver-1.0.25/alsa-kernel
checking for directory with kernel source... /lib/modules/3.5.0-21-generic/build
checking for directory with kernel build... /lib/modules/3.5.0-21-generic/build
checking for kernel linux/version.h ... linux/version.h
checking for kernel linux/autoconf.h generated/autoconf.h... generated/autoconf.h
checking for kernel linux/utsrelease.h generated/utsrelease.h... generated/utsrelease.h
checking for kernel version... 3.5.0-21-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (Ubuntu/Linaro 4.7.2-2ubuntu1) 4.7.2

*** NO PREDEFINED KERNEL COMPILER IS DETECTED
*** Assuming the same compiler is used with the current system compiler.

*** Please make sure that the same compiler version was used for building kernel.

checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for updating alsa-kernel version.h... yes
checking for CONFIG_EXPERIMENTAL... yes
checking for directory to store kernel modules... /lib/modules/3.5.0-21-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... no
checking for processor type... x86_64
checking for ISA DMA API... yes
checking for 32bit compat support... yes
checking for kernel linux/config.h... no
Creating <linux/config.h>...
checking for deprecated linux/config.h... checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... no
Creating a dummy <linux/utsrelease.h>...
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel linux/export.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/ratelimit.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/isa.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/log2.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/io.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel linux/pm_qos.h... yes
checking for kernel linux/pm_qos_params.h... no
Creating <linux/pm_qos_params.h>...
checking for kernel linux/kthread.h... yes
checking for kernel asm/irq_regs.h... yes
checking for kernel linux/seq_file.h... yes
checking for kernel linux/debugfs.h... yes
checking for kernel linux/gpio.h... yes
checking for kernel linux/bug.h... yes
checking for kernel linux/math64.h... yes
checking for kernel linux/regulator/consumer.h... yes
checking for kernel linux/dmi.h... yes
checking for kernel linux/bitrev.h... yes
checking for kernel linux/hrtimer.h... yes
checking for kernel linux/gcd.h... yes
checking for kernel linux/gfp.h... yes
checking for kernel pcmcia/cs_types.h... no
Creating <pcmcia/cs_types.h>...
checking for kernel pcmcia/cs.h... no
Creating <pcmcia/cs.h>...
checking for kernel linux/lzo.h... yes
checking for kernel linux/async.h... yes
checking for kernel linux/bitrev.h... yes
checking for kernel linux/smp_lock.h... no
Creating a dummy <linux/smp_lock.h>...
checking for kernel linux/i8253.h... yes
checking for kernel linux/atomic.h... yes
Copying trace/events headers
checking for kernel linux/tracepoint.h... yes
checking for kernel trace/define_trace.h... yes
Creating a workaround <linux/tracepoint.h>...
checking for kernel module symbol versions... yes
checking for has ioport support... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... yes
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for pc-speaker platform in kernel... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... no
checking for Kernel ISA-PnP module support... no
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for vzalloc... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_drvdata... yes
checking for V4L1 layer... no
checking for V4L2 layer... yes
checking for kernel media/v4l2-ctrls.h... yes
checking for io_remap_pfn_range... yes
checking for kcalloc... yes
checking for kstrdup... yes
checking for kstrndup... yes
checking for kzalloc... yes
checking for create_workqueue with flags... no
checking for pci_ioremap_bar... yes
checking for saved_config_space in pci_dev... yes
checking for new pci_save_state... yes
checking for register_sound_special_device... yes
checking for driver extra-version... 
checking for driver version... 1.0.25
checking for dynamic minor numbers... no
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC support... no
checking for HPET support... yes
checking for Procfs support... yes
checking for USB support... yes
checking for kernel linux/usb/audio-v2.h... yes
checking for kernel linux/usb/audio.h... yes
checking for valid v1 in linux/usb/audio.h... yes
checking for invalid v2 in linux/usb/audio.h... no
checking for valid linux/usb/audio-v2.h... no
Creating <linux/usb/audio-v2.h>...
checking for kernel linux/usb/ch9.h... yes
checking usb_alloc_coherent... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for new IRQ handler... yes
checking for gfp_t... yes
checking for GFP_DMA32... yes
checking for page_to_pfn... yes
checking for PnP suspend/resume... yes
checking for device_create_drvdata... no
checking for pm_qos_request... yes
checking for static pm_qos_request... no
checking for new pm_qos_request... no
checking for new unlocked/compat_ioctl... yes
checking for builtin _Bool support... yes
checking for x86-compatible PC... no
checking for High-Res timers... yes
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for CONFIG_HAS_DMA... yes
checking for FireWire support... yes
checking for cards to compile driver for... cmipci
checking for additonal options to compile driver for... all
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: WARNING:  'Makefile.conf.in' seems to ignore the --datarootdir setting
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/i2c-id_compat.h
config.status: creating include/config.h
config.status: creating include/config1.h
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
make dep
make[1]: Entering directory `/usr/src/alsa-driver-1.0.25'
make[2]: Entering directory `/usr/src/alsa-driver-1.0.25/include'
make -C sound prepare
make[3]: Entering directory `/usr/src/alsa-driver-1.0.25/include/sound'
make .includes.tmp
make[4]: Entering directory `/usr/src/alsa-driver-1.0.25/include/sound'
/bin/sh: 1: cannot create .includes.tmp: Permission denied
make[4]: *** [.includes.tmp] Error 2
make[4]: Leaving directory `/usr/src/alsa-driver-1.0.25/include/sound'
make[3]: *** [.includes] Error 2
make[3]: Leaving directory `/usr/src/alsa-driver-1.0.25/include/sound'
make[2]: *** [prepare] Error 2
make[2]: Leaving directory `/usr/src/alsa-driver-1.0.25/include'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/usr/src/alsa-driver-1.0.25'
make: *** [include/sndversions.h] Error 2
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /usr/src/alsa-driver-1.0.25/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
rm: nelze odstranit &#8222;/usr/include/sound/asound_fm.h&#8220;: Operace zamítnuta
rm: nelze odstranit &#8222;/usr/include/sound/hdspm.h&#8220;: Operace zamítnuta
rm: nelze odstranit &#8222;/usr/include/sound/asequencer.h&#8220;: Operace zamítnuta
rm: nelze odstranit &#8222;/usr/include/sound/asound.h&#8220;: Operace zamítnuta
rm: nelze odstranit &#8222;/usr/include/sound/hdsp.h&#8220;: Operace zamítnuta
rm: nelze odstranit &#8222;/usr/include/sound/sb16_csp.h&#8220;: Operace zamítnuta
rm: nelze odstranit &#8222;/usr/include/sound/emu10k1.h&#8220;: Operace zamítnuta
rm: nelze odstranit &#8222;/usr/include/sound/compress_params.h&#8220;: Operace zamítnuta
rm: nelze odstranit &#8222;/usr/include/sound/compress_offload.h&#8220;: Operace zamítnuta
rm: nelze odstranit &#8222;/usr/include/sound/sfnt_info.h&#8220;: Operace zamítnuta
install: nelze získat informace o &#8222;include/sound/*.h&#8220;: Adresá&#345; nebo soubor neexistuje
make: *** [install-headers] Error 1

```Thanks for every help.

Sorry, my language is czech.....the lines at the botom:
rm: nelze odstranit &#8222;/usr/include/sound/asound_fm.h&#8220;: Operace zamítnuta    .....it means
rm: can't remove &#8222;/usr/include/sound/asound_fm.h&#8220;: operation denied

---

