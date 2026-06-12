---
title: "Grub error 22"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by Johndo1 on 2010-01-24
My friend was messing with his partitions and something wen't wrong. When he rebooted his Grub gave the error: Grub error 22. He doesn't have internet right now. Know of any fixes? He's booted into a live cd. 

Ubuntu 9.10

---

### Post by presence1960 on 2010-01-24
[http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors](http://www.gnu.org/software/grub/manual/grub.html#Stage1_002e5-errors)

Messing with the partitions? Well GRUB is now pointing to a non-existant partition. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Johndo1 on 2010-01-24
Unfortunately he doesn't have internet. I'll try to get him over to my house and we'll do what you said.

---

### Post by presence1960 on 2010-01-24
> **Johndo1 said:**
> Unfortunately he doesn't have internet. I'll try to get him over to my house and we'll do what you said.

I will need that info to see exactly how the partitions are setup now so we can configure GRUB to boot again.

---

### Post by Johndo1 on 2010-01-30
here is the entire document.




```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       208,844       208,782  de Dell Utility
/dev/sda2             208,896    21,180,415    20,971,520   7 HPFS/NTFS
/dev/sda3    *     22,362,480   261,136,574   238,774,095   7 HPFS/NTFS
/dev/sda4         261,136,699   312,578,047    51,441,349   f W95 Ext d (LBA)
/dev/sda5         307,337,216   312,578,047     5,240,832  dd Dell Media Direct
/dev/sda6         306,986,148   307,323,449       337,302  82 Linux swap / Solaris
/dev/sda7         307,323,513   307,337,215        13,703  83 Linux
/dev/sda8         261,136,764   302,118,389    40,981,626  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D8-0303                              vfat       DellUtility                   
/dev/sda2        10601B24601B1058                       ntfs       RECOVERY                      
/dev/sda3        BEBE1ECEBE1E7ED9                       ntfs       OS                            
/dev/sda5        C422-C7F0                              vfat       MEDIADIRECT                   
/dev/sda6        becf7bde-18d2-45e4-8054-32c42392f1d2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda5/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda8

00000000  ff a1 00 00 2a 00 00 00  6a 55 5a 4b aa 68 ec 4a  |....*...jUZK.h.J|
00000010  aa 68 ec 4a 00 00 00 00  00 00 01 00 00 00 00 00  |.h.J............|
00000020  00 00 00 00 00 00 00 00  2e 2e 2f 63 6f 6e 66 2e  |........../conf.|
00000030  61 76 61 69 6c 2f 35 33  2d 6d 6f 6e 6f 73 70 61  |avail/53-monospa|
00000040  63 65 2d 6c 63 64 2d 66  69 6c 74 65 72 2e 63 6f  |ce-lcd-filter.co|
00000050  6e 66 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |nf..............|
00000060  00 00 00 00 04 42 ae 55  00 00 00 00 00 00 00 00  |.....B.U........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  ff a1 00 00 1b 00 00 00  6a 55 5a 4b aa 68 ec 4a  |........jUZK.h.J|
00000090  aa 68 ec 4a 00 00 00 00  00 00 01 00 00 00 00 00  |.h.J............|
000000a0  00 00 00 00 00 00 00 00  2e 2e 2f 63 6f 6e 66 2e  |........../conf.|
000000b0  61 76 61 69 6c 2f 36 30  2d 6c 61 74 69 6e 2e 63  |avail/60-latin.c|
000000c0  6f 6e 66 00 00 00 00 00  00 00 00 00 00 00 00 00  |onf.............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 05 42 ae 55  00 00 00 00 00 00 00 00  |.....B.U........|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  ff a1 00 00 26 00 00 00  6a 55 5a 4b aa 68 ec 4a  |....&...jUZK.h.J|
00000110  aa 68 ec 4a 00 00 00 00  00 00 01 00 00 00 00 00  |.h.J............|
00000120  00 00 00 00 00 00 00 00  2e 2e 2f 63 6f 6e 66 2e  |........../conf.|
00000130  61 76 61 69 6c 2f 36 34  2d 74 74 66 2d 61 72 70  |avail/64-ttf-arp|
00000140  68 69 63 2d 75 6d 69 6e  67 2e 63 6f 6e 66 00 00  |hic-uming.conf..|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 06 42 ae 55  00 00 00 00 00 00 00 00  |.....B.U........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  a4 81 e8 03 97 52 05 00  e6 83 4a 4b e6 83 4a 4b  |.....R....JK..JK|
00000190  e6 83 4a 4b 00 00 00 00  e8 03 01 00 b8 02 00 00  |..JK............|
000001a0  00 00 00 00 00 00 00 00  00 10 00 00 01 10 00 00  |................|
000001b0  02 10 00 00 03 10 00 00  04 10 00 00 05 10 00 00  |................|
000001c0  06 10 00 00 07 10 00 00  08 10 00 00 09 10 00 00  |................|
000001d0  0a 10 00 00 0b 10 00 00  0c 10 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 89 65 65 93  00 00 00 00 00 00 00 00  |.....ee.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


```

---

### Post by presence1960 on 2010-01-30
Ok you got a little mess there. Your sda7 & sda8 have a problem and are unmountable. GRUB 0.97 is on MBR (as it should be!) but looks to sda9 for /boot/grub/menu.lst

sda9 does not exist. I am assuming when you did whatever you tried to do that your Ubuntu partition is now sda8 (root).

Try runing fsck from the Ubuntu Live CD. Boot the CD and choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo e2fsck /dev/sda8 -y -f -v -c
```
let it complete.

Then open a file browser and see if you can mount sda8 by highlighting it on the left pane. If you aren't sure which partitions are which run another boot info script and post it back here. Hopefully those partitions can now be mounted and we can find out if they are your ubuntu partitions or not.

Hopefully sda8 is ubuntu. If they are not we can fix the MBR so windows can boot if need be. Then you can reinstall ubuntu at your leisure.

---

### Post by Johndo1 on 2010-01-30
my ubuntu used to be on sda9 but now for some reason it says its on sda8 not sure how that happened but ill try what you said.

---

### Post by presence1960 on 2010-01-30
> **Johndo1 said:**
> my ubuntu used to be on sda9 but now for some reason it says its on sda8 not sure how that happened but ill try what you said.

recheck my post. I edited it. sda7 is too small to be ubuntu root.

---

### Post by Johndo1 on 2010-01-30
this is what i have now.

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #9 for /boot/grub/stage2 and /boot/grub/menu.lst.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /ntldr /NTDETECT.COM

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda8: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       208,844       208,782  de Dell Utility
/dev/sda2             208,896    21,180,415    20,971,520   7 HPFS/NTFS
/dev/sda3    *     22,362,480   261,136,574   238,774,095   7 HPFS/NTFS
/dev/sda4         261,136,699   312,578,047    51,441,349   f W95 Ext d (LBA)
/dev/sda5         307,337,216   312,578,047     5,240,832  dd Dell Media Direct
/dev/sda6         306,986,148   307,323,449       337,302  82 Linux swap / Solaris
/dev/sda7         307,323,513   307,337,215        13,703  83 Linux
/dev/sda8         261,136,764   302,118,389    40,981,626  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        07D8-0303                              vfat       DellUtility                   
/dev/sda2        10601B24601B1058                       ntfs       RECOVERY                      
/dev/sda3        BEBE1ECEBE1E7ED9                       ntfs       OS                            
/dev/sda5        C422-C7F0                              vfat       MEDIADIRECT                   
/dev/sda6        becf7bde-18d2-45e4-8054-32c42392f1d2   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda5/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=1024

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda8

00000000  ff a1 00 00 2a 00 00 00  6a 55 5a 4b aa 68 ec 4a  |....*...jUZK.h.J|
00000010  aa 68 ec 4a 00 00 00 00  00 00 01 00 00 00 00 00  |.h.J............|
00000020  00 00 00 00 00 00 00 00  2e 2e 2f 63 6f 6e 66 2e  |........../conf.|
00000030  61 76 61 69 6c 2f 35 33  2d 6d 6f 6e 6f 73 70 61  |avail/53-monospa|
00000040  63 65 2d 6c 63 64 2d 66  69 6c 74 65 72 2e 63 6f  |ce-lcd-filter.co|
00000050  6e 66 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |nf..............|
00000060  00 00 00 00 04 42 ae 55  00 00 00 00 00 00 00 00  |.....B.U........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  ff a1 00 00 1b 00 00 00  6a 55 5a 4b aa 68 ec 4a  |........jUZK.h.J|
00000090  aa 68 ec 4a 00 00 00 00  00 00 01 00 00 00 00 00  |.h.J............|
000000a0  00 00 00 00 00 00 00 00  2e 2e 2f 63 6f 6e 66 2e  |........../conf.|
000000b0  61 76 61 69 6c 2f 36 30  2d 6c 61 74 69 6e 2e 63  |avail/60-latin.c|
000000c0  6f 6e 66 00 00 00 00 00  00 00 00 00 00 00 00 00  |onf.............|
000000d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000e0  00 00 00 00 05 42 ae 55  00 00 00 00 00 00 00 00  |.....B.U........|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  ff a1 00 00 26 00 00 00  6a 55 5a 4b aa 68 ec 4a  |....&...jUZK.h.J|
00000110  aa 68 ec 4a 00 00 00 00  00 00 01 00 00 00 00 00  |.h.J............|
00000120  00 00 00 00 00 00 00 00  2e 2e 2f 63 6f 6e 66 2e  |........../conf.|
00000130  61 76 61 69 6c 2f 36 34  2d 74 74 66 2d 61 72 70  |avail/64-ttf-arp|
00000140  68 69 63 2d 75 6d 69 6e  67 2e 63 6f 6e 66 00 00  |hic-uming.conf..|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  00 00 00 00 06 42 ae 55  00 00 00 00 00 00 00 00  |.....B.U........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  a4 81 e8 03 97 52 05 00  e6 83 4a 4b e6 83 4a 4b  |.....R....JK..JK|
00000190  e6 83 4a 4b 00 00 00 00  e8 03 01 00 b8 02 00 00  |..JK............|
000001a0  00 00 00 00 00 00 00 00  00 10 00 00 01 10 00 00  |................|
000001b0  02 10 00 00 03 10 00 00  04 10 00 00 05 10 00 00  |................|
000001c0  06 10 00 00 07 10 00 00  08 10 00 00 09 10 00 00  |................|
000001d0  0a 10 00 00 0b 10 00 00  0c 10 00 00 00 00 00 00  |................|
000001e0  00 00 00 00 89 65 65 93  00 00 00 00 00 00 00 00  |.....ee.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


```

---

### Post by presence1960 on 2010-01-30
At this point since you can't mount sda8 to even see what it is I would have to say reinstall ubuntu. Unless you have important data on sda7 & sda8 delete those partitions using gparted from the Live Cd and reinstall.

---

### Post by Johndo1 on 2010-01-30
i just reinstalled ubuntu over everything because i really didnt need anythong else on there. but now i cant activate any of my hardware drivers or update because i need to activate them in order to connect to the internet (my only access to the internet is a wireless connection)

---

### Post by |{urse on 2010-01-30
Oh.. 

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

Works great, in a pinch.

---

### Post by Johndo1 on 2010-01-30
im not able to do that because i need to activate my hardware drivers in order to connect to the internet.

---

### Post by |{urse on 2010-01-31
Oh I see, I guess I didnt catch that part. You have no ethernet connection available, only wireless. You're gonna have to ask a friend if you can use their jack or do it at school if you go to school. I've been in your situation before, sucks man.

---

