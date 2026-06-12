---
title: "After updating grub, will my system still boot?"
date: 2015-11-16
forum: Installation &amp; Upgrades
---

### Post by adante on 2015-11-16
I'm on 14.04. I just ran an update in anticipation of an impending dist-upgrade and got some unexpected prompts/behaviour when grub was updating:

[http://imgur.com/MoMVDUc](http://imgur.com/MoMVDUc)

I'm hoping the /dev/sde1 was the most appropriate. Must admit I'm a bit confused here because I'm fairly certain that the boot has always been /dev/sde1 (ie it has not changed). Can't think of anything that might have triggered a UUID change.

After this the install log dumped out a bunch of read errors for /dev/sdc. Got to admit I'm a bit perplexed by this as I don't currently have a /dev/sdc (I did some time ago - but the disk failed and I removed it). See lines 272-355

[http://pastebin.com/43nbs6Fg](http://pastebin.com/43nbs6Fg)

I'm a bit concerned that as it happened immediatelly after the GRUB prompt, GRUB has somehow gotten confused and I'm in for a sad time (ie non-boot) next time I reboot my computer.

I've never had a pleasant experience so trying to forestall this. How can I check this?

[http://pastebin.com/dPbiSX4h](http://pastebin.com/dPbiSX4h)

---

### Post by grahammechanical on 2015-11-16
I have seen that dialog. In my case it was due to customizing Grub in some way and I was asked if I wanted to keep the customized version of the configuration file or replace it with the default version.

In your case the explanation is quite clear and it has to do with that removal of a hard disk. If we remove a hard disk then the labels such as sda, sdb and sdc will change but the UUIDs will stay the same and as Grub works with UUIDs and not "sd" type labels it usually means the OS still loads.

Do you have Logical Volume Management (LVM)? I have no experience with that. So, is there any procedure that should be followed when having LVM and removing a disk? And did you follow it?

Grub has not only been updated it has been reinstalled. Therefore, I think that Ubuntu will reload. I also think that all these errors come from the removal of that hard disk which did not cause problems until Grub needed to be upgraded and having LVM in the mix.

Regards.

---

### Post by adante on 2015-11-17
> In your case the explanation is quite clear and it has to do with that removal of a hard disk. If we remove a hard disk then the labels such as sda, sdb and sdc will change but the UUIDs will stay the same and as Grub works with UUIDs and not "sd" type labels it usually means the OS still loads.


Just to provide some context: the system drive is on /dev/sde and sde only. Disks sda, sdb, sdc (no longer present) and sdd are all mechanical storage disks.

I appreciate that grub is trying to tell me the disks have changed. However as you say, Grub works with UUIDs which should not have changed from the removal of sdc. In addition I am a little confused as to why Grub would have been installed into sdc.

For what it's worth and stated in OP the sd labels did not change on drive removal. I recall on installation that the SSD drive was on sde (a SSD).

> Do you have Logical Volume Management (LVM)? I have no experience with that. So, is there any procedure that should be followed when having LVM and removing a disk? And did you follow it?


I had the default LVM options for sde that are setup when you install ubuntu.

I also had LVM setup on the mechanical disks but very simplistic (one lv per pv - no striping across disks). Thanks for bringing this up as it appears to have identified the issue. Running pvdisplay/lvdisplay causes the "/dev/sdc: read failed after 0 of 1024 at 0: Input/output error". So I guess the problem is something in lvm memory remembering sdc.

Thanks for your help!

---

### Post by oldfred on 2015-11-17
But you do not install grub to a partition but to a drive. Only a few exceptions on that. With RAID you do not install to the drive but the root of the RAID. If you have standard /boot partition with LVM then you have standard boot and grub must be installed to sde not sde1. BIOS cannot boot from a partition.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see similar drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on major updates
sudo dpkg-reconfigure grub-pc 
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

