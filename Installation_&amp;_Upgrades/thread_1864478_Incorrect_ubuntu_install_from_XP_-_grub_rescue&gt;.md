---
title: "Incorrect ubuntu install from XP - grub rescue&gt;"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by HawkeyeJ on 2011-10-19
Hello all (Noob in it deep, here),

I installed ubuntu 10.10 from a CD in Windows XP SP3 on a Dell latitude E6500 laptop. From the install CD I downloaded, I chose the setup alongside Windows option and in my infinite and absent-minded **noob** wisdom, didn't think to set up a partition on my disk, just assumed that by using the recommended partition size it offered, it would present some type of partition menu at some point or just partition the disk using that recommended size.

So basically, I installed ubuntu 10.10 in the same partition as XP, and now cannot access either OS. When trying to unlock my hard drive with my username and password, I'm presented with a message "error: no such partition. grub rescue>".

I've tried some suggestions from other threads, such as booting from XP's install cd, pressing 'r' for repair, then when presented with the C:\> command line, typing fixboot, then fixmbr. However, this doesn't work; I get a message "the new master boot record could not be written".

I'd just like to run XP again and remove ubuntu, getting my machine working as it was before I wrecked the place up. I'll try re-installing ubuntu later AFTER setting up a partition for Ubuntu - and using a proper tutorial, of course :).

PLEASE help a noob out! I've really hosed my laptop up over here! :confused:

---

### Post by garvinrick4 on 2011-10-19
Use your XP disk and reinstall. It will overwrite Ubuntu and put windows boot loader back in place.
When you install ubuntu after Windows just choose to install side by side and will split the hard drive
and have both Operating systems and have a boot menu with choose of either. Will do it all for you so
is quite easy.

---

### Post by HawkeyeJ on 2011-10-19
Wow, that was fast! Thanks for the quick reply.

Is there a way for me to recover XP without having to re-install? I have a lot of programs and projects set up in Windows, and it would be a real hassle to have to re-install and set up *everything* again. I suppose that's the last ditch solution, though...

On the second note, my having chosen the install side by side option is what caused my issue. Like I said, I didn't partition my disc prior, I assumed what you had said garvinrick, that it would split the hard drive and set up both next to each other, then present a menu for which to boot. What could have gone wrong here if I don't need to split the disc before install?

Thanks again for the help, it is appreciated!

---

### Post by garvinrick4 on 2011-10-19
If you want to know all about what is going on with your drive and what is there and not there and why
no boot do this below and post results. 
Put in install cd and boot off of and  choose Try Ubuntu  and when boots download the bootscript from link
below to DESKTOP. Right click on and choose to extract with Archive Manager.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 

Then run this line of code in terminal. [ctrl/alt/t]  (copy and paste it in to terminal hit enter)
```
sudo bash ~/Desktop/boot_info_script.sh
```Will make a RESULTS.txt file on Desktop open and copy and paste in a Message box and highlight
whole thing (is Long) and hit # in upper right of message box and will put in nice little box to read from.

Now we can see what went wrong and what is on your Hard Disk.

---

### Post by HawkeyeJ on 2011-10-19
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 134 MB, 134217728 bytes
255 heads, 63 sectors/track, 16 cylinders, total 262144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *              1    16,450,550    16,450,550  7d Unknown
/dev/sda2     ?    33,686,018    67,372,035    33,686,018   2 XENIX root
/dev/sda3     ?    50,529,027   101,058,053    50,529,027   3 XENIX /usr
/dev/sda4     ?    67,372,036   134,744,071    67,372,036   4 FAT16 <32M

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda2 overlaps with /dev/sda3
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda3 overlaps with /dev/sda4
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8036 MB, 8036285952 bytes
255 heads, 63 sectors/track, 977 cylinders, total 15695871 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  44    15,679,439    15,679,396   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sdb1        9805-A9CF                              vfat       Cruzer

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Cruzer            vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda

