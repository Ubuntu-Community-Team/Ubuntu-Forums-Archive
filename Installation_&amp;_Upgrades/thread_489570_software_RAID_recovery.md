---
title: "software RAID recovery"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by tecie1980 on 2007-07-01
How do I recover my RAID information in the even of a total operating system loss?
I have 2 software RAIDs running on my box here:
the boot drives are a RAID1 that I built out using the Alternate install disc, and I've linked together 4 drives together into a RAID5 for storage.  
My original plan was to do this via the hardware, but it turned out that I had purchased a mb with windows only raid controllers.  
 I'm doing regular backups of my personal, critical files on the /home , /etc  filesystems, but if I try to do an upgrade and it all goes wrong, I need a backout plan to recover the RAID5, and if possible the RAID1. the raid5 was built using md. 
Where is the information stored? How do I go about pulling it into a fresh install?

Thanks in advance!

---

### Post by CheShA on 2007-07-01
This was something I always wondered about.  I'm using nVidia fakeraid, I installed ubuntu using dmraid to read the fakeraid array, but I always wondered how one would go about doing rebuilds, etc.  I still have windows installed for various  legacy purposes so it wouldn't be a problem for me yet since I could rebuild under windows but it's just  another thing that's preventing me from giving up the dirty MS habit.

---

### Post by Pumalite on 2007-07-01
Raids are a waste of time and a bad idea, especially in Linux. Raid 0: minimal performance improvement. Raid 1: Double the danger of lost data.

---

### Post by CheShA on 2007-07-01
> **Pumalite said:**
> Raid 1: Double the danger of lost data.

eh?

---

