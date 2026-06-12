---
title: "grub rescue"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by Anoop Jose on 2012-10-30
Hi,

I am using a Lenovo Ideapad Z520. its has got a  HDD of 640. It was pre loaded with Windows 7 Home premium. Initially i installed Ubuntu ultimate 3.0 along with windows 7 using approximately 150 GB. since i found its difficult to use i installed Ubuntu 12.04LTS over that and reduced the space to 100GB. Even after that system was functioning properly and i upgraded the Ubuntu 12.04LTS to GNOME 3. And i used the windows partition manager to use the free 50 GB. after that when i restarted the system an error comes stating that 'PARTITION NOT FOUND' 'GRUB RESCUE' .

When i tried to reinstall the Ubuntu its doesnt show any of my partition. hence i didnt do it again. i dnt have a windows rescue CD. Now i boot from Live usb. What am i supposed to do now? I am a beginner in Ubuntu. i have a preloaded recovery partition in HDD but i am afraid of using it because all my data are saved in Home folder of Windows. Pls advice me what to do next. Is it possible to save both operating system without reinstalling both?

---

### Post by dino99 on 2012-10-30
oops, erased per darkod comment

---

### Post by Anoop Jose on 2012-10-30
Thanks dino.

but it ddnt wokout. when i tried gparted it says no partitions found
pls see attachment .. also m a beginner with ubuntu

---

### Post by darkod on 2012-10-30
Dino, that command doesn't work like that from live mode. Please be careful and don't give wrong advice. It's not the first time.

Anoop, it seems the windows partition manager messed up the partition table. You have to be very careful when changing partitions.

Boot the ubuntu cd in live mode, open terminal and post the output of:
sudo parted -l (small L)

Lets see what that gives you.

---

### Post by Anoop Jose on 2012-10-30
Thanks darkod
this is how it comes

---

### Post by darkod on 2012-10-30
This is only a usb stick, it can't see the hdd at all, any partitions on it.

You might be able to restore the partition table with testdisk. It's best to have a backup before running it but now you can't make any backup since the partition table is messed up.

The only idea I have is testdisk. Maybe someone else will have another idea.

You can use testdisk from live mode. The details how to run it are here:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

After you do the Deeper Search it's best to write down the detected partitions and then try to figure out which is which. Testdisk can locate older partitions that you deleted on purpose, not, just the ones you want to restore. That's why it's important to select the correct partitions.

---

### Post by Anoop Jose on 2012-10-30
hi,

after downloading testdisk where should i extract the files to?
i tried home folder but later m nt able to load testdisk from terminal

---

### Post by oldfred on 2012-10-30
If using testdisk to backup files (or any other software) you need another drive, flash drive or device with enough room to back up all your data.

Since the error message was partition outside of disk and you use Windows to make a partition after Ubuntu, you may have to common bug in Windows partition tools that do not set last partition or extended partition correctly. Testdisk also sometimes does the same thing.

I might try fixparts.

Fixparts - Repair broken partition tables (not overlapping issues) 
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by darkod on 2012-10-30
> **Anoop Jose said:**
> hi,

after downloading testdisk where should i extract the files to?
i tried home folder but later m nt able to load testdisk from terminal

It doesn't matter where you extract them, as long as you remember where they are. For example, if you extract in your home folder (in live mode), the testdisk folder created will be something like:
~/testdisk-XXXXX. Just so there is no confusion, the ~ symbol replaces Home. If I remember correctly the executable of testdisk was in the folder linux and is called testdisk_static. So the full path would be something like:
~/testdisk-XXXX/linux/testdisk_static

But oldfred might have a point, fixparts might solve this better and easier than testdisk. Give that a shot first.

---

### Post by Anoop Jose on 2012-10-31
hi,
i am thankfull to all of you. with your help i could solve my problem without loosing any data :)

I tried with fixparts as u advised. and i could print all partitions except the one in which i installed ubuntu. i changed the boot loader to windows partition and exited from there.

after that also i was not able to load os normally. so i tried to install Ubuntu again and i was able to see all partitons and the one in which i installed ubuntu before has shown as freespace. hence i reinstalled ubuntu and now both the OS are functioning normally

---

### Post by oldfred on 2012-10-31
Glad that worked and you have working system.

Best to use Windows tools for Windows or just shrinking Windows and use Linux tools for Linux.

---

