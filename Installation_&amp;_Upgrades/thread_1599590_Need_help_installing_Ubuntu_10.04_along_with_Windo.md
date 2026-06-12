---
title: "Need help installing Ubuntu 10.04 along with Windows 7"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Homi Kaushal on 2010-10-18
Hi,

I am trying to dualboot windows 7 and ubuntu 10.04

I was following this guide for installation

[http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-04-lucid-lynx/)

When I reached the final step of installation(Ready to install) of above guide, I didn't understand the part where i should install the boot loader. 

After Clicking install( without changing advance settings) installation is completed but I dont get the boot menu for selecting operating system and windows boot up.

So I need help with the boot loader?

Thanks in advance

---

### Post by oregonbob on 2010-10-18
From your description it sounds like you must have answered "NO" when it asked if you want to install the boot loader. I think you want to install grub, the Ubuntu boot loader. I think it is pretty easy to do but you'll have to boot from the install media again. Or if you are installing on a second hard disk, you can go into bios and tell it to boot from second hard disk.

On the link you give, I wouldn't agree to install grub on second hard disk unless you have specific needs. You should search ubuntu documentation for "Installing grub" and "dual boot".

Did you install Ubuntu on same drive or a second hard disk?

---

### Post by Rubi1200 on 2010-10-18
Assuming you are installing Ubuntu after Windows, you should not need to answer any questions about where to install GRUB unless you are clicking on the advanced options.

By default, Ubuntu installs GRUB to the MBR of the first drive (sda). Unless you have a secondary drive, that is where GRUB needs to go so please don't fiddle around (friendly warning because otherwise you will have to reinstall GRUB).

Under advanced options, leave the default which should say sda.

Good luck!

---

### Post by Homi Kaushal on 2010-10-18
kk problem is solved... I have 3 hard drives and in my previous installation, Ubuntu was using other drive which also have a windows boot loader(sda) (:confused: )... So this time i choose the hard drive(sdc) in which windows and ubuntu are installed(different partitions) and everything went perfect... Using Ubuntu at the moment.. :popcorn:

Thanks for response...

Can you pls answer my other query I created swap on my first attempt of installing Ubuntu but as it didnt work so i deleted ubuntu partition and kept swap. I didnt created another swap for new installation. Do I have to delete the old swap and create new or can i use the old one? thanks

---

### Post by Rubi1200 on 2010-10-18
You should be fine with the swap partition that was already there.

To check for certain:

```
cat /etc/fstab
```

If you see the swap partition there (with the correct UUID and partition number) then all should be good.

---

