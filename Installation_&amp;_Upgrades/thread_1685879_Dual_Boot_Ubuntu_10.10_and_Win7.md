---
title: "Dual Boot Ubuntu 10.10 and Win7"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by Muhnamana on 2011-02-11
Ok, I've tried this a couple of times and can't load Ubuntu.

Here's the scenerio, I have 3 partitions.
      /dev/sda1 = ntfs (Win7)
      /dev/sda2 = ext4 with the / mount point
      /dev/sda3 = swap space

I've some tutorials where I need a /boot partition as well and others where I just need the root partition.

At the bottom, there is a drop down box for you to select the device for boot loader installation.
Those options include /dev/sda, /dev/sda1 (Win7) and /dev/sda2.

Can anyone assist in what else I need to do to get the dual boot  working? My first thought is to install the boot loader onto /dev/sda  but I'm unsure. It keeps booting Win7 and can't get the option to load  Ubuntu.

---

### Post by zvacet on 2011-02-11
I think you should install it on  /dev/sda because that way grub will be installed on MBR and you will have dual boot.

---

