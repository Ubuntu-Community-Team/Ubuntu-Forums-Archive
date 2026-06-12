---
title: "Can´t install ubuntu on RAID array..."
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by KalaNag on 2008-09-03
Hi, and thanks for reading. This is the problem I have.

I have a PC with a Gigabyte 7NNXP motherboard (old machine for Athlon XP processors), in which I have the following configuration:

- A RAID 0 array, 2x 80GB SATA discs, with a NTFS partition with Windows XP. This array is controlled by a integrated Sil3112 chip.
- A IDE 250GB disc with a non-bootable FAT32 partition, connected to a integrated Gigaraid chip (ITE 8212 chip)

I had months running this configuration with Windows XP with no problems, and then I decide to install Ubuntu on this machine. I had already done it with clean installs in other PCs. So I start the livecd, and choose the "manual" partitioning. This is a sequence of what happened:

- Wizard correctly detects the Array and the other disc, with the partitions on it.
- I decide to install Ubuntu on the 250GB disc, on some unused space (no need to resize any partition)
- Installation happens normally. At the end, I check the Grub configuration in the advanced button and it sayd it is putting it in the sda0 (what I assume it to be the Array)
- PC restarts, and I get a GRUB error 21. Booting with the livecd and running gparted shows NO array, and instead shows both 80GB discs as separate drives. 250GB disc seems fine.
- Disconnect 250GB disc, as it has important docs in the FAT32 partition.
- I try to repair the Array's MBR with the XP installation cd, and I manage to boot again in windows after formatting the partition (I didn't want that installation anyway ;)). 
- I run partition magic software from windows and it tells me that "the mbr has errors: LBA is different to CHS values, it will be corrected using LBA values". It shows me that message three times, then it says that it can't determine drive letters and exits.
- Even after this, booting with livecd and runniong gparted still doesn't shows the array. BUT if I download and install dmraid, it shows the array under /dev/mapper, but still can't install, create or do anything related to the partition. Reading the error logs shows errors from ntfsresize...
- I wipe the array and create it again from the controller's bios. Re-install windows and partition magic, which now runs fine without errors or messages.
- Boot from livecd and... still doesn't shows the array, unless I install dmraid... and even so can't do anything partition-related. The NTFS drive doesn't shows on the list of mountable units.

Sorry for the wall of text. Any help you can give me will be greatly appreciated.

---

### Post by KalaNag on 2008-09-03
Bump? I still need help with this :(

---

### Post by Michael Barna on 2008-09-07
This is a good question and similar to one I have.

Anyone...?

---

### Post by listener on 2008-09-07
It sounds like a software RAID rather than true hardware.  Ubuntu doesn't always recognize.  I had to dismantle a RAID 1 nVidia RAID, but I am learning to dislike RAID more and more.  Better to keep backups. IMO  (MUCH better with RAID 0!)

good luck

---

### Post by rickyrockrat on 2008-10-04
Try:
[http://hol.net.nz/blog/kubuntu-with-fakeraid](http://hol.net.nz/blog/kubuntu-with-fakeraid)

If you don't need windows, use the Linux software raid, which uses the disks with out the raid controller.

You're crazy to run Raid 0!

---

