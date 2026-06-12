---
title: "boot repair"
date: 2024-04-12
forum: Installation &amp; Upgrades
---

### Post by larryb1607 on 2024-04-12
Trying to switch from older Ubuntu distro to newest Ubuntu Cinnamon.  All files are on an external HDD that has several partitions.  Device is sdc.  The older Ubuntu is on sdc5 & sdc6.  Grub 2 is on sdc5.  Cinnamon us on sdc8 & sdc7.  I did not install a bootloader when installing the Cinnamon as I found that part very confusing.  I was just hoping Grub would see the Cinnamon and give me that option.  I would like to have both distros available and slowly move to the Cinnamon one.  I ran boot repair and it basically says I should move the Grub to sdc.  That still does not solve being able to boot either system.  If I did this, and then just installed  Cinnamon bootloader at /boot would that accomplish what I want?  Here are the screens of the advanced boot repair opions options unchanged.  I am also including the repair log.  thanks


pastebin
```
Paste from boot-repair 12 April 2024 17:55 +0000

This paste expires on 2024-05-13.

Syntax highlighting: bash
View raw

boot-repair-4ppa2075                                              [20240412_1354]

============================== Boot Info Summary ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sdc and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sdc1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sdc5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.6 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img

sdc6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        


================================ 3 OS detected =================================

OS#1:   The OS now in use - Ubuntu 20.04.6 LTS on sdc5
OS#2:   Windows 7 (boot) on sda2
OS#3:   Windows 7 on sda3

================================ Host/Hardware =================================

CPU architecture: 64-bit
Video: 3rd Gen Core processor Graphics Controller from Intel Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.4.0-176-generic root=UUID=7143b8d5-260d-42cc-b24b-c1f963d1a305 ro quiet splash vt.handoff=7
df -Th / : /dev/sdc5      ext4   28G   11G   16G  42% /

===================================== UEFI =====================================

BIOS/UEFI firmware: A13 from Dell Inc.
This installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).



============================= Drive/Partition Info =============================

Disks info: ____________________________________________________________________

sdc    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2046 sectors * 512 bytes
sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    has-win,    63 sectors * 512 bytes
sdb    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, no-os,    no-wind,    2048 sectors * 512 bytes

Partitions info (1/3): _________________________________________________________

sdc5    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ng,    update-grub,    not-far
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda2    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda3    : is-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda5    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sda7    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc2    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sdc7    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdc8    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    end-after-100GB
sdb1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far

Partitions info (2/3): _________________________________________________________

sdc5    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot
sda2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda3    : isnotESP,    part-has-no-fstab,    no-nt,    haswinload,    no-recov-nor-hid,    bootmgr,    is-winboot
sda5    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda7    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc2    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc7    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdc8    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sdb1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    recovery-or-hidden,    no-bmgr,    notwinboot

Partitions info (3/3): _________________________________________________________

sdc5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sdc
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda3    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda5    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda6    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda7    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sdc2    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc6    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc7    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdc8    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdc
sdb1    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sdb

fdisk -l (filtered): ___________________________________________________________

Disk sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk identifier: 0x0001fb10
     Boot     Start       End   Sectors   Size Id Type
sda1              63     80324     80262  39.2M de Dell Utility
sda2           81920  58101759  58019840  27.7G  7 HPFS/NTFS/exFAT
sda3  *     58101760 359698431 301596672 143.8G  7 HPFS/NTFS/exFAT
sda4       359700417 976764927 617064511 294.2G  f W95 Ext'd (LBA)
sda5       359700480 486510591 126810112  60.5G  7 HPFS/NTFS/exFAT
sda6       486512640 527470591  40957952  19.5G  b W95 FAT32
sda7       527472640 976764927 449292288 214.2G  7 HPFS/NTFS/exFAT
Disk sdb: 29.84 GiB, 32017047552 bytes, 62533296 sectors
Disk identifier: 0x6ffdaf18
     Boot Start      End  Sectors Size Id Type
sdb1        2048 16775167 16773120   8G 84 OS/2 hidden or Intel hibernation
Disk sdc: 931.49 GiB, 1000170586112 bytes, 1953458176 sectors
Disk identifier: 0x6416a379
     Boot     Start        End    Sectors   Size Id Type
sdc1            2046  293416959  293414914 139.9G  f W95 Ext'd (LBA)
sdc2       293417088 1953458111 1660041024 791.6G  7 HPFS/NTFS/exFAT
sdc5            2048   60000255   59998208  28.6G 83 Linux
sdc6        60002304  172584959  112582656  53.7G 83 Linux
sdc7       217643008  293416959   75773952  36.1G 83 Linux
sdc8       172587008  217641695   45054688  21.5G 83 Linux
Partition table entries are not in disk order.

parted -lm (filtered): _________________________________________________________

sda:500GB:scsi:512:4096:msdos:ATA ST500LT012-9WS14:;
1:32.3kB:41.1MB:41.1MB:fat16::diag;
2:41.9MB:29.7GB:29.7GB:ntfs::;
3:29.7GB:184GB:154GB:ntfs::boot;
4:184GB:500GB:316GB:::lba;
5:184GB:249GB:64.9GB:ntfs::;
6:249GB:270GB:21.0GB:fat32::;
7:270GB:500GB:230GB:ntfs::;
sdb:32.0GB:scsi:512:512:msdos:ATA SAMSUNG SSD PM83:;
1:1049kB:8589MB:8588MB:::irst;
sdc:1000GB:scsi:512:512:msdos:WD Elements 10A8:;
1:1048kB:150GB:150GB:::lba;
5:1049kB:30.7GB:30.7GB:ext4::;
6:30.7GB:88.4GB:57.6GB:ext4::;
8:88.4GB:111GB:23.1GB:ext4::;
7:111GB:150GB:38.8GB:ext4::;
2:150GB:1000GB:850GB:ntfs::;

Free space >10MiB: ______________________________________________________________

sdb: 8191MiB:30534MiB:22343MiB

blkid (filtered): ______________________________________________________________

NAME   FSTYPE          UUID                                 PARTUUID                             LABEL      PARTLABEL
sda    isw_raid_member                                                                                      
&#9500;&#9472;sda1 vfat            5450-4444                            0001fb10-01                                     
&#9500;&#9472;sda2 ntfs            4E30C3EF30C3DC59                     0001fb10-02                          RECOVERY   
&#9500;&#9472;sda3 ntfs            3448C71648C6D630                     0001fb10-03                          OS         
&#9500;&#9472;sda4                                                      0001fb10-04                                     
&#9500;&#9472;sda5 ntfs            01D6AA41EF5AF4C0                     0001fb10-05                          L          
&#9500;&#9472;sda6 vfat            865C-8A44                            0001fb10-06                          NEW VOLUME 
&#9492;&#9472;sda7 ntfs            8C689D01689CEAEA                     0001fb10-07                          New Volume 
sdb    isw_raid_member                                                                                      
&#9492;&#9472;sdb1                                                      6ffdaf18-01                                     
sdc                                                                                                         
&#9500;&#9472;sdc1                                                      6416a379-01                                     
&#9500;&#9472;sdc2 ntfs            92A816A5A81687BD                     6416a379-02                          G          
&#9500;&#9472;sdc5 ext4            7143b8d5-260d-42cc-b24b-c1f963d1a305 6416a379-05                                     
&#9500;&#9472;sdc6 ext4            5e840212-391d-4052-ad88-244b25d2be9f 6416a379-06                                     
&#9500;&#9472;sdc7 ext4            2441c36f-eedb-408f-9251-2b819077f21e 6416a379-07                                     
&#9492;&#9472;sdc8 ext4            afbfb1bf-1ec6-414c-abdb-6255eb593cc4 6416a379-08                                     

Mount points (filtered): _______________________________________________________

             Avail Use% Mounted on
/dev/sda1      39M   0% /mnt/boot-sav/sda1
/dev/sda2    12.6G  55% /mnt/boot-sav/sda2
/dev/sda3    83.8G  42% /mnt/boot-sav/sda3
/dev/sda5      50G  17% /mnt/boot-sav/sda5
/dev/sda6    19.5G   0% /mnt/boot-sav/sda6
/dev/sda7     168G  22% /mnt/boot-sav/sda7
/dev/sdc2   700.8G  11% /mnt/boot-sav/sdc2
/dev/sdc5    15.6G  39% /
/dev/sdc6    30.5G  37% /home
/dev/sdc7    33.5G   0% /mnt/boot-sav/sdc7
/dev/sdc8    19.9G   0% /mnt/boot-sav/sdc8

Mount options (filtered): ______________________________________________________

/dev/sda1   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda2   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda3   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda5   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sda6   vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda7   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc2   fuseblk         rw,relatime,user_id=0,group_id=0,allow_other,blksize=4096
/dev/sdc5   ext4            rw,relatime,errors=remount-ro
/dev/sdc6   ext4            rw,relatime
/dev/sdc7   ext4            rw,relatime
/dev/sdc8   ext4            rw,relatime

====================== sdc5/boot/grub/grub.cfg (filtered) ======================

Linux Lite GNU/Linux   7143b8d5-260d-42cc-b24b-c1f963d1a305
Windows 7 (on sda2)   4E30C3EF30C3DC59
Windows 7 (on sda3)   3448C71648C6D630
### END /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_uefi-firmware ###

========================== sdc5/etc/fstab (filtered) ===========================

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdg5 during installation
UUID=7143b8d5-260d-42cc-b24b-c1f963d1a305 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdg6 during installation
UUID=5e840212-391d-4052-ad88-244b25d2be9f /home           ext4    defaults        0       2
/swapfile                                 none            swap    sw              0       0

======================= sdc5/etc/default/grub (filtered) =======================

GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR='Linux Lite'
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_BACKGROUND="/boot/grub_linux_lite.png"

==================== sdc5: Location of files loaded by Grub ====================

           GiB - GB             File                                 Fragment(s)
  21.095188141 = 22.650785792   boot/grub/grub.cfg                             2
   8.262863159 = 8.872181760    boot/grub/i386-pc/core.img                     1
  15.302787781 = 16.431243264   boot/vmlinuz                                   2
  12.732471466 = 13.671387136   boot/vmlinuz-5.4.0-174-generic                 2
  15.302787781 = 16.431243264   boot/vmlinuz-5.4.0-176-generic                 2
  12.732471466 = 13.671387136   boot/vmlinuz.old                               2
  17.102172852 = 18.363318272   boot/initrd.img                                5
  15.024040222 = 16.131940352   boot/initrd.img-5.4.0-174-generic              5
  17.102172852 = 18.363318272   boot/initrd.img-5.4.0-176-generic              5
  15.024040222 = 16.131940352   boot/initrd.img.old                            5

===================== sdc5: ls -l /etc/grub.d/ (filtered) ======================

-rwxr-xr-x 1 root root 18224 Jan 11  2022 10_linux
-rwxr-xr-x 1 root root 42359 Aug 17  2020 10_linux_zfs
-rwxr-xr-x 1 root root 13101 Dec 18  2022 20_linux_xen
-rwxr-xr-x 1 root root 12059 Dec 14  2019 30_os-prober
-rwxr-xr-x 1 root root  1424 Feb 26  2020 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 14  2019 40_custom
-rwxr-xr-x 1 root root   216 Dec 14  2019 41_custom



Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to reset grubenv) and reinstall the grub2 of
sdc5 into the MBR of sdc.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s

Final advice in case of suggested repair: ______________________________________

Please do not forget to make your BIOS boot on sdc (WD Elements 10A8) disk!

New paste
```
Poster:

