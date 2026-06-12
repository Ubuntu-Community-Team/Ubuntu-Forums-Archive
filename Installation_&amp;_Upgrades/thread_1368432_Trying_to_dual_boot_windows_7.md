---
title: "Trying to dual boot windows 7"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by wiz_master49 on 2009-12-30
Ok, so I have a problem. I will copy/paste what I wrote on another forum I frequently visit:

Let me just apologize for the long post beforehand. Now on to the matter at hand. I only have one 250GB hard drive. It is partitioned into 2 parts. One 130GB partition and another 100GB partition. Before it was just these 2 partitions though, it was partitioned into 3. 100GB, 30GB, and 100GB. Windows 7 was on the first but space got low so I used Partition Wizard Home Edition to resize it combining the 100 and the 30GB partition. After that my computer kept stalling at "Verifying DMI Pool Data." So I did a little bit of Google searching and most of it said to try fixing the MBR with a the Windows 7 dvd, so I did. Here is the exact commands I did:
```
E:
enter
DIR
enter
CD boot
enter
bootsect /nt60 SYS
enter
exit
```
After this I restarted and could boot right back into Windows 7 just fine. Windows 7 x64 Professional is installed in the 130GB partition. I am trying to dual boot Ubuntu 9.10 by installing it in the 100GB partition but whenever I boot into the Live CD and get to the partition part of the installation, I notice it doesn't list my Windows 7 partition. So I opened up Gparted and it shows an error on that specific partition: [http://i45.tinypic.com/309pp48.jpg](http://i45.tinypic.com/309pp48.jpg)

So I booted into the Windows 7 dvd and ran that command, but now I get stuck at Verifying DMI Pool Data again so I am stuck going in circles. If I do ```
chkdsk /f
``` I get stuck at Verifying DMI Pool Data, if I redo the MBR like earlier I can boot into Windows 7 successfully but Ubuntu doesn't see my Windows partition. So anyone have any idea what could be going on?

---

### Post by wiz_master49 on 2009-12-30
Bump, any help is appreciated.

---

### Post by Moozillaaa on 2009-12-30
This is a stab in the dark, but something to consider anyway...

Windows 7 and some GRUB versions do NOT get along because of inode sizing differences. I do not remember the fix either.

The first time I saw it, it was SuSE 11.1, and my Ubuntu version. SuSE uses a different inode size than the GRUB that I had.

Now, I'm seeing that Windows 7 has a problem with a very popular app (Ext2fsd) that allows Windows to mount, read, and write to Linux. It's because of inode size incompatibility.

If that's your problem, I can't say for sure...

---

### Post by presence1960 on 2009-12-30
The great thing about Linux is you can use it to diagnose & repair windows problems too. I need to see exactly what you have on there. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by oldfred on 2009-12-31
Run the script presence recommends so we can see your configuration.

I have seen where the windows repair only repairs one thing at a time so you should run it several times to get it fixed.

Comment from a windows forum:
boot from Windows 7 dvd and select repair your computer at the Install Now screen. 
Run Startup repair thrice and reboot.

---

### Post by wiz_master49 on 2009-12-31
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/sdg
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd91f9e7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   273,121,064   273,121,002   7 HPFS/NTFS
/dev/sda2         273,121,547   488,392,001   215,270,455   f W95 Ext d (LBA)
/dev/sda5         273,121,610   488,392,001   215,270,392   7 HPFS/NTFS


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 2017 MB, 2017459712 bytes
4 heads, 32 sectors/track, 30783 cylinders, total 3940351 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd3486dc6

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             32     3,940,350     3,940,319   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

sda5: UUID="01CA6AEEB700BCC0" LABEL="DRV1_VOL2" TYPE="ntfs" 
sdf1: UUID="9AA6E9A8A6E9855B" LABEL="My Book" TYPE="ntfs" 
sdg1: SEC_TYPE="msdos" LABEL="CRUZER MINI" UUID="2D97-00A9" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdg1 on /media/CRUZER MINI type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  22 3f 3a 3c 00 3d 4f 05  00 00 55 15 c9 8a 4b 4c  |"?:<.=O...U...KL|
00000010  93 22 9f 3d 3d 00 25 13  29 91 55 23 fc 62 22 2d  |.".==.%.).U#.b"-|
00000020  65 25 23 5d b1 1b 25 1f  ac 17 00 09 8d 6c 08 23  |e%#]..%......l.#|
00000030  a4 a9 22 5d b2 52 44 02  22 dd ab 1c 23 7f ac 1b  |.."].RD."...#...|
00000040  00 1d 54 f8 22 1d aa 53  13 e9 8b 1c 5c 46 22 1d  |..T."..S....\F".|
00000050  4b 1b 54 04 7d 47 3f 44  74 22 0c 40 01 0a 00 1b  |K.T.}G?Dt".@....|
00000060  00 73 f2 3f 00 0a 9f 00  0e 00 10 9d 06 40 5c 02  |.s.?.........@\.|
00000070  22 bf 55 44 00 10 44 01  12 29 82 0f 23 ed 5d 0f  |".UD..D..)..#.].|
00000080  54 04 7c 02 01 0e 00 0f  00 7d 00 0f 54 1a 7d 07  |T.|......}..T.}.|
00000090  02 5c 67 7d 22 02 5c 3f  22 2e 54 4c 00 22 35 be  |.\g}".\?".TL."5.|
000000a0  00 55 19 02 13 28 93 22  4c 3f 22 dc 33 22 4c 44  |.U...(."L?".3"LD|
000000b0  6d 01 0e 23 e4 b2 7d 1a  0e 47 1d 00 00 25 44 05  |m..#..}..G...%D.|
000000c0  22 fc 41 22 54 b3 22 5c  42 01 4a 00 24 00 7c 05  |".A"T."\B.J.$.|.|
000000d0  01 06 00 01 00 22 9c 3e  24 bd 63 00 55 0a 01 23  |.....".>$.c.U..#|
000000e0  4d 66 06 54 02 22 be 3e  56 00 65 8e 00 55 4a 1e  |Mf.T.".>V.e..UJ.|
000000f0  44 45 22 dc b4 24 9c 53  6c 06 22 df 4b 56 00 1e  |DE"..$.Sl.".KV..|
00000100  9d 4f 0e 54 21 6d 0f 43  15 ab 87 24 00 0e 13 ab  |.O.T!m.C...$....|
00000110  86 44 00 31 9d 00 2f 1b  e1 96 00 55 47 43 13 69  |.D.1../....UGC.i|
00000120  88 2f 5c 02 7d 25 1d 5c  00 22 9d 46 61 55 0b 4d  |./\.}%.\.".FaU.M|
00000130  23 fd b0 00 13 0b 87 1f  00 41 1b b0 8d 61 ae 42  |#........A...a.B|
00000140  5d 41 4d 5c 01 22 7c 47  6c eb 7f 00 4d 00 43 44  |]AM\."|Gl...M.CD|
00000150  4e 7e 09 0c 00 7f 01 61  00 4d 9c 01 6c 26 a4 16  |N~.....a.M..l&..|
00000160  64 d5 ae 00 56 ce 38 5c  af 6c a8 74 04 6c 79 7c  |d...V.8\.l.t.ly||
00000170  00 22 2d 4e c8 5c 9f fc  00 6c bf 7c c8 7c c0 09  |."-N.\...l.|.|..|
00000180  f4 6c ea 40 ce 08 80 41  d1 22 5b bd 7c db 7c cf  |.l.@...A."[.|.|.|
00000190  7c d3 01 e8 d9 0f c1 22  2c 2b 22 2c 29 22 ac 2f  ||......",+",)"./|
000001a0  22 dc 29 22 ac 2f 0d 6a  4d 03 c1 ba 49 a6 40 9a  |".)"./.jM...I.@.|
000001b0  19 88 41 4d f3 f6 3f 6c  dc 7c d5 6c e7 22 00 fe  |..AM..?l.|.l."..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 f8 c3 d4 0c 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdg1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 40 01 00  |.<.DOK01.02..@..|
00000010  02 00 02 00 00 f8 f1 00  20 00 04 00 20 00 00 00  |........ ... ...|
00000020  df 1f 3c 00 80 01 29 a9  00 97 2d 00 00 00 00 00  |..<...)...-.....|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

