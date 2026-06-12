---
title: "Installation problem (VFS:  Cannot open root device; IBM server)"
date: 2013-12-14
forum: Installation &amp; Upgrades
---

### Post by rwan.work on 2013-12-14
Dear all,

I'm trying to install Ubuntu on an IBM X server and I have not been successful with either the latest 12.04 or 13.10 via a CD boot disc.

During booting, it gives the following error message:

md: Audodetecting RAID arrays.
Scanned 0 and added 0 devices.
...
VFS:  Cannot open root device "(null)" or unknown-block(0,0): error -6
Please append a correct "root=" boot option; here are the available partitions:
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

Then a call trace is printed and the system freezes.  The system uses a ServeRAID M5110e RAID card and I've read that it can be a bit tricky ([http://www.ubuntu.com/certification/hardware/201203-10669/](http://www.ubuntu.com/certification/hardware/201203-10669/)) [this is not the server model in question; but the same RAID card].  This is a new installation so the hard disk is empty.

I'm unsure if the above link is related to my problem or not.  I would prefer to use Ubuntu but out of desparation, I tried the latest version of Fedora and it managed to detect the hard disk.  There is only one HDD and it's in a RAID-0 configuration.  I'm not sure if this means it should have said "added 1 devices" because it is managed by the hardware and not by mdadm.

Looking through Google, I've seen people with this problem but it's usually related to a problem with grub on a system with Ubuntu already installed.  I'm booting from disc and want to install it on a new system.  So, I think it is not relevant.  Also, no available partitions were found at all...so that is somewhat worrying.  That's different from problems faced by others where partitions could be found.

Anyway, I'm stuck and don't know what to try.  Any pointers would be appreciated...  Thank you very much!

Ray

---

### Post by rwan.work on 2014-01-03
Dear all,

Just a quick follow-up to my own question...

I just tried the latest version of Debian (wheezy, 7.3) and it worked.  The hard drive was detected fine during boot-up of the disc and the OS was installed fine.

I still have a preference for Ubuntu since I am more familiar with it, but Debian is close enough so I might stick with Debian unless anyone has any suggestions on what I can try...

Thank you!

Ray

---

