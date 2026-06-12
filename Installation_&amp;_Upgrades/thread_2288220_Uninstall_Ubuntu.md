---
title: "Uninstall Ubuntu"
date: 2015-07-25
forum: Installation &amp; Upgrades
---

### Post by bruno36 on 2015-07-25
Hello!

Today I changed to proprietary drivers and totally screw my computer. After booting I'm welcomed with pink screen and can't access the terminal (ALT+F1). Because this is not my first problem I decided to uninstall Ubuntu and wait some time and then try it again. 

Ubuntu and GRUB are installed on my second hard disk. To uninstall Ubuntu I have to format the partition where ubuntu is located (I assume), but how can I remove the GRUB boot loader safely?

Thank you for response.

---

### Post by Vladlenin5000 on 2015-07-25
Hi and welcome.

DO NOT format the Ubuntu partition before changing the bootloader.
Assuming your other OS is Windows tyou need either an installation media or recovery media for that OS and proceed with the recommended method for that OS (there are forums to ask for help if you need; it isn't a Ubuntu question *per se*).

We can help you with your issue with Ubuntu but that mostly depends on a) you willingness to do it and b) a complete description of your hardware, namely the graphics card, so we can suggest the better solution.

---

### Post by oldfred on 2015-07-25
Best to have a Windows repairCD or flash drive so you can make repairs to Windows.

But restoring a Windows type boot loader can be done from Linux as well.
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Also with two drives, best to have grub installed to the Ubuntu drive and keep the Windows boot loader on the Windows drive. Then from BIOS or one time boot key, often f10 or f12, you can directly boot every system. Or change BIOS to use Ubuntu drive as default and normally boot grub menu.

From grub, the Windows boot is usually so fast that you cannot get f8 to work. A few have said that repeat tries and pressing keys at almost same time can work eventually.
      
 [http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)

---

### Post by bruno36 on 2015-07-25
Sorry I wasn't clear enough. GRUB is on my second HD and windows boot loader is located on my first HD. They are both functioning properly without a problem (I can switch between them). The thing is I want to remove GRUB and Ubuntu from my second disk.

---

### Post by kansasnoob on 2015-07-25
> **bruno36 said:**
> Sorry I wasn't clear enough. GRUB is on my second HD and windows boot loader is located on my first HD. They are both functioning properly without a problem (I can switch between them). The thing is I want to remove GRUB and Ubuntu from my second disk.

