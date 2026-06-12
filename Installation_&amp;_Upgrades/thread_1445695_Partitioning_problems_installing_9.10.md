---
title: "Partitioning problems installing 9.10"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by keipana on 2010-04-02
Absolutely new to Ubuntu.  Bought a netbook to use as testbed to learn about Linux.  Netbook came with hdd of 230gb divided into C at 114gb and D at 114 gb.  Netbook comes with XP SP3 installed in C drive.  I started to install 9.10 and when I get to partitioning section I am presented with 2 options, (1) erase and use entire disk or (2) specify manual partition (advanced).  I tried the manual option and ended up dividing the D drive which resulted in half the drive space disappearing.  I used the recovery disk and got back to square one.

When I select the manual option I am present with the following:
/dev/sda
   /dev/sda1  NTFS  122383mb    6966mb used
   /dev/sda2  NTFS  122383mb    3221mb used
   /dev/sda3  Fat32  5247mb       3678mb used
   /dev/sda4            49mb           unknown

The options at the bottom of page are, New partition table or Revert.

On the previous page to this one, it shows that elements of XP are on sda1 and sda3.

I am trying to get Ubuntu on to sda2 or the D drive.  I do not need to make the drive smaller.

Instructions in small words regarding mount points etc would be really appreciated.

Tks  Keipana

---

### Post by prodigy_ on 2010-04-02
1. Read [this](https://help.ubuntu.com/community/HowtoPartition) and [this](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-9.html) (nice guides with pictures and explanations).

2. Boot into Windows. **Make a backup of all valuable data.** Then delete all partitions except the system partition. The reason why you should do that from Windows is that it won't let you to delete the system partition by mistake.

3. Try to install Ubuntu again. :-)

---

### Post by keipana on 2010-04-05
Took a while to work out how to remove partitions in Windows but got there and have now installed 9.10.  tks for help Prodigy

---

