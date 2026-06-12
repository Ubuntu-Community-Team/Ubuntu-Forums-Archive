---
title: "install 11.10 aside 10.04 grub"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by ahso4271 on 2011-11-03
hi
can i install 11.10 on a pc with various os and grub of 10.04? any special about grub to watch out?
Thanks

---

### Post by darkod on 2011-11-03
You could, as long as you have unallocated space to use as a root partition. As far as grub is concerned, you need to decide whether to use the existing, or let the 11.10 install a new one.

If using the existent, while installing 11.10 watch out for Advanced button during install (or options about where to install the bootloader) and select not to install a bootloader. Then boot your 10.04 and just use sudo update-grun which will find your new 11.10 and add it to the list.

---

### Post by recluce on 2011-11-03
> **darkod said:**
> You could, as long as you have unallocated space to use as a root partition. As far as grub is concerned, you need to decide whether to use the existing, or let the 11.10 install a new one.

If using the existent, while installing 11.10 watch out for Advanced button during install (or options about where to install the bootloader) and select not to install a bootloader. Then boot your 10.04 and just use sudo update-grun which will find your new 11.10 and add it to the list.

So did they actually fix the bug linked below?

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690926](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/690926)

Because the history of the bug says that they did not fix it for 11.10 (nor do they seem to care to ever fix it). So I assume that there is no option not to install a boot-loader. (After Natty, I don't care to look at new Ubuntu releases anymore, so I don't know first hand.)

If you are forced to install GRUB somewhere, there are a couple of options:

- install it to Oneiric's boot partition. Once you fix 10.04's boot loader (boot into 10.04 and run 'sudo update-grub') you are good to go, the GRUB installation by Oneiric will never be used.

- have an USB flash drive handy (any size, formatted to ext2/ext3/ext4 or reiserfs, should not contain data you care for), let the installer install GRUB to the MBR of the flash drive (remove the flash drive before rebooting) - the new, enhanced way of "Do not install a boot loader" :mad: Of course you still need to run "update-grub" in Lucid to make the option to boot Oneiric appear in GRUB's menu.

---

### Post by darkod on 2011-11-03
Sorry about the misinformation. I was not aware of that "bug" (oe removal of the option rather).
When I installed 11.10 on my desktop and netbook I let it install grub and run the show so I didn't even notice it.

---

### Post by drs305 on 2011-11-03
During the installation at the bottom of the partitioning screen will be a dropdown menu from which you can designate where to install Grub 2. It's easy to overlook.

---

### Post by darkod on 2011-11-03
> **drs305 said:**
> During the installation at the bottom of the partitioning screen will be a dropdown menu from which you can designate where to install Grub 2. It's easy to overlook.

I have noticed that. We were discussing the option not to install grub at all. Apparently it was removed in 11.10. Earlier it was usually Advanced button at the last step/screen during installation.

---

