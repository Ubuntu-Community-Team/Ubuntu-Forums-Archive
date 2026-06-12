---
title: "installing ubuntu from a usb memory stick"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by manu2010 on 2007-08-22
Dear Sirs,

I need to install Ubuntu on a laptop where the cd drive is out of order. So I decided to use the usb stick. I followed step by step, a couple of tutorial:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2#comment-841](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar-p2#comment-841)

Everything seems to go well, until I reboot from my memory stick  and get the message: "Operating System Not Found"

I did everything written in the tutorial (even fixing the mbr with lilo), but I always get the same message

can anybody Help?
tanks

---

### Post by windstory on 2007-08-22
It might be that the mbr on usb is corrupted. Try to "sudo apt-get install lilo" then "lilo -M /dev/sdb" (change /dev/sdb to proper one on your system) to fix it.

The following link is more useful in installing from usb disk:
[http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/](http://www.pendrivelinux.com/2007/02/12/usb-ubuntu-tutorial-for-linux-users/)

---

### Post by manu2010 on 2007-08-22
I have already fixed the mbr, but it gives me always the same message. 
I tried to follow also this new guide but it gives me the same problem

what could it be?

---

### Post by windstory on 2007-08-22
so did you put usb device before hard disk in boot sequence?

---

### Post by manu2010 on 2007-08-22
yes, I did it

---

### Post by manu2010 on 2007-08-22
It still doesn't work. I have bought an other usb memory but it give me exactly the same message : Operating System Not Found.

what could it be?

---

### Post by windstory on 2007-08-22
Well, you can try network boot and install by setting up PXE boot on your laptop and using another machine serving as dhcp server and tftp server. It is easy to find instructions by googling. But it is a more complicated process.

For usb install, it'd be useful to show your command history during your install process. That could possibly pinpoint where exactly went wrong.

From the error message, linux boot image was not loaded at all. Would you please post your usb device partition info by using "fdisk /dev/sdx" (replace x with yours) then "p" command? Also, your FAT16 partition root directory content (ls).

BTW, which ubuntu version do u use?

---

### Post by manu2010 on 2007-08-25
I think I realized what was going wrong with the usb memory stick. I tried it on a new laptop bought this year and it works fine. Maybe it is the bios of my old  laptop (I bought it 4 and half years ago) that doesn't support the boot from the usb memory stick. 
Now I won't be at home for a week. I'll try to do the network installation when I'll be back home.
thanks for helping

---

### Post by manu2010 on 2007-08-25
7.04 version

---

### Post by manu2010 on 2007-09-03
I have followed this guide [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot) 
trying to install ubuntu 7.04 on my laptop by netboot , but I receive the following error on startup: 
no DHCP or PROXYDHCP offers were received
what could it be?

---

