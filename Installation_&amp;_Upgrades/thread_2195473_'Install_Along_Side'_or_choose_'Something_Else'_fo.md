---
title: "'Install Along Side' or choose 'Something Else' for Dual-Boot Windows8/Ubuntu"
date: 2013-12-24
forum: Installation &amp; Upgrades
---

### Post by nicolas.husser on 2013-12-24
Hello everyone,

This is the first time Im installing ubuntu in dual-boot mode on my windows machine and I saw a bunch of tutorials saying different things.
Some of them say to use the 'Install Along Side' and some of them use 'Something Else'.
In the 'Something Else' option, they assign different sizes for /, /home, /boot, swap. I was wondering what are the best proportions if I have a partition of my hard drive of 50Gb to host Ubuntu.
What is the difference between the two options and which one is preferable? Also, is there something I should be aware of before I start?

Thanks a lot.

---

### Post by cmcanulty on 2013-12-24
10GB is plenty for / make it 20 if you plan to install many desktops (ex Kubuntu, lxde, etc) for swap you need to at least = your ram if you want to be able to hibernate, rest for /home

---

### Post by Mark Phelps on 2013-12-24
> Also, is there something I should be aware of before I start?

Most definitely -- if you choose the Aside option and shrink the Win8 OS partition to make room for installing Ubuntu, it's highly likely you'll corrupt the Win8 filesystem as a result -- as NTFS partitions don't do well when modified using Linux utilities.

You should use the Win8 Disk Management utility to do any partition shrinkage.

---

### Post by grahammechanical on 2013-12-24
The Something Else option allows us to choose the partition in which Ubuntu is to go. The partitioner will also allow us to create and resize partitions. At a  minimum Ubuntu needs two partitions. One for Ubuntu that is mounted as / and one for swap. The size of the swap partition is related to the amount of memory and whether you need to use hibernation because the data in RAM is stored in the swap partition during installation. A too small swap partition will prevent a reload from hibernation.

So, you need to use the partitioner in the installer to turn the 50GB partition into two partitions. One large and one small (2GB or there abouts). 

Then select the larger of the two partitions and click change. In the dialog box that appears select use as Ext4, tick to format the partition and make the mount point /. Click OK.

Next select the smaller of the of the two partitions and in the dialog box select to use as Ext4, to format the partition and to give it a mount point of swap and then Click OK.

When back at the partitioning screen you can now click to Install.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by ajgreeny on 2013-12-24
For safety's sake I would alwsus suggest you use the "Something else" option when installing as it gives you a much clearer vision of the current partitions and, I think, an easier way to edit what is there.

---

### Post by nicolas.husser on 2013-12-24
Thank you very much, really appreciate your help, I did the partition thing and everything works fine!
Thanks again, and merry Christmas!

---

