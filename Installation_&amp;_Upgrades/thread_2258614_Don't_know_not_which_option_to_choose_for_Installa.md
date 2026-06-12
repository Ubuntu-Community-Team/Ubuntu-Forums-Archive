---
title: "Don't know not which option to choose for Installation Type"
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by lapaul07 on 2014-12-29
I had ubuntu and windows 7 dual booted on my laptop previously but then windows was giving me problems so I reinstalled windows and set my laptop back to factory settings. When windows reinstalled it looks like it installed on the same partition that it was on before leaving the partition that ubuntu was installed on blank. I want to install ubuntu on that partition again, but I'm not sure how to. When I go through the installation wizard there is no option to "Install ubuntu alongside windows 7" like it shows in the instructions here: [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop). There is only the option to "Erase disk and install Ubuntu" or "Something Else". From what I read "Something Else" option is for more advanced users that know what they are doing, but I don't really know what I am doing. Any suggestions? If I choose "Erase disk and install Ubuntu" will it erase my entire HD including Windows?

---

### Post by Dennis N on 2014-12-29
"Something Else" will allow you to select the already existing partition for your Ubuntu installation. That would be the choice to use.

---

### Post by buzzingrobot on 2014-12-29
> **lapaul07 said:**
>  If I choose "Erase disk and install Ubuntu" will it erase my entire HD including Windows?

Yes.  It does exactly what it says:  Erase the entire *disk*.

You need to determine the partitions on the drive now, after the Windows reinstall.  If the installer isn't showing the "alongside" option, it may be that the previous Ubuntu partition is gone.

---

### Post by grahammechanical on 2014-12-29
When you re-installed Windows 7 the Ubuntu boot loader (Grub) was over-written by the Windows boot loader. If you were careful when re-installing Windows and did not allow it to use the entire disk but directed it to install into a partition, then it could be that Ubuntu is still there and you need to re-install the Ubuntu boot loader (Grub).

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot Repair will offer to fix these kind of boot problems and will make a report that is stored at the Pastebin site. You will be given a URL to the location of the Boot Repair report. Post that URL in this thread and then we can see the report also. And give more accurate advice.

Regards.

---

### Post by lapaul07 on 2014-12-30
> **grahammechanical said:**
> When you re-installed Windows 7 the Ubuntu boot loader (Grub) was over-written by the Windows boot loader. If you were careful when re-installing Windows and did not allow it to use the entire disk but directed it to install into a partition, then it could be that Ubuntu is still there and you need to re-install the Ubuntu boot loader (Grub).

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Boot Repair will offer to fix these kind of boot problems and will make a report that is stored at the Pastebin site. You will be given a URL to the location of the Boot Repair report. Post that URL in this thread and then we can see the report also. And give more accurate advice.

Regards.

Ok I ran boot repair disk to "fix most common problems" and now my windows won't load! Whenever I reload my laptop it boots into the Lenevo Onekey Rescue Sytem 7.0 that is used to restore the laptop to it's factory settings. It won't load anything else. How do I get my windows back now?

