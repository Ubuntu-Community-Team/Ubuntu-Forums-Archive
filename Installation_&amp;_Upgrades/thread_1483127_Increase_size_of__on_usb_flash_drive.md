---
title: "Increase size of / on usb flash drive"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by shakeeb on 2010-05-14
Hi

I am booting ubuntu from my usb flash drive and It works very well, but after installing additional s/w using apt I ran in to the problem of low disk space in /. I used the unetboot to create the bootable usb drive.
My drive is 8 gb in size .

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**aufs                 1007M 1005M  1.6M 100% /**
none                 1002M  292K 1002M   1% /dev
/dev/sdb1             7.5G  713M  6.8G  10% /cdrom
/dev/loop0            672M  672M     0 100% /rofs
none                 1007M  212K 1006M   1% /dev/shm
tmpfs                1007M  196K 1006M   1% /tmp
none                 1007M  116K 1007M   1% /var/run
none                 1007M  4.0K 1007M   1% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
/dev/sda1              56G   42G   15G  75% /media/System

How do I do this ? Gparted does not work :confused:


Thanks

---

### Post by darkod on 2010-05-14
What are you trying to achieve? unetbootin is usually used to create a bootable usb stick that you can use to boot live mode of ubuntu and install to a computer. Like a replacement of live cd, instead of a cd you are using usb stick.

But if you plan to have a full installation on the stick and use it like that, usually you would install ubuntu with the stick as destination. Is that what you did? The procedure is the same as installing on hdd but the destination is a usb stick.

---

### Post by ajgreeny on 2010-05-14
Gparted would do it, but not from your installed system.

You will need to do it from a live CD version, or if you are using a netbook with no CD drive, from another usb live version while the current external OS drive is still plugged in.

---

### Post by shakeeb on 2010-05-14
> **darkod said:**
> What are you trying to achieve? unetbootin is usually used to create a bootable usb stick that you can use to boot live mode of ubuntu and install to a computer. Like a replacement of live cd, instead of a cd you are using usb stick.

But if you plan to have a full installation on the stick and use it like that, usually** you would install ubuntu with the stick as destination. Is that what you did?** The procedure is the same as installing on hdd but the destination is a usb stick.
No, that's not what I did . I guess I will have to do that. 

Thanks for the help

---

### Post by darkod on 2010-05-14
> **shakeeb said:**
> No, that's not what I did . I guess I will have to do that. 

Thanks for the help

During the partitioning step take note of your stick device name, for example /dev/sdf, and in the last screen in the installer before clicking Install, click on Advanced and select grub2 to be installed on the same device, /dev/sdf for example. Not on a partition (there should be no number).

If you don't do that grub2 might go to the internal hdd on the computer where you will be performing this, and once the usb stick is unplugged, that computer will not have a bootloader to boot. This is VERY IMPORTANT!

---

### Post by wilee-nilee on 2010-05-14
> **darkod said:**
> during the partitioning step take note of your stick device name, for example /dev/sdf, and in the last screen in the installer before clicking install, click on advanced and select grub2 to be installed on the same device, /dev/sdf for example. Not on a partition (there should be no number).

If you don't do that grub2 might go to the internal hdd on the computer where you will be performing this, and once the usb stick is unplugged, that computer will not have a bootloader to boot. This is _**very important**_!

+1

---

