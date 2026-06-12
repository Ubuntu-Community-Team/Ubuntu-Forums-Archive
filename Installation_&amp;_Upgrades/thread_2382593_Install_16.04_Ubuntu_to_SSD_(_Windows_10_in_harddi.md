---
title: "Install 16.04 Ubuntu to SSD ( Windows 10 in harddisk )"
date: 2018-01-15
forum: Installation &amp; Upgrades
---

### Post by papatya2 on 2018-01-15
Hi,

I would like to install 16.04 Ubuntu to SSD.
My hardware has two partition : 400 GB for Windows 10. 600 GB for storage.
Windows 10 has been already installed.
What is instruction rules to install 16.04 Ubuntu to SSD ( Windows 10 will be exist on HD also) ?

(Dual boot : HD has Windows 10, one partition in HD is for storage, so Windows or Linux should use it,
I would like to have 16.04 Ubuntu on SSD also, so I would like to choose operation system on bios : Windows 10 or 16.04 Ubuntu )

---

### Post by oldfred on 2018-01-15
UEFI or BIOS hardware?
Did you install Windows in UEFI or BIOS boot mode?
Best to have Ubuntu in same boot mode. How you booted installer is then how it installs.

What brand/model system? What video card/chip?
Is SSD seen as sda, or HDD? Post this:
sudo parted -l

Either way you will need to use Something Else install option where you specify which partition is for which folder of Ubuntu.
I prefer to partition in advance with gparted, seems slightly easier, but you still have to use Something Else and choose(change button) to specify which partition is which.

 [URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If UEFI more info in link in my signature, below.

I do not have Windows, but this is my Ubuntu SSD. Trusty has been replaced with Bionic, but I still use 16.04 Xenial current LTS as main working install and will only convert to Bionic 18.04 LTS after it is fully released.
       Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413) 
    

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by papatya2 on 2018-01-16
[COLOR=#000000]Windows 10 has been installed as BIOS mode/Legacy mode.
How will I install ubuntu 16.04 to SSD ?

(All installation videos for hard disk. I can't find SSD installation.
Screen card is Nvidia.)[/COLOR]

---

### Post by oldfred on 2018-01-16
There is no difference between SSD & HDD installs. Only after install, you may want to add/change a few settings, but with new SSD  very little if any changes are required.

If Ubuntu is going on its own drive, I suggest using the newer gpt partitioning. If gpt you can then easier convert from BIOS to UEFI without having to totally redo drive. It is only Windows that must have MBR partitioning for BIOS boot and gpt for UEFI boot.

You must use Something Else. I do prefer using gparted to partition in advance and if you want more than default of / (root) and maybe swap of 16.04 as with 17.04 swap partition is not used, but swap file is used.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT

[/URL]Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning 
      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found) 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended). 
    
 I typically leave space for a second 25GB / (root) partition and some unallocated space.
Depending on size of SSD, you can add other partitions also.
While all my systems are now UEFI and only use gpt, I still add both ESP and bios_grub to almost all drives & larger flash drives.

 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond) 
        [URL="https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT"]
[/URL]

---

### Post by papatya2 on 2018-01-16
SSD and HD have MBR partitioning.

---

### Post by oldfred on 2018-01-16
Then now is a good time to convert SSD to gpt. If you have any data, be sure to back that up first.

You also may be able to convert in place, but still need good backups.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by papatya2 on 2018-01-17
> **oldfred said:**
> Then now is a good time to convert SSD to gpt. If you have any data, be sure to back that up first.

You also may be able to convert in place, but still need good backups.
       Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

Ley me summarize :
Windows 10 has been installed as BIOS mode/Legacy mode.
So I should install ubuntu to ssd in BIOS mode/Legacy mode similarly.
SSD and HD have MBR partitioning now.
I should add a few partioning to ssd with gpt.

---

### Post by oldfred on 2018-01-17
Only Windows requires MBR(msdos) partitioning for BIOS/Legacy boot.

And using gpt then give future flexibility. Once you get lots of data on drive, you then make it more difficult to convert.
I converted all new drives & larger flash drives to gpt since 2010. But system was then BIOS only.

Do you already have data on SSD?

---

### Post by papatya2 on 2018-01-17
No data on ssd.

---

### Post by oldfred on 2018-01-17
Then use gpt and add both ESP and bios_grub as first two partitions. Neither is large so no real wasted space. 
If not currently using ESP, it can be 100MB which was the default size Windows used. Larger ESP is for future use, non-standard configurations etc which you will not get to for quite a while, if ever.

---

