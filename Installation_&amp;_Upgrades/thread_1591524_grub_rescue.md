---
title: "grub rescue"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by TomCollier on 2010-10-09
first post :D
and its one you've probably seen time and time again.
but this is a weird variation of one :/

so, whole story
i downloaded ubuntu from the website,so i had the ISO,
then, i downloaded the program to make an ubuntu usb,
but i installed it to a blank hard-drive instead
no problems up to now,
then,
i booted from my *usb* and installed a small partition of linux on my main harddrive (with windows 7 preinstalled) but then when on widows i deleted the linux partition because it was too small, 
then when i restarted, i had the fabled GRUB RESCUE
i thought, if i reinstall linux, everything will be fine, so i tried again,
but now, on the screen when you set partition size of the install, it says there are no operating systems installed, and i can't do anything but format the entire harddrive,

but i really need to keep windows!
i should point out : i CAN access my windows from inside the linux *usb*,
but i can't access the internet or any REAL usb ports
so i can't just move the files off
what can i do???

---

### Post by jso2897 on 2010-10-09
Get "Super Grub", and burn an image disk, and boot to it.
It can fix both Linux and Windows partitions in a single session.

---

### Post by sikander3786 on 2010-10-09
Hi and a warm welcome to the community :popcorn:

Can you please post the output of bootinfo script as per instructions from the following page. You'll need to boot into a Live CD to do that. That will give us a better idea of your partitioning setup thus helping us to diagnose the problem.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

While posting, please select the text and then click '#' from top. It will be easier to read that way.

---

### Post by Rubi1200 on 2010-10-09
> **sikander3786 said:**
> Hi and a warm welcome to the community :popcorn:

Can you please post the output of bootinfo script as per instructions from the following page. You'll need to boot into a Live CD to do that. That will give us a better idea of your partitioning setup thus helping us to diagnose the problem.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

While posting, please select the text and then click '#' from top. It will be easier to read that way.
+1 to this suggestion.

Also, for future reference, you need to resize drives from within Windows 7 using the built-in Disk Management tool.

Do you have the Windows 7 installation/recovery disc? You may need it.

But first post the results of the script asked for above and please wrap the text with the code tag#

Thanks.

---

### Post by TomCollier on 2010-10-09
i don't know if i can do that D:
i'm not on the pc in question at the moment
and i can't get the results off by usb or the internet,
because when i'm on ubuntu, it won't rcognise my network card or my usb ports,
which leads me to think maybe that super grub could be a good idea

unless you have any suggestions on how i can get the results of the command you're asking for?

---

### Post by TomCollier on 2010-10-09
> **TomCollier said:**
> i don't know if i can do that D:
i'm not on the pc in question at the moment
and i can't get the results off by usb or the internet,
because when i'm on ubuntu, it won't rcognise my network card or my usb ports,
which leads me to think maybe that super grub could be a good idea

unless you have any suggestions on how i can get the results of the command you're asking for?

actually,
i've just managed to get the USB working,
i'll post the results of the script very soon

---

