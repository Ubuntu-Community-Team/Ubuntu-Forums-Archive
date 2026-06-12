---
title: "What partition to restore GRUB?"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by beesblaas on 2010-03-02
[FONT=Fixedsys]My fellow Ubuntu comrades,
I have a Win-XP and Ubuntu 9.10 on a dual boot Asus laptop,
My laptop crashed for unknown reason. It gave me some error when booting Ubuntu,
some kind of corruption, and it suggested fdisk, which did not help, now I get a Grub loading error 17.
To look at my disk, I booted from the Ubuntu install disk, and I get the following,
which is exactly the same as what it was when it was healthy, because I wrote down all the details:

[/FONT][FONT=Fixedsys][FONT=Fixedsys]ubuntu@ubuntu:~$ sudo fdisk -l

   Device   Boot      Start            End            Blocks          Id   System
/dev/sda1                                             1         1530        12289693+   1c    Hidden W95 FAT32 (LBA)
/dev/sda2   *           1531        12401        87321307+    7     HPFS/NTFS
/dev/sda3               12402        30401     144585000        f      W95 Ext'd (LBA)
/dev/sda4               16731        30401     109812276        7     HPFS/NTFS
/dev/sda5               12402        13616       9759424+   83    Linux
/dev/sda6     13617        13738              979933+   82   Linux swap / Solaris
/dev/sda7               13739        16730        24033208+   83   Linux

[Why does the forum editor screw up the spaces in above  table????]

In normal english, this is as follows:
sda1= Asus laptop Vista "recovery" partition 
sda2= Win XP
sda4= Data partition
sda5= Ubuntu partition

I have a utility disk "Super Grub Disk", (SGD) but it could not restore Grub.
From this SGD I can manually boot into hda2 (hd0,1) to boot Win-XP sucessfully.
If I try to boot with SGD into hda5, (hd0,4) which is the Linux, I get:

error 13 : Invalid or unsupported executable format
" This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD). "

So, firstly I want my boot menu back, so I can at least boot XP, because I have already proved that it boots OK manually. Then I want to fix Ubuntu.

But where to restore the GRUB, what partition? ( I used SGD to restore grub to MBR, but it failed).

advice please, thanks[/FONT]        
[/FONT]

---

### Post by darkod on 2010-03-02
Do you know how big is your root partition? You have two Linux partitions (not counting swap), sda5 and sda7. sda7 is almost 3 times larger.

Depending which one was your root partition, you can easily restore grub (and DO NOT use SGD). Boot with a cd into Try Ubuntu live desktop and execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

If actually /dev/sda7 is your root partition just replace /dev/sda5 in the first command. The second command stays the same.
Restart without the cd and you should see your grub menu allowing you to boot both ubuntu and XP.

---

### Post by beesblaas on 2010-03-02
Thanks Darkod,
My Linux root is sda5.
I tried to follow your advice but could not mount it,
although I could mount sda7. So I did
fsck /dev/sda5
it came up with endless errors which I replied "y" to fix. 

Then I could mount it, and I installed Grub.
Now it boots but ends up with the grub prompt sh:grub>

what now?, thanks

---

### Post by darkod on 2010-03-02
Hmmm. Can you run the boot info script as per these instructions and post the content of your results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by beesblaas on 2010-03-02
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,579,449    24,579,387  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     24,579,450   199,222,064   174,642,615   7 HPFS/NTFS
/dev/sda3         199,222,065   488,392,064   289,170,000   f W95 Ext d (LBA)
/dev/sda5         199,222,191   218,741,039    19,518,849  83 Linux
/dev/sda6         218,741,103   220,700,969     1,959,867  82 Linux swap / Solaris
/dev/sda7         220,701,033   268,767,449    48,066,417  83 Linux
/dev/sda4         268,767,513   488,392,064   219,624,552   7 HPFS/NTFS

/dev/sda3 overlaps with /dev/sda4

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16028794368 bytes
254 heads, 63 sectors/track, 1956 cylinders, total 31306239 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  52    31,283,909    31,283,858   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        3C98-AC5D                              vfat       RECOVERY                      
/dev/sda2        BE6C7CAD6C7C61D7                       ntfs                                     
/dev/sda4        F13201C9A94E13AA                       ntfs       DATA                          
/dev/sda5        8d010a0e-ed02-43e9-932b-a1ac3019765b   ext3                                     
/dev/sda6        9757483e-027e-4ce8-90dd-b5f89a83470b   swap                                     
/dev/sda7        f40dd62a-b982-4689-9f73-257169efd987   ext3                                     
/dev/sdb1        6E34-7E2B                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/6E34-7E2B         vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sda7        /media/f40dd62a-b982-4689-9f73-257169efd987 ext3       (rw,nosuid,nodev,uhelper=devkit)
/dev/sda2        /media/BE6C7CAD6C7C61D7  fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

