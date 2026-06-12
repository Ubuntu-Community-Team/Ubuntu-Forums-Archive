---
title: "partitions of windows other than c"
date: 2015-03-01
forum: Installation &amp; Upgrades
---

### Post by surya_teja2 on 2015-03-01
This is first time I'm installing ubuntu on my pc.While i'm running windows i have c,d,e partitions.'c' for windows and 'd' and 'e' for storage.I want to completely remove windows and install ubuntu. My  que is will ubuntu recognize my 'd' and 'e'  partitions or should i need to full format my hdd ?

---

### Post by Bucky Ball on 2015-03-01
Welcome. Ubuntu will recognise all partitions on the drive. My advice is to download the Ubuntu ISO and create Live media to install with (disk or USB). If creating a USB in Windows try Univeral USB Installer.

Once you've created install media, boot from it>Try Ubuntu>open Gparted>Remove the Windows partition (you will see it in Gparted and it will be an NTFS partition)>if things are running OK in Try Ubuntu>Install Ubuntu>When you get to the partitioning section choose 'Something Else'.

You will see your d and e partitions, both NTFS (but Linux will call them sda*, for example sda5 and 6, might be different on your machine). Don't touch them. Install Ubuntu to the free space left by removing Windows. You need two partitions for Ubuntu, / and /swap.

If you are not installing with UEFI you have a four partition limit per physical disk. To get around this, you can create and extended partition, like a container for other paritions, and inside that can create any number of logical drives. The system sees the extended partition as one partition, regardless of how many logical drives it contains. It pays to do a little planning re. how you want your drive partitioned.

/ = partition where the OS goes;
/swap = equivalent to Win pagefile, 2Gb is fine unless you intend to hibernate, in which case /swap should be the same size as your installed RAM or larger.

You can also have a /home partition for personal data, but I'm presuming what is now d and e partitions are your data partitions which you can link to from Ubuntu. If this is the case and you are not going to be storing personal data in /, then I wouldn't worry with a separate /home partition and would make the Ubuntu / partition no more than 25Gb (and that is plenty).

Have a read through [this]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") for help on installing using 'Something Else'. ALWAYS backup any valuable data prior to installing. Good luck and let us know if you have problems/questions.

---

### Post by Mark Phelps on 2015-03-02
You would best booting your PC from the Ubuntu install media and trying it out -- BEFORE you remove all vestiges of Windows.  Until you try it out, you don't know how well Ubuntu will detect your hardware and install the right drivers.

---

### Post by oldfred on 2015-03-02
Backup all your data.

And only use Something Else. At least with UEFI there is this bug which while just fixed, is still in all the older ISO that you are downloading. 

       Reinstall says overwrite Ubuntu but it also erases existing Windows or any other partitions.
Sept 2014 Fix being released for one drive installs, but multiple drive installs must use Something Else. And fix is not in current versions.
this bug was fixed in the package ubiquity - 2.18.8.3 jan 2015
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

---

