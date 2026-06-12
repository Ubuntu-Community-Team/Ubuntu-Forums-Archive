---
title: "grub: filesystem type unknown after installing Ubuntu"
date: 2005-04-29
forum: Installation &amp; Upgrades
---

### Post by antonio on 2005-04-29
I am a new user and in my innocence I thought that I could keep some data with my old operating system (Window$ 2000) while using Ubuntu for the rest. 

The problem is, after installation, which was quite succesfull, I can't boot from the old NT partition anymore. If I select its option in the menu, what I get on the screen is:

GNU GRUB 0.95 (639K lower / 261056 upper mem)

    Booting 'Windows NT/2000/XP'

root (hd0,0)
     filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1

And the computer halts.  :-x I would really appreciate any online help, and I am ready to pay if someone living in the San Sebastian area (Basque Country, Spain) could fix this for me.

---

### Post by antonio on 2005-04-29
Well, I've been doing my homework and after reading recent posts to this excellent forum, I'm going to try two strategies to fix my problem:

1. get into the BIOS, set disk type to LBA
2. boot with the Window$ 2k Install CD, launch the recovery console and type "fixmbr"

And see what happens. I'm still not quite sure of what I'm doing, but will keep you posted about results!

---

### Post by antonio on 2005-05-01
:)  :)  :)  It was quite simple: I change the disk type in the BIOS and pronto! Dual boot with no worries. My thanks to all the folks who contributed to this issue in the past. This is a great community.

---

### Post by Bartholomaeus on 2005-05-10
[QUOTE=antonio]:)  :)  :)  It was quite simple: I change the disk type in the BIOS and pronto! Dual boot with no worries. My thanks to all the folks who contributed to this issue in the past. This is a great community.[/QUOTE]

Your right and I´m very happy that my windows is working again. Thanks.

---

### Post by mindcry on 2008-02-13
i have the same problem, except windows are installed in another disk (not in the same with ubuntu)
linux disk is hd0 and windows disk hd1

i get the same error message but i cannot change the disk type in bios (or i do not know how to do this)

in the menu.lst the windows part looks like this:

title		Microsoft Windows XP Home Edition
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


(what is map?? if i remove these lines it does not boot and it returns to grub)


Also the "windows" disk is partitioned, the first partition is the one with the OS the second is for storing files and i also have a small partition that was used to work around with linux before i bought the other drive.
Any ideas?

---

