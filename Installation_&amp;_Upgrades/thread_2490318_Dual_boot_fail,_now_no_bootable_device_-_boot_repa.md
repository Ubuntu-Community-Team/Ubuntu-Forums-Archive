---
title: "Dual boot fail, now no bootable device - boot repair output below"
date: 2023-08-30
forum: Installation &amp; Upgrades
---

### Post by rwps on 2023-08-30
Any help appreciated. Win10 Pro, attempted dual boot install of latest Ubuntu
ubuntu-22.04.3-desktop-amd64
Rufus complained it didn't have the right Grub & that it would download the required one
After install had Grub rescue prompt
And on restart no bootable device
Attempt a new install with full erase, and run into errors to do with Boot
Tried Boot repair utility, and Boot repair output:

```
boot-repair-4ppa203                                              [20230830_0621]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/10/11/2012: NTFS
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       102399 sectors, but according to the info from fdisk, 
                       it has 1048575 sectors.
    Operating System:  
    Boot files:        /bootmgr

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.03
    Boot sector info:  Syslinux looks at sector 8216 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /ldlinux.sys


================================ 0 OS detected =================================


================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: HD Graphics 630 from Intel Corporation
Live-session OS is Ubuntu 64-bit (Boot-Repair-Disk 64bit 20200604, bionic, x86_64)

===================================== UEFI =====================================

BIOS/UEFI firmware: 1.25.0 from Dell Inc.
The firmware is EFI-compatible, and is set in EFI-mode for this live-session.
SecureBoot disabled (confirmed by mokutil).
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001
Boot0001* UEFI:  PMAP    PciRoot(0x0)/Pci(0x14,0x0)/USB(3,0)/HD(1,MBR,0x64c751f,0x800,0x3d3c00)..BO
Boot0007  Windows Boot Manager    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...l................


============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    farbios

Partitions info (2/3): _________________________________________________________

sda1    : is---ESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : maybesepboot,    no-kernel,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Disk identifier: DAB38F83-0332-4F0A-8DEF-5EA4C2CE2AC1
        Start       End   Sectors   Size Type
sda1     2048   1050623   1048576   512M EFI System
sda2  1050624 250068991 249018368 118.8G Linux filesystem
Disk sdb: 1.9 GiB, 2055733248 bytes, 4015104 sectors
Disk identifier: 0x064c751f
      Boot Start     End Sectors  Size Id Type
sdb1  *     2048 4015103 4013056  1.9G  c W95 FAT32 (LBA)
Disk zram0: 980.7 MiB, 1028288512 bytes, 251047 sectors
Disk zram1: 980.7 MiB, 1028288512 bytes, 251047 sectors
Disk zram2: 980.7 MiB, 1028288512 bytes, 251047 sectors
Disk zram3: 980.7 MiB, 1028288512 bytes, 251047 sectors

parted -lm (filtered): _________________________________________________________

sda:128GB:scsi:512:4096:gpt:ATA SK hynix SC308 S:;
1:1049kB:538MB:537MB:ntfs:EFI System Partition:boot, esp;
2:538MB:128GB:127GB:ext4::;
sdb:2056MB:scsi:512:512:msdos: :;
1:1049kB:2056MB:2055MB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL           PARTLABEL
sda                                                                                                       
&#9500;&#9472;sda1 ntfs     6436754736751AEE                     978e272d-3108-4e97-8906-2a513e791a79 System Reserved EFI System Partition
&#9492;&#9472;sda2 ext4     a5fe72a3-099a-4827-8794-f20c915f07a1 833d93bd-a6e6-4e82-8d69-413436b325d0                 
sdb                                                                                                       
&#9492;&#9472;sdb1 vfat     6A88-FD89                            064c751f-01                          BOOT-REPAIR     

Mount points (filtered): _______________________________________________________

            Avail Use% Mounted on
/dev/sda1    41.8M  16% /mnt/boot-sav/sda1
/dev/sda2   110.4G   0% /mnt/boot-sav/sda2
/dev/sdb1     1.1G  45% /cdrom

Mount options (filtered): ______________________________________________________


====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Boot-Repair-Disk session
Boot-Repair-Disk session (failsafe)

========================= sdb1/syslinux.cfg (filtered) =========================

DEFAULT loadconfig

LABEL loadconfig
  CONFIG /isolinux/isolinux.cfg
  APPEND /isolinux/

==================== sdb1: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             boot/grub/grub.cfg                             1

================== sdb1: Location of files loaded by Syslinux ==================

           GiB - GB             File                                 Fragment(s)
            ?? = ??             syslinux.cfg                                   1
            ?? = ??             ldlinux.sys                                    1



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would not act on the boot.
```

---

### Post by yancek on 2023-08-30
Boot repair shows sda1 as an EFI partition but it is not.  THere is no EFI partition and sda1 (windows?) does not show boot files and sda2 (Ubuntu?ext4) does not show boot files either.  Your disk is GPT so windows needs and would have had an EFI partition.   Your UEFI boot entries show one for windows but none for Ubuntu and since you have overwritten windows, you can't boot anything.

Your boot repair shows a lot less than is seen normally.  Probably due to not having a successful install of Ubuntu and overwriting windows.  When you reinstall Ubuntu,  make sure you boot in EFI mode and create an EFI partition.  Boot repair shows it booted in UEFI mode so leave that setting in the BIOS when you reinstall.

---

### Post by tea for one on 2023-08-30
```
sda1 [COLOR="#FF0000"]ntfs[/COLOR] 6436754736751AEE 978e272d-3108-4e97-8906-2a513e791a79 System Reserved EFI System Partition
```
Your supposed ESP has a ntfs file system rather than fat32.
The Ubuntu installer would not do that automatically, do you know how that happened?

---

### Post by oldfred on 2023-08-30
If posting code or text/terminal output, please use code tags.
Easy to add in Go Advanced Forum editor with # icon.
But with Boot-Repair better to use its option to post report to pastebin site.

Use gparted to change sda1 to FAT32 and then use Boot-Repair's advanced options to totally reinstall grub.
Be sure to boot installer in UEFI boot mode for UEFI type repairs.

---

### Post by rwps on 2023-08-30
Thanks all, I made an absolute mess of this, but managed to get it cleaned up by using Windows 10 Install media, then followed by Ubuntu full install (erase and install). No have Ubuntu firing well.

---

### Post by rwps on 2023-08-30
> **oldfred said:**
> If posting code or text/terminal output, please use code tags.
Easy to add in Go Advanced Forum editor with # icon.
But with Boot-Repair better to use its option to post report to pastebin site.
thanks for the good pointers!

---

