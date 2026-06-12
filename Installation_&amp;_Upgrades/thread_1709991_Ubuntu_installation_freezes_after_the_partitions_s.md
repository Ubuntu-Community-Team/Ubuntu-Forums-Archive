---
title: "Ubuntu installation freezes after the partitions specification"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by Warriah on 2011-03-19
Hi guys.. I'm new of this forum and either of Ubuntu itself (I used Slackware for years some times ago).

I wanted to install Ubuntu 10.10 on my netbook Samsung N150 but the installation from the pendrive freezes after the partition table specification, both in the case of the manual specification and in the case of the automatic path. I (think correctly..) specified 35 GB of ext4 journ (but I tried also with ext3 journ) and 1GB of swap but when I confirm these specs the installation freeze yet at the "Searching for the file system" (I use a localized lang but I think this is a quite literal translation), when I'm asked for the time zone.. 

What's the problem with? Thank you all.

---

### Post by Dutch70 on 2011-03-19
Welcome to UF Warriah,

 Could you post a pic of your partitions from Gparted? Just use the paper clip in the toolbar to attach the pic so we can have a look at them.

---

### Post by Rubi1200 on 2011-03-19
Hi,

as well as the screenshot, please post the output of this command from the terminal (Applications > Accessories):

```
sudo fdisk -lu
```
lowercase L not 1

Thanks.

---

### Post by Warriah on 2011-03-19
Thank you for your help,

