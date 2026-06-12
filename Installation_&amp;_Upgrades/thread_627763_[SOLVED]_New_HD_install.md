---
title: "[SOLVED] New HD install"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by rsh on 2007-11-30
I was given a hand-me-down computer from an old friend.  It had no hard drive so I picked up a 120GB ATA/100 and installed it.  Jumper is set to cable select and it is on master 0.  DVD is installed as well, on secondary bus.  BIOS recognizes the following:

MOBO: PC Chips M811 V3.1
Primary Master: MAXTOR 120GB (just installed)
Secondary Master: TOSHIBA DVD/CD
AMD Duron 1800Mhz / 256GB RAM

Boot sequence set to Floppy --> HDD-0 --> CD

I insert a CD (Gutsy, Gentoo, DSL, etc.. tried them all) and this is where the fun starts.  It boots to CD, but then promptly restarts before anything happens.  I don't catch any errors, just black screen and BIOS starts up again.  This goes on as long as there is power to the box.

Any ideas?

---

### Post by Pumalite on 2007-11-30
You can install:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Use Gparted Live CD to prepare your drive. A good scheme is:
10 GB for '/'
1 GB for /swap
The rest for /home.
Go manual and use the prepared partitions.

---

### Post by rsh on 2007-11-30
UPDATE:

After letting it cycle through about 15 cycles it finally went to Gentoo's boot prompt.  I hit <enter> for default and it went back and did the same thing again.  I am going to install a new DVD drive in case that is the problem.  I have no way to verify the condition of the HW because it was a gift/curse.  Thanks for the help.

---

### Post by rsh on 2007-11-30
UPDATE/SOLVED:

Bad DVD drive.  Sorry for not checking that first.  Thanks for your help.

---

### Post by Pumalite on 2007-11-30
You are welcome. Good luck.

---

