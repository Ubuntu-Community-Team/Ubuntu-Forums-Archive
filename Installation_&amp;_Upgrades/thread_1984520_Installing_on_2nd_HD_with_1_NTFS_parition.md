---
title: "Installing on 2nd HD with 1 NTFS parition"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by Humber on 2012-05-21
My 2nd HD (drive D in Windows) is currently formatted at 100% NTFS. Since I'm using maybe 15% of it's total space, I tried creating the 3 partitions Ubuntu needs (primary, boot and swap). Not only wouldn't Ubuntu create partitions on it, but it even said the size I selected for the root partition (20,480 mB) was way too small.

I'm thinking all this may be due to a situation where I have to shorten the size of the NTFS partition so that the part where Linux goes becomes "free" or "unpartitioned", and do so  with some other software. After this is done, can I create the 3 partitions and install Ubuntu on that space? Also, what program(s) can I use to do this? Hopefully it'll something Windows based since Ubuntu is now on a flashdrive. 

Finally, does all the stuff now on the NTFS partition have to be moved to another drive and put back into the remaining NTFS space?

---

### Post by oldfred on 2012-05-21
Is it truly a second physical drive or another partition? Windows call a d: drive whether a partition on the first drive or on a second drive.

Post this and/or a screen shot from gparted. Gparted is one of the Linux partitioning tools included on the liveCD/USB. 

sudo fdisk -lu

If a Windows system partition use Windows to shrink the partition, but do not use Windows to create partitions as it may convert to dynamic which does not work with Linux.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

If a second drive:
Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