=================== sda5: Location of files loaded by Grub: ===================


 106.1GB: boot/grub/core.img
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda5

00000000  a4 81 00 00 00 00 00 00  6b 79 35 4b 6b 79 35 4b  |........ky5Kky5K|
00000010  6b 79 35 4b 6b 79 35 4b  00 00 00 00 00 00 00 00  |ky5Kky5K........|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 20 f0 2b 96  00 00 00 00 00 00 00 00  |.... .+.........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  04 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000100  a4 81 00 00 00 00 00 00  6b 79 35 4b 6b 79 35 4b  |........ky5Kky5K|
00000110  6b 79 35 4b 6b 79 35 4b  00 00 00 00 00 00 00 00  |ky5Kky5K........|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 21 f0 2b 96  00 00 00 00 00 00 00 00  |....!.+.........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  04 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000200

---

### Post by beesblaas on 2010-03-02
Hi Darko,

It is now past midnight here so I'm off to bed,
maybe the partition is so stuffed that I will have to re-install Ubuntu,
but anyway, I will read what you have to say tomorrow morning. Thanks.

---

### Post by darkod on 2010-03-02
sda5: __________________________________________________   _______________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/core.img

Unfortunately, it doesn't look like you only need to reinstall grub2 to the MBR. You are also missing two boot files from sda5, /etc/fstab and /boot/grub/grub.cfg.
But on top of that, it's not even reported that the operating system is recognized as Ubuntu 9.10, it should say that.

Maybe all of this has to do with the crash and the report about corruption you mentioned. If you don't have any data you need to recover from the ubuntu install, just doing a reinstall might be best at this moment.

If you want to use the same partition you need to use Manual partitioning in step 4 and with the Change button specify the mount points and filesystems for all the ubuntu partitions.

---

### Post by beesblaas on 2010-03-03
I have managed to get my laptop now to boot straight to the WIN-XP partition.
(I removed a grub from one partition and made the sda2 partition active, the wrong one somehow got  - marked with *)

So then I tried to install Ubuntu, but GPARTED does not recognise any partition, it says my whole disk is UNALLOCATED, which is rubbish. I can see all partitions with FDISK,
and I can boot into WIN-XP. This is a BUG in GPARTED, but I cannot find a way around it.

So how do I fix this? I do not want to loose my Win-xp and data partition.

Look at my disk, see above fdisk -l output as well as this:
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 24579387, Id=1c
/dev/sda2 : start= 24579450, size=174642615, Id= 7, bootable
/dev/sda3 : start=199222065, size=289170000, Id= f
/dev/sda4 : start=268767513, size=219624552, Id= 7
/dev/sda5 : start=199222191, size= 19518849, Id=83
/dev/sda6 : start=218741103, size=  1959867, Id=82
/dev/sda7 : start=220701033, size= 48066417, Id=83


thanks

---

### Post by beesblaas on 2010-03-03
more info:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    24579449    12289693+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    24579450   199222064    87321307+   7  HPFS/NTFS
/dev/sda3       199222065   488392064   144585000    f  W95 Ext'd (LBA)
/dev/sda4       268767513   488392064   109812276    7  HPFS/NTFS
/dev/sda5       199222191   218741039     9759424+  83  Linux
/dev/sda6       218741103   220700969      979933+  82  Linux swap / Solaris
/dev/sda7       220701033   268767449    24033208+  83  Linux

---

### Post by meierfra. on 2010-03-03
> dev/sda3 overlaps with /dev/sda4

> 
Unknown BootLoader on sda5

00000000 a4 81 00 00 00 00 00 00 6b 79 35 4b 6b 79 35 4b |........ky5Kky5K|
00000010 6b 79 35 4b 6b 79 35 4b 00 00 00 00 00 00 00 00 |ky5Kky5K........|
00000020 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|

 > GPARTED does not recognise any partition, 

Your partition table is messed up.  If you are lucky, testdisk will be able to correct your partition table and you won't even have to reinstall Ubuntu:

Boot from the Ubuntu  Live CD.
Go to   "System->Administration->Software Source" and place a check mark next to "Community-maintained Open Source software(universe)"

