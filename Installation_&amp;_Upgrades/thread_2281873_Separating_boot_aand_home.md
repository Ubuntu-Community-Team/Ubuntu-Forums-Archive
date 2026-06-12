---
title: "Separating /boot aand /home"
date: 2015-06-10
forum: Installation &amp; Upgrades
---

### Post by EzioAuditore on 2015-06-10
Okay Hi everyone, been here after a long time.. ):P

Umm.. I got a problem, hope I can get it sorted out here..

**_What I want to do:_**
I want to dual boot with Windows 8.1 for some college work. I've a 1TB HDD. How I'd like the layout be (Excluding the pre-made partitions by the manufacturer) :
- 3 partitons
      - 1 Ubuntu partition
      - 1 Windows partition
      - Shared /home partition b/w Ubuntu and Windows

**_Here's the current hdd layout:_**

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3       906G   59G  802G   7% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           772M  868K  771M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  160K  1.9G   1% /run/shm
```

For some reason, one OS partition i.e the recovery partition couldn't be mounted so I'm attaching a snip here below of my HDD :

[ATTACH=CONFIG]262505[/ATTACH]

Now what I'd like is to just somehow separate the /boot and /home partition and leave others intact.
How do I go about it now ?

---

### Post by stephen73 on 2015-06-10
You could use GParted to create the partitions. The shared partition would be formatted as HPFS.

You would edit your fstats file in /etc to make the shared partition /home

---

### Post by EzioAuditore on 2015-06-10
> **stephen73 said:**
> You could use GParted to create the partitions. The shared partition would be formatted as HPFS.

You would edit your fstats file in /etc to make the shared partition /home

I could just shrink off my /dev/sda3 boot partition and used the left over space for 8.1 installation. That' okay. 
But how do I separate the /boot and /home which are on same partition?

---

### Post by TheFu on 2015-06-10
You cannot share /home with Windows.  HOME must be a Linux file system with full support for Linux ownership, groups, permissions. NTFS doesn't do that.
Also, you must have a swap partition for Linux.
Whether you need a /boot partition as separate or not depends on whether you use LVM and/or encryption. If you use either, then /boot must be separate and a supported Linux partition type - ext2, ext3, ext4 all work. I suspect others will work as well, but I always use ext2. Small, lite, partition type.

Generally, it is a smart idea to place "data" (and only data) on an NTFS partition to be shared between Windows and other OSes.  Think "media" for that use and perhaps documents where you don't care about everyone in the world having access.

So ... with Win8, you probably have UEFI booting and GPT. That means that you can easily setup many partitions without the old worries about extended/logical partitioning.  So, for a beginning, I would do something like this:

1MB for EFI (whatever is already there from Windows is fine)
100G for C: - Windows + applications
7G for the Windows Reinsdtall-save-your-butt partition
????G for D: - this is the "Data" Drive

Then ...
500MB for /boot - ext2
25G for / - ext4
5-15G for /home - ext4 - if you program in Java, make it 35G. For python, perl, php, ruby, 15G is absolutely fine.
4G - 16G for Linux swap ... Min for 4G for desktops. If you want to suspend or hibernate, make swap a tiny bit larger than the amount of physical RAM.

And I wouldn't allocate all the storage until it is needed. That ???G above - will be NTFS - start with a health 500G. The smaller the better, since you need to have a backup solution for all of this used storage.

So ... that is what I would do, with the limited information provided.

Ah ... just looked at that image.  Why is the disk MBR formatted? Why, oh why?  that just made everything hard.  Can you switch it over the GPT?  You need to massively shrink sda3 and I would delete sda4 and sda5 for now, while you work on moving to GPT.  GPT has many better things about it for Windows AND for Linux.

---

### Post by EzioAuditore on 2015-06-10
> **TheFu said:**
> You cannot share /home with Windows.  HOME must be a Linux file system with full support for Linux ownership, groups, permissions. NTFS doesn't do that.
Also, you must have a swap partition for Linux.
Whether you need a /boot partition as separate or not depends on whether you use LVM and/or encryption. If you use either, then /boot must be separate and a supported Linux partition type - ext2, ext3, ext4 all work. I suspect others will work as well, but I always use ext2. Small, lite, partition type.

Generally, it is a smart idea to place "data" (and only data) on an NTFS partition to be shared between Windows and other OSes.  Think "media" for that use and perhaps documents where you don't care about everyone in the world having access.

So ... with Win8, you probably have UEFI booting and GPT. That means that you can easily setup many partitions without the old worries about extended/logical partitioning.  So, for a beginning, I would do something like this:

1MB for EFI (whatever is already there from Windows is fine)
100G for C: - Windows + applications
7G for the Windows Reinsdtall-save-your-butt partition
????G for D: - this is the "Data" Drive

Then ...
500MB for /boot - ext2
25G for / - ext4
5-15G for /home - ext4 - if you program in Java, make it 35G. For python, perl, php, ruby, 15G is absolutely fine.
4G - 16G for Linux swap ... Min for 4G for desktops. If you want to suspend or hibernate, make swap a tiny bit larger than the amount of physical RAM.

And I wouldn't allocate all the storage until it is needed. That ???G above - will be NTFS - start with a health 500G. The smaller the better, since you need to have a backup solution for all of this used storage.

So ... that is what I would do, with the limited information provided.

Ah ... just looked at that image.  Why is the disk MBR formatted? Why, oh why?  that just made everything hard.  Can you switch it over the GPT?  You need to massively shrink sda3 and I would delete sda4 and sda5 for now, while you work on moving to GPT.  GPT has many better things about it for Windows AND for Linux.

Well.. regarding the MBR formatted disk, it came that way. Its the factory setup, all the partitions and whatsoever..
And that is an overwhelming amount of information and I'm kinda lost how to go around them.. maybe if you could guide the way..?
And I'm basically after a setup with the least amount of partitions..

---

### Post by grahammechanical on 2015-06-10
Did that machine come with Windows 8 pre-installed? No? Again that changes things. The only experience I have with Windows 8 was when installed a Windows 8 pre-view edition. From that experience I suggest that:

It is possible to install Windows 8 into a single partition at the start of the disk. It used to be said that Windows has to be at the start of the disk. I do not know if that is still true. Windows will install its own boot loader and so you will loose the use of Ubuntu until you re-install the Linux boot loader (Grub). You can use Boot Repair to do that.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

So, you will need to create space for the Windows partition. Turn it into a partition and then use the Windows install disk to format the partition to a Windows format and then the installer will let you install Windows into the partition.

But you will then need a partition that is formatted to a Windows format to use as a shared data partition. Become clear in your mind what you want to do or need to do, then we can point you to some guides.

An alternative that is much simpler is to buy another hard disk and install Windows on that. Disconnect the Ubuntu disk first otherwise the Windows installer will install the Windows boot loader to every disk it finds in the machine and again you will loose Ubuntu.

Once the install is completed reconnect the Ubuntu disk and load Ubuntu and run

```
sudo update-grub
```

And that should create a boot menu with both Ubuntu and the Windows boot loader listed.

Regards.

---

### Post by EzioAuditore on 2015-06-10
Well, I was just want a dual boot system and a common data drive for them.

What I'm getting it, is that if I just shrink my /dev/sda3 to say 100*GB* and then set the 100GB (from the remaining 800GB partition) as the Windows partition and the remaining 700GB as the data drive, I'd be good to go?
And no, the machine came with Ubuntu pre-installed. Dell Inspiron 15 3542 here.

---

### Post by oldfred on 2015-06-10
You are not showing any NTFS partitions. And Windows 8 only works from NTFS, so did system come with Windows 8 and you erased it when you installed Ubuntu or are you now installing Windows 8 from scratch?

My suggestion is  a bit different from TheFu, but there is no one right way to partition. It depends on your use and later experience. Even my own optimal partition plan is not so good a few years later, but by then I usually have a new drive to start over with.

I suggest no /boot, / (root) of 25GB and keep /home inside /. Then a large NTFS shared data partition where you keep all your data. And you can move data folders from /home and link them back to /home so Documents, Videos etc look like they are in /home but really in the shared data partition.

If using Windows 8 you must make sure the always on hibernation or fast startup is off and you shut Windows down. Otherwise it is hibernated and you cannot mount any NTFS partitions.
       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by EzioAuditore on 2015-06-10
> **oldfred said:**
> You are not showing any NTFS partitions. And Windows 8 only works from NTFS, so did system come with Windows 8 and you erased it when you installed Ubuntu or are you now installing Windows 8 from scratch?

My suggestion is  a bit different from TheFu, but there is no one right way to partition. It depends on your use and later experience. Even my own optimal partition plan is not so good a few years later, but by then I usually have a new drive to start over with.

I suggest no /boot, / (root) of 25GB and keep /home inside /. Then a large NTFS shared data partition where you keep all your data. And you can move data folders from /home and link them back to /home so Documents, Videos etc look like they are in /home but really in the shared data partition.

If using Windows 8 you must make sure the always on hibernation or fast startup is off and you shut Windows down. Otherwise it is hibernated and you cannot mount any NTFS partitions.
       Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

There's no NTFS partition because it didn't come with Windows. It came with Ubuntu pre-installed. 
So you mean to say to let Ubuntu be the way it is, just make the windows and data partition, install windows and symlink data files to /home directory?

---

### Post by TheFu on 2015-06-10
> **EzioAuditore said:**
> There's no NTFS partition because it didn't come with Windows. It came with Ubuntu pre-installed. 
So you mean to say to let Ubuntu be the way it is, just make the windows and data partition, install windows and symlink data files to /home directory?

That cannot work.  There isn't any free storage for Windows to use.  You will be doing some major partition resizing to let Windows install and work at all. Since that is the situation, if you have an EFI/UEFI BIOS, please, please, please switch to GPT as the partition method and work from that point out. Do it now. It will be slightly painful now, but it is so much more flexible as to be worth the effort.  Plus moving Linux around is much easier than moving Windows around.  GPT requires EFI BIOS for Windows and Win must be x64.  Linux doesn't care if you have EFI or old BIOS for GPT support.  Trust me - GPT is important enough and will make your life easier going forward.

Some short reading: [http://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/](http://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/)

Oldfred gives good advice - even when it disagrees with mine. ;)  There is no "right" answer here.

The first question we need answered - is your system BIOS or UEFI?  This is absolutely critical to know.

---

### Post by oldfred on 2015-06-10
With BIOS/MBR partitioning, Windows has to be installed to a primary partition formatted NTFS with the boot flag. Default install will use two primary, a small boot and main install, but you do not have to have the separate Windows boot partition if you directly install to a NTFS partition.

You already have a lot of data in your / partition, so then you should shrink it to less than about 100GB or go thru several steps to move data to a NTFS data partition. Better to have Windows in its own system partition and set it to read only. And then have a read/write data partition. But with Windows 8 you still must have the fast startup or hibernation off or any data from Ubuntu into NTFS will be lost. It restores old info when recovering from hibernation and does not see any new info.

---

### Post by EzioAuditore on 2015-06-10
> **TheFu said:**
> That cannot work.  There isn't any free storage for Windows to use.  You will be doing some major partition resizing to let Windows install and work at all. Since that is the situation, if you have an EFI/UEFI BIOS, please, please, please switch to GPT as the partition method and work from that point out. Do it now. It will be slightly painful now, but it is so much more flexible as to be worth the effort.  Plus moving Linux around is much easier than moving Windows around.  GPT requires EFI BIOS for Windows and Win must be x64.  Linux doesn't care if you have EFI or old BIOS for GPT support.  Trust me - GPT is important enough and will make your life easier going forward.

Some short reading: [http://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/](http://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/)

Oldfred gives good advice - even when it disagrees with mine. ;)  There is no "right" answer here.

The first question we need answered - is your system BIOS or UEFI?  This is absolutely critical to know.

I see option such as Boot mode: Legacy or UEFI and Secure Boot options too, so I suppose its an UEFI based bios. Am i correct?
And regarding that GPT conversion, for that wouldn't I have to erase (clean) all of my HDD thereby losing everything on it? Even the factory recovery partition?

---

### Post by EzioAuditore on 2015-06-10
> You already have a lot of data in your / partition, so then you should  shrink it to less than about 100GB or go thru several steps to move data  to a NTFS data partition. Better to have Windows in its own system  partition and set it to read only. And then have a read/write data  partition. But with Windows 8 you still must have the fast startup or  hibernation off or any data from Ubuntu into NTFS will be lost. It  restores old info when recovering from hibernation and does not see any  new info. 				

That's what I was thinking..

---

### Post by oldfred on 2015-06-10
You can stay with BIOS/MBR, but with a new UEFI system, there are some advantages of UEFI/gpt partitioning. But now is the time to decide.

I knew several years ago, I was eventually getting a new UEFI system, so I started converting new drives to gpt partitioning. Ubuntu will boot from gpt with BIOS, but Windows only boots from gpt with UEFI and Windows only boots from MBR(msdos) with BIOS. So partitioning determines boot method. And then how you boot installer determines if it installs in UEFI or BIOS mode, so you have to boot installer in mode that matches partitioning, or you may erase drive.

Or you need to have good backups, which you should have anyway.

Normally converting from/to gpt erases drive, but there are tools that will convert, but may not be best way to convert.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by TheFu on 2015-06-10
> **EzioAuditore said:**
> I see option such as Boot mode: Legacy or UEFI and Secure Boot options too, so I suppose its an UEFI based bios. Am i correct?
And regarding that GPT conversion, for that wouldn't I have to erase (clean) all of my HDD thereby losing everything on it? Even the factory recovery partition?

That is correct, but you don't have any real choice.  As the drive is setup today, you are already using 4 primary partitions. That is the limit for MBR disks.  Windows **must** go into a primary partition, so you will be deleting at least 1 partition.
And the "factory" partition setup from dell is  .... er ... how we say this - - about the dumbest thing I've ever seen.

Boot off a liveCD (ubuntu or gparted) and shrink all the partitions to be as small as you can.  Then back them up.  Post the sizes and we can move forward from there.

You really don't have any choice in this matter if you must dual boot.

If the CPU is fast enough, there is sufficient RAM, and you don't need high-end graphics, using a virtual machine could be an option to run Windows.  That would remove the need to repartition today - though it would still be highly recommended by me.  So - how much RAM and which processor does the machine have?

---

### Post by EzioAuditore on 2015-06-11
i5 4th gen, 4GB RAM. And I guess, that whole GPT repartitioning thing would require quite a time and unfortunately I don't have much.. So for now, I've installed it in Virtualbox, for now.
Once I get free, I'll surely do as suggested..

---

### Post by TheFu on 2015-06-11
So - solved?  Vbox is a reasonable trade-off.

The CPU is certainly fast enough and while 4G can be limiting for some needs, I run a Windows media center that records 4 concurrent hidef streams with 2 vCPUs and 1.5G of RAM. Works fine - after I tuned the storage for Windows - since that OS refused to write to network-based storage for recording.

The GPT thing will take some time - perhaps 4 hrs. The easiest way is to have a spare 1TB disk and migrate over. It also depends on your understanding of the fstab and boot process for Linux. Nothing hard, just the detailed knowledge isn't something non-admin people usually bother to learn.

---

### Post by EzioAuditore on 2015-06-11
> So - solved?  Vbox is a reasonable trade-off.

I don't think it can be marked as SOLVED 'cause the main purpose of this thread ie dual boot hasn't yet been achieved.. So, just leaving it as it is for the time being or maybe some moderator can lock it and unlock later on request..

> The GPT thing will take some time - perhaps 4 hrs. The easiest way is to  have a spare 1TB disk and migrate over. It also depends on your  understanding of the fstab and boot process for Linux. Nothing hard,  just the detailed knowledge isn't something non-admin people usually  bother to learn.

Technicality isnt a problem. I infact enjoy gettin my hands dirty.. Its just that in case something goes wrong, I wouldn't be having much time to deal with it as of now..

And yeah i allocated 2 virtual CPU's and 2GB RAM and its running just fine.

---

### Post by EzioAuditore on 2015-07-29
Okay I'm all set to dual boot now.. Windows 7 (Upgrade to 10 afterwards) + Ubuntu 14.04. I've decided to move from MBR to GPT.. 
The thing is, what is the easiest way to achieve that?
I basically want to delete all my current partitions and convert my HDD to GPT style and then make the required partitions and then continue with the installation phase.

I took a look at the GPT fdisk tool as mentioned by Oldfred. How do I go about it?

EDIT: Windows 7 can't be installed to a disk partitioned as GPT?

---

### Post by oldfred on 2015-07-29
Windows only boots in UEFI mode from gpt partitioned drives. So if a newer system with UEFI you have to boot Windows installer in UEFI mode to have it install to gpt.
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

Be sure you have all your data well backed up before deleting partitions. You can use gparted from live installer.
I would just delete all partitions, so drive is blank, boot Windows installer in UEFI mode & install. Then use Windows disk tools to shrink Windows. Reboot immediately so it can run chkdsk and update to its new size. Do not create any additional partitions with Windows disk tools. Possible exception is a NTFS data partition. 
I prefer to create partitions with gparted, but part of that is I know gparted. 

I also prefer smaller system partitions and larger data partitions for both Windows & Linux. But Windows system partition must keep 30% free to maintain reasonable speed. It slows down when space is limited. so do not make Windows too small.

I use 25GB for Ubuntu / (root) but have all data in data partition(s), often on other drives. I end up using about 13GB of my / and 2GB is /home without any data other than the hidden files & folders like .wine and Firefox & Thunderbird. 

If you prefer terminal/command line tools for partitioning you need gdisk. I install it to review & adjust settings, but not for partitioning.
New installs seem to now have it. If not:
sudo apt-get install gdisk

---

