---
title: "Problem partitioning drive"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by T08E on 2010-01-28
Hey, I am trying to install ubuntu 9.10 alongside windows on my laptop's harddrive. When I was going through the procedure it gave me the option of a guided partition of my harddrive... however there was an error. At this stage I unplugged my external harddrive because it's sometimess a bit dodgy and restarted the installation process. However everytime since that I have tried to install, it only gives me the option of erasing the entire disk or specifying the partitions manually, which I have no idea to do. Any help would be appreciated.

---

### Post by darkod on 2010-01-28
If you are only getting those options, most likely you already have 4 partitions on your hdd, and that's the maximum. To confirm this, boot the live desktop and in terminal execute:
sudo fdisk -l

Copy the result here.

---

### Post by T08E on 2010-01-28
sudo 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f61df32

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         702     5632000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         702        9729    72515168+   7  HPFS/NTFS

---

### Post by darkod on 2010-01-28
Well, you have only two partitions which is good, but the first one is unknown system which doesn't sound good. If it can't get properly recognized maybe that's the reason ubuntu is not offering some of the install options.
Also, when you got the error the first time, did it happen after the actual install started, or during the 7 screen you were going through? If the actual installation was interrupted, who knows in what state it left the hdd.

---

### Post by T08E on 2010-01-28
Well it was still on the options screens, I just clicked quit when it didn't have the guided option so it shouldn't have started installing.

---

### Post by darkod on 2010-01-28
No, it shouldn't. How about booting windows and trying some disk checks on that first partition / or the whole disk? Maybe that will sort out some errors.

---

### Post by T08E on 2010-01-29
Yep, that sorted it... Ubuntu is installed now and all seems to be running swimmingly, thank you very much for your help!

---

