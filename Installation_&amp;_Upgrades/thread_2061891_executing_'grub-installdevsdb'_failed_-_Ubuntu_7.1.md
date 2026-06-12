---
title: "executing 'grub-install/dev/sdb' failed - Ubuntu 7.10 to 12.04"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by tehforum on 2012-09-23
Hi,

I put the ubuntu 12.04 iso onto a bootable usb drive

then all was fine until this error came up

executing 'grub-install/dev/sdb' failed

I selected the option where it installed onto the whole hard drive (wiping out all previous partitions. I believe the whole 500gb drive is called /dev/sda


I now have a screen saying

Sorry, an error occurred and it was not possible to install the bootloader at the specified location.

How would you like to proceed?

Choose a diffrent device to install the bootloader on:

/dev/sdb - the one that faild
/dev/sda -ATA SAMSUNG HDS02IJ (500.1 GB)
/dev/sda1

If I choose /dev/sda, will it fix the problem?

Thanks for any help

---

### Post by tehforum on 2012-09-23
Update

I chose /dev/sda and ubuntu wouldn't load.

it said it installed though

Now I'm trying to install boot-repair via the usb however

whenever I type in
sudo add-apt-repository ppa:yannubuntu/boot-repair

It says
E: Invalid operation repository

help

edit: i typed in the command wrong, currently installing boot-repair

...this update is taking ages

---

### Post by tehforum on 2012-09-23
Okay, I gave up on boot-repair, and I tried re-installing and it works.

great.

---

### Post by darkod on 2012-09-23
Just for info, choosing /dev/sda which is the MBR of the hdd was the correct choice. Not sure why you said it didn't work after that (didn't load ubuntu).

---

### Post by YannBuntu on 2012-09-25
Please use the Thread Tools to mark it [SOLVED].

---

