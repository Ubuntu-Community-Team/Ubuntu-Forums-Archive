---
title: "Should I use a swap partition or swapfile on Xubuntu 18.04"
date: 2018-05-14
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2018-05-14
I am trying to understand if I should use a swap partition or a swap file, when installing Xubuntu 18.04.  In the past I have always used a swap partition. One of the reasons I used a swap partition is because I have multiple OS partitions--one for xubuntu 16.04, one for xubuntu 17.04, one for xubuntu 18.04, one for kubuntu 18.04, etc.  I also have a data partition that can be accessed from any OS partition. To save disk space I have always used the same swap partition for all these different 0Ss.  I always made it twice the size of my RAM so now I have an 8GB swap partition.  

Now when I install xubuntu 18.04, it came up with a swap file of 507.4MB. That's a lot smaller than 8GB.  I have a number of questions:
1. Is that large enough?
2.  Will that swap file increase in size if more space is necessary?
3.  If I fill the disk so that the swap file can't grow, will the system hang, or does it have a graceful solution and keep running.
4.  I am short of mass memory space (SSD), so I don't want to waste any.

Please tell me the pros and cons of swap partitions vs swap file.  And also tell me how I can change from swap partition to swap file, and vice versa.

Any help much appreciated......

---

### Post by kerry_s on 2018-05-15
if you have swap partition it will automatically use it. ubuntu has switched to using a 2gb swap file in place of a partition.

why yours is only 500mb is strange.

---

### Post by vanadium on 2018-05-15
- In your scenario, where you share swap space between installs, you surely should go for a dedicated swap partition. You probably can also share a swap file between installs, but it will be more complicated.

- Swap files in linux (unfortunatelly) are not dynamically resized. However, an advantage remains that at any point, you can easily change its size as opposed to the size of a partition.

- As such, you cannot run into a scenario where the swap cannot anymore grow. If memory (including swap) is full, the system will start terminating processes, which may lead to crashes or hangs. The larger the available swap, the slimmer the chance that will ever happen.

You could probably do equally well with 5 or 6 GB of swap.

---

### Post by oldos2er on 2018-05-15
If you use hibernation, I believe it requires a swap partition, and other than that I don't think it matters much which you use. But as kerry_s said, if you already have a swap partition the Ubuntu installer will see and use it.

Whether your swap file is large enough depends on your system usage. Do you often see swap being used? Have you changed the default swappiness (60)?

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by Ralph L on 2018-05-20
Thank you to everybody who responded on this.  I chose to keep my shared swap partition, since that saves me disk space.  Because I installed the system originally with a swap file, I noticed that using a swap file results in a special entry for it in /etc/fstab.  I suppose this has to be set up manually if one adds a swap file after the original installation.

---

