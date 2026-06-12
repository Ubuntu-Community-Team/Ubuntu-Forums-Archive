---
title: "Please help-lost partitions after upgrade"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by WestCoastSuccess on 2010-10-30
I'm having a problem and could really use some help: I  upgraded from 8.04 to 10.04 yesterday; now my system refuses to boot -  it hangs at the Ubuntu logo with the five circles alternating red/white,  but no hard drive activity. At that point, the mouse works but  ctrl+alt+del does nothing. Nor does ctrl+alt+backspace or ctrl+alt+F1.  The computer needs to be turned off and on again to restart.

I've booted with the CD and tried mounting my partitions, however I am  unable to mount them. Very strangely, some programs (gparted; fdisk -l)  see my partitions just fine, however they do not appear correctly in  /dev, and in the file browser they're wrong too (I assume the file  browser takes its information from /dev?)

My partitions are as follows:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00086912

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2441       38913   292969372+  83  Linux
/dev/sda2            1833        2440     4883760   82  Linux swap / Solaris
/dev/sda3             374        1832    11719417+  83  Linux
/dev/sda4   *           1         373     2996091   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ae7ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38658   310520353+  fd  Linux raid autodetect
/dev/sdb2           38659       38913     2048287+  82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cf093

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38658   310520353+  fd  Linux raid autodetect
/dev/sdc2           38659       38913     2048287+  82  Linux swap / Solaris
```sdb1 and sdc1 were a RAID 0 array on /md0.
sda3 was /home (ext3).
sda1 was /var/lib (xfs).

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda: TYPE="nvidia_raid_member" 
/dev/sdb: TYPE="nvidia_raid_member" 
/dev/sdc1: UUID="37e691c3-1f43-bb41-d66b-80de52cbc87c" TYPE="linux_raid_member" 
/dev/sdc2: UUID="97f28fc6-9b8a-468c-9e1d-e0067a884093" TYPE="swap" 
/dev/mapper/nvidia_aebeeibc1: UUID="416db4f2-912e-45a3-b0b2-55e1bf111a4e" SEC_TYPE="ext2" TYPE="ext3" 
```Not sure why sda is being identified above as "nvidia_raid_member".  Likewise I have no idea what "/dev/mapper/nvidia_aebeeibc1" refers to.

I gather the info below isn't particularly useful, given I've booted from the CD, but thought I'd include anyway:

```
ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdc2 swap swap defaults 0 0
``````
ubuntu@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
aufs                   2.1G   946M   1.2G  46% /
none                   2.1G   328k   2.1G   1% /dev
/dev/sr0               720M   720M      0 100% /cdrom
/dev/loop0             687M   687M      0 100% /rofs
none                   2.1G   304k   2.1G   1% /dev/shm
tmpfs                  2.1G    21k   2.1G   1% /tmp
none                   2.1G    91k   2.1G   1% /var/run
none                   2.1G   4.1k   2.1G   1% /var/lock
none                   2.1G      0   2.1G   0% /lib/init/rw
```Gparted shows the partitions properly, except it shows the partitions as empty.

I don't think I can fix whatever is causing the failure to boot without  mounting sda4 to examine the boot info, and I cannot mount sda4 because  it is not being recognized. Interestingly, my external 500GB backup  drive, attached via USB, isn't recognized either.

Can anyone help? I really desperately need to get this sorted out. Prior  to attempting the upgrade, 8.04 ran rock solidly for the past 2.5  years, and the computer runs 24/7.

If I attempt to install 10.04 via the live CD, will it destroy the  existing partitions? Or will it recognize them and allow me to  incorporate them into the build? 

**UPDATE:**

I used TestDisk to examine the drive and it finds the partitions fine. I'm also able to access the files in some of the partitions (unfortunately not the XFS partition nor the RAID 0 array). I managed to copy various logs via TestDisk (kernel.log, boot.log, everything in /var/crash, etc.) and am happy to share these if it helps.

