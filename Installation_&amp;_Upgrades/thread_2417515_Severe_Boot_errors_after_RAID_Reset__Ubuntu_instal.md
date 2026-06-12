---
title: "Severe Boot errors after RAID Reset / Ubuntu install (on old Win7 dual boot)"
date: 2019-04-23
forum: Installation &amp; Upgrades
---

### Post by bgzurich on 2019-04-23
Summary: 
----------
I have carried out a single-boot, Ubuntu 16.04 LTS 64  full install (deleted  everything while installing) but I can't boot this PC any more. 
Also tried bootrepair Live USB disk, but no success.   PC starts up, presents grub menu to choose from Ubuntu or Advanced Options, but if I chose to start ubuntu, it hangs and produces the following error:

```

[          0.921282] Couldn't get size:  0x800000000000000000e
[          0.921295] MODSIGN: Couldn't get UEFI db list 
[          0.923056] Couldn't get size:  0x800000000000000000e

Busybox v1.22.1 (Ujbunt +:+.22.0-19ubuntu2) built-inshell (ash)
Enter help for a list of built-in commands

(initramfs) Unable to find a medium containing a live file system


```
---------


Here is the Summary Info from Bootrepair:
(full dump is here:   [http://paste.ubuntu.com/p/4mxWjKmxYr/](http://paste.ubuntu.com/p/4mxWjKmxYr/)  )

```


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.
 => Windows 7/8/2012 is installed in the MBR of /dev/sde.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdf.

sda1: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg /grub/i386-pc/core.img

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/ubuntu/fwupx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                       /EFI/ubuntu/shimx64.efi

sdc2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sdc3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 2048.
    Operating System:  
    Boot files:        /EFI/ubuntu/grub.cfg /EFI/ubuntu/fwupx64.efi 
                       /EFI/ubuntu/grubx64.efi /EFI/ubuntu/mmx64.efi 
                       /EFI/ubuntu/shimx64.efi

sdd2: __________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /grub/grub.cfg

sdd3: __________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info: 

sde1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdf1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 29418 of /dev/sdf1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

ubuntu-vg-root: ________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/LVM/ubuntu-vg-root: unknown filesystem type ''.

ubuntu-vg-swap_1: ______________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/LVM/ubuntu-vg-root: unknown filesystem type ''.
mount: /mnt/BootInfo/LVM/ubuntu-vg-swap_1: unknown filesystem type ''.

sdb: ___________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: /mnt/BootInfo/LVM/ubuntu-vg-root: unknown filesystem type ''.
mount: /mnt/BootInfo/LVM/ubuntu-vg-swap_1: unknown filesystem type ''.
mount: /mnt/BootInfo/FD/sdb: unknown filesystem type ''.



```

_______________________________________________________________________________________

Background Info:

System Config:
--------------
3.80 gigahertz Intel Core i5-7600K,  256 kilobyte primary memory cache
1024 kilobyte secondary memory cache, 6144 kilobyte tertiary memory cache
64-bit ready, Multi-core (4 total) Not hyper-threaded
4x 120 GB SSD Disks   (=> grouped into 2  RAID1 with two 120 Disk each)
1x  1000 GB HDD (Backup Disk)
Intel(R) Desktop/Workstation/Server Express Chipset SATA RAID Controller
Boot Mode: Legacy BIOS in UEFI ([Secure Boot]("http://www.belarc.com/secureboot.html") not supported)                 



History of current Problems:
----------------------------
This used to be a RAID0  EvoRaid SMART with a dual boot 32bit / 64bit  Win7 Pro.  I believe there was a RAID stripe setup in the beginning,  with a couple of partitions over the 4 SSD disks.

1) This PC wasn't online for more than a year, I had subsequently  problems with recent flurry of catch-up Windows updates and the system  became unstable. I decided to convert this PC into a Linux-only machine  that I intend to use as operating system, and use VMWare workstation on  top of it in the future.  Data and Application preservation are of NO  CONCERN here, just a clean, simple and most stable Ubuntu-only install.

2) When attempting to install Ubuntu (tried different variations during  install process - delete everything, use LVM Option, Use Other Options  => Create New Partition Table, or attempted to use Ubuntu Live USB  Boot Repair) - nothing of this worked in the original configuration  (still on old Win7 Dual Boot Raid stripe setup) because the Ubuntu  install was never able to create / write into a proper boot sector, or  the Ubuntu Install already hanged somewhere in between.

3) I then chose (recklessly?) to delete the old RAID setup and chose the  following configuration (which should have erased everything).


CURRENT STATUS:
---------------------

1) I have set up (via Intel Raid Tool before startup) a new RAID, combining the 4  120 GB disk into 2 Mirrored disk RAID1 setup to make it as simple and straightforward as possible.


2) started Ubuntu Install from USB stick. 
I chose to:  install & update everything, delete everything, ticked LVM option, and chose GPT file system.  

This was the first time over this journey when the full install ran through smoothly and in the end the installer told me to restart the system to use it.

3) I restarted the system, and then it goes into a black screen with a blinking cursor upper left corner.

4) Tried Ubuntu Boot Repair via USB, but this spits out the error codes mentioned above in the introduction and then hangs.


I suspect there might only a small part be missing

I am just not too familiar with that part of the task.
Any help would be highly appreciated.

---

### Post by wildmanne39 on 2019-04-23
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Please do not create new threads on the same topic instead just use the report button and ask us to move the thread for you instead of removing it from public view.

---

### Post by wildmanne39 on 2019-04-23
I have added the code tags again please leave them this time.

Thanks

---

### Post by bgzurich on 2019-04-23
Thanks for the hint, sorry, I'm still new,  but why should we use CODE here? 

This is not code, it is informational output from the Bootinfo app and -  
the first and last paragraph that you included with this Code bracket into the system info is not from the Bootinfo app anyways, so this grouping makes no sense hierarchically, imho.

---

### Post by wildmanne39 on 2019-04-23
The script is run in the terminal hence we call any info created from the terminal code and it is easier to read in code tags, I may have included something that the script did not produce, it happens.

---

