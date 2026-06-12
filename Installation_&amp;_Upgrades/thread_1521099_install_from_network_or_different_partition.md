---
title: "install from network or different partition"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by Garthhh on 2010-06-30
I don't have the ability to boot from USB or CD  on this notebook
I would like to follow a procedure similar to this
[https://help.ubuntu.com/community/Insta  ... /FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")
but need to understand
where the ISO  should be stored [I can find the mostly empty partition I want to use]
what  changes to make to this code to reflect the location of the ISO?
  mkdir /tmp/install_cd
 mkdir /tmp/installer

 sudo mount  disk-image.iso -o loop /tmp/install_cd
 sudo mount /dev/sda1  /tmp/installer

 sudo rsync -a /tmp/install_cd/ /tmp/installer

 sudo umount /tmp/install_cd
 sudo umount /tmp/installer

Replace  the name of the iso to whatever you downloaded and /dev/sda1 with  whatever your new partition is.

Step 3. Edit your grub  configuration file (typically /etc/grub.conf or /boot/grub/menu.lst) to  boot from the new partition by adding the lines

title            installer
root            (hd0,0)
kernel          /casper/vmlinuz  boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd           /casper/initrd.gz

---

### Post by Garthhh on 2010-06-30
I have installed in the past using an adapter & plugging the HDD  into the bus on my pc
I've done probably 10 different installs this  way, but there is always some level of flakeyness
I am on 10.04lts  right now, but lost the ability to boot into mint,  I prefer mint [ so far ] as I have had no success getting the sound to work on 10.04lts as yet

---

### Post by Garthhh on 2010-06-30
is Gateway 7330gz, does not have a boot from USB option in bios
the  CD/DVD is broken & I'm not going to fix it, being unemployed
10.04  is ok, but my sound only seems to work in mint, I can't seem to find  the missing package
I have been able to set static ip addresses using  wicd
I have a pc [dual boot mint9 & 10.04] on this network

---

### Post by Garthhh on 2010-07-04
I did a new install by plugging the HHD drive into a different computer

---

