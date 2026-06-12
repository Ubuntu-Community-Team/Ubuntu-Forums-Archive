---
title: "Boot info"
date: 2024-03-13
forum: Installation &amp; Upgrades
---

### Post by sajadhaibat on 2024-03-13
```
boot-repair-4ppa2075                                              [20240313_1437]


============================== Boot Info Summary ===============================


 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------


sda1: __________________________________________________________________________


    File system:       vfat
    Boot sector type:  FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/ubuntu/grubx64.efi


sda2: __________________________________________________________________________


    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 


sda5: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 20.04.4 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /etc/default/grub 
                       /boot/grub/i386-pc/core.img


sda6: __________________________________________________________________________


    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        




================================ 1 OS detected =================================


OS#1:   The OS now in use - Ubuntu 20.04.4 LTS on sda5


================================ Host/Hardware =================================


CPU architecture: 64-bit
Video: HD Graphics 5500 GM108M [GeForce 840M] from Intel Corporation NVIDIA Corporation
BOOT_IMAGE of the installed session in use:
/boot/vmlinuz-5.15.0-79-generic root=UUID=a7ea17bd-2682-4b39-89e7-83bf0e7193f7 ro quiet splash vt.handoff=1
df -Th / : /dev/sda5      ext4  116G   77G   33G  70% /


===================================== UEFI =====================================


BIOS/UEFI firmware: A04(5.6) from Dell Inc.
The firmware seems EFI-compatible, but this installed-session is in Legacy/BIOS/CSM mode (not in EFI mode).




64349b3622c65f495a99dbf6102496e3   sda5/boot/bootx64.efi
a660182adef313615746a665966d2ccc   sda5/boot/mmx64.efi
a1da253696a304dce6b4668b70151c0e   sda1/ubuntu/grubx64.efi


============================= Drive/Partition Info =============================


Disks info: ____________________________________________________________________


sda    : notGPT,    no-BIOSboot,    has-noESP,     not-usb,    not-mmc, has-os,    no-wind,    2048 sectors * 512 bytes


Partitions info (1/3): _________________________________________________________


sda5    : is-os,    64, apt-get,    grub-pc ,    grub2,    grub-install,    grubenv-ok,    update-grub,    end-after-100GB
sda1    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far
sda6    : no-os,    64, nopakmgr,    no-docgrub,    nogrub,    nogrubinstall,    no-grubenv,    noupdategrub,    not-far


Partitions info (2/3): _________________________________________________________


sda5    : isnotESP,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda1    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot
sda6    : isnotESP,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot


Partitions info (3/3): _________________________________________________________


sda5    : not--sepboot,    with-boot,    fstab-without-boot,    not-sep-usr,    with--usr,    fstab-without-usr,    std-grub.d,    sda
sda1    : not--sepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda
sda6    : maybesepboot,    no---boot,    part-has-no-fstab,    not-sep-usr,    no---usr,    part-has-no-fstab,    no--grub.d,    sda


fdisk -l (filtered): ___________________________________________________________


Disk sda: 119.25 GiB, 128035676160 bytes, 250069680 sectors
Disk identifier: 0x965e7668
     Boot   Start       End   Sectors   Size Id Type
sda1          2048   1050623   1048576   512M  b W95 FAT32
sda2       1052670 250068991 249016322 118.8G  5 Extended
sda5       3100672 250068991 246968320 117.8G 83 Linux
sda6  *    1054720   3100671   2045952   999M 83 Linux
Partition table entries are not in disk order.


parted -lm (filtered): _________________________________________________________


sda:128GB:scsi:512:512:msdos:ATA SK hynix SC210 m:;
1:1049kB:538MB:537MB:fat32::;
2:539MB:128GB:127GB:::;
6:540MB:1588MB:1048MB:ext4::boot;
5:1588MB:128GB:126GB:ext4::;


blkid (filtered): ______________________________________________________________


NAME   FSTYPE   UUID                                 PARTUUID                             LABEL PARTLABEL
sda                                                                                             
&#9500;&#9472;sda1 vfat     7C1B-B4F2                            965e7668-01                                
&#9500;&#9472;sda2                                               965e7668-02                                
&#9500;&#9472;sda5 ext4     a7ea17bd-2682-4b39-89e7-83bf0e7193f7 965e7668-05                                
&#9492;&#9472;sda6 ext4     b065fb1e-2ae6-4402-9f45-54c425c8b916 965e7668-06                                


Mount points (filtered): _______________________________________________________


                        Avail Use% Mounted on
/dev/sda1              508.5M   0% /mnt/boot-sav/sda1
/dev/sda5               32.9G  66% /
/dev/sda6              900.1M   0% /mnt/boot-sav/sda6


Mount options (filtered): ______________________________________________________


/dev/sda1              vfat            rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro
/dev/sda5              ext4            rw,relatime,errors=remount-ro
/dev/sda6              ext4            rw,relatime


====================== sda5/boot/grub/grub.cfg (filtered) ======================


Ubuntu   a7ea17bd-2682-4b39-89e7-83bf0e7193f7
### END /etc/grub.d/30_os-prober ###
System setup   uefi-firmware
### END /etc/grub.d/30_uefi-firmware ###


========================== sda5/etc/fstab (filtered) ===========================


# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=a7ea17bd-2682-4b39-89e7-83bf0e7193f7 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
/swapfile                                 none            swap    sw              0       0


======================= sda5/etc/default/grub (filtered) =======================


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false


==================== sda5: Location of files loaded by Grub ====================


           GiB - GB             File                                 Fragment(s)
  14.866565704 = 15.962853376   boot/grub/grub.cfg                             1
  14.866546631 = 15.962832896   boot/grub/i386-pc/core.img                     1
  23.824695587 = 25.581572096   boot/vmlinuz-5.15.0-41-generic                 2
  91.926673889 = 98.705514496   boot/vmlinuz-5.15.0-56-generic                 1
  49.876949310 = 53.554966528   boot/vmlinuz-5.15.0-79-generic                 2
  91.926673889 = 98.705514496   boot/vmlinuz.old                               1
  90.689449310 = 97.377054720   boot/initrd.img                               11
 112.767574310 = 121.083260928  boot/initrd.img-5.15.0-41-generic             10
 117.958065033 = 126.656507904  boot/initrd.img-5.15.0-56-generic              7
  90.689449310 = 97.377054720   boot/initrd.img-5.15.0-79-generic             11
 117.958065033 = 126.656507904  boot/initrd.img.old                            7


===================== sda5: ls -l /etc/grub.d/ (filtered) ======================


-rwxr-xr-x 1 root root 12808 Feb  1  2023 10_linux
-rwxr-xr-x 1 root root 11298 Feb  1  2023 20_linux_xen
-rwxr-xr-x 1 root root 12059 Feb  1  2023 30_os-prober
-rwxr-xr-x 1 root root  1418 Feb  1  2023 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Feb  1  2023 40_custom
-rwxr-xr-x 1 root root   216 Feb  1  2023 41_custom






Suggested repair: ______________________________________________________________


The default repair of the Boot-Repair utility would reinstall the grub2 of
sda5 into the MBR of sda.
Grub-efi would not be selected by default because no ESP detected.
Additional repair would be performed: unhide-bootmenu-10s


paste.ubuntu.com ko ()
paste.debian.net ko ()
```

---

### Post by oldfred on 2024-03-13
Please use code tags if posting longer text or code output.
Easy to add with Forum's Go Advanced editor and # icon.

But with Boot-Repair better to just  post link to pastebin site it gives.

You did not say what your issue is. 
Boot-Repare report looks normal.

But it also looks like you have a newer UEFI system, but install is in old BIOS boot with very old MBR partitions.
Microsoft required vendors to installs Windows in UEFI boot mode to gpt partitioned drives starting in 2012, so most hardware is UEFI/gpt.

---

