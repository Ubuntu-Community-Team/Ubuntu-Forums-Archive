---
title: "How do I recompile the kernel?"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by vbertola on 2005-06-05
I installed Hoary on a new PC, but the kernel shipped on the CD will not recognize my integrated Ethernet card on the motherboard. I need to install a kernel patch that I downloaded separately from the manufacturer site, and thus I need to recompile the kernel.

I have downloaded the latest kernel package, but I can't config it - all of 'make menuconfig', 'make gconfig' and 'make xconfig' fail because some packets are missing (and, honestly, configuring the kernel via a text-only interface with 'make config' is a total pain). I have looked for the package 'libncurses-dev' but apparently it's neither on the CD nor on archive.ubuntu.com/archive (the online package pool). I don't have the network, so I need to get it separately and install it via dpkg, I guess.

Considering that I don't have the network, how do I compile a new kernel in Ubuntu? It seems to me that the necessary -dev packages are not installed by default, and this leaves users like me in an almost impossible situation.

Thanks,

---

### Post by mtron on 2005-06-05
Follow the wiki entry howto rebuild a [kernel](http://www.ubuntulinux.org/wiki/KernelHowto) 

The needed packages can be downloaded from another computer, and installed on ubuntu. See azz reply to [this](http://ubuntuforums.org/showthread.php?t=6060) thread for details how to downlad packages.

---

### Post by az on 2005-06-05
Use linux-tree instead of linux-source!

You will not get screwed up with configuration!

---

### Post by vbertola on 2005-06-11
[QUOTE=mtron]Follow the wiki entry howto rebuild a [kernel](http://www.ubuntulinux.org/wiki/KernelHowto) 

The needed packages can be downloaded from another computer, and installed on ubuntu. See azz reply to [this](http://ubuntuforums.org/showthread.php?t=6060) thread for details how to downlad packages.[/QUOTE]

I tried to follow the Kernel HowTo, but I didn't get past the first step: apt-get tells me that 'kernel-package' does not exist. Similarly, it won't find 'linux-source', 'libncurses-dev' or 'libqt3-dev' (the latter two, by the way, would at least allow me to compile the kernel outside of the  packaging system). Perhaps it's because my network card is not working?

What do I do? I've tried to find those packages by browsing the pool at archive.ubuntu.com directly, but they're not there. Also I've seen the pointer at debian-cd, but if I'm not wrong I would need another Hoary PC to build custom CDs, which I don't have. Is there any way to get those packages via direct HTTP links?

Thanks,

---

### Post by mtron on 2005-06-11
did you add the [extra repositories](http://ubuntuguide.org/index.html#extrarepositories) ?

---

### Post by xtrm on 2005-06-11
if u have gcc, u can use the "not debian" way :wink:

cp your current config file (/boot/config-??? or maybe /proc/config.gz) to /usr/src/linux/.config
Then cd /usr/src/linux/ && make oldconfig && make && make modules_install 
cp vmlinux(ppc) or arch/i386/boot/bzImage(x86) to /boot and play with symbolic links in / and your bootloader.

It should run if your patch applied to an existing module (& if selected in the "all in modules" ubuntu kernel).

---

### Post by dresnu on 2005-06-11
The best (and the clearest) site I found is this [http://newbiedoc.sourceforge.net/system/kernel-pkg.html#BUILD-KERNEL-PKG](http://newbiedoc.sourceforge.net/system/kernel-pkg.html#BUILD-KERNEL-PKG).
Just apt-get linux-source-<version of the kernel> and follow the iinstructions on that site from paragraph 3.2. After you have compiled and installed the new kernel(so that is till paragraph 6) scroll right down this thread [http://www.ubuntuforums.org/showthread.php?t=9807&highlight=mkinitrd](http://www.ubuntuforums.org/showthread.php?t=9807&highlight=mkinitrd)   and do the mkinitrd part that's in tarasbulba post. Aftes that just update-grub, make a little prayer and reboot ;-)

---

### Post by dresnu on 2005-06-11
well i guess you can apt-get linux-tree-<version> instead of source as azz suggested. Sorry but i had not seen his post before and that's something new to me too  :grin:

---

