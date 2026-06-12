---
title: "Dual Boot Windows 8.1 with Ubuntu 14.04 UEFI with caching SSD and HDD"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by anonymouschief on 2014-04-23
Hello Folks,

I am trying to dual boot Ubuntu desktop 14.04 with Windows 8.1 on an Asus Ultrabook (Vivobook). This device has a 24GB SSD and a 750GB HDD. I can see the HDD in Windows Disk Management but not in Explorer, so I guess the SSD is a caching disk.

I have created the partition for Ubuntu using Windows (it is the 26GB in the results below), but I would like to know what steps to take to ensure that I do not mess up Windows 8. I am posting this from within a live disk Ubuntu. Plese let me know what I need to do so as not to mess this up. Thanks.


```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  316MB   315MB   fat32        EFI system partition          boot
 2      316MB   1259MB  944MB   ntfs         Basic data partition          hidden, diag
 3      1259MB  1394MB  134MB                Microsoft reserved partition  msftres
 4      1394MB  301GB   300GB   ntfs         Basic data partition          msftdata
 5      301GB   301GB   472MB   ntfs                                       hidden, diag
 6      301GB   702GB   400GB   ntfs         Basic data partition          msftdata
 7      702GB   729GB   26.8GB  ntfs         Basic data partition          msftdata
 8      729GB   750GB   21.5GB  ntfs         Basic data partition          hidden, diag


Model: ATA SanDisk SSD U100 (scsi)
Disk /dev/sdb: 24.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
 2      1049kB  6443MB  6442MB  ntfs         Basic data partition  hidden
 1      6445MB  24.0GB  17.6GB               HFS


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!  


```

---

### Post by oldfred on 2014-04-23
Do not create partitions with Windows. It cannot create Linux formatted and may convert from basic to dynamic or LDM in gpt partitioned drives.

Some install ? (root) to SSD, but then do not have the speed up in Windows that the cache gives. But Ubuntu then is a lot faster. :)

I do not know if from the installer you correctly see all the partitions and if grub will install correctly. The Windows cache or Intel SRT used to cause major issues, then was only a grub install issue.

Always best to fully backup Windows just in case and make a Windows repair CD or flash drive as you may need those if Windows has issues.

If you have rebooted Windows it should have done its chkdsk or fixes to its new size.
Turn off fast boot and turn off Intel SRT if that is the cache you have.
Often better with secure boot off, but should not be required.

       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

The Intel SRT is the same across vendors, but other settings may be different.

 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

 Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)


  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)

May not be required now?

 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

---

### Post by anonymouschief on 2014-04-24
I prefer to keep the Windows SSD cache feature.
In which partition do I set as the "Device for boot loader installation"? Do I use the root partition that I will create for Ubuntu on /dev/sda* or I set it to /dev/sda?
Also, how do I uninstall Ubuntu if things do not go well; it is neat to have a backup plan.

---

### Post by anonymouschief on 2014-04-24
Also, what does the following mean?

```

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!
```

Thanks,
AC 
:popcorn:

---

### Post by oldfred on 2014-04-24
The DVD is oversize for a CD. 
sr0 is the cd/dvd drive which is read only.

Best to have full back up of Windows and a Windows repair cd or flash drive.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

With UEFI each system installs another folder with boot files into the efi partition. You must boot Ubuntu in UEFI mode for it to install in UEFI mode. But you still specify sda as install location for grub and it knows with UEFI to install files into the efi partition.

      
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Change default boot to Windows in UEFI. Windows often will do this with any update, or maintenance.
You can just delete the Linux partitions and the ubuntu folder in the efi partition. UEFI also has its own NVRAM and stores the ubuntu boot as an entry, so you have to delete that. Some UEFI let you delete directly, others require you to use efibootmgr which is a command line tool.
      
 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by anonymouschief on 2014-04-24
[COLOR=#000000]I prefer to keep the Windows SSD cache feature.[/COLOR]
[COLOR=#000000]In which partition do I set as the "Device for boot loader installation"? Do I use the root partition that I will create for Ubuntu on /dev/sda* or I set it to /dev/sda?[/COLOR]
[COLOR=#000000]Also, how do I uninstall Ubuntu if things do not go well; it is neat to have a backup plan.[/COLOR]

---

### Post by oldfred on 2014-04-24
Is it UEFI or BIOS.
If UEFI, you just have to set to boot Windows by default instead of Ubuntu.
If BIOS you need to reinstall a Windows boot loader to the MBR.
You can use the Windows repair CD or Flash for that or Boot-Repair or just about any Linux live repair CD or flash drive. But most Windows repairs need the Windows repairCD.

You can use gparted to delete the new partitions you create. Gparted is on the Ubuntu live installer. Or use Windows third party partition tools. 
Generally use Windows tools for Windows and Linux tools for Linux. And Windows does not see Linux partitions, but Linux sees and can do some minor fixes to Windows.

---

### Post by anonymouschief on 2014-04-24
I am installing it now.

---

### Post by anonymouschief on 2014-04-24
Sorry, I forgot to say that the following page answered my last question about the "device for boot loader installation": [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

Thanks,
:KS
AC

---

### Post by anonymouschief on 2014-04-24
Thanks Oldfred. You rock!!! :guitar:The installation was successful.

I just need help with one more thing before considering this issue resolved.

Ubuntu sees all Windows 8 partitions through its browser. How do I hide some of them from showing up in Ubuntu's file manager?

Thanks,

:popcorn:
AC

---

### Post by oldfred on 2014-04-24
You can hide mounts by mounting them, or make them read only.
        
This has instructions on editing fstab.
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

    
 Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0
sudo mkdir /mnt/SysRes
#hide windows 7 second hard drive
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0
#hide windows 7 second hard drive
UUID=8A4029F24029E5A3 /mnt/reserved ntfs defaults,noauto 0 0
UUID=80A02B83A02B7F32 /mnt/win7 ntfs defaults,noauto,umask=777 0 0

    Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

   Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

---

### Post by anonymouschief on 2014-04-25
Thanks for the tip, oldfred. Consider this issue resolved.

---

