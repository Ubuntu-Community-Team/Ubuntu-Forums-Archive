---
title: "Installed 10.10 Netbook via Wubi on XP. &quot;grub rescue&gt;&quot; is all I get"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by rudasn on 2010-10-28
Installed 10.10 netbook via Wubi on windows XP. After installing some updates and restarting all I get is "grub rescue>" command line.

I now booted from a USB stick and used the bootinfoscript. Here are the results:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
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

/dev/sda1                  63     8,193,149     8,193,087  12 Compaq diagnostics
/dev/sda2    *      8,193,150    90,124,649    81,931,500   7 HPFS/NTFS
/dev/sda3          90,124,650   312,576,704   222,452,055   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders, total 7818184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     7,818,047     7,817,985   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       4d297b12-a8cd-4d3e-a3ca-8cf93b9c2c08   ext4                                     
/dev/sda1        7435-22A0                              vfat       WINRE                         
/dev/sda2        C298D32898D319AD                       ntfs       OS_Install                    
/dev/sda3        5820FC2820FC0F2E                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        007E-2A9A                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\wubildr.mbr = "Ubuntu Netbook"

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 20 20 00  |.X.SYSLINUX..  .|
00000010  02 00 00 00 00 f8 00 00  3f 00 20 00 3f 00 00 00  |........?. .?...|
00000020  01 4b 77 00 75 07 00 00  00 00 00 00 02 00 00 00  |.Kw.u...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 9a 2a 7e 00 4b  49 4e 47 53 54 4f 4e 20  |..).*~.KINGSTON |
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
00000100  7d 00 66 b8 aa c9 15 00  66 ba 00 00 00 00 bb 00  |}.f.....f.......|
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


=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

In another thread someone suggested using lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```

Would that work for me? Otherwise, what can I do?

Thanks

---

### Post by format_LIFE on 2010-10-28
[B]I have windows 7 ultimate and i install ubuntu 9.04 with wubi.   Everything works fine howeve i update ubuntu 10.10 and i got boot   error... when i choose ubuntu from boot screen it restart the computer..   and i didnt found solution. i just find myself... follow these steps;
1-)boot linux with live CD.(or usb) and open terminal type "sudo apt-get install lilo"
2-)sudo lilo -M /dev/sda mbr
3-) after then close terminal we finish with terminal
4-)Go Places->Computer->File System->host
5-) They are 2 file "wubildr" and "wubildr.mbr" copy that files.
6-) again Go [/B][B]Places->Computer->File   System->host->Ubuntu->disks->boot->grup-> and paste   these 2 files in here. (if you get error about permission, you should   open terminal and copy these files with sudo)
7-) restart Computer and select Ubuntu... after selecting ubuntu i got error message but your ubuntu will open..:grin:

NOTE: in windows 7, I install ubuntu with Wubi in this   directory(c:/Ubuntu).. so if you install ubuntu somewhere else you must   copy these file into where you installed ubuntu...

This solution works for everyone.. i dont know.. but it works on me..:wink:

Good luck with your problems..:razz:[/B]

---

### Post by rudasn on 2010-10-28
> 4-)Go Places->Computer->File System->host

there is no host folder in there

---

### Post by bcbc on 2010-10-28
> **rudasn said:**
> 
In another thread someone suggested using lilo:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```

Would that work for me? Otherwise, what can I do?

Thanks

Yes, but change /dev/sdb to /dev/sda as this is your internal drive. /dev/sdb is your usb
i.e.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Explanation:
You've replaced the windows bootloader in the drive MBR with grub. 
> => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.
You can use lilo in the form shown above instead of the windows bootloader or reinstall the windows bootloader using a windows repair USB/CD. (ignore errors when running those lilo commands as they will be referring to booting linux, not windows).

---

### Post by bcbc on 2010-10-28
> **format_LIFE said:**
> I have windows 7 ultimate and i install ubuntu 9.04 with wubi.   Everything works fine howeve i update ubuntu 10.10 and i got boot   error... when i choose ubuntu from boot screen it restart the computer..   and i didnt found solution. i just find myself... follow these steps;
1-)boot linux with live CD.(or usb) and open terminal type "sudo apt-get install lilo"
2-)sudo lilo -M /dev/sda mbr
3-) after then close terminal we finish with terminal
4-)Go Places->Computer->File System->host
5-) They are 2 file "wubildr" and "wubildr.mbr" copy that files.
6-) again Go [/B][B]Places->Computer->File   System->host->Ubuntu->disks->boot->grup-> and paste   these 2 files in here. (if you get error about permission, you should   open terminal and copy these files with sudo)
7-) restart Computer and select Ubuntu... after selecting ubuntu i got error message but your ubuntu will open..:grin:

NOTE: in windows 7, I install ubuntu with Wubi in this   directory(c:/Ubuntu).. so if you install ubuntu somewhere else you must   copy these file into where you installed ubuntu...

This solution works for everyone.. i dont know.. but it works on me..:wink:

Good luck with your problems..:razz:
You have a special situation because you installed 9.04 which uses grub-legacy, then you upgraded to a version of Ubuntu that uses grub2. This is not typical and cannot be applied to anyone who installed wubi from version 9.10. (I'm also not sure that your problems are completely solved based on what you have done)

The part about lilo is correct though since this particular user has got grub installed to the MBR :)

---

