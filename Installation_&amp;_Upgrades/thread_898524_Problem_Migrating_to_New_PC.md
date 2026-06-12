---
title: "Problem Migrating to New PC"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2008-08-23
I am moving from a PC with two hard drives totalling 480 GB on two drives to one with a single 500 GB hard drive.  I have 5 NTFS partitions and 3 ext3 partitions, and am using 3 upgraded versions of Ubuntu 8.04 on the three ext3 partitions.  I used True Image under Windows to backup and restore all partitions.

First Problem:  True Image does not adequately resize ext3 partitions, so I made the new ext3 partitions the same size.

2nd Problem:  The NTFS partitions could not be restored to boot, so I ended up reinstalling those from scratch.

3rd Problem:  The Ubuntu 8.04.1 i uses fuse for accessing the drives (what for?  You still have to enter a password to access these), and that appears to prevent VirtualBox from accessing the drives as shared folders (bug reported submitted).

4th Problem:  Updated Sun VirtualBox or Ubuntu 8.04.x now dows not allow USB drives to be passed through to guest OS (USB connected printers and mouse still work), so a reinstall of Ubuntu and VirtualBox is not desireable.

5th Problem:  Have restored the ext3 Ubuntu partitions from backup, but now I need to see if I can get grub updated to allow me to boot to any of these partitions.  However, at this point I can only boot into Windows.

6th Problem:  Researched this matter, but suggestions to use Live CD and run from it don't seem to work with Ubuntu Live CD.  I went ahead and set up another ext3 partition in free disk space and am installing Ubuntu 8.04.1 in it even as we speak.

7th Problem:  I will have Ubuntu 8.04.x installed on drives /media/sda8, /dev/sda9, /dev/sda10, and /dev/sda11, with boot enabled only for /dev/sda11.  The boot drive will be /medis/sda1 (C:\ drive).  So how do I get grub to recognize the other three ext3 Ubuntu installs as bootable as well?  And don't forget that in this version of Ubuntu, the drives actually show up as removable media in /media/ instead of /dev/.

Some help here would be greatly appreciated.  I'm tired of having to reinstall Ubuntu when I can just bring it back from a backup, but grub needs to be updated to recognize it.

Incidentally, I have already replaced the uuid= references in /etc/fstab to reflect the drive designations instead, so that there should be no problem with volume ids during the boot process. All the Ubuntu installs were bootable on the old PC.

---

