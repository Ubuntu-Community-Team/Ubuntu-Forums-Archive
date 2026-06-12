---
title: "Config file for kernel 2.6.24-21-generic"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by Pierre Habraken on 2008-09-10
Hello,

I recently installed with success new modules snd-hda-intel.ko, agrmodem.ko and agrserial.ko on a laptop hp 6720s running Ubuntu 8.04.1 with kernel 2.6.24-19-generic, in order to have support for the built in Agere modem hardware. These modules are available ready to install at [http://linmodems.technion.ac.il/packages/ltmodem/11c11040](http://linmodems.technion.ac.il/packages/ltmodem/11c11040).

Since that time I had to upgrade the kernel to version 2.6.24-21-generic, in order to get the wireless link (broadcom) working.
The latter is now ok but not surprisingly the modem does not work any longer.

As I absolutely need both types of connection (modem and wireless), I am trying to re-build the required modem and sound modules, but I could not success for now.

I installed both packages linux-headers-2.6.24-21-generic and linux-source-2.6.24.
After having unpacked the kernel source tree, I copied file /boot/config-2.6.24-21-generic as /usr/src/linux-source-2.6.24/.config.
Then I discovered that this config file does not enable ALSA, and thus is not consistent with the running 2.6.24-21-generic kernel (sound is actually working).

I tried to select right options and modules "by hand", using 'make menuconfig' but could not get the sound working after reboot.

My question is : where (how) can I get a config file which reflects exactly the configuration of the 2.6.24-21-generic kernel ?

Thanks in advance for any help.

Pierre

---

### Post by cgomez.cu on 2008-10-22
Hi,

how I can compile the driver agrmodule to kernel 2.6.24-21-generic, I recently installed precompiled modules snd-hda-intel.ko, agrmodem.ko and agrserial.ko running Ubuntu 8.04.1 with kernel 2.6.24-19-generic, but i update kernel

---

