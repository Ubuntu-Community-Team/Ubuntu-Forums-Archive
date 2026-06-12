---
title: "Getting disk number for Windows hal.dll problem"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by ray field on 2015-01-20
Unfortunately I have to boot my old XP partition. I'm getting the "missing hal.dll" error, and hoping that editing the Windows boot.ini file will fix it. I just don't know what number to try & hoping someone will be able to take a better guess than I can.

BIOS is set to boot Trusty off an SSD drive (sda), and XP is on the HD -- sdb5, thus

```
NAME   FSTYPE   SIZE MOUNTPOINT                      LABEL
sda           223.6G                                 
&#9500;&#9472;sda1            1K                                 
&#9500;&#9472;sda2 ext4    88.5G /usr/local/data                 
&#9500;&#9472;sda5 ext4    93.1G /home                           
&#9492;&#9472;sda6 ext4    41.9G /                               
sdb             1.8T                                 
&#9500;&#9472;sdb1 ntfs   244.1G                                 
&#9500;&#9472;sdb2            1K                                 
&#9500;&#9472;sdb4 ext4   976.6G /media/whouse                   
&#9500;&#9472;sdb5 ntfs   195.3G /media/raphael/3E3C627C3C622ED9 
&#9500;&#9472;sdb6 swap     9.3G [SWAP]                          
&#9500;&#9472;sdb7 ext4    23.3G                                 
&#9492;&#9472;sdb8 ext4    93.1G                                 
sdc             3.7T                                 
&#9492;&#9472;sdc1 ntfs     3.7T /media/sext                     Seagate Expansion Drive
sdd             3.7T                                 
&#9492;&#9472;sdd1 ntfs     3.7T /media/ext                      Seagate Expansion Drive
sde           931.5G                                 
&#9492;&#9472;sde1 ext4   931.5G /media/extext                   
sr0            1024M                                 

```

(The XP partition is not ordinarily mounted when I boot Ubuntu, I only needed to look at it)

Here's the boot.ini from the XP partition

```
[boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Windows" /noexecute=optin /fastdetect

```

Hopefully just changing those numbers will do it. I *think* I basically tossed my old copy of XP onto it when I built this machine last spring -- er, actually I can't remember, it might even be that I simply added the SSD onto my working system and installed Trusty on that, hopefully that won't make a difference.

---

### Post by yancek on 2015-01-20
xp as other windows systems, needs its boot files on a primary partition.  sdb5 is a logical partition.  What is on sdb1, the other ntfs partition?  I think you need to change the number for disk from zero to one because xp is now on the second drive and it counts from zero as you can see.  xp on sdb5, partition(4).  I don't know that this will repair anything though.

---

### Post by ray field on 2015-01-20
hmm, sdb1 looks like another drive I created, it's got a bunch of Windows stuff on it including a boot.ini file:

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

---

### Post by LostFarmer on 2015-01-20
XP needing its boot files on a primary partition is a misconception.  I have done it many of times.  What is true is one can not install without its boot files going to a primary partition, but can be cloned to a logical partition with its boot files and work.

Did it ever work in its present setup ?  How did you get XP on a logical partition ?  What is on sdb1 ?   Does sdb1 have any XP boot files ?  Just to be sure, is the boot.ini from sdb5 or sdb1 ?
Post the grub.cfg entire for XP.  

Looks like you could use 'testdisk' to change your sdb4 and sdb5 to primary if needed, but always a slight possibility of a problem when changing partitions around.. Where you would have:    

```
sdb             1.8T                                 
&#9500;&#9472;sdb1 ntfs   244.1G                                 
&#9500;&#9472;sdb2 ext4   976.6g /media/whouse                                 
&#9500;&#9472;sdb3 ext4   195.3G /media/raphael/3E3C627C3C622ED9                 
&#9500;&#9472;sdb4    
&#9500;&#9472;sdb5 swap     9.3G [SWAP]                          
&#9500;&#9472;sdb6 ext4    23.3G                                 
&#9492;&#9472;sdb7 ext4    93.1G
```

---

### Post by ray field on 2015-01-20
I honestly can't remember if this XP installation worked the way it's set up now. I suspect it was probably working a year ago -- especially since it appears to have an Ubuntu partition on i (probably my old Quantal installation) -- think I just bought the SSD and set up the BIOS to boot that first and never thought about it again.

I wasn't aware of testdisk -- would it change the boot.ini files? 

