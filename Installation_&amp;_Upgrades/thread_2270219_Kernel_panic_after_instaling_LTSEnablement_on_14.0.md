---
title: "Kernel panic after instaling LTSEnablement on 14.04"
date: 2015-03-21
forum: Installation &amp; Upgrades
---

### Post by Gerhard_Huebner on 2015-03-21
I have tried to upgrade my Ubuntu 14.04 to 14.04.2 using the instructions for installing the LTS enablement stack:

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

I have got a standard installation with LVM and encrypted hard disk, as offered by the installer, without any additional changes to the configuration.

When booting with an external hard drive connected, the internal encrypted hard disk is not recognised and the kernel gets stuck during the boot process. (The external drive just contains data, no boot sector). When I disconnect the external drive, then the internal encrypted drive is recognised and Ubuntu boots completely and I can log in. After one minute, I get a kernel panic (caps and num lock LEDs flashing). This is fully repeatable, happens everytime I try again. The problem prevails with the kernel 3.16.0-31. I have to switch back to the existing 3.13.0-46 in order to run without kernel panic.

I have tried this hack:

[http://askubuntu.com/questions/526193/preseeding-3-16-hardware-enablement-kernel-requires-manual-update-initramfs](http://askubuntu.com/questions/526193/preseeding-3-16-hardware-enablement-kernel-requires-manual-update-initramfs)

in order to get the new kernel running properly but this has absolutely no effect on the failure to recognise the encrypted internal HD or the kernel panic.

The only specialty in hardware configuration that may affect this issue is that I have got a laptop computer with Nvidia Optimus and I am running the non-free NVidia drivers and using Bumblebee to enable graphics acceleration and OpenCL support.

---

