---
title: "How to install Ubuntu with no cdrom"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by scarab-one on 2010-04-04
Is there a way to install the last Ubuntu without using cdrom and usb? I have got an old laptop where I have installed Ubuntu from Windows XP (50% Win XP and 50% Ubuntu). But now I would like to install Ubuntu only, have no use for Win XP any longer. My laptop got a broken cdrom (unable to use) and no bootable usb. Is it possible to just install Ubuntu on this laptop?

Regards, Sigurd

---

### Post by halj32 on 2010-04-04
you can make a new partition on your HDD (must be first partition) format it with "fat"
then you can use a program like unetbootin to extract a cd image to that partition
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

& boot from it

goodluck

edit
you can also use it as a live boot

---

### Post by C.S.Cameron on 2010-04-04
If I understand correctly you now have two 50% partitions with XP on one and Ubuntu on the other?
Is it an option to pry out your hard drive and hook it up to another so that you can use gparted to delete the windows partition and expand the Ubuntu one?
Another method similar to the above is to download the latest iso and use UNetbootin:
Type: Hard Disk, Drive: C:\
This should put a "virtual" Live CD on your hard disk that can be used to install from.
See Unetbootin documentation for more info.

---

### Post by Sef on 2010-04-04
> Is there a way to install the last Ubuntu without using cdrom and usb? I  have got an old laptop where I have installed Ubuntu from Windows XP  (50% Win XP and 50% Ubuntu). But now I would like to install Ubuntu  only, have no use for Win XP any longer. My laptop got a broken cdrom  (unable to use) and no bootable usb. Is it possible to just install  Ubuntu on this laptop?

Yes, read [Community Ubuntu Documentation: Installation]("https://help.ubuntu.com/community/Installation").

---

