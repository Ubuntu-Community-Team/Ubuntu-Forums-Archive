---
title: "GRUB2 broken after clean 10.04 install - Please help!!"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by PinnacleMountain on 2010-05-26
After doing a clean 10.04 install (Ubuntu only, no Windows), I cannot get past the BIOS screen.  When booting from the live CD, I am able to run "boot_info_script*.sh" (see below).  I have tried re-installing GRUB2 following instructions on help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202 , but after rebooting I am back to the blank screen.  Does this have something to do with my "core.img" file being in the wrong place?




                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 3759740145 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048 3,759,740,144 3,759,738,097 Linux or Data
/dev/sda2   3,759,765,504 3,907,026,943   147,261,440 Linux Swap
/dev/sda3   3,759,740,145 3,759,765,503        25,359 Bios Boot Partition

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048 3,907,026,943 3,907,024,896 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        20b1616a-77a4-4bda-b030-41bcfc022efc   ext4                                     
/dev/sda2        c59279f9-08c5-4d99-a86d-d793793064a6   swap                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        31477e78-9456-4655-9caf-3d63512b59d7   ext4                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)
/dev/sda1        /mnt/boot                ext4       (rw)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=20b1616a-77a4-4bda-b030-41bcfc022efc /               ext4    errors=remount-ro 0       1
# /disk2 was on /dev/sdb1 during installation
UUID=31477e78-9456-4655-9caf-3d63512b59d7 /disk2          ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=c59279f9-08c5-4d99-a86d-d793793064a6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 852.6GB: grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 f2 14 19 e0  00 00 00 00 2f 00 20 08  |............/. .|
00000200

---

### Post by wilee-nilee on 2010-05-26
Would you consider editing the script to code tags please.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end
It is much easier to read. ;)

Also either your system is missing some stuff or the script is you might run it again. putting it in tags will help to begin with.

I think it is the GPT in sdb that is making the readout messed up.

---

### Post by kansasnoob on 2010-05-26
Your installation is failing badly. You're missing most of the /boot files:

> =================== sda1: Location of files loaded by Grub: ===================


852.6GB: grub/core.img

Here's a general example of what you should have:

>  20.3GB: boot/grub/core.img
  20.3GB: boot/grub/grub.cfg
  20.3GB: boot/initrd.img-2.6.32-16-generic
  20.2GB: boot/vmlinuz-2.6.32-16-generic
  20.3GB: initrd.img
  20.2GB: vmlinuz

Have you checked the integrity of the CD? With that new "silent boot" you have to press any key the moment the initial purple screen shows up then you'll see where you can select language and then you can choose to Check CD for defects.

Or maybe it has something to do with this:

> sda3: __________________________________________________ _______________________

File system: **[COLOR="Red"]Bios Boot Partition[/COLOR]**
Boot sector type: Unknown
Boot sector info: 

I haven't seen that before.

---

### Post by kansasnoob on 2010-05-26
A quick google shows:

> GRUB 2 (1.97~beta1 or later): when a BIOS Boot Partition is found during installation, GRUB will embed itself in it.

