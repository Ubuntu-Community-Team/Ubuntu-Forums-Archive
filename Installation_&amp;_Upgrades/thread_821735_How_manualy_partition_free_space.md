---
title: "How manualy partition free space"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by dillon111222 on 2008-06-07
Hi this is my first time installing ubuntu and im setting up a dualboot with vista. I freed up about 53 gb for ubuntu with vistas partitioner and its just called unallocated space. When i boot up the live cd and get to the part where it asks where i want to install i only get the option to completely install on disk or manual. For some reason it doesnt give me the option to do a guided install on free space...... So i just want to do it manualy but im not sure what to do. could someone give me step by step instructions on how to do the manual install( like what to make swap and stuff)

Thx

---

### Post by tamoneya on 2008-06-07
well if it forces you to do the manual install you need to make at least two partitions:
1) swap.  This should be 4 GB or so depending on how much RAM you have.  It should be at least as large as you ram so that in the event of a kernel panic or something ubuntu can dump the ram onto swap if it has time.

2) /.  This is the root partition.  This should be the rest of your space and it is here that all of your files and your OS reside.

Some people also recommend that you make /home so if you reinstall you can just replace the / partition with your new OS and keep all your files on the /home partition without need for backup and transfering everything back and forth.

---

### Post by dillon111222 on 2008-06-07
well i got 2 gigs of ram so ill make like a 3gb swap? then i just make the rest of the space /. but like what file types do i use

---

### Post by avtolle on 2008-06-07
For the / partition, ext3 is the file type. With 2 gigs of Ram, I'd just make a 2 gig Swap, so you could hibernate, etc.

---

### Post by dillon111222 on 2008-06-07
thx man ill try it out

---

