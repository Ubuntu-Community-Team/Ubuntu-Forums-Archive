---
title: "Cannot install Realtek sound drivers."
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by aidenscool09 on 2011-06-02
A bit of a problem here; I can't install the Realtek drivers in my Ubuntu partition. I am running Ubuntu 10.04 64-bit and my Realtek chipset is ALC888B.

When I run ./install I get this:
```
aiden@TheJeezusMachine:~/RT Driver$ sudo ./install
.....Decompress Driver source v1.0.24-5.16rc14
Compile Driver........
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
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
checking for current directory... /home/aiden/RT Driver/alsa-driver-1.0.24
checking cross compile... 
checking for directory with ALSA kernel sources... /home/aiden/RT Driver/alsa-driver-1.0.24/alsa-kernel
checking for directory with kernel source... /lib/modules/2.6.35-28-generic/build
checking for directory with kernel build... /lib/modules/2.6.35-28-generic/build
checking for kernel linux/version.h ... linux/version.h
checking for kernel linux/autoconf.h generated/autoconf.h... generated/autoconf.h
checking for kernel linux/utsrelease.h generated/utsrelease.h... generated/utsrelease.h
checking for kernel version... 2.6.35-28-generic
checking for GCC version... Kernel compiler:  Used compiler: gcc (Ubuntu/Linaro 4.4.4-14ubuntu5) 4.4.5

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
checking for directory to store kernel modules... /lib/modules/2.6.35-28-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i686
checking for ISA DMA API... yes
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
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
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
checking for kernel linux/pm_qos_params.h... yes
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
checking for kernel pcmcia/cs_types.h... yes
checking for kernel pcmcia/cs.h... yes
checking for kernel trace/events/asoc.h... no
Creating <trace/events/asoc.h>...
checking for kernel linux/lzo.h... yes
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
checking for Kernel ISA-PnP support... yes
checking for strlcpy... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for scnprintf... yes
checking for sscanf... yes
checking for vmalloc_to_page... yes
checking for old kmod... no
checking for PDE... yes
checking for pci_set_consistent_dma_mask... yes
checking for pci_dev_present... yes
checking for msleep... yes
checking for msleep_interrupt... yes
checking for msecs_to_jiffies... yes
checking for tty->count is the atomic type... yes
checking for video_get_drvdata... yes
checking for video_drvdata... yes
checking for V4L1 layer... yes
checking for V4L2 layer... yes
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
checking for driver version... 1.0.24-5.16rc14
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
checking for valid v1 in linux/usb/audio.h... no
Creating <linux/usb/audio.h>...
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
checking for cards to compile driver for... hda-intel
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
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24/alsa-kernel/': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24/alsa-kernel/': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24/alsa-kernel/': No such file or directory
make dep
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24/alsa-kernel/': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24/alsa-kernel/': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24/alsa-kernel/': No such file or directory
make[1]: Entering directory `/home/aiden/RT Driver/alsa-driver-1.0.24'
make[2]: Entering directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include'
make -C sound prepare
make[3]: Entering directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include/sound'
make .includes.tmp
make[4]: Entering directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include/sound'
make[4]: Leaving directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include/sound'
make prepare2
make[4]: Entering directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include/sound'
cp ../../alsa-kernel/include/ac97_codec.h .
patch -p0 -i ac97_codec.patch ac97_codec.h
patching file ac97_codec.h
ln -s ../../alsa-kernel/include/aci.h
ln -s ../../alsa-kernel/include/ad1816a.h
ln -s ../../alsa-kernel/include/ad1843.h
ln -s ../../alsa-kernel/include/ak4113.h
ln -s ../../alsa-kernel/include/ak4114.h
ln -s ../../alsa-kernel/include/ak4117.h
ln -s ../../alsa-kernel/include/ak4531_codec.h
ln -s ../../alsa-kernel/include/ak4xxx-adda.h
ln -s ../../alsa-kernel/include/alc5623.h
ln -s ../../alsa-kernel/include/asequencer.h
ln -s ../../alsa-kernel/include/asound.h
ln -s ../../alsa-kernel/include/asound_fm.h
ln -s ../../alsa-kernel/include/asoundef.h
ln -s ../../alsa-kernel/include/atmel-abdac.h
ln -s ../../alsa-kernel/include/atmel-ac97c.h
ln -s ../../alsa-kernel/include/control.h
cp ../../alsa-kernel/include/core.h .
patch -p0 -i core.patch core.h
patching file core.h
ln -s ../../alsa-kernel/include/cs4231-regs.h
ln -s ../../alsa-kernel/include/cs46xx.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_scb_types.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_spos.h
ln -s ../../alsa-kernel/include/cs46xx_dsp_task_types.h
ln -s ../../alsa-kernel/include/cs8403.h
ln -s ../../alsa-kernel/include/cs8427.h
ln -s ../../alsa-kernel/include/emu10k1.h
ln -s ../../alsa-kernel/include/emu10k1_synth.h
ln -s ../../alsa-kernel/include/emu8000.h
ln -s ../../alsa-kernel/include/emu8000_reg.h
ln -s ../../alsa-kernel/include/emux_legacy.h
ln -s ../../alsa-kernel/include/emux_synth.h
ln -s ../../alsa-kernel/include/es1688.h
ln -s ../../alsa-kernel/include/gus.h
ln -s ../../alsa-kernel/include/hda_hwdep.h
ln -s ../../alsa-kernel/include/hdsp.h
ln -s ../../alsa-kernel/include/hdspm.h
ln -s ../../alsa-kernel/include/hwdep.h
ln -s ../../alsa-kernel/include/i2c.h
ln -s ../../alsa-kernel/include/info.h
ln -s ../../alsa-kernel/include/initval.h
ln -s ../../alsa-kernel/include/jack.h
ln -s ../../alsa-kernel/include/l3.h
ln -s ../../alsa-kernel/include/max98088.h
ln -s ../../alsa-kernel/include/memalloc.h
ln -s ../../alsa-kernel/include/minors.h
ln -s ../../alsa-kernel/include/mixer_oss.h
ln -s ../../alsa-kernel/include/mpu401.h
ln -s ../../alsa-kernel/include/opl3.h
ln -s ../../alsa-kernel/include/opl4.h
ln -s ../../alsa-kernel/include/pcm-indirect.h
cp ../../alsa-kernel/include/pcm.h .
patch -p0 -i pcm.patch pcm.h
patching file pcm.h
Hunk #3 succeeded at 310 (offset 1 line).
Hunk #4 succeeded at 331 (offset 1 line).
Hunk #5 succeeded at 359 (offset 1 line).
Hunk #6 succeeded at 377 (offset 1 line).
Hunk #7 succeeded at 415 (offset 1 line).
Hunk #8 succeeded at 435 (offset 1 line).
ln -s ../../alsa-kernel/include/pcm_oss.h
ln -s ../../alsa-kernel/include/pcm_params.h
ln -s ../../alsa-kernel/include/pt2258.h
ln -s ../../alsa-kernel/include/pxa2xx-lib.h
ln -s ../../alsa-kernel/include/rawmidi.h
ln -s ../../alsa-kernel/include/s3c24xx_uda134x.h
ln -s ../../alsa-kernel/include/sb.h
ln -s ../../alsa-kernel/include/sb16_csp.h
ln -s ../../alsa-kernel/include/seq_device.h
ln -s ../../alsa-kernel/include/seq_kernel.h
ln -s ../../alsa-kernel/include/seq_midi_emul.h
ln -s ../../alsa-kernel/include/seq_midi_event.h
ln -s ../../alsa-kernel/include/seq_oss.h
ln -s ../../alsa-kernel/include/seq_oss_legacy.h
ln -s ../../alsa-kernel/include/seq_virmidi.h
ln -s ../../alsa-kernel/include/sfnt_info.h
ln -s ../../alsa-kernel/include/sh_dac_audio.h
ln -s ../../alsa-kernel/include/sh_fsi.h
ln -s ../../alsa-kernel/include/snd_wavefront.h
ln -s ../../alsa-kernel/include/soc-dai.h
ln -s ../../alsa-kernel/include/soc-dapm.h
ln -s ../../alsa-kernel/include/soc.h
ln -s ../../alsa-kernel/include/soundfont.h
ln -s ../../alsa-kernel/include/tea575x-tuner.h
ln -s ../../alsa-kernel/include/tea6330t.h
ln -s ../../alsa-kernel/include/timer.h
ln -s ../../alsa-kernel/include/tlv.h
ln -s ../../alsa-kernel/include/tlv320aic3x.h
ln -s ../../alsa-kernel/include/tlv320dac33-plat.h
ln -s ../../alsa-kernel/include/tpa6130a2-plat.h
ln -s ../../alsa-kernel/include/trident.h
ln -s ../../alsa-kernel/include/uda134x.h
ln -s ../../alsa-kernel/include/uda1380.h
ln -s ../../alsa-kernel/include/util_mem.h
ln -s ../version.h
ln -s ../../alsa-kernel/include/vx_core.h
ln -s ../../alsa-kernel/include/wavefront.h
ln -s ../../alsa-kernel/include/wm2000.h
ln -s ../../alsa-kernel/include/wm8903.h
ln -s ../../alsa-kernel/include/wm8904.h
ln -s ../../alsa-kernel/include/wm8955.h
ln -s ../../alsa-kernel/include/wm8960.h
ln -s ../../alsa-kernel/include/wm8962.h
ln -s ../../alsa-kernel/include/wm8993.h
ln -s ../../alsa-kernel/include/wm9081.h
ln -s ../../alsa-kernel/include/wm9090.h
ln -s ../../alsa-kernel/include/wss.h
ln -s ../../alsa-kernel/include/ymfpci.h
make[4]: Leaving directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include/sound'
make[3]: Leaving directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include/sound'
make[2]: Leaving directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include'
make[2]: Entering directory `/home/aiden/RT Driver/alsa-driver-1.0.24/acore'
Makefile:5: /home/aiden/RT: No such file or directory
Makefile:5: Driver/alsa-driver-1.0.24/toplevel.config: No such file or directory
Makefile:6: /home/aiden/RT: No such file or directory
Makefile:6: Driver/alsa-driver-1.0.24/Makefile.conf: No such file or directory
Makefile:16: /home/aiden/RT: No such file or directory
Makefile:16: Driver/alsa-driver-1.0.24/alsa-kernel/core/Makefile: No such file or directory
Makefile:28: /home/aiden/RT: No such file or directory
Makefile:28: Driver/alsa-driver-1.0.24/Rules.make: No such file or directory
make[2]: *** No rule to make target `Driver/alsa-driver-1.0.24/Rules.make'.  Stop.
make[2]: Leaving directory `/home/aiden/RT Driver/alsa-driver-1.0.24/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/home/aiden/RT Driver/alsa-driver-1.0.24'
make: *** [include/sndversions.h] Error 2
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24/alsa-kernel/': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24/alsa-kernel/': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24': No such file or directory
find: `/home/aiden/RT': No such file or directory
find: `Driver/alsa-driver-1.0.24/alsa-kernel/': No such file or directory
if [ -L /usr/include/sound ]; then \
        rm -f /usr/include/sound; \
        ln -sf /home/aiden/RT Driver/alsa-driver-1.0.24/include/sound /usr/include/sound; \
    else \
        rm -rf /usr/include/sound; \
        install -d -m 755 -g root -o root /usr/include/sound; \
        for f in include/sound/*.h; do \
            install -m 644 -g root -o root $f /usr/include/sound; \
        done \
    fi
find /lib/modules/2.6.35-28-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.35-28-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.35-28-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.35-28-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include'
make[1]: Nothing to be done for `modules_install'.
make[1]: Leaving directory `/home/aiden/RT Driver/alsa-driver-1.0.24/include'
make[1]: Entering directory `/home/aiden/RT Driver/alsa-driver-1.0.24/acore'
Makefile:5: /home/aiden/RT: No such file or directory
Makefile:5: Driver/alsa-driver-1.0.24/toplevel.config: No such file or directory
Makefile:6: /home/aiden/RT: No such file or directory
Makefile:6: Driver/alsa-driver-1.0.24/Makefile.conf: No such file or directory
Makefile:16: /home/aiden/RT: No such file or directory
Makefile:16: Driver/alsa-driver-1.0.24/alsa-kernel/core/Makefile: No such file or directory
Makefile:28: /home/aiden/RT: No such file or directory
Makefile:28: Driver/alsa-driver-1.0.24/Rules.make: No such file or directory
make[1]: *** No rule to make target `Driver/alsa-driver-1.0.24/Rules.make'.  Stop.
make[1]: Leaving directory `/home/aiden/RT Driver/alsa-driver-1.0.24/acore'
make: *** [install-modules] Error 1
Creating mixer?...done.
Creating sequencer...done.
Creating midi0?...done.
Creating dsp?...done.
Creating audio?...done.
Creating sndstat...done.
Creating music...done.
Creating dmmidi?...done.
Creating dmfm?...done.
Creating amixer?...done.
Creating adsp?...done.
Creating amidi?...done.
Creating admmidi?...done.
rm: cannot remove `/dev/snd': Is a directory
rm: cannot remove `/dev/snd/by-id': Is a directory
rm: cannot remove `/dev/snd/by-path': Is a directory
rmdir: failed to remove `/dev/snd': Directory not empty
Creating snd/control?...done.
Creating snd/seq...done.
Creating snd/timer...done.
Creating snd/hw??...done.
Creating snd/midi??...done.
Creating snd/pcm??p...done.
Creating snd/pcm??c...done.
Creating aload?...done.
Creating aloadSEQ...done.
Remove Folder.....
./install: 48: alsaconf: not found
aiden@TheJeezusMachine:~/RT Driver$
```

The output is the same as regular user and as root. Really annoying now as I currently am getting no sound output.

---

### Post by aidenscool09 on 2011-06-02
Bump?
I need to be quick about this...

---

### Post by mörgæs on 2011-06-02
You need to be patient about this... 

Bumping only annoys people.

---

### Post by aidenscool09 on 2011-06-03
Well this is tedious, since I now have no sound output in my Ubuntu partition, would there at least be a way of reverting to the original driver?

---

### Post by aidenscool09 on 2011-06-05
Bump

---

### Post by aidenscool09 on 2011-06-06
Bump?

---

### Post by Toz on 2011-06-06
> find: `/home/aiden/RT': No such file or directory
Try renaming the "RT Driver" directory so that it doesn't have a space in it.