here the screens (splitted in two since the 10'' doesn't fit them all)

[[IMG]http://img846.imageshack.us/img846/705/img00991.th.jpg[/IMG]]("http://img846.imageshack.us/i/img00991.jpg/")

[[IMG]http://img638.imageshack.us/img638/3421/img00821v.th.jpg[/IMG]]("http://img638.imageshack.us/i/img00821v.jpg/")

Note: "Sconosciuto" means "Unknown" or not specified yet.

Sorry for the localization..I didn't choose English only for the keyboard layout. 

as soon as possible I'll provide also the output of the command line required.

---

### Post by Warriah on 2011-03-19
[[IMG]http://img856.imageshack.us/img856/2130/img01031.th.jpg[/IMG]]("http://img856.imageshack.us/i/img01031.jpg/")


:)

As far I know (I own the netbook since a week) in the hard-disk there are:
- two win7 partition (the usual C:\ and a backup partition D:\)
- a "hidden" partition for the recovery of Win7
- partitions eventually originated today from failed Ubuntu installations (around 34-35GB for root and 1GB for swap)


EDIT: I fixed also the two previous screenshots.

---

### Post by Rubi1200 on 2011-03-19
There seems to be a mismatch between what the Ubuntu installer is reporting as your partition layout and what fdisk is showing.

I need to check a few things and will get back to you on this as soon as I can.

---

### Post by Warriah on 2011-03-19
To make the situation more clear I checked with a software on Win7 and I can conclude

sda1 --> *: SYSTEM / 0,1 GB / NTFS (I don't have any clue on why this partition)
sda2 --> C: / 110 GB / NTFS
sda3 --> [COLOR=Red]?? does appear only with fdisk[/COLOR]..[COLOR=Red] It should be[/COLOR] [COLOR=Red]the free space[/COLOR]
sda4 --> *: SAMSUNG RECOVERY / 16 GB / NTFS 
sda5 --> D: / 80 GB / NTFS

sda6
sda7

the two with Ubuntu I'm trying to write.

---

### Post by Rubi1200 on 2011-03-19
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Warriah on 2011-03-19
NOTE: Waiting for some replies I moved the free partition to the right of D (since it originated from C partition it was between C and D). This may have affected the name sd* of the free space (the old sda4 is now sda3 and vice versa).

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   215,126,311   214,919,464   7 HPFS/NTFS
/dev/sda3         455,153,580   488,392,064    33,238,485   7 HPFS/NTFS
/dev/sda4         215,126,415   384,869,204   169,742,790   f W95 Ext d (LBA)
/dev/sda5         215,126,478   384,869,204   169,742,727   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             48     7,831,551     7,831,504   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D00A504B0A503128                       ntfs       SYSTEM                        
/dev/sda2        5EDC9D9DDC9D704F                       ntfs                                     
/dev/sda3        261A1B531A1B1EFD                       ntfs       SAMSUNG_REC                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        7E2AA9442AA8FA73                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        2D12-0CE7                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 24 00  |.X.SYSLINUX...$.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 30 00 00 00  |........?...0...|
00000020  d0 7f 77 00 d2 1d 00 00  00 00 00 00 02 00 00 00  |..w.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 e7 0c 12 2d 4e  4f 20 4e 41 4d 45 20 20  |..)...-NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 b0  64 68 00 66 ba 00 00 00  |..E}.f..dh.f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by Rubi1200 on 2011-03-19
Hi,
this is what I see from the results:

3 primary partitions with essential files needed for Windows.

1 extended partition with a logical partition.

What are you using sda5 for?

If it was me, that is where I would want to install Ubuntu.

Be aware, that the 10.10 installer has been known to cause problems, so please choose the manual partitioning option.

---

### Post by Warriah on 2011-03-19
> **Rubi1200 said:**
> Hi,
this is what I see from the results:

3 primary partitions with essential files needed for Windows.

1 extended partition with a logical partition.

What are you using sda5 for?

If it was me, that is where I would want to install Ubuntu.

Be aware, that the 10.10 installer has been known to cause problems, so please choose the manual partitioning option.

hmm..

/dev/sda1 -> SYSTEM (hidden to win)                        
/dev/sda2 -> C:                              
/dev/sda3 -> SAMSUNG_REC (hidden to win)                  
/dev/sda4
/dev/sda5  

your is a good point.. sda4 and sda5 should be the free space and the D:\ (which is empty excepting for sys/hidden files) but the order isn't that clear and the same goes for the Start/End/Id System attributes.. maybe I should try to get rid of both of them and installing Ubuntu in the NEW free space I'll get

---

### Post by Warriah on 2011-03-19
Nope.. still the same problem.

Maybe I should try with Ubuntu desktop.


EDIT: With Ubuntu desktop the same problem. (Obviously they share the same software but maybe it was a corrupted file or something like this..)


What I do:

- remove sda5
- generate (from the existing free space + additional space from sda5) a ext4+j new **logic*** partition for /
- generate a ext4+j partition for /home
- generate a swap partition


*if I generate instead a primary partition, after that I can't generate other partitions for the remaining space because it is labeled as "not usable" (maybe it is for the 4 primary partitions limit?)

---

### Post by Warriah on 2011-03-19
I'm started to think that it could be the same problem as [http://ubuntuforums.org/showthread.php?t=1594354](http://ubuntuforums.org/showthread.php?t=1594354) .. I'll try the same solution

---

### Post by Rubi1200 on 2011-03-19
It might be? I think running chkdsk and defragmenting might be a good idea too.

Make sure you have backups of important data before starting.

---

### Post by Warriah on 2011-03-19
sob, I realized again why I left Linux some years ago after long time of profitable usage..I lost a half of a day for getting a freeze of gparted while creating and extended partition. I hope that it won't damage the table or the hd itself. I'm downloading a bootable gparted different than the one from ubuntu (that freezes so often) hoping to fix the problem.

A question: can I put all the linux partitions (swap, root and home) in an extended one or in that case they won't boot?

---

### Post by Warriah on 2011-03-19
I set up perfectly the partition (1 extended with 4 logical: swap, root, home e common in fat32) but the freeze still occurs. I think I'll give another chance to an older version like the 10.04 which is said to be more stable and eventually I'll try another distribution. :(

---

### Post by Dutch70 on 2011-03-19
If 10.10 is freezing on you, 10.04 will likely freeze also. What video card do you have?

---

### Post by Warriah on 2011-03-20
It is a superstandard integrated Intel chipset.. This netbook (Samsung N150) is like the other millions out there. :p

In fact I heard (on Google results) of other guys obtaining Ubuntu running on this netbook.

I'll post the same images as before with the new configuration if the installation go screwed again.

---

### Post by Rubi1200 on 2011-03-20
Did you run chkdsk as suggested?

Was the drive ever part of a RAID array?

Have you considered trying the Alternate CD?

---

### Post by Warriah on 2011-03-20
> **Rubi1200 said:**
> Did you run chkdsk as suggested?

I think chkdsk automatically runned a couple of times while booting Windows after the various shrinking/resizing without problems, however I'll run chkdisk another time after I download the distros. 
> **Rubi1200 said:**
> 

Was the drive ever part of a RAID array?

No. (It is a netbook, I recall it)
> **Rubi1200 said:**
> 
Have you considered trying the Alternate CD?Never hard about. I googled but I think it shouldn't be necessary to use a textual based installer since I have a standard integrated video.. :(

---

### Post by Warriah on 2011-03-20
Oh dear this time it happened a very strange thing.. As I said earlier I tried with a 10.04 netbook edition. 

The order of the installation steps is a bit different with this earlier distro: I specified language, layout, time zone, then partitions and account info. I clicked on "Next" but.. The window returned to the main view (with the various apps ready to run). It didn't freeze but it didn't progress either.. After about 10 minutes admiring this sort of Ubuntu-live homepage, I rebooted.. But it seems that it was installing somewhat! It installed GRUB and at least a part of the distro (which now starts and works(?) without the pendrive inserted).

Some windows could have said "*Ehy, I'm installing*".. O.o

However I would to go back to 10.10 for two reasons:
- Since I restarted, the installation could be corrupted somewhere
- 10.04 doesn't recognize on-the-fly the wireless connection I have

If the 10.04 would have done the dirty job of good partitioning then maybe 10.10 could work this time..

PS. Maybe GNOME is revenging since I used to be a KDE-fan? XD

---

### Post by Warriah on 2011-03-20
fullsize to reduce lcd artifacts

[[IMG]http://img860.imageshack.us/img860/2452/img0110uw.th.jpg[/IMG]]("http://img860.imageshack.us/i/img0110uw.jpg/")

[[IMG]http://img717.imageshack.us/img717/8388/img0107r.th.jpg[/IMG]]("http://img717.imageshack.us/i/img0107r.jpg/")

[[IMG]http://img853.imageshack.us/img853/3262/img0108u.th.jpg[/IMG]]("http://img853.imageshack.us/i/img0108u.jpg/")

[[IMG]http://img218.imageshack.us/img218/2710/img0111ne.th.jpg[/IMG]]("http://img218.imageshack.us/i/img0111ne.jpg/")

](*,)

EDIT: I also ran chkdisk and the result is OK (no damaged sectors or any other problem).

---

### Post by Dutch70 on 2011-03-20
The only thing I can really make out of your last post is that Ubuntu is at least partially installed and you can boot into it. 
Have you tried updating it by running the following in terminal?

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Warriah on 2011-03-20
It's upgrading.. (I've had to connect via eth instead of wireless because 10.04 was unable to detect or connect to the network)

At the end of apt-get upgrading I'll have a 10.10 brand new? (I'm not so expert of packages manager since I used Slackware until now)

---

### Post by Dutch70 on 2011-03-20
Hopefully that will fix any issues you had. Including the wireless. If not, and you can't find anything via the search tool or google. Just start another thread on the subject.

---

### Post by Warriah on 2011-03-20
It seems it works almost all I'm trying to run.. I apt-updated and upgraded and now I'm upgrading the minor version through the instructions found here: [http://www.ubuntulinux.org/netbook/get-ubuntu/upgrade](http://www.ubuntulinux.org/netbook/get-ubuntu/upgrade) ..I'll post the result soon.

---

### Post by Warriah on 2011-03-20
It seems I got a 10.10 after all.. Unsure whether to put the Resolved tag in the title bar.. :D

---

### Post by Dutch70 on 2011-03-20
Great, It should be fine. Only mark it solved when you're satisfied that it's taken care of. On the other hand, this thread is titled "Ubuntu installation freezes after the partitions specification"

I think that problem is definitely taken care of. If you have any more problems, you'd want to start a new thread titled correctly anyway, but I'll leave that up to you.

Good luck, hope it all works out for you.

---

### Post by Warriah on 2011-03-20
Yep.. the only think that still doesn't work is the samsung-tools & co. packages, but it is a completely different story. Thank you for your help. ;-)

---

### Post by Dutch70 on 2011-03-20
Your quite welcome!!!

---

