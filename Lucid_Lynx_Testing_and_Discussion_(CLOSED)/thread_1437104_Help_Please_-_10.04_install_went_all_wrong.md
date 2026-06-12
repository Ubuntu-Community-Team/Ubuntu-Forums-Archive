---
title: "Help Please - 10.04 install went all wrong"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Duncan J Murray on 2010-03-23
Dear All,

I thought I would install 10.04 to try it out and submit any bugs.

I downloaded the beta ISO, and tried running it from the CD - had no problems with it.

I installed it by making a new 7GB partition, and assigning '/' to that, and then using the swap I already had, and made the 9.10 partition smaller.

Now when I boot it comes up with:

GNU GRUB version 1.98-1ubuntu1

minimal bash-like line editing is supported. For the first word, TAB lists possible command completion,  Anywhere else TAB lists possible device or file completions.

grub> _


I have tried typing 'boot', but this says error: no kernel loaded.


Any ideas much appreciated!

Duncan.

---

### Post by Duncan J Murray on 2010-03-24
Think I've figured it out.

This page:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Suggested typing in:

'ls' which gives you the partitions
'linux /vmlinuz root=/dev/sdXY ro'  where sdXY = sda3 on my system (see ls sda 3 is sd0,3)
'initrd /initrd.img'
'boot'

Unfortunately it's hit and miss to figure out which drive, and you have to do this on each reboot.  However, if you get it work and boot ubuntu, then go to terminal and type 'sudo update-grub'.  This then gives you back the menu.

Hope this helps anyone else with this problem.

---

