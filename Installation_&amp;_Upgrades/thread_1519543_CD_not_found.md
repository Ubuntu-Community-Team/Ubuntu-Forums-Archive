---
title: "CD not found"
date: 2010-06-28
forum: Installation &amp; Upgrades
---

### Post by wsteffen on 2010-06-28
I am trying to upgrade to Xubuntu 10.04 from a Slakware install. I downloaded the ISO image, burned that to a CD, and then created a floppy with SBM.bin image. The system is an old i386 which has a BIOS that will not boot from CD. I can mount and read the CD under the currently installed Slackware system with no problem. When I boot from the floppy I get a menu that shows the hard drive and the floppy as boot options, but not the CD. The CD drive is an ide on the same controller as the hard drive with the hard drive being master and the CD drive being slave.
Any hints, suggestions, information or links?

Thanks

---

### Post by kalistona on 2010-06-28
I think you make a little confusion, an upgrade is only 'check the box'.
If your machine do not accept cd, it is normal that you cannot.
It must accept usb/key, i suppose even the one, or two (10 is ready for usb3).
If you are agree, you could downloaded an iso and with (see pendrive-linux) an usb/key; install your 10 without problem (click install on the picture : install ubuntu -desktop ). 
From a slackware ? very strange, i cannot help you to this way and from this method.
sorry.
From a floppy (you mean cd i suppose) to mount and make the boot you have two ways :
flag with gparted or from terminal (see ubuntu.org - command lines are clearly explained
without errors or doubts).
if your are in dual-boot (several partitions), you need to follow the tutorial.

---

### Post by wsteffen on 2010-06-28
Perhaps upgrade was not the best wording for what I am doing. In
my original post, I stated this is an OLDER PC (386), and it can
not boot from CD and has no USB ports. That is where the floppy comes into play. It is a two stage process: booting the SBM from the floppy which is then smart enough to boot the CD (if it can find it). In my case the CD is not found.

Wsteffen

---

