---
title: "PC boots only from usb drive after Ubuntu 12.04 installation"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by kpatsis on 2012-05-22
Hello,

I just installed Ubuntu 12.04 on my dual boot system (Windows 7 and Ubuntu). For the installation i used a usb flash drive and on the install screen I chose Replace Ubuntu 11.10 with 12.04. Now my pc boots only from the usb drive and when I boot from my hard drive it pops out some old grub interface with the correct entries that dont work ("no partition found"). What can I do to fix it?


Thanks

---

### Post by roelforg on 2012-05-22
Reinstall grub.
Do a google search and see what article matches your situation the best.

---

### Post by darkod on 2012-05-22
Boot your ubuntu with the usb stick connected.

Check whether your hdd is /dev/sda or /dev/sdb with:
sudo fdisk -l (small L)

Then just use that to install grub2 to the MBR of the disk:
sudo grub-install /dev/sdX

You might also want to deselect the stick as destination for grub2:
sudo dpkg-reconfigure grub-pc

You select/deselect with Space.

---

### Post by kpatsis on 2012-05-22
Worked perfectly! Thank you very much. :)

---

