---
title: "Install Kubuntu from Hard Drive"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Kemono on 2010-01-27
Hi guys

Here's my situation: I have two hard drives, one internal and one external. I have Mint 7 installed on my external hard drive and would like to install Kubuntu 9.10 on it, and I'd like to do it from HDD. I tried following the instructions [[COLOR="DarkOrange"]here[/COLOR]]("http://deepbluespaces.blogspot.com/2008/07/install-ubuntu-804-from-hard-disk.html") but I'm stuck at the partition number (hd0,4) because I don't know my number. Is there any way I could find out which number is my home partition?

P.S. If that fails, is there another easy way to do this (without using USB sticks or CDs)?

Thanks.

---

### Post by dabl on 2010-01-27
```
fdisk -lu
``` should show all drives and partitions on the system (assuming you are running a Linux OS).

I don't know of an "easy" way to do a *buntu installation, with no CD and no bootable USB stick.  I suppose you could use the "mount the ISO file and copy all the files out of it" approach, with the target being your chosen partition on the external drive.  I wouldn't call it "easy", but it's a way that is known to work.  Getting the boot menu set up will be among the challenges, once you've got the basic file-copying task done.  Google should help you find "how to install from a mounted ISO image" or something like that.

EDIT:  Here's bit of a tutorial for another Linux distro:  [http://www.linuxforu.com/teach-me/tips-tricks/install-linux-straight-from-an-iso/](http://www.linuxforu.com/teach-me/tips-tricks/install-linux-straight-from-an-iso/)

---

### Post by Kemono on 2010-01-27
Thanks. I'll try it now and keep you posted.

EDIT: Nope. It wants me to unmount the whole hard drive before installing. It seems it has to be done from a second hard drive. The installer keeps crashing otherwise. I'll try and borrow a flash drive and install it that way this time but in the future I'll make a Linux partition on my internal hard drive just for this type of installation. Thanks again.

---

