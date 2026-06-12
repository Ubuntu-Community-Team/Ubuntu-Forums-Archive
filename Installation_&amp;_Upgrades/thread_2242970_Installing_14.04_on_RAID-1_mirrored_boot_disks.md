---
title: "Installing 14.04 on RAID-1 mirrored boot disks"
date: 2014-09-05
forum: Installation &amp; Upgrades
---

### Post by Quantum7 on 2014-09-05
I'm trying to install Ubuntu 14.04 with mirrored boot disks. There are instructions for this [here]("https://help.ubuntu.com/community/Installation/SoftwareRAID"), but they are out of date. For starters, the alternate install cds seem to no longer be available, so the instructions cannot be followed literally. Using the standard livecd and gparted, I created identical partitions for both disks, but the instructions about configuring RAID itself aren't generic enough to follow from there.

Is there a different way to get the RAID options to be displayed in the 14.04 installer? Are there better instructions available anywhere?

Although I would like an answer to how to install RAID-1 on the boot partition, I would also consider suggestions for alternate partition/raid schemes. This box has 2 small (120GB) SSDs and 3 large (1TB) disks. I was planning on mirroring the SSDs for reliability and using RAID-5 on the large disks for storage. It would be nice if programs and the OS were on SSDs, as well as the mysql db. It seemed like RAID-1 was the best way to accomplish that.

Thanks!

---

### Post by lukeiamyourfather on 2014-09-05
I'd suggest RAID Z for the larger data disks. ZFS on Linux has come a long way and is a much better option than Linux software RAID these days.

[http://zfsonlinux.org/](http://zfsonlinux.org/)

I taught a class on it a while back with Ubuntu as the example. There are lots of resources out there about ZFS on Linux that are much more comprehensive, this might get you started with it though.

[https://docs.google.com/presentation/d/1TPIWcSngHa9euNbcdDMATcs4lucmC3sDmnYsvjRjbZ0/edit?usp=sharing](https://docs.google.com/presentation/d/1TPIWcSngHa9euNbcdDMATcs4lucmC3sDmnYsvjRjbZ0/edit?usp=sharing)

As for the boot drives I'd still use Linux software RAID because Linux has a lot of gotchas booting from ZFS, but booting from Linux software RAID is commonplace. See this for setting up your software RAID mirror during the install. It looks like a lot of steps but once you do it you'll realize it's not that bad. If you have access to another machine try setting up a virtual machine like VirtualBox and tinker with it using virtual disks.

[https://help.ubuntu.com/14.04/serverguide/advanced-installation.html#software-raid](https://help.ubuntu.com/14.04/serverguide/advanced-installation.html#software-raid)

---

