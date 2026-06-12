---
title: "Please help, How to install ubuntu on second HD?"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by P@trick99 on 2008-07-18
Hi there

I have Dell Vostro (Intel Core2 Duo CPU T7500 @ 2.2GHz, 3GB Ram, Nvidia GeForce 8600GT Vista H.
This laptop has 2 Hard Drives (2x160 GB)

I have tried to install Ubuntu on the second HD and I have selected GRUB loader to be install on the same HD (hd1)(sdb) I don't want to have the grub loader on my (hd0)(sda) where my vista is installed. If I want to boot Linux Ubuntu F12 boot menu select boot from second HD. That is how I would like to have Vista & Linux Ubuntu on my laptop.

After installation F12 boot from second HD I have "Error 17 Cannot mount selected partition". I have spend 2 days trying to install Ubuntu 8.04 

I have installed Ubuntu on my old laptop PIII 900Mhz and it works fine,(no windows installed)
I think, I am doing something wrong with (hd1)

Installation;

1 welcome (select language)
2 Where are you? (City, time zone)
3 Keyboard layout
4 Prepare disk space
*Guided - resize partition (sda) vista
*Guided - use entire disk 
(sda)
(sdb) [COLOR="Red"]I selected this one [/COLOR]
*Manual
5 Who are you and password
7 Ready to install
*Advanced - Boot loader (device for boot loader installation) [COLOR="Red"]That is where I don't know what to choose I have tried (hd1) ,  dev/sdb , /dev/sdb1 , (hd1,0) It didn't work.
[/COLOR]
So where is the problem? (I am new to Linux, please write replies in English, not Linux)

Thank you

Patrick

---

### Post by falcon61102 on 2008-07-18
Boot up from your liveCD and mount your HD with your Ubuntu installation on it.  Open up the /boot/grub/menu.lst file and post that here.  Also, run:
```
sudo fdisk -l
```
And post that here.  That will list your partitions.  Note that "-l" is a dash and a lower case L.

---

### Post by Pumalite on 2008-07-18
Search:
Dualboot Two Hard Drives - Ubuntu Forums

---

