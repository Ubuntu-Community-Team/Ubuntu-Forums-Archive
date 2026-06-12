---
title: "installation blues"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by ascelpius07 on 2011-04-21
hello all,

this is my very first day with Linux and obviously i'm facing a few  problems. i currently have windows 7 ultimate 64-bit along with windows  xp sp3 on my system. both are in separate partitions and while creating  partitions i had kept a spare 50GB partition for installing Linux which,  to date, is empty.

now i downloaded Ubuntu 11.04 beta 64 bit setup and was trying to install, but it gave me a couple of problems

1) when i tried a complete installation, it did not detect any existing  operating system and gave me two options - either erase my entire HD or  manually setup the partitions. when i tried to manually set up, it once  didn't show any partitions at all on /dev/sda1. i didn't create a fresh  partition table because i didn't want to lose my existing data, so i  quit the installation.

2) i tried to install it within windows 7, using wubi. when it asked me  for the partition in which i wanted to install, i told it to install it  in the 50GB spare which i already had for linux (windows 7 is installed  in a separate partition). it was installing fine but when it rebooted,  it gave me the message - Root file system not defined. Correct it from  the partitioning menu. i tried to access my hard disks but gparted won't  run (showing some error like "can't copy from /user/something  something") and although disk utility did run but it wouldn't do any  task giving me the message "daemon is being inhibited". being new to  linux i didn't have any idea what to do about these so once again i'm  back to windows 7, clueless...

can somebody please help me and guide me? and guys, i'm an absolute beginner so a little bit of spoon feeding won't hurt...

thanks

---

### Post by dino99 on 2011-04-21
follow this help for a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

note:
- when you make installation, nothing else have to disturb it, so close all apps/services calling hdd
- your existing distro have to be cleaned/defraged
- organize your partitions: max 3 "primary" partitions, its better to create a huge extended one and then create the next ones into it
- let windows at the beginning of hdd partition

---

### Post by Elfy on 2011-04-21
moved to natty

---

### Post by Blasphemist on 2011-04-21
boot to the iso please, choose try ubuntu, run gparted and update your post with a screen shot of that. That may help explain why the install isn't seeing your existing partitions.

---

### Post by ascelpius07 on 2011-04-21
following is the screenshot when i run gparted... from what i understand it seems to be having troubles identifying the partition table. how can i fix that? i don't even know the current partition system on my hard disk
[ATTACH]189648[/ATTACH]

second and third attachments show the ubuntu installer's response. it does not detect any existing operating system and gives me two options (the second screenshot). when i click on the second it shows me what's there on the third screenshot. once again the entire disk is clean and it expects me to create a fresh partition table.
[ATTACH]189649[/ATTACH]

[ATTACH]189650[/ATTACH]

my current windows7 is completely defragmented and chkdsk isn't showing any file system errors. my hard disk has 8 partitions, of which 2 are primary and the rest are logical. windows7 is installed in a logical partition (i don't know if that makes any difference)

PS : about the duplicate threads, i'm really sorry i did that. actually i first posted in the absolute beginner's section but since i wasn't getting any response there, i figured i better post it in the installation section, and didn't remove the first thread, i apologise and will be more careful in future :)

---

### Post by Blasphemist on 2011-04-21
I am not able to see how you get to windows from looking at this. How many hard drives do you have? Try this please. Go to this link from the try ubuntu when booted to the live cd.
 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

The link will tell you how to install and use the script, and how to get to the results. Please paste the results into your response using the quote tags tool.

---

### Post by ascelpius07 on 2011-04-21
i have only one hard disk of 2TB size. i ran the boot info script and i have attached the result.txt . please go through it and see if you can find some solution.

[ATTACH]189665[/ATTACH]

---

### Post by Blasphemist on 2011-04-21
I think your results.txt got truncated somehow. Could you run the script again and send the new results. It will be results1.txt if you do everything in the same directory.

