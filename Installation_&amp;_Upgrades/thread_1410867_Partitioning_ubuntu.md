---
title: "Partitioning ubuntu"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by Delevix on 2010-02-19
Heya

Firstly im a linux newbie so try and bear with me, and make any advice clear :)

anywho Ive been running ubuntu for a while on a single partition. Ive recently been looking into other distros and came across arch linux. As i installed arch it was recommended that you create partitions for various directories, such as boot, tmp etc. 

Ive read the advantages of this and would now like to set ubuntu up in a similar fashion, alongside arch. Whats the 'best' way to do this. Can ubuntu use the partitions set up by arch? Will i have to reinstall ubuntu?

eh i dont know if my question makes sense since its late here and its a topic i know little about. To put it simply:

how do you create a multi-partitioned system running both ubuntu and arch

---

### Post by elliotn on 2010-02-19
Gparted can partition well

---

### Post by Delevix on 2010-02-19
just to make things clearer, search 'linux partition scheme' in google or check out these links 

[http://bbs.archlinux.org/viewtopic.php?id=50039](http://bbs.archlinux.org/viewtopic.php?id=50039)
[http://bbs.archlinux.org/viewtopic.php?pid=376698](http://bbs.archlinux.org/viewtopic.php?pid=376698)

thats what im trying to do, but with both ubuntu and arch (ive already got arch set up like that) I just dont know what to do with ubuntu. :/

---

### Post by darkod on 2010-02-19
In Ubuntu you would need to start the install process and in step 4 select Advanced (Manual). Then you can create as many partitions and their corresponding mount points as you like.

Usually you can't share these partitions between two different linux distros because they often use slightly different settings/configuration so there will be conflict.
But if you want to create all those partitions for Arch, and then also for Ubuntu, go ahead.

For standard home desktop you wouldn't need anything more than /, /home and swap. This is slightly overdoing it, but it's good practice anyway. :)

---

