---
title: "Kubuntu 6.06 problem with failed GRUB"
date: 2006-05-09
forum: Installation &amp; Upgrades
---

### Post by shergill on 2006-05-09
Hi all. Today I tried to install the latest/greatest Kubuntu on my computer. The installation went fine; but at the end I ran into a problem where GRUB did not install properly. It gave an error message about some sort of failure. Sorry I did not write down the message :(

This is what my partition map looks like. I have a 160gig drive mapped into 4 partitions.

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/hda2            7650       19928    98631067+   f  W95 Ext'd (LBA)
/dev/hda5            7650       12748    40957686    7  HPFS/NTFS
/dev/hda6           12749       17847    40957686    7  HPFS/NTFS
/dev/hda7           17848       17913      530113+  82  Linux swap / Solaris
/dev/hda8           17914       19928    16185456    b  W95 FAT32


/dev/hda1 is the XP disk. /dev/hda5 and /dev/hda6 are just my windows partition that contain some data. /dev/hda7 is my SWAP partition. /dev/hda8 is the one I actually installed Kubuntu on. 

How do I go about installing Grub so that I have an option to chose between Windows/Kubuntu at startup?

Thanks!

---

### Post by shergill on 2006-05-09
This is the error I had.

"Unable to install GRUB in (hd0). Executing 'grub-install (hd0)' failed. This is a fatal error."

---

### Post by Sef on 2006-05-09
> /dev/hda8 17914 19928 16185456 b W95 FAT32
> /dev/hda8 is the one I actually installed Kubuntu on.

Problem:

/dev/hda8 is not formatted right for running Gnu/Linux root.  It should be a root partition with either ext3 or reiserfs, not FAT32.  You should have a FAT32 partition so you can share files between Windows and Kubuntu.

Solution:

Run an install disk.  When you get to the partition manager, do a manual install.  Delete /dev/hda8.  You will want to install 3 new partitions.  Because you can't have more than 4 primary partitions, you will need to make some or all of them logical partitions.  

The partitions you will want to make are root (/), home (/home), and FAT32 (/FAT32.)  

1) Root is where Kubuntu will reside; home is for your files.  If you need to reinstall or update Kubuntu, your files will not be written over. 

2)  FAT32 is for sharing files between Windows and Gnu/Linux.  For size, I would make root about 10 GB; FAT32 about 5-10, depending on how much file sharing and the size of the files that you will share that you will do; 

3) Home I would make about 20 GB or more if you will have lot of photos or videos or other memory intensive files.

First setting  up the partitions:

First, set up the root partition, and make it bootable.

Second, set up the home partition.

Third, set up the FAT32 partition.

If you do that, GRUB should install with no problems.

Read the tutorial for a more detailed explaination.  If you have any questions, please post them here.

---

### Post by shergill on 2006-05-09
Thanks for the detailed instructions. I will try it tonight. Question: Can I just have 1 partition for 'root /' and 'home'? Is there any harm in that; other than the issue you mentioned regarding the upgrades being dificult.

---

### Post by shergill on 2006-05-09
Another question: Do I need anything called a '/boot' partition?

---

### Post by shergill on 2006-05-09
Thank you SEF.. your instructions worked great. Posting from kubuntu :)

---

