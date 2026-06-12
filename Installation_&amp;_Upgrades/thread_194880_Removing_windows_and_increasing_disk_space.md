---
title: "Removing windows and increasing disk space"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by double_mint on 2006-06-12
Hi All,

Now that I have installed Dapper and managed to get my printer working, I have finally been able to ditch windows.  What is the best way to remove Windows, and reclaim the disk space as part of Ubuntu?

Rod
(Almost Linux newbie)

---

### Post by aysiu on 2006-06-12
```
sudo aptitude update
sudo aptitude install gparted ntfsprogs gksu
gksudo gparted
``` Right-click the Windows partition and delete it. Right-click and create an Ext3 partition.

Then, go here:
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

