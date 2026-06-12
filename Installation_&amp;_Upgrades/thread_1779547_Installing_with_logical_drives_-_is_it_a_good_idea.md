---
title: "Installing with logical drives - is it a good idea?"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by nzjethro on 2011-06-10
Hi guys. I'm currently dual booting Maverick with Win 7. My HDD is set up with a primary partition for 'buntu, a primary partition for Win, a 100MB primary partition called "System Reserved" flagged as boot, and a primary partition for Common Files - my storage between the two OSes (see gparted screenshot).
Basically:
/dev/sda1 = boot, but not sure if this is for Windows or Ubuntu
/dev/sda2 = Win
/dev/sda3 = Maverick
/dev/sda4 = Common files

I thought I'd like to give Oneiric a hoon, see what the early stages are like, and down the track I thought running Fedora or Suse for a laugh might be fun, but I can't create more than four primary partitions.

My question is, wise Ubuntu users of the internet, can I wipe my Win 7 partition, merge that space with the unallocated space next to it (which I created when I shrunk my Win 7 partition), then create an extended partition in it's place containing logical drives to install Win, Oneiric, and future OSes?

---

### Post by dabl on 2011-06-10
Given that you have already used your maximum four primary partitions, you're a little stuck, to be adding partitions -- you would have to delete one, and then re-make it as an extended type partition, and then you could make logical partitions within it.

An alternative (the one I do) would be to install VMware Player, and then install your alternative OS's on VMs.  No re-partitioning needed.

---

### Post by nzjethro on 2011-06-10
> **dabl said:**
> you're a little stuck ... you would have to delete one, and then re-make it as an extended type partition, and then you could make logical partitions within it.

An alternative (the one I do) would be to install VMware Player, and then install your alternative OS's on VMs.  No re-partitioning needed.

My Win 7 is pretty much a clean install, I have no problems deleting that. :p If I remove the Win 7 partition, will I be able to merge the partition where Win 7 was with my unallocated partition next to it, and then turn that into an extended partition with n logical drives?

And what is the setup with installing OSes on logical drives. Will they still be bootable from Grub?

And thanks for the tip but I'm not really into virtualisation. My system specs mean that performance isn't perfect. I'd much rather do a full install (if possible) of multiple OSes, then pick and choose which one to boot. :D

---

### Post by coffeecat on 2011-06-10
> **nzjethro said:**
> 
My question is, wise Ubuntu users of the internet, can I wipe my Win 7 partition, merge that space with the unallocated space next to it (which I created when I shrunk my Win 7 partition), then create an extended partition in it's place containing logical drives to install Win, Oneiric, and future OSes?

If you delete sda2, you can certainly create an extended partition in the space vacated (plus any adjacent unallocated space) and create as many logical partitions as you want. That will be fine for Linux but not necessarily so for Windows. Windows cannot boot from a logical partition but can exist in one if you have the boot files in a primary. It looks like your sda1 may be the small ~100MB boot partition which Windows 7 likes to set up in which case it is theoretically possible to use that and have the Windows 7 C: partition in a logical. But I've never done this so I can't advise you how to go about it.

If you check the contents of sda1 and confirm that it is the Windows boot partition, then you could delete both sda1 and sda2, and in the resultant space create a new larger sda1 (NTFS) for Windows and an extended sda2 for your logicals. Left to its own devices, the Windows 7 installer will make a separate 100MB boot partition but you can force it to install to just one partition in the way you used to with Vista and XP.

A third option would be to erase everything and start over with something like:

sda1 Windows C:
sda2 Shared Data
sda3 Extended partition with all your logicals for various Linux installs.

**EDIT**: Missed your Gparted screenshot at first. Yes, sda1 is your Windows 7 boot partition.

---

### Post by nzjethro on 2011-06-10
Thanks coffeecat, I'll give it a go now, and if I come across anything I'll post back.

---

### Post by dabl on 2011-06-10
If "starting over" is an option, why don't you just make the entire hard drive an extended partition?  Then you can add as many logical partitions in it as you wish (well, there are limits, ultimately).  For sure you could have lots of Linux OSs there.

But I suspect Win 7 will insist on having at least 2 primary partitions for itself, so there's your bottleneck.

---

### Post by nzjethro on 2011-06-10
Hmmm, well I've given it a go, and there's good news and bad news. I've successfully repartitioned my drive as follows:
sda1: Win
sda2: Extended partition (all blank at the mo, but I'll fill it in)
sda3 and 4: unchanged (so still Maverick and shared files).

I also reinstalled Win 7, on just the one partition. I reinstalled Grub, and when I boot to Grub it shows me my linux kernel (+recovery mode + 2 memtests). I figure Win isn't there because I am yet to update-grub. My problem is, though, when I try to boot to my Ubuntu 10.10, i.e. the top kernel in the Grub list, it doesn't find anything. It just hangs on a screen with a blinking cursor. I've tried editing the grub file to show nomodeset instead of quiet splash, but when I do this it runs through a bunch of text and hangs on "running /scripts/init-bottoms".

Does anyone know what might be causing  Grub to not be able to boot my Ubuntu? I'm going to keep hunting for a solution, but if anyone knows a hint or two that'd be primo!

And @dabl, it may be the best option, depending on how I go from here. If I can, I'd like to avoid nuking everything, because I like my 10.10 setup as it is now. But down the track when I finally give up Maverick, and have a massive overhaul (who knows, maybe finally say goodbye to Win!) I may do that. As is, I have about 80GB of extended partition, which will hopefully be enough for a test machine of Oneiric, and then maybe a couple more non-primary OSes to play around with!

---

### Post by nzjethro on 2011-06-11
Ok guys, couldn't resolve the flashing cursor issue, it looks like a few people have come up against it usually after mucking around with Windows MBR. Last time I touch anything made by MS for a while. I decided instead to backup, repartition, and reinstall. I have essentially gone with dabl's suggestion except I've installed Ubuntu in its own primary partition. Thanks for the suggestions about the OP, I'll tag this thread as solved. :D

---

### Post by coffeecat on 2011-06-11
I'm glad you've found a solution that suits you. However, next time (if there is a next time :wink:) you have a problem with grub not booting something that ought to be working, have a look here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you then run the boot info script and post the output, someone will be able to help you troubleshoot it.

Not for now, obviously, but one for your bookmarks. Good luck!

---

### Post by nzjethro on 2011-06-11
Thanks coffeecat. I'll keep that in favourites for if (or maybe when is more likely) I run into boot issues again.

---

### Post by srs5694 on 2011-06-11
I realize this is closing the barn door after the horses have gone, but....

In your case it would have been significantly easier to use my [FixParts](http://www.rodsbooks.com/fixparts/) program, which can convert primary partitions to logical and vice-versa, with certain restrictions. Given the screen shot you posted, though, I can say with near-100% certainty that you could have converted both /dev/sda3 and /dev/sda4 into logical partitions. (The "near" in "near-100%" is just a hedge against the possibility of a damaged partition table or bug causing problems.) Linux wouldn't care about this change, unless you've edited /etc/fstab or your GRUB 2 configuration to use disk device references rather than UUID numbers. Since /dev/sda4 is (or was) data storage and not a boot device, changing it to a logical wouldn't matter. After the conversion, you'd be able to add more partitions in the gaps you already had available; or you could have moved partitions if absolutely necessary.

---

### Post by nzjethro on 2011-06-11
Cheers srs5694. I'll keep that in mind for next time. :D

---