I tried writing the partition structure to disk using TestDisk, and I also wrote TestDisk MBR code to first sector (which in hindsight appears to be a particularly stupid decision: now when I try to boot it shows a blank screen, except for "1234F:" From the TestDisk instructions, this allows one to select the partition to boot, with "F" being "floppy". Selecting any of these does nothing, except for making the HD light blink very briefly once).

I really, really need help...

Thank you!

---

### Post by Rubi1200 on 2010-10-31
Using a LiveCD to boot the computer, post the results of the boot-script linked at the bottom of my post.

Please wrap the text with the # tag when posting back here.

Also, do you intentionally have a RAID array?

The problem may have been caused, in part, by the upgrade because, from what I understand, there are issues with RAID in 10.04.

Hopefully, the results from the boot-script will also help.

Thanks.

---

### Post by WestCoastSuccess on 2010-10-31
Many thanks for the reply! Here's RESULTS.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/mapper/nvidia_aebeeibc

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdc2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

nvidia_aebeeibc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/mapper/nvidia_aebeeibc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


nvidia_aebeeibc2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: wrong fs type, bad option, bad superblock on /dev/mapper/nvidia_aebeeibc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     5,992,244     5,992,182  83 Linux
/dev/sda2           5,992,245    29,431,079    23,438,835  83 Linux
/dev/sda3          29,431,080    39,198,599     9,767,520  82 Linux swap / Solaris
/dev/sda4          39,198,600   625,137,344   585,938,745  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   621,040,769   621,040,707  fd Linux raid autodetect
/dev/sdc2         621,040,770   625,137,344     4,096,575  82 Linux swap / Solaris


Drive: nvidia_aebeeibc ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_aebeeibc: 640.1 GB, 640145817600 bytes
255 heads, 63 sectors/track, 77826 cylinders, total 1250284800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_aebeeibc1                 63   621,040,769   621,040,707  fd Linux raid autodetect
/dev/mapper/nvidia_aebeeibc2        621,040,770   625,137,344     4,096,575  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_aebeeibc1 416db4f2-912e-45a3-b0b2-55e1bf111a4e   ext3                                     
/dev/mapper/nvidia_aebeeibc: PTTYPE="dos" 
/dev/sda                                                nvidia_raid_member                               
/dev/sdb                                                nvidia_raid_member                               
/dev/sdc1        37e691c3-1f43-bb41-d66b-80de52cbc87c   linux_raid_member                               
/dev/sdc2        97f28fc6-9b8a-468c-9e1d-e0067a884093   swap                                     
/dev/sdc: PTTYPE="dos" 
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sda4: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_aebeeibc
nvidia_aebeeibc1
nvidia_aebeeibc2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on sda3


Unknown BootLoader  on sda4


Unknown BootLoader  on nvidia_aebeeibc2

