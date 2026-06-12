---
title: "Installing Ubuntu 11.10 after failing"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by spa21788 on 2012-04-22
Hello,

I carelessly deleted my ubuntu partition (80gb approx) on my laptop, which is dual booted for ubuntu 10 and windows 7, because I deleted the partition my boot loader doesn't work.

 I put ubuntu 11.10 on my memory stick and attempted an install, I was warned that if I didn't have 2.4gb on each partition the installion might fail, which it did, now when I try to re-install it brings me to the partition table, which I cannot understand :( 

 I was hoping someone could explain the steps I need to take to fix my stupid mistake! 

 Attached are some screens to hopefully help in the process.

Thanks in advance.

---

### Post by jerrrys on 2012-04-22
You may be able to save the existing install with TestDisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by spa21788 on 2012-04-22
I would but I can't get an operating system to run, except ubuntu from my stick, how can I run the executable?

---

### Post by darkod on 2012-04-22
> **spa21788 said:**
> I would but I can't get an operating system to run, except ubuntu from my stick, how can I run the executable?

Testdisk can be run in ubuntu live mode.

---

### Post by LinuxFan999 on 2012-04-22
> **spa21788 said:**
> Hello,

I carelessly deleted my ubuntu partition (80gb approx) on my laptop, which is dual booted for ubuntu 10 and windows 7, because I deleted the partition my boot loader doesn't work.

 I put ubuntu 11.10 on my memory stick and attempted an install, I was warned that if I didn't have 2.4gb on each partition the installion might fail, which it did, now when I try to re-install it brings me to the partition table, which I cannot understand :( 

 I was hoping someone could explain the steps I need to take to fix my stupid mistake! 

 Attached are some screens to hopefully help in the process.

Thanks in advance.
Shrink the large NTFS partition (/dev/sda3) untill there is enough room to expand one of the ext4 partitions to the size required for Ubuntu, then use it (the ext4 partition you chose to expand) as a / (root) partition.

---

