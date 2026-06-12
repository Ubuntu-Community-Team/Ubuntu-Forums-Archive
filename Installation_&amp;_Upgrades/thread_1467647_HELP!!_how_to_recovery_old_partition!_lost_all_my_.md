---
title: "HELP!! how to recovery old partition! lost all my work! :-("
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by fudzz on 2010-04-30
Really Need Help,

This morning, i want to install ubuntu 9.10 and want to upgrade to 10.04. Im using live CD and while install, i go to advance partition and resize the windows partition and after i resize the partition i saw my windows partition has lost.

Here the details:

**Windows XP size: 80gb and free size 35gb**

i want to use my ubuntu size around 10gb, after i resize to 10gb and format etx4 as root my windows partition has gone. :(

how to recovery and revert my windows partition back??


Actually, i'm still not install the ubuntu and now still using live cd to get the solution.

Someone can help?

---

### Post by fudzz on 2010-05-01
Here the screen shot

[ATTACH]154904[/ATTACH]

---

### Post by parn on 2010-05-01
Was you Windows XP's partition occupying your entire hdd before you modified the partition? Did you change the size of the Windows partition in ubuntu (installtion)?

If yes... ouch..

---

### Post by oldfred on 2010-05-01
First do not write anything to the drive and use the liveCD for testdisk:

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

---

### Post by srs5694 on 2010-05-01
If you changed the start of the Windows partition, then Windows will react like a recalcitrant child. The solution (if any) will be entirely in Windows. It's conceivable that a Windows recovery CD will be able to get Windows booting again, but my experience with this has been pretty poor, even following various online guides that claim to provide solutions to this problem. Personally, my usual solution to this problem is to re-install Windows. I find that I spend less time doing this than I do trying to track down solutions that ultimately don't work. :(

---

### Post by vettypayal223 on 2010-05-01
There's this tool called "EASEUS Data Recovery Wizard Professional" a **commericial** program for **Windows** which recovers data from Lost windows partitions. I'm not sure about the Linux tools, it's better that you do not make any writes to your Hard disk. Remove hard disk, attach it to another PC running windows, recover your important files using this software and then do whatever you wish to do. Hope this helps. Good luck

---

### Post by spandey on 2010-05-01
If you have not done any more changes then from another PC download system rescue cd ([www.sysresccd.org](www.sysresccd.org)). Go through manual online for partimage. You will be able recover the whole partition within 30 minutes or so.

---

