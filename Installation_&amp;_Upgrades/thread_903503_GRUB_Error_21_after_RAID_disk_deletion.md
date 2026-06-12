---
title: "GRUB Error 21 after RAID disk deletion"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by sake on 2008-08-28
Hi,

I have set up a new system, based on the Gigabyte EP35-DS4 motherboard. This motherboard has 2 disk controllers, the Intel one from the southbridge (Intel® ICH9R) and one Gibabyte SATA-II controller. At first I thought to use the Intel controller to create a RAID5 data disk, but it turns out to be "fake-RAID", so I chose to use Linux softraid instead (as this is the only OS that will be run on the box anyway). I attached 4 samsung disks to the Intel controller (giving it 2 more SATA slots for future expansion) and attached my Raptor system disk to the Gigabyte controller. This has been working fine over the last few weeks.

Today I thought I gave the RAID a quick test by un-attaching one of the 4 data disks that make up the RAID5 disk. Unfortunately GRUB halts with "Error 21". From reading other posts I understand that this means that GRUB can't find a necessary disk. I think this is because the BIOS detects one disk less and renumbers the disks which means the system-disk with GRUB on it has a different device name (/dev/sdd instead of /dev/sde). I guess my choice to put the system disk on the Gigabyte controller to keep the Intel controller free for extending my RAID5 was not very handy (I think adding a disk to the Intel-controller would also mean that GRUB will fail with Error 21).

Am I correct in my analysis?

If so, what would be the best way to "fix" this? I see the following options:

1) Reinstalling the whole system with the system disk as the first disk on the Intel controller. Moving the data-disks one slot down. Unfortunately I have already migrated data and services to this system so I would like to keep it running as it is. So this option would be my last choice.

2) Instead of reinstalling, moving the disks as in 1), but reconfiguring everything so that I don't have to reinstall things. What would be involved to perform such a migration?

3) Keep the system running "as is" and solve the issue by changing the MBR after a disk failure or if a disk is added. Can this be done? If so, how?

4) Is there a way to tell the bios to label disks in a certain order?

Any ideas are welcome...

Cheers,


Sake
(who is more of a Linux user than a Linux system admin :confused:)

---

