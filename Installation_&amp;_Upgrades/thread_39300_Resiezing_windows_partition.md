---
title: "Resiezing windows partition"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by niels on 2005-06-04
I have three partitions.

/dev/hda1 - fat32 - Windows XP - 7.771 MB unused
/dev/hda2 - linux-swap
/dev/hda3 - ext3 - Ubuntu 5.04 - 877 MB unused

Now I would like to use the 7.771 MB unused disk from Windows at my Ubuntu partition (mabye as /home/). I have tryed to resize my windows partition with Norton Partitionmagic, but i get some strange errors.
Is it possible to do the repartitioning from Ubuntu (I have installed Gparted)? How?


Niels

---

### Post by Dogmeat on 2005-06-04
Oops!  :---) sorry I misread that, have you tried resizing with parted ?

---

### Post by mingus on 2005-06-04
[QUOTE=Dogmeat]I don't think Gparted can resize NTFS partitions. However, you can try getting the ntfsprogs package from synaptic or with apt-get. It has a tool called ntfsresize which does the trick (I just used it yesterday and it booted to windows just fine). However after the resize you will have to use fdisk, delete the NTFS partition and create a new one equal or bigger than what ntfsresize resized it to, and make it bootable!

Also check [this](http://linux-ntfs.sourceforge.net/man/ntfsresize.html)  out for more information![/QUOTE]

Am I missing something here . . . isn't his hda1 FAT32, not NTFS?

---

### Post by mingus on 2005-06-04
[QUOTE=niels]I have three partitions.

/dev/hda1 - fat32 - Windows XP - 7.771 MB unused
/dev/hda2 - linux-swap
/dev/hda3 - ext3 - Ubuntu 5.04 - 877 MB unused

Now I would like to use the 7.771 MB unused disk from Windows at my Ubuntu partition (mabye as /home/). I have tryed to resize my windows partition with Norton Partitionmagic, but i get some strange errors.
Is it possible to do the repartitioning from Ubuntu (I have installed Gparted)? How?

Niels[/QUOTE]

If PartitionMagic is giving you errors, it would be wise to investigate why first.  Before ever modifying a FAT32 partition, it is critical that chkdsk be run with the option to fix not only filesystem linkages but any bad blocks as well (this can take a while).  Then the partition needs to be defragged.  Then try PM again; this is safest because the partition was created in a Windows environment and PM is native to Windows.

---

