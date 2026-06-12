---
title: "Not enough space for 11.10 upgrade?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by rashby3 on 2011-10-14
Tried to upgrade from 11.04 to 11.10.

I got a message from the update manager saying I need 3400 M to do the upgrade and need to free up at least 296 M on '/'

I freed up a lot of disk space, several GB, but keep getting similar messages. In fact, each time I free some disk space the amount I need to free up on '/' goes up the next time I run the update manager.

Here is what a df shows:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9851308   6305388   3045500  68% /
none                   1019400       700   1018700   1% /dev
none                   1026024      1580   1024444   1% /dev/shm
none                   1026024       264   1025760   1% /var/run
none                   1026024         0   1026024   0% /var/lock
/dev/sda3            180298120  11193996 159945468   7% /home

My guess is that the update manager is telling me I need more free space on /dev/sda1. I obviously have over 150 GB of space available on /dev/sda3.

The disk utility tells me that volume /dev/sda1 has "Partition Flags" equal to "bootable." 

How do I free space on /dev/sda1? Or can someone suggest what else my problem might be.

Thanks very much.

---

### Post by 23dornot23d on 2011-10-14
You need space on sda1 as you say - from a terminal you could do ....

sudo apt-get clean

sudo aptitude clean

may get some space back

bleachbit ..... is a tool for regaining space ..... if you still do not gain enough
from the previous commands ..... and can be installed with

apt-get install bleachbit

---

