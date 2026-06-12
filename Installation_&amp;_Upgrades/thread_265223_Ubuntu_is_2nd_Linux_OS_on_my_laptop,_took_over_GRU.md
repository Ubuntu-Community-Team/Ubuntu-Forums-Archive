---
title: "Ubuntu is 2nd Linux OS on my laptop, took over GRUB"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by stewharr on 2006-09-25
I have a laptop with a single 100 Gig HD on it.  I have windows on /dev/sda1, and /dev/sda2 is an extended partition that encompasses my linux swap paritition /dev/sda5, and a reiser paritition that SUSE Linux Enterprise Desktop 10 is installed on /dev/sda6, and an ext3 parition that Ubuntu is installed on /dev/sda7.  In SLED I have the option to install GRUB on the boot sector of one of my paritions, but I don't have that option for Ubuntu, or at least I don't know how to make it do that.  I would like to use Grub as installed by SLED to be my first boot menu, then chain grub as installed by Ubuntu from there.  Looking at my Grub config for SLED, he currently does not know about Ubuntu and I fear that an update will wipe my ability to boot into Ubuntu.  Creating a boot disk for both would be nice too, in case Grub on the MBR ever messes up on me.  Thanks for any help that you can give me on how to force grub to install onto another partition.

---

