---
title: "Installing Ubuntu onto USB stick/drive?"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by hadmut on 2008-02-01
Hi,

is there a summary about how to install Ubuntu onto a USB hard disk or memory stick? 

There are plenty of summaries about how to copy the Live CD onto a USB stick and to use it like the Live CD. This is not what I am looking for. 

I want to run Ubuntu from a stick like from a regular hard disk, i.e. be able to install packages, modify files persistently, like a regular installation, but still have the hardware detection and auto configuration of the LiveCD. 

I guess it basically means to have two partitions, a dos partition with kernel, initrd and syslinux, and a regular ext2 partition with the main system, but it would be nice to have some docs for the caveats, and to know how to keep the autoconfiguration active. 

I need to have a regular but portable ubuntu on a USB stick. 

regards

---

### Post by zvacet on 2008-02-01
[This](http://www.pendrivelinux.com/2007/09/21/usb-ubuntu-704-persistent-install/)?

---

### Post by hadmut on 2008-02-02
Not Really, 

I do not want to have a copy of the LiveCD with an overlay, but a regular installation. 

Seems as if I have to fiddle around with debootstrap...

---

