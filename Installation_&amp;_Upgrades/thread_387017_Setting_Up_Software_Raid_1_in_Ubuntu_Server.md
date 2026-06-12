---
title: "Setting Up Software Raid 1 in Ubuntu Server"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by browneye253 on 2007-03-17
I'm setting up my first LAMP server and my question is I would like to use the software raid during the install.

I have a dual 2.4 Xeon box with two 36gb SCSI hard drives.  I'm familiar with the basics of RAID setup but rather unfamiliar with using the software raid.

My goal is to have Ubuntu Server running with LAMP and have as much space available after that for websites.  I want to eventually host a few personal websites on this box.

Can someone explain to me or point me in the right direction?  So far I've been very impressed with the Ubuntu community.

Thanks - Paul

---

### Post by elmosgot on 2007-03-19
During the alternative installation cd you will go to the partition part. Then you can format 2 partitions of by example 36 gb and partition type RAID then you active Software Raid. First it will write down the 2 partitions and then you can connect these two partitions in the next dialog. And then finally at the bottom you will find the unused partition of 72 gb and then you can format it like you want. I hope this has helped you.

Greetings

---

### Post by elmosgot on 2007-03-19
I almost forgot you need to have a small non software raid partition of around 100 mb to mount as /boot partition.

---

