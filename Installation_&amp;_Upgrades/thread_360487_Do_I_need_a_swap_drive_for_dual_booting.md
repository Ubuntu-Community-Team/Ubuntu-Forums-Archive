---
title: "Do I need a swap drive for dual booting"
date: 2007-02-13
forum: Installation &amp; Upgrades
---

### Post by truck87bp on 2007-02-13
I have a 400 gig hd with XP on the front end.  4 partitions/100 gigs each.  
Do I still need a small swap partition?  Do I have to change 2 partitions for this?  Or Is the requirement for a swap drive only required when no dual booting..Ubuntu only?

---

### Post by mikewhatever on 2007-02-13
Hi,
I sense, you're mixing up two different concepts. A swap partition, is a partition, that an Operating System uses when there is not enough RAM. It is similar to the page file in Windows. If you have 1GB or more of RAM you do not really need a swap partition, unless doing some heavy graphics editing. If not sure, make the swap partition to be the size of RAM.
The other concept is FAT32 partition, which many users find useful when dual booting, because both Windows and Linux can read and write to it out of the box. This is an easy way to use the same files from both Windows and Ubuntu operating systems. For example, Open Office documents. Ubuntu can also write to NTFS file system (Windows) with additional drivers installed.
To install Ubuntu on your PC, you may need to delete one of the four partitions, and create extended ones. That's because of the four primary partitions rule, assuming of cause, all the existing partitions are primary.

---

### Post by Kateikyoushi on 2007-02-13
Swap partition is always recommended regardless of dual booting, you need at least a swap and a / partition for your machine. Swap can be as small as half a GB.
You do not need to change 2 partition for that resizing the last one should be enough, of course it depeds whether those are all primary partitions or extended.

---

### Post by truck87bp on 2007-02-13
Thanx everyone...gonna play it safe and have a swap...with a ?????? see below

60   gig  XP NTFS
275 gig  Fat 32
60   gig  EXT3
2+  gig  Swap

Then a 200 gig secondary with (2) 100 gig Fat 32 Partitions

Q: Will Ubuntu see the Second drive without problems if I use Gparted for the initial setup?

---

### Post by mikewhatever on 2007-02-13
That setup should work. 2GB for swap is usually more then enough, so you definitely do not need more, and if that's the size of RAM you have, it is pretty safe to make it half that size.
Your second hard drive will need to be mounted, in order for Ubuntu to see it. The mount point should be something like this: /media/sdbX if that's SATA drive, or /media/hdbX if that's PATA/IDE drive. 'X' stands for partition number on that drive. I think Ubuntu installer should mount it automatically though.
Good Luck, and post back after you're done.

---

### Post by Pollywoggy on 2007-02-13
> **truck87bp said:**
> I have a 400 gig hd with XP on the front end.  4 partitions/100 gigs each.  
Do I still need a small swap partition?  Do I have to change 2 partitions for this?  Or Is the requirement for a swap drive only required when no dual booting..Ubuntu only?

The fact that you also have XP installed on a separate partition does not change the fact that a swap partition for Linux is a good idea.  I believe the rule of thumb is that the swap partition be twice the amount of physical RAM.  That's how I do it.

---

