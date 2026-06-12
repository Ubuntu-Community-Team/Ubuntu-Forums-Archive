---
title: "Need more space for ubuntu"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by jafarnhh on 2013-03-23
Hello guys!

it was a long time ago when i used ubuntu (last time was maybe when 6.04 came out >p) and recently i've decided to give it a try again so i installed ubuntu 12.04 LTS with wubi but that gave me only 30gb and now when i fell in love with it i want more space is there any way to do that....
any help would be greatly appreciated :D

---

### Post by oldos2er on 2013-03-23
30 GB hard disk space is the upper limit for Wubi; you'd need to create one or more partitions for Ubuntu if you want something larger.

---

### Post by bcbc on 2013-03-23
Although it's possible to go higher I wouldn't recommend it. With Wubi all your data is stored in a single file, and if it gets corrupted you could lose everything. This doesn't happen to everyone, but it happens enough that I think Wubi should come [with a warning]("https://bugs.launchpad.net/wubi/+bug/1078959").

In any case, you can review these:
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[https://help.ubuntu.com/community/ResizeWubiDisk](https://help.ubuntu.com/community/ResizeWubiDisk)
[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

---

### Post by jafarnhh on 2013-03-23
thx for the answer guys i'll see what i can do :D

---

