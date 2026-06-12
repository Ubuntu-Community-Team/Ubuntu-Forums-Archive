---
title: "Can't install Ubuntu alongside Windows 7"
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by creepy_turtle92 on 2014-07-23
Hello everybody.

When I try to install Ubuntu 14.04 (with Windows 7 already installed) I don't get the 'install alongside Windows 7' option.

[ATTACH=CONFIG]254952[/ATTACH]

Before I've tried to install Ubuntu, I shrinked partition with Windows 7 on.
I don't know much about Ubuntu (almost nothing at all). I've searched forums for the solutions, but nothing has worked so far. I've read in other threads to run these 2 commands:
```

sudo parted -l
sudo blkid

```

here is my output:
```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD5000BPVT-1 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   240MB  134MB  primary
 3      240MB   318GB  317GB  primary  ntfs


Model: Generic Flash Disk (scsi)
Disk /dev/sdb: 2097MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      65.5kB  2097MB  2097MB  primary  fat32        boot, lba


```

```

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0DE0176A0DE0176A" TYPE="ntfs" 
/dev/sda3: UUID="1A5CC6985CC66E57" TYPE="ntfs" 
/dev/sdb1: LABEL="UUI" UUID="1401-1E65" TYPE="vfat" 

```

Does anybody know how to fix this?

EDIT: I've tried to install Ubuntu from USB flash drive, if it matters.

---

### Post by TheFu on 2014-07-23
If you are looking for the old "WUBI" installs, those are gone thanks to UEFI and SecureBoot.
To run Ubuntu on a computer these days, 2 partitions just for Linux are required (/ and swap), however, 3 or 4 partitions would be a better idea for a future-Linux user to get used to so that updates to newer releases are less hassle.

Also, if you copy/paste data (instead of using images) then we can more easily review and respond.

[http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/](http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/) tries to explain things.  It appears you have an MBR formated HDD, so you will be getting into the old-school Extended partition + logical partitioning stuff to solve this.  Linux partitions can be in primary OR logical partitions, it doesn't care.

To get started, you'll need to resize your Windows Partitions to make it/them smaller (15-20G should be enough for a beginner). Use the windows tools to do that and leave free space.  I'd shift all the Windows partitions to the left, so they are next to each other (not at the end of the disk) too.
Next, use gparted to create an extended partition at the end of the disk, then add partitions for /, /home and swap based on your specific needs and system.  If you have less than 20G available, I wouldn't bother with a separate partition for /home - it will be a hassle at update time, but there are other hassles you will avoid by keeping those two together.

Of course, please, please, please make a save-your-butt backup that you absolutely KNOW can be restored before beginning. Partition stuff can be extremely dangerous and may wipe your HDD if a mistake is made.

---

### Post by Mark Phelps on 2014-07-23
If you're unable to make an image backup of Win7 to an external drive, at least use the Backup feature to create and burn a Win7 Repair CD.  That will provide you the tools needed to repair/restore Win7 booting should the boot loader become damaged from your dual-boot install.

Also, be sure to follow TheFu's advice and use ONLY the Win7 Disk Management tool to do any shrinking of the Win7 OS partition.  Don't use GParted or the Ubuntu installer to resize Win7 as that risks corrupting the windows filesystem.  IF you've already done the shrinkage, don't charge into the Ubuntu install just yet; instead, reboot into Win7 a couple of times to let it make the needed filesystem adjustments.

---

### Post by Bucky Ball on 2014-07-23
Resize Win7 partition with Win software, NOT Gparted. You can severely screw up the boot (for a start) using Gparted on that partition. Gparted works ok with xp partition, no other newer Win versions, though.

