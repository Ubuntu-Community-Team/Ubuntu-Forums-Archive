---
title: "Grub Issue"
date: 2008-09-19
forum: Installation &amp; Upgrades
---

### Post by B3n3v3nt3 on 2008-09-19
Hi, I bought an eee pc 1000h, and I tried to install ubuntu eee. The installation went fine, but it froze when trying to restart. After force-restarting the netbook, all I get is a grub prompt instead of the boot menu, which means I think, that the grub is not working well. How can I fix it or even delete it?

Thanks

---

### Post by B3n3v3nt3 on 2008-09-19
I've tried this while searching around:

>root (hd0,3)
>kernel /boot/vmlinuz-2.6.24-21-eeepc root=/dev/hda4
>initrd /boot/initrd.img-2.6.24-21-eeepc
>boot

it shows a lot of lines but stops at [163.467042] sd 0:0:0:0: attached scsi generic sgo type 0
and doesn't do anything more.
Help?

---

### Post by caljohnsmith on 2008-09-19
First, let's make sure your Grub MBR is pointing to the correct partition, so try the following from your Live CD:
```
sudo grub
grub> find /boot/grub/stage1
```
That should return your Ubuntu partition in the form of (hdX,Y), use that:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, and also post the following:
```
sudo fdisk -lu
```

---

