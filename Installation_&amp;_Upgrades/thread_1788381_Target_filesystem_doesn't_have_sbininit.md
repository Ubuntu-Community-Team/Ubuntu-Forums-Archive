---
title: "Target filesystem doesn't have /sbin/init"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by chaozuper on 2011-06-22
Hi there. For some reason, I can't get Ubuntu to boot. The computer isn't actually mine so I don't know exactly what happened, but I think an update went badly wrong...

Anyway, whenever I try and boot Ubuntu, i get this

```

Killed
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init= bootarg

(and then something about initramfs)

```

I've been trying to find out what the error is on the forums, and I think it could be to do with grub not being able to find something, but I really don't know because I don't understand exactly what's going on.

I can load the grub menu, but I can't boot Ubuntu from there. Also, I can't run or install Ubuntu on a live usb because it just hangs at the Ubuntu loading screen.

Any help would be greatly appreciated.

chaozuper.

---

### Post by Rubi1200 on 2011-06-22
Try using Slax to boot the computer:
[http://distrowatch.com/table.php?distribution=slax](http://distrowatch.com/table.php?distribution=slax)

You should be able to put it on a USB stick and run it:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If you do manage to get it booted, please do the following so we can get a better idea of what is going on:

Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by chaozuper on 2011-06-23
Ok, i got the results.txt file
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 3.71 2008-07-31
    Boot sector info:   Syslinux looks at sector 540800 of /dev/sdb1 for its 
                       second stage. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /boot/syslinux/syslinux.cfg /boot/syslinux/ldlinux.sys

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdh: ___________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   According to the info in the boot sector, sdh has 
                       1415168 sectors.. But according to the info from the 
                       partition table, it has 31506432 sectors.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00084d8b

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   973,848,575   973,846,528  83 Linux
/dev/sda2         973,850,622   976,773,119     2,922,498   5 Extended
/dev/sda5         973,850,624   976,773,119     2,922,496  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e29e1

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048     7,473,151     7,471,104   b W95 FAT32
/dev/sdb2           7,475,198     7,933,951       458,754   5 Extended
/dev/sdb5           7,475,200     7,933,951       458,752  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        249cd791-45d0-45f8-9d8b-65bac7e8d70f   ext4       
/dev/sda5        c3f67a6e-3291-496d-a4a3-1b8a45e29062   swap       
/dev/sdb1        1CEC-1AD6                              vfat       
/dev/sdb5        f49dfc99-2007-4c7a-a0f4-6561b2b662e2   swap       
/dev/sdh         8C84-649B                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /mnt/sdb1                vfat       (rw,noatime,quiet,umask=0,check=s,shortname=mixed)
/dev/sdg         /mnt/sdg                 vfat       (rw)
/dev/sdh         /mnt/sdh                 vfat       (rw)


======================= sdb1/boot/syslinux/syslinux.cfg: =======================

--------------------------------------------------------------------------------
INCLUDE /boot/slax.cfg
--------------------------------------------------------------------------------

=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/initrd.gz
            ?? = ??             boot/vmlinuz

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/syslinux/ldlinux.sys
            ?? = ??             boot/syslinux/menu.c32
            ?? = ??             boot/syslinux/syslinux.cfg

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 boot/syslinux/menu.c32             :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

hda sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

File descriptor 11 (socket:[12153]) leaked on lvscan invocation. Parent PID 8993: /bin/bash
mdadm: No arrays found in config file


```

---

### Post by Rubi1200 on 2011-06-23
It appears there is possible damage to the file-system which is most likely why those errors appeared.

You can use the Slax CD to try and fix this by running the following command:

```
e2fsck -f -y -v /dev/sda1
```

Once the command completes, and assuming there are no errors, reboot the computer taking out the LiveCD.

Let me know if this allows you to boot normally.

---

### Post by chaozuper on 2011-06-23
Ok, i tried e2fsck -f -y -v /dev/sdal , but i got this error:

```

e2fsck 1.41.3 (12-Oct-2008)
e2fsck: No such file or directory while trying to open /dev/sdal

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
[INDENT]e2fsck -b 8193 <device>
[/INDENT]
```

i wonder if maybe i was doing something wrong, but i'm not sure because i don't really have a clue what any of this means :)

I was running slax in text mode if that makes any difference. Thanks for the help, though!

---

### Post by Rubi1200 on 2011-06-24
It looks as if you might have typed an l (L) not a 1 in the command?

If it still doesn't work then we can try something else.

---

### Post by chaozuper on 2011-06-26
Brilliant! It worked first time, after you pointed out that typo. Thankyou very much, Rubi1200, you've saved my bacon.

---

### Post by Ferralll on 2011-12-29
OH MY GOD!!! 
This post saved my life! 

I let my brother in law use my computer for 10 min.  And I have no idea how, but I got the same error. 
I got a ubuntu live CD and did the command above, and now it works. 


(I tried to use the USB for teh live, but I get the "Unable to enumerate device" error, so it did not work.)

THANKYOU SOOO MUCH!!!!

---

### Post by ThomWilhelm on 2012-01-07
Wow this thread saved me also, thank you. I disconnected the hard drive of a laptop before a flight so I could carry the drive in my hand luggage, but pack the laptop itself in my checked-in baggage.

When I connected them back together again I got this error, was convinced something had been damaged during the journey. Luckily doing this process has restored it all again nicely, would love to know why this happened in the first place but at least it's solved :)

---

### Post by JackTheKnife on 2012-03-13
I have similar issue but can't get it to fix. Here is my boot info dump file:

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 2 for /grub.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'
mount: unknown filesystem type 'ext4'

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,048    31,999,999    31,997,952  82 Linux swap / Solaris
/dev/sda2    *     32,000,000    33,001,471     1,001,472  83 Linux
/dev/sda3          33,001,472   130,705,407    97,703,936  83 Linux
/dev/sda4         130,707,454   488,280,063   357,572,610   5 Extended
/dev/sda5         130,707,456   155,142,143    24,434,688  83 Linux
/dev/sda6         155,144,192   174,721,023    19,576,832  83 Linux
/dev/sda7         174,723,072   488,280,063   313,556,992  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2040 MB, 2040528896 bytes
2 heads, 63 sectors/track, 31630 cylinders, total 3985408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00055b37

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     3,985,407     3,985,376   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        c3fffc34-b45f-4997-8c70-b383fd5721ad   swap       
/dev/sda2        aeb81e2a-6ef3-41eb-973e-25e86aeb8a15   ext4       
/dev/sda3        c7d9b090-574f-42dd-ac2a-4f3072dee22a   ext4       
/dev/sda5        4d973622-0147-4859-89cf-44d65013d850   ext4       
/dev/sda6        7bfcb745-b079-4e73-bedf-b6433a244e35   ext4       
/dev/sda7        ca2fb76e-0e44-4a0c-a7e7-b55f46ceb010   ext4       
/dev/sdb1        2C50-0615                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /mnt/sdb1                vfat       (rw,noatime,quiet,umask=0,check=s,shortname=mixed)
/dev/sr0         /mnt/sr0                 iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  21 19 12 0b 0a 07 0a 22  3f 66 8c a6 c3 d5 e1 ef  |!......"?f......|
00000010  f5 fb fd fa ff 1c fe f9  d8 b0 85 69 4e 34 27 1f  |...........iN4'.|
00000020  21 29 30 34 38 38 37 35  34 34 36 38 37 35 34 36  |!)04887544687546|
00000030  38 39 38 01 38 39 f7 3a  f8 3b fe 3c ff 3a 15 3b  |898.89.:.;.<.:.;|
00000040  3c 3c 3b 39 38 35 35 36  38 38 39 39 3a 3b 3f 43  |<<;985568899:;?C|
00000050  44 41 3d 3c 3d fe 3e 04  3f 40 41 42 44 fe 45 30  |DA=<=.>.?@ABD.E0|
00000060  43 40 3f 3f 42 48 4d 51  52 50 4f 4e 4c 4b 4a 4a  |C@??BHMQRPONLKJJ|
00000070  49 47 44 42 3f 3d 3d 3e  3e 3a 36 30 2c 2b 2b 2e  |IGDB?==>>:60,++.|
00000080  36 40 4d 60 6d 7f 92 a0  b1 ba c3 cb ce d3 d7 d9  |6@M`m...........|
00000090  da fe d9 09 db de e1 e5  e6 e9 ee f4 f9 fd fd ff  |................|
000000a0  ff fe 00 fa 33 f4 eb e3  dd d9 d9 db da da dc de  |....3...........|
000000b0  e1 e4 e6 e8 e7 e8 e7 e8  eb f2 f7 fa f8 f1 e9 de  |................|
000000c0  ce c2 b0 a1 96 8b 86 88  8d 96 a2 ab b7 c2 ca d2  |................|
000000d0  d5 d9 de e0 e4 e9 ef f7  fd fe ff 11 f9 f2 e7 dd  |................|
000000e0  d8 de e9 f5 fb fe ff fe  fa f3 ee f0 f7 fe fd ff  |................|
000000f0  0e fe f0 e0 d1 c8 c5 cb  d5 e0 e7 ed f4 f7 fb fd  |................|
00000100  fd ff 0f fd fc fd ff ff  fc f8 f3 ee e9 e7 e5 e1  |................|
00000110  dd d9 d6 12 d4 d3 d4 d2  cd c6 bd b7 b1 a8 a1 9b  |................|
00000120  9a 9a 9c 9e 9e 9d 9b fd  9a 05 9b 9c 9c 9d 9e 9f  |................|
00000130  fe a0 01 9f 9d f8 9c 39  9d a0 a3 a8 ae b2 b8 bb  |.......9........|
00000140  c0 c7 cd d3 d5 d9 e1 e8  ee f0 ef e8 de d5 d0 cf  |................|
00000150  d2 d9 dc db d8 d4 d0 d2  db e5 eb ee e5 d2 ba 9b  |................|
00000160  87 6c 4e 38 1f 12 0e 10  1a 22 25 26 25 23 21 21  |.lN8....."%&%#!!|
00000170  20 20 fe 21 03 20 1e 1c  1a fe 18 ff 19 01 17 16  |  .!. ..........|
00000180  fd 14 ff 15 06 14 12 11  11 12 15 17 ff 18 33 16  |..............3.|
00000190  13 11 12 14 16 18 18 17  14 11 0f 10 11 14 17 18  |................|
000001a0  1c 24 2d 3f 53 66 75 79  75 6a 5a 47 38 27 1a 11  |.$-?SfuyujZG8'..|
000001b0  08 05 06 09 0e 11 12 13  15 16 17 17 16 16 00 fe  |................|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 d8 74 01 00 fe  |............t...|
000001d0  ff ff 05 fe ff ff 02 d8  74 01 00 c0 2a 01 00 00  |........t...*...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file



```

Any thoughts? 

Thanks

---

### Post by ucracker on 2012-06-22
Hello JackTheKnife!
I've got a similar problem, Ubuntu 10.04 did not wanted to load, tried the comand above but was always receiving that the device was mounted.
What i did:
Booted an Ubuntu Live CD, opened the terminal and typed:
```

sudo debugfs -w /dev/sdax

```
change x for your ubuntu partition.
then you'll have this:
```

sudo debugfs -w /dev/sda1
debugfs 1.41.11 (14-Mar-2010)
debugfs: 

```
type in: clri <8>
and after hitting enter, 
type this: quit
then reboot and boot live cd again. 
Then open the terminal and type:
```

e2fsck -f -y -v /dev/sdax

```

And this will repair your partition and after rebooting, you will be able to enjoy your ubuntu again :)

Source: this thread and [http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038).

---

### Post by Falkendawg on 2012-07-29
Thanks so much for this! Woke up this morning and my computer froze coming out of sleep, rebooted and all this happened! Luckily I found this page and still had my Live USB! A strange tidbit from my experience, upon botting from the USB, I had no mouse control! Not from my laptops touchpad or my USB mouse. Strange indeed, don't know if I'll be updating anymore after this >_>

---

### Post by brown320 on 2012-08-05
I'm trying to just re-install a new version of Ubuntu after encountering this problem.

I burned Ubuntu 12.0.4 onto a stick and I'm trying to boot it up on the busted laptop but I'm still getting the same black screen BS.  I did change the boot order--moved USB memory into position 1.  

Any help??

edit:  I played around with the BIOS settings, restored defaults, then re-ordered the booting order again.  Then I restarted and just hit enter before I saw any HDD booting, and voila.  It finally booted from the USB.  Now I'm trying to install 12.0.04 with the option to carry over my files from the existing copy of Ubuntu 10.0.4.  If that works, great, but I didn't have anything particularly important on that OS so no biggie.  As long as I HAVE an OS that works I'm happy.

---

### Post by hh holmes on 2012-08-29
> **ucracker said:**
> Hello JackTheKnife!
I've got a similar problem, Ubuntu 10.04 did not wanted to load, tried the comand above but was always receiving that the device was mounted.
What i did:
Booted an Ubuntu Live CD, opened the terminal and typed:
```

sudo debugfs -w /dev/sdax

```change x for your ubuntu partition.
then you'll have this:
```

sudo debugfs -w /dev/sda1
debugfs 1.41.11 (14-Mar-2010)
debugfs: 

```type in: clri <8>
and after hitting enter, 
type this: quit
then reboot and boot live cd again. 
Then open the terminal and type:
```

e2fsck -f -y -v /dev/sdax

```And this will repair your partition and after rebooting, you will be able to enjoy your ubuntu again :)

Source: this thread and [http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038).

:guitar:  This worked for me!  My issue was very similar to JackTheKnife's.  Here is my boot info script for any others that may experience this error.

```


                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => MS-DOS 3.30 through Windows 95 (A) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type 'ext4'

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 240.
    Operating System:  
    Boot files:        

hda: ___________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /boot/syslinux/syslinux.cfg

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b2cbf

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   187,336,703   187,334,656  83 Linux
/dev/sda2         187,338,750   195,371,007     8,032,258   5 Extended
/dev/sda5         187,338,752   195,371,007     8,032,256  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2043 MB, 2043674624 bytes
62 heads, 61 sectors/track, 1055 cylinders, total 3991552 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04030201

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                 240     3,991,551     3,991,312   6 FAT16


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/hda                                                iso9660    SLAX
/dev/sda1        411c6ce6-46e6-4663-99c1-b2680ad98231   ext4       
/dev/sda5        f08962a9-ad30-4570-8177-8e214b80d717   swap       
/dev/sdb1        BEFA-D200                              vfat       New Volume

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/hda         /mnt/hda                 iso9660    (ro,noatime)
/dev/sdb1        /mnt/sdb1                vfat       (rw)


======================= hda/boot/syslinux/syslinux.cfg: ========================

--------------------------------------------------------------------------------
INCLUDE /boot/slax.cfg
--------------------------------------------------------------------------------

==================== hda: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/initrd.gz
            ?? = ??             boot/vmlinuz

================== hda: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/syslinux/syslinux.cfg

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  b3 01 89 c4 79 7a a2 f8  a5 17 40 20 0f 08 b7 82  |....yz....@ ....|
00000010  38 8a 21 1e f5 55 ef 28  dd f2 b5 b2 cc c5 83 15  |8.!..U.(........|
00000020  30 7b e0 35 df 58 d5 b8  b1 38 d0 47 db 6b 03 5c  |0{.5.X...8.G.k.\|
00000030  7c 52 ad 46 a8 51 3c bb  04 55 b9 6c 9a 3a dd 68  ||R.F.Q<..U.l.:.h|
00000040  a0 5f 5c 14 6b 72 bb 47  51 49 78 1c 99 bb f2 cd  |._\.kr.GQIx.....|
00000050  4a c1 fa a0 75 ef 97 ef  b7 ba 22 58 98 d8 d5 e2  |J...u....."X....|
00000060  3e b6 ff 83 1e 06 5e f8  46 8c 6b 29 29 cf f9 5d  |>.....^.F.k))..]|
00000070  03 39 a0 4c a8 46 77 f8  4e 9f 4c d1 96 26 ad 18  |.9.L.Fw.N.L..&..|
00000080  1d af 2f 13 4e 8d 42 9f  07 7a 6f 09 47 4d 5a a5  |../.N.B..zo.GMZ.|
00000090  42 f9 4a 0d b5 83 ab 1a  b7 f7 64 bc 6c 18 e3 c6  |B.J.......d.l...|
000000a0  a8 95 b3 63 df 8f 3a d7  97 de bf 7d fc 8a c7 80  |...c..:....}....|
000000b0  72 cd f4 ef e9 28 8d c7  7b 0e ab 53 ba 77 d5 20  |r....(..{..S.w. |
000000c0  8b 38 7a 6a 86 39 ad e7  20 d4 d2 6a 91 d5 83 98  |.8zj.9.. ..j....|
000000d0  a1 5a 9f 45 54 7b e5 ba  df e0 18 23 d1 d7 fc 5d  |.Z.ET{.....#...]|
000000e0  96 fe d8 c0 b1 35 26 bb  4c ca 3a fc 55 ff 0e e8  |.....5&.L.:.U...|
000000f0  19 e3 24 bb f1 e0 8f 33  b9 dc 95 09 f4 fc 03 09  |..$....3........|
00000100  f5 a5 26 87 aa 47 e3 bf  58 a7 df e4 8a b4 18 66  |..&..G..X......f|
00000110  25 89 51 57 7f b6 ea 4f  df 28 8b 9a 2f f2 a8 3d  |%.QW...O.(../..=|
00000120  57 10 f9 4f d6 6c 50 23  ed bf 53 15 7f cb e5 4f  |W..O.lP#..S....O|
00000130  73 58 61 b8 73 d3 e5 fb  fc c4 dc 0a 4b c2 10 30  |sXa.s.......K..0|
00000140  8e 07 6f 16 a2 32 84 eb  0c 7c 5d bf 12 72 2b 53  |..o..2...|]..r+S|
00000150  ec 65 1b 54 92 9e 19 ba  a5 76 8f be a4 bf aa b3  |.e.T.....v......|
00000160  99 3e 55 80 ab 38 23 97  e2 9e 96 a7 d7 6d ff fe  |.>U..8#......m..|
00000170  3c bb 31 7c 51 22 7a df  62 e4 8a c1 9a 55 f5 36  |<.1|Q"z.b....U.6|
00000180  55 32 cc 83 bc a9 49 86  82 3f 6d 6c ba 8e bd 47  |U2....I..?ml...G|
00000190  67 3a a7 ab 06 b0 66 a3  ca 14 de d0 3e d4 50 ad  |g:....f.....>.P.|
000001a0  a0 2c 4e 3e c6 e0 29 f3  37 98 a6 81 76 49 02 84  |.,N>..).7...vI..|
000001b0  fb 28 f2 ef b6 b1 d1 d5  ca 80 61 67 6f 94 00 fe  |.(........ago...|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 90 7a 00 00 00  |............z...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
File descriptor 11 (socket:[10390]) leaked on lvscan invocation. Parent PID 5868: /bin/bash
mdadm: No arrays found in config file 

```

---

### Post by alecz20 on 2012-09-19
Is there any way of fixing this without booting from another OS?
Maybe ubuntu has some recovery console that can be accessed?

Otherwise, it would be a good idea to have another instance of linux installed on another partition and boot from that one to fix the ubuntu partition.

---

### Post by Krakken on 2013-01-27
Hi guys no luck for me in this issue. The command e2fsck is giving me the following error

Attempt to read block from filesystem resulted in short read while trying to open dev/sda2 
Could it be a zero length partition?

Any suggestions?

---

### Post by hh holmes on 2013-02-12
This hit me again.  It looks like a complete mess this time around, possibly due to my amateur tinkering.  Yikes.

I'm about ready to just re-install.  I have most everything backed up so it wouldn't be too painful.  Oh well, maybe this post and a response will help someone else.


```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No known boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Syslinux 4.03 or higher
    Boot sector info:  Syslinux looks at sector 3678208 of /dev/sdb1 for its 
                       second stage. It is very unlikely that Syslinux is 
                       (still) installed. The second stage could not be 
                       found. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2043 MB, 2043674624 bytes
62 heads, 61 sectors/track, 1055 cylinders, total 3991552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *            240     3,991,551     3,991,312   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1                                              squashfs   
/dev/loop2                                              squashfs   
/dev/loop3                                              squashfs   
/dev/loop4                                              squashfs   
/dev/loop5                                              squashfs   
/dev/loop6                                              squashfs   
/dev/sdb1        803C-4C2E                              vfat       NEW VOLUME
/dev/sr0                                                iso9660    Slax CD
/dev/zram0       58c8287f-6d36-4b97-92d8-ee7342286b75   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb1        /media/NEW VOLUME        vfat       (rw,nosuid,nodev,uid=0,gid=0,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown MBR on /dev/sda



=============================== StdErr Messages: ===============================

hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
hexdump: /dev/sda: Input/output error
  /dev/sda: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda: read failed after 0 of 4096 at 100030152704: Input/output error
  /dev/sda: read failed after 0 of 4096 at 100030234624: Input/output error
  /dev/sda: read failed after 0 of 4096 at 4096: Input/output error
  /dev/sda1: read failed after 0 of 4096 at 95915278336: Input/output error
  /dev/sda1: read failed after 0 of 4096 at 95915335680: Input/output error
  /dev/sda1: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda1: read failed after 0 of 4096 at 4096: Input/output error
  /dev/sda5: read failed after 0 of 4096 at 4112449536: Input/output error
  /dev/sda5: read failed after 0 of 4096 at 4112506880: Input/output error
  /dev/sda5: read failed after 0 of 4096 at 0: Input/output error
  /dev/sda5: read failed after 0 of 4096 at 4096: Input/output error
  No volume groups found
mdadm: No arrays found in config file or automatically


```

---

