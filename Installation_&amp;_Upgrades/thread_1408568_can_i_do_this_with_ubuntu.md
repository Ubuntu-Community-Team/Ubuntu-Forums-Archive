---
title: "can i do this with ubuntu"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by balkrish999 on 2010-02-16
i have a laptop which had vista on it and had a 160gb hdd i then partioned it 
so i had windows 7 dual boot
vista= 80gb 

andther hd =  30gb which has my recovery init 

windows 7 = 30gb wich has my dual boot 2nd os on it 


so my laptop now has a dual boot of  vista and 7 

can i partion my hard drive which has my recovery init into another 15gb  

and install ubuntu on that 15gb hdd   and have   vista windows 7 and ubuntu  on a triple boot   is this possible????

---

### Post by Mark Phelps on 2010-02-16
While it certainly is POSSIBLE, in general, it may be very difficult in your case -- depending on how your partitions are setup.

If the drive you want to use for Linux already has four primary partitions, it could be quite a bit of work to reformat that to allow the creation of new Ubuntu partitions.

To give us a better picture, boot into an Ubuntu Live CD, open a terminal, and enter "sudo fdisk -lu" (that's a lowercase L, not a one).

Post the results back here.

---