00000000  e9 6c 00 00 00 00 00 00  00 00 00 00 02 00 01 00  |.l..............|
00000010  00 00 00 40 0b f8 00 00  3f 00 10 00 00 00 00 00  |...@....?.......|
00000020  00 00 00 00 00 00 29 00  00 00 00 00 00 00 00 00  |......).........|
00000030  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000050  00 00 00 00 00 00 0d 0a  70 62 4d 42 52 20 76 30  |........pbMBR v0|
00000060  33 30 38 0d 0a 00 0d 0a  57 65 42 61 63 6b 00 fc  |308.....WeBack..|
00000070  33 c0 8e d8 8e d0 bc 00  70 66 68 22 22 11 11 66  |3.......pfh""..f|
00000080  50 66 53 66 51 66 52 66  56 66 57 66 68 44 44 33  |PfSfQfRfVfWfhDD3|
00000090  33 8b ec fb be 00 7c bf  00 00 b8 70 00 8e c0 06  |3.....|....p....|
000000a0  68 a9 00 b9 00 01 f3 a5  cb 0e 1f 88 16 24 00 b8  |h............$..|
000000b0  c0 07 8e c0 bb 00 00 66  b8 02 00 00 00 8a 16 24  |.......f.......$|
000000c0  00 b9 7e 00 e8 6e 00 9a  00 7c 00 00 0e 1f 8a 16  |..~..n...|......|
000000d0  24 00 80 ca 80 eb 13 b8  00 09 cd 13 73 0c 80 f2  |$...........s...|
000000e0  01 b8 00 09 cd 13 73 02  cd 19 88 16 24 00 66 b8  |......s.....$.f.|
000000f0  00 00 00 00 8e c0 bb 00  7c 8a 16 24 00 e8 0b 00  |........|..$....|
00000100  b6 00 8a 16 24 00 ea 00  7c 00 00 60 53 52 66 50  |....$...|..`SRfP|
00000110  58 5a f7 36 18 00 8a ca  41 33 d2 f7 36 1a 00 8a  |XZ.6....A3..6...|
00000120  e8 c0 e4 06 0a cc 8a f2  5b 8a d3 5b b8 01 02 cd  |........[..[....|
00000130  13 61 72 14 c3 06 e8 d2  ff 66 40 53 8c c3 83 c3  |.ar......f@S....|
00000140  20 8e c3 5b e2 f0 07 c3  8d 36 9f 01 e8 04 00 cd  | ..[.....6......|
00000150  19 eb f5 60 bb 07 00 ac  0a c0 74 06 b4 0e cd 10  |...`......t.....|
00000160  eb f5 61 c3 86 e0 e8 06  00 86 e0 e8 01 00 c3 50  |..a............P|
00000170  c0 e8 04 e8 05 00 58 e8  01 00 c3 50 83 e0 0f 83  |......X....P....|
00000180  f8 0a 7c 03 83 c0 07 83  c0 30 e8 02 00 58 c3 60  |..|......0...X.`|
00000190  bb 07 00 b4 0e cd 10 61  c3 4e 6f 50 42 52 00 4d  |.......a.NoPBR.M|
000001a0  42 52 45 72 72 00 00 00  00 00 00 00 00 00 00 00  |BRErr...........|
000001b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001c0  03 00 7d fe 3f ff 01 00  00 00 f6 03 fb 00 02 02  |..}.?...........|
000001d0  02 02 02 02 02 02 02 02  02 02 02 02 02 02 03 03  |................|
000001e0  03 03 03 03 03 03 03 03  03 03 03 03 03 03 04 04  |................|
000001f0  04 04 04 04 04 04 04 04  04 04 04 04 04 04 55 aa  |..............U.|
00000200

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

---

### Post by garvinrick4 on 2011-10-19
Drive has nothing in it at all but some empty partitions.
Format drive NTFS and install Windows first can then install Ubuntu at your leisure. 
Most likely tried one to many fixes just reinstall xp to whole disk. Can do anything else later
will keep your thread subscribed so it you have more questions about installing Ubuntu will
answer you.

---

