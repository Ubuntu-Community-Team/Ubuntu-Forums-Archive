---
title: "WUBI fails to install on Mac using iPartition"
date: 2011-07-14
forum: Installation &amp; Upgrades
---

### Post by GSande on 2011-07-14
I have a Mac Pro with multiple NTFS partitions created using iPartition. Windows 7 (32 bit) and Windows 7 (64 bit) work well in separate partitions. I wanted to try WUBI in a separate Windows 7 (32 bit) partition. Windows works and the WUBI install starts. On the reboot there is a display of the four MBR partitions on the two disks. However all the NTFS partitions are labelled "non-MS" with the result that the WUBI installation then cannot find GRLDR (really I think it wants WUBILDR but the message was never updated). Several partition table utilities including Windows itself think the MBR partition table is OK and a couple complain about either bad head geometry or bad cylinder counts. WUBI/GRUB is clearly in the camp with the complainers. 

The folks who supply iPartition blame the other guys and say to not use WUBI at all. Their argument is that a Mac is not a PC which should also apply to Windows. Oh well! The discussion ended up going in small circles with them insisting that their advice was the definitive advice. It appears that WUBI works with a single NTFS partition created using BootCamp. So it seems not all advice is truly definitive. Some aspect of the iPartition created MBR partition table must be slightly different in a way that does not happen with BootCamp.

How does one find out what WUBI is complaining about in adequate and precise enough technical detail to be able to file a bug report that the iPartition folks will treat seriously? Or is WUBI being overly fussy and it can be calmed down enough to take the iPartition created partition table? Or does WUBI/GRUB have a requirement that conflicts with requirements of other sensible requirements on the form of a MBR partition table?

Are there any utilities that can be run from Windows that would help get a better diagnosis?

---

### Post by Rubi1200 on 2011-07-15
Hi and welcome to the forums :-)

I don't know enough about your particular setup to offer any immediate solutions, but the first place to start is by doing the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by GSande on 2011-07-15
Thanks. 

Using an Ubuntu live CD for a good disk utility is much better than hoping for one under Windows.

The bash under MacOsX does not have some of the expected programs so I could not run it there. Not a big surprise.

Hopefully running the live CD will just work.

---

### Post by GSande on 2011-07-15
The live CD just woks. Terminal was not immediately obvious but I found it fairly quickly. Accessories.

The boot_info_script ran with a minor grumble about GAWK. Ir used a substitute. 

The RESULTS,txt is below

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda4/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda5: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:   According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 40.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  -
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb4: __________________________________________________________________________

    File system:       hfsplus
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,001,782,311 1,001,782,311  ee GPT
/dev/sda2       1,001,782,312 1,190,525,984   188,743,673   7 NTFS / exFAT / HPFS
/dev/sda3       1,190,525,985 1,379,269,657   188,743,673   7 NTFS / exFAT / HPFS
/dev/sda4    *  1,379,269,658 1,568,013,330   188,743,673   7 NTFS / exFAT / HPFS


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1              40       409,639       409,600 EFI System partition
/dev/sda2   1,001,782,312 1,190,525,984   188,743,673 Data partition (Windows/Linux)
/dev/sda3   1,190,525,985 1,379,269,657   188,743,673 Data partition (Windows/Linux)
/dev/sda4   1,379,269,658 1,568,013,330   188,743,673 Data partition (Windows/Linux)
/dev/sda5         409,640 1,001,520,167 1,001,110,528 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda6   1,568,013,331 1,756,757,010   188,743,680 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda7   1,757,019,155 1,945,762,834   188,743,680 Hierarchical File System Plus (HFS+) partition (Mac OS X)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                   1   604,160,751   604,160,751  ee GPT
/dev/sdb2         604,160,752   625,142,408    20,981,657   7 NTFS / exFAT / HPFS


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sdb1              40       409,639       409,600 EFI System partition
/dev/sdb2     604,160,752   625,142,408    20,981,657 Data partition (Windows/Linux)
/dev/sdb3      21,938,928   603,898,607   581,959,680 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sdb4         409,640    21,676,783    21,267,144 Hierarchical File System Plus (HFS+) partition (Mac OS X)

