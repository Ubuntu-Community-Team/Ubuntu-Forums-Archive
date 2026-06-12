---
title: "grub  error 17"
date: 2010-01-15
forum: Installation &amp; Upgrades
---

### Post by nodenet on 2010-01-15
I had dual boot ubuntu and vista on my laptop. Then I dropped it. Vista wouldn't boot after that, but I was able to live with that
as I was able to mount the partition and could see my files.
I lived with that for six months but today i dropped it again and am getting grub error 17.
Put ubuntu into ram , ran diagnostics, tells me to replace harddrive.
However in that mode I can still see the Vista partition files.
My problem is that I want to recover a few text files from my old ubuntu desktop.

Where do I start?

---

### Post by darkod on 2010-01-15
If it can work, boot with ubuntu cd, Try Ubuntu option, and look in Places. Both vista and ubuntu partitions will show something like xxGB filesystem (if they can be read).

Open your root partition (you would be able to guess it by size) and look inside for the files you need. Copy to usb stick or external hdd. Same for vista partition.

---

### Post by nodenet on 2010-01-15
have done that but it is only showing the vista partition.

fstab shows

unionfs /unionfs rw 0 0
tmpfs tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap swap defaults 0 0

---

### Post by nodenet on 2010-01-15
have downloaded the Boot Info script onto usb stick, put on desktop of Try version
Do i just right click it and run?

---

### Post by nodenet on 2010-01-15
This is result of Boot Info Script

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c62b218

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   171,991,889   171,991,827   7 HPFS/NTFS
/dev/sda2         171,991,890   234,436,544    62,444,655   5 Extended
/dev/sda5         171,991,953   231,769,754    59,777,802  83 Linux
/dev/sda6         231,769,818   234,436,544     2,666,727  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2002 MB, 2002780160 bytes
16 heads, 32 sectors/track, 7640 cylinders, total 3911680 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3193ce41

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,064     3,911,679     3,903,616   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6274A9BA5FA690E3" TYPE="ntfs" 
/dev/sda6: UUID="d99001db-1246-69ba-d3b9-3502ba8b9090" TYPE="swap" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="STORE N GO" UUID="1B9A-F07D" TYPE="vfat" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdb1 on /media/STORE N GO type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2


Unknown BootLoader  on sda5


Unknown BootLoader  on sdb1

00000000  eb 42 90 4d 53 44 4f 53  35 2e 30 00 02 40 20 00  |.B.MSDOS5.0..@ .|
00000010  02 00 02 00 00 f8 00 01  20 00 10 00 80 1f 00 00  |........ .......|
00000020  80 90 3b 00 00 01 29 7d  f0 9a 1b 53 54 4f 52 45  |..;...)}...STORE|
00000030  20 4e 20 47 4f 20 46 41  54 31 36 20 20 20 10 00  | N GO FAT16   ..|
00000040  01 00 00 7e fc bd 00 7c  66 bb 00 00 00 00 8e d3  |...~...|f.......|
00000050  8b e5 fb 8e c3 26 c5 77  78 52 1e 56 8b fd b9 0b  |.....&.wxR.V....|
00000060  00 f3 a4 8e db c6 46 09  0f 8a 46 18 88 46 04 89  |......F...F..F..|
00000070  6f 78 89 5f 7a 32 e4 cd  13 84 d2 79 2a b4 41 bb  |ox._z2.....y*.A.|
00000080  aa 55 cd 13 72 0f 81 fb  55 aa 75 09 d1 e9 73 05  |.U..r...U.u...s.|
00000090  c6 06 3f 7d 74 b4 08 cd  13 72 0c 83 e1 3f 89 4e  |..?}t....r...?.N|
000000a0  18 8a ce 41 89 4e 1a 0f  b6 46 10 f7 66 16 e8 ac  |...A.N...F..f...|
000000b0  00 8b 4e 11 c1 e9 04 51  e8 53 00 be dd 7d 8b fb  |..N....Q.S...}..|
000000c0  b9 0b 00 f3 a6 75 2e f6  05 18 75 29 58 e8 9c 00  |.....u....u)X...|
000000d0  8b 47 1a 66 ff 76 46 50  48 48 3d ed ff 77 24 0f  |.G.f.vFPHH=..w$.|
000000e0  b6 4e 0d f7 e1 e8 85 00  e8 23 00 81 7f 09 e8 5f  |.N.......#....._|
000000f0  75 11 e9 14 01 83 c3 20  79 c1 b8 01 00 e8 6c 00  |u...... y.....l.|
00000100  59 e2 b4 66 8b 46 fa 66  a3 78 00 e9 da 00 bf 05  |Y..f.F.f.x......|
00000110  00 51 8b 46 48 33 d2 f7  76 18 91 8b 46 46 f7 76  |.Q.FH3..v...FF.v|
00000120  18 42 87 ca 3b 56 1a 73  18 f7 76 1a 8a f2 86 c5  |.B..;V.s..v.....|
00000130  c1 e8 02 c0 cc 02 0a c8  0a f4 84 e4 b8 01 02 eb  |................|
00000140  08 8c 46 44 b4 42 be 3e  7c bb 00 7e 8a 56 fe cd  |..FD.B.>|..~.V..|
00000150  13 59 73 1f 4f 74 ac 32  e4 cd 13 eb b4 03 46 1c  |.Ys.Ot.2......F.|
00000160  13 56 1e 89 46 46 89 56  48 8b 46 0e 99 01 46 46  |.V..FF.VH.F...FF|
00000170  11 56 48 c3 00 00 00 00  00 00 00 00 00 00 00 00  |.VH.............|
00000180  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  00 00 00 00 00 00 00 00  00 0d 4e 6f 6e 2d 73 79  |..........Non-sy|
000001c0  73 74 65 6d 20 64 69 73  6b 2c 20 70 72 65 73 73  |stem disk, press|
000001d0  20 61 6e 79 20 6b 65 79  2e 2e 2e 07 00 42 4f 4f  | any key.....BOO|
000001e0  54 57 49 5a 20 53 59 53  be b9 7d ac b4 0e b3 07  |TWIZ SYS..}.....|
000001f0  cd 10 ac 84 c0 75 f5 98  cd 16 cd 19 00 00 55 aa  |.....u........U.|
00000200


=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
ls: cannot access /dev/mapper: No such file or directory

---

### Post by darkod on 2010-01-15
Not sure, but if it's on desktop you can execute it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create the mentioned results.txt file on desktop.

---

### Post by darkod on 2010-01-15
From the live desktop try:

sudo fsck /dev/sda5
sudo fsck /dev/sda6

It will check filesystem on root and swap partition. If you're lucky it will sort them out. You notice in the script results the filesystem of /dev/sda5 and /dev/sda6 are not recognized.

---

### Post by nodenet on 2010-01-15
the result from running fsck /dev/sda5
was
> fsck.ext2 Attempt to read block from filesystem resulted in short read while trying ti open /dev/sda5
Could this be zero length partition?

result from fsck /dev/sda6

> fsck.swap : not found
Error 2 while executing fsck.swap for /dev/sda6

---

### Post by darkod on 2010-01-15
Sorry, this is beyond my knowledge. Maybe someone else will jump in.

---

