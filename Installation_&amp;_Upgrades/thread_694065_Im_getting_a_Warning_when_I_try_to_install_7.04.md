---
title: "Im getting a Warning when I try to install 7.04"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by Alexeon Lanar on 2008-02-11
I need help. Im trying to dual-boot WIndows XP and Ubuntu. After having some problems earlier, I reinstalled 5.04 and left it alone for a long time. Now I want to install 7.04 and when I did the whole partition thing, Im about to format the Ubuntu partition and I get a Warning.

File System doesnt have expected sizes for Windows to like it. Cluster size is 2k (1k expected); number of cluster is 20017 (39957 expected); size of FATs is 79 sectors (157 expected).

Heres a screenshot:

[http://img144.imageshack.us/img144/5521/screenshotui3.png](http://img144.imageshack.us/img144/5521/screenshotui3.png)

My options are Ignore and Cancel.

What should I do? I dont want to uninstall Windows XP. Thanks in advance.

---

### Post by Pumalite on 2008-02-11
Post your specs.

---

### Post by Alexeon Lanar on 2008-02-11
All right, here are my specs. If you need more info, just ask.


Windows XP/Ubuntu Dual Boot
62.4 GB/11.5 GB
1.25 GB Ram
80 GB HDD
64 MB Integrated Graphics Card
1 CD-R/RW drive
1 DVD-R/RW drive
250 GB HDD external

I think thats it. I might have missed some things...

---

### Post by Pumalite on 2008-02-11
Check your hard drive with TestDisk and/or Rescuecd:
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)
Unless you can boot Windows?
If so, get Gparted Live CD: [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Burn to disk and boot from it. See if it shows any errors. Also, you can do all your partitioning prior to installation.

---

### Post by Alexeon Lanar on 2008-02-11
I can access Windows. In fact, Im doing so now.

Ill try GParted. It doesnt seem like there is anything wrong with anything. I can still access my 5.04 partition and everything boots fine (except for Ubuntu... I get some weird error.)

---

### Post by Alexeon Lanar on 2008-02-15
Sorry for this late post and the fact that Im double posting, but I tried using Gparted but I dont know what to do with it.

I defragmented my hard drive on WIndows XP and when I tried to install Ubuntu again, I got the same problem, but I was able to see the used space in the Windows partition (which, if you look at my original screenshot, is something I wasnt able to do before I defragmented) but I still get the same problem so defragmenting isnt the fix...

Again, I dont know how to use Gparted, but if anyone can tell me what to do, Ill give it a try. Id like to have the latest version of Ubuntu running.


The weird thing is that when I installed Ubuntu 5.10 using the old partitioner, I didnt get any problems. I completely erased the old Ubuntu and SWAP partitions and used the free space to automatically re-partition it into the new install of 5.10. This means that I now have a working Ubuntu install but I cant upgrade to the latest one. -sigh-

---

### Post by Pumalite on 2008-02-16
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
[http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_](http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_)

---

