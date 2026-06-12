---
title: "Grub Install"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by kylilin on 2010-01-31
so when I boot up I get the following error: hard disk read failure non bootable devices


booted up from the live disk and tried the following commands:

sudo fdisk -l

got the directory I wanted to boot from, which is /dev/sda1

then entered: sudo mount /dev/sda1/mnt

got this reply: mount: can't find /dev/sda1/mnt in etc/fstab or /etc/mtab

I am now banging my head against the walls.

Anyone have any ideas on what's wrong?

---

### Post by darkod on 2010-01-31
You need space in between:

sudo mount /dev/sda1 /mnt (if that is your root partition)
sudo grub-install --root-directory=/mnt/ /dev/sda

That will put grub2 on the MBR of /dev/sda but only if /dev/sda1 is your / partition.

The above commands are if you are trying to install grub2 using 9.10 livecd. For earlier version the commands are different.

---

