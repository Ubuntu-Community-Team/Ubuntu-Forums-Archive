---
title: "How to reconfigure an existing installation across multiple SSDs"
date: 2015-06-16
forum: Installation &amp; Upgrades
---

### Post by poplarmark on 2015-06-16
On my ThinkPad X220 I am running 14.04, which is installed in a single partition on a 250GB SSD (SDA). I've now installed a second SSD, a 120GB mSATA internal device, which is present as SDB, and I'd like to divide it into three 40GB partitions, and use these in turn as the root filesystem for successive releases. I want to keep the 250GB SSD as a single partition for use as /home. I've used this kind of setup in the past, albeit on a single HDD, and it worked pretty well.


My question is this: what's the best way to get from where I am now to my planned setup? 


I'd hope to be able to copy all of SDA1 except /home to SDB1, then somehow (how?) make that the bootable partition, then remove the non-/home directories from SDA. Is that possible?


I have an external disk large enough for a complete backup of SDA (and I will make a backup) but I'd like to work out a way to get to the new disk configuration without having to selectively restore gigs of data.

---

### Post by dino99 on 2015-06-16
so you are glancing at cloning the current installation to an other partition: [http://askubuntu.com/questions/2724/best-way-to-clone-an-installation-copying-to-identical-hardware](http://askubuntu.com/questions/2724/best-way-to-clone-an-installation-copying-to-identical-hardware)

---

### Post by poplarmark on 2015-06-16
Thanks - the linked article is not at all what I'm looking to do, but there were links from there to some other useful articles.

---

### Post by Bucky Ball on 2015-06-16
Welcome. I'd go like this. Use Clonezilla (see links at end of post) to clone the sda partition you want to keep and back to the sdb drive. Wipe sda so it is free space.
__

Clonezilla:
[http://clonezilla.org/](http://clonezilla.org/)

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)
__

You may need to tweak with your grub once installed to sdb. [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") may be able to help with that. 

I'd then do a bit of research on moving your current /home partition. You may need to shrink your current sda partition to 40Gb if you want it to be 40Gb on the other drive as Clonezilla will only clone to a target the same size as the source partition or larger, doesn't matter how much data is in the source partition (i.e. a 100Gb partition with 20Gb data still need to go to a 100Gb partition).

The way I go, as passed on by another forum user, is to create symlinks in the /home directory to data in another partition (/data for instance) that can be shared by all my installs. This prevents redundancy and would save you a bit of time.

You would simply make sda a big data partition, create folders on there that replicate the ones in your current /home partition, then move all your data to them. Delete the folders in the /home partition and create symlinks to the data on sdb instead. Hope that makes sense. It's easy. :)

There's a few ways of going about this. Do you already have a separate /home partition? Can you attach a Gparted screen shot of your current setup (Adv Reply> Paperclip icon).

---

### Post by oldfred on 2015-06-16
I believe in new installs. Then both installs will work. If a true clone you have duplicate UUIDs which is not allowed. I understand clonezilla my let you update to different UUIDs, but you still have to edit fstab & reinstall grub.

Is system UEFI or BIOS? If only Ubuntu on drive and drives may in future be moved to an UEFI system I would also suggest using gpt. I converted to using gpt with 10.10 for BIOS boot and about two years ago started adding an efi partition to beginning of new or reformatted drive, even though I recently build new UEFI system.

 I do have different installs of Ubuntu on every drive and all my data on a data partition on my HDD. I keep /home inside / on each install and link to my data partition. Many years ago I copied data from /home (and Windows) into my data partition originally organized with the same folders as /home has. Now I have several additional folders.

My backup procedure is so I can easily reinstall, and restore /home. I separately backup data partition. I also have a few settings but have scripted those into the linking of my data partition.
In copying /home to data partition, you can also exclude a lot of temporary info as in links below on backups.

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by poplarmark on 2015-06-16
Thanks Bucky Ball and oldfred. I now have plenty of information to ponder. I quite like the idea of linking from /home on the root drive to data directories on the second drive. I have run into conflicts in the past when re-using an existing /home partition with a newly installed root filesystem, I guess because different releases of the OS and applications use different and not necessarily compatible configuration files. On the other hand, it's convenient not to have to reconfigure applications (email accounts, browser bookmarks, all kinds) just because I upgraded the OS.

Anyway, there's a lot to think about so I'm going to try to work out a detailed plan and may return to bounce it off you before I proceed.

---

### Post by Bucky Ball on 2015-06-17
> **poplarmark said:**
> On the other hand, it's convenient not to have to reconfigure applications (email accounts, browser bookmarks, all kinds) just because I upgraded the OS.



You can also set your machine up so your Firefox and Thunderbird profiles are on the /data drive and not in the /home partition. Again, all installs can be pointed to  the same profiles. And again, avoids redundancy. This is possible with other app profiles too. For instance, I am a heavy Zotero user. I keep its database on the /data drive so doesn't matter which OS I boot, same data.

---