"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        2860-11F4                              vfat       EFI
/dev/sda2        85014AF53524E9E9                       ntfs       Win7.32
/dev/sda3        AF0AC6CF2CF9BAAD                       ntfs       Win7.64
/dev/sda4        596C92AC92F4708E                       ntfs       WUBI
/dev/sda5        56123cc6-3e10-3a87-91d0-ad0f04f69e40   hfsplus    Macintosh HD
/dev/sda6        c892f0a7-00ed-319c-bd32-8dd9712cc5c8   hfsplus    P4
/dev/sda7        a11278cb-fb08-3a3c-9964-1d66c53c7368   hfsplus    P5
/dev/sdb1        70D6-1701                              vfat       EFI
/dev/sdb2        30EECB036DD1A22A                       ntfs       Win
/dev/sdb3        ff1724a8-3b69-392b-a265-58e091641ffc   hfsplus    Time
/dev/sdb4        56314cea-767b-31a5-bd07-468803311cc3   hfsplus    Mac

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  3f 00 ff 00 28 00 00 00  |........?...(...|
00000020  00 40 06 00 67 0c 00 00  00 00 00 00 02 00 00 00  |.@..g...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 f4 11 60 28 45  46 49 20 20 20 20 20 20  |..)..`(EFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader on sda4/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200

Unknown BootLoader on sdb1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 01 17 d6 70 45  46 49 20 20 20 20 20 20  |..)...pEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by Rubi1200 on 2011-07-16
Thanks for posting the results.

Again, to stress what I said before, I do not know enough about this particular setup of yours.

However, I do see a problem with the Wubi install and the fix I will suggest only addresses that problem.

In other words, the commands I give you will not affect any other part of the system (unless you make a typo or some other error).

Best to copy and paste the commands to avoid such mistakes.

So, from a LiveCD open a terminal and run these commands:

```
sudo mkdir /media/win
sudo mount /dev/sda4 /media/win
sudo e2fsck -f -y -v /media/win/ubuntu/disks/root.disk
```

After the last command completes (it may take some time), do this:
```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

If you can mount the root.disk then you should be able to reboot the computer, taking out the CD, and have the option to boot into the Wubi Ubuntu install normally.

Good luck and let me know the results please.

---

### Post by GSande on 2011-07-16
Thanks. 

Any hint on the problem you noticed. (Thanks for the fish - ie how to proceed - but I am also interested in how to fish - ie what the problem is - to use the old saying about forms of help.)

The file system check came back with 

```

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /media/win/ubuntu/disks/root.disk
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /media/win/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:

```

which if clearly a problem. My guess is that even if there had not been "non-MS" partitions this would have been a game stopper.

It now seems that there are two issues:

1. the "non-MS" partitions cause the initial reboot to fail

2. the emulated file system would be corrupt if the reboot were to work.

When I first got the bad superblock diagnostic I tried uninstalling WUBI, running CHKDSK in Windows and reinstalling WUBI but nothing changed. So I do not think it something I have done elsewhere.

---

### Post by bcbc on 2011-07-17
I think you're out of luck on this... even if the Wubi boot process (grub4dos) did manage to locate the wubildr, I suspect you'd have issues with the ubuntu installer with the mix of MBR and GPT partition tables.

There is also a bug out there referring to GPT partition tables (EFI boot partitions) that wubi does't work. 

I don't know how iPartition works (or bootcamp for that matter, or macs)... so I really can't offer any comment on that. But there are obviously people using ubuntu on Macs so hopefully one of them can help.  Maybe a direct install would be better than wubi.

---

### Post by GSande on 2011-07-17
Thanks.

My understanding is BootCamp is two things. One is a set of drivers needed to let Windows run the Mac devices. The other is a partition re-sizer and manager to set up an MBR partition table to use the space allocated in the GPT partition table. It only sets up one NTFS partition. Apple supplies BootCamp.

iPartition is a fancier partition manager for the Mac. It also sets up an MBR table for some of the space allocated in the GPT table. Once there is a set of iPartition spaces one then uses the BootCamp drivers.

The initial set of diagnostics was about "non-MS" partitions. Some DOS/Windows partition tools complain about bad head geometry and the "XXX" field and the "YYY" field not having proper values. I would have to run them slowly and copy the details down to give a better report. I was hoping to to get a compact set of diagnostics to be able to figure out if iPartition or grub4dos should take more of the blame for the problem. I would not be surprised if the space that is to be used under both schemes has more restrictions than iPartition is currently meeting. The nuisance is that many DOS/Windows programs could care less so this is more a question of how much back compatibility one wants to insist in. The iPartition folks claim they are good and the others guys are at fault. More detail is needed to make any progress.

