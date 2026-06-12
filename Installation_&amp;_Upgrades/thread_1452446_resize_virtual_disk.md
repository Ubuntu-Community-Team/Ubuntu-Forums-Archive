---
title: "resize virtual disk"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by six616 on 2010-04-11
/ is almost used up, want to shift some spaces from /home to /, reduce /home from 15G to 10G at virtual disk,
created 10G of home.disk is fine, 
after cp, i copied 15G to home.disk,  
as i have expanded my /home recently, 10G should be quite enough, did i miss some options at cp command? 
(installed ubuntu 9.10 by wubi in winXp sp3)

cd  /host/Ubuntu/disks/
mv  home.disk  home.backup
sudo sh   wubi-add-virtual-disk  /home 10000
cp -r  home.backup  home.disk

---

