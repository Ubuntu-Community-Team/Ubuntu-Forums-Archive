---
title: "changed mother boards and cpu type"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2011-03-04
My motherboard gave up its lifetime after 7 years 24/7.

The old motherboard/system had:

1. AMD single core
2. 3 GB RAM
3. NVIDIA GS 7600

New new system has now:

1. AMD 4 core
2. 16 GB RAM
3. NVIDIA GS 7600

My doubts and problems:

1. do I use multi core?
uname -a
Linux ronald-desktop 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 20:52:10 UTC 2011 x86_64 GNU/Linux

(I thought there must be a SMP somewhere)

2. Each time I reboot my computer I have to re-install nvidia:
sudo sh NVIDIA-Linux-x86_64-260.19.36.run 
sudo gdm start

What do I miss here?

bye

Ronald

---

### Post by Hedgehog1 on 2011-03-05
ELMIT,

How did you end up in Taiwan? :D

Do you have the ability to save your data and do a fresh install?  I think that might be best.

Ideally (to ease the pain next time) if you separate your '/' (OS) and '/home' (YOur data) onto separate partitions (or separate drives), it makes OS re-installation and upgrades easier when your data and OS is separated.

***The Hedge***

:KS

---

### Post by ELMIT on 2011-03-05
Actually I did not want to answer to a chit-chat only, but you have such a cute picture.

Believe it or not, once I sat in an airplane, and bang I was in Taiwan. Unfortunately I have not collected money enough for the airfare back, ...

How do you gain the ability to save the data, from a broken mother board? It is just the same challenge as to find the money for the airfare.

To make it more complicated, I used LVM, with 3 hard disks. I was glad that I could get it to work again, just have the mentioned doubts.

To make that message not also just a chit chat, I found that a kernel -generic is SMP up to 8 CPUs, I just do not know how I can make use of each core of it or to see the load of each core, ... yet.

Upgrading is always a challenge, it is like marrying a new wife. All seems the same, just with a new hardware, but the usage is still slightly different, or different "named". Like that the closing X is now on the left side of the window, ... really annoying!, but there are sure some left handed wives around too.

It was nice chatting with you, although I have not gained any useful answers to my problems, ....


bye

Ronald

---

