---
title: "Questions about dual booting with ssd/hdd"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by Endoroid on 2013-12-07
Hey folks, i'm looking to install ubuntu alongside windows 7 and seem to be having some issues

I recently upgraded my laptop to have a 128GB ssd boot drive for windows, in addition to a 1TB hdd. I would like to install ubuntu on the hdd, not on the ssd however. When i went to install, the installer said that it could not find an OS on the computer already and when i cancelled i had some problems trying to boot windows again. Firstly, i'm wondering if it's because i chose the EFI boot as opposed to legacy(EFI boot is how i did it when i installed windows 7 on the ssd)that i had problems? And second, how do i want to go about partitioning the hdd properly for install, and to which drive do i want to install the bootloader?

If you need any furthur info please let me know, and thank you in advance

---

### Post by oldfred on 2013-12-07
If Windows is UEFI, then it would be better to have Ubuntu as UEFI. But you can only boot UEFI with gpt partitioned drives. Is hard drive MBR(msdos) or gpt.
Post this from live installer's terminal
sudo parted -l

If you install Ubuntu in BIOS mode the only way you can boot is from UEFI/BIOS and you may have to turn onoff UEFI or turn off/on CSM each time depending on which system you boot. Some auto switch, but you still can only boot from UEFI or one time boot key, not from grub menu.
Also better to have efi partition on hard drive if in UEFI mode, but it is supposed to be near beginning of drive. How full is drive and can you make space easily? 
There are tools to convert from MBR to gpt, but I have not used them. They all say to have good backups.

---

### Post by Endoroid on 2013-12-08
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ADATA SX900 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                          Flags
 1      17.4kB  105MB  105MB  fat32                                      boot
 2      105MB   239MB  134MB               Microsoft reserved partition  msftres
 3      239MB   128GB  128GB  ntfs                                       msftdata


Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      17.4kB  273MB   273MB   fat32                                      boot
 2      273MB   407MB   134MB                Microsoft reserved partition  msftres
 3      407MB   1000GB  1000GB  ntfs                                       msftdata


Model: Lexar USB Flash Drive (scsi)
Disk /dev/sdc: 7871MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7871MB  7870MB  primary  fat32        boot, lba

```

---

### Post by oldfred on 2013-12-08
Be sure to boot installer in UEFI mode. More info in link in my signature.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
You will want to install grub to an efi partition, but it really should not matter which one. I prefer to have grub on same drive as install. Installer may default to the SSD efi partition. With UEFI and efi partition, you can just copy the /efi/ubuntu folder. But fstab will only use one efi partition for updates and that is the one you do want to use to boot from as default.

With two drives you will want to use Something Else or manual install. I prefer to partition in advance with gparted as it is a bit clearer, but you still have to use manual install to choose format like ext4, mount like / (root) for each system partition. Swap has no format. 

Usually best to use Windows tools to shrink NTFS partitions and reboot and run chkdsk. More important for Windows system partitions, so you could use gparted on a NTFS data partition. But still reboot into Windows and manually run chkdsk on the data partition before installing.
Once you have the free unallocated space the auto install may work, but I still suggest manual install.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by Endoroid on 2013-12-08
I went ahead with the install, 30GB for / and almost 300GB home with 16GB swap all on the HDD and everything seems good. Chose the HDD for bootloader install and i resized the partitions via windows beforehand. On the first boot i couldn't boot into windows from grub, gav me an error, but from the BIOS i could chose the windows install directly, which worked and i can now boot into windows from grub no problem.

Thank you for the help

---

### Post by oldfred on 2013-12-08
Glad that worked. :)

---

