---
title: "Installer not seeing partitions, ? overlapping partitions"
date: 2012-09-22
forum: Installation &amp; Upgrades
---

### Post by santanoo on 2012-09-22
I am trying to install Ubuntu in AMD 64 machine with Windows 7 and Windows 8 Developer Preview installed.

Neither the installer or GPARTED sees any partition. However I have access to all windows and data partitions from live desktop. Removing dmraid did not work. Using Fixparts also did not correct the issue.

Below is the report from sfdisk:

ubuntu@ubuntu:~$ sudo sfdisk -uS -l /dev/sda

Disk /dev/sda: 91201 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1          2046  28811263   28809218   f  W95 Ext'd (LBA)
        end: (c,h,s) expected (1023,254,63) found (769,106,41)
/dev/sda2      30722048  93839359   63117312   7  HPFS/NTFS/exFAT
/dev/sda3   *  93839360 261713919  167874560   7  HPFS/NTFS/exFAT
/dev/sda4     261714915 1465149166 1203434252   7  HPFS/NTFS/exFAT
/dev/sda5      28811264  30722047    1910784  82  Linux swap / Solaris
/dev/sda6          4096  28811263   28807168  83  Linux
        end: (c,h,s) expected (1023,254,63) found (769,106,41)
ubuntu@ubuntu:~$ 

Any help will be appreciated.

Thanks

---

### Post by jerrrys on 2012-09-23
Welcome to the forums santanoo :)

[http://ubuntuforums.org/showthread.php?t=1854524](http://ubuntuforums.org/showthread.php?t=1854524)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=extended+partition+does+not+start+at+a+cylinder+boundary&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=extended+partition+does+not+start+at+a+cylinder+boundary&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by darkod on 2012-09-23
What did fixparts say about the partitions positions? Did some of them looked overlapped?

The partition table looks like a big mess. Looks like you tried to add ubuntu before the windows partitions. That's not a problem, but usually you would add it at the end.

The swap partition, /dev/sda5, is supposed to be logical but it's outside the extended partition which is impossible for a logical partition. All logical partition should be inside one single extended partition.

With fixparts you can probably change sda5 to logical and that should recreate the extended partition correctly.

You can also see what parted says for the partitions, with:
sudo parted -l (small L)

PS. If the installer is not seeing partition, that means you haven't installed yet. How come there are linux partitions on the disk? Old installation?

---

### Post by oldfred on 2012-09-23
Moving Windows partitions can be a major problem. Windows has to have primary NTFS formated partitions. And Windows has in the PBR partition boot sector information on the start and size of the partition. That info has to match the partition table and if partition is moved by other than Windows tools the PBR is not updated. 

Discusses Vista but same for new versions.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Also:

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by santanoo on 2012-09-23
Thanks guys for the 'push'. I deleted the linux partition, moved windows, lost one of them and had to rebuild from the backup. Find this tool 'testdisk'; really helpful.

---