---

### Post by aidenscool09 on 2011-06-06
> **Toz said:**
> Try renaming the "RT Driver" directory so that it doesn't have a space in it.
Aha! I'll give that a whizz now. If that works, I will facedesk /very/ hard. Lol.
EDIT: Still gives "./install: 48: alsaconf: not found". Thanks for the help though.
EDIT2: Compiled an alsaconf from source and placed in /usr/bin directory. Hope this works...
EDIT3: Damn, when alsaconfig is run, I can't find my sound chip... :(

---

### Post by Toz on 2011-06-06
Have you tried modifying the /etc/modprobe.d/alsa-base.conf file yet? If not, open the file as root and append to the end of the file:```
options snd-hda-intel model=auto
```

Save. Reboot. On restart, double-check all settings in alsamixer.

---

### Post by aidenscool09 on 2011-06-07
> **Toz said:**
> Have you tried modifying the /etc/modprobe.d/alsa-base.conf file yet? If not, open the file as root and append to the end of the file:```
options snd-hda-intel model=auto
```Save. Reboot. On restart, double-check all settings in alsamixer.
snd-hda-intel? I'm on an AMD board, with a Realtek chip, or is this like a fallback?

---

### Post by Toz on 2011-06-07
Lets find out.

Can you post back the contents of your /etc/modprobe.d/alsa-base.conf file?

