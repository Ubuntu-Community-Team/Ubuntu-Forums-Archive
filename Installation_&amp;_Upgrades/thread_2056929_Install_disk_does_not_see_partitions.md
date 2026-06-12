---
title: "Install disk does not see partitions"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by Tranas on 2012-09-12
Installing 12.04 as dual boot with XP. When the install screen gets to the spot where you should be able to partition free space there are no partitions visible. No error codes or messages - just nothing displayed, including the XP partitions. Partitions were created prior to install using Parted Magic - which does see the partitions. Guidance would be appreciated.

---

### Post by oldfred on 2012-09-12
Post this:

sudo fdisk -lu

and a screenshot from gparted. 

I have had gparted not even show a drive when my XP needed chkdsk. My XP still booted, but after running chkdsk in Windows gparted showed the entire drive and XP booted a bit faster.

---

