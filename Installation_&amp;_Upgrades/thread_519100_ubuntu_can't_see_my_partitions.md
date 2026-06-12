---
title: "ubuntu can't see my partitions"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by elchuppa on 2007-08-06
(Sorry for the cross post on general forum, but issue was not resolved)
my machine has three hard drives. Two 256 gig hitachi sata drives and one external usb drive.
Originally I had Windowxp64 installed on sata1 (the first hitachi) taking up the whole drive with one primary partition.  When I installed ubuntu (by resizing the ntfs partition) ubuntu would start fine but when I tried to select windows from grub I would get a disk error (can't quite remember the exact error but it wasn't 'non-system disk..'.)  

To fix this issue I tried fdisk /mbr, fixmbr, and then a full on windows repair, however nothing worked.  Eventually I used the windows install disk to delete the first primary ntfs partition, create a new one, reformat it, and reinstall windowsxp 64.  After this was done I used supergrub to reinstall grub in the mbr. 

So now windowsxp 64 boots fine :). 

Sadly when I select ubuntu from Grub I get Error 17.

When I boot from the Ubuntu live cd and start gparted Ubuntu shows sda1 as empty with no partitions ntfs or otherwise on the drive (unpartitioned space).  This is clearly not the case as I'm booting windows from it. Both other disks (sda2, sda3) which are formatted fat32,  mount and work normally. 

running fdisk -l from the console does not even list sda1 or sda2, just sda3 which is the usb drive..

So this is the end of a long saga of install and reinstall, and reinstall, and I would love to not have to start from scratch.  Does anybody know what might be going on and whether I can somehow get Ubuntu to read or fix the partition table?  (I'm guessing somehow ubuntu messed up the windows partition when it installed and then windows returned the favor when I recreated the windows partition)

any help would be greatly appreciated.  
thanks,

---

### Post by Pumalite on 2007-08-06
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17)

---

### Post by fredj on 2007-08-06
Check in the bios and see what mode is set for your SATA drives. In general this can be
either IDE RAID or AHCI. If we discount RAID for the moment Windows is happy to install in IDE
mode. Ubuntu may install in IDE mode but sometimes refuses to boot when this mode is set.
The way to get rid of these problems is to set the SATA mode to ACHI (however if you have
installed Windows in IDE mode then you may have to re-install it).
Then install Ubuntu from the Alternate CD (rather than the Live CD) because the partition editor
on the live CD doesn't always see SATA partitions correctly.
Also if you are installing to a SATA drive then look at the post 'Is Ubuntu destroying your hdd'
for a work around for disk shutdown problems. The kernels used at present don't shutdown
SATA drives correctly.

---

