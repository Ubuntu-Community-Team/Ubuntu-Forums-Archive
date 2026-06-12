---
title: "installing from live CD fails near end, no msgs shown"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by tmoble on 2007-08-31
dang, I'm tired of fighting with computers.

DL'd the live CD, ran the install, like at 90% the progress window disappears, no error msgs.  tried it twice now, when I reboot all I get is the word GRUB and blinking underline cursor.  no response, not the three finger salute from our friends in Redmond.

I know I can mount the FS from the live CD, but where to look for a log that might give a clue?  Not exactly new to linux, but new to Ubuntu so just a pointer is all I need.  /var/log/dmesg?  Does the install keep a log of it's own somewhere?

It's an ECS board with the cruddy imitation AGP slot, Ath 64 3500, 512MBs ram.  I'm not trying to do anything 64 bit and don't want to.  drive is a 20GB WD.  I ran the CD checker, OK.  ran the memtest, OK.

suggestions, pointers, laugh and point, all that welcome. 

BTW, I'm DLing the alt CD now.

---

### Post by Sef on 2007-08-31
1) Did you md5sum the download?

2)  Did you burn the cd at 4x or less?

---

### Post by tmoble on 2007-09-01
> **Sef said:**
> 1) Did you md5sum the download?

2)  Did you burn the cd at 4x or less?

neither, didn't know I needed to.  I did run the checker tool on the CD a couple times, it thought the CD was OK.  ran the memory checker for half hour, good there too.

DL'd and burnt the ALT install, ran it.  it locked up at about 75%

ran it again, it completed but the desktop locked, had to BRB

rebooted again, it came up and was OK but after awhile it got weird, started doing all of weird stuff in the terminal session.  cursor jumping around, wiping off command lines etc.  rebooted again, came and seems normal.

What this is all about:  I need to access a 2 disk RAID0 created on this same mobo under an XP install.

apt-get install dmraid, OK.  saw my two disk stripe set.  /dev/mapper has them with same names as they had in RHEL4.  still can't mount them though.  apparently dmraid is seeing them as two disks rather than a stripe set.  /dev/mapper I see control and the two disks named
crw-rw----  1 root root  10, 62 2007-09-01 00:07 control
brw-rw----  1 root disk 254,  1 2007-09-01 00:07 isw_cjcjcghegd_ARRAY
brw-rw----  1 root disk 254,  0 2007-09-01 00:07 isw_cjcjcghhah_ARRAY

in /dev I have sda, sdb and sdb1.  fdisk -l claims sda doesn't have a partition table.  sdb seems OK.  I would have guessed that sdb1 was the RAID partition, but feisty won't mount it.  here's the output of fdisk -l:
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19451   156240126    7  HPFS/NTFS

mount -t ntfs /dev/sda /mnt/winraid gives errors :
mount: /dev/sda already mounted or /mnt/winraid busy  neither is the case

or sdb:
mount: /dev/sdb already mounted or /mnt/winraid busy


I was really hopeful about sdb1:

 sudo  mount -t ntfs /dev/sdb1 /mnt/winraid
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try  dmesg | tail  or so\

per fdisk it's the right fs type, there are no options, ntfs drives don't have superblocks and I don't know about the code page stuff.  I think my feisty is using utf-8, dunno what XP uses. 

anybody know what sdb1 is if it's not the RAID partion?  there's only 2 sata disks.

cripes I've been posting on forums since 2400 baud Compuserv days, this has got to be the longest mess I've ever put up.

---

### Post by tmoble on 2007-09-01
a long, sordid tale, no doubt.  but, fixed.

discovered dmraid -r, it lists a lot of stuff about what dmraid finds.  mine was treating my via raid as   isw   raid, which is some kind of intel deal.  we don't need no stinking intel.

dmraid -ay -f via correctly discovered the the raid, I was able to mount it OK using normal mount commands.

---

