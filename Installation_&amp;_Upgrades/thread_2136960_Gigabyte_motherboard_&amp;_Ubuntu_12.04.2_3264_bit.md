---
title: "Gigabyte motherboard &amp; Ubuntu 12.04.2 32/64 bit"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by johnaaronrose on 2013-04-19
I've done this post as a result of reading [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI). Just a note on my experiences with a Gigabyte motherboard (GA-H61M-S2PC 2.0 with 8GB memory) and installing Ubuntu 12.04.2. The UEFI BIOS does not appear to have parameters for Quickboot/FastBoot or Intel Smart Response Technology (SRT) or Secure Boot. Do these parameters have other aliases? 

I intended to only have Ubuntu on the PC's hard disk. What are the advantages of UEFI when that is the case?

I installed 12.04.2 64 bit from a USB stick created by Startup Disk Creator. But it did not pick up (lsusb did not show it) my Logitech Webcam properly for use in Skype, set up Virtual Magnifying Glass properly, and Wine has to have a 32 bit prefix setup with /etc/environment modified appropriately. 

So I tried to install 12.0.4.2 32 bit from a USB stick (created by using Startup Disk Creator). However, BIOS would not let me as it said that it does not have a bootloader: interestingly the BIOS shows that it is a UEFI device. This seems to contradict the article [http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/ ]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")which states "And as part of our committment to enabling new hardware on the current LTS release, we will be backporting this work for inclusion in 12.04.2." (though does that mean that it will be done sometime after the release of 12.04.2 in February 2013?). I was able to install 12.04.2 32 bit from a DVD, presumably because the BIOS did not show it as UEFI. [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" (from [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)) shows that the HDD is Legacy boot.

---

### Post by oldfred on 2013-04-19
The quikboot/fastboot seems to be primarily Windows 8  setting to skip most or all of the BIOS/UEFI startup. Secure boot is a UEFI setting but only Microsoft with Windows 8 required it to be implemented, most motherboard vendors have not yet implemented it.
Intel SRT is a Windows cache program that uses a small SSD. Not sure you can install yourself as I only have seen it  on newer UltraBook laptops. Again to make it seem like Windows is booting faster when it really is only recovering from hibernating on an fast SSD.

UEFI has new features, is the future, but most users do not understand it. If you have only Ubuntu you can install in either UEFI or Legacy/CSM/BIOS mode. 
But I would suggest using gpt partitioning even if booting in BIOS mode. With UEFI gpt partitioning is required. Then you could convert to UEFI in the future if desired. Ubuntu will boot from gpt partitioning in BIOS or UEFI, but Windows will only boot from gpt partitioning with UEFI.

I did find a link to gigabyte's UEFI update page, but did not save it as my motherboard was too old. They have a major UEFI/BIOS update to convert some newer motherboards that had a limited UEFI to a full UEFI.

Since only newer computers can run with UEFI, only the 64 bit version supports UEFI. If you have a newer computer you should be installing the 64 bit version anyway. But you will not have any issues of secure boot. 
And all the updates to UEFI are included in the newer versions with secure boot capability, so I would use those new version only.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
Installing Grub for UEFI secure boot is only possible if you have booted your system using EFI. 

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by johnaaronrose on 2013-04-19
Can any disk be made into GPT? If so, how?  I still don't see how UEFI is advantageous to an end user like me. Please explain.  I don't even see how 64 bit Ubuntu Precise is better than 32 bit for an average end user. Please explain how. As I previously said 64 bit did not recognise my Logitech Webcam.

---

### Post by fantab on 2013-04-19
Lets say, UEFI is the new alternative (and later replace) BIOS. Like oldfred says its the future. UEFI supposedly communicates better with the Hardware. "[Demystifying UEFI]("http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement")" should allay your doubts.

Similarly, 64bit is the future, and is faster than the 32bit to say the least. We still have 32bit around because there is still a lot "older" hardware around that can only run 32bit max. [**THIS**]("http://www.techsupportalert.com/content/32-bit-and-64-bit-explained.htm") should help you.

I am not sure why your Webcam was not recognized by 64bit Ubuntu. However, most of the Logitech wecams work out of the box on Linux. Once you install 64bit we can work on that as well.

