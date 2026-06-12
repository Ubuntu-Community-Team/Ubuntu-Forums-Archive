---
title: "grub missing; boot repair disk unable to correct"
date: 2014-10-26
forum: Installation &amp; Upgrades
---

### Post by anupam3 on 2014-10-26
Hi folks,

I was dual booting with LXLE and windows 7 .The system ran fine till 4-5 month. However yesterday windows 7 was missing from grub. I went into windows recovery environment and ran fixmbr and fixboot .However now the grub is missing and computer directly boots into windows 7 .
gparted shows unallocated apace .
I have tried boot repair disk and recommended repair but fails to correct.

am pasting boot info summary..
 
 [http://paste.ubuntu.com/8683014/](http://paste.ubuntu.com/8683014/)
Kindly help if i would be able to recover my LXLE partition..

---

### Post by yancek on 2014-10-26
> I went into windows recovery environment and ran fixmbr and fixboot  .However now the grub is missing and computer directly boots into  windows 7 .

That's expected behavior and is what the two commands you entered do, overwrite the master boot record with windows code.  Where was Ubuntu?  All of your partitions are windows filesystems except sda4 which just shows iso9660.  I see some files on sda1 such as menu.lst and grldr.  Were you using Grub4Dos or EasyBCD?

---

### Post by oldfred on 2014-10-26
You are not showing any Linux partition. But you do have a space at the beginning of the extended partition.

If you ran Windows repairs it may have ignored a Linux partition inside the extended partition. It seems to do that a lot.
You should be able to use testdisk from the live installer to restore the missing partition. Note you have lots of other partitions. Not sure if testdisk changes will keep those automatically or if you have to include all partitions when restoring one.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)


 [https://help.ubuntu.com/community/DataRecovery#Lost_Partition](https://help.ubuntu.com/community/DataRecovery#Lost_Partition)
You may be able to use parted rescue as the start is near the beginning of the extended partition and the end is near the beginning of sda5.

---

