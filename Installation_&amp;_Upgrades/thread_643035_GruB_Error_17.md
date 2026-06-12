---
title: "GruB Error 17"
date: 2007-12-17
forum: Installation &amp; Upgrades
---

### Post by babaton on 2007-12-17
Hello,

I'm having a nightmare trying to dual boot xp and Ubuntu 7.04. I'm following the videocast method from the ubuntu site.

 - I have one drive with a fresh installation of XP.
 - I boot from the Ubuntu Live CD
 - I run through the install procedure and choose to resize the partition
 - Everything installs just fine, I'm left with 3 partitions, xp on ntfs,Ubuntu on Ext3 (Boot) and aswap partition for Ubuntu

However everytime I reboot I get Grub Error 17. I've searched around trying to find fixes for this but there seem to be a lot of diferent causes.I've tried editing the menu.lst file but no luck.

Someone please help.

Thanks, Baba

---

### Post by Jabcor on 2007-12-17
I'm having the same issue and have yet to work out what is wrong.  

Very few suggestions were posted in my thread so far:

[http://ubuntuforums.org/showthread.php?p=3966418](http://ubuntuforums.org/showthread.php?p=3966418)

I've got a link in there you may try.  It did not work for me, but you may be lucky! ;)

---

### Post by babaton on 2007-12-17
Thanks, I've tried those threads before. One thing I have noticed is that my drives are labelled as /dev/sda1 rather than /dev/hda1.

---

### Post by ajgreeny on 2007-12-17
Start up the live CD and show us the output of ```
sudo fdisk -l
``` in the terminal.  It should then be possible to tell you how to edit the menu.lst file to point to the correct partitions for each OS.

---

### Post by ericartman on 2007-12-17
Check out Super Grub, its helped me many times

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

BTW read the instructions, its a great learning tool

Cart

---

