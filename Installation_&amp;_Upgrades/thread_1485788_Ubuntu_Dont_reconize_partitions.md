---
title: "Ubuntu Dont reconize partitions"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by true_friend on 2010-05-17
HI
I am trying to install Ubuntu LTS 10.04 on an IBM Lenovo T61 Thinkpad notebook with Windows 7 preinstalled on it. There were two hard drives one 30 GB and other almost 110 GB which (the second one) I resized in three partitions with the help of Windows 7 disk management. Now when I try to install Ubuntu, the partition manager doesn't recognize the newly created partitions it only shows 2 partitions C:\ and old 100+ GB D:\. I had created a separate partition for Ubuntu also but I can't see it so can't install Ubuntu on it, I can't resize the visible partition because it is divided into three actually and I have data on each of three.
Any ideas to enable Ubuntu to see these partitions?
Regards

---

### Post by darkod on 2010-05-17
1. You don't create partitions in advance for ubuntu, especially not from windows. It will be ntfs and ubuntu doesn't install on ntfs. Create partitions during the install process.

2. When you say it can't see the partition you planned to use, are you talking about the Manual Partitioning method? If you have 4 primary partitions on the 100GB hdd, you install options will be limited.

I suggest: Boot win7 and delete the partition you created for ubuntu. Then boot ubuntu in live mode and in terminal execute:

sudo fdisk -l (small L)

Post the result. And give us some explanation where you want installed, even better using linux terms like /dev/sda, /dev/sda1, etc. C: and D: don't mean anything, it can be a whole hdd, only a partition, etc.

---

### Post by true_friend on 2010-05-18
Thanks for reply. I usually create a partition from Windows and then format it through linux installer, but this time partition is not visible.
I could use that command to get results but I am posting some screen shots: first 2 of Ubuntu installer, 3rd of Gparted and 4th from Windows 7 Disk management.
[IMG]http://lh6.ggpht.com/_OXuiTKOTjv0/S_JsONi7tAI/AAAAAAAABdE/EIJ4Z2EE3y8/s400/Screenshot.png[/IMG]
[IMG]http://lh6.ggpht.com/_OXuiTKOTjv0/S_JsObFQVRI/AAAAAAAABdI/znENk6VKq8Q/s400/Screenshot-1.png[/IMG]
[IMG]http://lh6.ggpht.com/_OXuiTKOTjv0/S_JsOeGE6oI/AAAAAAAABdM/lLZQ4SWC970/s400/Screenshot-2.png[/IMG]
[IMG]http://lh5.ggpht.com/_OXuiTKOTjv0/S_JsOoCoAnI/AAAAAAAABdQ/Qtgsu0SGcFY/s400/Screenshot-3.png[/IMG]
As it can be seen that Gparted is recongnizing 2 partitions but ubuntu installer cannot. I can mount those two partitions also but still 2 are invisible. Windows disk management doesn't tell about primary or logical type of partitions.
Regards

---

### Post by darkod on 2010-05-18
I can't read the windows screenshot but maybe your disk is using GPT because I can see 5 partitions there. Otherwise, primary or logical are marked with different colors but these partitions are marked the same color.
I don't have any experience with GPT and can't help you if that the problem.

You can definitely tell if you run in terminal in live mode:

sudo fdisk -l

It will say if GPT is used.

---

### Post by true_friend on 2010-05-18
Here is the output of the command sudo fdisk -l
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfbe7fbe7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           1         992+  42  SFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *           1          13      102400   42  SFS
Partition 2 does not end on cylinder boundary.
/dev/sda3              13        3825    30617600   42  SFS
Partition 3 does not end on cylinder boundary.
/dev/sda4            3825       19458   125568856   42  SFS
Partition 4 does not end on cylinder boundary.
Regards

---

### Post by darkod on 2010-05-18
OK, it's not GPT partition table but it's SFS partitions you got there. That is also some newer type of filesystem which works well on windows but I'm not sure how linux can recognize it.

I'm not familiar with it, sorry. Maybe google seach can help it, or someone else.

---

