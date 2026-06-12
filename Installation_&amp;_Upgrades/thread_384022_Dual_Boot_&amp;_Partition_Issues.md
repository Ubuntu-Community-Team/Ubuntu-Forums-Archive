---
title: "Dual Boot &amp; Partition Issues"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by pseudosig on 2007-03-14
I'm relatively new to ubuntu and I'm trying to create a dual boot system with Windows and Ubuntu.

I have a 250 gig hard drive that I partitioned 80 gigs to Windows.  I left the remaining 170 gigs unformatted.

I then installed Windows XP on the 80 gig partition. 

I'm now in the Ubuntu install CD (booted off from CD... i.e. burned disk image) and I'm now at step 4 of 5 in the Ubuntu installer, where it is asking me to create my partions.

So with the remaining 170 gigs, I'm trying to make three partitions for: ext3, swap, and fat32.

When I click the forward button to create those partitions, I get a partion error that says the following:
[B]
"An error occurred while applying the operations"
"The following operation could not be applied to disk:
Create Primary Partition #1 (ext3, 79 GiB) on /dev/sda"[/B]

The details give a tree with the partion I was trying to make?

What could cause this error?  Windows had no problems partioning my dirve, so I doubt it's a bad drive... (maybe).

Thanks,
pseudosig

---

### Post by wonk-o-matic on 2007-03-14
I haven't faced this problem, so it's a bit of a guess.  

First off, it's unsettling that it is trying to create Primary Partition #1, which it seems to me would be your windows drive.  Exercise some caution.  

I've seen Windows do some weird formatting.  Linux seems to dislike partitions that cross cylinder boundaries (which is only natural.)  I'd let the installer resize my Windows partition just a tiny bit smaller, to get a more natural boundary, and see if that doesn't let the other partitions get created.

---

### Post by zvacet on 2007-03-14
Try manualy optoin and see if same error occur.

---

### Post by Kateikyoushi on 2007-03-14
Try to make an extended partition and make the 3 new partitions as logical in it.

---

### Post by pseudosig on 2007-03-15
I've tried everything listed above.  Manually trying to create the partitions fails in creating the partitions.  If I choose to use the largest continuous free space for installation, it fails in mounting the swap partition.

My computer is sort of bleeding edge... maybe an issue with Ubuntu on my new hardware?

This is what I have:
ASUS P5N32-E SLI Plus LGA 775 NVIDIA nForce 650i SLI ATX Intel Motherboard

Western Digital Caviar SE16 WD2500KS 250GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM

Intel Core 2 Duo E6600 Conroe 2.7GHz LGA 775 Processor Model BX80557E6600

2 X EVGA 512-P2-N637-AR GeForce 7950GT 512MB GDDR3 PCI Express x16 HDCP KO Superclocked Video Card (Total vid mem: 1024 MB)

G.SKILL 4GB(2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory Model F2-6400CL6D-4GBMQ

ASUS 16X DVD±R DVD Burner with 12X DVD-RAM Write and LightScribe Black E-IDE/ATAPI Model DRW-1612BL-BK - OEM

---

