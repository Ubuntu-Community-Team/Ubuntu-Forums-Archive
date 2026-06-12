---
title: "installed grub on the wrong disk"
date: 2016-11-29
forum: Installation &amp; Upgrades
---

### Post by technodactyl on 2016-11-29
I recently got ubuntu installed on an external hard drive, so that i could use it alongside windows without having to worry about space too much.

Everything works fine, except that i accidentally installed grub on an internal hard drive.
So now it won't take me directly to windows when the external drive is unmounted.

I need help locating GRUB and removing it, so that i can retry installation onto the external drive.

Please send help.

---

### Post by yancek on 2016-11-29
I would guess that you used one of the 'auto-install' options such as "Install alongside windows" which has defaults and the user has very little control over what happens in the installation.  If you use the manual install method "Something Else", you can select the location to install the Grub bootloader.  If you used the Something Else option, you can select 'Device for bootloader installation' and you got the wrong device.

> 
I need help locating GRUB and removing it, so that i can retry installation onto the external drive.

No, you don't.  You first need a windows installation DVD to use to repair the MBR of the drive on which you have windows.  If you installed Grub to the windows drive MBR, you have writen over the windows code and you need to repair that.  If you simply remove Grub at this stage, you won't be able to boot anything.  You need to post back as to which release of windows you are using and whether you are using an MBR install or the newer UEFI install as the method for repair is very different between the two.

---

### Post by technodactyl on 2016-11-29
i'm using windows 10, boot mode for which is UEFI.

I've been trying to install ubuntu in UEFI, so i guess that's the repair method i need?

---

### Post by ajgreeny on 2016-11-29
I have not used Windows since XP, and apart from a virtual install of that which I still use very occasionally to update my GPS SatNav, I am totally out of date with it as an OS.

However, I am fairly certain that you can use Boot-Repair in my signature below to repair the boot-loader files of Windows, including Windows 10 in UEFI mode, so start there and see if that helps you out. Alternatively, if you have an install DVD for Windows 10, or the repair DVD you should have been prompted to create when you installed Windows 10, you can use that, though how you do so is beyond my knowledge.

---

### Post by oldfred on 2016-11-29
UEFI install to external is not directly supported by grub2.
Grub only installs its boot loader to the ESP - efi system partition on the drive seen as sda.
And UEFI only boots from /EFI/Boot/bootx64.efi from external devices. Both Windows installer & Ubuntu installer use that path & filename with obviously different actual files.

Did you create an ESP, FAT32 formatted with boot flag on external? I normally partition in advance to make sure it is gpt & has ESP, / and I typically add data partition(s).
The version of grubx64.efi or shimx64.efi in a full install is hard coded to find more files in /EFI/ubuntu in ESP.
So we have to copy /EFI/ubuntu from sda's ESP to external's ESP.
Then we copy again to EFI/Boot and then rename shimx64.efi to bootx64.efi

I have found it easier to do while still in live mode just after install.
Once you boot into actual install, the newer versions of fstab mount ESP with no permissions or 0077 which you want to change to UUID of external drive and change permissions.

 14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

You should in UEFI be able to set external drive first, and then Windows second. So if external drive not present, it boots directly to Windows. Or if external drive present it boots to grub and lets you choose Ubuntu or Windows.

Once you get external drive correctly configured you can delete the /EFI/ubuntu folder in ESP on internal drive and delete any UEFI boot entries for the internal drive's ubuntu.

to see current entires in UEFI boot menu
sudo efibootmgr -v
       Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

---

### Post by technodactyl on 2016-12-04
> **oldfred said:**
> UEFI install to external is not directly supported by grub2.
Grub only installs its boot loader to the ESP - efi system partition on the drive seen as sda.
And UEFI only boots from /EFI/Boot/bootx64.efi from external devices. Both Windows installer & Ubuntu installer use that path & filename with obviously different actual files
Did you create an ESP, FAT32 formatted with boot flag on external? I normally partition in advance to make sure it is gpt & has ESP, / and I typically add data partition(s).


I am 100% sure i created an ESP on the external disk, with the boot flag and esp flag. I can't check it now, however, as gparted is missing on this install. Could i check the flags on Windows' diskmgmt?

Anyway, i wasn't able to install with the GRUB install location set to the external drive. Only when i accidentally installed GRUB to sda was the install successful.

