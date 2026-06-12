---
title: "Ubuntu Installation Help - Partitioning Hard Drive"
date: 2006-09-30
forum: Installation &amp; Upgrades
---

### Post by BrettJ on 2006-09-30
Hey all. I'm not exactly good when it comes to installing operating systems on my computer (Or rather, Laptop). Anyway, my laptop has recently had some problems running windows xp *cough*Don't go into regedit.exe and try to alter permissions*cough*. Anyway, I'm installind Ubuntu on a CD disk I found lying around (I burned the ISO onto a disk a while ago...Version 5.04). I am trying to install it, but my laptop's hard drive has one partition and I'm not sure what i should do (Bear in mind I dont wanna lose my data)

PS: Can Ubuntu view my files located on my windows partition

PSS: Can Ubuntu run apps for Windows, for instance Sony Vegas, Adobe Photoshop (Yes, I know, the Gimp... Still)

Thanks in advance

---

### Post by JGuru on 2006-09-30
Have 10 GB of unpartitioned space in your harddisk. While partitioning,
 choose the option **Use the largest continuous free space available**
 (Option 2). Ubuntu will partition the harddisk for you. Or you can also 
 manually partition the harddisk, allocate 8 GB for 'root' ('/') & 1.5 GB
 for 'swap'. Swap in Windows terms is called 'Virtual Memory'.
 Yes, you can access the Windows partitions in Ubuntu, you need to mount them.

---

### Post by marcelm on 2006-09-30
If you have valuable data, make a backup!

---

