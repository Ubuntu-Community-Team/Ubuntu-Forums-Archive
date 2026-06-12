---
title: "Problem &quot;No root file system is defined&quot; during installation process"
date: 2013-07-17
forum: Installation &amp; Upgrades
---

### Post by akhil23uchil193 on 2013-07-17
I have windows 7 (64 bit) installed in my laptop & want to use ubuntu 13.04 with it. So i tried installing it (through wubi i guess) which extracted all files & asked me to reboot the computer. When i rebooted the computer, it started checking for configuration and other details & then a pop up message appears saying that "No root file system is defined. Please correct this from the partitioning menu."

      What is the root file system? where is it defined? what is partitioning manager? how can i access it?

I have seen a similar problem in one of the thread.
[http://ubuntuforums.org/showthread.php?t=922331](http://ubuntuforums.org/showthread.php?t=922331)

I tried following the post mentioned in the third spot from the last. But i couldn't run that command.  Is there any specific way to execute that command? 

Or can i overcome this problem by any other method?

---

### Post by Old_Grey_Wolf on 2013-07-17
Moved to Installation & Upgrades forum.

---

### Post by Old_Grey_Wolf on 2013-07-17
If you did try to install Ubuntu 13.04 with WUBI then you have a problem. The last time I read about it, WUBI did not support Ubuntu 13.04. WUBI does support Ubuntu 12.04. You may try to install Ubuntu 12.04 which is a Long Term Support release.

I would recommend a true dual-boot rather than WUBI in either case.

---

### Post by akhil23uchil193 on 2013-07-17
Can you please help me in the process of how to do true dual boot instead of using wubi?
And there isn't any problem in true dual boot? I had heard earlier that if you perform dual boot, it might cause a problem when you try to uninstall either of them?

---

### Post by fantab on 2013-07-17
NO. There is no problem in true dual-boot. WUBI was meant for Windows Users to 'TRY Ubuntu' before doing a 'true dual-boot'.
Wubi install inside windows is just like any software application you install and run in Windows. You can remove it from Windows using Add/Remove software or something similar. 
Since you tried installing then there is possiblity that you may have to remove it first from Windows, Here's a how to: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

Does your HP have Windows8 or Windows7? Pre-installed? If you have pre-installed Win8 then you could be booting in UEFI mode. This needs a few extra steps compared to 'Legacy BIOS boot' mode.

A screen shot of your Hard Disk and its partitions taken from Windows Disk Management tool will help us help you.
Download Ubuntu.iso and burn it to a USB/DVD. Boot with it and "Try Ubuntu without Installling", this will load Ubuntu, wait till the desktop is fully loaded. Open Terminal (Ctrl+Alt+T) and run the following commands:
```
sudo parted -l
sudo fdisk -l
```
... then post the outputs here.

---

### Post by bcbc on 2013-07-18
If you got a "no root filesystem is defined" error with Wubi, you'll get it when you do the normal dual boot. That's an error from parted, which is used by ubiquity, the ubuntu installer. 

Typically the problems are either some GPT metadata leftover on a disk that's now MBR formatted. Sometimes it can be an unsupported Raid or MBR partition table errors (like a partition that ends outside the disk). When you provide the results that fantab asked for it will become clear what the issue is. 

PS It can't be a UEFI computer, or the Wubi install wouldn't have got that far.

---

### Post by akhil23uchil193 on 2013-07-19
Instead of burning into a dvd/pendrive, i tried rebooting the ubuntu image file through virtual disk using daemon tools. The computer booted normally and there isn't anything installed. Could there be any fault in the image file i have?
Is booting through a virtual disk any different from booting through dvd/pendrive?
And my hard disk and its partitions are as follows
[ATTACH=CONFIG]244859[/ATTACH]

---

### Post by Old_Grey_Wolf on 2013-07-19
I do not have experience with trying to install Ubuntu using a VHD. I don't know if many people on the forum do. I have googled the subject. It seems to be more complicated than following the [instructions on the Ubuntu site]("http://www.ubuntu.com/download/desktop/install-desktop-long-term-support") for 12.04. **Maybe** you will get the answer you are looking for.

These are the Ubuntu instructions for [installing Ubuntu 13.04]("http://www.ubuntu.com/download/desktop/install-desktop-latest").

---

### Post by fantab on 2013-07-20
> **akhil23uchil193 said:**
> Instead of burning into a dvd/pendrive, i tried rebooting the ubuntu image file through virtual disk using daemon tools. The computer booted normally and there isn't anything installed. Could there be any fault in the image file i have?
Is booting through a virtual disk any different from booting through dvd/pendrive?

It is possible that you have a bad download. Do a [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM") to find out.
Look in your Windows 'C' partition or where ever your Windows System files are for:
C:\ubuntu 
C:\wubildr* 
And remove them. For more see [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

From Ubuntu Live DVD/USB post the output of the commands:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by akhil23uchil193 on 2013-08-13
Sorry for the late reply, but i couldn't get a ubuntu disk. Today i got it & tried the commands given above. This are the screenshots of the outputs. I couldn't understand it properly but it says absence of partition table. Please advise me how to proceed.
[ATTACH=CONFIG]245331[/ATTACH][ATTACH=CONFIG]245332[/ATTACH]

---

### Post by fantab on 2013-08-13
NO it doesn't say anything about 'absence of Partition table'. You have 'msdos' partition table as the output of 'sudo parted -l' shows us.
Here is your problem:
'msdos' Partition Table can only have FOUR Primary Partitions, which you already do. You cannot make a fifth. (You can actually but Windows will turn the HDD into a 'Dynamic Disk' and Linux/Ubuntu won't work on it).
To overcome this limitation you will have to delete one of the partitions on the Disk and make a new EXTENDED Partition. (An Extended partition is a Primary Partition but also acts as a container for Logical Partitions. We can have more than 100 Logical Partitions).
In your case DELETE either 'D' or 'F'. But before you do that, BACKUP all your important DATA. 
Boot Ubuntu DVD/USB and 'Try Ubuntu without installing'. Let the desktop load. Open Gparted. Select the 'unallocated space' and create an EXTENDED PARTITION. Apply changes. You will notice that you still have 'unallocated space'. Now create LOGICAL Partitions as needed and format as required. For instance:
25-30GB Logical Ext4 (Mountpoint=/) for Ubuntu system.
2GB Logical SWAP
All the remaing GB Logical Ext4 to store linux data. (If you want to share data between Ubuntu and Windows then format it as NTFS.)

Close Gparted. Install Ubuntu from desktop. When the installation reaches the dialog 'Installation Type' choose 'SOMETHING ELSE'. At the next dialog select the 25-30GB Logical Partition and Use As=Ext4, Mountpoint=/. Apply changes. Then select 2GB partition and Use As= SWAP. Proceed with rest of the installation.

Good Luck....

---

### Post by bcbc on 2013-08-13
@Fantab, there is already an extended partition on /dev/sda as well as a logical partition. So that's not the problem. Besides, ubiquity checks for that - it's not an error condition - it will still install with Wubi or allow you to replace the entire drive with Ubuntu.

@[**[COLOR=#000000]akhil23uchil193[/COLOR]**]("http://ubuntuforums.org/member.php?u=1840219") The error is that you "can't have a partition outside the disk". It's unclear where that error is from - fdisk says that the 32GB /dev/sdb has an invalid partition table. Parted says that /dev/sdb doesn't have a label, and then that the partition cannot be outside the disk. So I'd guess its complaining about /dev/sdb. From your earlier screenshot from Windows, it shows it as an 11GB uninitialized disk with an unallocated partition. Can you just remove this before installing? Or format it?

---

### Post by akhil23uchil193 on 2013-08-16
I would like to initialize that disk (11GB) but am worried to do as i don't what that disk belongs to. Is it related to the SSD as my laptop has 500 GB HDD + 32 GB SSD? Initializing it won't cause any problem to booting system? Any idea what that disk might be related to?
And any idea about system reserved drive? will anything important be stored in 99MB which isn't accessible to users? If not, can i can extend that drive into c drive?

---

### Post by bcbc on 2013-08-16
You're right to be cautious. Maybe the 32GB SSD is used for caching. Open the "Intel Rapid Storage Technology" app from the system tray and see if it is running. 

I don't know what the 99MB system partition is for. It's not a boot partition, and most likely has something to do with system recovery. But you don't need to do anything with it because you already have an extended partition. So there's no need to delete a primary partition and all the effort you will go to, to merge it with C: will only give you an extra 99MB which is not worth it. Just leave it and forget about it.

---

### Post by akhil23uchil193 on 2013-08-17
I guess that 11 GB belongs to SSD as rest make up 466GB which is the  usual capacity of a 500 GB harddisk. If that's the case, what should i  do next? 

@bcbc: I guess the ssd is working. This is the homepage of intel rapid storage technology. What do you say?

[ATTACH=CONFIG]245435[/ATTACH]

---

### Post by bcbc on 2013-08-17
Well, the thing is that, while the SSD is working properly on Windows - with a striped setup to increase speed (raid 0) - it appears invalid to *parted* and I'm not sure how you'd fix it so it appears correct to *parted* but still working on Windows.

Your options would be to either:
1. use a partitioning tool to repair it (hopefully without breaking IRST functionality) - this seems like the easiest option.
2. rebuild it using IRST manual/documentation?

I'd be looking at the documentation that came with the system or asking on the intel forums (or perhaps the manufacturer of the computer) to see if anyone else encountered something like this.

---

### Post by akhil23uchil193 on 2013-08-19
so may i know which partitioning tool should i use? any guidance? i have no idea about it.

---

### Post by fantab on 2013-08-20
AFAIK, Intel SRT (Smart Response Technology) will NOT work with Linux. You have to DISABLE it. It only works with Windows. It is only used for 'cacheing', it speeds up Windows a bit but does not affect its overall functionality. You can live without it.
I suggest you [DISABLE SRT... format SSD]("http://superuser.com/questions/476777/properly-disabling-intel-srt") and use it to install Ubuntu on the space you retreive.

Once you have disabled Intel SRT you can use **Gparted** to reformat and recreate partitions on SSD.

More Info: 
[http://www.gossamer-threads.com/lists/gentoo/user/274027](http://www.gossamer-threads.com/lists/gentoo/user/274027)
[http://ubuntuforums.org/showthread.php?t=2097815&p=12420448#post12420448](http://ubuntuforums.org/showthread.php?t=2097815&p=12420448#post12420448)
[http://askubuntu.com/questions/308481/howto-run-ubuntu-with-uefi-and-intel-smart-response-technology](http://askubuntu.com/questions/308481/howto-run-ubuntu-with-uefi-and-intel-smart-response-technology)

---

### Post by akhil23uchil193 on 2013-08-22
So finally i will have to disable the ssd? I guess it won't be much of a  problem but can i make it function as it is functioning now if i want  to remove ubuntu in the future? And is compulsory that i install ubuntu  is the ssd drive and not in the other drives as many said in those  links?

---

### Post by akhil23uchil193 on 2013-09-05
Can i re-enable my ssd for its normal functioning if i remove ubuntu in near future after formatting it now?

---

### Post by akhil23uchil193 on 2013-09-14
Will my ssd function with ubuntu if i remove windows and install ubuntu in place of it?

---

