---
title: "Grub Triple OS"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by paragonconcept on 2010-01-17
Howdy Guys,
I think ive gotten myself into a bit of a situation. Ive got 3 operating systems across 2 hard drives, and i need to get them loading properly. 

I have my primary ubuntu 8.10 install @

/dev/sda1

I have a new Windows XP install @

/dev/sdb2

and i have a new install of Ubuntu 9.10 @ 

/dev/sdb3

I'd like to be able to selectively boot into all 3 until i can return my current 8.10 install. Can someone show me how to get my /boot/grub/menu.lst file in order?

---

### Post by kansasnoob on 2010-01-17
What can you boot right now?

I should add that 9.10 uses grub2 which no longer has a menu.lst.

---

### Post by paragonconcept on 2010-01-17
actually turns out /dev/sda1 is a 9.10 install but its all borked from the upgrade from 8.10, that is my current primary OS.

---

### Post by perspectoff on 2010-01-18
I like the solution at Ubuntuguide.org:

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

A boot partition is created that contains a copy of Grub.

The Master Boot Record points to the copy of Grub in the small boot partition, which presents the boot menu.

The menu merely chainloads the bootloader that is stored in the partition of whichever operating system is chosen (be it Windows, Mac, Ubuntu, or other Linux).

It makes each OS truly independent of each other in regards to bootloading.

See the site for details.

---

### Post by ssican on 2010-01-18
Your case is like this thread:

Grub2 Dual boot issues
[http://ubuntuforums.org/showthread.php?t=1379735](http://ubuntuforums.org/showthread.php?t=1379735)

EDIT 1
The first solution, is to change the BOOT Device in the BIOS.

EDIT 2
The 2nd solution would be FIX MBR of the Windows XP, **IF** Windows XP not start when in the BIOS the Hard Disk of the Windows XP is the First Boot Device.

---

