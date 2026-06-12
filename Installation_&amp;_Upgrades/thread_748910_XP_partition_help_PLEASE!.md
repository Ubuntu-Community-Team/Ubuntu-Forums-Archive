---
title: "XP partition help PLEASE!"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by zackymcharvest on 2008-04-07
I have a Toshiba Satellite A-105. i have a 60gb HDD and i want to install Ubuntu dual boot with xp. I have XP up and running and i have 31.73gb left. but when I go to install Ubuntu and the partition manager pops up it only allows for a 32gb install...all i want is 10gb install with 1gb swap. also the HDD has a 251mb partition that it says is (unknown partition) i don't know what that is and i don't wanna mess with it. i have no unallocated space and would like to know how to get unallocated space in XP to use the partitioner in the ubuntu install to "Use the largest continues free space" 
                     Any help would be greatly appreciated!!

---

### Post by Partyboi2 on 2008-04-07
When you have booted the live cd and have reached the desktop open up partition editor (System>Admin>Partition Editor) and use the resize feature to shrink down xp. Then close partition editor and start the install and when you get to the partitioning part choose manual and setup a 10gig partition for /root and a 1 gig swap.

---

### Post by zackymcharvest on 2008-04-07
i have created roughly 10gb unallocated space can i use the use largest free space button in the install? and will it do the swap for me(im not good enough to use the manual feature) and when i hit apply to create the unallocated space it says to backup valuable info... will it damage my info on the windows side... i did a defrag before entering the live cd

---

