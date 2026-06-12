---
title: "CanoScan 9000F driver"
date: 2010-08-05
forum: Installation &amp; Upgrades
---

### Post by RodBoudreaux on 2010-08-05
Reciently bought a canoscan 900f only to find that Ubunto does not have a driver for it. Anybody have a driver or info that might make it work.

rod

---

### Post by davidmohammed on 2010-08-05
unless canon themselves support your scanner (which they dont) - I'm afraid you'll have to wait for the opensource community to catch up.  Your's is a very new scanner - you may have to wait for the [Sane]("http://www.sane-project.org/sane-backends.html") project to provide a driver.  At the moment, it doesnt look like that it has been resolved in the development git.

... then again, you could download the code, and have a go fixing the code yourself.  At a guess, your starting point should be the 8800F driver since that is the nearest equivalent scanner!

Easier - return your scanner for a refund and buy a linux compatible scanner.

---

### Post by Jack Jebedee on 2010-08-31
You're looking for VUESCAN, the first-rate scanning program for Windows, Mac and Linux.  The Linux program was compiled using Ubuntu. Get it here: [http://www.hamrick.com/](http://www.hamrick.com/)

JJ

---

### Post by RodBoudreaux on 2010-09-28
I am working with xsane people to develop a driver. 9600 not perfect yet but close. 

VUESCAN does not have a CanoScan 9000F driver for linux But thanks for replying.

Anyone know what technique Cannon uses for 9600 let me know.

---

### Post by Timokl on 2011-04-22
I'm facing the same situation. However, there is one working driver for this scanner with SANE, but it's not included into the CVS, yet. Should be available for the next version.

See [this discussion thread]("http://forums.debian.net/viewtopic.php?f=7&t=54246").

---

