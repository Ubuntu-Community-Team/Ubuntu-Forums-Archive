---
title: "Install Ubuntu with /Home on it's own Partition"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by Ichido on 2011-04-14
I was told:

"Why not put your /home folder on its own partition and it will persist when you upgrade."

Anyone know how to do this?

---

### Post by ajgreeny on 2011-04-14
[Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")

---

### Post by Ichido on 2011-04-14
Thank you very much :D

---

### Post by bryanl on 2011-04-14
Basically, what you do is the choose 'manually partition' during install. 

Set up a root partition with 12 to 16 GB and whatever is left for /home. You should also provide for a swap partition that is the same size as your memory. I prefer to set up a swap file in the root partition but that isn't as automatic as a separate swap partition.

When you set up the partitions, you tell it the file system type - use EXT4 for / and /home and swap for the swap. You tell it the size. And you tell it the mount point (/ and /home).

The install should then do its thing.

The link refers to the 4 partition limit in MBR type schemes. True, but you can make one of those an extended partition and put all the Ubuntu partitions inside that if you need to.

---

### Post by Ichido on 2011-04-14
Thank you bryanl !

I'll try this on my Dual Boot Laptop.

---

