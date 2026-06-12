---
title: "dual boot of &quot;red hat enterprise 5 and ubuntu 9.10&quot;"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by chuina on 2009-12-10
helo,

i'm using Ubuntu 9.10 .
now i wish to install RHEL5.
how should i proceed ?

thanks for helping me.

---

### Post by phillw on 2009-12-10
Hi,

linuxes can sahare swaps, So make an area for your RH linux, and then go thru' their manual instructions - or, you can use the auto ones & it will create an additional swap area - which is a waste of disk spce.

When it comes to GRUB - We can only support grub here - if you leave it as ubuntu grub2, then running the update of grub will get it to see the red hat area for you.

regards,

Phill.

---

### Post by chuina on 2009-12-10
thanks for response phill.
i'll try & let u know.

---

### Post by chuina on 2009-12-11
hey phill (and any one),
i've  install rhel5 but it remove everything from /boot.
all the kernel and initrd files of ubuntu9.10 is deleted.
so, only RHEL5 is booted.

on the other hand,
if i install rhel5 first and then Ubuntu9.10,
Ubuntu grub find rhel5 as a CD install image (u know anaconda..). not the boot from hard disk image.

then i tryed to upgrade rhel5 grub by dvd. it did but don't find Ununtu9.10 and swap partition.
if i use **mkswap**...., **/etc/fstab** entry for swap it detect but after reboot it again failde to find swap and of course Ubuntu9.10.  

and i wish to install them in **ext3** file-system both in a same hard disk.
if needed i'll use different swap partition but what should be the OS install sequence RHEL5 first or Ubuntu9.10 

also RHELs,Fedoras and earlier Ubuntus detect my hard disk as /dev/hdb1 . though i've only one hard disk attached in. but Karmic detect it as /dev/sda1.

i never face such zigzag in earlier versions of Ubuntu and RHEL's . so i forced to back in Ubuntu9.10 in single booting :(.

waiting for your comment, thanks

---

