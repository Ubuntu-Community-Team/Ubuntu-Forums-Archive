---
title: "Windows XP does not boot on dual booting system"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by quantumtex on 2012-08-08
On a newly installed Ubuntu 12.04 on a laptop with existing Windows XP, when I select Windows XP from the boot menu, I get a blinking cursor at the top-left corner and the system stop there. Ubuntu runs fine. Here is the report from boot-repair:

[paste.ubuntu.com/1126526]("http://paste.ubuntu.com/1126526")

Please suggest. Thanks.

---

### Post by oldfred on 2012-08-09
Welcome to the forums.

Offically XP does not boot from extended partitions. Why did you move it into the extended. Linux boots just fine from logicals in an extended.

I see you edited boot.ini to be partition 5, but NTFS partition also have to have the same partition info as the partition table. Script says your sda5 used to start at sector 63 which was the normal start for sda1 and a default install of XP.

You can rearrange partitions with fixparts, but may have to reinstall grub or edit fstab if not using UUIDs & reedit boot.ini.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

You may be able to run chkdsk to get the partition table's partition boot sector updated. With XP there may be some work arounds to get it to boot from grub, but a Windows boot loader will not boot it except if you have another install in a primary partition.

How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)
Vista Win7 missing boot files meieifra. More info on Herman's post
[http://ubuntuforums.org/showthread.php?t=813628#4](http://ubuntuforums.org/showthread.php?t=813628#4)
meierfra. - How to fix XP when the boot files are missing + download
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
How to fix Vista/Window 7 when the boot files are missing post4
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)

---

