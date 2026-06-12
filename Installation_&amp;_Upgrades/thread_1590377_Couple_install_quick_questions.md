---
title: "Couple install quick questions"
date: 2010-10-07
forum: Installation &amp; Upgrades
---

### Post by geek2330 on 2010-10-07
want to install u/kubuntu tomorrow, have Windows 7 on a SATA disk, partition 1 is Windows 7, about 50gb.
Partition2 is data storage, don't want to touch at all.

So want to install ubuntu on C drive, or partition 1.
I've seen that a ubuntu installs you create the main OS in / root, then there's a SWAP partition and Home partition?

Aside from / root, are the other 2 necessary?
How can i best manipulate this 50gb partition1 for ubuntu?

Also, if i need a Home partition for data, can I just point to my 2nd partition?

I want to be able to wipe ubuntu OS at any time without risking any data.

---

### Post by sikander3786 on 2010-10-07
You don't need a separate /home partition. "/" will handle it all. You'll definitely need a Swap partition. Split the existing C; partition into 2 partitions by using the Partitioning Tool during Installation.

You need an ext3/ext4 partition for /home and if your 2nd partition has data on it, it is not recommended to use it as /home.

Post back if you've got any further queries.

---

### Post by geek2330 on 2010-10-07
> **sikander3786 said:**
> 
You need an ext3/ext4 partition for /home and if your 2nd partition has data on it, it is not recommended to use it as /home.



I'm a bit confused on this one. But i guess I will just split 1st partition for /root and /swap, then if i need to save any data files i should be able to browse to 2nd partition.

One more question for the 1st 50gb partition, since i have 4g of memory i think /Swap should be 8gb, does that mean /root will be 42gb then.

thanks...!!

---

### Post by sikander3786 on 2010-10-08
> **geek2330 said:**
> I'm a bit confused on this one. But i guess I will just split 1st partition for /root and /swap, then if i need to save any data files i should be able to browse to 2nd partition.

One more question for the 1st 50gb partition, since i have 4g of memory i think /Swap should be 8gb, does that mean /root will be 42gb then.

thanks...!!
For me 3-4 GB has always been enough and I haven't seen it being used. I have 4 GB RAM and that doesn't get filled up that easily. If you've got enough RAM, you only need SWap for hibernation etc. Any size between 2-4 GB will work.

---

### Post by geek2330 on 2010-10-08
but then that will leave me with a partition for the ubuntu OS for about 45gb, isn't that too much just for the OS?

---

### Post by 23dornot23d on 2010-10-08
[COLOR=Blue]if you do it like this - you should have no real problems ....

/[/COLOR] = 20 gig
[COLOR=Blue]swap[/COLOR] = 4 gig
[COLOR=Blue]/home[/COLOR] = 26 Gig


..... and plenty of space for programs that go in [COLOR=Blue]/[/COLOR]

and 26 Gig for Data and config that go in [COLOR=Blue]/home[/COLOR]

I have never needed to use more than 4 Gig for [COLOR=Blue]swap[/COLOR] ......

Just if I was doing it ...... this is what I would probably do ............. :guitar:
We all use our computers for different things though .... you may have 30 Gig of Films and Music
in which case you would make your home bigger to accommodate the required use for your files ......

But if you are just testing it out the above will be good and films and music can sit anywhere really
even on an external Hard Drive ...... lots of options once you have it set up.

---

### Post by geek2330 on 2010-10-08
thanks a bunch, all these info helps.

---

