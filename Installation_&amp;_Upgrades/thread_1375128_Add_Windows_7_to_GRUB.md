---
title: "Add Windows 7 to GRUB"
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by bearsomg on 2010-01-07
I just got a new computer that has Windows 7 Ultimate, and I want to install Ubuntu to a partition that I created. I want to be able to re-add my Windows 7 to the GRUB, without erasing either of my operating systems. I have seen people that changed the menu.lst file, but got the BOOTMGR not found error. Will I get this problem? My computer came with one drive split in two partitions, WIN7 and DATA. I took 150GB out of the DATA partition to make a new one called Linux. So, how would I put Windows 7 in GRUB, but not erase eithr operating system, and will I get the BOOTMGR not found error?

---

### Post by llawwehttam on 2010-01-07
Change the windows 7 partition with gparted so you can make room at the end for ubuntu, and GRUB 2 should automatically find and add windows 7 to its list when you install. If not when in ubuntu run
```
sudo update-grub
``` (i think).

EDIT: if you do have a problem with grub2 and windows 7 try the instructions here: [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

EDITEDIT: This method is easier quicker and better [http://ramamaganti.wordpress.com/2009/10/30/solution-for-grub-2-to-detect-windows-7-in-ubuntu-karmic-koala/](http://ramamaganti.wordpress.com/2009/10/30/solution-for-grub-2-to-detect-windows-7-in-ubuntu-karmic-koala/)  .

Hope I helped you.

---

### Post by darkod on 2010-01-07
First, delete the partition you created for linux and leave the space as unallocated. I guess you created it from windows as ntfs. You can't create partitions for linux from windows, it doesn't use ntfs. Also, standard ubuntu install uses two partitions, root and swap. One won't be enough. Delete it and leave it as unallocated space.
Then boot with ubuntu cd, Install Ubuntu option, and in step 4 tell it to Use Largest Available Free space. It will set itself into the unallocated space, creating necessary partitions.
In 99% of cases, win7 will be added to the grub menu automatically, so you don't need to think about adding win7 to grub menu right now. Only if it doesn't work by default, we'll deal with it.
Cheers.

---

### Post by kansasnoob on 2010-01-07
> **llawwehttam said:**
> Change the windows 7 partition with gparted so you can make room at the end for ubuntu, and GRUB 2 should automatically find and add windows 7 to its list when you install. If not when in ubuntu run
```
sudo update-grub
``` (i think).

EDIT: if you do have a problem with grub2 and windows 7 try the instructions here: [http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/](http://erickoo.wordpress.com/2009/06/14/how-to-add-vista-partition-to-grub-2-ubuntu-9-10-karmic-koala/)

EDITEDIT: This method is easier quicker and better [http://ramamaganti.wordpress.com/2009/10/30/solution-for-grub-2-to-detect-windows-7-in-ubuntu-karmic-koala/](http://ramamaganti.wordpress.com/2009/10/30/solution-for-grub-2-to-detect-windows-7-in-ubuntu-karmic-koala/)  .

Hope I helped you.

**Do not** "Change the windows 7 partition with gparted"! It can be done but frequently results in a broken Win 7 or Vista boot sector!

Both Win 7 and Vista have their own partitioning tools, so use them as shown here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Beginning with Ubuntu 9.10 those instructions for grub are outdated, but the installation procedure is basically the same.

---

