---
title: "Accidentally Installed Ubuntu 14.04 on top of Windows 7"
date: 2014-05-01
forum: Installation &amp; Upgrades
---

### Post by nick108 on 2014-05-01
So I was upgrading to 14.04 from 11.04 which I was dual booting with Windows 7. I wasn't paying attention and the new Ubuntu got installed over my Windows 7 partition as well. Does anyone know of a way that I can recover that data? After reading some other post it looks like I won't be able to recover anything since Ubuntu went on top of the Window's partition but I was hoping I was wrong because I had some relatively important information on there that I was hoping to recover.

---

### Post by TheFu on 2014-05-01
Just restore from the backup that you made prior to the installation.
If you don't have a backup - well - life will be much more difficult.
1 - stop using that HDD - pull it out!
2 - make a mirror copy of the original HDD to work on - use ddrescue for this
3 - use something like **testrec** to scan the partitions for data. This will be painful. You'll see.

Backups are much less trouble and much less costly.  I had a scare today myself - a disk controller went bad, but thankfully all the data on the HDDs was/is fine. It was just a short-term storage location - usually just a few days of videos, so losing it wouldn't have been the end of the world.  I'll swap in a new disk controller this weekend during a maintenance period.

---

### Post by fantab on 2014-05-01
Like TheFu suggests stop using the HDD immediately. If you don't have access to another computer then only boot with Live Ubuntu DVD/USB.
If Ubuntu was installed on the HDD then it will have overwritten some of the data. So 100% recovery may not be possible.
You can try one of the following Data/Partition recovery tools (there are plenty more but look for a tool that can load from bootable CD/DVD/USB ):[URL="http://www.minitool-partitionrecovery.com/"]
[http://www.minitool-partitionrecovery.com/](http://www.minitool-partitionrecovery.com/)
[/URL][http://www.easeus.com/partition-recovery/](http://www.easeus.com/partition-recovery/)
Some of the best data/partition recovery tools for windows may not be freeware, so be ready to pay if need be. Your data your choice.

You can also try **Testdisk** and **Photrec** to recover your data from the HDD from Linux for free.
[URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL][http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by sammiev on 2014-05-01
If you have your data backup then likely faster to reinstall and if you have a full backup then you have it made.

---

### Post by nick108 on 2014-05-02
Thanks for all of the responses. I do have a back-up but it isn't completely up to date so it doesn't have everything. But anything I may have lost isn't very important just more annoying than anything. I have a bunch of photos that are backed up different places so I will have to get everything together. But I am running Testdisk right now so we will see what comes of it.

---

### Post by Mark Phelps on 2014-05-02
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

