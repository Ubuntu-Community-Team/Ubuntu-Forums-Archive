---
title: "Using Grub to boot ISO images"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by Tclarkie on 2009-12-18
I've have followed a set of instructions to allow me to boot ubuntu iso's off a external hdd using grub 2.

I followed all the instructions and now a get dropped to a grub shell every time i boot off it.
I think the problem is that it cant find a kernal image or something.
Sorry for the newbie post

---

### Post by phillw on 2009-12-18
> **Tclarkie said:**
> I've have followed a set of instructions to allow me to boot ubuntu iso's off a external hdd using grub 2.

I followed all the instructions and now a get dropped to a grub shell every time i boot off it.
I think the problem is that it cant find a kernal image or something.
Sorry for the newbie post

Hi & Welcome

We have 2 possible issues
1) You didn't follow the instructions (e.g. simply putting a full-stop in the wrong place can break it)
2) The instructions are wrong (e.g. they missed out a full stop !)

Can you post the instructions you have !!

Phill.

---

### Post by darkod on 2009-12-18
> **Tclarkie said:**
> I've have followed a set of instructions to allow me to boot ubuntu iso's off a external hdd using grub 2.

I followed all the instructions and now a get dropped to a grub shell every time i boot off it.
I think the problem is that it cant find a kernal image or something.
Sorry for the newbie post

Do you require them to be ISOs or you just thought it's easier?
From one side, having the ISO is helping that you can just quickly replace it with newer ISO. On the other hand, the ISO has to be "unpacked" during the boot which might make problems (emulation, etc). I was trying to boot on a small usb stick of 2GB both Ubuntu 32bit and 64bit versions and CloneZilla ISO.
It couldn't work because it needed more free space on the stick to unpack the ISO.
What I found out testing around, it's better to unpack the ISO in it's own folders, or even better partitions, and use in menu.lst of the grub bootloader the command same as in the config files from inside the ISOs. Worked great. Because the files are unpacked it doesn't need extra room to do that.
So that's one option to consider.

---

