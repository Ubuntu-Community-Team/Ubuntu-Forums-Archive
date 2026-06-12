---
title: "Multi-Boot DVD"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by nierewa on 2008-05-02
Hi,

first, sorry for my english.
I used to speak german :)

I've downloaded Ubuntu, Kubuntu and Xubuntu.

Now I want this distros on a DVD with a boot menu to
choose which distro would be installed (with bootable cd wizzard and
isolinux).

folder structure:

-dvd
|_ bcdw
|_ isolinux
|_ kub804
|_ ub710
|_ ub804
|_ xub804


The bcdw.ini: "Linux Distribution installieren ; /isolinux/linux.bin

The isolinux.cfg to load the used kernel (vmlinuz)

```
DEFAULT /casper/vmlinuz

GFXBOOT bootlogo

LABEL

  menu label ^Kubuntu 8.04 installieren

  kernel /kub804/casper/vmlinuz

  append  file=/kub804/preseed/kubuntu-kde4.seed boot=casper only-ubiquity initrd=/kub804/casper/initrd.gz quiet splash --

LABEL 

  menu label ^Ubuntu 7.10 installieren

  kernel /ub710/casper/vmlinuz

  append  file=/cdrom/ub710/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/ub710/casper/initrd.gz quiet splash --
  .....
```


The kernel loads, but then I get the following message:


```
BusyBox v1.1.3 (Debian 1:1.1.3-5 ubuntu 12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs)
```

Anybody knows what wrong?

---

