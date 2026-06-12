---
title: "Software RAID5 initial setup issues"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by bigtex on 2005-11-20
Hi.  This is my first post here, and my first time installing Ubuntu.  I'm actually typing right now using the 5.10 live CD because I couldn't complete installation.

I'm trying to set up a software RAID 5 array.  I have a VIA EPIA M10000 (C3 Nehemiah processor, 1.0 GHz) with 512MB RAM.  I'm using four identical Seagate 120 GB Parallel ATA drives.  I have the drives connected to the on-board IDE channels and I'm using a Maxtor/Promise ATA133 PCI card temporarily to have a CD drive attached.  My eventual goal is a headless fileserver, so I won't need the CD drive later.

In the installer's partitioning tool, I've identified each drive as a physical RAID volume.  Then I created a software RAID 5 array with 4 drives, no spares, and selected all four drives.  After that, I've had loads of problems.  I've tried every way I can think of to create partitions, but I always end up with an angry red screen at the end of formatting the partitions.  The error is vague but tells me that it couldn't write the filesystem or couldn't format the partition or something like that.

I've tried the guided partitioning option, which creates a root "/' and a swap, with the root being primary and bootable.  Ext3 seems to be the default, but that never works.  I've tried formatting with Ext2, ReiserFS, and XFS, but I get similar errors.  There were a few times I think I got a sucessful partition made, but I hadn't made it bootable so I had to start over.  Also strange is that I never get the option to select primary/logical or enable making a disk bootable unless I run the guided partitioning tool first.

Is there a particular filesystem that works better on a software RAID 5 array?  Should I have a seperate, non-RAID disk for a boot drive?  What am I doing wrong?

---

### Post by bigtex on 2005-11-20
Is it possible to boot off of a RAID5 array, even?

---

