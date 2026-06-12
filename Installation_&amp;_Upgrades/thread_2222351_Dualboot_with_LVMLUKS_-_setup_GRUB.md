---
title: "Dualboot with LVM/LUKS - setup GRUB"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by Holger_Danske on 2014-05-06
Dear UbuntuUsers,

I've to install two Ubuntu-Systems on the same machine. Something that is descript in many place if the systems are unencrypted becomes very hard in that moment the system are encrypted.

This is my setup:
[LIST]
[*]sda1 (256MB) P-Partition /boot 
[*]sda2 (320GB) P-Partition /  -- MainSys 
[*]sda5 (64GB)  L-Partition /  -- MultiMediaSys 
[/LIST]
 
I figure out how to install this both systems encrypted. But installing the second system it becomes clear that I will come in trouble. While install the second system the install-process can't see the other installation. Totally clear, it can't look into the encrypted partition. Therefore no GRUB was configured for Dual-/Multi-Boot. That means, I've to configure GRUB manually.

It's not easy the find an tutorial anounce this (and nothing to post here, because my native language is german) but I come too the following (unsuccessful) solution:

> sudo su
cryptsetup luksOpen /dev/sda2 MainSystem
mount /dev/mapper/MainSystem /mnt
mount /dev/sda1 /mnt/boot
mount -o rbind /dev /mnt/dev
mount -t proc proc /mnt/proc
mount -t sysfs sys /mnt/sys
chroot /mnt
grub-install /dev/sda

I know, this solution is incomplett. This setup will, even if it runs, only configure the MainSystem. It will not, and that is the most imported part, setup both, Main and MultiMediaSystem. But as I said, even this simpler example I didn't get running.

It ended up, that I still have the encrypt sda5

>  UUID------------......(sda5)

and even if I give the passphrase for this system the system will not start

> Gave up waiting for root device
....
(intiramfs)


So, it's totally frustrationed. It seams to be so abnormal to install 2 encrypted system that I can not find any solution for it in the WWW.

Because both installation are totally unworked I will be grateful for every hint.

Andreas

---

