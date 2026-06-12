---
title: "extended partition and dual boot"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by jwxie on 2011-03-12
I have Ubuntu 10.10 installed on my Lenovo ThinkPad Edge 14 already, and I am trying to install Windows XP on the same hard drive. I never had the experience where I exceed the maximum numbers of partitions...

Upon searching, I was told that I need to create an extended partition.

Current disk I have
boot 499MB ext4, 8.2GB ext4(/), 1.0GB Swap,  and 9.0 GB (/home)
I also have an unknown extended 9.0GB along with 41GB Free space...

This extended 9.0GB said "Usage: Container for Logical Partitions...) I don't remember when did I create this.....

1. My question is, can I delete this partition?

2. If I were to re-install Ubuntu, when I create an extended partition, do I create boot, swap, home, and / within the extended partition?

Thanks.

---

### Post by srs5694 on 2011-03-12
First, some background. There are three types of partitions on the Master Boot Record (MBR) partitioning scheme used on most PCs' hard disks:


[list]
[*]**Primary** -- These partitions are the most basic type. They're limited in number to four. Some OSes, such as Windows, must boot from a primary partition.
[*]**Extended** -- An extended partition is a special type of primary partition that's used as a placeholder for logical partitions, in order to get around the 4-primary-partition limit.
[*]**Logical** -- You can have an arbitrary number of logical partitions, but they must all reside inside a single extended partition. Linux can boot fine from a logical partition, but Windows can't.
[/list]


Thus, the premise of your question -- that you need to create an extended partition for Windows -- is incorrect. Instead, you must create a *primary* partition for Windows. You should *not* delete your current extended partition, since doing so will also delete the logical partitions that currently hold at least part of Linux.

It's unclear from your description precisely how your partitions are laid out and therefore how you should proceed. If you need more detailed advice, please type the following commands:

```

sudo fdisk -lu
df -h

```

Post the output here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility. Alternatively, post a screen shot of the GParted utility's main screen. That will tell us precisely how your disk is currently laid out and how much of each partition you're using. You should also say how much disk space you want to give to Windows and how much space you want for shared data or data exchange. (Writing to the Windows C: volume from Linux is inadvisable except on a limited or emergency basis, so if you expect to exchange or share files, using a separate partition for that purpose is the best course of action.)

---

