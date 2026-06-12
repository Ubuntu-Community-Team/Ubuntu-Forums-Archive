---
title: "Running out of space on my system drive"
date: 2016-09-07
forum: Installation &amp; Upgrades
---

### Post by seanbw2 on 2016-09-07
I have enough hard disk space but chose to install in the smallest hdd I had - 320GB. Yes STUPID I know.
Now I am running out of space and Ubuntu is so slowwwww.
I tried to clone the system disk to another drive but after a day of grub getting stuck and just flashing its cursor at the logging into Drive C.., I gave up and managed to log back into my original disk, I decided it was better to ask for help.
Is it possible to leave my system disk as is and then join that to another hard drive?
I read on the forum about something called LVM but i really have no idea how to go about it.
The current structure is HP Gen 8 server with 5 disks. sda and sdb are each 4TB each. sdc and sde are each 3TB each. The system disk is on sdg.
Is it possible to retrospectively create sdg and sda as LVM disks so that the excess flows into sda?
To complicate matters, I have snapraid and mergerFS on the other 11 hdds but since these are already formed into a pool, I am hoping it won't impact the LVM solution?
Or am I doomed?
I cannot afford to reinstall as I have a lot of programs already set up.
Any help will be appreciated.
many thanks

sean

---

### Post by TheFu on 2016-09-07
Storage isn't tightly bound to the OS or applications or settings.  As long as the files "appear" to be where they should, the OS just doesn't care.

You can always reinstall - after all, what will you do when too many disks fail?  Go to the backups.  A backup should restore config, apps, data where it needs to be.

Unix systems don't like full disks - especially for /var/.  /usr and be 100% full and not impact performance, but /var/ can't get full.  If /boot/ is full, kernel updates can fail - mid-stream. That makes for a less-good day.

Anyway ... we need concrete data to be any real help.  The output from **lsblk** and **parted -l** would be very helpful to start. Please use "code tags", so the output is readable.

---

### Post by seanbw2 on 2016-09-08
```
 NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTsda      8:0    0   3.7T  0 disk 
&#9500;&#9472;sda1   8:1    0   3.3T  0 part 
&#9500;&#9472;sda2   8:2    0  37.5M  0 part 
&#9500;&#9472;sda3   8:3    0   301M  0 part 
&#9492;&#9472;sda4   8:4    0 374.4G  0 part [SWAP]
sdb      8:16   0 298.1G  0 disk 
&#9500;&#9472;sdb1   8:17   0 268.1G  0 part /
&#9500;&#9472;sdb2   8:18   0     3M  0 part 
&#9500;&#9472;sdb3   8:19   0   301M  0 part 
&#9492;&#9472;sdb4   8:20   0  29.7G  0 part [SWAP]
sdc      8:32   0  60.1G  0 disk 
&#9492;&#9472;sdc1   8:33   0  60.1G  0 part /media/usb1
sdd      8:48   0   256M  1 disk 
&#9492;&#9472;sdd1   8:49   0   251M  1 part /media/usb0
sde      8:64   0  29.8G  0 disk 
&#9492;&#9472;sde1   8:65   0  29.8G  0 part /mnt
seanbw@nas:~$ 



```

