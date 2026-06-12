---
title: "Installing UNR 10.10 alongside Windows XP"
date: 2011-01-10
forum: Installation &amp; Upgrades
---

### Post by pauloz on 2011-01-10
Hi 

I know my problem is similar to others I've read but being new to UNR and not being tech savvy, I need to explain my situation:

When I get to the "Allocate Drive Space" section, I have only 2 options, namely "Erase and use the entire disk", which alarms me because I want to install UNR alongside Windows XP on my ASUS Eee PC 1005HA. The other option is "Specify partitions manually (advanced)". For obvious reasons, I am reluctant to try this. 

I have a C Drive (Windows) and a D Drive (mainly for Backup of Windows). Each drive is about 72GB with about 60GB free on my D Drive. Obviously, this is where I would like to install UNR, but will I have to clear my D Drive completely? I still have about 27GB free on my C Drive. 

Can anybody out there take me through step by step instructions to fix this problem? I am very reluctant to dispense with UNR just for this reason. I managed to install Ubuntu Desktop on a friend's ancient PC and it works like a new computer, so you can imagine how impressed I am with it.

Thanks in advance

pauloz[SIZE=4]
[/SIZE]

---

### Post by kansasnoob on 2011-01-10
Begin by booting the Live CD/USB and choosing to "Try Ubuntu" rather than choosing to install. Then from the live desktop post the output of the following command from terminal:

```
sudo parted -l
```

BTW that's a lower case L.

Just very general instructions:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by pauloz on 2011-01-11
Appreciate your reply. Unfortunately this is way over the top of my head. I'll get help professionally or dispense with the idea altogether. I typed the command but it's all too confusing for this ageing brain.
Thanks for your time - pauloz

---

### Post by pauloz on 2011-01-14
Now I'm really confused.
I enquired at a local computer shop and was advised that it was not possible to dual boot my ASUS netbook with Windows XP (which it came with) and UNR 10.10. But the installation instructions on the Ubuntu website clearly state that it is possible to do so. I have plenty of HD space available as mentioned previously. Unfortunately, my knowledge of partitioning etc is abysmal and I'm reluctant to try this without guidance.
Something else I noticed was that UNR is much slower than the Ubuntu Desktop Edition, which I also tried on my netbook (both from the USB drive). If somehow, I can get the dual boot up and running, is there any problem having Ubuntu Desktop running on my netbook?
Please help if you can!
pauloz

---

### Post by Quackers on 2011-01-14
There would be no problem running desktop edition rather than UNR.
First things first, how many primary partitions (including recovery) are currently being used in your system?
It may be better to resize your D: drive (which I presume is a partition, rather than a separate drive) thus creating free space for Ubuntu to install into.

If you are at all unsure about your partition structure please boot from the live cd and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by pauloz on 2011-01-14
OK thanks Quackers - I'm out of action for 24-36 hours, but will get back to you ASAP. Appreciate your help!
cheers pauloz

---

### Post by pauloz on 2011-01-15
Hello Quackers - I hope I've done this right! Again, thanks for your time. Regards from pauloz

                ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

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

