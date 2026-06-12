---
title: "Ubuntu not booting"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by llamositopia on 2013-01-18
I had Ubuntu 11.10 for a very long time and recently attempted to update to 12.04 on my laptop. The battery died while installing. As you can imagine, this led to a lot of problems. While trying to fix it, I have made it worse so now it will not boot. I have 12.04 on a USB, ready to install but whenever I make an attempt to, I always end up with problems because it does not have sufficient rights to overwrite the previous installation. Through Recovery Console, I have terminal commands and I also have the Debian boot manager. No other OS. Does anyone know how I can remove Ubuntu either through BIOS, grub or Terminal?

tl;dr How can I uninstall Ubuntu via BIOS, grub or Terminal?

---

### Post by Bucky Ball on 2013-01-18
Welcome to the forums.

Do you have and CD/DVD drive? You could try making a gparted cd, boot from that and delete the Ubuntu partition. Then try installing from the USB again. 

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Other things is, when you boot from the USB, can you get to a desktop (try ubuntu)? If so, launch gparted from there and delete the partition, then try installing from the desktop from the USB.

---

### Post by dannyboy79 on 2013-01-18
> **llamositopia said:**
> I had Ubuntu 11.10 for a very long time and recently attempted to update to 12.04 on my laptop. The battery died while installing. As you can imagine, this led to a lot of problems. While trying to fix it, I have made it worse so now it will not boot. I have 12.04 on a USB, ready to install but whenever I make an attempt to, I always end up with problems because it does not have sufficient rights to overwrite the previous installation. Through Recovery Console, I have terminal commands and I also have the Debian boot manager. No other OS. Does anyone know how I can remove Ubuntu either through BIOS, grub or Terminal?

tl;dr How can I uninstall Ubuntu via BIOS, grub or Terminal?if you boot to a usb installed ubuntu, you should be able to install gparted within the live session, and format your internal harddrive so it's ready for to be installed on.

---

### Post by llamositopia on 2013-01-18
> **dannyboy79 said:**
> if you boot to a usb installed ubuntu, you should be able to install gparted within the live session, and format your internal harddrive so it's ready for to be installed on.
The current installation is for some reason blocking me even from reaching the Try Ubuntu desktop. No I do not have CD drive (netbook). It could be that mounting the iso to the USB failed. I have not yet retried mounting. I would assume, however that it would work. I mounted it using UUI. The suggested one by Ubuntu.

---

