---
title: "How do I boot pre-installed Ubuntu/Fedora with installation CD/DVD?"
date: 2007-10-05
forum: Installation &amp; Upgrades
---

### Post by regnumimbrium on 2007-10-05
Hey All,

I've been working on setting up a triple-boot Vista/XP/Linux system and am pretty close to success. My major concern, however, is the fast frequency at which new Linux distros are released. Because of this, I'm trying to figure out the best way to perform a clean install of Linux to a single partition and keep Vista's bootloader (which loads all 3 OSs) completely intact (i.e. no GRUB installation). 

I've already ironed out a longer process which involves installing some Linux distro w/ GRUB, backing up its boot parameters in a ".bin" file, repairing Vista's bootloader, and then re-adding the ".bin" file to XP's "boot.ini".

After noticing that, for example, Fedora 7 (I'm not sure about Ubuntu), gives the option to **not** install GRUB, I started wondering how much I could shorten the above-said process (for users who frequently switch or re-install their Linux distro).

Here's what I've got: if I can install the Linux distro **without** GRUB and then still boot into the Linux distro in some way (Note: I'd really prefer if someone could tell me a way to boot into the Linux distro via the distro's installation CD/DVD, as this would make the whole process a great deal easier), then I'll be able to copy the boot parameters into the ".bin" file, restore it in XP, and substantially cut down the steps required to complete this process.

Recap: is it possible to boot a Linux distro - at least for Fedora/Ubuntu - from its installation CD/DVD **without** installing a bootloader to the MBR?

Thanks (very much!) in advance,
-Peter

---

