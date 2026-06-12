---
title: "grub2 add entry restore dd"
date: 2017-12-17
forum: Installation &amp; Upgrades
---

### Post by pacecal on 2017-12-17
With** dd if=/srv/boot.img of=/dev/sda1** i can make an image. With **dd if=/srv/boot.img of=/dev/sda1** i can restore an image.

Is it possible to add an entry in the grub2 menu to restore an image?

---

### Post by yancek on 2017-12-17
> Is it possible to add an entry in the grub2 menu to restore an image? 		

You can put an entry in the /boot/grub/grub.cfg file 'boot' a restored image but you can't restore it with grub because grub is just a bootloader.  Do you have another OS with grub2 installed?

Creating an image would be done with:  **dd if=****[B]/dev/sda1** of=[/B]**/srv/boot.img**i

---

