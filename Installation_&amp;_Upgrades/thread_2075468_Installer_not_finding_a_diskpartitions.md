---
title: "Installer not finding a disk/partitions"
date: 2012-10-23
forum: Installation &amp; Upgrades
---

### Post by chilisastry on 2012-10-23
I am trying to install Ubuntu on an old computer, and having many problems.  I am reasonably experienced with OS installation in general, and Ubuntu in particular, having done such stuff for over 10 years,

First, Ubuntu 12.04.  While booting from the LiveCD, there is a (error) message stating (IBM system detected - correctly - and) unable to load a certain module because it will rewrite a Serial EEPROM.  Booting does continue, but the graphics chip (S3) is not recognized, and it boots in low res mode.  Not very useful, because I can't really use the installer screens and the partitioner in this mode.  (Perhaps 384M of memory is not enough!)

Next, Ubuntu 10.04.  Tried it only because I still have the LiveCD.  Boots perfectly, good graphics, through to the desktop.  I can go through the install steps up till the partitioning.  I have two hard drives in the computer:  Drive A with 3 Primary partitions (Windows, NTFS data, and Linux-Swap), and Drive B with one Extended partition containing two logical partitions (for /boot and for /) and two Primary partitions (both NTFS, for data).  The partitioner only sees the first drive, Drive A (configured as the Master drive).

Note:  I created the partitions using gparted (v0.7, I believe) without any problems.
Note:  I can mount the Drive B partitions from the Linux Desktop.  So the second disk is visible in Linux!

So, of course, I cannot install Linux on Drive B partitions like I want to.


Any suggestions on what may be the problem, and how to resolve this?  Will installing Lubuntu help?


For what it is worth, I switched Drive B and Drive A (changed the jumpers) so Drive B is Master and Drive A is Slave.  Surprisingly, Drive A (the Slave) is recognized by the installer, not Drive B (the Master).  Of course, from the desktop, I can mount partitions from both drives.

Just an afterthought:  Perhaps the problem is that the first partition on Drive B is the Extended partition.  I have not yet tried making the first partition a Primary partition.  Will post the results of that experiment in a day.

---

### Post by dino99 on 2012-10-24
as i know S3 will be a real problem with actual distros; maybe try with 8.04 or so, or puppy

---

### Post by darkod on 2012-10-24
If disk B was ever used in raid, it might have meta data remains. Usually that's the reason the installer doesn't show a disk as destination to install, but live mode can see it and open it.

Assuming you switch them back and disk B is /dev/sdb, you remove meta data from live mode with:
sudo dmraid -Er /dev/sdb

384MB memory does sound very low for ubuntu and Unity. And the GUI installer. The Alternate CD installer might work, but the question is how will the system perform on 384MB.

Xubuntu and Lubuntu are better alternatives it seems. You would still have to get rid of the meta data if there really is one on that disk.

---

### Post by chilisastry on 2012-10-24
Thaks, Darko.  That solved the problem.

If Linux will run, however slowly, on 384MB, I am happy.  I plan to use this computer in my experimental network for distributed processing, and it will be useful even if it only handles 20% of the load that other computers on the network will handle.

That is, until it dies, or becomes absolutely unusable (because of radically changed technology - power supplies, SATA drives, etc).

---

