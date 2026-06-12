---
title: "Ubuntu 14.04 UEFI boot partition and GRUB reinstall problem"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by erotavlas on 2014-05-13
Hi,

I have installed Ubuntu 14.04 just two weeks ago and now after an update I have a huge problem since I'm not able to recover my system. I tried many things also boot-repair disk [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and I have deleted both the boot partition by myself and the GRUB by boot-repair disk.
So now I have to reinstalled both. If I run gparted I get the following partitions (attached image).
The first partition in /dev/sda is the new UEFI boot partition. I have wrongly delete and reformatted it.
My /etc/fstab is this
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5ec28e7e-8b03-4497-924f-3ea2f2cf6713 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=CADB-73B5  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=8977bcd9-1adf-4cce-b8d7-c3fac5793ec0 none            swap    sw              0       0
UUID=b3559466-a574-4ace-b6e6-c53bc95eb4fc    /home     ext4     nodev,nosuid     0     2

```

I verified and change the UUID of the UEFI partition after that I have deleted it.
```

 sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="CADB-73B5" TYPE="vfat" // comment this is /dev/sda1
/dev/sda2: UUID="5ec28e7e-8b03-4497-924f-3ea2f2cf6713" TYPE="ext4"
/dev/sda3: UUID="8977bcd9-1adf-4cce-b8d7-c3fac5793ec0" TYPE="swap"
/dev/sda4: UUID="b3559466-a574-4ace-b6e6-c53bc95eb4fc" TYPE="ext4"
/dev/sdb1: LABEL="UUI" UUID="13ED-3E27" TYPE="vfat"  // comment this is USB devices

```

I tried with this
```

sudo efibootmgr -c -L Ubuntu -d /dev/sda1 


******************************************************
Warning! This MBR disk does not have a unique signature.
If this is not the first disk found by EFI, you may not be able
to boot from it without a unique signature.
Run efibootmgr with the -w flag to write a unique signature
to the disk.
******************************************************

BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0000,0001
Boot0001* UEFI: USB 2.0 Flash Disk 5.00
Boot0000* Ubuntu
ubuntu@ubuntu:~$ sudo efibootmgr -w
BootCurrent: 0001
Timeout: 0 seconds
BootOrder: 0000,0001
Boot0000* Ubuntu
Boot0001* UEFI: USB 2.0 Flash Disk 5.00

```
Now I think that I have the right UEFI boot partition in /dev/sda1 linked to /boot/efi. If I'm correct what I can do to reinstall the GRUB?

Thank you

---

### Post by erotavlas on 2014-05-13
I made some progresses.
```

sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2387EF34-CE79-4736-980C-9E7EB43305A5
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          585727   285.0 MiB   EF00  
   2          585728       195928063   93.1 GiB    8300  
   3       195928064       211552255   7.5 GiB     8200  
   4       211552256      1953523711   830.6 GiB   0700  


```
I mounted the system partition with Ubuntu inside the path /mnt/system. sda2 (Ubuntu system)
```


sudo mount /dev/sda2 /mnt/system


```
and the I repeated the same for the EFI boot partition in the path /mnt/system/boot/efi that is /boot/efi of Ubuntu system in sda2. sda1 (EFI folder)

```

sudo mount /dev/sda2 /mnt/system/boot/efi

```

I successfully installed one entry into the UEFI BIOS boot list with the following command and now I can choose the boot option inside the boot menu.
```

efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu

```
Now I have to install the GRUB. If I type 
```

