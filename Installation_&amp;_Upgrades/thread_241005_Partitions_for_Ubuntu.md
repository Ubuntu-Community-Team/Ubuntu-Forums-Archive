---
title: "Partitions for Ubuntu"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by xjosie729 on 2006-08-21
Is it true that I have to create 2 partitions for Ubuntu, one is where I'd install it, and the other is for something, about twice the size of the RAM?

---

### Post by avtolle on 2006-08-21
What you are referring to is the swap partition, and yes, it needs to be there along with the "root" partition.  If you are experienced with installations and partitioning a HDD, go ahead and do them yourself; otherwise, I'd let the automatic partitioner do its thing. BTW, there is a debate over how large the swap partition needs to be; if you have 1gb or more of RAM, the thinking of many forum members is that 512mb for swap is sufficient.

---

### Post by xjosie729 on 2006-08-21
Also, I tried G-Parted in another computer. For some reason, the "New" button was disabled. How would I create a partition?

When I booted from the G-Parted live CD, I was asked for the screen depth. What *is* it?

Then later in the process, it said something like extra features couldn't be used? It had a choice of skipping them, so I did. Would that have anything to do with the "new" button?
[SIZE="1"]
Maybe this isn't the best place to ask.[/SIZE]

---

### Post by jupion on 2006-08-21
you know, i stated a problem on this board about a similar partitioning problem and i dont get any answers. i aint no noob, but my problem is with the hardware itself. the hd is new, and i got dapper to install before on my old one. but i tried other distros on my new hd, they worked. but with ubuntu, it wont let me create partitions at all. it formats but creating a partition is just not possible. DAMN IT! if your problem is fixed then let me know ok?









gosh!

---

### Post by xjosie729 on 2006-08-23
[quote="givré"][If you can, it's always better to prefer ext3 to share file between windows & linux](http://ubuntuforums.org/showthread.php?t=217009&highlight=NTFS)[/quote]So, can Ubuntu be installed on a NTFS partition?

---

