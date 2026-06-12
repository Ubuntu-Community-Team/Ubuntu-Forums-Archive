---
title: "[SOLVED] LVM on RAID - Forced to use LILO?"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by forbjok on 2008-07-05
Hi.

I've been testing Ubuntu Server 8.04.1, and trying to get it set up properly with LVM on top of software RAID.

The setup is not in itself a problem - basically I made 2 partitions on each disk - 1 for /boot and a second for LVM (which in turn contains the root mount point).
Then I configured software RAID so that I have 2 RAID-1 arrays, consisting of one partition from each disk (/dev/md0 = /dev/sda1 + /dev/sdb1, and so on)
Then on the MD0 array, I create an Ext3 partition (w/ bootable flag on) and set it as the /boot mount point, and configure LVM with a VG and an LV to use for /)

This basically works - the install goes fine, however when it gets to the point of installing the bootloader, it always tries to install LILO - I'm not even given any choice of installing GRUB, which is normally the default.

I know it's possible to do this using GRUB, as I have a similar server setup (LVM on top of software RAID) running Gentoo, which has worked fine for about 3 years now, and uses GRUB.

I could see there might be a problem if I had done something funky like put /boot on a RAID-0 or 5 array, or on an LVM volume, but I haven't done this - /boot is on a plain RAID-1 array, and it should be no problem for either LILO or GRUB to be installed onto /dev/md0. (as I have done on my current Gentoo server)

Currently I've just been testing this new setup on a VirtualBox machine w/ 2 virtual SATA disks, however, I will probably be replacing the Gentoo server installation at some point in the future.

Does anyone know a way to fix this?
I'd rather not have my server running ancient junk like LILO :(

---

### Post by avtolle on 2008-07-05
Have you seen this? [https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)

---

### Post by forbjok on 2008-07-05
Thanks for the reply.

Yes, I think I've seen that article before.
Judging by the version numbers mentioned (5.x and 6.x) it is quite old, and it says under Expectations/Caveats that: GRUB will not work, LILO is the only viable bootloader (at this time)

However, as I said, I know this is not true anymore (or at least it is not a limitation of GRUB), as I've had a server running software RAID and LVM with Gentoo for several years.

I guess I'll continue looking around. If I don't find any in-GUI solution, I might try to just install GRUB manually from the terminal, which should work anyway.

EDIT:

I found out what the problem was.
Apparently the partition manager silently loses mount point information when entering the LVM configuration screen, so after I had configured LVM and added the root mount point, the /boot i had previously set up on the MD0 raid device had been set back to "do not use", which caused the /boot directory to be installed into the / partition on the LVM - which GRUB naturally wouldn't be too happy about.

I'm not sure if this is a bug in the partitioner, or done intentionally for some non-obvious reason, but whatever the case, now it installs GRUB as it should when /boot is on a non-LVM partition.

---

