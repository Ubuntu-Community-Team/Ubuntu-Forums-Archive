---
title: "creating new /boot partition"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by tatoniss on 2008-06-04
I accidentally erased my /boot partion, so i can no longer boot ubuntu. Is it possible to create a new one with out formating and reinstalling my whole system
I have hardy 8.04
Your help would be greatly apperciated.

---

### Post by mikewhatever on 2008-06-04
Boot partitions usually contain the kernel and files needed to boot. I'd be quite surprised if there was an easy way to recover that.

---

### Post by tatoniss on 2008-06-04
I was making a new bigger /boot partion and i copyed them to it, it just is not being reconized by the computer but i have the files backed up, they were from the boot folder. So can i use those to make a new one without erasing my system

---

### Post by sisco311 on 2008-06-04
All you need is to boot up a live cd, create the new /boot partition,
copy the files from the old one and reinstall grub.

EDIT: and edit the fstab and change the uuid of the /boot partitio[URL="https://help.ubuntu.com/community/GrubHowto#head-f60bd54bfea5b5afbbb8eab20586240d973cdde3"]n.

HowTo reinstall grub.[/URL]

---

### Post by sisco311 on 2008-06-04
> **mikewhatever said:**
> Boot partitions usually contain the kernel and files needed to boot. I'd be quite surprised if there was an easy way to recover that.

I don't know if this is easy or not, but it works.
Just for fun, the steps:

i.) boot the live cd

ii.) mount the boot partition(/mnt/boot)

iii.) copy the kernel from the live cd:
```
cp -r /boot/* /mnt/boot/
```iv) create the grub directory and copy the needed files:
```
mkdir /mnt/boot/grub
cp -r /usr/lib/grub/x86_64-pc/* /mnt/boot/grub 
```v.) reinstall grub

vi.) create the menu.lst file

vii) reboot

---

### Post by tatoniss on 2008-06-04
What if the partion is not mounted as boot, or called boot, how do i mount it, how do i make a menu.lst file.

sorry Im pretty new to ubuntu, i would just reinstall it but it took me forever to figure out how to install drivers for d-link wirless uunless i could copy the drivers and all the configureation to put on the fresh install

---

### Post by sisco311 on 2008-06-05
> **tatoniss said:**
> What if the partion is not mounted as boot, or called boot, how do i mount it, how do i make a menu.lst file.

sorry Im pretty new to ubuntu, i would just reinstall it but it took me forever to figure out how to install drivers for d-link wirless uunless i could copy the drivers and all the configureation to put on the fresh install


Boot the live cd and open the Partition Editor (gparted).
Find the name of your root partition ("/") and boot partition ("/boot").

Assuming the root partition is /dev/sda1 and the boot partition is /dev/sda2 run this commands from the terminal
(Note: You will need to change sda1 and sda2 from the commands):
```
sudo mkdir /mnt/root
sudo mount -t ext3 /dev/sda1 /mnt/root
sudo mount -t ext3  /dev/sda2 /mnt/root/boot

```open the file browser:
```
gksudo nautilus
```and copy the backup files to the /mnt/root/boot directory.

in the terminal:
```
ls /mnt/root/boot
```the output should be something like:
> abi-2.6.24-16-generic             initrd.img-2.6.24-17-generic.bak
abi-2.6.24-17-generic             initrd.img-2.6.24-18-generic
abi-2.6.24-18-generic             initrd.img-2.6.24-18-generic.bak
config-2.6.24-16-generic          memtest86+.bin
config-2.6.24-17-generic          System.map-2.6.24-16-generic
config-2.6.24-18-generic          System.map-2.6.24-17-generic
grub                              System.map-2.6.24-18-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-17-generic
initrd.img-2.6.24-17-generic      vmlinuz-2.6.24-18-generic
reinstall grub:
```
sudo grub-install --root-directory=/mnt/root /dev/sda
```You need to change the uuid of the partition in the menu.lst and fstab.

To get the uuid:
```
sudo blkid /dev/sda2
```the output:
> /dev/sda2: UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" TYPE="ext3where x is a digit.

edit the files:
```
gksu gedit /mnt/root/boot/grub/menu.lst
gksu gedit /mnt/root/etc/fstab
```in the menu.lst
> title        Debian GNU/Linux, kernel 2.6.24-16-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=**xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx** ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
in the fstab:
> # /dev/sda2
UUID=**xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx** /boot           ext3    relatime,defaults        0       2reboot.

---

