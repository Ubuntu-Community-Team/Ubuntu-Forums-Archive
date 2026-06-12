---
title: "How can I Give more HD disc space to Ubuntu?"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by rhudeboye on 2008-09-26
Im looking to go in 75% Ubuntu. While transfering files I ran out of disc space. The hard drive is big enough as this info (mostly music and movies) was already on this machine. i put it all on a external HD and then went to drop it in ubuntu. 

I assume its a matter of how the partition is set up. how would i go about giving more space to ubuntu and taking it away from XP? Or is it another issue?  

Thanx

---

### Post by Partyboi2 on 2008-09-27
You can use gparted live cd or ubuntu live cd (System>Admin>Partition Editor) to resize your partitions. 
You can also check how much space you have left on your ubuntu partitions by opening a terminal (Applications>Accessories>Terminal)
and typing
```
df -h
```
then check that the available space is enough for you to transfer your data over. If not resize your partition.

---

