---
title: "Installing Ubuntu on 8Gb Flash drive and using External HDD as Primary HDD"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by John_M. on 2014-11-08
*SYSTEM SPECS*  (more information available if necessary)
      Gateway NEseries - NE56R41u
      Memory - 4Gb DDR3
      Processor - Intel Pentium(R) CPU B960 @ 2.20GHz x 2
      Graphics - Intel Sandybridge Mobile
 (If it makes a difference this machine was purchased at Walmart)



 *PROBLEM*

      Since a drop from an estimated 2 1/2' - 3' The internal HDD has not been normal since and was given to me. Windows 8 is no longer on the HDD and I am starting from scratch. I have attempted to install Ubuntu onto the WD HDD and have it recognizable by the BIOS several times.  Each attempt has failed and the installation has never been bootable though I have followed forum threads and YouTube videos to a "T" in an attempt to make it work.  I have now decided to take advantage of the bootable live Ubuntu from my Sandisk and use my WD HDD as the primary if at all possible.  Added challenge?  No money for the project.

 

 

 *IDEA*
      Due to the (assumed) failure of the internal HDD I would like to run Ubuntu independently on my 8Gb Sandisk Flash drive (like an internal SSD) and use my external Western Digital 300Gb HDD as the primary drive (Like a run of the mill internal HDD). The machine with this setup will remain stationary.
 

 

 *DESIRED END RESULT*
      I would like to have a completely functional Ubuntu OS with the ability to install programs/Games and change settings that will all survive a shutdown and boot with no loss of information or settings.

---

### Post by oldfred on 2014-11-08
An 8GB flash is pretty small for  a full working Ubuntu now. I do have a full install in an 8GB partition with another 8GB for data. But that is just for emergency boot and has only a few updates. 
Flash drives are a lot slower, particularly with writes, but you can change some settings to help reduce writes.

But why cannot you boot external hard drive. I would expect the same issues with a flash drive.

Since system is Windows 8, it is UEFI. 
Did you turn off secure boot?
Does it have a CSM/BIOS boot mode? Sometimes that works when UEFI boot just does not, but most can get UEFI to boot.
Many vendors now are modifying UEFI internally to only boot Windows, so we have to do work arounds to try to make them work.
Do you still have an install on external? And what was issue? With one install, you will not get grub menu so it may have been booting but had video or other driver issues?

If you still have install on external run Boot-Repair and post link to summary report.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by John_M. on 2014-11-08
I believe it is BIOS and I seem to be running into a problem with boot repair.  It keeps giving me this prompt "Filesystem repair requires to unmount partitions. Please close all your programs. Then close this window." however there are no other applications running at the time and from what I can tell WD or SDB has been unmounted.  After pulling up Gparted to try and unmount the drive i did notice that the 5mb partition for Grub did appear to have an issue. (so perhaps grup was being installed and failed...several times) 

This is the error when i click on the ! icon

<i>Filesystem volume name:   <none>
Last mounted on:          /target
Filesystem UUID:          2c8de2c8-3239-4673-be87-495ed763fe3b
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              19218432
Block count:              76872192
Reserved block count:     3843609
Free blocks:              74612707
Free inodes:              19009704
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1005
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8192
Inode blocks per group:   512
Flex block group size:    16
Filesystem created:       Sun Nov  2 03:22:30 2014
Last mount time:          Sun Nov  2 03:58:40 2014
Last write time:          Sun Nov  2 04:01:54 2014


Also (for whatever it is worth) this is the error i continually get when accessing GParted in refrence to my Internal "Input/output error during read on /dev/sda"

---

### Post by oldfred on 2014-11-09
I do not know if this is the same as Windows dynamic or not. 
Did you orginally partition with Windows?

Filesystem revision #:    1 (dynamic)

Windows converts a 4 primary partitioned MBR drive to dynamic. And that does not work with Linux. It is a logical overlay over the physical partitions somewhat like LVM in Linux.

Post this to confirm. If it says SFS then it is dynamic.
sudo fdisk -lu

---

### Post by nerdtron on 2014-11-09
Full install on an 8 GB USB drive will result to a lower life span. Several flash drives I used lasted less than 6 months running 24x7.

Installation on making an external HDD as media is possible as I have also tried in the past. The easiest way to do it is use the 8GB flash drive to boot into Live Mode. It would be better if you disconnect the internal hard drives first to avoid confusion on drive. Then plug in also the external drive. Now you can install as usual and ubuntu should install on the external drive.

---

### Post by John_M. on 2014-11-09
I think I'm going to resort to that. Simply installing it onto the WDHDD the only issue is I have attempted it several times and the latest issue has been that the partitions seem to be incorrect. Simply installing it using the normal settings does not seem to work.  Complete and accurate instructions would be appreciated. I have used forums and youtube previously but with no success. Hopefully we can get it this time. (I wouldnt think it would be this difficult to get it working).  Would you suggest removing the internal HDD to eliminate possible confusion? it would be no problem at all,  just want to know if this would be a good idea (I dont even know if the laptop will start without having an internal HDD plugged in)

ALSO!
Windows is no longer on the computer. All formating and work will need to be within Ubuntu. The computer did not even come with the OS disk in the box so using any of the utilities that would be found there are out of the question.

---

### Post by oldfred on 2014-11-09
If no Windows, best not to have any NTFS partitions.
And I now suggest, but not require gpt partitions. 
Gpt is required if drive is over 2TiB or you boot with UEFI, but I have used gpt on my Linux only partitions since 10.10 with BIOS boot and I really do not notice any difference. No more primary, extended & logical partitions and it has a backup partition table if issues.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

I also prefer to create partitions with gparted, but still have to use Something else to choose which partition is / (root). I use data partition(s), but if a newer user a separate /home is a bit simpler to implement.

How you partition is totally up to you and no one scheme we suggest is right for you. Even my own optimal partition plan usually is not so good a couple of years later.


 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)

---

