---
title: "Hard Drive Partitions"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by nick334 on 2008-07-12
Right, I'm getting my new computer soon and I want to dual boot XP and Ubuntu. The last time I tried installing Linux I rushed straight into it without thinking and managed to format my hard drive by accident :icon_frown::oops:

The hard drive will be 320GB and I've asked for it to be partitioned into 40GB, 40GB and 220GB drives. I wanted the OS on the first partition, programs on the second and media on the third.  I haven't ordered an OS but I have an XP disc and an Ubuntu 8 disk.

How shall I set everything up? I understand I need a root partition, a swap partition and maybe a home partition. By having media (music, films etc.) on a separate partition drive ("E:") will I be able to access them from both Ubuntu and XP? Does it need to be a special format or is NTFS fine? I don't want to use FAT32 as I have .MKV files bigger than 4GB.

Can someone please give me like a plan on how to partition my OS partition of 40GB? 

Thanks.

---

### Post by avtolle on 2008-07-12
Have a read of this [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) for some general ideas and thoughts. On the OS partition, install XP first (15 gb?), Ubuntu on / (root) second, about 5 gb or so if using a separate /home, otherwise make it larger, /swap (automatic installer usually installs at 1.5 to 2 x RAM, if you have more than 1 gb RAM, make it equal to RAM if planning to hibernate or suspend, otherwise 512 mb should be sufficient IMHO), and if using a separate /home, have it use the rest of the space on that partition. 

As it appears that there will already be three physical partitions on the drive, there is going to be an issue with the four physical partition limit; is the media partition going to be a "logical" partition? 

As to the shared data partition, NTFS should be fine.

---

### Post by nick334 on 2008-07-12
I will have 2GB of RAM so I'll make a 4GB /swap. Does /home store the settings so you can just do a clean reinstall and it'll be the same? 

I'm not sure what a logical partition is, can you explain please?

---

### Post by nick334 on 2008-07-12
I will have 2GB of RAM so I'll make a 4GB /swap. Does /home store the settings so you can just do a clean reinstall and it'll be the same? 

I'm not sure what a logical partition is, can you explain please?

---

### Post by avtolle on 2008-07-12
Bad phrasing; should have said "logical partition within an extended partition", which, as I understand things Linux wise, an extended partition allows creation of "virtual" rather than "physical" partitions on the disk, referred to as logical partitions. I'm totally unaware of how Windows handles these things (presuming the partitioning you requested is being done under a Windows schema), but from reading, etc., I'm aware of the fact that on a HDD one may have four "physical" partitions, or three "physical" partitions and one extended partition, and under the extended partition (depending upon how the drive is identified) there may either be an unlimited number of logical partitions unless the drive is id'd as a SCSI drive, which has a 15 "drive" limit in a chain. 

With 2 GB RAM, your Swap partition need not be any larger than 2 gb, and may be smaller if you do not plan on using hibernate.

---

### Post by YaroMan86 on 2008-07-12
Here's how I partition, or used to. About 20 to 30 GiB for XP, 15 for Ubuntu, 5 for swap.

The rest you format as ext2, download and install the ext2 IFS driver on Windows XP, then change your /home to the biggest partition in the fstab. That's your chared and home partition.

Of course, if you use Windows heavily, you might wanna put it on its own hard disk, since most applications for Windows nowadays are quite large.

---

### Post by avtolle on 2008-07-12
To respond to your other question about /home; yes, your settings and data files are stored there, which makes a subsequent clean install go more easily. There's a bit of debate in the community about using a separate /home, as some feel this lulls the user into a false sense of security and therefore, the user doesn't back up the files as should be done; others feel that creation of a separate /home is self-limiting on the user, as once the partition is full, the user must take some action to clean it out or not have an operable system, even though there is space available on the remainder of the HDD; thus, some recommend only having a / and /swap, with regular backups of the /home folder (directory, to those of us with a bit of age) to external media as being sufficient. I have a separate /home on three of my four Linux OS; on another, I don't (kind of experimenting here). Whether to have a separate /home is your choice.

---

