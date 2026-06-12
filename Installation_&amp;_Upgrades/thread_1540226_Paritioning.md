---
title: "Paritioning"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Sanix on 2010-07-27
Hi,
Hope this is the correct forum for that.

I have on sda1 Windows 7 installed
On sda2 I have 3 sub partions (extended partition)
with Ubuntu 10.04 and a swap space
and one partition for /usr/local

Now I tried to move space from sda2 to sda1 using gparted. It's not possible. I deallocated space from sda2 which works. But I cannot merge it with sda2. Is that, because sda2 is an extended partition? Is there a work around without killing all partitions and lose my complete data?

---

### Post by dabl on 2010-07-27
I think you have to use the Win 7 partitioning tool, not Linux/Gparted.

---

### Post by Sanix on 2010-07-27
Same with that tool. I think it's something because it's an extended partition or something?

---

### Post by lechien73 on 2010-07-27
Hi,

I presume you're using GParted Live? Since you obviously can't resize a mounted partition.

You have to reduce both the size of the partitions within the extended partition, and then the extended partition itself. For example, if sda1 is Windows, sda2 is extended and sda3 contains Ubuntu, you would need to:
[LIST=1]
[*]Reduce the size of sda3
[*]Reduce the size of sda2
[*]Increase the size of sda1
[/LIST]

It can all be done through the GParted GUI, just make sure that you have the extended partition highlighted when you do step 2.

---

### Post by dabl on 2010-07-27
It might be the case that you can use Gparted to reduce (first) the /dev/sda3 logical partition, then (second) the sda2 extended partition, then stop and reboot and start Win 7.

Then you might be able to use the Win 7 tool to increase that partition.

I have read that Win 7 does not like to be resized by an external partitioning tool, but is OK being resized with its own partitioning tool.  I haven't tried it myself.

---

