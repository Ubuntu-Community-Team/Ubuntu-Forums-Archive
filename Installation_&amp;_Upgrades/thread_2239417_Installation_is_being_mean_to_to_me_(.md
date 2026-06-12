---
title: "Installation is being mean to to me :("
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by niko8 on 2014-08-13
So I am going through the  process of installing ubuntu 14.04 alongside win8. Since the installer didn't recognize win8 I
had to custom partition my drive. Set it up into 4 parts 50gb (/) 50gb (home/) 40gb (boot/) and 43gb (leftover) for swap.
so nothing extravagant. Should work normally, and, sure enough it takes me to the next screen. 3 seconds later I get a prompt that literally looks like:
 ___________________
|____??????????______|
|.................................|
| ......???????????? .......|   (Not all in ASCII of course)
|.................................|
|___________________|

and sends me to the previous screen and tells me that I didn't specify a root system ( which I OBVIOUSLY did) and makes me reselect the partitions... Been at this all night to no avail. If someone here could help me out here that would be amazing as I am utterly lost.
cheers,
Niko.

---

### Post by yancek on 2014-08-13
1-2GB should be more than enough for a boot partition if you are going to have a separate one.
2-4GB for swap should be sufficient, depends upon the amount of RAM you have.

Are you selecting the partition in the main installation window by highlighting it, then clicking the change tab and selecting a Mount point of /, for the root of the filesystem?

---

### Post by niko8 on 2014-08-13
I'm double clicking the partition then changing "do not use" to somethingsomething 4. Selecting format (even though theres nothing there) and selecting the / on the drop down menu and clicking OK.
the / is then displayed next to the partition on the menu but the thing doesn't work...
...........
wait.... Is that not how you do it?



16GB RAM btw.. :)

---

### Post by fantab on 2014-08-14
When assigning '/' in the installer you have to use following options:
Use as = Ext4 journaling system
Mountpoint= /
Format= yes/no

Swap need not be more than 2-4gb unless you want to 'Hibernate' you pc. In that case SWAP should be equal to or more than the size of your RAM in GiB and not in GB.
Before I tell you about /boot partition can you post the output of the following commands, booting Live?
```
sudo parted -l
sudo fdisk -l
```

Since you have Win8, was it pre-installed or did you install it?
what machine you use, laptop/desktop, model/make ?

---

### Post by niko8 on 2014-08-14
[ATTACH=CONFIG]255464[/ATTACH][ATTACH=CONFIG]255465[/ATTACH]
The results of "sudo parted -l"  && "sudo fdisk -l"
possibly I partitioned one drive and selected the other to boot from?
I'm on an AORUS x7 v.2 with Pre-Installed windows
so I have a 256GB SSD and a 1TB HDD.... is that the problem here?

---

### Post by fantab on 2014-08-14
Please copy the full output from the 'terminal' and paste it here, preferably in BB code.

You say you have 256gb SSD, It doesn't show in the output but the 'Error' or it could be encrypted. Does Windows show the SSD?
Boot into Windows and paste the screenshot of all your drives in Disk Management 

There is something not normal about that output. 
Can you link your previous threads? It'll help to know what you covered.

---

### Post by niko8 on 2014-08-14
[ATTACH=CONFIG]255467[/ATTACH]  windows doesn't seem to have a problem with the SSD.... 
I have the full terminal output for both commands... but its longer than most of my theory papers...(867 words)
I don't have any other threads however. first thing I posted.

---