(Just noticed, as TheFu and Mark Phelps advise, but this can't be stressed enough so not a bad thing. ;))

---

### Post by creepy_turtle92 on 2014-07-23
OK, few more infos.

I did not try to install Ubuntu with WUBI, but downloaded Ubuntu, burned image to bootable USB flash drive and tried to install with it.

I did backup all my data before doing anything, no worries.

I used tutorial from the link above and I installed Ubuntu. BUT.
When computer restarted, it directly booted into Ubuntu. It didn't ask me whether I want to use Windows or Ubuntu. So I restarted computer once again, took out flash drive, but it didn't change. It just simply booted into Ubuntu.
I couldn't get into Windows so I decided to do everything all over again. This time I found tutorial of how to install Windows 7 after Ubuntu. So I installed clean Ubuntu again, deleting everything. After it had installed, it didn't boot into Ubuntu! After restart, computer gives a message something like 'insert boot device'. I restarted again, pressed F12 to get 'select boot device' menu where I get to choose 'Ubuntu' and it starts, but if I choose hard drive (that is my primary boot device) it gives the same message.
I could try and install Windows 7 now, but it is already behaving with no sense. What should I do?

---

### Post by oldfred on 2014-07-23
May be best to see details of where you are at. Post link to BootInfo report but do not run autofix until someone reviews details.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by creepy_turtle92 on 2014-07-23
[http://paste.ubuntu.com/7843474/](http://paste.ubuntu.com/7843474/)

---

### Post by oldfred on 2014-07-23
You have installed Ubuntu in UEFI boot mode, with gpt partitioning which UEFI requires.

You show no NTFS partitions.

Standard Windows 7 DVD installer is BIOS only and will not install to gpt partitioned drive.
Windows only installs to gpt partitioned drives with UEFI.
       Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

That may be why before that you did not get an alongside install option. Only if you boot installer in the same boot mode UEFI or BIOS as your other install do you get the along side option. To install Ubuntu in UEFI mode it had to convert drive to gpt which was a total drive reinstall.
Ubuntu installer has two boot options from USB flash drive installer. From UEFI/BIOS mode you get both UEFI and BIOS boot option on flash drive and how you boot flash drive is how it installs.

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by creepy_turtle92 on 2014-07-23
I had the black screen when opted to install Ubuntu. So, I installed it in UEFI mode.
If I got it right, I installed Windows 7 in BIOS mode which conflicted with Ubuntu and its UEFI mode? So I should install Windows in UEFI mode and then install Ubuntu the same way?

---

### Post by oldfred on 2014-07-23
Either both BIOS or both UEFI.

And if drive is currently gpt and you install Windows in BIOS mode it does not correctly convert drive to MBR(msdos) partitioning. You have to use fixparts to remove backup gpt partition table.

BIOS is old (since 1980's) and well known, but may not work well in future.
UEFI is relatively new (actually over 10 years old), but only used a lot when Apple converted to Intel chips and  Microsoft with Windows 8.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

You can get black screen with either BIOS or UEFI and often on first boot after install. Drivers are implemented differently with BIOS & UEFI.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by creepy_turtle92 on 2014-07-24
I really have no idea what should I do now. I hardly understand any of it. I'll try to install Windows 7 now UEFI mode and come back with the results.
UPDATE: First I noticed that my /home was between / and swap, so I couldn't make room for Windows 7. I went to reinstall Ubuntu and got this message:
> 
[COLOR=#000000]The partition table format in use on your disks normally requires you to create a separate partition for boot loader code. This partition should be marked for use as an "EFI boot partition" and should be at least 35MB in size. Note that this is not the same as a partition mounted on /boot.[/COLOR]

[COLOR=#000000]If you do not go back to the partitioning menu and correct this error, boot loader installation may fail later, although it may still be possible to install the boot loader to a partition.[/COLOR]

What should I do?
UPDATE2: I'm installing fresh copy of Windows BIOS mode. I guess it will transform GPT into MBR, but not completely. So after installation, I should use fdisk to fix whatever's left from GPT and then install Ubuntu (BIOS mode). I hope I'm doing t right now, it's all so confusing.

---

### Post by oldfred on 2014-07-24
FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If it was looking for an efi partition but you had Windows installed then Windows was not in UEFI boot mode.
Windows has to use gpt partitioning with UEFI and needs the same efi partition.
Both Ubuntu and Windows only boot in BIOS mode from MBR(msdos) partitioned drives.

But how you boot installer is how it will install, so just be sure to boot in mode you want.
      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by creepy_turtle92 on 2014-07-24
Solved!
What I did was:
1. Install clean Windows 7 BIOS mode, which created MBR partition table
2. Used FixParts to delete any remaining GPT staff
3. I got warning something like '0xEE isn't in first sector'. Fixed it by installing clean Windows 7 one more time
4. Installed Ubuntu BIOS mode (it finally showed 'install alongside Windows 7' option)
5. Hooray, it works

Thank you for links and help.

---

### Post by Bucky Ball on 2014-07-24
Good work. Enjoy!

---

### Post by satheasan on 2015-05-29
Check your Windows partitions.(My computer-Right click-Manage-Disk Management) If the The partitions are 'Dynamic' You can't Install Ubuntu like this.You must change the partitions to 'Basic' by
1. Using a third party software.But you must pay for it.  
                or
2.Connect your Hard drive to another system and change the partitions to 'Basic'.
         or
3.Format your Hard drive using The Ubuntu CD. Then Install Windows first and You can Install Ubuntu easily. If you use the second or third way you must back up your datas.

---

### Post by Bucky Ball on 2015-05-29
> **satheasan said:**
> Check your Windows partitions.(My computer-Right click-Manage-Disk Management) If the The partitions are 'Dynamic' You can't Install Ubuntu like this.You must change the partitions to 'Basic' by
1. Using a third party software.But you must pay for it.  
                or
2.Connect your Hard drive to another system and change the partitions to 'Basic'.
         or
3.Format your Hard drive using The Ubuntu CD. Then Install Windows first and You can Install Ubuntu easily. If you use the second or third way you must back up your datas.

Welcome. Thanks for your contribution, but old thread, already solved and ...

*Thread closed*.

---

