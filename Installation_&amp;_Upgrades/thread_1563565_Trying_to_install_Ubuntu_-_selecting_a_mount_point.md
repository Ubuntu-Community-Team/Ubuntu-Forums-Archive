---
title: "Trying to install Ubuntu - selecting a mount point?"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by komatsu on 2010-08-29
I am trying to install Ubuntu on one partition on my hard drive. There is 100GB free.


I've tried formatting with ext3 with a 2000mb swap file but it still does not work.

I think I am not selecting a "mount point" - how do I do this?

---

### Post by e79 on 2010-08-29
If you are doing a simple manual partitioning on a drive where NO other OS reside, simply type **/** as your mount point for your ext3 partition (also don't forget to flag the partition as 'bootable').

If you want to dual boot a Ubuntu/Windows set up, you can begin read more about it here :

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Hope this helps

---

### Post by komatsu on 2010-08-29
ok e79 thanks for that.

When formatting the partitions on the hdd do I make them primary or logical?

(remember I am trying to up a dual boot system with Vista and Ubuntu)

---

### Post by KdotJ on 2010-08-29
> **komatsu said:**
> ok e79 thanks for that.

When formatting the partitions on the hdd do I make them primary or logical?

(remember I am trying to up a dual boot system with Vista and Ubuntu)

I think it's up to you, though bare in mind you can only have five primary partitions on one hard disk (Well, I think it's five, may be four). I usually go with primary...

---

