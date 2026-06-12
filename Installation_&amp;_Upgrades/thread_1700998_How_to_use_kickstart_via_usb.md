---
title: "How to use kickstart via usb?"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by JerkyChew on 2011-03-05
I have a bootable USB key that I've created with UnetBootin. On a 32-bit Ubuntu 10.10 machine I installed and used system-config-kickstart to create a ks.cfg file with the settings I'd like to use for an unattended install. However, I can't find much info on pointing to a kickstart file on USB; the documentation all points to either pXe boot or CDrom install, neither of which are available to me.

UNetBootin creates a menu system at boot. I've modified syslinux.cfg and added my own entry at the bottom. However, when I try to boot from it I'm just kicked to a busybox terminal with a limited list of commands. I guess I'm just not using the correct syntax. Below are the entry UnetBootin uses for a standard install, followed by the entry I've created. 

I'm not married to UnetBootin so if there's another option to boot off USB, I'm open to it.

```
label ubnentry2
menu label ^Install Ubuntu
kernel /casper/vmlinuz
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash --

label ubnentry6
menu label ^Install kickstart
kernel /casper/vmlinuz
append ks=/ks.cfg initrd=/casper/initrd.lz

```

---

