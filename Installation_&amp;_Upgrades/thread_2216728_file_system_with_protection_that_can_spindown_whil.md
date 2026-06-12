---
title: "file system with protection that can spindown while not used"
date: 2014-04-13
forum: Installation &amp; Upgrades
---

### Post by shahar2 on 2014-04-13
[COLOR=#000000][FONT=Arial]
hi,

i am looking for a file system that i can use, that can withstand a single drive fail, but can also spin down the drives while they are not used(the usage is not for system as i have a 4th system drive).
 i did a test with MD raid 5(ext4 on top), and even though nothing was accessing it, it kept 4-5 IO/s to all the drives. 
the spin-down is for power savings, and heat(3 drives in a small case). 
will zfs raid 5 work ?

thanks.[/FONT][/COLOR]

---

