---
title: "grub boot menu has only a single entry"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by linuxdoniv on 2008-09-23
Hi

My boot menu has only one entry 

Ubuntu 7.10, memtest86+

Please tell me how I could boot with Ubuntu


Thanks a lot for any help...

---

### Post by mike1821 on 2008-09-23
In order to help you need to post your menu.lst file.

You can find this into /boot/grub/menu.lst

Use the following command to edit it:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2008-09-23
From your Live CD, open a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
Post the results of that, and also figure which is your Ubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then use that as follows:
```
sudo mount /dev/sdXY /mnt
cat /mnt/boot/grub/menu.lst
```
The above should give us enough info to help you get Grub working again.

---

