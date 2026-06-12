---
title: "Gparted and Windows in logical O.o"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by vincenzoo on 2007-12-22
Hello you all.
Yesterday i tryed to install Ubuntu 7.10 on my acer aspire  1350.
i found no problem until i tryed to use windows.

The first problem was:
GRUB didn't see Windows. So i tryed to insert the commands line in /boot/grub/menu.lst.....
But there were a BIG PROBLEM. in my computer there were 5 partitions.
So, the question was: "where is windows? /dev/hda5"  
but.... "What is hda5?" 
I reboted again with Ubuntu Live, and i saw that Windows is installed in hda5, the **LOGICAL** partition oh hda1.


[take a look here: ]("http://img147.imageshack.us/img147/3498/screenshotps6.png")

before the ubuntu installation windows was in primary partition. it must return there!
How can i do?

---

