---
title: "Grub: filesystem type unknown, partition type 0x7"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by bethebunny on 2008-04-12
Okay, there's a huge amount of documentation about this problem, but after looking through a few pages of google and a half dozen other ubuntu forum threads about this, I can find no solution that works for my situation.

I have another computer that I'm giving to my parents to replace their old one. It has two drives, one with two Debian installs (one for using and one just for grub) and the other with an XP partition which works fine and an XP partition I just added, cloned from their old comp over an old vista partition.

It is this second XP partition which will not boot.

The current menu.list entry looks like this:

title="Windows XP"
root (hd1,3)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

This is identical to the one that boots my other XP (although obviously it calls a different partition).

When I try to boot, I see:
Booting Windows XP...
root (hd1,3)
Filesystem type unknown, partition type 0x7
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

_

And there it hangs. Switching to "rootnoverify" will stop the error message from occurring, but the boot hangs anyways.

A common solution was to change the drive to LBA in setup, however my setup only offers me the options of Auto and Off, and since the other XP partition boots just fine, this should not be the problem.

What must I do to boot this drive?

---

### Post by Herman on 2008-04-12
You need to use grub's hide and unhide commands if you want more than one Windows to boot on the same hard drive.

Like this, 
```
title  Windows XP number 1 install
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
hide (hd1,3)
unhide (hd1,0)
chainloader +1

title  Windows XP number 2 install
 root (hd1,3)
savedefault
 makeactive
 map (hd0) (hd1)
 map (hd1) (hd0)
hide (hd1,0)
 unhide (hd1,3)
 chainloader +1
```Where: (hd1,0) and (hd1,3) are the partition numbers your two Windows installations are installed in.

Can you please post a copy of 'sudo fdisk -lu' and 'sudo parted /dev/hdb p', (or sudo parted /dev/sdb p) if you still need help? (So we can see what we're trying to do). :)
```
sudo fdisk -lu
``````
sudo parted /dev/hdb/ p
```You might also need to edit boot.ini in Windows, and/or run CHKDSK /R too maybe.

---

