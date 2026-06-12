---
title: "Ubuntu alongside Windows 10 on Asus H170 Pro Gaming"
date: 2017-03-21
forum: Installation &amp; Upgrades
---

### Post by prudhvirazz on 2017-03-21
I am trying to follow the general guidelines of disabling the secure boot. But in the Asus H170 UEFI I can't find such option. 

I want dual boot because I play games on Windows and do Machine/Deep Learning on Ubuntu. GTX 1080 | i5 6500.

I have spent almost a day but still confused. If anyone has done in Asus H170/Z170 please help me.

My bios looks like this. This guy confused me a lot. 

[https://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility](https://www.technorms.com/45538/disable-enable-secure-boot-asus-motherboard-uefi-bios-utility)

---

### Post by mastablasta on 2017-03-21
a few pointers here: [https://ubuntuforums.org/showthread.php?t=2311543](https://ubuntuforums.org/showthread.php?t=2311543)

---

### Post by prudhvirazz on 2017-03-22
I now have a new question. I have C Drive - has Windows. D drive - has movies, games and Data Sets for Machine learning. G drive has 50 Gb - where I want to install ubuntu. 
1. how should i split 50 gb in to home, root and swap ? I am thinking 20 for Root and 15 each for swap and home.
2. i swill still be able to read and write from drive D right ?

---

### Post by oldfred on 2017-03-22
As long as you use Something Else install option, you have total control over what partitions you create, change or delete.
I prefer to use gparted to create my partitions in advance, but still have to use Something Else to choose(change button) to tell system which partition is which.

With only 50GB I might just use / & swap. And if you have more than 4GB of RAM, you may not need swap but I suggest 2 or 3GB if a larger drive just to have some swap.

My typical install is 20 to 30GB for / (root) including /home and then 100GB or more for /mnt/data. I used to have two data partitions, one NTFS when I still had XP. But I move almost all data normally in /home into data partition. Only the mostly hidden user configuration settings are still in my /home so it is tiny.

With Windows 8 or 10 you have to make sure Windows fast start up or always on hibernation is off. It keeps all NTFS partitions mounted, and then you cannot read/write from Linux.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

I have an Asus Z97 and it required a lot of UEFI settings changes. The main one for UEFI is "Windows" and "Other". Other is Secure boot off, as fine print says if installing Windows 7 use "Other" as Windows 7 does not support UEFI Secure Boot. 
 Asus-ar screenshots oldfred
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

