---
title: "Grub on multiple hard disks and partitions"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Tekno_Cowboy on 2007-10-21
I have the problem of having grub on an unknown number of hard disks, due to some drive swapping I did. Are there any files I can check for to delete to get rid of it? What would be the best way to get rid of all traces of grub anywhere on my system and reinstall grub from super grub disk?
Any help would be very welcome!

---

### Post by confused57 on 2007-10-21
This is probably the best guide on grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

As long as you have grub on the main boot drive's mbr, it doesn't hurt anything to have grub on any of your other hard drives' mbr.

---

### Post by Tekno_Cowboy on 2007-10-23
Thanks, I'll probably use that guide. I found the corrupt menu.lst file that was pointing to the wrong files, and now it seems to work. It was sure on a strange drive though.

---

