---
title: "cannot create ext4 filesystem on Intel P55 SATA RAID 0 volume"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by remi_2 on 2010-06-05
Hi!
I've built  new machine with the following specs :

Intel Corei7 860
Gigabyte GA-P55A-UD4 1156 motherboard with bios F11
8Gigs of RAM

I've crammed 4 samsung F3 1Tb in there.

I assembled two RAID0 volumes using the hardware Intel P55 SATA manager on the mother board.

The first RAID0 volume is split in two, the first half has windows 7 on it, the second half was meant as the ubuntu root partition and linux swap. 

The second RAID0 volume is also split in two, the first half is NTFS, the second half was meant for linux swap and ubuntu  /home.

The alternate install CD encounters an error : 

"the creation of the ext4 filesystem on partition XX of SATA RAID isw_biefaceg_Volume0 (strip) has failed" so it cannot install.

I read about the fakeRAID issue so I tried to install using the liveCD, making sure that the dmraid package was present in synaptic, as it supposedly allows to handle fakeRAID systems (I wasn't sure whether the intel SATA RAID controller was a genuine of fake hardware RAID that needs support from the OS to function).

Anyway now I'm stuck ! What can I do to make ubuntu install on the hardware P55 SATA RAID?

Cheers!

---

### Post by darkod on 2010-06-05
I believe most desktop boards are fakeraid. Maybe a server board might have onboard hardware raid, but I doubt a desktop board would.

However, I always thought using the alternate cd is better than live cd for RAID. Unfortunately I don't have much experience with it, except short testing in Virtual Box, and I have no idea about that error.

How about trying the alternate cd and the filesystem to be ext3, just to see if it works. But even if that works, you should have the option to use ext4 too.

---

### Post by remi_2 on 2010-06-06
Hi!

I've tried different filsystems (ext2/3/4) none of them works.

I've found the fakeRAID wiki page which says we should use gparted to set up the paritions, but it does not see my raid volume, all it sees is 4 unpartitionned disks...

Alternate is better for setting up software raid.

---

