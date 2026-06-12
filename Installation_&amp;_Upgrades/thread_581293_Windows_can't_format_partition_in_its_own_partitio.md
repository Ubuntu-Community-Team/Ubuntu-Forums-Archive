---
title: "Windows can't format partition in its own partition manager"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Cinot on 2007-10-19
Well, after a few hours of trying to solve problem, it drives me insane!

After I've installed Xubuntu 7.10, I've decided to install Windows for gaming purpose.

XP's installator didn't even launch. Just for two seconds I saw a message about preparing and then a black screen shown. I've readed somewhere it's caused by partition conflict. Well. whatever, I've tried with Windows 2000 and it did launch.

The next problem is there where's partition manager. I selected a partition that was created for this OS via gparted and for some reason it was called as "Unformatted or corrupted". Of course, installator couldn't format it, thus refusing to install OS.

There's fdisk -l output:

```

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1               1          13      104391   83  Linux 
/dev/sda2              14        1983    15824025   83  Linux 
/dev/sda3            1984        3557    12643155    7  HPFS/NTFS 
/dev/sda4            3558       38913   283997070    5  Extended 
/dev/sda5            3558        4876    10594836   83  Linux 
/dev/sda6            4877       32310   220363573+  83  Linux

```

Short descriptions:

sda1 - boot partition
sda2 - partition with main directory (/)
sda3 - partition for Windows system
sda4 - extended partition, which contains:
->sda5 - /home partition
->sda6 - storage partition
->sda7 - windows storage partition (which is unformatted, so it isn't shown in fdisk -l)

/etc/fstab output:

```

proc /proc proc defaults 0 0 
# Entry for /dev/sda2 : 
UUID=28cf0464-81f7-4bf9-aa1e-f9376e91b1aa / xfs defaults 0 1 
# Entry for /dev/sda1 : 
UUID=69cb4eb8-2768-498d-bfba-28250be6c142 /boot ext3 defaults 0 2 
# Entry for /dev/sda5 : 
UUID=ad3e2bf7-cf61-4dad-af60-a0e52e7e2911 /home xfs defaults 0 2 
/dev/sda6 /media/storage ext3 defaults 0 2 
#/dev/sda3 /media/winxp ntfs umask=222,utf8 0 1 
#/dev/sda7 /media/games ntfs umask=222,utf8 0 1 
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0 

```

Now, I'm going to describe problem. The point is, as I've said, I can't install windows on sda3 because of partition problem. Installator says funny things like possibility of destroyed partition or terminator being connected to SCSI disc and et cetera.

After playing few hours with my PC's humour, I've come to clue that after doing those the most important thing:

1). disabling window partitions in fstab
2). unmounting window partitions in Xubuntu
3). unchecking options in ntfs-config
4). rebooting in cultural way
5). putting gparted LiveCD and formatting window partitions to NTFS 
6). rebooting and booting windows installator

I can't still install windows.

I have no idea, why it doesn't work. Xubuntu doesn't use window partitions, even it they're unformatted, installator can't format them. I have unclear feeling that Xubuntu somehow 'reserves' those partitions before windows installator boots.

The possibility of destroyed partition is small, since I have hard disc for two weeks.

Please not to tease me with installing windows OS before ubuntu. Before I thought it's a matter of GRUB issue, but since it requires only three commands in Live CD to solve this problem, I wasn't bothered what I install first.

The another alternative is to plug another hard drive and copy all files, delete whole disc, create partitions and install windows first. But, since it's a workaround, takes a lot of getting hard drive working and time of copying and configuring new xubuntu, I would rather to ask you if there's a solution.

---

### Post by Rivindu on 2008-06-12
I'v got a similar problem. 

I'v just got Ubuntu 8.04 LTS Desktop Edition (64-bit) and after installing it, i got an error trying to access windows vista. An error msg came up (which I cannot remember),I also tried the 'repair startup' in vista disk but didn't work. so I decided to reinstall vista.  When i got to the partition step, windows said I couldn't install windows on my old c: drive. I decided to try booting up again. This time ubuntu also failed to load.
I tried a couple of things after this but nothing was successful:
   I formatted c: - windows said windows still can't be installed          on c:, but i can access c: on command prompt. 
   I formatted the disk including the 1 i installed ubuntu with live CD as NTFS then just left it unpartitioned. Nothing worked. Windows even said that it couldn't find any disks on the computer once. 
 
I fortunately backed up my data with command prompt. Even formatting the partioions didn't work. Please help! 
  I won't mind even if it is a way of making my hard disk back to factory standards.

---

