---
title: "Big red error when installing Ubuntu (No installable kernel found)"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by fresh27 on 2005-05-29
Ok, my brother screwed up our family's desktop with all sorts of spyware and viruses, so I formatted whole thing and started from scratch.

I have 2 physical HDDs, and now I'm trying to set up Windows XP and Ubuntu as a dual boot.

I have 5 partitions now.
[list][*]Disk 1, Partition 1 - Windows XP (NTFS)
[*]Disk 1, Partition 2 - Linux (EXT3)
[*]Disk 2, Partition 1 - Windows Programs (NTFS)
[*]Disk 2, Partition 3 - Linux Swap
[*]Disk 2, Partition 2 - Shared Media (FAT32)[/list]
I installed Windows and that went great (I set up all these partitions after I installed Windows using Partition Magic.) Now I'm installing Ubuntu, and I ran into a strange error. I got past the partitioning part (manually mounting / and /media) and got about 65% through the install. Then the screen goes red and I get this:
> **[!!] Install the base system**
*No installable kernel found*
No installable kernel was found in the defined APT sources.

The current default kernel package in 'kernel-image'.

You may try to continue though this rather strange error is probably fatal.

<Go Back> <Continue>

This is the second install CD I tried and I got the exact same problem. They are both both official ShipIt CDs.

Help is appreciated :D

---

### Post by jobezone on 2005-05-29
[QUOTE=fresh27]Ok, my brother screwed up our family's desktop with all sorts of spyware and viruses, so I formatted whole thing and started from scratch.

I have 2 physical HDDs, and now I'm trying to set up Windows XP and Ubuntu as a dual boot.

I have 5 partitions now.
[list][*]Disk 1, Partition 1 - Windows XP (NTFS)
[*]Disk 1, Partition 2 - Linux (EXT3)
[*]Disk 2, Partition 1 - Windows Programs (NTFS)
[*]Disk 2, Partition 3 - Linux Swap
[*]Disk 2, Partition 2 - Shared Media (FAT32)[/list]
I installed Windows and that went great (I set up all these partitions after I installed Windows using Partition Magic.) Now I'm installing Ubuntu, and I ran into a strange error. I got past the partitioning part (manually mounting / and /media) and got about 65% through the install. Then the screen goes red and I get this:


This is the second install CD I tried and I got the exact same problem. They are both both official ShipIt CDs.

Help is appreciated :D[/QUOTE]
 That's strange, have you tried choosing continue, and see if you get a bootable system? At any point, does the install ask you to download packages from the net? It may be that you're having conectivity problems, and so it would be safer not to download packages from the net during your installation. But I'm guessing...

Good luck!

---

### Post by fuit_ilium on 2005-08-12
This was a bug under Warty Warthog too, it seems. Somebody suggested that the CD-ROM drive stopped spinning after awhile during the unpacking/config process, and suggested changing your hardware setup to HD-master CD-slave on the same channel. I tried this and it didn't work. However, I tried a weird workaround: open up your box and take out the CDROM. At a point during the install pretty soon before you've been hanging, unplug the power from the CDROM and then plug it back in. Maybe even eject the CD and reinsert it. It's like voodoo, but it worked for me, and got me past the "no installable kernel" redscreen.

PS I was using an old box:

HP Pavilion 6535 w/ HP CD-Writer Plus
Celeron 466
Samsung 8.5 GB HD
64 mb RAM

HD-master, CD-slave on same channel.

---

### Post by anacron on 2005-08-12
I got that same error with one old computer (400Mhz), I just replaced the cd-drive with another one(actually it was an dvd-drive what I used) and it worked after that. so that unplugging cd-drive power might work too.

---

