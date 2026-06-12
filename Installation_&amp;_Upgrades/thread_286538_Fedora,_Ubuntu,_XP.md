---
title: "Fedora, Ubuntu, XP"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by paul85 on 2006-10-27
I've installed ubuntu on my FC5 system and have added separate drive for XP.   There is no problem accessing ubuntu or XP, however I can't get to FC5 at all.

menu.lst

title Ubuntu, kernel 2.6.15-27-386
root (hd1,2)
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/sdb3 ro quiet splash
initrd /boot/initrd.img-2.6.15-27-386
savedefault
boot

title Fedora Core (2.6.17-1.2187_FC5) (on /dev/sda2)
root (hd0,0)
kernel /vmlinuz-2.6.17-1.2187_FC5 ro root=LABEL=/ rhgb quiet
initrd /initrd-2.6.17-1.2187_FC5.img
savedefault
boot

title Windows XP
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1

device map:
(hd0) /dev/sda
(hd1) /dev/sdb
(hd2) /dev/hda


When I boot the first time I get GRUB_ and it just sits there. If I reboot all is fine is this a GRUB or fstab problem.  Have no problem getting to Dapper or XP from menu.list

---

