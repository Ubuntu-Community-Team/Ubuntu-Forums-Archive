---
title: "install ubuntu without CD or DVD ??"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by shashikm on 2006-08-04
hi,
  I need help on the steps to install ubuntu without using install CD/DVD ie.
directly from hard drive. I have seen some method from web and use one of them described a followed.

1. extracted & placed, vmlinuz & initrd.gz from iso image into /boot/  

2. edited menu.lst and added the following
  
title           Ubuntu Install
root            (hd0,0)
kernel          /vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd          /initrd.img
boot

and placed the iso cd image in one of the drives (my case /mnt/g)

i got the following error on boot
error 15: file not found

please help 

regards

shashi

---

### Post by FenrisAbraxas on 2006-08-04
> **shashikm said:**
> hi,
  I need help on the steps to install ubuntu without using install CD/DVD ie.
directly from hard drive. I have seen some method from web and use one of them described a followed.

1. extracted & placed, vmlinuz & initrd.gz from iso image into /boot/  

2. edited menu.lst and added the following
  
title           Ubuntu Install
root            (hd0,0)
kernel          /vmlinuz root=/dev/ram0 devfs=mount,dall ramdisk_size=17000
initrd          /initrd.img
boot

and placed the iso cd image in one of the drives (my case /mnt/g)

i got the following error on boot
error 15: file not found

please help 

regards

shashi

Probably this link will be usefull to you:

[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

### Post by dielois1 on 2006-08-04
I tried instalux but i can't get it to work. When I restart my computer it askes me to uninstall?

---

