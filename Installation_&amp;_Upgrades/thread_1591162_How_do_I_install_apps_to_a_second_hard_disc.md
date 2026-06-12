---
title: "How do I install apps to a second hard disc"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by zl1ogx on 2010-10-08
Hi

I have searched the forums but can't find the answer, so please if you know where the answer is please direct me to it.

I have a Dell mini 9, which has a 8gb SDHD, I purchased a 16gb SHHC card.  Now my plan is when 10.10 is released in a couple of days, is to install the UNR version.  Than will see to most of the 8gb SDHD.

So when I want to install other application which are not installed as default, I would like then to go onto the 16gb SDHC card, instead og the 8gb SDHD.

How do I do it?  Can it be done, surely it can, after all Windoz asks for the install directory and a superior OS such as Ubuntu must be able to also.

Cheers

Ian

---

### Post by srs5694 on 2010-10-09
Linux's filesystem model is very different from Windows'. Most software packages install components in several directories, and if you install from a .deb package (as is typical on Ubuntu), there's very little flexibility in where the packages reside. For your type of situation, there are several possible ways to spread your files across multiple disks:


[list]
[*]You can split your partitions across the two disks, strategically placing them to spread the load. Most Linux program files reside in /usr, so you might create a separate /usr partition on one disk, keeping the rest of the system on another disk. Alternatively, you could keep all the system files on one partition and split off user files in /home to another partition. Using a separate /home has several other advantages, which have been discussed repeatedly in this forum.
[*]If you just want to separate a specific program or two, you could do something similar to the above, but put /usr/local on its own partition/disk and compile the programs you want isolated yourself, rather than use a Debian package. Programs you compile yourself typically get installed to /usr/local, so this will effectively isolate them.
[*]You can use an [LVM](http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/) configuration, which enables you to combine two or more disks into one virtual storage area that can then be broken up in whatever way is convenient, vs. whatever way the sizes of your disks permit. Unfortunately, Ubuntu doesn't make LVM installation easy. Fedora's much better on this score.
[*]You can install programs normally, then move files or, better, directory trees, from one location to another and create symbolic links in the original locations to point to the files' or directories' new locations. This is, IMHO, a rather ugly workaround. Particularly if you move individual files rather than directory trees, it can create problems when you upgrade packages, since the replacement files are likely to replace symbolic links rather than the linked-to files, thus consuming space where you don't want it consumed.
[/list]


All but the last of these methods require a degree of planning that Windows doesn't require, but they help keep the system in a consistent and logical state. (See the [Filesystem Hierarchy Standard, or FHS,](http://www.pathname.com/fhs/) for the logic behind Linux's directory tree layout.) Doing it the Windows way, where any program can be installed anywhere, creates a lot of system-to-system variability that creates its own problems, some of which have ugly solutions. (The Windows Registry, for instance.)

---

### Post by zl1ogx on 2010-10-09
Thanks for the good explaination of using the /user partition.  I will investigate this, so it loks like a custom install when 10.10 becomes available to put the /user onto the SDHC card. 

Here's hoping I don't stuff up too much.

Thanks

Ian

---

### Post by xjesse on 2010-10-09
Spelling Windows as 'Windoz' is the reason why this community is hated so much.

---

### Post by DanPerecky on 2010-10-10
> Spelling Windows as 'Windoz' is the reason why this community is hated so much.
I've browsed several Linux distro forums... they all do that. It's normal.

---

