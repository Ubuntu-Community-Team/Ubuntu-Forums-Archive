---
title: "Guidance on MythTV partition /var/lib"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by md2020 on 2007-06-18
My first linux install. Very impressed so far with all the info and help available for Ubuntu. I searched the forums, MythTV.org, etc. but didn't seem to see anything addressing my question.

I am creating a MythTV install. (Ubuntu 7.0.4) Following the awesome instructions here:
[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop?highlight=%28mythtv%29](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop?highlight=%28mythtv%29)

I have 2 harddrives. HD1, HD2 for the sake of this post. Going to use HD1 (20 GB, the smaller of the two) for the root (/) and swap partitions. Using HD2 for MythTV storage. Following the instructions, it indicates to create a XFS partition and mount at **/var/lib**. So I created the XFS partition on HD2 with mount point **/var/lib**. No problem. 

After install, I was a little surprised at all the other stuff in **/var/lib**. So what I thought was going to be purely used for MythTV recordings is obviously sharing the space with other stuff located in **/var/lib**. 

My questions are these:
1. Does the other stuff under /var/lib benefit from the XFS partitioning and should remain there?

2. Do I leave my install as is, or do I repartition and have the XFS partition mount at **/var/lib/mythtv** instead? (thereby giving myself more recording space on HD2)

Thanks in advance for your guidance.

---