```




Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 0309927D-30D3-40FC-9C63-233574B24085


Device          Start        End    Sectors   Size Type
/dev/sda1      624640 7028220107 7027595468   3.3T Linux filesystem
/dev/sda2  7028220108 7028296905      76798  37.5M BIOS boot
/dev/sda3  7028296906 7028913353     616448   301M EFI System
/dev/sda4  7028913354 7814037134  785123781 374.4G Linux swap


Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.
Partition 4 does not start on physical sector boundary.




Disk /dev/sdb: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 0309927D-30D3-40FC-9C63-233574B24085


Device         Start       End   Sectors   Size Type
/dev/sdb1     624640 562849791 562225152 268.1G Linux filesystem
/dev/sdb2     618496    624639      6144     3M EFI System
/dev/sdb3       2048    618495    616448   301M EFI System
/dev/sdb4  562849792 625141759  62291968  29.7G Linux swap


Partition table entries are not in disk order.




Disk /dev/sdc: 60.1 GiB, 64490569728 bytes, 125958144 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x041c0717


Device     Boot Start       End   Sectors  Size Id Type
/dev/sdc1  *     2048 125958143 125956096 60.1G  c W95 FAT32 (LBA)




Disk /dev/sdd: 256 MiB, 268435456 bytes, 524288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000046


Device     Boot Start    End Sectors  Size Id Type
/dev/sdd1          63 514079  514017  251M  c W95 FAT32 (LBA)




Disk /dev/sde: 29.8 GiB, 32015679488 bytes, 62530624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x09ec127b


Device     Boot Start      End  Sectors  Size Id Type
/dev/sde1  *     2048 62530623 62528576 29.8G  c W95 FAT32 (LBA)



```

---

### Post by seanbw2 on 2016-09-08
parted -l did not do anything so I tried fdisk -l

/dev/sdb is the system disk.
/dev/sda is where I cloned it to but it did not work so i am back to /dev/sdb as my system drive.
I have shut down the other drives to save space.
Many thanks for responding.

---

### Post by TheFu on 2016-09-08
**parted** needs elevated privileges. fdisk has issues and really shouldn't be used anymore. Wish they'd stop teaching that and plain FTP servers. Both should die.

Appears you have a bunch of flash drives connected. Please remove those. They shouldn't be part of this issue.
BTW, the swap is entirely too big. 4G is the size for swap needed unless you hibernate. Hibernation is bad security-wise, so I never do it.

I bet the answer is simple.
/ 25G
swap 4G
/home - whatever is left.  Then add symbolic links to the other storage.
/boot 1G

I strongly suspect you've just filled up /home with crap that shouldn't be there on a server. Put it somewhere else.  That includes all media (audio/video/images) files, games, everything that isn't relatively tiny.  I'd keep documents and settings in ~/, but almost everything else belongs elsewhere.

Oh ... and please, please, please, please get backup religion ASAP.

---

### Post by seanbw2 on 2016-09-08
```
seanbw@nas:~$ sudo parted -l[sudo] password for seanbw: 
Model: ATA Hitachi HDS5C404 (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name          Flags
 1      320MB   3598GB  3598GB  ext4            GenG1610T001
 2      3598GB  3598GB  39.3MB                  bios_grub     bios_grub
 3      3598GB  3599GB  316MB   fat32           efi_boot      boot, esp
 4      3599GB  4001GB  402GB   linux-swap(v1)  linux-swap




Model: ATA Hitachi HCC54323 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size    File system     Name          Flags
 3      1049kB  317MB  316MB   fat32           efi_boot      boot, esp
 2      317MB   320MB  3146kB                  bios_grub     boot, esp
 1      320MB   288GB  288GB   ext4            GenG1610T005
 4      288GB   320GB  31.9GB  linux-swap(v1)  linux-swap




Model: HP iLO Internal SD-CARD (scsi)
Disk /dev/sdc: 64.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      1049kB  64.5GB  64.5GB  primary  fat32        boot, lba




Warning: Unable to open /dev/sdd read-write (Read-only file system).  /dev/sdd
has been opened read-only.
Model: HP iLO LUN 01 Media 0 (scsi)                                       
Disk /dev/sdd: 268MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  263MB  263MB  primary  fat32        lba





```

Thanks for the response.
The output from parted -l is as above.

/dev/sdb is the system disk and it has only 39G as swap so I am assuming that this is OK.
I have tried to use the other disks as much as possible using home for the bare essentials but some applications insist on using it and as this is a nas, I do have a lot of them.
Let me do a listing of my home folder.

