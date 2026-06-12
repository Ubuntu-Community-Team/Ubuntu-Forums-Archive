---
title: "Blitzed my kubuntu install..."
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by jnorthr on 2007-06-30
and i had it all working perfectly!!! Dunno what happened when i tried to use apt-get update which erased all kde files (?!) so i figured i'd try the full ubuntu install on 256MB kit w/20GB disk. 

I have read elsewhere that it's better to make separate partitions to /, /home/swap,/usr but i can only make 4 partitions during the install. It seems to balk when i try to set up the 5th partition. 
Partition 1 is FAT32 Windows; 2 is linux swap; 3 is /home and 4 is root / and so how can i get /usr created ?
I've kept my /home partition and swap file intact (which was built under kubuntu) and i'm hoping the files on those partitions are still there as i did a lot of work to install java, eclipse etc.

Any ideas ?

---

### Post by tpg on 2007-06-30
It sounds like you're trying to create 5 primary partitions: you can't do that. There is a limit of 4 primary partitions per hard drive. To create more partitions, you must create 1 extended partition (which counts as one of your primary partitions), inside which you can create as many logical partitions as you want. I'm not sure how to do this in the installer, but that's the theory.

---

