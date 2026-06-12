---
title: "usb boot"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by travolter on 2009-12-03
hi,


i'm running ubuntu 8.04 from my usb flash drive. now It would be easier if I could run it from lacie external harddisk. now my question is.

is this possible without having to format my harddisk and/or dammaging my files.
and if that's possible. if I run it from usb is it then still possible to copy/save/... files to my harddisk?

thanks

grtzz

---

### Post by darkod on 2009-12-03
You want to move it from the usb stick to usb external hdd?

---

### Post by travolter on 2009-12-03
no. instead of running it from my normal usb flash drive, I want to run it from my external hard drive so that, if it is possible, i can store files directly to my external hard drive without going to the c: drive of my computer. 

by the way: I want this because i don't have enough usb-ports to connect a normal usb flash drive, an external hard drive and the usb drive with ubuntu on. using an usb hub doesn't work either. then it only reads or the hard drive or the falsh drive.

---

### Post by darkod on 2009-12-03
Are you running it with the Try Ubuntu option from the stick right?

---

### Post by travolter on 2009-12-03
yes because i've got trouble with my c: drive

---

### Post by efflandt on 2009-12-03
Best way to do that is to shrink the vfat partition on the Lacie first to make as much room as you want for Linux, then install a regular ext3 or whatever Linux filesystem (and swap if you need it).  If you still run Windows, you may want to defrag the Lacie first.

Best way to resize partitions is probably most recent version of gparted-live CD.  I have never had problems resizing a vfat or ntfs partition properly.  When I tried to use it on a different laptop drive that had crashed, it safely refused to touch that partition until Windows fixed it.

While installing Ubuntu on it, pay attention to the **Advanced** button near the end when it provides a summary of what it is going to do.  You need to use Advanced to put grub in the mbr of USB drive (unless that is the only PC you use it on, and want the default to your main hard drive mbr).

---

### Post by darkod on 2009-12-03
Sorry, I don't know how to transfer it on your external hdd without formatting it.
But you could consider actually installing 9.10 on your external usb hdd, it can work like that. If that's what you want. But if you don't have cd-rom then both your usb stick and usb external hdd have to be plugged in to install ubuntu on the hdd.

---

### Post by travolter on 2009-12-03
> **efflandt said:**
> Best way to do that is to shrink the vfat partition on the Lacie first to make as much room as you want for Linux, then install a regular ext3 or whatever Linux filesystem (and swap if you need it).  If you still run Windows, you may want to defrag the Lacie first.

Best way to resize partitions is probably most recent version of gparted-live CD.  I have never had problems resizing a vfat or ntfs partition properly.  When I tried to use it on a different laptop drive that had crashed, it safely refused to touch that partition until Windows fixed it.

While installing Ubuntu on it, pay attention to the **Advanced** button near the end when it provides a summary of what it is going to do.  You need to use Advanced to put grub in the mbr of USB drive (unless that is the only PC you use it on, and want the default to your main hard drive mbr).

so you say that i first have to make a partition on my lacie. but then i don't understand it. do i have to use this guide [http://www.pendrivelinux.com/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/usb-ubuntu-804-installation-from-windows/) that i orignilay used to get linux on my usb or do i have to actually intsall it?

---

