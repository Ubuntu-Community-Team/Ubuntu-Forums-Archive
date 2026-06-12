---
title: "Ubuntu 9.10 Woes -MacBook late 2008 install- Mac OS X 10.6.2"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by dejournett on 2010-01-04
I tried to install Ubuntu 9.10 by following instructions for 8.10 through bootcamp. The final step (repairing master boot record through rEFIt) failed miserably (The option of repairing it didn't appear). Now, I'm missing about 34G of hard drive space that bootcamp took up. Both drives created using gParted are unmounted and wont mount (I have deleted the third drive, Linux Swap, but couldnt delete these two). Here's the kicker though: When I try to repartition my drive through disk utility (even when booting off install disc), I get this error message: 

Disk Utility has lost its connection with the Disk Management Tool and cannot continue. Please quit and relaunch Disk Utility.

And apparently even the disk utility on the install disk had the problem too. I have screenshots to post if anyone needs them. Thanks in advance.

One more Mac-related question: should I flat-out re-install my system? if I do, will it erase all of my drives and make one new partition? Thanks.

---

### Post by gabo.cr on 2010-01-04
Sometimes Mac OS doesn't like it when another program makes changes in the partitions.
Installing Mac again will delete all those partitions, I recommend making the Ubuntu partition at the installation of Mac.

---

### Post by dejournett on 2010-01-04
>>shameless bump<<

---