Also, I failed to mention that I did in fact try running startup repair but it never found anything wrong.

---

### Post by wiz_master49 on 2009-12-31
Bump

---

### Post by oldfred on 2009-12-31
Windows xp and Ubuntu start at sector 63. Vista and Win7 start at sector 2048. When you repartitioned you moved the win partition to the left and this is why it is having problems. 

I am not sure of the fix, I thought the windows repair fixed this and after several reboots it would work.

I did find:
This realignment will prevent Vista/Win 7 from booting until the Boot Configuration Database (BCD) is repaired.

Then with the win7 install dvd, used the repair command line and type:
bootrec /fixmbr (press enter)
bootrec /fixboot (press enter)
bootrec /rebuildbcd (press enter)

---

### Post by wiz_master49 on 2009-12-31
> **oldfred said:**
> Windows xp and Ubuntu start at sector 63. Vista and Win7 start at sector 2048. When you repartitioned you moved the win partition to the left and this is why it is having problems. 

I am not sure of the fix, I thought the windows repair fixed this and after several reboots it would work.

I did find:
This realignment will prevent Vista/Win 7 from booting until the Boot Configuration Database (BCD) is repaired.

Then with the win7 install dvd, used the repair command line and type:
bootrec /fixmbr (press enter)
bootrec /fixboot (press enter)
bootrec /rebuildbcd (press enter)

I will try this and edit my post with results but I wanted to mention that I have only ever had Windows Vista/7 on this computer and only currently have Windows 7 on it. I always reformat before installing an OS so I don't know why it says I have Windows XP.

Edit: Ok ran the commands now;
bootrec /fixmbr
Operation Successful
bootrec /fixboot
Operation Successful
bootrec /rebuildbcd
This may take awhile.
Number of Windows installations found: 0

Rebooted and booted into Windows 7 no problem, booted up live cd and still has the same error.

---

### Post by wiz_master49 on 2009-12-31
Bump

---

### Post by meierfra. on 2009-12-31
This is very weird.   I would like to figure out what changes when you run "chkdsk  /f".  Do this:


1) Before running "chkdsk /f", boot from the Ubuntu LiveCD, open a terminal and 

```
sudo apt-get install testdisk
sudo testdisk /dev/sda

```

Choose "proceed" on the first screen, then

"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"


Post the content of  that screen.

Then press "q" a few times to  exit testdisk.


2)  Run "chkdsk -f" from the Windows 7 DVD. Then boot from the Ubuntu Live CD,  run the boot_info_script again and post the "RESULTS.txt". Also run "testdisk RebuildBS" again and post the "RebuildBS" screen, just as above,

---

### Post by wiz_master49 on 2009-12-31
Ok here is the first go at it before chkdsk /f:
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 17000 254 63  273121002 [DRV1_VOL1]

filesystem size           273121002 273121001
sectors_per_cluster       8 8
mft_lcn                   5166768 5166768
mftmirr_lcn               1 1
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.

