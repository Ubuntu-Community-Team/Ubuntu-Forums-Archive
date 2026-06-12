---
title: "Can't log into ubuntu after installing a fresh copy of window"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by Calvert on 2014-04-23
Hi,

I installed a fresh copy of window which previously the hdd also contain Ubuntu. How do I get back the part where the bios will give me the OS selection to boot? 

I tried running a bootable usb for ubuntu and repair using boot-repair but it seems nothing changed.

Is there a way to add that in in window or any other ways that can recover it? I hope it is not too difficult as I am very new to linux.

Thanks in advance.

---

### Post by Double.J on 2014-04-23
Hi there!

You're absolutely correct that boot repair is pretty much the easiest was to get back to where you were. What could matter is if it's a newer windows 8 laptop or an older xp/vista/7 machine. If it's an older laptop with a bios, the following should help:

if you boot the live disk and the open a terminal with ctrl+alt+t, and type
```
sudo fdisk -l
``` we can get an idea of how your disk is partitioned.

basically you want to make sure that boot repair installs grub to the first sector of the hdd (/dev/sdX where X is a letter, not followed by a number)

if it is a newer windows 8 laptop, then you are using uefi and gpt partition table - if you've made a bios partition on the drive you'd need to install to there

from inside windows there is easy BCD, but again this depends which windows version you are running?

Jj

---

### Post by Calvert on 2014-04-23
Hi, 

Thanks for your reply and well I didn't get much of it though.

I am running WIndow 7 pro, sorry that I didn't mention and you said first sector which means the window partition? 

Form gparted in Ubuntu where I boot up using usb, /dev/sda3 is the place where my Ubuntu is. /dev/sda2 is my Window 7 and /dev/sda is the system reserved of window.

I tried using the boot repair and choose for the recommended choice and I didn't go for the advance button but nothing happen.

If I'm not mistaken easybcd is not a free software, right?

---

### Post by robire on 2014-04-23
Hi,
boot from installation disk ( no installation, just use bthe try ubuntu option )

open a a terminal and:

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair

copy and paste line by line and press enter after each line inserted.

---

### Post by Double.J on 2014-04-23
Hi there!

very sorry for the confusion; it's one of those strange times where some users (with new windows 8 laptops) use one system and everyone else is using the same system we've had for 30 years. It sounds like you're one of the second group. This means that your hard drive likely is laid out like this:

mbr (first 512bytes- /dev/sda) -> partition 1 (dev/sda1) -> partition 2(/dev/sda2) and so on.

the windows reserved partition is usually the first partition on the drive, and the windows 7 c drive the second, then ubuntu comes third (the actual partition numbers can be anything, but that's usually the order)

because the mbr is 512 bytes it's too small to contain a whole bootloader, so it just contains information for the computer telling it what to boot. When you installed windows 7 again, it put it's bootloader in /dev/sda and wrote over grub's entry. You have to put the bootloader back in the mbr, so install grub to /dev/sda 


that should get the menu back.

easy bcd is not free as in open source, but for individual use you don't have to pay for it ;)

---

### Post by Calvert on 2014-04-25
No luck, I tried boot repair by booting a bootable usb again but no changes. I put the bootloader in /dev/sda still no luck.

I don't know if I did wrong or something but can you list some of the common errors or any other solution like a few command lines might fix it?

I also tried Easybcd by choosing grub2 and linux for the os selection.

My mind is blank and have almost no idea.

---

