---
title: "Not finding Hard Drive during Install?"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by snowman2795 on 2012-04-20
Just got this oldish IBM Think-Pad Centrino M 1gig of RAM memory. And a new (Used) wiped clean 40 gig hard-drive 

Been playing with Ubuntu on the CD. I really love it.

Now I want to use Ubuntu as the only operating system.  There is no OS on the HD. During the Install, everything is fine. Except, there is an 'X' on the line that says 'Ensure you have 4.4 mgs of space'.  

What do I have to do now?

Format the drive first?  If so how do I do that?

Or is there an operation within Ubuntu I am missing?

---

### Post by darkod on 2012-04-21
From the cd in live mode, open Gparted.

If the hdd doesn't have a partition table (totally wiped out), just go into Device - Create Partition Table.

That will create msdos partition table by default. You do not have to create any partition in advance. You can if you want to, but then during the install you need to use the manual method and tell it to use the existing partitions (it will not do it by default).

Start the installer and see if the hdd is discovered now.

You can also check in BIOS if the hdd is discovered correctly, because with the cd it would run even without a hdd. Maybe the computer does not see it as present at all.

---

