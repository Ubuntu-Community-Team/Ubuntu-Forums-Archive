---
title: "Installing Ubunutu with XP partition"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by Sicilianmandolin on 2007-02-12
I've been using a variety of Windows platforms for years and have recently decided that it's time to expand my horizons. I'm not a big fan of Macs, so I thought I'd go ahead and give Ubuntu a try. My primary motivation in installing Ubuntu is experience; I hope to become a network/system administrator someday and I know the experience will help me become more well-rounded, and many servers run Linux-based platforms.

I want to partition my HDD. Windows XP already occupies a great deal of space; I have only about 40 GB left, and I want to dedicate this to Ubuntu. I came across this website: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm) (does it look reliable?) which details the partitioning and installation process. The problem is that I already have another partition reserved for my Windows XP recovery files, and I'm under the impression I can only have 4 (primary?) partitions on one drive. Is having a total of 2 partitions already on my drive going to create a problem? I wouldn't think so, but I want to double check because I do not have a means of backing up my files.

My drive is 141 GB formatted and, as I said, I have about 40 GB free space. 512 RAM. How should I divide the partitions? Lots of questions, I know.

Thanks a lot!

---

### Post by dcstar on 2007-02-13
> **Sicilianmandolin said:**
> 
.........
My drive is 141 GB formatted and, as I said, I have about 40 GB free space. 512 RAM. How should I divide the partitions? Lots of questions, I know.

Thanks a lot!

40GB is more than enough for Ubuntu, but I would recommend a 20GB Ubuntu partition and a 20GB FAT32 partition for sharing/transferring files between the two systems (if required).

A FAT32 partition will be able to be safely written to by XP and Ubuntu, where the NTFS partition may have some potential for problems.

Set up the 20GB FAT32 partition in Windows, and then let the Ubuntu installer take the remainder of the disk for itself.

---

### Post by Sicilianmandolin on 2007-02-13
> **dcstar said:**
> 40GB is more than enough for Ubuntu, but I would recommend a 20GB Ubuntu partition and a 20GB FAT32 partition for sharing/transferring files between the two systems (if required).

A FAT32 partition will be able to be safely written to by XP and Ubuntu, where the NTFS partition may have some potential for problems.

Set up the 20GB FAT32 partition in Windows, and then let the Ubuntu installer take the remainder of the disk for itself.

That makes sense, but when I run compmgmt.msc and select "Disk Management" there seems to be no way of partitioning the remaining space. Is there another method I could go about doing this in Windows or am I missing something?

Thanks.

---

### Post by Sicilianmandolin on 2007-02-13
A little bump. Hope ya's don't mind.

---

### Post by mikewhatever on 2007-02-13
Hi Sicilianmandolin,
I've also used Herman's site you linked to, and I think it is one of the best. Having two primary partitions in place, you can only create two more primary ones. Those can be Ubuntu root and Ubuntu swap. If you need more then two, make them all extended/logical as shown in the guide, or make one more primary and the rest extended.
I am not sure why you need to partition the empty space for Ubuntu from Windows, hope you know what you're doing. I used the installation CD tool and Herman's instructions and would recommend those.

Good Luck with the installation.

---

### Post by Sicilianmandolin on 2007-02-13
> **mikewhatever said:**
> Hi Sicilianmandolin,
I've also used Herman's site you linked to, and I think it is one of the best. Having two primary partitions in place, you can only create two more primary ones. Those can be Ubuntu root and Ubuntu swap. If you need more then two, make them all extended/logical as shown in the guide, or make one more primary and the rest extended.
I am not sure why you need to partition the empty space for Ubuntu from Windows, hope you know what you're doing. I used the installation CD tool and Herman's instructions and would recommend those.

Good Luck with the installation.

Thanks for all your help, people. That makes perfect sense. :)

---

