---
title: "root swap and home partition"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by klw on 2011-01-15
Hello,
I have a laptop with win7 installed. I have now made a 60gb partition  which I want to install ubuntu into. The question I have before I do  that is how large each of the root, swap, and home partition should be? I  have read some place that root could be as small as 8GB, but isn't that  too small? Since I guess beside ubuntu all the softwares installed will  reside there as well? And I think I'm going to set my swap to be 2GB  large.

I'm mainly going to use ubuntu for some programming and browse the web.

---

### Post by solar george on 2011-01-15
Why not simply let the installer decide how big to make the partitions, its best not to customise such things untill you've got an idea of what your useage is likely to be.
If you've prepared to do some mucking about at the cli if you run into problems you could use lvm to create easily resizeable partitions (there should be an option in the installer to use lvm).

If you do decide to set the partitions out manually my maverick install with lots of added software is taking up about 7.9Gb of / (which for me is 30Gb and much larger than I've ever seen used by /).

---

### Post by srs5694 on 2011-01-15
By default, the installer creates only root (/) and swap; it doesn't create a separate /home partition. This works, but IMHO it's better to create a separate /home partition, since that tucks your user files away in a way that makes it easier to completely trash the installation without damaging user files (say, if you decide to wipe the installation and install a different distribution).

As to the original question, here's my recommendation:


[list]
[*]**root (/)** -- 5-20 GB, depending on how much space you can afford to devote to Ubuntu in total and how big an installation you want. 5 GB will be sufficient for a bare-bones installation, but if you plan to install lots of stuff, something closer to 20 GB is preferable.
[*]**swap** -- Make this 1-2 times the amount of RAM you've got. The reason is that suspend-to-disk uses swap space, so if it's smaller than your RAM size, you won't be able to use this feature. If you're 100% positive you'll never use suspend-to-disk, you could go with less than this, but IMHO disk space is cheap enough that it's good insurance to make swap space big enough for any eventuality in the first place.
[*]**/home** -- The rest of your allocation. This is where your user files reside, so plan your total disk space appropriately.
[/list]


Also, if you're dual-booting, you may want to devote another partition, typically using NTFS or FAT, for shared data files. In some cases this partition might even be bigger than /home, or if you don't expect to have any Linux-only user files, you could omit /home and use the shared-data partition for all your user data. (You can't mount an NTFS partition as /home, though; Linux requires filesystem features in /home that NTFS doesn't support.)

---

### Post by gordintoronto on 2011-01-15
> **srs5694 said:**
> Also, if you're dual-booting, you may want to devote another partition, typically using NTFS or FAT, for shared data files. In some cases this partition might even be bigger than /home, or if you don't expect to have any Linux-only user files, you could omit /home and use the shared-data partition for all your user data. (You can't mount an NTFS partition as /home, though; Linux requires filesystem features in /home that NTFS doesn't support.)

This isn't required, since Ubuntu has full access to the Windows 7 NTFS partition(s).

---

### Post by srs5694 on 2011-01-16
Using a separate data-exchange partition isn't required, but it is a good idea. The reason is that Linux doesn't recognize most of the filesystem security features that are built into NTFS and used by Windows. This makes it too easy for a user to accidentally move, delete, rename, overwrite, or otherwise damage a critical Windows system file from Linux. Furthermore, it's unclear just how safe the NTFS-3g drivers are. Sure, plenty of people have posted that they've used it for months or years without problems, but I don't know of a scientific study of the issue. Without evidence to the contrary from such a study, it's hard to believe that NTFS-3g equals or exceeds Microsoft's own NTFS driver for safety. Between these two factors, and especially the first, it's rather risky at best to be accessing the Windows boot partition from Linux, except in read-only mode and/or for very limited purposes.

These arguments don't apply to a simple data-exchange partition. The latter argument would still apply to a shared-data partition that holds important data, but there might not be good alternatives in that case, particularly if you've just got one computer. (If you care to invest in a network server, you could store your important data on it and access it using network protocols like NFS or SMB/CIFS.)

Note that the same argument applies to accessing just about any OS's critical boot partition(s) from just about any other OS -- I wouldn't give Windows access to a Linux boot partition, for instance.

---

