---
title: "input/output error in11.4 installition!"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by senaps on 2011-05-25
hi...
when i try to install 11.4, i get this error:
[IMG]http://up.iranblog.com/images/glimkdlsgapee7txs3.jpg[/IMG]
and,when i was trying to make the partition's that i need for install,by accident i have removed D and F drive's of windows 7...
and i can not load windows 7.....but C where i have installed it,is still remain!!
how can i fix 7?
why i can't install ubunntu on my system?!

---

### Post by Hedgehog1 on 2011-05-26
OK - you really need some help.

We need to get a look at your PC to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

---

### Post by tommcd on 2011-05-26
Be sure to run the option to check the CD for defects when the computer boots. See this to get the option to check the CD for defects: [https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)
The errors you are getting can be due to a faulty CD (as it is telling you in the screen shot you posted).
If the CD passes the integrity check without any errors, then the CD is good.

---

### Post by senaps on 2011-05-26
> **Hedgehog1 said:**
> OK - you really need some help.

We need to get a look at your PC to get an idea what is going on.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

[IMG]http://img854.imageshack.us/img854/4563/codetags.png[/IMG]


***The Hedge***

:KS

here it is:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 204799 sectors, 
                       but according to the info from fdisk, it has 1984 
                       sectors.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 206848. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       204593151 sectors, but according to the info from 
                       fdisk, it has 204799 sectors.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda4 starts 
                       at sector 409602048. But according to the info from 
                       fdisk, sda4 starts at sector 204802046. According to 
                       the info in the boot sector, sda4 has 174079999 
                       sectors, but according to the info from fdisk, it has 
                       771969025 sectors.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 614402048. But according to the info from 
                       fdisk, sda5 starts at sector 204802048. According to 
                       the info in the boot sector, sda5 has 321406975 
                       sectors, but according to the info from fdisk, it has 
                       7811071 sectors.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       206,847       204,800  42 SFS
