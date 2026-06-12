---
title: "Selecting partition to install Ubuntu"
date: 2008-05-23
forum: Installation &amp; Upgrades
---

### Post by sapien on 2008-05-23
Hi, I'm pretty new to this way of contact (Forums) and to Linux. I'm using Windows XP on C:\drive. I have D:\empty and formatted to Linux, I also have E:\Data and F:\Backup. When I insert the Ubuntu CD (8.04) it tells me it's going to install it on sda1, which I think is my C: drive. Is that correct? How do I get it to install on my D:drive?

---

### Post by Pumalite on 2008-05-23
Get Gparted Live CD and 'shrink' XP:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Right click on XP, choose resize from the menu. In the new space, create 3 'New' partitions:
10 GB for '/'
1 GB for /swap (/swap=RAM in laptops)
The rest for /home.
Install Ubuntu, go Manual and choose partitions already prepared. The installer will do the rest.

---

### Post by sapien on 2008-05-24
Pumalite - Thanks for the help. I downloaded and ran Gparted but it was indicating it was going to reformat my whole drive. I don't want that. I've got a 250Gb HD with 4 partitions. I had vista on D:\ with 40Gb. That has been deleted and reformated. It is there I want to put Ubuntu. Maybe I'll try further down the track when I've read up a bit more. Once again - Thanks.

---

