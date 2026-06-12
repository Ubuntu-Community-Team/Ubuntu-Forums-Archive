---
title: "Give installation directory for apt-get"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by arulkrishna on 2011-10-29
I have installed ubuntu in 3 GB drive and it is full. But I have free partitions. How I can use "sudo apt-get install"  command to install in the free space rather than the default location. Its like where we can specify folder path to install as in windows.

---

### Post by raja.genupula on 2011-10-29
Hi 
  I think its not gonna possible man.

---

### Post by dino99 on 2011-10-29
3 Gb is way too small :(

here is a standard config installation:

first you need to choose a good formatting tool: [http://partedmagic.com/](http://partedmagic.com/), install it on cd or usb stick, its a nice tool in case of trouble in future.

usually Ubuntu is installed that way :

- prepare partitions with external prog (partedmagic)
- built 3 partitions:
1) / which is the main one (root), need to be bootable and is ext3 or ext4 formated with about 10/12 go
2) swap: about twice the real ram but max 2 gb (4 gb if suspend/hibernation is used)
3) /home which is your data partition: as much go that you need

- download the "alternate" image and install it on usb ( unetbootin) if you are able to boot on usb, or burn it on cd (4x max speed). the "alternate" let you customize your installation, so as you have previously prepared your partitions and noted their names (/dev/sda or so), its easier to make a safe installation and place grub, when asked, on the / mbr partition.

---

