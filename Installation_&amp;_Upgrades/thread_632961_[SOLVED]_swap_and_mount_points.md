---
title: "[SOLVED] swap and mount points"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by vsiege on 2007-12-06
I am going to reinstall U server....

I was told by one person that i need to have my ram + .1 of swap and another half the amount of RAM - which is it?

I have 4 gigs of RAM

Second thing....
where should I mount my second HD so that all user can read and write... currently its in media/ but i was also told /mnt. Is there any advantage to either - or is there a better place?

---

### Post by Pumalite on 2007-12-06
/swap is 2x Ram up to 1 GB. /media is the perfect place to mount your drive.

---

### Post by vsiege on 2007-12-06
Thanx.
Should both drives set to be : Primary

ok so here are my settings im going ot use... tell me what you think

1st drive gets 1 gb of swap
Settings (i am ging to store win. and os X files on this machine):
use as: ext 3 journeling file system
mount points: /    **2nd drive:** /media/someFolderNameRight
Mount Options: defaults (I have no idea what this does)
Label: None (is this where you put a name for the drive itself?)
reserved blocks: 5% (I have no idea what this does)
typical usage: standard (I have no idea what this does)
bootable flag: off (i think this is used for RAID, otherwise i have no idea)

if I want all users to have a common place to store their files such as a spot on drrive A and drive B, is installation the place to set this up?

---

### Post by Pumalite on 2007-12-06
[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10)

---

### Post by vsiege on 2007-12-06
thanx.... ill my experience be much different since im using 7.10?

---

### Post by Pumalite on 2007-12-06
I doubt it. A server is a server.

---

### Post by vsiege on 2007-12-06
Thanks again. See you around.

---

### Post by Pumalite on 2007-12-06
Good luck.

---

