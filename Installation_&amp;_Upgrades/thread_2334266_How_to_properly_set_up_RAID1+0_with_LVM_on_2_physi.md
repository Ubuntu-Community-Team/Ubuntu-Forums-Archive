---
title: "How to properly set up RAID1+0 with LVM on 2 physical disks and boot Ubuntu from it?"
date: 2016-08-17
forum: Installation &amp; Upgrades
---

### Post by jant90 on 2016-08-17
The scenario is like this: my server contains 2x3TB physical hard drives. I wish to install Ubuntu Server 16.04 on RAID1 (by taking 50GB off the 3TB disks) to keep my server safe in case of a disk failure. I want to use the remaining space (2x 2.95TB) as RAID0 (totaling 5.9TB) for good performance and store large amounts of non-critical data there. After a lot of researching (all this is new to me) I got it working.

The screenshot below shows how I set it all up in the Ubuntu installer.
[ATTACH=CONFIG]270727[/ATTACH]

To be more precise this is the exact procedure I followed:
[LIST]
[*]Booted the Ubuntu installer in UEFI mode (as my BIOS allowed both UEFI and Legacy for my install medium), GRUB2 menu showed and I started the Ubuntu Installer from there.
[*]Created 2x ESP (EFI System Partition) of 512MiB (sda1 and sdb1).
[*]Created 2x RAID partition of 50GB on sda and sdb.
[*]Created 2x RAID partition of remaining space (2x 2.95TB) on sda and sdb.
[*]Created software RAID1 (md0) of 50GB and RAID0 (md1) of 5.9TB.
[*]Made the raids physical volumes for LVM.
[*]Created a 50GB volume group on md0 called RAID1-vg.
[*]Created a 5.9TB volume group on md1 called RAID0-vg.
[*]Created 2 logical volumes on the RAID1-vg (1 for swap and 1 for Ubuntu root).
[*]Created 1 logical volume on the RAID0-vg (for /home non-critical data).
[*]Created the required filesystems and mountpoints on the logical volumes.
[*]Installed Ubuntu Server 16.04.
[/LIST]

Ubuntu installed fine and boots without issues right away. So now my OS installation and swap space are safely stored on RAID1 and my /home directory is mounted on the large 5.9TB RAID0.


Well now, I have a bunch questions about this setup:

[LIST=1]
[*]**First and foremost, is this way of partitioning considered "best practise" for my needs (RAID1 and RAID0 volumes on the same 2 disks)?**
[*]Is LVM even the way to go in this setup? Or does it just add a lot of overhead and/or complexity (in particular with rebuilding a degraded RAID and restoring the vg's and lv's in that case)?
[*]GRUB is installed on the EFI partition (ESP) on sda1, how do I install and configure GRUB on sdb1 as well so I can boot when disk sda fails? Will this secondary ESP be kept up-to-date automatically?
[*]How do I configure mdadm so my server will continue to run and boot in case a disk fails?
[*]Once I have everything configured, how do I restore my system (the RAID *and* LVM setup) in case of a disk failure?
[/LIST]

I believe a lot of guides show me part of what I need, but do lots of things a little differently, making that these guides only confuse me more. So that's why I've come here for help. If you have any pointers, suggestions or guides that may help me I would love to hear from you :).

Thanks.

---

### Post by jant90 on 2016-08-29
Bump. Any advice is appreciated.

---

