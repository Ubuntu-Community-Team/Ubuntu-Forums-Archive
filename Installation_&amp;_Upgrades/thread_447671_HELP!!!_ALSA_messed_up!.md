---
title: "HELP!!! ALSA messed up!"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2007-05-18
Help! I got completely lost, and I have messed up my sound system completely!

I have a Realtek AC'97 onboard sound which uses the atiixp driver.

```
timo@aristoteles:/usr/src/alsa$ lspci -v
[...]
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
        Subsystem: Acer Incorporated [ALI] Aspire 5024WLMMi
        Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
        Memory at c0003400 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
[...]

```

Everything worked fine but I could not record any sound. As I would like to use my notebook for internet phone calls, this is quite annoying. :-) So, I was looking on the forum for threads about Realtek, and came about this post: [http://ubuntuforums.org/show...nt=2]("http://ubuntuforums.org/showpost.php?p=2031398&postcount=2"). So, I downloaded the Realtek drivers from here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#AC]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=23&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false#AC"). I tried to install, but it failed, and my ALSA driver is wasted. :-(

I tried re-installing ALSA-Common with Synaptic but to no avail.

I then looked here: [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide") 

This lead me to this page from the Alsa project: [http://www.alsa-project.org/alsa-doc/....IXP+SB400&module=atiixp]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=ATI&card=ATI-IXP+southbridge+AC97+audio.&chip=IXP+SB150%2C+IXP+SB200%2C+IXP+SB250%2C+IXP+SB300%2C+IXP+SB400&module=atiixp")

I downloaded the source code, and tried to compile the driver from the scratch, which lead to some errors:

```
root@aristoteles:/usr/src/alsa/alsa-driver-1.0.13# ./configure --with-cards=atiixp --with-sequencer=yes;make;make install
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
checking for which soundcards to compile driver for... atiixp
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
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
Hacking autoconf.h...
if [ ! -d include/sound -a ! -L include/sound ]; then \
          ln -sf ../alsa-kernel/include include/sound ; \
        fi
cp -auvf include/version.h include/sound/version.h
„include/version.h“ -> „include/sound/version.h“
make dep
make[1]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13'
make[2]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore'
copying file alsa-kernel/core/info.c
patching file info.c
copying file alsa-kernel/core/pcm_native.c
patching file pcm_native.c
Hunk #3 succeeded at 2815 (offset -32 lines).
Hunk #4 succeeded at 2835 (offset -32 lines).
Hunk #5 succeeded at 2888 (offset -32 lines).
Hunk #6 succeeded at 2915 (offset -32 lines).
Hunk #7 succeeded at 3006 (offset -32 lines).
Hunk #8 succeeded at 3025 (offset -32 lines).
Hunk #9 succeeded at 3044 (offset -32 lines).
Hunk #10 succeeded at 3077 (offset -32 lines).
Hunk #11 succeeded at 3110 (offset -32 lines).
Hunk #12 succeeded at 3143 (offset -32 lines).
Hunk #13 succeeded at 3172 (offset -32 lines).
Hunk #14 succeeded at 3193 (offset -32 lines).
Hunk #15 succeeded at 3211 (offset -32 lines).
Hunk #16 succeeded at 3231 (offset -32 lines).
Hunk #17 succeeded at 3243 (offset -32 lines).
Hunk #18 succeeded at 3275 (offset -32 lines).
Hunk #19 succeeded at 3341 (offset -32 lines).
Hunk #20 succeeded at 3370 with fuzz 1 (offset -32 lines).
Hunk #21 succeeded at 3411 (offset -32 lines).
Hunk #22 succeeded at 3561 (offset -32 lines).
copying file alsa-kernel/core/control.c
patching file control.c
Hunk #2 succeeded at 1411 (offset 194 lines).
copying file alsa-kernel/core/hwdep.c
patching file hwdep.c
Hunk #1 succeeded at 309 (offset 6 lines).
copying file alsa-kernel/core/init.c
patching file init.c
Hunk #2 succeeded at 204 (offset 12 lines).
Hunk #3 succeeded at 277 (offset 13 lines).
copying file alsa-kernel/core/rawmidi.c
patching file rawmidi.c
Hunk #1 succeeded at 1297 (offset 30 lines).
Hunk #2 succeeded at 1380 with fuzz 1 (offset 30 lines).
copying file alsa-kernel/core/sound.c
patching file sound.c
copying file alsa-kernel/core/timer.c
patching file timer.c
Hunk #1 succeeded at 1012 with fuzz 1 (offset 17 lines).
Hunk #2 succeeded at 1925 (offset 134 lines).
Hunk #3 succeeded at 1970 with fuzz 2 (offset 125 lines).
copying file alsa-kernel/core/memalloc.c
patching file memalloc.c
Hunk #2 succeeded at 83 (offset -1 lines).
Hunk #3 succeeded at 143 (offset -1 lines).
Hunk #4 succeeded at 174 (offset -1 lines).
Hunk #5 succeeded at 207 (offset -1 lines).
Hunk #6 succeeded at 228 (offset -1 lines).
Hunk #7 succeeded at 264 (offset -1 lines).
Hunk #8 succeeded at 286 (offset -1 lines).
Hunk #9 succeeded at 311 (offset -1 lines).
Hunk #10 succeeded at 329 (offset -1 lines).
Hunk #11 succeeded at 608 (offset -1 lines).
Hunk #12 succeeded at 697 (offset -1 lines).
Hunk #13 succeeded at 712 (offset -1 lines).
Hunk #14 succeeded at 746 (offset -1 lines).
copying file alsa-kernel/core/misc.c
patching file misc.c
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/ioctl32'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/ioctl32'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/oss'
copying file alsa-kernel/core/oss/mixer_oss.c
patching file mixer_oss.c
Hunk #1 succeeded at 379 with fuzz 1 (offset 2 lines).
copying file alsa-kernel/core/oss/pcm_oss.c
patching file pcm_oss.c
Hunk #1 succeeded at 2528 (offset 2 lines).
Hunk #2 succeeded at 2579 (offset 2 lines).
Hunk #3 succeeded at 2702 (offset 2 lines).
Hunk #5 succeeded at 3012 (offset -2 lines).
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/oss'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/seq'
copying file alsa-kernel/core/seq/seq.c
patching file seq.c
Hunk #1 succeeded at 57 (offset 6 lines).
copying file alsa-kernel/core/seq/seq_clientmgr.c
patching file seq_clientmgr.c
Hunk #2 succeeded at 2209 (offset 68 lines).
Hunk #3 succeeded at 2558 with fuzz 1 (offset 89 lines).
copying file alsa-kernel/core/seq/seq_memory.c
patching file seq_memory.c
Hunk #3 succeeded at 248 (offset 3 lines).
make[4]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/seq/instr'
make[4]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/seq/instr'
make[4]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/seq/oss'
copying file alsa-kernel/core/seq/oss/seq_oss.c
patching file seq_oss.c
Hunk #1 succeeded at 189 (offset 3 lines).
Hunk #2 succeeded at 223 with fuzz 1 (offset 3 lines).
Hunk #3 succeeded at 326 (offset -8 lines).
make[4]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/seq/oss'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore/seq'
make[2]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore'
make[2]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/i2c'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/i2c/other'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/i2c/other'
make[2]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/i2c'
make[2]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/mpu401'
copying file alsa-kernel/drivers/mpu401/mpu401.c
patching file mpu401.c
Hunk #1 succeeded at 30 (offset 2 lines).
Hunk #2 succeeded at 46 (offset 2 lines).
Hunk #3 succeeded at 64 with fuzz 2 (offset 2 lines).
Hunk #4 succeeded at 92 with fuzz 2 (offset -55 lines).
Hunk #5 succeeded at 296 (offset 49 lines).
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/mpu401'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/opl3'
copying file alsa-kernel/drivers/opl3/opl3_lib.c
patching file opl3_lib.c
Hunk #1 succeeded at 435 (offset 2 lines).
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/opl3'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/opl4'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/opl4'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/pcsp'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/pcsp'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/vx'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers/vx'
make[2]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/drivers'
make[2]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/ad1816a'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/ad1816a'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/ad1848'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/ad1848'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/cs423x'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/cs423x'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/es1688'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/es1688'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/gus'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/gus'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/msnd'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/msnd'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/opti9xx'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/opti9xx'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/sb'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/sb'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/wavefront'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa/wavefront'
make[2]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/isa'
make[2]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/synth'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/synth/emux'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/synth/emux'
make[2]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/synth'
make[2]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci'
copying file alsa-kernel/pci/ad1889.c
patching file ad1889.c
Hunk #1 succeeded at 53 with fuzz 2 (offset 1 line).
copying file alsa-kernel/pci/bt87x.c
patching file bt87x.c
Hunk #1 succeeded at 815 (offset 5 lines).
Hunk #2 succeeded at 954 (offset 6 lines).
copying file alsa-kernel/pci/intel8x0.c
patching file intel8x0.c
Hunk #1 succeeded at 41 (offset -2 lines).
Hunk #2 succeeded at 728 (offset -21 lines).
Hunk #3 succeeded at 739 (offset -21 lines).
Hunk #4 succeeded at 3052 (offset 239 lines).
copying file alsa-kernel/pci/maestro3.c
patching file maestro3.c
Hunk #5 succeeded at 2911 (offset 1 line).
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ac97'
copying file alsa-kernel/pci/ac97/ac97_codec.c
patching file ac97_codec.c
Hunk #1 succeeded at 35 (offset 2 lines).
Hunk #2 succeeded at 1890 with fuzz 2 (offset 77 lines).
Hunk #3 succeeded at 1924 with fuzz 2 (offset 78 lines).
copying file alsa-kernel/pci/ac97/ac97_bus.c
patching file ac97_bus.c
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ac97'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ali5451'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ali5451'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/asihpi'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/asihpi'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/au88x0'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/au88x0'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ca0106'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ca0106'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/cs46xx'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/cs46xx'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/cs5535audio'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/cs5535audio'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/echoaudio'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/echoaudio'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/emu10k1'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/emu10k1'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/hda'
copying file alsa-kernel/pci/hda/hda_codec.c
patching file hda_codec.c
Hunk #1 succeeded at 262 (offset 2 lines).
Hunk #2 succeeded at 301 (offset 2 lines).
Hunk #3 succeeded at 320 (offset 2 lines).
Hunk #4 succeeded at 336 (offset 2 lines).
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/hda'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ice1712'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ice1712'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/korg1212'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/korg1212'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/mixart'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/mixart'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/nm256'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/nm256'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/pcxhr'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/pcxhr'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/pdplus'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/pdplus'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/riptide'
copying file alsa-kernel/pci/riptide/riptide.c
patching file riptide.c
Hunk #1 succeeded at 1273 (offset 4 lines).
Hunk #2 succeeded at 2230 (offset 4 lines).
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/riptide'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/rme9652'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/rme9652'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/trident'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/trident'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/vx222'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/vx222'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ymfpci'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci/ymfpci'
make[2]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pci'
make[2]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/codecs'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/codecs'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/core'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/core'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/fabrics'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/fabrics'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/soundbus'
make[4]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/soundbus/i2sbus'
make[4]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/soundbus/i2sbus'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa/soundbus'
make[2]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/aoa'
make[2]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/usb'
copying file alsa-kernel/usb/usbaudio.c
patching file usbaudio.c
Hunk #3 succeeded at 659 (offset 1 line).
Hunk #4 succeeded at 686 (offset 1 line).
Hunk #5 succeeded at 767 (offset 1 line).
Hunk #6 succeeded at 782 (offset 1 line).
Hunk #7 succeeded at 1149 (offset 1 line).
Hunk #8 succeeded at 2073 (offset 38 lines).
Hunk #9 succeeded at 2092 (offset 38 lines).
Hunk #10 succeeded at 2109 (offset 38 lines).
Hunk #11 succeeded at 2656 (offset 45 lines).
Hunk #12 succeeded at 2728 (offset 44 lines).
Hunk #13 succeeded at 3013 (offset 44 lines).
Hunk #14 succeeded at 3085 (offset 44 lines).
Hunk #15 succeeded at 3154 (offset 44 lines).
Hunk #16 succeeded at 3172 (offset 44 lines).
Hunk #17 succeeded at 3186 (offset 44 lines).
Hunk #18 succeeded at 3199 (offset 44 lines).
Hunk #19 succeeded at 3395 (offset 70 lines).
Hunk #20 succeeded at 3486 (offset 70 lines).
Hunk #21 succeeded at 3624 (offset 76 lines).
Hunk #22 succeeded at 3645 (offset 76 lines).
Hunk #23 succeeded at 3667 (offset 76 lines).
copying file alsa-kernel/usb/usbmidi.c
patching file usbmidi.c
Hunk #2 succeeded at 225 with fuzz 2 (offset -3 lines).
Hunk #3 succeeded at 249 with fuzz 2 (offset -3 lines).
Hunk #4 succeeded at 343 (offset -3 lines).
Hunk #5 succeeded at 1363 (offset 53 lines).
Hunk #6 succeeded at 1707 (offset 58 lines).
copying file alsa-kernel/usb/usbmixer.c
patching file usbmixer.c
Hunk #2 succeeded at 49 (offset 1 line).
Hunk #3 succeeded at 1726 (offset 27 lines).
Hunk #4 succeeded at 1775 (offset 27 lines).
Hunk #5 succeeded at 1796 (offset 27 lines).
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/usb/usx2y'
copying file alsa-kernel/usb/usx2y/usX2Yhwdep.c
patching file usX2Yhwdep.c
copying file alsa-kernel/usb/usx2y/usbusx2y.c
patching file usbusx2y.c
copying file alsa-kernel/usb/usx2y/usbusx2yaudio.c
patching file usbusx2yaudio.c
copying file alsa-kernel/usb/usx2y/usx2yhwdeppcm.c
patching file usx2yhwdeppcm.c
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/usb/usx2y'
make[2]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/usb'
make[2]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pcmcia'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pcmcia/pdaudiocf'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pcmcia/pdaudiocf'
make[3]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pcmcia/vx'
make[3]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pcmcia/vx'
make[2]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/pcmcia'
make[1]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13'
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/usr/src/alsa/alsa-driver-1.0.13  CPP="gcc -E" CC="gcc" modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.o
In file included from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h:742: Fehler: Redefinition von »jiffies_to_msecs«
include/linux/jiffies.h:268: Fehler: Vorherige Definition von »jiffies_to_msecs« war hier
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h:761: Fehler: Redefinition von »msecs_to_jiffies«
include/linux/jiffies.h:290: Fehler: Vorherige Definition von »msecs_to_jiffies« war hier
In file included from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.c:1:
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h: In Funktion »snd_pci_orig_save_state«:
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h:1099: Fehler: zu viele Argumente für Funktion »pci_save_state«
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h: In Funktion »snd_pci_orig_restore_state«:
/usr/src/alsa/alsa-driver-1.0.13/include/adriver.h:1103: Fehler: zu viele Argumente für Funktion »pci_restore_state«
make[3]: *** [/usr/src/alsa/alsa-driver-1.0.13/acore/memalloc.o] Fehler 1
make[2]: *** [/usr/src/alsa/alsa-driver-1.0.13/acore] Fehler 2
make[1]: *** [_module_/usr/src/alsa/alsa-driver-1.0.13] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Fehler 2
find /lib/modules/2.6.20-15-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Betrete Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore'
mkdir -p /lib/modules/2.6.20-15-generic/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.20-15-generic/kernel/sound/acore
cp: Aufruf von stat für „snd-page-alloc.ko“ nicht möglich: No such file or directory
cp: Aufruf von stat für „snd-pcm.ko“ nicht möglich: No such file or directory
cp: Aufruf von stat für „snd-timer.ko“ nicht möglich: No such file or directory
cp: Aufruf von stat für „snd.ko“ nicht möglich: No such file or directory
make[1]: *** [modules_install] Fehler 1
make[1]: Verlasse Verzeichnis '/usr/src/alsa/alsa-driver-1.0.13/acore'
make: *** [install-modules] Fehler 1
root@aristoteles:/usr/src/alsa/alsa-driver-1.0.13# 
```

In case this might help:

```
timo@aristoteles:/usr/src/alsa$ aplay -v
ALSA lib confmisc.c:560:(snd_determine_driver) could not open control for card 0
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:955:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3948:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2090:(snd_pcm_open_noupdate) Unknown PCM default
aplay: main:550: Fehler beim Öffnen des Audiogerätes: No such device
```

So, how can I get back to the state I started from?

Thnx, Timo

---

### Post by Timokl on 2007-05-19
Hi,

is there no one with an idea? :-(

Any idea is highly appreciated!!!

Bye,Timo

---

### Post by Timokl on 2007-05-19
I tried purging and re-installing the whole sound system on my notebook. Did not work.

However, it seems there are some kernel modules missing. How can I re-install them?

```
timo@aristoteles:~/src/alsa/alsa-driver-1.0.13$ sudo modprobe snd-atiixp
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/pci/ac97/snd-ac97-codec.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/pci/snd-atiixp.ko': No such file or directory
```

thnx for your help,
Timo

---

