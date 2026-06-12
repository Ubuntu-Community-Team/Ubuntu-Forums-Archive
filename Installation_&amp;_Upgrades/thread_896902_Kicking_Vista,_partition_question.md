---
title: "Kicking Vista, partition question"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by Inane_Asylum on 2008-08-21
I had Vista/Kubuntu on a dual-boot, and needless to say, using Vista only helped increase my love for Ubuntu exponentially.  I killed Vista (on purpose, in cold blood8-)), and now want to have Kubuntu on the entire HDD (with a couple smaller partitions for /home and whatnot), while running XP as a virtual box.  Since Kubuntu was installed on the second partition after Vista, will there be any problems merging the partitions, or at least shrinking the Vista partition to put my /home files in?

If not, how would I go about doing it?  Messing around with partitions makes me nervous...

---

### Post by mattduckman on 2008-08-21
the easiest way to mess with partitions is to boot into a (K)Ubuntu live CD and run QTParted or GParted. it'll give you a graphical representation of your drive and any changes you make won't be saved until you click on Apply. if you delete the Vista partition, you can create new partitions and expand you kubuntu one. even though it's relatively safe you should still do backups.

---

### Post by SkonesMickLoud on 2008-08-21
How big is your drive, and how big is your current Kubuntu / partition?

If you're going to be doing a separate /home, you'll probably want to have that as your larger partition.  You shouldn't need more than 10 Gb for /.  The rest can go to /home and swap.

---

### Post by Inane_Asylum on 2008-08-21
70G (old) Vista partition/40G Kubuntu

---

### Post by SkonesMickLoud on 2008-08-22
> **Inane_Asylum said:**
> 70G (old) Vista partition/40G Kubuntu

You could simply format Vista to ext3 and make it your /home.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

