---
title: "help with grub menu not showing up"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by railz68 on 2006-07-24
hey all, I gave a friend at work a Dapper cd, and pointed him to a guide on installing and dual booting ubuntu and WinXP.

He has it working, somewhat. If he "reboots" from either O/S, everything is fine, grub boot loader shows up with a countdown. He can boot ubuntu and WinXP.

But, if he "shuts down" the pc, when he powers back on, the grub menu is not showing up. He tells me he just has a black screen listing the partitions on the drive.

Only way he can get the grub menu back, is to put the ubuntu cd in the drive and reboot. When install starts, he cancels it, and then gets the grub menu back.

any ideas whats wrong ?.

thanks for any help on this.

---

### Post by richbarna on 2006-07-24
He needs to change the time from 0 to something like 3 seconds in the menu.lst

First :-
> gksudo gedit /boot/grub/menu.lst 
Then change this :-

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        [COLOR=Red]3[/COLOR]


---

