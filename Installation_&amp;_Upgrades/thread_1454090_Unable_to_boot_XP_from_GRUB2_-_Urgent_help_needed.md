---
title: "Unable to boot XP from GRUB2 - Urgent help needed"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by betruger on 2010-04-14
i have two hdd dual booting with xp and ubuntu 

i have installed both the os in the 1st hard disk (hd0)
sda1= winxp
sda6 = ubuntu 10.4 (beta2) 


my config

---------------------------------------
Disk /dev/sda: 80.0 GB, 80032038912 bytes
255 heads, 63 sectors/track, 9730 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe3657373

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/sda3            7019        9730    21784140    5  Extended
/dev/sda5            7020        7262     1951897+  82  Linux swap / Solaris
/dev/sda6            7263        9730    19824178+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        7013    56323890    f  W95 Ext'd (LBA)
/dev/sdb2            7014       46532   317436367+   7  HPFS/NTFS
/dev/sdb3   *       46533       49082    20480000    7  HPFS/NTFS
/dev/sdb4           49082       60801    94134816+   7  HPFS/NTFS
/dev/sdb5               2        7013    56323858+   7  HPFS/NTFS

--------------------------------------------------------------------

details of my HDD UID

/dev/sda1: LABEL="WINXP" UUID="6270DE7670DE5101" TYPE="ntfs" 
/dev/sda5: UUID="0c78843e-a8d9-4a05-b197-d94b6d911455" TYPE="swap" 
/dev/sda6: UUID="ae702955-2b5f-4f4d-a7d0-c7ff2dfeea9c" TYPE="ext4" 
/dev/sdb2: LABEL="GAMEZ" UUID="70A4BA86A4BA4DFA" TYPE="ntfs" 
/dev/sdb3: LABEL="DUMP2" UUID="469820589820492F" TYPE="ntfs" 
/dev/sdb4: LABEL="DUMP" UUID="7CA006E1A006A1AE" TYPE="ntfs" 
/dev/sdb5: LABEL="MUSIX" UUID="F0C8E71FC8E6E338" TYPE="ntfs" 

-----------------------------------------------------------


after day long googling, i edit grub2 loader as follows;

add the following line in 40_custom file in order to add winxp boot entry;

-----------------------

menuentry "Windows xp (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 6270DE7670DE5101
	drivemap -s (hd0) %{root}	
	chainloader +1
}

---------------------------
while updating grub2, grub.cfg find the xp partition successfully.
but after rebooting and loading xp it left blank and returned grub boot loader menu.. 

now i am in lot of confusion.. 

pl help me urgently..

---

### Post by plucky on 2010-04-14
> menuentry "Windows xp (loader) (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 6270DE7670DE5101
drivemap -s (hd0) %{root}
chainloader +1
}



My entry looks like ```
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
	insmod ntfs
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 4c50fb0750faf714
	drivemap -s (hd0) ${root}
	chainloader +1
}

```

It has a $ in front of the {root} not a %

Good Luck

---

### Post by betruger on 2010-04-15
tried.. no use 
:confused:

---

