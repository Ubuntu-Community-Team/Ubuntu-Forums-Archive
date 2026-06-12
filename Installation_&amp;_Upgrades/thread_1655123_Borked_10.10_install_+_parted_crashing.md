---
title: "Borked 10.10 install + parted crashing"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by crazymatt1 on 2010-12-29
I attempted an installation of 10.10 Desktop from a LiveCD on my old-ish  laptop (2GHz Pentium M; 1.2 GB RAM; 60 GB HDD).  When given the option,  I elected to remove my old operating system (WinXP) and replace it with  Ubuntu, using the entire drive.  When I clicked on 'Forward' and got to  the time zone screen, the installation hung, and I eventually got a  black screen and error message (which, of course, I didn't write down at  the time).

I suspect that the error was related to read error(s) from my CD drive,  because I proceeded to get them in bunches when re-attempting the  installation.  I switched to a LiveUSB and things seemed to be back on  track.  Unfortunately, this time the installation hung after clicking  'Forward' on the "Preparing to install Ubuntu" screen.

I suspected that the error might have come from the failing during the  formatting/repartitioning, so I booted into Ubuntu from the LiveUSB and  checked the Disk Utility.  It showed the hard drive as formatted with no  partitions.  I created partitions using Disk Utility and tried running  the installer from the desktop.  It hung in the same place, but this  time I got a crash notification: "parted_server has stopped working".   When I tried running GParted, it gave the same error.

I tried researching problems with installation and parted on the forums and found [these]("http://ubuntuforums.org/showthread.php?t=1654855") [two]("http://ubuntuforums.org/showthread.php?t=1653915") threads.  Neither was able to really help me, but I can at least post some more information here.

output of **sudo parted -l** (small L)
```
Model: ATA Hitachi HTS54106 (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      32.3kB  5001MB  5001MB  primary  ext4            boot
 2      5001MB  7000MB  1999MB  primary  linux-swap(v1)
 3      7000MB  60.0GB  53.0GB  primary  ext4


Backtrace has 16 calls on stack:
  16: /lib/libparted.so.0(ped_assert+0x2a) [0x2e487a]
  15: /lib/libparted.so.0(+0x41257) [0x31c257]
  14: /lib/libparted.so.0(+0x42077) [0x31d077]
  13: /lib/libparted.so.0(+0x4336c) [0x31e36c]
  12: /lib/libparted.so.0(+0xe161) [0x2e9161]
  11: /lib/libparted.so.0(ped_disk_add_partition+0x262) [0x2ec9f2]
  10: /lib/libparted.so.0(+0x44dc5) [0x31fdc5]
  9: /lib/libparted.so.0(+0x44fcf) [0x31ffcf]
  8: /lib/libparted.so.0(ped_disk_new+0x75) [0x2ed7d5]
  7: parted() [0x804db58]
  6: parted() [0x804ece3]
  5: parted() [0x8050ffa]
  4: parted() [0x8052671]
  3: parted(main+0x2e) [0x805277e]
  2: /lib/libc.so.6(__libc_start_main+0xe7) [0x687ce7]
  1: parted() [0x804bbb1]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

    http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

    http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

    parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (head_size <= 63) at ../../../libparted/labels/dos.c:662 in function
probe_partition_for_geom() failed.

Aborted (core dumped)
```Report from** Boot Info Script**:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     9,767,519     9,767,457  83 Linux
/dev/sda2           9,767,520    13,671,314     3,903,795  82 Linux swap / Solaris
/dev/sda3          13,671,315   117,210,239   103,538,925  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,064     7,831,551     7,823,488   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        073f4eb4-e906-4ee6-8677-132a0192021b   ext4       Ubuntu                        
/dev/sda2        10e9e76d-9739-4173-bb10-a18802e9c9cc   swap       Swap                          
/dev/sda3        af2762f4-9e93-4b9d-850f-1bff046b864d   ext4       Data                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        1BE2-327C                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/Data              ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/Ubuntu            ext4       (rw,nosuid,nodev,uhelper=udisks)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 80 1f 00 00  |........?.......|
00000020  80 60 77 00 ca 1d 00 00  00 00 00 00 02 00 00 00  |.`w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 7c 32 e2 1b 4e  4f 20 4e 41 4d 45 20 20  |..)|2..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 bc 3b 00 00  66 ba 00 00 00 00 bb 00  |}.f..;..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```So that's where I am.  I'd really like to get a functioning OS back onto my laptop.  Any help is greatly appreciated!

---

### Post by coffeecat on 2010-12-29
Did you use the same ISO for the live CD and for the live USB? And did you check the md5sum for the downloaded ISO? You need to exclude a faulty download.

Apart from that I have little to offer. It's odd that parted is crashing after (seemingly) creating perfectly good partitions. If the md5sum is correct, try this. Boot up into the live desktop - not directly to the installer. Go to System > Administration > Gparted. Then from the Device menu create a new (ms-dos) partition table. Don't do anything else - leave the whole disc as unallocated but with a fresh partition table. Now close Gparted, start the installer and select 'use whole disc', or whatever the wording is, at the partitioning stage.

---

### Post by crazymatt1 on 2010-12-29
Thanks for the suggestions.

I did use the same ISO for both the CD and USB.  I just checked the md5 and it matches what's listed @ releases.ubuntu.com

I can't run GParted because it crashes.  I get a crash report notification in the top bar.  When I click on it, it says "Sorry, GParted closed unexpectedly".  If I try to report the problem, I get another error box that says ```
The problem cannot be reported:

The program crashed on an assertion failure, but the message could not be retrieved.
Apport does not support reporting these crashes.
```  I suspect this is related to the bug that's listed in my parted -l output.

Using Disk Utility to reformat the drive results in the same parted_server error I was previously receiving during installation.

---

### Post by coffeecat on 2010-12-29
Hmmm. Very odd. I've had the reverse problem trying to install PCLinuxOS where Gparted in PCLinuxOS kept crashing on me. Eventually I used Ubuntu's Gparted to prepare my partitions (which behaved just fine) and then in the PCLinuxOS installer avoided reformatting the partitions.

Another suggestion then. Use [Gparted live]("http://gparted.sourceforge.net/livecd.php"), or a partitioner on any other recent Linux live CD, to prepare your partitions. Then boot up the Ubuntu live CD, start the installer and use the manual/advanced option. Tell the installer to use whichever partition you want for / - it will pick up swap automatically - plus any other partitions such as /home that you may have prepared. But this time untick the 'format this partition' box for each partition. If you don't reformat any partitions in the installer, parted will not be used and the installer will simply go on to copy all the files to the partition(s).

Hopefully. :| I say hopefully because whatever you do, it insists on reformatting the swap partition but giving it the same UUID (the ultimate in futile gestures, in my view), which may involve parted.

---

### Post by Bucky Ball on 2010-12-29
If you have another computer I would perhaps download the iso, burn another cd and try again. This time, remove all partitions with gparted on the live cd leaving free space. Then go for an install. 

There is also an option to check the disk for defects from memory when you boot from it. Do that.

I generally get the ISOs via torrents. Much more reliable that way. Available on the 'alternative downloads page' or something like that. Good luck.

10.04 is the current long term release and possibly a little more stable (1 year more support than 10.10). ;)

---

### Post by crazymatt1 on 2010-12-29
> **coffeecat said:**
> <snip>
Another suggestion then. Use [Gparted live]("http://gparted.sourceforge.net/livecd.php"), or a partitioner on any other recent Linux live CD, to prepare your partitions. Then boot up the Ubuntu live CD, start the installer and use the manual/advanced option. Tell the installer to use whichever partition you want for / - it will pick up swap automatically - plus any other partitions such as /home that you may have prepared. But this time untick the 'format this partition' box for each partition. If you don't reformat any partitions in the installer, parted will not be used and the installer will simply go on to copy all the files to the partition(s).<snip>

Thanks again for the further suggestions.  I downloaded and installed Gparted Live to a USB.  Ran fine and detected my HDD (although it saw it as 55.89GB, whereas Disk Utility saw it as 60).  Tried running the installer after successfully creating 0, 1, and 3 partitions using Gparted Live.  In all 3 cases, the installer gave the same parted_server error as before, and when booting into Ubuntu live, GParted also still crashed.

> **Bucky Ball said:**
> If you have another computer I would perhaps download the iso, burn another cd and try again. This time, remove all partitions with gparted on the live cd leaving free space. Then go for an install.

There is also an option to check the disk for defects from memory when you boot from it. Do that.

I generally get the ISOs via torrents. Much more reliable that way. Available on the 'alternative downloads page' or something like that. Good luck.

10.04 is the current long term release and possibly a little more stable (1 year more support than 10.10). ;)

Thanks for your suggestions.  I have been using the ISO from the torrent on the download page and the md5 checks out.  I recreated my LiveUSB, but that didn't fix the problem.  I am limited to using a LiveUSB (and not a LiveCD) because my wonky CD drive is what got me into this mess in the first place.

I'm not sure where the option to check the disk is.  There's an option to run Memtest86, but I don't see anything that would check the HDD.

As for 10.04, if I don't get this figured out in a few days, I'll try to switch to that.

---

### Post by coffeecat on 2010-12-29
> **crazymatt1 said:**
> Ran fine and detected my HDD (although it saw it as 55.89GB, whereas Disk Utility saw it as 60).

Gibibytes (GiB) and Gigabytes (GB). Gparted is reporting in GiB (1 GiB = 1024x1024x1024 bytes) and Disk Utility in GB (1GB = 1000000000 bytes). 60GB = 55.88 GiB.

> **crazymatt1 said:**
> As for 10.04, if I don't get this figured out in a few days, I'll try to switch to that.

Good luck with that. Since 10.04 simply uses earlier versions of Gparted and parted you may get the same. I'm beginning to wonder if there is something wrong with the hard drive. Perhaps a bad sector in the area of the partition table.

---

