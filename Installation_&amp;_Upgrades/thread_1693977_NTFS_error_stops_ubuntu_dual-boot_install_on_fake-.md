---
title: "NTFS error stops ubuntu dual-boot install on fake-raid?"
date: 2011-02-23
forum: Installation &amp; Upgrades
---

### Post by Waggoneer on 2011-02-23
I am attempting to install Maverick on an older pc. It has (2) mirrored 153 GB SATA drives. I set aside 33GB for a linux partition, by shrinking the partition in Vista. 

Choosing to "Install along side windows" is not an available option. I can only choose use who disk, or use empty area. 
I choose use the empty area, and the Ubiquity installer gets hung up when attempting to format the empty space as EXT4. When I scroll up on the output I notice some error messages referencing NTFS. When I use Gparted it shows a possible problem. 

> Warning: 
The device /dev/sda1 doesn't exist

ntfsresize v2.0.0 (libntfs 10:0:0
ERROR(2):Failed to check 'dev/sda1' mount state: No such
file or directory
Probably /etc/mtab is missing. It's too risky to continue. You
might try
an another Linux ditro.

Unable to read the contents of this file system!
Because of this some operations may be unavailable. 

The following list of software packages is required for ntfs
file system support: ntfsprogs. I ran chkdsk /r on the Vista partiton, in case there was a problem there. The issue still persists. 

Is there any way to get the install to work?

---

### Post by YesWeCan on 2011-02-23
The Windows RAID system is also known as host RAID or fake RAID.
Ubuntu doesn't officially support it, but have a read of this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by ronparent on 2011-02-23
It sounds like you are installing 10.10. The FakeRaidHowto hasn't been updated for 10.10 and will be of little help to you. Since you are trying to install to a raid set YOU DO NOT WANT TO INSTALL TO SDA!

You need to boot to the live cd and install kpartx (Ubuntu Software Center, Synaptics or 'sudo apt-get kpartx) to the session before the installer will see the raid partitions as raids. Then I suggest you choose the partition manually option to pick the install partition and format to ext4 (and select '/' as the mount point). The install should proceed normally after that. Don't forget to create a swap partition as well. Also, if you want to use gparted within your install, you will have to install kpartx there as well (unless a gparted update has fixed the bug).

Post if you need more help.

---

