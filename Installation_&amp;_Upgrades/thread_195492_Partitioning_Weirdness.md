---
title: "Partitioning Weirdness"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by Imexius on 2006-06-12
Alright recently I made a mistake and somehow god my entire drive deleted. So I quickly decided to perform a complete reinstallation of both windows (Just for Guildwars Factions :P) and of course ubuntu (kubuntu in this case).

So heres how I set up my partions

windows: 15GB
Ubuntu / : 20GB
Ubuntu /home : 123.2GB
Ubuntu swap : 1GB

Now I have succesfully got it to work albeit there is a .47MG free space that I cant seem to use up.

What happened was QTparted kept creating a 5mb buffer between each partition without me telling it too, so I had to use fdisk to prepare the partitions. 

Anyways to my question: is this just a buggy GUI installater or is my harddrive messed up?

---

### Post by user1397 on 2006-06-12
i'm not really sure, but have you tried any other partitioner? maybe gparted? (it has a live cd, and it's the one being used in the dapper desktop cd.)

btw, y make your / partition so large?  i would recommend just 15 GB or so, 20 GB just seems too much!!

---

### Post by Imexius on 2006-06-13
15GB would be the minimum that I devote to /. Considering that just after an install I have already used up 3GB and I still have to install all my games... which should take up quite a bit.

---