```

Will edit in the 2nd go once done.

Edit: After;Boot script info;
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sde
 => Windows is installed in the MBR of /dev/sdf
 => Windows is installed in the MBR of /dev/sdg
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdf1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdg1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd91f9e7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   273,121,064   273,121,002   7 HPFS/NTFS
/dev/sda2         273,121,547   488,392,001   215,270,455   f W95 Ext d (LBA)
/dev/sda5         273,121,610   488,392,001   215,270,392   7 HPFS/NTFS


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 997 MB, 997195776 bytes
64 heads, 32 sectors/track, 951 cylinders, total 1947648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *            369     1,945,599     1,945,231   6 FAT16


Drive: sdf ___________________ _____________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 2017 MB, 2017459712 bytes
4 heads, 32 sectors/track, 30783 cylinders, total 3940351 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd3486dc6

Partition  Boot         Start           End          Size  Id System

/dev/sdg1    *             32     3,940,350     3,940,319   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

sda1: UUID="01CA884544737A20" LABEL="DRV1_VOL1" TYPE="ntfs" 
sda5: UUID="2C90738790735674" LABEL="DRV1_VOL2" TYPE="ntfs" 
sde1: SEC_TYPE="msdos" LABEL="" TYPE="vfat" 
sdf1: UUID="9AA6E9A8A6E9855B" LABEL="My Book" TYPE="ntfs" 
sdg1: SEC_TYPE="msdos" LABEL="CRUZER MINI" UUID="2D97-00A9" TYPE="vfat" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdf1 on /media/My Book type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sde1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdg1 on /media/CRUZER MINI type vfat (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  22 3f 3a 3c 00 3d 4f 05  00 00 55 15 c9 8a 4b 4c  |"?:<.=O...U...KL|
00000010  93 22 9f 3d 3d 00 25 13  29 91 55 23 fc 62 22 2d  |.".==.%.).U#.b"-|
00000020  65 25 23 5d b1 1b 25 1f  ac 17 00 09 8d 6c 08 23  |e%#]..%......l.#|
00000030  a4 a9 22 5d b2 52 44 02  22 dd ab 1c 23 7f ac 1b  |.."].RD."...#...|
00000040  00 1d 54 f8 22 1d aa 53  13 e9 8b 1c 5c 46 22 1d  |..T."..S....\F".|
00000050  4b 1b 54 04 7d 47 3f 44  74 22 0c 40 01 0a 00 1b  |K.T.}G?Dt".@....|
00000060  00 73 f2 3f 00 0a 9f 00  0e 00 10 9d 06 40 5c 02  |.s.?.........@\.|
00000070  22 bf 55 44 00 10 44 01  12 29 82 0f 23 ed 5d 0f  |".UD..D..)..#.].|
00000080  54 04 7c 02 01 0e 00 0f  00 7d 00 0f 54 1a 7d 07  |T.|......}..T.}.|
00000090  02 5c 67 7d 22 02 5c 3f  22 2e 54 4c 00 22 35 be  |.\g}".\?".TL."5.|
000000a0  00 55 19 02 13 28 93 22  4c 3f 22 dc 33 22 4c 44  |.U...(."L?".3"LD|
000000b0  6d 01 0e 23 e4 b2 7d 1a  0e 47 1d 00 00 25 44 05  |m..#..}..G...%D.|
000000c0  22 fc 41 22 54 b3 22 5c  42 01 4a 00 24 00 7c 05  |".A"T."\B.J.$.|.|
000000d0  01 06 00 01 00 22 9c 3e  24 bd 63 00 55 0a 01 23  |.....".>$.c.U..#|
000000e0  4d 66 06 54 02 22 be 3e  56 00 65 8e 00 55 4a 1e  |Mf.T.".>V.e..UJ.|
000000f0  44 45 22 dc b4 24 9c 53  6c 06 22 df 4b 56 00 1e  |DE"..$.Sl.".KV..|
00000100  9d 4f 0e 54 21 6d 0f 43  15 ab 87 24 00 0e 13 ab  |.O.T!m.C...$....|
00000110  86 44 00 31 9d 00 2f 1b  e1 96 00 55 47 43 13 69  |.D.1../....UGC.i|
00000120  88 2f 5c 02 7d 25 1d 5c  00 22 9d 46 61 55 0b 4d  |./\.}%.\.".FaU.M|
00000130  23 fd b0 00 13 0b 87 1f  00 41 1b b0 8d 61 ae 42  |#........A...a.B|
00000140  5d 41 4d 5c 01 22 7c 47  6c eb 7f 00 4d 00 43 44  |]AM\."|Gl...M.CD|
00000150  4e 7e 09 0c 00 7f 01 61  00 4d 9c 01 6c 26 a4 16  |N~.....a.M..l&..|
00000160  64 d5 ae 00 56 ce 38 5c  af 6c a8 74 04 6c 79 7c  |d...V.8\.l.t.ly||
00000170  00 22 2d 4e c8 5c 9f fc  00 6c bf 7c c8 7c c0 09  |."-N.\...l.|.|..|
00000180  f4 6c ea 40 ce 08 80 41  d1 22 5b bd 7c db 7c cf  |.l.@...A."[.|.|.|
00000190  7c d3 01 e8 d9 0f c1 22  2c 2b 22 2c 29 22 ac 2f  ||......",+",)"./|
000001a0  22 dc 29 22 ac 2f 0d 6a  4d 03 c1 ba 49 a6 40 9a  |".)"./.jM...I.@.|
000001b0  19 88 41 4d f3 f6 3f 6c  dc 7c d5 6c e7 22 00 fe  |..AM..?l.|.l."..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 f8 c3 d4 0c 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdg1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 40 01 00  |.<.DOK01.02..@..|
00000010  02 00 02 00 00 f8 f1 00  20 00 04 00 20 00 00 00  |........ ... ...|
00000020  df 1f 3c 00 80 01 29 a9  00 97 2d 00 00 00 00 00  |..<...)...-.....|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd 
```

Testdisk info;
```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 17000 254 63  273121002 [DRV1_VOL1]

filesystem size           273121002 273121001
sectors_per_cluster       8 8
mft_lcn                   5166768 5166768
mftmirr_lcn               1 1
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.
```

