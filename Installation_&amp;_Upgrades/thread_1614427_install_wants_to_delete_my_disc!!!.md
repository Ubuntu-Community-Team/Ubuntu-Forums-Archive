---
title: "install wants to delete my disc???!!!"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by john1066 on 2010-11-05
So after getting UNE 10.10 installed on my Acer laptop and working in dual boot mode (also have W7 there) I felt confident enough to install it on my little Asus netbook. So got to the screen where I can choose to run ubuntu from my usb or to install. I choose install after all  (as the blurb says) I can run alongside my existing system (again W7). So then I get the fright of my life - I get two options for install - either delete and reformat my disc or advanced (=fiddle about with partitions = big trouble as far as I am concerned). So my question is - how on earth do you get UNE installed without being an expert and without getting your entire disc reformatted and losing W7?

John

PS - my Acer has two discs and luckily I installed on the non-W7 one. I suspect that I would have been in deep trouble otherwise.

---

### Post by wilee-nilee on 2010-11-05
You need to shrink the W7 partition with its disk manager first; leaving a open space for the Ubuntu install.

Just to be safe here though boot that thumb or cd again on the computer and take a screenshot of gparted so we can see whats actually there.

---

### Post by garvinrick4 on 2010-11-05
> **wilee-nilee said:**
> You need to shrink the W7 partition with its disk manager first; leaving a open space for the Ubuntu install.

Just to be safe here though boot that thumb or cd again on the computer and take a screenshot of gparted so we can see whats actually there. Hello Mr. Willee do they not have a install side by side anymore and it takes about 50% for each and is simple for the new users to install with. Of course defrag windows 7 a couple of times if it has been in use and remember to put grub in sda and done. I use manual so much I should look, but they could not have taken that option out.

---

### Post by wilee-nilee on 2010-11-05
> **garvinrick4 said:**
> Hello Mr. Willee do they not have a install side by side anymore and it takes about 50% for each and is simple for the new users to install with. Of course defrag windows 7 a couple of times if it has been in use and remember to put grub in sda and done. I use manual so much I should look, but they could not have taken that option out.

Yeah its there but it is different looking in Maverick. Not sure if it is there though if a MS OS is there covering the whole disc, at least at times people post with this conundrum.

I always just on the safe side advise the W7 partitioner. This gets people to do the resizing and rebooted to make sure everything is working then install.

What we do see on occasion it seems though is a new user that doesn't really know what their doing and just try the alongside option which resizes the W7 and creates space for Linux, this does cause problems it seems on occasion. I just never advise that route because many who come on here have no backups and just are acting before thinking.

You may notice that I try to be systematic in my analysis of a problem, I.E getting all the information, I just don't want to be part of anybody losing their setup, so I use the tools available. Of course I am limited in my own toolset as to what I can help with, so I try to stop when it gets to that point.

To be honest Ubuntu installs seem easy to us regular users. But to a person not familiar with partitioning and uncomfortable with a little cli I think it may be quite confusing. I can appreciate the want of the Ubuntu developers to have a easy install and promote it that way, but I think it is misleading. It is misleading because we all have a different definition of easy to install. I think Arch is a easy install but I'm biased I know how to do it.;)

---

### Post by garvinrick4 on 2010-11-05
Just ran an install and quit after choosing side by side and it is very neatly done. Will show how much
is Windows how much is Ubuntu and you can slide to take more or less for ubuntu and shows where grub is going on same page. (Did not show logical partitions but most new comers will not no what they are anyway.)
Is just about as easy as you can make it. (Matter of fact easier than Anaconda that all redhat offshoots use.)
So John1066  go ahead and remember you can quit at anytime before the last step when you say INSTALL.
It will tell you what it is doing to your drive.
Do defrag Windows 7 a couple of times to tidy up your drive if you have used it.

---

