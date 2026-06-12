---
title: "Installing Ubuntu"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by AaronC on 2006-12-21
HELP! i was informed i could install the ISO from a partition and this is how far i have..i have placed the grub files on a new partition as follows.

boot/grub/

with a menu.list file with the following information on:

> title Install Ubuntu
root (hd0,1)
kernel /boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /boot/initrd.gz

and then i have


boot/grub/boot/

with the ISO and the two files initrd.gz, vmlinuz.

i also have a new partition for the OS to go..what do i do next, do i need to install grub...if so how? and if not how do i boot that partition.

---

### Post by wpshooter on 2006-12-21
> **AaronC said:**
> HELP! i was informed i could install the ISO from a partition  



What is your source for this information ?

Are you trying to install Ubuntu on your computer that already has an O/S on it or is Ubuntu going to be the only O/S on this computer ?

Does you computer have a CD-ROM drive ?

Thanks.

---

### Post by AaronC on 2006-12-21
xp is already installed, and yes  i had a cd drive but all my cds are 650 meg! ](*,)

---

### Post by wpshooter on 2006-12-21
If the drive on this machine is a CD-RW or better, then my recommendation would be that you buy yourself a few good name brand (I like Imation) CD-RW media 700mb or more, so that you can use them over and over and over again.

Then burn the ISO image to one of those babies at 4X or slower and boot to that CD and you are on your way.

Make sure that you check the integrity of the CD by running the verification test that is found on the initial Ubuntu boot screen menu.

Good luck.

---