I also took a couple pictures of the chkdsk /f process with my digital camera just to possibly help out in any way possible:
[http://i49.tinypic.com/2qavfw3.jpg](http://i49.tinypic.com/2qavfw3.jpg)
[http://i50.tinypic.com/16kbczk.jpg](http://i50.tinypic.com/16kbczk.jpg)
[http://i45.tinypic.com/102wl7c.jpg](http://i45.tinypic.com/102wl7c.jpg)

Now that I did chkdsk /f I have to boot from Windows 7 dvd and do bootsect /nt60 SYS because it gets stuck at Verifying DMI Pool Data like I said in the first post.

---

### Post by meierfra. on 2010-01-01
None of the parameters in the boot parameter block changed. So I have no clue what is going on.

I'm not sure whether this will lead to anything, but I suggest to compare the boot sectors before and after "chkdsk". (Sorry, I should of asked for this earlier instead of making you run chkdsk again)

Boot from the Ubuntu Live CD


```

sudo dd if=/dev/sda1 of=before.mbr count=126
sudo tar -czvf before.mbr.tar.gz before.mbr

```
(Be very careful with the "dd" command, if it runs for more one just a few seconds, stop the process with "ctrl c")
This created the file "before.mbr.tar.gz" in the home directory. Attach it to your next post.

Then run "chkdsk /f" again and repeat the above procedure, but replace  each "before" by "after". Post again and attach "after.mbr.tar.gz" 

If you want, you can  go ahead and install Ubuntu after you ran "chkdsk /f". There is even a very small chance that you will be able to boot Window 7 from the Grub menu, without having to run "bootsect /n60 SYS" again. 

 But most lilkely,  until we figure out what is going wrong, you  will have to run "/bootsect /n60 SYS again and you won't be able to access the Window 7 partition from Ubuntu. And you might have to add Ubuntu to the Window 7 boot loader, rather than being able to add Window 7 to the grub menu.


You might also try to run "bootrec /fixboot" in place of "bootsect /nt60 SYS".  Both are designed to fix the Windows boot sector, but are sligtly different.

---

### Post by wiz_master49 on 2010-01-01
Alright, I will edit my post as I complete the process and I will install Ubuntu using wubi for now. Hopefully the wubi version will work fine.

Edit1: before.mbr.tar.gz attached.
Edit2: after.mbr.tar.gz attached.

After doing chkdsk /f still got stuck at Verifying DMI Pool Data so I tried bootrec /fixboot this time and it seems to have worked as you said it would so I am able to reboot into Windows 7/Ubuntu successfully.

---

### Post by meierfra. on 2010-01-01
The two files differ by just a little bit, but don't think that  that difference is causing your problems. I'll do some research.
 

> I will install  Ubuntu using wubi for now. Hopefully the wubi version will work fine.

I actually think a regular Ubuntu install is more likely to succeed (since Ubuntu and Windows will be independent from each other). But you can give it a try.


> so I tried bootrec /fixboot this time and it seems to have worked 

Are you able to access the Windows partition from Ubuntu after you ran "bootrec /fixboot"?   (Does "sudo mount /dev/sda1 /mnt" in an Ubuntu terminal produce an error message?)

---

### Post by wiz_master49 on 2010-01-01
> **meierfra. said:**
> The two files differ by just a little bit, but don't think that  that difference is causing your problems. I'll do some research.
 


I actually think a regular Ubuntu install is more likely to succeed (since Ubuntu and Windows will be independent from each other). But you can give it a try.




Are you able to access the Windows partition from Ubuntu after you ran "bootrec /fixboot"?   (Does "sudo mount /dev/sda1 /mnt" in an Ubuntu terminal produce an error message?)

I installed Ubuntu using wubi but I installed it on my free 100gb partition apart from my Windows installation. No it still didn't see my Windows partition but I didn' try that command, if you want me to I can though.

---

### Post by Sef on 2010-01-01
Please wait until 24 has passed before bumping your thread.  Thank you.

---

### Post by meierfra. on 2010-01-01
Running "chldsk /f" wrote zero's to 96 bytes of the /dev/sda1 boot sector (Ox1e00-Ox1e5f).  I have not been able to figure out what the significants of those bytes are. My Win 7 boot sector has very similar bytes in that place as yours. Then I run "/chkdsk /f"  it does not erase those bytes. Erasing them manually does not make any difference to my system.  Googeling  didn't yield any results.

If you are not sick of experimenting, I would like to determine whether changing whose 96 bytes has  any effect on your system. I attached two scripts

Make_Windows_Bootable.txt and Make_Windows_Accessible.txt. 

Boot from the Ubuntu Live CD, and download them to your Desktop.

Then run "Make_Windows_Accessible.txt" via

```

sudo bash ~/Desktop/Make_Windows_Accessible.txt
```

See whether you are now able to access your Windows partition from the LiveCD.  You might have to reboot to see the effects. Also  check whether you are able to boot into Windows.

To undo the effect of the first script run the second script via

```
sudo bash ~/Desktop/Make_Windows_Bootable.txt
```

---

### Post by wiz_master49 on 2010-01-01
I did the first script, checked and still no visible Windows partition. Rebooted, booted into Windows no problem at all. Rebooted back into Ubuntu still no Windows partition, but I checked Gparted again and it is giving a different error this time, albeit still an error and it seems to mean about the same. [http://i46.tinypic.com/2hzmsjm.png](http://i46.tinypic.com/2hzmsjm.png)

---

### Post by oldfred on 2010-01-01
Your Vista partition is starting at 63 and it should be 2048. Meierfia knows a whole lot more than I and may have a better way to fix this.

Some site said the BCD has to be rebuilt.

I suggested a bunch of windows commands to one user and he said it worked. I do not know if it just made Vista work with sector 63 or moved it back to 2048.
[http://ubuntuforums.org/showthread.php?t=1369161](http://ubuntuforums.org/showthread.php?t=1369161)
You will need to boot with your Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr 
BootRec.exe /FixBoot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by wiz_master49 on 2010-01-01
Ok, ran those commands:
[http://i46.tinypic.com/10gbm2f.jpg](http://i46.tinypic.com/10gbm2f.jpg)
Didn't work.

---

### Post by meierfra. on 2010-01-02
I'm at a loss. But I'll make one last attempt to figure out what is going on.


Boot into Ubuntu

```

sudo dd if=/dev/sda of=sda_before.mbr count=63
sudo tar -czvf sda_before.mbr.tar.gz sda_before.mbr

```
(Be very careful with the "dd" command, if it runs for more one just a few seconds, stop the process with "ctrl c")
This created the file "sda_before.mbr.tar.gz" in the home directory. Attach it to your next post.

Boot into Windows and click on Start. Type "cmd" and "press "CTRL+SHIFT+ENTER". This will open the Window 7 command line with administrator rights.

Type

```
chkdsk /r > C:\chkdsk_log.txt
```
and agree to run "chkdsk" after reboot.
Reboot. Chkdsk should run. After chkdsk, see whether you can boot into Windows (very unlikely).   Then  boot  into Ubuntu or  Ubuntu Live CD. 

As above run "dd" but replace  each "before" by "after". Post again and attach "sda_after.mbr.tar.gz" 

If necessary run "bootrec /fixboot"from the Windows 7 DVD  to be able to boot into Windows. Post the file "C:\chkdsk_log.txt"

---

### Post by wiz_master49 on 2010-01-02
Ok, finally got done with everything. I need to explain something though. The log you requested didn't log the actual chkdsk event but I did find out that Windows logged in for me and found that log using Event Viewer as you will see [here](http://i48.tinypic.com/2njk5ub.jpg).

Also, attaching the other files as requested. The 2nd chkdsk log is the actual log.

---

### Post by wiz_master49 on 2010-01-03
Bump

---

### Post by meierfra. on 2010-01-03
I might have found the cause of your problem:


> TestDisk 6.11, Data Recovery Utility, April 2009
...
sectors_per_cluster       8 8
mft_lcn                   5166768 5166768
mftmirr_lcn               1 1


This says your MFT Mirror (the  backup of the Master file table) is located at cluster 1.   There are 8 sector  per cluster.  So the MFT Mirror is located at sector 8 of /dev/sda1.  Windows 7 uses the first 9 sector of the hard drive for boot information.

So if you run "chkdsk", it fixes the MFT Mirror:

> (From your chkdsk log: )  The MFT mirror is different from the MFT.
Correcting errors in the Master File Table (MFT) mirror.

and overwrites some of the boot information.  And if you run "bootrec /fixboot"  it overwrites the MFT mirror. It seems that Ubuntu checks on the MFT mirror and refuses to mount the Windows partition.

To fix it, you would have to changed the location of the MFT Mirror.

So far, so good. But this theory does not match the "after.mbr" file you posted above: It should contain the MFT mirror, but it does not. (Did you run "bootsect /nt60 SYS"  in between "chkdsk" and producing the "after.mbr" file?)

Also I don't know any good way to change the location of the MFT Mirror.
Seems I have to do some more research.

---

### Post by wiz_master49 on 2010-01-03
> **meierfra. said:**
> I might have found the cause of your problem:




This says your MFT Mirror (the  backup of the Master file table) is located at cluster 1.   There are 8 sector  per cluster.  So the MFT Mirror is located at sector 8 of /dev/sda1.  Windows 7 uses the first 9 sector of the hard drive for boot information.

So if you run "chkdsk", it fixes the MFT Mirror:



and overwrites some of the boot information.  And if you run "bootrec /fixboot"  it overwrites the MFT mirror. It seems that Ubuntu checks on the MFT mirror and refuses to mount the Windows partition.

To fix it, you would have to changed the location of the MFT Mirror.

So far, so good. But this theory does not match the "after.mbr" file you posted above: It should contain the MFT mirror, but it does not. (Did you run "bootsect /nt60 SYS"  in between "chkdsk" and producing the "after.mbr" file?)

Also I don't know any good way to change the location of the MFT Mirror.
Seems I have to do some more research.

I used bootrec /fixboot after the chkdsk, yes.
Also, I just want to thank you for sticking through the whole situation and trying to help me resolve this. Your help is much appreciated. :)

---

### Post by meierfra. on 2010-01-04
I searched the web for a way to move the MFT  Mirror, but did not find anything. So I developed my own method and moved the MFT Mirror of my Virtual Windows 7 to the first cluster. After that my system behaved exactly like yours: 

If I want to access Windows from Ubuntu, I have to run chkdsk.
 After that I cannot boot into Windows and have to run "bootsec".
Of course, then I'm no longer able to access Windows from Ubuntu.

I was able to restore my system back to normal by moving  the  MFT Mirror back and  running chdsk and bootsect.

So I'm pretty sure that one can fix your system in the same way. But I not sure  whether I can recommend  my method. It involves editing the MFT. I wrote a script which will do that for you.  But since I'm the only person who ever  tried it, there is some chance that it will seriously mess up your file system.  

If you can back up all you important data, and don't mind reinstalling Window 7 if you have to, let me know and I will show you how to move the MFT Mirror.

Your only other options are:

1) Find some other program which moves the MFT Mirror for you, but no such program will be risk free.

2) Reinstall Windows 7.

3) Leave it as is. But that is also risky since you currently do not have an MFT Mirror. So if your MFT gets corrupted, chkdsk will have a tough time repairing it.

---

### Post by wiz_master49 on 2010-01-04
I have a 1TB external hard drive I use to back up to so I don't mind reinstalling Windows 7. Go ahead and post your method and I will give it a try.

---

### Post by meierfra. on 2010-01-05
Small roadblock: To move the MFT mirror, one has to find a place on the Windows partition which is not used by the file system.  This can be done by reading the MFT,  but I have never done that.  So it might take me a couple of days  to sort out the details.

---

### Post by meierfra. on 2010-01-09
O.k, I finish writing the program  to move the MFT mirror.

Before I give you instruction  how to use it, let me explain what the program does:

Step 1)  It  searches  your windows partition for an empty and unused space big enough to fit the MFT_Mirror.

Step2) It replaces the location of the MFT_Mirror, as it is recorded in  the boot sector and in the MFT, by the location found in Step 1.

