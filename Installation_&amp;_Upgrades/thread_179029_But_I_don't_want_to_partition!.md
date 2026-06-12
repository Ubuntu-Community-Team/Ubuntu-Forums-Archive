---
title: "But I don't want to partition!"
date: 2006-05-18
forum: Installation &amp; Upgrades
---

### Post by halfthelaw on 2006-05-18
I'm at the point in the install process where it asks the user to partition the disk. However, I already have my disks partitioned nicely and don't want to tamper with them. Unfortunately the only option to move is "write changes"... so how do I move to the next step without having to re-partition?

---

### Post by kokiri on 2006-05-18
choose advanced partitioning, through here you can declare what mount points you want which partitions during the setup. That way you won't have to repartition, just format.

---

### Post by halfthelaw on 2006-05-18
So "Finish partitioning and write changes to disk" doesn't necessarily reformat those partitions?

---

### Post by Nano Geek on 2006-05-18
[QUOTE=halfthelaw]So "Finish partitioning and write changes to disk" doesn't necessarily reformat those partitions?[/QUOTE]Nope

---

### Post by halfthelaw on 2006-05-18
[QUOTE=asjdfwejqrfjcvm msz34rq33]Nope[/QUOTE]

Thanks.
However, now that I got to actually use that option, it just dumps me back into the same advanced partitioning screen (with two exclamation marks in the title). I tried to get around this by going to the main install menu and choosing to install the base system, but it keeps dumping back into the partition screen. Why??

---

### Post by Sef on 2006-05-19
What you will have to do is this.

Go into a manual install > Highlight Ubuntu's root partition > press enter > delete the root partition > you should be in the main manual partition section > Highlight the deleted space that you just created > press enter > you can recreate the partition now > Just do the defaults > when you are done > click finished > back at the main manual partition > click write > it will reinstall your root partion > the others should be left alone.

**Back up** your files first. This is not 100% guaranteed.

---

