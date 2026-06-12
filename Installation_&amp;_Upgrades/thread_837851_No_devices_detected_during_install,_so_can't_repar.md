---
title: "No devices detected during install, so can't repartition (or install for that matter)"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by Pajot10 on 2008-06-22
I'm attempting to install Ubuntu for the first time, and so I get to step 4 where you're supposed to manage your partitions and there is nothing there.

I've tried a few times now, modified a few things in BIOS, and nothing ever shows up, it's just an empty table.

When I exit the install and Ubuntu runs, if I go to gparted I get the same problem: it apparently can't find any devices.

Here's my system:
E8400
Abit IP35 Pro
4GB RAM
8800GS
Seagate 320GB SATA

I only have that one Seagate drive, and it currently has 2 partitions: one for XP, and another for all my software and media.

I really have no clue why it wouldn't be able to detect the drive and the partitions.

Any ideas?  I suppose I could use other software to repartition the drive, but would that even matter if my hard drive isn't even being detected?

---

### Post by Pajot10 on 2008-06-23
A little more info...

I downloaded the CD installer (8.04) and verified with a checksum, burned it at 4X and verified the integrity of the disc, so there's nothing wrong with the CD.

Would getting the alternate desktop CD help?

I know looking through the documentation I was never given an option to choose manual or guided or anything like that... it just came to step 4 where it's supposed to show your partitions and since nothing shows up I can't do anything.

---

### Post by Pajot10 on 2008-06-27
Anyone?

---

### Post by Pumalite on 2008-06-27
Is your system 64 bit?

---

### Post by Pajot10 on 2008-06-27
My XP is 32-bit, my processor is 64-bit, and I'm using the 64-bit Ubuntu media

---

### Post by Pumalite on 2008-06-27
Burn a new CD. Clean the lens in your burner.

---

### Post by Pumalite on 2008-06-27
If it doesn't work; try editing the boot line and adding all_generic_ide at the end.

---

