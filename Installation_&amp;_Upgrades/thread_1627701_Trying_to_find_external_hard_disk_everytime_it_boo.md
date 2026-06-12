---
title: "Trying to find external hard disk everytime it boots"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by jit.sd on 2010-11-21
Hey , 

I recently upgraded to 10.04 and during the upgrade process my external hard disk was plugged in. Now everytime I boot up ubuntu informs me that sdb1 is missing and wont boot up till I ask it to "skip" waiting for it. Also I am assuming because of this I have trouble mounting any other external hard disk other than my own, keeps giving some sort of unable to mount problem. 

Any ideas how I can fix this ? 

Thanks

---

### Post by Naitsirhc Hsem on 2010-11-21
as root, backup and edit /etc/fstab

sudo cp /etc/fstab /etc/fstab.old
sudo gedit /etc/fstab

if you see a line with sdb1 in there you can delete it.
if the disks are mounted via UUID in fstab, you can see which is which in 
system>administration>disk utility

for more info, search for a guide on editing /etc/fstab

---

### Post by jit.sd on 2010-11-21
Excellent , that fixed it, thank you so much.

---

