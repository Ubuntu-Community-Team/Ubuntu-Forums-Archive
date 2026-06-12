---
title: "Dual Boot Ubunt and another linux"
date: 2007-04-13
forum: Installation &amp; Upgrades
---

### Post by eoldynski on 2007-04-13
I have Xandros (debian) V 4 installed and I would like to install Ubuntu as a second boot . 

How do I configure the HD to do this ?

ed.

---

### Post by zvacet on 2007-04-14
During the installation you will came to the partition step,and then you choose manual way to do it.You wil see your partitions and free space.Of course you will install Ubuntu on the free space,and you will make
1. root =no more then 10GB     mountpoint /
2.home =rest of free space       mountpoint /home

I belive you allready have swap partition,and I´m not sure shering home is good idea,so that is the reason I sugested you to make home for Ubuntu.I write this in faith that you have enough free space.If you have 10 or less free space you willl not do partition.let ubuntu automaticly make partition for you.

---

