---
title: "Wubi on Windows with RAID0"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by divxclub on 2011-02-01
Hi there ! I have a little problem here. I am trying to install Ubuntu 10.10 using Wibu inside Windows and installation looks good without any problems but when I select Ubuntu in Boot POST menu after I see Ubuntu Desktop I see error it's saying that Root directory is not specified and there is OK button and if I press it I see same message .....only way to get out is to click restart in top right corner. My Windows installation is on RAID0 SSDs and I actually tried to install it on same partition as windows and even tried to install on NEW unallocated and freshly formatted partition. Nothing works. I am thinking to install it from Live CD however in advance formatting on let's say 20gb of space what do i assign ? Like how do I partition it like root directory and swap and other partition i ll need. Like can you specify all I think 3 different partitions I'll need and how much space to allocate for each on let's say 20GB of space. Thanks !

P.S.

I remember I had a choice "Use all free space" and it was soo simple I could have windows and some unallocated space on hard drive and Ubuntu would of use it . Now I don't see this option. I see use entire disk ...or advanced where You have to create on unallocated space all parts of partitions needed that's where i need you help at, or let me know how to fix Wubu problem.

Thank you very much guys


EDITED: My System info if u need it.

Mobo: Asus P6T Deluxe
CPU: i7 920
RAM: 6GB G.Skill PC1333 cards
BOOT HDD: OCZ Vertex 2 64gb x 2 in RAID0
PROGRAMS HDD: WD 3x750gb Caviar Black in RAID0
BACK UP HDD: WD VeloRaptor 300GB via eSATA

Ireally don't know if you need anything else but plz let me know

---

### Post by Rubi1200 on 2011-02-02
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

Thanks.

---

### Post by divxclub on 2011-02-02
Thank you very much. I'll do it once I'll get home.

---

### Post by psusi on 2011-02-02
By definition, wubi installs to a file within the windows partition.  Don't use wubi.  Boot from the cd and do a normal install to its own partition.

---

### Post by divxclub on 2011-02-03
Here is requested info.

And about install from CD, as I stated before I really love to do this however for some reason I see only 2 options "Use entire Drive" and Advanced, when before in Ubuntu I saw options like install beside windows and in partition I saw option "Use free space" because that exactly what I did when installed windows I got about 30 GB of unallocated space for ubuntu to use. And I simply never formatted manually HDD for ubuntu so I don't know can I just format whole thing with etx4 ? OR I need swap and root and home partitions.

I just looked on results and I See a lot of unknowns in there ... can't be that good. I mean my setup is not that complicated. I have 2 SSDs in RAID0 on ASUS P6T Deluxe ...it's hardware RAID0 that I am using as boot drives ...and I also have 3x WD HDDs for programs and other things ... I really don't know what is going on and why ubuntu having problem with my setup. Only 1 thing I can *** is when on boot with live CD between first purple screen and screen when you see Ubuntu 10.10 and 4 dot's on the bottom, it takes pretty long time to load ...usually I see Ubuntu 10.10 and 4 dot's almost right away after first "Purple screen with some logos on bottom ...like battery logo or something"

---

### Post by Rubi1200 on 2011-02-03
I don't have time to look at this now, but I am posting it so others can also offer advice.

Will get back to you on this later today.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/mapper/isw_dfajjchfee_RAID0
 => Windows is installed in the MBR of /dev/mapper/isw_dieaaffgdd_RAID0_SSD

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 324. But according to the info from fdisk, 
                       sdc5 starts at sector 1948299264.
    Operating System:  
    Boot files/dirs:   

isw_dfajjchfee_RAID01: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dfajjchfee_RAID02: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_dieaaffgdd_RAID0_SSD1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

isw_dieaaffgdd_RAID0_SSD2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   187,344,895   187,138,048   7 HPFS/NTFS

/dev/sda2 ends after the last sector of /dev/sda

Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048 1,948,298,939 1,948,296,892   7 HPFS/NTFS
/dev/sdc2       1,948,298,940 1,953,520,064     5,221,125   5 Extended
/dev/sdc5       1,948,299,264 1,953,517,567     5,218,304   7 HPFS/NTFS


