---
title: "Dualboot (Win 7 + Ubuntu 14.04) broken after Windows 10 upgrade (lost partitions)"
date: 2015-08-07
forum: Installation &amp; Upgrades
---

### Post by koenigma-qraum on 2015-08-07
Hey,

I tried smashing it all into the title but here is the more detailed version of my story:

I've been using a dualboot with Windows 7 and Ubuntu on my desktop pc for a while and everything worked out great until I decided to upgrade to Windows 10. After upgrading, nothing worked, grub just went into rescue. 
I then used a live usb stick to run boot-repair, which at least got the system back running. However, I did not get the OS selection at startup but it just booted straight into Windows 10.
Next step was - again - a live usb stick to run gparted and see that my Ubuntu partition showed up as unallocated space. Using testdisk I was able to restore this partition, after reboot I could boot into Ubuntu. BUT not into Windows 10. Another round of gparted showed that now the Windows partition was marked as unallocated space...
Using testdisk another time I was able to restore the Windows partition, but not the Ubuntu partition. So here is the heart of the problem: I can't restore both partitions at once because testdisk gives me "bad structure" when I try to activate them all.

Has anybody else faced this problem and can help?

Cheers,
Matthias

---

### Post by oldfred on 2015-08-07
Are you clicking on correct type.
Windows will want the * or bootable on the primary partition with the boot files. And then Windows is almost always in another primary partition.
Many install of Ubuntu then are in Logical partitions or L in testdisk. 
If you try to make too many primary partitions it will complain, 3 primary is the most you can have as the extended to hold the logical partitions will be the fourth.

Post this with whatever you have:
sudo parted -l

Many have used testdisk to restore the missing partition. 
Testdisk uses the old CHS and finds all old versions of partition table. So selecting correct set of partitions is a bit more difficult.
Also some have used parted rescue.

Others upgrading from Windows 7 to Windows 10 are having similar issues. And in past we have seen where Windows reinstall will "forget" to write a Linux logical partition when it rewrites the partition table. For some reason it includes the extended, unallocated & swap. The unallocated then is the Linux partition as a logical partition. If Windows install is after the extendedpartition, it may not even write the extended partition.

 Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)


Best before upgrading to Windows 10 or any reinstall of Windows to backup partition table. If you do not change partition sizes, then you can just restore partition table.
       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

And since the sfdisk partition list is a text file, you can manually edit it. Some of the old time users here that really knew partitions have edited and restore partitions. But you have to know the partition table rules to make sure you do not violate them.


 Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)
caljohnsmith and meierfra use sfdisk links:
Exported partition table & reimported to fix with sfdisk.
[http://ubuntuforums.org/showthread.php?t=1591704](http://ubuntuforums.org/showthread.php?t=1591704)

---

