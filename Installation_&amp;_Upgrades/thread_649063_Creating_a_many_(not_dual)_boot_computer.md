---
title: "Creating a many (not dual) boot computer"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by vtowner on 2007-12-24
Ok so i have gusty running as my sole OS on my main computer without any problems. But i have a second computer that i don't use for really anything and i was wondering if it would be possible to create a multi-boot with several distros and OS's such as BSD, Debian, XP, Vista, SUSE, gOS, Solaris etc. I have read that i can share the swap between linux distros with no problems but i was wondering how would i go about setting up the /boot. I have dual booted between windows and linux in the past but never anything like this. I don't really know anything about the MBR, so if this is possible i would really appreciate the help.

---

### Post by visiblesun on 2007-12-24
I don't know much about it either, though I managed to get my laptop running with Vista, and 3 different linux distros, all the linux distros sharing the same 1gb swap...only problem was that I maxed out the number of partitions I could use - my 160gb hard drive running Vista could only take three partitions at once (vista, two linux distros, and swap). To get the the extra linux i just split the last partition into two virtual partitions, which you should be able to do either using Vista disk management or Ubuntu's own installation disk.

Either way, I managed it (im a not very good at this stuff usually) just by starting with vista, adding ubuntu, then installing different distros by taking apart unused space from these. It will usually give you these options when you install.

it's worth a try, so good luck

---

### Post by rsambuca on 2007-12-24
> **vtowner said:**
> Ok so i have gusty running as my sole OS on my main computer without any problems. But i have a second computer that i don't use for really anything and i was wondering if it would be possible to create a multi-boot with several distros and OS's such as BSD, Debian, XP, Vista, SUSE, gOS, Solaris etc. I have read that i can share the swap between linux distros with no problems but i was wondering how would i go about setting up the /boot. I have dual booted between windows and linux in the past but never anything like this. I don't really know anything about the MBR, so if this is possible i would really appreciate the help.

It should be pretty easy to set up.  You just might want to make note of a few things:

1. The most hassle-free method to install everything would be XP first, Vista second, and then the rest don't matter which order.
2. XP and Vista like to be on primary partitions.
3. Swap can be shared.

You will want to set up the partitions in advance, and then install the OS's into the pre-existing partitions.  My personal recommendation would be to partition the drive along these lines:

1. ntfs - for XP
2. ntfs - for Vista
3. One big Extended Partition containg a number of logical partitions (partitions 5 to 10)for your distro's:
  5. Ext3 - debian
  6. Ext3 - gOS
  7. Ext3 - gentoo
  8. Ext3 - Suse
  9. Ext3 - Fedora...
  10. swap
4. Shared data for all OS's. Can be either ext3 or ntfs.

You can set up the partitioning in advance using the [gParted liveCD]("http://gparted-livecd.tuxfamily.org/"), which is very easy to use.

I personally like to have one distro as my main use distro, and have that grub installed to the MBR (hd0).  All the other distros I install grub to the logical partition which holds the new distro, and not the MBR.  I then edit my first grub menu.lst to point to all of the other distro's, and chainload grubs.  This way you only have to edit the grub menu once.  All future updates are automatically configured for you.

---

