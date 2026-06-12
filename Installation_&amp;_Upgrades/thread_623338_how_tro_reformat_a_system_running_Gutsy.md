---
title: "how tro reformat a system running Gutsy"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by gino on 2007-11-25
Hi,
I got a new laptop and enthusiastically wiped Vista and installed Gutsy thinking that worse case scenario I would just restore if I really found a need for Vista. Turns out that gutsy works fine except that it will not support the webcam or compiz. I tried different fixes and none works, there seems to some issues that will be solved in Hardy. Any way...
I need to reinstall Vista but when I try to install from scratch the HP restore disks only sees a small fraction of the hard drive and install it there. I tried using Gparted but is not clear to me what I should do..I tried to create just one partition and install Vista ( to later add ubuntu as dual boot) but the restore disk keeps on instaling in a small fraction of the hard drive (too small a fraction).
Any help would be greatly appreciated
Gino

---

### Post by LaRoza on 2007-11-25
The restore disks will wipe the drive, so you will have to reinstall Ubuntu.

After restoring, use GParted LiveCD to create the partitions for Ubuntu and then install.

---

### Post by gino on 2007-11-25
Well the problem is that the restored Vista is a partition that is to small to be usable. I have a 250 Gig hard drive. I would like to give Vista 100 and the rest for Ubuntu. My problem is how to reinstall vista. I have Gparted I just do not know how to wipe out all info from the hard drive, assuming that this would trick the restore into installing vista in the whole hard drive.
Also when I installed Gutsy in the original system (that had Vista) I never saw an option for dual install so that would be my second round of questions...how do I install a dual boot but for now I need to reinstall Vista in the whole ( or 100 Gigs of the) hard drive

:)

Gino

---

### Post by logos34 on 2007-11-25
Use HP restore or Gparted to delete all the partitions on the disk (except, of course, the HP partition!) and then create a new 100 GB NTFS partition out of the unallocated space, or as much of the space as it will let you--you can always try to resize/enlarge it afterwards.  Read the guides and documentation at the Gparted website.  Use Gparted to create an ext3 and swap in the remaining space.  If the only way is to format the entire disk as NTFS, then do that and install vista...then use vista's disk management tool to shrink it again to make room for ubuntu.  

Dual boot:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

---

