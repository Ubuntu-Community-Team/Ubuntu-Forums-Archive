---
title: "Upgrade Xubuntu 14.04 to 16.04 with BTRFS RAID 1 array attached"
date: 2017-01-12
forum: Installation &amp; Upgrades
---

### Post by PaulM55 on 2017-01-12
Hi,

I'm not a sys admin, just an enthusiastic home user with a hardware engineering background who converted to Linux with Ubuntu 12.04.

A couple of years ago I set up a home server that consists of an HP Microserver running Xubuntu 14.04 desktop, with unnecessary apps removed, BTRFS installed supporting a 2 x 2Tb data array for our home data storage and two VirtualBox Virtual Machines running a local firewall (IPCop) and a data/media/email server (Ubuntu 14.04 minimal install recently upgraded to 16.04). I won't go into the various reasons for this configuration apart from to say I used BTRFS as it was (almost) stable at the time and was supposedly *the* upcoming file system for Linux ! I assumed (hoped ?) it would shortly be supported by an easy to use GUI maintenance app, but sadly that hasn't happened.

I'm now in the position of wanting to upgrade Xubuntu 14.04 to 16.04 but unsure how to do this with the BTRFS RAID 1 array attached. Needless to say all our data is backed up. Should I just go ahead and do a 'dist-upgrade' with the BTRFS array live ? Should I disable the BTRFS array, and possible remove the 2Tb hard disks, before the upgrade, then replace and re-enable the BTRFS array when complete ? I've been reading around the subject, but found little specific on this upgrade issue, and concluded if I upgrade with the BTRFS array live it may well do a snapshot of the array during the upgrade. If so, and the array is not destroyed during the upgrade, I'm not sure how to handle this once the upgrade is completed.

Any advice with this upgrade would be very much appreciated. This system has been working faultlessly since I set it up and I would very much like to avoid starting from scratch with a new server if possible. I'm reasonably familiar with the command line but not so confident with the multitude of BTRFS commands, having used an online guide to set it up successfully and had no problems with it since, so need some guidance here if possible.

Thanks in advance
Paul

---

### Post by untenops on 2017-01-26
This comment is kind of a bump as I am in a similar situation.  I have a home server setup with Ubuntu server edition 14.04 running for close to 2 years now.  I have a BTRFS array setup as well.  Originally 2 2TB drives set at RAID 1.  Since, I have added to the array so it is now 4, 2TB drives set at RAID 1.  Is it safe to dist-upgrade?

---

