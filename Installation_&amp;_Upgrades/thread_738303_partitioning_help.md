---
title: "partitioning help"
date: 2008-03-28
forum: Installation &amp; Upgrades
---

### Post by malluda on 2008-03-28
hi everyone!

i tried to install ubuntu 8.04 but i stopped the installation because i was not sure.
i would like to ask you the following:

i have 2 partition in my disks.One is  installed windows vista and the other 30GB is empty (ntfs).
i want to install ubuntu in the empty partition. 

When i go to the partition view of ubuntu installation, i have the options of manually and guided installation. what must i choose?

my problem is that if i choose guided, system shows a partition of ubuntu 55GB that means all the space available except of vista space. i want to install ubuntu in the partition of 30GB, i ve already made.

Could you please help me? What i have to do?

Thanks!

---

### Post by zvacet on 2008-03-28
Use manual way and  do it lik this

1. root = 10GB                  mountpoint /
2. swap =1 GB (maybe less depends how much ram you have)
3. home = rest of free space   mountpoint /home

Ubuntu use ext3 format

---

### Post by malluda on 2008-03-28
ok !

could you please tell me about the root and home?

what are these and how much space do you suggest me for (30GB all the space).
In addition my RAM is 2GB, how much space to give for swap?

and sth else: will i have  any problems if i install a beta version?
Thanks!

---

### Post by housam on 2008-03-28
ubuntu'll be installed on the root file (/) - 15 GB is ok
/home , is the place that you'll store your data - 14 GB is ok
swap is your virtual memory - 1 GB is ok

it is not advisable for a beginner to install a beta version because you'll face some problems that you can't solve easily.

---

### Post by malluda on 2008-03-28
and the additional programs(if i want to install later)  where are installed? in home?

also with the basic cd installation (7.10) i have problem with video/graphics card. the installation fail.
so install alternate 7.10 better?

Thanks

---

### Post by zvacet on 2008-03-28
All programs wich are installed with apt-get or synaptic will be in root partition.
If you have problems press F1 ( it is help) and search for safe graphic mode.If that doesn´t work go for alternate CD.

---

