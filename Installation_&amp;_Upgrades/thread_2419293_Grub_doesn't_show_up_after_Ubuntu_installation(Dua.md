---
title: "Grub doesn't show up after Ubuntu installation(Dual Boot)"
date: 2019-05-19
forum: Installation &amp; Upgrades
---

### Post by kukufleto33 on 2019-05-19
Basically, I installed Ubuntu(last version, 19.04 I think) to do a dual boot with windows 10, but after doing all the setup and restarting, my pc just boots into windows as it did before. 
                             Details 
I installed Ubuntu(19.04) on a USB, using BalenaEtcher, after leaving free space(23gb) on my ssd and 420gb on my Hdd. On the installation, I set the 23gb of ssd for /,  8 GB of the Hdd for swap and 412gb remaining for /home. After I finished setting up everything,  A screen popped up saying something like "Remove the media tool and restart". I proceeded to do so and the pc just booted into windows, the grub menu didn't even appear.

---

### Post by oldfred on 2019-05-19
What brand/model system?
What video card/chip?
New versions of Ubuntu now use a swap file. It will use a swap partition if one is found, but otherwise you do not need a swap partition.

Windows should be in UEFI boot mode if you purchased system. Did you then install Ubuntu in UEFI boot mode?]
From one time UEFI boot menu, can you boot the ubuntu entry? Some systems do not recognized it as first in boot order. Many that did not, will with UEFI update as vendors now are not quite as Windows only.
If Acer you have to set 'Trust'.

May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by kukufleto33 on 2019-05-20
Custom PC, I built it miself. MSI Motherboard, AMD 1600 processor, GT710(upgrading in 1-2 months). I don't know if Ubuntu is installed in UEFi mode, how can I check? I have dual booted other PCs, and this is the first time I have an issue.

---

### Post by yancek on 2019-05-20
One method to check if you have UEFI is to boot Ubuntu using the install media and from a terminal run the following command which will output partition info and indicate whether there is an EFI partition.

```
sudo parted -l
```

That's a lower case letter L in the command.  You might also review the Ubuntu documentation at the link below.  Also, go into your BIOS setup and look for UEFI settings and Boot Options.  These vary greatly with manufacturers.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-05-20
If custom built, you also then installed Windows.
Both Windows & Ubuntu install in the same boot mode as you boot install media UEFI or BIOS. And you really need to have both in same boot mode.
Windows also only boots in UEFI mode from gpt partitioned drives and only in BIOS boot mode from MBR(msdos) partitioned drives.

Microsoft has required vendors to install in UEFI/gpt mode since Windows 8 in 2012. But BIOS/MBR mode is available for those that really wanted the now 35 year old configuration. That was primarily large users who wanted newer systems to be same configuration as older systems.

---