/dev/sda1    *             63   151,123,454   151,123,392   7 HPFS/NTFS
/dev/sda2         151,123,455   302,230,844   151,107,390   7 HPFS/NTFS
/dev/sda3         302,230,845   312,480,314    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda4         312,480,315   312,576,704        96,390  ef EFI (FAT-12/16/32)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2019 MB, 2019557376 bytes
19 heads, 18 sectors/track, 11533 cylinders, total 3944448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          8,192     3,944,447     3,936,256   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4A30C94A30C93E27                       ntfs                                     
/dev/sda2        A000B2F200B2CF12                       ntfs                                     
/dev/sda3        CCED-990E                              vfat       PE                            
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F87C-A46E                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 26 00  |.X.SYSLINUX...&.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 20 00 00  |........?.... ..|
00000020  00 10 3c 00 fd 0e 00 00  00 00 00 00 02 00 00 00  |..<.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 6e a4 7c f8 4e  4f 20 4e 41 4d 45 20 20  |..)n.|.NO NAME  |
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
00000100  7d 00 66 b8 28 1e 00 00  66 ba 00 00 00 00 bb 00  |}.f.(...f.......|
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

### Post by wilee-nilee on 2011-01-16
Your computer has the maximum allowed primary partitions as of now. In order to partition install Ubuntu, you will have to remove one, don't just do this though without some help.

---

### Post by Quackers on 2011-01-16
Hi pauloz, as wilee-nilee has stated, you already have the maximum number of primary partitions on your disc. You should not create another until one is deleted.
sda1 carries the boot flag and I would surmise that this is your C: (it's about 75GB)
sda2 is approx 150GB and I would suspect is your D: partition

Does this tally with your C: and D: size partitions in Windows?

sda3 is a hidden partition (probably recovery)
sda4 is shown as unmountable and is an EFI partition of some kind.

Depending on how much data you have on your D: partition, that may be the best choice to be deleted.
I presume that you won't want to delete the recovery partition?
And the EFI partition is probably being used by a program of some kind, so shouldn't be deleted.
Please let us know what you think.

---

### Post by pauloz on 2011-01-16
Quackers - I hope the info below will help you (I got it from Belarc Advisor). In your comments, you suggested my D: partition is 150 GB. That's not correct, it is 77.37 GB - in other words, my hard drive has been split down the middle. There is nothing on my D: partition presently. I would not want to delete my recovery partition. 

Assuming I go ahead and delete the D: partition, is there a risk my C: partition will be affected? I backed up My Docs in XP to an external drive today.

Again thanks - you have been fantastic help. @ wilee-nilee - I appreciate your help too.

pauloz

```

```Drives	 	
154.74 Gigabytes Usable Hard Drive Capacity
117.66 Gigabytes Hard Drive Free Space

ST9160314AS [Hard drive] (160.04 GB) -- drive 0, SMART Status: Healthy	 	

Memory Modules c,d
1016 Megabytes Usable Installed Memory
Slot 'DIMM0' has 1024 MB

Local Drive Volumes
c: (NTFS on drive 0)	77.38 GB	40.70 GB free
d: (NTFS on drive 0)	77.37 GB	76.96 GB free

Network Drives
None detected

---

### Post by pauloz on 2011-01-16
Quackers - to also help you, I've pasted the result of a sudo command that was suggested by kansasnoob a few days ago. Thanks pauloz

```

```To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST9160314AS (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  77.4GB  77.4GB  primary  ntfs         boot
 2      77.4GB  155GB   77.4GB  primary  ntfs
 3      155GB   160GB   5248MB  primary  fat32        hidden, lba
 4      160GB   160GB   49.4MB  primary


Model: JetFlash Transcend 2GB (scsi)
Disk /dev/sdb: 2020MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4194kB  2020MB  2015MB  primary  fat32        boot


ubuntu@ubuntu:~$

---

### Post by Shreddy_K on 2011-01-16
Hi guys,

I'm having a similar issue to Pauloz, and am eager to see a solution. I'm attempting to install UNR 10.10 on a Asus 1015PEM using the live USB drive. The Asus (brand new) comes from the factory with four partitions:

sda1: 107GB Win7 Starter (NTFS)
sda2: 16.1GB Win7/Vista recovery (FAT32)
sda3: 127GB Empty storage (NTFS)
sda4: 21.2MB Asus Boot Booster doohickey

SO. In the installation, I have two choices: "Erase and use the entire disk" or "Specify partitions manually". Since I'm going for a dual boot, I selected the latter. In tutorials, I have seen a "Install alongside other OS" options, but I didn't have that.

I selected sda3, and set "Use as:" to Ext4. I clicked the "Format partition" box, and set the mount point to /. Then, I selected sda3 in the "Device for boot loader installation" dropdown. I elected not to designate a swap space.

I let the installer run, and it appears to have completed satisfactorily. However, I don't have any boot options upon startup. I was expecting to have two selectable volumes when pressing ESC, like I did with the live USB drive. Instead, I just have the hard drive, and selecting it results in a Win7 boot.

I went back in to the USB load, and found a 10.10 install sitting on sda3.

```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST9250315AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  107GB  107GB   primary  ntfs         boot
 2      107GB   123GB  16.1GB  primary  fat32        hidden
 3      123GB   250GB  127GB   primary  ext4
 4      250GB   250GB  21.2MB  primary
 
 Model: Sony Storage Media (scsi)
 Disk /dev/sdb: 4027MB
 Sector size (logical/physical): 512B/512B
 Partition table: msdos
 
 Number  Start   End     Size    Type     File system  Flags
  1      16.4kB  4017MB  4027MB  primary  fat32        boot, lba

```

What did I do wrong? I read on another thread that there are GRUB options that must be set, but I don't recall being asked to do so. Any advice?

---

### Post by Shreddy_K on 2011-01-16
(double post)

---

### Post by Quackers on 2011-01-16
It seems that you have installed grub to sda3. For booting the system looks at the mbr of the drive (sda). That's where grub needs to be installed.

---

### Post by Shreddy_K on 2011-01-16
Thanks, Quackers. I'll select "sda" in the "Device for boot loader installation" dropdown and report back.

---

### Post by Quackers on 2011-01-16
If you are re-installing,yes. But you can do it from a terminal in the live cd desktop.
Start gparted in the live cd desktop and after it has scanned your disc see if the ext4 partition is /dev/sda3. I presume it will be. If it isn't change sda3 in the command below.
To re-install grub to the mbr of sda 
```
sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Then reboot

---

### Post by Shreddy_K on 2011-01-16
I was too late reading your post, and reinstalled. It worked like a charm, though! Thanks so much for the help.

---

### Post by Quackers on 2011-01-16
Oh dear. This forum's too slow :-)
Happy Ubuntuing :-)

---

### Post by pauloz on 2011-01-17
Hi Quackers - pauloz here again. With allocating drive space, I guess I'll have to delete the sda2 partition before I create another one. Do I highlight this then delete? Or do I use the "Change" option? Any chance you can guide me through otherwise I'm flying blind. Also, I have 5 options in "Device for boot loader installation":

1. /dev/sda ATA ST9160314AS (160GB)
2. /dev/sda1 Microsoft Windows XP
3. /dev/sda2
4. /dev/sda3 Windows NT/2000/XP
5. /dev/sda4

Which one is it? Any help appreciated.

---

### Post by Quackers on 2011-01-17
Are you in gparted? or the installer?

---

### Post by wilee-nilee on 2011-01-17
> **pauloz said:**
> Hi Quackers - pauloz here again. With allocating drive space, I guess I'll have to delete the sda2 partition before I create another one. Do I highlight this then delete? Or do I use the "Change" option? Any chance you can guide me through otherwise I'm flying blind. Also, I have 5 options in "Device for boot loader installation":

1. /dev/sda ATA ST9160314AS (160GB)
2. /dev/sda1 Microsoft Windows XP
3. /dev/sda2
4. /dev/sda3 Windows NT/2000/XP
5. /dev/sda4

Which one is it? Any help appreciated.

Boot the live Ubuntu cd, take a screen shot of gparted and post it.

---

### Post by pauloz on 2011-01-17
I was in the installer i.e. the screen that comes up after checking the "Specify partitions manually" option.
Thanks pauloz

---

### Post by pauloz on 2011-01-17
I've finally managed to install the Ubuntu Desktop edition alongside Windows XP on my netbook after being told by a computer shop owner that it couldn't be done.

I decided on the Desktop edition rather than UNR for netbooks - I didn't like those launchers on the LHS of the screen, which won't budge for anyone - they took up too much space. Also IMHO, it wasn't as quick as the Desktop edition, which I've found quick and really crisp. I need to do a bit of tweaking for it to display OK on my netbook but so far so good.

Thanks to the guys who posted on this thread to help me out.

---

### Post by Quackers on 2011-01-17
Aha! Excellent news! I can take you off the list now :wink:
You're welcome. Enjoy Ubuntu :-)

---

