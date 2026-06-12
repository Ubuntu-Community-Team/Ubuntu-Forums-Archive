---
title: "Computer Date/Time change - Ubuntu 9.10 Live ISO"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by singhk on 2010-04-06
I am using Grub4Dos to boot Ubuntu 9.10 Desktop Live CD. In the menu.lst  i made the following changes.

> title Ubuntu LiveCD 9.10
find --set-root  /ubuntu-9.10-desktop-i386.iso
map /ubuntu-9.10-desktop-i386.iso  (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper  iso-scan/filename=/ubuntu-9.10-desktop-i386.iso quiet splash --
initrd  /casper/initrd.lz
bootThe code runs  fine and Ubuntu loads also from the ISO stored in the C: drive of my  system.

The problem is when Ubuntu loads it changes my clock  time. I have set the timezone to Indian Standard Time. Since it is live  CD it should not make any changes in the system however, it does change  the Data/Time of my system. Please help me address this issue.

---

### Post by singhk on 2010-04-27
The LiveCD 9.10 changes the system clock. Is this issue resolved in the upcoming Ubuntu 10 version??

---

