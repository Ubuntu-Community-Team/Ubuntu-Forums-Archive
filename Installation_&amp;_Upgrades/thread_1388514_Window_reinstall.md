---
title: "Window reinstall"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by emma00 on 2010-01-23
Hi,

I have dual boot Ubuntu with window xp,but uses Ubuntu all the time.The problem is the same bugging problem of virus in my window so i want to reinstall my window without any data loss for my Ubuntu so anyone knows how to do it or any good link to it.

Thanku

---

### Post by terrapin893 on 2010-01-23
Are they on the same partition?

---

### Post by feelshift on 2010-01-23
Did you installed Ubuntu using Wubi or on a separate partition?

---

### Post by emma00 on 2010-01-23
No they are not on the same partition i installed it through Ubuntu live cd

---

### Post by feelshift on 2010-01-23
If they are on separate partitions you could format the Windows partition and do a fresh install. This will leave the Ubuntu partition intact, but it will delete GRUB (there are many tutorial on how to restore it thought)
Make sure to backup important data before you proceed with managing partitions.

---

### Post by emma00 on 2010-01-24
ok thanku i will give it a try:KS

---

### Post by darkod on 2010-01-24
Reinstalling grub:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Don't forget, if you have 9.04 you need a 9.04 cd and to follow the procedure for 9.04. If you have 9.10 as clean install (not upgrade from 9.04), you need to use 9.10 cd and follow the procedure for 9.10.

---

### Post by emma00 on 2010-01-31
thanks :D

---

