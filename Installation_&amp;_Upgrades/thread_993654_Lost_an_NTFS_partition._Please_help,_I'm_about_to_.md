---
title: "Lost an NTFS partition. Please help, I'm about to cry."
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Omega Destroyer on 2008-11-25
I will give as brief an explanation of what happened as possible.

I have 4 drives in my computer. One has has windows installed on it. A second drive was split up into 3 partitions. 1 NTFS partition, 1 ext3 partition and 1 swap partition. I already had Ubuntu installed on it.

I decided to do a clean install on 8.10 on the SAME partition that 8.04 was installed on. I chose manual partitioning in the options and chose the EXT3 partition on my second drive as the root folder. I formatted that partition and the install went well, but when I booted back into Windows, the NTFS volume is now gone. It shows up in the disk management window, but it's not NTFS anymore (although fdisk -l in Unbuntu says that it is).

I have over 70 000 photos on that partition, many of which are from weddings from my clients. I need them back. Please tell me that it was only the table of contents that was changed by Ubuntu. I didn't tell it to touch that partition at all, it was only supposed to install on the 2nd and third partitions. 

I know next to nothing about Linux, so I need explicit instructions on how to fix this. Please tell me I didn't just lose everything.

---

### Post by Omega Destroyer on 2008-11-26
Okay I was able to fix the problem. Just in case anyone else runs into the same problem, I'll give a brief explanation of how I fixed it.
I used the testdisk software downloaded from here:

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

After choosing the correct disk, and filesystem, I went to the advanced tools and restored the backup MBR with the one that Ubuntu created and restarted my computer. This brought the disk back to life. I can't boot into Ubuntu anymore, but I'm not too concerned about that, as long as I get all my photos back.

---

### Post by TFX360 on 2008-11-26
Backup, BACKUP, *BACKUP*, **BACKUP**!!!

---

