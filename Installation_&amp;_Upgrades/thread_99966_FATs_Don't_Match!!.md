---
title: "FATs Don't Match!?!"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by wyvis on 2005-12-06
First time installer of Ubuntu.  I downloaded and burned the 5.10 CD and booted up the default installer.

I have 2 existing drives as follows:
 - SATA drive with 1 NTFS (main WinXP) partition & lots of free space
 - IDE drive with 2 existing FAT partitions

I created / and swap partitions manually on the SATA drive through the Partitioner and removed the mount points for the FAT partitions.  Once I selected "Next>" I got this error message:
    FATs don't match!

along with some text about running scandisk and retrying. :confused: 

I can't find anything in the forums about this error message...can anyone help?

Thanks.

---

### Post by audax321 on 2005-12-06
I get an error message when I install saying something about there being uncorrected errors with my FAT32 drive and to go back to the menu to correct these, but nothing is wrong. Although the file system on my FAT32 drive is completely screwy ... in Linux I apparantly have 8 GB free on it and under Windows I have 24.8. I just formatted the partition and replaced it with ReiserFS.

I'd try booting into Windows and running Scan Disk like the message said (I think you right click on My Computer, Properties, then it's in one of the tabs but may not be called Scan Disk anymore). See if it corrects any errors. My drive was so messed up, Scan Disk crashed!  Also are you using FAT16 or FAT32?  I recommend FAT32 if you can reformat those drives and have FAT16 right now. And if you are ditching Windows all together, you might want to format the FAT32 drives to a Linux file format... FAT drives tend to get very defragmented and corrupt after some time if you don't take care of them.

---

### Post by wyvis on 2005-12-07
Thanks for the reply.

The FAT partitions are FAT32 (created in XP) and I wanted to share some of the info on the disks (e.g. dev libraries, etc) between WinXP and Linux.  I don't really want to reformat them if I can avoid it -- too much hassle.

I ran the disk scans from XP and no errors were reported.  Do you think I can safely ignore the messages and carry on?

---

### Post by audax321 on 2005-12-07
Unfortunately, if you can't reformat, there's isn't much other choice. Also putting another file system on there will lead to read/write problems between Windows and Linux, so FAT32 is the only option you have here. The good thing is that the paritions are on another drive, so Ubuntu didn't mess them up or anything. Just make sure to reboot into Windows every so often and Scan Disk/Defragment and it should be fine. Pay particular attention to the free space reported in Windows and Linux. My drive in Linux said 8 GB, in Windows said 24.8  GB, and after formatting I have 124.9 GB :rolleyes:  Since I don't use Windows much, I just converted to ReiserFS and am going to use ReiserGUI to transfer files to Windows if needed (also have a small 10 GB FAT32 just in case). From my experience System > Administration > Disks tends to show the same amount of free space as Windows, but Nautilus doesn't for some reason.

Good luck.

---

### Post by ssalman on 2005-12-07
I had the same error when I installed Ubuntu, and I installed it twice and had the same error, I Ignored it both times and continued with the installation and it worked fine. At the time I had Windows XP partition (NTFS), Windows recovery partition (FAT32), SUSE 10.0 (ReiserFS), Linux Swap partition, and an empty partition I prepared for Ubuntu (ReiserFS).
   
  All my partitions were unharmed, although I had a small trouble with starting SUSE from Grub, but that is a different story!
   
  If your are confident about not having any partition/disk errors (I was) ignore the warning and continue with the installation, but be careful anyway. It is always best if you could backup your important stuff.

---

### Post by bwog on 2005-12-07
Are you aware that you can copy files on an ext3 partition from windows with explore2fs?

Because you can read NTFS files from ubuntu you dont need a FAT partition for sharing except in special cases like auto-synchronization.

---