### Post by TomCollier on 2010-10-09
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #7 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /grldr /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda6: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   302,104,573   302,104,511   7 HPFS/NTFS
/dev/sda2         302,104,574   312,580,095    10,475,522   5 Extended
/dev/sda5         312,229,888   312,580,095       350,208  82 Linux swap / Solaris
/dev/sda6         302,104,576   306,989,055     4,884,480  83 Linux
/dev/sda7         306,991,104   307,339,263       348,160  82 Linux swap / Solaris
Invalid MBR Signature found
Empty Partition


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 20.0 GB, 20000000000 bytes
255 heads, 63 sectors/track, 2431 cylinders, total 39062500 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048    39,059,455    39,057,408   c W95 FAT32 (LBA)


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 527 MB, 527730688 bytes
2 heads, 63 sectors/track, 8180 cylinders, total 1030724 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             32     1,030,723     1,030,692   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AC90E1CA90E19ADA                       ntfs       Windows                       
/dev/sda2: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4CB2-B491                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        0013-6564                              vfat       DISK_IMG                      
/dev/sdc: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc1        /media/DISK_IMG          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /media/20080922_082744   iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=999,gid=999,iocharset=utf8,mode=0400,dmode=0500)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  4a f0 c8 ae 0a cc 69 86  d4 17 d1 a3 5d 8c b0 d9  |J.....i.....]...|
00000010  03 56 34 aa 91 a7 b2 69  ba 17 e4 2c 98 a9 eb 94  |.V4....i...,....|
00000020  8c 07 af cc 9b 30 25 63  cd 2e cc 46 47 68 69 21  |.....0%c...FGhi!|
00000030  20 b1 02 24 c3 6a 07 24  dd 2a c2 c4 48 cf 91 11  | ..$.j.$.*..H...|
00000040  2c b1 55 e0 8b 5b 94 92  c9 a3 9c 60 86 38 b6 23  |,.U..[.....`.8.#|
00000050  ea b3 7c f2 71 15 a5 27  6b 48 d5 cc 59 3e c3 38  |..|.q..'kH..Y>.8|
00000060  ea 94 ea 53 85 3b a8 f9  57 4a f3 03 f8 ab f0 95  |...S.;..WJ......|
00000070  99 5e 57 19 30 a4 37 a2  30 0d 9b c2 be 94 49 13  |.^W.0.7.0.....I.|
00000080  06 d0 9d 44 17 2e e5 da  85 c3 5f 15 71 4d f8 aa  |...D......_.qM..|
00000090  1e d2 79 bc 90 66 44 b2  c0 4a b5 8f 33 16 2d c0  |..y..fD..J..3.-.|
000000a0  00 00 00 00 31 82 2e 6e  d7 99 08 22 c4 c4 27 4c  |....1..n..."..'L|
000000b0  41 22 f3 18 81 2e a8 5c  4a 1b b3 24 5d 2d 6b 4e  |A".....\J..$]-kN|
000000c0  2f 83 a4 a3 6e 81 6b 88  44 0f 02 57 6c b1 3b 63  |/...n.k.D..Wl.;c|
000000d0  49 59 14 59 74 11 97 5d  60 59 93 2f 6a ed 63 b0  |IY.Yt..]`Y./j.c.|
000000e0  44 b1 a1 bb ed 09 fc 7f  a0 37 d1 fc 60 ef ff 69  |D........7..`..i|
000000f0  e3 b0 b8 da f4 62 a2 d9  a0 96 48 34 f3 23 ea 0c  |.....b....H4.#..|
00000100  db 34 4a 80 4f 21 81 c1  ec 77 40 2b a1 a3 89 35  |.4J.O!...w@+...5|
00000110  0a 49 1c 50 77 6c 7a 09  e8 13 45 b7 b6 05 89 39  |.I.Pwlz...E....9|
00000120  4b b6 2d 17 64 64 8d a2  9b cb c1 6e 84 97 f1 52  |K.-.dd.....n...R|
00000130  a0 37 d6 ee 66 bb 98 67  6c 02 46 e9 f2 ff 44 25  |.7..f..gl.F...D%|
00000140  fd d1 77 98 ec 69 6f 67  59 4e d5 29 61 0b bb 0b  |..w..iogYN.)a...|
00000150  b6 8d b6 c3 37 a2 f0 c9  45 ec 17 8f db b6 b7 7c  |....7...E......||
00000160  ff e9 d5 5f a0 af 7a 4f  80 01 18 18 0d 2c 0e 18  |..._..zO.....,..|
00000170  82 91 35 8c 82 cc a1 cd  94 22 a0 40 94 fb 39 83  |..5......".@..9.|
00000180  d2 29 f2 41 e9 84 44 7d  d8 22 a6 2d ac a6 1f 89  |.).A..D}.".-....|
00000190  59 95 5f 94 be ed d5 f8  bc bf 1b a4 8d f0 a2 82  |Y._.............|
000001a0  eb a7 24 be 82 0f 7f 13  c7 89 ce 89 cd 81 6a c2  |..$...........j.|
000001b0  a5 12 02 d2 43 6c 1c aa  24 9c 9c a7 28 0f 00 fe  |....Cl..$...(...|
000001c0  ff ff 82 fe ff ff 02 80  9a 00 00 58 05 00 00 fe  |...........X....|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 88 4a 00 00 00  |............J...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by TomCollier on 2010-10-10
anyone?
really in bother here, 
need this for my computing A level

---

### Post by Rubi1200 on 2010-10-10
I am not sure I can help you sort this out, but there is quite a mess here unfortunately.

I will point out some of the problems and then suggest some possible solutions with the caveat that you may want to wait for some other suggestions before moving ahead.

> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in      partition #7 for /boot/grub. except that on sda7 there appears to be no file system 
> sda7: _________________________________________________________________________      File system:            Boot sector type:  -     Boot sector info:       Mounting failed: mount: unknown filesystem type '' mount: unknown filesystem type '' mount: unknown filesystem type '' In fact, on sda5 and sda6 there is a similar problem.

The next problem is this:
> Invalid MBR Signature found which is probably due to this:
> Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe                         /grldr /boot/grub/core.img My assessment is that the bootloader files for Ubuntu were somehow placed on the Windows partition.

But, where did the Ubuntu operating system go?

My first suggestion would be to try and recover the Windows installation by reinstalling the bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If, as you said, you can access files on the Windows partition you should first delete some files before taking the steps to install the Windows bootloader.

These files need to go (but be very careful please!): 
> /boot/grub/core.imgI am not sure if you should/need to delete the > grldrfile and I would wait to hear more from others about this.

You can also consider using Testdisk to try and recover the Ubuntu partitions.

You could also try running this from the LiveCD to see if it will get the Linux partitions back:

```
sudo e2fsck -C0 -p -f -v /dev/sdax

```if there are errors then run this:
```
sudo e2fsck -f -y -v /dev/sdax
```where x represents the partition where Ubuntu was installed. If you are unsure or do not remember then don't do this. It is probably sda7, but be careful!

---

### Post by TomCollier on 2010-10-10
thanks for the info, i'll take on board what you've said, but i'll also wait for a second opinion, ( like you also said)

cheers though!

---

### Post by Rubi1200 on 2010-10-10
No problem :)

I will ask oldfred, one of the more experienced members, to take a look and offer his thoughts on this.

---

### Post by oldfred on 2010-10-10
+1 for Rubi1200 suggestions.

You have /grldr which is grub4dos which can confuse things and should be deleted. Windows will not boot with /Boot & /boot folders as windows sees them as the same thing. Delete the /boot folder. If really concerned you can rename it to /bootold or something then delete when everything is working. From the author of the boot script:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

Test disk is the best way to rewrite the partitions, while I have not used to repair a partition (knock on wood) several others with similar issues have.You have some issue as it shows a partition table then:
Invalid MBR Signature found Empty Partition

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
repairs including testdisk info & link to testdisk, testdisk is in repository and on most linux based repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
download TestDisk [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

So different tools that looks at different info are finding inconsistenies.

The e2fsck may work and will not hurt anything as it is looking for file inconsistencies.

---

