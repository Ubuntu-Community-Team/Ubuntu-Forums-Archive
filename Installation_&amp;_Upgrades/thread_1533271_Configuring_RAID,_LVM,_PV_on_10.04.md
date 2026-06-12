---
title: "Configuring RAID, LVM, PV on 10.04"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by checksum_failure on 2010-07-17
Hi all

I'm looking for some advice on configuring RAID, LVM and my physical volumes for a new 10.04 Server install (used mostly as a windows file server and print server).  My hardware setup consists of 2 identical 500GB hard drives.  My desired end state is:

[LIST=1]
[*]An ext4 root partition (20 GB) 
[*]A swap partition (2GB)
[*]A fat32 partition (450 GB) (to be accessed via Samba)
[*]The above all to be on RAID1 across the 2 disks
[/LIST]

The way I see it, the there are a number of possible ways to configure the above, and I am looking for some advice on the best (feasible) option:

[LIST=1]
[*]Create a single MD0 raid volume accross the entire two disks, and then create a single LVG across this, with 3 sepreate LVs, on for each partition above
[*]Create 2 physical volumes on each disk, create two raid volume on these (MD0, MD1), one for the LVG with two LVs for the Root and swap, a the other for the FAT32 partition (this seems like more work?)
[*]Other more suitable options?
[/LIST]

Any advice on these options (or others that may be more suitable) would be most welcome.

Cheers

---

### Post by jmate24 on 2010-07-17
it is best if you do not spread 2 or more partitions across a raid 0 (striping uses min of 2 disks) because if one of the HDD fails you loose twice your information. however it would be better if you had another 500GB HDD and create a raid 5 (striping w/parity uses min of 3 disks maximum space and safer). but you can get away with a raid 1 (mirroring no parity: most cost effective). but you only have half the space.

jmate24:D

---

### Post by checksum_failure on 2010-07-18
Thanks for the advice - I was planning on a RAID 1 array anyway - any thoughts on the LVM config?

---

### Post by dino99 on 2010-07-18
change fat32 by ntfs: better and easily used by ntfsprogs on linux side, and fs-driver on windoz side ([http://www.fs-driver.org/](http://www.fs-driver.org/))

[https://wiki.ubuntu.com/Raid](https://wiki.ubuntu.com/Raid)

---

### Post by checksum_failure on 2010-07-18
Cheers Dino99, following the links you pointed me to and I'm 55% through the install - will post some info once completed and tested (only thing is that you are not given the choice of installing a NTFS file system as part of the install options in 10.04, so I've just created an unformatted LV in addition to the swap and root LVs, and I'll configure it as NTFS once I'm cooking with gas.)

---

