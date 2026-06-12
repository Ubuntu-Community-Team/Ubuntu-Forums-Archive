---
title: "Problems installing Ubuntu Hardy with Dual Boot"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by jeremycollins on 2008-11-28
I am trying to dual boot Ubuntu Hardy with my Windows XP Home edition computer.  I chose the first option, guided partition, in the partition editor, but when I clicked on forward, it said Too Small Size.  What does this mean?  How might I fix this?  I didn't see a place to manipulate the space that will be available for Ubuntu, but it showed a 50/50 split between my WindowsXP partition and the new Ubuntu partition.  Thats 40GB each.  Why won't this install?  I would really appreciate any help that I can get! Thanks!

---

### Post by Partyboi2 on 2008-11-30
Try manually creating the partitions first using gparted. Boot the ubuntu live cd and go to System>Admin>Partition Editor) and resize your windows parttion down to the size you want. then with the new unallocated space make a ext3 partition and a /swap partition the swap should be about x2 the ammount of onboard ram, but would go more then 3 gig. So example for 40 gigs towards ubuntu would look like
38 gig ext3 partition 
2 gig /swap (1 gig of ram)
Then after these have been done start the installer and at the partitioning stage choose "manual" then edit the ext3 partition so that the mount point is set to / then  proceed with the installation.

---

