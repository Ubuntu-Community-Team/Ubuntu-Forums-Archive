---
title: "Partition Problem where is my memory :D"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by mnml on 2007-10-17
I have a strange problem, more than 10gigs missing ?
cf:screen

---

### Post by logos34 on 2007-10-17
/home (size: 42.9 GB) mounting at /media/sda2? 

That's all I can figure out.  Looks like you have a 60 GB hard disk (which the OS sees as ~56 GB).  If you want a dedicated /home you need to mount it on a [separate partition ]("http://www.psychocats.net/ubuntu/separatehome")rather than as a directory within / (root).

---

