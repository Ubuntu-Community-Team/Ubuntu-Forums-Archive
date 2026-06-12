---
title: "Pendrive tutorial ruined my flash drive"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by singleflow on 2007-11-05
I have a serious problem. I tried to follow the tutorial to install gutsy gibbon on my pendrive. When I tried to boot to it, it failed, no big woop. I decided to just reformat and resume using my flash drive as a storage device. I was surprised, however, to find that my 2GB flash drive was now a 199MB drive.

Don't laugh, but I reformatted anyway, hoping in vein that this might fix the problem. I'm at my wits end and I don't have another linux machine to fix this with (the P3 finally died). Is there anything I can do to fix this?!

---

### Post by wieman01 on 2007-11-05
Have you tried formatting it via Windows? It might do a better job.

---

### Post by Nano Geek on 2007-11-05
Did you use GParted to repartition it?

---

### Post by Nano Geek on 2007-11-05
> **wieman01 said:**
> Have you tried formatting it via Windows? It might do a better job.You know you aren't allowed to say that here. :)

---

### Post by drratchet on 2007-11-05
Sounds like a big drive with a small partition. Have you tried repartitioning the drive? Perhaps deleting all the existings partitions on the pendrive and creating one new one would do it.

---

### Post by wieman01 on 2007-11-05
> **asjdfwejqrfjcvm msz34rq33 said:**
> You know you aren't allowed to say that here. :)
And I really, really hate saying it but sometimes, occassionally, rarely Windows does a better job there. 	:-#

---

### Post by singleflow on 2007-11-06
Actually when I tried to reformat it I was in Windows. Unfortunately I'm not proficient enough in Linux to do a lot of the re-partitioning stuff. I'm hoping that I can boot to a live CD and maybe fix the problem there. I'm really good at finding the unknown fix out there, but I was surprised to find that no one else (that I could find anyway) has the same problem.

I should also clarify my position since I feel the title of the thread may be misleading. The pendrive tutorial didn't ruin my flash drive, my inability to follow directions did. :lolflag:

---

### Post by snickers295 on 2007-11-06
one day my pendrive did that then i looked at it in gparted and it said it was full so i deleted the partition in gparted and formated at then it wen't back to normal.

---

### Post by az on 2007-11-06
> **singleflow said:**
> Actually when I tried to reformat it I was in Windows. Unfortunately I'm not proficient enough in Linux to do a lot of the re-partitioning stuff. I'm hoping that I can boot to a live CD and maybe fix the problem there. I'm really good at finding the unknown fix out there, but I was surprised to find that no one else (that I could find anyway) has the same problem.

I should also clarify my position since I feel the title of the thread may be misleading. The pendrive tutorial didn't ruin my flash drive, my inability to follow directions did. :lolflag:

A quick and easy way is to boot a live cd, plug in the drive and run 

sudo cfdisk /dev/whatever

where "whatever" is the pen drive device name.  Erase all partitions that cfdisk is showing you and then write the partition table to disk.  Remove and reinstert the drive again and you should be able to create a partition and format it with gparted.

---

