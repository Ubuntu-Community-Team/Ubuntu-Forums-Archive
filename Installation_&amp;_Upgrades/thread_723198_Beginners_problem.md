---
title: "Beginners problem"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by drkeselj on 2008-03-13
Hello,

I have 2 partitions on my disk. On the first one is Windows and all applications.
I want to install Ubuntu on second partition.
So, I have heard that it could be a problem, because Ubuntu wants to make his own partitions.
Now, I am worried about data on the Windows partition.
What should I do?

Thanx

---

### Post by housam on 2008-03-13
No worry about windows partition . all what you need is to creat 2 partitions for ubuntu. 
using the Gparted tool on the live cd , you can create them both from the 2nd partition you have .
You need one partition for the root ( / ) ext3 format and the second one for the swap ( only 1 GB ) and during the install process assign them manually.

---

### Post by Sef on 2008-03-13
**Back up** your data.  There is no 100% guarantee that all will go without a hitch.  Read [Psychocat's Installing Ubuntu]("http://www.psychocats.net/ubuntu/installing") before attempting to install.

---

