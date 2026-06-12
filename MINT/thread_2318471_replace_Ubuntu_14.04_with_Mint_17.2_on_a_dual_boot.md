---
title: "replace Ubuntu 14.04 with Mint 17.2 on a dual boot system with Ubuntu 14.04 &amp; 17.2"
date: 2016-03-26
forum: MINT
---

### Post by sequimbob on 2016-03-26
I have a HP g71-340US Notebook with Ubuntu 14.04 and Windows 7 Professional installed as a dual boot system.  I want to replace the Ubuntu 14.04  with Linux Mint 17.2.  How do I do that without messing up the windows installation and the dual boot?

---

### Post by Bucky Ball on 2016-03-26
*Thread moved to **Mint**.*

Might improve your chances of support posting on the active Mint forums as well.

I'd imagine you could just boot the installer, choose 'Something Else' at the partitioning section, install the Mint / over the existing Ubuntu / partition if that part of Mint works the same as Ubuntu.

---

### Post by yancek on 2016-03-26
You're a little short on information.  As stated above, if you have Ubuntu on only one partition, you can boot it and from a terminal run:  df -h
The output will show which partition Ubuntu is on as in the example below, it is sda8;

> Filesystem      Size  Used Avail Use% Mounted on
/dev/sda8        39G   29G  8.8G  77% /


You can run:  sudo fdisk -l to find the ntfs partitions.  If you have other partitions, you would need to post that output and someone might be able to help.  If you have a swap partition already, you do not need to create another one.  If you have other data partitions, make sure you don't overwrite those.

---

### Post by sequimbob on 2016-03-27
okay thanks all.  I was pretty sure I could just install it over the existing Ubuntu installation which is on SDA1, but I wanted to verify that.  I appreciated the feedback.

---

