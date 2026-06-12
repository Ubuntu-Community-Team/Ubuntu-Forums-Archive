---
title: "GRUB2 USB command return empty list"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by blaz_boy on 2013-05-29
i have a brand new HP ProBook 4540s, installed windows8 then ubuntu 13.04
so GRUB2 is installed to my HDD successfully 
each of the OSs loads correctly.

now i'm trying a small experiment the goal is make grub boot the OS after finding a usb stick with
a certain serial number.

checked GRUB2 command list and found "USB" which should list all USB devices i have.
so i started my Laptop, pressed "C" to enter GRUB command line, executed "usb"
while having a USB Flash stick connected but the command always return empty list
like it cannot find any USB devices,

note the i tried the following and the result is the same :
- tried all USB ports 
- tried "insmod usb", "insmod usbtest"

any ideas to reach this goal ?

---

