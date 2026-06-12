---
title: "How to upgrade Ubuntu 9.04 if software source no longer available"
date: 2011-05-23
forum: Installation &amp; Upgrades
---

### Post by davidonlaptop on 2011-05-23
Hey I just got this PC with Ubuntu 9.04 Jaunty and cannot upgrade it.

When I go into Software Sources, and choose reload it fails with error 404.

How can I upgrade / install new software?

---

### Post by Hedgehog1 on 2011-05-23
This method works for upgrading your system to your choice of 10.04, 10.10 or 11.04 Ubuntu. It will require that you have a separate '/home' partition for your data.

Download the ISO and us it to create a LiveCD or LiveUSB of your chooses version of Ubuntu.

Begin an install from the LiveCD/LiveUSB and eventually get to the **Disk Space Allocation** screen.  

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE OR A REINSTALL, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by davidonlaptop on 2011-05-24
@Hedgehog1: Thanks!

---

