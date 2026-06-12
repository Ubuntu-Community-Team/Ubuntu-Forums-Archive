---
title: "Problems Mounting Hardware RAID after reboot"
date: 2010-06-21
forum: Installation &amp; Upgrades
---

### Post by defunkt on 2010-06-21
hey guys,  

most of the time i can find out problems just with a quick Google search, but this one has had me stumped for a few days now.  

Ive built a new file server and am migrating my data too it.

i have a hardware raid controller, with 6 2TB drives in a raid 5.  i have created a GPT partition table and setup a JFS file system (for ease of expansion in the future).

works great until i reboot, and then it refuses to auto mount (via fstab), and when i manually mount the drive i get:

mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Ive tried:

sudo mount /dev/sdb /RAID
mount: you must specify the filesystem type

sudo mount -t jfs /dev/sdb /RAID
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


i have also tried sdb1 instead of sdb (although i thought jfs wrote to teh raw drive and not the partition, sdb1 does exist in /dev)

im not new to raid, and Ive been working with ubuntu for years, but i cannot seem to figure this one out.  Ive formatted this partition about 6 or 7 times trying to find a solution.  

i know choosing a file system has had several heated discussions on which one to choose any why, and i don't really care which one i use as long as it's not super complicated to expand the partition.  

the raid card is a Areca 1680IX but im pretty sure the problem isn't the raid card.
im running 9.10 32bit desktop edition



any ideas would be greatly appreciated.

---

### Post by defunkt on 2010-06-21
update...  in some reading i found jfs_tune -l...

sudo jfs_tune -l /dev/sdb1
jfs_tune version 1.1.12, 24-Aug-2007

JFS filesystem superblock:

JFS magic number:	'JFS1'
JFS version:		1
JFS state:		mounted
JFS flags:		JFS_LINUX  JFS_COMMIT  JFS_GROUPCOMMIT  JFS_INLINELOG  
Aggregate block size:	4096 bytes
Aggregate size:		15624452896 blocks
Physical block size:	512 bytes
Allocation group size:	16777216 aggregate blocks
Log device number:	0x811
Filesystem creation:	Sun Jun 20 18:09:52 2010
Volume label:		'RAID'

sudo umount /dev/sdb1
umount: /dev/sdb1: not mounted


the JFS volume says its mounted... even though it isnt... wierd.

---

### Post by defunkt on 2010-06-21
so after pulling all my hair out, it looks like it needed to be forced to do the fsck even though it was marked as clean: jfs_fsck -f /dev/sdb1

after that the drive mounted fine.

hope someone else gets sumtin out of this.

---

