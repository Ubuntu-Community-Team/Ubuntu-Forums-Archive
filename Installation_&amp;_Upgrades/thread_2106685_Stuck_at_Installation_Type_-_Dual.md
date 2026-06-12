---
title: "Stuck at Installation Type - Dual"
date: 2013-01-19
forum: Installation &amp; Upgrades
---

### Post by eddievvv on 2013-01-19
Hey guys, ubuntu newbie here. I have an ASUS X54C with 2 internal hard drives - OS (C:) 186GB and what i named FreeSpace (D:) 254GB (its empty btw, formatted it to delete the 4GB i had on it earlier in preparation)

My problem is installing ubuntu 12.04 at all, I am installing from a USB drive and the issues begin when selecting Installation Type. The "install alongside" option does not even show up, and considering i plan to install ubuntu on (D) (and dedicate that harddrive or most of it to ubuntu) anyways that doesnt matter to me, so i select "something else", and i end up with something like this on the next step.

/dev/sda
 /dev/sda1 ntfs ................... dont remember values exactly
 /dev/sda2 ntfs ................... and one of these is actually
 /dev/sda3 ntfs ................... the usb drive
      <- but no /dev/sdb at all in the list.

however underneath this table of values and other things i dont quite understand, in a drop down menu titled "Device for boot loader installation:", i can select /dev/sdb but there is no name for it, like /dev/sdb WDCasdlfasdkfh (300.45GB) <-lame example. I have noooo idea what to do about this, and i dont want to risk messing with /dev/sda or i will be screwed out of my windows os.

Ive been reading everything i can find, but no one elses problems seem to mirror mine, as far as i can tell anyways, and im getting frustrated so im back here on my windows 7 os looking for help before jumping back into it lol, had ubuntu on my toshiba but it had only 1 hard drive and had no problems.
if anyone has any advice id be more than happy to hear it, thank you very much in advance

---

### Post by darkod on 2013-01-19
First, if you created a ntfs partition on the disk where you want to install ubuntu, delete that partition. It needs unallocated space to create linux partitions, it doesn't install on ntfs.

Second, if one of the disks is not shown in the installer but is correctly shown otherwise (in live mode for example), that usually means the disk has been used in fakeraid before and it still has meta data remains. In that case the installer ignores it.

You can remove meta data by booting the ubuntu usb in live mode, opening terminal and if we are talking about the /dev/sdb disk executing something like:
sudo dmraid -Er /dev/sdb

It will ask you to confirm to remove meta data. If it does, it did find it and after removing it the install should go fine.

And in case you are not sure, the bootloader device is the MBR of the hdd which is /dev/sdb, without any number in it (numbers mean partition on that disk).

Let us know how it goes.

---

### Post by eddievvv on 2013-01-19
thats the thing though, i reformatted it from windows, just right clicked the D: and selected format, but there is no other option for filesystem besides ntfs, do i have to try reformat from within ubuntu live or something ? 

also, maybe getting ahead of myself, but ive heard that with ubuntu installed on sdb and windows on sda you cannot select which os to start up when turning on the computer, is there a simple way around that ? lol i think im biting off more than i can chew, but maybe best to address that before i actually install ubuntu ? not sure... thanks btw

---

### Post by darkod on 2013-01-19
You can boot from any disk you like, if your bios allows you that. And most bioses do. It's true that bios will try to boot from your first disk, sda, since it's probably configured like that right now.

But if you go into bios and tell it to boot from the second disk first, it will. And if you put grub2 on sdb, that's what it will boot. That way you will have your windows bootloader intact on sda which many people prefer.

Of course formatting from windows will make it only ntfs, it can't make linux partitions. Also, formatting doesn't delete raid meta data, so if you actually have meta dta on the disk it will never be deleted by windows formatting.
Instead of formatting the disk when you open Disk Management, right-click the partition and select Delete. That should leave the whole disk as unallocated, or unused, or whatever windows will call it (don't remember the exact syntax right now).
You never ever try to create disks/partitions for linux from windows! It knows only ntfs and linux installs on its own filesystem like ext4 for example.

Yes, you can use ubuntu live mode and delete the ntfs partition and create partitions for ubuntu before hand, but usually it's not needed since you can create them during the install. It might only confuse you more. And depending how experienced you are, starting from clean unallocated disk is best, but not necessary.

For example, you can use manual partitioning during the ubuntu install and delete the ntfs partition then, and create the linux partitions yourself. It will still work. But if planning to use the auto method, not manual, it's better the ntfs partition to be deleted before you start.

---

### Post by oldfred on 2013-01-19
Do not create partitions in Windows, it may convert to dynamic which is proprietary to Windows and does not work with Linux.

Are you sure you have two drives and not two partitions. Windows calls both physical drives and partitions as drives.

Post this:

       sudo parted /dev/sda unit s print
            sudo parted /dev/sdb unit s print

---

### Post by eddievvv on 2013-01-19
sorry darko, between you posting that last one and me reading it im already in ubuntu live.
but i used gparted to show me what was going on and it turns out that what i thought was a second hard drive is actually just /dev/sda4  so its just a partition then ? its file system is still ntfs, its label is show as free space (what i had nicknamed that drive) and its size is 254.36GB  sooo i found my drive. but where do i go from here ?
i have the option to reformat that partition with gparted, but im not sure if thats what my next step should be, or what to do, so i shall await to hear back from you guys, thanks alot im getting somewhere i think lol

---

### Post by oldfred on 2013-01-19
Ubuntu will not install into NTFS (unless wubi). And to be able to create more than the allows 4 primary partitions you need to convert one primary to the extended partition. Then you can have as many logical partitions in the extended as you want.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

If you create partitions in advance you still use manual install. If you just want / & swap, just delete your NTFS partition and let Ubuntu auto install into the unallocated space.

---

### Post by darkod on 2013-01-19
No, the next step is to delete that partition. That will leave the space as unallocated, and three primary partitions on the disk.

That is enough so that ubuntu can install on logical partitions using the unallocated space if you use the auto method.

If using the manual method and creating partitions yourself, create them as logical, not primary.
That's it.

---

### Post by eddievvv on 2013-01-19
sorry this is what you were looking for,  

Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start       End         Size        Type     File system  Flags
 1      2048s       52430847s   52428800s   primary  fat32        hidden, lba
 2      52430848s   52635647s   204800s     primary  ntfs         diag
 3      52635648s   443344895s  390709248s  primary  ntfs         boot
 4      443344896s  976773167s  533428272s  primary  ntfs

Im in the installation again, have deleted sda4 so it is free space, only quesstion i have now, is the location for "device for boot loader installation" 
/dev/sda ATA TOSHIBA MQ01ABD0 (500.1 GB)
/dev/sda1 Windows Recovery Environment (loader)
/dev/sda2 Windows 7 (loader)
/dev/sda3 Windows 7 (loader)
/dev/sdb
..... confused.

---

### Post by darkod on 2013-01-20
Since you confirmed you have only one 500GB disk, the bootloader goes to the MBR of the disk as I said earlier, which is /dev/sda (with no numbers in it).

---

