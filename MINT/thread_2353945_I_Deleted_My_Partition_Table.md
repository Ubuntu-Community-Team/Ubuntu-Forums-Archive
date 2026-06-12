---
title: "I Deleted My Partition Table"
date: 2017-02-26
forum: MINT
---

### Post by Linuxuser3 on 2017-02-26
Hello!
I made some dumb decisions and completely deleted and overwrote my partition table (DOS type) on my one terabyte drive

My partitions used to be as follows:
Partition 1: (NTFS) Windows 7 (about 880 gigabytes)
Partiton 2: (SWAP) Linux SWAP (10 gigabytes)
Partiton 3: (ext4) Linux Mint (about 45 gigabytes iirc)

I have tried for *many hours* trying to figure this out
My friend insists that it is an easy fix.

Heres what i have tried so far:
Testdisk:
```
The harddisk (1000 GB / 931 GiB) seems too small! (< 1622 GB / 1511 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partition can't be recovered:
     Partition               Start        End    Size in sectors
>  FAT12                63093   0  1 197290  26  6 2155876449

```

Gpart
Gparted live cd (Returns ```
kernel panic-not syncing vfs unable to mount root fs on unknown-block (1,0)
``` on boot)
[URL="http://www.tldp.org/HOWTO/Partition/recovering.html"]this (even with fdisk -c=dos)
[/URL]
Some notes:
-fdisk tells me that my logical sector size is 512, and physical sector size is 4096
-I am getting confused with all of these darn numbers (i passed math class with a 51% last semester if that has any meaning)
-I don't think i overwrote anything but y'know, anything is possible

Any help is appreciated and ily have a nice day :)

---

### Post by oldfred on 2017-02-26
Does testdisk show all partitions?
It often shows multiple versions as it finds all the old partitions, so if resized several times it may show all of them. You have to pick the combination that does not overlap and was your old configuration.

       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) 
            Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step) 
    
Some also like parted rescue, if you have approx. start & end in sectors for partition.
       Used parted rescue
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)
backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT.txt
So you know sectors:
sudo parted /dev/sda unit s print

---

### Post by LostFarmer on 2017-02-27
> I made some dumb decisions and completely deleted and overwrote my partition table (DOS type) on my one terabyte driveWhat program or  terminal command was used ?  Do you know if the hdd is GPT or MBR partitioned ?

---

### Post by howefield on 2017-02-27
Moved to the "*MINT*" forum.

---

### Post by Linuxuser3 on 2017-02-27
MBR
I used the windows installer to make the first partition, and Linux mint installer to make the other 2.

---

### Post by LostFarmer on 2017-02-27
Just what did you do to delete the partition table ?    when you ran 'testdisk' it will make a log file at /home/username/testdisk.log , can you post it ?  It might give us some lite on your problem.

---

### Post by Linuxuser3 on 2017-02-27
uhh well its quite embarrassing actually...
i opened gparted with the intent of shrinking my windows partition, and i went "Hey, i dont need to waste 10GB on SWAP!" and deleted the swap partition. Then i noticed that the EXT4 partition was also gone! The session was still live, and i knew i couldnt really reboot... So i tried for about an hour to fix it, then made the dumbest decision ever. I pressed the "create new partition table"...
I have since then tried to make a new partition table, and i did it wrong. So no real chance of just recovering the table from there.

Anyways, the output of testdisk after both a quick scan and deeper scan are [here]("http://pastebin.com/65mc02DW")
Some noticeable things (to me at least) are that: It shows the SWAP partition values perfectly, and the SWAP is in between both other partitions. I figure that if i make a partition from the first sector to the start of the swap, then from there to the end of swap, and from there to the last sector, it should be fine. Also, it says "Warning: the current number of heads per cylinder is 255 but the correct value may be 16.", which could be an issue i guess

Thanks for the responses guys!

---

### Post by LostFarmer on 2017-02-27
Lets make a guess that the first partition starts at the 1m bounty (2048th sector).  You can use 'dd' to look at the data and see if it is a NTFS boot record, if so it will contain at beginning offset 28 the total number of sectors in partition.