Drive: isw_dfajjchfee_RAID0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_dfajjchfee_RAID0: 2250.5 GB, 2250461675520 bytes
256 heads, 63 sectors/track, 272534 cylinders, total 4395432960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dfajjchfee_RAID01                  1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/mapper/isw_dfajjchfee_RAID01             34       262,177       262,144 Microsoft Windows
/dev/mapper/isw_dfajjchfee_RAID02        264,192 1,174,204,415 1,173,940,224 Linux or Data

Drive: isw_dieaaffgdd_RAID0_SSD ___________________ _____________________________________________________

Disk /dev/mapper/isw_dieaaffgdd_RAID0_SSD: 120.0 GB, 120040194048 bytes
255 heads, 63 sectors/track, 14594 cylinders, total 234453504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dieaaffgdd_RAID0_SSD1   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_dieaaffgdd_RAID0_SSD2            206,848   187,344,895   187,138,048   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dfajjchfee_RAID0: PTTYPE="gpt" 
/dev/mapper/isw_dieaaffgdd_RAID0_SSD1 36C84EC4C84E825B                       ntfs       System Reserved               
/dev/mapper/isw_dieaaffgdd_RAID0_SSD2 942E53CD2E53A6D0                       ntfs                                     
/dev/mapper/isw_dieaaffgdd_RAID0_SSD: PTTYPE="dos" 
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               
/dev/sdc1        26C0F80EC0F7E1CB                       ntfs       WD                            
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        E60EEC0B0EEBD31B                       ntfs       WD2                           
/dev/sdc: PTTYPE="dos" 
/dev/sde                                                isw_raid_member                               
/dev/sdf                                                isw_raid_member                               
/dev/sdg                                                isw_raid_member                               
error: /dev/mapper/isw_dfajjchfee_RAID01: No such file or directory
error: /dev/mapper/isw_dfajjchfee_RAID02: No such file or directory
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory
error: /dev/sdd: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dfajjchfee_RAID0
isw_dieaaffgdd_RAID0_SSD
isw_dieaaffgdd_RAID0_SSD1
isw_dieaaffgdd_RAID0_SSD2

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdc5        /media/WD2               fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdc1        /media/WD                fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1


Unknown BootLoader  on sda2


Unknown BootLoader  on isw_dfajjchfee_RAID01


Unknown BootLoader  on isw_dfajjchfee_RAID02



=======Devices which don't seem to have a corresponding hard drive==============

sdd 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/mapper/isw_dfajjchfee_RAID01: No such file or directory
hexdump: /dev/mapper/isw_dfajjchfee_RAID01: No such file or directory
hexdump: /dev/mapper/isw_dfajjchfee_RAID02: No such file or directory
hexdump: /dev/mapper/isw_dfajjchfee_RAID02: No such file or directory