00000000  58 51 25 e9 f2 4a 2f cf  c3 56 06 aa f1 c6 7b be  |XQ%..J/..V....{.|
00000010  2e cc 77 df a3 d4 4c fc  cd f8 8d 91 d3 89 3a f5  |..w...L.......:.|
00000020  df b3 0e 75 71 44 ea f3  6c 03 1a da 28 f1 e3 0f  |...uqD..l...(...|
00000030  fb b6 8a e9 a0 ac 1b 39  46 dd 12 7c 36 d0 53 51  |.......9F..|6.SQ|
00000040  84 05 f4 82 f2 13 6d c6  9d a0 a0 67 f2 45 9c a1  |......m....g.E..|
00000050  f0 d4 e9 3c b9 01 06 89  47 85 6d 93 5d d0 c1 6b  |...<....G.m.]..k|
00000060  b9 db 53 b9 a8 fb 99 fa  12 7b 79 ca 29 cc f9 48  |..S......{y.)..H|
00000070  81 35 73 2c 72 d8 d6 5d  55 7f 53 dd 89 ff 10 d8  |.5s,r..]U.S.....|
00000080  f8 de 56 fa 7a 1d 76 8e  66 4a 6a 5c c8 0a a1 6c  |..V.z.v.fJj\...l|
00000090  d6 d0 53 bc cb dc d3 88  f1 b7 e1 60 f1 8b 51 2e  |..S........`..Q.|
000000a0  78 73 69 16 83 86 90 9a  a5 fc 01 e1 87 df 2b 5a  |xsi...........+Z|
000000b0  5e 34 06 6e dc e3 65 60  bf 3d ed 9e e3 b2 93 a9  |^4.n..e`.=......|
000000c0  d6 7c fe 7d 77 5a f2 0a  cf e8 b8 89 c7 0f 76 67  |.|.}wZ........vg|
000000d0  42 73 86 ff 67 38 68 eb  20 f9 ad 89 50 7f 85 27  |Bs..g8h. ...P..'|
000000e0  a4 e6 60 8e f7 a8 40 b5  82 34 17 af ef 5c 70 3f  |..`...@..4...\p?|
000000f0  b7 4f 3c bd 56 5c 7f 29  e2 f2 2a 8d 03 4a 91 33  |.O<.V\.)..*..J.3|
00000100  8c 06 d2 4c bb d3 88 fe  8d 5c 69 ee 8e d9 97 80  |...L.....\i.....|
00000110  95 8a 9c dd f4 e9 e1 4a  1f 50 5d 95 ff f8 b9 f1  |.......J.P].....|
00000120  1e e9 15 05 60 12 fb 76  47 54 c5 32 55 60 fd b1  |....`..vGT.2U`..|
00000130  ea 0b 81 34 76 65 b2 72  a4 38 30 2c 8a 7d e0 33  |...4ve.r.80,.}.3|
00000140  03 0a ec e6 b8 ff 81 40  bc 24 f6 f4 3f 2e 3b 6d  |.......@.$..?.;m|
00000150  09 2b 74 00 d2 62 99 29  b8 3e 45 6d b5 57 e8 3f  |.+t..b.).>Em.W.?|
00000160  97 c8 16 e4 a7 6a c2 1b  ca dc 9c 9a a4 d1 9d 01  |.....j..........|
00000170  47 bd aa 44 99 ad e4 cf  47 9d 4e ae 08 99 11 25  |G..D....G.N....%|
00000180  78 97 29 7e 4f 70 fd c0  a6 ba fb 91 b8 c2 b0 32  |x.)~Op.........2|
00000190  be 5b 3d 7c 6b 24 1a 9b  05 52 df 3f 34 23 2d 35  |.[=|k$...R.?4#-5|
000001a0  7f ac e4 e5 54 67 fc 17  78 72 02 db e7 b4 de 42  |....Tg..xr.....B|
000001b0  63 ec 6f 1e 1e 92 de 54  43 85 2a 24 1c 9b 59 23  |c.o....TC.*$..Y#|
000001c0  9c e4 21 b4 07 cf 4e 35  96 a2 88 f7 0c 3f 09 de  |..!...N5.....?..|
000001d0  58 e2 51 45 5a 64 27 64  16 e2 05 1f b2 aa ab f7  |X.QEZd'd........|
000001e0  dc be b7 76 64 97 20 42  26 33 7a 0b 9c fc 44 c2  |...vd. B&3z...D.|
000001f0  e4 ff 2e 2e 20 fb 83 a2  8d d5 ba c7 88 ca 6f 9b  |.... .........o.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory
```Interesting: /dev/sdb1 and /dev/sdb2 seem to have been renamed /dev/mapper/nvidia_aebeeibc1 and /dev/mapper/nvidia_aebeeibc2.

Re RAID array: yes - sdb1 and sdc1 were members of a RAID 0 array which used to get mounted on /mnt/raid/.

