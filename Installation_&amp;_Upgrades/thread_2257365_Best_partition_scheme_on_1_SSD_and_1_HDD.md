---
title: "Best partition scheme on 1 SSD and 1 HDD?"
date: 2014-12-19
forum: Installation &amp; Upgrades
---

### Post by linuxthunder on 2014-12-19
Greetings,

I would like to install Ubuntu 14.04 64-bit on 1 250GB SSD and 1 1TB HDD and I'm trying to figure out the best partitioning scheme.  The build is a linux gaming rig to be used with Steam and native linux games.  I'll also use it for general computing ie. web-surfing, documents and storing some photos and videos.

Based on my limited knowledge I would put / on the SSD and then /home and swap on the HDD?  Some say to put swap on the HDD to reduce wear on the SSD but others say it doesn't matter if the SSD optimized correctly.

/ would be primary at the beginning, /home would be logical beginning and swap would logical at the end?  

Thanks for your advice.

---

### Post by fantab on 2014-12-19
SWAP on HDD is a good idea, not that it matters IMO. However, the immediate advantage of having swap on same disk as '/', the other HDD can be used for data only and can be freely moved to another computer, if need be.
If you have decent RAM, then 4gb SWAP should be plenty.
250gb of '/' space is way too much, but since you say 'gaming' I'd be generous and make it 50gb.
Use the rest of the space for storage.
If you want to multiboot linux distros or any other OS then leave space/partitions for those.
I would use HDD only for personal data storage.

Consider your storage needs now, what they could be in future and plan ahead before you set up your partitions for storage.

You may find this useful: [gparted tutorial]("http://www.dedoimedo.com/computers/gparted.html")

Good Luck.

Use GPT partitioning on your both SSD and HDD, if its not so by default.

---

### Post by linuxthunder on 2014-12-19
This is excellent advice fantab!  Thanks for your help.

---

### Post by oldfred on 2014-12-19
Are you also installing Windows?
Is hardware newer and has both UEFI and BIOS boot modes? What motherboard?
How much RAM and what video chip/card?

"Best" varies by user and user needs. I find even my own best partition plan is obsolete a couple of years later, but then I get a new hard drive and totally reorganize.  I do not trust drives whether SSD or rotating to last more than a few years, so main working install is on a newer drive.

I like to install additional copies of Ubuntu or other systems, so I leave room on SSD or hard drive for additional / (root) of 20 or 25GB. And with new drive may not fully partition initially.

I now suggest gpt partitioning, if only Ubuntu or if system can boot in UEFI. The only issue with gpt is that if you want Windows in dual boot Windows only boots from gpt partitioned drives with UEFI. Both Windows & Ubuntu only boot from MBR (msdos) partitioned drives with BIOS.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

    
If a new SSD, it does not matter where swap is.
And if your system has 4GB of RAM or more, you may not even use swap, so it does not matter where swap is.

Since I do not install games, I keep / (root) on SSD with /home inside / and all data in data partitions on hard drive. I believe you can choose where to install most games, but if .wine based then that is in /home and can be difficult to try to move wine from /home to another partition. 

For data, I create a data partition and top level folders for all the standard data folders in /home like Documents, Pictures, Videos etc. And then I delete those folders in /home and link all those folders to the folders in my data partition on hard drive. Then all saved data is in default locations but really on my hard drive. I really only want or need the hidden user settings that are in /home on SSD as they are used more than any specific data files then on hard drive.

I would think you want all of system and most games on SSD for speed. So either keep /home on SSD or in /, but have a data partition on SSD for most games.

---

### Post by linuxthunder on 2014-12-19
This will not be a dual boot machine with windows.  Here is my build on pcpartpicker so you can see exactly what hardware I am using:

[http://pcpartpicker.com/user/thunderwolf/saved/tMYfrH](http://pcpartpicker.com/user/thunderwolf/saved/tMYfrH)

---

### Post by oldfred on 2014-12-19
Definitely use gpt partitioning.

But you probably will have two issues. 
Be sure to update Gigabytes UEFI/BIOS to newest available.
You will have to change IOMMU setting in UEFI to get a variety of things working.
And with nVidia 750Ti you will need to install newer nVidia drivers than are in Ubuntu's repository. But do not download from nVidia but use a ppa.

On both drives create efi partition for UEFI boot and a bios-grub partition for BIOS boot. Only one or the other will be used, but then you can install in either mode or easily later change to the other boot mode. And space used is not large, but if you install in BIOS mode and later want UEFI, it can be difficult to add an efi partition at beginning of drive where it really should be.

I prefer to partition in advance with gparted. Default with installer may still be MBR partitioning if in BIOS boot mode, which you really do not want. You can use gparted on live installer or separate gparted liveCD. If you boot in UEFI mode then it will install in UEFI mode with gpt partitioning.
  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

      
 UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)       
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/Grub](https://wiki.archlinux.org/index.php/Grub)


 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

      
 Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)


 Maxwell 750 
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)