Your name (30 characters max)
Syntax:
Expiration:

Approximate and not guaranteed
Content:
© 2024 Canonical Ltd. Ubuntu and Canonical are registered trademarks of Canonical Ltd.

    Legal info 

Go to the top of the page

---

### Post by oldfred on 2024-04-12
Please use Code tags with text or terminal output.
And with Boot-Repair better to just post link it provides to pastebin site for your report.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


You show older BIOS/MBR system with Windows 7 (obsolete) and Linux Lite, but no other install?
System says RAID, so do you have Intel RST or Optane (Obsolete) drive as sdb? That often confuses installer. May need RAID drivers to see partitions.

BIOS systems only boot from MBR and MBR can only have one boot loader. Best to keep Windows boot loader in Windows drive and grub in Linux drive.
Grub will boot other systems, if not hibernated and able to be seen by os-prober. 

Do not attempt to share a /boot partition, that leads to systems getting mixed up.
You can only share a /home if upgrading as older or different versions of software may need different settings in /home.
You can share a data only partition. I put all data normally in /home into a data only partition, so can multiple boot many Ubuntu installs but have same data, but possibly different settings in /home.

Your / (root) is not particularly large. Ubuntu now uses snaps which can take a lot of space. I use Kubuntu with no snaps and use 15GB, but have seen posts where users have 20GB in snaps alone.

What model Dell system?
Many with Optane remove it. It only is used for Windows fast startup hibernation file to make Windows boot faster. Some have replaced Optane with newer larger M.2 SSD. I recommend SSD for faster system.

Optane removal apps
removal (setuprst.exe and setupoptanememory.exe - both from Dell
Windows AHCI driver install:
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
Used Intel App in Windows to disable Optane, need AHCI driver in Windows.
[https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735](https://ubuntuforums.org/showthread.php?t=2458373&p=14022735#post14022735) & 
[https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab](https://www.microsoft.com/en-us/p/intel-optane-memory-and-storage-management/9mzng5hzwz1t?activetab=pivot:overviewtab)

---

### Post by hyperlinxe on 2024-04-12
Yes larryb1607 you must properly install grub, in order to use the grub bootloader...if you have grub properly installed on both operating systems, which is done automatically by the installers, or by you manually, and turn on grub OS prober in the one that gets loaded first, update grub, reboot, and update grub again it will identify the other OS, and you will be able to boot them both from one menu.

(there are other ways to get it working, there are many possible configurations, but that is the most basic.)

---

