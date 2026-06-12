---
title: "External Hard Drive LILO dual boot"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by Battlemarz on 2007-11-16
I am looking to install Ubuntu 7.10 on a small partition of my external 500G hard drive (USB).  My problem is most of the explanations on doing so are written with GRUB in mind.  I am not able to use GRUB because it causes my laptop's hard drive to not be recognized.

I will be dual booting with XP(SP2) and would like to know the most painless method of installing Gusty to a partition on my external hard drive.  I want to be able to boot my system into XP or Ubuntu while the hard drive is plugged in and have no issues booting XP with the hard drive disconnected. (<- Difficult part)

If someone could help me out with a step by step or with some instructions of what to do once Ubuntu is installed to my external hard drive partition i would be very grateful. :)

---

### Post by MrFSL on 2007-11-16
I found this:
[http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/](http://xubuntublog.wordpress.com/2007/06/17/ubuntu-feisty-on-your-usb-drive-finally/)

In this example the author seems to be using lilo so perhaps it will work for you.

---

### Post by Battlemarz on 2007-11-16
That information is all mostly about persistent installs on flash drives, pen drives, etc. I don't need  a persistent live CD. I want to have an actual install just need to know how to setup LILO to boot it well.

---

### Post by Battlemarz on 2007-11-17
Bumping. Still looking for the best way to boot to external using LILO :(.

---

### Post by Pumalite on 2007-11-17
Maybe this will help:
[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)

---

### Post by Battlemarz on 2007-11-17
I have looked over both of those, and they still use GRUB. I cannot use GRUB because it causes my dvd drive to be unseen. Must use LILO and i cannot find much in the way of LILO tutorials. Which is why i posted :).

---

