---
title: "Dual Boot problem?"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Dikzak_Dolf on 2007-04-14
Hi,

I first installed Ubuntu on one partition of my hd and, later I installed Windows XP on another partition of my hd.
Now, my computer can't find the Ubuntu partition anymore.

Can someone give me an easy method how to fix this? (I've read several tutorials about this problem, but I don't understand them at all).

Greets,

Dolf

---

### Post by bulldog on 2007-04-14
Yes,
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

Some advice.
Install windows on the first primary partition of your hdd.
Ubuntu doesn't care on which partition it is installed,GRUB will find it :D

EDIT:
Some useful command to find out how your disk is partitioned.
```
sudo fdisk -l
``` will show you.
If windows isn't on the first primary,correct it first,because it's likely you will get trouble to boot your windows install!

---

### Post by Dikzak_Dolf on 2007-04-14
Hej Bulldog,

thank you very much for your clear explanation. I can boot again from Ubuntu.

Greets,

Dolf

---

