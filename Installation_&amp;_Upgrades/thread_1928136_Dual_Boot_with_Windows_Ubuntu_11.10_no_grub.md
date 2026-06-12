---
title: "Dual Boot with Windows Ubuntu 11.10 no grub"
date: 2012-02-19
forum: Installation &amp; Upgrades
---

### Post by tbobker on 2012-02-19
This seems to be a common problem with Ubuntu 11.10. I have not tried installing Ubuntu three times each time I get to the end of the install and I have an error message that grub cannot be installed on dev/sda.
Then upon restart my machine just boots directly into windows. 
The install is successful as I can see all the partitions, it looks like from reading other posts that grub is not installed. Other posts people have pasted in the results from "boot info script". So see below. If anyone can advise I would appreciate it immensely as I would like to see Ubuntu on my machine. 

> 
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/mapper/isw_bfgfdbbbac_ARRAY.

sdb1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sdb2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_bfgfdbbbac_ARRAY1: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

isw_bfgfdbbbac_ARRAY2: _________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

isw_bfgfdbbbac_ARRAY5: _________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /etc/fstab /boot/grub/core.img

isw_bfgfdbbbac_ARRAY6: _________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.
/dev/sdb1     ? 3,153,641,472 6,687,539,205 3,533,897,734  81 Minix / old Linux
/dev/sdb2     ?             0 3,109,814,271 3,109,814,272   0 Empty
/dev/sdb4       3,153,592,320 3,153,592,325             6   0 Empty

/dev/sdb1 ends after the last sector of /dev/sdb
/dev/sdb2 ends after the last sector of /dev/sdb
/dev/sdb4 ends after the last sector of /dev/sdb

Drive: isw_bfgfdbbbac_ARRAY _____________________________________________________________________

Disk /dev/mapper/isw_bfgfdbbbac_ARRAY: 320.0 GB, 319995248640 bytes
255 heads, 63 sectors/track, 38903 cylinders, total 624990720 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bfgfdbbbac_ARRAY1   *        112,455   317,765,699   317,653,245   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bfgfdbbbac_ARRAY2        317,766,142   624,990,719   307,224,578   5 Extended
/dev/mapper/isw_bfgfdbbbac_ARRAY5        317,766,144   620,801,023   303,034,880  83 Linux
/dev/mapper/isw_bfgfdbbbac_ARRAY6        620,801,536   624,990,719     4,189,184  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_bfgfdbbbac_ARRAY1 01CCD831643C91F0                       ntfs       
/dev/mapper/isw_bfgfdbbbac_ARRAY5 9ecc3df7-999c-473a-b3f3-6f9c6cee60a1   ext4       
/dev/sda                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bfgfdbbbac_ARRAY
isw_bfgfdbbbac_ARRAY1
isw_bfgfdbbbac_ARRAY5
isw_bfgfdbbbac_ARRAY6

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================= isw_bfgfdbbbac_ARRAY1/boot.ini: ========================

