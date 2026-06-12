---
title: "Grub Trouble"
date: 2008-07-24
forum: Installation &amp; Upgrades
---

### Post by Krixo99 on 2008-07-24
Hey guys,

*insert random im not good with linux line here*
*sorry for any typos which i garuntee exist*

I recently upgraded to hardy heron(usb install) from linuxmint(usb install).
I installed hardy to USB following this guide
[http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/) to a T.

I recieve Grub Error 17 Cannont Mount Partition.
My bios is setup to boot from USB and everything was working fine on mint.

I have tried doing
grub> root (hd1)
grub> setup (hd1,0)
ect
correct me if this is wrong.

\dev\sda (hd0) is my internal HD(laptop).
\dev\sdb (hd1) is my USB thumb drive.

aswell as using Supergrub to repair/reinstall grub on my USB

the grub menu comes up to chose my OS but upon selecting a OS to boot the error 17 ensues when i pick any of the ubuntu options and with vista it says "stage 2..." then repeats .....'s for screens and screens(not really concerend with the vista aspect if i want to use vista ill take out the USB).

vista boots fine when the USB isn't in my computer.

ive have searched grub errors and grub 17 error and tried all that seem applicable as some do not pertain to USB installs.

UGH had some info like fdisk -l, devices.map, and menu.lst but it got fubared when i saved and reopened on windows if you need of of that info just ask

---

### Post by confused57 on 2008-07-24
In the grub boot menu, make sure the first Ubuntu entry is highlighted(selected), press "e", highlight the line with root, press "e" again, change root from (hd1,y) to (hd0,y), press "enter", then "b" to boot...y means leave whatever value it shows "as is".  This is temporary, if it works, but can be made permanent in your /boot/grub/menu.lst.

---

