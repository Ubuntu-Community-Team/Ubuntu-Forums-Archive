---
title: "Sound is Broken."
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by Thief- on 2005-03-20
Last night I upgraded to Hoary, and when I booted up this morning, there was no sound at all.

I was wondering if there were any fixes for this problem, because it is getting very annoying.

---

### Post by rwjblue on 2005-03-20
Same issue here.  Can't here any audio after update at around 05:00 UTC 03/20/2005. 

esd is running and the sound modules are loaded.  

Any insight is definately appreciated.

---

### Post by ubuntu-geek on 2005-03-20
What kind of sound cards do you have?

---

### Post by gnutux on 2005-03-20
Hi,

Try to use ALSA as much as possible since it's the base. ALSA is now also multi-threaded, therefore you have more than 1 program that can access your soundcard like in Windows.

gnutux

---

### Post by Thief- on 2005-03-20
[QUOTE=ubuntu-geek]What kind of sound cards do you have?[/QUOTE]

I have a Sound Blaster Audigy 2.

---

### Post by Thief- on 2005-03-20
If this helps, I 'updated' using Synaptic.

---

### Post by ubuntu-geek on 2005-03-20
Ok, if you type "alsamixer" at the command line do you get an error or does it load the mixer settings? If it loads the mixer settings look for the analog/digital output jack and make sure its not turned off.

If you get an error when running alsamixer you are in the same boat as alot of Hoary users with Audigy 2 cards, I have opened a bug report with ubuntu but they wont fix it until after Hoary is released so..

To fix for audigy 2 users:
Other sound card users check: [http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix](http://www.alsa-project.org/alsa-doc/index.php?vendor=All#matrix)
For the exact driver to compile for your card.

 Install the linux-headers package that suits your kernel. I am running kernel 2.6.10-5-386
so I did:

sudo apt-get install linux-headers-2.6.10-5-386 linux-headers-2.6.10

cd /usr/src
sudo wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.8.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.8.tar.bz2")
tar xvjf alsa-driver-1.0.8.tar.bz2
cd alsa-driver-1.0.8
sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
sudo make
sudo make install

sudo nano /etc/modules
add in

snd-pcm-oss
snd-emu10k1
snd-mixer-oss

Then reboot your pc you should have sound. You might have to run alsamixer after you reboot to turn on the analog/digital output jack. Hope that helps.

---

### Post by Thief- on 2005-03-20
It helped like you *wouldn't believe.*

---

### Post by ozorba on 2005-03-21
I have been running Ubuntu 5.04 and the sound was working until last night. When I upgraded the modules using

apt-get update
apt-get upgrade

I notice that a new ALSA package had been upgraded.  Following that I lost the sound. I am using Acer Travelmate 803i Centrino. 

When I type esd I got  " /dev/dsp not found" message.  

Has anyone got any solution? Maybe a new ALSA upgrade?

---

### Post by atrus on 2005-03-22
[QUOTE=ubuntu-geek]If you get an error when running alsamixer you are in the same boat as alot of Hoary users with Audigy 2 cards, I have opened a bug report with ubuntu but they wont fix it until after Hoary is released so..[/QUOTE]

What if alsamixer generates an error, but you're not on an Audigy? SB Live Digital 5.1 here.

```

agaeris:/dev# lsmod | grep snd
snd_emu10k1            98116  0
snd_rawmidi            24928  1 snd_emu10k1
snd_seq_device          8524  2 snd_emu10k1,snd_rawmidi
snd_ac97_codec         74208  1 snd_emu10k1
snd_pcm_oss            52516  0
snd_mixer_oss          19776  1 snd_pcm_oss
snd_pcm                94920  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              25156  1 snd_pcm
snd_page_alloc          9796  2 snd_emu10k1,snd_pcm
snd_util_mem            4480  1 snd_emu10k1
snd_hwdep               9476  1 snd_emu10k1
snd                    55268  9 snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep
soundcore              10080  1 snd

```

```
atrus@agaeris:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
```

---

### Post by adbak on 2005-04-04
Ubuntu-geek:  I followed what you wrote and got all the way to the ./configure part, but at the very end of configuring, it has this message:
> checking for which soundcards to compile driver for... configure: error: Unsupported soundcard emu10k1

The full message is below:
```
adam@adamdell:/usr/src/alsa/alsa-driver-1.0.8$ sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
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
checking for current directory... /usr/src/alsa/alsa-driver-1.0.8
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

---

### Post by adbak on 2005-04-05
I don't know what was different, but I did this again and the process ran all the way through.  I then rebooted and I still have no sound.  I fiddled with aumix to no avail.  Will they have this bug fixed by the time they release (tomorrow)?

---

### Post by jimmac on 2005-04-20
I've had similar issues with sound after upgrading to the latest Hoary kernel. The matter appears to be the snd-ac97-codec module get passed an index parameter that it doesn't understand anymore. This module is required by many sound card drivers including my emu10k1. 

I wasn't able to locate WHERE exactly is this index parameter supplied though? Only after I manually insert the module I can modprobe the emu10k:

sudo insmod /lib/modules/2.6.10-5-686-smp/kernel/sound/pci/ac97/snd-ac97-codec.ko

I looked in /etc/modprobe.d/, /etc/modules.conf, but haven't found anything that would appear to passing that parameter to snd-ac97-codec. Any ideas?

---

### Post by vsujohn on 2005-04-20
I am a big linux n00b and having a great deal of difficulty getting any sound at all to work for my SB live value 5.1, (emu10k1)  anything thats possible, I have tried, im at a loss right now, I've changed all the alsa settings, but to no avail. any help?

---

### Post by GrayFox^ on 2005-04-20
I tried the steps for Audigy 2 cards and got stuck here.
```
conrad@XXXXX:/usr/src/alsa-driver-1.0.8$ sudo ./configure --with-cards=emu10k1 --with-sequencer=yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
```

*EDIT* nvm i did a apt-get install gcc and it worked fine. Starting to learn the ins and outs:)

---