```
root@nas:/home/seanbw# ls -lstotal 148264
   96 -rw-r--r--   1 seanbw root    95023 Aug 30 02:40 166607-polar-night.tar.gz
  676 -rwxrwxr-x   1 seanbw root   692184 Aug 26 22:19 20160826111943.nzb.zip
    4 -rw-r--r--   1 seanbw root       26 Aug 26 22:20 20160826111943.nzb.zip:Zone.Identifier
  484 -rwxrwxr-x   1 seanbw root   492541 Aug 26 17:22 AniAdd.jar
    4 -rw-r--r--   1 seanbw root       26 Aug 26 17:22 AniAdd.jar:Zone.Identifier
    4 drwxr-xr-x   4 seanbw root     4096 Aug 26 16:25 AnimDB
 2396 -rwxrwxr-x   1 seanbw root  2452086 Aug 26 16:15 AOM_0.5.18.276.zip
    4 -rw-r--r--   1 seanbw root       26 Aug 26 16:15 AOM_0.5.18.276.zip:Zone.Identifier
 2296 -rw-r--r--   1 seanbw root  2349107 Aug 30 02:17 arc-theme-master(1).zip
 2296 -rw-r--r--   1 seanbw root  2349107 Aug 30 02:16 arc-theme-master.zip
    4 drwxrwsr-x  21 seanbw root     4096 Aug 11 10:49 AtoMiC-ToolKit
    0 lrwxrwxrwx   1 seanbw root       25 Jun 22 17:56 Box -> /mnt/data/Gen/GenPool/Box
    0 lrwxrwxrwx   1 seanbw root       32 Jun 22 18:01 Comics -> /mnt/data/OricO/OricoPool/Comics
    4 drwxrwxr-x   2 seanbw root     4096 Aug 26 22:24 Desktop
    0 lrwxrwxrwx   1 seanbw root       31 Jun 22 17:54 Documents -> /mnt/data/Gen/GenPool/Documents
    4 -rw-r--r--   1 seanbw root      558 Aug 27 01:00 download
    0 lrwxrwxrwx   1 seanbw root       38 Aug  6 22:50 Downloads -> /mnt/data/StarT/1StarTech005/Downloads
   12 -rw-rw-r--   1 seanbw root     8980 Jun  9 22:42 examples.desktop
24220 -rw-r--r--   1 seanbw root 24801145 Aug 30 02:11 faenza-icon-theme_1.3.zip
   16 -rw-r--r--   1 seanbw root    14233 Aug 30 02:27 FantasyBlue-Xfce.tar.bz2
  676 -rw-r--r--   1 seanbw root   691267 Aug 30 02:29 flatts_09022014_by_nale12-d75r2c9.zip
   32 -rw-r--r--   1 seanbw root    31784 Aug 30 02:28 Fugitive_pack.tar.gz
   12 -rwxr-xr-x   1 root   root    10516 Aug  6 17:00 fupp upgrades
    0 lrwxrwxrwx   1 seanbw root       28 Jun 22 17:57 GDrive -> /mnt/data/Gen/GenPool/GDrive
    4 drwxr-xr-x   3 seanbw root     4096 Aug 26 00:28 grive
  912 -rw-r--r--   1 seanbw root   931198 Aug 30 02:14 iris_light_gtk_theme__v1_7_5_by_thevirtualdragon-d73dv3h.targz
   12 -rw-r--r--   1 seanbw root    10186 Aug 17 18:12 kodi_crashlog-20160817_181159.log
    8 -rw-r--r--   1 seanbw root     6566 Aug 17 18:17 kodi_crashlog-20160817_181727.log
   12 -rw-r--r--   1 seanbw root    10185 Aug 27 22:01 kodi_crashlog-20160827_220053.log
   12 -rw-r--r--   1 seanbw root    10186 Aug 28 21:35 kodi_crashlog-20160828_213443.log
    8 -rw-r--r--   1 seanbw root     7588 Aug 30 02:38 launcher-list-indicator-master.zip
    0 lrwxrwxrwx   1 seanbw root       29 Jun 22 17:59 Library -> /mnt/data/Gen/GenPool/Library
  768 -rwxrwxr-x   1 seanbw root   786016 Aug 26 16:09 msxml4msms.exe
    4 -rw-r--r--   1 seanbw root       26 Aug 26 16:11 msxml4msms.exe:Zone.Identifier
   24 -rwxrwxr-x   1 seanbw root    23086 Aug 26 16:09 MSXML4SP_RelNote.htm
    4 -rw-r--r--   1 seanbw root       26 Aug 26 16:10 MSXML4SP_RelNote.htm:Zone.Identifier
  724 -rwxrwxr-x   1 seanbw root   739408 Aug 26 16:09 msxmlcab.exe
    4 -rw-r--r--   1 seanbw root       26 Aug 26 16:10 msxmlcab.exe:Zone.Identifier
 5168 -rwxrwxr-x   1 seanbw root  5289984 Aug 26 16:09 msxml.msi
    4 -rw-r--r--   1 seanbw root       26 Aug 26 16:12 msxml.msi:Zone.Identifier
    0 lrwxrwxrwx   1 seanbw root       31 Jun 22 17:49 Music -> /mnt/data/StarT/StartPool/Music
16184 -rw-r--r--   1 seanbw root 16564488 Aug 27 00:20 nb672-full.exe
 5608 -rw-r--r--   1 seanbw root  5742224 Aug 26 00:58 NewsbinND-Install.exe
 4716 -rw-r--r--   1 seanbw root  4825360 Aug 26 04:36 nl_setup.exe
 4356 -rw-r--r--   1 seanbw root  4458413 Aug 30 02:12 numix-icon-theme-circle-master.zip
  420 -rw-r--r--   1 seanbw root   426932 Aug 30 02:15 numix_solarized_by_bitterologist-d6wm3nc.zip
    4 drwxrwxr-x+  5 seanbw root     4096 Aug 23 05:35 nzbget
24100 -rw-r--r--   1 seanbw root 24671916 Aug 23 05:21 nzbget-17.0-bin-linux.run
22220 -rw-r--r--   1 seanbw root 22752523 Dec  5  2015 nzbget-latest-bin-linux.run
    0 lrwxrwxrwx   1 seanbw root       30 Jun 22 17:58 OneDrive -> /mnt/data/Gen/GenPool/OneDrive
    0 lrwxrwxrwx   1 seanbw root       38 Aug 26 02:49 PlayOnLinux's virtual drives -> /home/seanbw/.PlayOnLinux//wineprefix/
   76 -rw-r--r--   1 seanbw root    73908 Aug 30 02:27 Polaris_pack.tar.gz
    0 lrwxrwxrwx   1 seanbw root       28 Jun 22 18:44 Public -> /mnt/data/Gen/GenPool/Public
    4 -rw-r--r--   1 seanbw root      392 Jul  3 02:54 rmlint.json
    8 -rwx------   1 seanbw root     5217 Jul  3 02:54 rmlint.sh
   28 -rw-r--r--   1 seanbw root    23217 Aug 29 14:11 sabcli-master.zip
   56 -rwxr-xrwx   1 seanbw root    56537 Apr 24  2013 sabcurses.py
    4 drwxr-xr-x   3 seanbw root     4096 Aug 29 15:19 SabNZBD
  188 -rw-r--r--   1 seanbw root   190384 Sep  6 22:28 Screenshot from 2016-09-04 17-21-50.png
    0 lrwxrwxrwx   1 seanbw root       29 Jun 22 18:43 scripts -> /mnt/data/Gen/GenPool/scripts
    0 lrwxrwxrwx   1 seanbw root       31 Jun 22 18:44 Templates -> /mnt/data/Gen/GenPool/Templates
    4 -rw-r--r--   1 root   root     1229 Jun 29 19:47 test.log
    4 -rw-r--r--   1 root   root     1287 Jun 29 17:34 test-root.log
    0 lrwxrwxrwx   1 seanbw root       34 Jun 22 17:52 TV-Shows -> /mnt/data/StarT/StartPool/TV-Shows
    4 -rw-r--r--   1 seanbw root        6 Aug 27 23:30 upstart-dbus-bridge.15263.pid
    4 -rw-r--r--   1 seanbw root        6 Aug 27 23:30 upstart-file-bridge.15263.pid
    4 -rw-r--r--   1 seanbw root        6 Aug 27 23:30 upstart-udev-bridge.15263.pid
    4 drwx--S---   3 seanbw root     4096 Aug 29 03:18 videotools
28704 -rw-r--r--   1 seanbw root 29391015 Aug 17 17:29 VuzeInstaller.tar.bz2
  656 -rwxr-xr-x   1 seanbw root   668874 Aug 26 01:40 winetricks
    0 lrwxrwxrwx   1 seanbw root       35 Jun 22 17:53 XXX-Adult -> /mnt/data/StarT/StartPool/XXX-Adult
    0 lrwxrwxrwx   1 seanbw root       36 Jun 22 18:03 XXX-Comics -> /mnt/data/OricO/OricoPool/XXX-Comics
root@nas:/home/seanbw# 



``` 

