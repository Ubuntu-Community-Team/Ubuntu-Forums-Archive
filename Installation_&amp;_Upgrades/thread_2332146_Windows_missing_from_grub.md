---
title: "Windows missing from grub"
date: 2016-07-28
forum: Installation &amp; Upgrades
---

### Post by EricDallal on 2016-07-28
The short story is that I have Windows 10 installed on my computer, but that the grub lists only ubuntu as an available operating system. I have tried both "sudo update-grub" and boot-repair. Neither of them seems to detect the Windows OS. The Pastebin file from boot-repair is [here]("http://paste.ubuntu.com/21339402/"). The beginning of the file is shown below.

```
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------
 => Syslinux MBR (4.04-4.07) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda5 
                       and looks at sector 948389096 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub. It also embeds following 
                       components:
                       
                       modules
                       -------------------------------------------------------
                       fshelp ext2 part_msdos biosdisk
                       -------------------------------------------------------
                       -------------------------. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda4: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 2103522 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *        718,848   209,512,447   208,793,600   7 NTFS / exFAT / HPFS
/dev/sda2         209,512,448   210,434,047       921,600   7 NTFS / exFAT / HPFS
/dev/sda3         210,434,048   959,995,903   749,561,856   f W95 Extended (LBA)
/dev/sda5         210,454,528   834,146,303   623,691,776   c W95 FAT32 (LBA)
/dev/sda6         834,166,784   959,995,903   125,829,120  83 Linux
/dev/sda4         959,995,904   976,773,119    16,777,216  82 Linux swap / Solaris
```

The long story is as follows. I upgraded from Windows 7 to Windows 10 yesterday. The system is using legacy bios mode, not uefi, so this overwrote the mbr, causing the system to only boot into Windows. At this point, I had lost access to both my FAT32 data partition and my Linux and Linux swap partitions. I then used a program called Testdisk to find the missing partitions and add them to the MBR. When I restarted, the system found no operating systems. I then used the Ubuntu live cd to run boot-repair. It found the Linux OS and recreated the grub, but apparently it could no longer find Windows and the result is a grub that has no Windows option, which is my current situation.

---

### Post by oldfred on 2016-07-29
Windows 10 whether UEFI or BIOS has a fast start up or always on hibernation.
The Linux NTFS driver will not mount nor grub boot hibernated Windows.
So best to have a Windows repair flash drive.
You probably have to temporarily reinstall Windows boot loader to MBR, boot Windows and make repairs/turn off fast start up and then reinstall grub with Boot-Repair or manually. And since Windows likes to turn on fast start on updates or other changes be prepared to make sure it is off when shutting down or have procedure and tools to reset handy.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

      [/URL]
 f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 
    [       ]("https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System")
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive) 
    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by EricDallal on 2016-07-29
I don't have a Windows repair flash drive. I probably should have created it when I had access to Windows, but I never thought that the process of recovering Ubuntu would cost me Windows. Also, fast startup was not the issue. I had already seen that in other forums, disabled it, and re-ran boot-repair (which didn't fix the problem) before using Testdisk. How can I resinatll Windows boot loader to MBR without a Windows repair flash drive?

---

### Post by oldfred on 2016-07-29
Boot-Repair can install a Windows type boot loader to MBR - syslinux, if it sees Windows.

Or you can add manually install syslinux which is a full boot loader for BIOS systems, but only install the small part of syslinux that is in MBR. We do not want all of syslinux installed as that would further corrupt Windows.

       sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 
    
But it looks like you are missing /Boot/BCD in your Windows install. That would not have been deleted by any Linux changes. Did you originally have another Windows install or Boot partition? That would have had both bootmgr & BCD. You only show bootmgr in main Windows. Normal Windows 7 or later BIOS installs have a 100MB boot partition with bootmgr & BCD. The internal repair console was also normally in the Windows Boot partition.

Some Windows 3rd party repair tools can recreate the BCD.
       Repair BCD - not recommended for dual booting, just Windows repairs
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

---

### Post by EricDallal on 2016-07-29
It's possible I had a boot partition. This would seem to be sda2. I strongly suspect that I made a mistake when using Testdisk, which is what caused me to lose access to Windows, even if I was able to gain access to Ubuntu.

---

