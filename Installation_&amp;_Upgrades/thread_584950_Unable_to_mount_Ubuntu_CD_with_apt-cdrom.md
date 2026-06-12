---
title: "Unable to mount Ubuntu CD with apt-cdrom"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Mugis on 2007-10-21
I'm currently trying to install Ubuntu Gutsy from the live CD to my Fujitsu Siemens M3438G laptop computer.  The computer already has Windows XP on it and I want to retain the OS and also the raid 0 configuration which it is in.

I have been following the guide to install Ubuntu here: [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto) and am currently at the stage "Chroot into the target system and install necessary packages".

When I attempt to use the apt-cdrom add command, I get the error:
> root@ubuntu:/# apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
E: Unable to stat the mount point /cdrom/ - stat (2 No such file or directory)
E: Unable to stat the mount point /cdrom/ - stat (2 No such file or directory)
E: Failed to mount the cdrom.
root@ubuntu:/# 


Due to this, I cannot install the ubuntu-base or other necessary packages.  I believe the problem may be related to the bug described in this report: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/115536](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/115536)

Any help towards how I can either mount the CD, or download/install the packages directly would be greatly appreciated.

Thanks.

---

