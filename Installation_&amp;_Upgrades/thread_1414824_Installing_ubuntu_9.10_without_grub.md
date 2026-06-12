---
title: "Installing ubuntu 9.10 without grub"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by suitaroh on 2010-02-24
Hello everyone,

I'm trying to set up a multiboot system running Windows7 and ubuntu on one drive and another OS on a second drive (this drive has my bootloader on it) My drive for W7 and ubuntu is partitioned like this: mbr, 100gb W7, 51gb for linux, and 445gb ntfs data partition to be read/writable by both. As my second drive has the bootloader I want to use on it,I don't need grub because it would further complicate the selection of the OS at startup-I think. If I had grub I think the startup would look like this: primary bootloader (OS1 and grub)>OS1 or grub>windows7 or ubuntu. Feel free to correct my on this though. My question is how do I install ubuntu to the 51gb partition w/o installing grub, or messing with windows or the data partition? 

Thank you for your time

---

### Post by Dayofswords on 2010-02-24
at the end, just before the OS installs, there is an advanced button, i think you can turn off grub there

make sure the bootloader you want to use can boot ubuntu

---

