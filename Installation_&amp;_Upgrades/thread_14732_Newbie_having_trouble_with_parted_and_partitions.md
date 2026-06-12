---
title: "Newbie having trouble with parted and partitions"
date: 2005-02-09
forum: Installation &amp; Upgrades
---

### Post by Pete H on 2005-02-09
I currently have a windows system with a C and D drive .  The D drive is empty and i plan to install ubuntu there.  Fdisk shows a primary partition (C) and extended partition and a logical partition that fills the extended partition (D)  Parted shows  drives labeled 1,2, and 5, with 2 and 5 apparently being the D drive.  

Should I remove both the 2 and 5 partitions during the installation?

Does the fact that fdisk, parted, and qparted all show different sizes for these partitions pose a problem?

Should boot and " /"  each have a primary partition and can I put swap and /home in logical partitions?

Why aren't there partitions numbered 3 and 4?

thanks in advance,
Pete H.

---

### Post by Joeb on 2005-02-09
Partitions numbers 1 through 4 are used for primary partitions, 5 and above are for logical partitions.

It sounds like your windows partition on drive C is a primary partition (which it usually is).  Your drive D sounds like it has been set up as a logical partition inside the second primary partition.  That, too, isn't a problem.

As to whether you should delete 2 and 5 or not, that depends.  Does partition 2 take up the rest of the disk space?  If so, there isn't any reason to delete it.  If not, assuming there is enough available free space, you can create another primary partition for Linux.

If 2 does take up the rest of the disk space, what about partition 5?  If it fills partition 2, then you will need to delete it or shrink it to make room for Linux.  If not, the same applies as above, if there is enough free space, make a new logical partition.

My hard drive has hda1,2,5,6,7 and 8 where 5 through 8 are inside 2.

As for a separate boot vs /  a lot of people used to do that, but I think most now combine boot and /.  I would recommend a separate /home partition, though.  That way, if you reinstall, sometime in the future, you can format / but leave your data files intact on /home (ie choose not to format it).  

It wont' matter if /, /boot, /home or swap are in primary or logical partitions.  

When you say that fdisk, parted and qparted show different sizes for these partitions, could you be more specific?

---

### Post by thestarman on 2005-02-09
[QUOTE=Pete H]Should I remove both the 2 and 5 partitions during the installation?

Does the fact that fdisk, parted, and qparted all show different sizes for these partitions pose a problem?

Should boot and " /"  each have a primary partition and can I put swap and /home in logical partitions?

Why aren't there partitions numbered 3 and 4?[/QUOTE]

Pete,

   Well, Joeb already answered your last question fine; see his post above, and his other answers were to the point as well.  Regarding the different sizes you've observed for those utils, *if* they are not more than about 8 MB different, I would't be all that concerned about it.  Also, you need to know that some utils display size in **true** MB or GB (as do all HDD manufacturers) whereas most use Binary MB or GB which are powers of 2 (not 10) and should now be labeled as MiB or GiB, etc.  I'm mainly writing to warn people about a problem with 'parted' in many distros, but as far as which partitions to delete and how many partitions to use when installing Ubuntu I'll say this:

   You only need to delete your present /dev/hda5 (the Logical D: drive) leaving nothing but empty space inside your present Extended Partition (/dev/hda2).  Personally, I like to create a separate '/boot' partition (in most cases 60 MiB will leave you with more room than you'll ever use; though RedHat9.0 suggested 75-80 MiB!); the /boot will contain the kernel's boot-up files and the boot manager (often GRUB), and can be useful in fixing problems with other partitions.  

Also as Joeb said, a separate /home partition is nice to have, but its size is difficult (especially for a Linux newbie) to determine!  I'm not even sure if I could suggest a comparative ratio to the remainder of files in your '/ ' (root) partition!  There are many "hidden" folders and files in your /home directory(ies); only 1 subdirectory for each user...  and all your config. files (often hidden) for the GUI apps., etc. and any files you D/L for yourself (pics/music/etc.) are placed here.  The choice would depend greatly on how much room you have to begin with and what you expect to download in the future... this is why many people just use a single '/ ' partition to start out with until they get used to Linux (this most likely will not be your only installation of Linux!  ;-) ).

Regarding **parted**:  Around AUG 2004, many major Linux distros started getting complaints about new users losing all the data in their Win2k/XP  FAT32 partitions when they used 'parted' to resize them in order to make room for Linux!  This affected such companies as SuSE (9.1) and RedHat's spin-off Fedora Core 2, along with many others.  So, until I see a guarantee in writing from the authors of a particular distro, that they'll recover your data for free if anything goes wrong with the resize, I wouldn't ever trust a Linux distro for something like that on a Windows NT, 2000, XP or 2003, etc. partition!  I have heard some good things about 'ntfs-resize', but have not tested it out myself.

Daniel (aka, The Starman).

---

### Post by Pete H on 2005-02-09
[QUOTE=thestarman]Pete,

   Well, Joeb already answered your last question fine; see his post above, and his other answers were to the point as well.  Regarding the different sizes you've observed for those utils, *if* they are not more than about 8 MB different, I would't be all that concerned about it.  Also, you need to know that some utils display size in **true** MB or GB (as do all HDD manufacturers) whereas most use Binary MB or GB which are powers of 2 (not 10) and should now be labeled as MiB or GiB, etc.  I'm mainly writing to warn people about a problem with 'parted' in many distros, but as far as which partitions to delete and how many partitions to use when installing Ubuntu I'll say this:

   You only need to delete your present /dev/hda5 (the Logical D: drive) leaving nothing but empty space inside your present Extended Partition (/dev/hda2).  Personally, I like to create a separate '/boot' partition (in most cases 60 MiB will leave you with more room than you'll ever use; though RedHat9.0 suggested 75-80 MiB!); the /boot will contain the kernel's boot-up files and the boot manager (often GRUB), and can be useful in fixing problems with other partitions.  

Also as Joeb said, a separate /home partition is nice to have, but its size is difficult (especially for a Linux newbie) to determine!  I'm not even sure if I could suggest a comparative ratio to the remainder of files in your '/ ' (root) partition!  There are many "hidden" folders and files in your /home directory(ies); only 1 subdirectory for each user...  and all your config. files (often hidden) for the GUI apps., etc. and any files you D/L for yourself (pics/music/etc.) are placed here.  The choice would depend greatly on how much room you have to begin with and what you expect to download in the future... this is why many people just use a single '/ ' partition to start out with until they get used to Linux (this most likely will not be your only installation of Linux!  ;-) ).

Regarding **parted**:  Around AUG 2004, many major Linux distros started getting complaints about new users losing all the data in their Win2k/XP  FAT32 partitions when they used 'parted' to resize them in order to make room for Linux!  This affected such companies as SuSE (9.1) and RedHat's spin-off Fedora Core 2, along with many others.  So, until I see a guarantee in writing from the authors of a particular distro, that they'll recover your data for free if anything goes wrong with the resize, I wouldn't ever trust a Linux distro for something like that on a Windows NT, 2000, XP or 2003, etc. partition!  I have heard some good things about 'ntfs-resize', but have not tested it out myself.

Daniel (aka, The Starman).[/QUOTE]
 thanks for both responses.  You have cleared things nicely.
Pete H.

---

