---
title: "Install ubuntu 10.10 with dualboot to windows 7"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by angrykiwi on 2010-10-21
Hi everybody,

I have a problem installing ubuntu 10.10 (64 bit) with dualboot together with windows 7.

The situation is a follows: on the pc is windows 7 (home premium) installed, the windows bootloader is in the MBR and THIS CANNOT BE CHANGED (it's not a private pc).

I wanted to do this the way I have done with the previous ubuntu realeaes I used (8.04 and 9.04): install everything normaly and only tell the installer to install GRUB into /dev/sda5 (root-partition of the ubuntu-System). Then I used 
```
dd if=/dev/sda5 of=/mnt/usbdrive1/bootlinux.bin bs=512 count=1
```
to copy the bootsector in a file and integrate this file into the  Windows Bootloader. The problem is: this file has only zeros inside (00hex), so it seems, that there is no GRUB written into the bootsector of the linux-partition.

The whole procudure works without any problems using Windows 7 and ubuntu 9.04, but I want to have the new release of ubuntu!

Has anyone an idea?

Yours
angry kiwi

---

### Post by Megaptera on 2010-10-21
Is a Wubi install an option for you? No partitioning or major changes:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by angrykiwi on 2010-10-21
Not really. The partitions already exist. I really don't link these "operating-system in operating-system" solutions. I want a **real** Linux coexisting with my windows 7. The only problem is, that I have to use the windows bootmanager (if it would be my own pc I would just install GRUB into the MBR, but unfortunatly I can't).

The funny thing is, that my described solution worked on different distributions without any problems (including ubunut up to 9.04).

Yours
angry.kiwi

---

### Post by Megaptera on 2010-10-22
As a temporary measure, could you boot and run 10.10 from a pen-drive (USB stick) with persistence? 
I've got my back-up 10.04 on a flash-drive and it boots and loads as fast as the installed version.

---

### Post by angrykiwi on 2010-10-22
Hi again,
 
this could be a possible solution for me. Perhaps I can use my USB-Harddisk doing so (4 or 8 GB of a stick may not be enough for me). Is there anything I have to care for during installation?
 
Yours
angry.kiwi

---

### Post by bcbc on 2010-10-22
Never used this, but it sounds like it will do what you want.
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

PS I just noticed the instructions require that you install grub to the MBR temporarily.

---

