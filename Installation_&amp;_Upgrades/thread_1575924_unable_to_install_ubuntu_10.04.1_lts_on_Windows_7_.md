---
title: "unable to install ubuntu 10.04.1 lts on Windows 7 x64 bit"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by sahildave on 2010-09-16
1. I have an ubuntu 10.04.1 lts installation iso image...
2. I burned it to a cd and restarted my computer..
3. When i reached to the partitions menu
   a. There was not "install side by side" option.
   b. 70 gb of windows 7 part (which is OK)and a 249 Gb of free space were shown in-spite i have this space partition in 2 drives of 100 and 149 gb in windows.
4. I wanted to install ubuntu in my F: drive (of 149 gb) but there was no method due to the above reason.

What should i do? should i download it once again.
I dont want to install with WUBI as someone told me it is not good because it slows down the computer(Is it so?)...

Pls reply...

---

### Post by odelance on 2010-09-16
Can you boot on Ubuntu CD, option "Try but don't install" and type command "sudo parted -l" and post result.

---

### Post by PJ Ritz on 2010-09-16
x

---

### Post by sahildave on 2010-09-17
> **odelance said:**
> Can you boot on Ubuntu CD, option "Try but don't install" and type command "sudo parted -l" and post result.

Thanks for Replying
Here's the result

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD3200BEVT-7 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  132MB   132MB   primary  fat16
 2      132MB   132MB   516kB   primary  fat32
 3      132MB   10.7GB  10.6GB  primary  ntfs         boot
 4      10.7GB  75.2GB  64.4GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$

---

### Post by garvinrick4 on 2010-09-17
You already have four partitions that are Primary and that is
all you get is 4 primarys per disk.

You have a fat 16 in #1 that is only 132 meg and does not have boot flag?
You have a fat 32 in #2 that is only 516 k ?
Download this file at the URL I give you, make sure to download it to DESKTOP.
Using a Ubuntu CD.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Now run this code and a text file will be on your desktop copy and paste it here.
It is a text file about your drive.
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by sahildave on 2010-09-17
> **garvinrick4 said:**
> You already have four partitions that are Primary and that is
all you get is 4 primarys per disk.

You have a fat 16 in #1 that is only 132 meg and does not have boot flag?
You have a fat 32 in #2 that is only 516 k ?
Download this file at the URL I give you, make sure to download it to DESKTOP.
Using a Ubuntu CD.

