---
title: "Installed Ubuntu on HDD but will only boot when USB inserted"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by nirpius on 2010-07-19
I installed ubuntu on my HDD alongside windows vista. Currently my partitions are as followed

vista loader - vista - linux swap - ubuntu - home
ntfs - ntfs - linux swap - ext4 - ext4


if the usb is not in, it loads vista, if the usb is in, it loads grub



the boot order for my laptop is


usb
hdd0 toshiba blah blah blah
hdd1
hdd2
network boot
usb cdrom


(I only have one hdd btw)



This is on an Acer Travelmate TM8371-944G25n



I thought maybe I could run gparted off an USB installation and delete the swap linux and home partitions, grow vista until it is at the end of the disk, then shirnk it down at the end of the disk, grow the vista loader so it is up to the nw end then shrink it down then reinstall ubuntu at the start of the disk. I just didn't want to do all this if it probably won't work as it will take about 12 hours to run it.


Any suggestions?

---

### Post by byStanderone on 2010-07-19
...it seems that your grub is in the usb, you'd have to reinstall grub on the partition wherein vista is intalled.

---

### Post by C.S.Cameron on 2010-07-19
Yes, reinstall grub from the Live CD.

---

### Post by nirpius on 2010-07-19
Thanks guys, it seems so simple now. I'll try that.

---

### Post by nirpius on 2010-07-19
It turns out that grub is in fact installed on my ubuntu partition, not my usb. I am going to leave gparted running through the night to see if that helps.

---