AFAIK, any Disk (HDD, USB flash, external) can be converted to GPT. But to that you will have to Delete all the partitions and then change the partition table to GPT. Our regular MSDOS table won't support more than 2TB Drives/Disks and it has only 4 Primary Partition Limitations. Where as with GPT we can have more than 100.

---

### Post by oldfred on 2013-04-19
I first used gpt just to learn about it with my install of 10.10 on an old 160GB drive that I totally reformatted.
Since then all new drives are now gpt partitioned including my SSD & a 16GB flash drive with a full install of Ubuntu.

 I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning.

You can also use gdisk which is the command line replacement for fdisk with gpt partitioning. You may be able to convert to gpt from MBR. It is in repository.
      
 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

If you have more than somewhere between 2 & 3GB processing will be faster. If you have more than 3GB, the 64 bit version will directly access the memory rather than using the PAE kluge to swap memory in and out.
      
 Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by johnaaronrose on 2013-04-19
Thanks, oldfred & fantab for your replies. I understand a little better about UEFI.

I noticed that oldfred stated:
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better  to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 (for UEFI boot or future use for UEFI, you only  can have one per drive, so if already existing do not attempt another)
gpt: 1 MB bios_grub no format (for BIOS boot not required for UEFI)
gpt or MBR(msdos)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Is this all done as Ubuntu installs? What does "gpt or MBR(msdos)" on a line on its own refers to? As I have a 730GB disk, should I have the partitions (all as GPT Primary):
250 MB efi FAT32
25 GB  / ext4
all but 2 GB (e.g. 700GB) /home ext4
2 GB swap

I have a problem with the PC freezing: this started to happen about 2 weeks ago. It seems to happen when scrolling webpages in Firefox. Could this be due to not using UEFI as I didn't specify it either in the 32 bit install or the 64 bit install?

I also wondered if it would be a good idea to Flash the latest BIOS (for my motherboard) that I've obtained from Gigabyte's website before doing the Ubuntu 64 bit install. What do you think?

---

### Post by oldfred on 2013-04-19
I do not think installer gives choice on gpt or MBR(msdos). And Ubuntu will install in either. But with UEFI only gpt works. And installer does default to gpt if drive is somewhere over 1TB and drive is not partitioned.

I have always partitioned in advance then used manual install to format and mount partitions. But you can do it as part of install.

I do not think a freezing issue is related to UEFI or BIOS or 32 bit or 64 bit. But there have been several threads on freezing issues.

Generally the recommendation is to only update BIOS if the update fixes a specific issue you have. But UEFI is changing a lot in a short time, so I would probably do the upgrade if it was me.
My old Gigabyte board did offer several ways to upgrade BIOS. Either from Windows, a bootable flash drive, or just a file on the flash drive(which is what I use).
Also an update to UEFI/BIOS resets to defaults. If you have made any changes to settings in UEFI/BIOS you have to reset them. I found I lost a lot of settings, had to rediscover them and then took photos of every screen for next time. I think UEFI may be better as it can save settings to its memory.

---

### Post by johnaaronrose on 2013-04-19
Is sequence of what I have to do is:

1. Boot from 64 bit on a USB stick (after flashing latest BIOS) & select try out Ubuntu & set disk as GPT by using 'create partition table' with gparted? 

2 Create primary partitions with gparted?
250MB efi FAT32
2GB swap
25GB  / ext4
all but 2GB (e.g. 700GB) /home ext4
2 GB swap

3. Install 64 bit Ubuntu.

---

### Post by oldfred on 2013-04-19
That should work. 

From UEFI menu when booting flash drive you should get two choices. One is usually pretty clear that it is UEFI and the other BIOS/Legacy/CSM or something that is not UEFI. 

How you boot flash drive live installer is how it installs.

You have not mentioned video. I have nVidia and have to add nomodeset on every live installer boot, and first boot after install or until I get nVidia driver installed. Some motherboards also need other boot parameters, but best to see what happens first.

---

### Post by fantab on 2013-04-20
Instead of having a separate /home you can have a simple ext4 formatted partition to house your DATA. If you don't create a separate /home your "Home" folder will be created in '/' partition. One out right advantage is that you don't have to worry about your DATA too much when re-installing or installing newer versions of Ubuntu. Secondly, if you later decide to have more than one Distro on your HDD this setup will come in handy, as it is not recommended to share a common /home between different distros.