[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Now run this code and a text file will be on your desktop copy and paste it here.
It is a text file about your drive.
```
 sudo bash ~/Desktop/boot_info_script*.sh 
```

I am not able to understand this...i am a newbie....:(:confused:

all i knw is that i have these partitions, i m attaching this pic here....[http://www.picscrazy.com/view/partition]("http://www.picscrazy.com/view/partition")

wat now ?

---

### Post by sahildave on 2010-09-17
pls someone reply to this thread...plsssssssssssss....
:(

---

### Post by efflandt on 2010-09-17
You use your web browser (like Firefox) to download that file from that link while running from the live CD, but download it to Desktop instead of the default Downloads.  Then from a terminal do what he says in the Code block.  Open RESULTS.txt with gedit and copy/paste it to a reply.  But highlight that pasted text with the mouse and click on the # in the Message border to put code tags around it so it remains formatted.

Who or what partitioned and formatted your drive like it is now?  You apparently have available unallocated space, using only about 75 GB of a 320 GB drive.  But you already have 4 primary partitions (including a tiny one), so you cannot make any additional partitions on it unless you remove the tiny partition.

---

### Post by sahildave on 2010-09-18
> **efflandt said:**
> Who or what partitioned and formatted your drive like it is now?  You apparently have available unallocated space, using only about 75 GB of a 320 GB drive.  But you already have 4 primary partitions (including a tiny one), so you cannot make any additional partitions on it unless you remove the tiny partition.

the 125 MB and recovery part were made on there own when i installed windows 7 ultimate. I made three partiotions of the remaining space which is C:, D: and F:....
Is there any problem with this?

---

### Post by wilee-nilee on 2010-09-18
> **sahildave said:**
> the 125 MB and recovery part were made on there own when i installed windows 7 ultimate. I made three partiotions of the remaining space which is C:, D: and F:....
Is there any problem with this?

Your only problem appears to be the maximum=4 primary partitions. You will have to remove one to get a extended partition for Ubuntu. Now with Ubuntu or Linux distros that extended partition will actualy allow you to put as many logical partitions in there you can fit.

When a partition is inside a extended partition it is named logical, but this is a regular partition that can be formatted to run the ext that are the partitions for Linux.

Be very careful when removing any partitions, make sure you know what your doing. Feel free to ask questions.

---

### Post by sahildave on 2010-09-18
> **wilee-nilee said:**
> Your only problem appears to be the maximum=4 primary partitions. You will have to remove one to get a extended partition for Ubuntu. Now with Ubuntu or Linux distros that extended partition will actualy allow you to put as many logical partitions in there you can fit.

When a partition is inside a extended partition it is named logical, but this is a regular partition that can be formatted to run the ext that are the partitions for Linux.

Be very careful when removing any partitions, make sure you know what your doing. Feel free to ask questions.

As u can see in this pic [http://www.picscrazy.com/view/partition]("http://www.picscrazy.com/view/partition") there is only 1 primary partition and 4 simple volume....am i wrong or am i missing something....what should i do now ??? pls help....

(I actually like ur name *wilee-nilee* :p)

---

### Post by sahildave on 2010-09-18
should i try with WUBI ??? but its not good i guess....is it ?

---

### Post by wilee-nilee on 2010-09-18
> **sahildave said:**
> should i try with WUBI ??? but its not good i guess....is it ?

Simple partitions are the same as primary, primary might just be a unix/linux word I'm not sure. I'm more then sure somebody will tell us.;)

Actually wubi would be okay to try out the OS, it is not made for longterm use, but people have used it this way. There is also a thread on the forum on how to take your wubi set up and install it in a partition to dual boot in the end.

I think you said you built the partitions for windows yourself, so you know whats in them. You can remove one of them if it is not holding the operating system, but just extra data like your media, pictures....etc. It is just important to know what is in it and back up that stuff or move it to another partition. Then you can delete it.

To be honest if you want to go beyond a wubi install I would want to see the boot script that is in my signature to make sure that you have a standard set up not, one of the newer boot or partitioning schema we see on occasion that needs a little special work and somebody who knows how to deal with it.

If you just got the OEM install DVD from the manufacturer or you could get them to release a regular install dvd that would activate you could probably remove the recovery, since once you dual boot it is unlikely that you could get the recovery to trigger if you needed it. In your pic of the disc manager the boot is on C so we would just want to confirm that this is the case with the bootscript.

I'm a big fan of having a hard copy or ISO of my installs, I don't do anything but fresh installs always whether MS or Linux. The hard copy will allow you to do repairs if needed and also reinstalls.

---

### Post by sahildave on 2010-09-18
this is the RESULTS.TXT...the format and alignment of the document is not good...pls bear with it...
I am Attaching the file as well..


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 258048. But according to the info from 
                       fdisk, sda1 starts at sector 63. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda1 has 
                       20721663 sectors, but according to the info from 
                       fdisk, it has 256976 sectors.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 20979712. But according to the info from 
                       fdisk, sda2 starts at sector 257040. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       125829119 sectors, but according to the info from 
                       fdisk, it has 1007 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 146808832. But according to the info from 
                       fdisk, sda3 starts at sector 258048. According to the 
                       info in the boot sector, sda3 has 207618047 sectors, 
                       but according to the info from fdisk, it has 20721663 
                       sectors.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 354426880. But according to the info from 
                       fdisk, sda4 starts at sector 20979712. According to 
                       the info in the boot sector, sda4 has 270710783 
                       sectors, but according to the info from fdisk, it has 
                       125829119 sectors.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       257,039       256,977  de Dell Utility
/dev/sda2             257,040       258,047         1,008  42 SFS
/dev/sda3    *        258,048    20,979,711    20,721,664  42 SFS
/dev/sda4          20,979,712   146,808,831   125,829,120  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        004CD4904CD481B8                       ntfs       RECOVERY                      
/dev/sda2        E446468246465608                       ntfs       OS                            
/dev/sda3        C2F24B77F24B6EAB                       ntfs       Games                         
/dev/sda4        468AAFE08AAFCAAF                       ntfs       Others                        
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/Others            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/OS                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  c1 1f 32 02 00 00 00 00  |FILE0.....2.....|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  05 00 94 96 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  dc ee b4 d3 78 3e cb 01  dc ee b4 d3 78 3e cb 01  |....x>......x>..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  dc ee b4 d3 78 3e cb 01  |............x>..|
000000c0  dc ee b4 d3 78 3e cb 01  dc ee b4 d3 78 3e cb 01  |....x>......x>..|
000000d0  dc ee b4 d3 78 3e cb 01  00 40 00 00 00 00 00 00  |....x>...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  ff 09 00 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 a0 00 00 00 00 00  |@...............|
00000130  00 00 a0 00 00 00 00 00  00 00 a0 00 00 00 00 00  |................|
00000140  32 00 0a 00 00 0c 00 b4  b0 00 00 00 50 00 00 00  |2...........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  01 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 20 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |. ..............|
00000180  08 10 00 00 00 00 00 00  31 01 ff ff 0b 11 01 ff  |........1.......|
00000190  00 00 01 00 00 70 94 96  ff ff ff ff 00 00 00 00  |.....p..........|
000001a0  00 00 04 00 00 00 00 00  31 40 00 00 0c 00 48 85  |........1@....H.|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 00 01 00 00 70 05 00  |1............p..|
00000200
MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  52 65 20 fa 02 00 00 00  |FILE0...Re .....|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  aa 00 a6 91 00 00 00 00  10 00 00 00 60 00 00 00  |............`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  dc 6c 2c 45 52 4a cb 01  dc 6c 2c 45 52 4a cb 01  |.l,ERJ...l,ERJ..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  dc 6c 2c 45 52 4a cb 01  |.........l,ERJ..|
000000c0  dc 6c 2c 45 52 4a cb 01  dc 6c 2c 45 52 4a cb 01  |.l,ERJ...l,ERJ..|
000000d0  dc 6c 2c 45 52 4a cb 01  00 40 00 00 00 00 00 00  |.l,ERJ...@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  ff 69 00 00 00 00 00 00  |.........i......|
00000120  40 00 00 00 00 00 00 00  00 00 a0 06 00 00 00 00  |@...............|
00000130  00 00 a0 06 00 00 00 00  00 00 a0 06 00 00 00 00  |................|
00000140  32 00 67 00 00 0c 32 00  03 b9 0a 01 00 fa ff ff  |2.g...2.........|
00000150  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
00000160  00 00 00 00 00 00 00 00  04 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 50 00 00 00 00 00 00  |@........P......|
00000180  08 40 00 00 00 00 00 00  08 40 00 00 00 00 00 00  |.@.......@......|
00000190  31 01 ff ff 0b 31 04 b0  07 01 00 04 80 fa ff ff  |1....1..........|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 00 01 00 00 40 aa 00  |1............@..|
00000200


```

---

### Post by sahildave on 2010-09-18
pls tell me the steps what should i do (in simple words...i am not used to the technical terms)....thanks

---

### Post by wilee-nilee on 2010-09-18
Boot files/dirs:   /Windows/System32/winload.exe /**grldr**

Good job posting the script, I'm not familiar enough with grldr, but there are others who are so we should let them take a look. I'm am just hesitant to advise anything without being darn sure. ;)

---

### Post by sahildave on 2010-09-18
hey tell me one thing, how can i take snapshots while i install ubuntu so that i can show all the problem...

---

### Post by wilee-nilee on 2010-09-18
> **sahildave said:**
> hey tell me one thing, how can i take snapshots while i install ubuntu so that i can show all the problem...

As I said I'm not familiar with the grldr thang so I say wait until you have some qualified help.

---

### Post by phillipdhall on 2010-09-18
Somehow I lost all my motivation to help when I clicked the link to your disk manager screenshot and my screen was filled with porn. I don't appreciate it for myself, and happen to also have 6 kids here in my living room this morning.
 
I recommend going here to get yourself up to speed on linux: [http://www.linux.org/lessons/beginner/l1/lesson1a.html](http://www.linux.org/lessons/beginner/l1/lesson1a.html)
 
This is a good place to understand drive partitioning and dual booting: [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
 
Please be patient for those who offer up their time, free of charge, to help out newbies like you and me. I've found that doing my own research is more effective than asking others to simplify it specifically for me.
 
Phil

---

### Post by sahildave on 2010-09-18
> **phillipdhall said:**
> Somehow I lost all my motivation to help when I clicked the link to your disk manager screenshot and my screen was filled with porn. I don't appreciate it for myself, and happen to also have 6 kids here in my living room this morning.


Ohh sorry phil....i google "picture upload sites" and this site was the result....It was not intentional...And Thanks for your Reply...

---

### Post by phillipdhall on 2010-09-18
> **sahildave said:**
> Ohh sorry phil....i google "picture upload sites" and this site was the result....It was not intentional...And Thanks for your Reply...
 
Thank you, and I hope you are able to get your system worked out.

---

