---
title: "Grub2 install problem with RAID0"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by mike1122 on 2011-11-17
noobe here... it appears I cannot install Grub2 using RAID0 so I'm trying to figure the next best solution. I would like to have the dual boot option, and preserve my files.
 
Specs:
- Two 320gb SATA HD
- Vista32
- Intel Raid controller card
- Ext 500gb HD
 
Was thinking maybe I should just buy another hard drive and set it up in some non-RAID0 configuation, or possibly re-installing everything on my current hard drives using RAID1. Thanks!

---

### Post by darkod on 2011-11-17
Are you using the standard desktop cd? For raid installs you need to use the alternate install cd.

On the other hand, if you already have the system installed and only grub2 is missing, you can add it like explained here (make sure you read carefully and find the section about adding grub2 with the Live CD):
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Or you can repeat the installation with the alternate cd.

---

### Post by mike1122 on 2011-11-30
delete and start new post

---

