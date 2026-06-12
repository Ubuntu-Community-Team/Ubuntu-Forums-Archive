---
title: "Dual Boot Questions-NTFS &amp; Partitioning"
date: 2006-09-12
forum: Installation &amp; Upgrades
---

### Post by WildcatRay on 2006-09-12
I have been unable to confirm this. It used to be that for dual boot systems, there NEEDED to be a FAT or FAT32 partition other than for data-sharing. It appears that this is no longer so. In other words, I can install my Win2K OS on an NTFS partition and then when I go to install U 6.06, there will be no problem because the install can't find a FAT/FAT32 partition. Is that correct?

Also, I have a brand new HDD. All the instructions say to resize the Windows partition to provide room for the U 6.06 installation. I would prefer to set up a partition for Windows with the rest of the HDD unpartitioned until I go to install U 6.06 and then let it do the appropriate partitioning for it then. Any problems with that approach?

---

### Post by WildcatRay on 2006-09-12
Bumping this up.

---

### Post by confused57 on 2006-09-12
> **WildcatRay said:**
> I have been unable to confirm this. It used to be that for dual boot systems, there NEEDED to be a FAT or FAT32 partition other than for data-sharing. It appears that this is no longer so. In other words, I can install my Win2K OS on an NTFS partition and then when I go to install U 6.06, there will be no problem because the install can't find a FAT/FAT32 partition. Is that correct?

Also, I have a brand new HDD. All the instructions say to resize the Windows partition to provide room for the U 6.06 installation. I would prefer to set up a partition for Windows with the rest of the HDD unpartitioned until I go to install U 6.06 and then let it do the appropriate partitioning for it then. Any problems with that approach?

I haven't read anything in this forum that a FAT partition is necessary for a dualboot with Windows & Ubuntu...I've only been using Linux since December, so I wasn't aware it was once needed to have a FAT partition.  Your preferred plan sounds like the best way to go.

---

### Post by WildcatRay on 2006-09-13
Thanks. It does seem that I can install Windows using an NTFS file system, which I have found to be much more stable than Win2K on FAT32.

---

### Post by cotcot on 2006-09-13
You do not need a FAT partition to be able to dual boot XP with Ubuntu. 
The discussion about about a FAT partition comes in when you want to share data between linux and windows. Generally a seperate partition for these data is suggested to be FAT because both linux and windows can read/write on FAT. I personally prefer the shared partition to be EXT3 instead of FAT. Using a ext3 driver in windows    (see [www.driver-fs.org](www.driver-fs.org)) makes it possible the write/read from windows on EXT3 without the 4 GB limit per file of FAT.
Writing from linux on NTFS is possible but not at all recommended.

---

### Post by WildcatRay on 2006-09-13
> **cotcot said:**
> You do not need a FAT partition to be able to dual boot XP with Ubuntu. 
The discussion about about a FAT partition comes in when you want to share data between linux and windows. Generally a seperate partition for these data is suggested to be FAT because both linux and windows can read/write on FAT. I personally prefer the shared partition to be EXT3 instead of FAT. Using a ext3 driver in windows    (see [www.driver-fs.org](www.driver-fs.org)) makes it possible the write/read from windows on EXT3 without the 4 GB limit per file of FAT.
Writing from linux on NTFS is possible but not at all recommended.
Thanks for this and the added tidbit about EXT3 for the data-sharing partition. :)

I just tried the link and got a server can't be found error. Do you if this is only a temporary problem?

Is the link supposed to be [www.fs-driver.org](www.fs-driver.org)?

---

