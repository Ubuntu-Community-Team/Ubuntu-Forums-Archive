---
title: "Ubuntu Not Recognizing All My Partitions"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by anonymousdude on 2011-02-04
Hi Everyone,

I'm attempting to install Ubuntu alongside Windows 7.  I've done so successfully before, but I'm running into a little trouble this time.  Previously when I did it I was presented with a few different options which included..

1. Installing alongside Windows 7
2. Overwriting the entire drive
3. Manually editing the partition table.

For some reason this time, I'm not being presented with an option to automatically install alongside Windows 7.  I was a little nervous about manually editing the partition table, so I decided to create a 25GB partition from within Windows 7 and try again.  This time I selected the option to manually edit the partition table, but for some reason the 25GB partition I created is not showing up.

I tried formatting this partition as both NTFS and FAT32 as well as just leaving it completely unallocated and none of those worked.  Still doesn't show up as a partition in Ubuntu.

I don't know a ton about partitions, but I'm thinking maybe it means it's not a Primary partition?  Is there a way to confirm that and change it, if needed?  I wasn't presented with an option in Windows when I created it.

Any tips or suggestions would be appreciated!

---

### Post by Quackers on 2011-02-04
Welcome to UF.
Ubuntu will not install to a NTFS or fat32 type partition. The default file system for Ubuntu is now ext4. If you delete the partition that you created you can create a new one in the installer by using the resulting "unallocated space".

If you are installing Ubuntu 10.10, it is the "install alongside" option that you should be afraid of! It has a nasty habit of eating Windows partitions! It is safer to choose the manual option - but scarier :-)

---

### Post by anonymousdude on 2011-02-04
Thanks for the tip.  So I tried deleting the partition and just leaving it completely unallocated.  However, it's still not showing up in Ubuntu.  It seems like it's lumping it in with partition that I originally shrunk to make the new partition.  

I attached 2 screenshots.  The first is what I see in Windows 7 and the second is what I am seeing in the Ubuntu installer.  You'll notice there is no 25GB partition in Ubuntu.  Any ideas why?

---

### Post by lindsay7 on 2011-02-04
take a look at the partitions using Gparted. You should find it using the live cd under system/administration.  I would try formatting the unallocated space using Gparted and then restart the live cd and see if you can see the new partition set up under the manual install process.

---

### Post by Quackers on 2011-02-04
Your Windows partitions have been changed from basic to dynamic disks (SFS).
This is often caused by creating a fifth primary partition on the same disc. In an mbr partitioned disc, only 4 primary partitions are allowed. Exceeding that limit is bad news.
It may be possible to change them back to basic (see post 5 in the link below) but it is likely to be somewhat lengthy. It may be easier to re-install Windows. 
It is not possible, as far as I'm aware, to install a second operating system on a hard drive which includes Windows dynamic disks.

[http://ubuntuforums.org/showthread.php?t=1669910](http://ubuntuforums.org/showthread.php?t=1669910)

---

