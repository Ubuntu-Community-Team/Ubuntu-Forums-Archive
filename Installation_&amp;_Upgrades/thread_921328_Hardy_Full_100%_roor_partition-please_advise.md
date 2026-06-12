---
title: "Hardy: Full 100% roor partition-please advise"
date: 2008-09-16
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2008-09-16
Hi,
I had a full working, fresh install Kubuntu Hardy PC. Running apt for updates it began downloading about 250 MB of updates, yet crashed midway. Looking into it I found 100% usage om my / partition which probably caused the crash. My Trash can is empty, yet looking into /var (same partition) I got, among others, the following:
 -----partial output of root@Ira-desk:/var# du -h | grep M
----
28M     ./lib/dpkg/info
32M     ./lib/dpkg
41M     ./lib/apt/lists
41M     ./lib/apt
87M     ./lib
4.0K    ./spool/cups-pdf/ANONYMOUS
8.0K    ./run/NetworkManager
8.9M    ./cache/debconf
2.0M    ./cache/apt/archives/partial
39M     ./cache/apt/archives
63M     ./cache/apt
74M     ./cache
4.1M    ./log/partimage
6.6M    ./log
169M    .
-----------------------
Can I delete ANY of the above-especially the last 169M one (what is it)?



---------pC/Setup details------------
Linux partitions consist of 3:
a. / 3.9GB ext3 100% used (logic partition)
b. /home ext3 (primary partition) practically empty
c. /swap

It's a dual boot (old) with  a 80GB disk. The (single) XP/ntfs  partition resides on sda1.

----Output of df-h-----------
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             3.9G  3.9G     0 100% /
varrun                252M  156K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   56K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   38M  215M  15% /lib/modules/2.6.24-16-generic/volatile
/dev/sda3             8.3G  147M  7.7G   2% /Images
/dev/sda2              29G  173M   27G   1% /home
overflow              1.0M  352K  672K  35% /tmp
-------------

Please advise!

Thanks

Michael Badt
:(

---

### Post by linuxonbute on 2008-09-16
> **mibadt said:**
> Hi,
 -----partial output of root@Ira-desk:/var# du -h | grep M
----
28M     ./lib/dpkg/info
32M     ./lib/dpkg
41M     ./lib/apt/lists
41M     ./lib/apt
87M     ./lib

32M is the total in ./lib/dpkg
41M is the total in ./lib/apt
87M is the totla in ./lib
and so on for those below. 
> 
4.0K    ./spool/cups-pdf/ANONYMOUS
8.0K    ./run/NetworkManager
8.9M    ./cache/debconf
2.0M    ./cache/apt/archives/partial
39M     ./cache/apt/archives
63M     ./cache/apt
74M     ./cache
4.1M    ./log/partimage
6.6M    ./log
169M    .
-----------------------
Can I delete ANY of the above-especially the last 169M one (what is it)?

the 169M is the total of all the above so you would need to delete them all to recover it.
DONT DO IT. You will mess up your system!!!!!

> 
---------pC/Setup details------------
Linux partitions consist of 3:
a. / 3.9GB ext3 100% used (logic partition)


This is quite small for the full system. 
I guess that is why you have run out of space.

---

### Post by zvacet on 2008-09-16
linuxonbute is right.It is small partition for root.If you want to (and if you have space to do it) you can resize it with ["]Gparted live CD.]("aptoncd.sourceforge.[/URL) Other solution is to clean your root with 


```
sudo apt-get autoclean
sudo apt-get clean
```

That should create some free space.

---

### Post by mibadt on 2008-09-17
Thanks all,
I've decided to create a new partition (at the "expense" of my /home) and move /var to there.

Michael Badt

---