Will show you what the boot record for win7-10 should look like. (first sector for MS Windows 7-10)
[http://www.ntfs.com/ntfs-partition-boot-sector.htm](http://www.ntfs.com/ntfs-partition-boot-sector.htm)
[http://thestarman.pcministry.com/asm/mbr/W7VBR.htm](http://thestarman.pcministry.com/asm/mbr/W7VBR.htm)

sudo dd if=/dev/sda skip=2048 count=1 bs=512 | hexdump -C  (not sure if hexdump is include with the live linux cd, if the command give a error command not found try
sudo dd if=/dev/sda skip=2048 count=1 bs=512 | hd

Make sure that /dev/sda is the correct hdd.
if the first line contains 'NTFS' post the 3rd line offset 20. so the total sector count at offset 28 can be calculated.  The number will be in [FONT=Arial][SIZE=4]*little-endian*[/SIZE][/FONT] format.  where 123456 would be 563412 hex, will need to add 1 for the correct sector #.   Then the last sector can be checked for the same dd output , then the last sector is verified and the data can be written to the MBR with fdisk ,sdisk.

---

### Post by Linuxuser3 on 2017-02-27
Here is the result of the first command:
```
$ sudo dd if=/dev/sda skip=2048 count=1 bs=512 | hexdump -C 
1+0 records in
1+0 records out
00000000  78 02 00 4d 53 57 49 4e  34 2e 31 00 02 40 68 00  |x..MSWIN4.1..@h.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 40 7f 6d df 6b 03 00  00 00 00 00 02 00 00 00  |.@.m.k..........|
512 bytes copied, 0.000270273 s, 1.9 MB/s
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 62 19 b3 32 4e  4f 20 4e 41 4d 45 20 20  |..)b..2NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 00 00 00 00 00 00  |  FAT32   ......|
00000060  40 45 00 9c 2f 7f 00 00  78 00 00 9c 2f 7f 00 00  |@E../...x.../...|
00000070  20 4d 00 9c 2f 7f 00 00  90 1d 00 9c 2f 7f 00 00  | M../......./...|
00000080  c1 59 70 74 00 00 00 00  ef 13 00 00 00 00 00 00  |.Ypt............|
00000090  af 6d 70 74 00 00 00 00  ff ff ff ff 08 00 00 00  |.mpt............|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000000b0  c0 00 00 00 00 00 00 00  64 00 00 00 00 00 00 00  |........d.......|
000000c0  00 00 00 00 00 00 00 00  50 45 00 9c 2f 7f 00 00  |........PE../...|
000000d0  20 4d 00 9c 2f 7f 00 00  90 1d 00 9c 2f 7f 00 00  | M../......./...|
000000e0  3f 00 00 00 00 00 00 00  c1 07 00 00 00 00 00 00  |?...............|
000000f0  ff 07 00 00 00 00 00 00  ff ff ff ff 04 00 00 00  |................|
00000100  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000110  00 00 00 00 00 00 00 00  f1 00 00 00 00 00 00 00  |................|
00000120  20 1d 00 9c 2f 7f 00 00  60 50 00 9c 2f 7f 00 00  | .../...`P../...|
00000130  20 4d 00 9c 2f 7f 00 00  90 1d 00 9c 2f 7f 00 00  | M../......./...|
00000140  00 08 00 00 00 00 00 00  c1 25 ff 6c 00 00 00 00  |.........%.l....|
00000150  c0 2d ff 6c 00 00 00 00  01 00 00 00 00 00 00 00  |.-.l............|
00000160  10 54 c9 b1 2f 7f 00 00  00 00 00 00 00 00 00 00  |.T../...........|
00000170  b0 45 00 9c 2f 7f 00 00  91 00 00 00 00 00 00 00  |.E../...........|
00000180  10 4d 00 9c 2f 7f 00 00  90 24 00 9c 2f 7f 00 00  |.M../....$../...|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001b0  40 00 00 00 00 00 00 00  54 00 00 00 00 00 00 00  |@.......T.......|
000001c0  00 00 00 00 00 00 00 00  00 08 00 00 00 00 00 00  |................|
000001d0  c1 25 ff 6c 00 00 00 00  c0 2d ff 6c 00 00 00 00  |.%.l.....-.l....|
000001e0  00 20 21 00 0b fe ff ff  00 08 00 00 c1 25 ff 6c  |. !..........%.l|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

Im not sure if FAT32 is what we are looking for here, but i certainly dont see NTFS anywhere.
Thanks again for the help!!

---

### Post by LostFarmer on 2017-02-28
The dd' dump indicates that FAT32 partition took most of the hdd space, so it is not what you want.  An old deleted partition.
The next step to find the correct start sector manually (the only way I know how) .  Normally testdisk works 

in terminal:"  sudo hexeditor -d /dev/sda  "  Note:verify sda is correct hdd  Note: program will not be writing to hdd

Control + W for search  (look at bottom of hexeditor for control keys)
new box pops up select "search for Hex bytes" Note: use arrow keys and press enter
new box type in "eb 52 90 4e 54 46" Note:do not enter the spaces and prss enter  Note: if your keyboard has right side number keys its enter may not work.

The search should only display if the first line has ".R.NTFS" at its start.

verify that the[COLOR=#2f4f4f] offset (left side digits '[/COLOR][COLOR=#000080]3D100000[/COLOR][COLOR=#2f4f4f]'[/COLOR] =[COLOR=#ff0000]Hidden Sectors[/COLOR] X 200)
 also verify that the [COLOR=#000080]offse[/COLOR]t/200= a whole number (no fraction /leftover)
if the [COLOR=#000000]a[/COLOR]bove 2 test are not met , search for next match

from my hdd:
[COLOR=#000080]3D100000[/COLOR]  EB 52 90 4E  54 46 53 20   20 20 20 00  02 08 00 00              .R.NTFS    .....
3D100010  00 00 00 00  00 F8 00 00   3F 00 FF 00 [COLOR=#ff0000] 00 88 1E 00[/COLOR]              ........?.......
3D100020  00 00 00 00  80 00 80 00  [COLOR=#800080] FF BF 04 00  00 00 00 00[/COLOR]              ................

Number of Hidden Sectors-OFFSET (1C-1Fh)-[COLOR=#ff0000]-00 88 1e 00=1e8800 hex = 2000896[/COLOR]
Total Sectors-OFFSET (20-2f)--[COLOR=#800080] ff bf 04 00 00 00 00 00 =04bfff hex=311295[/COLOR]
Hidden + Total = Last sector ([COLOR=#ff0000]2000896[/COLOR]+[COLOR=#800080]311295[/COLOR]=[COLOR=#800000]2312191=******[/COLOR][COLOR=#000000])[/COLOR]
the start sector data = last sector data, if not wrong sectors

One partition on my hdd :2000896 start   2312191  last 152.0 MiB 
one sector is 512 bytes ==200 hex bytes

sudo dd if=/dev/sda skip=[COLOR=#800000]******[/COLOR] count=1 bs=512 | hexdump -C Note: run to compare first and last sector.the first 5 lines are important.

Hope you can understand my poor instructions, if not ask.  Must be off to sleep.
If you find the correct sector #'s be sure to write them down., for next step.



to search for next pattern match - control +w--select next--enter

---

### Post by Linuxuser3 on 2017-03-01
"hexeditor" doesn't exist. Did you mean something else?

---

### Post by LostFarmer on 2017-03-01
just noticed when one runs the program it is 'hexeditor" but to install the name is 'ncurses-hexedit'.

to install:
sudo apt -get update
sudo apt -get install ncurses-hexedit

---

### Post by Linuxuser3 on 2017-03-04
Sorry for the big delay, my friend assisted me in recovering my linux partition (yay!), however, the windows partition was giving me trouble. I tried making an ntfs partition from 2048 to the start of the SWAP partition. This did not work. I then googled for a while, and came across a different thread. I used a command they gave, and it STARTED FORMATTING THE PARTITION!! I mashed ctrl + c a bunch to no avail. I then ALT + F4'd, and it closed. Now the partition is corrupted! ](*,)
The command i ran was makentfs /dev/sda1, with sda1 being the "windows partition" (2048-start of swap). I thought it would just set the type to ntfs, not change the whole file system!!
I know that the data is recoverable still, but the format only ran for 3 seconds.
;-;

---

### Post by Linuxuser3 on 2017-03-10
bumpo

---

### Post by oldfred on 2017-03-10
In 3 sec a lot of damage can occur.
Not familar with makentfs command?

You can use Disks, it has both format & change partition type, but have to be careful not to choose the wrong one.

Have you tried chkdsk. That almost always should be one of the first repairs done to NTFS partitions, but that must be run from Windows or your Windows installer or repair disk with its repair console.

---

### Post by Linuxuser3 on 2017-03-10
I want to try chkdsk so bad, but i only have a windows xp install disk.. When i googled if it was the same, the [results]("https://superuser.com/questions/322331/is-it-safe-to-use-chkdsk-exe-of-the-windows-7-dvd-on-windows-xp-repair-mode-i") seem to show that the chkdsk for xp is different from 7.

---

### Post by oldfred on 2017-03-10
I only had XP and did create a Windows 7 repair disk back when that was a free download.
And chkdsk in XP kinda worked, but ran Windows 7 repair disk's chkdsk. It fixed more things, but converted the NTFS partition boot sector (PBR) to use bootmgr to boot, not XP's ntldr. That is in PBR, so I had to further repair my XP to convert back.

You probably can download any of the newer Windows legal from Microsoft as they let you run it for 30 days before you have to pay for it.
Then you have an installer with a repair console or can temporarily install it and make a newer repair disk.

         Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

For the current version of every operating system your install, you need to have the repair disk or an installer that can also run repairs like Ubuntu's live installer.
I typically have several flash drives and some multi-boot various ISO as repair tools.

---

### Post by Linuxuser3 on 2017-03-11
Ok so i made a repair disk, and tried to do "chkdsk c:" and it told me that it was RAW filesystem. I have the windows partition set to "HPFS/NTFS (Bootable)", and im not sure if that is correct.
Thanks again for the help, you are keeping me sane by giving me hope lol

---

### Post by oldfred on 2017-03-11
RAW means Windows thinks it is unformatted.
It looks at the partition boot sector, or PBR or BS.

You may have a backup? Some have written grub incorrectly into the PBR and then Windows sees it as RAW.
You can try same fix of restoring from backup if available.
If backup not available, use testdisk to create new  - rebuild BS, but I think that is still an XP type, but chkdsk from Windows 7 or later will convert it.

       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by Linuxuser3 on 2017-03-14
I ran testdisk and told it to rebuild the BS, although i am still unsure whether or not my partition does start at sector 2048. Testdisk ran for a long time, but it just went back to this screen: [ATTACH=CONFIG]274149[/ATTACH]  
Is there any way to be certain where my partition begins?

Thanks

---

### Post by oldfred on 2017-03-14
Old XP systems started at sector 63, new systems start at sector 2048, but that is really required for new 4K drives or SSDs.

---

### Post by Linuxuser3 on 2017-03-14
Hello
I just checked my partition table, and i did indeed set my partition to start at 2048, which would be correct for a 4k physical sector drive.
This is what fdisk returns when i do the p command:[ATTACH=CONFIG]274152[/ATTACH]
The next question then would be why testdisk didn't seem to do anything when i told it to rebuild the boot sector..

Thanks!

---

### Post by oldfred on 2017-03-14
It just resets the NTFS partitions boot sector to be NTFS.
But it probably is the XP type.
You almost always have to run chkdsk from your Windows repair disk to totally fix it then.

Does testdisk now show boot sector as good?

If you looks at dump, that compares backup vs current.
When I ran a Windows 7 chkdsk on my XP install, the dump showed on second page that one said bootmgr (Windows 7) and the other ntldr (XP). I then ran XP chkdsk again and it fixed it so I could boot XP.

---

### Post by Linuxuser3 on 2017-03-14
oh my gosh i just remembered, when i first set up this computer, i had windows xp, then installed another xp with the same partition. Then I installed 7 on the same partition. I remember now that i had 3 windows folders, one called "windows", one called "windows.old" and one that was like "windows.1" or something. So it would have been an XP made partition!

No, the one time i ran testdisk and told it to rebuild the bs it took a long time then returned the same screen saying they were bad.

Here are the results of the dump: [http://pastebin.com/AvRDSrV5](http://pastebin.com/AvRDSrV5)
It doesnt give me the option to "Backup BS" if that means anything..

Thank you!!

---

### Post by oldfred on 2017-03-14
All zeros looks like an unformatted partition on a new drive.
Some random data then in backup looks like unformatted partition that overlapped old data.

Once you installed Windows 7 you converted BS from XP style to Windows 7 style.

If backup is bad, it may not copy it.
And the backup is created when you create a new BS usually by formatting the NTFS with standard formatting tools.

---

### Post by Linuxuser3 on 2017-03-14
So.. what do i do? it doesnt give me the option to recover backups on testdisk.. Should i just make the partition start at 63/64 and run testdisk again?

---

### Post by oldfred on 2017-03-15
With testdisk you let it find partition, not create one & expect it to recover data.

If testdisk cannot find partitions, then you may have to use photorec. 
But then it is much easier just to restore from backup.

---

### Post by Linuxuser3 on 2017-03-15
Testdisk deep search shows a bunch of random Linux partitions, and a couple FAT12's. I think at this point i would be fine with buying a new drive and photorec'ing the files to it. I just wanna make sure that is the only option.

---

### Post by oldfred on 2017-03-15
Some Windows tools may work better for NTFS partitions.

       An alternative Windows data recovery program is Recuva -- and it is free
[http://ubuntuforums.org/showthread.php?t=2247461](http://ubuntuforums.org/showthread.php?t=2247461)
[http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950](http://ubuntuforums.org/showthread.php?t=2236951&p=13086950#post13086950)
You could start by using Recuva -- to see what it finds. If it doesn't work, you should then try RecoverMyFiles -- to see what it finds.
NTFS file recovery suggestion by Mark Phelps (not free but works)
[http://ubuntuforums.org/showpost.php?p=12490412&postcount=4](http://ubuntuforums.org/showpost.php?p=12490412&postcount=4)

---

### Post by Linuxuser3 on 2017-03-15
I think i will buy a new hard drive tonight/tomorrow, install windows 7 to it, and put my current drive in as a slave. Then use recuva to copy from the old to the new. 

Thank you so much for all of your help!!

---

### Post by Linuxuser3 on 2017-03-15
Ok so i bought a new tb disk and i have them both in my computer right now. I also installed windows 7 to the new drive, and I tried recuva. It doesnt recognize the fs, which makes sense. I ran photorec, and realized that it just dumps the data. No file names or directories. I researched more, and it seems like it wouldnt be necessary to just dump all the files in a huge pile.
I am currently thinking about making a "new" partition on my old drive that covers approximately the same sectors as Windows did, then using ntfsfix to make it readable. Then i can use Recuva.
If this were to work, i need to know absolutely what sector the partition starts at. Is there aaaaany way to know for sure?
Thanks, im excited!

---

### Post by oldfred on 2017-03-16
I think testdisk searchs for the starts & ends of partitions. It does the scan for you.
So if it is having issues then it may be difficult. 
I include in my normal backup a copy of bootinfoscript which includes a copy of current partition table.

Ntfsfix does very little, it mostly turns on the chkdsk flag so Windows will run chkdsk on the NTFS partition when booted.
Better to use Windows tools and chkdsk directly, but you have to know partitions.

Does drive say it is ok in smartdata?
You can use Disks and click on upper right corner.
Smartdata can also run lots of tests on drive, but all I know is good or bad.

---

### Post by Linuxuser3 on 2017-03-16
Testdisk only shows CHS (Cylinder, Head, Sector) format which is usesless. Testdisk also has never shown an NTFS partition.
Are you sure it isnt an option to manually make the partition? It cant be *that* hard, right?
 I used Hexedit last night and found the sectors of where i think got formatted.

Drive is OK

---

### Post by Linuxuser3 on 2017-03-16
UPDATE: I ran testdisk with the partition table type set to "None". Now i get tons of partitions, and lots that are NTFS. I found some that have a folder called "System Volume Information" which is a good sign. All i need to do now is pick the right ones...

UPDATE 2: I FOUND THE PARTITION AND I CAN READ THE FILES AND IM SO HAAAAAAPPY
Now to add it to my partition table eeeeeeeeeeeeeeeeeeeeeeeeeeee

How can i ever repay you?!!
oh man im am just shaking with excitement

UPDATE 3: it would appear that testdisk cannot add partitions that it finds with the table type set to "None". I am unsure what to do about that, as i dont think Intel would show the NTFS.

---

### Post by oldfred on 2017-03-16
Normally partition table should be either MBR(msdos) or gpt(GUID).
If Windows was installed in BIOS mode, you had to have MBR.
If Windows was installed in UEFI boot mode, you have to have gpt.

---

### Post by Linuxuser3 on 2017-03-16
I am following this guide from this [thread]("https://ubuntuforums.org/showthread.php?t=387922&page=3"):

> 
1.  Make sure that testdisk is creating a log file as it goes.
2.  Use the "Analyse" feature on your "None" partitioned disk.
3.  After it finds the partitions, open up your log file.

In my case, the reason the NTFS partitions were not reading in the "PC"  partition section was that the wrong Head and Sector #s were being used.   The proper #s are listed in the log file.  It looked something like 

D 35 heads/cyl(NTFS) 24 sectors/track : hdd 255 heads/cyl 64 sectors/track
So, in my case the partitions were use 35 heads and 24 sectors instead of the default 255/64.

4.  After you've figured out the proper number of heads and sectors for  your partition(s), fire up testdisk again, but this time select "PC" for  partition type.
5.  Go into "Options" and then "Geometry".
6.  Now change the cylinders and heads to the proper #s.
7.  Run "Analyse" and the partitions should show up and be writable to the partition table.


I am currently running a "None" scan in the hopes that i will be able to get the proper geometry, then i can run an Intel scan and be able to write the partition to the table.

---

### Post by Linuxuser3 on 2017-03-17
Heres an issue with this plan: When i run a "None" scan, it pulls up maybe 40 partitions. The first one is correct, but cannot be added because it is a None scan.
I tried some other geometries and it didnt show the partition.
So i tried parted rescue, which returned nothing
Then i tried Gpart, which ran for a bit, then returned: 
> Possible partition(Windows NT/W2K FS), size(953859mb), offset(3229mb)

*** Fatal error: dev(/dev/sdb): seek failure.


I screenshotted the partition as it appeared in the none scan: [ATTACH=CONFIG]274185[/ATTACH] (the one highlighted)
I think what i need now is a new command that will allow me to use all of this new information and just create the darn partition, regardless of corruption
Then i can just run chkdsk and fix everything
Then i may have to replace the boot sector using Testdisk

UPDATE: ran gpart with a sector size of 4096, it ran much longer. But it seems like gpart takes 12 hours to run.. So now im downloading knoppix

---

### Post by oldfred on 2017-03-17
If you were able to see files with a deeper search you should immediately copy those to another drive.

---

### Post by Linuxuser3 on 2017-03-17
Most folders appear to be empty, probably because of the partial format.
I can't see anything in: users, Windows, program files, and some user made folders.
But I can see some files (of little value) that appear correctly.
I need to chkdsk it, which means I need to have a proper filesystem, which means I need the partition back the way it was.

---

