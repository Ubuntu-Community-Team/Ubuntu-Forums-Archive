---
title: "Ubuntu ubuntu-8.04.1-server-i386 install fails on HP ProLiant DL380 G3"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by sgreszcz on 2008-08-06
I keep trying to install Ubuntu Hardy Server 8.04.1 (alternative) CD - text based on an ProLiant DL380 G3.

After the partitioner does its thing and formats the drives, the installer fails with various problems.

Does anyone have any tips on how to get a successful install?  I've installed various versions of Ubuntu on laptops and servers, with no problems.

---

### Post by Partyboi2 on 2008-08-06
>  After the partitioner does its thing and formats the drives, the installer fails with various problems.What are the various problems?

---

### Post by Frankincell on 2008-08-30
I tried several times to install 8.04.1 server onto a compaq dl380g2 with a 5i controller with no success.
During the part of the install labeled...
  "[!!] Load installer components from CD"
I recieved the errors...
  "There was a problem reading data from the CD-ROM..."
  "Failed to copy file from CD-ROM."
or it would simply hang while copying the following files:
  binutils-static-udeb or libc6-udeb
I tested the media, replaced the cd-rom drive and tried a dozen other things, including reading half the internet ;)
  CentOS 4 would install so I  figured Ubuntu should.
  I downloaded 8.10 Alpha 4 from
[http://cdimage.ubuntu.com/releases/intrepid/alpha-4/](http://cdimage.ubuntu.com/releases/intrepid/alpha-4/)
and it installed easily.

---