### Post by niko8 on 2014-08-14
[FONT=arial]```
ubuntu@ubuntu:~$ sudo parted -l[/FONT]
[FONT=arial]Model: ATA HGST HTS721010A9 (scsi)[/FONT]
[FONT=arial]Disk /dev/sda: 1000GB[/FONT]
[FONT=arial]Sector size (logical/physical): 512B/4096B[/FONT]
[FONT=arial]Partition Table: msdos[/FONT]

[FONT=arial]Number  Start   End     Size    Type     File system  Flags[/FONT]
[FONT=arial] 1      1049kB  1000GB  1000GB  primary  ntfs         boot[/FONT]


[FONT=arial]Error: Invalid argument during seek for read on /dev/sdb                  [/FONT]
[FONT=arial]Retry/Ignore/Cancel? Ignore                        [/FONT]
[FONT=arial]Error: The backup GPT table is corrupt, but the primary appears OK, so that will[/FONT]
[FONT=arial]be used.[/FONT]
[FONT=arial]OK/Cancel? OK                            [/FONT]
[FONT=arial]Backtrace has 8 calls on stack:[/FONT]
[FONT=arial]  8: /lib/x86_64-linux-gnu/[/FONT][FONT=arial]libparted.so.0(ped_assert+[/FONT][FONT=arial]0x31) [0x7f7973ec54b1][/FONT]
[FONT=arial]  7: /lib/x86_64-linux-gnu/[/FONT][FONT=arial]libparted.so.0(+0x3f5f6) [0x7f7973ef55f6][/FONT]
[FONT=arial]  6: /lib/x86_64-linux-gnu/[/FONT][FONT=arial]libparted.so.0(ped_disk_new+[/FONT][FONT=arial]0x49) [0x7f7973ecaf99][/FONT]
[FONT=arial]  5: parted() [0x406dff][/FONT]
[FONT=arial]  4: parted() [0x407bda][/FONT]
[FONT=arial]  3: parted(main+0x154b) [0x4065cb][/FONT]
[FONT=arial]  2: /lib/x86_64-linux-gnu/libc.so.[/FONT][FONT=arial]6(__libc_start_main+0xf5) [0x7f79736a2ec5][/FONT]
[FONT=arial]  1: parted() [0x406617][/FONT]


[FONT=arial]You found a bug in GNU Parted! Here's what you have to do:[/FONT]

[FONT=arial]Don't panic! The bug has most likely not affected any of your data.[/FONT]
[FONT=arial]Help us to fix this bug by doing the following:[/FONT]

[FONT=arial]Check whether the bug has already been fixed by checking[/FONT]
[FONT=arial]the last version of GNU Parted that you can find at:[/FONT]

[http://ftp.gnu.org/gnu/parted/](http://ftp.gnu.org/gnu/parted/)

[FONT=arial]Please check this version prior to bug reporting.[/FONT]

[FONT=arial]If this has not been fixed yet or if you don't know how to check,[/FONT]
[FONT=arial]please visit the GNU Parted website:[/FONT]

[http://www.gnu.org/software/parted](http://www.gnu.org/software/parted)

[FONT=arial]for further information.[/FONT]

[FONT=arial]Your report should contain the version of this release (2.3)[/FONT]
[FONT=arial]along with the error message below, the output of[/FONT]

[FONT=arial]    parted DEVICE unit co print unit s print[/FONT]

[FONT=arial]and the following history of commands you entered.[/FONT]
[FONT=arial]Also include any additional information about your setup you[/FONT]
[FONT=arial]consider important.[/FONT]

[FONT=arial]Assertion (last_usable <= disk->dev->length) at[/FONT]
[FONT=arial]../../../libparted/labels/gpt.[/FONT][FONT=arial]c:994 in function _parse_header() failed.[/FONT]

[FONT=arial]ubuntu@ubuntu:~$ sudo fdisk -l[/FONT]

[FONT=arial]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 4096 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/FONT]
[FONT=arial]Disk identifier: 0x3fe97f02[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sda1   *        2048  1953521663   976759808    7  HPFS/NTFS/exFAT[/FONT]

[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]Disk /dev/sdb: 128.0 GB, 128035676160 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x3fe97ee8[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sdb1               1   750195455   375097727+  ee  GPT[/FONT]

[FONT=arial]Disk /dev/sdc: 128.0 GB, 128035676160 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x00000000[/FONT]

[FONT=arial]Disk /dev/sdc doesn't contain a valid partition table[/FONT]

[FONT=arial]Disk /dev/sdd: 128.0 GB, 128035676160 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x00000000[/FONT]

[FONT=arial]Disk /dev/sdd doesn't contain a valid partition table[/FONT]

[FONT=arial]WARNING: GPT (GUID Partition Table) detected on '/dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1'! The util fdisk doesn't support GPT. Use GNU Parted.[/FONT]


[FONT=arial]Disk /dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1: 384.1 GB, 384100073472 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 46697 cylinders, total 750195456 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 16384 bytes / 49152 bytes[/FONT]
[FONT=arial]Disk identifier: 0x3fe97ee8[/FONT]

[FONT=arial]                              Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p1               1   750195455   375097727+  ee  GPT[/FONT]
[FONT=arial]Partition 1 does not start on physical sector boundary.[/FONT]

[FONT=arial]Disk /dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p1: 314 MB, 314572800 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 38 cylinders, total 614400 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 16384 bytes / 49152 bytes[/FONT]
[FONT=arial]Disk identifier: 0x73736572[/FONT]

[FONT=arial]This doesn't look like a partition table[/FONT]
[FONT=arial]Probably you selected the wrong device.[/FONT]

[FONT=arial]  Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p1p1      1920221984  3736432267   908105142   72  Unknown[/FONT]
[FONT=arial]/dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p1p2   ?  1936028192  3889681299   976826554   6c  Unknown[/FONT]
[FONT=arial]/dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p1p3   ?           0           0           0    0  Empty[/FONT]
[FONT=arial]/dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p1p4        27722122    27722568         223+   0  Empty[/FONT]
[FONT=arial]Partition 4 does not start on physical sector boundary.[/FONT]

[FONT=arial]Disk /dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p2: 272 MB, 272629760 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 33 cylinders, total 532480 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 16384 bytes / 49152 bytes[/FONT]
[FONT=arial]Disk identifier: 0x500a0dff[/FONT]

[FONT=arial]This doesn't look like a partition table[/FONT]
[FONT=arial]Probably you selected the wrong device.[/FONT]

[FONT=arial]  Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p2p1   ?  1948285285  3650263507   850989111+  6e  Unknown[/FONT]
[FONT=arial]Partition 1 does not start on physical sector boundary.[/FONT]
[FONT=arial]/dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p2p2   ?           0           0           0   74  Unknown[/FONT]
[FONT=arial]/dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p2p4        28049408    28049848         220+   0  Empty[/FONT]

[FONT=arial]Partition table entries are not in disk order[/FONT]

[FONT=arial]Disk /dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p3: 134 MB, 134217728 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 16 cylinders, total 262144 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 16384 bytes / 49152 bytes[/FONT]
[FONT=arial]Disk identifier: 0x00000000[/FONT]

[FONT=arial]Disk /dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p3 doesn't contain a valid partition table[/FONT]

[FONT=arial]Disk /dev/mapper/isw_dedjjfehej_[/FONT][FONT=arial]Volume1p4: 184.2 GB, 184225366016 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 22397 cylinders, total 359815168 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 16384 bytes / 49152 bytes[/FONT]
[FONT=arial]Disk identifier: 0x73736572[/FONT]

[FONT=arial]This doesn't look like a partition table
```






