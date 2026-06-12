---
title: "Second Ubuntu partition fails"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by AkiraBergman on 2009-12-18
I have recently installed Ubuntu-9.10 AMD64 on my new machine with ASUS P7P55D-E mobo, i5 CPU, 4G RAM and 1TB Samsung HD, and it is running good.

I tried to install Ubuntu 8-10 AMD64 as the second OS on the same HD but the guided partitioning failed with the error;

"An error occurred while writing the changes to the storage devices. The size operation has been aborted."

I changed the proposed partition percentages with the sliding scale in the guided partitioning, but I don't think this is the reason for the error.

Previously I had a 32b system and had no problems with multiple partitions.

Should I use a special partitioning tool to create a new partition and somehow install the 2nd OS in that? Or is this error with the guided installation easy to get around?

---

### Post by oldfred on 2009-12-19
I think we need to see your partitions. either this command or a screen shot of gparted.

sudo fdisk -l   (-l is an el not 1 or i)

---

### Post by AkiraBergman on 2009-12-19
Thanks for the reply. This partition was made recently at the installation of 9.10 on the new HD;

nuri@nuri:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000405ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120124   964895998+  83  Linux
/dev/sda2          120125      121601    11864002+   5  Extended
/dev/sda5          120125      121601    11863971   82  Linux swap / Solaris

---

### Post by oldfred on 2009-12-19
I do not know why what you did, did not work? I would try downloading the gparted liveCD and see if you can set up the partitions in advance and the use a manual install to choose the previously set up partitions.

With as much space as you have and multiple installs you should consider additional partitions. Many recommend a separate /home to make it easy to reinstall as you can reuse your home without reformatting and still reformat root for a new clean install. I just did that after three years of home inside my install but also created a separate /data for almost all my data and link that data into my home. I now do not see much use for a separate /home as it is so small that it is easy to back up. Another advantage of a separate data partition is that you can use the same data with multiple installs where home cannot be used unless you use different user names and still may not be useable with some systems as the are not compatible. A data partition ln -s into your system is compatible.

---

### Post by AkiraBergman on 2009-12-19
Thanks oldFred. 

I tried installing 9.10 after installing 8.10 and it worked. It seems the Ubuntu-8.10 amd64 live-disc does not like the proposed partition altered, although it gives you that option by a sliding scale to change the percentages. I did not try altering the percentages offered by the 9.10 disc, since it offered a 50%-50% partition that I wanted. The 8.10 disc offers about 5%-95% partition in the favor of the second installation and it does not like change.

Later on I realized that I could have probably used the gparted disc to partition the original 9.10 installation without overwriting it.

Thank you also for the additional wisdom about the /home and /data directories. I am happy enough with the current solution. I may consider having common directories later. These days installation is pretty easy and I don't have much data at the moment.

All the best.

---

