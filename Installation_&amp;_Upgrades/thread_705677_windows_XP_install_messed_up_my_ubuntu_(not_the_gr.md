---
title: "windows XP install messed up my ubuntu (not the grub problem)"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by bendt.v.rasmussen on 2008-02-23
In an attack of sheer idiocy, I decided to install windows to my computer...

I have a sataII drive which holds(held?) my ubuntu install. I installed an ide drive to hold my new windows XP.

So I boot up the windows XP install cd, but when I get to the harddrive recognition part, the win install recognises the sata drive as drive C in one big unknown partition and the ide drive as drive d.

I repartition the d drive and ask the win install to install windows there, but this I am denied.

Then I unplug the sata drive and install windows on to the ide drive, which is now recognized as drive C.

At the end of my install, I reinstall the sata drive and reboot my computer, in hope of seeing my beloved Ubuntu start screen.

I get a screen looking like this:
_________________________________________________________________________

_  <- blinking cursor










________________________________________________________________________

Then I think its the good old grub-reinstall problem, so I boot up my ubuntu livecd, but this informs med, that /dev/sda1 is one partition.
mount refuses to mount this partition.
Grub refuses to recognice /dev/sata og (hd0,0). Also find /boot/grub/stage1 in the grub prompt returns nothing.

I unplug the IDE drive and reboot - still nothing...

I install ext2 support for windows and try to find the drive in file explorer - but this only returns, that the drive (now recognized as E:) is not formatted.

HELP ME!!!

I think my first encounter with the win install cd is where things messed up, but how do I get back my precious ubuntu drive(whith all my data - months work - no backup :-( )

---

### Post by bendt.v.rasmussen on 2008-02-24
All ok.

Fixed with gpart:

gpart -w /dev/sda /dev/sda

Then the grub reinstall.

---

