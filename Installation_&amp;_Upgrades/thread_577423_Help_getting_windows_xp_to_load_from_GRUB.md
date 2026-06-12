---
title: "Help: getting windows xp to load from GRUB"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by beg4mercy on 2007-10-16
Hello, first off I'm new and want too say that your all awsome for helping us newbies out on these tedious problems.

I'm tired and want to go to bed so I'll post up whats happened tonight and hopefully I may have recieved help by tomorrow.

Partitioned my 114GB HD into like 
(  30GB -ubuntu 7.04-  )  (   80GB -windows XP-  )

I installed Ubuntu first then Windows, got GRUB going again but has no bootable windows XP option. 

I tried loading from the XP disc but when I choose the recovery option I get asked for an administrators password which I don't recall ever dealing with so how could I possibly know it?

So I revert to the GRUB> command line after hitting 'C', try typing in 

root (hd0,0)

grub>

then I try

root (hd1,0)

grub>

...all I get is a short wait then I get a new GRUB> command line, the computer does **** all, doesn't say nothing.

So thats the story, I can give you more specs tomorrow, but thats where im at, i've got all this new software for windows and im keen as to get it going iff only i could boot the damn thing..

THANKYOU to anybody who listened too this and DOUBLE THANKS if you can help out.

---

### Post by Stormboy on 2007-10-16
This link may help.

[http://ubuntuforums.org/showthread.php?t=576788&highlight=reloading+grub](http://ubuntuforums.org/showthread.php?t=576788&highlight=reloading+grub)

---

### Post by logos34 on 2007-10-16
add windows boot entry to ubuntu menu.lst:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty/BootMenu#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty/BootMenu#How_to_add_Windows_entry_into_GRUB_menu)

---

