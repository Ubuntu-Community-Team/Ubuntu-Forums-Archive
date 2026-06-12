---
title: "Recover accidentially formated hard drive"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by bhanuday-sharma on 2015-03-01
Hello everyone....
I am in serious trouble. I was using Ubuntu 12.04 on my laptop. It was having 3 partitions at that time. Out of these three, one was having ubuntu (40 GB) and other two was containing my files. There name was KNOWLEDGE (NTFS, size approx 40 GB) and ENTERTAIN (NTFS, Size approx 70 GB). One day when I was tring to update my ubuntu to 14.04 LTS, accidentially I selected 1st option during installation and  the whole hard drive get formated. After that, when I restarted my laptop I found only one partion (of 150 GB) in which ubuntu is installed. I want to recover all my data again because it contain information that really matters for me. Immediatly I stoped using my laptop. And tried TestDisk 6.14 by booting the PC on a USB bootable drive (ubuntu). Through deep scan in TestDisk what I found was that the "Knowledge" drive is showing files but "Entertain" does not. I want to recver the "entertain" drive especially. After deep scan the TestDisk says that the hard drive does not have enough space. So how to recover these drives? Is it possible to save recovery files on onther laptop by connecting my laptop to another laptop by a LAN wire? I haven't made any changeg to my laptop after that incident.[ATTACH=CONFIG]260345[/ATTACH][ATTACH=CONFIG]260346[/ATTACH][ATTACH=CONFIG]260347[/ATTACH]

---

### Post by Mark Phelps on 2015-03-01
Your best bet in recovering files from former Windows filesystems is using Windows data recovery apps.  You most likely will NOT be able to recovery the ENTERTAIN partition, so you should focus on recovering the files.

To do this, you will need to do the following:
1) Remove the hard drive from the laptop
2) Connect the hard drive to a working Windows PC
3) On the Windows PC, download and install a data recovery app.  A free one is "recuva".
4) Run the app in the deepest discovery mode and see what it finds
5) If it finds the files you want, recover them to the Windows PC or to an external USB drive or USB stick
6) IF it does not find the files you want, then try using RecoverMyFiles.  It is free to download and test to see what it finds.  If it finds the files you want, then you will need to go online and buy a license to do the actual recovery.

Good Luck

---

