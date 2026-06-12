---
title: "Advice on dual-boot partitions for a college laptop"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by jermf810 on 2008-07-21
I just got a new Dell XPS M1330 and I'm looking to dual-boot vista x64 and ubuntu hardy x64. 

I already use 32-bit windows XP and 64-bit ubuntu hardy on my desktop, dual boot. I have four partitions - an NTFS one for XP, an ext3 one for ubuntu,a swap, and an ext3 one for all of my data. I use the ext3 crack for windows to view my data files on the ext3 partitions from XP.

My laptop has 4 gigs of ram, so I'm looking to use 64 bit vista (xp x64 I read is buggy) and ubuntu. The problem is that I don't know what filesystem to make my data partition. I honestly have no clue which OS I will be using more. I imagine that for recreation I will use ubuntu and for school I will use vista (my school has some windows only software, and I prefer MS Office over Open Office. I also need iTunes for an iPhone). Therefore, I imagine I will be using both OS's about equally.

If I use an NTFS data partition, it will need formatting and managing from windows, and if I find myself using Ubuntu more then it will be pointless. If I use an ext3 data partition, will it work in Vista x64? Also windows handles those cracked ext3 drives oddly, making recycled and lost+found folders in ubuntu that are just a nuisance if I'm switching back and forth.

Or maybe all of my assumptions are wrong and ubuntu will be fine in college, or maybe vista will be all I use. Should I virtualize instead? Any advice will be appreciated!

---

### Post by zvacet on 2008-07-22
Ubuntu should read/write on NTFS by default.If you want to format as ext3 you will need [this.]("http://www.fs-driver.org/")

---

