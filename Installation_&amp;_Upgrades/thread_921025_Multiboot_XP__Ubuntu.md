---
title: "Multiboot XP / Ubuntu"
date: 2008-09-15
forum: Installation &amp; Upgrades
---

### Post by Srividya Vikram on 2008-09-15
Hi All,

Please guide me how to Install Ubuntu in my PC.

I ve already installed Windows XP in my PC. I have 250 GB HDD(Single Hard disk). I ve partitioned 30 GB for windows XP. The remaining space in my HDD has not been partitioned yet.

1)Please let me know how to partition for Ubuntu Linux. I want to give equal amount of space to both Windows and Ubuntu.

2)Will I be able to allocate more space for Windows after partioning?

3)The Ubuntu partition can be accessed by windows also? because when I tried Installing Ubuntu, the partions made for Ubuntu are not shown in My Computer (Windows).

Thanks in Advance.

---

### Post by Partyboi2 on 2008-09-15
> 1)Please let me know how to partition for Ubuntu Linux. I want to give equal amount of space to both Windows and Ubuntu.You can either choose to use the largest continous space option or choose manual option and make a / (root) ext3 partition with the mount point set as / then make a swap partition roughly 1.5 to x2 the amount of your onboard ram but you probably wouldn't need it above 2-3 gig.
Or you could follow a tutorial like [[COLOR=Blue]this[/COLOR]]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm") one 
>  2)Will I be able to allocate more space for Windows after partioning?Yes, but it will probably be quicker if you where to resize the windows partition before installing ubuntu. You can do this by booting the ubuntu live cd and when you have arrived at the Desktop open up gparted (System>Admin>Partition Editor) and umount your windows partition if it is not already and use the resize feature to grow your window partition to the size you are wanting. In saying all of this ubuntu can read/write to ntfs so you could just create a ntfs later on for storage that you can access from windows or ubuntu.

> 3)The Ubuntu partition can be accessed by windows also? because when I tried Installing Ubuntu, the partions made for Ubuntu are not shown in My Computer (Windows).For windows to see ext3 filesystems (what ubuntu uses) you will need to install a small program. have a look at [[COLOR=Blue]this[/COLOR]]("http://www.howtoforge.com/access-linux-partitions-from-windows")

---

