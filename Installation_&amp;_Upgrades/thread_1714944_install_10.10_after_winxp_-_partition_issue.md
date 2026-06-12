---
title: "install 10.10 after winxp - partition issue"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by omgurindanger on 2011-03-26
i have two partition for my winxp
so now when i boot using ubuntu 10.10 CD (failed to boot with USB, has already submitted the details), and goes into manual partition...I can only create two more partition, the rest will become unused space.

i tried to go to winxp, and create the partition first, then change it in ubuntu, but my winxp only allows me to create logical partition.

please advice.

newbie here, might not provide enough info for you guys

---

### Post by coffeecat on 2011-03-26
The mbr partition table only allows a maximum four partitions. You must be trying to create primary partitions for Ubuntu. Instead of one primary partition you can create an extended partition which is used a container for as many logical partitions as you might need. I don't know what you mean by winxp only allowing you to create logical partitions. Don't use the WinXP Disk Management tool. It is not sophisticated enough for what you need.

When you boot up the Ubuntu CD, choose 'try Ubuntu', not 'install Ubuntu' and that will take you to the live desktop. Before you start the installer (icon on the desktop), open System > Administration > Gparted. You'll see that your two Windows partitions are primary. Create one large extended partition in the available space, and then as many logical partitions as you need in the extended. Linux will happily boot from a logical partition which windows cannot do.

See here for more:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by Hedgehog1 on 2011-03-26
omgurindanger,

Here is an example of a drive with 3 windows partitions, and an extended partition with 3 Ubuntu partitions inside the extended partition:

[IMG]http://img853.imageshack.us/img853/841/10diskutility2.png[/IMG]

***The Hedge***

:KS

---

### Post by omgurindanger on 2011-03-28
thanks coffeecat

---

### Post by omgurindanger on 2011-03-28
nicely done Hedgedog1

---