/dev/sda3             206,848   204,799,999   204,593,152  42 SFS
/dev/sda4         204,802,046   976,771,071   771,969,026   5 Extended
/dev/sda5         204,802,048   212,613,119     7,811,072  82 Linux swap / Solaris
/dev/sda6         212,615,168   224,331,775    11,716,608  83 Linux
/dev/sda7         224,333,824   976,771,071   752,437,248  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6E6C902D6C8FEE61                       ntfs       System Reserved
/dev/sda2        247878F27878C3D8                       ntfs       
/dev/sda3        867e5210-0264-4eaa-88d2-467ad510be7b   swap       
/dev/sda4        3E7F00387EFFE695                       ntfs       
/dev/sda5        86DAB857DAB844E9                       ntfs       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  ea 22 10 00 00 00 00 00  |FILE0...."......|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  02 00 86 87 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  b4 d9 df 8f b8 2f cb 01  b4 d9 df 8f b8 2f cb 01  |...../......./..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  b4 d9 df 8f b8 2f cb 01  |............./..|
000000c0  b4 d9 df 8f b8 2f cb 01  b4 d9 df 8f b8 2f cb 01  |...../......./..|
000000d0  b4 d9 df 8f b8 2f cb 01  00 40 00 00 00 00 00 00  |...../...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  3f 00 00 00 00 00 00 00  |........?.......|
00000120  40 00 00 00 00 00 00 00  00 00 04 00 00 00 00 00  |@...............|
00000130  00 00 04 00 00 00 00 00  00 00 04 00 00 00 00 00  |................|
00000140  21 40 55 21 00 01 50 90  b0 00 00 00 50 00 00 00  |!@U!..P.....P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  21 01 54 21 21 01 fe fd  |........!.T!!...|
00000190  00 00 01 00 00 00 86 87  ff ff ff ff 00 00 00 00  |................|
000001a0  00 00 04 00 00 00 00 00  21 40 55 21 00 01 50 90  |........!@U!..P.|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  21 01 54 21 21 01 fe fd  00 00 01 00 00 00 02 00  |!.T!!...........|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  1a 5b 1d 0a 00 00 00 00  |FILE0....[......|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  07 00 00 00 00 00 00 00  |................|
00000030  e1 5c 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |.\..........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  56 7e c2 77 08 30 cb 01  56 7e c2 77 08 30 cb 01  |V~.w.0..V~.w.0..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  56 7e c2 77 08 30 cb 01  |........V~.w.0..|
000000c0  56 7e c2 77 08 30 cb 01  56 7e c2 77 08 30 cb 01  |V~.w.0..V~.w.0..|
000000d0  56 7e c2 77 08 30 cb 01  00 00 80 08 00 00 00 00  |V~.w.0..........|
000000e0  00 00 80 08 00 00 00 00  06 00 00 00 00 00 00 00  |................|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  7f b0 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 08 0b 00 00 00 00  |@...............|
00000130  00 00 08 0b 00 00 00 00  00 00 08 0b 00 00 00 00  |................|
00000140  32 80 2f 00 00 0c 33 00  81 00 0e 7b 76 00 6c 8c  |2./...3....{v.l.|
00000150  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 06 00  |....P.....@.....|
00000160  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 70 00 00 00 00 00 00  |@........p......|
00000180  00 64 00 00 00 00 00 00  00 64 00 00 00 00 00 00  |.d.......d......|
00000190  31 01 ff ff 0b 31 06 ce  76 02 00 00 00 d0 6c 8c  |1....1..v.....l.|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
000001b0  ff ff ff ff 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 e1 5c  |...............\|
00000200
Unknown BootLoader on sda6


Unknown BootLoader on sda7



=============================== StdErr Messages: ===============================

hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda6: No such file or directory
hexdump: /dev/sda7: No such file or directory
hexdump: /dev/sda7: No such file or directory

```



can i have 7 back?!
can i install ubuntu?!
my hard drive is formated?!!
can i get the files back?

---

### Post by senaps on 2011-05-26
any body?

---

### Post by Hedgehog1 on 2011-05-26
There is a serious mismatch on the data from your disk.

Partitions sda5, sda6 and sda7 are presenting very differently:

```
sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda5 starts 
                       at sector 614402048. But according to the info from 
                       fdisk, sda5 starts at sector 204802048. According to 
                       the info in the boot sector, sda5 has 321406975 
                       sectors, but according to the info from fdisk, it has 
                       7811071 sectors.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda7: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
```

vs

```
/dev/sda5         204,802,048   212,613,119     7,811,072  82 Linux swap / Solaris
/dev/sda6         212,615,168   224,331,775    11,716,608  83 Linux
/dev/sda7         224,333,824   976,771,071   752,437,248  83 Linux
```

vs

```
/dev/sda3        867e5210-0264-4eaa-88d2-467ad510be7b   swap       
/dev/sda4        3E7F00387EFFE695                       ntfs       
/dev/sda5        86DAB857DAB844E9                       ntfs       New Volume
```

I need to ask the forums partition map expert to take a look at this.

In the meantime, when you boot from the LiveCD, are you able to copy data from your windows partition to an external Hard Drive? If so please back up your documents this way (if you have not already backed them up).

Please avoid writing to the hard disk; depending on what the solution is, writing to the Hard drive may make recovery more difficult or impossible.

***The Hedge***

:KS

---

### Post by srs5694 on 2011-05-26
Hedgehog1 asked me to take a look at this. What you've got is a disk with three "SFS" partitions, which is what fdisk calls Windows Logical Disk Manager (LDM; aka "dynamic disks") partitions, along with an extended partition and three Linux partitions. This is extremely unusual. I'm not an LDM expert, but when I see this sort of thing, there are usually *four* LDM/SFS partitions and nothing else on the disk. My hunch is that you got into this state by your accidental removal of the D: and F: partitions you mentioned in the first post.

My recommendation is:


[list=1]
[*]If necessary, obtain a spare/backup disk big enough to hold all your data. If you don't already have such a disk, buy one -- you should have one for backup purposes anyhow. (Alternatively, use a tape backup unit, a stack of recordable DVDs, or whatever.)
[*]Using Windows tools, back up your Windows partitions. I've used [DriveImage XML](http://www.runtime.org/driveimage-xml.htm) to back up and restore Windows in the past; however, it needs a specially-prepared recovery DVD, as described [here.](http://www.runtime.org/peb.htm) Backing up just your user data and planning to restore by re-installing Windows and then restoring your user data might work, too.
[*]If you need to recover data from your deleted D: and F: partitions, use [PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec) or some similar tool (there are Windows equivalents, but I don't know anything about them) to do so.
[*]Delete all your partitions.
[*]Create new partitions to restore Windows. Create no more than three such partitions using the Windows partitioning tool. If you want more than three Windows partitions, use a third-party partitioner or a Linux partitioner and create some of them as logical partitions. The key here is to be sure you do ***not*** create another LDM/"dynamic disk" configuration, which is what the Windows tools will do if you create more than four partitions. (If you create four Windows partitions, you won't be able to create any logical partitions, hence my 3-partition limit.) Leave space for Linux; or if you use a Linux tool and know how, go ahead and create your Linux partitions.
[*]Restore Windows and your Windows data. You can do this by re-installing Windows and restoring just your user data or by restoring everything from a backup.
[*]Test Windows to be sure it boots and works correctly. If there are problems, fix them before proceeding.
[*]Install Linux.
[/list]


Note that I'm suggesting a course of action that I understand. I'm not an expert on LDM, and somebody who is an expert on LDM might be able to offer a quicker and easier path to recovery. I don't know of an LDM expert on this forum, so you might want to post to a Windows forum for advice before you implement my solution. (Other than buying a backup drive; that's a vital piece of equipment whether or not you need to use it today.)

---

