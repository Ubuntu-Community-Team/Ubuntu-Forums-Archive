---
title: "Partitioning and sharing drives between ubuntu and windows"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by ktp.kti on 2012-09-11
I am installing both windows and ubuntu in a PC. From my previous experiences, I've learnt that the easiest way to share files between both OS' is by using drives common to both of them. In the past, I installed windows first, created partitions with windows and then installed ubuntu in the rest of the free space. Thereby, all the drives in windows (most likely to be NTFS) were available in ubuntu.

But will it work the other way around? Creating drives in Ubuntu and sharing with windows. 
 - What should be the file format for the drive (because the default of Ubuntu is ext4 which is not recognized by windows)? 
 - What should be the mount point for such a drive?
 - Will the drives created (after ubuntu installation) with gparted be recognized by windows?

PS: For some reason, when I used my older method recently, the drives created using windows installation CD (used only for partitioning without installing the windows OS) were not recognized by ubuntu. I presume that that happened because I did not proceed with a full windows OS installation before installing Ubuntu. Am I right?

---

### Post by Mark Phelps on 2012-09-11
While you CAN create an NTFS partition for installing Windows, the first thing you should do when you then go to install Windows in that partition is have the installer REFORMAT it.  This works better in the long run.

For sharing data, you should create an NTFS format partition with Gparted.  That will work out fine -- no special Windows formatting is needed for a data partition.

Also, if you install Windows second, it will overwrite the MBR and wipe out the GRUB code there.  You will then need to reinstall GRUB.

---

### Post by ktp.kti on 2012-09-11
Thanks a lot!

---

### Post by Bucky Ball on 2012-09-11
I would stick with the method you have been using. There have been a few changes which is perhaps why you are having problems mounting the NTFS data drives created with Windows.

I would go the regular route with one exception. Install Win on first drive/first primary partition, as per normal, but then, instead of creating your data drives, create one big extended partition with the remaining free space and then install Ubuntu on a logical drive inside that. You would have something, then, like this:

1/ Win (30Gb or the minimum you need)
2/ Boot the LiveCD and create an extended partition with the free space left on the rest of the disk;
3/ Ubuntu on a logical drive inside the extended (15Gb does me but store /home stuff elsewhere)
3/ swap on logical drive inside extended (2Gb fine)
4/ free space inside the extended partition (whatever's left)

Boot and make sure you can get into both OSs okay. 

Now, boot into Ubuntu, launch Gparted and create your NTFS storage partition(s) as logical drives using the free space left inside the extended partition.

Restart and boot into both OSs to make sure the new partitions are recognised.

There are twists, turns and variations to this, left to your discretion and needs, but above is a launchpad. You can add a separate /home partition or use symlinks in the /home directory inside / to link to directories on your NTFS data partition so the data can be shared. Whatever suits. Pays to sit with a beverage of your choice, a piece of paper and pencil and plan this. 

Also, you may need more than one partition for Win (because Win demands it be so). Be aware that four primary partitions is the limit on one physical drive. Thus the extended partition. Theoretically you can have as many logical drives inside there as your hardware can handle. 

So, three primary partitions and an extended with four logical drives inside is fine. 

Hope that helps and good luck ... ;)

---

### Post by oldfred on 2012-09-11
Do not use Windows to create the extra partitions. It may convert to dynamic partitions which then do not work with Linux.

Use Windows to install or shrink the Windows system partition, but then use gparted for everything else.

---

### Post by ktp.kti on 2012-09-11
Thanks again everyone! My special thanks to the detailed answer by Bucky Ball.

---

