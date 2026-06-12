---
title: "need help making vista/xp/ubuntu behave"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by Meow27 on 2010-03-23
here is my drive map

primary
XP (20gb, ntfs) DATA (150gb ntfs) Ext4 (20 gb) Swap (2gb) 

slave (currently disconnected!)
Vista OEM (40gb?) Data (the rest.... doesn't really matter)


i need to use the empty space within my offline (pun intended) harddisk, but i hear, that Vista starts messing around, or doesn't work properly, or whatever with the system as a whole.....


if there is a problem with reconnecting my second harddisk? i prefer for my second drive to remain the slave.

---

### Post by oldfred on 2010-03-24
I do not have Vista but I do not think it will cause any major issues. If you are going to resize the Vista partition, use Vista's tools to resize it. Are you making another NTFS data partition or an EXT3 or 4 partition for data?

---

### Post by Meow27 on 2010-03-24
no im simply planning to have Vista available in grub, and use its existing Data partition as another spot to store data

(ntfs so i can browse on both windows and linux)

---

### Post by andrewthomas on 2010-03-24
You should be fine.  Just update grub after you plug the Vista drive back in.

---

### Post by Meow27 on 2010-03-31
ok ive got the two harddisks connected at once.


im on a ubuntu 9.04 liveUSB

i need to install grub. however i have just realized that i have absolutely no linux partitions on my primary harddisk.

my linux os, along with the no longer used MBR is on my Slave disk.

would installing grub in the slave disk, make it work?

i need a little help here

here is my drive map

#1

Dell utility patyition (50MB primary) Recovery partition (10 primary) (Vista) (primary) [extended= swap(1), NTFS(2)]

#2

XP (primary) ext4 (primary) [logical= swap, NTFS]

---

### Post by oldfred on 2010-03-31
Grub or windows boot loaders have to be in the primary master. BIOS starts booting and jumps to the MBR of the primary master to continue booting.
Older PATA drives set primary master with jumpers or location on the cable for cable select. New SATA drives usually have a BIOS that lets you set primary master or boot drive separate or in addition to boot device, Hard drive, floppy, CD etc.
You can install grub to the slave but unless it is the boot drive it will not boot. I would install it to the slave drive and make it primary.

---

