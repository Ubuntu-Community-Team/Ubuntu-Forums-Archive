---
title: "Unable to Install on Raid-1"
date: 2010-07-19
forum: Installation &amp; Upgrades
---

### Post by Cerin on 2010-07-19
I have an old Fedora machine setup to use Raid-1. I'm trying to install Ubuntu 10.04 Desktop on it, but the installer can't seem to override the raid partition.

I have two 80GB drives, but the "Prepare disk space" screen only shows one 80GB partition called "/dev/mapper/isw_dfafhagdgg_RAID_Volume01". When I selected "Erase and use the entire disk", it gives me the error "The ext4 file system creation in partition #1 of Serial ATA RADI isw_dfafhagdgg_RAID_Volume0 (mirror) failed".

So I tried going back and specifying partitions manually. However, it only shows me the one device /dev/mapper/isw_dfafhagdgg_RAID_Volume01, and I can't delete it to get my original two hard drives, so I can recreate a RAID-1 setup.

What am I doing wrong? I thought Ubuntu supported software RAID-1?

---

### Post by ronparent on 2010-07-19
The problem I've experienced is that gparted doesn't modify or create raid partitions under 10.04 - thus the install fails if any raid partition modifications are required as part of a 10.04 install. The work around is to use gparted in a prior version of an ubuntu install or live cd to preformat a target partition to install to. As long as no formatting is required of a raid partition during install, everything should work fine. At least up to step 8 of 8 - if you are installing the grub 2 bootloader to the raid drive That step will likely fail (but it is fixable despite a message indicating a 'fatal failure' of the install). Fedora may be able to create the blank formatted target raid partition for your install. It might also be useful for booting into the 10.04 install to setup a grub 2 bootloader - if you intend to leave it installed that is. Post if you need additional info.

---

### Post by pyn on 2010-07-19
I'm glad to see that I'm not the only one having this issue.  I've been experiencing this regardless if I have ICH SATA Control Mode set to AHCI or IDE.  I figured the error was on my end since this is a reasonably new build (i7 920, GA-X58A-UD3R, WD 300GB VelociRaptors).  I'll see if partitioning with a previous version of Ubuntu or GParted works.

---

### Post by Cerin on 2010-07-19
I initially tried using the desktop ISO. I'll try the alternative ISO, which I read has better tools for manipulating RAID.

---

### Post by ronparent on 2010-07-19
pyn: I don't know how prevalent the problem is but gigabyte mb's appeared more than once.

Cerin: I would try any version prior to 10.04

---

### Post by pyn on 2010-07-19
I  can confirm that the drives are represented properly using the 9.04 installer.  I'm assuming that I could just install to one of the drives and set up something in mdadm afterwards, right?

---

### Post by Cerin on 2010-07-20
> **ronparent said:**
> 
Cerin: I would try any version prior to 10.04

Yes, sadly, I've confirmed the 10.04 installer is unable to setup RAID.

sigh

---

### Post by Cerin on 2010-07-20
I'm trying to follow [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID) but the 9.10 installer doesn't seem to follow the same steps.

In steps 2-5, where you configure one drive for ext4/swap partitions, it works fine for the first drive. But when I try it for the second drive, as directed, it appears to wipe-out the root mapping on the first drive. Going back and remapping the first drive just wipes out the mapping on the second...

So I tried ignoring that, and going to "Configure software RAID", but of course it gives me the error "no root file system is defined"

---

### Post by Cerin on 2010-07-21
After a few hours of playing around, I finally figured out how to trick the RAID installer into installing RAID. The previous link I posted is a relatively good guide, but it's missing a few minor, but critical, steps. For example, after "automatically partitioning" your second drive, you need to go back and manually specify the formatting and mount point of the first drive, because a bug in the automatic partitioner causes this to be deleted.

The rest of the install seemed to go well, until I finally had to reboot. Then I found my RAID setup was already degraded, but I don't know why.

mdadm reveals:
```
sudo mdadm --query --detail /dev/md*
/dev/md0:
        Version : 00.90
  Creation Time : Tue Jul 20 22:46:44 2010
     Raid Level : raid1
     Array Size : 74894912 (71.43 GiB 76.69 GB)
  Used Dev Size : 74894912 (71.43 GiB 76.69 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Jul 21 00:12:37 2010
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : d4877a0b:84e84635:65fbc0b5:c6c4ebd0
         Events : 0.554

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1     252        1        1      active sync   /dev/block/252:1

```

The Palimpset Disk Utility shows a "77 GB Raid-1 Drive" with a single component, "77 GB RAID Component (/dev/mapper/isw_dfafhagdgg_RAID_Volume01)", with a state listed as "In Sync".

What does this mean? Why is it still showing the "isw_dfafhagdgg_RAID_Volume01" label from my old RAID setup that should have been wiped out? Did that somehow survive and is not breaking my new RAID-1 setup? Shouldn't it be showing the two hard drives I configured to be used in the array?

I've tried using mdadm to add my two hard drives to the array (/dev/sda, /dev/sdb), but it reports they're in use. The disk utility reports both drives are good (although one has a few bad sectors). How do I get my array out of degraded status?

---

### Post by Cerin on 2010-07-21
I have a spare drive to test with, in case the disk with bad sectors is damaged enough to degrade the array.

However, I'm unclear on how to include the new drive in the array. The guide mentions using mdadm --add. Is anything else required? Do I have to format the drive identically to the first beforehand?

---

### Post by Cerin on 2010-07-21
I finally found a [nearly complete guide]("http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array") that explains how to correctly rebuild an array after replacing a drive.

The only omission is that you need to run "sudo grub-install /dev/sdb" (replacing sdb for the device of the new drive) afterwards, or else the array won't be bootable.

No single guide I found reported this last detail accurately, which is frustrating, because without it all the other work is meaningless.

---

