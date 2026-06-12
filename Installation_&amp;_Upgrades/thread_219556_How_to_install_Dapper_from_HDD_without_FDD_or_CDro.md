---
title: "How to install Dapper from HDD without FDD or CDrom"
date: 2006-07-20
forum: Installation &amp; Upgrades
---

### Post by fr33ky on 2006-07-20
Hi folks, i have this problem - i want to install Dapper on a computer that does not have CDROM nor FDD. I have tried the network boot, but without success, so my solution is to remove the HDD, copy Dapper install on to the HDD and install from there.

My question is - how to set up the HDD to be able to boot and install Dapper - it is formatted to fat32 and empty. I gues I shoul d change somehow the MBR, maybe include GRUB, but because I am fresh "convert: to Linux, i am not familiar with this - is it possibel to prepare/copy files to this HDD in windows system? 

thanx

---

### Post by john_spiral on 2006-08-09
You will need to boot from either a cd/floppy/usb or another hard disk to partition the destination drive. You can't boot the ubuntu installer from a disk and install to the same disk.

---

### Post by avtolle on 2006-08-09
I don't know if this will be helpful, but [http://www.ubuntuforums.org/showthread.php?t=232201&page=2](http://www.ubuntuforums.org/showthread.php?t=232201&page=2), post 12 in particular, follow link in said post. It isn't the easiest thing to do, IMO, but it looks like he was able to do something like you are wanting to do. HTH.

---

### Post by john_spiral on 2006-08-10
Firstly will still need to partition the disk from another media before the installer will work correctly.

avtolle is correct in suggesting you use the hdmedia files:

initrd.gz
vmlinuz

from:

[http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)

for the boot process.

(a) Partition the drive - add ext2 partition, create the /boot/install dir
(b) Place the above files into the newly created ext2 partition, plus your .iso file you intend to install (ubuntu, xubuntu, kubuntu) into /boot/install
(c) Install grub
(d) add the following entry to menu.lst, to boot the installer, menu.lst file should be inside /boot/grub

title Install Ubuntu
kernel   (hd0,0)/boot/install/vmlinux vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd   (hd0,0)/boot/install/initrd.gz

you might need to change 'hd0,0' to 'hd0,1' or 'hd0,2' depending on how many partitions you have created.

reboot the machine, choose 'Install Ubuntu', during the install choose to partition the part of the disk not containing the initrd.gz, vmlinuz and iso file.

good luck

---

### Post by jaripetteri on 2006-11-17
I manage start the installation with this guide but is there a way to change the default installation package? I would like to install lamp-server and I'm using server iso but it never ask which package to install... :-k

---

### Post by john_spiral on 2006-11-18
Did the install complete?

Once the basic server has been installed, you can use apt-get to download all the exciting software.

---

### Post by jaripetteri on 2006-11-18
yep I already know how to do network installation and I did it and apt-get all I need. I just were looking for plan lamp-server install from hdd. anyway I'm just fine now, thanks.

---

