---
title: "Plz help me partitioning :("
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by tehjord on 2007-06-17
All right I wanna try the ubuntu and Im lost. 
What kind of partition should I have and what size ? I have about 10gb of space for unbuntu 
thx for your precious hlep

---

### Post by Pumalite on 2007-06-17
> **tehjord said:**
> All right I wanna try the ubuntu and Im lost. 
What kind of partition should I have and what size ? I have about 10gb of space for unbuntu 
thx for your precious hlep

Are you dual Booting?. If so, defrag your Windblows several times after erasing all yor temp files and getting rid of anything you don't need. Then use Gparted to create one big partition with the rest. format ext3. Install Ubuntu with the option: Guided>Use largest Free Space Available. Ubuntu will take care of the rest. If you are using just Ubuntu in one entire hard drive, then it's easier: use Gparted and make one BIG partition of the hard drive formatted ext3. Then install and choose Guided>Use Entire Disk.If you are dual booting with Vista, then is different: You have to partition FROM Vista if they are going to reside in the same hard drive.

Hope it helps.

Good luck.

---

### Post by tehjord on 2007-06-17
Thx for the fast reply, seems like something that could work :D 
Ima try that out

---