Here's my fstab, which I recovered - I include this because it seems to me the UUIDs differ from those reported above:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=df42c8bd-2596-426f-89e1-797fcd2bb3cb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=547defd8-1426-406c-aba5-2e98f6c31a25 /boot           ext3    defaults        0       2
# /dev/sda1
UUID=5fac2116-0225-457a-968f-bd8d48d34a97 /var/lib        xfs     defaults        0       2
# /dev/sda2
UUID=a7d89c0e-b69b-42a0-92f0-124c804352a1 none            swap    sw,pri=0        0       0
/dev/md0    /mnt/raid    ext3    defaults    0    0
/dev/sdb2    none        swap    sw,pri=0    0    0
/dev/sdc2    none        swap    sw,pri=0    0    0
none     /dev/shm      tmpfs     defaults     0     0
```

---

### Post by Rubi1200 on 2010-10-31
Hi WestCoastSuccess,
I am very concerned with these results because, amongst other things, it shows no bootloaders installed and the file-systems are not mounting.

> No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/mapper/nvidia_aebeeibc

> Mounting failed:
mount: unknown filesystem type

as well as this:

> mount: wrong fs type, bad option, bad superblock on /dev/mapper/nvidia_aebeeibc1,
       missing codepage or helper program, or other error



All of this leads me to the unfortunate conclusion that you may have completely wiped things out.

Hopefully, someone with experience of RAID arrays will come along and offer some advice.

Also, in terms of possible data recovery options.

---

### Post by WestCoastSuccess on 2010-10-31
Ordinarily the boot loader would be on /dev/sda4 - it shows in the results:

```
============================= Boot Info Summary: ==============================

 => Testdisk is installed in the MBR of /dev/sda

