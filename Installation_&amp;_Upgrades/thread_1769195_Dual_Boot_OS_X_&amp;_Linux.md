---
title: "Dual Boot OS X &amp; Linux"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by skynetz on 2011-05-27
What is the best way to install Linux alongside OS X?  My first attempt failed.

This is what I tried.

Created a new partition using bootcamp.
Restart and boot from live cd.
deleted the partition and created two partitons "/" and "swap" Advanced > NO BOOT Loader.  installed.
Reboot hold Option key
Only the OSX partition appears nothing else.


I keep running into rEFIt.  Is that something I should try? or Did I do something wrong with bootcamp?

thanks

---

### Post by zvacet on 2011-05-30
Only thing I can think of is to try reinstall grub following [this]("https://help.ubuntu.com/community/Grub2#SIMPLEST - Copy GRUB 2 Files from the LiveCD") instructions.I don't know how will grub act with OSX and will it recognize,but that ia another story.Maybe you will get faster help if you ask on [Apple users]("http://ubuntuforums.org/forumdisplay.php?f=328") subforum.

---

