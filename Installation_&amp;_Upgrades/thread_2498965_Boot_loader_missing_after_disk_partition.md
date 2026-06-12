---
title: "Boot loader missing after disk partition"
date: 2024-07-05
forum: Installation &amp; Upgrades
---

### Post by paolo345 on 2024-07-05
Hello, I wanted to create a disk partition for a VM with sudo fdisk but accidentally used EFI partition type and i think it became bootable and deleted some other disk partitions (some error messages poppep up that said it failed to delete some other disk partitions).
After restarting it loaded into grub and /boot is missing.
Tried using Boot repair iso but it just gave me the black screen with flashing underscore.
Loaded into ubuntu with an usb and got Boot repair from terminal but it's missing the Recommended Repair option.
Here's the summary file, any help is appreciated.

                       boot-repair-4ppa2075                                              [20240705_2039]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v2.00) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (hd0,msdos1)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    biosdisk fshelp fat exfat ext2 ntfs ntfscomp part_msdos
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       1048572 sectors.. But according to the info from the 
                       partition table, it has 209715199 sectors.
    Operating System:  
    Boot files:        /efi/BOOT/fbia32.efi /efi/BOOT/fbx64.efi 
                       /efi/BOOT/mmx64.efi /efi/fedora/gcdia32.efi 
                       /efi/fedora/gcdx64.efi /efi/fedora/grubia32.efi 
                       /efi/fedora/grubx64.efi /efi/fedora/mmia32.efi 
                       /efi/fedora/mmx64.efi /efi/fedora/shim.efi 
                       /efi/fedora/shimia32.efi /efi/fedora/shimx64.efi 
                       /efi/ubuntu/grubx64.efi /efi/ubuntu/mmx64.efi 
                       /efi/ubuntu/shimx64.efi /efi/fedora/grub.cfg 
                       /efi/ubuntu/grub.cfg

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  MSWIN4.1: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /efi/boot/bootx64.efi 
                       /efi/boot/grubx64.efi /efi/boot/mmx64.efi


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: Navi 23 [Radeon RX 6600/6600 XT/6600M] from Advanced Micro Devices, Inc. [AMD/ATI]
Live-session OS is Ubuntu 64-bit (Ubuntu 24.04 LTS, noble, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 5.17(5.17) from American Megatrends International, LLC.
The firmware seems EFI-compatible, but this live-session is in Legacy/BIOS/CSM mode (not in EFI mode).


ab547d1341a481f92da0bb0a2228ce98   sda1/BOOT/fbia32.efi
359777f2165aa64c53e45fb416017e4e   sda1/BOOT/fbx64.efi
a660182adef313615746a665966d2ccc   sda1/BOOT/mmx64.efi
15ac98f26a04ef572fa9ffdb3c19595e   sda1/fedora/gcdia32.efi
6a365f13820e67fb0edf7f170d97d2c6   sda1/fedora/gcdx64.efi
0a23c424eedac1039fc6cac5c7e718b5   sda1/fedora/grubia32.efi
f65c7e48c5c259ec5ad80bb8978a3c0b   sda1/fedora/grubx64.efi
c1a35c46b1d7625629e66aa286f46a72   sda1/fedora/mmia32.efi
9d18a9032cb340c1c80eed077e7b684a   sda1/fedora/mmx64.efi
1f76deb94e513a018ca76c3854804f43   sda1/fedora/shim.efi
ea9f4f7a2beffc41e4ed615659af8e8a   sda1/fedora/shimia32.efi
1f76deb94e513a018ca76c3854804f43   sda1/fedora/shimx64.efi
a1da253696a304dce6b4668b70151c0e   sda1/ubuntu/grubx64.efi
a660182adef313615746a665966d2ccc   sda1/ubuntu/mmx64.efi
64349b3622c65f495a99dbf6102496e3   sda1/ubuntu/shimx64.efi
ea9f4f7a2beffc41e4ed615659af8e8a   sda1/BOOT/BOOTIA32.efi
1f76deb94e513a018ca76c3854804f43   sda1/BOOT/BOOTX64.efi

============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 953.87 GiB, 1024209543168 bytes, 2000409264 sectors
Disk identifier: 010FFB47-61C7-46F7-9850-73336DBAA84B
     Start       End   Sectors  Size Type
sda1   2048 209717247 209715200  100G EFI System
Disk sdb: 58.59 GiB, 62914560000 bytes, 122880000 sectors
Disk identifier: 0x01625f9a
     Boot Start       End   Sectors  Size Id Type
sdb1  *     2048 122879935 122877888 58.6G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:1024GB:scsi:512:512:gpt:ATA P3-1TB:;
1:1049kB:107GB:107GB:fat32::boot, esp;
sdb:62.9GB:scsi:512:512:msdos:VendorCo ProductCode:;
1:1049kB:62.9GB:62.9GB:fat32::boot, lba;

Free space >10MiB: ______________________________________________________________

sda: 102401MiB:976762MiB:874361MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL       PARTLABEL
sda                                                                                                   
&#9492;&#9472;sda1 vfat     0D25-C0E6                            b71dbb4d-794d-480b-8ed8-1bbf99973de0             
sdb                                                                                                   
&#9492;&#9472;sdb1 vfat     1D1F-2C56                            01625f9a-01                          UBUNTU 24_0 

Mount points (filtered): _______________________________________________________

                           Avail Use% Mounted on
/dev/sda1                 486.9M   5% /mnt/boot-sav/sda1
/dev/sdb1                  52.9G  10% /cdrom

Mount options (filtered): ______________________________________________________

/dev/sda1                 vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sdb1                 vfat            ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

===================== sda1/efi/fedora/grub.cfg (filtered) ======================

search --no-floppy --fs-uuid --set=dev 6991c9d7-1c72-4a09-8f5d-958990d6e663
set prefix=($dev)/grub2
export $prefix
configfile $prefix/grub.cfg

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 258379e7-4ec1-4e04-9f33-5c63cacbdab3 root hd0,gpt2 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Try or Install Ubuntu
Ubuntu (safe graphics)
Boot from next volume
UEFI Firmware Settings
Test memory

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.

---

### Post by tea for one on 2024-07-05
```
================================ 0 OS detected =================================
```
You only have sda1 ESP visible.
> accidentally used EFI partition type and i think it became bootable and [COLOR="#0000FF"]deleted [/COLOR]some other disk partitions
It certainly seems that this is what happened.
The way forward - Install Ubuntu 24.04 and restore your data backup.

---

