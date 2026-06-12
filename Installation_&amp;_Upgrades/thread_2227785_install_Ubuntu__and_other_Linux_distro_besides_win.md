---
title: "install Ubuntu  and other Linux distro besides win8.1"
date: 2014-06-03
forum: Installation &amp; Upgrades
---

### Post by speedman2202 on 2014-06-03
hello guys

i was trying moving to Linux . but my elders bro's very cant deal with Linux , just that dump OS windows , anyway ... i bout new pc and now have 1 Terabyte HDD capacity , i let first partition be 75 GB for win8.1 and the next partition is 100 Gb and rest partitioning it for save my other data .....so i have now free 100Gb partition for Linux OS's and i will start with Ubuntu ... so can u plz tell me how to install it beside the current win8.1 OS .....i have partitioned my HDD with GPT partitioning .... plz tell me in  a specific way without made my current OS crashed or corrupted install Ubuntu and made a dual boot option for both OS and if there a video for installing i would be grateful 


i dont want be Idiot anymore with using Windows OS :( :(


thx

---

### Post by oldfred on 2014-06-04
Is Windows booting in UEFI mode? If drive is gpt it must be in UEFI mode to work.

Best to backup your Windows, even if you do not now think you need it. Many later come back and have one game, one application, or school or work that has to run on Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And make a Windows repair flash drive. Most Windows repairs cannot be done from Linux.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

One suggestion, adjust as you see fit.
      
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

These are now older, but the install process has not changed much.
 Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
[https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)
Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
Dual-Boot Windows 8 and Ubuntu 12.10 (BIOS)
[http://www.youtube.com/watch?v=wNCSbTyUzoM](http://www.youtube.com/watch?v=wNCSbTyUzoM)

---

### Post by Bucky Ball on 2014-06-04
*Thread moved to **Installation & Upgrades**.*

---

### Post by fantab on 2014-06-04
> **speedman2202 said:**
> hello guys

i was trying moving to Linux . but my elders bro's very cant deal with Linux , just that dump OS windows , anyway ... i bout new pc and now have 1 Terabyte HDD capacity , i let first partition be 75 GB for win8.1 and the next partition is 100 Gb and rest partitioning it for save my other data .....so i have now free 100Gb partition for Linux OS's and i will start with Ubuntu ... so can u plz tell me how to install it beside the current win8.1 OS .....i have partitioned my HDD with GPT partitioning .... plz tell me in  a specific way without made my current OS crashed or corrupted install Ubuntu and made a dual boot option for both OS and if there a video for installing i would be grateful 


HDD partitions are a very personal thing, yet important. If set up 'properly' (as per YOUR needs) then they could last the life of the HDD.

I have another example for you, (all Partitions in a GPT are Primary):
Total Space=1TB
```
300Mb FAT32 ESP 'boot'flag   
4Gb Swap
25Gb Ext4 Ubuntu 14.04 '/'
25Gb Ext4 other Distro '/'
25Gb Ext4 other Distro '/'
25Gb Ext4 other Distro' '/'
25Gb Free
870Gb Ext4 Data Partition, shared amongst all installed distros

```

You can adapt it accordingly to use with Windows.
If you want to share the 'Data Partition' with windows as well then, format it as NTFS.
It is a good idea to keep ESP (EFI System Partition) as your first or second partition.
It doesn't matter where you place SWAP partition but in the past years we'd keep it upfront so when needed it will be quickly available.

UEFI firmware though a 'standard' is not being implemented by the OEMs as such. UEFI varies from OEM to OEM. Some need special attention during install.
So finding a step by step guide which may apply to you is not easy. *oldfred's* post offers most of the information you need.

Just install Ubuntu after you've set up your HDD partitions.

Note: Do NOT use any auto install method option offered by the installer. Choose 'manual' method aka, 'Something Else' and install to the partition you've readied for the purpose.
Otherwise you may run the risk of wiping out all the other partitions from the HDD and new ones created.

---

### Post by speedman2202 on 2014-06-06
> **oldfred said:**
> Is Windows booting in UEFI mode? If drive is gpt it must be in UEFI mode to work.

Best to backup your Windows, even if you do not now think you need it. Many later come back and have one game, one application, or school or work that has to run on Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And make a Windows repair flash drive. Most Windows repairs cannot be done from Linux.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

One suggestion, adjust as you see fit.
      
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

These are now older, but the install process has not changed much.
 Intel - Install Ubuntu 12.10 part 3 of series for new system  w/secure boot, part one install keys, part 2 install Windows 8
[https://www.youtube.com/watch?v=_cEwj8bBBC4](https://www.youtube.com/watch?v=_cEwj8bBBC4)
Acer Windows 8 Video on getting into UEFI
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
Dual-Boot Windows 8 and Ubuntu 12.10 (BIOS)
[http://www.youtube.com/watch?v=wNCSbTyUzoM](http://www.youtube.com/watch?v=wNCSbTyUzoM)


thx mate , i have the full knowledge about what i am doing now , but .... i just download the latest version from Ubuntu and now being busy in my final exams ..... but i have some questions:

1- i am current working and installing in 8.1 and have another 3 partitions (NTFS) , and there is 100GB un mount space for Linux Distro's ( partitioned like  ....|fat32| |anotherone| | c| |freespace| |D| |E| |F| ) that i desire to install ....should i choose manual install or Automatic one!!!!

2-if i wanna remove/add win8.1/ubuntu/other destro (manage the Boot menu just in case ) , how i will do that??!!!



and really thx soo much for ur help ... and for now , i will made the thread is resolved and after do installing process  and face any kinda of problem , i will replay here again as soon as have time to install the OS 

 


> **fantab said:**
> HDD partitions are a very personal thing, yet important. If set up 'properly' (as per YOUR needs) then they could last the life of the HDD.

I have another example for you, (all Partitions in a GPT are Primary):
Total Space=1TB
```
300Mb FAT32 ESP 'boot'flag   
4Gb Swap
25Gb Ext4 Ubuntu 14.04 '/'
25Gb Ext4 other Distro '/'
25Gb Ext4 other Distro '/'
25Gb Ext4 other Distro' '/'
25Gb Free
870Gb Ext4 Data Partition, shared amongst all installed distros

```

You can adapt it accordingly to use with Windows.
If you want to share the 'Data Partition' with windows as well then, format it as NTFS.
It is a good idea to keep ESP (EFI System Partition) as your first or second partition.
It doesn't matter where you place SWAP partition but in the past years we'd keep it upfront so when needed it will be quickly available.

UEFI firmware though a 'standard' is not being implemented by the OEMs as such. UEFI varies from OEM to OEM. Some need special attention during install.
So finding a step by step guide which may apply to you is not easy. *oldfred's* post offers most of the information you need.

Just install Ubuntu after you've set up your HDD partitions.

Note: Do NOT use any auto install method option offered by the installer. Choose 'manual' method aka, 'Something Else' and install to the partition you've readied for the purpose.
Otherwise you may run the risk of wiping out all the other partitions from the HDD and new ones created.


i am planning left about 25 GB for linux files (EXT4) and rest 75Gb for install/add other destro , that i am planning for and above i show u how my HDD is partitioned , and thx for ur suggest :)

---

### Post by oldfred on 2014-06-06
You cannot create partitions from Windows for Linux. You have to have Linux formatted partitions.
Hopefully it did not convert to dynamic partitions or LDM in gpt partitioning as that does not work at all with Linux nor some Windows repair tools.

Auto install uses all of the unallocated space. Better to create a partition with gparted and a swap. Then use Something else to choose that partition to install. Do the same for all additional installs, but you can use same swap.

---

### Post by tom94 on 2014-06-07
to run gparted, boot with a live disk or usb, then open ubuntu software manager, then find gparted and install it. Then run gparted, and follow this guide:
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

About windows 8.1: There are some compatibility issues about UEFI and coexisting linux and windows on the same hard disk. But if you insist on make it happen, i've suxceeded by following this order:
1- reboot with windows disk and install it following instructions; remember leaving enough free space for the step -2-
2- run with a live disk or usb of ubuntu, install as mentioned on the guide above.
3- Make sure, running UEFI BIOS at startup (try canc or some F* key at startup), that pc is not running with  SECURE BOOT. There shall be an option to disable it, and if not, there  should be an option to CLEAR the secure boot keys.
4- run again with the LIVE DISK after installation, and this time run boot-repair. Follow this guide:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

at the next startup, in GRUB LOADER, you should have ubuntu option along windows boot loader. 

There's not an easy way to "add and remove" os's. The only way is to install them. Fact is, when you install windows, it corrupts and delete other system partitions or boot loaders. So, as long you make sure every time to install it FIRST and manage it after whith linux os you should be fine.
If some step is not going as it should, don't panic, and remember you always have the live disks, and that you can browse the net for answers or seek support. It's fun and gratifying to make it on your own.

Whish you the best,
Tom.

---

