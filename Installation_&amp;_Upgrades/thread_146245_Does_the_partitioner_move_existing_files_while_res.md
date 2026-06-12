---
title: "Does the partitioner move existing files while resizing?"
date: 2006-03-17
forum: Installation &amp; Upgrades
---

### Post by facugaich on 2006-03-17
I have one big FAT32 partition in my Primary IDE. What I want to do is shrink it aprox. 7GB.

Now, I would like to know if Ubuntu's buillt-in partitioner moves files while shrinking a partition. That's because I have some files pretty near the end of the actual partition and I can't move them closer to the beginning no matter how many Defragmentors/Optimizers I try.

So, will the files in the last 7GB of the partition be erased OR moved (to another place in the partition?

---

### Post by teasum on 2006-03-17
Don't know if this helps, but when I installed Ubuntu (I'm new to this), I used the GParted (Gnome Partition Editor) live CD to change my Windows partition and create my Linux ones first.  You can get it here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).

I thing GParted is also available from several other Live CD versions of Linux, but in any case, I felt more comfortable adjusting my partitions with a graphical interface.  That, and it resized my XP partition with no problem.

Good luck!

---

### Post by JoshHendo on 2006-03-18
I don't know, though I don't think it does.

A good thing to do would be to backup all your important files and do it that way.

---

### Post by mcduck on 2006-03-18
Have you tried running defrag in safe mode?

---