From what I see I haven't figured it out. You do have many more partitions than I do but you also have a lot more drive. Not that means you should make more partitions necessarily. Others will see your results and if I can't figure it out, they may.

---

### Post by Blasphemist on 2011-04-21
I think you may have too many primary partitions. Can you use Win 7 disc management to tell me how many it can see? I'm still looking at your results and doing research but let me know this please.

---

### Post by ascelpius07 on 2011-04-21
i'm really grateful for your efforts, man... i'm also trying to do some research, but its really an uphill task for me as my knowledge about linux and partitioning of hard drives is almost zilch..

anyway, my disk management says i have 2 primary partitions - drive labels "ROOT XP" (where i have installed winxp) and "SETUPS" (where i have kept the setups of all the programs and games i use)... the rest of the 6 partitions are within a single extended partition, which lies between the aforementioned primary partitions

---

### Post by Blasphemist on 2011-04-21
I do see know that you have sda1 that is primary and sda2 the extended partition. sda5 through sda10 are logical drives to windows within the extended partition. I believe you see them in windows as drives D, E, F and so on. Is D drive your setups drive? Are there logical drives that you don't have anything on? Or could there be? If so, use windows disc management to delete unused logical drives.

This may be wrong, but I think Linux may not be able to shrink the extended partition to put Linux on since it is filled with logical drives. I don't see any harm in removing a logical drive that is unused to test that theory. At worst you could always add it back if that didn't help us figure this out.

I also think you should delete sda11 as it isn't in the extended partition and that looks invalid to me.

After you delete the sda11 and one other logical partition, please see what gparted shows and we can see where to go from there.

---

### Post by Quackers on 2011-04-21
Your apparently truncated boot script output, in code tags
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2048.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr

sda7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda10 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   102,397,951   102,395,904   7 HPFS/NTFS
/dev/sda2         102,397,952 3,907,007,999 3,804,610,048   5 Extended
/dev/sda5         102,400,000   204,795,903   102,395,904   7 HPFS/NTFS
/dev/sda6         204,797,952   409,591,807   204,793,856   7 HPFS/NTFS
/dev/sda7         409,593,856   819,185,663   409,591,808   7 HPFS/NTFS
/dev/sda8         819,187,712 1,638,387,711   819,200,000   7 HPFS/NTFS
/dev/sda9       1,638,389,760 2,457,589,759   819,200,000   7 HPFS/NTFS
/dev/sda10      2,457,591,808 3,276,793,855   819,202,048   7 HPFS/NTFS
/dev/sda11      3,276,795,904 3,907,008,511   630,212,608   7 HPFS/NTFS

the logical partition /dev/sda11 is not contained in the extended partition /dev/sda2

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda10       FC48925E4892180A                       ntfs       Visual Delights               
/dev/sda11       0E70A13570A12505                       ntfs       Set ups                       
/dev/sda1        14AC407EAC405C7C                       ntfs       Root XP                       
/dev/sda2: PTTYPE="dos" 
/dev/sda5        D07C4F147C4EF4AE                       ntfs       Root Linux                    
/dev/sda6        D4F45A19F459FDE4                       ntfs       Root 7                        
/dev/sda7        8E846B94846B7D99                       ntfs       Spare                         
/dev/sda8        8C7C745A7C74414E                       ntfs       Installations                 
/dev/sda9        F89884CA988488B8                       ntfs       Music                         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

;

;Warning: Boot.ini is used on Windows XP and earlier operating systems.

;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.

