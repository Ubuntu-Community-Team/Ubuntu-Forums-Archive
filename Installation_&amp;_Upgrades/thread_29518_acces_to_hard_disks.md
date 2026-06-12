---
title: "acces to hard disks"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by trst on 2005-04-24
Hi. I just installed ubuntu ww 4.10 and i have 3 hard disks on. How do i acces to my hard disks. I see those drives in /dev but there are too many partitions and small "x"   
in the upper-right corner of short-cut and i cannot acces them. What should i do??

I dont know does this help, but i tell my assembly.
PentiumII 233mhz
128mb of ram
4.3 gb ide hard disk (hda, ext3)
8.6gb ide hard disk (hdb, ext3)
4.3 gb ide hard disk (hdc, ext3)
elsa tnt 2 graphic card

Sorry for my bad english.

edit.

---

### Post by nigel on 2005-04-24
are these disks formatted?

if they are windows formatted the info [here](http://ubuntuguide.org/4.10/index.html#windows) should help if you want the hard drives mounted when the system boots then just read further down that page

---

### Post by trst on 2005-04-25
all of them are ext3

---

### Post by nigel on 2005-04-25
Well in that case I don't know how to help

at a guess
what do the entries for these drives in your * /etc/fstab* file say, or better still post them here

should be near the bottom of the file

possibly this could be a problem with access, by this I mean they may be set up for root access only

Thats my best guess, until someone more knowledgeable comes along

---