As you can see, most of the folders that would have consumed space are in the pool and are linked to them in the home folder.
I could move all the theme files to a separate part of the pool and link back to the hole folder.


QUESTION
Is there any way of extending the home folder to the /dev/sda partition without reinstallation? 
For instance could I add the /dev/sda partition to the home folder by some permanent mounting?
Can I create a pool of the home folder in /dev/sdb and dev/sda?

Many thanks for your time. i am grateful.
I have installed aptik and that has backed up all the installed and configuration files.
I just wish grub-repair had worked on /dev/sda but it did not. It just blinked and did not even enter grub rescue.

---

### Post by seanbw2 on 2016-09-08
I believe I have identified the problem but the solution escapes me.
In my trash is 245GB of files.
Using files I tried to open the file to delete but it showed up as an unallowed operation.
I don't know the route to trash via the terminal.
that could be the easiest solution.
Do you know how I could access trash via the terminal and then delete the files?

---

### Post by seanbw2 on 2016-09-08
I have gone to the desktop but I think the trash is not actually located in my home folder.
Let me explain.
I have 18 disks and in order to identify the source of the problem, I removed all but the two system disks.
Now it looks to me as if the trash is physically located on the removed disks but which i don't know so it looks as if I have to shut down, reattach the disks and then try to delete trash and see if performance improves.
So let me do that and I will come back to let you know how I get on.
Many thanks for your time and patience.

