---
title: "How to get a correct logical LVM2 pv partitioning on Ubuntu 14.04.2"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by bachlubaki on 2015-05-04
Hello,
 I am in the process of knowledge of Linux-Ubuntu 14.04.2.

 I just reinstalled it with a live CD, but the partitioning is not logical, because for a 500 GB HD, I only have 255 MB I used GParted, but I still can not redo properly partitioning.
 
Could you help me put order into my system?

Below, the link of my partitioning table

[http://www.partage-fichiers.com/upload/gsbc9my9/Capture_du_2015-05-02_18_06_20.png](http://www.partage-fichiers.com/upload/gsbc9my9/Capture_du_2015-05-02_18_06_20.png)
 
Thank you in advance

---

### Post by ubfan1 on 2015-05-04
The first 255M partition is your boot partition, which is  necessary.  The rest of the disk is in a logical volume, so you have no problem.

---

### Post by bachlubaki on 2015-05-04
Thanks a lot my brother for your quick anwer. 

But this 255M partition appears in the launch pad Unity as my main hard disk and it's impossible to organize it by creating, importing or downloading files and directories because the short volume. Previously, what appeared as main disk had biggest place (around 49 Gb). Also, I didn't succed to modify any partition and files system because it's blocked.

1) So how could I first replace the main volume in the launch pad Unity ? 
2) How to enlarge or to shorten easily partition blocs ?
3) Do 255M partition boot is suffiscient for the system or it gonna be better to enlarge it ? How to proceed ? I found some troubles with my Grub2.

Thank you so much for your help.

---

### Post by ubfan1 on 2015-05-04
I do not use logical volumes myself.  Do you really need to use one (for encryption for instance)?  They just add more unnecessary complication for most people.  I do not know how a system running off a logical volume would appear on the unity launch bar.  I would expect it to be there just like the mounted /boot partition, but you sound like that's not the case.  Without the logical volume, you just intstall to partitions like /dev/sda? and you  don't need a separate /boot partition, so size problems are not present.  If you really need the logical volume, 255M for the boot is barely enough to update the kernel, you have no room at all for any of your own files, and in any case, you are not expected to store any of your files there anyway.  Your files typically get put into /home/username.   Since 30-50G is generous for an Ubuntu root partition, you could have two 50G partitions for use as root (one for testing new releases, one to use for daily work).  The rest of the disk may be made into a big data partition which you use for your files, and which you can remount on a new root when you update, and which should not be deleted when you do reinstall a system.  If you decide on keeping /boot, maybe 500M or 1G would give you some additional room for kernel updates, but you still will need to keep deleting the old ones yourself (see the many threads on "no room in /boot".  There are many threads in this forum on partitioning recommendations, but I'm not sure how many are applicable to logical volumes.

---