Anyways here is the url that boot repair gave me:
[http://paste.ubuntu.com/9643853](http://paste.ubuntu.com/9643853)

Any help ASAP would be greatly appreciated because I don't want to have to reset my laptop back to factory settings.

---

### Post by lapaul07 on 2015-01-03
> **Dennis N said:**
> "Something Else" will allow you to select the already existing partition for your Ubuntu installation. That would be the choice to use.

Ok when I choose "Something Else" which device to I install to? The one that says "Free Space"?

Also, for where it says "Device for boot loader installation:" which one do I choose? It shows:
/dev/sda ATA WDC WD7500BPVT-2 (750.2GB)
/dev/sda1
/dev/sda2
/dev/sda4
/dev/sda5

---

### Post by yancek on 2015-01-03
> Ok when I choose "Something Else" which device to I install to? The one that says "Free Space"?

If you are in the Installation Type screen, you should be seeing whatever partitions you have on the drive.  The far left column is labelled Device, the column immediately to the right is "Type" which is the filesystem type.  If it shows ntfs, that is windows.  If it shows ext4, that would be your old Ubuntu.  Do not select the partition showing ntfs.  If you have no ext4 but only Free space, select that and create your partitions.

> Also, for where it says "Device for boot loader installation:" which one do I choose? It shows:

The first one which is the default:  /dev/sda ATA WDC WD7500BPVT-2 (750.2GB)
will install the Ubuntu Grub bootloader to the master boot record and should create an entry in the boot menu for windows.  Don't put it on a windows partition.  
You have three primary partitions, two are probably windows and one is an Extended and the fourth partition is a logical.  What is sda5?  Does it show a filesystem type.

---

### Post by lapaul07 on 2015-01-04
> **yancek said:**
> If you are in the Installation Type screen, you should be seeing whatever partitions you have on the drive.  The far left column is labelled Device, the column immediately to the right is "Type" which is the filesystem type.  If it shows ntfs, that is windows.  If it shows ext4, that would be your old Ubuntu.  Do not select the partition showing ntfs.  If you have no ext4 but only Free space, select that and create your partitions.



The first one which is the default:  /dev/sda ATA WDC WD7500BPVT-2 (750.2GB)
will install the Ubuntu Grub bootloader to the master boot record and should create an entry in the boot menu for windows.  Don't put it on a windows partition.  
You have three primary partitions, two are probably windows and one is an Extended and the fourth partition is a logical.  What is sda5?  Does it show a filesystem type.

It shows sda5 is ntfs.

Here is a screenshot of the Installation screen:
[ATTACH=CONFIG]258982[/ATTACH]

---

### Post by yancek on 2015-01-04
You deleted Ubuntu when you select to restore to factory settings.  That's expected behavior.  If you want to try to install Ubuntu, boot the installation medium and select the something else option and when you get to the window shown in your last post, highlight free space and click the + sign just below and on the left side of that window which should give you and Edit window where you can make the necessary entries.  I'm not sure why you have 4 ntfs partitions, usually it is 3 and also why you have three primary and one logical with no Extended. Are you using GPT partitioning?  I would suggest you go to the link below which has a step by step tutorial on installing Ubuntu with the Something Else option, scroll down about half way on the page. 

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by oldfred on 2015-01-04
I am not sure I understand the gparted screen. Please post this:

sudo parted -l
sudo fdisk -lu

You show an sda5 which is a logical partition. I do not think you have gpt partitioning as you do not show an efi partition which Windows requires to boot from gpt. Only if gpt would sda5 not be a logical partition.

So you may have the 4 primary partition limit and have to first expand the extended partition to include the unallocated, so you can make a new logical partition.

---

### Post by Impavidus on 2015-01-04
The partitioning window of the installer doesn't show extended partitions, but it's there. In the unallocated space next to the logical partition you can create new logical partitions. Click on the unallocated space in the list, click the + sign and create new partitions. At least an ext4 partition with mount point / and a swap partition. You can also create the partitions beforehand using gparted and use the partitioning window of the installer only to select them an set the mount points.

---

### Post by lapaul07 on 2015-01-05
> **oldfred said:**
> I am not sure I understand the gparted screen. Please post this:

sudo parted -l
sudo fdisk -lu

You show an sda5 which is a logical partition. I do not think you have gpt partitioning as you do not show an efi partition which Windows requires to boot from gpt. Only if gpt would sda5 not be a logical partition.

So you may have the 4 primary partition limit and have to first expand the extended partition to include the unallocated, so you can make a new logical partition.


Ok here is the output of those commands:

```
mint@mint ~ $ sudo parted -l
Model: ATA WDC WD7500BPVT-2 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  211MB  210MB   primary   ntfs         boot
 2      211MB   381GB  380GB   primary   ntfs
 3      381GB   734GB  354GB   extended               lba
 5      703GB   734GB  31.1GB  logical   ntfs
 4      734GB   750GB  15.8GB  primary   ntfs         diag


Model: Sony Storage Media (scsi)
Disk /dev/sdb: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  4007MB  4007MB  primary  fat32        boot, lba


mint@mint ~ $ sudo fdisk -lu

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x3ac12acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   743303951   371446152    7  HPFS/NTFS/exFAT
/dev/sda3       743305214  1434222591   345458689    f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda4      1434222592  1465149167    15463288   12  Compaq diagnostics
/dev/sda5      1373403136  1434222591    30409728    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d9095

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7826383     3913161    c  W95 FAT32 (LBA)
mint@mint ~ $ 
```

I'm using linux mint because I can't get Ubuntu to connect to my wireless network.

---

### Post by oldfred on 2015-01-05
The unallocated is in the extended partition as impavidus says in post #11. So you can create logical partition(s).

---

