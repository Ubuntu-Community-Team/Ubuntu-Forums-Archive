---
title: "Partitioning scheme for installing two versions of Ubuntu in the same machine"
date: 2013-11-29
forum: Installation &amp; Upgrades
---

### Post by crazymonmon85 on 2013-11-29
I want to know the best  partitioning scheme for installing two versions of ubuntu in the same  machine. My hdd is about 180 Gib. I am more looking forward to  suggestions regarding the size of parition.

  Also on a side-note can I install a 64-bit version of Ubuntu on my  i686 machine? When I do lscpu it says it can operate in 64-bit mode (i.e  32-bit pae). I have run live CD and it works and the installer also  started.

---

### Post by ibjsb4 on 2013-11-29
There is no best way to partition.  There are many ways and people have the best for them.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partitioning+scheme&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partitioning+scheme&sa=Search&cof=FORID:9)

I would recommend a data partition for your personal files (music,video and things).  This can be shared with your dual install and gives you some backup if things go bad.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)

---

### Post by crazymonmon85 on 2013-11-29
Thanks for the reply. But could you tell how much space should be sufficient for my root partition, given that my home directory is on a separate partition.

---

### Post by ibjsb4 on 2013-11-29
> **crazymonmon85 said:**
> Thanks for the reply. But could you tell how much space should be sufficient for my root partition, given that my home directory is on a separate partition.

Sorry, but I can not help with that as I do things different.  I just create a free space and use the standard install with a data partition and backup with rsync.

In the link above, look for post by "oldfred", he has posted some really good info on this in the past.

Edit: A better (oldfred) link

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partitioning+scheme+oldfred&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=partitioning+scheme+oldfred&sa=Search&cof=FORID:9)

Happy hunting :)

---

### Post by rewyllys on 2013-11-29
> **crazymonmon85 said:**
> Thanks for the reply. But could you tell how much space should be sufficient for my root partition, gi ven that my home directory is on a separate partition.

I have my Linux installations on a 1.5TB drive, so I'm generous with my partition allocations.  I use 40GB for each different version of a root Linux partition, but, in fact, 20GB should suffice.  In my case, I still have a little over 1TB left for my /home partition.

I suggest that you try 20GB.  It should take quite a while for you to fill that much space with any of your root partitions.

---

### Post by deadflowr on 2013-11-29
+1 to 20gb.
In reality, for most cases, as little as 10gb should suffice.
However, no one knows what you intend to install, so an additional amount should help
leverage against any lack of space issues.

The key to using a smaller amount is knowing when and what can be purged.(ie, kernels, various caches, etc,etc)

---

