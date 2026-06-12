---
title: "Problems with Ubuntu 20.04 dual boot"
date: 2020-05-23
forum: Installation &amp; Upgrades
---

### Post by jgalindoj on 2020-05-23
Hello!

I have dual boot for Ubuntu and Windows. I tried to Upgrade Ubuntu from 19.10 to 20.04 but the system crashed during upgrade.

I tried to re-install Ubuntu using a bootable USB Drive maintaining all files and software, yet this message appeared:

"No EFI System Partition was found. This system will likely not be able to boot successfully, and the installation process may fail."

I run GParted from the USB Drive and this is my actual configuration:

[ATTACH=CONFIG]285989[/ATTACH]

According to GParted, the /dev/sda1 partition is a FAT32 partition with boot flag. 
I also run tboot-repair and got the following results shown below. These results are available at: [https://paste.ubuntu.com/p/KNfh6jks6n/](https://paste.ubuntu.com/p/KNfh6jks6n/) . Thank you for your help.
Juan

boot-repair-4ppa123                                              [20200523_1822]

============================== Boot Info Summary ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (5.00 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 8/2012: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/Boot/fbx64.efi 
                       /efi/Boot/mmx64.efi /efi/ubuntu/grubx64.efi 
                       /efi/ubuntu/mmx64.efi /efi/ubuntu/shimx64.efi 
                       /efi/ubuntu/grub.cfg /efi/HP/BIOSUpdate/CryptRSA.efi 
                       /efi/HP/BIOSUpdate/HpBiosMgmt.efi 
                       /efi/HP/BIOSUpdate/HpBiosUpdate.efi 
                       /efi/HP/SystemDiags/CryptRSA.efi 
                       /efi/HP/SystemDiags/HpSysDiags.efi 
                       /efi/HP/SystemDiags/SystemDiags.efi 
                       /efi/Microsoft/Boot/bootmgfw.efi 
                       /efi/Microsoft/Boot/bootmgr.efi 
                       /efi/Microsoft/Boot/memtest.efi

sda2: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info: 

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 10
    Boot files:        /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        /etc/fstab

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 6.04
    Boot sector info:  Syslinux looks at sector 32784 of /dev/sdb1 for its 
                       second stage. The integrity check of Syslinux failed. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg 
                       /efi/BOOT/grubx64.efi /efi/BOOT/mmx64.efi /ldlinux.sys


================================ 5 OS detected =================================

OS#1:   Ubuntu 20.04 LTS on sda1
OS#2:   Ubuntu 20.04 LTS on sda3
OS#3:   Ubuntu 20.04 LTS on sda4
OS#4:   Ubuntu 20.04 LTS on sda5
OS#5:   Ubuntu 20.04 LTS on sda6

============================ Architecture/Host Info ============================

CPU architecture: 64-bit
Live-session OS is Ubuntu 64-bit (Ubuntu 20.04 LTS, focal, x86_64)


===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
SecureBoot enabled.

efibootmgr -v
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 2001,0000,3000,0001,2002,2004
Boot0000* ubuntu	HD(1,GPT,fb7dc12e-799b-442e-8006-ed674c7e24ad,0x800,0x82000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* Windows Boot Manager	HD(1,GPT,fb7dc12e-799b-442e-8006-ed674c7e24ad,0x800,0x82000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...H................
Boot0002* USB Hard Drive (UEFI) - SanDisk	PciRoot(0x0)/Pci(0x14,0x0)/USB(2,0)/HD(1,MBR,0x2d1542,0x800,0x1ca3800)RC
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot3000* Internal Hard Disk or Solid State Disk	RC



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sda	: is-GPT,	no-BIOSboot,	has---ESP, 	not-usb,	not-mmc, has-os,	2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sda1	: is-os,	64, apt-get,	grub-pc ,	grub2,	grub-install,	grubenv-ok,	update-grub,	not-far
sda3	: is-os,	64, apt-get,	grub-pc ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios
sda4	: is-os,	64, apt-get,	grub-pc ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios
sda5	: is-os,	64, apt-get,	grub-pc ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios
sda6	: is-os,	64, apt-get,	grub-pc ,	grub2,	grub-install,	grubenv-ok,	update-grub,	farbios

Partitions info (2/3): _________________________________________________________

sda1	: is---ESP,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda3	: isnotESP,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot
sda4	: isnotESP,	fstab-without-efi,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
sda5	: isnotESP,	fstab-without-efi,	no-nt,	no-winload,	recovery-or-hidden,	no-bmgr,	notwinboot
sda6	: isnotESP,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Partitions info (3/3): _________________________________________________________

sda1	: not-sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda3	: not-sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda4	: not-sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda5	: not-sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda
sda6	: not-sepboot,	with-boot,	fstab-without-boot,	not-sep-usr,	with--usr,	fstab-without-usr,	std-grub.d,	sda

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: EB87A399-A93F-48A1-B705-52E1E8EAB40D
          Start       End   Sectors   Size Type
sda1       2048    534527    532480   260M EFI System
sda2     534528    567295     32768    16M Microsoft reserved
sda3     567296 632883683 632316388 301.5G Microsoft basic data
sda4  935659520 937666559   2007040   980M Windows recovery environment
sda5  937666560 976762879  39096320  18.7G Microsoft basic data
sda6  632885248 935659519 302774272 144.4G Linux filesystem
Partition table entries are not in disk order.
Disk sdb: 14.33 GiB, 15376318464 bytes, 30031872 sectors
Disk identifier: 0x002d1542
      Boot Start      End  Sectors  Size Id Type
sdb1  *     2048 30031871 30029824 14.3G  c W95 FAT32 (LBA)

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:4096:gpt:ATA ST500LT012-1DG14:;
1:1049kB:274MB:273MB:fat32:EFI system partition:boot, esp;
2:274MB:290MB:16.8MB::Microsoft reserved partition:msftres;
3:290MB:324GB:324GB:ntfs:Basic data partition:msftdata;
6:324GB:479GB:155GB:ext4::;
4:479GB:480GB:1028MB:ntfs:Basic data partition:hidden, diag;
5:480GB:500GB:20.0GB:ntfs:Basic data partition:hidden, msftdata;
sdb:15.4GB:scsi:512:512:msdos:SanDisk Cruzer Blade:;
1:1049kB:15.4GB:15.4GB:fat32::boot, lba;

blkid (filtered): ______________________________________________________________

NAME   FSTYPE   UUID                                 PARTUUID                             LABEL            PARTLABEL
sda                                                                                                        
&#9500;&#9472;sda1 vfat     5E5A-B8FB                            fb7dc12e-799b-442e-8006-ed674c7e24ad                  EFI system partition
&#9500;&#9472;sda2                                               31dc4588-fe7e-48c1-8145-dee431ba1ef1                  Microsoft reserved partition
&#9500;&#9472;sda3 ntfs     E8B45E93B45E63DA                     727b367e-059a-46b7-a1b9-8a6200e714c8 Windows          Basic data partition
&#9500;&#9472;sda4 ntfs     5A1E46B81E468D47                     2f6648a5-9486-4ed7-a0cb-fb06e467cf17 Windows RE tools Basic data partition
&#9500;&#9472;sda5 ntfs     F81EB5EA1EB5A1D4                     f82be1a4-df13-450a-b6e6-6e53adddd16f RECOVERY         Basic data partition
&#9492;&#9472;sda6 ext4     3033201f-8e42-4738-9b52-a9add911f2a0 70a7fb96-9146-4835-b561-d1af53026211                  
sdb                                                                                                        
&#9492;&#9472;sdb1 vfat     126C-81E3                            002d1542-01                          UBUNTU 20_0      

df (filtered): _________________________________________________________________

       Avail Use% Mounted on
sdb1   11.8G  18% /cdrom

Mount options: __________________________________________________________________

sdb1  ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro

===================== sda1/efi/ubuntu/grub.cfg (filtered) ======================

search.fs_uuid 581c463b-27d9-4451-b9b9-580783e441a0 root hd0,gpt6 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg

========================== sda6/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/swapfile                                 none            swap    sw              0       0

====================== sdb1/boot/grub/grub.cfg (filtered) ======================

Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Boot from next volume
UEFI Firmware Settings

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

The default repair of the Boot-Repair utility will purge (in order to fix packages) and reinstall the grub-efi-amd64-signed of
sda1,
using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file    



Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04 LTS entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file) !

---

### Post by ubfan1 on 2020-05-23
Looks like you have secure boot on, but in the efi/Boot/ directory, assuming bootx64.efi is a copy of efi/ubuntu/shimx64.efi (check sizes), then grubx64.efi is missing from that directory.  Copy it from efi/ubuntu/grubx64.efi and see if that allows a boot.  The efi/Boot directory is the device boot directory, used for removable media, but may be used as a fallback boot if the nvram boot selection fails for any reason (like some vendor limit on what name a bootloader may have).

---

### Post by jgalindoj on 2020-05-24
It worked. Thank you!

---

