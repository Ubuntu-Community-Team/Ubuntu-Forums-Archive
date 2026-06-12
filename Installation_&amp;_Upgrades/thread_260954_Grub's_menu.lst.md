---
title: "Grub's menu.lst"
date: 2006-09-19
forum: Installation &amp; Upgrades
---

### Post by CapnCook on 2006-09-19
I am runnig Dapper Drake 6.06

Everytime there is a kernel update the grubs menu.lst file is updated also. The problem is this, the hd1 argument (root (hd1,0)) is rewriten as root (hd2,0). I have to either remember to change it back to hd1,0 or use the live cd and mount the boot partition and make the change. 

My system has 2 250 meg sata drives and for some reason even when I do a fresh install the samething happens. I also have 2 IDE DVD Roms and 1 IDE zip drive in the system.

I am dual booting XP with XP installed on the 1st sata drive hd0 and Ubuntu installed on the 2nd sata drive hd1. Grub is installed on the boot partiton of the 2nd drive hd1 and I use XP's loader to load grub.

Any help would be appreciated.

---

### Post by lorre on 2006-09-19
Check out 
[this]("http://www.ubuntuforums.org/showpost.php?p=1507562&postcount=11")
post, I had the same problem..

---

### Post by CapnCook on 2006-09-19
Thanks I'll check it out.

---

