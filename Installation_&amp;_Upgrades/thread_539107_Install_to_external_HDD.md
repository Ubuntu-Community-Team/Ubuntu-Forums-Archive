---
title: "Install to external HDD"
date: 2007-08-30
forum: Installation &amp; Upgrades
---

### Post by darkness193 on 2007-08-30
Hi i've just bought an external harddrive in the hopes of installing ubuntu onto it. I just wanted to know weather the ubuntu installer will install the bootloader (GRUB) to my external HDD? Also if so will the ubuntu installer leave my internal HDD entirely alone?

Thanks

---

### Post by darkness193 on 2007-08-30
Anyone?

---

### Post by confused57 on 2007-08-30
Here's a howto that might help:
[http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external](http://ubuntuforums.org/showthread.php?t=226638&highlight=success+external)

You might be able to do a regular install to your external hard drive, using the live cd...what you would want to do is set your external drive in bios to boot before your internal hard drive, before you boot up the live cd to install.  There should be an "Advanced" button that allows you to select where to install grub, here you need to type in the designation shown by the partitioner for your external hard drive, e.g. type in /dev/sdb, or whatever your drive is designated as.

---