After you run my program you will have to run chkdsk. chkdsk will copy the first four records  of the  MFT to the new location of the MFT_Mirror.


Anyway, boot into Ubuntu and  download the attached file "move_mft_mirror.txt" to  your desktop. Open a terminal and run

```
sudo bash ~/Desktop/move_mft_mirror.txt /dev/sda1 
```

Searching for the empty spot on your partition might take quite a while. I tried it on seven different partitions. For some of them it finished in a few seconds, for  others it  took a couple of minutes. It  just depends where the  first empty spot is located.

Once the program is done, run "chkdsk /f" a few times, until it returns no more errors.

---

### Post by wiz_master49 on 2010-01-13
Sorry for the delayed response, been busy, but I finally got around to trying this and am sad to say it didn't work for me. I did exactly as you said but after I tried rebooting I was still stuck at verifying dmi pool data.

---

### Post by meierfra. on 2010-01-13
Any problems while running my program?

Are you able to boot into Windows after "bootsec"

Still not able to access Windows from Wubi?

I would like to know whether the MFT_Mirror was actually moved:

Could you do Step 1 from post 11 again (running testdisk and post  the rebuildBS screen). No need to use the Live CD, just do it from Wubi.

---

### Post by wiz_master49 on 2010-01-15
> **meierfra. said:**
> Any problems while running my program?
No
> **meierfra. said:**
> Are you able to boot into Windows after "bootsec"
Yes, after.

> **meierfra. said:**
> Still not able to access Windows from Wubi?
Actually I can mount the drive fine now and Gparted reports the partition correctly.

> **meierfra. said:**
> I would like to know whether the MFT_Mirror was actually moved:

Could you do Step 1 from post 11 again (running testdisk and post  the rebuildBS screen). No need to use the Live CD, just do it from Wubi.
```
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1 17000 254 63  273121002 [DRV1_VOL1]

filesystem size           273121002 273121001
sectors_per_cluster       8 8
mft_lcn                   5166768 5166768
mftmirr_lcn               199920 199920
clusters_per_mft_record   -10 -10
clusters_per_index_record 1 1
Extrapolated boot sector and current boot sector are different.
```

Just for the heck of it I also ran the bootinfo script also:
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdg
 => Windows is installed in the MBR of /dev/sdh
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda5/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

sdg1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbd91f9e7

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   273,121,064   273,121,002   7 HPFS/NTFS
/dev/sda2         273,121,547   488,392,001   215,270,455   f W95 Ext d (LBA)
/dev/sda5         273,121,610   488,392,001   215,270,392   7 HPFS/NTFS


Drive: sdg ___________________ _____________________________________________________

Disk /dev/sdg: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8900690

Partition  Boot         Start           End          Size  Id System

/dev/sdg1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 2017 MB, 2017459712 bytes
4 heads, 32 sectors/track, 30783 cylinders, total 3940351 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd3486dc6

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             32     3,940,350     3,940,319   e W95 FAT16 (LBA)


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: UUID="79208d6a-dfdf-4940-824f-3f7ecb9dfb54" TYPE="ext4" 
/dev/sda1: UUID="01CA884544737A20" LABEL="DRV1_VOL1" TYPE="ntfs" 
/dev/sda5: UUID="2C90738790735674" LABEL="DRV1_VOL2" TYPE="ntfs" 
/dev/sdg1: UUID="9AA6E9A8A6E9855B" LABEL="My Book" TYPE="ntfs" 
/dev/sdh1: SEC_TYPE="msdos" LABEL="CRUZER MINI" UUID="2D97-00A9" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/loop0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /host type fuseblk (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/miguel/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=miguel)
/dev/sdh1 on /media/CRUZER MINI type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=miguel)
/dev/sdg1 on /media/My Book type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sda1 on /media/DRV1_VOL1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


