---
title: "Ubuntu Server both Lucid and Natty"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by OnyxDragun on 2011-10-23
I've been trying to install some more recent version of Ubuntu Server and I just keep coming up against wall after wall.

If I try Lucid, install hangs at the child_rip line.
I tell the installer to acpi=off and it gets me further, but then it stops at the Detect disks section where it doesn't detect a drive

The BIOS sees the drive, it's a SATA2 1TB drive. It was working fine with Gutsy. 

I tried running Natty, same deal. Stops because it cannot find a driver for my drive. 

I read somewhere that setting my drive to RAID would work, but it didn't. Same issue.

When I was at Gusty and tried to upgrade to Lucid or even Natty, after a reboot, I guess GRUB screws up even after doing apt-get update, apt-get upgrade and apt-get dist-upgrade

I forget the exact kernel, but it was something with 22 at the end of it. I did read that going to .32 was better, but I can't even get a LiveCD working.

Is there a driver I can choose that will work with a SATA2 hard drive? Like I mentioned, Gusty was able to be installed, but I can't seem to get a more recent release working. I upgraded because I needed access to my USB->Serial converter and Gusty didnt seem to support that.

Any ideas?

---

