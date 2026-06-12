---
title: "/home: waiting for /dev/disk/by-uuid STILL stops a clean boot « on: Today at 04:34"
date: 2010-01-05
forum: Installation &amp; Upgrades
---

### Post by 51m0n on 2010-01-05
OK 1 in 5 boots is successful. This is kubuntu 9.10.

I get the above message sometimes multiple times during a boot. It is not a hardware error, this system was fine under the previous install, and boots to windows without issue.

blah@blah:~$sudo blkid
/dev/sda1: UUID="5EFE92117E8C3E78" LABEL="Windows" TYPE="ntfs"
/dev/sda5: UUID="96CC1704CC16DE75" LABEL="Swap" TYPE="ntfs"
/dev/sda6: UUID="B030260A3025D85C" LABEL="Temp" TYPE="ntfs"
/dev/sda7: TYPE="swap"
/dev/sda8: LABEL="root" UUID="74b99dff-b914-473f-a99d-136774c2de04" TYPE="reiserfs"
/dev/sda9: LABEL="usr/local" UUID="ad51a4e4-136f-4dcc-b63a-1a16503eaf24" TYPE="reiserfs"
/dev/sda10: LABEL="var" UUID="7cea3db3-b2a6-404b-ba63-dda339acc932" TYPE="reiserfs"
/dev/sda11: LABEL="tmp" UUID="f156f8f7-9156-4b4a-8553-196b59b6a687" TYPE="reiserfs"
/dev/sda12: LABEL="home" UUID="cdb6aeaf-dfdd-4606-a776-2b67909e5b8d" TYPE="reiserfs"
/dev/sda13: UUID="F474764674760B9C" LABEL="Games" TYPE="ntfs"
/dev/sda14: LABEL="DROP ZONE" UUID="A847-BCC0" TYPE="vfat"
/dev/sda15: UUID="9E880E23880DFB13" LABEL="Data" TYPE="ntfs"
/dev/sda16: UUID="8A0C12C10C12A7E9" LABEL="Music" TYPE="ntfs"
/dev/sda17: LABEL="boot" UUID="1b373167-4440-405b-adb4-4d5f8c9c9b97" TYPE="reiserfs"

blah@blah:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda8 during installation
UUID=74b99dff-b914-473f-a99d-136774c2de04 /               reiserfs defaults        0       1
# /boot was on /dev/sda17 during installation
UUID=1b373167-4440-405b-adb4-4d5f8c9c9b97 /boot           reiserfs notail          0       2
# /home was on /dev/sda12 during installation
UUID=cdb6aeaf-dfdd-4606-a776-2b67909e5b8d /home           reiserfs defaults        0       2
# /mnt/windows/C was on /dev/sda1 during installation
#UUID=5EFE92117E8C3E78 /mnt/windows/C  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /mnt/windows/D was on /dev/sda5 during installation
#UUID=96CC1704CC16DE75 /mnt/windows/D  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /mnt/windows/E was on /dev/sda6 during installation
#UUID=B030260A3025D85C /mnt/windows/E  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /mnt/windows/F was on /dev/sda13 during installation
#UUID=F474764674760B9C /mnt/windows/F  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /mnt/windows/G was on /dev/sda14 during installation
UUID=A847-BCC0  /mnt/windows/G  vfat    utf8,umask=007,gid=46 0       0
# /mnt/windows/H was on /dev/sda15 during installation
#UUID=9E880E23880DFB13 /mnt/windows/H  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /mnt/windows/I was on /dev/sda16 during installation
#UUID=8A0C12C10C12A7E9 /mnt/windows/I  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /tmp was on /dev/sda11 during installation
UUID=f156f8f7-9156-4b4a-8553-196b59b6a687 /tmp            reiserfs defaults        0       2
# /usr/local was on /dev/sda9 during installation
UUID=ad51a4e4-136f-4dcc-b63a-1a16503eaf24 /usr/local      reiserfs defaults        0       2
# /var was on /dev/sda10 during installation
UUID=7cea3db3-b2a6-404b-ba63-dda339acc932 /var            reiserfs defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

blah@blah:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40566959    20283448+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2        40580190   156296384    57858097+   f  W95 Ext'd (LBA)
/dev/sda5        41126463    43167599     1020568+   7  HPFS/NTFS
/dev/sda6        43167663    47416319     2124328+   7  HPFS/NTFS
/dev/sda7        47416383    49517999     1050808+  82  Linux swap / Solaris
/dev/sda8        49518063    62107289     6294613+  83  Linux
/dev/sda9        62113023    72606239     5246608+  83  Linux
/dev/sda10       72606303    74707919     1050808+  83  Linux
/dev/sda11       74707983    76809599     1050808+  83  Linux
/dev/sda12       76809663    89374319     6282328+  83  Linux
/dev/sda13       89374383   116635679    13630648+   7  HPFS/NTFS
/dev/sda14      116648028   120824864     2088418+   b  W95 FAT32
/dev/sda15      120839103   137622239     8391568+   7  HPFS/NTFS
/dev/sda16      137622303   156295439     9336568+   7  HPFS/NTFS
/dev/sda17       40580316    41126399      273042   83  Linux

Partition table entries are not in disk order

//-----------
The last warning has always been there btw, I had to expand the size of the boot partition a long time ago.
Never been an issue before.

This is the weirdest distro! First time ever my broadcom chip worked ootb (this is an HP nx6125 with broadcom wifi), yet it cant boot 80% of the time, and every 45 minutes just freezes up.

Any help much appreciated, I 'm getting desperate!!!

---

