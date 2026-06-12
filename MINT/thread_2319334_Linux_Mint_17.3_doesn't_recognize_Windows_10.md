---
title: "Linux Mint 17.3 doesn't recognize Windows 10"
date: 2016-04-03
forum: MINT
---

### Post by schneemann2 on 2016-04-03
Hey guys!

I'm was going to install Linux Mint 17.3 parallel to Windows 10, but the Installer don't show the option for installing parallel. 
I already googled about it, but i can see all partitions, and no errors are there when i type "sudo parted -l" in the terminal (Live-Version).


mint@mint ~ $ sudo parted -l
Model: ATA SanDisk SD7SB3Q2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  525MB  524MB  primary  ntfs         boot
 2      525MB   256GB  256GB  primary  ntfs


Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  1000GB  1000GB  ntfs         Basic data partition  msftdata


Model: Generic Flash Disk (scsi) /* This is just my USB Stick on which Linux is "installed" */
Disk /dev/sdc: 8189MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8189MB  8189MB  primary  fat32        boot


This is what happens if i type "sudo parted -l" in terminal. I don't want to partition manually, but if it doesn't work anyhow else, i
would do it with a tutorial or something. 

PS: I need Windows for school, because they're using just windows, and i need the office programs... 
And i'm german, so sorry for my bad english.

Hope that you can help me!
Schneemann

---

### Post by kc1di on 2016-04-03
Perhaps the best place to ask your question would be on the Mint Forums [found here.]("https://forums.linuxmint.com/")
This is the Ubuntu forum and we welcome you here, but although mint is based upon Ubuntu - they are not entirely the same ;) 
and [this page]("https://community.linuxmint.com/tutorial/view/2191") may be of help also.
Good Luck.

---

### Post by yancek on 2016-04-03
Your parted output shows two windows partitions on the 256GB drive.  These two partitions take up the entire disk so you can't install Mint there without making changes.  This disk shows MBR/msdos partitioning.

The second (1TB) disk has nothing on it, no partitions and no filesystems.  It does show a GPT partition table.  I don't think you can mix MBR and GPT on the same computer but you might wait for someone else to post who is more familiar with UEFI/GPT.  So which drive do you want to install Mint to, the 256GB or the 1TB?  You might have to use the manual method, referred to as Something Else in Ubuntu/Mint.  Do you see the various drives/partitions when you do this.  Using the Install Alongside is basically and auto install and though it generally worked well when only MBR is available, with the onset of UEFI it will be problematic.  Try selecting the Something Else option to see if the drive/partitions are seen but don't proceed with the install.  

I would suggest you read the link below on using UEFI and scroll down to the section "Identifying if the computer boots the HDD in UEFI mode" and run that command from a terminal on the install to verify whether the machine is using UEFI and post back.

---

### Post by schneemann2 on 2016-04-03
I can't choose the "Install Alongside" Option, because Windows is not detected. All my partitions are detected well. /dev/sdb should not be involved with the installation, so everything of linux should be on /dev/sda. I was partitioning right now, and that's what came out:

Model: ATA SanDisk SD7SB3Q2 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  525MB  524MB   primary   ntfs            boot
 2      525MB   155GB  155GB   primary   ntfs
 3      155GB   256GB  101GB   extended
 5      155GB   189GB  33.8GB  logical   linux-swap(v1)
 6      189GB   201GB  11.5GB  logical   ext4
 7      201GB   256GB  55.4GB  logical   ext4


Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  1000GB  1000GB  ntfs         Basic data partition  msftdata


Model: Generic Flash Disk (scsi)
Disk /dev/sdc: 8189MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  8189MB  8189MB  primary  fat32        boot

Now, in /dev/sda, i used an extended partition /dev/sda3, which includes /dev/sda5, /dev/sda6 and /dev/sda7. The installation program now asks me where to put the bootloader. On a specific partition or just on /dev/sda?

---

### Post by yancek on 2016-04-03
In your initial post, your output showed two ntfs partitions using up the entire drive.  Your last post shows several other new partitions.  First off, 33GB is extremely excessive for a swap partition.  Partition 6 shows 11.5GB, what is that for?  Partition sda7 shows 55.4GB, is that your /home partition?  11.5GB is a little small for an install of Ubuntu so you need to clarify what each partition is intended for.  You certainly won't need 33GB for swap.

You would install the bootloader to /dev/sda which will put it in the master boot record of that drive pointing to the Grub files on whichever partition you install Ubuntu and it should detect and create a menuentry in the Grub boot menu of Ubuntu for windows.  This will overwrite the windows code if it is currently in the MBR.  If you are not sure you will continue using Ubuntu and might want to go back to windows, you will need a windows installation DVD to replace the Grub code with windows code later.  If you do not install to /dev/sda, you won't be able to boot Ubuntu because a default windows will not boot any Linux without some third party software installed on windows.

---

### Post by schneemann2 on 2016-04-03
33 GB swap, because i have 16 GB RAM, and all tutorials said that swap should be the double amount of the RAM...

I tried to install now, but the installation program crashed after failing to install the bootloader... I'm now writing from windows and removed all the changes...
Tomorrow, i'll try again, but now i have to learn for next weeks exams...

---

### Post by yancek on 2016-04-03
> 33 GB swap, because i have 16 GB RAM, and all tutorials said that swap should be the double amount of the RAM...


Ten or fifteen years ago, that was the standard.  When you're doing research on things like this, check the date on the site where you get the info.  If there is no date, ignore it.  When computers came with 256 or 512MB of memory double the RAM made sense.  If you do a lot of hibernating you made need a lot of RAM.  I don't so I'm not really sure about that.

With an 11GB partition for the installation, you should be OK if you are just testing the system and won't be installing a lot of software.  

You should go into windows Disk Management and see what that 512MB partition at the beginning of the drive is.  If it is an EFI partition, then you MUST install Mint EFI.  If it is not, you will need to install MBR.  If you see that it is EFI, take a look at the link below which gives some info on dual-booting Linux with a windows EFI system.  It's Ubuntu documentation but everything should also apply to Mint.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If the machine is MBR and not EFI, read the link below which has detailed instructions on dual-booting Ubuntu/Mint with a windows system.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

