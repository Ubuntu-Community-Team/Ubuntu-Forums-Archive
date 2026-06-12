---
title: "LAMP server with RAID1 for video streaming looking for optimal partition"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by erasmo.da.rotterdam on 2007-03-27
Hi!!
I am going to install a LAMP server for multimedia purpose.
The server will have to do a lot of video streaming.

Xeon 5140 2.33GHz/4MB 1333FSB
4GB FB 667MHz Memory (4x1GB dual rank DIMMs)
250GB SATA2 Universal (7,200 rpm) 3.5 inch Hard Drive (2x250GB)

RAID1 is needed

I need some suggestions on partitions.
I was thinking to create on each hard disk
[LIST=1]
[*]10GB root
[*]8GB swap
[*]232GB home
[/LIST]

10GB for root seems to be a lot but considering all the log activities should be right.
Looking at the swap FAQ [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
> If you have a disk big enough, just put 2*n Mb swap.
 where n is the number of RAM Mb

Have you any suggestions?

---

