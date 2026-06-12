---
title: "Gparted will not work on live cd"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by bojangles2800 on 2007-08-29
Hi,
     I am a newbie and I want to try Ubuntu 7.04. I downloaded the
live cd and set my machine to boot from cd. After it starts installing
to my hdd it gets as far as partition and it only gives me one option.
Manual partition. I loaded it on my old athlon comp and it gave me
the guided partition option where it partitions automatically. So I
go back to starting point and select system-administration-Gparted
and it says it recognizes no devices. I have xp-pro loaded already
and don't want to lose it. Any help would be appreciated.:):)

---

### Post by be4truth on 2007-08-29
Can you be a bit more specific about your machine?

---

### Post by ddrichardson on 2007-08-29
You will need to do a couple of things:

1. Backup Windows XP
2. Use the manual option to resize your Windows partition, leaving enough space for Ubuntu and a swap artition - about 8-10Gb would be OK.
3. Create an ext2 or 3 partition and choose / as the mount point in the empty space
4. Create a Linux Swap partition equal to twice your memory.

Have a look at some of the excellent dual booting guides - including the one on the documentation on the live cd for more information.

---

### Post by bojangles2800 on 2007-08-29
My machine:

Intel E6320 cpu
Gigabyte G33m-ds2r
corsair DDR2 800
Hdd   seagate sata2   80 gig
video   ATi Diamond Stealth X550
windows xp-pro sp2
Swiftech watercooling
soundblaster Audigy
Lg  dvd-rw
nec floppy
enermax case 4 80mm fans

---

### Post by ddrichardson on 2007-08-29
I think be4truth is more concerned with how your hard disk is laid out - is Windows currently using the entire disk?

---

### Post by bojangles2800 on 2007-08-29
All i have loaded is xp-pro and I ran defrag before trying to load
Ubuntu. I am using 14 gigabytes of the hdd

---

### Post by be4truth on 2007-08-31
Your XP installation has only C; or D: and other letters? Can you go into the admin tools in Windows and post a screen shot of your HD?

---