Choose newest version available in ppa, example now is an older version (but still newer than in Ubuntu's repository).

 14.04 drivers for Nvidia GeForce GT 730 desktop board - 
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702)
PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)

---

### Post by linuxthunder on 2014-12-19
Thanks oldfred this is a lot of useful information I will read through.  It is feeling a bit complicated for my skills and was looking for something simple.  I am pretty good at understanding manual partitioning with the ubuntu installer but will look at gparted as you suggest.  Perhaps a breakdown of what to do on each hard drive would be helpful for the SSD and HDD for /, boot, /home, swap would visually help.

Thanks again for all the information!

---

### Post by oldfred on 2014-12-19
This is my working partitions, deleted lines on internal.

```
fred@trusy-ar:~$ df -h
df: ‘/root/.gvfs’: Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        24G   11G   13G  46% /

/dev/sdb5        28G  1.4G   25G   6% /mnt/backup
/dev/sdb4       385G   70G  296G  19% /mnt/data
/dev/sdc1       384M  242M  142M  64% /media/fred/NEWEFI_32
```

I did a test install of myth with a data partition for it. But will be reusing that for something else later. I also create ISO partitions on each drive, so I can install a test into a partition on the other drive using grub to loopmount the ISO directly. Makes for quick installs. The backup partition on hard drive is just for the /home and some other configuration data on SSD, so I could reinstall easily. I consider my copy of most critical data to DVDs as real backup. i.e. photos of grandchild, personal data etc.

```
fred@trusy-ar:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot
 2      525MB   527MB   2097kB                           bios_grub
 3      527MB   26.7GB  26.2GB  ext4            trusty
 5      121GB   126GB   5163MB  ext4            iso_ssd
 4      126GB   128GB   2000MB  linux-swap(v1)


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  525MB   524MB   fat32        EFI System Partition  msftdata
 2      525MB   527MB   2097kB                                     bios_grub
 3      527MB   26.7GB  26.2GB  ext4         myth
 4      26.7GB  446GB   419GB   ext4         data
 5      446GB   476GB   29.9GB  ext4         backup
 7      713GB   993GB   280GB   ext4         homerun
 6      993GB   1000GB  7337MB  ext4         iso_hdd

```

---

### Post by linuxthunder on 2014-12-19
Thank you oldfred for the visual.  This looks to be too advanced for my skill set.  I think I'll just install on the SSD and return the HDD for a usb drive and store/backup that way.  I thought it would be easy to make a single partition for storage on the HDD but now I'm more confused than when I started.  I'm just going to do the efi partition, /, /home and swap on the SSD.

Thanks for all your time and effort!

---

### Post by fantab on 2014-12-19
Read through the Gparted tutorial I linked in earlier post. Its simple.
If I were you, I would set up my partitions as follows:

SSD-
300Mb Fat32 EFI 'boot' flag
5Mb 'unformatted' 'bios_grub' flag
50Gb Ext4 Ubuntu '/'
25gb Ext4 'free'
25gb Ext4 'free'
145gb Ext4 for personal data (data on SSD will load faster than on HDD)
4gb Linux_SWAP

I don't use a separate /home partition, instead I keep my personal files in ext4 formatted Data partition. I mount this data parition(s) with '*fstab*' file and use '*bind*' to bind the data folders with Home folders. (If you want to know more about this, then first set up your partitions and Install Ubuntu, I'll tell you how to go about it later)
If you want to use a separate /home then make 145gb partition as /home.
If we use more than one linux distro or multiboot then separate /home partition causes complications. If we don't create a separate /home then Home will be created in '/' partition.

HDD-
300Mb Fat32 EFI 'boot'
5Mb 'unformatted' 'bios_grub'
25gb ext4 free
All the remaining GB Ext4 for personal data.. 

Its all very simple...

---

