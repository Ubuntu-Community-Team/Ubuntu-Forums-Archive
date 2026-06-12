---
title: "Xubuntu 7.10 installation along with win XP"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by plastichero on 2008-07-05
I'm going to install Xubuntu 7.10 on my machine[256 RAM, 1.7 GHz Celeron]. XP is already running on D:. 

If I select a seperate Linux etx3 partition as the root partition and provide another 512MB swap partition, will there be any damage on the other FAT32 drives? bcoz, I'm running winXP in the same machine and I want both of them. I dont want to loose all my data in other drives.I only want Xubuntu to be installed on the etx3 partition leaving other partitons uharmed.

Another thing, what should be the minimum space given to the root partition? I'm giving 3.5GB ... is it enough for the installation?

Let me know please.

---

### Post by dominiquec on 2008-07-05
As always, back up data first. :-)

A reasonable amount to reserve for Ubuntu's root would be 5GB.  7GB would be even better, just so you don't have to resize if you need more. This is assuming you place your /home directory elsewhere.  /home will carry the bulk of your data.  (Even if you offload /home data to FAT32 drives, still a good idea to leave ample space.)

There should be no damage to your FAT partitions (but again, backup just in case).  Ubuntu can resize them if needed.

---

### Post by plastichero on 2008-07-05
Thanx. I've to manage another HDD to backup my 60GB data. :(

---

