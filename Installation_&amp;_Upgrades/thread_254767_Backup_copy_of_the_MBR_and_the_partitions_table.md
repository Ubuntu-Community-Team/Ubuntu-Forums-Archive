---
title: "Backup copy of the MBR and the partitions table"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by Raf Rzedowski on 2006-09-10
Hello!

I want to transform one of my NTFS partitions into Linux partitions. 
First, I want to make a copy of the MBR and the partitions table to be able to recover my partitions.
I'm considering the command *dd if=/dev/hda of=~/Desktop/mbr.bak bs=512 count=1*.

Is it enough?

---

### Post by Original Brownster on 2006-09-10
Hi, in short, yes. 

here's a great article I found a while ago which you might find useful:

[Partition Table Under the microscope]("http://homepage.smc.edu/morgan_david/cs40/assignments/assgt4.htm")

---

