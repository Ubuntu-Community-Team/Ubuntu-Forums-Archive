---
title: "Completely erase hard drive"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by PharmaPhunk on 2008-08-11
Ok so I have Ubuntu 6.10, and Windows XP running on a 50gb hard drive, using Grub 1.5 as a boot loader. Now, I want to clear everything off my hard drive (I've exported my important files elsewhere) and install the newest version of Ubuntu (8.04, from cd). Now, is there any simple command for this? Something that will just wipe off everything and let me start fresh?

---

### Post by logos34 on 2008-08-11
yes, start up the Hardy installation and choose partitioning option 'guided--use entire disk'.  It will overwrite everything on the hard drive.

If you want to do a secure wipe try [dban]("http://www.dban.org/")

---

### Post by Bucky Ball on 2008-08-11
Download the appropriate flavour of Ubuntu iso (torrent is fastest), make cd and boot from that. When you get to the partitioner, delete all partitions. Then start from scratch or even let the partitioner do it for you. There are a number of options if you have no other OS dual booting.

Good idea to get a piece of paper and plan what partitions you are going to make and how big. Don't forget the swap (2x your RAM generally).

:)

* Update: Like logos34 said ... again. ;)

---

### Post by PharmaPhunk on 2008-08-11
ah excellent thanks for the help

---

### Post by PharmaPhunk on 2008-08-11
erm, I'm having more trouble with this then I thought. It seems I can't do the simple task of booting from the CD. I change the driver priority in my BIOS, but the grub loader still comes up. I'm quite sure I burned the iso correctly (using nero7, click and drag, easy enough). Any reason why this is?  Does Grub load automatically at start-up, regardless of boot priority? I'm pretty sure it doesn't, or at least shouldn't. Ideally I'd like to wipe the hard drive clean using the installation CD, if not then I'll use the previously mentioned tool dban.

---

### Post by logos34 on 2008-08-11
If the cdrom is first in the Bios device boot order it should be starting the hardy install disc.  

Try[ burning it in nautlius]("https://help.ubuntu.com/community/BurningIsoHowto#In%20Ubuntu")

---

### Post by Bucky Ball on 2008-08-11
With logos34. The grub won't auto-boot through any bios settings. Check in the BIOS again. :)

---

