---
title: "How to install Windows 8/8.1/10 after Linux Ubuntu 14.04 in UEFI"
date: 2015-08-05
forum: Installation &amp; Upgrades
---

### Post by john435 on 2015-08-05
Hello guys, 
this is my first time posting here, but I've been reading this forum for long time. I'm light linux user, nothing special, but now I need your help.
I've just bought new Dell Inspirion 3543 Laptop, with preinstalled Ubuntu 14.04, but I have to install Windows due to required school software. I tried  install Windows 8 from DVD, but it said it can't due to EFI partition or something like that, so I assume that Ubuntu is installed in UEFI and later I even saw that partition I've tried to install is formated in ext4. So basically what is the process I should follow to install windows alongside preinstalled Ubuntu 14.04.
Thanks in advance

---

### Post by ruzekle on 2015-08-05
The safest route would be to install it on a virtual machine like VMware or VirtualBox.

Otherwise you'll need to backup your data, resize your partitions via a LiveCD, create an NTFS partition. Install Windows in that reserved NTFS partition.

Boot via the LiveCD. Reinstall grub with sudo update-grub. You can also use boot-repair. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Vladlenin5000 on 2015-08-05
+1 to a VM. 

Dual boot in such scenario is for experts only and even them will have a hard time figuring out the best configuration. 

PS - A school requiring proprietary software is no school, it's a FRAUD.

---

### Post by yancek on 2015-08-05
> I tried  install Windows 8 from DVD, but it said it can't due to EFI partition or something like that

Specifics rather than "something like that" would be more useful.  There should be no problem installing windows 8 in UEFI and in fact, almost all pre-installed windows 8 are UEFI.  The boot files for windows and Linux on a UEFI system would both be in a FAT32 formatted partition, generally at the beginning of the disk.
  
> I even saw that partition I've tried to install is formated in ext4. 

You can't install windows on a Linux type filesystem such as ext4, it won't work.  Do you have free space or an ntfs formatted partition on which to install windows?  If you could post an image from GParted showing your drives/partitions someone might be able to advise.  

If you haven't done this type of thing before, it will probably be a lot easier to do as suggested and use virtual software in Ubuntu.

---

### Post by oldfred on 2015-08-05
How you boot install media for both Ubuntu & Windows is how it installs.
And Windows only installs to gpt partitioned drives with UEFI, so if you boot in BIOS boot mode it will not install or will erase drive.
Or if you have a BIOS/MBR sysem and install Windows or Ubuntu in UEFI it will convert to UEFI/gpt partitioning erasing drive.

Make sure you boot in UEFI mode, and you must have available space for Windows. It also wants more than just one NTFS partition, typically a tiny Microsoft reserved unformatted partition must be before the first NTFS partition. It should find & reuse existing ESP - efi system partition, only one per device or hard drive.
 
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition
[/URL]
 Only 64 bit supported for UEFI boot Windows 7 but all Windows UEFI.
[URL="http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html"]http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html
      [/URL]
 Install Windows 8
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

    [URL="http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html"]
[/URL]

[URL="http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition"]
[/URL]

---

### Post by john435 on 2015-08-05
OK, I have checked and there is next partitions:
1) ESP (524 MB/ 502 MB free) 
2) DIAGS(42 MB)
3) OS(3.2GB)
4) Filesystem(488GB) ext4
5) Swap(8.4GB)
6) Free Space(1.1MB)

So from above I can see that is UEFI boot, sorry for being unclear.  I know that I will have to make UEFI bootable drive, it's not problem. DVD I've tried is MBR ISO based, tipically burnt with ImgBurn. I've installed ubuntu and windows many times before, but this is my first touch with UEFI. So i should shrink this large partition of 488GB which is ext4, and make new partition and format it in NTFS so I can install Windows, right? But how many partition should I make for UEFI windows? Is this ESP partition only for Ubuntu bootloader or is it Windows going to make new ESP partition for itself or it will delete and make there just linux entries (or or or :) ), I'm totaly confused with this??

I'm also afraid that dell would void warranty if I completely format HDD(and remove this DIAGS partition), and than install windows first, and Ubuntu second. So this dual boot would mean so much.

P.S. If there's anyway I can thank you I'll do it even with a coffe :)

---

### Post by oldfred on 2015-08-05
I recently bought a Dell SFF with Windows 8. I did not plan on using Windows but made all the backups suggested. But it took multiple DVDs & flash drives. I had a Dell backup, a Windows backup & a full backup of entire system. 
With Linux I do not back up system since that is easy to download & reinstall. But do backup settings & /home and all data and now with UEFI, I backup my ESP separately.
You should have good backups & a working live installer flash drive of the current version Ubuntu you have installed.

You need the Microsoft Reserved partition if you partition in advance. See post above.

You can only have one (some exceptions) ESP - efi system partition per device. That is the FAT32 formatted partition with the boot flag or your first partition. Windows & Ubuntu will create separate folders in the ESP. Not all systems have the /EFI/Boot folder in the ESP. 

/EFI/Boot
/EFI/ubuntu
/EFI/Windows

The ESP partition is just for UEFI boot and should not be confused with the Ubuntu /boot. The /boot may be a partition or a folder inside / (root). Generally desktops do not need a separate /boot partition. Not sure if your OS partition is / (seems small), /boot or something else?

---

