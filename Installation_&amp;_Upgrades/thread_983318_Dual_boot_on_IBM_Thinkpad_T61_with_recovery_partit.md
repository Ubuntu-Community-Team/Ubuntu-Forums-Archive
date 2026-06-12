---
title: "Dual boot on IBM Thinkpad T61 with recovery partition"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Yankees9920 on 2008-11-15
I currently have a IBM/Lenovo Thinkpad T61 laptop with a 140gb hd. I have never installed linux before and I am looking to dual boot with XP. The laptop has a hidden recovery partition which has a pre-installation environment for recovery. In addition, that partition has the image for me to reinstall the XP OS.  Therefore I want to leave this unharmed, and have it still be able to be accessed with a dual boot setup. I am also looking to have a partition that is shared with both XP and Ubuntu(an I heard I could use NTFS which I think I would prefer).

-It is my understanding that I first want to do a clean install of XP since it is a mess right now.
-After that I think I have to set the partitions, but I am not exactly sure how to set this up. Would I have 1 for the recovery partition, one for XP, one for Linux, one for Linux swap, and one partition for shared data (NTFS or FAT?) I am not sure what order to make these partitions or what way I have to set each up.
-In order to not mess up the MBR I have to install grub to the same partition that the Linux OS is installed?

Is this all or am I missing anything else?
Again, I have never done this before, and step by step instructions would be the most helpful.

Also how can I simply make a backup of the MBR in case I mess any of this up, so I will no screw up that recovery partition.

---

### Post by cariboo on 2008-11-15
I would suggest, that you get your XP installation working properly first, whether you reinstall or just fix it is up to you. If you elect to fix XP defrag it at least twice and backup any important data you have. 

After you are satisfied with XP use the LiveCD to install Ubuntu, when you get to the partitioning step, allow it to resize your Windows partition, I would suggest you have approximately 20Gb of space to install Ubuntu. 

Linux does not use the same type of file system as Windows, so it can't share a partition. Linux can use almost any type of partition you can think of, so you will be able to access your Windows partition, but Windows will not be able to access your Ubuntu partition.

Have fun installing Ubuntu.

Jim

---

### Post by Yankees9920 on 2008-11-15
I was under the impression that I could make a FAT32 partition and mount it in Linux and both OSs would be able to access that information, whether it be documents, videos, or music. Is that correct?

---

