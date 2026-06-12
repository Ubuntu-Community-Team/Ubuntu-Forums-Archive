---
title: "dualbooting media center/ubuntus"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by scriv316 on 2006-11-10
Hey guys

I'm new to linux but I really want to start learning this os so I don't have to rely on Windows too much. I was doing an install and after it was done doing the partioning it was asking me about to mount the partitions. I've never installed linux before so I really don't want to mess up the windows installation. Unfortunately I don't have exactly what it says on the screen but heres what its typically going to be setup for

Partition 1: windows xp
Partition 2: system restore for xp
partition 3: swap file
partition 4: ubuntu

If this isn't enough info I could probably get what exactly it says but its just wanting the mounting options for these partitions

Thanks

---

### Post by darcmaniak on 2006-11-10
This may help, this is how I have it:

1 20 gb NTFS ( XP) 
2 50 gb NTFS
3 30 gb Extended
4 1gb Logical Linux Swap ( 2 times what your Ram is)
5 9 gb Logical Ext 3 ( this will be your / or root)
6 10 gb Logical Ext 3 ( this will be your home)

---

