---
title: "how to make separate home folder on new install?"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by northwestuntu on 2010-05-03
im gonna do a fresh install of ubuntu 10.04 and want to make a separate partition for the home folder.

anyone know a UPDATED how to link or explain how that is done.

thanks

---

### Post by oldfred on 2010-05-03
Do you have an existing /home?

You have to do manual install. I prefer to create partitions in advance with gparted. I download a gparted live but you can use the version in the Ubuntu liveCD to create partitions.

I suggest 10-20GB for / (root), swap equal to RAM, and /home as the rest unless you plan on other installs or data directories. You can leave part of the drive unallocated if not sure but it is not always easy to move partitions around.

With manual install when you get to the partitions you select your root and right click to choose that it is / and choose what format ext3 or ext4 (or many others). The same with /home but if you have an existing /home you do NOT format it. It finds the swap on its own.

---

### Post by northwestuntu on 2010-05-03
> **oldfred said:**
> Do you have an existing /home?

You have to do manual install. I prefer to create partitions in advance with gparted. I download a gparted live but you can use the version in the Ubuntu liveCD to create partitions.

I suggest 10-20GB for / (root), swap equal to RAM, and /home as the rest unless you plan on other installs or data directories. You can leave part of the drive unallocated if not sure but it is not always easy to move partitions around.

With manual install when you get to the partitions you select your root and right click to choose that it is / and choose what format ext3 or ext4 (or many others). The same with /home but if you have an existing /home you do NOT format it. It finds the swap on its own.

no i don't have an existing /home.  this will be all new.  

does the gparted live have better setup for partitions?

---

### Post by oldfred on 2010-05-03
No not really. 

I just like to have several ways to boot my computer. I also have systemrescue, parted magic and several old versions of Ubuntu all on one USB as ISOs that I can boot. I stopped using CDs as every new system install I used a bunch since I wanted alternative/backup ways into computer. For either of my main systems I have not needed them. 
But experimenting with a 10 year old toshiba a year or two ago required a variety of boots/versions to finally figure out the correct settings and versions that worked.

---

