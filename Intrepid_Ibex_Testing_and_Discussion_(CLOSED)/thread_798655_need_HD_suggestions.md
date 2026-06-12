---
title: "need HD suggestions"
date: 2008-05-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ronacc on 2008-05-18
I know this is not specificly Intrepid related but I figgure that the people here will probably be able most to help with this . My data drive ( 500 gb sata 1 partition ext3 ) started giving problems . fsck gives this message .

ron@ron-desktopA:~$ sudo e2fsck  -f -p -v /dev/sdd1
[sudo] password for ron: 
e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sdd1
ron@ron-desktopA:~$ 

there is only a few gigs on that drive as yet any ideas how to procede ?

---

### Post by Gina on 2008-05-18
You could run [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") to try and fix the drive (or rather the data on the drive).  I have it as part of the [SystemRescueCD]("http://www.sysresccd.org/Main_Page").

---

### Post by ronacc on 2008-05-18
Thanks I've got a copy of system rescue disk , I'll give that a shot .

---

### Post by Gina on 2008-05-18
Good luck :)

---

