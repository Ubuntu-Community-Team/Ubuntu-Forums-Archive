---
title: "Installer won't resize my NTFS partitions, even manually..."
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2008-02-01
I'm trying to install Ubuntu on my girlfriends' dads' computer, and he gets this error that comes up on the screen during the partitioner part of the installation.  Whether I tell it to do the default guided, or use largest contiguous space, it never works.

The hard drive has a Windows XP installation on it, and I'm wanting to do a dual boot configuration.  I'm thinking that I might have to use some sort of windows based partitioning utility to do this, since I'm 4 hours drive away from the actual computer (using VNC to do as much as I can remotely).

Gparted would probably knock this problem out too, I suspect, but I can't use that from here and I'm nervous about trying to walk him through it over the phone.

I'm thinking the cause of the problem is the location of windows system files being near the edge of the hard drive, and it's not wanting to move those files over to make space for a new partition.  Does that make sense or am I just making stuff up?  :confused:

---

### Post by taurus on 2008-02-01
It's best to defrag the drive a few times in windows.  Then, use gparted to resize it.

---