> 
The version of grubx64.efi or shimx64.efi in a full install is hard coded to find more files in /EFI/ubuntu in ESP.
So we have to copy /EFI/ubuntu from sda's ESP to external's ESP.
Then we copy again to EFI/Boot and then rename shimx64.efi to bootx64.efi

I have found it easier to do while still in live mode just after install.
Once you boot into actual install, the newer versions of fstab mount ESP with no permissions or 0077 which you want to change to UUID of external drive and change permissions

 14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1


How do i find the efi folder?

And i have no idea how to use fstab, or what it even is. Linux novice here. I'm sorry

---

### Post by oldfred on 2016-12-04
This user documented the process.
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad 

You can use parted to see partitions using terminal.
sudo parted -l

And I always install gparted to my new installs. Its just you cannot use it on the drive your install is in, other than view partitions. But I use it on my sdb drive or flash drives regularly.
sudo apt install gparted

---

### Post by technodactyl on 2016-12-17
Okay, so i removed the GRUB files from the EFI folder on disk 0 (the internal disk) using instructions from here:

[http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/](http://linuxbsdos.com/2015/09/05/how-to-delete-grub-files-from-a-boot-efi-partition-in-windows-10/)

Windows 10 boots just fine, so i think that's fixed.

> **oldfred said:**
> This user documented the process.
 UEFI Full install to external USB drive or flash drive
[https://ubuntuforums.org/showthread.php?t=2338836](https://ubuntuforums.org/showthread.php?t=2338836) by Halbarad 

You can use parted to see partitions using terminal.
sudo parted -l

And I always install gparted to my new installs. Its just you cannot use it on the drive your install is in, other than view partitions. But I use it on my sdb drive or flash drives regularly.
sudo apt install gparted

I deleted the ubuntu partitions on my external hdd; now I will try installing according to this chat.

---

### Post by oldfred on 2016-12-17
I found it easiest to make the changes after install but while still in installer. After it says continue to use system. You then have full access to ESP on sda & ESP on external drive to easily copy files.

---

### Post by technodactyl on 2016-12-19
Now the installer crashes whenever i try to install.

Sometimes, before i start installation, it gives me an error - ubi-partman crashed. A restart resolves this though...

I've put my esp in the beginning of the drive. Is this okay? (I originally had it in the end of the drive)

---

### Post by oldfred on 2016-12-19
UEFI recommends ESP be first. But Windows makes it second or third with a recovery partition first?
But it should be ok with smaller drives anywhere. One or two users posted Boot-Repair summary reports with it far into a drive. Many efibootmgr commands assume default ESP is first partition on first drive. But others can be set with extra parameters.

But not sure if new very large multi-TB drive if it would be found if near end of one of those drives.

Are you partitioning in advance with gparted and then using Something Else install option to choose partitions you created on external drive?

---

### Post by technodactyl on 2016-12-20
> **oldfred said:**
> UEFI recommends ESP be first. But Windows makes it second or third with a recovery partition first?
But it should be ok with smaller drives anywhere. One or two users posted Boot-Repair summary reports with it far into a drive. Many efibootmgr commands assume default ESP is first partition on first drive. But others can be set with extra parameters.

But not sure if new very large multi-TB drive if it would be found if near end of one of those drives.

Are you partitioning in advance with gparted and then using Something Else install option to choose partitions you created on external drive?


Yes I am! It still crashes every time. The error report says something about ubiquity crashing... I'm not sure if that's because of a problem with the installer or...

---

### Post by oldfred on 2016-12-20
Is it then at partitioning stage where it crashes?

Post this:
sudo parted -l
sudo fdisk -lu

Was drive ever RAID or Intel SRT?
Did you ever let Windows add partitions?

---

### Post by technodactyl on 2016-12-23
> **oldfred said:**
> Is it then at partitioning stage where it crashes?

Post this:
sudo parted -l
sudo fdisk -lu

Was drive ever RAID or Intel SRT?
Did you ever let Windows add partitions?

The installer doesn't crash at the partitioning stage; it crashes after I enter the username, hostname, and password that I want my system to use.

My drive was never RAID, and Intel SRT was never active on it.

I've been partitioning only through gparted.

(I actually tried getting rid of all the data by a secure wipe.)

Here's the output for sudo parted -l
```

ubuntu-gnome@ubuntu-gnome:~$ sudo parted -l
Model: ATA SAMSUNG SSD CM87 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Warning: failed to translate partition name
Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  525MB  524MB   fat32        EFI system partition          boot, esp
 2      525MB   660MB  134MB                Microsoft reserved partition  msftres
 3      660MB   114GB  114GB   ntfs         Basic data partition          msftdata
 4      114GB   115GB  472MB   ntfs                                       hidden, diag
 5      115GB   128GB  13.3GB  ntfs                                       hidden, diag


Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  135MB   134MB                Microsoft reserved partition  msftres
 2      135MB   1000GB  1000GB  ntfs         Basic data partition          msftdata


Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdc: 8004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8004MB  8003MB  primary  fat32        boot, lba


Model: WD Elements 25A2 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  316MB   315MB   fat32                 boot, esp
 2      316MB   979GB   978GB   ext4
 3      979GB   1000GB  21.5GB  linux-swap(v1)
```

...and sudo fdisk -lu
```

ubuntu-gnome@ubuntu-gnome:~$ sudo fdisk -lu
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/loop0: 1.2 GiB, 1246838784 bytes, 2435232 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C120849A-0828-4316-97D8-D5A46D7AAAE4

Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1026047   1024000   500M EFI System
/dev/sda2    1026048   1288191    262144   128M Microsoft reserved
/dev/sda3    1288192 223180799 221892608 105.8G Microsoft basic data
/dev/sda4  223182848 224104447    921600   450M Windows recovery environment
/dev/sda5  224104448 250068991  25964544  12.4G Windows recovery environment


Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: AED86EA1-3146-4FC9-A776-088F23234EA7

Device      Start        End    Sectors   Size Type
/dev/sdb1    2048     264191     262144   128M Microsoft reserved
/dev/sdb2  264192 1953523711 1953259520 931.4G Microsoft basic data


Disk /dev/sdc: 7.5 GiB, 8004304896 bytes, 15633408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0002b730

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 15633407 15631360  7.5G  c W95 FAT32 (LBA)


Disk /dev/sdd: 931.5 GiB, 1000170586112 bytes, 1953458176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: D86603B9-0CE1-4027-956F-E1126C367C7E

Device          Start        End    Sectors   Size Type
/dev/sdd1        2048     616447     614400   300M EFI System
/dev/sdd2      616448 1911514885 1910898438 911.2G Linux filesystem
/dev/sdd3  1911515136 1953456127   41940992    20G Linux swap

```

EDIT1: WAIT I SEE IT

I created the wrong partition table type

It's supposed to be gpt, but it's dos instead

EDIT2: Never mind... I changed the partition table back to gpt and it's still not working.

<changed output for sudo parted -l and sudo fdisk -lu>

EDIT3: Now it's giving me an error saying ubi-partman crashed. But this error gets resolved on rebooting.

---

### Post by oldfred on 2016-12-23
You do not show any ext4 partitions.
Use Windows to shrink the NTFS partition and reboot so it can run chkdsk.
Then use gparted to create at least one ext4 partition & swap.
Then use the Something Else install option to choose(change) the ext4 partition to use as / (root).

---

### Post by technodactyl on 2016-12-23
> **oldfred said:**
> You do not show any ext4 partitions.
Use Windows to shrink the NTFS partition and reboot so it can run chkdsk.
Then use gparted to create at least one ext4 partition & swap.
Then use the Something Else install option to choose(change) the ext4 partition to use as / (root).

What? It's right there...

```
Model: WD Elements 25A2 (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  316MB   315MB   fat32                 boot, esp
 2      316MB   979GB   978GB   ext4
 3      979GB   1000GB  21.5GB  linux-swap(v1)
```

---

### Post by oldfred on 2016-12-23
Sorry, did not scroll all the way down.

Is that an external drive? 
Grub does not correctly install to external drives. With UEFI it only installs to the ESP - efi system partition on sda.
And then UEFI only boots external devices from /EFI/Boot/bootx64.efi.
So after install we have to copy /EFI/ubuntu from sda to external, and then copy again to /EFI/Boot and rename shimx64.efi to bootx64.efi. Grub is hard coded to find files in /EFI/ubuntu so both copies/folders required on external.

---

### Post by technodactyl on 2016-12-25
I solved the installer crashing problem, starting the installer from the terminal (sudo ubiquity).

I'm gonna try copying grub from sda to sdd now.

---

### Post by technodactyl on 2017-01-04
I've actually given up on this (only temporarily though), because even with grub on another disk, i still have a working configuration. "Don't fix what's not broken," as they say.

If i do feel the need, however, i think this thread has a solution and i can just get here and check it out again. Thanks for all the help guys.

---