--------------------------------------------------------------------------------
[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

--------------------------------------------------------------------------------

======================= isw_bfgfdbbbac_ARRAY5/etc/fstab: =======================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/isw_bfgfdbbbac_ARRAY5 /               ext4    errors=remount-ro 0       1
/dev/mapper/isw_bfgfdbbbac_ARRAY6 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
--------------------------------------------------------------------------------

=========== isw_bfgfdbbbac_ARRAY5: Location of files loaded by Grub: ===========

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sdb

00000000  44 01 00 00 01 00 04 80  14 01 00 00 24 01 00 00  |D...........$...|
00000010  00 00 00 00 14 00 00 00  02 00 00 01 02 00 00 00  |................|
00000020  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000030  20 00 00 00 20 02 00 00  00 00 18 00 ff 01 1f 00  | ... ...........|
00000040  01 02 00 00 00 00 00 05  20 00 00 00 20 02 00 00  |........ ... ...|
00000050  18 ee 90 7c 40 40 20 00  02 00 00 00 b0 29 db 00  |...|@@ ......)..|
00000060  92 93 80 7c 02 00 00 00  78 01 3f 00 7c b9 06 00  |...|....x.?.|...|
00000070  b8 29 db 00 34 00 00 c0  f0 7f db 00 0a 00 00 00  |.)..4...........|
00000080  78 01 3f 00 18 00 00 00  00 00 00 00 78 01 3f 00  |x.?.........x.?.|
00000090  40 00 00 00 50 29 db 00  00 00 00 00 00 00 00 00  |@...P)..........|
000000a0  00 00 00 00 00 00 00 00  f8 bb 06 00 00 00 00 00  |................|
000000b0  74 00 1a 02 d0 ed 11 00  f8 fb fd 7f 6c 00 00 00  |t...........l...|
000000c0  d0 ed 11 00 34 00 00 c0  00 00 00 00 f8 bb 06 00  |....4...........|
000000d0  88 b9 06 00 75 e8 81 7c  00 fc fd 7f a4 ba 06 00  |....u..|........|
000000e0  f9 81 07 01 05 82 07 01  04 01 00 00 1e 82 07 01  |................|
000000f0  43 3a 5c 57 7b 02 00 00  57 53 5c 24 4e 74 55 6e  |C:\W{...WS\$NtUn|
00000100  69 6e 73 74 c0 b9 06 00  00 00 00 00 c8 05 91 7c  |inst...........||
00000110  90 46 ab 00 8c ba 06 00  01 02 00 00 00 00 00 05  |.F..............|
00000120  20 00 00 00 20 02 00 00  01 01 00 00 00 00 00 05  | ... ...........|
00000130  12 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000140  c9 21 3a f3 64 02 00 00  40 63 01 00 00 00 00 00  |.!:.d...@c......|
00000150  44 01 00 00 01 00 04 80  14 01 00 00 24 01 00 00  |D...........$...|
00000160  00 00 00 00 14 00 00 00  02 00 00 01 02 00 00 00  |................|
00000170  00 00 18 00 ff 01 1f 00  01 02 00 00 00 00 00 05  |................|
00000180  20 00 00 00 20 02 00 00  00 00 18 00 ff 01 1f 00  | ... ...........|
00000190  01 02 00 00 00 00 00 05  20 00 00 00 20 02 00 00  |........ ... ...|
000001a0  18 ee 90 7c 40 40 20 00  02 00 00 00 18 b9 06 00  |...|@@ .........|
000001b0  92 93 80 7c 02 00 00 00  fd dc 90 7c 7c b9 06 00  |...|.......||...|
000001c0  4a ea 81 7c 34 00 00 c0  f8 bb 06 00 a3 d2 85 7c  |J..|4..........||
000001d0  00 00 00 00 18 00 00 00  00 00 00 00 5c b9 06 00  |............\...|
000001e0  40 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |@...............|
000001f0  00 00 00 00 00 00 00 00  f8 bb 06 00 00 00 00 00  |................|
00000200

Unknown BootLoader on sdb1


Unknown BootLoader on sdb2


Unknown BootLoader on sdb4


Unknown BootLoader on isw_bfgfdbbbac_ARRAY2



========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb1: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb2: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/sdb4: No such file or directory
hexdump: /dev/mapper/isw_bfgfdbbbac_ARRAY2: No such file or directory
hexdump: /dev/mapper/isw_bfgfdbbbac_ARRAY2: No such file or directory
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in



---

### Post by darkod on 2012-02-19
There is a message that the partitions on /dev/sdb are not OK, they go outside the disk. Not sure if this is a result of installing onto raid or not.

I would suggest, boot windows, open Disk Management and delete the linux partitions. Leave the space as unallocated.

Then try to install ubuntu but with the Alternate Install CD. You should use the alternate for installing on raid. If you use the standard cd the grub installation often fails, which is the error you are getting. But the messages about the partitions on /dev/sdb should not be there even with using the standard cd.

Do as suggested above and lets see how it goes.

---

### Post by tbobker on 2012-02-19
Hi, thanks for getting back so quickly. Can you please advise what the  Alternate Install CD is? The same live CD but a different option?

Sorry, found it here: [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

I give this a try.

---

### Post by darkod on 2012-02-19
Yes, you found it. It needs to have the word 'alternate' in the file name. There are two versions for 32bit and 64bit.

The installer is text based (the old XP style) but the installed system is THE SAME as the standard live cd. You end up with the same. But the alternate has built in raid support and is recommended for raid.

If it still doesn't install grub, leave the ubuntu install on the disk. There is an option to try and grub2 later from the live cd.

---

### Post by tbobker on 2012-02-19
Hi. It didnt install grub2 but at least I now have a grub rescue message. I loaded up live cd and tried grub repair but I think something went wrong. It said the boot loader was repaired but I still get the same message.
Any help appreciated.

---

### Post by darkod on 2012-02-19
Can you run the script again and post the new results?

---

### Post by tbobker on 2012-02-19
If I follow these instructions and run the sudo commands from terminal in live cd I get the below error message when i run boot repair:

Error : /var/log/boot-sav/log/2012-02-19__22h55boot-repair12//current_mbr.img does not exist. MBR could not be restored.

---

### Post by darkod on 2012-02-19
What commands are you talking about?

I just asked if you could run the script again and post the new results file after you installed ubuntu. If you are trying to run Boot-Repair I am not sure it can repair raid installations.

---

### Post by tbobker on 2012-02-20
Ok I was running boot repair.
Funnily enough, I have had Ubuntu 11.04 installed on my computer before with no issues. Its possible that it is Ubuntu 11.10 that is  causing problems.  Seeing as I can't get passed grub rescue, I may as well try a full install and wipe the entire hard drive. 
I let you know how it goes.
Thanks.

---

### Post by tbobker on 2012-02-21
if anyone is interested, neither Ubuntu 11.10 or Linux MINT are installing with out a grub install error. 
Fortunately, Opensuse 12.1 is working. I have reverted back to this with gnome 3. Not the best solution, however, it is installing. If anyone has any other ideas, please let me know would be great to get ubuntu 11.10 installed.

---

### Post by YannBuntu on 2012-02-21
Hello
OpenSuse still uses GRUB Legacy, so the problem comes from GRUB2.

```
Error : /var/log/boot-sav/log/2012-02-19__22h55boot-repair12//current_mbr.img does not exist. MBR could not be restored.
```

I guess this means that no OS was detected by GRUB2's os-prober. A probable solution would have been to create a separate /boot partition outside the arrays.

@darkod: Boot-Repair has RAID (dmraid and mdadm) support, and is generally able to reinstall GRUB2 on RAID systems, which solves most of boot problems on those systems. Please don't hesitate to [report cases where it fails on the tracker]("https://bugs.launchpad.net/boot-repair").

---

