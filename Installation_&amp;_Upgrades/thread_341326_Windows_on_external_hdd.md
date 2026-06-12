---
title: "Windows on external hdd?"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by Harin on 2007-01-18
Would it be possible for me to install windows onto an external hard drive and make an entry in grub/menu.lst telling it:

title Microsoft Windows XP
root (sda,1)
savedefault
makeactive
chainloader +1

I'm completely new to grub and ubuntu, I just need to use windows when I'm at home for some programs which are incompatible with ubuntu as of yet, so installation of windows on an external hard drive would be perfect for me, but I need to do it under ubuntu since I don't want to lose my files. Thanks.

---

### Post by logos34 on 2007-01-18
Make sure your BIOS can boot from USB drive or 'Other' device.

Grub sees all drives as 'hd_' (doesn't distinguish between pata, usb, sata)...So your root line would be 
> root (hd1,0)

assuming windows gets installed on /dev/sda1.

You may have to add 'rootnoverify' and/or 'map' lines to menu.lst (to fool windows into thinking its on the first boot drive):

> title Microsoft Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

OR
> title Microsoft Windows XP
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

your /boot/grub/device.map should look like this:

(hd0) /dev/hda    [your internal drive; or 'sda' if sata]
(hd1) /dev/sda    [your usb; or 'sdb' if internal is 'sda']

---

