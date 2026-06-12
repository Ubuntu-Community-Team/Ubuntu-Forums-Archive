---
title: "Doesnt complete the installation"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by eliwis on 2006-07-04
Hi, I have the ShipIt LiveCd with the installation, and I tried to install ubuntu so that it will dual boot with Winblows X(tra)P(ain), so I set two partition with in the ubuntu installer one that is about 8 GB for the root and another that is about 1GB for the swap wich I dont know what it means, when it starts to install it finishes very fast when it is about 15 percent done and it closes the installation, but when I reboot the computer it boot Winblows.
My Sepcs are:
Intel Pentium 4 HT 3GHz
ATI Radeon 9200
120 GB SATA Maxtor Hard drive
Here are the installation screens:
[http://ubuntuforums.org/attachment.php?attachmentid=12220&stc=1&d=1152030146](http://ubuntuforums.org/attachment.php?attachmentid=12220&stc=1&d=1152030146)
[http://ubuntuforums.org/attachment.php?attachmentid=12221&stc=1&d=1152030146](http://ubuntuforums.org/attachment.php?attachmentid=12221&stc=1&d=1152030146)
[http://ubuntuforums.org/attachment.php?attachmentid=12222&stc=1&d=1152030146](http://ubuntuforums.org/attachment.php?attachmentid=12222&stc=1&d=1152030146)
p.s. 
sorry for my english :)
Thanks

---

### Post by Qrk on 2006-07-04
Swap is like RAM, its part of the hard disk that your computer can use as RAM if you happen to run out. It was needed back in the days when RAM was expensive and you could run out. Most people don't need much now, but if you don't have much RAM you may want to set Swap. 1 GB is larger than you'll need.

From the screen shot, it appears that you are trying to install to an ntfs formated drive. Its been a while since I've installed Ubuntu (and I haven't used the new installer, I upgraded when that hadn't been released) but you need to select /dev/sda1 and make it ext3 formated in the partitioning phase.

---

### Post by vayde on 2006-07-04
Defrag the ntfs partition, and shrink it down first using your choice of windows partition tool.  Then install Ubuntu into the free space.  Ive noticed that sometimes the install works better if you let it compute it's own swap space rather than specifying it yourself.

---

### Post by Qrk on 2006-07-04
On the third screenshot, it seems he has chosen for / to be on an ntfs partition, and didn't make it ext3. I never thought the installer would let you attemp this, though.

---

### Post by eliwis on 2006-07-05
Thanks alot guys, I loged to windows and changed the ntfs partition to an ext3 partition and the installation worked great. The odd thing is that it didnt say anywhere in the installation that the ubuntu partition should be an ext3 type partition, lets hope that it will be fixed in the next release :)

---

