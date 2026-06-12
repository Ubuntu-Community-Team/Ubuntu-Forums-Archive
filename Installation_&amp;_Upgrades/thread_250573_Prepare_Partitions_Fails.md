---
title: "Prepare Partitions Fails"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by WarrenCarl on 2006-09-04
Hi,

I am totally new to Linux and Ubuntu.  I would very much like
to become part of the Ubuntu community.  I am trying to install
Ubuntu on two different computers and have failed on both, so far.

Here is problem 1.  I have a HP Pavilion 7920 desktop running
Windows XP home edition.  When I try to install Ubuntu in a dual
boot configuration, I get to the Prepare Partitions screen
and am told that Ubuntu cannot read my hard drive to partition it.
It indicates correctly that the system is FAT32.  

I could try a commercial partition program, but I was wondering if there was some way to do the partition without having to go to this trouble and expense.  

The computer originally came with something like Windows ME on it.  HP sent me a XP update diskette when XP came out and I installed XP.  I don't know if this could cause Ubuntu problems.

Please help.

I will explain my second problem in another posting.

Thanks,
Warrencarl

---

### Post by zxee on 2006-09-04
If you're using the desktop (6.06) release there is an automatic partition option. You can also edit your partition table manually with > sudo cfdisk /dev/hda typed in a terminal.
Take a look at the install guides too: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

