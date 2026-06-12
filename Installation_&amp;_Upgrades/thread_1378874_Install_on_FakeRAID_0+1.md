---
title: "Install on FakeRAID 0+1"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by gregdavisfromnj on 2010-01-11
A special place should be reserved in hell for the creators of the winmodem, winprinter, and firmware-RAID AKA FakeRAID AKA ATARAID devices.  Especially when marketing their devices as "real" hardware controllers

That said, I want to install (K)Ubuntu 9.10 on an Nvidia nForce 720a chipset FakeRAID array that has already been built, and that also hosts my Windows drive for dual booting.  It is a 0+1 array, which the dmraid utility, for some reason, refers to as 10.  It is a mirror of 2 stripes.

The normal desktop install cds get to the point where the disk drives are partitioned, etc, but no drives are detected.  Ho hum, there are many howtos on getting beyond this.  I have gotten the farthest to my goal by following the ones along the lines of "boot the live cd, activate the raid array with 'sudo dmraid -ay', partition the '/dev/mapper/nvidia_cdiabcgf' drive however it needs to be with fdisk, start the livecd installer, magically see the RAID array, go on with life."

I get stuck on the "magic" and "going on with life" parts because the livecd installer seems to only assemble the stripes, but not the mirrors.  In other words, it looks like I have two identical drives to install on, as opposed to a single drive with some partitions.

How do I properly install on a Fake 0+1 RAID array without clobbering the Windows install that took me a few days to get stabile?

Below is some useful information retrieved while running the livecd.  I made 4 partitions in this order:  ntfs for windows, linux swap, linux for root, and linux for a data partition.
```

ubuntu@ubuntu:~$ ls -c1 /dev/mapper/
nvidia_cdiabcgf3
nvidia_cdiabcgf4
nvidia_cdiabcgf2
nvidia_cdiabcgf1
nvidia_cdiabcgf
nvidia_cdiabcgf-1
nvidia_cdiabcgf-0
control

ubuntu@ubuntu:~$ sudo dmraid -s
*** Active Superset
name   : nvidia_cdiabcgf
size   : 625163520
stride : 128
type   : raid10
status : ok
subsets: 2
devs   : 4
spares : 0
```...and from the installer, see the attached screenshot.  Notice how the partitions are in the form [array]-[0|1][1-4], instead of [array][1-4].

---

### Post by gregdavisfromnj on 2010-01-14
Found some blogs that describe successfully doing the RAID install, but they only refer to a single level of RAID.  This one seems to be what I am experiencing for the nested RAID:

[dual boot on RAID 10 fakeraid]("http://blog.dipinkrishna.info/2009/09/howto-dual-boot-ubuntu-and-windows.html")

Basically, a bug in libparted is preventing the ubiquity installer from seeing the second level of RAID.  The blog post recommends rebuilding libparted without a patch (somebody forgot to regression test apparently) to resolve the matter.  I'll try this when I have more time.  In the mean time, maybe there is a bug report.

---

### Post by darkod on 2010-01-14
Not sure how far you can get with the standard desktop cd because for RAID (including fakeraid) the alternate install cd is recommended. Plus, this might help:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by gregdavisfromnj on 2010-01-17
Thanks Darkod.  The primary problem I am having is due to an Ubuntu patch to parted (the disk partitioner), as described in my previous post.  I found a launchpad bug ([https://bugs.launchpad.net/ubuntu/+source/parted/+bug/311179](https://bugs.launchpad.net/ubuntu/+source/parted/+bug/311179)) which is really old, but still open, and I am reproducing it almost exactly.  Looks like the sentiment is "as-designed" or "low priority".

Used the LiveCD to get a shell and followed the instructions at [http://blog.dipinkrishna.info/2009/09/howto-dual-boot-ubuntu-and-windows.html](http://blog.dipinkrishna.info/2009/09/howto-dual-boot-ubuntu-and-windows.html) to compile libparted without the questionable patch.  Then the instructions on the fakeraid howto using the LiveCD ubiquity installer worked, at least until bootloader installation.  Ubiquity showed me the proper dmraid devices among the other ones (the mirror of stripes in addition to the individual stripes), but wants to install grub2.  It seems like Grub2 is not ready to use RAID devices, or at least nested RAIDs.  It fails to install to the MBR, which is probably because the MBR is a virtual one presented by the FakeRAID.

So the task now is to properly install Grub1 (0.96) onto the RAID device, without foobar unto the Windows partition, or the RAID array altogether.  Super Grub Disk is helping me experiment here.

---

### Post by gregdavisfromnj on 2010-01-18
Couldn't get Grub installed per the FakeRAID Howto.  Looks like it installs to the MBR, but upon reboot I just get the Windows boot loader.  Super Grub Disk doesn't seem to find the root partition, and when I manually specify which (hd0,2), I get a partition read error.  I give up.  I installed OpenSUSE, and it worked on the first try.  Their partitioner GUI didn't seem to understand the concept of nested RAID, but at least it activated the RAID in their installer, and let me specify which RAID partitions to format and use.

I miss Ubuntu already, but at least I have Linux again.  Maybe in a year Ubuntu will support nested RAID in their installer without having to jump through hoops.

:(

---

