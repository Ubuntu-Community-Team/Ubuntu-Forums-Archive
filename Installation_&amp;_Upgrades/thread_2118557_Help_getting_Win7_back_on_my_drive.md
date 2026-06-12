---
title: "Help getting Win7 back on my drive"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by morganpatrick on 2013-02-21
Hi, 

I could use some help with a partitioning issue. In short, I want to shrink my /home partition to make room for a Windows 7 installation, without getting disk errors like I was last time. Also I might want to convert a logical partition to a primary one.

My computer was Windows7 with 2 NTFS partitions: OS and data.

I used gparted to shrink data and add an Ubuntu partition, mounting NTFS data as /home.

Somehow in the process this rendered Win7 unbootable, and /home started to become unwritable with recurring disk errors.

So I wiped the whole drive and started fresh, with one Ubuntu root partition and one /home partition, both ext4.

Now I'm realizing I do still need Win7 on here. How to I resize my /home to make room for Win7 without corrupting the disk again?

One more thing: somehow /home ended up a logical partition, not a primary one. So I have sda1, ext4, mounted as /. then sda2 is extended, with one partition inside of it: sda5. I don't know if this matters, but if it does I need to know how to convert a logical partition to a primary one.

Thanks so much for your help.

---

### Post by Mark Phelps on 2013-02-21
> **morganpatrick said:**
> Hi, 

I could use some help with a partitioning issue. In short, I want to shrink my /home partition to make room for a Windows 7 installation, without getting disk errors like I was last time. Also I might want to convert a logical partition to a primary one.

My computer was Windows7 with 2 NTFS partitions: OS and data.

I used gparted to shrink data and add an Ubuntu partition, mounting NTFS data as /home.
BAD idea.  NTFS doesn't understand Linux filesystem permissions -- so, as you found out, this is likely to fail.  You need /Home to be a Linux filesystem, probably Ext4, although others will do.

> Somehow in the process this rendered Win7 unbootable, and /home started to become unwritable with recurring disk errors. First is due to messing with Win7 partitions using Gparted.  IF you're going to mess with those, you would do better doing it with the Win7 Disk Management utility.  It's less flexible than GParted, but it won't corrupt the boot loader.

> Now I'm realizing I do still need Win7 on here. How to I resize my /home to make room for Win7 without corrupting the disk again?
Presuming  /home is an Ext4 partition, right? If so, just boot from CD or USB and run Gparted to do this.

> One more thing: somehow /home ended up a logical partition, not a primary one. So I have sda1, ext4, mounted as /. then sda2 is extended, with one partition inside of it: sda5. I don't know if this matters, but if it does I need to know how to convert a logical partition to a primary one.
Don't think primary vs. logical is a problem in this case.

---

