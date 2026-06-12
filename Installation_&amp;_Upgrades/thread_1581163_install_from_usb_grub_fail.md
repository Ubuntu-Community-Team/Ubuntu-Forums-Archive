---
title: "install from usb grub fail"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by ethan1el on 2010-09-24
Hello,

I've just downloaded ubuntu server 10.04.1 and put it on my usb flashdisk, the installation works fine until the point, where it tries to install grub.

The thing is, that the installer is trying to write the grub to /dev/sda (which is my usb flashdisk) and not the raid itself.

I'm using a fakeraid intel ich9r, which maps the newly created storage to /dev/mapper/isw_ecdhgaacgh_Volume0.
Why doesn't install use that instead? It sees it, partitions it, even copies files to.

---

### Post by ethan1el on 2010-09-24
I might have a hold of this - here's how I'm trying to fix this:

I hit alt-f2, open a new console. Then I do:

chroot /target (/target has /dev/mapper/is_ecdhgaacgh_Volume01 mounted)
sudo grub-install --root-directory=/ /dev/mapper/isw_ecdhgaacgh_Volume0 (somehow the installer does the same, but uses "sudo grub-install --no-floppy -force /dev/sda" instead).

CLEARLY A BUG IN THE INSTALLER.

---

### Post by ethan1el on 2010-09-24
damn, now I have a grub prompt on boot.
still not what I need.

---

### Post by ethan1el on 2010-09-24
PROBLEM SOLVED.

This document helped alot:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Here is what I did (search for: Ubuntu 8.10 (Intrepid Ibex) Installation)

1. Do the standard installation all the way till it hits the grub problem (make sure that the flash disk is in write-lock mode, otherwise you'll have grub installed on the disk instead of the raid) which means that you will be able only to boot with flash inserted.

2. hit alt-f2, open a new console.
do this:

check if /dev/mapper/isw_ecdhgaacgh_Volume0 is already mounted on /target. if not - then: (basically, it doesn't matter if it's /target or /mnt or anything else)

> mount /dev/mapper/isw_ecdhgaacgh_Volume0 /target

then:

> mount --bind /dev /target/dev/
mount -t proc proc /target/proc/
mount -t sysfs sys /target/sys/
cp /etc/resolv.conf /target/etc/resolv.conf
chroot /target/

> apt-get update
apt-get install -y dmraid
apt-get install -y grub
mkdir /boot/grub
cp /usr/lib/grub/x86_64-pc/* /boot/grub/
grub --no-curses

> grub> device (hd0) /dev/mapper/isw_ecdhgaacgh_Volume0
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

> update-grub
Hit Yes, when it offers to create a menu.lst file.

Then unmount everything and reboot. Don't forget to remove the flash disk.

---

### Post by ethan1el on 2010-09-24
One more thing, /dev/mapper/isw_ecdhgaacgh_Volume0 is my device. Your device will be named differently, but still in /dev/mapper.

Also, make sure you use Volume0 and Volume01 properly.

Rule of thumb - think of them as /dev/sda and /dev/sda1.

---

### Post by ethan1el on 2010-09-24
One more thing, /dev/mapper/isw_ecdhgaacgh_Volume0 is my device. Your device will be named differently, but still in /dev/mapper.

Also, make sure you use Volume0 and Volume01 properly.

Rule of thumb - think of them as /dev/sda and /dev/sda1.

---