### Post by linuxthunder on 2014-12-19
> **oldfred said:**
> This is my working partitions, deleted lines on internal.

```
fred@trusy-ar:~$ df -h
df: ‘/root/.gvfs’: Permission denied
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda3        24G   11G   13G  46% /

/dev/sdb5        28G  1.4G   25G   6% /mnt/backup
/dev/sdb4       385G   70G  296G  19% /mnt/data
/dev/sdc1       384M  242M  142M  64% /media/fred/NEWEFI_32
```

I did a test install of myth with a data partition for it. But will be reusing that for something else later. I also create ISO partitions on each drive, so I can install a test into a partition on the other drive using grub to loopmount the ISO directly. Makes for quick installs. The backup partition on hard drive is just for the /home and some other configuration data on SSD, so I could reinstall easily. I consider my copy of most critical data to DVDs as real backup. i.e. photos of grandchild, personal data etc.

```
fred@trusy-ar:~$ sudo parted -l
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot
 2      525MB   527MB   2097kB                           bios_grub
 3      527MB   26.7GB  26.2GB  ext4            trusty
 5      121GB   126GB   5163MB  ext4            iso_ssd
 4      126GB   128GB   2000MB  linux-swap(v1)


Model: ATA WDC WD10EZEX-00B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  525MB   524MB   fat32        EFI System Partition  msftdata
 2      525MB   527MB   2097kB                                     bios_grub
 3      527MB   26.7GB  26.2GB  ext4         myth
 4      26.7GB  446GB   419GB   ext4         data
 5      446GB   476GB   29.9GB  ext4         backup
 7      713GB   993GB   280GB   ext4         homerun
 6      993GB   1000GB  7337MB  ext4         iso_hdd

```

Thanks oldfred, I have read through your posts in more detail and read instructions and I'm starting to understand this much better thanks to your help.

---

### Post by linuxthunder on 2014-12-19
> **fantab said:**
> Read through the Gparted tutorial I linked in earlier post. Its simple.
If I were you, I would set up my partitions as follows:

SSD-
300Mb Fat32 EFI 'boot' flag
5Mb 'unformatted' 'bios_grub' flag
50Gb Ext4 Ubuntu '/'
25gb Ext4 'free'
25gb Ext4 'free'
145gb Ext4 for personal data (data on SSD will load faster than on HDD)
4gb Linux_SWAP

I don't use a separate /home partition, instead I keep my personal files in ext4 formatted Data partition. I mount this data parition(s) with '*fstab*' file and use '*bind*' to bind the data folders with Home folders. (If you want to know more about this, then first set up your partitions and Install Ubuntu, I'll tell you how to go about it later)
If you want to use a separate /home then make 145gb partition as /home.
If we use more than one linux distro or multiboot then separate /home partition causes complications. If we don't create a separate /home then Home will be created in '/' partition.

HDD-
300Mb Fat32 EFI 'boot'
5Mb 'unformatted' 'bios_grub'
25gb ext4 free
All the remaining GB Ext4 for personal data.. 

Its all very simple...

Ok, thank you fantab.  I think I'm understand this better now and will give gparted a shot.

---

### Post by linuxthunder on 2014-12-21
I tried gparted on the live usb but efi partition was not available so I just used the graphical installer for /, /home and swap and everything installed fine and booting well.

Tried xorg ppa for my GeForce GTX 750 Ti and it works but scrolling down webpages is choppy and steam give me an error about openGL rendering not working.  I tried some fixes for these and now my machine just boots to blank screen and had to completely reinstall the system.

My current problem is with the Nvidia card now and deciding between ppa vs direct install from nvidia site since the xorg ppa stable release was not stable on my system.

---

### Post by oldfred on 2014-12-21
While most should install the LTS versions, your Maxwell card may do better with 14.10 or even try 15.04, even though it is not even to beta level yet.
The issue is not just the video driver but kernel & support software as well.

---

### Post by linuxthunder on 2014-12-22
> **oldfred said:**
> While most should install the LTS versions, your Maxwell card may do better with 14.10 or even try 15.04, even though it is not even to beta level yet.
The issue is not just the video driver but kernel & support software as well.

Strange, I installed Steam directly from the steam website instead of from the software manager and it works flawlessly now.  I got a warning when installing steam from the steam website to install from the software center instead because of better support but the opposite is true for my system in this case.

The nvidia card seems to be working fine now for everything else.

Thanks for your help!

---