### Post by kukufleto33 on 2019-05-20
After entering boot options and trying all the options, I was able to enter Ubuntu. I used Boot repair to do this summary:
 
    ```
Boot Info Script 8f991e4 + Boot-Repair extra info      [Boot-Info 25oct2017]

[FONT=book antiqua][I]
    ============================= Boot Info Summary: ===============================

     => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 
        222822704 of the same hard drive for core.img. core.img is at this 
        location and looks for (,gpt5)/boot/grub. It also embeds following 
        components:
        
        modules
        ---------------------------------------------------------------------------
        fshelp ext2 part_gpt biosdisk
        ---------------------------------------------------------------------------
     => Windows 7/8/2012 is installed in the MBR of /dev/sdb.

    sda1: __________________________________________________________________________
    
        File system:       ntfs
        Boot sector type:  Windows 8/2012: NTFS
        Boot sector info:  No errors found in the Boot Parameter Block.
        Operating System:  
        Boot files:        

    sda2: __________________________________________________________________________

        File system:       vfat
        Boot sector type:  Windows 8/2012: FAT32
        Boot sector info:  No errors found in the Boot Parameter Block.
        Operating System:  
        Boot files:        /EFI/Boot/bootx64.efi /EFI/Microsoft/Boot/bootmgfw.efi 
                           /EFI/Microsoft/Boot/bootmgr.efi 
                           /EFI/Microsoft/Boot/memtest.efi
    
    sda3: __________________________________________________________________________
    
        File system:       
        Boot sector type:  -
        Boot sector info: 
        Mounting failed:   mount: /mnt/BootInfo/sda3: unknown filesystem type ''.

    sda4: __________________________________________________________________________

        File system:       ntfs
        Boot sector type:  Windows 8/2012: NTFS
        Boot sector info:  No errors found in the Boot Parameter Block.
        Operating System:  
        Boot files:        /Windows/System32/winload.exe

    sda5: __________________________________________________________________________

        File system:       ext4
        Boot sector type:  -
        Boot sector info: 
        Operating System:  Ubuntu 19.04
        Boot files:        /boot/grub/grub.cfg /etc/fstab 
                           /boot/grub/i386-pc/core.img

    sdb1: __________________________________________________________________________

        File system:       
        Boot sector type:  -
        Boot sector info: 
        Mounting failed:   mount: /mnt/BootInfo/sda3: unknown filesystem type ''.
    mount: /mnt/BootInfo/sdb1: unknown filesystem type ''.

    sdb2: __________________________________________________________________________

        File system:       ntfs
        Boot sector type:  Windows 8/2012: NTFS
        Boot sector info:  No errors found in the Boot Parameter Block.
        Operating System:  
        Boot files:        

    sdb3: __________________________________________________________________________

        File system:       swap
        Boot sector type:  -
        Boot sector info: 

    sdb4: __________________________________________________________________________

        File system:       ext4
        Boot sector type:  -
        Boot sector info: 
        Operating System:  
        Boot files:        

    ============================ Drive/Partition Info: =============================

    Drive: sda _____________________________________________________________________
    Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectors
    Disk model: KINGSTON SA400S3
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes

    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

    /dev/sda1                   1   234,441,647   234,441,647  ee GPT


    GUID Partition Table detected.

    Partition  Attrs   Start Sector    End Sector  # of Sectors System[/I][/FONT]
```

---

### Post by kukufleto33 on 2019-05-20
I also tried sudo parted -l, this is the output:

```
[I]Model: ATA KINGSTON SA400S3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   628MB   104MB   fat32        EFI system partition          boot, esp
 3      628MB   645MB   16,8MB               Microsoft reserved partition  msftres
 4      645MB   96,4GB  95,7GB  ntfs         Basic data partition          msftdata
 5      96,4GB  120GB   23,7GB  ext4


Model: ATA ST1000DM010-2EP1 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      17,4kB  16,8MB  16,8MB                  Microsoft reserved partition  msftres
 2      16,8MB  580GB   580GB   ntfs            Basic data partition          msftdata
 3      580GB   588GB   8110MB  linux-swap(v1)
 4      588GB   1000GB  412GB   ext4[/I]
```

---

### Post by oldfred on 2019-05-20
Please use code tags. Easy to add in Forum's advanced editor with the # icon.
But with Boot-Repair better to just post link to pastebin site it gives. It includes the parted output also.

Without full Summary report, I cannot tell for sure, but it looks like you installed Windows in UEFI boot mode to gpt partitioned drive. But then installed Ubuntu in BIOS boot mode as you have grub in gpt's protective MBR. Grub does not correctly install in BIOS mode to gpt drive without a bios_grub partition. But you should have Ubuntu in UEFI boot mode.
If you boot live installer in UEFI mode, add Boot-Repair and in advanced options do the full uninstall and reinstall of grub in UEFI boot mode, then you will have both systems in UEFI boot mode. You could also just reinstall Ubuntu, but must boot in UEFI mode. See link in my signature for lots of details on UEFI.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

