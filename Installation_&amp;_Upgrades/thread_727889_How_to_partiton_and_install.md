---
title: "How to partiton and install"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by mugs on 2008-03-18
hi, my daughter just got a new laptop, an Acer 4720z.  It came with vista, and it has a c and a d partition as well as a restore partitiion.

I want to know the best way to install Ubuntu and leave vista on there.  QTPARTED shows:

dev/sda1
dev/sda-1
dev/sda2
dev/sda3

sda1 and sda-1 seem to be the restore partiton.  Actually, I just want to leave that intact incase I ever need to restore it

Can I combine sda2 and sda3 and use them for Ubuntu?  When I go to install it only gives me the option to install on the whole disk, or manually.

It is a 160 gb drive.

Please let me know the best way.  Thanks.

---

### Post by housam on 2008-03-18
you need at least 2 partitions for ubuntu - one as a root ( / ) ext3 format and the other one is for the swap ( 1 -to 2 GB is ok ) . you can create them manually using Gparted tool ( on the live CD ) . you can delete one of your partitions let say hda 2 and reformat it as extended partition which can be devided to many logical partitions ( you need only two of them ) . then during the installation process assign the root ( / ) partition manually.

---

