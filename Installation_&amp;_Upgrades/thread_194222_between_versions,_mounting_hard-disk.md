---
title: "between versions, mounting hard-disk"
date: 2006-06-11
forum: Installation &amp; Upgrades
---

### Post by erikringmar on 2006-06-11
Dear all, somehow or another I seem to be between Kubuntu versions.  I tried installing Dapper but something went wrong and Breezy is only partially operational.  Stupidly I didn't make a backup!!!  I'm trying to rescue the situation by using the Dapper Desktop live-CD but I can't get access to the old Breezer installation on the hard-disk that way.  I know I need to mount it somehow, but how should I do that?  The old hard-disk is identified as hdc1.  If I only get hard-disk access, the backup should be a breeze.

Dapper looks great, btw!

Erik

---

### Post by glotz on 2006-06-11
system > admin > dísks > select the right disk and partition > mount

---

### Post by catlett on 2006-06-11
This is from the live cd and assuming the partititon is hdc1.
First make a place to mount it.```
 sudo mkdir /media/breezy
``` Now to mount it. This assumes it is ext3 and on hdc1. ```
sudo mount /dev/hdc1 -t ext3 /media/breezy
``` If it is ext3 and on hdc1 then there should be an icon on the desktop labeled breezy with hdc1 mounted.

---

### Post by erikringmar on 2006-06-11
Thanks, but it doesn't seem the Desktop CD has the system> admin> menus.  What to do?

Btw, if I install Dapper will my own files -- OpenOffice, Gimp, etc -- be overwritten or will Dapper only replace Breezy?

sorry for being such a novice,

Erik

---

### Post by erikringmar on 2006-06-11
Catlett!

That's amazing.  It works.  You've saved me after hours of teeth-gnashing and hair-pulling.  You are a good citizen of the Linux world.

all the best,

Erik

---