Suggested Partition Scheme:
250MB efi FAT32
2GB swap (if you hibernate your computer then you must have SWAP equal to or more than your RAM)
15-20GB  / ext4
15-20GB  ext4 (in case you want to install another version of Ubuntu or another Linux Distro). I have three distros on my HDD.
Remaing GB ext4 for DATA.

The Shared ext4 DATA partition can be automounted with Ubuntu on boot using /etc/fstab or manually mounted after Ubuntu boot from 'file-manager', by clicking on the device. I save my Data to DATA partition by changing the default save path in applications to save in my DATA partition. For instance, I have set the save path in firefox downloads to save in DATA partition. (By default, firefox saves our downlods to 'Downloads' folder in 'HOME"). There are other methods too, if you are interested.

My two cents....

---

### Post by oldfred on 2013-04-20
I agree with fantab and use data partitions myself.

But very new users probably only need the default install of / (root) and swap.

If a newer user understands partitions a little bit and will just be reinstalling to upgrade then the separate /home makes good sense.

And any user dual booting with Windows should have a NTFS data partition for shared data and set Windows system partition as read-only from Ubuntu to avoid issues.

And like fantab & myself smaller system partitions and large data partitions that can be shared with different installs is for those that may want to multi-boot, or even upgrade by installing in another partition keeping old install. It is a bit more advanced as you are into editing fstab to mount partitions and setting ownership & permissions to use partition. None of which is really difficult but can be a lot for a new user who just wants a system that works.

---

### Post by johnaaronrose on 2013-04-21
2 more questions:

1. size of swap: computer according to Sysinfo has Memory Total of 7989MiB & Swap Total of 8,084MiB. What should I allocate to swap partition (in gparted)? My guess is 8GiB.

2. size of home: Disk Usage Analyser states that disk is 730.8GB. Does gparted automatically allow specifying rest of disk for this partition (i.e. after specifying swap, 25GB for / (excluding /home)? If not, if I specify 690GiB for this in gparted, would it tell me if there is room?

---

### Post by oldfred on 2013-04-21
With 8GB of RAM you will never use swap unless you hibernate or edit large videos and have ever program you have open at once. I have 4GB and never use swap, but I only open at most a couple of larger apps and maybe a couple more smaller apps. If you want to hibernate you need the 8GiB swap just in case you are editing all that video and have almost filled RAM. But Ubuntu boots quickly, so hibernation does not save much if any time. IF you do not hibernate, I would just have 2GB of swap just to have some.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
    
If you are manually installing or Something Else you have to specify all partitions, only if swap already exists will it reuse the existing swap. I only install in 25GB root partitions on my various drives and use a script to edit & mount my data partitions since I was doing the same thing over and over when reinstalling a beta or testing someting. And it finds my swap on other drives. I have swap on two drivis and it usually auto mounts both and I have to delete one.

---

### Post by johnaaronrose on 2013-04-22
What's the difference between /home & data partitions (and how are data partitions used by the installer)? If a new version of Ubuntu was to be installed, would this mean that all existing partitions would be used by the installer but only the efi, /, swap partitions would be changed? And given that app config files reside in the /home partition, would they be left alone?

---

### Post by oldfred on 2013-04-22
You can only have one /home and it will have all your data and mostly in hidden files & folders user settings to configure your screens and applications. Some applications also store data in their folders also. If you reuse an existing /home you have to mount it as part of your install, but DO NOT format it. It will then keep your existing data and most settings, but may write new settings for new applications or updates apps need. If you format /home of course it then overwrites everything.

I leave /home inside my / (root) so it really only gets defaults. I may copy settings from a previous install or my own install script modifies some settings. And all data is in other data partition(s) like Docuements, Music, Videos etc. I also move some of the hidden folders like Firefox & Thunderbird profiles.

The installer only has options for system related partitions, but they have changed it and I am not sure of all those changes. I always just install to /  in an existing partition and quickly go thru that screen. I edit fstab after install to add my /mnt/data partition.

Severals posts on size of / and use of linking to data partition.
[http://ubuntuforums.org/showthread.php?t=2137726](http://ubuntuforums.org/showthread.php?t=2137726)

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

