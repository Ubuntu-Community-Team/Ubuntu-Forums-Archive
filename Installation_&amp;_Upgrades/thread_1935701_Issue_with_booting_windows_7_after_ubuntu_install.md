---
title: "Issue with booting windows 7 after ubuntu install"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by Rankin1 on 2012-03-04
Hey everyone 

Im having a really stressful day here :(

Basically I created a partition for ubuntu (12.04) which went fine, I then installed ubuntu into the partition from a live CD which also went fine. upon reboot though after the installation my laptop booted straight into windows 7 but failed stating that there was an error. It then recommended for me to go into startup recovery which I proceeded to do. All the options failed to do anything, all of them stating some non specific or helpful issue (please ask if you want to know them word for word). I attempted using a recovery cd for windows 7 as well which proved to achieve the same result as the startup recovery. So now I am stuck without a proper OS and just running off of a live CD which has the options for booting into "PartedMagic" as well If thats any help.

Please don't hesitate to insult my abilities :D and please feel free to ask any questions, Im relatively capable with terminal so you dont have to dumb things down to much.

Any help would be much appreciated 

cheers

---

### Post by vidtek on 2012-03-04
> **Rankin1 said:**
> Hey everyone 

Im having a really stressful day here :(

Basically I created a partition for ubuntu (12.04) which went fine, I then installed ubuntu into the partition from a live CD which also went fine. upon reboot though after the installation my laptop booted straight into windows 7 but failed stating that there was an error. It then recommended for me to go into startup recovery which I proceeded to do. All the options failed to do anything, all of them stating some non specific or helpful issue (please ask if you want to know them word for word). I attempted using a recovery cd for windows 7 as well which proved to achieve the same result as the startup recovery. So now I am stuck without a proper OS and just running off of a live CD which has the options for booting into "PartedMagic" as well If thats any help.

Please don't hesitate to insult my abilities :D and please feel free to ask any questions, Im relatively capable with terminal so you dont have to dumb things down to much.

Any help would be much appreciated 

cheers

Rankin-

Hopefully nobody here would insult your abilities. Everyone's a noobie at first.

Have a look at this thread here:
  [http://ubuntuforums.org/showthread.php?t=1830554](http://ubuntuforums.org/showthread.php?t=1830554)

it may help you solve some issues, and give you some ideas.

Best of luck, Tony.

---

### Post by presence1960 on 2012-03-04
We need to see exactly what you have on that machine so do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Boot to the desktop, when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded unzip & move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by Rankin1 on 2012-03-05
> **vidtek said:**
> Rankin-

Have a look at this thread here:
  [http://ubuntuforums.org/showthread.php?t=1830554](http://ubuntuforums.org/showthread.php?t=1830554)

it may help you solve some issues, and give you some ideas.

Best of luck, Tony.

Thanks very much, not really the issue as what im having but still some very useful info cheers

---

### Post by Rankin1 on 2012-03-05
> **presence1960 said:**
> We need to see exactly what you have on that machine so do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Boot to the desktop, when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded unzip & move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Yeah probably should have included this haha. 

here it is :

 ```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   According to the info in the boot sector, sda2 starts 
                       at sector 409600. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       892981240 sectors, but according to the info from 
                       fdisk, it has 407551 sectors.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   893,390,847   892,981,248  42 SFS
/dev/sda4         893,390,848   976,773,119    83,382,272  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7ED0180BD017C873                       ntfs       SYSTEM
/dev/sda2        C4621BEC621BE24A                       ntfs       
/dev/sda3        11cdfb71-7085-4bed-adaf-95199c12113c   ext4       
/dev/sda4        36fb00f6-ab37-45b5-b8a9-7e3d73f14b51   ext4       
/dev/sda5        4A52-2170                              vfat       HP_TOOLS
/dev/sr0                                                iso9660    LUDDVD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /media/C4621BEC621BE24A  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda4        /mnt                     ext4       (rw,commit=0,commit=0)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  8c 4b 68 24 05 00 00 00  |FILE0....Kh$....|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  07 00 00 00 00 00 00 00  |................|
00000030  4f 18 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |O...........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  bb 34 fb 1a 3a 4e cc 01  bb 34 fb 1a 3a 4e cc 01  |.4..:N...4..:N..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  bb 34 fb 1a 3a 4e cc 01  |.........4..:N..|
000000c0  bb 34 fb 1a 3a 4e cc 01  bb 34 fb 1a 3a 4e cc 01  |.4..:N...4..:N..|
000000d0  bb 34 fb 1a 3a 4e cc 01  00 00 20 09 00 00 00 00  |.4..:N.... .....|
000000e0  00 00 20 09 00 00 00 00  06 00 00 00 00 00 00 00  |.. .............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  bf 17 02 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 7c 21 00 00 00 00  |@.........|!....|
00000130  00 00 7c 21 00 00 00 00  00 00 7c 21 00 00 00 00  |..|!......|!....|
00000140  33 40 a6 00 00 00 0c 43  80 71 01 03 ef b0 02 00  |3@.....C.q......|
00000150  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 06 00  |....P.....@.....|
00000160  00 00 00 00 00 00 00 00  11 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 20 01 00 00 00 00 00  |@........ ......|
00000180  00 19 01 00 00 00 00 00  00 19 01 00 00 00 00 00  |................|
00000190  31 0d cf 35 07 31 05 28  48 08 00 06 80 fa ff ff  |1..5.1.(H.......|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
*
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 4f 18  |..............O.|
00000200

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")
```


sda2 is my system partition for windows, sda3 is where all my files are, sda4 is my ubuntu is

cheers for the time your putting in to help me

---

### Post by oldfred on 2012-03-05
Could you please rerun boot script with the git version. Gert has been looking for an example of the error you have and wants to confirm it is fixed. You may have grldr file in Windows that has triggered the error. But do not delete it until rerunning script.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

@presence1960
Glad to see you back posting. For those who may not know I learned about, and how to use boot script from presence1960 and meierfra one of the authors of the boot info script. meierfra used to post new version of script with just about every correction. Gert Hulselmans is now updating script for grub1.99 changes, but seems to want to have all fixes before releasing it as a new version.

---

### Post by Rankin1 on 2012-03-05
> **oldfred said:**
> Could you please rerun boot script with the git version. Gert has been looking for an example of the error you have and wants to confirm it is fixed. You may have grldr file in Windows that has triggered the error. But do not delete it until rerunning script.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```@presence1960

Ok this is what I got:

```
                   Boot Info Script 0.60      [17 May 2011]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 409600. But according to the info from 
                       fdisk, sda2 starts at sector 2048. The info in boot 
                       sector on the starting sector of the MFT is wrong. 
                       According to the info in the boot sector, sda2 has 
                       892981240 sectors, but according to the info from 
                       fdisk, it has 407551 sectors.
    Operating System:  Windows 7
    Boot files:        /grldr /bootmgr /boot/BCD 
                       /Windows/System32/winload.exe /grldr

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu precise (development 
                       branch)
    Boot files:        /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   893,390,847   892,981,248  42 SFS
/dev/sda4         893,390,848   976,773,119    83,382,272  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        7ED0180BD017C873                       ntfs       SYSTEM
/dev/sda2        C4621BEC621BE24A                       ntfs       
/dev/sda3        11cdfb71-7085-4bed-adaf-95199c12113c   ext4       
/dev/sda4        36fb00f6-ab37-45b5-b8a9-7e3d73f14b51   ext4       
/dev/sda5        4A52-2170                              vfat       HP_TOOLS
/dev/sr0                                                iso9660    LUDDVD

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=36fb00f6-ab37-45b5-b8a9-7e3d73f14b51 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/vmlinuz-3.2.0-2-generic                   1
               =                vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

MFT Sector of sda2

00000000  46 49 4c 45 30 00 03 00  8c 4b 68 24 05 00 00 00  |FILE0....Kh$....|
00000010  01 00 01 00 38 00 01 00  a8 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  07 00 00 00 00 00 00 00  |................|
00000030  4f 18 00 00 00 00 00 00  10 00 00 00 60 00 00 00  |O...........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  bb 34 fb 1a 3a 4e cc 01  bb 34 fb 1a 3a 4e cc 01  |.4..:N...4..:N..|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  bb 34 fb 1a 3a 4e cc 01  |.........4..:N..|
000000c0  bb 34 fb 1a 3a 4e cc 01  bb 34 fb 1a 3a 4e cc 01  |.4..:N...4..:N..|
000000d0  bb 34 fb 1a 3a 4e cc 01  00 00 20 09 00 00 00 00  |.4..:N.... .....|
000000e0  00 00 20 09 00 00 00 00  06 00 00 00 00 00 00 00  |.. .............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 50 00 00 00  01 00 40 00 00 00 01 00  |....P.....@.....|
00000110  00 00 00 00 00 00 00 00  bf 17 02 00 00 00 00 00  |................|
00000120  40 00 00 00 00 00 00 00  00 00 7c 21 00 00 00 00  |@.........|!....|
00000130  00 00 7c 21 00 00 00 00  00 00 7c 21 00 00 00 00  |..|!......|!....|
00000140  33 40 a6 00 00 00 0c 43  80 71 01 03 ef b0 02 00  |3@.....C.q......|
00000150  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 06 00  |....P.....@.....|
00000160  00 00 00 00 00 00 00 00  11 00 00 00 00 00 00 00  |................|
00000170  40 00 00 00 00 00 00 00  00 20 01 00 00 00 00 00  |@........ ......|
00000180  00 19 01 00 00 00 00 00  00 19 01 00 00 00 00 00  |................|
00000190  31 0d cf 35 07 31 05 28  48 08 00 06 80 fa ff ff  |1..5.1.(H.......|
000001a0  ff ff ff ff 00 00 00 00  ff ff ff ff 00 00 00 00  |................|
*
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 4f 18  |..............O.|
00000200

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
```

---

### Post by oldfred on 2012-03-05
Partitions look well messed up. Dynamic partitions, but one list shows sda3 as SFS and blkid shows it as Linux?? And you do not show extended partition, but again blkid shows a sda5? So it may not be easy to repair.

Before doing anything I would back up partition table using Ubuntu liveCD. But dynamic partitions have other data inside the dynamic partitions.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

If you can see any of the partitions from Ubuntu you also want to backup anything you might want to save, if you have not backed up yet. 

You are showing SFS or dynamic partitions in sda2 & sda3. That is a Windows format that is used when you try to create in Windows more than the 4 primary partitions MBR allows.

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Several users have used this, it has a liveCD download to use:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.

Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted with EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Windows partition boot sector or PBR has to have the same partition start & end and some other boot info that the partition table has. The Windows repair tools or a Windows repairCD is probably required to fixBoot or repair PBR.

---

### Post by Rankin1 on 2012-03-05
Ok thats fine. Just to clarify which partition or partitions should I be changing from dynamic to basic?

---

### Post by Mark Phelps on 2012-03-06
Couple of points you should know ...

First, Minitool Wizard Pro Edition costs money -- it is not free.  The free version (from what I read) does not do the Dynamic-to-Basic conversions.

Second, the Release Notes for Ubuntu 12.04 for this BETA version clearly indicate that this version has "issues" and is only for Developers and Testers.  Which of these are you?

If you are neither, then do NOT install 12.04, but instead, go with 11.10 -- or wait until 12.04 is out in April.

---

### Post by Rankin1 on 2012-03-06
> **Mark Phelps said:**
> Couple of points you should know ...

First, Minitool Wizard Pro Edition costs money -- it is not free.  The free version (from what I read) does not do the Dynamic-to-Basic conversions.

Second, the Release Notes for Ubuntu 12.04 for this BETA version clearly indicate that this version has "issues" and is only for Developers and Testers.  Which of these are you?

If you are neither, then do NOT install 12.04, but instead, go with 11.10 -- or wait until 12.04 is out in April.

little bit late for that now isn't it, but thanks for the warning about the minitool.  Got any other suggestions for a partitioning boot tool? constructive help is always useful.

Cheers

---

### Post by Mark Phelps on 2012-03-06
> **Rankin1 said:**
> Got any other suggestions for a partitioning boot tool? constructive help is always useful.

Cheers

Oldfred already mentioned EASEUS Partition Master.  I would hunt that down and see if their FREE version supports Dynamic-to-Basic conversions.

If it doesn't, then I know of no FREE MS Windows tools that will do the conversions you need.  MS does allow you to do this with their native tools -- but those presume EMPTY partitions, and are likely to result in data loss.

Until you do that conversion, you now have unusable partitions -- outside of MS Windows.  So, no Linux partitioning tool is going to do you any good.

---

### Post by Rankin1 on 2012-03-06
> **Mark Phelps said:**
> Oldfred already mentioned EASEUS Partition Master.  I would hunt that down and see if their FREE version supports Dynamic-to-Basic conversions.


Until you do that conversion, you now have unusable partitions -- outside of MS Windows.  So, no Linux partitioning tool is going to do you any good.

Ok I found out that yes I would have to purchase Easus as well to, so thats kinds annoying :( 

can I not just do what this guy has done?

[http://ubuntuforums.org/showthread.php?t=1675420&page=2](http://ubuntuforums.org/showthread.php?t=1675420&page=2)

I have parted magic and have backed up my files.
Also if I was going to convert from dynamic to basic which partition would I be doing it to?

cheers

---

### Post by oldfred on 2012-03-06
One place says sda2 & sda3 are SFS. And does not show sda1 or sda5. The other says you have a sda1 and sda5 and sda3 is Linux not NTFS. I have never seen those differences. I might pay to see what all the other tools like testdisk or other tools find. 

Dynamic partitions are logical and can overlap physical. If logical is the same as physical then I think the conversion back is more straightforward.

I thought when I looked the free version of EASEUS would work. I did not know the free version of MiniTool would not.

I have seen users just use Testdisk and some other tools, but again that must be when it is more straightforward.

Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Not sure if in "free" version, but older version had it & was free see 4.2:
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)
[http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm](http://www.hdd-tool.com/partition-manager/change-partition-type-logical-to-primary-without-data-losing.htm)
[http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/](http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/)

---

### Post by presence1960 on 2012-03-07
> **oldfred said:**
> Could you please rerun boot script with the git version. Gert has been looking for an example of the error you have and wants to confirm it is fixed. You may have grldr file in Windows that has triggered the error. But do not delete it until rerunning script.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

@presence1960
Glad to see you back posting. For those who may not know I learned about, and how to use boot script from presence1960 and meierfra one of the authors of the boot info script. meierfra used to post new version of script with just about every correction. Gert Hulselmans is now updating script for grub1.99 changes, but seems to want to have all fixes before releasing it as a new version.

Hi oldfred. Good to "see" you too. Sorry for the delay as I have been busy with my daughter, lots of stuff for school. BTW she is 9 and dual boots Ubuntu & windows 7. In school she uses OSX. Not bad for a 9 year old.

We have a veritable mess on this OP's partition table. No easy fix. If it were me I would back up my files and start over. +1 on what Mark said about 12.04...don't want to discourage people from testing alpha & beta versions however with that being said if you are not proficient with troubleshooting, partitioning & OS installtions I would stay away until the final version is released.

P.S. meierfra is truly a godsend. Have had some PMs with him in the past which have yielded me tremendous insight not just about linux but windows as well. I hope he is well and still active here.

---

### Post by Rankin1 on 2012-03-08
> **presence1960 said:**
> We have a veritable mess on this OP's partition table. No easy fix. If it were me I would back up my files and start over.
 
This is probably my preferable option, but I really have no clue how to go about it. Should I just format all of my partitions and get a windows install disk and write over my windows install?

---

