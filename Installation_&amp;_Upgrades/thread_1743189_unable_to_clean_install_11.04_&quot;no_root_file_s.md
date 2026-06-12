---
title: "unable to clean install 11.04 &quot;no root file system is defined&quot;"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by ilya222 on 2011-04-29
i've tried the windows installer and go this message after the reboot, then i tried from a cd, and got exactly the same error at the partition selection. 
i tried several drives and always go the same message.

---

### Post by oldos2er on 2011-04-29
Root filesystem is / in the drop-down menu.

---

### Post by ilya222 on 2011-04-29
in which dropdown menu?
when i use wubi there's no menu, it's the first thing i see...
screenshot: [http://img843.imageshack.us/i/img2085hb.jpg/](http://img843.imageshack.us/i/img2085hb.jpg/)

---

### Post by oldos2er on 2011-04-29
Sorry, I don't know anything about Wubi. Looks like this is a known bug: [https://bugs.launchpad.net/wubi/+bug/259540](https://bugs.launchpad.net/wubi/+bug/259540)

---

### Post by bcbc on 2011-04-29
Usually this is due  to:
1. mix of GPT and MBR partition table - this confuses ubiquity
2. leftover fakeraid metadata or unsupported raid option

If you burn an Ubuntu CD (or USB), boot from it, select "Try without installing" and run [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) it should give some clues.

---

### Post by ilya222 on 2011-04-30
> **bcbc said:**
> Usually this is due  to:
1. mix of GPT and MBR partition table - this confuses ubiquity
2. leftover fakeraid metadata or unsupported raid option

If you burn an Ubuntu CD (or USB), boot from it, select "Try without installing" and run [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) it should give some clues.

Thanx,
It's probably the first one because i never used RAID, so how can i  fix it?

---

### Post by srs5694 on 2011-04-30
I wouldn't jump to any GPT conclusions, ilya222. Please be more precise about where you're seeing this error. Is it when you're trying to install Ubuntu, or after it's been installed and when you reboot? How does the Windows installer fit into things? As it is, I at least am left guessing about critical details like this. (I didn't respond earlier for this reason, but I see this thread heading into potentially very dangerous territory in its current direction.)

If you've installed Ubuntu and it's not booting, try booting the installer into "live CD" mode and running the [Boot Info Script.](http://sourceforge.net/projects/bootinfoscript/) This will produce a file called RESULTS.TXT. Post it here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. That should provide additional information that can be used to diagnose your problem.

---

### Post by bcbc on 2011-04-30
+1 
I'm reporting on specific failures I've seen before - but that doesn't mean you don't need to investigate and confirm the problem. Running any fix without understanding it - or whether it's required - is a bad idea.

---

### Post by ilya222 on 2011-04-30
> **srs5694 said:**
> I wouldn't jump to any GPT conclusions, ilya222. Please be more precise about where you're seeing this error. Is it when you're trying to install Ubuntu, or after it's been installed and when you reboot? How does the Windows installer fit into things? As it is, I at least am left guessing about critical details like this. (I didn't respond earlier for this reason, but I see this thread heading into potentially very dangerous territory in its current direction.)

If you've installed Ubuntu and it's not booting, try booting the installer into "live CD" mode and running the [Boot Info Script.](http://sourceforge.net/projects/bootinfoscript/) This will produce a file called RESULTS.TXT. Post it here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. That should provide additional information that can be used to diagnose your problem.

when i use the wubi, it runs on windows, then i reboot into the ubuntu install, and the error message appears the second the install starts.
when i run from the cd, it happens when i try to select a partition, and i get it no matter what drive or partition i select.
also, i tried installing 10.10 and got exactly the same results.

---

### Post by srs5694 on 2011-04-30
I still don't understand what you mean -- "the second the install starts" could mean many things, from the second you begin booting the installer to the moment the computer begins copying files. It's also unclear what you mean by "when i try to select a partition" -- where are you selecting a partition? A simple boot into the live CD doesn't require selecting a partition, and once it's booted, there are so many procedures and utilities that support "selecting a partition" that it'd take pages to enumerate them all. I'm afraid you just have to be much more precise in your descriptions. Posting a screen shot (taken with a digital camera, if necessary) will help us, since that might reveal enough of the context for us to figure out what you mean.

---

### Post by ilya222 on 2011-05-01
> **srs5694 said:**
> I still don't understand what you mean -- "the second the install starts" could mean many things, from the second you begin booting the installer to the moment the computer begins copying files. It's also unclear what you mean by "when i try to select a partition" -- where are you selecting a partition? A simple boot into the live CD doesn't require selecting a partition, and once it's booted, there are so many procedures and utilities that support "selecting a partition" that it'd take pages to enumerate them all. I'm afraid you just have to be much more precise in your descriptions. Posting a screen shot (taken with a digital camera, if necessary) will help us, since that might reveal enough of the context for us to figure out what you mean.

i mean, in the wubi case, ofter the installation loads, i get to the desktop-like screen (with the network and logout option at the top) and when it completes i get the message
it says "verifying the installation configuration"

in the second case i run install directly from the cd, i do not run live ubuntu from it (nor did i mentioned doing so before)
when i get to select the partition in which to install it, i get the message when i click "install"

---

### Post by Quackers on 2011-05-01
It sounds like you haven't selected a mount point for your root partition. The mount point should be " / "

---

### Post by ilya222 on 2011-05-01
> **Quackers said:**
> It sounds like you haven't selected a mount point for your root partition. The mount point should be " / "

but with wubi there's no option of selecting any mountpoint, it only asks me in what drive to install and all the rest is auto...
how can i do it in the cd install?

---

### Post by bcbc on 2011-05-01
In the wubi case the mountpoint is predefined, but it doesn't change the actual steps ubiquity goes through. The only difference is that the install is "preseeded". So the cause is the same.

What this means is that the kernel has no problem loading, but ubiquity has a problem dealing with the drive. So basically you should boot from the CD, "try without installing" (which bypasses the drive) and then run the bootinfoscript.

Or even just drop to a root shell during the ubiquity install (CTRL+ALT+F2) and enter "sudo fdisk -l" (lower case -L) and copy the output verbatim.

---

### Post by ilya222 on 2011-05-01
OK, here is the bootinfoscrip results:

>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
 => Windows is installed in the MBR of /dev/sdd

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
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr /wubildr

sdd1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
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

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   312,575,999   312,369,152   7 HPFS/NTFS


GUID Partition Table detected, but does not seem to be used.

Partition           Start           End          Size System

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *         16,065   976,768,064   976,752,000   5 Extended
/dev/sdb5              16,128   976,768,064   976,751,937   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312579695 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1               2,048   312,575,999   312,573,952   7 HPFS/NTFS


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdd1                  63 1,250,258,624 1,250,258,562   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AEB80EF1B80EB83B                       ntfs       System Reserved               
/dev/sda2        4028C8A928C89F72                       ntfs       Games                         
/dev/sda: PTTYPE="dos" 
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        543C992748E06E89                       ntfs       Storage                       
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        EA84134A84131921                       ntfs       System                        
/dev/sdc: PTTYPE="dos" 
/dev/sdd1        01C950BC949DC0D0                       ntfs       Backup                        
/dev/sdd: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200




---

### Post by bcbc on 2011-05-01
> =========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 * 2,048 206,847 204,800 7 HPFS/NTFS
/dev/sda2 206,848 312,575,999 312,369,152 7 HPFS/NTFS


[COLOR="Red"]GUID Partition Table detected, but does not seem to be used.[/COLOR]


So it is some leftover GPT partition table data that is causing the problem. I could refer you to some threads, but really srs5694 is the expert so I'll defer here.

PS I think someone should get a bug to the attention of Evan Dandrea so that he can get Ubiquity to deal with this

---

### Post by srs5694 on 2011-05-01
My [FixParts](http://www.rodsbooks.com/fixparts) program detects and, if requested, erases stray GPT data. Its Web page describes the process, so please read it. Given that you've got a working Windows installation, it's probably simplest to use the Windows version of FixParts to take care of the problem.

---

### Post by ilya222 on 2011-05-02
Thanx! it worked

---

### Post by pearce007 on 2011-05-05
> **srs5694 said:**
> My [FixParts]("http://www.rodsbooks.com/fixparts") program detects and, if requested, erases stray GPT data. Its Web page describes the process, so please read it. Given that you've got a working Windows installation, it's probably simplest to use the Windows version of FixParts to take care of the problem.

Hi srs5694 could you check to see if I have the same problem, thanks

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 63. The info in boot sector on 
                       the starting sector of the MFT is wrong. According to 
                       the info in the boot sector, sda1 has 960403447 
                       sectors, but according to the info from fdisk, it has 
                       1984 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048   960,405,495   960,403,448  42 SFS
/dev/sda3         960,405,496   976,771,119    16,365,624  42 SFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4A3AA3C73AA3AE7F                       ntfs                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sda2: No such file or directory
error: /dev/sda3: No such file or directory
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

MFT Sector of sda1

00000000  46 49 4c 45 30 00 03 00  49 54 6d 0a 00 00 00 00  |FILE0...ITm.....|
00000010  01 00 01 00 38 00 01 00  a0 01 00 00 00 04 00 00  |....8...........|
00000020  00 00 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |................|
00000030  30 00 e7 84 00 00 00 00  10 00 00 00 60 00 00 00  |0...........`...|
00000040  00 00 18 00 00 00 00 00  48 00 00 00 18 00 00 00  |........H.......|
00000050  00 8e f9 a0 40 0b cc 01  00 8e f9 a0 40 0b cc 01  |....@.......@...|
*
00000070  06 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  00 00 00 00 00 01 00 00  00 00 00 00 00 00 00 00  |................|
00000090  00 00 00 00 00 00 00 00  30 00 00 00 68 00 00 00  |........0...h...|
000000a0  00 00 18 00 00 00 03 00  4a 00 00 00 18 00 01 00  |........J.......|
000000b0  05 00 00 00 00 00 05 00  00 8e f9 a0 40 0b cc 01  |............@...|
000000c0  00 8e f9 a0 40 0b cc 01  00 8e f9 a0 40 0b cc 01  |....@.......@...|
000000d0  00 8e f9 a0 40 0b cc 01  00 40 00 00 00 00 00 00  |....@....@......|
000000e0  00 40 00 00 00 00 00 00  06 00 00 00 00 00 00 00  |.@..............|
000000f0  04 03 24 00 4d 00 46 00  54 00 00 00 00 00 00 00  |..$.M.F.T.......|
00000100  80 00 00 00 48 00 00 00  01 00 40 00 00 00 01 00  |....H.....@.....|
00000110  00 00 00 00 00 00 00 00  bf 2c 00 00 00 00 00 00  |.........,......|
00000120  40 00 00 00 00 00 00 00  00 00 cc 02 00 00 00 00  |@...............|
00000130  00 00 cc 02 00 00 00 00  00 00 cc 02 00 00 00 00  |................|
00000140  32 c0 2c 00 00 0c 00 aa  b0 00 00 00 50 00 00 00  |2.,.........P...|
00000150  01 00 40 00 00 00 05 00  00 00 00 00 00 00 00 00  |..@.............|
00000160  02 00 00 00 00 00 00 00  40 00 00 00 00 00 00 00  |........@.......|
00000170  00 30 00 00 00 00 00 00  08 20 00 00 00 00 00 00  |.0....... ......|
00000180  08 20 00 00 00 00 00 00  31 01 ff ff 0b 11 01 ff  |. ......1.......|
00000190  31 01 de 17 06 00 e7 84  ff ff ff ff 00 00 00 00  |1...............|
000001a0  00 00 04 00 00 00 00 00  31 40 00 00 0c 00 b8 87  |........1@......|
000001b0  b0 00 00 00 50 00 00 00  01 00 40 00 00 00 05 00  |....P.....@.....|
000001c0  00 00 00 00 00 00 00 00  01 00 00 00 00 00 00 00  |................|
000001d0  40 00 00 00 00 00 00 00  00 20 00 00 00 00 00 00  |@........ ......|
000001e0  08 10 00 00 00 00 00 00  08 10 00 00 00 00 00 00  |................|
000001f0  31 01 ff ff 0b 11 01 ff  00 00 01 00 00 70 30 00  |1............p0.|
00000200
Unknown BootLoader  on sda2


Unknown BootLoader  on sda3



=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory

---

### Post by srs5694 on 2011-05-05
Pearce007,

It's generally best to start your own thread rather than "hijack" an existing one. I'll respond here only because ilya222 seems to be satisfied with the solution. Also, when posting text-mode program output, please enclose it in [noparse]```
[/noparse] and [noparse]
```[/noparse] tags; that greatly improves legibility.

The answer to your question is that, no, your issue is not the same as ilya222's. FixParts won't help. You've got a Windows SFS/LDM/"dynamic disk" configuration, which is a Windows-only system similar to Linux's Logical Volume Manager (LVM). AFAIK, it's difficult or impossible to install Linux to such a disk. You have four options:


[list]
[*]**Give up** -- You can forget about installing Linux (or anything else) on the computer.
[*]**New disk** -- You can buy a new disk and install Linux on it, keeping Windows on the original disk.
[*]**Conversion** -- A couple of Windows programs ([EASEUS](http://www.partition-tool.com/personal.htm) and [Partition Wizard](http://www.partitionwizard.com/)) are claimed to be able to convert from "dynamic disk" format to "basic disk" (that is, regular partition) format. I've not tried either tool, though.
[*]**Wipe out** -- You can completely delete your partitions and start over again.
[/list]


FWIW, this problem often occurs when users attempt to prepare a hard disk for Linux use by preparing partitions in Windows. If you exceed four partitions in Windows, the partitioning software tends to convert from "basic disk" to "dynamic disk" format, either without warning you or without making it sufficiently clear why this is a bad thing to do. Thus, if you decide to start fresh or convert back, you should be sure *not* to use the standard Windows tools to create new partitions. You can shrink your existing partitions and even move them around using the Windows tools, but don't try to create new partitions; leave that to Linux tools (or perhaps to third-party Windows tools that are clearer about what they do).

---

### Post by donten on 2011-05-15
First let me say that I admire the efforts of those who frequently give up their time to help the newbies discover the joys of using Linux.  While I recognize that these selfless acts introduce the new user to the community and thereby contribute to the cause, I cannot help but feel sorry for those people who in good faith set out to install Ubuntu (or Kubuntu) and end up in this forum trying to get answers to their problems.
This is not where they should be - they should be having fun exploring this great OS.  These defects (and that is what it is after all) should not be allowed to continue unfixed like this.  To put it another way...the installation process is the first introduction to the OS for all new users.  It is the very first impression that a potential convert experiences.  And for a new user to encounter all this hardship in their first interaction with a product is nothing short of emabarassing and I would not blame anyone for never returning to Linux after an experience like this!
It is simply inexcusable to have the product hoist the colors to a new user in the form of this trial by fire.
I have searched through these threads and it is evident that this problem has gone on for quite some time.  
When I installed Ubuntu on my crappy old HP notebook, the install went by without a hitch.  I have just built a new I7 machine with 1Tb HDD and Win7 and three partitions and gues what....sure enough, I have exactly the same result in the install as the people above.   Oh yes, I grant you that one problem may not be exactly like another but you know what, I DON'T CARE.  This sort of thing should not happen and that is all.  The only people benefiting from this fiasco is Microsoft.
BTW - looked at fixparts....clearly could not help to solve the problem but it really does not matter now.  I wasted a day of my time chasing this joke, now I am just not bothering with the OS any more.

---

### Post by pauuthupm on 2011-07-11
what he is trying to say..we insatll Ubuntu inside windows,,,once its completed,,it asks for reboot...now wen we reboot the screen goes to completing installation screen where we get verifying installation process screen which he has posted a screen shot...in that screen we get this error " No root system defined" .. We cannot do anything from that screen..
Now what happens is.. i thought may b the installation was courrpted ,,let me go ahead uninstalll ubuntu from windowsand re install it...so boot to win7,, uninstall Ubuntu11.04 ,,restrt ,,boot back into windows.Here's the catch,,if i run wubi.exe again...i dont get an option to instal inside windows.. i only get demo option or some other option.. No way to install inside windows then,, For this u have a work around,, u got to do a command promt in administrator mode in windows,, and chkdsk /f /r,,, restsrt..chk,, and then u wil b able to install ubuntu again inside windows.. bt we are back to the same problem when it restarts.. :(

---

### Post by Sky High on 2011-08-15
Hi all.
This is my first message to this group so I'd like to say hello. I am very new to Ubuntu although I have some experience with Unix and Linux from the old days.

When I ran into Ubuntu about a month ago I was quite impressed by its appearence and features, so I couldn't stop myself from trying it out. I downloaded Wubi for 11.04 and got to the same problem alright like others where the installation hung with "no root file system is defined". Now I do have the bad habit that I can not stand being stopped by what looked like a small technical issue. After all, the "demo" mode (running from the iso without installing) worked fine and I could access all my partitions without a problem.

So I ended up investigating and debugging and although it did cost a lot of more time than anticipated I eventually found a solution and am running Ubuntu with wubi with great pleasure now. The solution consists of patching a couple (3) of Ubiquity scripts.

As this issue seems to hamper quite some people I certainly do no mind sharing my solution, but I am not sure how to do that. In the first place, is this the right forum and group for this? Or is launchpad the place to go? Though I do not know how that works either.

Furthermore, the solution might be quite specific for only a limited number of cases. The problems I fixed are apparently related to the use of a firmware raid 0 drive set (also affectionately called fake-raid). So it may not be of help for other situations. And I even can not tell if it might be harmful.

Also, because I am a real newbie to this forum, I am quite probably violating some "rules" or habits so I like to get some assistance from the group to help me out in uploading the patches and description.

regards
- Eric

---

### Post by bcbc on 2011-08-15
Sky High,

Generally a fix involving ubiquity patches will probably be better on launchpad.net. Ubuntuforums.org has so many support threads on the subject it could get buried here. e.g. here is a blog with links to launchpad.net on the subject of raid 10 issues: [http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/](http://rbtcollins.wordpress.com/2011/06/30/dmraid-fakeraid-mirror-striped/)

If your solution differs or has something to add then you can probably add it to the linked launchpad bugs or create new ones and publish the patch there. 

(I'm certainly curious to read about it, because I've seen a couple of people with raid0 having problems)

---

### Post by Sky High on 2011-08-15
Thanks bcbc . I think my problem was of a different nature.
So for follow up I posted the question on Ubuntu launchpad #168097
- Eric

---

