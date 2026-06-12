---
title: "LiveCD could not mount hard disk, and RESULT.txt file from Boot Info Script"
date: 2012-12-25
forum: Installation &amp; Upgrades
---

### Post by qiangling on 2012-12-25
I have a  Ubuntu 12.04 desktop (solo Ubuntu only), and recently due to my son's mistake, it could not reboot again. So I used my LiveCD but could not mount to the computer Hard Disk. I checked the webage and found the script ([http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net/")) and ran it and the results were listed below. Could anyone having this experience help me re buit my GRUB and rescue my computer?

THanks,
Bruce
```

##################################################
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/
sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    96,423,935    96,421,888  83 Linux
/dev/sda2          96,425,982   488,396,799   391,970,818   5 Extended
/dev/sda5         482,127,872   488,396,799     6,268,928  82 Linux swap / Solar
is
/dev/sda6          96,425,984   482,127,871   385,701,888  83 Linux


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPF
S


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6c4715ce-5422-4ca7-b5c3-549321347a1b   ext4       extra
/dev/sda5        440b48ad-6a5c-4880-8760-a93006dc730a   swap       
/dev/sda6        12cbd578-8996-4640-aa8c-6ad5675adb0a   ext4       
/dev/sdf1        249891B19891824A                       ntfs       Iomega HDD
/dev/sr0                                                iso9660    Ubuntu 12.04 
LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/extra             ext4       (rw,nosuid,nodev,uhelper=ud
isks)
/dev/sdf1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_othe
r,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  65 2a 7f da 27 1c fa 0f  63 5d 45 92 c8 aa 51 e4  |e*..'...c]E...Q.|
00000010  58 d0 e5 5f c8 56 ce ff  00 ef 3e 32 08 c1 c6 05  |X.._.V....>2....|
00000020  79 f8 89 72 27 74 75 46  8a 94 15 d9 d3 c0 c2 48  |y..r'tuF.......H|
00000030  c3 f9 91 bb 46 de 4e 63  8e 41 23 a8 3c 31 07 a1  |....F.Nc.A#.<1..|
00000040  e3 1c 7a 0c d5 2b f2 7e  62 14 b3 ef 3b 24 6e 49  |..z..+.~b...;$nI|
00000050  53 d0 91 d8 f4 aa c3 55  6f e2 56 34 54 a9 b8 f2  |S......Uo.V4T...|
00000060  c5 98 92 5d a8 51 b7 ca  df b8 c4 77 2a 9c 11 d7  |...].Q.....w*...|
00000070  e9 c8 ed e9 55 5a 7f 96  53 97 f9 4e e7 04 29 18  |....UZ..S..N..).|
00000080  3d 72 7b 03 e9 5d 15 31  2a 96 cc c9 e1 5c 62 d9  |=r{..].1*....\b.|
00000090  2e f9 26 44 fb 3a 21 05  bc a4 7b 72 48 c9 ed 8e  |..&D.:!...{rH...|
000000a0  bc 1e 0e 2b 2a 79 26 dc  0c 39 18 94 c4 fe 43 8c  |...+*y&..9....C.|
000000b0  92 38 e3 18 c8 f7 1e b5  54 31 54 ea 37 76 70 4a  |.8......T1T.7vpJ|
000000c0  8d 65 57 55 a1 ce 5d 44  b3 b5 d2 fd a4 5b ca e5  |.eWU..]D.....[..|
000000d0  d0 23 c7 bc 02 71 8c f7  3c f6 e4 f5 fa 57 8a f8  |.#...q..<....W..|
000000e0  b6 dd 95 4b cd 16 e8 5d  82 66 09 b1 f2 80 79 2b  |...K...].f....y+|
000000f0  8e 39 24 7e 3d 2b 7a f2  8f 26 c7 5d 17 3f ac 2e  |.9$~=+z..&.].?..|
00000100  56 7c b5 e2 db 25 12 36  db 79 97 7c 66 39 a5 89  |V|...%.6.y.|f9..|
00000110  40 4d b9 18 f7 04 74 24  56 16 80 1a 19 e3 91 57  |@M....t$V......W|
00000120  0f bc 85 c8 52 36 e0 e0  90 7f 0e 3f c6 be 62 b4  |....R6.....?..b.|
00000130  dc a4 b5 3e 9a a6 94 9e  ba 9f 53 f8 1e e0 65 52  |...>......S...eR|
00000140  46 89 a3 4c ab 96 ca c8  a0 e7 9c 70 00 27 ae 3f  |F..L.......p.'.?|
00000150  91 af 6a b4 88 c6 22 97  73 65 83 29 73 1e 08 04  |..j...".se.)s...|
00000160  f1 c7 71 82 2b 6a 72 b2  b3 3c 85 cd 15 7b 5c b7  |..q.+jr..<...{\.|
00000170  2a f9 67 6f 9f 1c eb 1b  95 13 44 15 83 b0 f5 ed  |*.go......D.....|
00000180  ec 7b 55 2b 94 68 96 48  bc a6 96 32 01 91 c3 e1  |.{U+.h.H...2....|
00000190  40 6e bc 75 ca fa f4 e9  5e ad 17 17 6d 4e 7a a9  |@n.u....^...mNz.|
000001a0  cf c8 42 24 58 3c a7 1b  d1 10 3a 1d 8c 1b 27 df  |..B$X<....:...'.|
000001b0  a9 c0 f5 e3 ae 3b 9a f3  3f 1d a1 93 4e 99 00 fe  |.....;..?...N...|
000001c0  ff ff 82 fe ff ff 02 58  fd 16 00 a8 5f 00 00 fe  |.......X...._...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 58 fd 16 00 00  |...........X....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
  No volume groups found
mdadm: No arrays found in config file or automatically

ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ more RE*
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        
Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/
sda6,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdf1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    96,423,935    96,421,888  83 Linux
/dev/sda2          96,425,982   488,396,799   391,970,818   5 Extended
/dev/sda5         482,127,872   488,396,799     6,268,928  82 Linux swap / Solar
is
/dev/sda6          96,425,984   482,127,871   385,701,888  83 Linux


Drive: sdf _____________________________________________________________________

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPF
S


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6c4715ce-5422-4ca7-b5c3-549321347a1b   ext4       extra
/dev/sda5        440b48ad-6a5c-4880-8760-a93006dc730a   swap       
/dev/sda6        12cbd578-8996-4640-aa8c-6ad5675adb0a   ext4       
/dev/sdf1        249891B19891824A                       ntfs       Iomega HDD
/dev/sr0                                                iso9660    Ubuntu 12.04 
LTS i386

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/extra             ext4       (rw,nosuid,nodev,uhelper=ud
isks)
/dev/sdf1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_othe
r,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  65 2a 7f da 27 1c fa 0f  63 5d 45 92 c8 aa 51 e4  |e*..'...c]E...Q.|
00000010  58 d0 e5 5f c8 56 ce ff  00 ef 3e 32 08 c1 c6 05  |X.._.V....>2....|
00000020  79 f8 89 72 27 74 75 46  8a 94 15 d9 d3 c0 c2 48  |y..r'tuF.......H|
00000030  c3 f9 91 bb 46 de 4e 63  8e 41 23 a8 3c 31 07 a1  |....F.Nc.A#.<1..|
00000040  e3 1c 7a 0c d5 2b f2 7e  62 14 b3 ef 3b 24 6e 49  |..z..+.~b...;$nI|
00000050  53 d0 91 d8 f4 aa c3 55  6f e2 56 34 54 a9 b8 f2  |S......Uo.V4T...|
00000060  c5 98 92 5d a8 51 b7 ca  df b8 c4 77 2a 9c 11 d7  |...].Q.....w*...|
00000070  e9 c8 ed e9 55 5a 7f 96  53 97 f9 4e e7 04 29 18  |....UZ..S..N..).|
00000080  3d 72 7b 03 e9 5d 15 31  2a 96 cc c9 e1 5c 62 d9  |=r{..].1*....\b.|
00000090  2e f9 26 44 fb 3a 21 05  bc a4 7b 72 48 c9 ed 8e  |..&D.:!...{rH...|
000000a0  bc 1e 0e 2b 2a 79 26 dc  0c 39 18 94 c4 fe 43 8c  |...+*y&..9....C.|
000000b0  92 38 e3 18 c8 f7 1e b5  54 31 54 ea 37 76 70 4a  |.8......T1T.7vpJ|
000000c0  8d 65 57 55 a1 ce 5d 44  b3 b5 d2 fd a4 5b ca e5  |.eWU..]D.....[..|
000000d0  d0 23 c7 bc 02 71 8c f7  3c f6 e4 f5 fa 57 8a f8  |.#...q..<....W..|
000000e0  b6 dd 95 4b cd 16 e8 5d  82 66 09 b1 f2 80 79 2b  |...K...].f....y+|
000000f0  8e 39 24 7e 3d 2b 7a f2  8f 26 c7 5d 17 3f ac 2e  |.9$~=+z..&.].?..|
00000100  56 7c b5 e2 db 25 12 36  db 79 97 7c 66 39 a5 89  |V|...%.6.y.|f9..|
00000110  40 4d b9 18 f7 04 74 24  56 16 80 1a 19 e3 91 57  |@M....t$V......W|
00000120  0f bc 85 c8 52 36 e0 e0  90 7f 0e 3f c6 be 62 b4  |....R6.....?..b.|
00000130  dc a4 b5 3e 9a a6 94 9e  ba 9f 53 f8 1e e0 65 52  |...>......S...eR|
00000140  46 89 a3 4c ab 96 ca c8  a0 e7 9c 70 00 27 ae 3f  |F..L.......p.'.?|
00000150  91 af 6a b4 88 c6 22 97  73 65 83 29 73 1e 08 04  |..j...".se.)s...|
00000160  f1 c7 71 82 2b 6a 72 b2  b3 3c 85 cd 15 7b 5c b7  |..q.+jr..<...{\.|
00000170  2a f9 67 6f 9f 1c eb 1b  95 13 44 15 83 b0 f5 ed  |*.go......D.....|
00000180  ec 7b 55 2b 94 68 96 48  bc a6 96 32 01 91 c3 e1  |.{U+.h.H...2....|
00000190  40 6e bc 75 ca fa f4 e9  5e ad 17 17 6d 4e 7a a9  |@n.u....^...mNz.|
000001a0  cf c8 42 24 58 3c a7 1b  d1 10 3a 1d 8c 1b 27 df  |..B$X<....:...'.|
000001b0  a9 c0 f5 e3 ae 3b 9a f3  3f 1d a1 93 4e 99 00 fe  |.....;..?...N...|
000001c0  ff ff 82 fe ff ff 02 58  fd 16 00 a8 5f 00 00 fe  |.......X...._...|
000001d0  ff ff 05 fe ff ff 01 00  00 00 01 58 fd 16 00 00  |...........X....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
  No volume groups found
mdadm: No arrays found in config file or automatically

ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ 
ubuntu@ubuntu:~/Downloads$ more RE*
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => No boot loader is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 
--More--(11%)
Most commands optionally preceded by integer argument k.  Defaults in brackets.
Star (*) indicates argument becomes new default.
-------------------------------------------------------------------------------
<space>                 Display next k lines of text [current screen size]
z                       Display next k lines of text [current screen size]*
<return>                Display next k lines of text [1]*
d or ctrl-D             Scroll k lines [current scroll size, initially 11]*
q or Q or <interrupt>   Exit from more
s                       Skip forward k lines of text [1]
f                       Skip forward k screenfuls of text [1]
b or ctrl-B             Skip backwards k screenfuls of text [1]
'                       Go to place where previous search started
=                       Display current line number
/<regular expression>   Search for kth occurrence of regular expression [1]
n                       Search for kth occurrence of last r.e [1]
!<cmd> or :!<cmd>       Execute <cmd> in a subshell
v                       Start up /usr/bin/vi at current line
ctrl-L                  Redraw screen
:n                      Go to kth next file [1]
:p                      Go to kth previous file [1]
:f                      Display current file name and line number
.                       Repeat previous command
-------------------------------------------------------------------------------

...skipping 23 lines
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    96,423,935    96,421,888  83 Linux
/dev/sda2          96,425,982   488,396,799   391,970,818   5 Extended
/dev/sda5         482,127,872   488,396,799     6,268,928  82 Linux swap / Solar
is
/dev/sda6          96,425,984   482,127,871   385,701,888  83 Linux


Drive: sdf _____________________________________________________________________


...skipping one line
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPF
S


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6c4715ce-5422-4ca7-b5c3-549321347a1b   ext4       extra
/dev/sda5        440b48ad-6a5c-4880-8760-a93006dc730a   swap       
/dev/sda6        12cbd578-8996-4640-aa8c-6ad5675adb0a   ext4       
/dev/sdf1        249891B19891824A                       ntfs       Iomega HDD
/dev/sr0                                                iso9660    Ubuntu 12.04 
LTS i386

================================ Mount points: =================================

...skipping one line
Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/extra             ext4       (rw,nosuid,nodev,uhelper=ud
isks)
/dev/sdf1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_othe
r,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  65 2a 7f da 27 1c fa 0f  63 5d 45 92 c8 aa 51 e4  |e*..'...c]E...Q.|
00000010  58 d0 e5 5f c8 56 ce ff  00 ef 3e 32 08 c1 c6 05  |X.._.V....>2....|
00000020  79 f8 89 72 27 74 75 46  8a 94 15 d9 d3 c0 c2 48  |y..r'tuF.......H|
00000030  c3 f9 91 bb 46 de 4e 63  8e 41 23 a8 3c 31 07 a1  |....F.Nc.A#.<1..|
00000040  e3 1c 7a 0c d5 2b f2 7e  62 14 b3 ef 3b 24 6e 49  |..z..+.~b...;$nI|
00000050  53 d0 91 d8 f4 aa c3 55  6f e2 56 34 54 a9 b8 f2  |S......Uo.V4T...|
00000060  c5 98 92 5d a8 51 b7 ca  df b8 c4 77 2a 9c 11 d7  |...].Q.....w*...|
00000070  e9 c8 ed e9 55 5a 7f 96  53 97 f9 4e e7 04 29 18  |....UZ..S..N..).|
00000080  3d 72 7b 03 e9 5d 15 31  2a 96 cc c9 e1 5c 62 d9  |=r{..].1*....\b.|

...skipping 23 lines
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
  No volume groups found
mdadm: No arrays found in config file or automatically
sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 
--More--(11%)
Most commands optionally preceded by integer argument k.  Defaults in brackets.
Star (*) indicates argument becomes new default.
-------------------------------------------------------------------------------
<space>                 Display next k lines of text [current screen size]
z                       Display next k lines of text [current screen size]*
<return>                Display next k lines of text [1]*
d or ctrl-D             Scroll k lines [current scroll size, initially 11]*
q or Q or <interrupt>   Exit from more
s                       Skip forward k lines of text [1]
f                       Skip forward k screenfuls of text [1]
b or ctrl-B             Skip backwards k screenfuls of text [1]
'                       Go to place where previous search started
=                       Display current line number
/<regular expression>   Search for kth occurrence of regular expression [1]
n                       Search for kth occurrence of last r.e [1]
!<cmd> or :!<cmd>       Execute <cmd> in a subshell
v                       Start up /usr/bin/vi at current line
ctrl-L                  Redraw screen
:n                      Go to kth next file [1]
:p                      Go to kth previous file [1]
:f                      Display current file name and line number
.                       Repeat previous command
-------------------------------------------------------------------------------

...skipping 23 lines
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048    96,423,935    96,421,888  83 Linux
/dev/sda2          96,425,982   488,396,799   391,970,818   5 Extended
/dev/sda5         482,127,872   488,396,799     6,268,928  82 Linux swap / Solar
is
/dev/sda6          96,425,984   482,127,871   385,701,888  83 Linux


Drive: sdf _____________________________________________________________________


...skipping one line
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdf1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPF
S


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6c4715ce-5422-4ca7-b5c3-549321347a1b   ext4       extra
/dev/sda5        440b48ad-6a5c-4880-8760-a93006dc730a   swap       
/dev/sda6        12cbd578-8996-4640-aa8c-6ad5675adb0a   ext4       
/dev/sdf1        249891B19891824A                       ntfs       Iomega HDD
/dev/sr0                                                iso9660    Ubuntu 12.04 
LTS i386

================================ Mount points: =================================

...skipping one line
Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/extra             ext4       (rw,nosuid,nodev,uhelper=ud
isks)
/dev/sdf1        /media/Iomega HDD        fuseblk    (rw,nosuid,nodev,allow_othe
r,default_permissions,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  65 2a 7f da 27 1c fa 0f  63 5d 45 92 c8 aa 51 e4  |e*..'...c]E...Q.|
00000010  58 d0 e5 5f c8 56 ce ff  00 ef 3e 32 08 c1 c6 05  |X.._.V....>2....|
00000020  79 f8 89 72 27 74 75 46  8a 94 15 d9 d3 c0 c2 48  |y..r'tuF.......H|
00000030  c3 f9 91 bb 46 de 4e 63  8e 41 23 a8 3c 31 07 a1  |....F.Nc.A#.<1..|
00000040  e3 1c 7a 0c d5 2b f2 7e  62 14 b3 ef 3b 24 6e 49  |..z..+.~b...;$nI|
00000050  53 d0 91 d8 f4 aa c3 55  6f e2 56 34 54 a9 b8 f2  |S......Uo.V4T...|
00000060  c5 98 92 5d a8 51 b7 ca  df b8 c4 77 2a 9c 11 d7  |...].Q.....w*...|
00000070  e9 c8 ed e9 55 5a 7f 96  53 97 f9 4e e7 04 29 18  |....UZ..S..N..).|
00000080  3d 72 7b 03 e9 5d 15 31  2a 96 cc c9 e1 5c 62 d9  |=r{..].1*....\b.|

...skipping 23 lines
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 

=============================== StdErr Messages: ===============================

xz: (stdin): Compressed data is corrupt
  No volume groups found
mdadm: No arrays found in config file or automatically
```

---

### Post by oldfred on 2012-12-25
It looks like script cannot mount sda6 which grub is trying to boot from. I then assume that is you main install.

Try this from liveCD.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

---