here is the relevant section of grub.cfg (with TWO entries for XP, which it's had I think for as long as I can remember, I never gave it a second thought)

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows XP Media Center Edition (on /dev/sdb1)' --class windows --class os $menuentry_id_option 'osprober-chain-D82C4F3E2C4F1742' {
	insmod part_msdos
	insmod ntfs
	set root='hd1,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  D82C4F3E2C4F1742
	else
	  search --no-floppy --fs-uuid --set=root D82C4F3E2C4F1742
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry 'Windows (on /dev/sdb5)' --class windows --class os $menuentry_id_option 'osprober-chain-3E3C627C3C622ED9' {
	insmod part_msdos
	insmod ntfs
	set root='hd1,msdos5'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos5 --hint-efi=hd1,msdos5 --hint-baremetal=ahci1,msdos5  3E3C627C3C622ED9
	else
	  search --no-floppy --fs-uuid --set=root 3E3C627C3C622ED9
	fi
	parttool ${root} hidden-
	drivemap -s (hd0) ${root}
	chainloader +1
}


```

---

### Post by ray field on 2015-01-21
BTW here is the file generated from Boot-Repair a day or two ago

[http://paste.ubuntu.com/9794669/](http://paste.ubuntu.com/9794669/)

---

### Post by yancek on 2015-01-21
I don't see any problem with the grub.cfg files for either Ubuntu 14.04 or 12.10 as they are pointing to the correct partitions and have the correct UUID.  There are also map entries since xp is now installed on a secondary drive.  I'm not sure why you have Grub installed to the mbr of sdc and sdd since those are windows only drives.  Grub basically chainloads windows and does not boot it directly so there is nothing you can modify in Grub to make it boot.  As indicated in your initial post, the problem is with your windows partitiion(s) or boot files.  Not sure what you have on sdb5.  You have xp boot files there and also the message below which doesn't look like good news.

> According to the info in the boot sector, sdb5 starts                         at sector 63.

Which option of the windows boot options from Grub gives you the missing hal.dll error?
You show windows 7 on both sdc and sdd but no boot entries in either grub.cfg file.  Did you not have those drives attached?  Are they not system installations of windows 7?

It's been a long time since I've used a system with a boot.ini file but the entry below for sdb1 does not look right.  You might do some googling on what is expected to be there.

> default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

The first drive and first partition are seen as (0).  I'm not sure which of the first three options points to a hard drive but they all show zero which would mean the first dirve and xp is on the second drive.  Also, the partition entry shows 2 which would be the third partition or sdb3 which isn't right.  I think that entry should be zero and one of the disk options should be 1.  You'll have to do some research on boot.ini.

---

### Post by oldfred on 2015-01-21
I just checked my old boot.ini and Windows partitions start at 1. 
So your correct boot.ini in sdb1 is drive 1 and partition 1.
Then entry for install in sdb5 is drive 1 and partition 5.

I would install a windows boot loader into sdb, you can use Boot-Repair's advanced mode or your Windows XP installer to install a Windows boot loader.

Windows normally is in the first drive & first partition where it is most happy. It really is not designed to recognize other installs.
But if you directly boot sdb using its own boot loader, it may still be drive 0 as I know with grub the boot drive is always hd0. Often grub uses a drivemap command to switch default drives when Windows is in second drive.

Your 4TB drive is also unusally configured. You do not have gpt partitioning, but then used 4K logical sectors. That was a work around to let XP work with large drives, as it would not work with gpt partitioning which is the correct way to partition drives over 2TB.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by LostFarmer on 2015-01-21
Had to get time and connect my hdd with XP on a logical volume and see some stuff.  It looks like your 'boot.ini' sdb5 is likely wrong.  " default=multi(0)disk(0)rdisk(0)partition([COLOR=#ff0000]3[/COLOR])\WINDOWS"  , it is the 3rd partition.

"According to the info in the boot sector, sdb5 starts                         at sector 63."  I do not believe XP uses that data but it is likely correct,  It is the sectors from the logical partition table to the volume, not from start of disk.

---

### Post by ray field on 2015-01-21
Thanks, all, for the help, but right now it looks kinda toxic. First I tried Boot-Repair's advanced mode, but it didn't seem to find anything on sdb -- the only options it offered were on sda. I haven't got much experience using Boot-Repair except for the things it does automatically (superbly), so then I tried the XP installation disk, but it threw up a nasty error early on -- muttered something about a virus and suggested running chkdsk before halting.

Right now the only thing that makes sense to me would be to disconnect the SDD (or set the HD to boot first) and then see if XP boots, and if not, to reinstall it, and then revert to the old setup. 

As it happens, I've only got a day or two more to do what I need to do in XP, and while doing those tasks is desirable it's not completely necessary. If anyone has further suggestions, please do offer them, and my thanks for your time. One of the things I've grown most fond of about using Ubuntu is this user community -- may I say, oldfred, your suggestions have proven invaluable over the last few years.

---

### Post by oldfred on 2015-01-22
From LostFarmer's post:
> "According to the info in the boot sector, sdb5 starts                          at sector 63."  I do not believe XP uses that data but it is  likely correct,  It is the sectors from the logical partition table to  the volume, not from start of disk.

Windows PBR or partition boot sector also does have the start and size of the NTFS partition and must match the partition table.
If a copy of Windows from first partition then it would have the start sector at 63. Not sure if then booting from the first partition would let you boot one in sda5 or not.
Normally you use chkdsk to update the PBR.

XP is the one exception where you can directly boot it in a logical partition, but not with a Windows boot loader. The Windows boot loader only allows or checks for primary partitions. But if you use the Lilo boot loader in the MBR (not a full install of Lilo), and update all the other parameters with chkdsk and boot.ini, you can directly boot XP. Not possible with newer versions of Windows.

       Boot WinXP from extended partition - See posts by Herman
[http://ubuntuforums.org/showthread.php?t=1192147](http://ubuntuforums.org/showthread.php?t=1192147)
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

 How to fix XP when the boot files are missing & info on windows in logical partitions-  meierfra.
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)
missing boot files meieifra - post 10
[http://ubuntuforums.org/showthread.php?t=1241394](http://ubuntuforums.org/showthread.php?t=1241394)
Herman on booting XP in logical
[http://ubuntuforums.org/showthread.php?p=4701367#post4701367](http://ubuntuforums.org/showthread.php?p=4701367#post4701367)

---