### Post by garvinrick4 on 2010-11-05
Yes I understand that willee-nillee it would be terrible to get the I wiped out my whole drive post.
It can be one of those 23 post threads if I start getting involved with newcomer on how to partition and
how to install and so on, very hard on them, the manual install, I remember myself. Each a little to their
own but I have to hope Ubuntu keeps making it easier and easier to get more new users not to screw up
first install. They do not come back it seems. I just cannot seem to just give them a URL and hope it gets figured out I want to see them succeed and tell me so. I see some users in these forums give out code like a Philadelphia Lawyer to a new guy. He is lost forever and scared of linux. Should be plain and simple and told what he is doing so he understands the commands not just copy and pasting and not knowing what he just did. Ego' seem to get in the way of some users in all forums. That is just a personal opinion of my own.
No more coffee am typing like a mad fool here.
EDIT: Did we help the OP or talk to ourselves.

---

### Post by john1066 on 2010-11-05
RE reply 2 - gparted starts up, scans the discs and then closes down without displaying whatever it found out! So not a lot I can do there.

RE reply 5 - the side by side option does not apear on the installation menu for my netbook (it did appear when I was doing my laptop installation). The only options that appear are
- delete disc and reformat
- advanced partitioning

John

---

### Post by wilee-nilee on 2010-11-05
> **john1066 said:**
> RE reply 2 - gparted starts up, scans the discs and then closes down without displaying whatever it found out! So not a lot I can do there.

RE reply 5 - the side by side option does not apear on the installation menu for my netbook (it did appear when I was doing my laptop installation). The only options that appear are
- delete disc and reformat
- advanced partitioning

John

At least for me I would suggest running the bootscript in my signature on the live Ubuntu cd and posting the text in code tags. Using code tags can be done manually as described in my sig or by hitting the # in the reply window and putting the text betweeen the tags generated.

A little strange that gparted on the live cd is not running correctly, hard to say why. You can actually download a gparted only ISO, it is a good tool to have.
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Is the media (cd/thumb?) you used to try to see gparted the same as you have been using to try to install?

---

### Post by garvinrick4 on 2010-11-05
> **john1066 said:**
> RE reply 2 - gparted starts up, scans the discs and then closes down without displaying whatever it found out! So not a lot I can do there.

RE reply 5 - the side by side option does not apear on the installation menu for my netbook (it did appear when I was doing my laptop installation). The only options that appear are
- delete disc and reformat
- advanced partitioning

John I am going to download a unity and burn to take a peek at. If you have a 10.10 desktop you can install that and then add unity interface I know that has a side by side. All Unity installs come with desktop installed also and is a choice at login screen. Destop you have to install netbook does not take long. But I want to look for my own self
I like to see it in person. Be back to see what you chose, or someone who has a unity install disk will chirp in here. See ya soon. Hey you do not have any USB drives in that
gparted has trouble reading do you a external drive of some sort? Besides your install USB flash drive. gparted should be able to read the sda installed in netbook. Can disk utility read your sda

---

### Post by garvinrick4 on 2010-11-05
> **john1066 said:**
> So after getting UNE 10.10 installed on my Acer laptop and working in dual boot mode (also have W7 there) I felt confident enough to install it on my little Asus netbook. So got to the screen where I can choose to run ubuntu from my usb or to install. I choose install after all  (as the blurb says) I can run alongside my existing system (again W7). So then I get the fright of my life - I get two options for install - either delete and reformat my disc or advanced (=fiddle about with partitions = big trouble as far as I am concerned). So my question is - how on earth do you get UNE installed without being an expert and without getting your entire disc reformatted and losing W7?

John

PS - my Acer has two discs and luckily I installed on the non-W7 one. I suspect that I would have been in deep trouble otherwise. Well john1066 I am on a live cd of 10.10 unity (netbook) and it does have install side by side. Your disk is not being read by the installer for some reason. gparted is not reading your disk so something is up partner. I can think of one thing to try and if does not work start a thread on installer not reading disk, I have seen it quite a few times and there are users who are experts in the subject. This has worked for some users I have seen.
```
Put in your USB and boot into Ubuntu live USB and run:
[CODE]sudo apt-get remove dmraid
```It is installed in my Live Cd from .iso file I just downloaded as you can see. Maybe will do it.
AFTER removing go to INSTALL and see if it sees your drive and choose side by side> let me know.