[http://en.wikipedia.org/wiki/BIOS_Boot_Partition_%28GPT%29](http://en.wikipedia.org/wiki/BIOS_Boot_Partition_%28GPT%29)

A bit more here:

[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)

So I'll bet that's the problem, I'm just clueless about it :confused:

---

### Post by PinnacleMountain on 2010-05-26
Wilee-Nilee, sorry about not using the code tags.  I ran it again and here it is.  

```
                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 3759740145 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /grub/core.img

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       Bios Boot Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1           2,048 3,759,740,144 3,759,738,097 Linux or Data
/dev/sda2   3,759,765,504 3,907,026,943   147,261,440 Linux Swap
/dev/sda3   3,759,740,145 3,759,765,503        25,359 Bios Boot Partition

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                   1 3,907,029,167 3,907,029,167  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sdb1           2,048 3,907,026,943 3,907,024,896 Linux or Data

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        20b1616a-77a4-4bda-b030-41bcfc022efc   ext4                                     
/dev/sda2        c59279f9-08c5-4d99-a86d-d793793064a6   swap                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        31477e78-9456-4655-9caf-3d63512b59d7   ext4                                     
/dev/sdb: PTTYPE="gpt" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt                     ext4       (rw)
/dev/sda1        /mnt/boot                ext4       (rw)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=20b1616a-77a4-4bda-b030-41bcfc022efc /               ext4    errors=remount-ro 0       1
# /disk2 was on /dev/sdb1 during installation
UUID=31477e78-9456-4655-9caf-3d63512b59d7 /disk2          ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=c59279f9-08c5-4d99-a86d-d793793064a6 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 852.6GB: grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  52 e8 28 01 74 08 56 be  33 81 e8 4c 01 5e bf f4  |R.(.t.V.3..L.^..|
00000010  81 66 8b 2d 83 7d 08 00  0f 84 e9 00 80 7c ff 00  |.f.-.}.......|..|
00000020  74 46 66 8b 1d 66 8b 4d  04 66 31 c0 b0 7f 39 45  |tFf..f.M.f1...9E|
00000030  08 7f 03 8b 45 08 29 45  08 66 01 05 66 83 55 04  |....E.)E.f..f.U.|
00000040  00 c7 04 10 00 89 44 02  66 89 5c 08 66 89 4c 0c  |......D.f.\.f.L.|
00000050  c7 44 06 00 70 50 c7 44  04 00 00 b4 42 cd 13 0f  |.D..pP.D....B...|
00000060  82 bb 00 bb 00 70 eb 68  66 8b 45 04 66 09 c0 0f  |.....p.hf.E.f...|
00000070  85 a3 00 66 8b 05 66 31  d2 66 f7 34 88 54 0a 66  |...f..f1.f.4.T.f|
00000080  31 d2 66 f7 74 04 88 54  0b 89 44 0c 3b 44 08 0f  |1.f.t..T..D.;D..|
00000090  8d 83 00 8b 04 2a 44 0a  39 45 08 7f 03 8b 45 08  |.....*D.9E....E.|
000000a0  29 45 08 66 01 05 66 83  55 04 00 8a 54 0d c0 e2  |)E.f..f.U...T...|
000000b0  06 8a 4c 0a fe c1 08 d1  8a 6c 0c 5a 52 8a 74 0b  |..L......l.ZR.t.|
000000c0  50 bb 00 70 8e c3 31 db  b4 02 cd 13 72 50 8c c3  |P..p..1.....rP..|
000000d0  8e 45 0a 58 c1 e0 05 01  45 0a 60 1e c1 e0 03 89  |.E.X....E.`.....|
000000e0  c1 31 ff 31 f6 8e db fc  f3 a5 1f e8 3e 00 74 06  |.1.1........>.t.|
000000f0  be 3b 81 e8 63 00 61 83  7d 08 00 0f 85 1d ff 83  |.;..c.a.}.......|
00000100  ef 0c e9 0f ff e8 24 00  74 06 be 3d 81 e8 49 00  |......$.t..=..I.|
00000110  5a ea 00 82 00 00 be 40  81 e8 3d 00 eb 06 be 45  |Z......@..=....E|
00000120  81 e8 35 00 be 4a 81 e8  2f 00 eb fe bb 17 04 80  |..5..J../.......|
00000130  27 03 c3 6c 6f 61 64 69  6e 67 00 2e 00 0d 0a 00  |'..loading......|
00000140  47 65 6f 6d 00 52 65 61  64 00 20 45 72 72 6f 72  |Geom.Read. Error|
00000150  00 bb 01 00 b4 0e cd 10  46 8a 04 3c 00 75 f2 c3  |........F..<.u..|
00000160  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 f2 14 19 e0  00 00 00 00 2f 00 20 08  |............/. .|
00000200


```

kansasnoob,  thanks for the link.  Yes, I was getting an error message when trying to re-install GRUB2 that "blocklists" were a very bad idea.  I found that you could create a BIOS Boot Partition with Gparted and that would solve the blocklists issue.  I did an md5 check on the CD and it looked ok.  I will go check it on the purple screen though.

---

### Post by PinnacleMountain on 2010-05-26
And I have no idea what you are talking about pear802 and story901.  Is that a joke?

---

### Post by wilee-nilee on 2010-05-26
Never mind kansasnoob posted the same link already.

---

