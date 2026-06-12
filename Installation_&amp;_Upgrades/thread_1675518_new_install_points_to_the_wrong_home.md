---
title: "new install points to the wrong /home"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2011-01-25
I have a peculiar problem - I did a new install of 10.10 last night. I thought I had set the partitioner to see my exisiting /home partition on sdb1. However when it booted up it was wrong. (My mistake - it should have been sdb5)

All the files and links etc are already in sdb5 the partition is labeled /media/home How do I make the system use this existing partition as /home and get rid of the false one on sdb1

I tried altering /etc/fstab with the correct uuid but when I booted it couldn't get past the .ice authority (whatever that is)

any help appreciated

---

### Post by ronparent on 2011-01-25
The simplest thing may be to just do the install all over again using the correct /home. We could get cute and try to fix the permissions, etc., but the end result would be you would probably have to search out missed updates to the home that would be picked up automatically in a reinstall. Post how you make out. Good luck.

---

### Post by tropdoug on 2011-01-25
Thanks ronparent - I took your advice and re installed. Two things I did notice, and maybe the developers of the install partitioner could consider this, is that when the partitioner opens it is small and cannot be made larger, thus making it difficult to see the set up if you have multiple hard drives with multiple partitions and secondly none of the partition labels show up, therefore if you get mixed up with which partition is which, you can make some serious errors, particularly if you format the wrong partition. 

Luckily I did not do that and so lost nothing. I know that I should have checked prior, but the purpose of my labeling is to assist those of us that are not tech heads so to speak. 

Anyway - all is well now and perhaps my suggestions might spark some thought. 

Thanks once again

---

### Post by ronparent on 2011-01-25
Glad to hear it worked out. And yes it is easy to make serious errors during partitioning. Fortunately as the installation gets progressively developed some improvements do get worked in.

---

