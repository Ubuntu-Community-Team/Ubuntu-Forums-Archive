---
title: "Help"
date: 2015-09-26
forum: Installation &amp; Upgrades
---

### Post by Mikeyy233 on 2015-09-26
About too install ubuntu on my C: drive will it erase other drives because i have a second hard drive

---

### Post by suprleg on 2015-09-26
So to be clear, are you asking if the new install will erase current partitions on your C: drive or erase information on other physical HDD's within your system?

---

### Post by Bashing-om on 2015-09-26
Mikeyy233; Hello. Welcome to the forum.

> **Mikeyy233 said:**
> About too install ubuntu on my C: drive will it erase other drives because i have a second hard drive

Let's also be clear about terminology. In Windows " on my C: drive " would translate in linux as a single partition on a single physical hard disk.
In our world - now-days with SATA as the preeminent interface - hard drives have the nomenclature
sda is the 1st hard drive
sdb is the second hard drive
sdc is the third hard drive.
On these hard drives the individual partitions are named with a number
sda1 is the 1st partition on the 1st hard drive
sda4 is the 4th partition on the 1st hard drive
sdb3 is the 3rd partition on the 2nd hard drive
sdc8 is the 8th partition on the 3rd had drive
and so on.

When you refer in Windows speak of :C drive we have to ask is there but one physical hard drive installed ?
Then next we want to "see" the partitioning on the hard drive(s).
This is best done from a liveDVD(USB) showing the output of terminal commands:
```

sudo fdisk -lu ## for the legacy partitioning scheme
sudo gdisk -l ## GPT partitioning 
sudo gdisk -l /dev/sda
sudo parted -l ## A look at the partitioning from a different angle

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

When we know what we are working with; We can better address your questions and concerns ( rightly to be concerned).

[INDENT][INDENT]we all want to be on the same page
[INDENT][INDENT][INDENT]same same point of reference
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mikeyy233 on 2015-09-26
C: Sorry for late reply

---

### Post by Mikeyy233 on 2015-09-26
2 is installed one 500gb 2 1tb. well i cant access the second one cause its NTFS. so i dont know. if my games are on there.

---

### Post by Bashing-om on 2015-09-26
Mikeyy233' Well;

ubuntu can access and read/write to Windows' NTFS file system. Post the requested outputs so we can see what is on the hard drives.

[INDENT][INDENT]we can better then advise
[/INDENT][/INDENT]

---

