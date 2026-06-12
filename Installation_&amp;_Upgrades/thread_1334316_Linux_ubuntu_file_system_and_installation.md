---
title: "Linux ubuntu file system and installation"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by bpascal123 on 2009-11-22
Hi,

I have been using Ubuntu for a while however i don't have an "academic" understanding of Linux in general.

- I'd like to know how to keep configuration gnome or kde or ... files such as desktop police size, desktop panels configuration, icons size... from one cd installation to another. From this document : 
[https://help.ubuntu.com/7.04/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/7.04/installation-guide/i386/directory-tree.html)

...i understand a "etc" partition would do the thing (keep desktop configuration files the same from one cd install to another).

For now, I have a separate root, home, boot and usr partition.

 If i install Ubuntu with gnome over from a cd, do programs in usr will remain if i don't format it the usr partition I have created? As install takes quite long i don't feel like experimenting it. If someone could tell, it would be really nice.

 The Boot hd partition :

I don't know if having this partition would help face for instance installing a new system on a usb flash drive without messing grub configs on hd.

Thanks,

Pascal

---

### Post by zvacet on 2009-11-23
Your setting should be on your home partition under hidden files ( ctrl + h to seee them).Yes,if you don´t format usr partition all files will be there after install.For fresh install format just root partition and **do not format other partitions.**

---

### Post by bpascal123 on 2009-11-24
Hi

Thank for your help zvacet,

Does etc have nothing to do here? Config files for gnome are in home but maybe other config files are in etc? Shouldn't i care?

I have also set up  a boot partition. Would that help me if i install let say kubuntu on a flash memory drive. Because last time i tried, kubuntu moved grub onto ssd during install and even during update. That meant, without kubuntu ssd on the flash drive, the system couldn't boot unless with a live cd.

Thanks again,

Pascal

---