```This is the Testdisk MBR I (probably stupidly) put on there.

Interestingly, learning that one of the components of the RAID array had been renamed from /dev/sdb1 to /dev/mapper/nvidia_aebeeibc1, I tried building the array - successfully, it appears:

```
ubuntu@ubuntu:/dev$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 
  Creation Time : Sun Oct 31 12:00:21 2010
     Raid Level : raid0
     Array Size : 621040640 (592.27 GiB 635.95 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0

    Update Time : Sun Oct 31 12:00:23 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1     252        1        1      active sync   /dev/block/252:1
```However it still refuses to mount.

Putting aside the RAID concerns, how can I place a boot loader onto /dev/sda4? Also, how can I write a correct partition table onto /dev/sda?

PS: what's completely baffling to me is that fdisk SEES all the partitions! However they don't appear correctly in the /dev folder and I cannot access them!

```
ubuntu@ubuntu:/dev$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         373     2996091   83  Linux
/dev/sda2             374        1832    11719417+  83  Linux
/dev/sda3            1833        2440     4883760   82  Linux swap / Solaris
/dev/sda4            2441       38913   292969372+  83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ae7ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38658   310520353+  fd  Linux raid autodetect
/dev/sdb2           38659       38913     2048287+  82  Linux swap / Solaris

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cf093

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38658   310520353+  fd  Linux raid autodetect
/dev/sdc2           38659       38913     2048287+  82  Linux swap / Solaris

Disk /dev/md0: 635.9 GB, 635945615360 bytes
2 heads, 4 sectors/track, 155260160 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Alignment offset: 33280 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

---

### Post by Rubi1200 on 2010-10-31
Presumably you had Ubuntu 10.04 on sda4 correct?

Let's try running these commands from the LiveCD to see if we can get things up and running again:
```
sudo e2fsck -C0 -p -f -v /dev/sda4
```If this shows errors, run this command:
```
sudo e2fsck -f -y -v /dev/sda4
```Obviously, if Ubuntu was not on sda4, change it to the correct partition number.

EDIT: is sda1 a /boot partition?

---

### Post by WestCoastSuccess on 2010-10-31
Here's the output:

```
ubuntu@ubuntu:/dev$ sudo e2fsck -C0 -p -f -v /dev/sda4
e2fsck: No such file or directory while trying to open /dev/sda4
/dev/sda4: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

``````
ubuntu@ubuntu:/dev$ sudo e2fsck -f -y -v /dev/sda4
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such file or directory while trying to open /dev/sda4

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```Using Testdisk, I found these superblocks:

```
Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63

     Partition                  Start        End    Size in sectors

  Linux                    0   1  1   372 254 57    5992176
superblock 0, blocksize=4096 []
superblock 32768, blocksize=4096 []
superblock 98304, blocksize=4096 []
superblock 163840, blocksize=4096 []
superblock 229376, blocksize=4096 []
superblock 294912, blocksize=4096 []

``````
ubuntu@ubuntu:/dev$ sudo e2fsck -C0 -p -f -v -b 32768 /dev/sda4
e2fsck: No such file or directory while trying to open /dev/sda4
/dev/sda4: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

``````
ubuntu@ubuntu:/dev$ sudo e2fsck -C0 -p -f -v -b 98304 /dev/sda4
e2fsck: No such file or directory while trying to open /dev/sda4
/dev/sda4: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```If I try it without specifying the partition:

```
ubuntu@ubuntu:/dev$ sudo e2fsck -C0 -p -f -v -b 98304 /dev/sda
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?

```The naming of the partitions used to be not in order - ie:


[LIST]
[*]sda4: now sda1 (EXT3; used to get mounted on /boot)
[*]sda3: now sda2 (EXT3; used to get mounted on /)
[/LIST]

[LIST]
[*]sda2: now sda3 (swap)
[*]sda1: now sda4 (XFS; used to get mounted on /var/lib)
[/LIST]
I think what I need to do is:


[LIST]
[*]recreate correct partition records on the disks
[*]get the /dev/mapper/nvidia* partitions to be correctly seen on /dev/sdb
[*]put a new MBR on sda
[/LIST]
Ubuntu 10.04 should be on (using the current naming) sda2 - I upgraded but it never did actually run 10.04, altho it booted to the splash screen, where it died.

Here's the final boot.log from 10.04 boot attempt:

```
swapon: /dev/disk/by-uuid/a7d89c0e-b69b-42a0-92f0-124c804352a1: swapon failed: Device or resource busy 
mountall: swapon /dev/disk/by-uuid/a7d89c0e-b69b-42a0-92f0-124c804352a1 [30704] terminated with status 255 
mountall: Problem activating swap: /dev/disk/by-uuid/a7d89c0e-b69b-42a0-92f0-124c804352a1 
swapon: /dev/sdb2: swapon failed: Device or resource busy 
mountall: swapon /dev/sdb2 [30715] terminated with status 255 
mountall: Problem activating swap: /dev/sdb2 
swapon: /dev/sdc2: swapon failed: Device or resource busy 
mountall: swapon /dev/sdc2 [30717] terminated with status 255 
mountall: Problem activating swap: /dev/sdc2
```And here's a bunch of interesting stuff from syslog:

```
Oct 29 17:26:44 HTPC laptop-mode: Remounting filesystems.
Oct 29 17:26:44 HTPC laptop-mode: /dev/sda3 not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: / not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking /dev/sda3 against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    /dev/sda3 contains /dev/sda, which is in HD, so we will remount it.
Oct 29 17:26:44 HTPC laptop-mode: Original options: rw,errors=remount-ro
Oct 29 17:26:44 HTPC laptop-mode: Reducing file system type.
Oct 29 17:26:44 HTPC laptop-mode: No saved mount options, so apparently we never remounted this filesystem during this session.
Oct 29 17:26:44 HTPC laptop-mode: Not remounting.
Oct 29 17:26:44 HTPC laptop-mode: Executing: /sbin/blockdev --setfra 256 /dev/sda3
Oct 29 17:26:44 HTPC laptop-mode: proc not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /proc not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking proc against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /sys not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /sys/fs/fuse/connections not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /sys/kernel/debug not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /sys/kernel/security not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /dev not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /dev/pts not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /dev/shm not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /var/run not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /var/lock not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /lib/init/rw not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: /dev/sda4 not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /boot not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking /dev/sda4 against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    /dev/sda4 contains /dev/sda, which is in HD, so we will remount it.
Oct 29 17:26:44 HTPC laptop-mode: Original options: rw
Oct 29 17:26:44 HTPC laptop-mode: Reducing file system type.
Oct 29 17:26:44 HTPC laptop-mode: No saved mount options, so apparently we never remounted this filesystem during this session.
Oct 29 17:26:44 HTPC laptop-mode: Not remounting.
Oct 29 17:26:44 HTPC laptop-mode: Executing: /sbin/blockdev --setfra 256 /dev/sda4
Oct 29 17:26:44 HTPC laptop-mode: /dev/sda1 not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /var/lib not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking /dev/sda1 against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    /dev/sda1 contains /dev/sda, which is in HD, so we will remount it.
Oct 29 17:26:44 HTPC laptop-mode: Original options: rw
Oct 29 17:26:44 HTPC laptop-mode: Reducing file system type.
Oct 29 17:26:44 HTPC laptop-mode: No saved mount options, so apparently we never remounted this filesystem during this session.
Oct 29 17:26:44 HTPC laptop-mode: Not remounting.
Oct 29 17:26:44 HTPC laptop-mode: Executing: /sbin/blockdev --setfra 256 /dev/sda1
Oct 29 17:26:44 HTPC laptop-mode: /dev/md0 not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /mnt/raid not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking /dev/md0 against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: none not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /dev/.bootchart/proc not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking none against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
Oct 29 17:26:44 HTPC laptop-mode: binfmt_misc not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: /proc/sys/fs/binfmt_misc not found in PARTITIONS.
Oct 29 17:26:44 HTPC laptop-mode: Checking binfmt_misc against HD because PARTITIONS contains "auto".
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sda.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdb.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdc.
Oct 29 17:26:44 HTPC laptop-mode:    Considering /dev/sdd.
```I still cannot understand how Gparted and fdisk can see the partitions properly but the kernel or whatever else cannot.

---

### Post by oldfred on 2010-10-31
I do not know RAID but it looks like you have two different RAIDs mixed up. The nvidia and a linux raid.

Was sda ever in a fake raid (nvidia?)?

Fakeraid writes metadata into the drive than can cause issues. You may want to run this on sda, but not on sdb or sdc. Only if sda is not part of your raid set.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) remove dmraid

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
Also check BIOS for raid settings
More discussion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by ronparent on 2010-10-31
It is hard to tell what you might have now by mixing mdadm raid and dmraid raid. The first is used to implement a software raid. The latter is used to discover and use a hybrid set up using a raid set on the MB (most often set up in windows systems).
> Interesting: /dev/sdb1 and /dev/sdb2 seem to have been renamed /dev/mapper/nvidia_aebeeibc1 and /dev/mapper/nvidia_aebeeibc2.
The correct interpretation of this is that /dev/mapper/nvidia_aebeeibc is a symbolic link representing usually a two disk raid set and the names ending with 1 and 2 represent the partitions on that disk.