I curious that the presence of a GPT should have any effect on what claims to be a purely Windows program. Somebody is peeking that too many things somewhere.

I tried to report the bug on what appears to be a WUBI reporting site but after 20+ tries of guessing "1" vrs "l" of a funny seriffed font on a noisy background I gave up. I must be a machine as I could not past the capcha test. I would be happy to help but at this point I am locked out. :-(

---

### Post by bcbc on 2011-07-17
> **GSande said:**
> I curious that the presence of a GPT should have any effect on what claims to be a purely Windows program. Somebody is peeking that too many things somewhere.

I tried to report the bug on what appears to be a WUBI reporting site but after 20+ tries of guessing "1" vrs "l" of a funny seriffed font on a noisy background I gave up. I must be a machine as I could not past the capcha test. I would be happy to help but at this point I am locked out. :-(

The windows part of Wubi is just what you saw running on Windows. (The windows installer). The rest of it is all Ubuntu and that's the part that will likely complain about the GPT & MBR mix.

Grub4dos is used to hook up with Ubuntu's Grub2... and it will output a diagnostic for each partition it checks...
Try (hd0,n): type: no wubildr

Is this the part you are referring to that says "Non-MS"?

To file a Wubi bug go here: [https://bugs.launchpad.net/wubi/+filebug](https://bugs.launchpad.net/wubi/+filebug)

You will need a launchpad account.

---

### Post by GSande on 2011-07-17
The reboot leads to a table with eight lines, two disks of four partitions each. Six partitions are listed as type "non-MS" with action of "skipped" and two with empty. It matches what I believe is there.

The interesting disk has partition 1 for the Mac and partitions 2, 3 and 4 as NTFS partitions. They are healthy according to the administrative tool for devices in Windows and the Windows hosted in them work as expected.

At the end to the eight lines is the unable to find GRLDR diagnostic which makes sense if there are no NTFS partitions available.

So why do some programs think there are OK NTFS partitions and others reject them? Rather specific reasons are needed if I am to get the suppliers of the Mac partition utility to pay attention.

Maybe all that is needed is for the partitions to start on special segment numbers. If that is all then a delete and rebuild will cure the immediate problem and better documentation will warn others.

The boot/partition problem should be solved but then there is the bad superblock issue the exp2 file system check utility reports.

I spent another not very amusing half hour trying to get past the captcha. Failed again. I must have learned printing and font design in the wrong school as I am pretty sure my glasses are clean. There is not even a scheme to have an email return.

---

### Post by bcbc on 2011-07-17
Just to clarify there is no bad superblock on the wubi virtual disk - it isn't formatted until the second phase of the install - and this is the part you haven't been able to get to. So right now it contains a bunch of hex 30s in the front of the file - that's it.

I can't speculate why grub4dos doesn't see the iPartition 'ntfs' partitions as NTFS. That's problem 1. 
Problem 2 would be Ubuntu - that doesn't like a mix of GPT and MBR partition tables. I think that will be the next hurdle.

---

### Post by GSande on 2011-07-17
I was asked to run the file system check by an earlier replier who seemed to know what was required. All I can tell is that Windows has allocated the file in the NTFS file system. You are telling me that is about what it should be. False alarm averted. Good.

Back to the question of what are the specifications for an NTFS partition? Various programs are either happy or upset with the MBR partition table created by iPartition. It would be nice to know what WUBI/dos2grub/whatever-component-it-actually-is is expecting.

From things I have found using google it appears that the MBR partition table created by the BootCamp partition table component leads to a working Ubuntu under WUBI so one guesses that the hybrid of MBR and GPT is OK in some circumstances. What has Apple's BootCamp done right that iPartition gets wrong?

---

### Post by bcbc on 2011-07-17
> **GSande said:**
> Back to the question of what are the specifications for an NTFS partition? Various programs are either happy or upset with the MBR partition table created by iPartition. It would be nice to know what WUBI/dos2grub/whatever-component-it-actually-is is expecting.

From things I have found using google it appears that the MBR partition table created by the BootCamp partition table component leads to a working Ubuntu under WUBI so one guesses that the hybrid of MBR and GPT is OK in some circumstances. What has Apple's BootCamp done right that iPartition gets wrong?

This is what wikipedia says about bootcamp:
> Its functionality relies on BIOS emulation through EFI and a partition table information synchronization mechanism between GPT and MBR combined.[2]
Maybe it's that 'emulation' that's probably making the difference.

I think that if you paid for iPartition then they should be able to provide a little bit better response than "don't use your mac for windows/ubuntu". That's not really an answer.

Or can you not install directly to the partitions you create? (i.e. not using Wubi?)

---

### Post by srs5694 on 2011-07-17
> **bcbc said:**
> Problem 2 would be Ubuntu - that doesn't like a mix of GPT and MBR partition tables. I think that will be the next hurdle.

The "mix of GPT and MBR partition tables" is known as a [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) It's an ugly and dangerous hack that Apple chose to use as part of getting Windows booted on a Mac; but the Linux kernel sees a hybrid MBR the same way as OS X does -- that is, as a valid GPT disk, ignoring the MBR data. A hybrid MBR works fine (or as "fine" as is possible for something as nasty as a hybrid MBR) on a conventional (non-WUBI) installation of Ubuntu on a Mac.

That said, I don't know enough about how WUBI kicks off the Ubuntu boot process or other WUBI-specific quirks to speculate about whether there would be any WUBI-specific issues with a hybrid MBR. It's entirely possible that there are such issues, but if so, I don't know what they are.

Given that some tools are complaining about head and cylinder counts, it's possible that iPartition created a hybrid MBR that's a bit weird in some way. You could try another tool, such as gptsync or GPT fdisk (gdisk); however, be aware that messing with the hybrid MBR could make Windows unbootable. I recommend backing up your partition table, including the raw MBR data, before you mess with it. GPT fdisk can do this with its backup option ("b" on the gdisk main menu).

You could also try a non-WUBI install of Ubuntu. Since Linux sees disk with hybrid MBRs as GPT disks, there's no need to cram the Ubuntu partitions into the MBR side; Ubuntu will boot just fine with all its partitions available as GPT partitions but not as MBR partitions.

---

### Post by GSande on 2011-07-18
> **srs5694 said:**
> 
You could also try a non-WUBI install of Ubuntu. Since Linux sees disk with hybrid MBRs as GPT disks, there's no need to cram the Ubuntu partitions into the MBR side; Ubuntu will boot just fine with all its partitions available as GPT partitions but not as MBR partitions.


Where would I find a GPT version of Ubuntu? My impression is that the standard ones expect to operate from a MBR setup. The ones I have on my PC operate that way. I was trying WUBI to avoid the joys of extended partitions for Ubuntu/Linux and its swap space as I already have a GPT protective partition for my main Mac space and two NTFS's (Win7 - 32 and Win7 - 64). I want to execute some OpenMP code for timings under Ubuntu as my MAC is both faster and has more cores than my PC.

My take has been that there is some obscure difference in what iPartition has laid down. They look at the MacOsX sourced dumps of the MBR partition table and GPT one and say everything is exactly as they intended. So no corruption but questionable intended form. The diagnostics I have been able to get are so vague and nonspecific that they are dismissed with "the complaint is about something that is OK so the complaint must be about something else not in the diagnostic". That may be the case but it sure is convenient for them.

I have not been able to get any hints of what is causing WUBI/etc to regard the NTFS partitions as sufficiently off specification to be "non-MS". So things end up going nowhere.

---

### Post by srs5694 on 2011-07-18
> **GSande said:**
> Where would I find a GPT version of Ubuntu? My impression is that the standard ones expect to operate from a MBR setup. The ones I have on my PC operate that way.

The standard Ubuntu installer can handle either MBR or GPT; there's no need to locate a special Ubuntu installer just for GPT support. (There are, however, installers intended specifically for Macs, but I'm not sure precisely how they differ from the regular ones.)

> I was trying WUBI to avoid the joys of extended partitions for Ubuntu/Linux and its swap space as I already have a GPT protective partition for my main Mac space and two NTFS's (Win7 - 32 and Win7 - 64).

On a GPT disk, you don't need extended or logical partitions; those concepts are meaningless under GPT. On the MBR side of a hybrid configuration, using extended and logical partitions is an invitation to disaster. Fortunately, I know of no utilities that will help you shoot yourself in the foot by creating such a monstrosity.

> My take has been that there is some obscure difference in what iPartition has laid down. They look at the MacOsX sourced dumps of the MBR partition table and GPT one and say everything is exactly as they intended.

I'd be willing to take a look at what you've got, but I'll need a backup of your partition table. You can create this with my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program (versions for Linux, OS X, and Windows; use whatever's convenient). Use the "b" option on the main menu to create a backup, then e-mail it to me.

---

