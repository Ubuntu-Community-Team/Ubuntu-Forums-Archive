---
title: "Dual boot XP and Feisty grub help"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by itsmeagain on 2007-04-27
Hello
I have Windows XP and Feisty installed as a dual booting machine.  Feisty by default is the OS set to boot.  How can I change grub so that Windows XP  is the default OS to boot without user intervention?

---

### Post by garlik42 on 2007-04-27
there is a file /boot/grub/menu.lst you will have to edit.
It has a line
```
default 0
```
You need to change this to the selection # that is your windows xp.
You can find the selection number by pressing escape during the boot sequence and seeing which entry is xp.
The #'s start from 0, so if you see:
Linux blah blah
Other Linux Blah BLah
Other Other Linux Blah BLah 
Windows XP

Then XP being the 4th entry, would be "default 3"

---

