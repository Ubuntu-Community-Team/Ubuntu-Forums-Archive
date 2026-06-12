---
title: "Install GRUB but keep Vista Bootloader"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by zach382 on 2007-09-18
I am planning on taking my hard drive and splitting it into 2 separate partitions to install Ubuntu (7.04) on it. I am wondering if there is a way to install grub on the partition I am installing Ubuntu on and keep it from messing with the MBR. I already have Vista installed on one partition and I don't want to risk messing it up and keep it from booting. I have a program that will allow me to add entries to the Vista boot menu (EasyBCD 1.7).

---

### Post by arkara on 2007-09-18
you cant do that man
there is one mrb only
so have to install grub
if you want to remove ubuntu then pop in vista cd and boot from it
go to the repair console
select your windows install
type the admin pass
and then type : fixmbr
then type exit for the pc to reboot
it should boot to windows vista
then right click to my computer... and select manage there you can delete the ubuntu partitions

BE CAREFULL FIRST DO THE FIXMBR STUFF AND THEN DELETE THE PARTITIONS OR YOUR COMPUTER WONT BOOT
 

oh and just to know how boot works
when you install grub you dont delete windows boot loader you just create a link to it
when you choose win from grub it simply hands over  the boot process to the windows boot loader and then windows boot up i hope i helped
with regards :D

---

### Post by logos34 on 2007-09-18
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
(-->'Vista before linux' #2)

---

### Post by zach382 on 2007-09-18
@ arkara: Thanks for describing the boot process.

@ logos34: Thanks for that link it looks like what I need.

---

