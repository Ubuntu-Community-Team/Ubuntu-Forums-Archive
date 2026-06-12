---
title: "Grub ubunty/XP"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by Licicin on 2007-09-13
Hi,

PC produces Grub error after installing Grub
i installed XP, than ubuntu from live CD

sudo fdisk -l 
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda3  /mnt/root
ls /mnt/root
ls /mnt/root/boot
sudo grub-install --root-directory=/mnt/root/dev/sda

i used information from
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Licicin on 2007-09-14
I have fixed the problem.
i just should not use the same disk for Windows and ubuntu.

---

### Post by vacman1 on 2007-09-14
Super Grub may be a useful utility for you in the future... pressed for time and don't have a link right now... but a simple search here should turn it up :)

---

