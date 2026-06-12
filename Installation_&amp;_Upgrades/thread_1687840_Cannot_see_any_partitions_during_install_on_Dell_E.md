---
title: "Cannot see any partitions during install on Dell E5410 / Corrupt GPT"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by snevs on 2011-02-14
Hey guys, 

I' trying to install **10.10** Desktop from a CD onto a **Dell E5410** notebook with Windows 7 installed.

The problem is that during the installation, the installer doesn't see the Windows partition, moreover, it doesn't see **_any_** other partition.

I've tried with **CentOS 5.5** as well and it returned some error related to **GPT Partition Table** corrupt which might have been corrupted by a software (or not).

Removing Windows 7 completely is not an option, there's a bunch of business applications which will not run on Linux even with Wine.

I'm not sure if the problem lies on the hardware, or the installer.
The BIOS provides advanced UEFI boot options and legacy boot, but this doesn't explain why no partition is discovered.

Tech specs: core i5, 4GB ram, 320 GB disk space. The installer is 32 bit, but I'm quite the architecture doesn't really matter.

If someone has more knowledge about this kind of issue, any answer is welcome.

---

### Post by jerrrys on 2011-02-14
for partition recovery

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Quackers on 2011-02-14
Are you using a GUID Partition Table? Do you have a boot booster?

---

### Post by snevs on 2011-02-14
Thank you, jerrrys, I will do some research.

@Quackers: No, I only did a fresh windows install, then created other NTFS partitions. 
There are 2 primary partitions, 2 logical and 40 Gb unallocated space.
I haven't used anything to create partitions table.
This thing is quite strange because if I'm not wrong, GPT is used for hard drives larger than 1TB, but I might be wrong.

@jerrrys: Will that application just rebuilt the GPT table, or try to remove all the partitions and then create the table?

I tried booting with Gparted Live, but even there the hard drive seems to be empty. No partition.

There's a setting to mark the device as active but this returns a warning message that will destroy ALL DATA on hard drive.

---

### Post by Mark Phelps on 2011-02-14
If your Dell came with Win7 preinstalled, it's likely that it already has the maximum of 4 primary partitions on the drive -- in which case, the installer is NOT going to be able to create any more partitions for you.  

That will leave you with Wubi (installing inside Windows) as the only option -- unless you want to mess around with removing and shrinking existing partitions.

Sounds like you're concerned about damaging your existing Win7 install -- a possible result of messing around with partitions.

So, if your Dell has a CD/DVD burning drive, the first thing you should do is use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will allow you to restore Win7 boot capability should that become damaged during your Ubuntu install.

---

### Post by Quackers on 2011-02-14
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by snevs on 2011-02-14
```
ubuntu@ubuntu:~$ cd Desktop/
ubuntu@ubuntu:~/Desktop$ sudo sh boot_info_script055.sh 
ubuntu@ubuntu:~/Desktop$ sudo bash boot_info_script055.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
Searching sdb for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop
ubuntu@ubuntu:~/Desktop$ cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda3 starts at sector 104859648.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   104,859,647   104,652,800   7 HPFS/NTFS
/dev/sda3         104,859,648   209,717,247   104,857,600   b W95 FAT32
/dev/sda4         209,719,233   471,865,343   262,146,111   f W95 Ext d (LBA)
/dev/sda5         209,719,296   367,005,695   157,286,400   7 HPFS/NTFS
/dev/sda6         367,007,744   471,865,343   104,857,600   7 HPFS/NTFS


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A65A23675A233389                       ntfs       System Reserved               
/dev/sda2        2CCE2980CE294384                       ntfs                                     
/dev/sda3        1F15-310E                              vfat       ZZ                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        4A3818033817ED27                       ntfs       New Volume                    
/dev/sda6        D23423B734239D8B                       ntfs       New Volume                    
/dev/sda: PTTYPE="dos" 
/dev/sdb         07E0-2418                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 88 77 00 89 3b 00 00  00 00 00 00 02 00 00 00  |..w..;..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 18 24 e0 07 4e  4f 20 4e 41 4d 45 20 20  |..).$..NO NAME  |
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
00000100  7d 00 66 b8 36 77 00 00  66 ba 00 00 00 00 bb 00  |}.f.6w..f.......|
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


ubuntu@ubuntu:~/Desktop$ 

```

the sdb is an USB thumb containing the Gparted Live.
The windows is installed on /dev/sda2. The first partition was automatically created by the Windows installer.

---

### Post by Quackers on 2011-02-14
I see
"GUID Partition Table detected, but does not seem to be used."
I haven't seen that before (the not used bit).
With a GUID partiton table the installation is slightly different. It may be worth having a look at the Apple Users section of the forum, as they use GPT.
It may also be worth having a look at oldfred's post in this thread for some info

