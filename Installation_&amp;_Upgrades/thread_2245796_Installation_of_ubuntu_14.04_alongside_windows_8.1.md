---
title: "Installation of ubuntu 14.04 alongside windows 8.1"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by govinda3 on 2014-09-26
I will be installing ubuntu 14.04 alongside preinstalled windows 8 .I have C: drive with 150GB  and D with 100GB free space,what i want to know is, will i get ubuntu installed on same drive or on different drive if i select option install ubuntu alongside ubuntu ??

---

### Post by edison23 on 2014-09-26
you mean alongside windows? 
a/w since ubuntu and windows use different file systems, i dont believe they can be installed on same partition (even if they could by some magic, it would be pretty messy)... but dunno, never tried
I suggest creating a new ext4 partition

---

### Post by yancek on 2014-09-26
You will need to post more information.  It's not clear whether you have only one physical hard drive or two or more.  You will not see the naming conventions used by windows such as C:\ and D:\, etc. to name partitions.  Linux naming conventions for drives/partitions are totally different.  If you have only one hard drive and you also have free or unallocated space on that hard drive, the "Alongside" option should work.  If you have no free space, you will need to shrink a windows partition to make some.   If you have windows 8, there are some other factors you will need to deal with such as GPT/UEFI and fastboot.

---

### Post by govinda3 on 2014-09-30
I have Windows 8.1 on C: drive and i want to install Ubuntu14.04 on D: drive and i will be extending D: drive with E: what i want to know is ,is it fine if i select install "Ubuntu alongside windows" option and is it ok to keep three partitions?

scenario:
C: 100GB Primary partion(Boot,page file,crash dump) <== windows 8.1 installed
D:50GB Logical partition
E:50GB Logical partition <==will merge with D:
F:90GB Logical partition

---

### Post by Vladlenin5000 on 2014-09-30
Please don't open multiple thread for the same issue. It dilutes the community effort.

---

### Post by coffeecat on 2014-09-30
@govinda3, I've merged your two threads.

---

### Post by govinda3 on 2014-09-30
I have 3Gb RAM ,how much swap space should i allocate?

---

### Post by Vladlenin5000 on 2014-09-30
Before that read again post #3.

---

