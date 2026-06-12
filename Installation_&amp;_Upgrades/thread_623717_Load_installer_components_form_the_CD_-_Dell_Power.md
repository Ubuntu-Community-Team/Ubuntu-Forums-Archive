---
title: "Load installer components form the CD - Dell Power Edge 860"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by jamesjohn on 2007-11-26
I have a dell power edge 860 server on which i am trying to install open xchange express edition which runs on ubuntu 6.06. After a few screens of installation when it tries to load the hardware, I get the message " Load installer components form the CD. There was a problem reading data frm the CD ROM". I really need this to work. How do u think I can get around this.

---

### Post by aashay on 2007-11-26
try making an iso of the cdrom and mounting it. Are there scratches on the cd?

---

### Post by jamesjohn on 2007-11-26
The orginal file which I downloaded was an ISO image which I made iinto a CD. The CD is prefectly clean and I even tried with CDs burned at a lower speed. Its still the same.

---

### Post by aashay on 2007-11-26
Assuming the iso is healthy (try the checksum), mount the iso using this:
```
mount myiso.iso /media/cdrom/ -t iso9660 -o ro,loop=/dev/loop0
```
See if results vary

---