[http://ubuntuforums.org/showthread.php?t=1622938&highlight=GUID](http://ubuntuforums.org/showthread.php?t=1622938&highlight=GUID)

---

### Post by snevs on 2011-02-14
Thank you for the recommendation. 
From that post I've found other related resources which all point to the EFI boot options.

Sincerely, it didn't even cross my mind to swtich to EFI at the boot screen just to skip the legacy boot mode. 

I'll try it it out and I will get back with a feedback. 
It might work.

---

### Post by Quackers on 2011-02-14
I haven't used GPT so am unable to help in that respect. Have a good read and take your time :-)  Good luck.

---

### Post by srs5694 on 2011-02-14
First, some background: The Master Boot Record (MBR) and GUID Partition Table (GPT) are two different ways of storing partitioning data on the disk. MBR is the older system, and it stores its primary partition table on a single sector (sector 0, aka the MBR). GPT is the newer system, and it stores data both in sector 0 (which takes the form of a "protective MBR" whose purpose is to prevent GPT-unaware tools from messing with the disk) and elsewhere on the disk. Keep this fact in mind. GPT is most commonly used on Macs and other (U)EFI-based systems, although it can be used on BIOS-based computers, too.

What you've got is a disk that was partitioned with GPT and then incompletely converted back to MBR format by a GPT-unaware tool, such as Linux's fdisk or the Windows installer. In this incomplete conversion, the GPT's hybrid MBR was converted to a regular MBR, but the bulk of the GPT data was left untouched. Technically, this makes the disk a legal MBR disk; however, libparted (upon which the Ubuntu installer relies) gets confused by this and produces the symptoms you report.

***Do not*** use TestDisk on the disk. Although it might work, it might also create a new set of problems that could actually be harder to fix.

I recommend you read [this page of mine,](http://www.rodsbooks.com/gdisk/wipegpt.html) which describes how to fix the problem. In brief, you should download my [GPT fdisk (gdisk and sgdisk)](http://www.rodsbooks.com/gdisk/) package from [its Sourceforge download page](http://sourceforge.net/projects/gptfdisk/files/) and use it to erase the old GPT data:

```

sudo sgdisk --zap /dev/sda

```

Be sure to download the version of GPT fdisk from Sourceforge; the version in the Ubuntu repositories is hopelessly out of date and has known bugs.

---

### Post by srs5694 on 2011-02-14
> **snevs said:**
> Thank you for the recommendation. 
From that post I've found other related resources which all point to the EFI boot options.

Sincerely, it didn't even cross my mind to swtich to EFI at the boot screen just to skip the legacy boot mode. 

Switching to EFI boot mode will not fix the problem. Your partition layout clearly indicates that Windows is currently booting using BIOS mode, and switching between the two modes is not simple, so making the attempt will be a waste of time at best and could conceivably cause more problems at worst.

---

### Post by snevs on 2011-02-15
Hello Rod, 

I'd like to thank you for the reply and for writing that page as well. 
As from that page, it looks like you had the time to answer all the questions that one could have.

I will try that solution as soon I finish the job with the laptop, I'm currently at work. 

When I first started the Windows installation, I didn't notice that the BIOS does have the UEFI boot option, I thought the installation method will be the same as on the other laptops I had before.

The installation failed for 3 times in a row, then I did some changed to the boot options and finally managed to install the OS. 

I did notice some strange changes to the boot sectors though.

Between the restarts during the Windows installation it crossed my mind to change the boot devices order and when I got to the advanced boot option I saw that the Windows installer has performed a few changes. 
The UEFI boot option was set as the default, and the path to the boot file was a .wim file located on the C partition where the Windows had to be installed.

After a few reboots, the Windows installer has finished the job and the boot options were automatically switched back to the legacy boot mode, the path to that .wim file was erased and the Windows OS was able to boot into normal mode. 

Many thanks for the time you spent writing that page.

I will get back with a feedback.

---

### Post by snevs on 2011-02-22
Hi, 

Sorry for not answering till now.

The solution didn't work. 
In fact, it erased all the hard drive but I'm lucky I created a data backup.

I had to reset the BIOS, the I repartitioned the hard drive, installed Windows and then Ubuntu.

Problem fixed, but with a huge headache.

---

### Post by srs5694 on 2011-02-22
There's no way that sgdisk could have "erased all the hard drive." At worst, it might erase the partition table, but the --zap option should only erase the GPT data, not the MBR data. (The --zap-all option erases both the GPT and MBR data.) Can you tell me what version of sgdisk you used, and ideally what precise command you used? If you recall anything about messages displayed during the operation, that would also be very helpful. I'd like to check for bugs, in case there's some way to call it that erases more than it should be erasing.

---

### Post by snevs on 2011-02-23
I've installed [gdisk_0.6.14-1_i386.deb]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.6.14/gdisk_0.6.14-1_i386.deb/download"), then 
```
# **fdisk -l /dev/sda**
```to list the partition table.
```
# gdisk /dev/sda
```option #2 for GPT

then w for saving data and in ther end I've used the zap option z
```
# sgdisk -z /dev/sda
```After that I rebooted the laptop to see the changes and no partitions were listed so I re-inserted the bootable CD, re-created the partitions and chose to install the windows on the second partition to leave space for Ubuntu on the first.

It may be that the sgdisk has erased only the GPT data, but no partitions were visible after the reboot.

---

### Post by srs5694 on 2011-02-23
> **snevs said:**
> I've installed [gdisk_0.6.14-1_i386.deb]("http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.6.14/gdisk_0.6.14-1_i386.deb/download"), then 
```
# **fdisk -l /dev/sda**
```to list the partition table.
```
# gdisk /dev/sda
```option #2 for GPT

then w for saving data

By doing this, which I *never* told you to do, you converted the disk from MBR with old GPT data into a technically correct GPT disk (in the sense that the partition table was legal; there's no telling what partitions it defined), wiping out your MBR partitions. Then....

> and in ther end I've used the zap option z
```
# sgdisk -z /dev/sda
```

This command, which I *did* tell you to run, wiped the GPT data from the disk, leaving nothing but the protective MBR that you created in place of your valid MBR data. This command would have been correct to run *if* you hadn't run gdisk and saved the partition table. If you'd run this command straight away, without first using gdisk, it would have wiped the old GPT data, leaving your valid MBR data intact.

In sum, I'm afraid this is a case of user error. I'm glad you were able to recover your data from a backup, but I suggest you think of this as a learning experience: Be more careful in the future when dealing with partitions, and when following instructions you don't fully understand!

---

### Post by snevs on 2011-02-28
Thank you for the detailed description. 

I'll keep this thread as a reference for future cases when I'll be put into the situation of installing multiple OSes on a computer with EFI boot options. 

Best regards.

---