And while you're at it, running the whole alsa bug report wouldn't hurt either.```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```Choose the upload option and post back the link.

---

### Post by aidenscool09 on 2011-06-07
> **Toz said:**
> Lets find out.

Can you post back the contents of your /etc/modprobe.d/alsa-base.conf file?

And while you're at it, running the whole alsa bug report wouldn't hurt either.```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```Choose the upload option and post back the link.

Ok, I'll hop to Ubuntu later, in W7 atm.

---

### Post by aidenscool09 on 2011-06-08
[http://www.alsa-project.org/db/?f=d9fb5d2ecc4d046d37f461c6bfd453c54a3c6a01](http://www.alsa-project.org/db/?f=d9fb5d2ecc4d046d37f461c6bfd453c54a3c6a01)
There is the debug file.

This is my /etc/modprobe.d/alsa-base.conf contents:

```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2

```

I'll tell you if appending
```

options snd-hda-intel model=auto

```
helped.

---

### Post by Toz on 2011-06-08
Your alsa install looks borked. A re-install is probably in order. Follow the instructions from this link [http://ubuntuforums.org/showpost.php?p=10101057&postcount=4]("http://ubuntuforums.org/showpost.php?p=10101057&postcount=4") then post back a new version of the alsa script.

---

### Post by aidenscool09 on 2011-06-08
Ok, done that, I'll give the Realtek installer another try. I'll get back with results.

---

### Post by aidenscool09 on 2011-06-08
Same result with the installer... Just gonna stick with the default drivers for now...

---

### Post by Toz on 2011-06-08
Post back alsa script info.

---

### Post by aidenscool09 on 2011-06-09
The output of the installer script?
EDIT: Maybe I should have added this before:
```

aiden@TheJeezusMachine:~/RTDriver$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]

```

---

### Post by Toz on 2011-06-09
The alsa report from post #11

---

