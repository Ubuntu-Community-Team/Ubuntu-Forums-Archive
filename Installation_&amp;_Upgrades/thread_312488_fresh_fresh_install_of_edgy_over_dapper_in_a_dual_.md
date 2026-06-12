---
title: "fresh fresh install of edgy over dapper in a dual boot pc"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by valid.user.name on 2006-12-04
I have a dual-boot PC with XP and Ubuntu Dapper. Boot loader is GRUB, ofcourse. I recently had some problems with Dapper after installing KDE desktop (don't ask why KDE :mrgreen: ), and many things just seem to go wrong: my themes don't work, many applications just refuse to install. Uninstalling of KDE didn't help either.
So I planned to do a fresh install with Edgy over Dapper. I'm not going to resize, move or do anything similar with my partitions, just reformat those which belong to Dapper and do the install of Edgy on them. I don't have many files, backup is not a problem. So I'm wondering, will the new GRUB recognize my XP? I'm not very familiar with MBR...

I didn't get the new Edgy yet, and it's not completely sure I will get it. But I hope.:cool: But I'm planning to do the do the new, fresh, install in every case. So my question is: are the things I asked for new Edgy install over Ubuntu, same for Dapper (over Dapper:D )

---

### Post by LLRNR on 2006-12-04
valid.user.name,

If you want to do a fresh install of Edgy on a dual boot system, keeping XP, it shouldn't be a problem. Just make sure **not** to touch the partition that you want to keep... You didn't say in your post if you have two separate hard drives for XP and Ubuntu, but it doesn't matter anyway as long as you know which partition you shouldn't touch. 

When you do the reinstall, you will be of course prompted to choose on which partition you want to install. Just pay attention on the filesystems you already have and don't touch the NTFS one ;)

You can take a look at Aysiu's guide on [partitioning](http://www.psychocats.net/ubuntu/partitioning), also it would be good if you would consider making a separate /home partition - you will find it useful at a future reinstall, when you will most probably want to keep your existing settings and personal stuff. It's covered in the "Partitioning guide" in the link above.

HTH,

LLRNR

---