Open a terminal and type

```

sudo apt-get update
sudo apt-get install testdisk
sudo testdisk /dev/sda

```


At the first screen press "Enter" to "Proceed"
At the next screen choose "Intel"
"Analyze",
"Quick search",
Press "Y" or "N" (depending whether you have any partition created by Vista)
Press "Enter" to continue,
select "Deeper Search" (so it does a deeper search, which could take a while)

Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let us  know exactly which partitions give you a directory listing.

---

### Post by beesblaas on 2010-03-03
Testdisk Results so far:

----------------------------------------------------------------------
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

The harddisk (250 GB / 232 GiB) seems too small! (< 262 GB / 244 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
  HPFS - NTFS          16729 254 63 31929 254 62  244188000
----------------------------------------------------------------------------------------------------------------------
COMMENT: The partition above that it says can't be recovered is sda4, the last partition.
From what I understand (I could be wrong), sda4 is a primary partition, but it wrongly falls into the extended partition (?)
-----------------------------------------------------------------------------------------------------------------------
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* FAT32 LBA                0   1  1  1529 254 63   24579387 [RECOVERY]
P HPFS - NTFS           1530   0  1 12400 254 63  174642615
L Linux                12401   2  1 13615 254 63   19518849
L Linux Swap           13616   1  1 13737 254 63    1959867
L Linux                13738   1  1 16729 254 63   48066417
P FAT32 LBA            16730   0  1 18004 254 63   20482875 [NO NAME]
------------------------------------------------------------------------------
COMMENT: I could see files in the following partitions:
1st = Asus vista "recovery" partition
2nd = Win-XP (I know this is good because I can boot to it)
3rd = see below, it is now analysing deeper:
Will post when completed.
-----------------------------------------------------------------------------------------
Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63

     Partition                  Start        End    Size in sectors

 1 * FAT32 LBA                0   1  1  1529 254 63   24579387 [RECOVERY]
 2 P HPFS - NTFS           1530   0  1 12400 254 63  174642615
 3 E extended LBA         12401   0  1 16729 254 63   69545385
 4 P FAT32 LBA            16730   0  1 18004 254 63   20482875 [NO NAME]
 5 L Linux                12401   2  1 13615 254 63   19518849
 6 L Linux Swap           13616   1  1 13737 254 63    1959867
 7 L Linux                13738   1  1 16729 254 63   48066417

It seems to me I have to delete (4)/sda4, so what I will do is first backup the data in it. Will continue tomorrow.

---

### Post by beesblaas on 2010-03-05
HAPPY ENDING! FIXED!

As I now understand, the problem with the partitions was this layout, in sequential order (my interpretation):

sda1 primary partition
sda2 primary partition
sda3 primary partition containing the following (four) logical partitions:
     sda5 logical partition of sda3
     sda6 logical partition of sda3
     sda7 logical partition of sda3
     sda4 primary partition located in space of sda3

Note: The TestDisk utility indicates Primary/Logical partitions, but fdisk not.
This is wrong, because partition 4 is a primary partition, it cannot also be a logical partition contained within partition 3, that is why Gparted reported: "Can't have overlapping partitions." 
I used TestDisk to analyse the partitions, it found the problem 
"Space conflict between the following two partitions" 3 & 4 and when I continued with TestDisk analysis it listed the corrected
partition table as follows (my interpretation):

sda1 primary partition
sda2 primary partition
sda3 primary partition containing the following (three) logical partitions:
     sda5 logical partition of sda3
     sda6 logical partition of sda3
     sda7 logical partition of sda3
sda4 primary partition

I then used **TestDisk **to write this partition table to disk.
Data on sda4 was lost (but I did back it up), and there was now unallocated space after sda4. Now Gparted could see all the partitions, and I could re-install Linux.
Once I had Linux running again, I used its tool System>Administration>**Disk Utility** to delete sda4 and then create it again using all the unallocated space.

I do not know how this problem came about, because I used the laptop for 6 months with faulty partition allocation without hassle, until one day. Possibly when I edited partitions originally with fdisk ?

I am extremely **disappointed in gparted/parted**, (actually a libparted problem), because it could not even display the faulty partition table, let alone help to fix it. Is that not the kind of thing you expect a partition editor to do? Even fdisk could display it perfectly well. It has been a bug for a very long time with libparted, and as I understand it now has a fix, but it is only due in the next release.

Thanks to everyone who helped.

---

