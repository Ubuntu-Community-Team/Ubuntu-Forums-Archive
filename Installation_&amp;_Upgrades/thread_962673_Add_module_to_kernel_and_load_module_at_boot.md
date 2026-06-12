---
title: "Add module to kernel and load module at boot?"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by jagomai on 2008-10-29
Hello,

I have a Highpoint Rocket ATA non-RAID 133 controller card in my machine:

02:0a.0 RAID bus controller: HighPoint Technologies, Inc. HPT302/302N (rev 02)

I know there is native support for this card in the kernel (I used Gentoo before, and it was a breeze to compile my own kernel and activate this as built-in) but I don't know how to enable it in Kubuntu.

I'm using Kubuntu 8.10 right now, and an 'lsmod | grep hpt' gets me only:

pata_hpt37x            19712  0
libata                177312  4 ata_piix,ata_generic,pata_hpt37x,pata_acpi

I checked out the config file in /boot/, and found:

CONFIG_PATA_HPT366=m
CONFIG_PATA_HPT37X=m
# CONFIG_PATA_HPT3X2N is not set
CONFIG_PATA_HPT3X3=m
# CONFIG_PATA_HPT3X3_DMA is not set

uname -r gives me:

2.6.27-7-generic


I think there should be more of these "hpt" modules... I feel pretty lost now.

Does anybody know how to activate this module and make my controller card work?

Thanks alot!

---

### Post by fendres on 2008-10-29
If it is a loadable module (i.e. you expect it to be listed with lsmod) you can load it via 'sudo modprobe <modulename>'. If you want it permanently I think it has to be mentioned in a file of which I do not remember the name (/etc/modules?).

---

### Post by puppywhacker on 2008-10-29
Hi,

fendres is right. if modprobe works fine to load the module you can put in in /etc/modules to load it each time

however, if you want to boot from the device, and it is a module and not compiled in the kernel you could still use the initrd load the module before the kernel starts. In that case you need to use mkinitramfs to create a new initrd.

---

### Post by jagomai on 2008-10-29
> **puppywhacker said:**
> Hi,

fendres is right. if modprobe works fine to load the module you can put in in /etc/modules to load it each time

however, if you want to boot from the device, and it is a module and not compiled in the kernel you could still use the initrd load the module before the kernel starts. In that case you need to use mkinitramfs to create a new initrd.

Alright, I tried to load the pata_hpt366 module with modprobe - and it loaded successfully (no output).

How do I check if the hard drives are working? I tried to see if fdisk could see them

fdisk -l

but they were not visible.


Also, what do I do if there is no module for the hard drives in the kernel version that Kubuntu uses?

---

### Post by puppywhacker on 2008-10-30
Normally device names are named something like sda or hdb with the partition numbers. fdisk -l will show you the partitions of the active default device, not the whole list of devices. In your case (and my old computer with an HPT376) the device name is a longer (about 8 characters), I just can't remember them so well. but the following two commands may help identify the device name. I ran the disks in a RAID, but that is irrelevant to the device name.
```

dmesg | egrep "[s|h|x]d[a-p]"
lshal | grep "block.device"

```

I'm not sure why kubuntu wouldn't have the module, I thought the only difference between kubuntu was the use of KDE instead of Gnome, but you could still use the regular Ubuntu and switch to KDE by installing the KDE libraries.

Otherwise you could compile the kernel yourself, although I've never been so successful using the kernel-source and/or kernel-headers to compile a single kernel module. So I always end-up compiling everything from the fresh linuxhq source.

---

### Post by jagomai on 2008-10-31
Thanks a lot for the info puppywhacker, but the problem remains. I tried to do:

dmesg | egrep "[s|h|x]d[a-p]"

but this didn't show those harddrives at all, only my other ones. No change after trying to modprobe both pata_hpt366 module and pata_hpt37x module. 

I guess I will compile my own kernel later - the only problem I have is that I don't know what options Ubuntu has as default, and if the configs for the Ubuntu kernel is completely compatible with any other kernel source.

The ideal for me would be to simply copy all the config for the Ubuntu kernel and just add the module for my controller card as a built-in. But I don't know if I can do this since perhaps the Ubuntu kernel config is different in some aspects?

---

### Post by claesl on 2008-11-07
I have the same problem with Ubuntu Server 8.10 amd64 with my HPT302 card.
The module pata_hpt37x is loaded automatically but not pata_hpt366 that seems to be the correct driver for this card but like you mentioned before nothing happens when loading the module. If I boot kubuntu 8.04 Live CD that requires the kernel option "all_generic_ide" the hpt366 module is loaded and all drives are detected. Could this be a bug in the new kernel or what could be missing? One thing I can think of is that when I installed Ubuntu server, I did not need the all_generic_ide option.

If you find a solution, please write it down here. :)

---

