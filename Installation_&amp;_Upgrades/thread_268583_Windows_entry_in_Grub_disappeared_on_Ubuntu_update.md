---
title: "Windows entry in Grub disappeared on Ubuntu update"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by bhalper on 2006-09-30
I just ran the updater which installed two new versions of the kernal (.26 and .27).  It also updated the Grub boot list and overwrote the Windows XP entry.

That's a bit of a problem since this laptop is my main work system and we need Windows for various internal programs.  

Can someone tell me where the list is stored and what the entry looks like?

Much thanks.

---

### Post by bhalper on 2006-09-30
NM...

Found it in the on-line documentation.  Should have looked there before posting! :>)

---

### Post by Herman on 2006-09-30
Beware of following dodgy advice about where to add your Windows entry in your menu.lst file if you do not want this to happen repeatedly. 

Some people who want to make Windows the 'default' operating system do so by cutting the Windows entry from the bottom of menu.lst and pasting it above the Ubuntu boot entries, so that it is entry number 0, which will be booted by default.
Although this seems like an easy way to accomplish their goal, unfortunately, the happiness is shortlived as this places Windows at the top of the automagic kernels list. The entry is placed by the installer below the  automaigic kernels list for good reason. The automagic kernels list is not safe for a boot entry other than the one belonging to the operating system it belongs to.
Intead, it is better either to edit your menu.lst file by changing the line for 'defualt' from '0' to read 'saved' or a number corresponding with the Windows entry, perhaps '4' for example.
Click 'GO' for more detailed information, Changing the default (operating system booted by the timer)..................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")
Regards, Herman :D

---

