---
title: "Restoring partitions"
date: 2015-06-07
forum: Installation &amp; Upgrades
---

### Post by infyniti on 2015-06-07
Hi all, I am installing ubuntu 14 on my pc which already has vista on it. I used the wubi.exe to install and on reboot got the "no root file system is defined" error.  Using gparted i tried to delete the extended partitions and allocate the space the main partition. By doing that i messed up my main partition and now i get "no bootable device". I am attaching gparted screenshot. Any advise on how to restore main partition. 

Thanks
Anant

[ATTACH=CONFIG]262480[/ATTACH]

---

### Post by sandyd on 2015-06-07
> **infyniti said:**
> Hi all, I am installing ubuntu 14 on my pc which already has vista on it. I used the wubi.exe to install and on reboot got the "no root file system is defined" error.  Using gparted i tried to delete the extended partitions and allocate the space the main partition. By doing that i messed up my main partition and now i get "no bootable device". I am attaching gparted screenshot. Any advise on how to restore main partition. 

Thanks
Anant

[ATTACH=CONFIG]262480[/ATTACH]
Before I begin to tell you how to recover data, a bit of info about Wuby is needed:
Wubi installs a copy of Ubuntu inside Windows as a disk image file. That being said, using gparted will have no effect on wubi since the Ubuntu installation is a file on a windows partition. That being said, the usage of Wubi is no longer encouraged as it has a few problems, mainly with resizing the image file and non-support of UEFI-based computers.

If you want to recover data, you can do so if you have not written anything to the deleted partitions. Instructions can be found [here]("https://help.ubuntu.com/community/DataRecovery#Lost_Partition") for how to do it with a LiveCD.

---

### Post by Mark Phelps on 2015-06-08
From the screenshot, it appears you trashed both the Windows boot partition (the small one at the beginning) and the larger Windows OS partition.

While Testdisk MAY be able to recover those partitions, since they were Windows filesystem partitions, you are likely to have better luck with Windows data recovery apps.

If you have access to a working Windows PC, then download and install Active@Partition Recovery on that PC, connect your drive to it -- and see if it can recovery the former Windows partitions for you.

---

### Post by infyniti on 2015-06-09
Thank you very much for the info, but i am not able to recover the data. Ended up in formatting the disk. 

Anant

---