Boot the live media you installed Ubuntu with and select Try Ubuntu without installing. Then from the live desktop open a terminal. Next run the following command and copy-n-paste the full output here [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") so we can be sure what we're dealing with:

```
sudo parted -l
```

Then we can give you some knowledgeable advice. BTW is there anything on that Ubuntu drive that you wish to keep? Data?

---

### Post by oldfred on 2015-07-25
There is no reason to remove grub if on a drive you will reuse later, or just want for data now.
Boot loader in MBR is not used if you just want data. Just do not try to boot it.

Then if you install another operating system, that system will overwrite MBR with its boot loader.

---

### Post by Geoffrey_Arndt on 2015-07-26
Or, if Ubuntu, because of it's requirements for proper video drivers did not work for you, another option is to replace Ubuntu with Ubuntu-Mate or Linux Mint Mate.   

You're likely then _not to have the graphics issue_, and both of these distros perform very well (faster than Win).   

That update will also take care of Grub, so your system will be immediately usable and certainly better than a Windows only system.   There is a saying "don't throw out the baby with the bath water" . . . capish?

---

### Post by bruno36 on 2015-07-26
> **kansasnoob said:**
> Boot the live media you installed Ubuntu with and select Try Ubuntu without installing. Then from the live desktop open a terminal. Next run the following command and copy-n-paste the full output here [using code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168") so we can be sure what we're dealing with:

```
sudo parted -l
```

Then we can give you some knowledgeable advice. BTW is there anything on that Ubuntu drive that you wish to keep? Data?

Here it is: 

```
Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1074MB  1073MB  ntfs         Basic data partition          hidden, diag
 2      1074MB  1451MB  377MB   fat32        EFI system partition          boot
 3      1451MB  1585MB  134MB                Microsoft reserved partition  msftres
 4      1585MB  986GB   984GB   ntfs         Basic data partition          msftdata
 5      986GB   1000GB  14.6GB  ntfs         Basic data partition          hidden, msftdata


Model: ATA KINGSTON SH103S3 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  77.1GB  77.1GB  primary  ntfs
 2      77.1GB  85.3GB  8193MB  primary  linux-swap(v1)
 3      85.3GB  106GB   20.5GB  primary  ext4            boot
 4      106GB   120GB   14.3GB  primary  ext4


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  15.6GB  15.6GB  primary  fat32        boot, lba

```

Yes. I would like to keep the 77GB partition.  



> **oldfred said:**
> There is no reason to remove grub if on a drive you will reuse later, or just want for data now.
Boot loader in MBR is not used if you just want data. Just do not try to boot it.

Then if you install another operating system, that system will overwrite MBR with its boot loader.

I'm probably going to install Ubuntu in the future when I buy more supported graphics card (my current is not well supported by windows and ubuntu [AMD Radeon R7 240 4 GB + AMD Quad Core A10-7800 DUAL GRAPHICS]). Still I need to delete ubuntu so I have more space on my disk.

---

### Post by kansasnoob on 2015-07-26
> **bruno36 said:**
> Here it is: 

```
Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1074MB  1073MB  ntfs         Basic data partition          hidden, diag
 2      1074MB  1451MB  377MB   fat32        EFI system partition          boot
 3      1451MB  1585MB  134MB                Microsoft reserved partition  msftres
 4      1585MB  986GB   984GB   ntfs         Basic data partition          msftdata
 5      986GB   1000GB  14.6GB  ntfs         Basic data partition          hidden, msftdata


Model: ATA KINGSTON SH103S3 (scsi)
Disk /dev/sdb: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  77.1GB  77.1GB  primary  ntfs
 2      77.1GB  85.3GB  8193MB  primary  linux-swap(v1)
 3      85.3GB  106GB   20.5GB  primary  ext4            boot
 4      106GB   120GB   14.3GB  primary  ext4


Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      4129kB  15.6GB  15.6GB  primary  fat32        boot, lba

```

Yes. I would like to keep the 77GB partition.  





I'm probably going to install Ubuntu in the future when I buy more supported graphics card (my current is not well supported by windows and ubuntu [AMD Radeon R7 240 4 GB + AMD Quad Core A10-7800 DUAL GRAPHICS]). Still I need to delete ubuntu so I have more space on my disk.

OK, that shows the 1TB Disk **/dev/sda** is obviously your Windows OS drive (which BTW has a GPT partition table so I suspect that's a UEFI install), and the 120GB Disk **/dev/sdb** has a 77.1GB partition (/dev/sdb1) which is apparently the 77GB partition you want to keep. Then /dev/sdb also has three Linux partitions that I assume you want to delete?

One of the Linux partitions is swap, I'm not sure if the other two are just the root partition (designated as /) and a separate /home, or maybe you had to create a separate /boot partition to deal with dual-booting a non-UEFI Ubuntu system next to a UEFI Windows install?

Anyway I assume you know what the two ext4 partitions are since you created them? And you know that once you delete those two partitions all data contained therein is gone forever! Also - there is always a slight chance of data loss when performing any repartitioning operation so creating a backup is always wise!

With that said I need to warn of something that seldom happens, but it does happen once in a blue moon. Once in a while when you boot the live media it recognizes drives in a different order - that is the designations /dev/sda and /dev/sdb may be reversed when you boot the live USB next time so be sure to watch that!

All that taken into account you can easily delete the two ext4 partitions and the swap partition by booting the live USB again and launching Gparted. In the upper right hand corner you can select which drive to work on, then you can right-click on the desired partitions and select Delete. NOTE: You will first have to right-click on the swap partition and select Swapoff.

After all the Linux partitions have been deleted you can right-click on the 77.1GB ntfs partition and select Resize, then just drag the right end of that partition all the way to the right to use the newly freed space. NOTE: I had not mentioned, but it's fairly obvious that you must click on the green check mark to confirm each operation!

Now, remember I warned that sometimes drive designations may change when you boot the live media, but while working in Gparted (which you've closed after completing the repartitioning work) you will have noticed if the 120GB drive is still recognized as /dev/sdb. If not you'll want to change the designation in this next command to create a generic Windows-ish mbr on that 120GB drive - to do that open a terminal and run:

```
sudo apt-get install lilo
``` 

```
sudo lilo -M /dev/sdb mbr
```

That should be it. When you do get ready to install Ubuntu (or a member of the Ubuntu family) again please ask here first. I think your experience will be better if both Windows and Ubuntu are installed in UEFI mode - if in fact Windows is installed in UEFI mode.

---

### Post by oldfred on 2015-07-26
Windows only installs to gpt partitioned drives to boot in UEFI mode.

But we have seen Ubuntu installed to a MBR(msdos) drive as sdb, but install a UEFI boot loader to sda's efi partition. 
Are you selecting drive sdb to boot from sdb's MBR in BIOS mode, or is Ubuntu in the UEFI boot menu?

Once you start using system with UEFI & gpt, you need to plan to convert drives to gpt partitioning and only boot in UEFI mode. Not a requirement but makes for much better consistency. Repartitioning and reformatting will erase drive, so you probably do not want to change current sdb now.

---

