---
title: "Setup doesn't detect my hard drive!"
date: 2007-04-10
forum: Installation &amp; Upgrades
---

### Post by afmanuk on 2007-04-10
Hi all, I have a bit of a problem!
I recently got a new laptop with Vista Home Basic installed and I tried installing Ubuntu Edgy but the setup won't detect my hard drive at the Partition part. I've tried gPartition (I think that's what it's called) It just says "No devices detected" and now I'm completely stuck. Any help would be immense :)
Thanks

---

### Post by taurus on 2007-04-10
Open a terminal and see what's the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by afmanuk on 2007-04-10
It doesn't say anything. Just get another "ubuntu@ubuntu:-$" line.

---

### Post by taurus on 2007-04-10
What's the spec of your laptop then?

---

### Post by afmanuk on 2007-04-10
Dell Inspiron 1501
AMD Turion 64 x2 Moile Technoloy TL50
Gig of RAM
256Mb VRAM
120Gb Hard drive

---

### Post by taurus on 2007-04-10
Is that a PATA, SATA, or even RAID harddrive?

---

### Post by afmanuk on 2007-04-10
I'm not too sure. I would of thought it was SATA.
Is there anyway I can find out for sure?

---

### Post by dan171717 on 2007-04-10
does anything appear in the computer menu on the live cd?? try a newer vertion of ubuntu???:biggrin:

---

### Post by afmanuk on 2007-04-10
Just the CD-RW/DVD-R drive and
FileSystem
And last time I checked. Edgy is the latest.

---

