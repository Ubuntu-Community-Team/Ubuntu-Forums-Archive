---
title: "ubuntu fails to install"
date: 2016-02-25
forum: Installation &amp; Upgrades
---

### Post by greg105 on 2016-02-25
Hi All, 

over the last few days ive been trying to install ubuntu in dual boot with windows 7 on an HP pavilion g series laptop. 

Firstly i'm using a sandisk cruzer 8gb usb stick, that ive written the ISO to using UUI. 

Ive set the BIO to boot to usb first.

It boots to the Ubuntu menu - try or install etc.

I select Install. 

I type in network credentials and it connects to the net no problem. 

I click install and it gets through two circles on the loading screen and kicks me to the black select OS screen where my only option is booting Windows 7.

This happens every time I choose Install. 

When I select try, it works perfectly fine and I can use ubuntu no problem when reading directly from the USB.
Ive tried both 14.04 and 12.04 and the same errors continually occur.

Ive ran the boot repair program too, still wont install. 

Please help

---

### Post by yancek on 2016-02-25
Generally, windows will install itself and take up the entire drive.  Do you have any unallocated space available outside your windows partitions on which to install Ubuntu?  If you can boot the Ubuntu usb, do that and open a terminal and run this command and post the output here:  sudo fdisk -l(Lower Case Letter L in the command).

---

