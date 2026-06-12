---
title: "How to partition this space"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by Victor_Davis on 2011-06-19
I have 237170 MB of space. How should I partition this in order to run Ubuntu? The only space currently taken is a windows restore enviroment should I ever decide to switch back. I searched the forums for something similar to this but I'm an idiot and kinda need to be told exactly what to do. Most helpful poster gets a star.

---

### Post by jerrrys on 2011-06-20
if you need to restore windows, you will need the restore disk (cd)

---

### Post by oldfred on 2011-06-20
Will you ever reinstall windows. Are you just installing Ubuntu or maybe try other installs? Do you need a NTFS partition for sharing with windows?

There is no such thing as best, and each of us have what we think may be best. But I find my own best partition layout is not so good a couple of years later.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

But do not create /boot unless real old system with 137GB BIOS boot limit.
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

