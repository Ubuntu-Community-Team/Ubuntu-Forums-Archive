---
title: "Problem with partitions"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by bosmanos on 2008-11-15
Hi guys, Im new with Ubuntu but I like it=). There is one problem tho. When I installed Ubuntu I made partitions, and somehow my /home partition now is /boot partition. 

The question is, how can I make it /home without formatting? 

Best reg.

---

### Post by taurus on 2008-11-15
Open terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

