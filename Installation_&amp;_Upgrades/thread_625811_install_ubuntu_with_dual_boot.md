---
title: "install ubuntu with dual boot"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by siongz on 2007-11-28
hi im trying to install ubuntu  on my laptop with existing windows XP on it.... however i do not wish to erase the ntfs partition... 

ive installed ubuntu before using the guided method but it ended up erasing my windows partition...
so can anyone guide me how to do it? starting from the partition setup?? how do i do it manually?

im stuck at the  point where i created a new partition in my free space... where i use it as ext3
but where do i mount it on??? "/home"? '/boot"?

---

### Post by kellemes on 2007-11-28
Startingpoint..
[https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo]("https://help.ubuntu.com/community/WindowsDualBoot?action=show&redirect=WindowsDualBootHowTo")

---

### Post by siongz on 2007-11-28
but im running windows xp home and i wish to load it on my d drive... which i think refers to the "free space" so any idea how to do it? thx in advance...!!!

---

### Post by aysiu on 2007-11-28
Don't use the "free space" option. That will attempt to resize your existing Windows partition and make a new partition out of the free space the resize allowed.

If you already have predefined free spaec (the entire D drive), go with the manual option, format the D drive as Ext3 and mount it as /

---

