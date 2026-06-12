---
title: "Installing and booting from external hard disk"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by ittiam on 2007-07-10
I am planning to install ubuntu on an external hard disk and boot my laptop from that? I have not done this before. Can anyone throw light as how feasible it is and also how the peformance will be when i boot from an external hard disk plugged in through an USB.

thanks

---

### Post by phidia on 2007-07-10
As long as your laptop supports booting from usb it should be ok. I don't have any real world figures on performance through usb, but since that bus is fast enough (usb2) to transfer video and large files rapidly I don't think there's any big performance hit. 
You will need to make at least one partition on the external drive. I recommend the cli partitioner cfdisk. It's fast and fairly intuitive. Once you have partitioned you can run the install disk and hopefully install there. There are several ways to accomplish this though so you could try to get the partitioner on the install disc to do it also.

---

### Post by ittiam on 2007-07-10
Thanks a lot for the reply! Will try it

---

### Post by logos34 on 2007-07-10
It's pretty easy now...no hassles with the usb modules, etc...just make sure you send grub to the MBR on the USB drive and not the internal, and edit a few line in menu.lst and you're set!

Check out this thread (especially #502):

[http://ubuntuforums.org/showthread.php?t=80811&page=51](http://ubuntuforums.org/showthread.php?t=80811&page=51)

---

