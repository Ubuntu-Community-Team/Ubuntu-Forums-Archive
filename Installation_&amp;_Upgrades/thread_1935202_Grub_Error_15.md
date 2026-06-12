---
title: "Grub Error 15"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by salgala2000 on 2012-03-03
Hello Ubuntu Forums,

I'm having trouble installing Ubuntu server on my old Dell Dimension 3000 desktop (Intel Pentium 4 processor: 2.80 GHz). At the moment, it has no operating system installed. The only OS i can use right now is the Slitaz/OPHcrack Live CD. Luckily, it has GParted (and other useful things) installed. When I try to boot from a Ubuntu CD it tells me Grub Error 15 or Grub Error 22. When i try to install Slitaz onto the hard drive and i reboot i get Grub Error 15. This is because I installed Slitaz successfully and then deleted the partition with GParted. All I want to do is install Ubuntu Server. Right now I have /dev/hda1 which is 10GB, and the rest (65GB) of my hard drive is empty. Can anyone help? :)

TL;DR: Old Desktop. Broken Grub. Only Slitaz Live CD Loads, else: Grub Error 15 or 22. Goal: Ubuntu Server.

---

### Post by darkod on 2012-03-03
The broken grub on the hdd has nothing to do with booting CDs.
Make sure your ubuntu server cd is good, try to boot on another computer for example. Then boot it on this computer and install how you want, you can create/delete partitions during the install, etc.

---

### Post by maxijuni0r on 2012-03-03
I have a similar problem trying to boot from an USB ...GRUB missing and still haven't got any help... or found any solutions

---

### Post by salgala2000 on 2012-03-03
darkod was right. I can't believe I made such a dumb mistake, but thank you! I was burning the .iso file to the CD on a mac (I assumed that burning a disk on a mac or a pc would result in the same thing, but apparently not). I burnt the .iso to the CD on a windows machine and everything worked well.

maxijuni0r, I'd recommend getting a CD and doing it that way (if the USB won't work for you). You can get a pack of 5 CD-RW for around $5 :D

---

### Post by darkod on 2012-03-04
It would be the same problem with the usb stick. Did you simply extract the ISO on it? You need to create a boot sector, just copying (or extracting) files won't work. To boot from it it needs a boot sector.

It's best to create it on another ubuntu machine using Start up disc creator, or if you have only windows you can use universal usb installer, unetbootin, etc.

---

