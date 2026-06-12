---
title: "dm-crypt/LUKS + btrfs - how to install?"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by zerothink on 2010-05-25
Hi! I am quite new to ubuntu and need to do non-typical installation, so I would like to ask for comments to avoid wrong attempts. I am not afraid of command line (my present distro is ArchLinux), but I at the end would like more or less standart ubuntu system (ie. without custom kernel, hacked init script and so on...)

I would be grateful for any hints.

**What I have:** I have laptop, first partition is used by Win XP (must be kept intact) and than there is unpartitioned space.

**What I would like:**
[LIST=1]
[*]Create small boot partition
[*]Create big partition using all free space on hdd
[*]Encrypt big partition using dm-crypt/LUKS
[*]Inside encrypted partition use btrfs filesystem (with few subvolumes)
[*]For most btrfs subvolumes use compression (not only enabled,but have files actually compressed).
[*]Have minimal ubuntu 10.04 installed inside of this environment.
[*]Swapping to file inside encrypted partition
[*]Have hibernation working if possible
[/LIST]

**My plans how to do it:**
[LIST=1]
[*]boot minimal ubuntu iso (netinstall)
[*]manually create /boot partition and format it to ext2
[*]manually create main partition and format it using cryptsetup luksFormat
[*]open it using cryptsetup luksOpen and create btrfs partition inside
[*]create btrfs subvolumes as I see fit (ie. separate subvolume for home)
[*]mount subvolumes (with btrfs compression enabled) and chroot into this environment
[*]**INSTALL UBUNTU**
[*]pray that hibernation works...
[/LIST]
(I can't use method *inbstall to ext2/ext3/et4 partition an then convert it to btrfs*, because files would not be compressed.)

How to **INSTALL UBUNTU** I am not sure yet. Things which seems worth trying:
[LIST=1]
[*]Try to install into this chrooted environment using installer from Alternate CD somehow.
[*]Install using debootstrap (but I am afraid I will end with installation too far from standart ubuntu).
[*]Before all this make normal installation to ext3 ot ext4, backup it to external USB and now instead of in istallation just mount this external USB and copy files to hdd, than correct fstab. 
[/LIST]

---

