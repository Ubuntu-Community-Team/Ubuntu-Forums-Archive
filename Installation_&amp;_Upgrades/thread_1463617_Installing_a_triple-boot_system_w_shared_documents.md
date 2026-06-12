---
title: "Installing a triple-boot system w/ shared documents, Ubuntu first"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by PHi11Y on 2010-04-27
Hi, I currently use my PC for work, music [I'm a DJ by profession], and gaming. It's got good specs and I've recently gotten a 500GB hard drive for it. I've installed Ubuntu 10.04 [using the 9.10 CD and running *update-manager --devel-release*]. However, in my infinite foresight, I installed Ubuntu to take up the whole drive, /home and all. I've only used about 80GB of space in /home so backing it up to start off a triple boot shouldn't be a problem.

Currently, my partitioning is /dev/sda1 at 494GB [ext3, mounted as /], /dev/sda2 is a 6.2GB extended partition, and /dev/sda5 is a 6.2GB swap partition. Basically, I need to do the following things, but don't know the least hacky way around it.

1) Repartition to make the Ubuntu's root filesystem take up ~40GB of space
2) Probably have the swap partition immediately after / (is the other extended partition even necessary?)
3) Install Windows 7 to use for gaming in a 60GB partition
4) Windows XP to use for music production in another 60GB part
5) Have the rest of the space on the hard drive formatted as NTFS & used for documents for Windows 7 (as D:\), Windows XP (also as D:\), and Ubuntu (used as /home/saxon).

Any pointers? I've searched around but I couldn't find anyone else with my exact problem - most people have Windows installed first and only want a dual boot. I'm fairly comfortable with the shell so I'm not too bothered about using Term either. Sorry if I've worded this awfully or seemed like a bit of an idiot :)

---

### Post by ottosykora on 2010-04-27
but when I count, this will make 5 partitions already, so this is not possible, the extended partition is a must in your case.
But you might do it so that one primary partition is for XP, the next primary for w7 and the rest is then extended partition and inside that you can have the ubuntu partition, the swap partition and the common data partition. However to have the data same time as home, well this can be problematic. I would not do that , but have separate data partitions for linux and windows and one smaller 'share' one with fat32 to exchange files between them. Yes, linux can somehow write to ntfs, but don't be surprised when windows one day tells you that the file system is broken or what.
I can also recommend to have a separate small grub partition and use this to start all the operating systems from there (main menu).

---

### Post by oldfred on 2010-04-27
If you have more than one drive it is easier, but you can repartition at will. It is just moving things around can sometimes cause problems so be sure to have good backups. Both copies of windows should be in primary partitions. Windows will want to combine its boot into the first windows that is the active (boot flag) partition. You then cannot directly boot the second windows as it is not complete. You can install the second windows to a logical partition but if you ever delete the first the one in the logical is just about impossible to boot (I did see an exception but it was not easy).

If you have to you can delete swap to allow easier reorganization, but will have to reset the new UUID in fstab to allow booting. All changes have to be done from a liveCD as you cannot edit partitions you have mounted.

You can separate the two windows installs this way but then windows will not boot the second one only grub as it can turn on boot flag to boot either.
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

