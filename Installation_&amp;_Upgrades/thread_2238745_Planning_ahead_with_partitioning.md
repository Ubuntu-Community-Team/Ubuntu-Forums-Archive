---
title: "Planning ahead with partitioning"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by andrei11 on 2014-08-09
Hello,

I am planning a very slow transition to Ubuntu 14.04.1, dual-booting with Windows 7.
The Total amount of space I am dedicating to the whole ubuntu installation is 2 TB and my aim is to get rid (in time) of windows. 
This issue may be complicated or very simple but I aim to keep my Ubuntu Installation for at least 4 years, during wich time I plan to learn (try out many linux programs), and also alternative games to that what I might find in windows. I've read and calculated from the documentation that a 12.04 version of Ubuntu takes up around 25-30 Gigabytes for the Root alone including a 4 gig swap area for a 6 month intense usage.

This question is a two part issue: First for such a long period of time would I even be able to have or maintain a stable Ubuntu Linux environment ? (I am also considerind upgrading not reinstalling at each new major release of ubuntu) I ask this because I dont seem to get a long lasting life out of a tipical windows installation.

And second: If I were to succed in keeping Linux for 4+ years without reinstallation (not reformating the root partition) what are the ultimate space requirements for the root folder. (100 Gigs is to much or to small then optimal to install anything and try everything without worry even after several upgrades and the regular updates ?)

PS: I am still unsure if programs installed from the official repository and other packages from the Internet actually stay in root and not spill out into the home partion.

The scheme I am planning is simple: 4 Gigs for Swap, ??? Gigs for Root and the rest for home partion filling the entire 2 tb total for the whole filesystem.

This question is important because I am wary of resizing partions due to past expiriences in the past (with Windows partions).

Thanks in advance.

---

### Post by Bashing-om on 2014-08-09
andrei11; Hi ! Welcome to the forum and our world.

You are real early in the planning stages for long term care and use.
But here goes my thoughts and actions:
1) 30 Gigs for "root" is plenty and more than enough;
2) consider a separate /home directory, and later symbolic links to added partitions;
3) consider, for testing other distros of linux, there really is no need to install them ( though you can, and make provisions for that "testing" partition(s); directly boot the .iso file:
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot) <-Ubuntu ISOs are designed to allow booting directly from the hard drive using GRUB 2 and eliminates the need for burning a CD/DVD.
4) make up a couple of spare 50 gig partitions for expansion, future uses;
5) leave some space as "unallocated" just for whatever might cross your mind later.
For reference, my very long time in service set up, works for me very well !
```

sysop@1404mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  2.0G  2.6G  44% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  8.0K  1.9G   1% /dev
tmpfs           2.0G   12K  2.0G   1% /tmp
tmpfs           396M  744K  395M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G   15M  2.0G   1% /run/shm
none            100M  8.0K  100M   1% /run/user
/dev/sda8       4.7G  1.3G  3.2G  30% /var
/dev/sda2       9.5G  1.3G  7.8G  14% /home
sysop@1404mini:~$ 

---------------
sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux
sysop@1404mini:~$

--------sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:~$ 


```

If you really require "peace of mind" dual boot 'buntu on separate hard drives. Break one, the other is available for use .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by papibe on 2014-08-09
Hi andrei11. Welcome to the forums ):P

A few thoughts.

In general 25-30Gb would suffice for 4 years. Note that this would require some maintenance though (basically cleaning old kernels and header about every year) .

Games, including Humble Bundle and Steam, has change that. Games are installed on the root partition (/usr/bin, or /opt for instance), and can add up a lot depending on how many games you download.

There's no rules for games and software downloaded independently. They either go to root or stay in your directory.

The 'rule of thumb' for swap is matching your RAM.

Finally, all this can be change later. You can resize an existing partition, create a new one, etc. fairly easily.

As always, I'd recommend backup your personal data before modifying partitions.

Just my thoughts. I hope it helps.
Regards.

---

