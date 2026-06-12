---
title: "ext3 on win or ntfs on ubuntu?"
date: 2010-08-11
forum: Installation &amp; Upgrades
---

### Post by molgan on 2010-08-11
I use dualboot win xp/ubuntu 10.04, where both systems are equally used.

I just bought a 2TB hdd that I will use on both OS's - which file system is preferable? (Primarily in sense of stability, but also performance.)

---

### Post by Fludizz on 2010-08-11
When considering ease of use, go for NTFS. Windows does not have ext3 support, you can get it working with third party tools but still it is not desirable. To keep it simple, use NTFS. Ubuntu knows very well how to handle NTFS filesystems and it doesn't make you jump through hoops to get it to work under windows.

---

### Post by dabl on 2010-08-11
> **Fludizz said:**
> When considering ease of use, go for NTFS. 


I must agree, but with a caveat:

"And don't forget to run Windows chkdsk on it regularly, and _every time_ there is an abnormal shutdown."   ;)

---

### Post by molgan on 2010-08-13
Alright, I'll stick with NTFS, thanks for the answers.

---

