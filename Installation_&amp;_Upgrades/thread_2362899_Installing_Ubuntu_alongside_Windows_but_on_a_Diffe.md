---
title: "Installing Ubuntu alongside Windows but on a Different Drive"
date: 2017-06-03
forum: Installation &amp; Upgrades
---

### Post by limhenry on 2017-06-03
Good morning or good afternoon or good evening to all (depending on where you are  :))

I'm from Singapore. I was first exposed to UNIX way back in 1985 or so. Other than that I've been using MS-DOS and then Windows all along. I recently became interested in the UNIX family again, which brought me here.

I have a desktop PC which runs 64-bit Windows 7 Professional with a 128GB SSD and a 1TB HD partitioned into 5 partitions D:\ ...... to H:\.

I read the ubuntu docs on WindowsDualBoot with a view to setting up ubuntu GNOME on the PC, but could not find the answer to what I want to do.

What I wld like to do is: **to install ubuntu GNOME on the empty D:\, leaving the SSD intact solely for Windows on C:\, with the ability to boot into either Windows or ubuntu.**

How do I do that? Any pointer to already-existed instructions will be most appreciated.

Thank you.

Henry

---

### Post by oldos2er on 2017-06-04
You would use the "Something else" option, which gives you the ability to choose exactly where you want Ubuntu on your HD. There is some more information here: [https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by yancek on 2017-06-04
If your drive partition on the 1TB drive all have windows partitions/filesystems, that won't work.  You would first need to use windows Disk Management to shrink at least one of the windows partitions leaving unallocated space on which to install Ubuntu.  No point creating a partition in windows as you will need to create a filesystem also on that partition and a default windows is not capable of doing that.

Do you have free space?  If you have windows 7 isntalled MBR rather than UEFI, the instructions at the site below for dual booting should work.  The link also has a lot of useful information on partitioning.


[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2017-06-04
Windows 7 is almost always in the ofl BIOS/MBR configuration. Not the newer UEFI/gpt that Windows 8 or later uses.
But then you have the old MBR limit of 4 primary partitions, and must have one primary to be the extended partition, so you can make logical partitions.
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD. 

Do not create partitions with Windows tools, It may convert to dynamic from basic and dynamic is proprietary to Microsoft and does not work with Linux.
You also cannot use Windows formats like NTFS or FAT32 to install Ubuntu into. Those do not support ownership nor permissions. You can read & write NTFS data partitions with Linux NTFS driver.

 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions old BIOS info:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

---

### Post by limhenry on 2017-06-05
Thank you folks for the useful & helpful info & links.

Have a great week ahead!

Henry

---

