---
title: "Installed UBUNTU in G: partition but all the data contained in G: was lost"
date: 2013-04-24
forum: Installation &amp; Upgrades
---

### Post by kamalbel on 2013-04-24
Hello there,

First I must say that I feel so stupid, and here is why.
I installed Ubuntu on a win7 machine in a different drive than C: - G: partition- and lost all the data contained in G:.
Tried to retrieve the data but it looks gone. another partition was wiped as well. 
When in ubuntu, disks and Gparted show the partitions and I tried to undo the changes, but without success. 
I should have known that installing ubuntu in the G; partition would wipe it clean.
Can anyone help me figure out how -if possible- to bring those partitions back either in linux on win7?

---

### Post by Mark Phelps on 2013-04-25
Any time you install to a partition, it's going to be overwritten -- guess that was not obvious?

If the partition contained a Windows filesystem, and you're willing to spend some money to get the files back ... read on ...

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by darkod on 2013-04-25
Before paying for solutions you can also try testdisk. You can use it from ubuntu live mode. In fact, it's best to use it from live mode because that way you are not booting from the disk in question. See if the deeper Search can find your previous partition. It can usually restore it back, even if some of the data is lost (that was overwritten meanwhile). If you have questions when in testdisk, ask first BEFORE writing any partition table.

[www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by Bucky Ball on 2013-04-25
If it was blank drive you'd accidentally wiped clean I'd agree with all of the above, but it sounds like you've written over the data with new data. Not sure how you're going to get that back. 

When you wipe a drive the info stays there but the sections of the drive it lives on are marked as 'writable'. Where you haven't written new data over the old could be retrievable I guess ...

---

