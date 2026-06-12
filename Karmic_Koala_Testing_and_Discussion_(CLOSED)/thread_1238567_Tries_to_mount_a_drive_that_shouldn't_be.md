---
title: "Tries to mount a drive that shouldn't be"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2009-08-12
I'm running 2.6.31-5 64 bit (formatted ext4) with two SATA drives which have other versions of Ubuntu (formatted ext3). I'm using a shared swap disk with all versions. When I boot up the PC asks for authentication to mount one of the other drives that has a different version of Ubuntu. I found an entry for this drive in /etc/mtab, but not in /etc/fstab. If I remove the drive entry in mtab on next boot the PC asks to authenticate a different drive :confused::confused::confused:
Both mtab and fstab do not have entries for any of the other Ubuntu (version) drives. Karmic is only on sdb8 and swap is on sda8.
Any advice ?

---

### Post by fjosh on 2009-08-12
I was under the impression it is a known bug.  Not positive though because I haven't searched launchpad nor seen a link.

---

### Post by plun on 2009-08-12
> **fjosh said:**
> I was under the impression it is a known bug.  Not positive though because I haven't searched launchpad nor seen a link.

Yup and also a "known issue" for Alpha 3 and now Alpha 4

> If you have internal hard disk partitions aside from Ubuntu itself, GNOME will attempt to automatically mount them at startup and ask for your password. Just cancel the dialog, unless you actually want to work with them. (396448 ) 

[http://www.ubuntu.com/testing/karmic/alpha3](http://www.ubuntu.com/testing/karmic/alpha3)
 

This is the bug:
[https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/396448](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/396448)

--

---

### Post by Kevbert on 2009-08-13
Thanks plun. I've subscribed to the bug.

---

### Post by sonicb00m on 2009-08-13
I also get this problem too. It's nothing major...just an annoyance.

---

