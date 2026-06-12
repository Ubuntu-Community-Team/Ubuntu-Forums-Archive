---
title: "Installer Crashed"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by alymac10 on 2011-01-02
Hi,

I bought this HP 2133 netbook for my mother about a year ago, it came pre-installed with a linux called SUSE which i found pretty difficult to do anything with really never mind my mother.

I downloaded the netbook remix 10.10 on the ubuntu website, followed instructions for putting iso onto a USB pen and changed boot order fine and insatlled it, everything looked like it was completed and installed but i got two error messages at the end. Since its not properly installed and SUSE wont load at all now i have written them down.

First one is:
"apt confirguration problem
an attempt to confirgure apt to install additional packages from the cd failed"
I should not that there is no cd as its a netbook and its been insatlled from USB.

Second error
Similar to the error in the first post of this thread here [http://ubuntuforums.org/showthread.php?t=1540900&highlight=Installer+Crashed]("http://ubuntuforums.org/showthread.php?t=1540900&highlight=Installer+Crashed") but with no information or details whatsoever after "partman: "
and thats all i get, clicking close does nothing and i have to shut it down with the power button and now of course the old OS, SUSE isnt working at all either, just the HP screen and then a black screen with flashing cursor and thats it.

I have tried this 3 times now, all with the same result.

Any help would be appreciated, i reported a bug report like the message said as well.

Thanks

---

### Post by alymac10 on 2011-01-03
Bump

Anyone able to help with this?

---

### Post by Quackers on 2011-01-03
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by alymac10 on 2011-01-03
Hi Quackers, thanks for reply, at work now, will do this as soon as i can, thanks.

---

### Post by alymac10 on 2011-01-03
I m having some problems with wireless firmware now but following steps on the documentation to hopefully sort that out.

I re-downloaded the UNR and put it on USB drive again and i noticed during insatllation it came up with a dialog saying "cannot delete output file E:\ubuntu" and then carries on saying its completed successfully, i remember this happening the first time to, could this be the problem?

Will reply again when i get this wifi working and get that text file.

---

### Post by alymac10 on 2011-01-03
Hi, heres the results.txt

```
                             
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swsuspend
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'swsuspend'

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048   228,300,799   228,298,752  83 Linux
/dev/sda2         228,302,846   234,440,703     6,137,858   5 Extended
/dev/sda5         228,302,848   234,440,703     6,137,856  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16026435072 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31301631 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             52    31,283,909    31,283,858   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9d3f2dea-1dca-4f18-90c8-25d4a38d3aba   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        6aa323cf-a1bd-4f4c-9625-72995277397a   swsuspend                                
/dev/sda: PTTYPE="dos" 
/dev/sdb1        0A53-D27C                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


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
UUID=9d3f2dea-1dca-4f18-90c8-25d4a38d3aba /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6aa323cf-a1bd-4f4c-9625-72995277397a none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


    .2GB: boot/vmlinuz-2.6.35-22-generic
    .2GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 a8 5d 00 00 00  |............]...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 10 c8 08  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 34 00 00 00  |........?...4...|
00000020  92 5a dd 01 9c 3b 00 00  00 00 00 00 02 00 00 00  |.Z...;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 7c d2 53 0a 4e  4f 20 4e 41 4d 45 20 20  |..)|.S.NO NAME  |
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
00000100  7d 00 66 b8 00 80 20 00  66 ba 00 00 00 00 bb 00  |}.f... .f.......|
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


```

---

### Post by alymac10 on 2011-01-03
Update: I saw someone advise to try the USB pen and insatll on another seperate PC, (my bros desktop), and that failed with the exact same errors as well.....

So that would mean its the usb or the iso?
I downloaded from the ubuntu site from the guide, two seperate times and the third time i got the usb installer to download it.

All times i received the error during mounting the ISO showing "unable to delte output file E:\ubuntu"

Its a 16gig sandisk cruzer.

Any ideas?

---