======================== sda5/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
	insmod ntfs
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 2c90738790735674
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro   quiet splash
	initrd /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
	insmod ntfs
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 2c90738790735674
	loopback loop0 /ubuntu/disks/root.disk
	set root=(loop0)
	linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda5 loop=/ubuntu/disks/root.disk ro single 
	initrd /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda5/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================= sda5/Wubi: Location of files loaded by Grub: =================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  22 3f 3a 3c 00 3d 4f 05  00 00 55 15 c9 8a 4b 4c  |"?:<.=O...U...KL|
00000010  93 22 9f 3d 3d 00 25 13  29 91 55 23 fc 62 22 2d  |.".==.%.).U#.b"-|
00000020  65 25 23 5d b1 1b 25 1f  ac 17 00 09 8d 6c 08 23  |e%#]..%......l.#|
00000030  a4 a9 22 5d b2 52 44 02  22 dd ab 1c 23 7f ac 1b  |.."].RD."...#...|
00000040  00 1d 54 f8 22 1d aa 53  13 e9 8b 1c 5c 46 22 1d  |..T."..S....\F".|
00000050  4b 1b 54 04 7d 47 3f 44  74 22 0c 40 01 0a 00 1b  |K.T.}G?Dt".@....|
00000060  00 73 f2 3f 00 0a 9f 00  0e 00 10 9d 06 40 5c 02  |.s.?.........@\.|
00000070  22 bf 55 44 00 10 44 01  12 29 82 0f 23 ed 5d 0f  |".UD..D..)..#.].|
00000080  54 04 7c 02 01 0e 00 0f  00 7d 00 0f 54 1a 7d 07  |T.|......}..T.}.|
00000090  02 5c 67 7d 22 02 5c 3f  22 2e 54 4c 00 22 35 be  |.\g}".\?".TL."5.|
000000a0  00 55 19 02 13 28 93 22  4c 3f 22 dc 33 22 4c 44  |.U...(."L?".3"LD|
000000b0  6d 01 0e 23 e4 b2 7d 1a  0e 47 1d 00 00 25 44 05  |m..#..}..G...%D.|
000000c0  22 fc 41 22 54 b3 22 5c  42 01 4a 00 24 00 7c 05  |".A"T."\B.J.$.|.|
000000d0  01 06 00 01 00 22 9c 3e  24 bd 63 00 55 0a 01 23  |.....".>$.c.U..#|
000000e0  4d 66 06 54 02 22 be 3e  56 00 65 8e 00 55 4a 1e  |Mf.T.".>V.e..UJ.|
000000f0  44 45 22 dc b4 24 9c 53  6c 06 22 df 4b 56 00 1e  |DE"..$.Sl.".KV..|
00000100  9d 4f 0e 54 21 6d 0f 43  15 ab 87 24 00 0e 13 ab  |.O.T!m.C...$....|
00000110  86 44 00 31 9d 00 2f 1b  e1 96 00 55 47 43 13 69  |.D.1../....UGC.i|
00000120  88 2f 5c 02 7d 25 1d 5c  00 22 9d 46 61 55 0b 4d  |./\.}%.\.".FaU.M|
00000130  23 fd b0 00 13 0b 87 1f  00 41 1b b0 8d 61 ae 42  |#........A...a.B|
00000140  5d 41 4d 5c 01 22 7c 47  6c eb 7f 00 4d 00 43 44  |]AM\."|Gl...M.CD|
00000150  4e 7e 09 0c 00 7f 01 61  00 4d 9c 01 6c 26 a4 16  |N~.....a.M..l&..|
00000160  64 d5 ae 00 56 ce 38 5c  af 6c a8 74 04 6c 79 7c  |d...V.8\.l.t.ly||
00000170  00 22 2d 4e c8 5c 9f fc  00 6c bf 7c c8 7c c0 09  |."-N.\...l.|.|..|
00000180  f4 6c ea 40 ce 08 80 41  d1 22 5b bd 7c db 7c cf  |.l.@...A."[.|.|.|
00000190  7c d3 01 e8 d9 0f c1 22  2c 2b 22 2c 29 22 ac 2f  ||......",+",)"./|
000001a0  22 dc 29 22 ac 2f 0d 6a  4d 03 c1 ba 49 a6 40 9a  |".)"./.jM...I.@.|
000001b0  19 88 41 4d f3 f6 3f 6c  dc 7c d5 6c e7 22 00 fe  |..AM..?l.|.l."..|
000001c0  ff ff 07 fe ff ff 3f 00  00 00 f8 c3 d4 0c 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdh1

