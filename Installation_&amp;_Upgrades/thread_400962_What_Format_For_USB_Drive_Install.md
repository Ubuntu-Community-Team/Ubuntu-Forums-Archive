---
title: "What Format For USB Drive Install?"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by pablo88 on 2007-04-04
Hi -

My first post and hopefully an easy one to answer.

I have a Toshiba 80Gb USB external hard drive. I want to use the whole drive to install Ubuntu on. Currently the drive is empty, has no partitions and is not formatted. What steps should I take to install Ubuntu on this drive in the optimum manner?

I currently use Win XP Pro SP2. I am somewhat dense when it comes to partitioning and also vague as to whether the drive should be formatted as NTFS or FAT32.

Many thanks in advance.

-- Pablo88

---

### Post by tpg on 2007-04-04
Do you want to be able to access files on it from windows? If not, then use a linux filesystem, such as ext3 (which is the default for a Ubuntu installation) or ReiserFS. If you do, then I'd say create an "exchange" partition as well (FAT32) so you can transfer files between the operating systems. FAT32 is well supported by both linux and windows.

I think you ought to be able to setup partitions in the ubuntu installer program. 
Hope this helps! :)

---

### Post by pablo88 on 2007-04-05
Thanks for the response tpg. Turns out that the USB hard drive I want to use is faulty in some way. But I'll be acquiring a new one shortly and will go with ext3 throughout the drive. This intermediate step is my last one before jettisoning Windows completely and going Ubuntu on the main drive of the machine.

-- Pablo88

---

