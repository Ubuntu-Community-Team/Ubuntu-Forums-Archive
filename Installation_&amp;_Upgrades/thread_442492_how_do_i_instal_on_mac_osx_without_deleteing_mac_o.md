---
title: "how do i instal on mac osx without deleteing mac osx"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by lennshow66 on 2007-05-13
how do i instal on mac osx without deleteing mac osx please can someone help me from the downloading??????? please help me

---

### Post by bulldog on 2007-05-13
You could do some research on your own................

Nobody guarantees you won't lose data,**always backup valuable data before installing another OS**

Download a copy of ubuntu,I would take the alternative instead of the live cd.
Download a copy of gparted live cd,[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) burn it to a disk and boot from it.
Now you see a partitioner with a graphical interface,which should display your partitions.
You have to create two partitions for ubuntu as a minimum,a / root partition and a swap partition.
The swap you can make 1GB and the / root about 5-10GB,or more if you have space.
Apply this and exit the gparted cd when done.

Boot ubuntu cd and go to the desktop,hit the install button and follow the on screen steps.
When you come to the partition section,choose manual,mount the biggest as / and swap as swap.
Set only this two partitions to format / as ext3 and swap as swap and continue the install.

Have fun.

---

