---
title: "software RAID mounted on /  :: tips for installation of 10.04"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by TopicMapper333 on 2010-09-14
These tips assume you're doing a NEW INSTALL.  WARNING: What follows are DANGEROUS, DATA-DESTROYING COMMANDS NOT FOR USE BY THE FAINT OF HEART OR BY ANYONE WHO CARES AT ALL ABOUT THE DATA ON THE DISKS.

WARNING: Read *all* of this before doing *any* of it.  This advice may not be for you.

(0) Use the alternative installer.  (It's basically the familiar old Debian installer, really.)

(1) Connect only the disks you're going to use for the RAID you're going to mount as the root filesystem.  Disconnect all others.  This is a nuisance, but do it.  Much bigger nuisances await you if you don't do this.  Particularly, the bootloader may be installed to a disk other than the RAID, so your system won't work without that other disk.  Ugh.  The reason this can happen is that the installer doesn't ask you which disk you want to install it to; it writes on /dev/sda, whatever disk that happens to be.  (Installer people: you might want to fix this, to give some flexibility to those of us who run lots of disks in different ways and for different reasons.)

(2) DANGEROUS INSTRUCTION:  Zero the first 1% or so of all the disks in the RAID.  You'll need a Live CD to do this.  The purpose of this exercise is wipe out the old partition tables.  If you don't do this, and some or all of the disks used to be used in another RAID, the installer may see this RAID and assume you want to keep it or use it.  The installer *says* it can delete such a RAID, but it can't always really do it.  So you're stuck until you zero the first parts of the disks.  Having zeroed the first parts of the disks (where the partition tables are), the installer will not see the old RAID(s) or the old partition tables, and you'll be able to do what you want in the installer.  (Installer people, you might want to add an option to ignore existing partition tables, RAIDs, and so on.  It's really tedious to have to do this disk-zeroing thing.)  To zero a disk (let's say /dev/sda), I think the easiest way is the badblocks command:

badblocks -b 4096 -c 4096 -svw -t 0 /dev/sda

In the liveCD session, give yourself a terminal for each disk.  In each terminal, say

sudo bash

and then do the badblocks command for each of the disks.  When all the badblocks commands say they have done 1% or more of the task, you can stop them.  They've done all the damage they need to do!

(3) Now run the alternative installer disk.  When you get to the partitioning task, select
"manual".  Add a partition table to each disk. 

Now let me tell you what *I* do at this point, in case you will find it helpful.

I put 3 partitions (all primary) on each disk.  The first partition is 128 megabytes, which isn't much, but it's enough for the /boot directory.  I only use one of these: the one on the first disk.  The first partition on all the other disks are just placeholders; I set all of them to "Do Not Use".

The first partition on the first disk I make a reiserfs to be mounted on /boot.  I add the "notail" option, and I label it "boot".  I set the bootable flag "on".

The second partition on each disk I make 3-6 gigabytes, depending on how many disks I have and how much memory I have.  These will become, collectively, a RAID 5 that I will use for swap space (see below).  Obviously, they should all be the same size, whatever size you choose.  Each of the second partitions should be set to "volume for RAID".

The third partition on each disk gets whatever's left over (assuming all the disks are the same size).  Each is set to "volume for RAID".

Now go to the top of the page and do "configure software RAID".  After writing the partition tables to disks (you have to do this), I first create the swap area as a RAID 5.  It becomes a device called "/dev/md0".  I choose all the second partitions to make /dev/md0.  Then I create the main RAID 5 for the root filesystem, which will be called "/dev/md1".  Having done these things, I choose "Finish" (which is kind of misleading, because you're not done yet).

Now you're back at the main partition display, which now shows the two RAIDs at the top of it.  Set md0 to be used as swap area, and set md1 to be a reiserfs with default options (i.e., no options) to be mounted on /  (root).

Now you're done.  Continue the installation process.  At the very end, it asks whether you want to write the bootloader on the MBR (master boot record) of some disk.  Do it.  It will put it on /dev/sda, whatever disk that happens to be at the moment.  That's fine.

But don't take the last step and just reboot.  Instead: WAIT UNTIL THE DISK ACTIVITY LIGHT GOES OUT, which could take hours.  Your system is "resyncing" its RAIDs.  If you get antsy and want to get an idea how much longer it's going to take, press F2 and give yourself a command prompt.  Run

mdadm --detail /dev/md0

which is probably "clean" by now

and

mdadm --detail /dev/md1

which probably isn't yet "clean" but rather "resyncing".  You will see a percentage of completion number. 

Now reboot.  It should work.  If it doesn't, check the "boot" tab (or whatever) in your BIOS to be sure it's looking at the right disk for the bootloader.  In at least some BIOSes, I know of no alternative but simply to try each one until I find the one that works.  It's not predictable: /dev/sda isn't necessarily the first thing that appears in the BIOS's display of connected disks.

Good luck!

P.S. Why do I bother with all this RAID stuff?  Because disks die and I want my machines to keep working anyway, without recourse to backups (which I certainly do make daily).  Because large-file throughput is faster.  Because I get a larger space to work in than a single disk can provide.  Because it's cool.  And with software RAID, I get as good as (or maybe better-than) performance than I can get from a RAID card, or from the fakeraid chips that come with most motherboards these days.  And I don't have to pay for a RAID card or enclosure.  And I'm in a nonproprietary technology space, where I like to be.  Mdadm is simply awesome, and I don't often use that word.

P.P.S.  Why do I use reiserfs?  Because it always works, and it never bothers me with administrative chores that other filesystems make me do.  It takes care of itself.  Because it works reasonably fast.  Because it almost always recovers from an untidy shutdown or crash, without effort on my part.  Because it can handle enormous directories that ext3 can't handle.  Because it handles small files extremely efficiently (that's the tail-packing feature that has to be turned off in the /boot filesystem because the bootloader doesn't understand it -- see the "notail" thing I mentioned above).

---

### Post by TopicMapper333 on 2010-09-17
I've learned something important since writing this.  My advice above gives step-by-step directions whose result is that RAID volume partitions appear at the very end of each disk.  This is not a good idea, because (1) it causes confusion (failure) at boot time and (2) when re-installing ubuntu 10.04 on the same set of disks.  Instead, I recommend you put a non-RAID-volume partition, or just some unpartitioned empty space, at the high end of each disk.

Problem (1) occurs because /proc/partitions lists raw disks as well as partitions thereof, and because by default mdadm RAIDs have their superblocks at the high ends of their partitions. If the high end of the disk is also the high end of a RAID volume partition, then mdadm, as, at boot time, it shuffles through all the available partitions, thinks that, for example, /dev/sdd and /dev/sdd3 are two partitions that somehow have identical superblocks, which confuses the situation enough to cause booting to fail.

Problem (2) occurs when using the alternative installer on disks that already had a RAID on them with volumes at their high ends.  The installer, too, checks /proc/partitions and it thinks it has RAIDs that don't exist and that it can't delete, even if you have zeroed the low ends of the disks in order wipe out their partition tables! In order to make it possible to re-install Ubuntu 10.04, I've had to zero whole disks, which is pretty tedious. (Just zeroing the first and last 2% of each disk seems to work, but that too is pretty tedious.)

---

