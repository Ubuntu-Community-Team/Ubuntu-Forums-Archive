---
title: "Netbook remix dual boot install"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by Lafon on 2010-09-05
Hi one of my friends and I wanted to install Ubuntu Netbook Remix but we wanted to install it alongside his previous OS. When we load the installer we get to the choose how much space that you want ubuntu to have. However the OS that is already on there (Windows 7 Starter) seems to be taking up all the space (We only got the option to erase the previous OS to install ubuntu). When we go to the partition editor it says that Windows 7 (loader) has 32 Gb of the hard drive, Windows Vista (loader) has 149.6 Gb, and Unallocated 4 Gb or so (I could be mistaken, I'm doing this from memory) of disk space. So any idea how we could do this without losing any of the data on the OS that is already installed?
Thanks

---

### Post by zvacet on 2010-09-06
I know that you can resize partition with Windows7 but I dont know if that is possible with Vista.If it is then resize your Vista partition and on unallocated space install Ubutu.Format ubunt upartition as ext4 and mount point / root.

---

### Post by Lafon on 2010-09-13
Sorry for the long delay in replying. I had to prepare for school.
Ok now for it. The Windows 7 Starter edition seems to be treated as Vista. And it does not let me edit any of the partitions (one of them is a recovery partition for 7). So any idea what I can do?
Thanks

---

### Post by garvinrick4 on 2010-09-13
The Vista part is how Linux reads the recovery partition. If you look again it will be about 12 gig or so for Vista part and large portion for Windows 7 loader. If you choose side by side at install it will split the drive in half and give half to 7 and half to you. Other that that you have to read up on gparted and make partition for Ubuntu. Start by running defrag a couple of times of Windows. Leave the recovery partition alone it is OK, it will take care of itself.
Gparted sites
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[URL="http://www.dedoimedo.com/computers/gparted.htmlhttps://help.ubuntu.com/community"]
[/URL]

---

