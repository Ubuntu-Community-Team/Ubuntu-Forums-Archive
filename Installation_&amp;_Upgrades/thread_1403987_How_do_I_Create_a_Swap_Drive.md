---
title: "How do I Create a Swap Drive"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by emagine on 2010-02-10
Hell Linux Community,

I am about to install Linux alongside Windows vista.  Everything is ready to go.  But I just want to know how to create a swap partition during the installation. I would like to use hibernate/suspend, so how I would I create one upon installation.  Or is it automatic?

thank you.

---

### Post by Satoru-san on 2010-02-10
It should automatically create a partitioning solution. You just need to edit it, you will want your swap to be in the middle of your drive so not partition 1 not partition 4. 2 or 3 is the best place.

---

### Post by emagine on 2010-02-10
> **Satoru-san said:**
> It should automatically create a partitioning solution. You just need to edit it, you will want your swap to be in the middle of your drive so not partition 1 not partition 4. 2 or 3 is the best place.

Ok, how big should I make it? I have 2 gigs of ram.  And what file system should I use. ext3 or ext4?

---

### Post by Satoru-san on 2010-02-10
> **emagine said:**
> Ok, how big should I make it? I have 2 gigs of ram.  And what file system should I use. ext3 or ext4?
Read this for the size:

[http://www.sunmanagers.org/pipermail/summaries/2005-February/006111.html](http://www.sunmanagers.org/pipermail/summaries/2005-February/006111.html)

For the file type its a swap... so the file system is swap :KS

---

### Post by emagine on 2010-02-10
> **Satoru-san said:**
> Read this for the size:

[http://www.sunmanagers.org/pipermail/summaries/2005-February/006111.html](http://www.sunmanagers.org/pipermail/summaries/2005-February/006111.html)

For the file type its a swap... so the file system is swap :KS

I was talking about which file system should I use for the partition the OS is installed on.

---

### Post by Satoru-san on 2010-02-10
This might help.

[http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)

I would say ext4 > ext3 > reiserFS , though all 3 are great! do some googling and pick one. You cant change it later though ( or atleast not easily )

I use ext3.

---

### Post by emagine on 2010-02-11
Swap drive was created automatically.  Installation was smooth.  Dual boot city baby!

---

