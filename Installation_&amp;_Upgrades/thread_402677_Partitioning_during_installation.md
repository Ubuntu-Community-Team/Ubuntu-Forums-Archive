---
title: "Partitioning during installation"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by ricc on 2007-04-06
Hi All,

I am new to Ubuntu. I have earlier used FC and Open SuSE. I wanted to try out Ubuntu. So I downloaded Edgy Eft and have installed it.

I am not sure if I am correct or not. But I think there is a bug in the partitioning and formatting tool.

I wanted to load XP then Ubuntu and then FC6 each having a 20G partition of their own and a common 20 GB partition to be shared. Harddisk size is 80Gig. First I created only a Primary Partition and loaded XP. Next I loaded Ubuntu with 100MB /boot partition ( also a primary partition) and 20Gig Logical partition inside an Extended Partition. The total size of the extended partition is the rest of the drive.

But whenever I commit the changes, it just shrinks the Extended partition to the size of the logical partition allocated to it.

This happens even if I try to load FC6 first and Ubuntu later. The result is that the extended partition gets resized to total of FC6 +Ubuntu. 

This happens even if I do a manual partition using fdisk from the virtual console. The formatter just shrinks the total extended partition.:( 

Has anyone ever come across this?. I think it is has certainly got to do with the way Ubuntu treats the disk partitions and it shall be corrected. Any input will be highly appreciated. So that  if I am doing something wrong, I will correct myself. :) 

Thanks,

ricc.

---

### Post by LowRadio on 2007-04-06
Try doing your partitioning with the Gparted live CD
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

