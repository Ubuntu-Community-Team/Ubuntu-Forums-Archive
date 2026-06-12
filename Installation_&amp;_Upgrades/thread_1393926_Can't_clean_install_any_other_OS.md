---
title: "Can't clean install any other OS"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by gaijin2000 on 2010-01-29
Hi everyone.
I've recently bought an MSI notebook. Here are the specifications:
[http://www.msi.com/index.php?func=prodtmpspec&maincat_no=135&cat2_no=680&cat3_no=&prod_no=1841](http://www.msi.com/index.php?func=prodtmpspec&maincat_no=135&cat2_no=680&cat3_no=&prod_no=1841)
My problem is the following.
I have Windows 7 installed on it.
I've tried to install many OS's like:
Ubuntu 9.10,Ubuntu 8.10,Backtrack 3 beta, 3, 4 beta, 4 pre final, 4 ,Auditor, Mandrake, Hackintosh, nUbuntu, PHLAK, Knoppix,NOTHING WORKS !!!
After the installing instructions (screen) the computer freezes.
So far the only solution I've got is Ubuntu 9.10 installed with Wubi, and PHLAK on VMware Workstation 6.5.But no clean install so far.
Can you help me out ladies and gentlemens?
Thanks in advance.

---

### Post by oldfred on 2010-01-30
Has your windows install with hidden partitions used up all 4 primary partitions?  Have you tried partitioning in advance?

From liveCD run this. 

sudo fdisk -l  (el not 1 or I)

Info on partitioning:
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition](http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition)

---

### Post by gaijin2000 on 2010-01-30
Yes it has.
Windows made at least 2 or 3 partitions,maybe more.
The biggest one is 100MB I think.
I'll give a try and I'll be back with news.
Thank you.

---

### Post by gaijin2000 on 2010-01-31
I did it with the alternate version of 9.10. YEEEEEEE'
Now I'll see if everything works.
I'll be back with more questions,because I'm new in Ubuntu.
Thank you.

---