ubuntu@ubuntu:~$ aptitude show dmraid
Package: dmraid                   
State: installed
Automatically installed: no
Version: 1.0.0.rc16-3ubuntu2
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 184k
Depends: libc6 (>= 2.4), libdmraid1.0.0.rc16 (>= 1.0.0.rc16), libselinux1 (>=
         1.32), libsepol1 (>= 1.14), udev, dmsetup
Description: Device-Mapper Software RAID support tool
 dmraid discovers, activates, deactivates and displays properties of software
 RAID sets (eg, ATARAID) and contained DOS partitions. 
 
 dmraid uses the Linux device-mapper to create devices with respective mappings
 for the ATARAID sets discovered. 
 
 The following formats are supported: 
 Highpoint HPT37X/HPT45X
 Intel Software RAID
 LSI Logic MegaRAID
 NVidia NForce RAID (nvraid)
 Promise FastTrack
 Silicon Image(tm) Medley(tm)
 VIA Software RAID
 
 Please read the documentation in /usr/share/doc/dmraid BEFORE attempting any
 use of this software. Improper use can cause data loss!
Homepage: [http://people.redhat.com/~heinzm/sw/dmraid/]("http://people.redhat.com/%7Eheinzm/sw/dmraid/")

Enjoy your Ubuntu and let me know if fixed.

[/CODE]

---

### Post by john1066 on 2010-11-06
So the mystery deepens to something totally beyond my comprehension. I did a fresh build of une onto my usb in exactly the same way as I did for my laptop. What I got for the laptop (and what I installed on the laptop disc) was perfect - with that great desktop giving 3 menu choices at the top - applications, places and system. To my astonishment what I get on the netbook is that interface with flipping, nervous icons which I do not like. And I can't find my discs anywhere - files and folders icon just gives the folders for documents, images etc - no mention of the disc partitions. Any ideas? I'm flabbergasted. I guess it does solve one problem since there is no way I would want that installed on my netbook disc.

Thanks for your help,
John

---

### Post by garvinrick4 on 2010-11-06
> **john1066 said:**
> So the mystery deepens to something totally beyond my comprehension. I did a fresh build of une onto my usb in exactly the same way as I did for my laptop. What I got for the laptop (and what I installed on the laptop disc) was perfect - with that great desktop giving 3 menu choices at the top - applications, places and system. To my astonishment what I get on the netbook is that interface with flipping, nervous icons which I do not like. And I can't find my discs anywhere - files and folders icon just gives the folders for documents, images etc - no mention of the disc partitions. Any ideas? I'm flabbergasted. I guess it does solve one problem since there is no way I would want that installed on my netbook disc.

Thanks for your help,
John
Disks are on the left of any nautilus window or (file manager on launcher)? Give it a chance is rather nice, Unity. Did you learn to use Windows in 10 minutes?

---

### Post by john1066 on 2010-12-02
I'm still struggling with this. In the meantime I'm using 10.10 desktop from the usb rather than the netbook remix (I much prefer the desktop ui). W7 has partitioned the 250gb disc into a 107 drive and a 132 drive.
When I start up 10.10 the disk utility only sees one disc of 250 gb and doesn't see the 107/132 partitions. Gparted scans but doesn't find or report anything. If I try an installation I again get the two options

[LIST]
[*]delete disc and install (no way I'm going there)
[*]or advanced - if I use advanced then it sees the partitions ok but I am very nervous about proceeding further since my experience with allocating to partitions has been disastrous in the past
[/LIST]
So the question remains - how do I get Ubuntu installed on my netbook without being a guru on disc partitioning?

I would appreciate some help here since the start up procedure from the usb takes forever (it does work eventually but there is something very much wrong with it).

Thanks,
John

---

### Post by oldfred on 2010-12-02
Do you have the typical all 4 primary partitions are in use? Windows new installs create a 100MB hidden boot/recovery and vendors add another utilities partition, so all four primary partitions are used.

Post this or the gparted screen shot asked for in the second post.

```
sudo fdisk -l
```

You should shrink windows from windows, but do not attempt to create partitions from windows as it will convert your basic (the 4 primary partitions) to SFS or a logical volume manager that is compatible with nothing and windows says you cannot convert back without erasing drive.

---

### Post by matt_symes on 2010-12-02
Hi

It might be worth running the boot script in willie-nillies sig (post 2 of this thread). It will tell us exactly what is going on with your hard drive. The instructions for use are on the main page.

Kind regards

---

### Post by Rubi1200 on 2010-12-02
There are changes to the new live installer for 10.10 that users need to be aware of.

This is from kansasnoob:

> Well the Live Installer (aka: ubiquity) got a complete redo in 10.10. Some of the info here may be helpful:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

Be sure to check out post #15:

[http://ubuntuforums.org/showpost.php...6&postcount=15]("http://ubuntuforums.org/showpost.php?p=10145206&postcount=15")

---

### Post by john1066 on 2010-12-02
Here's the output from fdisk that oldfred asked for - hope this helps.


John


*********************************************************************

Disk /dev/sda: 250.1 GB, 250059350016 bytes

255 heads, 63 sectors/track, 30401 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0xe6086d7a



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       13055   104857600    7  HPFS/NTFS

/dev/sda2           13055       14360    10485760   1b  Hidden W95 FAT32

/dev/sda3           14360       30399   128833536    7  HPFS/NTFS

/dev/sda4           30399       30401       18112+  ef  EFI (FAT-12/16/32)



Disk /dev/sdb: 4043 MB, 4043309056 bytes

125 heads, 62 sectors/track, 1018 cylinders

Units = cylinders of 7750 * 512 = 3968000 bytes

Sector size (logical/physical): 512 bytes / 512 bytes

I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk identifier: 0xbb0eb409



This doesn't look like a partition table

Probably you selected the wrong device.



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   ?      444829      685686   933323145+  66  Unknown

Partition 1 has different physical/logical beginnings (non-Linux?):

     phys=(1010, 16, 43) logical=(444828, 47, 13)

Partition 1 has different physical/logical endings:

     phys=(906, 97, 3) logical=(131496, 79, 23)

Partition 1 does not end on cylinder boundary.

/dev/sdb2   ?           1           1           0   72  Unknown

Partition 2 has different physical/logical beginnings (non-Linux?):

     phys=(101, 116, 32) logical=(0, 41, 32)

Partition 2 has different physical/logical endings:

     phys=(370, 114, 47) logical=(0, 41, 31)

Partition 2 does not end on cylinder boundary.



Partition table entries are not in disk order

---

### Post by john1066 on 2010-12-02
And here's the input from bootscript.                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb: _________________________________________________________________________

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

/dev/sda1    *          2,048   209,717,247   209,715,200   7 HPFS/NTFS
/dev/sda2         209,717,248   230,688,767    20,971,520  1b Hidden W95 FAT32
/dev/sda3         230,688,768   488,355,839   257,667,072   7 HPFS/NTFS
/dev/sda4         488,355,840   488,392,064        36,225  ef EFI (FAT-12/16/32)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       1912fbd1-d692-ef4c-8b0d-b18ecbb405f8   ext2       casper-rw                     
/dev/sda1        0ED4CFE4D4CFCC61                       ntfs                                     
/dev/sda2        86F4-D40A                              vfat                                     
/dev/sda3        1E784E3B784E1247                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         F895-B419                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda3        /media/1E784E3B784E1247  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda1        /media/0ED4CFE4D4CFCC61  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 de 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 80 78 00 11 1e 00 00  00 00 00 00 02 00 00 00  |..x.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 19 b4 95 f8 4e  4f 20 4e 41 4d 45 20 20  |..)....NO NAME  |
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
00000100  7d 00 66 b8 68 c6 0d 00  66 ba 00 00 00 00 bb 00  |}.f.h...f.......|
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



Thanks,
John

```

```

---

### Post by oldfred on 2010-12-02
You have used all four primary partitions. Windows is on sda1, a recovery (vendors or windows?) is on sda2, another NTFS is on sda3, and you have an efi partition in sda4. If you have an efi boot option in BIOS.EFI that is what the efi partition is for and that should not be deleted.

The only other one you might delete is the system recovery. If you have not made backup DVDs and a repair CD from the recovery (if possible), then you should. That would let you totally reinstall your hard drive to the way it was when purchased. It is not really a install, but an image.

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Let us know what you want to do.

---

