---
title: "unallocated partition / not continguous"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by Chrissie on 2008-07-16
Hi all,

This is my gparted screenshot.
I'd like to use the big unallocated space for Ubuntu which is in sda4 but it won't let me neither move nor resize neither of them (neither unallocated nor sda4).
Windows is on sda2 and windows recovery on sda1.
I'm running gparted from a knoppix cd.

Any help welcome!
Thanks
Chrissie

---

### Post by Pumalite on 2008-07-16
You already have 4 primary partitions. Delete /swap and make an extended partition in the unallocated space. Within that make a /swap partition and leave the rest formatted ext3 for a separate /home for Ubuntu. I'd use Gparted Live CD
Backup everything before you start.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Chrissie on 2008-07-16
Thanks Pumalite, I'll try this and post my results/pbms.

---

### Post by Chrissie on 2008-07-17
Pumalite you're the best !!

Followed your instructions. Everything works fine.
Sincere thank yous.

Chrissie

---

### Post by Pumalite on 2008-07-17
You are welcome. Good luck!

---

