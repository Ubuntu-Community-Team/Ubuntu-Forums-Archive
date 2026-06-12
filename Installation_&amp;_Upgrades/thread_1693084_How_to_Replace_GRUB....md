---
title: "How to Replace GRUB...?"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by Its_Rishi on 2011-02-22
After installing windows 7 the ubuntu 10.10 grub was missing...
how can i replace grub and dual boot both windows and ubuntu linux...?

---

### Post by Pizarro on 2011-02-22
I did this and this was the cure
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by thefasterblueone on 2011-02-22
Have a look here.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Bob@dorset on 2011-02-22
I would suggest that you also download Supergrub2 you can do this by typing "Supergrub2" into a seearch engine and downloading the ISO file.  Once you have this creat a CD so that you can always rescue your system using it.  Supergrub2 allows you to boot any of your operating systems from the CD by searching for them on your hard disk when you boot from it.  :)

---

### Post by wilee-nilee on 2011-02-22
> **Bob@dorset said:**
> I would suggest that you also download Supergrub2 you can do this by typing "Supergrub2" into a seearch engine and downloading the ISO file.  Once you have this creat a CD so that you can always rescue your system using it.  Supergrub2 allows you to boot any of your operating systems from the CD by searching for them on your hard disk when you boot from it.  :)

Super grub is a great tool.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Download the one in the middle grub2, boot into Ubuntu and run this command to load the mbr.
sudo grub-install /dev/sda
then 
sudo update-grub
this is assuming that the sda hard drive is where Ubuntu is installed.

Other wise boot a live Ubuntu 10.10 cd follow these, three commands, first is the fdisk -l to identify the partitions the next two to load grub2.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