00000000  eb 3c 90 44 4f 4b 30 31  2e 30 32 00 02 40 01 00  |.<.DOK01.02..@..|
00000010  02 00 02 00 00 f8 f1 00  20 00 04 00 20 00 00 00  |........ ... ...|
00000020  df 1f 3c 00 80 00 29 a9  00 97 2d 00 00 00 00 00  |..<...)...-.....|
00000030  00 00 00 00 00 00 46 41  54 31 36 20 20 20 33 c9  |......FAT16   3.|
00000040  8e d1 bc fc 7b 16 07 bd  78 00 c5 76 00 1e 56 16  |....{...x..v..V.|
00000050  55 bf 22 05 89 7e 00 89  4e 02 b1 0b fc f3 a4 06  |U."..~..N.......|
00000060  1f bd 00 7c c6 45 fe 0f  38 4e 24 7d 20 8b c1 99  |...|.E..8N$} ...|
00000070  e8 7e 01 83 eb 3a 66 a1  1c 7c 66 3b 07 8a 57 fc  |.~...:f..|f;..W.|
00000080  75 06 80 ca 02 88 56 02  80 c3 10 73 ed 33 c9 fe  |u.....V....s.3..|
00000090  06 d8 7d 8a 46 10 98 f7  66 16 03 46 1c 13 56 1e  |..}.F...f..F..V.|
000000a0  03 46 0e 13 d1 8b 76 11  60 89 46 fc 89 56 fe b8  |.F....v.`.F..V..|
000000b0  20 00 f7 e6 8b 5e 0b 03  c3 48 f7 f3 01 46 fc 11  | ....^...H...F..|
000000c0  4e fe 61 bf 00 07 e8 28  01 72 3e 38 2d 74 17 60  |N.a....(.r>8-t.`|
000000d0  b1 0b be d8 7d f3 a6 61  74 3d 4e 74 09 83 c7 20  |....}..at=Nt... |
000000e0  3b fb 72 e7 eb dd fe 0e  d8 7d 7b a7 be 7f 7d ac  |;.r......}{...}.|
000000f0  98 03 f0 ac 98 40 74 0c  48 74 13 b4 0e bb 07 00  |.....@t.Ht......|
00000100  cd 10 eb ef be 82 7d eb  e6 be 80 7d eb e1 cd 16  |......}....}....|
00000110  5e 1f 66 8f 04 cd 19 be  81 7d 8b 7d 1a 8d 45 fe  |^.f......}.}..E.|
00000120  8a 4e 0d f7 e1 03 46 fc  13 56 fe b1 04 e8 c2 00  |.N....F..V......|
00000130  72 d7 ea 00 02 70 00 52  50 06 53 6a 01 6a 10 91  |r....p.RP.Sj.j..|
00000140  8b 46 18 a2 26 05 96 92  33 d2 f7 f6 91 f7 f6 42  |.F..&...3......B|
00000150  87 ca f7 76 1a 8a f2 8a  e8 c0 cc 02 0a cc b8 01  |...v............|
00000160  02 80 7e 02 0e 75 04 b4  42 8b f4 8a 56 24 cd 13  |..~..u..B...V$..|
00000170  61 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |aar.@u.B.^.Iuw..|
00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|
00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |
000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|
000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|
000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|
000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |
000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|
000001f0  00 41 bb 00 07 60 66 6a  00 e9 3b ff 00 00 55 aa  |.A...`fj..;...U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde sdf 
```

It seems the problem now is that every time I reboot my computer I get stuck at Verifying DMI Pool Data, so every time I have to boot into the Windows cd and do one of the 2 commands to fix the mbr. I guess this is a problem with my hard drive/partitions now instead of Ubuntu so I guess I should mark this thread solved.

---

### Post by meierfra. on 2010-01-16
> I guess this is a problem with my hard drive/partitions 

Yes, I'm pretty sure your problem has nothing to do with Ubuntu. But I'm intrigued by your case, and so if you don't mind I would like to  keep working on it.

Here is my current theory:  Moving the MFT_Mirror only  treated  the  symptoms but not the real cause of the problem. 
Your boot sector is a little bit longer than 1 cluster (=8 sectors=  4096bytes). So the MFT (Master File Table) should have reserved the first 2 clusters for the boot sector. But for some reason it only reserved  the first cluster and the   MFT_Mirror was written to the  second cluster.   This caused the problems of "bootsect" overwriting the MFT_Mirror (making Windows inaccessible for Ubuntu) and "chkdisk" overwriting the boot sector (making Windows unbootable).

My program moved the MFT_Mirror and you are now able to access Windows from Ubuntu. But moving the MFT_Mirror declared the second  cluster to  be free space  and some Windows program is using it now. So everytime you boot into Windows, the second cluster gets  used and your boot sector gets destroyed.

If I would have realized this earlier, it would have been easy to modify my program  and avoid  your new  problem.  But I'm not sure how to fix it, now that some unknown Windows program claimed that second cluster.

I'll think about it. In  the mean time,  I would like you to check whether  the MFT really only reserved one cluster for your boot sector:

Boot into Wubi, download the attached script "mft_file.txt" and run it via

```
sudo bash mft_file.txt /dev/sda1 7
```
The boot sector is the 7th file in the MFT. This will determine the size and location of your boot sector. The output should be 

run 1 of file 7 starts at Cluster 0 and has  2 Clusters.

But if my theory is correct it will say:

run 1 of file 7 starts at Cluster 0 and has  1 Clusters.

---

### Post by oldfred on 2010-01-16
Is thsi computer a Dell or HP with any of these issues?

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. Thanks for the links!

---

### Post by wiz_master49 on 2010-01-16
> **meierfra. said:**
> Yes, I'm pretty sure your problem has nothing to do with Ubuntu. But I'm intrigued by your case, and so if you don't mind I would like to  keep working on it.

Here is my current theory:  Moving the MFT_Mirror only  treated  the  symptoms but not the real cause of the problem. 
Your boot sector is a little bit longer than 1 cluster (=8 sectors=  4096bytes). So the MFT (Master File Table) should have reserved the first 2 clusters for the boot sector. But for some reason it only reserved  the first cluster and the   MFT_Mirror was written to the  second cluster.   This caused the problems of "bootsect" overwriting the MFT_Mirror (making Windows inaccessible for Ubuntu) and "chkdisk" overwriting the boot sector (making Windows unbootable).

My program moved the MFT_Mirror and you are now able to access Windows from Ubuntu. But moving the MFT_Mirror declared the second  cluster to  be free space  and some Windows program is using it now. So everytime you boot into Windows, the second cluster gets  used and your boot sector gets destroyed.

If I would have realized this earlier, it would have been easy to modify my program  and avoid  your new  problem.  But I'm not sure how to fix it, now that some unknown Windows program claimed that second cluster.

I'll think about it. In  the mean time,  I would like you to check whether  the MFT really only reserved one cluster for your boot sector:

Boot into Wubi, download the attached script "mft_file.txt" and run it via

```
sudo bash mft_file.txt /dev/sda1 7
```
The boot sector is the 7th file in the MFT. This will determine the size and location of your boot sector. The output should be 

run 1 of file 7 starts at Cluster 0 and has  2 Clusters.

But if my theory is correct it will say:

run 1 of file 7 starts at Cluster 0 and has  1 Clusters.

```
run 1 of file 7 starts at Cluster 0 and has  1 Clusters.
```
You are correct

