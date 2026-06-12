---
title: "wont boot"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by Pord on 2007-09-12
I keep getting a problem with my laptop...
I just formatted the disk and the install thinks it sda (its infact hda according to bios and knoppix) which means that when I restart after the install its says its an invalid boot sector disk.

How can I get it to work?
Its strage that the install thinks it sda when its a p-ata drive. Is there a fix to this?

I can get it to boot using the ultimate boot cd I have but dont know how to fix it so I dont need this cd everytime.

There are only 3 partitions according to fdisk:
/dev/sda1 40gig ext3 mounted as /
/dev/sda2 39gig ext3 mounted as /home
/dev/sda3 the swap partition

---

### Post by Pumalite on 2007-09-12
7.04 labels drives: sda, sdb, sdc, etc

---

### Post by Pord on 2007-09-13
how can I stop the invalid boot sector then when it starts up?? It says press H to rety hard disk but still doesnt work and like i said i have to used the cd to boot into an live os

The exact wording is:

Hard disk boot sector invalid
Press 'H' to retry Hard Disk, any other key for floppy

---

### Post by Pord on 2007-09-13
When I boot into the OS using the "ultimate boot cd" and then use fdisk -l it shows:

/dev/sda1 
/dev/sda2
/dev/sda3

I then went into gparted and it only shows:


/dev/sda1

and this is shown as the full disk and not as the partitions I had set-up and am using. This means I cannot change the boot flags aswell.

---

### Post by Pumalite on 2007-09-13
If Gparted does no see them; the partitions have not been set correctly. Why don't you you make one large partition of your hard drive with Gparted, formatted ext3 and then install>Guided>Use Entire Disk

---

### Post by Pord on 2007-09-13
Got it working in the end..... The bootflag wasnt on the 1st drive so had to put that on there using qtparted i think it was and it boots fine now :D

---