;

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT /NOEXECUTE=ALWAYSOFF
```

According to your boot_script output (limited though it is) your problem is the red bit
```

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   102,397,951   102,395,904   7 HPFS/NTFS
/dev/sda2         102,397,952 [COLOR="Red"]3,907,007,999[/COLOR] 3,804,610,048   5 Extended
/dev/sda5         102,400,000   204,795,903   102,395,904   7 HPFS/NTFS
/dev/sda6         204,797,952   409,591,807   204,793,856   7 HPFS/NTFS
/dev/sda7         409,593,856   819,185,663   409,591,808   7 HPFS/NTFS
/dev/sda8         819,187,712 1,638,387,711   819,200,000   7 HPFS/NTFS
/dev/sda9       1,638,389,760 2,457,589,759   819,200,000   7 HPFS/NTFS
/dev/sda10      2,457,591,808 3,276,793,855   819,202,048   7 HPFS/NTFS
/dev/sda11      3,276,795,904 [COLOR="Red"]3,907,008,511[/COLOR]   630,212,608   7 HPFS/NTFS
[COLOR="Red"]
the logical partition /dev/sda11 is not contained in the extended partition /dev/sda2[/COLOR]
```
In other words your sda11 partition is 512 blocks outside the extended partition. This is an illegal situation, as far as partitioning is concerned. Is there anything in sda11?

Also, as the disc appears to be filled with partitions, there is no space for Ubuntu to install into!

---

### Post by Blasphemist on 2011-04-21
So unlikely as it may be, someone with a ton of beans agrees with my diagnosis. He did figure out more than I did but I believe the solution is still what I described. Delete a logical partition or more than one. I think you have to delete sda11 but you could try one of the others if you think you need to.

---

### Post by Quackers on 2011-04-21
It is possible that deleting the sda11 partition could fix the partition table, but there are risks.
Alternatively there is a program written by a forum member (srs5694) which has fixed a similar problem for me recently. Here is a link to the details
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Even if the partition table is fixed, it still leaves Ubuntu with nowhere to install to,  as it can't go in a NTFS partition.

---

### Post by Blasphemist on 2011-04-21
ascelpius07, quakers passed a way to fix the partition table but said there are risks. I can't tell you if you should use fix parts first and then delete the partition to free up space for the install or just delete the partition or partitions. So, you should get backed up it seems to me as there may be risks either way. Sorry I can't be more sure of the risks.

---

### Post by Quackers on 2011-04-21
That's good advice from Blasphemist!
Although partitioning goes well more than 95% of the time, on the occasions that it doesn't go well you MUST have a means of recovering everything. Also, please remember that if partitioning goes really badly it can wipe out everything - including any recovery partition! It is wise to make a Windows recovery cd (often called a Windows repair cd) but it is much more important to make a set or two of recovery dvd's (which is effectively a copy of your recovery partition).

---

### Post by ascelpius07 on 2011-04-21
ok i do see now that there is some discrepancy with the partitions on my hard disk. boot info script and fdisk say that sda11 is a logical partition, but at the same time its showing the volume label as "setup", but when i run disk management in windows 7, it shows that same volume as a primary partition and not a logical one. also, it is showing some unallocated space (9MB or something) next to that primary partition. boot info script is showing only 1 primary and 1 extended, while disk management is showing 2 primaries and 1 extended. i do have important data in that volume, but i can make a backup and delete that volume i guess. but i did notice another thing in the boot info result which i would like to know - why are there missing blocks between the end of one logical partition and the start of the next one? its happening almost in every partition... even sda5 isn't starting at the same place as sda2. why is that happening?

---

### Post by Quackers on 2011-04-21
sda1 is a primary partition
sda2 is an extended partition (which is a different kind of primary partition)
sda5 and above are logical partitions which are within the extended partition (or should be :-) )

The discrepancy in start sectors is due to the partitions now starting at sector 2048, I believe.

Windows Disk Management screen on my system shows that I have 8 primary partitions. This is nonsense :-)  Windows has problems figuring out Linux partitions.
I would suggest that you back everything up (and make sure you have a system recovery option - other than the recovery partition) then give Fixparts a try.
It looks rather daunting, but it's easier than it looks. The instructions are there. It fixed my problem (similar to yours) in 2 minutes.

---

### Post by ascelpius07 on 2011-04-21
and yeah... one more thing... how should i create a non-ntfs partition for linux to install?

---

### Post by Quackers on 2011-04-21
> **ascelpius07 said:**
> and yeah... one more thing... how should i create a non-ntfs partition for linux to install?

With gparted on the live cd, or by selecting the manual option during Ubuntu installation.

---

### Post by ascelpius07 on 2011-04-21
alright... so data backup is in progress right now, lets see what happens... by the way, will fixparts also fiddle with the other partitions, or will it leave them in peace, just taking care of what's going out of line there?

---

### Post by Quackers on 2011-04-21
I have only used Fixparts from within a Linux system, but it should be the same from within Windows.
All you do really is print out (on the screen) your current partition table. The screen "print out" will not include the extended partition but will show all logical partitions. Then, when you write the partition table back to the system a new extended partition is created by Fixparts which includes all the logical partitions. Job done :-)
Take your time reading the instructions and you should be ok :-)

Nothing else should be touched. It doesn't actually write to the partitions - just the partition table.

---

### Post by Blasphemist on 2011-04-21
Do remember from one of quakers earlier posts, and mine less surely, that you will still need to delete a partition (at least one) to get space to install ubuntu on.

---

### Post by ascelpius07 on 2011-04-21
yes... i will have to create a linux partition to install ubuntu... but that thing is second in priority right now... currently the first priority is to take care of the partition table, because only then will gparted will be able to proceed with the partition

---

### Post by ascelpius07 on 2011-04-22
it worked, guys!!!

i didn't have a proper backup but i was so eager to try this out that i risked the files on my system, but the issue got resolved without a glitch. i made a backup of the content on sda11, logged in from windows, ran Fixparts, created space for ubuntu installation by omitting sda5 (which i had kept for a linux installation anyway), created a fresh extended partition and saved the settings, rewriting my MBR.

logged in from liveCD, ran gparted, and voila! everything was there.. all my partitions... ran the installation.. this time it detected windows 7, i told it to install alongside win7 (now i didn't create manual partitions here because i figured there was only one chunk of unallocated space for the installer to work with, so it will automatically create partitions there, without disturbing my ntfs partitions)... gave me a long long wait while it installed, but in the end we emerged triumphant!!! dual boot is also working like a charm and currently i have booted back into my win7. will start exploring Ubuntu from tomorrow onwards.

so anyway thank you Blasphemist and Quackers for guiding me through the entire process. yesterday my brain was absolutely blank about hard disk partitioning, and today, i know an iota, because you guys shared your knowledge with me.... i believe that's the true spirit of UBUNTU... sharing :)

---

### Post by Quackers on 2011-04-22
That's good news! :-) Well done. 
Happy Ubuntu-ing!

---

### Post by Blasphemist on 2011-04-22
Seconded, great news and glad to hear your joining the community.

---

### Post by srs5694 on 2011-04-22
As the author of FixParts, I'm glad it worked for you!

To answer an earlier question that's moot for you, but might be important to somebody else who reads this, FixParts *can* change things like partition ordering, but it shouldn't damage partitions' contents or delete partitions (unless there's a big problem like overlapping partitions). Checking (with the "p" command) is always wise, though, just in case there's a bug (or overlapping partitions!).

Basically, the program loads in the partitions, discards its internal record of the extended partition (but not the logicals it contains), and creates a new extended partition to house any logicals you've got when you write a new partition table. If it detects problems it tries to correct them -- it might reassign primary/logical status or delete one or more partitions if the current definitions are illegal. If the *only* problem going in is a mis-sized extended partition, such changes shouldn't be implemented, at least not automatically. Because of limitations in the program's algorithm for writing logical partition data, it sorts the logical partitions prior to writing them, so the order of logical partitions can change if they're not in sequential order to begin with.

---

### Post by ascelpius07 on 2011-04-22
@srs - your page was really helpful and descriptive.. after going through it one thing was clear to me that my problem was a minor one. it just needed an extended partition which will accommodate those extra 512 sectors. so i was almost sure my data won't be affected. but then it was my first time fiddling with partitions and i had literally no knowledge about all this, so all the apprehension came from there... but in the end it worked precisely the way it was supposed to... so all's well that ended well :)

---

