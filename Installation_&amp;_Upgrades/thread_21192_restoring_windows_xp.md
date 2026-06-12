---
title: "restoring windows xp"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by Razor on 2005-03-20
Hi, I recently installed ubuntu and I was trying to resize my ntfs file system hard drive (100 gigs) to about 60 gigs and install ubuntu, but that didnt work.. So I recreated the partition drive. Then i thought I might as well forget about it, and I shut down. I restarted and it said "Could not load operating system", so I just went ahead and redid my partitions. It never formatted, so my data must still be there. I set the partitions to the start so I know I will have "some" data missing. But i would like to retrieve the data that I need for my windows XP reinstallation. I only wanted to try out ubuntu. Plz help :)



God I want my xp back now :(
I totally forgot about all the things i had on there that took me a long time to get..
:(

---

### Post by Buffalo Soldier on 2005-03-20
I'm assuming what you were trying to do was reduce the size of your NTFS partition by deleting the original partition and then recreating a smaller partition?

If I'm not mistaken, deleting a partition and recreating a new one basically destroys any data in the old partition. Even without formating.

To resize a partition you need a proper software or application for that. It's more than deleting and creating a smaller partition.

There are many software for that, I think Partition Magic can handle that. But what I did was I boot using a LiveCD and run QParted to reduce my NTFS partition.

---