well........... I'm screwed.[/FONT]

---

### Post by oldos2er on 2014-08-14
I think you need to use *gdisk* in place of the parted command; see this askubuntu.com thread: [http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table)

---

### Post by niko8 on 2014-08-14
so my entire problem is a corrupt GPT table?
:confused:

---

### Post by oldfred on 2014-08-14
Did you use Windows to reformat 1TB drive. It says it is msdos(MBR), but you have a backup gpt partition table.
Windows regularly does that, it reformats a gpt drive to MBR and leaves backup gpt table. Windows seems to ignore backup gpt. But Linux sees both MBR & gpt and does not know what you want.

Also you are showing /mapper. Is that RAID, LVM or Intel SRT? Any of those add issues. Or did you install Ubuntu with encryption which uses LVM and usually is a full drive erase and convert to LVM.

Fixparts can remove backup gpt table, if that is what you want. 
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

gpt does have some advantages, but Windows will only boot from gpt with UEFI. Ubuntu can boot from gpt with either UEFI or BIOS if correct supporting partitions are on drive. Only XP would not read drives partitioned with gpt, everything else newer will read gpt partitioned drives.

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by oldos2er on 2014-08-14
> **niko8 said:**
> so my entire problem is a corrupt GPT table?
:confused:

We won't know until we see the output of ```
sudo gdisk -l
```

---

### Post by niko8 on 2014-08-15
Well I did something I may come to regret, but I think I solved my problem. I somehow tricked Ubuntu into finishing the installation, then I burnt a new copy onto my USB and reinstalled it, deleting the old (not working) ubuntu and instead of installing it on my windows drive. but it on my second 1TB HDD.. 
not perfect, not clean, but it works.

---

### Post by oldfred on 2014-08-15
Glad you got it working.

I always think it is better to keep Windows on one hard drive and Ubuntu on another, if you have more than one drive. But most laptops only have one drive. With USB3 an external is an option, just not quite as good as an internal drive.

You do still need to have Windows & Ubuntu in same UEFI or BIOS boot mode to make it easy to dual boot. Otherwise you have to use UEFI/BIOS or maybe one time boot key to boot.

---