---

### Post by TheFu on 2016-09-08
You can move the /home to another disk, if you like. Just mount that other disk (post-move) to /home/. Simple.  Do all this off alternate boot media. Extending partition sizes is something that ZFS and LVM can do, but not a good idea if you must span physical disks. I lost 80% of my data doing that, before I got backup religion.  LVM has to be used on a fresh partition, it cannot be added after the fact without losing everything on the partition first.

You can move an entire install easily using lots of different tools.  Backup/restore, rsync, dd, ddrescue, partimage, fsarchive ... any of these can be used provided simple storage is being used. For complex storage ... like SW-RAID or Fake-RAID, then only work at the file-system level, not the bit-level. Does that make sense?

Storage is limited to a partition. Seeing what is in your HOME isn't really very helpful. **df -h** would be more helpful, but that really isn't needed. **sudo du -sh /** will show you how the different directories are using filling the storage. The /etc/fstab would be helpful too.  I bet /home is using all but 15-45G.  Just move that to a new disk.

No, your swap is WAY, WAY, WAY, WAY too large.  Where is 4G anywhere near 32G?  That is 8x too big, IMHO. There are different opinions about sizing swap, but the old rules of thumb of 1-2x RAM were outdated when systems started having 2G of RAM and more.  Use **free -mh** to see what is actually being used. Bet you will be surprised. Bet most is being used as disk buffers only, if even that.

Never heard of aptik. I use **rdiff-backup** to backup and restore about 25 systems here.  Spent about 15 yrs looking for a reasonable, yet simple to use, solution before finding rdiff-backup.  rsync is good for a 1-time mirror, like moving files from 1 partition to a partition on a new disk, but besides that, not-so-useful as a daily backup tool.  Since I run servers, no GUI works for a backup tool. Plus GUI backup tools are hard to use at 2am, automatic, unattended.

---

### Post by TheFu on 2016-09-08
Trash?  What's that?  I don't have it on any of my servers OR desktops. My main desktop:
```
$ ls ~/.local/share/T*
ls: cannot access /home/thefu/.local/share/T*: No such file or directory

```
And a server ... (none of them have this "Trash" directory)
```

$ ls ~/.local/share/T*
ls: cannot access /home/thefu/.local/share/T*: No such file or directory

```

Used this:
```
$ find ~ -type d -iname  \*Trash\*
```
to find any Trash directories under $HOME ... found some under firefox and thunderbird cache and IMAP folders for a few different cached email accounts. Don't think those are the same.  I'm curious - what is *Trash* used for and how would it be created?

BTW, never run any GUI programs as root. NEVER.  At least until a fuller understanding of file and directory permissions is gained.

---

### Post by oldos2er on 2016-09-08
> **seanbw2 said:**
> Do you know how I could access trash via the terminal and then delete the files? ```
cd

rm -rf .local/share/Trash/
``` Note: Run that command as your user, do not use "sudo."

---

### Post by seanbw2 on 2016-09-08
OK. rdiff-backup? I will install that and start using it.
trash was installed automatically by ubuntu.
I managed to free more space by removing trash.
After running df -h as sudo, i got this:
```
Filesystem      Size  Used Avail Use% Mounted onudev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G   34M  1.6G   3% /run
/dev/sde1       264G   21G  231G   9% /
tmpfs           7.9G   37M  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.9G     0  7.9G   0% /sys/fs/cgroup
/dev/sdb1       3.6T   55G  3.6T   2% /mnt/data/Gen/GenG1610T003
/dev/sdc1       3.6T  675G  2.8T  20% /mnt/data/Gen/GenG1610T002
GenPool         7.5T  750G  6.5T  11% /media/GenPool
OricoPool       264G   21G  231G   9% /media/OricoPool
StartPool       264G   21G  231G   9% /media/StartPool
/dev/sdd1       3.6T   89M  3.6T   1% /mnt/data/parity/GenG1610T004P
/dev/sdg1       256M  226M   30M  89% /media/usb0
/dev/sdf1        61G  1.2G   59G   2% /media/usb1
tmpfs           1.6G   72K  1.6G   1% /run/user/1000



```

I now have 247GB free.

Plan of action:

Run Gparted and reduce swap to 8GB (apologies - i mixed up the figures in my head and the system was running so slowly that i did not want to go back to the post to recheck)
Allocate extra space freed to $Home
Test rdiff-backup. If i can use it, then start a weekly program of backup (have to automate this somehow. memory is not my strongest point)

PROBLEMS
_**Trash**_
How can I remove trash? I suspect I will have this issue more and more seeing as the files I will delete mostly are media files that are sizeable and since trash is located in my home folder, same issue will pop up again. 

options: Move trash to GenPool or remove it entirely.

Solution: Remove trash completely seeing as I have three pools and can delete from any.  Should be a system tweak or a googling for solution.


_**Grub**_
I have successfully cloned /dev/sde to /dev/sda but grub is not working even after using grub customizer and grub-repair.
I have checked and double checked that the uuid are different and are being correctly picked up in the grub config. Initially because they were cloned, the box had two identical system disks with same uuid
Somehow when HP gets to grub, it just stands there and blinks. Does not go farther. 

Options: Physically remove /dev/sde from the box. That way - I can have a pristine copy of the system disk in case anything goes wrong.

Resolution: Resolve the grub problem by posting a problem statement here. With grub, i am out of my depth.

_**Pool Drives Slowing System down**_
When i power up the remaining drives - OricoPool (4 disks and 1 parity) and StartPool (7 disks and 1 parity), the system slows down noticeably. I suspect that the system is trawling through all the drives almost constantly.
 
options: Is there a way to make the system semi-static? Most of the data are media files and not system critical data. maybe I can run system (data?) updates regularly - say every 30 minutes? cron?

Resolution: Investigate the possibility of upgrading the CPU (RAM is already at a max of the allowed 16GB) against the limitation of knowing that the system cannot accommodate a fan at any level. Only a heatsink.  or  Buy a more powerful system and sell this (More of a long term solution - this)

---

### Post by seanbw2 on 2016-09-08
To oldos2er and TheFU: I am very grateful for your assistance. Since i came back to Ubuntu, you, FU and OldFred have been extremely accommodating. the point is when people like me from a windows background (point and click and problem is solved) come to Linux, it is often a difficult transition and unlike Windows where there are myriads of forums that can help, Linux forums are often not that easy to navigate because the skillsets required to resolve the issue need a lot of hand holding and patience + original technical skills
Windows - usually there is a program out there that can provide the solution. 
The point is most people do not have the time and/or the patience. People like me get frustrated and run for the hills.
So thank you.  ):P):P

Before I mark the thread solved - any advice on the three problems identified? I know - wearing out my welcome mat...

Need to change my glasses.

---

### Post by TheFu on 2016-09-08
231G free. Don't understand how you got a different number.  Notice how all the storage was really sucked up in /home?  Don't do that going forward.  
/ was less than 25G, as expected.

As I said before, none of my systems have a "Trash" - probably some GUI program adds it that I've never used. Stop using that program? Might be hard for point-n-click people.

Grub isn't that hard if you just want to update and don't have any encrypted or fake-RAID devices. There is very little good reason to ever use Fake-RAID, IMHO. It has all the in-flexibility of HW-RAID without all the flexibility of SW-RAID.  Plus, for a home system, RAID shouldn't really be a priority, especially for media.  Backups are 1000x more important than RAID.

Still, 8G of swap is 2x more than needed. It will probably never be used on a 16G system. See what I mean?
```
$ free -hm
             total       used       free     shared    buffers     cached
Mem:           15G        15G       468M       2.5M       2.5G       2.5G
-/+ buffers/cache:        10G       5.5G
Swap:          4G       1.6G       2.4G

```  10G of RAM is being used for disk buffers.  Thw swap is being used for seldom run programs only.  4G of swap is probably overkill. This isn't Windows.

On my media server box, I don't merge file systems. All those funny FSes are sorta hokey anyways and aren't nearly as well tested/used as the normal ones. The media server knows that there are 3 separate directories on different disks for the different media types. I don't need to do anything for that, though if I did, I'd use symbolic links only. As I said, the only time I've had massive data loss was by using LVM to merge disks into single file systems. 1 of the disks involved died, which broke the other 2 and all the data on all 3 disks was lost. Didn't have backup religion back then. ;(  

rdiff-backup is great for normal OS files, but I wouldn't use it for media files that never change. I use rsync for that.

Other questions really need separate threads, IMHO. The skills needed to answer those are more generic.

---

### Post by seanbw2 on 2016-09-08
Thanks.
I've installed rdiff-backup. Will test run it.
will mark thread closed.

---

### Post by TheFu on 2016-09-08
[https://www.kirya.net/articles/backups-using-rdiff-backup/](https://www.kirya.net/articles/backups-using-rdiff-backup/) is the best primer for **rdiff-backup** that I know.

---

### Post by gordintoronto on 2016-09-09
One more command: sudo apt clean

removes the update downloads, which are not needed once the update is installed.

---

### Post by oldos2er on 2016-09-09
seanbw2, you're welcome. I remember being a Linux newbie and not knowing enough even to formulate a meaningful question, so I empathize with you. 

As TheFu said, it's best if you start new threads for each of your questions, it helps the forum community more effectively give you a good answer.

---