Often a raid set is used by windows without the user even recognizing that it is a raid. Since it appears that the raid is now broken the questions to you are 1) Did you have data on those drive worth recovering (unlikely that it is recoverable unless it was a raid1 - it was more likely a raid0)? 2) Did you have a windows install on the disk set that you would like to reinstall? 3) Do you want to permanently break apart the raid and use them as separate drives of do you want to continue using them as raid drives, and what kind, software raid or 'fakeraid' (I can't stand that term)?

How we would proceed depends on where you want to go from here?

Note: Just looking back over the post I noticed:
> => No boot loader is installed in the MBR of /dev/mapper/nvidia_aebeeibc
This indicates that no boot loader was ever place on the raid from which I conclude sda and sdb may have never been used a a raid set (at least in this computer). If so you may want to clear the raid meta data as suggested by oldfred and just proceed with a normal clean install.

---

### Post by WestCoastSuccess on 2010-10-31
Many thanks for the replies.

This computer has never had windows on it - I assembled the computer myself after picking out the parts - it's custom made.

The RAID 0 array consisted of sdb1 and sdc2. It was not a motherboard raid; it was created using mdadm. However I thought the same thing when I saw "nvidia...", so checked the BIOS and RAID is definitely disabled, but I think 3.5 years ago when I built this thing, not knowing anything about RAID, I initially tried to create the motherboard RAID, then reverted to software RAID. So perhaps way back then it marked the drives (which makes sense, because initially there was only sda and sdb; sdc came later).

Now that you mention it, in my setup prior to attempting the upgrade (when it was running 8.04), it never properly assembled the array, and I had to write a script to have it build and start the array, then put the script into a cronjob which ran at restart.

```
sudo mdadm --misc --stop /dev/md0
sudo mdadm --build /dev/md0 --chunk=64 --level=0 --raid-devices=2 /dev/sdb1 /dev/sdc1
sudo mount -a
```What I'd like to do is be able to recover some of the files from the RAID array. I'm resigned at this point to replacing the drives - think I'll go 30G solid state for the operating system and 2 X 2TB RAID 0 for the rest. 

I'm able to build and start the array, but I cannot get at any of the files - Testdisk reports the filesystem appears damaged. 

Also, Testdisk cannot access the files on the XFS partition (sda4 on the current numbering scheme). There are some I'd like to retrieve from there too, if possible.

Luckily all my important files get backed up to an external drive and the Ubuntu cloud, but I'd like to be able to check to make sure everything that should have been backed up was, and to attempt to retrieve anything that isn't backed up.

Still seems strange to me that I cannot mount these partitions - how can I erase the marking that the hardware RAID put on the partitions?

---

### Post by WestCoastSuccess on 2010-10-31
Thanks ronparent and oldfred - I think I'm beginning to get some insight as to what's happening here: I think Ubuntu is seeing the markers for the hardware RAID on sda and attempting to build an array of it and sdb2. This would explain why I can see sdc, sdc1 and sdc2 in /dev but only sda and sdb (ie no sda1, sda2, sda3, sda4 or sdb1 and sdb2).

So that leads me to this: how can I disable that hardware RAID flag on sda and sdb? I think if I get rid of that, I may be able to mount the partitions that are not currently available because they're tied up in the nvidia array.

---

### Post by WestCoastSuccess on 2010-10-31
So it seems there are overlying (ie conflicting) partitions on sdb and nvidia_aebeeibc (I'm reasonably certain these refer to the same physical drive - note the identical disk identifier):

```
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ae7ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38658   310520353+  fd  Linux raid autodetect
/dev/sdb2           38659       38913     2048287+  82  Linux swap / Solaris

``````
Disk /dev/mapper/nvidia_aebeeibc: 640.1 GB, 640145817600 bytes
255 heads, 63 sectors/track, 77826 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0x000ae7ac

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_aebeeibc1               1       38658   310520353+  fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.
/dev/mapper/nvidia_aebeeibc2           38659       38913     2048287+  82  Linux swap / Solaris
Partition 2 does not start on physical sector boundary.

```If I remove the /dev/mapper/nvidia_aebeeibc partitions, will that destroy data? It seems this all goes back to my experiments setting up RAID 3.5 years ago! My thinking is that if I can use fdisk to remove the "nvidia" partitions, then I'll be left with just the sdb partitions on that disk, but am worried that removing the partitions from /dev/mapper/nvidia_aebeeibc may destroy the partitions on /dev/sdb. Any thoughts?

---

### Post by ronparent on 2010-10-31
To erase any dmraid markers on a drive, from the live cd write the following to a terminal:
> sudo dmraid -E -r /dev/sda
Also sdb etc. If you aren't using raid this can't do any harm. The nvidia_ references are for your fakeraid markers. They should disappear also once the meta data is erased. It won't destroy data unless the drives were used in a raid set up and you wrote data to them as such.

---

### Post by ronparent on 2010-11-01
To erase raid meta data: **sudo dmraid -E-r /dev/sda** (for each drive in turn - no damage can result if you never set up or used fakeraid).

---

### Post by WestCoastSuccess on 2010-11-01
You guys are geniuses: I followed your instructions, ronparent, and removed the so-called fakeraid partitions. The thing still won't boot, but now, rebooting into the live CD, I can mount most of the partitions!

Still can't get the software RAID array to mount (altho it will assemble and start), so will continue with that. I'll also have to figure out how to get the Testdisk MBR off the disk (sda) and replace it with a correct MBR/boot loader. But at least I can access the disc now and modify/replace files on it as needed.

In the meantime, I cannot thank you both enough - I've been working on this for over 3 days now, and to see those partitions and to tentatively issue the mount command and then to see them mount and have access to my files has left me delighted! Once again, the Ubuntu community comes to the rescue!

Sincerely, thanks for your help, suggestions and guidance!

UPDATE: I spoke too soon: the only files available on the RAID 0 array in TestDisk were ones which had been deleted a long time ago (ie from 2007-2008 ); anything more current was missing/inaccessible.

---

### Post by oldfred on 2010-11-01
drs305 has instructions for reinstalling the boot loader and totally uninstalling grub & grub2 and reinstall grub2 from chroot. You can try the simple two line (three line if separate /boot) and if that does not work use the full chroot version.

Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
chroot & grub uninstall & reinstall
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by WestCoastSuccess on 2010-11-07
Well, just to wrap up this thread, things did not go so well. I post this as a warning to others: if you're using GParted, I _**strongly**_ recommend against using the "Check" functionality. I managed to get my RAID 0 array assembled and running, then tried "checking" it in GParted, only "Check" doesn't mean "check"; it means "check and automatically respond 'yes' to any questions and erase data indiscriminately". I lost around 600GB of data after this thing ran, and it is, as near as I can tell, irretrievable - TestDisk finds nothing. Thankfully I have an external drive which backs up everything important each day, and I also sync extra-important stuff to the cloud.

Also, it seems my problem with a RAID array being destroyed on an upgrade does not appear to be unique - it seems later versions of Ubuntu (starting with 9.10 as near as I can tell) are set to very aggressively attempt to mount RAID arrays, and it seems that's why mine failed. I don't know if it probes the BIOS to see if hardware RAID exists and acts accordingly (even if it is disabled in the BIOS) or how exactly it makes its decisions.

Lastly, I ended up doing a completely fresh install of 10.04 on a new 32GB SSD and installed a couple of additional HDDs (am up to 5 now with just slightly under 3TB), and everything seems to be running fine now, altho I've given up mounting my RAID 0 array for the time being - 6 days of monkeying around trying to fix this system is enough for now! I have managed to mount my former non-RAID discs successfully, however one last word of warning: I tried using a program called "Storage Device Manager", which purports to be a tool which allows one to alter /etc/fstab from a graphical interface, however there are serious glitches in this program: if I set a mount point for a particular partition, it automatically changed another partition's mount point! If I changed that partition, the original changed. This went on for some time and I never was able to get it to behave. It also mis-identified sda4 as sda3 and also inserted things into /etc/fstab which caused booting to fail. Ended up manually editing /etc/fstab.

Oh, and if you're trying to format a partition to XFS in GParted and it isn't available (ie XFS is grayed out in the GParted formatting options), it is likely you'll have to install "xfsprogs" - just search for "xfs" in Synaptic. Once it's installed, restart GParted and XFS should appear as a valid option.

Thanks again, sincerely, to all those who helped me out with this!

---

