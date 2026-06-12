---
title: "Problem installing netbook remix and number of partitions."
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by Zerstorer on 2010-06-17
Hi all,

I'm an old user of Ubuntu/Linux but have stumbled across my first major problem in years. I just can't get my head around it.

I own a Asus Eee Pc 1005HA it has roughly 160gb and is currently running WinXP. I'm trying to install the latest Netbook remix 10.04 onto the machine as a dual boot option.

I've loaded the iso onto a usb drive and everything works perfectly. The problem is during installation. I can't work out how to set up the partitions for a dual boot option. Below is the current configuration on the system.

/DEV/SDA
/DEV/SDA1/NTFS           77375MB Windows XP Partition
/DEV/SDA2/NTFS           77366MB Free space
/DEV/SDA3/FAT32           5247MB Recovery Partition (I believe)
/DEV/SDA4/                       49MB  Some sort of swap partition for Windows XP?

I would like to use the free space as my Ubuntu installation. Can anyone advise me on the best way to install this without affecting my WinXP system. 

Any help much appreciated.

---

### Post by darkod on 2010-06-17
If you want to use the space taken by /dev/sda2 you need to use the Manual Partitioning option and delete that partition, and in it's place create as LOGICAL partitions for / and swap, or also for separate /home if you plan to have one.

---

### Post by gadolinio on 2010-06-17
> **darkod said:**
> If you want to use the space taken by /dev/sda2 you need to use the Manual Partitioning option and delete that partition, and in it's place create as LOGICAL partitions for / and swap, or also for separate /home if you plan to have one.
Right. Delete the free partition (make sure you dont erase another one of the list! :P ), and then create a new one. Tell the installer to use filesystem ext3 or ext4, and to use that partition for "/"; set the partition's size keeping in mind to leave some space for the swap (I have something like 8GiB). Then create another one, and in filesystem pick "linux-swap".

---

### Post by Zerstorer on 2010-06-20
Thanks guys, going to give this a go right now. Hopefully I won't loose my WinXp.

---

