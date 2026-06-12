---
title: "Can't install 9.10 on Windows 7"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by coolyus5712 on 2010-03-09
I am using window 7. I want to get Ubuntu. I have the download & CD but windows can't read the files. What now?

---

### Post by efflandt on 2010-03-09
I guess it depends what you downloaded and what you did with it.  Typically you would download an iso file and burn that to a CD as an image (not as a data file).  Then you would boot from that CD.

I am not sure how Wubi works installing Ubuntu within Win7.

What I did was used administration tools in Win7 to shrink its partition and make room for Linux.  Then I booted the Ubuntu CD into a live system, and used Gparted to create the partitions I wanted to use for Linux (in my case just a main partition and swap partition).  Although during installation you could instead let Ubuntu create partitions in the unallocated space (the space you freed up when shrinking Win7).

---

### Post by presence1960 on 2010-03-09
Don't start duplicate threads on the same topic please. You have a thread here from 4 hours ago about the same problem: [http://ubuntuforums.org/showthread.php?p=8941731#post8941731](http://ubuntuforums.org/showthread.php?p=8941731#post8941731)

---

