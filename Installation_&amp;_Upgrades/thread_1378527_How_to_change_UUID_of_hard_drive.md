---
title: "How to change UUID of hard drive?"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by matthew_exon on 2010-01-11
I'm trying to make [backups]("http://jwz.livejournal.com/801607.html").  I bought my two new drives.  Even though I plan to use rsync to update the backups, I used dd to make the initial backups so that they would be bootable and to make sure the partitioning scheme is *exactly* the same.

This means that the UUIDs of the drives are identical.  So I need to change the UUID of the backup drives to something else.

How's this done then?

---

### Post by hanlin on 2010-01-11
tune2fs /dev/sda1 -U UUID

/dev/sda1 might have to go at the end. I don't remember exactly.

---

### Post by sisco311 on 2010-01-11
```
tune2fs -U random /dev/sdXY
```

for more info, read the man page:
```
man tune2fs | less +2/-U
```

EDIT: i'm slow... :)

---

### Post by matthew_exon on 2010-01-12
Thanks guys, just what I needed!

---

### Post by mahy on 2010-04-02
And what if it says this:

```
tune2fs /dev/sda1 -U 87de7cfe-5c84-4f54-b20d-90e4d9ac85b2
tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
```

Any ideas??

---

### Post by gsgleason on 2010-04-02
> **mahy said:**
> And what if it says this:

```
tune2fs /dev/sda1 -U 87de7cfe-5c84-4f54-b20d-90e4d9ac85b2
tune2fs 1.41.9 (22-Aug-2009)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
```

Any ideas??

It means it's not finding a second extended file system on that device.

Is it currently mounted?  Show us output of 'mount' and of 'sudo fdisk -l /dev/sda'

---

### Post by mahy on 2010-04-02
> **gsgleason said:**
> It means it's not finding a second extended file system on that device.

Is it currently mounted?  Show us output of 'mount' and of 'sudo fdisk -l /dev/sda'

Sorry for the panic, I already found the error. I've got a ReiserFS partition, so instead of "tune2fs" I had to use "reiserfstune". It works perfectly!

---

### Post by Herman on 2010-04-02
:D The title of this thread is misleading because you are asking 'how to change the UUID of a hard drive?', but you really mean 'how to change the UUID of a file system?'.

The hard disk has an ID number in the MBR, which we can see in out fdisk output, like this,
```
herman@ocz-lynx:~$ sudo fdisk -lu
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
[COLOR=Red]**Disk identifier: 0x389fe78f**[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1024   125033894    62516435+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
[COLOR=Red]**Disk identifier: 0x00080d93**[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1547300474   773650206   83  Linux
/dev/sdb2      1750346010  1953520064   101587027+  83  Linux
/dev/sdb3      1547300475  1750346009   101522767+  83  Linux

Partition table entries are not in disk order
```The file systems inside each partition have their own UUID number too, which can be see with the blkid command. :D

The 'Disk Identifier' in the MBR isn't very important for Ubuntu users, but it could be if we're dual booting with Windows 7 or Vista.
The BCD boot loader is fatally tied to this number, called 'the 'NT drive serial number', (which is their terminology for 'Disk Identifier').

We can see a different representation of our MBR's 'Disk Identifier' using the dd command as follows, 
```
herman@ocz-lynx:~$ sudo dd if=/dev/sda count=1 | hexdump -C
00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 01 00 00 00  |................|
00000060  00 00 00 00 ff fa eb 07  f6 c2 80 75 02 b2 80 ea  |...........u....|
00000070  74 7c 00 00 31 c0 8e d8  8e d0 bc 00 20 fb a0 64  |t|..1....... ..d|
00000080  7c 3c ff 74 02 88 c2 52  bb 17 04 80 27 03 74 06  ||<.t...R....'.t.|
00000090  be 88 7d e8 1c 01 be 05  7c f6 c2 80 74 48 b4 41  |..}.....|...tH.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  [COLOR=Red]**8f e7 9f 38**[/COLOR] 00 00 80 00  |...<.u.....8....|
000001c0  01 01 83 fe ff ff 00 04  00 00 a7 d9 73 07 00 00  |............s...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000430378 s, 1.2 MB/s
```So, as you can see, the Disk Identifying number is located within the first 446 bytes of the partition table along with the boot loader code, just before the partition table.

Anyone can make a backup of the first 446 bytes of their MBR with a dd command similar to the folowing,
```
sudo dd if=/dev/sda of=/home/ubuntu/080525MBR.img bs=446 count=1
```Where: 'ubuntu' is the username, (for example when using a live CD), or else replace with your own username as appropriate.

This would be important to do if a person needs to clone Windows 7 or Vista from a dying hard disk drive to a new hard disk, as it won't boot unless it has the copy of the original disk identifier in the MBR of the new hard disk. 
After using a dd command to copy the Windows 7 or Vista partitions, and another to copy the backup MBR backup to the MBR of the new hard disk, then a person could re-install GRUB if they like and GRUB will not overwrite the 'Disk Identifier'.

Probably a hex editor could be used to edit the disk identifier if for some reason somebody might want to do that for some reason, I'm only guessing. :D

---

### Post by mahy on 2010-04-03
Herman, you're most certainly right, but what you're suggesting is far more than OP and me need. :) Anyway, your GRUB howtos are splendid, thanks a lot! :KS

---

### Post by Nipplebeards on 2013-04-16
Herman, Wow. Just wow. Glad I bumped into this thread. Bit of a cookbook Ubuntu user here and I can verify that Windows does not like to see two drives with the same disk identifier. I am not anticipating a response to the following 3 questions.

1) Thank you
2) Why did my RAID5 on PCI card adopt the disk ID of my previous windows volume? I dd'd said windows onto array as a whole disk (90 gb onto 1500 gb array) and it made itself into a partition. I know, I know thats what dd is but it's only one partition. Does this mean first bytes are all that matters?
3) Had I not instructed the array to identify itself using the old windows identifier, where does the disk identifier come from?

Thank you so much. I hope I understand this someday.

---

### Post by QIII on 2013-04-16
From the Forum CoC:

> If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

Thread closed.

---

