---
title: "getting raid to work?"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by shultzjr on 2006-10-29
The following in in the dmesg file:

[42949400.490000] SiI680: IDE controller at PCI slot 0000:00:0d.0

I have two 250G hd's connected to the pci controller card.

How do I partition and mkfs the drive?  fdisk doesn't see it.
There is a 3G hd as hda on the ide controller from the motherboard.
But linux didn't assign any way to address the 2) 250s.

How do I get this pci raid/ide card to work under linux?

thanks......

---

### Post by midtoad on 2006-11-08
if you run the Alt installer (get the Alt CD from the Ubuntu downloads page), it has options for configuring RAID.  Also see the how-to somewhere on this site.

---

### Post by wkulecz on 2006-11-08
Your pci controller should be /dev/hde /dev/hdf /dev/hdg /dev/hdh
If you don't see these in dmesg output after the system boots its hopeless.

I was totally unsuccessful to make SIL680raid PCI controller work on Ubuntu software raid (mdadm).  System found all the drives and I could start and sync the array (raid5 & raid1), install a filesystem (tried ext3 and xfs) but when I tried to copy over some data many files were corrupted.  I gave up when data was still being corrupted after creating only a single normal ext3 partition on a single drive

This card worked under W2K, its possible its just a fluke between this card and my MB, but don't bet the farm on using your SIL680 based on my experience.

I got three IDE to SATA adaptors for $13 each and setup my raid5 using the MB SATA ports.

The best mdadm raid setup instructions I found were on a Gentoo site. Use the search on my threads, I've posted the link.

Good luck!
--wally.

---

