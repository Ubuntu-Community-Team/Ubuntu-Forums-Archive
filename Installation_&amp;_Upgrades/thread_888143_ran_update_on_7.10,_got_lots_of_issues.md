---
title: "ran update on 7.10, got lots of issues"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by khara on 2008-08-12
hi.  ok so i ran the update, and the most annoying of my problems is grub.  before i had it setup so grub had:

windows xp
ubuntu options:
ubuntu 7.10
ubuntu recovery mode
ubuntu memtest

after the update i now have:

ubuntu 7.10
ubuntu recovery mode
ubuntu 7.10
ubuntu recovery mode
ubuntu memtest

i go into ubuntu, all my video settings (which i fixed so i can run advanced desktop effects) are gone.  i try to open the file that has the grub load order, it says 

No application suitable for automatic installation is available for handling this kind of file.

i try to open it with gedit, it says 

gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

so then i tried what the results on google told me:

in terminal

grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found

so i tried ddoing this through the livecd.  it found it fine, so i did did setup (hd0,2)
and it supposedly ran flawlessly.  i restart, still with the same issue.

right now all i want is to get my windows partition back :P
thanks

---

### Post by Pumalite on 2008-08-12
Use Super Grub to fix your Windows MBR:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
In XP, with installation disk:
Hit 'r' for Recovery>FIXMBR>FIXBOOT

---

