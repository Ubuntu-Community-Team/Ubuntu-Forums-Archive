---
title: "Grub cannot find one hard drive after update/upgrade"
date: 2018-03-02
forum: Installation &amp; Upgrades
---

### Post by makem2 on 2018-03-02
I have a laptop running Xubuntu 16.04 and Windows 10. Both OS are sharing an SSD drive which is in a CD tray. Windows profile is on DataS on the HD which came with the laptop. Until today, the system had been working for months using only windows but today I updated/upgraded xubuntu.

There were a few changes and all appeared to go well. However, at the end of the update I had an error message saying that grub could not find sdb3 which is the DataS drive. I remembered that I had only set up xubuntu partly as the user would only be using windows until I convinced her to try linux. Therefore I had not got around to making an fstab entry or mount point for sdb3.

After making an fstab entry I got the following error:

```

han@TOSH:~$ sudo nano /etc/fstab
[sudo] password for han: 
han@TOSH:~$ sudo mount -a
Failed to read last sector (1434421246): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sdb3': Invalid argument
The device '/dev/sdb3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
han@TOSH:~$
```The fstab entries are:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=e202c90b-ed5a-464d-8048-4b21062dee42 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=bde01976-fe45-4777-b842-d25ed791f572 none            swap    sw              0       0

#LDC was on sdb2  during installation
#UUID="D860E2AD60E29214 /media/han/LDC ntfs-3g rw,defaults,nofail       0       0
#DataS was on sdb3  during installation
UUID=A8DA2644DA260F5E /media/data ntfs-3g rw,defaults,nofail    0       0
```

LDC is #'d out because although it did not have an fstab entry it did show in file manager correctly.

I do not want to lose the data on sdb3 so ask for guidance.

I think I may have enough room to copy all the data and move it to the ssd drive iif that would be simpler. But I also don't want to mess up windows symlinks if possible.

---

### Post by ubfan1 on 2018-03-02
Can you start Windows via the EFI menu (some key at power-up) to select device/OS to boot?  If so, run chkdsk on the DataS partition.,

---

### Post by oldfred on 2018-03-02
In addition to chkdsk from Windows, did Windows turn fast start up back on? It does that with updates which may be in background and you do not know it changed settings.
All NTFS partitions are then in hibernation mode and cannot be mounted read/write with Linux. You may be able to manually force mount in read only mode.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by makem2 on 2018-03-02
The machine has run out of battery so can't do anything for an hour or so.

But, as windows is working correctly, I feel sure i could check sdb2

---

### Post by makem2 on 2018-03-02
I will check fast start up when I have some battery. Whilst I was using it windows said it was downloading the latest windows but had not completed. So, unless (as it usually does) it has updated previously fast boot should still be off. I will check.

---

### Post by makem2 on 2018-03-02
Thank you both for your quick responses.

> [COLOR=#000000]ubfan1[/COLOR]
[COLOR=#000000][INDENT]**Re: Grub cannot find one hard drive after update/upgrade**
Can you start Windows via the EFI menu (some key at power-up) to select device/OS to boot? If so, run chkdsk on the DataS partition.,
[/INDENT]
[/COLOR][COLOR=#000000][INDENT]

Windows said I did not need to check the drive but did so anyway and no errors reported.

[/INDENT]
[/COLOR]
> [COLOR=#000000]oldfred[/COLOR]
[COLOR=#000000][INDENT]**Re: Grub cannot find one hard drive after update/upgrade**
In addition to chkdsk from Windows, did Windows turn fast start up back on? It does that with updates which may be in background and you do not know it changed settings.
All NTFS partitions are then in hibernation mode and cannot be mounted read/write with Linux. You may be able to manually force mount in read only mode.

[/INDENT]
[/COLOR]


Both fast-startup and hibernation were unselected.

Edit:I do not have enough space to copy sdb3 data to the SSD but could copy it to a raspberry pi backup drive. That will take quite a while to do but just in case. I will start an rsync going.

---

### Post by makem2 on 2018-03-03
More information:

```

han@TOSH:~$ sudo fdisk -l
[sudo] password for han: 
Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x88518851

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 126345989 126343942 60.3G  7 HPFS/NTFS/exFAT
/dev/sda2       126347264 128350207   2002944  978M 27 Hidden NTFS WinRE
/dev/sda3       128352254 232712191 104359938 49.8G  5 Extended
/dev/sda4       232712192 234438655   1726464  843M 27 Hidden NTFS WinRE
/dev/sda5       128352256 220356607  92004352 43.9G 83 Linux
/dev/sda6       220358656 232712191  12353536  5.9G 82 Linux swap / Solaris

Partition table entries are not in disk order.


Disk /dev/sdb: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xb283467b

Device     Boot Start        End    Sectors   Size Id Type
/dev/sdb1          63 1465147119 1465147057 698.7G 42 SFS