[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
EFI boot on HDD

```
from terminal of live Ubuntu 14.04 64 bit I recognize that my system is in EFI mode.
Then, the strange thing is that the available GRUB list doesn't contain the efi version but only the pc version.
```

dpkg -l | grep grub
ii   grub-common                                            2.02~beta2-9                                        amd64        GRand  Unified Bootloader (common files)
ii   grub-gfxpayload-lists                                  0.6                                                 amd64        GRUB  gfxpayload blacklist
ii   grub-pc                                                2.02~beta2-9                                        amd64        GRand  Unified Bootloader, version 2 (PC/BIOS version)
ii   grub-pc-bin                                            2.02~beta2-9                                        amd64        GRand  Unified Bootloader, version 2 (PC/BIOS binaries)
ii   grub2-common                                           2.02~beta2-9                                        amd64        GRand  Unified Bootloader (common files for version 2)

```
In fact, the command to install the GRUB with efi target does not work since in /usr/lib/grub there is only i386-pc version.
```

 sudo  grub-install --boot-directory=/mnt/system/boot --bootloader-id=ubuntu  --target=x86_64-efi --efi-directory=/mnt/system/boot/efi --recheck  --debug /dev/sda

```
The error is this
```

grub-install: error: /usr/lib/grub/x86_64-efi/modinfo.sh doesn't exist. Please specify --target or --directory.

```
So how can I do? Is there a way to boot the pen drive in efi mode?

Thank you

---

### Post by oldfred on 2014-05-13
Did you install with 32 bit not 64 bit Ubuntu? Only 64 bit has the UEFI boot capability.

Post link to BootInfo report from Boot-Repair.
You should have grub-efi for UEFI boot and grub-pc for BIOS boot. 

See also link in my signature for more info.

---

### Post by erotavlas on 2014-05-13
> **oldfred said:**
> Did you install with 32 bit not 64 bit Ubuntu? Only 64 bit has the UEFI boot capability.

Post link to BootInfo report from Boot-Repair.
You should have grub-efi for UEFI boot and grub-pc for BIOS boot. 

See also link in my signature for more info.

My pen drive contains Ubuntu 14.04 64 bit and my broken system has the same version.

The command says that I'm in EFI mode
```

[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
EFI boot on HDD

```
while the command says that the partition of pen drive is MBR and not GPT
```

GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sdd: 7884800 sectors, 3.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 7767E483-D715-4A42-8F09-88301474149B
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 7884766
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         7884799   3.8 GiB     0700  Microsoft basic data

```
Note: I created the Ubuntu live pen by using windows 7 machine.
I took a look at your thread. I can say that I solved the problem of UEFI and I need only to reinstall GRUB. Please correct me if I'm wrong.
What can I do?

---

### Post by oldfred on 2014-05-13
That flash drive is MBR is normal. 
It is used for both UEFI on BIOS installs. It should have one FAT32 partition.
Why is it showing gpt partitions? Normally you do not use gpt on a flash drive installer. 
But if flash drive is used as a full install then gpt would be normal. And Windows does not always create gpt partitioning correctly nor convert from gpt to MBR correctly.

---

### Post by erotavlas on 2014-05-13
> **oldfred said:**
> That flash drive is MBR is normal. 
It is used for both UEFI on BIOS installs. It should have one FAT32 partition.
Why is it showing gpt partitions? Normally you do not use gpt on a flash drive installer. 
But if flash drive is used as a full install then gpt would be normal. And Windows does not always create gpt partitioning correctly nor convert from gpt to MBR correctly.

Ok, how can I recover the GRUB from the live pen with Ubuntu 64 bit now that I have recovered the efi boot inside the UEFI BIOS?
As I posted before, the command
```

dpkg -l | grep grub
ii   grub-common                                            2.02~beta2-9                                        amd64        GRand  Unified Bootloader (common files)
ii   grub-gfxpayload-lists                                  0.6                                                 amd64        GRUB  gfxpayload blacklist
ii   grub-pc                                                2.02~beta2-9                                        amd64        GRand  Unified Bootloader, version 2 (PC/BIOS version)
ii   grub-pc-bin                                            2.02~beta2-9                                        amd64        GRand  Unified Bootloader, version 2 (PC/BIOS binaries)
ii   grub2-common                                           2.02~beta2-9                                        amd64        GRand  Unified Bootloader (common files for version 2)
```
shows that I cannot install the GRUB in efi mode, in fact the command
```

sudo  grub-install --boot-directory=/mnt/system/boot --bootloader-id=ubuntu  --target=x86_64-efi --efi-directory=/mnt/system/boot/efi --recheck  --debug /dev/sda

```
fails with this error 
```

grub-install: error: /usr/lib/grub/x86_64-efi/modinfo.sh doesn't exist. Please specify --target or --directory.

```
while the command
```

sudo  grub-install --boot-directory=/mnt/system/boot --bootloader-id=ubuntu  --target=i386-pc--efi-directory=/mnt/system/boot/efi --recheck  --debug /dev/sda

```
gives back
```

Installing for i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
grub-install: error: will not proceed with blocklists.

```
A confirm that the live Ubuntu is 64 bit comes from
```

uname -a
Linux ubuntu 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

Any suggestions?

---

### Post by oldfred on 2014-05-13
You are installing a BIOS or grub-pc version. Did you boot flash drive in UEFI mode? It can be booted from UEFI/BIOS menu in either UEFI or BIOS boot mode. 
BIOS and UEFI are not really compatible. So each has its own version of grub and once you start to boot in one mode you cannot switch to the other mode. 
Boot-Repair can help you chroot into an install and update grub or reinstall in other other version.

Better to just use Boot-Repair.

---

### Post by erotavlas on 2014-05-13
> **oldfred said:**
> You are installing a BIOS or grub-pc version. Did you boot flash drive in UEFI mode? It can be booted from UEFI/BIOS menu in either UEFI or BIOS boot mode. 
BIOS and UEFI are not really compatible. So each has its own version of grub and once you start to boot in one mode you cannot switch to the other mode. 
Boot-Repair can help you chroot into an install and update grub or reinstall in other other version.

Better to just use Boot-Repair.

Boot-Repair does not work and it needs to use legacy mode or BIOS mode. I tried Boot-repair and it has deleted the old GRUB. I would like to reinstall an efi version of GRUB. How can I detect if the drive is in UEFI mode?
I think that the right command is this
```

[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
EFI boot on HDD

```
so I'm in UEFI mode.
Is it right?

---

### Post by erotavlas on 2014-05-13
I re-ran Boot-Repair. This is the message if I run "create boot info summry" 
```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 
    130315744 of the same hard drive for core.img. core.img is at this 
    location and looks in partition 112 for .
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04 LTS 
    Boot files:        /etc/fstab /boot/grub/i386-pc/core.img

sda3: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 30718 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       585,727       583,680 EFI System partition
/dev/sda2         585,728   195,928,063   195,342,336 Data partition (Linux)
/dev/sda3     195,928,064   211,552,255    15,624,192 Swap partition (Linux)
/dev/sda4     211,552,256 1,953,523,711 1,741,971,456 Data partition (Windows/Linux)

Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4037 MB, 4037017600 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7884800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *          2,048     7,884,799     7,882,752   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        CADB-73B5                              vfat       
/dev/sda2        5ec28e7e-8b03-4497-924f-3ea2f2cf6713   ext4       
/dev/sda3        8977bcd9-1adf-4cce-b8d7-c3fac5793ec0   swap       
/dev/sda4        b3559466-a574-4ace-b6e6-c53bc95eb4fc   ext4       
/dev/sdd1        13ED-3E27                              vfat       UUI

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev             /mnt/system/dev          none       (rw,bind)
/dev             /mnt/system/dev          none       (rw,bind)
/dev             /mnt/system/dev          none       (rw,bind)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /mnt/system/boot/efi     vfat       (rw)
/dev/sda2        /mnt/system              ext4       (rw)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5ec28e7e-8b03-4497-924f-3ea2f2cf6713 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=CADB-73B5  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=8977bcd9-1adf-4cce-b8d7-c3fac5793ec0 none            swap    sw              0       0
UUID=b3559466-a574-4ace-b6e6-c53bc95eb4fc    /home     ext4     nodev,nosuid     0     2
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=========================== sdd1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "OEM install (for manufacturers)" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper only-ubiquity quiet splash oem-config/enable=true --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz.efi  cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-OSfuST79/Tmp_Log: No such file or directory
cat: /tmp/BootInfo-OSfuST79/Tmp_Log: No such file or directory
File descriptor 9 (/proc/9080/mounts) leaked on lvscan invocation. Parent PID 16733: bash
File descriptor 63 (pipe:[79171]) leaked on lvscan invocation. Parent PID 16733: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-05-13__15h58 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session (Ubuntu 14.04 LTS, trusty, Ubuntu, x86_64)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed cdrom-detect/try-usb=true noprompt floppy.allowed_drive_mask=0 ignore_uuid boot=casper quiet splash --

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== os-prober:
/dev/sda2:Ubuntu 14.04 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="CADB-73B5" TYPE="vfat"
/dev/sda2: UUID="5ec28e7e-8b03-4497-924f-3ea2f2cf6713" TYPE="ext4"
/dev/sda3: UUID="8977bcd9-1adf-4cce-b8d7-c3fac5793ec0" TYPE="swap"
/dev/sda4: UUID="b3559466-a574-4ace-b6e6-c53bc95eb4fc" TYPE="ext4"
/dev/sdd1: LABEL="UUI" UUID="13ED-3E27" TYPE="vfat"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.

/boot/efi detected in the fstab of sda2: UUID=CADB-73B5   (sda1)
=================== UEFI/Legacy mode:
Unusual EFI: Please report this message to boot.repair@gmail.com
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot disabled. (maybe sec-boot, Please report this message to boot.repair@gmail.com)


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/system/boot/efi.
sda2    : sda,    not-sepboot,    grubenv-ok    nogrub,    no-docgrub,    no-update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-has-goodEFI,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    nogrubinstall,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    /mnt/system.
sda4    : sda,    maybesepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    farbios,    /mnt/boot-sav/sda4.

sda    : GPT,    no-BIOS_boot,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA HGST HTS541010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  300MB   299MB   fat32                 boot
2      300MB   100GB   100GB   ext4
3      100GB   108GB   8000MB  linux-swap(v1)
4      108GB   1000GB  892GB   ext4                  msftdata


Model: USB 2.0 Flash Disk (scsi)
Disk /dev/sdd: 4037MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      1049kB  4037MB  4036MB  primary  fat32        boot, lba

=================== parted -lm:

BYT;
/dev/sda:1000GB:scsi:512:4096:gpt:ATA HGST HTS541010A9;
1:1049kB:300MB:299MB:fat32::boot;
2:300MB:100GB:100GB:ext4::;
3:100GB:108GB:8000MB:linux-swap(v1)::;
4:108GB:1000GB:892GB:ext4::msftdata;

BYT;
/dev/sdd:4037MB:scsi:512:512:msdos:USB 2.0 Flash Disk;
1:1049kB:4037MB:4036MB:fat32::boot, lba;


=================== mount:
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/sdd1 on /cdrom type vfat (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/999/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=ubuntu)
/dev/sda2 on /mnt/system type ext4 (rw)
/dev/sda1 on /mnt/system/boot/efi type vfat (rw)
/dev on /mnt/system/dev type none (rw,bind)
/proc on /mnt/system/proc type none (rw,bind)
/sys on /mnt/system/sys type none (rw,bind)
/dev on /mnt/system/dev type none (rw,bind)
/proc on /mnt/system/proc type none (rw,bind)
/sys on /mnt/system/sys type none (rw,bind)
/bin on /mnt/system/bin type none (rw,bind)
/bin on /mnt/system/bin type none (rw,bind)
/dev on /mnt/system/dev type none (rw,bind)
/proc on /mnt/system/proc type none (rw,bind)
/sys on /mnt/system/sys type none (rw,bind)
/dev/sda4 on /mnt/boot-sav/sda4 type ext4 (rw)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 sda4 size slaves stat subsystem trace uevent
/sys/block/sdd (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 size slaves stat subsystem trace uevent
/sys/block/sr0 (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus cdrom char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd full fuse hidraw0 hidraw1 hidraw2 hpet input kmsg kvm log mapper mcelog mei mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sda4 sdd sdd1 sg0 sg1 sg4 shm snapshot snd sr0 stderr stdin stdout uhid uinput urandom v4l vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control

=================== hexdump -n512 -C /dev/sda1
00000000  eb 58 90 6d 6b 64 6f 73  66 73 00 00 02 08 20 00  |.X.mkdosfs.... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 e8 08 00 40 02 00 00  00 00 00 00 02 00 00 00  |....@...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 b5 73 db ca 20  20 20 20 20 20 20 20 20  |..).s..         |
00000050  20 20 46 41 54 33 32 20  20 20 0e 1f be 77 7c ac  |  FAT32   ...w|.|
00000060  22 c0 74 0b 56 b4 0e bb  07 00 cd 10 5e eb f0 32  |".t.V.......^..2|
00000070  e4 cd 16 cd 19 eb fe 54  68 69 73 20 69 73 20 6e  |.......This is n|
00000080  6f 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 64 69  |ot a bootable di|
00000090  73 6b 2e 20 20 50 6c 65  61 73 65 20 69 6e 73 65  |sk.  Please inse|
000000a0  72 74 20 61 20 62 6f 6f  74 61 62 6c 65 20 66 6c  |rt a bootable fl|
000000b0  6f 70 70 79 20 61 6e 64  0d 0a 70 72 65 73 73 20  |oppy and..press |
000000c0  61 6e 79 20 6b 65 79 20  74 6f 20 74 72 79 20 61  |any key to try a|
000000d0  67 61 69 6e 20 2e 2e 2e  20 0d 0a 00 00 00 00 00  |gain ... .......|
000000e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


=================== df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  3.7G  132M  3.6G   4% /
/dev           none       3.7G   12K  3.7G   1% /mnt/system/dev
tmpfs          tmpfs      744M  1.2M  742M   1% /run
/dev/sdd1      vfat       3.8G  964M  2.9G  26% /cdrom
/dev/loop0     squashfs   923M  923M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      3.7G  2.4M  3.7G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      3.7G   80K  3.7G   1% /run/shm
none           tmpfs      100M   84K  100M   1% /run/user
/dev/sda2      ext4        92G   17G   71G  19% /mnt/system
/dev/sda1      vfat       285M  4.9M  280M   2% /mnt/system/boot/efi
/dev/sda4      ext4       818G  458G  319G  59% /mnt/boot-sav/sda4

=================== fdisk -l:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x337aeafe

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdd: 4037 MB, 4037017600 bytes
255 heads, 63 sectors/track, 490 cylinders, total 7884800 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00021cd2

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048     7884799     3941376    c  W95 FAT32 (LBA)


(debug) reinstall grub2 place-in-MBR no-BIOS_boot (sda2)
=================== Repair blockers
GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.
=================== Advice displayed in case of recommended repair
The boot of your PC is in EFI mode, but no EFI partition was detected. You may want to retry after creating a EFI partition (FAT32, 100MB~250MB, start of the disk, boot flag).
Do you want to continue?

=================== Default settings
Recommended-Repair
This setting would purge (in order to fix packages fix executable) and reinstall the grub2 of sda2 into the MBR of sda.
Additional repair would be performed: unhide-bootmenu-10s

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.


```

while this is the message if I run recommended repair

```

GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

```

It seems that I need necessarily a BIOS-Boot partition. Or I'm missing something...

---

### Post by oldfred on 2014-05-13
You have grub in the MBR, but with gpt partitioning you have to have a bios_grub partition for grub to correctly install in BIOS boot mode.
For whatever reason Boot-Repair does not see your efi partition. It looks correct as a FAT32 partition with the boot flag and partition table says it is the efi partition.
Perhaps the issue in the partition boot sector on start of partition is an issue?
Try this:
       sudo /sbin/fsck.vfat -V <the fat32 device>
or:
sudo fsck -t vfat /dev/sda1

If that does not work, just use gparted to delete the sda1 partition. If you do have any data in it back that up first. 
And then recreate a new FAT32 partition with the boot flag using gparted. 
Or use gdisk and give it code ef00. It is in repository.
sudo apt-get install gdisk
      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

    
Then see if Boot-Repair sees efi partition to let you install grub-efi for UEFI boot.

---

### Post by erotavlas on 2014-05-13
> **oldfred said:**
> You have grub in the MBR, but with gpt partitioning you 
have to have a bios_grub partition for grub to correctly install in BIOS boot 
mode.
For whatever reason Boot-Repair does not see your efi partition. It looks 
correct as a FAT32 partition with the boot flag and partition table says it is 
the efi partition.
Perhaps the issue in the partition boot sector on start of partition is an 
issue?
Try this:
sudo /sbin/fsck.vfat -V <the fat32 device>
or:
sudo fsck -t vfat /dev/sda1

If that does not work, just use gparted to delete the sda1 partition. If you 
do have any data in it back that up first.
And then recreate a new FAT32 partition with the boot flag using gparted.
Or use gdisk and give it code ef00. It is in repository.
sudo apt-get install gdisk

GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)


Then see if Boot-Repair sees efi partition to let you install grub-efi for 
UEFI boot.

The command sudo fsck -t vfat /dev/sda1 gives
```

fsck from util-linux 2.20.1
fsck.fat 3.0.26 (2014-03-07)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be 
corrupt.
1) Remove dirty bit
2) No action
? 1
Leaving filesystem unchanged.
/dev/sda1: 282 files, 1248/72812 clusters

```
Then, I tried with gparted and I made a fat32 partition with boot flag. But Boot-repairs gives the same answers as before.
Finally, with sudo gdisk -l /dev/sda
```

GPT fdisk (gdisk) version 0.8.8
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2387EF34-CE79-4736-980C-9E7EB43305A5
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          585727   285.0 MiB   EF00  
   2          585728       195928063   93.1 GiB    8300  
   3       195928064       211552255   7.5 GiB     8200  
   4       211552256      1953523711   830.6 GiB   0700 

Command (? for help): p
Disk /dev/sda: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2387EF34-CE79-4736-980C-9E7EB43305A5
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 3437 sectors (1.7 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          585727   285.0 MiB   EF00  EFI System
   2          585728       195928063   93.1 GiB    8300  
   3       195928064       211552255   7.5 GiB     8200  
   4       211552256      1953523711   830.6 GiB   0700  

Command (? for help): v

No problems found. 3437 free sectors (1.7 MiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

Command (? for help): w

Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
OK; writing new GUID partition table (GPT) to /dev/sda.
Warning: The kernel is still using the old partition table.
The new table will be used at the next reboot.
The operation has completed successfully.


``` 

Unfortunately the boot-repair behavior is the same as before with this output message
[http://paste.ubuntu.com/7459264/](http://paste.ubuntu.com/7459264/)
I tried also with another Ubuntu live with integrated Boot-repair [https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix), but the result is the same [http://paste.ubuntu.com/7459295/](http://paste.ubuntu.com/7459295/)
I hope to avoid to reformat :(

---

### Post by oldfred on 2014-05-13
The ef00 in gdisk should make the partition be the efi partition. 
Still do not know why installing of grub does not see the efi partition. 
The insistence of a bios_grub is only for BIOS boot. 
You now show a efi file entry in fstab which usually is from the grub-efi installing.

Can you copy files into the efi partition, just to verify it is writeable?

copy this from live installer into your efi partition.
/EFI/BOOT/grubx64.efi

That by itself will not boot Ubuntu.

---

### Post by ubfan1 on 2014-05-13
When you remade the EFI paritiion, the UUID changed, but the /etc/fstab file still has the old UUID.  That needs to be updated to 
441D-E8A8
You are booting in  legacy mode, probably because there apparently no grub boot files at all in the EFI (boot-repair will
list any found early in the report at the partition examination.  Check your BIOS/UEFI settings to ensure you are in the
UEFI mode and not in CSM or Legacy.

---

### Post by erotavlas on 2014-05-14
> **ubfan1 said:**
> When you remade the EFI paritiion, the UUID changed, but the /etc/fstab file still has the old UUID.  That needs to be updated to 
441D-E8A8
You are booting in  legacy mode, probably because there apparently no grub boot files at all in the EFI (boot-repair will
list any found early in the report at the partition examination.  Check your BIOS/UEFI settings to ensure you are in the
UEFI mode and not in CSM or Legacy.

You are right I forget to change UUID after that I used gdisk or gparted.
How can I boot in efi mode?
I have found this tutorial [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) that explains how to boot in efi mode and it seems that my live Ubuntu 14.04 is booted in efi mode.
```

[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

```
and the result is EFI boot on HDD. Moreover, the first screen is with menu list instead of graphical screen with disk and sticky man.

Now Boot-repair says as before
```

GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

```
 and the report is [http://paste.ubuntu.com/7461702/](http://paste.ubuntu.com/7461702/)

So seems that there is no solution to my problem...

---

### Post by erotavlas on 2014-05-14
> **oldfred said:**
> The ef00 in gdisk should make the partition be the efi partition. 
Still do not know why installing of grub does not see the efi partition. 
The insistence of a bios_grub is only for BIOS boot. 
You now show a efi file entry in fstab which usually is from the grub-efi installing.

Can you copy files into the efi partition, just to verify it is writeable?

copy this from live installer into your efi partition.
/EFI/BOOT/grubx64.efi

That by itself will not boot Ubuntu.

Where can I find /EFI/BOOT/grubx64.efi? 
I mounted /dev/sda2 (my Ubuntu system) in mnt/system/ and I mounted /dev/sda1 in /mnt/system/boot/efi 

I can make touch file inside the /mnt/system/boot/efi as sudo user. 
```

sudo touch /mnt/system/boot/efi/file

```

I tried to run boot-repair as sudo user without success.

---

### Post by oldfred on 2014-05-14
You can try to copy /boot/efi from your USB installer.
Then change the grub.cfg in that or create a /boot/ubuntu folder to just call the actual grub.cfg in your install.

 configfile (hd0,gpt2)/boot/grub/grub.cfg

---

### Post by erotavlas on 2014-05-14
> **oldfred said:**
> You can try to copy /boot/efi from your USB installer.
Then change the grub.cfg in that or create a /boot/ubuntu folder to just call the actual grub.cfg in your install.

 configfile (hd0,gpt2)/boot/grub/grub.cfg

My USB installer does not contain /boot/efi...

---

### Post by oldfred on 2014-05-14
Then you must have a 32bit installer and that is the entire issue.
Only the 64 bit has the UEFI install capability.

---

### Post by erotavlas on 2014-05-14
> **oldfred said:**
> Then you must have a 32bit installer and that is the entire issue.
Only the 64 bit has the UEFI install capability.

Ok. Probably I have not explained well the procedure. On first of May I installed Ubuntu 14.04 64 bit on my notebook. Two days ago I broken my system. Then, I download the ISO Ubuntu 14.04 64 bit and I made a USB pen with the guide [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows). So I think that the live Ubuntu is 64 bit system. If I type uname -a it says to me that I'm on 64 bit and moreover it says that it is UEFI system.

```

uname -a

```
result x86_64
```

[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

```
result EFI boot on HDD

If I disable from BIOS UEFI mode I receive Legacy boot on HDD.

Where is the problem? I cannot understand...

---

### Post by Luke M on 2014-05-14
> **erotavlas said:**
> My USB installer does not contain /boot/efi...

It's efi/boot, not boot/efi. :-)

---

### Post by oldfred on 2014-05-14
Sorry, Luke M is correct. I reversed the /boot and /efi.
Glad others do check. :)

If you have the amd64 bit version, then it is the 64 bit version. And will have the capability to boot with UEFI so must have efi files.

---

### Post by Luke M on 2014-05-14
By the way, when you run the ubuntu live CD, the grub-pc package (for BIOS) is installed, not grub-efi-amd64. That's why the grub-install command failed. Try:

sudo apt-get install grub-efi-amd64

---

### Post by erotavlas on 2014-05-16
> **Luke M said:**
> By the way, when you run the ubuntu live CD, the grub-pc package (for BIOS) is installed, not grub-efi-amd64. That's why the grub-install command failed. Try:

sudo apt-get install grub-efi-amd64

Thank you Luke M, you have stopped my nightmare :) The right command it is sudo apt-get install grub-efi-amd64

---

### Post by erotavlas on 2014-05-16
This is my final post with a summary of my problem and the corresponding solution in order to avoid to waste your time on resolving it.

The first thing to do is to check if you boot your live Ubuntu system in UEFI mode
```

[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

```
If the answer is "EFI boot on HDD" then you can proceed otherwise you have to modify your boot setting into the BIOS [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Then you have to: 1) restore your efi partition and 2) reinstall the GRUB
1) To restore your efi partition 
First install efi boot manager
```

sudo apt-get install efibootmgr

```
check that your partition is GPT and that you have an efi partition as first partition of your drive [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
```

sudo gdisk -l /dev/sda

```
Then you have to mount your Ubuntu system partition and efi partition. In my case the Ubuntu is located in /dev/sda2
```

sudo mkdir -p /mnt/system
sudo mount /dev/sda2 /mnt/system

```
while the efi partition is located in /dev/sda1
```

sudo mount /dev/sda1 /mnt/system/boot/efi

```

Finally you have to install one entry into the UEFI BIOS boot list with the following command
```

efibootmgr -c -d /dev/sda -p 1 -w -L ubuntu

```

Now you have installed the efi entry for the Ubuntu system.

2) To install the GRUB you have two possibilities. First, for both you have to install this
```

sudo apt-get install grub-efi-amd64

```
and now your live Ubuntu is able to install UEFI GRUB.

The first possibility is to manually install the GRUB with these following commands
```

sudo  grub-install --boot-directory=/mnt/system/boot --bootloader-id=ubuntu  --target=x86_64-efi --efi-directory=/mnt/system/boot/efi --recheck  --debug /dev/sda

```
and
```

sudo grub-mkconfig -o /mnt/system/boot/efi/EFI/GRUB/grub.cfg

```

while the second possibility is a guided procedure using Boot-repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo sh -c "sed -i 's/trusty/saucy/g' /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list"
sudo apt-get update
sudo apt-get install -y boot-repair && (boot-repair &)

```
Now you can launch Boot-Repair and follow the instructions at video. At certain point the Boot-Repair ask to you to launch these commands from terminal
```

sudo chroot "/mnt/system" dpkg --configure -a
sudo chroot "/mnt/system" apt-get install -fy
sudo chroot "/mnt/system" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic

```

At the end you can boot again your Ubuntu system :)

---

