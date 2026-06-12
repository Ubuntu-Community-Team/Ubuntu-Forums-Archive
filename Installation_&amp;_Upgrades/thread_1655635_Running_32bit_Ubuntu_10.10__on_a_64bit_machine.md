---
title: "Running 32bit Ubuntu 10.10  on a 64bit machine"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by walruspanzer on 2010-12-29
I'm currently running 32 bit Ubuntu 10.10 on my laptop. Apparently, my computer can support 64bit OS. My / and /home partitions are separated and exist on different physical hard drives. Is it possible to just install 64bit ubuntu over my 32bit existing installation? Could I preserve the customizations I've made? what about application settings like chrome, firefox, compiz, etc.?  Would I have to meticulously reinstall all of the little things I've done to my ubuntu installation?

---

### Post by ezsit on 2010-12-29
If your sig is accurate and you have less than 4GB of RAM I would not bother with 64bit Ubuntu. You won't gain much, maybe a little performance on highly CPU intensive tasks, but not much. The real benefit of 64bit OS's is to use more than 4GB or RAM and running virtual machines in all those many GB's of RAM.

---

### Post by walruspanzer on 2010-12-29
The most resource heavy thing I do with ubuntu is bittorrent. My concern is only using 66% of the RAM available. If it could make my ubuntu experience noticeably faster with such things and multitasking, I'd be willing to try. I'd do it if all I had to do was install the 64bit OS on the / partition and just download all the programs I use. Their config settings are in the /home folder, right? It should be a matter of just reinstalling the programs that I use. Am I even close to correct on this? I'm not a power user.

---

### Post by presence1960 on 2010-12-29
> **walruspanzer said:**
> The most resource heavy thing I do with ubuntu is bittorrent. My concern is only using 66% of the RAM available. If it could make my ubuntu experience noticeably faster with such things and multitasking, I'd be willing to try. I'd do it if all I had to do was install the 64bit OS on the / partition and just download all the programs I use. Their config settings are in the /home folder, right? It should be a matter of just reinstalling the programs that I use. Am I even close to correct on this? I'm not a power user.

Don't worry about the only 66% of ram used, linux uses RAM quite differently than windows does. Yes you can install 64 bit over the 32 bit linux. make sure you do manual partitioning at the partitioning screen of the install. Put / over the old /. Then edit the options for /home partition by setting it's mount point as /home. **_DO NOT TICK THE FORMAT BOX!!_**lEAVE IT BLANK AND PROCEED WITH THE INSTALL. This will make sure your home auto mounts when ubuntu boots. Even though you don't have 4 Gb of RAM I would still use 64 bit. Besides RAM is cheap you can always add a stick.

---

