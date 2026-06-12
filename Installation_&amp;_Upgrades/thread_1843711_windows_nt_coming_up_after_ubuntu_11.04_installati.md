---
title: "windows nt coming up after ubuntu 11.04 installation"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by venkatad on 2011-09-13
I have installed Ubuntu 11.04 from cd on my laptop HP Pavillion dv6. It has windows 7 before installtion. After I installed I am not getting two options while I boot my system. I did the following

1. chosen parallel operating systems
2. It asked for selecting the partition. I selected one of the partition from windows, it gave error saying that your partition is not at the root.
3. I then followed instructions and created a partition and also swap partition
4. Then installed the ubuntu. I was not able to see windows partition and windows o/s is not coming up during booting process. (It directly lands on ubuntu)

Attached my disk partition screen shot.


I am very much worried as I have a lot of data in windows partition. Please help.

---

### Post by Quackers on 2011-09-13
Have you run ```
sudo update-grub
``` in a terminal?

Also please run ```
sudo fdisk -lu
``` and post the output.

---

