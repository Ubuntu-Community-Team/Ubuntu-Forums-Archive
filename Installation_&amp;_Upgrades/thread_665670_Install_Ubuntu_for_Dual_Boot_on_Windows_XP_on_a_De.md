---
title: "Install Ubuntu for Dual Boot on Windows XP on a Dell Dimension E510"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by ash4linux on 2008-01-12
Hi There,

I have been wanting to install ubuntu on my windows machine for a long long time but am afraid of partitioning coz I do not know much about it. I have gone through a lot of help on dual boot installation but it mostly talks about a hard disk having a single partition. My hard disk presently has the following partition:

Partition -   Filesystem -    Size -    Used -    Unused -    Flags

/dev/sda1 - FAT16 -   54.88 MB - 7.79MB - 47.09MB -

/dev/sda2 - NTFS -    144.31 GB - 69.23MB - 75.07 MB - boot

Unallocated - Unallocated - 7.84MB -----------------------

/dev/sda3 - FAT32 -  4.64GB -    3.6GB -     1.04GB -  

I had read at some places that it is possible to have a maximum of only 4 partitions on a hard disk. Now as I understand Ubuntu Installation requires two partitions. So in my case the number of partitions will exceed 4 if I try to install Ubuntu. I wish to know for this scenario how is it possible for me to install Ubuntu on my machine? Would I be required to delete one of the existing partitions on my hard disk? I believe the two extra partition are for system recover and Dell Analytic Tools. So should I be messing up with these partitions at all? I need windows on my machine because I have some very important software installed which are only available for windows. Please advise. Thank you.

---

### Post by Pumalite on 2008-01-12
Shrink your XP partition with Gparted Live CD. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Read the instructions.
Make the new partition an extended one.

---

### Post by ash4linux on 2008-01-13
> **Pumalite said:**
> Shrink your XP partition with Gparted Live CD. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Read the instructions.
Make the new partition an extended one.
Thank you for reply. I found a useful guide explaining what I think I should be doing based on your suggestion of using GParted. I am posting the link here for anyone else's reference:
[http://partedmagic.com/docs/gparted.html](http://partedmagic.com/docs/gparted.html)

There are a couple of questions that I have:
1) Can I do this operation of making the new partition as extended and having logical partitions in it for Ubuntu, directly from Ubuntu installation using the manual partition option?  I beieve ubuntu also uses GParted for partitioning.

2) In my situation do I need to worry about Boot Loader Installation. During the installation in the Advanced setup you can specify Device for boot loader loader installation. I have read about people having problem with MBR and GRUB. I do not understand a lot about these, but I am wondering since my Windows will be the boot drive, do I need to take some special precaution regarding Boot Loader while doing manual partition.
Once again thank you for your help.

---

### Post by Pumalite on 2008-01-13
The stand alone program is better, gives you more control. Install Grub to MBR without fear. If you have any problems, they can be fixed easily. Remember to backup everything. Check this too:
[http://ubuntuforums.org/showthread.php?t=632013](http://ubuntuforums.org/showthread.php?t=632013)
(out of the extended partition you can make many logical partitions and Ubuntu works fine in them)

---