```

---

### Post by divxclub on 2011-02-03
Thanks a lot buddy, I am going to sleep then it's 2.30 Am in here was hoping to do install tonight but it's all good I'll wait till tomorrow when I come back from work. Later !

---

### Post by psusi on 2011-02-03
You need one partition for /, and should use ext4 for that.  You might want a swap partition unless you don't care to use hibernation and have plenty of free ram.  If you do make a swap partition, it should be at least as large as your physical ram.

---

### Post by Rubi1200 on 2011-02-03
Hi divxclub,
okay, so there are a few problems that we need to address.

First, what, if anything, can you still boot into?

There are problems mounting on sda as well as this worrying message:
> /dev/sda2 ends after the last sector of /dev/sda
sdc5 also has issues:
> According to the info in the boot sector, sdc5 starts 
                       at sector 324. But according to the info from fdisk, 
                       sdc5 starts at sector 1948299264.
As to how serious this is, we need to get more information.

Finally,
there is this:
> error: /dev/mapper/isw_dfajjchfee_RAID01: No such file or directory
error: /dev/mapper/isw_dfajjchfee_RAID02: No such file or directory


Again, you need to tell us what is going on because we are not there.

If you tried to install with Wubi, it has definitely failed.

I will also ask some others for their opinions about what can be done in this situation so please hang in there.

---

### Post by psusi on 2011-02-03
> **Rubi1200 said:**
> There are problems mounting on sda as well as this worrying message:

/dev/sda2 ends after the last sector of /dev/sda


That is because sda is a member of the raid array.  Ignore it.

> **Rubi1200 said:**
> sdc5 also has issues:
According to the info in the boot sector, sdc5 starts 
at sector 324. But according to the info from fdisk, 
sdc5 starts at sector 1948299264.


Harmless unless that is the windows boot partition, which I don't think it can be since it is an extended partition anyway.

---

### Post by divxclub on 2011-02-04
Hi guys. After I installed Wibu I had Windows7 and Ubuntu in boot menu. After wibu failed I uninstalled it in Windows and right now everything works just Windows. Computer Boot in Windows on my RAID0 without problem just like before I started wibu install.

So what is going on. You want me to make video or something >? OR you recommend install Ubuntu with advanced formatting option from live cd.

Thanks !

---

### Post by Rubi1200 on 2011-02-04
As I understand your first post, you tried to install Wubi on a separate partition correct?

I have only seen one instance of a Wubi install on a RAID setup and there the user had it installed on the Windows RAID.

In your situation that would be SSD2 if I am not mistaken (in other words, it needs to go on the partition where you would normally boot into Windows).

But to be honest, you might be better off with a proper install to a dedicated partition for Ubuntu and then have the dual-boot option.

Read up first on Ubuntu and RAID, though, as there can be issues sometimes:
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by divxclub on 2011-02-04
Well that exactly what I tried to begin with. I allocated 40GB from 120GB SDD RAID boot drive for Wibu and installed it there. I had same error with Separate partiton and ever separate Drive, I tried to use my eSATA too :D.

Anyhow. Is there a chance I'll be able to install Ubuntu from Life CD ? Right now I have 30GB of space I can use for ubuntu installation. Can you please tell me what I should allocate to what in Advanced formatting option ? Or I can just create one ext4 and that's it ? Just quick info for 30GB plz

---

### Post by Rubi1200 on 2011-02-05
Well, 30 GB is enough unless you need to save a lot of stuff. If you have an extra storage drive that would be great. If you want to create a partition for data that can be shared between Windows and Ubuntu format it as FAT32 unless you will be saving files of 4GB or more (the limit for FAT). 

How much RAM do you have installed? If more than, say, 3GB you could probably get away without creating a swap partition and just use the 30GB and format it as exr4 with / as the mount point. This will then contain all the system files and a home folder.

Alternatively, partition the 30GB space into / and swap. The swap partition is normally 1.5-2x the amount of RAM. So if you have 2GB of RAM, swap would be 4GB.

In any event, use manual partitioning for all of this please.

---

### Post by divxclub on 2011-02-07
Well guys I messed up my Boot parameters. I tried to install Ubuntu from Live CD and after restart GRUB is not showing Windows, only Ubuntu .....but even Ubuntu on load giving me error and basically telling me that it can't load. Right now only way to load for me in to Windows is to get my Ultimate Boot CD Beta 12 (i think) and boot from one of the programs in there that search for boot files and boot computer manually. Okay I've done with all this non scene and let's talk business.

I am Willing to go from scratch. Let's say I have fresh unformatted Array RAID0, How do I make windows and Ubuntu on this nice RAID0 Array ? And not Wibu but actual thing. I want to have Windows and Ubuntu in GRUB and load whatever I want in setup. As I stated before what I did this Time is when I installed Windows I left 30GB on unallocated space so I was thinking I'll install Ubuntu in it but for some reason there is no more "Use free space" option in Ubuntu install and at first I used Wubi to install Ubuntu and I did see Windows 7 and Ubuntu at load but Ubuntu never loaded ....after trying to install ubuntu with life CD whole thing just collapsed on me and now I am using CD just to get to Windows. So please guys help me I want Windows and Ubuntu on my RAID0 with 80gb windows /40gb Ubuntu allocation.

P.S.

What I can use to find Windows boot sttings and save it so I don't have to use boot cd ?

Thank guys I hope you can help me, and if not I'll have to drop RAID0 and just use 1 SSD for Windows and another SSD for Ubuntu without RAID ......

---

### Post by divxclub on 2011-02-10
Anyone on my last reply about installing W7 and Ubuntu on RAID0 from scratch advice ?

Thanks !

---