[COLOR=#ff0000]Partition 1 does not start on physical sector boundary.[/COLOR]
han@TOSH:~$ 


```

gparted:

Partition /dev/sdb1 File System unknown Size 698.64 GiB

I also notice that I do not have a separate partition for /home which I normally do. The space allocated for / which must include /home is too small. So, unless anyone can see otherwise, I think I should reinstall xubuntu correctly, making /home on sdb3 in its own ext4 partition.

I have a feeling that this is what I would have done previously to keep /home and windows profile away from both OS.

Edit: The disc in question, sdb1 is in fact a dynamic disc and linux is not recognising it. To convert it back to mbr I must use diskpart, remove all partitions and choose, change to basic disc. Or so it seems.

I thought linux recognised all windows 10 foible's. A dynamic disc cannot have partitions, it has 'volumes' and spans the whole disc.

---

### Post by oldfred on 2018-03-03
Your sdb1 is showing as SFS which is in Windows dynamic partitions, rather than Windows standard basic partitions.

Windows will often change to dynamic if you try to create more than the allowed 4 primary partitions with MBR(msdos) partitioning. It is a Windows alternative to primary, extended & logical partitions, but does not work with Linux.

       [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from) 
   [http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm) 
   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Partition wizard repaired NTFS partition table that gparted could not see with disk label error
[http://ubuntuforums.org/showthread.php?t=2112005](http://ubuntuforums.org/showthread.php?t=2112005) 
   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
 GRUB2 2.00 recognizes defunct LDM headers from old dynamic partitions
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1061255)

---

### Post by makem2 on 2018-03-03
I converted to basic, split the drive into two partitions and am currently replacing the data on the windows data partition making sure to keep the same partition letter to keep the symlinks going. When that is finished I will look at what linux makes of it.

All should be ok but I still cannot understand/remember why /home is not separate, this is mandatory for me usually.

I will need to find how to move /home to another partition or do a reinstall which would be ok as I have not gone far with setup. Will be of interest to look into moving /home.

Thanks for the input.

PS. I understand Archlinux can deal with dynamic disks (maybe wrong)

---

### Post by oldfred on 2018-03-03
There have been some upgrades to the Linux driver. I thought I saw where it could now read dynamic partitions. But not sure how well that works.
Not sure there is any reason for dynamic partitions anymore, as gpt is now the standard and it allows an unlimited (well 128 default) number of partitions.

You can use gpt even if BIOS booting Ubuntu, but not Windows as BIOS boot requires MBR. Even newer Windows in BIOS mode will read data on separate gpt drive.
I have used gpt on my Ubuntu only BIOS boot drives since 2010. Back then I still had XP on a separate MBR(msdos) drive.

If reusing an existing /home, best to use Something Else and include it during install. But must not check the format box or you erase it.

You can mount it after install. Details in the move /home instructions, you just do not need the move.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

I typically have several Ubuntu installs, and now prefer /mnt/data for all data and keep /home inside / (root) and link folders into /home. Then I have all data in all installs, and can have somewhat different configurations to test or just try next install without modifying settings in current install.

---

### Post by makem2 on 2018-03-03
Thanks for the link to moving /home. It looks quite a chore and possibly error prone. I think in my case a fresh install is best.

As a matter of interest it seems to be frowned on to have two file systems on the same disc. Do you think that also applies to a disc which only contains data?

---

### Post by oldfred on 2018-03-03
I have not seen any issue with different formats for partitions.

I typically have an install even if smaller / (root) partition on just about everything.
My 32 & 64GB flash drives have an install more for emergency boot, do they do not grow as large nor have as much installed.

---

### Post by makem2 on 2018-03-03
I got that suggestion from the last paragraph of the move /home link you gave.

---

### Post by oldfred on 2018-03-03
Am not sure what he was talking about. 
You cannot even use NTFS for /home as it does not support Linux ownership & permissions.

I did use NTFS for some shared data and linked that back into /home without issue.

---

### Post by makem2 on 2018-03-03
To finalize the thread:

The disk which could not be used by Linux was set up as a Dynamic disk. The whole disk was dynamic and as such partitions could not be made. Only Volumes could be made.

I copied all the data from the disk, deleted all partitions whilst in windows disk manager and made two new partitions. One was formatted as NTFS and given the same drive letter as the volume where the data was copied from (F in my case) and then transferred the saved data back to it. As the partition letter had not changed windows was happy and all symlinks such as the user profile on F were restored correctly.

For Linux, I reinstalled xubuntu, upgrading it to 17.01 at the same time, choosing the same partition as before for / and swap. The /home partition was placed on the remaining partition of the previous dynamic disk, alongside the data for windows.

The problem subject of the post title was nothing to do with the update/upgrade, I just thought it was.

---

