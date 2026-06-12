---
title: "control of partition sizes during install"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by mathias j sagartz on 2008-04-16
I'm a rookie and want to install Ubuntu along with Windows, duel boot.
When I use the install CD I created I apparently don't have any control
over how much of the free space on my hard disc is going to be used by Ubuntu and how much will be left for future Windows use.  I don't want
to commit to the install until I know how the space will be allocated and  I
don't want to have to learn how to patch up partitions after the install.

Current HD configuration:  200 GB disk with two partitions (both for WIndows):   C:  140 GB    F: 60 GB

Is there any way I can see what the partitioner is going to do to my
system before I OK the install?

---

### Post by tvtech on 2008-04-16
sure get[ gparted]("http://gparted.sourceforge.net/livecd.php") live cd 

do your partition with that instead.

do a little disk clean up first too.  in xp right click my computer,  go to properties

under properties your going to want to disable your page file virtual memory and your recovery file for xp  then defrag your disk until you can't defrag any more

---

### Post by SnakeHips on 2008-04-16
During the install from the liveCD ,when it gets to the "partition" section ,select "manual.

A common three partition setup is as follows

/               
/swap
/home  

hope it helps

---

