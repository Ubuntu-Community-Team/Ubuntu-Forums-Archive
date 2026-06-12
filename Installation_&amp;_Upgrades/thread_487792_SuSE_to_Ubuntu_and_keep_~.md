---
title: "SuSE to Ubuntu and keep ~"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by linuxpimp on 2007-06-29
Hi all

I have a machne with SuSE 9.3 on it and a large ~ that will take me way to long to backup onto CD's (no DVD drive).

I want to install Ubuntu on the machine but keep my /home

Is this possible?

Thanks in advance

lp

---

### Post by stchman on 2007-06-29
> **linuxpimp said:**
> Hi all

I have a machne with SuSE 9.3 on it and a large ~ that will take me way to long to backup onto CD's (no DVD drive).

I want to install Ubuntu on the machine but keep my /home

Is this possible?

Thanks in advance

lp

Create a new ext3 partition on your hdd.  Copy everything over to the new partition.  Erase the partition that contains Suse (make it free space).  When you install Ubuntu tell it to use the free space.

Once it is installed you will need to mount that partition in your fstab file.

That should do it.

---

