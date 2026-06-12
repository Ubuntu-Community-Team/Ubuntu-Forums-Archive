---
title: "dual boot ubuntu, XP, Mac OSx on a PC"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by thespicychicken on 2010-01-16
I am trying to set up a computer with Ubuntu 9.10, Windows XP and Mac OSx on a PC.. I am haveing trouble understanding how to get Mac OSx on a PC.. do I haft to downgrade my bios or install a pack? so from now you can tell that I'm not sure what I'm doing... once I do get this all working I would like the computer to automatically boot up on XP, not Ubuntu. i have the disks for Windows XP, Ubuntu and maybe Mac OSx, the file type is a .dmg, not compatible on my vista..

[COLOR=Navy]the PC this is going on:
300GB HDD
4MB RAM
single possessor
single graphics card
old PC "was Windows 98"[/COLOR]

idk much more...

If anyone could give some steps on how to get all these to work including the Mac OSx then I would be very happy... -.- :|


- TheSpicyChicken

---

### Post by jocko on 2010-01-16
> **thespicychicken said:**
> If anyone could give some steps on how to get all these to work including the Mac OSx then I would be very happy... -.- :|
Mac OS X will not install on a PC. There are ways to hack OS X so that it will install on a PC, but:
1. It's illegal and against the apple licence.
2. It's probably not working on just any PC.
3. The rules on these forums does not allow posts with instructions on how to do it, as it would be illegal activity.

For a windows/ubuntu dual boot, there are plenty of instructions available, but to make it short:
1. Install windows. Leave some unpartitioned space on your hard drive.
2. Install ubuntu. Let it create an ext3 or ext4 partition plus a swap partition.
3. There is no 3.

---

### Post by thespicychicken on 2010-01-16
> **jocko said:**
> Mac OS X will not install on a PC. There are ways to hack OS X so that it will install on a PC, but:
1. It's illegal and against the apple licence.
2. It's probably not working on just any PC.
3. The rules on these forums does not allow posts with instructions on how to do it, as it would be illegal activity.

For a windows/ubuntu dual boot, there are plenty of instructions available, but to make it short:
1. Install windows. Leave some unpartitioned space on your hard drive.
2. Install ubuntu. Let it create an ext3 or ext4 partition plus a swap partition.
3. There is no 3.
ohh, I was not aware that it was illegal. ;) But thanks for letting me know. Ok the rest sounds quite simple but what are the ext3, ext4 and swap partition for? Is it a backup?

---

### Post by Mr Nemo on 2010-01-16
Ext4 is the filing system Ubuntu uses (like how windows uses NTFS now) and swap space is comparable to memory management such as paging. Ext3 is the older form of the extended filing system. Karmic uses Ext4, I think every other Ubuntu release uses Ext3.

---