> **oldfred said:**
> Is thsi computer a Dell or HP with any of these issues?

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
[http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!
Another windows issue that caused grub2 issues.
Looks like I found the culprit. It was Norton Ghost running in the background, that I had just recently installed. I disabled it during startup through msconfig and no more trouble. Thanks for the links!

It is custom built by me and my dad but it does seem to be a Windows program causing this because it only gets stuck after I have booted into Windows. It restarts fine if I just came from Ubuntu.

---

### Post by meierfra. on 2010-01-17
> run 1 of file 7 starts at Cluster 0 and has [COLOR="Red"] 1 Cluster[/COLOR]s.
OK. That does seem to be the cause of all your problem.

I have been unable to find  a  way to change that number in the MFT.  I can change it manually, but every time I run "chkdsk" it reverts to the orginal size.  I tried more aggressive methods and now I'm  no longer able to boot my  Virtual Window 7 (which is o.k, since I only use it for testing purposes)

I could try a little bit longer,  but I don't have much hope. So at this stage I recommend to reinstall Window 7.  If you want to install Ubuntu afterward, I suggest to create the partitions before hand, so you won't have   to resize Window 7. I have the feeling that your problem was  created by resizing the partitions  with Partition Wizard Home Edition, but resizing can always go wrong. So it's best to avoid it.

Sorry that I wasn't able to provide better help.

---

### Post by wiz_master49 on 2010-01-17
> **meierfra. said:**
> OK. That does seem to be the cause of all your problem.

I have been unable to find  a  way to change that number in the MFT.  I can change it manually, but every time I run "chkdsk" it reverts to the orginal size.  I tried more aggressive methods and now I'm  no longer able to boot my  Virtual Window 7 (which is o.k, since I only use it for testing purposes)

I could try a little bit longer,  but I don't have much hope. So at this stage I recommend to reinstall Window 7.  If you want to install Ubuntu afterward, I suggest to create the partitions before hand, so you won't have   to resize Window 7. I have the feeling that your problem was  created by resizing the partitions  with Partition Wizard Home Edition, but resizing can always go wrong. So it's best to avoid it.

Sorry that I wasn't able to provide better help.

It is completely up to you, I am just happy you were willing to help me solve this problem. I am fine with reformatting. If you want to attempt anything further that is also fine. Either way post back here stating whether you want to keep trying or if your are done so I know whether I should mark the thread solved or not. Either way, I really do thank you for all your help. I really appreciate it.

---

### Post by meierfra. on 2010-01-18
I still have no clue how the fix the "1 Cluster" problem. But you might be able to work  around it, by using  a boot loader which does not use the boot sector.  So I suggest to give Grub4Dos a try.

Boot into Windows 7 and download this zip file:

[https://sourceforge.net/projects/grub4dos/files/grubinst/grubinst%201.0.1/grubinst_1.0.1_bin_win.zip/download](https://sourceforge.net/projects/grub4dos/files/grubinst/grubinst%201.0.1/grubinst_1.0.1_bin_win.zip/download)

Unzip it and place the resulting folder  "grubinst"  into "C:\".

Copy the file "grldr"  in "C:\grubinst" to "C:\"

Click on "Start", type "cmd" and press "Ctrl+Shift+Enter". This will open the Windows 7 command line with administrator rights.
Type

```
C:\grubinst\grubinst.exe (hd0)
```

(This command  did install the Grub4Dos boot code to the MBR)

Create a file called "menu.lst"   containing  the following two  lines:


```
title Windows 7
chainloader (hd0,0)/bootmgr
```

Save the file and place it in "C:".

Reboot and you should get the Grub4Dos boot menu.  Choosing "Window 7" should  give you the  "Window 7" boot menu, which  lets you choose between "Window 7" and "Wubi".  

You can also hide the Grub4Dos menu so that  you don't have to go though  two boot menus, but we'll worry about that later.


If things go wrong, and you can't boot into Window 7, use "bootrect /fixmbr"  to  remove the Grub4Dos code from the MBR.

---

### Post by meierfra. on 2010-01-18
I fixed a typo in my last post. (it has to be (hd0,0)/bootmgr, not (hd0,0)\bootmgr)

---

### Post by wiz_master49 on 2010-01-20
I tried what you posted but I think I might have done it wrong;
[http://i50.tinypic.com/2yxln4w.jpg](http://i50.tinypic.com/2yxln4w.jpg)
[http://i48.tinypic.com/jtvx54.jpg](http://i48.tinypic.com/jtvx54.jpg)
I couldn't fit the whole screen while still being readable in one photo so the first is the left half and the second is the right half.

After it showed that I booted into Windows disc and did bootrec /fixboot, restarted it displayed it again but I was able to hit any key like it said and it booted into Windows fine. I went into the root of C:\ and deleted the bootloader manually. I hope that you can just delete it to uninstall correct? I will retry again and soon and make another post.

---

### Post by meierfra. on 2010-01-20
The grub4dos in the MBR is trying to find "grldr" and fails. 
It seems that grub4dos does not like  the boot sector of your Windows partition and so does  not even look for "grldr" on the Windows partition.
No idea whether this can be fixed, but I'll think about it. 

Deleting the Grub4dos files won't make any difference, you need to  restore your MBR:

```
bootrec /fixmbr
```

---

### Post by meierfra. on 2010-01-21
I think I figured out what was causing your problem with Grub4Dos.  I had told you to download the "grubinst" version, since that  is the easiest way to install Grub4Dos to the MBR. But  I hadn't realized that "grubinst" is over 3 years old and has its problems.  So lets try again. This time you have to install Grub4Dos from Wubi.

Boot into Wubi and download this zip file 

[http://sourceforge.net/projects/grub4dos/files/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip/download](http://sourceforge.net/projects/grub4dos/files/GRUB4DOS/grub4dos%200.4.4/grub4dos-0.4.4.zip/download)

to your desktop. Extract the file, so that you have the folder "grub4dos-0.4.4" on your desktop.

Open a terminal and

```
cd ~/Desktop/grub4dos-0.4.4
sudo mount /dev/sda1 /mnt
sudo cp grldr /mnt
sudo dd if=grldr.mbr of=/dev/sda bs=1 count=440
sudo dd if=grldr.mbr of=/dev/sda seek=1 skip=1 

```

(Be very careful with the "dd" commands. If they run for more one just a couple of second, kill the process with "Ctrl+c". )

In case  you deleted the file menu.lst, you will have to create it again. It needs to be at  C:\menu.lst, just as before.

---

### Post by wiz_master49 on 2010-01-30
Sorry it took so long, busy with college. I got around to doing what your last post stated and it seems to be working. I booted into Ubuntu, followed your directions, booted into Windows just fine using the bootloader that was installed, once Windows loaded I restarted to see if it would create the verifying "error." It did not, it booted like it was supposed to do so for now it seems to have worked. Is their anything else you want me to try maybe to get some info or something?

---

### Post by meierfra. on 2010-01-30
> it seems to be working. 
Great.  

To avoid having to go through two boot menus, change  the file C:\menu.lst to


```
default 0
timeout 0

title Windows 7
chainloader (hd0,0)/bootmgr
```


> Is their anything else you want me to try maybe to get some info or something? 

No.  I already learned a lot from working on this case. Thanks for being so patient.

---

### Post by wiz_master49 on 2010-01-30
Done. Thanks for sticking with me through this whole problem. Marking as solved.

---

